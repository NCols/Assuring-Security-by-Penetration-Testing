# TARGET ENUMERATION

Enumerating target is a process that is used to find and collect information about ports, operating systems, and services available on the target machines.

## 1. INTRODUCING PORT SCANNING
----------------------------

In its simplest definition, port scanning can be defined as a method used to determine the state of the Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) ports on the target machines.


### Understanding the TCP/IP protocol

IP provides addressing, datagram routing, and other functions for connecting one machine to another, while TCP is responsible for managing connections and provides reliable data transport between processes on two machines. The IP is located in the network layer (layer 3) in the Open Systems Interconnection (OSI) model, whereas TCP is located in the transport layer (layer 4) of OSI.

	1) TCP SYN client -> server
	2) TCP SYN/ACK server -> client (ACK sent with client SYN ISN +1, SYN sent with another ISN)
	3) TCP ACK client -> server  (ACK sent with server ISN +1)

A TCP message is called a segment. A segment consists of a header and a data section.
The header is normally 20 bytes long without TCP options.

When performing a port scanning on the TCP port by using a SYN packet to the target machine, an attacker might face the following behaviors:

• The target machine responds with the SYN+ACK packet. If we receive this packet, we know that the port is open. This behavior is defined in the TCP specification (RFC 793), which states that the SYN packet must be responded with the SYN+ACK packet if the port is open without considering the SYN packet payload.
• The target machine sends back a packet with the RST and ACK bit set. This
means that the port is closed.
• The target machine sends an ICMP message such as ICMP Port Unreachable, which means that the port is not accessible to us most likely because it is blocked by the firewall.
• The target machine sends nothing back to us. It may indicate that there is no network service listening on that port or that the firewall is blocking our SYN packet silently.

During a port scanning activity to the UDP port on the target machine, an attacker
might face the following behaviors:

• The target machine responds with a UDP packet. If we receive this packet, we know that the port is open.
• The target machine sends an ICMP message such as ICMP Port Unreachable. It can be concluded that the port is closed. However, if the message sent is not an ICMP unreachable message, it means that the port is filtered by the firewall.
• The target machine sends nothing back to us. This may indicate one of the following situations:
	- The port is closed
	- The inbound UDP packet is blocked
	- The response is blocked


## 2. THE NETWORK SCANNER

### NMAP

Cf nmap cheat sheets.

Besides being used as a port scanner, Nmap has several other capabilities as follows:

	- Host discovery
	- Service/version detection
	- Operating system detection
	- Network traceroute
	- Nmap scripting engine

Let's have a look at the port states that can be identified:

• **Open**: This means that there is an application accepting a TCP connection, UDP datagram, or SCTP association.
• **Closed**: This means that although the port is accessible, there is no application listening on the port.
• **Filtered**: This means that Nmap can't determine whether the port is open or not because there is a packet-filtering device blocking the probe to reach the target.
• **Unfiltered**: This means that the port is accessible, but Nmap cannot determine whether it is open or closed.
• **Open|Filtered**: This means that Nmap is unable to determine whether a port is open or filtered. This happens when a scan to open ports doesn't give a response. It can be achieved by setting the firewall to drop packets.
• **Closed|Filtered**: This means Nmap is unable to determine whether a port is closed or filtered.

The biggest problem with the UDP scan is how to perform the scan quickly. A Linux kernel limits the sending of the ICMP Port Unreachable message to one message per second. Doing a UDP scanning of 65,536 ports to a machine will take more than 18 hours to complete.

To help mitigate this problem, there are several ways that can be used as follows:

	• Running the UDP scan in parallel
	• Scanning the most popular ports first
	• Scanning behind the firewall
	• Setting the --host-timeout option to skip slow hosts

These methods can help to decrease the time required for doing UDP port scans.

#### Nmap port specification:

	* -p port_range (1-1024)
	* -F (fast): scan only 100 common ports
	* -r: don't randomize, scan sequentially
	* --top-ports <1 or greater>: will scan the N highest ratio ports



#### Nmap output options:

	* interactive output: default setting
	* -oN: normal output, like interactive but doesn't include runtime info & warnings
	* -oX: XML output
	* -oG: grepable output (deprecated but still popular)
	* -oA to activate -oN, -oX and -oG

