# Kubernetes Nginx Application

A project that deploys an Nginx application on Kubernetes running on AWS EC2.

## Overview

This project provides the necessary configuration files and scripts to deploy an Nginx web server application using Kubernetes on an AWS EC2 instance. The deployment includes resource limits, replicas for high availability, and proper service configuration.

## AWS EC2 Configuration

- Instance Type: t2.medium (2 vCPU, 4 GiB Memory)
- AMI: Ubuntu Server 22.04 LTS (HVM)
- Storage: 20 GB gp2 SSD
- Security Group: Allow inbound traffic on ports 22 (SSH), 80 (HTTP), and 443 (HTTPS)
- Region: us-east-1

## Prerequisites

- AWS EC2 instance as specified above
- Ubuntu-based operating system
- Sudo privileges

## Installation

### 1. Install Docker

Run the Docker installation script:

```bash
chmod +x docker-install\ \(1\).sh
./docker-install\ \(1\).sh
```

### 2. Install kubectl

Run the kubectl installation script:

```bash
chmod +x install-kubectl.sh
./install-kubectl.sh
```

### 3. Deploy the Nginx Application

```bash
kubectl apply -f deployment.sh
kubectl apply -f service.yml
```

## Configuration Files

### Deployment Configuration

The `deployment.sh` file contains the Kubernetes Deployment configuration with:
- 3 replicas of Nginx
- Resource limits:
  - Memory: 128Mi (limit), 64Mi (request)
  - CPU: 500m (limit), 250m (request)
- Latest Nginx image

### Service Configuration

The `service.yml` file defines a ClusterIP service that:
- Exposes port 80
- Routes traffic to pods with the label `app: nginx-app`

## Verification

To verify the deployment:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

## License

See the [LICENSE](LICENSE) file for details.