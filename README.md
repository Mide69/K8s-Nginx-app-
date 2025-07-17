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

<img width="4" height="9" alt="Screenshot 2025-07-17 173736" src="https://github.com/user-attachments/assets/4733d2f7-ffae-43bb-a441-4538b6ea141d" />
<img width="1390" height="225" alt="Screenshot 2025-07-17 173750" src="https://github.com/user-attachments/assets/4f696a22-8def-4195-b04c-88363e35c2f4" />
<img width="1916" height="817" alt="Screenshot 2025-07-17 173912" src="https://github.com/user-attachments/assets/97521b89-2a7e-4c10-9535-70f8b13ddaa2" />
<img width="1896" height="1077" alt="Screenshot 2025-07-17 174015" src="https://github.com/user-attachments/assets/aa62d1f0-0fd8-4370-a154-9dfda0f670e7" />
<img width="1907" height="1006" alt="Screenshot 2025-07-17 180349" src="https://github.com/user-attachments/assets/2bc27234-af50-44c0-9f88-11f7306e3c62" />
<img width="1911" height="1012" alt="Screenshot 2025-07-17 180622" src="https://github.com/user-attachments/assets/42fed092-c01d-4b5e-95df-24237ad85e3c" />
<img width="1901" height="970" alt="Screenshot 2025-07-17 180725" src="https://github.com/user-attachments/assets/80ec7ac5-a9ef-44b9-b88d-fac2c1662a5a" />
<img width="1908" height="1004" alt="Screenshot 2025-07-17 180806" src="https://github.com/user-attachments/assets/134557e1-f460-4968-9c23-d8c0968c436d" />
<img width="1824" height="814" alt="Screenshot 2025-07-17 181529" src="https://github.com/user-attachments/assets/f603a775-0032-44ba-83f2-467b534bea3f" />
<img width="1918" height="1075" alt="Screenshot 2025-07-17 173033" src="https://github.com/user-attachments/assets/8fba4564-df08-4264-88a2-4589b00f5e51" />

