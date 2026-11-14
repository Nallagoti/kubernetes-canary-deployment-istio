# Project Architecture

```mermaid
flowchart TD
    A[AWS EC2 - Ubuntu] --> B[K3s Kubernetes Cluster]
    B --> C[Istio Ingress Gateway]
    C --> D[Istio VirtualService]
    D -->|80% Traffic| E[Application V1 - Stable]
    D -->|20% Traffic| F[Application V2 - Canary]
    E --> G[Canary App Service]
    F --> G
    G --> H[DestinationRule]
## Traffic Management
- Initial deployment: V1 receives 80%, V2 receives 20%.
- Promotion: V2 receives 100% traffic.
- Rollback: V1 receives 100% traffic.
```
