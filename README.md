# 🚀 Terraform AWS 3-Tier Infrastructure Deployment using Jenkins CI/CD Pipeline

![Terraform](https://img.shields.io/badge/Terraform-IaC-blueviolet?style=for-the-badge\&logo=terraform)
![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge\&logo=amazonaws)
![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-red?style=for-the-badge\&logo=jenkins)
![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge\&logo=github)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-yellow?style=for-the-badge\&logo=ubuntu)

---

# 📌 Project Overview

This project demonstrates a **Production-Ready 3-Tier Architecture Deployment on Amazon Web Services (AWS)** using:

* ✅ Terraform Infrastructure as Code (IaC)
* ✅ Jenkins CI/CD Pipeline Automation
* ✅ GitHub Version Control
* ✅ AWS Cloud Infrastructure
* ✅ Modular Terraform Architecture
* ✅ Automated Infrastructure Provisioning
* ✅ Secure Deployment Workflow
* ✅ Real-Time Production Deployment Strategy

The project was designed to simulate a **real-world enterprise infrastructure deployment** where the complete AWS infrastructure is deployed automatically through a Jenkins CI/CD Pipeline.

This infrastructure provides:

* High Availability
* Scalability
* Security
* Automation
* Modular Design
* Infrastructure Consistency
* Faster Deployment Cycles
* Production-Grade Architecture

The project contains more than **30+ AWS Resources** including networking, compute, database, load balancing, IAM, security, storage, and monitoring components.

---

# 🏗️ 3-Tier Architecture Overview

The infrastructure is divided into the following layers:

## 🌐 1. Web Layer

The Web Layer handles incoming traffic from users.

### Components:

* Application Load Balancer (ALB)
* Public Subnets
* Auto Scaling Group
* Web EC2 Instances
* Security Groups
* Internet Gateway

### Responsibilities:

* Accept user requests
* Route traffic to application layer
* Load balancing
* SSL termination
* Public internet access

---

## ⚙️ 2. Application Layer

The Application Layer contains the business logic of the application.

### Components:

* Private EC2 Instances
* Auto Scaling Group
* Application Security Groups
* Private Subnets
* NAT Gateway

### Responsibilities:

* Business logic processing
* Internal application communication
* Secure backend processing
* API handling

---

## 🗄️ 3. Database Layer

The Database Layer stores application data securely.

### Components:

* Amazon RDS
* Private Database Subnets
* DB Security Groups
* Multi-AZ Database Architecture

### Responsibilities:

* Data storage
* Data persistence
* Backup & Recovery
* High availability database setup

---

# ☁️ AWS Services Used

| AWS Service               | Purpose                                    |
| ------------------------- | ------------------------------------------ |
| Amazon VPC                | Network Isolation                          |
| Public & Private Subnets  | Layer Separation                           |
| Internet Gateway          | Public Internet Access                     |
| NAT Gateway               | Secure Internet Access for Private Servers |
| Route Tables              | Traffic Routing                            |
| EC2 Instances             | Application Hosting                        |
| Auto Scaling Group        | Automatic Scaling                          |
| Launch Template           | EC2 Configuration                          |
| Application Load Balancer | Traffic Distribution                       |
| Amazon RDS                | Database Service                           |
| IAM Roles & Policies      | Access Management                          |
| Security Groups           | Firewall Rules                             |
| CloudWatch                | Monitoring                                 |
| S3 Bucket                 | Terraform State / Artifact Storage         |
| Jenkins                   | CI/CD Automation                           |
| GitHub                    | Source Code Management                     |

---

# 🧱 High Level Architecture Diagram

