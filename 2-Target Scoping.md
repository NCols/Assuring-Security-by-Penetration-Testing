# TARGET SCOPING

Target Scoping is defined as an empirical process to gather target assessment requirements and characterize each of its parameters in order to generate a test plan, its limitations, business objectives, and time schedule.



## 1. THE SCOPING PROCESS

• **Gathering client requirements**: This deals with accumulating information about the target environment through verbal or written communication.

	- Can be drawn in the form of a questionnaire to devise all the information about target infrastructure from a client.
	- It is critical to identify all internal and external stakeholders at an early stage of a project and analyze their levels of interest, expectations, importance, and influence.
	- A strategy can then be developed to approach each stakeholder with their requirements and involvement in the penetration testing project.
	- The basic purpose of gathering client requirements is to open a true and authentic channel by which the pentester can obtain any information that may be necessary for the testing process.


• **Preparing the test plan**: This depends on different sets of variables. These variables may include shaping the actual requirements into a structured testing process, legal agreements, cost analysis, and resource allocation.

	- The key variables involved in preparing a test plan are structured testing process, resource allocation, cost analysis, non-disclosure agreement, penetration testing contract, and rules of engagement.

		• Structured testing process: Sometimes, this practice is known as test process validation. After analyzing the details provided by your customer, it may be important to restructure your testing methodology. It is a repetitive task that has to be revisited whenever there is a change in client requirements.
		• Resource allocation: Determining the expertise knowledge required to achieve the completeness of a test is one of the substantial areas.
		• Cost analysis
		• Non-disclosure Agreement (NDA)
		• Penetration testing contract: will address the technical and business matters between the client and penetration tester. The basic information in such contracts focuses on what testing services are being offered, their main objectives, how they will be conducted, payment declaration, and maintaining the confidentiality of the whole project.
		• Rules of engagement (ROE): You should never cross the boundaries set within the pre-agreed upon ROE. The process of penetration testing requires a clear understanding of the assessment's demands, support provided by the client, and type of potential impact or effect each assessment technique may have. Moreover, the tools used in the penetration testing processes should clearly state their purpose so that the tester can use them accordingly.

	- The test plan checklist:

			• Are all the requirements promised during the RFP being met?
			• Is the test scope defined clearly?
			• Have all the testing entities been identified?
			• Have all the non-testing entities been separately listed?
			• Is there any specific testing process that will be followed?
			• Is the testing process documented correctly?
			• Will the deliverables be produced upon the completion of a test process?
			• Has the entire target environment been researched and documented before?
			• Have all the roles and responsibilities been assigned for the testing activities?
			• Is there any third-party contractor to accomplish technology-specific assessment?
			• Have any steps been taken to bring the project to a graceful closure?
			• Has the disaster recovery plan been identified?
			• Has the cost of the test project been finalized?
			• Have the people who will approve the test plan been identified?
			• Have the people who will accept the test results been identified?

• **Profiling test boundaries**: This determines the limitations associated with the penetration testing assignment. These can be a limitation of technology, knowledge, or a formal restriction on the client's IT environment. Each limitation imposed may cause a serious interruption to the testing process and can be resolved using alternative methods. However, note that certain restrictions cannot be modified as they are administered by the client to control the process of penetration testing.

	- Technology limitations: This type of limitation occurs when the scope of a project is properly defined but the presence of a new technology in the network infrastructure does not let the auditor test it.
	- Knowledge limitations: For example, a dedicated database penetration tester would not be able to assess the physical security of a network infrastructure. Hence, it is good to divide the roles and responsibilities according to the skills and knowledge of the pentester to achieve the required goal.
	- Other infrastructure restrictions: Certain test restrictions can be applied by the client to control the assessment process. For instance, test all the devices behind the network segment A except the first router. Restrictions that are imposed by the client do not ensure the security of a router in the first place, which can lead to a compromise in the whole network, even if all the other network devices are hardened and security-assured. Thus, proper thinking is always required before putting any such restrictions on the penetration testing.

• **Defining business objectives**: This is a process of aligning business views with the technical objectives of the penetration testing program. Business objectives are the main source to bring the management and technical team together in order to support a strong proposition and an idea of securing information systems

	- Provide industry-wide visibility and acceptance by maintaining regular security checks.
	- Achieve the necessary standards and compliance by assuring business integrity.
	- Secure the information systems holding confidential data about the customers, employees, and other business entities.
	- List the active threats and vulnerabilities found in the network infrastructure, and help to create security policies and procedures that should thwart known and unknown risks.
	- Provide a smooth and robust business structure that will benefit its partners and clients.
	- Retain the minimum cost for maintaining the security of an IT infrastructure. The security assessment measures the confidentiality, integrity, and availability of the business systems.
	- Provide greater return on investment by eliminating any potential risks that might cost more if exploited by a malicious adversary.
	- Detail the remediation procedures that can be followed by a technical team at the concerning organization to close any open doors, and thus, reduce the operational burden.
	- Follow the industry best practices and best-of-breed tools and techniques to evaluate the security of the information systems according to the underlying technology.
	- Recommend any possible security solutions that should be used to protect 		the business assets.

