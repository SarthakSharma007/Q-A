# 📘 DevOps Complete Interview Preparation Guide (2026 Edition)

> **Role Levels Covered:** Fresher · Junior · Intermediate Engineer  
> **Updated:** April 2026 | Based on real hiring patterns at top companies  
> **Difficulty:** 🟢 Easy · 🟡 Intermediate · 🔴 Advanced

---

## 📋 Table of Contents

### 🟢 Easy Level
- [1. Linux Basics](#1-linux-basics)
- [2. Networking Basics](#2-networking-basics)
- [3. Git & GitHub Basics](#3-git--github-basics)
- [4. CI/CD Basics](#4-cicd-basics)
- [5. Docker Basics](#5-docker-basics)
- [6. Cloud Basics](#6-cloud-basics)

### 🟡 Intermediate Level
- [7. Linux Intermediate](#7-linux-intermediate)
- [8. Networking Intermediate](#8-networking-intermediate)
- [9. Git Advanced Usage](#9-git-advanced-usage)
- [10. CI/CD – Jenkins & GitHub Actions](#10-cicd--jenkins--github-actions)
- [11. Docker Intermediate](#11-docker-intermediate)
- [12. Kubernetes Basics](#12-kubernetes-basics)
- [13. Infrastructure as Code – Terraform & Ansible](#13-infrastructure-as-code--terraform--ansible)
- [14. Monitoring – Prometheus & Grafana](#14-monitoring--prometheus--grafana)

### 🔴 Advanced Level
- [15. Kubernetes Advanced](#15-kubernetes-advanced)
- [16. Cloud – AWS / Azure / GCP](#16-cloud--aws--azure--gcp)
- [17. Security – DevSecOps](#17-security--devsecops)
- [18. System Design for DevOps](#18-system-design-for-devops)
- [19. Scenario-Based Questions](#19-scenario-based-questions)
- [20. Quick Reference Cheat Sheet](#20-quick-reference-cheat-sheet)

---

---

# 🟢 EASY LEVEL

---

## 1. Linux Basics

### Q1: What is Linux and why do DevOps engineers use it?

**Answer:**
- Linux is an open-source operating system modeled on UNIX
- Core components: Kernel, Shell, File System, Daemons
- DevOps engineers use Linux because it is:
  - Stable and reliable for servers
  - Free and open source
  - Highly customizable and scriptable
  - Used in almost all cloud servers (AWS EC2, GCP, Azure VMs)

---

### Q2: What is a process in Linux?

**Answer:**
- A process is a running instance of a program
- Each process has a unique **PID** (Process ID)
- It consumes system resources: CPU, memory, disk I/O
- Types:
  - **Foreground process** – runs in the terminal, takes user input
  - **Background process** – runs independently (`&` at end of command)
  - **Daemon process** – system service running in background (e.g., `nginx`, `sshd`)

---

### Q3: How do you list and manage running processes?

**Answer:**
```bash
# List all running processes
ps aux

# Real-time process monitoring
top
htop         # Better version of top (needs installation)

# Find a specific process
ps aux | grep nginx

# Kill a process by PID
kill 1234
kill -9 1234    # Force kill (cannot be ignored)

# Kill by name
pkill nginx
killall nginx
```

---

### Q4: What are Linux file permissions?

**Answer:**
- Every file has 3 permission groups: **Owner**, **Group**, **Others**
- Each group has 3 permissions: **read (r=4)**, **write (w=2)**, **execute (x=1)**

```bash
# View permissions
ls -la file.txt
# Output: -rwxr-xr-- → Owner=rwx(7), Group=r-x(5), Others=r--(4)

# Change permissions
chmod 755 file.txt      # Owner: full, Group: read+execute, Others: read+execute
chmod +x script.sh      # Add execute permission to all

# Change ownership
chown user:group file.txt
chown -R user:group /folder/   # Recursive
```

---

### Q5: What are common Linux commands every DevOps engineer must know?

**Answer:**
```bash
# Navigation
pwd                  # Print current directory
ls -la               # List files with details
cd /var/log          # Change directory

# File operations
cp file1.txt /tmp/   # Copy file
mv file1.txt file2.txt  # Rename/move
rm -rf /tmp/folder/  # Delete folder recursively
mkdir -p /opt/app    # Create nested directories
cat file.txt         # View file contents
tail -f /var/log/syslog  # Follow live logs
grep "ERROR" app.log  # Search inside file

# Disk & memory
df -h                # Disk usage
du -sh /var/log/*    # Folder sizes
free -h              # Memory usage

# Network
ping google.com      # Test connectivity
curl https://example.com  # HTTP request
wget https://file.zip     # Download file
netstat -tulpn       # Open ports

# System info
uname -a             # OS info
uptime               # System uptime
whoami               # Current user
```

---

### Q6: What is SSH and how do you use it?

**Answer:**
- SSH (Secure Shell) is a protocol to securely connect to remote servers
- Uses encrypted communication over port 22

```bash
# Connect to a remote server
ssh user@192.168.1.10
ssh -i key.pem ubuntu@54.123.45.67  # Using a key file

# Copy file to remote server
scp file.txt user@server:/tmp/

# Copy file from remote server
scp user@server:/tmp/file.txt ./local/

# Generate SSH key pair
ssh-keygen -t rsa -b 4096
```

---

## 2. Networking Basics

### Q1: What is DNS and how does it work?

**Answer:**
- DNS (Domain Name System) translates domain names to IP addresses
- Like a phone book for the internet
- Flow: `Browser → DNS Resolver → Root Server → TLD Server → Authoritative DNS → IP returned`

```bash
# Look up a domain's IP
nslookup google.com
dig google.com
host google.com
```

---

### Q2: What is the difference between TCP and UDP?

**Answer:**

| Feature | TCP | UDP |
|---|---|---|
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Guaranteed delivery | No guarantee |
| **Speed** | Slower | Faster |
| **Use cases** | HTTP, SSH, FTP, Email | DNS, Video streaming, Gaming |
| **Error checking** | Yes | Minimal |

---

### Q3: What is a Load Balancer?

**Answer:**
- A load balancer distributes incoming traffic across multiple servers
- Prevents any single server from being overloaded
- Types:
  - **Layer 4 (Transport)** – routes based on IP and TCP/UDP port
  - **Layer 7 (Application)** – routes based on HTTP content (URL, headers)
- Examples: AWS ALB (Application Load Balancer), Nginx, HAProxy

---

### Q4: What is the difference between HTTP and HTTPS?

**Answer:**
- **HTTP** – Hypertext Transfer Protocol, port 80, plain text (not secure)
- **HTTPS** – HTTP + SSL/TLS encryption, port 443, data is encrypted
- HTTPS uses:
  - **SSL/TLS certificates** to verify the server's identity
  - Encryption to protect data in transit (passwords, payment info)
- Always use HTTPS in production environments

---

### Q5: What is a Firewall and how does it work?

**Answer:**
- A firewall controls incoming and outgoing network traffic based on rules
- Acts as a barrier between trusted internal network and untrusted external networks
- Types:
  - **Network firewall** – filters traffic at network level (iptables, AWS Security Groups)
  - **Application firewall (WAF)** – filters HTTP traffic (AWS WAF, Cloudflare)

```bash
# Check firewall rules on Linux
iptables -L -n -v

# Allow port 80 (HTTP)
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# Allow SSH (port 22)
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

---

## 3. Git & GitHub Basics

### Q1: What is Git and why is it used?

**Answer:**
- Git is a **distributed version control system** that tracks code changes
- Every developer has the **full project history** on their local machine
- Can work offline, create branches, and merge code safely
- Benefits:
  - Track every change with author, date, and message
  - Roll back to any previous version
  - Collaborate with teams without overwriting each other's work

---

### Q2: What is the difference between Git and GitHub?

**Answer:**

| Git | GitHub |
|---|---|
| A version control tool installed locally | A cloud-based platform to host Git repositories |
| Works offline | Requires internet |
| Command-line tool | Has a web UI + API |
| Open source project | Owned by Microsoft |

- Other similar platforms: **GitLab**, **Bitbucket**, **Azure Repos**

---

### Q3: What are the basic Git commands?

**Answer:**
```bash
# Setup
git config --global user.name "Your Name"
git config --global user.email "you@email.com"

# Start a project
git init                    # Initialize a new repo
git clone <repo-url>        # Copy a remote repo locally

# Daily workflow
git status                  # See what changed
git add file.txt            # Stage a file
git add .                   # Stage all changes
git commit -m "Add login feature"  # Save changes

# Remote operations
git push origin main        # Push to remote
git pull origin main        # Pull latest changes
git fetch                   # Download without merging

# Branching
git branch feature-login    # Create a branch
git checkout feature-login  # Switch to branch
git checkout -b feature-x   # Create and switch in one step
git merge feature-login     # Merge branch into current branch

# History
git log --oneline           # Short commit history
git diff                    # See changes not yet staged
```

---

### Q4: What is a Pull Request (PR)?

**Answer:**
- A Pull Request is a request to merge code from one branch into another
- Used to review code before merging into the main branch
- PR workflow:
  1. Developer creates a feature branch
  2. Pushes changes to GitHub
  3. Opens a Pull Request against `main`
  4. Team reviews the code, leaves comments
  5. After approval, the PR is merged

---

### Q5: What is `.gitignore` and why is it important?

**Answer:**
- `.gitignore` tells Git which files to **not track**
- Prevents sensitive or unnecessary files from being committed

```gitignore
# Example .gitignore
node_modules/        # Dependencies folder
.env                 # Environment variables (NEVER commit this!)
*.log                # Log files
.DS_Store            # Mac system file
dist/                # Build output
__pycache__/         # Python cache
*.tfstate            # Terraform state files
```

---

## 4. CI/CD Basics

### Q1: What is CI/CD and why is it important?

**Answer:**
- **CI (Continuous Integration):** Developers push code frequently; automated builds and tests run on every commit
- **CD (Continuous Delivery):** Code is always ready to deploy; release needs a manual trigger
- **CD (Continuous Deployment):** Every passing build is automatically deployed to production
- Why important:
  - Catches bugs early (cheaper to fix)
  - Reduces manual deployment errors
  - Delivers features to users faster

---

### Q2: What is a CI/CD pipeline?

**Answer:**
- A pipeline is a series of automated steps that code goes through before reaching production
- Typical stages:
  1. **Source** – Developer pushes code to Git
  2. **Build** – Compile/package the application
  3. **Test** – Run unit tests, integration tests
  4. **Scan** – Security and code quality checks
  5. **Deploy** – Push to staging, then production
  6. **Monitor** – Watch for errors after deployment

---

### Q3: What is Jenkins?

**Answer:**
- Jenkins is a popular open-source automation server for CI/CD
- Written in Java, runs on any server
- Features:
  - 1800+ plugins for integration with Git, Docker, Kubernetes, etc.
  - Pipelines defined in `Jenkinsfile` (code as pipeline)
  - Supports parallel jobs and distributed builds
- Alternative tools: GitHub Actions, GitLab CI, CircleCI, ArgoCD

---

### Q4: What is GitHub Actions?

**Answer:**
- GitHub Actions is a CI/CD tool built directly into GitHub
- Workflows are defined in `.github/workflows/*.yml` files
- Runs automatically on events: push, pull request, schedule

```yaml
# Example: .github/workflows/deploy.yml
name: Build and Test

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run Tests
        run: npm test
      - name: Build Docker Image
        run: docker build -t myapp:latest .
```

---

## 5. Docker Basics

### Q1: What is Docker and what problem does it solve?

**Answer:**
- Docker is a platform for building and running **containers**
- Solves the "it works on my machine" problem
- Packages an application with ALL its dependencies into one portable unit
- That unit (container) runs identically on any machine — laptop, server, or cloud

---

### Q2: What is the difference between a container and a virtual machine?

**Answer:**

| Feature | Container | Virtual Machine |
|---|---|---|
| **OS** | Shares host OS kernel | Has its own full OS |
| **Size** | Megabytes | Gigabytes |
| **Startup** | Seconds | Minutes |
| **Isolation** | Process-level | Hardware-level |
| **Performance** | Near-native | Overhead from hypervisor |

---

### Q3: What is a Dockerfile?

**Answer:**
- A Dockerfile is a text file with instructions to build a Docker image
- Each instruction creates a layer in the image

```dockerfile
# Simple Node.js app Dockerfile
FROM node:18-alpine          # Base image

WORKDIR /app                 # Set working directory

COPY package*.json ./        # Copy dependency files first (for caching)
RUN npm install              # Install dependencies

COPY . .                     # Copy app source code

EXPOSE 3000                  # Document the port

CMD ["node", "server.js"]    # Default command to run
```

---

### Q4: What are the most common Docker commands?

**Answer:**
```bash
# Images
docker build -t myapp:1.0 .        # Build image from Dockerfile
docker images                       # List local images
docker pull nginx                   # Download image from Docker Hub
docker rmi myapp:1.0                # Remove image

# Containers
docker run -d -p 8080:80 nginx      # Run container in background
docker run -it ubuntu bash          # Interactive container
docker ps                           # List running containers
docker ps -a                        # List all containers (including stopped)
docker stop <container-id>          # Stop a container
docker rm <container-id>            # Delete a container
docker logs <container-id>          # View container logs
docker logs -f <container-id>       # Follow live logs
docker exec -it <id> bash           # Enter a running container

# Cleanup
docker system prune                 # Remove unused resources
```

---

### Q5: What is Docker Hub?

**Answer:**
- Docker Hub is the default public registry for Docker images
- Like GitHub but for Docker images
- Contains official images for: `nginx`, `mysql`, `node`, `python`, `ubuntu`, etc.
- You can push your own images:

```bash
# Login and push image
docker login
docker tag myapp:1.0 username/myapp:1.0
docker push username/myapp:1.0
```

---

## 6. Cloud Basics

### Q1: What is cloud computing?

**Answer:**
- Cloud computing delivers IT resources over the internet on demand
- You pay only for what you use (pay-as-you-go)
- Types:
  - **IaaS (Infrastructure as a Service)** – Rent servers, storage (AWS EC2, Azure VMs)
  - **PaaS (Platform as a Service)** – Managed platforms for apps (Heroku, AWS Elastic Beanstalk)
  - **SaaS (Software as a Service)** – Ready-to-use apps (Gmail, Slack, Salesforce)

---

### Q2: What is AWS and what are its core services for DevOps?

**Answer:**
- AWS (Amazon Web Services) is the world's largest cloud provider
- Core DevOps services:

| Service | Purpose |
|---|---|
| EC2 | Virtual servers (compute) |
| S3 | Object storage |
| VPC | Private network in cloud |
| IAM | Identity & access management |
| EKS | Managed Kubernetes |
| ECS | Managed Docker containers |
| CodePipeline | CI/CD pipeline |
| CloudWatch | Monitoring and logging |
| Secrets Manager | Store sensitive credentials |

---

### Q3: What is the difference between scaling up and scaling out?

**Answer:**
- **Vertical Scaling (Scale Up):** Add more power to an existing machine (bigger CPU, more RAM)
  - Limit: maximum hardware capacity
  - Example: Change EC2 from `t3.small` to `t3.xlarge`

- **Horizontal Scaling (Scale Out):** Add more machines/instances
  - No hard limit — can keep adding servers
  - Example: AWS Auto Scaling Group adds more EC2 instances during traffic spikes

> In DevOps, **horizontal scaling** is preferred because it avoids single points of failure.

---

---

# 🟡 INTERMEDIATE LEVEL

---

## 7. Linux Intermediate

### Q1: What is systemd and how do you manage services?

**Answer:**
- `systemd` is the system and service manager for modern Linux systems
- It starts and controls services/daemons on boot

```bash
# Service management
systemctl start nginx          # Start service
systemctl stop nginx           # Stop service
systemctl restart nginx        # Restart service
systemctl reload nginx         # Reload config without restart
systemctl enable nginx         # Start on boot
systemctl disable nginx        # Disable on boot
systemctl status nginx         # Check service status

# View logs for a service
journalctl -u nginx            # All logs
journalctl -u nginx -f         # Follow live logs
journalctl -u nginx --since "1 hour ago"
```

---

### Q2: How do you troubleshoot high CPU usage on a Linux server?

**Answer:**
```bash
# Step 1: Find which process is using most CPU
top                            # Press 'P' to sort by CPU
htop                           # Visual version

# Step 2: Get more details about the process
ps aux --sort=-%cpu | head -10
ps aux | grep <Pid>

# Step 3: Check if it's a runaway loop or normal
strace -p <PID>               # Trace system calls of process

# Step 4: Check recent system changes
last                           # Login history
journalctl --since "1 hour ago"  # System events

# Step 5: Kill if necessary
kill -9 <PID>
```

---

### Q3: What is a cron job and how do you create one?

**Answer:**
- A cron job is a scheduled task that runs automatically at set times
- Managed by the `cron` daemon

```bash
# Edit cron jobs for current user
crontab -e

# Cron format: minute hour day month weekday command
# ┌──────── minute (0-59)
# │ ┌────── hour (0-23)
# │ │ ┌──── day of month (1-31)
# │ │ │ ┌── month (1-12)
# │ │ │ │ ┌ day of week (0=Sunday)
# │ │ │ │ │
  * * * * * /path/to/command

# Examples:
0 2 * * * /scripts/backup.sh             # Run daily at 2 AM
*/5 * * * * /scripts/health-check.sh     # Every 5 minutes
0 0 * * 1 /scripts/weekly-report.sh      # Every Monday at midnight

# List cron jobs
crontab -l
```

---

### Q4: What is LVM (Logical Volume Manager)?

**Answer:**
- LVM provides **flexible disk space management**
- You can resize volumes without unmounting or rebooting
- Key components:
  - **PV (Physical Volume)** – Physical disk or partition
  - **VG (Volume Group)** – Pool of physical volumes
  - **LV (Logical Volume)** – Virtual partition created from VG

```bash
# Extend a logical volume by 10GB
lvextend -L +10G /dev/vg01/lv_data
resize2fs /dev/vg01/lv_data   # Resize filesystem (ext4)
```

---

## 8. Networking Intermediate

### Q1: What is a VPC (Virtual Private Cloud)?

**Answer:**
- A VPC is a private, isolated network section in the cloud (AWS, GCP, Azure)
- You control IP address ranges, subnets, routing, and security
- Key components:
  - **Subnet** – A range of IP addresses within the VPC (public or private)
  - **Internet Gateway** – Allows public internet access
  - **NAT Gateway** – Allows private subnets to access internet (outbound only)
  - **Route Table** – Defines traffic routing rules
  - **Security Group** – Acts as virtual firewall for EC2 instances

---

### Q2: What is the difference between a Security Group and NACL (Network ACL) in AWS?

**Answer:**

| | Security Group | Network ACL (NACL) |
|---|---|---|
| **Level** | Instance level | Subnet level |
| **State** | Stateful | Stateless |
| **Rules** | Allow only | Allow and Deny |
| **Evaluation** | All rules evaluated | Rules evaluated in order |
| **Default** | Deny all inbound | Allow all |

---

### Q3: How does a request travel from browser to a web server?

**Answer:**
1. User types `https://example.com` in browser
2. Browser checks local DNS cache
3. DNS resolver queries root → TLD → authoritative DNS server
4. DNS returns IP address of the server
5. Browser opens a **TCP connection** (3-way handshake) to port 443
6. **TLS/SSL handshake** happens for HTTPS
7. Browser sends HTTP GET request
8. Request may hit a **Load Balancer** first
9. Load balancer forwards to a backend server (EC2 / Pod)
10. Server processes and sends back the response

---

## 9. Git Advanced Usage

### Q1: What is the difference between `git merge` and `git rebase`?

**Answer:**
- **`git merge`** → Creates a new "merge commit" combining two branches. Preserves full history.
- **`git rebase`** → Replays commits on top of another branch. Creates clean, linear history.

```bash
# Merge approach (preserves history)
git checkout main
git merge feature-branch    # Creates a merge commit

# Rebase approach (clean history)
git checkout feature-branch
git rebase main             # Replays feature commits on top of main
git checkout main
git merge feature-branch    # Now it's a fast-forward merge
```

> Use `merge` for `main`/`develop` branches to keep audit trail.  
> Use `rebase` for feature branches to keep history clean before merging.

---

### Q2: What is `git stash` and when would you use it?

**Answer:**
- `git stash` temporarily saves uncommitted changes without committing them
- Useful when you need to switch branches urgently without losing work

```bash
git stash                    # Save current changes
git stash list               # See all stashes
git stash pop                # Restore latest stash and delete it
git stash apply stash@{1}    # Restore specific stash (keep it)
git stash drop stash@{0}     # Delete a stash
git stash clear              # Delete all stashes
```

---

### Q3: How do you undo a commit that has already been pushed?

**Answer:**
```bash
# Safe way: create a new commit that reverses the changes
git revert <commit-hash>
git push origin main

# Risky way: rewrite history (never do on shared branches!)
git reset --hard <commit-hash>
git push --force origin branch-name
```

> Always prefer `git revert` on shared branches.  
> `git reset --force` rewrites history and breaks other developers' copies.

---

### Q4: What are Git branching strategies?

**Answer:**

| Strategy | Description | Best For |
|---|---|---|
| **Git Flow** | `main`, `develop`, `feature/*`, `release/*`, `hotfix/*` | Scheduled, versioned releases |
| **GitHub Flow** | `main` + short-lived feature branches | Continuous deployment |
| **Trunk-Based Dev** | Everyone commits directly to `main`, use feature flags | High-velocity CI/CD teams |

---

## 10. CI/CD – Jenkins & GitHub Actions

### Q1: How does a Jenkinsfile pipeline work?

**Answer:**
- A `Jenkinsfile` defines the CI/CD pipeline as code
- Lives in the root of your Git repository

```groovy
// Declarative Pipeline Example
pipeline {
    agent any
    
    environment {
        IMAGE_NAME = "myapp"
        REGISTRY   = "docker.io/myusername"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/org/repo.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Docker Build & Push') {
            steps {
                sh "docker build -t ${REGISTRY}/${IMAGE_NAME}:${BUILD_NUMBER} ."
                sh "docker push ${REGISTRY}/${IMAGE_NAME}:${BUILD_NUMBER}"
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                sh "kubectl set image deployment/myapp myapp=${REGISTRY}/${IMAGE_NAME}:${BUILD_NUMBER}"
            }
        }
    }
    
    post {
        failure {
            slackSend message: "Build FAILED: ${env.JOB_NAME} - ${env.BUILD_URL}"
        }
        success {
            slackSend message: "Build PASSED: ${env.JOB_NAME}"
        }
    }
}
```

---

### Q2: What are GitHub Actions secrets and how are they used?

**Answer:**
- Secrets are encrypted values stored in GitHub Settings → Secrets
- Used to store API keys, passwords, tokens — never hardcode these in workflows

```yaml
# Using secrets in a GitHub Actions workflow
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Configure AWS
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
      
      - name: Deploy to EKS
        run: kubectl apply -f k8s/deployment.yaml
```

---

### Q3: What is a self-hosted runner in GitHub Actions?

**Answer:**
- A **self-hosted runner** is a server you control that runs GitHub Actions jobs
- Instead of using GitHub's cloud machines, jobs run on your own infrastructure
- Use when:
  - Jobs need access to internal network resources
  - You need specific hardware (GPU, more RAM)
  - Reducing GitHub Actions billing costs
  - Compliance requires code not to leave your environment

---

## 11. Docker Intermediate

### Q1: What is Docker Compose and when do you use it?

**Answer:**
- Docker Compose is a tool to define and run **multi-container applications**
- Uses a `docker-compose.yml` file to define all services

```yaml
# docker-compose.yml example: Web app + database
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8080:80"
    environment:
      - DATABASE_URL=postgres://user:pass@db:5432/mydb
    depends_on:
      - db
    volumes:
      - ./app:/app

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

```bash
docker compose up -d         # Start all services in background
docker compose down          # Stop and remove containers
docker compose logs -f web   # Follow logs of web service
docker compose ps            # List running services
```

---

### Q2: What is a multi-stage Docker build and why use it?

**Answer:**
- Multi-stage builds let you use multiple `FROM` statements in one Dockerfile
- Final image only contains the runtime output — not the build tools

```dockerfile
# Stage 1: Build the application
FROM maven:3.9 AS builder
WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline      # Cache dependencies
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Lightweight runtime image
FROM openjdk:17-jre-slim
WORKDIR /app
COPY --from=builder /build/target/app.jar app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
```

- **Result:** Final image is ~200MB instead of ~800MB
- Fewer security vulnerabilities because build tools are not included

---

### Q3: How do you optimize Docker image size?

**Answer:**
- Use a small base image: `alpine`, `slim`, `distroless`
- Use multi-stage builds
- Clean up in the same `RUN` layer:

```dockerfile
# ❌ Bad: leaves cache behind
RUN apt-get update
RUN apt-get install -y curl

# ✅ Good: cleans up in same layer
RUN apt-get update && \
    apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*
```

- Order instructions so frequently changing ones come last (maximizes cache hits)
- Use `.dockerignore` to exclude unnecessary files

---

## 12. Kubernetes Basics

### Q1: What is Kubernetes and why is it needed?

**Answer:**
- Kubernetes (K8s) is an open-source **container orchestration platform**
- Originally created by Google, now maintained by CNCF
- Solves the problem of managing containers at scale:
  - Automatically deploys and restarts failed containers
  - Scales up/down based on traffic
  - Load balances traffic across replicas
  - Provides self-healing infrastructure

---

### Q2: What are the main components of Kubernetes?

**Answer:**

**Control Plane (Master Node):**
- `kube-apiserver` – Front door to Kubernetes; all kubectl commands go here
- `etcd` – Distributed key-value store; stores cluster state
- `kube-scheduler` – Assigns pods to nodes
- `kube-controller-manager` – Maintains desired state (restarts failed pods, etc.)

**Worker Node:**
- `kubelet` – Agent that runs on each node; communicates with control plane
- `kube-proxy` – Manages network rules for pod communication
- `Container Runtime` – Runs containers (containerd, CRI-O)

---

### Q3: What are the key Kubernetes objects?

**Answer:**

| Object | Purpose |
|---|---|
| **Pod** | Smallest unit; 1 or more containers sharing network + storage |
| **Deployment** | Manages stateless app replicas; handles rolling updates |
| **Service** | Stable endpoint to access pods; provides load balancing |
| **ConfigMap** | Store non-sensitive configuration data |
| **Secret** | Store sensitive data (passwords, tokens) |
| **Namespace** | Virtual cluster; isolates resources by team/environment |
| **Ingress** | Routes external HTTP traffic to services |
| **PersistentVolume** | Storage that survives pod restarts |

---

### Q4: What are the most important `kubectl` commands?

**Answer:**
```bash
# Get resources
kubectl get pods                         # List pods
kubectl get pods -n kube-system          # Pods in specific namespace
kubectl get all                          # List everything
kubectl get nodes                        # List cluster nodes

# Inspect
kubectl describe pod <pod-name>          # Detailed pod info + events
kubectl logs <pod-name>                  # View pod logs
kubectl logs <pod-name> --previous       # Logs from crashed pod
kubectl logs <pod-name> -f               # Follow live logs

# Deployments
kubectl apply -f deployment.yaml         # Create/update from file
kubectl delete -f deployment.yaml        # Delete from file
kubectl rollout status deployment/myapp  # Watch rollout progress
kubectl rollout undo deployment/myapp    # Roll back to previous version
kubectl scale deployment myapp --replicas=5  # Scale up/down

# Debugging
kubectl exec -it <pod-name> -- bash      # Shell into a pod
kubectl port-forward pod/<name> 8080:80  # Forward local port to pod
kubectl top pods                         # CPU/memory usage
kubectl top nodes                        # Node resource usage
```

---

## 13. Infrastructure as Code – Terraform & Ansible

### Q1: What is Infrastructure as Code (IaC)?

**Answer:**
- IaC is the practice of managing infrastructure through **code** instead of manual steps
- Infrastructure is defined in files (like code) and version-controlled in Git
- Benefits:
  - **Consistent environments** – No "it works on staging but not prod"
  - **Reproducible** – Spin up identical environments in minutes
  - **Version controlled** – Track changes, roll back anytime
  - **Automated** – No manual clicking in cloud console

---

### Q2: What are Terraform's core commands?

**Answer:**
```bash
terraform init       # Initialize project, download providers
terraform validate   # Check configuration syntax
terraform plan       # Preview changes (dry run)
terraform apply      # Provision infrastructure
terraform destroy    # Destroy all managed resources

terraform fmt        # Auto-format .tf files
terraform state list # List tracked resources
terraform output     # Show output values
```

---

### Q3: What is Terraform state and why is it important?

**Answer:**
- Terraform state (`terraform.tfstate`) maps your `.tf` code to real-world resources
- Without state, Terraform would try to create everything from scratch every time
- **Store state remotely** (never on local machine or in Git):

```hcl
# Remote state using AWS S3 + DynamoDB for locking
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "production/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-state-locks"
    encrypt        = true
  }
}
```

---

### Q4: What is Ansible and how is it different from Terraform?

**Answer:**

| | Terraform | Ansible |
|---|---|---|
| **Purpose** | Create/destroy infrastructure | Configure and manage servers |
| **When** | Day 0: Provisioning | Day 1 & 2: Configuration |
| **Approach** | Declarative | Procedural (playbooks) |
| **State** | Tracks state file | Stateless |
| **Agents** | None needed | None needed (uses SSH) |

> Smart answer: **"Terraform for Day 0 (create the infrastructure), Ansible for Day 1 and Day 2 (configure it)."**

---

### Q5: Show a simple Ansible playbook example.

**Answer:**
```yaml
# playbook.yml - Install and start Nginx
---
- name: Configure web servers
  hosts: webservers
  become: yes          # Run with sudo

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start and enable Nginx
      systemd:
        name: nginx
        state: started
        enabled: yes

    - name: Copy website config
      template:
        src: templates/nginx.conf.j2
        dest: /etc/nginx/sites-available/mysite.conf
      notify: Reload Nginx

  handlers:
    - name: Reload Nginx
      systemd:
        name: nginx
        state: reloaded
```

```bash
# Run the playbook
ansible-playbook -i inventory.ini playbook.yml
```

---

## 14. Monitoring – Prometheus & Grafana

### Q1: What is the difference between monitoring and observability?

**Answer:**
- **Monitoring:** Tells you *when* something is wrong. Uses predefined metrics and alerts.
- **Observability:** Tells you *why* something is wrong. Gives you insight into internal system state.

**Three pillars of observability:**
- **Metrics** – Numbers over time (CPU%, request rate, error rate)
- **Logs** – Text records of events (application logs, system logs)
- **Traces** – End-to-end request tracking across microservices

---

### Q2: What is Prometheus and how does it work?

**Answer:**
- Prometheus is an open-source **metrics collection and alerting** tool
- Works by **scraping** (pulling) metrics from HTTP endpoints at regular intervals
- Stores data as time-series

```yaml
# prometheus.yml - basic config
global:
  scrape_interval: 15s        # Scrape every 15 seconds

scrape_configs:
  - job_name: 'my-app'
    static_configs:
      - targets: ['localhost:8080']   # App exposes /metrics here

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['localhost:9100']   # Node metrics

alerting:
  alertmanagers:
    - static_configs:
        - targets: ['localhost:9093']
```

---

### Q3: What is Grafana and how does it relate to Prometheus?

**Answer:**
- Grafana is an **open-source visualization platform**
- It does NOT collect data itself — it **reads from data sources** like:
  - Prometheus (most common)
  - Elasticsearch, InfluxDB, MySQL, CloudWatch
- Used to build dashboards with graphs, heatmaps, alerts, and tables
- Typical setup: **Prometheus collects → Grafana visualizes**

---

### Q4: What is the ELK Stack?

**Answer:**
- **E**lasticsearch – Stores, indexes, and searches logs at scale
- **L**ogstash – Collects, parses, and transforms logs from multiple sources
- **K**ibana – Visualizes log data; search and create dashboards

```
Application → Filebeat (ships logs) → Logstash (parse/filter) → Elasticsearch (store) → Kibana (visualize)
```

- Common alternative: **EFK Stack** (replaces Logstash with **Fluent Bit** — lighter weight)

---

---

# 🔴 ADVANCED LEVEL

---

## 15. Kubernetes Advanced

### Q1: What is the difference between a Deployment and a StatefulSet?

**Answer:**

| Feature | Deployment | StatefulSet |
|---|---|---|
| **Use case** | Stateless apps (web, API) | Stateful apps (databases, queues) |
| **Pod identity** | Interchangeable, random names | Stable, ordered names (pod-0, pod-1, pod-2) |
| **Storage** | Shared or none | Individual PersistentVolumeClaim per pod |
| **Scaling order** | Any order | Ordered (scale up: 0→1→2, scale down: 2→1→0) |
| **Examples** | Nginx, React, REST APIs | MySQL, Kafka, Redis, Zookeeper |

---

### Q2: What is Kubernetes RBAC and why is it important?

**Answer:**
- RBAC (Role-Based Access Control) controls who can do what in Kubernetes
- Principle: give only the **minimum permissions needed**

```yaml
# Role: can only read pods in "production" namespace
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: production
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list", "watch"]

---
# Bind role to a user
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: production
subjects:
- kind: User
  name: jane
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

---

### Q3: What are Kubernetes Taints, Tolerations, and Node Affinity?

**Answer:**

- **Taint** – Marks a node so that pods are **repelled** from it unless they tolerate the taint
- **Toleration** – Allows a pod to be scheduled on a tainted node
- **Node Affinity** – Attracts pods to specific nodes based on node labels

```yaml
# Taint a node (only ML pods should run here)
# kubectl taint nodes gpu-node type=gpu:NoSchedule

# Pod with toleration (allowed on the tainted node)
spec:
  tolerations:
  - key: "type"
    operator: "Equal"
    value: "gpu"
    effect: "NoSchedule"
  
  # Also use affinity to PREFER that node
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: type
            operator: In
            values:
            - gpu
```

---

### Q4: What is Helm and why is it used?

**Answer:**
- Helm is the **package manager for Kubernetes**
- A "Helm chart" is a collection of Kubernetes YAML templates with configurable values
- Instead of editing 10+ YAML files, you pass a `values.yaml` file

```bash
# Install a chart from Helm Hub
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-postgres bitnami/postgresql

# Deploy your own app with Helm
helm install my-app ./my-chart -f custom-values.yaml

# Upgrade
helm upgrade my-app ./my-chart --set image.tag=2.0

# Rollback
helm rollback my-app 1
```

---

### Q5: What is the Kubernetes Horizontal Pod Autoscaler (HPA)?

**Answer:**
- HPA automatically scales the number of pod replicas based on metrics
- Default metric: CPU usage. Can also use memory, custom metrics.

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: myapp-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: myapp
  minReplicas: 2
  maxReplicas: 20
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70    # Scale up when CPU > 70%
```

---

## 16. Cloud – AWS / Azure / GCP

### Q1: What is the AWS Shared Responsibility Model?

**Answer:**
- AWS and the customer share security responsibilities

| AWS Responsible For | Customer Responsible For |
|---|---|
| Physical data centers | Data encryption |
| Hardware (servers, networking) | IAM users and permissions |
| Hypervisor and virtualization | OS patching on EC2 |
| Managed services (RDS patching) | Application security |
| Network infrastructure | Firewall rules (Security Groups) |

> Remember: **"Security of the cloud" (AWS) vs "Security in the cloud" (you)**

---

### Q2: What is the difference between AWS ECS and EKS?

**Answer:**

| | ECS | EKS |
|---|---|---|
| **Orchestration** | AWS-native (proprietary) | Kubernetes (open standard) |
| **Complexity** | Simpler | More complex but more powerful |
| **Portability** | AWS only | Multi-cloud portable |
| **Control plane cost** | Free | $0.10/hour |
| **Best for** | AWS-first teams | K8s expertise, multi-cloud |

---

### Q3: How do you design a highly available architecture in AWS?

**Answer:**
- Deploy across **multiple Availability Zones (AZs)** — at least 2
- Use **Application Load Balancer (ALB)** to distribute traffic
- Use **Auto Scaling Group** to replace failed instances automatically
- Use **RDS Multi-AZ** for database failover
- Use **S3** for static assets (99.999999999% durability)
- Use **CloudFront** CDN for global performance
- Set up **CloudWatch alarms** + SNS notifications

```
Internet
    ↓
Route 53 (DNS)
    ↓
CloudFront (CDN)
    ↓
ALB (Load Balancer)
  ↙           ↘
AZ-1 EC2    AZ-2 EC2   ← Auto Scaling Group
  ↓               ↓
RDS Primary ← ← RDS Replica (Multi-AZ)
```

---

## 17. Security – DevSecOps

### Q1: What is DevSecOps?

**Answer:**
- DevSecOps integrates security into **every stage** of the DevOps pipeline
- Security is not a gate at the end — it is a shared responsibility throughout
- Key principle: **Shift Left** — catch security issues earlier (cheaper to fix)

**Security at each CI/CD stage:**

| Stage | Security Action |
|---|---|
| Code | Pre-commit hooks: detect secrets (git-secrets, truffleHog) |
| Build | SAST: static code analysis (SonarQube, Snyk) |
| Test | DAST: dynamic testing against running app (OWASP ZAP) |
| Package | Container image scanning (Trivy, Clair) |
| Deploy | IaC scanning (tfsec, checkov for Terraform) |
| Runtime | Runtime threat detection (Falco for Kubernetes) |

---

### Q2: How do you manage secrets securely in a DevOps pipeline?

**Answer:**

**Never do:**
- Hardcode passwords in code
- Store secrets in `.env` files committed to Git
- Pass secrets as plain environment variables in Dockerfiles

**Always do:**
- Use a dedicated secrets manager:
  - **HashiCorp Vault**
  - **AWS Secrets Manager**
  - **Azure Key Vault**
- Inject secrets at runtime (not build time)
- Rotate secrets regularly
- Scan git history for leaked secrets

```bash
# Detect secrets in git history
truffleHog --regex --entropy=False https://github.com/org/repo

# Retrieve a secret from AWS Secrets Manager
aws secretsmanager get-secret-value \
    --secret-id prod/myapp/db-password \
    --query SecretString --output text
```

---

### Q3: What is container security and how do you harden Docker containers?

**Answer:**
- Use official, minimal base images (`alpine`, `distroless`)
- Keep images updated and scan for CVEs (Trivy)
- Never run containers as root:

```dockerfile
# Add a non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser          # Switch to non-root user
```

- Use read-only filesystems where possible:
```bash
docker run --read-only myapp
```

- Scan images before pushing:
```bash
trivy image myapp:1.0
```

- Set resource limits in Kubernetes:
```yaml
resources:
  limits:
    cpu: "500m"
    memory: "256Mi"
  requests:
    cpu: "100m"
    memory: "128Mi"
```

---

### Q4: What is a Security Group vs an IAM policy in AWS?

**Answer:**

| | Security Group | IAM Policy |
|---|---|---|
| **Controls** | Network traffic (firewall) | AWS API access (permissions) |
| **Applied to** | EC2 instances, RDS, etc. | Users, roles, services |
| **Example** | Allow port 443 from internet | Allow Lambda to write to S3 |

---

## 18. System Design for DevOps

### Q1: How would you design a CI/CD pipeline for a microservices application?

**Answer:**
```
Developer pushes code
        ↓
GitHub / GitLab (trigger webhook)
        ↓
CI Stage (Jenkins / GitHub Actions):
   ├── Checkout code
   ├── Lint & static analysis (SonarQube)
   ├── Unit tests
   ├── Security scan (Snyk / Trivy)
   ├── Build Docker image
   └── Push image to registry (ECR / Docker Hub)
        ↓
CD Stage (ArgoCD / Jenkins):
   ├── Deploy to DEV (auto on every merge)
   ├── Run integration tests
   ├── Deploy to STAGING (auto)
   ├── Run smoke tests + performance tests
   └── Deploy to PRODUCTION (manual approval OR canary)
        ↓
Post-deployment:
   ├── Prometheus monitors metrics
   ├── Alert triggers if error rate spikes
   └── Auto-rollback if health check fails
```

**Key principles:**
- Build once, promote the same artifact everywhere
- Fail fast — run fastest tests first
- Every deployment must be rollback-able in under 5 minutes
- Separate deploy from release (use feature flags)

---

### Q2: How would you design a fault-tolerant, high-availability architecture?

**Answer:**

**Key pillars:**

1. **Eliminate single points of failure**
   - Deploy across multiple AZs/regions
   - Use load balancers instead of direct server access

2. **Auto-healing**
   - Kubernetes restarts failed pods automatically
   - AWS Auto Scaling replaces failed EC2 instances

3. **Data redundancy**
   - RDS Multi-AZ for database failover
   - S3 with cross-region replication for critical data

4. **Circuit breakers**
   - Prevent cascading failures in microservices
   - Tools: Resilience4j, Istio

5. **Chaos engineering**
   - Deliberately inject failures to find weaknesses
   - Tools: Chaos Monkey, AWS Fault Injection Simulator

6. **Runbooks**
   - Documented, tested incident response procedures

---

### Q3: What is GitOps and how does it improve deployments?

**Answer:**
- GitOps: Git is the **single source of truth** for both code AND infrastructure
- All changes go through Git (pull requests, code review, approval)
- The cluster automatically **reconciles** to match what's in Git

```
Developer opens PR
        ↓
Code review + approval
        ↓
Merge to main
        ↓
ArgoCD / Flux detects change in Git
        ↓
Automatically applies to Kubernetes cluster
        ↓
Drift detection: If someone manually changes cluster state,
ArgoCD reverts it to match Git
```

**Benefits:**
- Full audit trail (every change tracked in Git)
- Easy rollback (revert the commit)
- Consistent environments across all clusters

---

---

## 19. Scenario-Based Questions

> ⚠️ These are the questions that **win or lose interviews**. Read each carefully.

---

#### Scenario 1: Your website is completely down in production. What do you do?

**Answer:**
- **Step 1: Don't panic — start with quick checks**
  ```bash
  ping your-domain.com              # Is the server reachable?
  curl -I https://your-domain.com   # Is the web server responding?
  ```

- **Step 2: Check server health**
  ```bash
  top                                # CPU/memory usage
  df -h                              # Disk space (full disk = silent killer)
  free -h                            # Memory
  ```

- **Step 3: Check service status**
  ```bash
  systemctl status nginx             # Is web server running?
  systemctl status docker            # Is Docker running?
  kubectl get pods -n production     # Are K8s pods healthy?
  ```

- **Step 4: Check application logs**
  ```bash
  tail -f /var/log/nginx/error.log
  kubectl logs <pod-name> --previous
  journalctl -u myapp --since "30 minutes ago"
  ```

- **Step 5: Rollback if recent deployment caused it**
  ```bash
  kubectl rollout undo deployment/myapp
  # OR revert last Git commit and re-deploy
  ```

- **Step 6: Communicate**
  - Notify team on Slack/PagerDuty immediately
  - Update status page (statuspage.io)
  - Give ETA for resolution

- **Step 7: Post-mortem**
  - Write a blameless post-mortem after resolution
  - Add better tests, monitoring, and alerts to prevent recurrence

---

#### Scenario 2: A Kubernetes Pod is stuck in `CrashLoopBackOff`. How do you debug it?

**Answer:**
- **Step 1: Get pod status and events**
  ```bash
  kubectl describe pod <pod-name> -n production
  # Look for: exit code, last state, events at bottom
  ```

- **Step 2: Check logs from the crashed container**
  ```bash
  kubectl logs <pod-name> --previous -n production
  # --previous shows logs from the last crashed instance
  ```

- **Step 3: Identify common causes and fix**

  | Exit Code | Likely Cause | Fix |
  |---|---|---|
  | Exit 1 | Application error | Fix the app bug |
  | Exit 137 | OOM (out of memory) | Increase memory limit |
  | Exit 2 | Missing config/file | Check ConfigMap/Secret mounts |
  | CreateContainerConfigError | Missing Secret/ConfigMap | Create the missing resource |

- **Step 4: Debug interactively (if container starts briefly)**
  ```bash
  kubectl run debug --image=busybox -it --rm -- sh
  # Test connectivity, environment variables, etc.
  ```

---

#### Scenario 3: A CI/CD pipeline fails midway through. What do you do?

**Answer:**
- **Step 1: Check the failed stage**
  - Open Jenkins / GitHub Actions and read the full error log
  - Look for the exact command that failed and the error message

- **Step 2: Common failures and fixes**

  | Failure | Cause | Fix |
  |---|---|---|
  | Build fails | Compilation error | Fix code, check dependencies |
  | Tests fail | Regression introduced | Fix failing tests |
  | Docker build fails | Syntax in Dockerfile | Fix Dockerfile |
  | Docker push fails | Auth error | Refresh registry credentials |
  | Deployment fails | kubectl error | Check namespace, RBAC, resource limits |
  | Timeout | Slow test or network | Optimize or increase timeout |

- **Step 3: Reproduce locally**
  ```bash
  docker build -t myapp:test .          # Test docker build
  docker run myapp:test npm test        # Test inside container
  kubectl apply -f deployment.yaml --dry-run=client  # Dry run K8s deploy
  ```

- **Step 4: Fix and re-trigger**
  - Push a fix commit or re-run the pipeline
  - Add better error messages or health checks to catch this earlier

---

#### Scenario 4: Server CPU is at 100%. How do you handle it?

**Answer:**
- **Step 1: Find the process**
  ```bash
  top                        # Sort by CPU usage (press P)
  ps aux --sort=-%cpu | head -10
  ```

- **Step 2: Investigate the process**
  ```bash
  # What is it doing?
  strace -p <PID>
  lsof -p <PID>              # What files/connections does it have open?
  ```

- **Step 3: Take action based on cause**
  - If runaway process → `kill -9 <PID>` (last resort)
  - If legitimate spike → scale up (add more instances)
  - If memory leak → restart the service + create a fix
  - If traffic spike → activate auto-scaling, add CDN caching

- **Step 4: Prevent future occurrences**
  - Set CPU limits on Kubernetes pods
  - Configure CloudWatch/Prometheus alerts at 80% CPU threshold
  - Set up Auto Scaling before next traffic event

---

#### Scenario 5: Docker container keeps exiting immediately after start. What do you do?

**Answer:**
- **Step 1: Check exit logs**
  ```bash
  docker ps -a                        # See exit code
  docker logs <container-id>          # See why it exited
  ```

- **Step 2: Common causes**
  - **CMD/ENTRYPOINT is wrong** → Container starts then exits because main process ended
  - **Missing environment variable** → App crashes on startup
  - **Port already in use** → Container can't bind port

- **Step 3: Debug interactively**
  ```bash
  # Override the entrypoint to get a shell
  docker run -it --entrypoint bash myapp:1.0
  # Then manually run your app to see the actual error
  ```

- **Step 4: Fix the Dockerfile**
  ```dockerfile
  # Ensure the CMD keeps the container alive
  # ❌ Bad: process exits immediately
  CMD ["echo", "hello"]

  # ✅ Good: long-running foreground process
  CMD ["nginx", "-g", "daemon off;"]
  ```

---

#### Scenario 6: A security breach is detected in your production environment. What do you do?

**Answer:**
- **Step 1: Isolate immediately**
  - Remove affected instance from load balancer
  - Revoke all API keys and tokens that may be compromised
  - Isolate the compromised server (remove from security groups)

- **Step 2: Assess the damage**
  ```bash
  # Check who logged in recently
  last
  who
  # Check for suspicious processes
  ps aux | grep -E "nc|ncat|python.*-c"
  # Check open network connections
  netstat -tulpn
  # Check cron jobs for backdoors
  crontab -l
  cat /etc/cron*
  ```

- **Step 3: Preserve evidence**
  - Take a snapshot of the affected instance before wiping
  - Save logs to a secure, isolated location
  - Do NOT turn off the machine yet — capture memory if possible

- **Step 4: Notify and escalate**
  - Notify security team and management immediately
  - Check compliance obligations (GDPR requires breach notification within 72 hours)

- **Step 5: Clean and restore**
  - Terminate the compromised instance
  - Restore from last known good backup
  - Rotate ALL credentials (database passwords, API keys, SSH keys)
  - Patch the vulnerability that allowed the breach

- **Step 6: Post-incident**
  - Root cause analysis
  - Improve monitoring (add runtime security tools like Falco)
  - Conduct security audit of entire environment

---

#### Scenario 7: Your Kubernetes cluster is running slow. Application has high response times. How do you investigate?

**Answer:**
- **Step 1: Check pod resource usage**
  ```bash
  kubectl top pods --sort-by=cpu -n production
  kubectl top pods --sort-by=memory -n production
  kubectl top nodes
  ```

- **Step 2: Check if pods are throttled**
  ```bash
  kubectl describe pod <pod-name> | grep -A5 "Limits\|Requests"
  # Look for: OOMKilled events, CPU throttling in metrics
  ```

- **Step 3: Check network connectivity between services**
  ```bash
  kubectl exec -it <pod-name> -- curl http://my-service:8080/health
  kubectl exec -it <pod-name> -- ping my-database
  ```

- **Step 4: Check HPA status**
  ```bash
  kubectl get hpa -n production
  # Is autoscaler scaling up? Is it hitting maxReplicas?
  ```

- **Step 5: Fixes based on findings**
  - CPU throttled → Increase CPU limits or optimize the app
  - Memory pressure → Increase memory limits or fix memory leaks
  - Hitting maxReplicas → Increase max replicas in HPA
  - Database bottleneck → Add connection pooling, read replicas

---

#### Scenario 8: You need to deploy a new version with zero downtime. How do you do it?

**Answer:**

**Option 1: Rolling Update (Default in Kubernetes)**
```yaml
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1          # Add 1 extra pod during update
      maxUnavailable: 0    # Never take down a pod before new one is ready
```

**Option 2: Blue-Green Deployment**
```bash
# Deploy new version (green) alongside old (blue)
kubectl apply -f deployment-green.yaml

# Wait for green to be ready
kubectl rollout status deployment/myapp-green

# Switch service to point to green
kubectl patch service myapp -p '{"spec":{"selector":{"version":"green"}}}'

# Delete old blue deployment
kubectl delete deployment myapp-blue
```

**Option 3: Canary Deployment (Argo Rollouts)**
- Send 5% of traffic to new version
- Monitor error rates for 10 minutes
- Gradually increase to 50%, then 100%
- Automatic rollback if error rate spikes

---

---

## 20. Quick Reference Cheat Sheet

### 🐧 Linux
```bash
ps aux | grep <name>        # Find process
kill -9 <PID>               # Force kill
df -h && free -h            # Disk and memory
tail -f /var/log/syslog     # Live logs
chmod 755 file && chown user:group file  # Permissions
crontab -e                  # Edit cron jobs
systemctl start|stop|status <service>   # Service control
```

### 🐙 Git
```bash
git clone / init / add / commit / push / pull
git checkout -b feature && git merge feature
git rebase main && git stash / stash pop
git revert <hash>           # Safe undo (use over reset)
git log --oneline           # Short history
```

### 🐳 Docker
```bash
docker build -t app:1.0 .
docker run -d -p 8080:80 app:1.0
docker ps && docker logs -f <id>
docker exec -it <id> bash
docker compose up -d && down
trivy image app:1.0         # Security scan
```

### ☸️ Kubernetes
```bash
kubectl get pods/nodes/all -n <ns>
kubectl describe pod <name>
kubectl logs <name> --previous
kubectl exec -it <name> -- bash
kubectl apply -f file.yaml
kubectl rollout undo deployment/<name>
kubectl scale deployment <name> --replicas=5
kubectl top pods && top nodes
```

### 🏗️ Terraform
```bash
terraform init → plan → apply → destroy
terraform state list
terraform fmt && terraform validate
# Store state in S3 with DynamoDB locking
```

### ☁️ AWS Core Services
```
EC2 → Compute | S3 → Storage | VPC → Network
EKS → Managed K8s | RDS → Database | IAM → Permissions
CloudWatch → Monitoring | CloudTrail → Audit | ALB → Load Balancer
Secrets Manager → Secrets | Lambda → Serverless
```

---

## 📚 Recommended Study Resources

| Resource | Link | Best For |
|---|---|---|
| DevOps Roadmap | roadmap.sh/devops | Learning path overview |
| Kubernetes Docs | kubernetes.io/docs | K8s fundamentals |
| AWS Free Tier | aws.amazon.com/free | Hands-on practice |
| GitHub DevOps Q&A | github.com/bregman-arie/devops-exercises | 600+ practice questions |
| Terraform Docs | developer.hashicorp.com/terraform | IaC deep dive |
| Play With Kubernetes | labs.play-with-k8s.com | Free K8s sandbox |

---

## 🎯 Interview Preparation Tips

- **Hands-on beats memorization** – Set up a Kubernetes cluster, break it, fix it
- **Tell stories, not definitions** – "In my last project, we used Terraform to..." beats any textbook answer
- **Narrate your thinking** – During troubleshooting rounds, think out loud
- **Know the non-negotiable 2026 stack:**
  - Git + GitHub
  - Docker + Kubernetes
  - Terraform + (Ansible)
  - One CI/CD tool: Jenkins or GitHub Actions
  - One cloud: AWS (preferred), Azure, or GCP
  - Prometheus + Grafana for monitoring
- **Own your mistakes** – Interviewers value self-awareness over perfection

---




