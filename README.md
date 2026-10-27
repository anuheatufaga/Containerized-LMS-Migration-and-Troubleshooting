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
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