```text
                           ┌────────────────────┐
                           │      GitHub        │
                           │ Terraform Code Repo│
                           └─────────┬──────────┘
                                     │
                                     │ Git Push
                                     ▼
                           ┌────────────────────┐
                           │      Jenkins       │
                           │    CI/CD Server    │
                           └─────────┬──────────┘
                                     │
                         Terraform Pipeline
                                     │
      ┌──────────────────────────────┼──────────────────────────────┐
      │                              │                              │
      ▼                              ▼                              ▼
┌─────────────┐             ┌────────────────┐             ┌────────────────┐
│ Terraform   │             │ Terraform Plan │             │ Terraform Apply│
│ Validation  │             │ & Approval     │             │ Infrastructure │
└──────┬──────┘             └────────┬───────┘             └────────┬───────┘
       │                             │                               │
       └─────────────────────────────┼───────────────────────────────┘
                                     ▼
                         ┌─────────────────────┐
                         │      AWS Cloud      │
                         └─────────────────────┘
                                     │
         ┌───────────────────────────┼────────────────────────────┐
         │                           │                            │
         ▼                           ▼                            ▼
 ┌──────────────┐           ┌────────────────┐           ┌────────────────┐
 │   Web Layer  │           │ Application    │           │ Database Layer │
 │ Public EC2   │──────────▶│ Private EC2    │──────────▶│ Amazon RDS     │
 │ ALB          │           │ App Servers    │           │ MySQL/Postgres │
 └──────────────┘           └────────────────┘           └────────────────┘
```

---

# 📂 Repository Structure

```text
terraform-3tier-architecture/
│
├── Jenkinsfile
├── README.md
├── provider.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
├── versions.tf
│
├── modules/
│   ├── autoscaling/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   │
│   ├── database/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   │
│   ├── networking/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
│
├── environments/
│   ├── dev/
│   ├── stage/
│   └── prod/
│
└── scripts/
    ├── install.sh
    └── deploy.sh
```

---

# 🔄 Complete CI/CD Workflow

## 🔁 Pipeline Flow

```text
Developer
   │
   │ Push Terraform Code
   ▼
GitHub Repository
   │
   │ Webhook Trigger
   ▼
Jenkins Pipeline
   │
   ├── Checkout Code
   ├── Terraform Init
   ├── Terraform fmt -check
   ├── Terraform Validate
   ├── Terraform Plan
   ├── Archive Plan Artifact
   ├── Manual Approval
   ├── Terraform Apply
   └── Deployment Notification
   │
   ▼
AWS Infrastructure Provisioned Successfully
```

---

# ⚡ Jenkins Pipeline Stages

| Stage              | Description                            |
| ------------------ | -------------------------------------- |
| Checkout Code      | Pull latest code from GitHub           |
| Terraform Init     | Initialize Terraform working directory |
| Terraform fmt      | Check Terraform formatting             |
| Terraform Validate | Validate Terraform configuration       |
| Terraform Plan     | Preview infrastructure changes         |
| Archive Artifact   | Store Terraform plan artifact          |
| Manual Approval    | Human approval before deployment       |
| Terraform Apply    | Deploy infrastructure to AWS           |
| Notification       | Send deployment status                 |

---

# 🛠️ Jenkins Server Setup on AWS

## ✅ Step 1: Launch Jenkins EC2 Instance

### Configuration:

| Component      | Value                    |
| -------------- | ------------------------ |
| AMI            | Ubuntu Server            |
| Instance Type  | t2.medium / t3.medium    |
| Storage        | 20 GB                    |
| Port           | 8080                     |
| Security Group | Allow SSH & Jenkins Port |

### Security Group Rules:

| Port | Purpose           |
| ---- | ----------------- |
| 22   | SSH Access        |
| 8080 | Jenkins Dashboard |
| 80   | HTTP              |
| 443  | HTTPS             |

---

# ☕ Step 2: Install Java on Jenkins Server

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

### Verify Java:

```bash
java -version
```

---

# ⚙️ Step 3: Install Jenkins

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null


echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y
```

---

# ▶️ Step 4: Start Jenkins Service

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

---

# 🌍 Step 5: Access Jenkins Dashboard

```text
http://<Jenkins-Public-IP>:8080
```

Retrieve Jenkins Initial Password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

# 🏗️ Step 6: Install Terraform on Jenkins Server

```bash
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common

