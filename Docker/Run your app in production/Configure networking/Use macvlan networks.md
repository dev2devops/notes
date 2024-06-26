#Docker 
# Use macvlan networks
Some applications, especially legacy applications or applications which monitor network traffic, expect to be directly connected to the physical network. In this type of situation, you can use the `macvlan` network driver to assign a MAC address to each container’s virtual network interface, making it appear to be a physical network interface directly connected to the physical network. In this case, you need to designate a physical interface on your Docker host to use for the `macvlan`, as well as the subnet and gateway of the `macvlan`. You can even isolate your `macvlan` networks using different physical network interfaces. Keep the following things in mind:

-   It is very easy to unintentionally damage your network due to IP address exhaustion or to “VLAN spread”, which is a situation in which you have an inappropriately large number of unique MAC addresses in your network.
    
-   Your networking equipment needs to be able to handle “promiscuous mode”, where one physical interface can be assigned multiple MAC addresses.
    
-   If your application can work using a bridge (on a single Docker host) or overlay (to communicate across multiple Docker hosts), these solutions may be better in the long term.
    

## Create a macvlan network[](https://docs.docker.com/network/macvlan/#create-a-macvlan-network)

When you create a `macvlan` network, it can either be in bridge mode or 802.1q trunk bridge mode.

-   In bridge mode, `macvlan` traffic goes through a physical device on the host.
    
-   In 802.1q trunk bridge mode, traffic goes through an 802.1q sub-interface which Docker creates on the fly. This allows you to control routing and filtering at a more granular level.
    

### Bridge mode[](https://docs.docker.com/network/macvlan/#bridge-mode)

To create a `macvlan` network which bridges with a given physical network interface, use `--driver macvlan` with the `docker network create` command. You also need to specify the `parent`, which is the interface the traffic will physically go through on the Docker host.

```
$ docker network create -d macvlan \
  --subnet=172.16.86.0/24 \
  --gateway=172.16.86.1 \
  -o parent=eth0 pub_net
```

If you need to exclude IP addresses from being used in the `macvlan` network, such as when a given IP address is already in use, use `--aux-addresses`:

```
$ docker network create -d macvlan \
  --subnet=192.168.32.0/24 \
  --ip-range=192.168.32.128/25 \
  --gateway=192.168.32.254 \
  --aux-address="my-router=192.168.32.129" \
  -o parent=eth0 macnet32
```

### 802.1q trunk bridge mode[](https://docs.docker.com/network/macvlan/#8021q-trunk-bridge-mode)

If you specify a `parent` interface name with a dot included, such as `eth0.50`, Docker interprets that as a sub-interface of `eth0` and creates the sub-interface automatically.

```
$ docker network create -d macvlan \
    --subnet=192.168.50.0/24 \
    --gateway=192.168.50.1 \
    -o parent=eth0.50 macvlan50
```

### Use an ipvlan instead of macvlan[](https://docs.docker.com/network/macvlan/#use-an-ipvlan-instead-of-macvlan)

In the above example, you are still using a L3 bridge. You can use `ipvlan` instead, and get an L2 bridge. Specify `-o ipvlan_mode=l2`.

```
$ docker network create -d ipvlan \
    --subnet=192.168.210.0/24 \
    --subnet=192.168.212.0/24 \
    --gateway=192.168.210.254 \
    --gateway=192.168.212.254 \
     -o ipvlan_mode=l2 -o parent=eth0 ipvlan210
```

## Use IPv6[](https://docs.docker.com/network/macvlan/#use-ipv6)

If you have [configured the Docker daemon to allow IPv6](https://docs.docker.com/config/daemon/ipv6/), you can use dual-stack IPv4/IPv6 `macvlan` networks.

```
$ docker network create -d macvlan \
    --subnet=192.168.216.0/24 --subnet=192.168.218.0/24 \
    --gateway=192.168.216.1 --gateway=192.168.218.1 \
    --subnet=2001:db8:abc8::/64 --gateway=2001:db8:abc8::10 \
     -o parent=eth0.218 \
     -o macvlan_mode=bridge macvlan216
```