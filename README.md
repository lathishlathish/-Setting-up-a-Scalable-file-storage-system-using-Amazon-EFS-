# SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
### REG NUMBER:212222230073
### NAME:LATHISH KANNA.M
 
## AIM:
To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT:
This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.
## ALGORITHM:
 ### Steps 1: Create two EC2 instances in different availability zones.
 Go to the EC2 service in the AWS Management Console.
Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.
Assign each instance a security group that allows NFS access on port 2049.
 ### Steps 2: Set up a security group that allows necessary communication between the instances and EFS.
 Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.
Attach this security group to the EFS file system to permit access from both instances.
 ### Steps 3: Create an EFS file system and mount it to both EC2 instances.
 In the AWS Console, navigate to the EFS service and select Create file system.
Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.
Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).
 ### Steps 4: Ensure that the EC2 instances can access the file system and share data between them.Instance 1
SSH into the first EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory and create a sample file:

Instance 2
SSH into the second EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory, list files, and view the content of the file created on Instance 1

## COMMANDS
Include the commands used in the Experiment.
### EC2 Instance 1:
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```
### EC2 Instance 2:
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  # Verify shared access by reading content created in Instance 1
```

## OUTPUT:
![386965681-c509af1a-92eb-45bc-bb31-9e0dc7174233](https://github.com/user-attachments/assets/98ae6071-f46e-4382-a6d8-9535caf7176b)
![386867742-b9f9af9d-9d66-46fd-9c0c-2344c807e401](https://github.com/user-attachments/assets/1150e28a-c230-4594-9501-ed44b72f0cfe)

### The creation of a file on Instance 1.
![387066599-3e9865fe-ed66-433c-8f3d-1dca50183729](https://github.com/user-attachments/assets/64f48e89-3c57-42d8-8ae7-9cb1ef7939b5)

### The display of that file’s contents on Instance 2 to verify shared access

![387066673-96cf5e99-a3a4-4066-aaa3-a1358b56f723](https://github.com/user-attachments/assets/220d95a6-78dd-42ee-a325-f1271e198bab)


## RESULT:
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing.

 

  


