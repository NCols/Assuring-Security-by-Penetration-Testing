
# TARGET DISCOVERY

The purpose of this process is as follows:

	- To find out which machine in the target network is available.
	- To find the underlying operating system used by the target machine.
	

## 1. IDENTIFYING THE TARGET MACHINE

#### PING
	
Check whether a particular host is available.

Works by sending ICMP echo requests to target. If host available and firewall not blocking ICMP packets, the target host then responds with an echo reply packet.
There are more ICMP control messages available: https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Control_messages
	
	
#### ARPING
	
The arping tool is used to ping a host in the Local Area Network (LAN) using the Address Resolution Protocol (ARP) request. You can use arping to ping a target machine using its IP, host, or Media Access Control (MAC) address.

Arping operates on the OSI 2 layer.
	
>  arping 192.168.56.102 -c 1
	
Process:

Our network card (MAC address: 08:00:27:1c:51:22) sends an ARP request to a broadcast MAC address (ff:ff:ff:ff:ff:ff), looking for the IP address 192.168.56.102. If the IP address 192.168.56.102 exists, it will send an ARP reply mentioning its MAC address (08:00:27:43:15:18), as can be seen from packet number 2.

However, if the IP address is not available, there will be no ARP replies, informing the MAC address of the 192.168.56.103 IP address.

Another common use of arping is to detect duplicate IP addresses in a local network.
	
>  arping -d -i eth0 192.168.56.102 -c 2

>  echo $?

> 1
	
	
#### FPING
	
Fping can be used to send a ping (ICMP echo) request to several hosts at once.

If we want to know which host among these 3 is alive, we can do:

>  fping 192.168.1.1 192.168.1.100 192.168.1.107

	192.168.1.1 is alive
	192.168.1.107 is alive
	ICMP Host Unreachable from 192.168.1.112 for ICMP Echo sent to 192.168.1.100
	ICMP Host Unreachable from 192.168.1.112 for ICMP Echo sent to 192.168.1.100
	ICMP Host Unreachable from 192.168.1.112 for ICMP Echo sent to 192.168.1.100
	192.168.1.100 is unreachable

We can also check for a range of IPs with:

>  fping -g 192.168.56.0/24

To change the number of ping attempts per target, we can use the retry limit -r:

>  fping -r 1 -g 192.168.1.1 192.168.1.10

We can get cumulative statistics with the -s flag:

>  fping -s www.yahoo.com www.google.com www.msn.com
	
	
#### HPING3
	
The hping3 tool is a command-line network packet generator and analyzer tool. The capability to create custom network packets allows hping3 to be used for TCP/IP and security testing, such as port scanning, firewall rule testing, and network performance testing.

Other uses:

• Test firewall rules
• Test Intrusion Detection System (IDS)
• Exploit known vulnerabilities in the TCP/IP stack

We can use different protocols:

	No.	Short option	Long option	Description
	1 	-0 				--raw-ip 	This sends raw IP packets
	2 	-1 				--icmp 		This sends ICMP packets
	3 	-2 				--udp 		This sends UDP packets
	4 	-8 				--scan 		This indicates the scan mode
	5 	-9 				--listen 	This indicates the listen mode
	
And when using TCP, we can set different flags:

	No.	Option	Flag name
	1 	-S 		syn
	2 	-A 		ack
	3 	-R 		rst
	4 	-F 		fin
	5 	-P 		psh
	6 	-U 		urg
	7 	-X 		xmas: flags fin, urg, psh set
	8 	-Y 		ymas
	
In interactive mode, we can use TCL commands. More info here:

	- http://www.invece.org/tclwise/
	- https://wiki.tcl-lang.org/
	- http://wiki.hping.org.
	
	
#### NPING
	
The nping tool is a tool that allows users to generate network packets of a wide range of protocols (TCP, UDP, ICMP, and ARP). You can also customize the fields in the protocol headers, such as the source and destination port for TCP and UDP.

nping can also be used for network stress testing, Address Resolution Protocol (ARP) poisoning, and the denial of service attacks.

The following are several probe modes supported by nping:

	No. Mode 			Description
	1 	--tcpconnect	This is an unprivileged TCP connect
	2 	--tcp 			This is a TCP mode
	3 	--udp 			This is a UDP mode
	4 	--icmp 			This is an ICMP mode (default)
	5 	--arp 			This is an ARP/RARP mode
	6 	--tr 			This is a traceroute mode (it can only be used in the TCP/UDP/ICMP mode)
	
>  nping -c 1 192.168.56.100-102
	
	
	
#### ALIVE6
	
If you want to discover which machines are alive in an IPv6 environment, you can't just ask the tool to scan the whole network. This is because the address space is very huge. You may find that the machines have a 64-bit network range. Trying to discover the machines sequentially in this network will require at least 264 packets. Of course, this is not a feasible task in the real world.

Fortunately, there is a protocol called ICMPv6 Neighbor Discovery. This protocol allows an IPv6 host to discover the link-local and autoconfigured addresses of all other IPv6 systems on the local network. In short, you can use this protocol to find a live host on the local network subnet.

>  alive6 -p eth0
	
	
	
#### DETECT-NEW-IP6
	
