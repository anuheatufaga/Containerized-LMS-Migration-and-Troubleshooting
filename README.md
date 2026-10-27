<h1>AWS- Containereized LMS Migration and Troubleshooting</h1>

 

<h2>Description</h2>
This project simulates EduTech Solutions’ migration of its learning management system (LMS) frontend from an on-premises environment to a containerized deployment on AWS ECS Fargate. It recreates the deployment issues encountered during the migration, then uses Amazon CloudWatch, ECS logs, and the AWS Management Console to diagnose and resolve them.

The goal is to gain hands-on experience troubleshooting real-world container issues in AWS and develop practical skills relevant to a cloud support engineer role.
<br />


<h2>Services and Utilities Used</h2>

- <b>Amazon ECS w/ Fargate</b> 
- <b>Application Load Balancer (ALB)</b>
- <b>Amazon CloudWatch</b>
- <b>AWS IAM</b>
- <b>Amazon ECR</b>
- <b>AWS Security Groups</b>



<h2>Environments Used </h2>

- <b>Local Environment- Windows 11</b> (26H2)
- <b>Cloud Environment- AWS- Amazon ECS with AWS Fargate</b>
- <b>Monitoring and Troubleshooting- 	Amazon CloudWatch, ECS logs, and the AWS Management Console</b>

<h2>Program walk-through:</h2>

<p align="center">
<h4>- After setting up the AWS Account, create roles in ECS so that it can interact with the AWS Services securely. The trusted entity type will be "AWS Service," and the Service or use case will be "Elastic Container Service." The name of this role is "EduTech-ECS-Service-Role." </h4> <br/>
<img src="screenshots/Screenshot 2026-10-27 145833.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h4>The next role that will be created is "EduTech-ECS-Task-Role." Again, the trusted entity type will be "AWS Service," and the Service or use case will be "Elastic Container Service," but the use case will be "Elastic Container Service Task." The permissions that need to be added are "AmazonECSTaskExecutionRolePolicy" and "CloudWatchLogsFullAccess." Once that is all done, the role can be created.</h4>  <br/>
<img src="screenshots/Screenshot 2026-10-27 152022.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h4> Now that the Roles have been created, a dedicated network environment for the containerized LMS environment needs to be created, so I created a VPC network named "EduTech-VPC" with the following settings:<br/>
 <br/>
  - Availability Zones: 2<br/>
  - Public Subnets: 2<br/>
  - Private Subnets: 0<br/>
  - NAT Gateways: None<br/>
  - VPC Endpoints: None<br/>
<img src="screenshots/Screenshot 2026-10-27 153333.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h4>Now security groups need to be configured in order to control the allowed network traffic as well as add an extra layer of security. The first security group created: <br/>
 <br/>
"EduTech-ALB-SG" - the Application Load Balancer (ALB) <br/>
&nbsp;&nbsp;&nbsp;&nbsp;- Description: "Allow web traffic to our load balancer." <br/>
&nbsp;&nbsp;&nbsp;&nbsp;- VPC: "EduTech-VPC" <br/>
&nbsp;&nbsp;&nbsp;&nbsp;- Inbound Rules: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Type: HTTP; Source: Anywhere <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Type: HTTPS; Source: Anywhere <br/>
<img src="screenshots/Containerized LMS Migration and Troubleshooting/Screenshot 2026-10-18 155839.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h4>The second security group created:  <br/>
"EduTech-Container-SG" <br/>
&nbsp;&nbsp;&nbsp;&nbsp;-Description: "Allow web traffic to containers." <br/>
&nbsp;&nbsp;&nbsp;&nbsp;- VPC: "EduTech-VPC" <br/>
&nbsp;&nbsp;&nbsp;&nbsp;- Inbound Rules: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Type: Custom TCP; Port: 3000; Source: EduTech-ALB-SG  <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Type: HTTPS; Source: Anywhere <br/>
<img src="screenshots/Containerized LMS Migration and Troubleshooting/Screenshot 2026-10-18 160412.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h4> Now that the AWS environment is set up, the next section will be establishing the LMS frontend in a containerized version. First the ECR Repository will need to be created.  <br/>
 &nbsp;&nbsp;&nbsp;&nbsp;`edutech-lms-frontend` -Repository Name: `edutech-lms-frontend` along with default settings<br/>
<img src="screenshots/Screenshot 2026-10-27 164241.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/>
 <br/>
 <br/>
 Now AWS will need to be installed in order to set up the tools needed to push the container images. Ensure the aws --version is installed and use your credentials.
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
