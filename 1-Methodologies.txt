# Vulnerability Assessment & PenTesting Methodologies



## 1. Open Source Security Testing Methodology Manual (OSSTMM)

	- http://www.isecom.org/research/osstmm.html
	- http://www.isecom.org/mirror/OSSTMM.3.pdf

A recognized international standard created by Pete Herzog and developed by ISECOM for security testing and analysis.
It's being used by many organizations in their day-to-day assessment cycle. From a technical perspective, its methodology is divided into four key groups—scope, channel, index, and vector. The scope defines a process of collecting information on all assets that operate in the target environment. A channel determines the type of communication and interaction with these assets, which can be physical, spectrum, and communication. All of these channels depict a unique set of security components that must be tested and verified during the assessment period. These components are comprised of physical security, human psychology, data networks, wireless communication medium, and telecommunication. The index is a method that is used to classify target assets that correspond to their particular identifications, such as MAC Address and IP Address. At the end, a vector concludes the direction through which an auditor can assess and analyze each functional asset. The whole process initiates a technical roadmap that evaluates the target environment thoroughly and is known as audit scope.

The overall testing procedures focus on what is to be tested, how it should be tested, what tactics should be applied before, during, and after the test, and how to interpret and correlate the final results. Capturing the current state of the protection of a target system is considerably useful and invaluable. Thus, the OSSTMM methodology has introduced this terminology in the form of RAV (Risk Assessment Values). The basic function of RAV is to analyze the test results and compute the actual security value based on three factors, which are operational security, loss controls, and limitations. This final security value is known as RAV score.

## 2. Key features and benefits

* Substantially reduces the occurrence of false negatives and false positives
* Adaptable to many types of security tests, such as penetration testing, white box audit, vulnerability assessment, and so forth
* Ensures that the assessment should be carried out thoroughly
* Four individually connected phases, namely, definition phase, information phase, regulatory phase, and controls test phase. Each of these obtains, assesses, and verifies the information regarding the target
* RAV calculates the actual security value based on operational security, loss controls, and limitations
* Formalizing an assessment report using the Security Test Audit Report (STAR) template can be advantageous to management as well as the technical team
* The methodology is regularly updated with new trends of security testing, regulations, and ethical concerns
* The OSSTMM process can be coordinated with industry regulations, business policy, and government legislations



## 3. Information Systems Security Assessment Framework (ISSAF)
-----------------------------------------------------------
	- https://sourceforge.net/projects/isstf/
		
This framework has been categorized into several domains to address the security assessment in a logical order. Each of these domains assesses different parts of a target system and provides field inputs for the successful security engagement. By integrating its framework into a regular business life cycle, it may provide the accuracy, completeness, and efficiency required to fulfill an organization's security testing requirements.

The output is a combination of operational activities, security initiatives, and a complete listing of vulnerabilities that might exist in the target environment. The assessment process chooses the shortest path to reach the test deadline by analyzing its target against critical vulnerabilities that can be exploited with minimum effort.

Problem of maintenance to keep updating the framework in order to reflect new or updated technology assessment criteria. When compared to the OSSTMM methodology, these obsolescence issues affect the OSSTMM less, because the auditor is able to use the same methodology over the number of security engagements using a different set of tools and techniques.
		
### 3.1 Key features and benefits
		
* high value proposition to secure the infrastructure by assessing the existing security controls against critical vulnerabilities
* ISSAF penetration testing methodology examines the security of a network, system, or application
* It bridges the gap between the technical and managerial view of security testing by implementing the necessary controls to handle both areas


OSSTMM and ISSAF can be used in combination with each other to assess the security of an enterprise environment.


## 4. Open Web Application Security Project (OWASP)

	- OWASP Testing Guide: https://www.owasp.org/index.php/OWASP_Testing_Project
	- OWASP Guide Project: https://www.owasp.org/index.php?title=Category:OWASP_Guide_Project&redirect=no
	- OWASP Code Review Guide: https://www.owasp.org/index.php/OWASP_Code_Review_Guide_Table_of_Contents


The OWASP top 10 project categorizes the application security risks by evaluating the top attack vectors and security weaknesses in relation to their technical and business impact.
		
### 4.1 Key features and benefits
* Testing web applications against OWASP top ten security risks ensures that the most common attacks and weaknesses are avoided
* The OWASP community has developed a number of security tools that focus on the automated and manual web application tests. A few of these tools are WebScarab, Wapiti, JBroFuzz, and SQLiX.
* It provides industry-wide acceptance and visibility.	



## 5. Web Application Security Consortium Threat Classification (WASC-TC)

	- WASC Threat Classification: http://projects.webappsec.org/f/WASC-TC-v2_0.pdf  /  http://projects.webappsec.org/w/page/13246978/Threat%20Classification