This tool can be used if you want to detect the new IPv6 address joining a local network. This tool is part of the THC-IPv6 Attack Toolkit.

The following command is an example of running this tool:

>  passive_discovery6 eth0
	
	
#### NBTSCAN
	
The nbtscan tool will produce a report that contains the IP address, NetBIOS computer name, services available, logged in username, and MAC address of the corresponding machines.
The NetBIOS name is useful if you want to access the service provided by the machine using the NetBIOS protocol that is connected to an open share.
Be careful as using this tool will generate a lot of traffic and it may be logged by the target machines.

Here's the list of NetBIOS services linked with the name of the computer:
	https://www.itprotoday.com/compute-engines/what-are-netbios-suffixes-16th-character
	
As an example, I want to find out the NetBIOS name of the computers located in my network (192.168.1.0/24). The following is the command to be used:

>  nbtscan 192.168.1.1-254
		
	Doing NBT name scan for addresses from 192.168.1.1-254
	IP address NetBIOS Name Server User MAC address
	-------------------------------------------------------------------------
	-----
	192.168.1.81 PC-001 <server> <unknown>
	00:25:9c:9f:b0:96
	192.168.1.90 PC-003 <server> <unknown>
	00:00:00:00:00:00
	...
	
Let's find the service provided by these machines by giving the following command:

>  nbtscan -hv 192.168.1.1-254

(-hv will print the output in human readable format and in verbose mode)
	


## 2. OS FINGERPRINTING

There's active and passive fingerprinting.

	
#### P0F
	
Passive fingerprinting.

It can be used to identify an operating system on the following machines:
	• Machines that connect to your box (SYN mode; this is the default mode)
	• Machines you connect to (SYN+ACK mode)
	• Machines you cannot connect to (RST+ mode)
	• Machines whose communications you can observe
	
The p0f tool works by analyzing the TCP packets sent during the network activities. Then, it gathers the statistics of special packets that are not standardized by default by any corporations. An example is that the Linux kernel uses a 64-byte ping datagram, whereas the Windows operating system uses a 32-byte ping datagram; or the Time To Live (TTL ) value.

Let's use p0f to identify the operating system used in a remote machine we are connecting to. Just type the following command in your console:

>  p0f –f /etc/p0f/p0f.fp -o p0f.log

	--- p0f 3.06b by Michal Zalewski <lcamtuf@coredump.cx> ---
	[+] Closed 1 file descriptor.
	[+] Loaded 314 signatures from '/etc/p0f/p0f.fp'.
	[+] Intercepting traffic on default interface 'eth0'.
	[+] Default packet filtering configured [+VLAN].
	[+] Log file 'p0f.log' opened for writing.
	[+] Entered main event loop.
	
This will read the fingerprint database from the /etc/p0f/p0f.fp file and save the log information to the p0f.log file.

Next, you need to generate network activities involving a TCP connection, such as browsing to the remote machine or letting the remote machine to connect to your machine.
	
If p0f has successfully fingerprinted the operating system, you will see information of the remote machine's operating system in the console and in the logfile (p0f.log).

Following is the information displayed to the console:

	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (syn) ]-
	|
	| client = 192.168.56.101/42819
	| os = Linux 3.x
	| dist = 0
	| params = none
	| raw_sig = 4:64+0:0:1460:mss*10,7:mss,sok,ts,nop,ws:df,id+:0
	|
	`----
	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (mtu) ]-
	|
	| client = 192.168.56.101/42819
	| link = Ethernet or modem
	| raw_mtu = 1500
	|
	`----
	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (syn+ack) ]-
	|
	| server = 192.168.56.102/80
	| os = Linux 2.6.x
	| dist = 0
	| params = none
	| raw_sig = 4:64+0:0:1460:mss*4,5:mss,sok,ts,nop,ws:df:0
	|
	`----
	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (mtu) ]-
	|
	| server = 192.168.56.102/80
	| link = Ethernet or modem
	| raw_mtu = 1500
	|
	`----
	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (http request) ]-
	|
	| client = 192.168.56.101/42819
	| app = Firefox 10.x or newer
	| lang = English
	| params = none
	| raw_sig = 1:Host,User-Agent,Accept=[text/html,application/
	xhtml+xml,application/xml;q=0.9,*/*;q=0.8],Accept-Language=[en-
	US,en;q=0.5],Accept-Encoding=[gzip, deflate],Connection=[keepalive]:
	Accept-Charset,Keep-Alive:Mozilla/5.0 (X11; Linux x86_64; rv:18.0)
	Gecko/20100101 Firefox/18.0 Iceweasel/18.0.1
	|
	`----
	.-[ 192.168.56.101/42819 -> 192.168.56.102/80 (http response) ]-
	|
	| server = 192.168.56.102/80
	| app = Apache 2.x
	| lang = none
	| params = none
	| raw_sig = 1:Date,Server,X-Powered-By=[PHP/5.2.4-2ubuntu5.10],?Content-
	Length,Keep-Alive=[timeout=15, max=100],Connection=[Keep-Alive],Content-
	Type:Accept-Ranges:Apache/2.2.8 (Ubuntu) DAV/2
	|
	`----


#### NMAP
	
> -O option

	