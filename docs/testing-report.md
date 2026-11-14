# Testing Report

## Project
Kubernetes Canary Deployment with K3s and Istio

## Test 1: Application Deployment
- Deployed Application V1 and V2.
- Verified all application pods were running successfully.

## Test 2: Canary Traffic Distribution
- Configured an 80:20 traffic split.
- Internal test: 83 requests reached V1 and 17 reached V2.
- External test: 82 requests reached V1 and 18 reached V2.

## Test 3: Canary Promotion
- Promoted Application V2 to receive 100% traffic.
- Result: All 20 test requests reached V2.

## Test 4: Rollback
- Rolled back traffic to Application V1.
- Result: All 20 test requests reached V1.

## Conclusion
The canary deployment, traffic distribution, promotion, and rollback were successfully tested using K3s and Istio.
