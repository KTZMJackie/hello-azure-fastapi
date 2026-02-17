# hello-azure-fastapi
A production-ready FastAPI backend deployed to Azure Container Apps with automated CI/CD, containerized using Docker, and delivered securely through Azure Container Registry.

# LIVE DEMO
API : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io

Swagger Docs : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io/docs

Health Check : https://aca-hello-fastapi.politesand-7d1fea26.southeastasia.azurecontainerapps.io/health

# ARCHITECTURE OVERVIEW
<img width="341" height="233" alt="Screenshot 2026-02-17 at 4 36 21 PM" src="https://github.com/user-attachments/assets/9b662e49-4a06-42b3-a563-0c2e61b0e75f" />


# TECH STACK
- Python FastAPI
- Docker + Buildx
- GitHub Actions (CI/CD)
- Azure Container Registry (ACR)
- Azure Container Apps (ACA)
- Azure CLI
- Managed Identity + IAM (AcrPull)

# HOW IT WORKS
- Push code to main
- GitHub Actions builds Docker image
- Image pushed to ACR
- Azure Container App updates automatically
- New revision deployed live

# ENGINEERING CHALLENGES SOLVED
| Problem                           | Solution                         |
| --------------------------------- | -------------------------------- |
| ARM vs AMD image mismatch         | Used buildx multi-arch builds    |
| Container app couldn't pull image | Assigned AcrPull role            |
| Docker build context failed       | Fixed Dockerfile paths           |
| CI login failed                   | Corrected JSON secret formatting |

# PROJECT STRUCTURE
<img width="378" height="298" alt="Screenshot 2026-02-17 at 4 39 08 PM" src="https://github.com/user-attachments/assets/a56ccb30-72b1-4a6f-a0ed-3eed8ad5e78c" />


# GITHUB DEPLOYMENT SUCCESS
<img width="1410" height="477" alt="Screenshot 2026-02-17 at 4 00 24 PM" src="https://github.com/user-attachments/assets/f70392bf-6783-4e8c-9ffa-f79c6b8c74d8" />

# Azure Container App Oveview
<img width="1419" height="408" alt="Screenshot 2026-02-17 at 3 59 15 PM" src="https://github.com/user-attachments/assets/01674068-7ac7-4299-98b7-fcf00d3446a0" />
