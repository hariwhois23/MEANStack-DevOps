# MEAN Stack Application Deployment 

---

## Steps

### **Phase 1: Containerization** 

#### 1. Create Dockerfiles
Create individual Dockerfiles for both frontend and backend applications to package all dependencies and application code into containers.

#### 2. Create Docker Compose Manifest
Build a docker-compose.yml file that orchestrates all services (MongoDB, Backend, Frontend) to work together seamlessly.

#### 3. Test Locally
Run `docker-compose up -d` to verify everything works locally before deployment.

---

### **Phase 2: AWS Setup** 

#### 1. Create EC2 Instance

**Instance Configuration:**
- Make sure the instance has a minimum required hardware and has an public IP and associated with a configured sercurity group.

#### 2. Connect to EC2
Use SSH to connect to your EC2 instance with your private key.

---

### **Phase 3: Server Setup** 

#### 1. Install Prerequisites
Install the following on your EC2 instance:
- **Docker**: Container runtime
- **Docker Compose**: Multi-container orchestration
- **Git**: Version control system
- **Nginx**: Web server and reverse proxy

#### 2. Clone Repository
Clone your project repository from GitHub to the EC2 instance.

#### 3. Deploy Application
Execute `docker-compose up -d` to start all services in detached mode.

---

### **Phase 4: Nginx Reverse Proxy** 

#### Configure Nginx
Set up Nginx as a reverse proxy
- The configuration steps are present in ./nginx-congig/README.md


---

### **Phase 5: CI/CD Pipeline Automation** 

#### 1. GitHub Actions Workflow
Create a workflow file that automatically:
- Triggers on push to main branch
- Builds Docker images for frontend and backend
- Pushes images to Docker Hub registry

#### 2. Configure GitHub Secrets
Set up secure credentials:
- Docker Hub username
- Docker Hub access token

#### 3. Pipeline Automation Flow

```
┌─────────────┐   ┌──────────────┐   ┌─────────────┐   ┌──────────────┐
│ Code Push   │──▶│ GitHub       │──▶│ Build       │──▶│ Push to      │
│ to main     │   │ Actions      │   │ Docker      │   │ Docker Hub   │
│ branch      │   │ Triggered    │   │ Images      │   │ Registry     │
└─────────────┘   └──────────────┘   └─────────────┘   └──────────────┘
```

---

##  Accessing the Application

### **Local Development:**
- Frontend: http://localhost:4200
- Backend API: http://localhost:3000
- Database: localhost:27017

### **Production (AWS EC2):**
- **Via Nginx Proxy**: http://your-ec2-public-ip

---
