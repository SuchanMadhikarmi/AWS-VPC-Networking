<h1>AWS VPC Networking and Security Implementation</h1>



<h2>Description</h2>
This project demonstrates the design and security configuration of an AWS Virtual Private Cloud (VPC). It covers key aspects such as VPC traffic flow, subnet management, Elastic IPs, VPC peering, and secure access to AWS services using VPC endpoints. The project also includes configuring monitoring with VPC Flow Logs and CloudWatch. By implementing these features, I built a secure, scalable cloud infrastructure, ensuring private communication between resources and applying AWS best practices for cloud networking and security.<br/>


<br />

<h2>Tools and Technologies Used</h2>

- **AWS VPC** – Virtual Private CLoud for isolated cloud environment.
 
- **AWS EC2** –  Virtual servers to host applications and test secure configurations.
  
- **AWS S3** –  Storage service for testing secure access from within the VPC.

- **Elastic IPs** – Static public IP addresses for dynamic resource assignments.

- **AWS VPC Peering** – Enables communication between two VPCs.
  
- **AWS VPC FLow Logs** – Monitors traffic flows within the VPC.
  
- **AWS CLI** – Command-line tool for managing AWS resources.
  
- **AWS Cloudwatch** – Service for monitoring and logging VPC activities.
 
- **AWS VPC Endpoints** – Private connections to AWS services without traversing the internet.


<h2>Key Features</h2>

- **VPC Traffic Flow & Security**: Configured security groups, route tables, and network ACLs to control traffic securely.

- **Private Subnet Creation**: Set up isolated subnets for private resources and deployed EC2 instances for secure application hosting.
  
- **VPC Peering**: Enabled VPC Peering to allow secure, cross-VPC communication and resource sharing.

- **S3 Access from VPC**: Configured secure, private access to AWS S3 storage without exposing data to the public internet.
 
- **VPC Endpoint Configuration**: Ensured private connectivity to AWS services via VPC endpoints, without using the public internet.
 
- **Flow Logs & Monitoring**: Set up VPC Flow Logs and CloudWatch for enhanced monitoring and traffic analysis.
  
- **Elastic IPs Implementation**: Assigned and managed Elastic IPs for EC2 instances to ensure static IP addresses for secure, consistent communication.


<h2>Steps Undertaken :</h2>

 ### Step 1: Building a VPC