wget -O- https://apt.releases.hashicorp.com/gpg | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update
sudo apt install terraform -y
```

### Verify Terraform:

```bash
terraform version
```

---

# 📦 Step 7: Install Git on Jenkins Server

```bash
sudo apt install git -y
```

### Verify Git:

```bash
git --version
```

---

# 🔐 Step 8: Install AWS CLI

```bash
sudo apt install awscli -y
```

### Verify AWS CLI:

```bash
aws --version
```

---

# ☁️ Step 9: Configure AWS CLI

```bash
aws configure
```

Provide:

```text
AWS Access Key ID
AWS Secret Access Key
Default Region
Output Format
```

---

# 🔌 Step 10: Install Jenkins Plugins

Install the following plugins:

* Pipeline
* Git
* GitHub Integration
* Terraform
* AWS Credentials
* Blue Ocean
* Pipeline Utility Steps

Go To:

```text
Manage Jenkins → Plugins
```

---

# 🔑 Step 11: Configure AWS Credentials in Jenkins

Go To:

```text
Manage Jenkins → Credentials → Global
```

Add:

| Credential Type       | Value       |
| --------------------- | ----------- |
| AWS_ACCESS_KEY_ID     | Secret Text |
| AWS_SECRET_ACCESS_KEY | Secret Text |

Credential IDs:

```text
aws-access-key-id
aws-secret-access-key
```

---

# 🔗 Step 12: Configure GitHub Repository in Jenkins

## Pipeline Configuration

### Select:

```text
Pipeline script from SCM
```

### SCM:

```text
Git
```

### Provide:

```text
Repository URL
Branch: main
Script Path: Jenkinsfile
```

---

# 🧾 Jenkinsfile Example

```groovy
pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-west-2'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/<your repo>/3-tier-architecture.git'
            }
        }

        stage('Terraform Init') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Format Check') {
            steps {
                sh 'terraform fmt -check'
            }
        }

        stage('Terraform Validate') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform validate'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform plan -out=tfplan'
                }
            }
        }

        stage('Archive Terraform Plan') {
            steps {
                archiveArtifacts artifacts: 'tfplan', fingerprint: true
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'Approve Terraform Apply?', ok: 'Deploy'
            }
        }

        stage('Terraform Apply') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform apply tfplan'
                }
            }
        }
    }

    post {

        success {
            echo 'Terraform Infrastructure deployed successfully!'
        }

        failure {
            echo 'Terraform deployment failed!'
        }
    }
}
```

---

# 🚀 Deployment Steps

## Step 1: Clone Repository

```bash
git clone https://github.com/your-repo.git
cd terraform-3tier-architecture
```

---

## Step 2: Initialize Terraform

```bash
terraform init
```

---

## Step 3: Format Terraform Files

```bash
terraform fmt
```

---

## Step 4: Validate Terraform Code

```bash
terraform validate
```

---

## Step 5: Generate Terraform Plan

```bash
terraform plan
```

---

## Step 6: Apply Infrastructure

```bash
terraform apply
```

---

## Step 7: Verify AWS Infrastructure

Verify:

* VPC
* EC2 Instances
* Load Balancer
* Auto Scaling Group
* RDS Database
* Security Groups
* Route Tables
* NAT Gateway

---

# 🔒 Security Best Practices Implemented

✅ IAM Least Privilege Access

✅ Private Subnet for Backend Servers

✅ Security Groups for Layer Isolation

✅ Sensitive Credentials Stored in Jenkins Credentials

✅ No Hardcoded Secrets

✅ Infrastructure Validation Before Deployment

✅ Manual Approval Before Production Deployment

✅ Secure Remote Access

---

# 📈 Benefits of This Project

* Infrastructure Automation
* Faster Deployments
* Production-Ready Architecture
* Scalable Infrastructure
* Reduced Manual Errors
* Modular Terraform Design
* CI/CD Pipeline Automation
* Infrastructure Consistency
* High Availability Setup
* Real-Time Deployment Workflow

---

# 🎯 Key Learning Outcomes

Through this project, I gained hands-on experience with:

* Terraform Modules
* Infrastructure as Code (IaC)
* Jenkins CI/CD Automation
* AWS Networking
* EC2 & Auto Scaling
* RDS Database Deployment
* GitHub Integration
* Terraform State Management
* Secure Infrastructure Design
* Enterprise Cloud Deployment Practices
* Real-Time Production Infrastructure Deployment

---

# 📊 Project Workflow Summary

```text
Local Development
        │
        ▼
Push Code to GitHub
        │
        ▼
Jenkins Pipeline Triggered
        │
        ▼
Terraform Validation & Planning
        │
        ▼
Manual Approval
        │
        ▼
Terraform Apply
        │
        ▼
AWS Infrastructure Provisioned
        │
        ▼
