### Top 20 (most commonly open) TCP ports
1.  Port 80 (HTTP)—If you don't even know this service, you're reading the wrong book. This accounted for more than 14% of the open ports we discovered.
2.  Port 23 (Telnet)—Telnet lives on (particularly as an administration port on devices such as routers and smart switches) even though it is insecure (unencrypted).
3.  Port 443 (HTTPS)—SSL-encrypted web servers use this port by default.
4.  Port 21 (FTP)—FTP, like Telnet, is another insecure protocol which should die. Even with anonymous FTP (avoiding the authentication sniffing worry), data transfer is still subject to tampering.
5.  Port 22 (SSH)—Secure Shell, an encrypted replacement for Telnet (and, in some cases, FTP).
6.  Port 25 (SMTP)—Simple Mail Transfer Protocol (also insecure).
7.  Port 3389 (ms-term-server)—Microsoft Terminal Services administration port.
8.  Port 110 (POP3)—Post Office Protocol version 3 for email retrieval (insecure).
9.  Port 445 (Microsoft-DS)—For SMB communication over IP with MS Windows services (such as file/printer sharing).
10.  Port 139 (NetBIOS-SSN)—NetBIOS Session Service for communication with MS Windows services (such as file/printer sharing). This has been supported on Windows machines longer than 445 has.
11.  Port 143 (IMAP)—Internet Message Access Protocol version 2. An insecure email retrieval protocol.
12.  Port 53 (Domain)—Domain Name System (DNS), an insecure system for conversion between host/domain names and IP addresses.
13.  Port 135 (MSRPC)—Another common port for MS Windows services.
14.  Port 3306 (MySQL)—For communication with MySQL databases.
15.  Port 8080 (HTTP-Proxy)—Commonly used for HTTP proxies or as an alternate port for normal web servers (e.g. when another server is already listening on port 80, or when run by unprivileged UNIX users who can only bind to high ports).
16.  Port 1723 (PPTP)—Point-to-point tunneling protocol (a method of implementing VPNs which is often required for broadband connections to ISPs).
17.  Port 111 (RPCBind)—Maps SunRPC program numbers to their current TCP or UDP port numbers.
18.  Port 995 (POP3S)—POP3 with SSL added for security.
19.  Port 993 (IMAPS)—IMAPv2 with SSL added for security.
20.  Port 5900 (VNC)—A graphical desktop sharing system (insecure).


### Top 20 (most commonly open) UDP ports
1.  Port 631 (IPP)—Internet Printing Protocol.
2.  Port 161 (SNMP)—Simple Network Management Protocol.
3.  Port 137 (NETBIOS-NS)—One of many UDP ports for Windows services such as file and printer sharing.
4.  Port 123 (NTP)—Network Time Protocol.
5.  Port 138 (NETBIOS-DGM)—Another Windows service.
6.  Port 1434 (MS-SQL-DS)—Microsoft SQL Server.
7.  Port 445 (Microsoft-DS)—Another Windows Services port.
8.  Port 135 (MSRPC)—Yet Another Windows Services port.
9.  Port 67 (DHCPS)—Dynamic Host Configuration Protocol Server (gives out IP addresses to clients when they join the network).
10.  Port 53 (Domain)—Domain Name System (DNS) server.
11.  Port 139 (NETBIOS-SSN)—Another Windows Services port.
12.  Port 500 (ISAKMP)—The Internet Security Association and Key Management Protocol is used to set up IPsec VPNs.
13.  Port 68 (DHCPC)—DHCP client port.
14.  Port 520 (Route)—Routing Information Protocol (RIP).
15.  Port 1900 (UPNP)—Microsoft Simple Service Discovery Protocol, which enables discovery of Universal plug-and-play devices.
16.  Port 4500 (nat-t-ike)—For negotiating Network Address Translation traversal while initiating IPsec connections (during Internet Key Exchange).
17.  Port 514 (Syslog)—The standard UNIX log daemon.
18.  Port 49152 (Varies)—The first of the IANA-specified dynamic/private ports. No official ports may be registered from here up until the end of the port range (65536). Some systems use this range for their ephemeral ports, so services which bind a port without requesting a specific number are often allocated 49152 if they are the first program to do so.
19.  Port 162 (SNMPTrap)—Simple Network Management Protocol trap port (An SNMP agent typically uses 161 while an SNMP manager typically uses 162).
20.  Port 69 (TFTP)—Trivial File Transfer Protocol.