- **Created a VPC**  
  Set up the Virtual Private Cloud (VPC) for the environment.  
  [Click here to the Screenshot](https://i.imgur.com/eOS4XUH.png)

- **Created a Public Subnet**  
  Added a public subnet within the VPC to enable internet access for the resources.  
  [Click here to view the Screenshot](https://i.imgur.com/0l9NstN.png)

- **Enabled Auto-Assign IP Address**  
  Enabled auto-assign for IP addresses on the public subnet to make resource allocation easier.  
  [Click here to view the Screenshot](https://i.imgur.com/TCZary9.png)

- **Created an Internet Gateway and Attached it to the VPC**  
  Set up an Internet Gateway and attached it to the VPC to allow resources to communicate with the internet.  
  [Click here to view the Screenshot](https://i.imgur.com/qpOMhoU.png)

---


### Step 2: VPC Traffic Flow and Security
- **Edited Routes in the Routing Table**  
  Updated the routing table to ensure proper routing between subnets and the internet.  
  [Click here to view the Screenshot](https://i.imgur.com/9Tt1aAB.png)

- **Subnet Association in the Routing Table**  
  Associated the public subnet with the appropriate route in the routing table to allow internet access.  
  [Click here to view the Screenshot](https://i.imgur.com/KhyaD4m.png)

- **Created a Security Group**  
  Created a security group to define the allowed inbound and outbound traffic for instances within the VPC.  
  [Click here to view the Screenshot](https://i.imgur.com/rl15CWR.png)

- **Inbound Rule for Security Group Allowing HTTP**  
  Set up an inbound rule in the security group to allow HTTP traffic to the instances.  
  [Click here to view the Screenshot](https://i.imgur.com/AqWZJsb.png)

- **Created a Network Access Control List (NACL)**  
  Created a NACL to control traffic flow at the subnet level.  
  [Click here to view the Screenshot](https://i.imgur.com/6YXVmTA.png)

- **Edited NACL's Inbound Rule**  
  Modified the NACL's inbound rule to define the allowed traffic coming into the subnet.  
  [Click here to view the Screenshot](https://i.imgur.com/sxNq1DQ.png)

- **Edited NACL's Outbound Rule**  
  Modified the NACL's outbound rule to manage traffic leaving the subnet.  
  [Click here to view the Screenshot](https://i.imgur.com/F8ZAfBt.png)

---
### Step 3: Creating a Private subnet
- **Set up a Private Subnet**  
  Configured the private subnet to host resources that do not need direct access to the internet.  
  [Click here to view the screenshot](https://i.imgur.com/fFTRF3m.png)

- **Configured the Routing Table for the Private Subnet**  
  Set up the routing table to control traffic flow and ensure correct routing for the private subnet.  
  [Click here to view the screenshot](https://i.imgur.com/WRdiXeQ.png)

- **Created a NACL for the Private Subnet**  
  Created a Network Access Control List (NACL) to control the inbound and outbound traffic for the private subnet.  
  [Click here to view the screenshot](https://i.imgur.com/0lQ7Xq1.png)

---

### Step 4: Launching VPC resources
- **Created a Public EC2 Instance**  
  Launched an EC2 instance in the public subnet to host a publicly accessible service.  
  [Click here to view the screenshot](https://i.imgur.com/lLeNEKo.png)

- **Created a Keypair for the Public EC2 Instance**  
  Generated an SSH keypair to securely access the public EC2 instance.  
  [Click here to view the screenshot](https://i.imgur.com/7AZCjqr.png)

- **Network Setting (Creating in Public VPC)**  
  Ensured the EC2 instance was created in the correct VPC, not the default VPC, by configuring the network settings properly.  
  [Click here to view the screenshot](https://i.imgur.com/xIfk8Iu.png)

- **Created a Private EC2 Instance**  
  Launched an EC2 instance in the private subnet, ensuring it's isolated from direct internet access.  
  [Click here to view the screenshot](https://i.imgur.com/AsZoxXN.png)

- **Created an Inbound Security Group Rule for Private Instance**  
  Configured the security group to allow necessary inbound traffic to the private EC2 instance.  
  [Click here to view the screenshot](https://i.imgur.com/e08EUfN.png)

---

### Step 5: Testing VPC Connectivity
- **Tried to Connect to Public Instance via EC2 Instance Connect**  
  Attempted connecting to the public EC2 instance directly using EC2 Instance Connect.  
  [Click here to view the screenshot](https://i.imgur.com/BCfDbcA.png)

- **Connection Error**  
  Encountered an error during the connection attempt.  
  [Click here to view the screenshot](https://i.imgur.com/tmMkBQX.png)

- **Changed Inbound Rule for Security Group (SSH)**  
  Updated the inbound security group rule to allow SSH access to the public EC2 instance.  
  [Click here to view the screenshot](https://i.imgur.com/8UOJkzC.png)

- **Connection Success**  
  Successfully connected to the public EC2 instance after updating the security group rule.  
  [Click here to view the screenshot](https://i.imgur.com/4Ekozm4.png)

- **Pinged Private Server from Public Server (Error)**  
  Tried pinging the private server from the public instance but encountered an error.  
  [Click here to view the screenshot](https://i.imgur.com/AzGBTsN.png)

- **Updated Inbound Rule for Private Subnet NACL (Allow ICMP)**  
  Modified the inbound NACL rule to allow ICMP traffic for successful pinging.  
  [Click here to view the screenshot](https://i.imgur.com/biDwEKR.png)

- **Updated Outbound Rule for Private Subnet NACL**  
  Modified the outbound NACL rule to ensure proper response from the private server.  
  [Click here to view the screenshot](https://i.imgur.com/F8ZAfBt.png)

- **Updated Security Group for Private Instance (SSH & ICMP)**  
  Adjusted the security group for the private instance to allow both SSH and ICMP traffic.  
  [Click here to view the screenshot](https://i.imgur.com/86e1Czq.png)

- **Connectivity Success**  
  Successfully pinged the private EC2 instance after configuring the NACL and security group rules.  
  [Click here to view the screenshot](https://i.imgur.com/4Ekozm4.png)

- **Tested Internet Connectivity of Public Instance with Curl Command**  
  Tested the public instance’s internet connectivity using the curl command.  
  [Click here to view the screenshot](https://i.imgur.com/HhJTFda.png)

---

### Step 6: VPC Peering
- **Created Two VPCs from the VPC Dashboard**  
  Created two separate VPCs using the "VPC and More" option in the VPC dashboard.  
  [Click here to view the screenshot](https://i.imgur.com/5DImVAZ.png)

- **Created a Peering Connection**  
  Established a peering connection between the two VPCs.  
  [Click here to view the screenshot](https://i.imgur.com/0UIZQgo.png)

- **Accepted the Peering Connection Request**  
  Accepted the pop-up connection request that appeared for VPC peering.  
  [Click here to view the screenshot](https://i.imgur.com/uio4Jqr.png)

- **Edited Route Tables of Both VPCs**  
  Updated the route tables in both VPCs to allow traffic flow between them.  
  [Click here to view the screenshot](https://i.imgur.com/838O4Ng.png)  
  [Click here to view the screenshot](https://i.imgur.com/xmwhGw4.png)

- **Launched EC2 Instances in Both VPCs**  
  Launched instances in both VPCs to test the peering connection.  
  [Click here to view the screenshot](https://i.imgur.com/dTK5Pzp.png)

- **Attempted EC2 Instance Connect but Failed (No Public IP)**  
  Tried to connect to the EC2 instance but failed because no public IP was assigned.  
  [Click here to view the screenshot](https://i.imgur.com/3woyNDC.png)

- **Allocated Elastic IPs and Associated Them**  
  Allocated Elastic IPs and associated them with the EC2 instances.  
  [Click here to view the screenshot](https://i.imgur.com/9t0LHhO.png)

- **Changed Inbound Rule for VPC1 Security Group and Connected**  
  Updated the inbound rule for VPC1's security group, allowing connection.  
  [Click here to view the screenshot](https://i.imgur.com/avYiCuZ.png)  
  [Click here to view the screenshot](https://i.imgur.com/YvZOHyu.png)

- **Ping Failed from VPC1 to VPC2 (Fixed Security Group Inbound Rule in VPC2)**  
  Ping from VPC1 to VPC2 failed; changed the inbound security group rule in VPC2.  
  [Click here to view the screenshot](https://i.imgur.com/dAZ9mpR.png)

- **Ping Success from VPC1 to VPC2**  
  Successfully pinged the EC2 instance in VPC2 after modifying the security group rule.  
  [Click here to view the screenshot](https://i.imgur.com/4XR6mwh.png)

---
### Step 7: VPC Monitoring with Flow Logs
- **Launched Two EC2 Instances in Separate VPCs with Security Group Allowing ICMP Requests**  
  Launched instances in two VPCs and set the security group to allow all ICMP traffic.  
  [Click here to view the screenshot](https://i.imgur.com/ZeBPxtr.png)

- **Created a Flow Log Group in CloudWatch**  
  Created a CloudWatch log group for monitoring VPC flow logs.  
  [Click here to view the screenshot](https://i.imgur.com/EGRnGPK.png)

- **Created an IAM Policy for Flow Logs**  
  Created an IAM policy as flow logs need the proper permissions to write logs.  
  [Click here to view the screenshot](https://i.imgur.com/NW7Vd9U.png)

- **Created a Role to Assign the IAM Policy to Flow Logs**  
  Created a role and assigned the IAM policy to enable flow logs to write to CloudWatch.  
  [Click here to view the screenshot](https://i.imgur.com/PQWTDaK.png)

- **Created the VPC Flow Logs**  
  Created VPC flow logs to capture network traffic data.  
  [Click here to view the screenshot](https://i.imgur.com/GXQZuDS.png)

- **Sent Ping Request and Monitored Results in VPC Flow Logs on CloudWatch**  
  Initiated a ping request and observed the results in the VPC flow logs on CloudWatch.  
  [Click here to view the screenshot](https://i.imgur.com/DxyqUgE.png)

- **Performed a Log Insight Query**  
  Executed a query on CloudWatch Logs Insights to analyze the VPC flow logs.  
  [Click here to view the screenshot](https://i.imgur.com/aWHCnDG.png)

- **Obtained Results from the Query**  
  Retrieved the results after running the CloudWatch Logs Insights query.  
  [Click here to view the screenshot](https://i.imgur.com/7RmxSW5.png)

---
### Step 8: Acessing S3 from VPC
- **Created a VPC**  
  Set up a new Virtual Private Cloud (VPC) for accessing S3.  
  [Click here to view the screenshot](https://i.imgur.com/DkrOtLI.png)

- **Added an Instance in the VPC**  
  Launched an EC2 instance within the created VPC.  
  [Click here to view the screenshot](https://i.imgur.com/HMeFZbj.png)

- **Created Access Keys for Accessing S3**  
  Generated access keys for AWS CLI to interact with S3.  
  [Click here to view the screenshot](https://i.imgur.com/6zvh0Zi.png)

- **Retrieved the Access Key**  
  Retrieved the created access key for AWS CLI use.  
  [Click here to view the screenshot](https://i.imgur.com/fhXMDHK.png)

- **Created an S3 Bucket**  
  Created a new S3 bucket to store files.  
  [Click here to view the screenshot](https://i.imgur.com/b0jbiig.png)

- **Added Files to the S3 Bucket**  
  Uploaded files to the newly created S3 bucket.  
  [Click here to view the screenshot](https://i.imgur.com/HXEMyqx.png)

- **Accessed S3 Using AWS CLI with Access Keys**  
  Configured AWS CLI using the generated access keys to access S3.  
  [Click here to view the screenshot](https://i.imgur.com/VQchg1B.png)  
  [Click here to view the screenshot](https://i.imgur.com/xa0TAE8.png)

- **Ran `aws s3 ls` to View Files in the Bucket**  
  Listed the contents of the S3 bucket using AWS CLI.  
  [Click here to view the screenshot](https://i.imgur.com/CR3JV8y.png)

- **Created a File in the S3 Bucket Using the `sudo touch` Command**  
  Created a file within the S3 bucket from the EC2 instance.  
  [Click here to view the screenshot](https://i.imgur.com/zzVxCu4.png)

---
### Step 9: VPC Endpoint Configuration
- **Created Endpoint (Connection)**  
  Set up an endpoint connection to enable secure communication with S3.  
  [Click here to view the screenshot](https://i.imgur.com/CHJrZtr.png)

- **Created Policy Denying S3 Access Except from Endpoint**  
  Configured a policy to restrict S3 access, allowing only access via the endpoint connection.  
  [Click here to view the screenshot](https://i.imgur.com/wcnGL0G.png)

- **Error When Trying to Access S3**  
  Encountered an error while attempting to access S3 without the proper endpoint configuration.  
  [Click here to view the screenshot](https://i.imgur.com/9IPlb5P.png)

- **Edited Route Table to Add Endpoint Connection**  
  Updated the route table to include the newly created endpoint connection for proper routing.  
  [Click here to view the screenshot](https://i.imgur.com/J4xnf1f.png)  
  [Click here to view the screenshot](https://i.imgur.com/ebMeCqv.png)

- **Success**  
  Successfully accessed S3 through the endpoint connection after route table updates.  
  [Click here to view the screenshot](https://i.imgur.com/AooID7y.png)

- **Removed S3 Bucket from Endpoint (Access via Console Not Allowed)**  
  Emptying and removing the S3 bucket from the endpoint connection due to access limitations from the console.  
  [Click here to view the screenshot](https://i.imgur.com/DwHzb4T.png)

---
<h2>Key Learnings</h2>

- Gained hands-on experience in VPC design, subnetting, and resource isolation within AWS.

- Learned to configure security groups, NACLs, and route tables for proper network security.

- Implemented secure, private access to AWS services like S3 and ensured compliance with security policies.
  
- Gained expertise in setting up VPC Peering for secure cross-region or cross-account connectivity.
  
-  Set up and analyzed VPC Flow Logs for network traffic monitoring, security, and troubleshooting.

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
