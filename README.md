# 🌍 Multi-Cloud Deployment with AWS + Azure

A high-availability web application setup deployed across **AWS** and **Azure**, featuring automated failover, DNS health checks, and infrastructure-as-code.

## 🚀 Project Overview

This project demonstrates:
- Cross-cloud deployment of a simple web app (frontend)
- DNS-based health check and traffic failover using AWS Route 53 + Azure Traffic Manager
- Use of **Terraform** and **CloudFormation** for complete infra automation
- GitHub Actions pipeline for multi-cloud deployment

## 🧱 Architecture

- Frontend deployed to:
  - **AWS S3 (static hosting)** + CloudFront
  - **Azure Blob Static Website**
- **Health Checks**: AWS Route 53 monitors Azure and AWS endpoints
- **Failover Routing**: If primary region fails, traffic is routed to backup cloud
- **Automation**: GitHub Actions for CI/CD into both clouds

               +---------------------+
               |   Route 53 (AWS)    |
               +----------+----------+
                          |
          +---------------+---------------+
          |                               |
+---------v----------+          +---------v----------+
|   AWS S3 + CF      |          |  Azure Blob Static |
|   (Primary)        |          |  (Failover)        |
+--------------------+          +--------------------+

## 🛠️ Tech Stack

| Layer         | Tool/Service           |
|---------------|------------------------|
| IaC           | Terraform, CloudFormation |
| Cloud 1       | AWS S3, Route 53, CloudFront |
| Cloud 2       | Azure Blob Storage, Traffic Manager |
| CI/CD         | GitHub Actions         |
| Monitoring    | Route 53 Health Checks |

## 📁 Project Structure

multi-cloud-deployment/
├── aws/
│ ├── main.tf
│ └── cloudformation.yaml
├── azure/
│ ├── main.tf
│ └── storage-setup.json
├── .github/workflows/
│ └── deploy.yml
├── public/
│ └── index.html
├── README.md
└── .gitignore

## 🔐 Security Considerations

- No secrets committed to repo
- OIDC used for GitHub → AWS/Azure authentication
- S3 buckets and Blob containers use HTTPS-only policies

## ✅ To Run Locally

1. Install Terraform CLI
2. Configure AWS and Azure credentials (via CLI or env vars)
3. Run:
   ```bash
   cd aws && terraform init && terraform apply
   cd ../azure && terraform init && terraform apply

   
💡 Future Enhancements:
1. Add monitoring dashboard (Grafana)
2. Add backend + DB (multi-cloud replication)
3. Use Pulumi for unified infra

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
👤 Author
Mansi Gangurde
Senior Cloud Engineer | DevOps Lead
🔗 LinkedIn
📧 mansigangurde0@gmail.com
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

⭐ Give it a star if you liked it!

