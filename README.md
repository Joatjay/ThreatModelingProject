<h1>Capstone Project: Threat Modeling - BigMart </h1>

<h2>Overview</h2>

Project consists of developing a distributed web store architecture using Python and Nginx for scalability, as BigMart aims to become a market leader in daily groceries and home requirements through a secure and seamless online shopping experience. Prioritized features include secure payment integration with third-party processors, user activity tracking, and regular database backups for disaster recovery. The ultimate goal is to surpass online competitors by delivering a seamless and secure shopping experience for customers.

<br />

<h2>Business Objectives</h2>

1.	To achieve the leading position in the market for everyday groceries and home essentials.
2.	To deliver a secure, seamless, and enhanced user experience for customers of Big Mart.
3.	To enable customers to conveniently browse products and complete orders through the online web store.
4.	To facilitate easy registration and account creation for customers to streamline the order placement process.
5.	To offer a diverse range of payment options, including digital wallets, online banking, debit cards, and credit cards.
6.	To empower the sales team with access to customer order details to ensure efficient processing and timely delivery.
7.	To authorize administrators to modify product information as necessary.

<br />

<h2>Security Objectives</h2>

1.  To ensure the confidentiality of customer identifiable information and order details and protect it from unauthorised access and disclosure.
2.	To maintain the integrity of customer data and prevent unauthorized modifications and tampering.
3.	To secure the authentication process to prevent unauthorized access to customer accounts.
4.	To safeguard payment transactions and secure customer payment information from theft or fraud.
5.	To implement robust access controls and protect against unauthorized access to the web store, database, and administrative functionalities.
6.	To monitor and track user interactions within the web store to detect and respond to any suspicious activity.
7.	To establish a reliable backup mechanism for the database to support disaster recovery and ensure data availability.


<br />


<h2>Tools Used</h2>

