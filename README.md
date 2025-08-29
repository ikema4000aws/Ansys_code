# Ansys_code

# Terraform AWS VPC and EC2 Infrastructure

This Terraform configuration creates a complete AWS infrastructure with:
- VPC with CIDR block 10.0.0.0/16
- 3 public subnets across different availability zones
- 3 private subnets across different availability zones
- Internet Gateway for public subnets
- NAT Gateway for private subnets
- EC2 instance in public subnet with nginx installed
- Security groups allowing HTTP (port 80) and SSH (port 22) access

## Project Structure

```
.
├── main.tf                 # Main Terraform configuration
├── variables.tf            # Variable definitions
├── outputs.tf              # Output definitions
├── terraform.tfvars        # Variable values
├── README.md               # This file
└── modules/
    ├── vpc/
    │   ├── main.tf         # VPC module configuration
    │   ├── variables.tf    # VPC module variables
    │   └── outputs.tf      # VPC module outputs
    └── ec2/
        ├── main.tf         # EC2 module configuration
        ├── variables.tf    # EC2 module variables
        └── outputs.tf      # EC2 module outputs
```

## Prerequisites

- Terraform >= 1.0
- AWS CLI configured with appropriate credentials
- EC2 key pair named "terraform-key" (or update key_name variable)

## Usage

1. Initialize Terraform:
   ```bash
   terraform init
   ```

2. Review the plan:
   ```bash
   terraform plan
   ```

3. Apply the configuration:
   ```bash
   terraform apply
   ```

4. Access the nginx server:
   - Use the public IP output from terraform
   - Access via HTTP on port 80

5. Destroy the infrastructure:
   ```bash
   terraform destroy
   ```

## Customization

Modify `terraform.tfvars` to customize:
- AWS region
- VPC CIDR block
- Environment name
- Project name
- Instance type
- Key pair name

## Outputs

- `vpc_id`: VPC ID
- `public_subnet_ids`: List of public subnet IDs
- `private_subnet_ids`: List of private subnet IDs
- `ec2_instance_id`: EC2 instance ID
- `ec2_public_ip`: Public IP of EC2 instance
- `ec2_public_dns`: Public DNS of EC2 instance
