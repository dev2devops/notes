#Docker 
# Disable networking for a container
If you want to completely disable the networking stack on a container, you can use the `--network none` flag when starting the container. Within the container, only the loopback device is created. The following example illustrates this.

1.  Create the container.
    
    ```
    $ docker run --rm -dit \
      --network none \
      --name no-net-alpine \
      alpine:latest \
      ash
    ```
    
2.  Check the container’s network stack, by executing some common networking commands within the container. Notice that no `eth0` was created.
    
    ```
    $ docker exec no-net-alpine ip link show
    
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    2: tunl0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN qlen 1
        link/ipip 0.0.0.0 brd 0.0.0.0
    3: ip6tnl0@NONE: <NOARP> mtu 1452 qdisc noop state DOWN qlen 1
        link/tunnel6 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 brd 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
    ```
    
    ```
    $ docker exec no-net-alpine ip route
    ```
    
    The second command returns empty because there is no routing table.
    
3.  Stop the container. It is removed automatically because it was created with the `--rm` flag.
    
    ```
    $ docker stop no-net-alpine
    ```