- [OWASP Threat Dragon](https://owasp.org/www-project-threat-dragon/)<br/> 
- [Lucid Chart](https://www.lucidchart.com/pages/landing?utm_source=google&utm_medium=cpc&utm_campaign=_chart_en_tier1_mixed_search_brand_exact_&km_CPC_CampaignId=1490375427&km_CPC_AdGroupID=55688909257&km_CPC_Keyword=lucid%20chart&km_CPC_MatchType=e&km_CPC_ExtensionID=&km_CPC_Network=g&km_CPC_AdPosition=&km_CPC_Creative=354596043016&km_CPC_TargetID=kwd-55720648523&km_CPC_Country=9071816&km_CPC_Device=c&km_CPC_placement=&km_CPC_target=&gclid=Cj0KCQjwoK2mBhDzARIsADGbjerltYFaqk8q1eybf2GmvTot07b8C21MaJKrjg1XNk-t1vIB8Z76jroaAsJqEALw_wcB)

<h2>Environments Used </h2>

- <b> [Kali Linux](https://www.kali.org/)</b>

With these objectives in mind, we can proceed to threat modelling of the application.

<h2>Threat Modeling Phases</h2>

<h3>PHASE 1: IDENTIFY ASSETS</h3>
<h3>Human Actors and non-human actors of the system</h3>
<br />
<h3>Human actors</h3>

<br />
Customers: Customers access the web store using a web browser or dedicated application. They browse through product listings, add items to their shopping cart, proceed to checkout, and submit orders. They may also create accounts, provide personal information for shipping and payment, and interact with customer support if needed.

<br />
Sales Team: The sales team manages customer interactions, processes order, generates invoices, and tracks shipments. They utilize the sales portal or CRM system to input and retrieve customer data, access sales records, and perform various sales-related tasks.

<br />
Administrators: The admin team performs administrative tasks such as managing product information, updating inventory, handling customer support inquiries, and managing employee information. They access the admin panel or backend system to make changes, monitor system performance, and handle administrative functions.
<br/>
<h3>Non-Human Actors</h3>
<br/>
Web Store Application: The software system that facilitates customer interactions and manages the web store functionalities.
<br/>
Backend Database: Stores customer data, product information, and order details. Data backup systems and processes used to create copies of the database for disaster recovery purposes.
<br/>
Third-Party Payment Processor: The external service provider responsible for processing credit card transactions.
<br/>
<h3>Data Elements</h3>
•	Customer Information: Customer Identifiable Information (CII) including full name, contact information (phone number, email address and residential address), and account credentials.<br/>
•	Order Details: Information related to customer orders, such as products purchased, quantities, and transaction history.<br/>
•	Product Information: Details about the products available in the web store, including descriptions, prices, and stock levels.<br/>
•	Payment Information: Credit card details, debit card details, online banking credentials, and digital wallet information.<br/>
<br/>
<h3>Technologies Used</h3>
•	Programming Language: Python which is use for developing the web store application and associated functionality.<br/>
•	Web Server: Nginx (Linux) server for serving web store and handling incoming requests.<br/>
•	Backend Database Options: Oracle or Microsoft SQL Server to store and retrieve data.<br/>

<h3>External Dependencies</h3>
•	Internet: External network connectivity required for customers to access the web store.<br/>
•	Third-Party Payment Processor: External service provider responsible for processing payment transactions. BigMart may rely on external payment processors, such as PayPal, Stripe, or a bank’s payment gateways, to handle and securely process customer payments.<br/>

<h3>Threat Actors</h3>
•	Hackers and Cybercriminals: Individuals or groups with malicious intent, aiming to exploit vulnerabilities in the system for financial gain or disruption.<br/>
•	Insiders: Disgruntled employees or individuals with authorized access to the system who may misuse their privileges or compromise sensitive data.<br/>
•	Advanced Persistent Threat (APT): Sophisticated threat actors, often state -sponsored, who target organizations to gain unauthorized access, steal sensitive data, or disrupt operations.<br/>
•	Cyber Terrorists: Individuals or groups who use cyber-attacks to promote a political, ideological, or social agenda.<br/>
•	Generic Hackers: Non-targeted hackers who exploit known vulnerabilities or use automated tools to gain unauthorized access or disrupt systems.<br/>
•	Competitors: Online competitors seeking to gain advantage or disrupt BigMart's business by exploiting vulnerabilities or conducting malicious activities.<br/>
•	Data Brokers: Entities interested in obtaining customer data for unauthorized marketing purposes or selling it on the dark web.<br/>

 
<h2>PHASE 2: CREATE ARCHITECTURAL OVERVIEW</h2>

BigMart's online strategy requirements include implementing a firewall for boundary protection, utilizing a Web Application Firewall (WAF) to secure the application, employing security solutions like IDS to monitor for malicious traffic, placing the application server in the DMZ, and locating the database server within the internal network. These measures aim to ensure the security and protection of BigMart's online platform, safeguarding customer data and preventing unauthorized access or attacks.<br/>

<p align="center">
Physical topology <br/>
<img src="https://i.imgur.com/7W1KJq1.png" height="80%" width="80%" alt="Physical Topology"/>
<br />

The logical topology for BigMart's online strategy would include the following components:<br/>

•	Sales Team: <br/>The sales team interacts with the web server through the sales portal or CRM system. They input and retrieve customer data, access sales records, and perform various sales-related tasks. They send requests to the web server to retrieve customer information, process orders, generate invoices, and track shipments. The web server handles requests, interacts with the application layer and database, and provides responses to the sales team.<br/>

•	Admin: <br/>The admin team interacts with the web server through the admin panel or backend system. They perform various administrative tasks such as managing product information, updating inventory, handling customer support inquiries, and managing employee information. They send requests to the web server to make changes, monitor system performance, and handle administrative functions. The web server processes these requests, retrieves, or updates data from the application layer and database, and sends the appropriate responses back to the admin.<br/>

•	Customers: <br/>Customers access the web store using their devices and establish a connection. They make requests to the server over the public internet, which are then processed by the web server, and it could be intercepted by an attacker. As such, the requests should require HTTP/S (SSL/TLS encryption). This will provide confidentiality and integrity. The web server retrieves data from the application layer and database as needed and sends the appropriate responses back to the customers' devices.<br/>

•	Web Server: <br/>The web server acts as the entry point for customers, receiving their requests and serving the web store's content. It operates within a trust boundary, separating it from the application layer. The server should be implemented with robust encryption algorithms and protocols and make sure that the encryption is applied to sensitive data both in rest and in transit.<br/>

•	Application: <br/>The application layer handles the business logic and processes customer requests received from the web server. It operates within its own trust boundary, separating it from the database layer. The web application stores credentials, so it should be encrypted. <br/> 

•	Database: <br/>The database stores and manages the product information, customer details, and order data. It operates within its own trust boundary, providing a layer of separation and security. Ensure an encrypted connection at the database server. This must be secure VPN.<br/>

•	Secure VPN: <br/>The connection between the application layer components, such as the web server and the database, is established using a secure Virtual Private Network (VPN). This ensures encrypted communication and secure data transfer between these components.<br/>


<p align="center">
Logical Topology <br/>
<img src="https://i.imgur.com/2V5V4yD.png" height="80%" width="80%" alt="Logical Topology"/>
<br />

<h3>PHASE 4: IDENTIFY THREATS</h3>

[STRIDE model](https://en.wikipedia.org/wiki/STRIDE_(security)) is used to identify threats for the BigMart’s business.

The STRIDE model is a threat modeling framework used to analyse and identify potential threats to software systems. It helps security professionals and developers understand and mitigate security risks by considering six categories of threats: Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege.<br/>

| STRIDE          | Desired Property | Possible Threats       |
|---------------|-----|------------------|
| Spoofing      | Authenticity  | Identity Spoofing, Session Hijacking|
| Tampering   | Integrity  | Cross-site Scripting (XSS), SQL Injection |
| Repudiation | Non-Repudiability  | No Audit Logs, Security Logging and Monitoring Failures  |
| Information Disclosure | Confidentiality  | Insufficient Encryption, Misconfigured Systems  |
| Denial od Service (DoS) | Availability  | DDoS, Phlashing(Permanent DoS attack) |
| Elevation of Privilege | Authorization  | Credential Theft, Privilege Escalation Exploits   |



<h3>PHASE 5: DOCUMENT THREATS</h3>


| Threats          | Threats Description | Threat Target | Attack techniques | Controls/Countermeasures |  Threat Rating     |
|------------------|---------------------|---------------|--------------------|--------------------------|--------------------|
| Identity Spoofing | An attacker impersonates another user by using stolen credentials or manipulating authentication mechanisms to gain unauthorized access. A hacker steals a user's login credentials and logs into their account, pretending to be the legitimate user. | User accounts or profiles, Authentication systems | Phishing: Attackers send fraudulent emails or messages to trick users into revealing their login credentials or personal information. Man-in-the-Middle (MitM) Attack: Attackers intercept communication between a user and a server, impersonating the user to gain unauthorized access.| Multi-factor authentication: Implementing additional verification steps, such as one-time passwords or biometric authentication, adds an extra layer of security. Strong password policies: Enforcing complex passwords and regular password updates reduces the risk of easy-to-guess credentials. | Medium |
| Session Hijacking | An attacker intercepts and takes control of an ongoing session between a user and a system, allowing them to perform actions on behalf of the user. An attacker captures the session cookie of a logged-in user and uses it to gain unauthorized access to the user's account. | Active user sessions, Web application session management systems | Session sniffing: Attackers intercept and capture session data, such as session IDs, to hijack an ongoing session. Session sidejacking: Attackers exploit insecure communication channels (e.g., unencrypted Wi-Fi) to intercept session information and gain unauthorized access. | Transport Layer Security (TLS): Encrypting session data using HTTPS helps prevent session data interception.Session timeouts and re-authentication: Implementing session timeouts and periodically requiring users to re-authenticate mitigates the risk of prolonged session hijacking. | Medium |
| Cross-site Scripting(XSS) | An attacker injects malicious scripts into web pages viewed by other users, allowing them to steal sensitive information or perform unauthorized actions. An attacker injects a script into a comment section of a website, which is then executed by other users' browsers, stealing their session cookies. | Web Browser, User Applications | Reflected XSS: Attackers inject malicious code into a website URL, which is then executed by unsuspecting users when they visit the compromised page. Stored XSS: Attackers inject malicious code into a website's database, which is then served to users when they access the affected web page. | Input validation and output sanitization: Implement strict input validation and output filtering to prevent the execution of malicious scripts. Content Security Policy (CSP): Enforce a CSP that restricts the execution of scripts to trusted sources, reducing the risk of XSS attacks.| High |
| SQL Injection | An attacker inserts malicious SQL statements into input fields to manipulate or gain unauthorized access to a database. By entering specially crafted input, an attacker exploits a vulnerability in a website's database query and retrieves sensitive data or modifies database contents. | Web applications using SQL databases, Database management systems | Classic SQL injection: Attackers exploit poorly sanitized user inputs to inject malicious SQL queries, allowing them to extract, modify, or delete data from the database. Blind SQL injection: Attackers leverage conditional SQL queries to infer information from the database, even without direct extraction capabilities.| Prepared statements and parameterized queries: Using prepared statements or query parameters instead of concatenating user inputs helps prevent SQL injection attacks. Input validation and output escaping: Validate and sanitize user inputs to remove or neutralize any potentially malicious SQL code.| High |
| No Audit Logs | Lack of proper logging and auditing mechanisms can allow malicious actors to perform unauthorized actions without traceability or accountability. It becomes difficult to identify and prove the occurrence of such actions. A system does not keep logs of user activities, making it challenging to investigate and attribute specific actions to individuals. | System logs and event records, Security monitoring systems | Log tampering: Attackers modify or delete logs to cover their tracks and hide their activities. Log flooding: Attackers generate a high volume of log entries to overwhelm logging systems, making it difficult to detect and analyse legitimate security events.| Regular log monitoring: Actively review and analyse system logs to detect any suspicious or abnormal activities. Secure log storage: Ensure that logs are stored securely, preventing unauthorized access, or tampering, and maintain backups to recover in case of log loss or manipulation.| Medium |
| Security Logging and Monitoring Failures | Inadequate monitoring or failure to analyse security logs can lead to undetected security incidents and make it challenging to identify and respond to unauthorized actions. A system fails to generate alerts or notifications when suspicious activities occur, resulting in delayed detection of security breaches. | Security monitoring systems and tools, Incident response processes |Log suppression: Attackers intentionally disable or manipulate security logging and monitoring mechanisms to avoid detection. False positives: Attackers exploit the high volume of security alerts and false positives to hide their actual malicious activities within the noise.| Implement robust monitoring solutions: Deploy intrusion detection and prevention systems (IDPS), security information and event management (SIEM) systems, and anomaly detection tools to enhance visibility and detect security incidents. Regularly test and validate logging and monitoring: Conduct regular assessments to ensure that logging and monitoring systems are functioning properly and generating accurate alerts. Perform penetration testing and log analysis to identify any gaps or weaknesses in the monitoring setup.| Medium |

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
