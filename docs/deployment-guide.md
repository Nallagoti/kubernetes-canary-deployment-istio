# Deployment Guide

## Prerequisites
- AWS EC2 Ubuntu instance
- K3s Kubernetes
- Istio 1.32.0
- kubectl
- istioctl

## Step 1: Install K3s
curl -sfL https://get.k3s.io | sh -

## Step 2: Configure kubectl
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml

## Step 3: Install Istio
Download and extract Istio 1.32.0, then run:

istioctl install --set profile=default -y

## Step 4: Create Application Namespace
sudo kubectl create namespace canary
sudo kubectl label namespace canary istio-injection=enabled

## Step 5: Deploy Applications
sudo kubectl apply -f app.yaml
sudo kubectl apply -f destination-rule.yaml
sudo kubectl apply -f gateway.yaml
sudo kubectl apply -f virtual-service.yaml

## Step 6: Verify Deployment
sudo kubectl get pods -n canary
sudo kubectl get services -n canary
sudo kubectl get virtualservice -n canary

## Step 7: Test Traffic
Access the application through the EC2 public IP and configured Istio NodePort.

## Step 8: Canary Promotion and Rollback
Update VirtualService traffic weights to promote V2 or roll back to V1.