• **Project management and scheduling**: This directs every other step of the penetration testing process with a proper timeline for test execution. This can be achieved using a number of advanced project management tools.


#### The customer requirements form

• Collect basic information such as company name, address, website, contact
person(s) details, e-mail address, and telephone number(s).
• Determine the key objectives behind the penetration testing project.
• Determine the penetration test type (with or without specific criteria):
	- Black box testing
	- White box testing
	- External testing
	- Internal testing
	- Social engineering included
	- Social engineering excluded
	- Investigate employee background information
	- Adopt employee's fake identity (legal council may be required)
	- Denial of service included
	- Denial of service excluded
	- Penetrate business partner systems
• How many servers, workstations, and network devices need to be tested?
• Which operating system technologies are supported by your infrastructure?
• Which network devices need to be tested? Firewalls, routers, switches, load
balancers, IDS, IPS, or any other appliances?
• Are disaster recovery plans in place? If yes, whom should we contact?
• Are there any administrators currently managing your network?
• Is there any specific requirement to comply with industry standards? If yes,
list them.

#### The deliverables assessment form

• What types of reports are expected?
	- Executive reports
	- Technical assessment reports
	- Developer reports
• In which format do you prefer the report to be delivered? PDF, HTML,
• How should the report be submitted? Encrypted e-mail or printed?
• Who is responsible for receiving these reports?
	- Employee
	- Shareholder
	- Stakeholder


## 2. INFORMATION GATHERING

In this phase, we try to collect as much information as we can about the target, for example, information about the Domain Name System (DNS) hostnames, IP addresses, technologies and configuration used, username's organization, documents, application code, password reset information, contact information, and so on. During information gathering, every piece of information gathered is considered important.

- Active information gathering: we introduce traffic to the target network
- Passive information gathering: gather information about a target network by utilizing third-party services, such as Google.

#### Using public resources
	http://www.archive.org
	http://www.domaintools.com/
	http://www.alexa.com/
	http://centralops.net/
	http://www.robtex.com
	http://www.pipl.com/
	http://yoname.com
	http://wink.com/
	http://www.isearch.com/
	http://www.tineye.com
	
	
#### Querying the domain registration information

After you know the target domain name, the first thing you would want to do is query the Whois database about that domain to look for the domain registration information. The Whois database will give information about the DNS server and the contact information of a domain.

> whois example.com

#### Analyzing the DNS records

	No.	Record type	Description
	1	SOA			This is the start of authority record.
	2	NS			This is the name server record.
	3	A			This is the IPv4 address record.
	4	MX			This is the mail exchange record.
	5	PTR			This is the pointer record.
	6	AAAA		This is the IPv6 address record.
	7	CNAME		This is the abbreviation for canonical name. It is used as an alias name for another canonical domain name.


For example, in a penetration test engagement, the customer may ask you to find out all of the hosts and IP addresses available for their domain. The only information you have is the organization's domain name. We will look at several common tools that can help you if you encounter this situation.

	
#### HOST

>  host www.example.com

gives us

	www.example.com has address 192.0.43.10
	www.example.com has IPv6 address 2001:500:88:200::10

To query for any records, just give the -a option to the command.

> host -a example.com

	Trying "example.com"
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25153
	;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 2
	;; QUESTION SECTION:
	;example.com. IN ANY
	
	;; ANSWER SECTION:
	example.com. 3201 IN SOA dns1.icann.org.
	hostmaster.icann.org. 2012080782 7200 3600 1209600 3600
	example.com. 46840 IN NS a.iana-servers.net.
	example.com. 46840 IN NS b.iana-servers.net.
	;; ADDITIONAL SECTION:
	b.iana-servers.net. 1401 IN A 199.43.133.53
	a.iana-servers.net. 1401 IN A 199.43.132.53
	Received 170 bytes from 202.152.165.39#53 in 563 ms

If you give the domain name as the command-line option in host, the method is called forward lookup, but if you give an IP address as the command-line option to the host command, the method is called reverse lookup.

		
#### HOST: DNS zone transfer
		
A DNS zone transfer is a mechanism used to replicate a DNS database from a master DNS server to another DNS server, usually called a slave DNS server.

> host -l example.com ns4.isp.com