WASC threat classification is another such open standard to assess the security of web applications. Similar to the OWASP standard, it is also classified into a number of attacks and weaknesses but addresses them in a much deeper fashion.

The overall standard is presented in three different views to help developers and security auditors understand the vision of web application security threats:

- Enumeration view: This view is dedicated to providing the basis for web application attacks and weaknesses.

- Development view: The development view takes the developer's panorama forward by combining the set of attacks and weaknesses into vulnerabilities, which are likely to occur at any of three consecutive development phases. This could be a design, implementation, or deployment phase.

- Taxonomy cross-reference view: Referring to a cross-reference view of multiple web application security standards can help auditors and developers map the terminology presented in one standard with another. With a little more effort, the same facility can also assist you in achieving multiple standard compliances at the same time.
			
### 5.1 Key features and benefits
* WASC-TC provides you with in-depth knowledge to assess the web application environment against the most common attacks and weaknesses
* The attacks and weaknesses presented by WASC-TC can be used to test and verify any web application platform using a combination of tools
* The standard provides you with three different views, namely, enumeration, development, and cross-reference.
* It can be aligned with other well-known application security standards, such as OWASP and SANS-CWE.


## 6. Penetration Testing Execution Standard (PTES)
-----------------------------------------------
	- http://www.pentest-standard.org/index.php/Main_Page
		
It consists of seven phases of penetration testing and can be used to perform an effective penetration test on any environment.

The seven stages of penetration testing that are detailed by this standard are as follows (source: www.pentest-standard.org):

• Pre-engagement interactions
• Intelligence gathering
• Threat modeling
• Vulnerability analysis
• Exploitation
• Post-exploitation
• Reporting
		

### 6.1	Key features and benefits
		
* Very thorough penetration testing framework that covers the technical as well as other important aspects of a penetration test.
* It has detailed instructions on how to perform many of the tasks that are required to accurately test the security posture of an environment
* It is inclusive of the most commonly found technologies as well as ones that are not so common
* It is easy to understand and you can adapt it to your own testing needs
		

## 7. General penetration testing framework
----------------------------------------

The framework is composed of a number of steps that should be followed in a process at the initial, medial, and final stages of testing in order to accomplish a successful assessment. These include the following:

	• Target scoping
	• Information gathering
	• Target discovery
	• Enumerating target
	• Vulnerability mapping
	• Social engineering
	• Target exploitation
	• Privilege escalation
	• Maintaining access
	• Documentation and reporting
		
#### TARGET SCOPING

	• What should be tested?
	• How should it be tested?
	• What conditions should be applied during the test process?
	• What will limit the execution of the test process?
	• How long will it take to complete the test?
	• What business objectives will be achieved?
	
#### INFORMATION GATHERING (Reconnaissance)

During this phase, a pentester uses a number of publicly available resources to learn more about his or her target. This information can be retrieved from Internet sources such as:

	• Forums
	• Bulletin boards
	• Newsgroups
	• Articles
	• Blogs
	• Social networks
	• Commercial or non-commercial websites
	
Additionally, the data can also be gathered through various search engines, such as Google, Yahoo!, MSN Bing, Baidu, and others. Moreover, an auditor can use the tools provided in Kali Linux to extract the network information about a target. These tools perform valuable data mining techniques to collect information through DNS servers, trace routes, Whois database, e-mail addresses, phone numbers, personal information, and user accounts.

#### TARGET DISCOVERY

This phase mainly deals with identifying the target's network status, operating system, and its relative network architecture.

#### ENUMERATING TARGET

This phase takes all the previous efforts forward and finds the open ports on the target systems. Once the open ports have been identified, they can be enumerated for the running services.

#### VULNERABILITY MAPPING

It is now time to identify and analyze the vulnerabilities based on the disclosed ports and services.

#### SOCIAL ENGINEERING

#### TARGET EXPLOITATION

After carefully examining the discovered vulnerabilities, it is possible to penetrate the target system based on the types of exploits that are available. The process coordinates three core areas, which involve pre-exploitation, exploitation, and post-exploitation activities.

#### PRIVILEGE ESCALATION

An auditor can now move freely into the system, depending on his or her access privileges. These privileges can also be escalated using any local exploits that match the system's environment, which, once executed, should help you attain super-user or system-level privileges. From this point of entry, an auditor might also be able to launch further attacks against the local network systems.

#### MAINTAINING ACCESS

Sometimes, an auditor might be asked to retain access to the system for a specified time period. Such activity can be used to demonstrate illegitimate access to the system without performing the penetration testing process again.

#### DOCUMENTATION AND REPORTING

Documenting, reporting, and presenting the vulnerabilities found, verified, and exploited will conclude your penetration testing activities.
		
		
		
		
		
		
		