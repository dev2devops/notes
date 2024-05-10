#Docker 
# Docker volume plugins[🔗](https://docs.docker.com/engine/extend/plugins_volume/#docker-volume-plugins)
Docker Engine volume plugins enable Engine deployments to be integrated with external storage systems such as Amazon EBS, and enable data volumes to persist beyond the lifetime of a single Docker host. See the [plugin documentation](https://docs.docker.com/engine/extend/legacy_plugins/) for more information.

## Changelog[](https://docs.docker.com/engine/extend/plugins_volume/#changelog)

### 1.13.0[](https://docs.docker.com/engine/extend/plugins_volume/#1130)

-   If used as part of the v2 plugin architecture, mountpoints that are part of paths returned by the plugin must be mounted under the directory specified by `PropagatedMount` in the plugin configuration ([#26398](https://github.com/docker/docker/pull/26398))

### 1.12.0[](https://docs.docker.com/engine/extend/plugins_volume/#1120)

-   Add `Status` field to `VolumeDriver.Get` response ([#21006](https://github.com/docker/docker/pull/21006#))
-   Add `VolumeDriver.Capabilities` to get capabilities of the volume driver ([#22077](https://github.com/docker/docker/pull/22077))

### 1.10.0[](https://docs.docker.com/engine/extend/plugins_volume/#1100)

-   Add `VolumeDriver.Get` which gets the details about the volume ([#16534](https://github.com/docker/docker/pull/16534))
-   Add `VolumeDriver.List` which lists all volumes owned by the driver ([#16534](https://github.com/docker/docker/pull/16534))

### 1.8.0[](https://docs.docker.com/engine/extend/plugins_volume/#180)

-   Initial support for volume driver plugins ([#14659](https://github.com/docker/docker/pull/14659))

## Command-line changes[](https://docs.docker.com/engine/extend/plugins_volume/#command-line-changes)

To give a container access to a volume, use the `--volume` and `--volume-driver` flags on the `docker container run` command. The `--volume` (or `-v`) flag accepts a volume name and path on the host, and the `--volume-driver` flag accepts a driver type.

```
$ docker volume create --driver=flocker volumename

$ docker container run -it --volume volumename:/data busybox sh
```

### `--volume`[](https://docs.docker.com/engine/extend/plugins_volume/#--volume)

The `--volume` (or `-v`) flag takes a value that is in the format `<volume_name>:<mountpoint>`. The two parts of the value are separated by a colon (`:`) character.

-   The volume name is a human-readable name for the volume, and cannot begin with a `/` character. It is referred to as `volume_name` in the rest of this topic.
-   The `Mountpoint` is the path on the host (v1) or in the plugin (v2) where the volume has been made available.

### `volumedriver`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriver)

Specifying a `volumedriver` in conjunction with a `volumename` allows you to use plugins such as [Flocker](https://github.com/ScatterHQ/flocker) to manage volumes external to a single host, such as those on EBS.

## Create a VolumeDriver[](https://docs.docker.com/engine/extend/plugins_volume/#create-a-volumedriver)

The container creation endpoint (`/containers/create`) accepts a `VolumeDriver` field of type `string` allowing to specify the name of the driver. If not specified, it defaults to `"local"` (the default driver for local volumes).

## Volume plugin protocol[](https://docs.docker.com/engine/extend/plugins_volume/#volume-plugin-protocol)

If a plugin registers itself as a `VolumeDriver` when activated, it must provide the Docker Daemon with writeable paths on the host filesystem. The Docker daemon provides these paths to containers to consume. The Docker daemon makes the volumes available by bind-mounting the provided paths into the containers.

> **Note**
> 
> Volume plugins should _not_ write data to the `/var/lib/docker/` directory, including `/var/lib/docker/volumes`. The `/var/lib/docker/` directory is reserved for Docker.

### `/VolumeDriver.Create`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedrivercreate)

**Request**:

```
{
    "Name": "volume_name",
    "Opts": {}
}
```

Instruct the plugin that the user wants to create a volume, given a user specified volume name. The plugin does not need to actually manifest the volume on the filesystem yet (until `Mount` is called). `Opts` is a map of driver specific options passed through from the user request.

**Response**:

```
{
    "Err": ""
}
```

Respond with a string error if an error occurred.

### `/VolumeDriver.Remove`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriverremove)

**Request**:

```
{
    "Name": "volume_name"
}
```

Delete the specified volume from disk. This request is issued when a user invokes `docker rm -v` to remove volumes associated with a container.

**Response**:

```
{
    "Err": ""
}
```

Respond with a string error if an error occurred.

### `/VolumeDriver.Mount`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedrivermount)

**Request**:

```
{
    "Name": "volume_name",
    "ID": "b87d7442095999a92b65b3d9691e697b61713829cc0ffd1bb72e4ccd51aa4d6c"
}
```

Docker requires the plugin to provide a volume, given a user specified volume name. `Mount` is called once per container start. If the same `volume_name` is requested more than once, the plugin may need to keep track of each new mount request and provision at the first mount request and deprovision at the last corresponding unmount request.

`ID` is a unique ID for the caller that is requesting the mount.

**Response**:

-   **v1**:
    
    ```
    {
        "Mountpoint": "/path/to/directory/on/host",
        "Err": ""
    }
    ```
    
-   **v2**:
    
    ```
    {
        "Mountpoint": "/path/under/PropagatedMount",
        "Err": ""
    }
    ```
    

`Mountpoint` is the path on the host (v1) or in the plugin (v2) where the volume has been made available.

`Err` is either empty or contains an error string.

### `/VolumeDriver.Path`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriverpath)

**Request**:

```
{
    "Name": "volume_name"
}
```

Request the path to the volume with the given `volume_name`.

**Response**:

-   **v1**:
    
    ```
    {
        "Mountpoint": "/path/to/directory/on/host",
        "Err": ""
    }
    ```
    
-   **v2**:
    
    ```
    {
        "Mountpoint": "/path/under/PropagatedMount",
        "Err": ""
    }
    ```
    

Respond with the path on the host (v1) or inside the plugin (v2) where the volume has been made available, and/or a string error if an error occurred.

`Mountpoint` is optional. However, the plugin may be queried again later if one is not provided.

### `/VolumeDriver.Unmount`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriverunmount)

**Request**:

```
{
    "Name": "volume_name",
    "ID": "b87d7442095999a92b65b3d9691e697b61713829cc0ffd1bb72e4ccd51aa4d6c"
}
```

Docker is no longer using the named volume. `Unmount` is called once per container stop. Plugin may deduce that it is safe to deprovision the volume at this point.

`ID` is a unique ID for the caller that is requesting the mount.

**Response**:

```
{
    "Err": ""
}
```

Respond with a string error if an error occurred.

### `/VolumeDriver.Get`[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriverget)

**Request**:

```
{
    "Name": "volume_name"
}
```

Get info about `volume_name`.

**Response**:

-   **v1**:
    
    ```
    {
      "Volume": {
        "Name": "volume_name",
        "Mountpoint": "/path/to/directory/on/host",
        "Status": {}
      },
      "Err": ""
    }
    ```
    
-   **v2**:
    
    ```
    {
      "Volume": {
        "Name": "volume_name",
        "Mountpoint": "/path/under/PropagatedMount",
        "Status": {}
      },
      "Err": ""
    }
    ```
    

Respond with a string error if an error occurred. `Mountpoint` and `Status` are optional.

### /VolumeDriver.List[](https://docs.docker.com/engine/extend/plugins_volume/#volumedriverlist)

**Request**:

```
{}
```

Get the list of volumes registered with the plugin.

**Response**:

-   **v1**:
    
    ```
    {
      "Volumes": [
        {
          "Name": "volume_name",
          "Mountpoint": "/path/to/directory/on/host"
        }
      ],
      "Err": ""
    }
    ```
    
-   **v2**:
    
    ```
    {
      "Volumes": [
        {
          "Name": "volume_name",
          "Mountpoint": "/path/under/PropagatedMount"
        }
      ],
      "Err": ""
    }
    ```
    

Respond with a string error if an error occurred. `Mountpoint` is optional.

### /VolumeDriver.Capabilities[](https://docs.docker.com/engine/extend/plugins_volume/#volumedrivercapabilities)

**Request**:

```
{}
```

Get the list of capabilities the driver supports.

The driver is not required to implement `Capabilities`. If it is not implemented, the default values are used.

**Response**:

```
{
  "Capabilities": {
    "Scope": "global"
  }
}
```

Supported scopes are `global` and `local`. Any other value in `Scope` will be ignored, and `local` is used. `Scope` allows cluster managers to handle the volume in different ways. For instance, a scope of `global`, signals to the cluster manager that it only needs to create the volume once instead of on each Docker host. More capabilities may be added in the future.