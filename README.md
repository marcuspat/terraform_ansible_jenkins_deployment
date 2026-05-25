# Terraform & Ansible Jenkins Deployment

Complete infrastructure as code solution for deploying Jenkins CI/CD platform on AWS with integrated Ansible automation.

## 🎯 Overview

This repository provides a complete Jenkins deployment solution combining **Terraform** for AWS infrastructure provisioning and **Ansible** for Jenkins configuration. It automatically sets up a production-ready Jenkins environment with proper networking, security, and scaling capabilities.

## 🏗️ Architecture

**Infrastructure Components:**
- **AWS VPC** with public and private subnets
- **Application Load Balancer** for high availability
- **EC2 instances** for Jenkins master and workers
- **Security groups** with proper access controls
- **DNS integration** for domain management
- **SSL/TLS certificates** via AWS ACM

## 📁 Contents

### Terraform Configuration
- **acm.tf** - SSL certificate management
- **alb.tf** - Application Load Balancer setup
- **backend.tf** - Terraform state backend configuration
- **dns.tf** - DNS routing and domain management
- **instances.tf** - Jenkins EC2 instance configuration
- **networks.tf** - VPC and networking setup
- **security_groups.tf** - Firewall and access rules
- **variables.tf** - Configuration variables
- **outputs.tf** - Deployment outputs
- **providers.tf** - AWS provider configuration

### Ansible Automation
- **ansible/templates/install_jenkins.yml** - Jenkins master installation
- **ansible/templates/jenkins-worker-sample.yml** - Worker configuration
- **ansible/templates/jenkins-master-sample.yml** - Master configuration
- **ansible/templates/install_worker.yml** - Worker setup
- **ansible.cfg** - Complete Ansible configuration (730KB)
- **ansible/templates/inventory_aws/** - Dynamic EC2 inventory

### Documentation
- **jenkins_aws_diagram.png** - Architecture diagram (730KB)

## 🚀 Quick Start

### Prerequisites
```bash
# Install Terraform
# Install Ansible
# Configure AWS credentials
aws configure
```

### Deployment
```bash
# Clone the repository
git clone https://github.com/marcuspat/terraform_ansible_jenkins_deployment.git
cd terraform_ansible_jenkins_deployment

# Initialize Terraform
terraform init

# Plan deployment
terraform plan

# Deploy infrastructure
terraform apply

# Configure Jenkins with Ansible
cd ansible
ansible-playbook -i inventory_aws/tf_aws_ec2.yml install_jenkins.yml
```

## 🔧 Configuration

### Required Variables
```hcl
# Example variables to set
variable "aws_region" {
  description = "AWS region for deployment"
  default     = "us-east-1"
}

variable "environment" {
  description = "Environment name"
  default     = "production"
}

variable "jenkins_instance_count" {
  description = "Number of Jenkins worker instances"
  default     = 2
}
```

### Ansible Configuration
The repository includes a comprehensive `ansible.cfg` file with:
- **Inventory settings** for AWS dynamic discovery
- **SSH configuration** for secure access
- **Jinja2 template** settings
- **Callback plugins** for logging
- **Retry patterns** for reliability

## 🛠️ Features

### Infrastructure Automation
- **VPC with HA architecture** - Multi-AZ deployment
- **Load Balancing** - ALB for traffic distribution
- **Auto Scaling** - Automatic worker scaling
- **SSL/TLS** - Secure HTTPS with ACM certificates
- **DNS Management** - Route53 integration

### Jenkins Configuration
- **Master-Worker Architecture** - Scalable build farm
- **Automated Installation** - Hands-off deployment
- **Security Hardening** - Proper access controls
- **Backup Ready** - Data persistence and recovery
- **Monitoring Ready** - CloudWatch integration

### Security Features
- **Security Groups** - Network-level access control
- **IAM Roles** - Proper AWS permissions
- **Key Management** - SSH key management
- **Network Isolation** - Private subnets for workers
- **SSL Encryption** - Data in transit protection

## 📋 Architecture Diagram

The repository includes `jenkins_aws_diagram.png` showing:
- VPC architecture with subnets
- Load balancer configuration
- Jenkins master and worker placement
- Security group relationships
- Network flow and routing

## 🎓 Use Cases

**CI/CD Infrastructure:**
- Production Jenkins deployment
- Multi-environment pipelines
- Automated testing infrastructure
- Continuous deployment platforms

**DevOps Automation:**
- Infrastructure as code demonstration
- Terraform + Ansible integration
- AWS best practices implementation
- High availability setup

## 🔧 Scaling

**Horizontal Scaling:**
```bash
# Scale Jenkins workers
terraform apply -var="jenkins_instance_count=5"

# Add build agents
cd ansible
ansible-playbook -i inventory_aws/ install_worker.yml
```

## 📊 Monitoring

**AWS CloudWatch:**
- Instance metrics and logs
- ALB health checks
- VPC flow logs
- Jenkins metrics integration

## 🤝 Contributing

Contributions welcome! This is a complete production-ready Jenkins deployment solution.

## 📚 Related Repositories

- **IAC** - General infrastructure as code
- **devops** - DevOps automation collection
- **Misc_Ansible_Playbooks** - Ansible playbook examples

## 📝 License

Infrastructure automation - Free to use and modify.

---

**Terraform & Ansible Jenkins Deployment** - Production-ready CI/CD infrastructure with comprehensive automation and security.