Deployment Notification
```

---

# 📷 Suggested Screenshots for README

Add the following screenshots for better GitHub presentation:

* Jenkins Dashboard
* Jenkins Pipeline Success
* Terraform Plan Output
* AWS VPC Architecture
* EC2 Instances
* Load Balancer
* RDS Database
* GitHub Repository
* AWS Infrastructure Diagram

# 📷 Push the code from JumpBox to GitHub
<img width="1362" height="393" alt="push the code local to GitHub1" src="https://github.com/user-attachments/assets/44795bff-0063-4fdb-938e-85c39dd5c878" />

# 📷 Jenkinsfile create on GitHub
<img width="1344" height="709" alt="Jenkinsfile script" src="https://github.com/user-attachments/assets/f748e129-5522-4e2a-9f39-d47cc75ef260" />

# 📷 Jenkins Pipeline Configuration
<img width="1366" height="637" alt="AWS pipeline configuration" src="https://github.com/user-attachments/assets/4390c716-c685-4e4d-8e54-e6c763519dd3" />

<img width="1362" height="637" alt="repo path and branch" src="https://github.com/user-attachments/assets/d47d84d2-fe7c-4a70-80ca-b23f0232e6c5" />

# 📷 Jenkins Build Run
<img width="1351" height="678" alt="Run AWS Infra Pipeline using Jemkins" src="https://github.com/user-attachments/assets/4462a803-5788-4db8-a3c7-cc92c664e992" />

<img width="1366" height="691" alt="Pipeline validate terraform and terraform plan" src="https://github.com/user-attachments/assets/4748dcc6-46b5-4d05-85a2-208f523b42de" />

<img width="1366" height="693" alt="AWS 40 resources add in plan" src="https://github.com/user-attachments/assets/f1830964-0f52-436a-9b86-4d12f3329578" />

# 📷 Jenkins Build Run Manual Approval
<img width="1365" height="643" alt="Approved the manual stage" src="https://github.com/user-attachments/assets/31fc14de-0bb4-43f7-8a03-acf1482906df" />

<img width="1366" height="600" alt="AWS Infra terraform code successfully deploy" src="https://github.com/user-attachments/assets/0f7e535c-85eb-4456-a97c-ecaabc0e6d9c" />

<img width="1365" height="622" alt="Jenkins CICD stage view" src="https://github.com/user-attachments/assets/39a3f08e-0663-4d46-973a-12c31eccd51f" />

# 📷 Jenkins Build Artifact
<img width="1365" height="634" alt="Jenkins build artifact" src="https://github.com/user-attachments/assets/f313a786-25df-4a35-b102-27ad15aaf29f" />

# 📷 AWS 3-Tier Application Infrastructure Deployed
<img width="1366" height="606" alt="AWS VPC" src="https://github.com/user-attachments/assets/88066303-a5fb-4fdd-86e3-49cb64079dde" />

<img width="1365" height="604" alt="LB 3 tier architecture" src="https://github.com/user-attachments/assets/59ff68dd-f681-47ea-bcc3-80279a0cfa0d" />

---

# 🧠 Future Enhancements

* Kubernetes (EKS) Integration
* Docker Containerization
* Ansible Configuration Management
* SonarQube Integration
* Prometheus & Grafana Monitoring
* Terraform Remote Backend
* Multi-Environment Deployment
* Blue/Green Deployment Strategy
* Slack Notifications
* GitHub Webhooks Automation

---

# 🏁 Conclusion

This project demonstrates a complete end-to-end implementation of:

* Terraform Infrastructure Automation
* Jenkins CI/CD Pipeline
* GitHub Integration
* AWS Cloud Deployment
* Production-Grade 3-Tier Architecture

The entire infrastructure deployment process is fully automated and follows modern DevOps best practices used in real-world enterprise environments.

This project significantly improved understanding of:

* Cloud Infrastructure Automation
* CI/CD Workflow Implementation
* AWS Architecture Design
* Secure Infrastructure Deployment
* Terraform Module Architecture
* Production Deployment Strategies

---

# 👨‍💻 Author

## Prashant Mukadam

### DevOps Engineer | Cloud Enthusiast | AWS | Terraform | Jenkins | CI/CD | Infrastructure Automation

---

# ⭐ Support
If you found this project useful:
    * Star the repository
    * Fork the repository
    * Share with the DevOps community
