<h1>AWS VPC Networking and Security Implementation</h1>



<h2>Description</h2>
This project demonstrates the design and security configuration of an AWS Virtual Private Cloud (VPC). It covers key aspects such as VPC traffic flow, subnet management, Elastic IPs, VPC peering, and secure access to AWS services using VPC endpoints. The project also includes configuring monitoring with VPC Flow Logs and CloudWatch. By implementing these features, I built a secure, scalable cloud infrastructure, ensuring private communication between resources and applying AWS best practices for cloud networking and security.<br/>


<br />

<h2>Tools and Technologies Used</h2>

- **AWS CloudFormation** – Deployed a vulnerable infrastructure including EC2 instances and S3 buckets.
 
- **Netxwork.org CloudFormation Template** –  Utilized to set up the infrastructure quickly.

- **OWASP Juice Shop** – A deliberately vulnerable web application hosted on an EC2 instance.

- **AWS GuardDuty** –  Monitors and detects suspicious activities and potential security threats.
  
- **Penetration Testing Techniques** – SQL Injection and Command Injection methods were applied.
  
- **AWS CLI** – Configured to interact with AWS services and execute commands.
  
- **Wget and Cat Commands** – Used for downloading and verifying files during exploitation.

<h2>Key Features</h2>

- **Automated Infrastructure Deployment**: Quickly set up a vulnerable environment using a pre-defined CloudFormation template.

- **Simulated Web Application Exploitation**: Demonstrated real-world attack vectors such as SQL injection and command injection.

- **Credential Extraction**: Successfully extracted AWS CLI credentials via a public JSON file.
  
- **Threat Detection and Analysis**: Employed AWS GuardDuty to identify unauthorized activities and generate security findings.

- **Malware Detection Integration**: Configured GuardDuty to detect a sample malware file (EICAR) within an S3 bucket.


<h2>Steps Undertaken :</h2>

 ### Step 1: Infrastructure Deployment
#### 1. CloudFormation Template Setup
- Selected the CloudFormation template provided by Netxwork.org.  
  <img src="https://i.imgur.com/wNmxRrA.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 2. Deployment of Vulnerable Components
Deployed the following resources:
- **EC2 Instance:** Hosts the OWASP Juice Shop web application.
- **S3 Bucket:** Contains a sensitive information file.
- **AWS GuardDuty:** Configured for continuous threat monitoring.


<img src="https://i.imgur.com/PpI4kmF.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  
#### 3. Verification of Deployment
- Verified that all resources were created successfully.
- Confirmed that the web application and S3 bucket were accessible.

  <img src="https://i.imgur.com/L0FoyIP.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/sG0TIVL.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

---

### Step 2: Exploitation Phase
#### 1. SQL Injection Attack
- Accessed the web app login page and used the payload:  
 
  <img src="https://i.imgur.com/Zo8SWGQ.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/sGNQKcf.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 2. Command Injection Attack
- Injected a command in the username field to trigger the creation of a JSON object.
- The JSON object contained AWS CLI credentials.

  <img src="https://i.imgur.com/h56y01U.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  
---

### Step 3: Credential Extraction and Utilization
#### 1. Accessing the JSON Object
- Retrieved the JSON file containing AWS credentials via the web application URL.

  <img src="https://i.imgur.com/XJMYS4T.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 2. Environment Setup and Credential Download
- Set up environment variables for AWS CLI.
- Used `wget` to download the credentials file.
- Verified the file content using `cat`.

  <img src="https://i.imgur.com/0JgxMH3.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/D5J6hjc.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 3. AWS CLI Profile Creation
- Created a new AWS CLI profile using the extracted credentials.
- Successfully connected to the S3 bucket using this profile.

  <img src="https://i.imgur.com/B6obqiR.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 4. S3 File Retrieval
- Downloaded the target file from the S3 bucket.
- Verified its content using terminal commands.
  
  <img src="https://i.imgur.com/UgAXuHS.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/kWi2H6o.png.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

---

### Step 4: Threat Detection and Analysis with AWS GuardDuty
#### 1. Initial Findings Review
- Logged into AWS GuardDuty and reviewed the initial findings that recorded the exploitation events.

  <img src="https://i.imgur.com/hxCqVNP.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/e3W6pCt.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/VWY4QT1.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 2. Malware Detection Setup
- Enabled malware detection for the S3 bucket.
- Uploaded a sample malware file (EICAR) to test detection.

  <img src="https://i.imgur.com/JxBAqH9.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/S01grzH.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/NGMeF5p.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>

#### 3. Final Findings Verification
- Revisited AWS GuardDuty to observe updated findings showing the detection of the sample malware.

  <img src="https://i.imgur.com/ShNFSah.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>


<h2>Key Learnings</h2>

- Enhanced skills in deploying and managing cloud environments using AWS CloudFormation.

- Gained practical insights into common vulnerabilities such as SQL injection and command injection.

- Learned how AWS GuardDuty can be leveraged to monitor, detect, and analyze threats in real time.
  
- Developed an understanding of ethical hacking techniques and the importance of secure configurations.
  
- Underlined the critical need for proper security controls around sensitive data and access permissions.

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
