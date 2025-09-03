net-tools muss separat installiert werden  
Nach der Instalation kann nicht ab sofort in bash verwendet werden  
-- Neue location und command fürs ausführen: sudo /sbin/ifconfig  

Wenn man ifconfig wie früher verwendet möchte
```
echo 'export PATH=$PATH:/sbin:/usr/sbin' >> ~/.bashrc
source ~/.bashrc
```

Alternativen
| Old `net-tools` command          | New `iproute2` equivalent                          | Description                                  |
|----------------------------------|---------------------------------------------------|----------------------------------------------|
| `ifconfig`                       | `ip addr show`                                    | Show all IP addresses and interfaces         |
|                                  | `ip -brief addr`                                  | Show a brief list of interfaces + addresses  |
|                                  | `ip link show`                                    | Show link-layer (MAC) information            |
| `ifconfig eth0 up`               | `ip link set eth0 up`                             | Bring interface up                           |
| `ifconfig eth0 down`             | `ip link set eth0 down`                           | Bring interface down                         |
| `ifconfig eth0 192.168.1.10`     | `ip addr add 192.168.1.10/24 dev eth0`            | Assign an IP to an interface                 |
| `ifconfig eth0 netmask 255.255.255.0`| `ip addr add 192.168.1.10/24 dev eth0`       | Assign IP with netmask (CIDR format)         |
| `ifconfig eth0 mtu 1500`         | `ip link set dev eth0 mtu 1500`                   | Set MTU                                      |
| `route`                          | `ip route show`                                   | Show routing table                           |
| `route add default gw 192.168.1.1` | `ip route add default via 192.168.1.1`          | Add default gateway                          |
| `route add -net 10.0.0.0/24 gw 192.168.1.1` | `ip route add 10.0.0.0/24 via 192.168.1.1` | Add a network route                          |
| `netstat -rn`                    | `ip route`                                       | Show kernel routing table                    |
| `netstat -i`                     | `ip -s link`                                     | Show network interfaces + statistics         |
| `arp -n`                         | `ip neigh show`                                  | Show ARP table                               |
| `arp -s 192.168.1.50 00:11:22:33:44:55` | `ip neigh add 192.168.1.50 lladdr 00:11:22:33:44:55 dev eth0` | Add static ARP entry |
| `netstat -tuln`                  | `ss -tuln`                                       | Show listening TCP/UDP sockets               |
| `netstat -plant`                 | `ss -plant`                                      | Show listening + established sockets + PIDs  |
