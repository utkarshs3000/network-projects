/ Local RHEL Network Lab

// Network Interface

  Interface: ens160 (VM)
  IPv4 address: 10.233.58.65
  Prefix: /24

/// Knowledge Acquired

IP adderss Identifies a System on a Network.
Network Interface is the connection the system is using to communicate.


// Default Gateway

  Gateway: 10.233.58.43
  Command: ping -c 4 (IP)
  Result: 4 packets received 4 sent 0 packets loss

/// Knowledge Acquired

Gateway is the door my system send packets to if it wants to connect to the external network.


// Internet Connectivity Test

  Target IP: 8.8.8.8
  Result: Internet connection is working

/// Interpretation

If the IP responds, basic network connectivity is working.


// DNS Test

  Domain: google.com
  DNS Server: 2409:40c4:34f:a06::4e
  Resolved IP: 192.178.173.139
  Result: Domain name got resolved to its IP address

/// What I learned

DNS converts domain names into IP addresses.
If direct IP works but domain names does not then, DNS may be the issue.

[Note] : RHEL uses IPv6 addresses, I configured it to show IPv4 for the projects, so IP address are different after this section.

// ARP \ Neighbor Table

  Gateway IP: 192.168.2.1 
  Gateway MAC: 50:2b:73:00:8e:d0 
  State: REACHABLE

/// Knowledge Acquired 

APR maps an IPv4 address to the MAC address on a network.


// ICMP Capture

  Command: ping -c wikipedia.org
  Wireshark Filter: icmp

/// Observation

ICMP Echo Request
ICMP Echo Reply


// DNS Packet Analysis

  Client IP: 192.168.2.110
  DNS Server: 192.168.2.1
  Domain Queried: wikipedia.org
  Returned IP: 103.102.166.224
  Protocols: eth:ethertype:ip:udp:dns


//  TCP Connection Analysis

  Source IP: 192.168.2.110
  Destination IP: 103.102.166.224
  Source Port: 58692
  Destination Port: 443

  Handshake Observation:
  SYN
  SYN-ACK
  ACK

// Ports
  
  Port: 22
  TCP/UDP: tcp
  Listening Address: 0.0.0.22
  Service: SSH


// HTTPs \ TLS Observation

  Target: wikipedia.org
  Port: 443
  TLS Traffic Observed: TLS packets were captured between RHEL system and the web server, I observed the TLS Handshake including 
   Client Hello with the supported Cipher Suites and Server Hello in Wireshark and encrypted application traffic.

/// Learning

HTTPS uses TLS to protect web traffic, Port 443 is defalut for HTTPS and Wireshark can capture the HTTPS traffic but it is not readable like the HTTP traffic.


[sate@localhost network-projects]$ 
[sate@localhost network-projects]$ cat network-basics.md 
/ Local RHEL Network Lab

// Network Interface

  Interface: ens160 (VM)
  IPv4 address: 10.233.58.65
  Prefix: /24

/// Knowledge Acquired

IP adderss Identifies a System on a Network.
Network Interface is the connection the system is using to communicate.


// Default Gateway

  Gateway: 10.233.58.43
  Command: ping -c 4 (IP)
  Result: 4 packets received 4 sent 0 packets loss

/// Knowledge Acquired

Gateway is the door my system send packets to if it wants to connect to the external network.


// Internet Connectivity Test

  Target IP: 8.8.8.8
  Result: Internet connection is working

/// Interpretation

If the IP responds, basic network connectivity is working.


// DNS Test

  Domain: google.com
  DNS Server: 2409:40c4:34f:a06::4e
  Resolved IP: 192.178.173.139
  Result: Domain name got resolved to its IP address

/// What I learned

DNS converts domain names into IP addresses.
If direct IP works but domain names does not then, DNS may be the issue.

[Note] : RHEL uses IPv6 addresses, I configured it to show IPv4 for the projects, so IP address are different after this section.

// ARP \ Neighbor Table

  Gateway IP: 192.168.2.1 
  Gateway MAC: 50:2b:73:00:8e:d0 
  State: REACHABLE

/// Knowledge Acquired 

APR maps an IPv4 address to the MAC address on a network.


// ICMP Capture

  Command: ping -c wikipedia.org
  Wireshark Filter: icmp

/// Observation

ICMP Echo Request
ICMP Echo Reply


// DNS Packet Analysis

  Client IP: 192.168.2.110
  DNS Server: 192.168.2.1
  Domain Queried: wikipedia.org
  Returned IP: 103.102.166.224
  Protocols: eth:ethertype:ip:udp:dns


//  TCP Connection Analysis

  Source IP: 192.168.2.110
  Destination IP: 103.102.166.224
  Source Port: 58692
  Destination Port: 443

  Handshake Observation:
  SYN
  SYN-ACK
  ACK

// Ports
  
  Port: 22
  TCP/UDP: tcp
  Listening Address: 0.0.0.22
  Service: SSH


// HTTPs \ TLS Observation

  Target: wikipedia.org
  Port: 443
  TLS Traffic Observed: TLS packets were captured between RHEL system and the web server, I observed the TLS Handshake including 
   Client Hello with the supported Cipher Suites and Server Hello in Wireshark and encrypted application traffic.

/// Learning

HTTPS uses TLS to protect web traffic, Port 443 is defalut for HTTPS and Wireshark can capture the HTTPS traffic but it is not readable like the HTTP traffic.

