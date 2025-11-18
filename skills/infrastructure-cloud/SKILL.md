---
name: infrastructure-cloud
description: Master cloud infrastructure, containerization with Docker, container orchestration with Kubernetes, and Infrastructure-as-Code with Terraform. Learn DevOps practices, CI/CD pipelines, and deployment strategies.
---

# Infrastructure & Cloud

## Quick Start

Cloud infrastructure automates deployment, scaling, and management of applications.

### Docker Container Basics:

```dockerfile
# Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

### Kubernetes Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-app:1.0
        ports:
        - containerPort: 8080
```

### Terraform Infrastructure:

```hcl
# main.tf
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "web-server"
  }
}
```

## Core Concepts

### 1. Container Technologies

#### Docker
- **Images**: Packaged application + dependencies
- **Containers**: Running instances of images
- **Registry**: Docker Hub, private registries
- **Networking**: Container-to-container communication
- **Volumes**: Persistent data storage
- **Multi-stage builds**: Optimize image size

#### Docker Compose
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "8000:8000"
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: secret
```

### 2. Container Orchestration

#### Kubernetes Architecture
- **Cluster**: Master + Worker nodes
- **Pods**: Smallest deployable unit
- **Services**: Expose pods to network
- **Deployments**: Manage pod replicas
- **StatefulSets**: For stateful applications
- **ConfigMaps & Secrets**: Configuration management

#### Key Kubernetes Resources
```yaml
# Service - expose pods
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
  type: LoadBalancer
```

### 3. Cloud Platforms

#### AWS Services
- **EC2**: Virtual machines
- **RDS**: Managed relational databases
- **S3**: Object storage
- **Lambda**: Serverless functions
- **CloudFormation**: Infrastructure-as-Code
- **VPC**: Virtual private network

#### Google Cloud & Azure
- Similar service offerings
- Different naming conventions
- Strengths in different areas

### 4. Infrastructure-as-Code

#### Terraform
- **Providers**: AWS, Azure, GCP, etc.
- **Resources**: Define infrastructure
- **Variables**: Input customization
- **Modules**: Reusable configurations
- **State Management**: Track current state

#### Benefits
- Version control for infrastructure
- Repeatable deployments
- Environment consistency
- Disaster recovery

### 5. CI/CD Pipelines

#### Pipeline Stages
```yaml
# GitHub Actions Example
name: CI/CD
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
      - name: Build Docker image
        run: docker build -t myapp .
      - name: Push to registry
        run: docker push myapp:latest
      - name: Deploy
        run: kubectl set image deployment/myapp myapp=myapp:latest
```

## Advanced Topics

### Monitoring & Logging
- Prometheus for metrics
- Grafana for visualization
- ELK Stack for log aggregation
- Alert management

### Security in Infrastructure
- Network policies
- RBAC (Role-Based Access Control)
- Secrets management
- Image scanning
- Pod security policies

### Scaling Strategies
- Horizontal Pod Autoscaling
- Vertical scaling
- Cluster autoscaling
- Load balancing

### Disaster Recovery
- Backup strategies
- Multi-region deployments
- Failover mechanisms
- RPO/RTO planning

## Real-World Projects

1. **Dockerize Application** - Create production-ready image
2. **Kubernetes Cluster** - Local or cloud cluster setup
3. **Terraform Infrastructure** - Deploy cloud resources
4. **CI/CD Pipeline** - Automated testing and deployment
5. **Multi-environment Setup** - Dev, staging, production

---

**Use this skill when:**
- Containerizing applications
- Setting up Kubernetes
- Learning Infrastructure-as-Code
- Building CI/CD pipelines
- Deploying to cloud
- Scaling applications
