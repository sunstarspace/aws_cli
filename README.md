# **AWS CLI commands - collection for basic tasks**

<br />

## 1. IAM

#### Creating a key pair:

    aws ec2 create-key-pair --key-name MyKeyPair \
    --query 'KeyMaterial' \
    --output text > MyKeyPairCli.pem
   

#### Deleting a key pair:
    aws ec2 delete-key-pair --key-name MyKeyPair

<br />


## 2. Security groups

#### Creating a security group:
    aws ec2 create-security-group --group-name my-new-sg-from-cli \
    --description "My new security group from cli" \
    --vpc-id vpc-xxxxxxx



#### Allow specific inbound ports:
    aws ec2 authorize-security-group-ingress --group-id sg-xxxxxxx \
    --protocol tcp --port 22 --cidr 0.0.0.0/0

    aws ec2 authorize-security-group-ingress --group-id sg-xxxxxxx \
    --protocol tcp --port 80 --cidr 0.0.0.0/0


#### Deleting a security group:
    aws ec2 delete-security-group --group-id sg-xxxxxxx


<br />

## 3. EC2

#### Create an EC2 instance:
    aws ec2 run-instances --image-id ami-xxxxxxx --count 1 \
    --instance-type t2.micro --key-name MyKeyPair \
    --security-group-ids sg-xxxxxxx \
    --subnet-id subnet-xxxxxxx \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=ec2-from-cli}]'



<br />

## 4. Organizations:





<br />


### Create a group
    aws iam create-group --group-name TestGroup --profile mgmt

### Attach policy to group
    aws iam attach-group-policy \
    --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess \
    --group-name TestGroup --profile mgmt

### Add user to group
    aws iam add-user-to-group --user-name myuser\
    --group-name TestGroup --profile mgmt

### Remove user from group
    aws iam remove-user-from-group --user-name myuser \
    --group-name TestGroup --profile mgmt

### Detach policy from group
    aws iam detach-group-policy --group-name TestGroup \
    --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess --profile mgmt

### Delete a group
    aws iam delete-group --group-name TestGroup --profile mgmt


<br />


###### **DISCLAIMER**
Please consult the official documentation before using.
NOBODY BUT YOU IS RESPONSIBLE FOR ANY USE OR DAMAGE THIS COMMANDS MAY CAUSE.
THIS IS INTENDED FOR EDUCATIONAL PURPOSES ONLY. USE AT YOUR OWN RISK.

###### The docs:
https://awscli.amazonaws.com/v2/documentation/api/latest/index.html
