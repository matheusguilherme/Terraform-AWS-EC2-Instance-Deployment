# Terraform AWS EC2 Instance Deployment

This project uses Terraform to deploy and manage AWS EC2 instances along with the necessary security groups. The configuration includes provisioning EC2 instances, setting up security groups for SSH, HTTP, and egress access, and running a script to install and configure Apache2 and clone a GitHub repository.

## Project Structure

- `main.tf`: Configures the Terraform provider for AWS.
- `ec2.tf`: Defines the EC2 instances to be created.
- `security_group.tf`: Defines the security groups for SSH, HTTP, and egress access.
- `script.sh`: A script that updates the system, installs Apache2, and clones a GitHub repository.

## Resources

### EC2 Instances

- **Count**: 3 instances
- **AMI**: `ami-04b4f1a9cf54c11d0`
- **Instance Type**: `t2.micro`
- **Key Name**: `terraform`
- **User Data**: `script.sh`

### Security Groups

- **acesso_ssh**: Allows SSH access on port 22.
- **acesso_http**: Allows HTTP access on port 80.
- **acesso_egress**: Allows all outbound traffic.

## Usage

1. Ensure you have Terraform installed.
2. Configure your AWS credentials.
3. Initialize the Terraform configuration:
    ```sh
    terraform init
    ```
4. Apply the Terraform configuration:
    ```sh
    terraform apply
    ```

## Script

The [script.sh](http://_vscodecontentref_/0) file performs the following actions on each EC2 instance:

```bash
#! /bin/bash

sudo apt-get update
sudo apt-get upgrade -y

sudo apt-get install apache2 -y

sudo git clone https:://github.com/denilsonbonatti/mundo-invertido.git
cd mundo-invertido
sudo cp * -R /var/www/html/
