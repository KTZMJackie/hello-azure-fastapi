# Azure FastAPI Microservice with CI/CD, Container Apps & Key Vault
A production-style cloud microservice built with FastAPI, Docker and Azure Container Apps.
The service retrieves secrets securely from Azure Key Vault using Managed Identity and is automatically deployed via GitHub Actions CI/CD.

# LIVE DEMO
Note: Infrastructure has been torn down to avoid ongoing Azure costs.

API : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io

Swagger Docs : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io/docs

Health Check : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io/health

Secret : Health Check : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io/secret

# ARCHITECTURE OVERVIEW
FastAPI runs in Azure Container Apps and retrieves secrets securely from Azure Key Vault using Managed Identity. 
CI/CD is handled through GitHub Actions which builds and deploys the Docker container automatically.

<img width="297" height="411" alt="Screenshot 2026-03-04 at 6 11 23 PM" src="https://github.com/user-attachments/assets/d76c0b6d-fcb4-421b-bfbd-d57b19bb331c" />

## Tech Stack
- Python
- FastAPI
- Docker
- Azure Container Apps
- Azure Container Registry
- Azure Key Vault
- Managed Identity
- GitHub Actions CI/CD

## API Endpoints
### Root
GET /
Returns service status.
Example response
{
 "status": "ok",
 "message": "Hello from FastAPI on Azure Container Apps"
}

### Health Check
GET /health
Used for monitoring and container health checks.
{
 "status": "healthy"
}

### Secret Retrieval
GET /secret
Retrieves a secret from Azure Key Vault using Managed Identity.
{
 "secret_name": "sthello",
 "retrieved": true
}

## CI/CD Pipeline
Deployment is automated using GitHub Actions.

Pipeline flow:
1. Developer pushes code to GitHub
2. GitHub Actions builds Docker image
3. Image pushed to Azure Container Registry
4. Azure Container Apps pulls new image
5. New revision deployed automatically

## Security
Secrets are never stored in the codebase.

The application retrieves secrets securely using:
- Azure Managed Identity
- Azure Key Vault

This eliminates the need for credentials or connection strings inside the application.

## Run Locally
Install dependencies
pip install -r requirements.txt
Run application
uvicorn src.main:app --host 0.0.0.0 --port 8000

# ENGINEERING CHALLENGES SOLVED
During development several cloud, container and CI/CD integration issues were encountered.  
The following table summarizes the key engineering challenges and how they were resolved.

| Problem | Solution |
| Docker build failed due to incorrect build context | Updated GitHub Actions workflow to build using the correct `./app` directory |
| Container App deployment failed in CI/CD | Corrected resource group and container app name in deployment configuration |
| Key Vault secret retrieval failed due to invalid name | Renamed secret to follow Azure Key Vault naming rules |
| Secure secret management without credentials | Implemented Azure Managed Identity for Container App to access Key Vault |

# PROJECT STRUCTURE
<img width="378" height="298" alt="Screenshot 2026-02-17 at 4 39 08 PM" src="https://github.com/user-attachments/assets/a56ccb30-72b1-4a6f-a0ed-3eed8ad5e78c" />

# GITHUB DEPLOYMENT SUCCESS
<img width="1112" height="638" alt="Screenshot 2026-03-04 at 6 25 54 PM" src="https://github.com/user-attachments/assets/0d538552-3ce0-4a05-91cb-a02425a75d4f" />

# Azure Container App Oveview
<img width="1419" height="408" alt="Screenshot 2026-02-17 at 3 59 15 PM" src="https://github.com/user-attachments/assets/01674068-7ac7-4299-98b7-fcf00d3446a0" />
