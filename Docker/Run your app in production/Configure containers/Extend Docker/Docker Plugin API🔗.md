#Docker 
# Docker Plugin API[🔗](https://docs.docker.com/engine/extend/plugin_api/#docker-plugin-api)
Docker plugins are out-of-process extensions which add capabilities to the Docker Engine.

This document describes the Docker Engine plugin API. To view information on plugins managed by Docker Engine, refer to [Docker Engine plugin system](https://docs.docker.com/engine/extend/).

This page is intended for people who want to develop their own Docker plugin. If you just want to learn about or use Docker plugins, look [here](https://docs.docker.com/engine/extend/legacy_plugins/).

## What plugins are[](https://docs.docker.com/engine/extend/plugin_api/#what-plugins-are)

A plugin is a process running on the same or a different host as the docker daemon, which registers itself by placing a file on the same docker host in one of the plugin directories described in [Plugin discovery](https://docs.docker.com/engine/extend/plugin_api/#plugin-discovery).

Plugins have human-readable names, which are short, lowercase strings. For example, `flocker` or `weave`.

Plugins can run inside or outside containers. Currently running them outside containers is recommended.

## Plugin discovery[](https://docs.docker.com/engine/extend/plugin_api/#plugin-discovery)

Docker discovers plugins by looking for them in the plugin directory whenever a user or container tries to use one by name.

There are three types of files which can be put in the plugin directory.

-   `.sock` files are UNIX domain sockets.
-   `.spec` files are text files containing a URL, such as `unix:///other.sock` or `tcp://localhost:8080`.
-   `.json` files are text files containing a full json specification for the plugin.

Plugins with UNIX domain socket files must run on the same docker host, whereas plugins with spec or json files can run on a different host if a remote URL is specified.

UNIX domain socket files must be located under `/run/docker/plugins`, whereas spec files can be located either under `/etc/docker/plugins` or `/usr/lib/docker/plugins`.

The name of the file (excluding the extension) determines the plugin name.

For example, the `flocker` plugin might create a UNIX socket at `/run/docker/plugins/flocker.sock`.

You can define each plugin into a separated subdirectory if you want to isolate definitions from each other. For example, you can create the `flocker` socket under `/run/docker/plugins/flocker/flocker.sock` and only mount `/run/docker/plugins/flocker` inside the `flocker` container.

Docker always searches for unix sockets in `/run/docker/plugins` first. It checks for spec or json files under `/etc/docker/plugins` and `/usr/lib/docker/plugins` if the socket doesn’t exist. The directory scan stops as soon as it finds the first plugin definition with the given name.

### JSON specification[](https://docs.docker.com/engine/extend/plugin_api/#json-specification)

This is the JSON format for a plugin:

```
{
  "Name": "plugin-example",
  "Addr": "https://example.com/docker/plugin",
  "TLSConfig": {
    "InsecureSkipVerify": false,
    "CAFile": "/usr/shared/docker/certs/example-ca.pem",
    "CertFile": "/usr/shared/docker/certs/example-cert.pem",
    "KeyFile": "/usr/shared/docker/certs/example-key.pem"
  }
}
```

The `TLSConfig` field is optional and TLS will only be verified if this configuration is present.

## Plugin lifecycle[](https://docs.docker.com/engine/extend/plugin_api/#plugin-lifecycle)

Plugins should be started before Docker, and stopped after Docker. For example, when packaging a plugin for a platform which supports `systemd`, you might use [`systemd` dependencies](https://www.freedesktop.org/software/systemd/man/systemd.unit.html#Before=) to manage startup and shutdown order.

When upgrading a plugin, you should first stop the Docker daemon, upgrade the plugin, then start Docker again.

## Plugin activation[](https://docs.docker.com/engine/extend/plugin_api/#plugin-activation)

When a plugin is first referred to -- either by a user referring to it by name (e.g. `docker run --volume-driver=foo`) or a container already configured to use a plugin being started -- Docker looks for the named plugin in the plugin directory and activates it with a handshake. See Handshake API below.

Plugins are _not_ activated automatically at Docker daemon startup. Rather, they are activated only lazily, or on-demand, when they are needed.

## Systemd socket activation[](https://docs.docker.com/engine/extend/plugin_api/#systemd-socket-activation)

Plugins may also be socket activated by `systemd`. The official [Plugins helpers](https://github.com/docker/go-plugins-helpers) natively supports socket activation. In order for a plugin to be socket activated it needs a `service` file and a `socket` file.

The `service` file (for example `/lib/systemd/system/your-plugin.service`):

```systemd
[Unit]
Description=Your plugin
Before=docker.service
After=network.target your-plugin.socket
Requires=your-plugin.socket docker.service

[Service]
ExecStart=/usr/lib/docker/your-plugin

[Install]
WantedBy=multi-user.target
```

The `socket` file (for example `/lib/systemd/system/your-plugin.socket`):

```systemd
[Unit]
Description=Your plugin

[Socket]
ListenStream=/run/docker/plugins/your-plugin.sock

[Install]
WantedBy=sockets.target
```

This will allow plugins to be actually started when the Docker daemon connects to the sockets they’re listening on (for instance the first time the daemon uses them or if one of the plugin goes down accidentally).

## API design[](https://docs.docker.com/engine/extend/plugin_api/#api-design)

The Plugin API is RPC-style JSON over HTTP, much like webhooks.

Requests flow _from_ the Docker daemon _to_ the plugin. So the plugin needs to implement an HTTP server and bind this to the UNIX socket mentioned in the “plugin discovery” section.

All requests are HTTP `POST` requests.

The API is versioned via an Accept header, which currently is always set to `application/vnd.docker.plugins.v1+json`.

## Handshake API[](https://docs.docker.com/engine/extend/plugin_api/#handshake-api)

Plugins are activated via the following “handshake” API call.

### /Plugin.Activate[](https://docs.docker.com/engine/extend/plugin_api/#pluginactivate)

**Request:** empty body

**Response:**

```
{
    "Implements": ["VolumeDriver"]
}
```

Responds with a list of Docker subsystems which this plugin implements. After activation, the plugin will then be sent events from this subsystem.

Possible values are:

-   [`authz`](https://docs.docker.com/engine/extend/plugins_authorization/)
-   [`NetworkDriver`](https://docs.docker.com/engine/extend/plugins_network/)
-   [`VolumeDriver`](https://docs.docker.com/engine/extend/plugins_volume/)

## Plugin retries[](https://docs.docker.com/engine/extend/plugin_api/#plugin-retries)

Attempts to call a method on a plugin are retried with an exponential backoff for up to 30 seconds. This may help when packaging plugins as containers, since it gives plugin containers a chance to start up before failing any user containers which depend on them.

## Plugins helpers[](https://docs.docker.com/engine/extend/plugin_api/#plugins-helpers)

To ease plugins development, we’re providing an `sdk` for each kind of plugins currently supported by Docker at [docker/go-plugins-helpers](https://github.com/docker/go-plugins-helpers).