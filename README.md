# Kubernetes Canary Deployment with K3s and Istio

## Project Overview
This project demonstrates a Canary Deployment strategy using Kubernetes (K3s) and Istio Service Mesh on AWS EC2.

Two application versions are deployed:
- V1: Stable Version
- V2: New Version

Istio VirtualService manages traffic distribution between the two versions.

## Tools and Technologies
- AWS EC2
- Ubuntu
- Kubernetes (K3s)
- Istio Service Mesh
- kubectl
- YAML

## Project Architecture
1. AWS EC2 hosts the K3s Kubernetes cluster.
2. Istio manages service-to-service communication and traffic routing.
3. Two application versions (V1 and V2) run as Kubernetes deployments.
4. DestinationRule defines subsets for V1 and V2.
5. VirtualService controls traffic distribution.
6. Istio Ingress Gateway exposes the application externally.

## Canary Deployment
Initial traffic distribution:
- V1: 80%
- V2: 20%

## Testing
- Verified that all application pods were running.
- Tested traffic distribution with 100 requests.
- Observed approximately 80% traffic to V1 and 20% to V2.
- Promoted V2 to receive 100% traffic.
- Verified that all requests reached V2.
- Performed rollback to V1 with 100% traffic.
- Verified that all requests reached V1 after rollback.

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
