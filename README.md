# AWS CLI commands

### Creating a key pair:
    ```
    aws ec2 create-key-pair --key-name MyKeyPair \
        --query 'KeyMaterial' \
        --output text > MyKeyPairCli.pem
    ```    


### Deleting a key pair:
    aws ec2 delete-key-pair --key-name MyKeyPair


#### The docs:
https://docs.aws.amazon.com/cli/latest/userguide/cli-services-ec2-keypairs.html#cli-services-ec2-keypairs-prereqs
