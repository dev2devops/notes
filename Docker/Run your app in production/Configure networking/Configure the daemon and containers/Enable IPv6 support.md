#Docker 
# Enable IPv6 support
Before you can use IPv6 in Docker containers or swarm services, you need to enable IPv6 support in the Docker daemon. Afterward, you can choose to use either IPv4 or IPv6 (or both) with any container, service, or network.

> **Note**: IPv6 networking is only supported on Docker daemons running on Linux hosts.

1.  Edit `/etc/docker/daemon.json`, set the `ipv6` key to `true` and the `fixed-cidr-v6` key to your IPv6 subnet. In this example we are setting it to `2001:db8:1::/64`.
    
    ```
    {
      "ipv6": true,
      "fixed-cidr-v6": "2001:db8:1::/64"
    }
    ```
    
    Save the file.
    
2.  Reload the Docker configuration file.
    
    ```
    $ systemctl reload docker
    ```
    

You can now create networks with the `--ipv6` flag and assign containers IPv6 addresses using the `--ip6` flag.