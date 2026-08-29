# EC2, EBS and IAM – AWS CLI Operations

## 1. EC2 Instance

EC2 provides the compute server used to access and verify the migrated data.

### Create EC2

```bash
aws ec2 run-instances \
  --image-id <ami-id> \
  --count 1 \
  --instance-type t2.micro \
  --key-name <key-name> \
  --security-group-ids <security-group-id> \
  --subnet-id <subnet-id>
```

### Start EC2

```bash
aws ec2 start-instances --instance-ids <instance-id>
```

### Stop EC2

```bash
aws ec2 stop-instances --instance-ids <instance-id>
```

### Terminate EC2

```bash
aws ec2 terminate-instances --instance-ids <instance-id>
```

### Create EC2 Tag

```bash
aws ec2 create-tags \
  --resources <instance-id> \
  --tags Key=Name,Value=CLIDemo
```

---

## 2. EBS Volume

EBS provides block storage that can be attached to an EC2 instance.

### Describe Volumes

```bash
aws ec2 describe-volumes
```

### Create EBS Volume

```bash
aws ec2 create-volume \
  --size 10 \
  --region ap-south-1 \
  --availability-zone ap-south-1a \
  --volume-type gp2
```

### Attach EBS Volume

```bash
aws ec2 attach-volume \
  --volume-id <volume-id> \
  --instance-id <instance-id> \
  --device /dev/sdh
```

### Detach EBS Volume

```bash
aws ec2 detach-volume --volume-id <volume-id>
```

### Delete EBS Volume

```bash
aws ec2 delete-volume --volume-id <volume-id>
```

---

## 3. IAM Role

IAM Roles provide temporary permissions to AWS resources without storing access keys directly on the EC2 instance.

```text
EC2 Instance
      |
      v
   IAM Role
      |
      v
Temporary Credentials
      |
      v
   AWS Services
```

For production workloads, use **least-privilege permissions**.

---

## 4. AWS CLI Configuration

Check AWS CLI version:

```bash
aws --version
```

Configure AWS CLI:

```bash
aws configure
```

The configuration includes:

- Access Key ID
- Secret Access Key
- Default Region
- Output Format

---

## 5. Project Use Case

In this project, EC2 is used as a Linux environment to access and verify the migrated files.

EBS provides additional block storage for the EC2 instance, while IAM Roles provide secure access to AWS services.

### Overall Flow

```text
AWS CLI
   |
   +----> EC2 Instance
   |          |
   |          +----> EBS Volume
   |
   +----> IAM Role
              |
              v
         AWS Services
```