The following is the DNS zone transfer result:

	Using domain server:
	Name: ns4.isp.com
	Address: 172.16.176.22#53
	Aliases:
	example.com name server ns1.isp.com.
	example.com name server ns2.isp.com.
	example.com has address 192.168.1.1
	smtp.example.com has address 192.168.1.2
	mail.example.com has address 192.168.1.3
	webmail.example.com has address 192.168.1.3
	www.example.com has address 192.168.1.4
	
		
		
#### DIG

The advantages of dig compared to host are its flexibility and clarity of output.
Without giving any options besides the domain name, the dig command will only return the A record of a domain. To request for any other DNS record type, we can give the type option in the command line:

> dig example.com any

	; <<>> DiG 9.7.0-P1 <<>> example.com any
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40971
	;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 2

	;; QUESTION SECTION:
	;example.com. IN ANY

	;; ANSWER SECTION:
	example.com. 3565 IN SOA dns1.icann.org.
	hostmaster.icann.org. 2012080782 7200 3600 1209600 3600
	example.com. 83186 IN AAAA 2001:500:88:200::10
	example.com. 48296 IN NS b.iana-servers.net.
	example.com. 48296 IN NS a.iana-servers.net.

	;; ADDITIONAL SECTION:
	a.iana-servers.net. 182 IN A 199.43.132.53
	b.iana-servers.net. 182 IN A 199.43.133.53

	;; Query time: 327 msec
	;; SERVER: 202.152.165.39#53(202.152.165.39)
	;; WHEN: Sat Aug 18 10:46:09 2012
	;; MSG SIZE rcvd: 198


#### DIG DNS zone transfer

We must set the authoritative DNS server for that domain and set axfr as the type:

> dig @ns4.isp.com example.com axfr

	; <<>> DiG 9.7.0-P1 <<>> @ns4.isp.com example.com axfr
	; (1 server found)
	;; global options: +cmd
	example.com. 3600 IN SOA ns1.isp.com. hostmaster.
	isp.com. 2011020409 900 600 86400 3600
	example.com. 3600 IN NS ns1.isp.com.
	example.com. 3600 IN NS ns4.isp.com.
	example.com. 3600 IN A 192.168.1.1
	example.com. 3600 IN MX 192.168.1.3
	mail.example.com. 3600 IN A 192.168.1.3
	webmail.example.com. 3600 IN A 192.168.1.3
	www.example.com. 3600 IN A 192.168.1.4
	example.com. 3600 IN SOA ns1.isp.com. hostmaster.
	isp.com. 2011020409 900 600 86400 3600
	;; Query time: 855 msec
	;; SERVER: 172.16.176.22#53 (172.16.176.22)
	;; WHEN: Sat Aug 18 10:59:11 2012
	;; XFR size: 9 records



#### DNSENUM

With dnsenum we can gather
• The host IP addresses
• The DNS server of a domain
• The MX record of a domain
• Get additional names and subdomains utilizing the Google search engine.
• Find out subdomain names by brute forcing the names from the text files. The dnsenum tool included in Kali Linux comes with a dns.txt dictionary file that contains 1,480 subdomain names and a dns-big.txt file, which contains 266,930 subdomain names.
• Carry out Whois queries on C-class domain network ranges and calculate its network ranges.
• Carry out reverse lookup on network ranges.
• Use threads to process different queries.


> dnsenum example.com

	dnsenum.pl example.com
	dnsenum.pl VERSION:1.2.2
	----- example.com -----
	Host's addresses:

	__________________
	Name Servers:

	______________
	ns1.isp.com 10771 IN A 172.168.1.2
	ns0.isp.com 7141 IN A 172.168.1.1
	Mail (MX) Servers:

	___________________
	hermes1.example.com 86400 IN A 192.168.10.3
	hermes.example.com 3600 IN A 192.168.10.2
	Trying Zone Transfers and getting Bind Versions:

	_________________________________________________
	Trying Zone Transfer for example.com on ns0.isp.com ...
	AXFR record query failed: NOERROR
	ns0.isp.com Bind Version:
	DNS server

	Trying Zone Transfer for example.com on ns1.isp.com ...
	example.com 86400 IN SOA
	example.com 86400 IN NS
	example.com 86400 IN MX
	example.com 86400 IN TXT
	admin.example.com 3600 IN NS
	blogs.example.com 3600 IN NS
	ftp.example.com 3600 IN A 192.168.10.4
	hermes.example.com 3600 IN A 192.168.10.2
	hermes.example.com 86400 IN TXT
	hermes.example.com 86400 IN SPF
	hermes1.example.com 86400 IN A 192.168.10.2
	www.example.com 3600 IN NS
	ns1.isp.com Bind Version:
	DNS server
	brute force file not specified, bay.


#### DNSDICT6

Enumerate subdomains in IPv6


#### FIERCE

