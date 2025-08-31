| Filter Type                              | Expression                                                                 |
| ---------------------------------------- | -------------------------------------------------------------------------- |
| Filter by IP                             | `ip.addr == 10.10.50.1`                                                     |
| Filter by Destination IP                 | `ip.dest == 10.10.50.1`                                                     |
| Filter by Source IP                      | `ip.src == 10.10.50.1`                                                      |
| Filter by IP range                       | `ip.addr >= 10.10.50.1 and ip.addr <= 10.10.50.100`                         |
| Filter by Multiple IPs                   | `ip.addr == 10.10.50.1 or ip.addr == 10.10.50.100`                          |
| Filter out/Exclude IP address            | `!(ip.addr == 10.10.50.1)`                                                  |
| Filter IP subnet                         | `ip.addr == 10.10.50.1/24`                                                  |
| Filter by multiple specified IP subnets  | `ip.addr == 10.10.50.1/24 and ip.addr == 10.10.51.1/24`                     |
| Filter by Protocol                       | `dns`<br>`http`<br>`ftp`<br>`ssh`<br>`arp`<br>`telnet`<br>`icmp`            |
| Filter by port (TCP)                     | `tcp.port == 25`                                                            |
| Filter by destination port (TCP)         | `tcp.dstport == 23`                                                         |
| Filter by IP address and port            | `ip.addr == 10.10.50.1 and tcp.port == 25`                                  |
| Filter by URL                            | `http.host == "host name"`                                                  |