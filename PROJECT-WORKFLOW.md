# AWS DataSync Project Workflow

## Project Flow

```text
ON-PREMISES
    |
    | NFS / SMB / HDFS
    v
DataSync Agent
    |
    | VPN / Direct Connect
    v
AWS DataSync
    |
    +------------------+
    |                  |
    v                  v
Amazon S3          Amazon EFS
                       |
                       v
                    EC2
                       |
                       v
                 Mount & Verify
```

## Workflow Steps

### 1. Prepare Source
Configure the on-premises storage containing the data to be migrated.

### 2. Deploy DataSync Agent
Deploy the AWS DataSync Agent in the on-premises environment to access NFS, SMB or HDFS storage.

### 3. Establish Connectivity
Connect the on-premises environment to AWS using VPN or AWS Direct Connect.

### 4. Configure DataSync
Create the DataSync source and destination locations and configure a DataSync task.

### 5. Transfer Data
Run the DataSync task to securely transfer data to AWS storage.

### 6. S3 to EFS Migration
Use AWS DataSync to transfer data from Amazon S3 to Amazon EFS.

### 7. Access Through EC2
Use a Linux EC2 instance to mount the EFS file system.

### 8. Verify Data
Check the mounted EFS directory and verify that the migrated files are available.

## AWS CLI Practice

The project also includes AWS CLI operations for:

- EC2 instance management
- EC2 tagging
- EBS volume management
- IAM role concepts
- AWS CLI configuration

## Result

The project demonstrates a complete data migration workflow from on-premises storage to AWS and shows how migrated data can be accessed and verified from an EC2 instance.