The fierce tool is a DNS enumeration tool that uses several techniques to find all of the IP addresses and hostnames of a target. It works by first querying your system's DNS server for the target DNS server; next, it uses the target DNS server. It also supports the wordlist supplied by the user to find subdomain names. It does this recursively until all of the wordlist items are tested. The main feature of fierce is that it can be used to locate noncontiguous IP space and hostnames against specified domains.

> fierce -dns example.com -threads 3

	DNS Servers for targetdomain.com:
		ns4.example.com
		ns1.example.com
		ns2.example.com
		ns3.example.com
		
	Trying zone transfer first...
		Testing ns4.example.com
			Request timed out or transfer not allowed.
		Testing ns1.example.com
			Request timed out or transfer not allowed.
		Testing ns2.example.com
			Request timed out or transfer not allowed.
		Testing ns3.example.com
			Request timed out or transfer not allowed.

	Unsuccessful in zone transfer (it was worth a shot)
	Okay, trying the good old fashioned way... brute force
	Checking for wildcard DNS...
	Nope. Good.
	Now performing 1895 test(s)...
	192.168.116.3 voips.example.com
	192.168.116.7 ns.example.com
	192.168.116.19 streaming.example.com
	192.168.117.50 dev.example.com
	192.168.117.16 mx1.example.com
	192.168.117.17 mx2.example.com
	192.168.117.18 mx3.example.com
	192.168.117.16 imap.example.com
	192.168.117.5 www.example.com
	192.168.117.6 intra.example.com
	192.168.117.17 mail.example.com
	192.168.117.5 web.example.com
	192.168.117.16 webmail.example.com

	Subnets found (may want to probe here using nmap or unicornscan):
		192.168.73.0-255 : 2 hostnames found.
		192.168.46.0-255 : 1 hostnames found.
		192.168.116.0-255 : 34 hostnames found.
		192.168.117.0-255 : 25 hostnames found.

	Done with Fierce scan: http://ha.ckers.org/fierce/


#### DMITRY

All-in-one information gathering tool.

• The Whois record of a host by using the IP address or domain name
• Host information from Netcraft.com
• Subdomains in the target domain
• The e-mail address of the target domain
• Open, filtered, or closed port lists on the target machine by performing a port scan

> dmitry -iwnse targethost

	Deepmagic Information Gathering Tool
	"There be some deep magic going on"

	HostIP:192.168.xx.xx
	HostName:targethost

	Gathered Netcraft information for targethost
	---------------------------------
	Retrieving Netcraft.com information for targethost
	No uptime reports available for host: targethost
	Gathered Subdomain information for targethost
	---------------------------------
	Searching Google.com:80...
	HostName:targethost
	HostIP:192.168.xx.xx
	HostName:www.ecom.targethost
	HostIP:192.168.xx.xx
	HostName:blogs.targethost
	HostIP:192.168.xx.xx
	HostName:static.targethost
	HostIP:192.168.xx.xx
	HostName:webmail.targethost
	HostIP:192.168.xx.xx
	...
	Gathered E-Mail information for targethost
	---------------------------------
	Found 0 E-Mail(s) for host targethost, Searched 0 pages containing 0 results


##### MALTEGO




## 3. Getting network routing information
-------------------------------------

#### TCPTRACEROUTE

The tcptraceroute tool can be used as a complement to the traceroute command.

The traceroute command sends a UDP or ICMP echo request packet with a Time To Live (TTL) of one and increments the TTL until the packet reaches the target, while the tcptraceroute tool uses TCP SYN to send out the packet to the target.

The advantage of using tcptraceroute is that, nowadays, it is common to find a firewall device filtered traceroute packet, so it will not be possible to trace the network path to the target completely. However, this firewall still allows a packet to reach a particular TCP port in the target machine. By using tcptraceroute, we will be able to find the network path to the target, even though there is a firewall in front of it.

The tcptraceroute tool will receive a SYN/ACK packet if the port is open and a RST packet if the port is closed.


#### TCTRACE

Another tool that can be used to do route analysis is tctrace. It works by sending a TCP SYN packet to the target.
		



## 4. Utilizing the search engine
-----------------------------

The Kali Linux tools grouped in this category can be used to collect domain, e-mail address, and document metadata information from the target.


#### THEHARVESTER

The theharvester tool is an e-mail accounts, username, and hostname/subdomains gathering tool.

> theharvester -d example.com -l 100 -b google


#### METAGOOFIL

Metagoofil is a tool that utilizes the Google search engine to get metadata from the documents available in the target domain. Currently, it supports the following document types:
• Word document (.docx, .doc)
• Spreadsheet document (.xlsx, .xls, .ods)
• Presentation file (.pptx, .ppt, .odp)
• PDF file (.pdf)


> metagoofil -d example.com -l 20 -t doc,pdf –n 5 -f test.html -o test

Metagoofil is also able to generate information in an HTML report format.

