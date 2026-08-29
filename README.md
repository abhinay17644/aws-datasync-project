# AWS DataSync – On-Premises to AWS Data Migration

Hands-on AWS project covering AWS DataSync, S3, EFS, EC2, EBS, AWS CLI and IAM Roles.

## Project Overview

This project demonstrates:

- On-premises to AWS data migration using AWS DataSync
- S3 to EFS data transfer
- DataSync Agent, Source, Destination and Tasks
- EC2 and EBS management using AWS CLI
- IAM Role-based access for EC2
- EFS mounting and file verification

## Architecture

```text
On-Premises
     |
 NFS / SMB / HDFS
     |
DataSync Agent
     |
VPN / Direct Connect
     |
AWS DataSync
   /  |  \
  S3 EFS FSx
S3 → EFS Workflow
S3
 |
AWS DataSync
 |
EFS
 |
EC2
 |
NFS Mount
 |
File Verification
AWS CLI
EC2
aws ec2 run-instances ...
aws ec2 start-instances --instance-ids <instance-id>
aws ec2 stop-instances --instance-ids <instance-id>
aws ec2 terminate-instances --instance-ids <instance-id>
aws ec2 create-tags --resources <instance-id> --tags Key=Name,Value=CLIDemo
EBS
aws ec2 describe-volumes
aws ec2 create-volume --size 10 --region ap-south-1 --availability-zone ap-south-1a --volume-type gp2
aws ec2 attach-volume --volume-id <volume-id> --instance-id <instance-id> --device /dev/sdh
aws ec2 detach-volume --volume-id <volume-id>
aws ec2 delete-volume --volume-id <volume-id>
IAM Security

For EC2 workloads, use an IAM Role instead of storing long-term access keys on the instance.

EC2 → IAM Role → Temporary Credentials → AWS Services
EFS Verification
yum install -y nfs-utils
mkdir vansh
mount -t nfs4 <EFS-DNS-NAME>:/ vansh/
cd vansh
ls
Real-World Use Case

Organizations can use AWS DataSync to migrate large amounts of data from on-premises NFS, SMB or HDFS environments to AWS storage such as S3, EFS or FSx.

Technologies

AWS DataSync | S3 | EFS | FSx | EC2 | EBS | AWS CLI | IAM | NFS | SMB | HDFS

Key Learnings
AWS DataSync architecture
DataSync Agent and Tasks
S3 to EFS migration
EC2 and EBS CLI operations
IAM Roles
EFS mounting and verification

Project Status

Completed hands-on AWS learning project covering DataSync, AWS storage, EC2, EBS, IAM and AWS CLI.
