/ Local RHEL Network Lab


// Network Interface  

  Interface: ens160 (VM)  
  IPv4 address: 10.233.58.65  
  Prefix: /24

/// Knowledge Acquired

IP adderss Identifies a System on a Network.
Network Interface is the connection the system is using to communicate.

<img width="1912" height="1078" alt="Screenshot 2026-08-25 172119" src="https://github.com/user-attachments/assets/0ee83308-4d9c-47a4-9a67-71e5b2944208" />

--

// Default Gateway

  Gateway: 10.233.58.43
  Command: ping -c 4 (IP)
  Result: 4 packets received 4 sent 0 packets loss

/// Knowledge Acquired

Gateway is the door my system send packets to if it wants to connect to the external network.

<img width="1920" height="1080" alt="Screenshot 2026-08-25 173906" src="https://github.com/user-attachments/assets/aa4bd473-ad6b-48a9-a510-771b441e4db2" />

--

// Internet Connectivity Test

  Target IP: 8.8.8.8
  Result: Internet connection is working

/// Interpretation

If the IP responds, basic network connectivity is working.

<img width="1920" height="1080" alt="Screenshot 2026-08-25 175148" src="https://github.com/user-attachments/assets/e851f89a-f0e9-4edc-94c2-90d99345d4a8" />

--

// DNS Test

  Domain: google.com
  DNS Server: 2409:40c4:34f:a06::4e
  Resolved IP: 192.178.173.139
  Result: Domain name got resolved to its IP address

/// What I learned

DNS converts domain names into IP addresses.
If direct IP works but domain names does not then, DNS may be the issue.

<img width="1920" height="1080" alt="Screenshot 2026-08-25 182854" src="https://github.com/user-attachments/assets/44d0b96f-5da4-4ad0-b1c5-8570962a4b33" />


[Note] : RHEL uses IPv6 addresses, I configured it to show IPv4 for the projects, so IP address are different after this section.



// ARP \ Neighbor Table

  Gateway IP: 192.168.2.1 
  Gateway MAC: 50:2b:73:00:8e:d0 
  State: REACHABLE

/// Knowledge Acquired 

APR maps an IPv4 address to the MAC address on a network.

<img width="1920" height="1080" alt="Screenshot 2026-08-25 231328" src="https://github.com/user-attachments/assets/e0b82556-d614-4821-9eac-0b0ea695b79b" />

--

// ICMP Capture

  Command: ping -c wikipedia.org
  Wireshark Filter: icmp

/// Observation

ICMP Echo Request
ICMP Echo Reply

<img width="1920" height="1080" alt="Screenshot 2026-08-25 233411" src="https://github.com/user-attachments/assets/6ecaff88-3600-4490-970f-12cc7cbf8e05" />

--

// DNS Packet Analysis

  Client IP: 192.168.2.110
  DNS Server: 192.168.2.1
  Domain Queried: wikipedia.org
  Returned IP: 103.102.166.224
  Protocols: eth:ethertype:ip:udp:dns

<img width="1920" height="1080" alt="Screenshot 2026-08-26 000755" src="https://github.com/user-attachments/assets/c400b559-9beb-491f-b3fb-27bbcbf33fe1" />

--

//  TCP Connection Analysis

  Source IP: 192.168.2.110
  Destination IP: 103.102.166.224
  Source Port: 58692
  Destination Port: 443

  Handshake Observation:
  SYN
  SYN-ACK
  ACK

<img width="1920" height="1080" alt="Screenshot 2026-08-26 005409" src="https://github.com/user-attachments/assets/709803a1-3cfc-4a5d-b470-02f35341c020" />

--

// Ports
  
  Port: 22
  TCP/UDP: tcp
  Listening Address: 0.0.0.22
  Service: SSH

<img width="1920" height="1080" alt="Screenshot 2026-08-26 011127" src="https://github.com/user-attachments/assets/7746c4f2-a00e-401a-945b-89a11616c4bb" />

--

// HTTPs \ TLS Observation

  Target: wikipedia.org
  Port: 443
  TLS Traffic Observed: TLS packets were captured between RHEL system and the web server, I observed the TLS Handshake including 
   Client Hello with the supported Cipher Suites and Server Hello in Wireshark and encrypted application traffic.

/// Learning

HTTPS uses TLS to protect web traffic, Port 443 is defalut for HTTPS and Wireshark can capture the HTTPS traffic but it is not readable like the HTTP traffic.

<img width="1920" height="1080" alt="Screenshot 2026-08-26 231151" src="https://github.com/user-attachments/assets/65367b36-2238-4c15-a03e-061a819ccde9" />