We can then convert the XML is HTML using xsltproc:

> xsltproc myscan.xml -o myscan.html

There are several libraries specifically developed to work with an Nmap output:

	• Perl: Nmap-Parser (http://search.cpan.org/dist/Nmap-Parser/)
	• Python: python-nmap (http://xael.org/norman/python/python-nmap/)
	• Ruby: Ruby Nmap (http://rubynmap.sourceforge.net/)
	• PowerShell: PowerShell script to parse nmap XML output (http://www.sans.org/windows-security/2009/06/11/powershell-script-toparse-nmap-xml-output)
	
#### Nmap timing options:

	- paranoid: 0 (every 5 minutes)
	- sneaky: 1 (every 15 seconds, no parallel transmission)
	- polite: 2 (every 0.4 seconds, no parallel transmission)
	- normal: 3 (multiple packets to multiple targets at same time, default mode)
	- agressive: 4 (scan given host for 5 minutes before moving to next target. Won't wait more than 1,25 seconds for response)
	- insane: 5 (scan given host for 75 seconds before moving to next target. Won't wait more than 0.3 seconds for response)
	
Then there's also:
	
	- service detection: -sV
	- OS detection: -O
	- disable ping: -Pn
	- aggressive scan: -A = -sV -O -sC (script scanning) --traceroute
	
	
Scanning IPv6 addresses:
	
> -6
	
> nmap -6 fe80::a00:27ff:fe43:1518
	
	
	
	
#### The Nmap scripting engine

Scripts categorized as follows:

- **auth**: The scripts in this category are used to find the authentication set on the target system such as using the brute force technique.
- **default**: These scripts are run by using the -sC or -A options. A script will be grouped in the default category if it satisfies the following requirements:
	• It must be fast
	• It needs to produce valuable and actionable information
	• Its output needs to be verbose and concise
	• It must be reliable
	• It should not be intrusive to the target system
	• It should divulge information to the third party

- **discovery**: These scripts are used to find the network.
- **doS**: The scripts in this category may cause Denial of Service (DoS) on the target system. Please use them carefully.
- **exploit**: These scripts will exploit security vulnerabilities on the target system. The penetration tester needs to have permission to run these scripts on the target system.
- **external**: These scripts may divulge information to third parties.
- **fuzzer**: These scripts are used to do fuzzing to the target system.
- **intrusive**: These scripts may crash the target system or use all of the target system resources.
- **malware**: These scripts will check for the existence of malware or backdoors on the target system.
- **safe**: These scripts are not supposed to cause a service crash, Denial of Service (DoS), or exploit target system.
- **version**: These scripts are used with the version detection option (-sV) to carry out advanced detection for the service on the target system.
- **vuln**: These scripts are used to check for security vulnerabilities on the target system.


There are several command-line arguments that can be used to call NSE as follows:

> -sC or --script=default: This performs scan using default scripts.

> --script \<filename\> | \<category\> | \<directories\>: This performs scan using the script defined in filename, categories, or directories.

> --script-args \<args\>: This provides script argument. An example of these arguments are username or password if you use the auth category.
	
There is a useful NSE script called Nmap NSE Vulscan (http://www.computec.ch/mruef/software/nmap_nse_vulscan-1.0.tar.gz) that can help you to map the version information you obtain from a target machine with the vulnerability database.
	
#### Nmap options for Firewall/IDS evasion
	
* -f (fragment packets): This purpose of this option is to make it harder to detect the packets. Packets will be split into 8 bytes or less after the IP header.
* --mtu: specify own packet size fragmentation (Maximum Transmission Unit - MTU - must be a multiple of eight)
* -D (decoy): some of packets sent from spoofed IP
* --source-port <portnumber> or –g (spoof source port): This option will be useful if the firewall is set up to allow all incoming traffic that comes from a specific port.
* --data-length: This option is used to change the default data length sent by Nmap in order to avoid being detected as Nmap scans
* --max-parallelism: This option is usually set to one in order to instruct Nmap to send no more than one probe at a time
* --scan-delay <time>: This option can be used to evade IDS/IPS that uses a threshold to detect port scanning activity
	
You may also experiment with other Nmap options for evasion as explained in the Nmap manual (http://nmap.org/book/man-bypass-firewalls-ids.html).
	

### UNICORNSCAN
	
Unicornscan is an information gathering and correlation engine tool. It is useful for introducing stimulus and measuring the response from a TCP/IP device.

Unicornscan has the following features:

	• Asynchronous stateless TCP port scanning
	• Asynchronous stateless TCP banner grabbing
	• Asynchronous UDP port scanning
	• Active and passive remote OS and application identification	

The main difference between Unicornscan and other similar tools is that it is a very fast and scalable port scanner.
	
In Unicornscan, you can define how many packets you want to send per second. The higher the packets per second (PPS) value, the faster the scan process; but this may cause an overload on the network, so be careful when using this capability. The default PPS is 300.	
	
	
	
	
	
	
	
### ZENMAP
	
Graphical nmap
	
	
### AMAP
		
Amap is a tool that can be used to check the application running on a specific port. Amap works by sending a trigger packet to the port and comparing the response with its database. It will print the application information if the application's response matches the database information.

In Kali Linux, the Amap trigger file is located in /etc/apmap/appdefs.trig, whereas the response file is available in /etc/amap/appdefs.resp.

For our exercise, we will analyze the application that runs on the target system's port 22. We will use the -b and -q options to get banner information without reporting the closed or unidentified ports as given in the following command:

> amap -bq 192.168.56.103 22

	Protocol on 192.168.56.103:22/tcp matches ssh - banner: SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1\n

	Protocol on 192.168.56.103:22/tcp matches ssh-openssh - banner: SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1\n
	


### SMB ENUMERATION

If you are testing a Windows environment, the easiest way to collect information about that environment is by using the Server Message Block (SMB) enumeration tool such as nbtscan.


#### NBTSCAN
	
The nbtscan tool can be used to scan the IP addresses for the NetBIOS name information. It will produce a report that contains the IP address, NetBIOS computer name, services available, logged in username, and MAC addresses of the corresponding machines.	

The tool generates a lot of traffic.

If you are connected to a 192.168.56.0 network and want to find the Windows hosts available in the network, you can use the following command:

> nbtscan 192.168.56.1-254

	Doing NBT name scan for addresses from 192.168.56.1-254
	
	IP address		NetBIOS Name	Server		User			MAC address
	------------------------------------------------------------------------------
	192.168.56.103	METASPLOITABLE	<server>	METASPLOITABLE	00:00:00:00:00:00
	
	
Now let's find the service provided by that machine by giving the following command:

> nbtscan -hv 192.168.56.103

	Doing NBT name scan for addresses from 192.168.56.103
	NetBIOS Name Table for Host 192.168.56.103:
	
	Incomplete packet, 281 bytes long.
	Name 			Service 	Type
	----------------------------------------
	METASPLOITABLE	Workstation Service
	METASPLOITABLE	Messenger Service
	METASPLOITABLE	File Server Service
	METASPLOITABLE	Workstation Service
	METASPLOITABLE	Messenger Service
	METASPLOITABLE	File Server Service
	WORKGROUP		Domain Name
	WORKGROUP		Browser Service Elections
	WORKGROUP		Domain Name
	WORKGROUP		Browser Service Elections
	
	Adapter address: 00:00:00:00:00:00
	----------------------------------------
	
		


### SNMP ENUMERATION

**Simple Network Monitoring Protocol**

Even though the information from a SNMP device may not look important, as pen-testers, we have seen misconfigured SNMP devices which allow us to read the configuration, get important information, and even have a privilege to modify the configuration.



#### ONTSIXTYONE
	
The onesixtyone tool can be used as a SNMP scanner to find whether the SNMP string exists on a device. The difference with respect to other SNMP scanners is that this tool sends all the SNMP requests as fast as it can (10 milliseconds apart). Then it waits for the responses and logs them. If the device is available, it will send responses containing the SNMP string.

> onesixtyone 192.168.56.103
	
	Scanning 1 hosts, 2 communities

	192.168.56.103 [public] Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
	192.168.56.103 [private] Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686	
	

If we want to scan more verbose:

> onesixtyone -d 192.168.56.103
		
	Debug level 1
	Target ip read from command line: 192.168.56.103
	2 communities: public private
	Waiting for 10 milliseconds between packets
	Scanning 1 hosts, 2 communities
	Trying community public
	192.168.56.103 [public] Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
	Trying community private
	192.168.56.103 [private] Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
	All packets sent, waiting for responses.
	done.	
	


#### SNMPCHECK

Able to give quite detailed information.

> snmpcheck -t 192.168.56.103

### VPN ENUMERATION

Based on the method used, VPN can be divided into at least three groups:

* **IPsec-based VPN**: This type is a popular VPN solution for connecting the branch office to the head office's LAN. The branch office will install an IPsec VPN client on the network gateway, while the head office will install an IPsec VPN server on its network gateway. It is not a popular method to connect a user to the head office's LAN due to the complexity of configuring the method. The user that uses this method is called a road warrior.

* **OpenVPN**: This type is a very popular VPN solution for road warriors. In OpenVPN, a user needs to install an OpenVPN client before being able to connect to the VPN server. The advantage of this mode is that it is very easy to set up and doesn't need an administrator-level privilege to run.

* **SSL-based VPN**: In this category, the user doesn't need a dedicated VPN client but can use a web browser to connect to the VPN server as long as the web browser supports an SSL connection.

### IKE-SCAN
	
The ike-scan tool is a security tool that can be used to discover, fingerprint, and test the IPsec VPN systems. IPsec is the most commonly used technology for LAN-to-LAN and remote access VPN solutions.

IPsec uses three major protocols as follows:

* **Authentication Headers (AH)**: This provides data integrity

* **Encapsulating Security Payloads (ESP)**: This provides data integrity and confidentiality
		
* **Internet Key Exchange (IKE)**: This provides support for the negotiation of parameters between endpoints; it establishes, maintains, and terminates the Security Association (SA).

IKE establishes security association through the following phases:
		
* **IKE phase 1**: This sets up a secure channel between two IPsec endpoints by the negotiation of parameters, such as the encryption algorithm, integrity algorithm, authentication type, key distribution mechanism, and lifetime. To establish the bidirectional security association, IKE phase 1 can either use the main mode or aggressive mode. The main mode negotiates SA through three pairs of messages, while the aggressive mode provides faster operations through the exchange of three messages.

* **IKE phase 2**: This is used for data protection.

* **IKE phase 1.5 or the extended authentication phase**: This is an optional phase and is commonly used in the remote access VPN solutions.
		
The ike-scan tool works by sending IKE phase 1 packets to the VPN servers and displaying any responses it receives.

The following are several features of ike-scan:

• Ability to **send** the IKE packets to any number of destination hosts
• Ability to **construct** the outgoing IKE packets in a flexible way
• Ability to **decode** and display any response packets
• Ability to **crack** the aggressive mode pre-shared keys with the help of the psk-crack tool

In short, the ike-scan tool is capable of two things:

• **Discovery**: Finding hosts running the IKE by displaying the hosts that respond to the IKE request.
• **Fingerprint**: Identifying the IKE implementation used by the IPsec VPN server. Usually, this information contains the VPN vendor and the model of the VPN server. This is useful for later use in the vulnerability analysis process.
	
The reason why you need a tool like ike-scan is that in general, port scanner will not be able to find an IPsec VPN server because these servers doesn't listen on any TCP ports.

As our exercise, we are going to discover, fingerprint, and test an IPsec VPN server using the following command:

> ike-scan -M -A –Pike-hashkey 192.168.0.10

	* -M: This splits the payload decoded across multiple lines to make the output easier to read
	* -A: This uses the IKE aggressive mode
	* -P: This saves the aggressive mode pre-shared key to this file

The pre-shared key is saved in the ike-hashkey file.

The next step is to crack the hash to get the password to connect to the VPN server.
	
For this purpose, we can use the psk-crack tool as follows:

> psk-crack –d rockyou.txt ike-hashkey

Here, -d is the wordlist file.

The next task is to fingerprint the VPN server.

> ike-scan -M --trans=5,2,1,2 --showbackoff 192.168.0.10
	
	
	