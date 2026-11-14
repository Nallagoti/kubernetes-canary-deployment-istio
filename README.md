# Kubernetes Canary Deployment with K3s and Istio

## Project Overview
This project demonstrates a Canary Deployment strategy using Kubernetes (K3s) and Istio Service Mesh on AWS EC2.

Two application versions are deployed:
- V1: Stable Version
- V2: New Version

Istio VirtualService manages traffic distribution between the two versions, allowing controlled releases, promotion, and rollback.

## Tools and Technologies
- AWS EC2
- Ubuntu
- Kubernetes (K3s)
- Istio Service Mesh
- kubectl
- YAML

## Project Architecture
AWS EC2 hosts the K3s cluster. Istio Ingress Gateway receives external traffic and forwards it through the VirtualService. DestinationRule defines V1 and V2 subsets.

See the [Architecture Diagram](docs/architecture.md).

## Canary Deployment
Initial traffic distribution:
- V1: 80% (Stable)
- V2: 20% (Canary)

## Testing Results
- Verified all application pods were running.
- Internal test: 83 requests reached V1 and 17 reached V2.
- External test: 82 requests reached V1 and 18 reached V2.
- Promoted V2 to receive 100% traffic: 20/20 requests reached V2.
- Rolled back to V1: 20/20 requests reached V1.

Traffic distribution is approximate and can vary between test runs.

## Documentation
- [Architecture Diagram](docs/architecture.md)
- [Deployment Guide](docs/deployment-guide.md)
- [Testing Report](docs/testing-report.md)

## Project Files
- app.yaml: Application deployments and service.
- destination-rule.yaml: Defines V1 and V2 subsets.
- gateway.yaml: Istio ingress gateway configuration.
- virtual-service.yaml: Traffic routing configuration.
- virtual-service-canary-backup.yaml: Backup traffic configuration.

## Key Learning Outcomes
- Kubernetes deployment and service management.
- Istio service mesh configuration.
- Canary release strategy.
- Traffic splitting and version-based routing.
- Application promotion and rollback.

## Author
Nissitha Nallagoti  
DevOps Engineer | Fresher

## Screenshots

### 1. Kubernetes Pods
![Kubernetes Pods](docs/screenshots/Kubernetes-Pods.png)

### 2. Canary Traffic Configuration
![Traffic Configuration](docs/screenshots/Canary-Traffic-Configuration.png)

### 3. Canary Traffic Split
![Traffic Split](docs/screenshots/Canary-Traffic-Split.png)

### 4. Canary Promotion
![Canary Promotion](docs/screenshots/Canary-Promotion.png)

### 5. Canary Rollback
![Canary Rollback](docs/screenshots/Canary-Rollback.png)

### 6. GitHub Repository
![GitHub Repository](docs/screenshots/GitHub-Repository.png)
