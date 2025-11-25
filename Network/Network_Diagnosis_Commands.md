# Network Diagnosis Commands

| Command | Parameters | Description | Example | OS |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| `ping [ip/url]` | -c [n]: sends [n] ICMP echo requests |  It sends an ICMP echo request to a host computer over an IP network. If the host is accessible, it sends an ICMP echo response | `ping -c 3 8.8.8.8` | Windows/Linux |
| `tracert/traceroute [ip/url]` | - |  It works with ICMP routers and trace the route between an origin and a destination. Reports the IP addresses of all routers involved. | `tracert example.com` | Windows(1)/Linux(2) |
| `pathping [ip/url]` | -h [n]: stop after [n] hops <br >-w [n]: will attempt to reach a new host after [n] milliseconds if it was not available on the first attempt. |  It combines tracert and ping functionality. Used to find routers that may be causing problems on a network | `pathping wikipedia.org -h 200` | Windows |
| `ipconfig/ifconfig` | /all: Shows extended information (Windows only) | The command displays the IP address, the subnet mask and the default gateway linked to each adapter. | - | Windows/Linux |
| `nslookup` | - | Network diagnostic tool that helps determine DNS problems. | `nslookup www.google.com` | Windows/Linux |
| `netstat` | - | Shows network connections for TCP, routing tables, and network protocols used | - | Windows/Linux |
| `route` | - | Used to view and make changes to routing tables. | - | Windows/Linux |

Almost all Linux commands are not installed per default. Use `$sudo apt-get install net-tools`