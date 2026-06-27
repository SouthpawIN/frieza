<<<<<<< HEAD
# Frieza — Server Management & Infrastructure Automation

![Frieza](https://v3b.fal.media/files/b/0a9fe98c/cjquofjkHmmA4d0hftOjI_owOvDV2u.png)

## What Frieza Does
- **Deploys** containers and services to Coolify infrastructure
- **Provisions** virtual machines, databases, and compute resources
- **Manages** infrastructure through GitOps (Terraform, Ansible workflows)
- **Monitors** system health and performance
- **Automates** repetitive infrastructure tasks

## Quick Start
=======
# Frieza — The DevOps Agent

The infrastructure specialist of the fleet. Frieza handles deployments, server management, CI/CD pipelines, and all infrastructure-related tasks.

## Installation
>>>>>>> 6da9959 (chore: auto-backup 2026-06-27T07:01:33Z)

### Install
```bash
hermes profile install https://github.com/SouthpawIN/frieza
```

<<<<<<< HEAD
### Verify
```bash
hermes profile list
```

### Run
```bash
hermes chat --profile frieza
=======
## Update

```bash
hermes profile update frieza
```

## What Does Frieza Do?

**Infrastructure and deployment management**

Frieza is your infrastructure guru. It manages servers, handles deployments, configures CI/CD pipelines, monitors system health, and ensures your applications run smoothly in production. When something needs to go live or needs fixing at the infrastructure level, Frieza takes care of it.

## Example Prompts

**Deployment:**
```
User: "Deploy the latest version to production"

Frieza:
🚀 Production Deployment: myapp v2.1.0

Pre-deployment checks:
✓ Tests passing (127/127)
✓ Build successful
✓ No security vulnerabilities
✓ Database migrations validated

Deployment steps:
1. Pulling image: myapp:2.1.0
2. Running database migrations (3 pending)
   ✓ users_add_last_login
   ✓ orders_add_tracking_number
   ✓ products_add_sku_index
3. Deploying to production (3 instances)
   ✓ instance-1: healthy (2.3s)
   ✓ instance-2: healthy (2.5s)
   ✓ instance-3: healthy (2.4s)
4. Updating load balancer
5. Running health checks
   ✓ All endpoints responding (avg 145ms)
6. Verifying SSL certificates valid

✅ Deployed successfully
🌐 Live at: https://myapp.com
⏱️ Total time: 47 seconds
📊 Zero-downtime deployment completed
```

**Server Health Check:**
>>>>>>> 6da9959 (chore: auto-backup 2026-06-27T07:01:33Z)
```
User: "Check if all our servers are healthy"

<<<<<<< HEAD
## Example Prompts

- *"Deploy the new Redis container to the prod cluster on Coolify"*
- *"Spin up a new Ubuntu VM with 4GB RAM for the CI runner"*
- *"Check if the database is healthy and running"*
- *"Scale up the web service from 2 to 4 replicas"*
- *"Create a new PostgreSQL database for the user service"*
- *"What's the current resource usage across all servers?"*
- *"Set up a GitHub Actions runner on a new VM"*
- *"Provision an S3-compatible bucket for our log archival"*

## Key Features
- Coolify integration — deploys containers and services through Coolify's API
- VM provision — creates and configures virtual machines on demand
- GitOps workflows — manages infrastructure as code through Terraform and Ansible
- Health monitoring — checks system health and reports on performance
- Resource awareness — knows what's running where and what resources are available

## Integration with Other Agents
Frieza is the infrastructure agent. Chizul builds features that Frieza deploys. Senter dispatches infrastructure tasks to Frieza. Anser asks Frieza when users report system issues. Kashik documents infrastructure that Frieza creates.

## Configuration
`~/.hermes/profiles/frieza/config.yaml`

Key settings:
- `coolify_api_url` — URL for Coolify API access
- `coolify_api_key` — authentication token for Coolify
- `default_cluster` — which cluster to deploy to by default
- `ssh_key_path` — SSH key for VM provisioning
- `terraform_state_bucket` — where to store Terraform state

## Troubleshooting

**Coolify deployment failing:** Check that the Coolify API token has correct permissions and the target cluster is accessible. Run `coolify status` to check cluster health.

**VM provisioning stuck:** Verify SSH key is configured correctly and the cloud provider has available capacity in the requested region.

**Terraform state conflicts:** Another process may be locking the state. Check for stale locks with `terraform state list` and remove if necessary.
**Part of the multi-agent fleet by SouthpawIN**
=======
Frieza:
🖥️ Infrastructure Health Report

📊 Overall Status: HEALTHY (9/10 services)

Production Cluster:
┌─────────────────────────────────────────┐
│ Node              Status    CPU    RAM  │
├─────────────────────────────────────────┤
│ app-prod-1       ✅ OK     42%    3.2GB│
│ app-prod-2       ✅ OK     38%    3.5GB│
│ app-prod-3       ⚠️ WARN   87%    4.8GB│
│ db-prod-master   ✅ OK     56%    12GB │
│ db-prod-replica  ✅ OK     34%    11GB │
│ redis-prod       ✅ OK     23%    1.2GB│
└─────────────────────────────────────────┘

⚠️ Warnings:
- app-prod-3: High CPU usage (87%)
  Recommendation: Scale horizontally or investigate load
  
✅ All systems operational
Last check: 2 minutes ago
```

**CI/CD Pipeline Setup:**
```
User: "Set up CI/CD for my Node.js project"

Frieza:

📦 Setting up CI/CD pipeline for: nodejs-app

Creating .github/workflows/main.yml:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '20'
        cache: 'npm'
    
    - name: Install dependencies
      run: npm ci
    
    - name: Run linter
      run: npm run lint
    
    - name: Run tests
      run: npm test
    
    - name: Generate coverage report
      run: npm run coverage
    
    - name: Upload coverage
      uses: codecov/codecov-action@v3

  build:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Build Docker image
      run: docker build -t myapp:${{ github.sha }} .
    
    - name: Push to registry
      run: |
        docker login -u ${{ secrets.DOCKER_USER }} -p ${{ secrets.DOCKER_PASS }}
        docker push myregistry.com/myapp:${{ github.sha }}

  deploy:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    
    steps:
    - name: Deploy to production
      run: |
        ssh ${{ secrets.SERVER_USER }}@${{ secrets.SERVER_IP }}
        docker pull myregistry.com/myapp:${{ github.sha }}
        docker service update --image myregistry.com/myapp:${{ github.sha }} myapp
```

✅ Pipeline configured
- Triggers: On push to main/develop, on PR to main
- Stages: Test → Build → Deploy (production only)
- Includes: Linting, testing, coverage, Docker build, auto-deploy
- Security: Uses GitHub Secrets for credentials
```

**Database Backup:**
```
User: "Create a backup of the production database"

Frieza:

💾 Production Database Backup: postgres_prod

Creating backup...
1. Connecting to production database
2. Creating snapshot (non-blocking)
3. Dumping schema and data

Progress:
[████████████████████] 100% (4.2GB)
⏱️ Completed in: 3m 24s

Backup details:
- Size: 4.2 GB (compressed: 892 MB)
- Tables: 47
- Rows: 12.4 million
- Checksum: a8f3e2b1c9d7e4f6a2b5c8d1e4f7a2b5

Storage:
✓ Uploaded to AWS S3
✓ Uploaded to Google Cloud Storage  
✓ Copied to backup server

Retention:
- Daily backups: keep 7 days
- Weekly backups: keep 4 weeks
- Monthly backups: keep 12 months

✅ Backup complete
📁 Location: s3://backups/postgres_prod/2024-03-15/
   File: postgres_prod_2024-03-15_02-00-00.sql.gz
```

**Monitoring Setup:**
```
User: "Set up monitoring for my web application"

Frieza:

📊 Configuring monitoring for: webapp-production

Metrics to track:
• Response time (p50, p95, p99)
• Error rate (4xx, 5xx)
• Request throughput (req/sec)
• CPU & memory usage
• Database query time
• Active connections
• Queue depth

Setting up Prometheus:
✓ Prometheus server deployed
✓ Node Exporter installed on all nodes
✓ PostgreSQL metrics collector configured
✓ Custom application metrics endpoint integrated

Setting up Grafana:
✓ Grafana server deployed
✓ Dashboards created:
  - Application Overview
  - Infrastructure Health
  - Database Performance
  - Business Metrics

Alerts configured:
🔴 Critical (immediate notification):
  - Error rate > 5%
  - Response time > 2s
  - Server down
  
🟡 Warning (within 15 min):
  - CPU > 80% for 5 min
  - Memory > 90% for 5 min
  - Error rate > 1%

Notification channels:
✓ PagerDuty (critical alerts)
✓ Slack (all alerts)
✓ Email (daily digest)

✅ Monitoring active
📈 Dashboard: https://grafana.myapp.com
```

**SSL Certificate:**
```
User: "Check SSL certificate status"

Frieza:

🔒 SSL Certificate Report

Primary Domain: myapp.com
┌──────────────────────────────────────────────┐
│ Certificate Details                          │
├──────────────────────────────────────────────┤
│ Provider: Let's Encrypt                      │
│ Type: DV (Domain Validation)                 │
│ Issued: March 1, 2024                        │
│ Expires: May 30, 2024 (76 days remaining)   │
│ Auto-renew: ✅ Enabled                       │
│ Status: ✅ Valid                             │
└──────────────────────────────────────────────┘

Subdomains:
• api.myapp.com      ✅ Valid (76 days left)
• admin.myapp.com    ✅ Valid (76 days left)
• www.myapp.com      ✅ Valid (76 days left)
• mail.myapp.com     ⚠️ Expires in 14 days

⚠️ Attention:
- mail.myapp.com expires in 14 days
  Auto-renew should handle this
  If issues, manually renew: `certbot renew --cert-name mail.myapp.com`

✅ All certificates valid
Next scheduled renewal: April 15, 2024
```

**Scaling:**
```
User: "We're getting high traffic, scale up the servers"

Frieza:

📈 Scaling Operation: webapp-production

Current state:
- Instances: 3
- CPU: avg 87%
- Memory: avg 4.2GB / 8GB
- Response time: avg 890ms (target: <500ms)

Scaling decision:
→ Horizontal scale: 3 → 6 instances
→ Vertical scale: Not needed (memory adequate)

Executing scale-up:
1. Updating auto-scaling group (min: 3, max: 10)
2. Launching 3 additional instances
   ✓ instance-4: launching... healthy (45s)
   ✓ instance-5: launching... healthy (47s)
   ✓ instance-6: launching... healthy (46s)
3. Registering with load balancer
4. Running health checks
   ✓ All instances healthy

Results (after 5 minutes):
- Instances: 6 (+3)
- CPU: avg 44% (-43%)
- Response time: avg 280ms (-68%)
- Throughput: 1,200 req/sec (+100%)

✅ Scaling successful
💰 Estimated cost increase: +$150/month
📊 Performance targets met
```

## Capabilities

### Deployment
- Docker container orchestration
- Kubernetes cluster management
- Blue-green deployments
- Rolling updates
- Database migrations
- Zero-downtime deployments

### Infrastructure
- Server provisioning
- Load balancer configuration
- Auto-scaling setup
- Network configuration
- DNS management
- Storage management

### CI/CD
- GitHub Actions
- GitLab CI
- Jenkins
- CircleCI
- Pipeline design
- Build optimization

### Monitoring
- Prometheus setup
- Grafana dashboards
- Alerting configuration
- Log aggregation
- Performance monitoring
- Uptime monitoring

### Security
- SSL/TLS certificates
- Firewall rules
- Security group management
- Secret management
- Audit logging
- Compliance checks

### Cloud Providers
- **AWS**: EC2, ECS, EKS, RDS, S3, CloudFront, Route53
- **GCP**: GCE, GKE, Cloud SQL, Cloud Storage, Cloudflare
- **Azure**: VMs, AKS, SQL Database, Blob Storage, Traffic Manager
- **DigitalOcean**: Droplets, Kubernetes, Managed Databases

## Advanced Features

### Infrastructure as Code (IaC)
```
Frieza can generate and manage:
- Terraform configurations
- Ansible playbooks
- CloudFormation templates
- Pulumi code (TypeScript/Python)
- Helm charts for Kubernetes
```

### Disaster Recovery
```
Automated backup and recovery:
- Database snapshots (hourly/daily)
- File system backups
- Cross-region replication
- Restoration testing
- RPO/RTO monitoring
```

### Cost Optimization
```
Analyzing and reducing cloud costs:
- Unused resource detection
- Right-sizing recommendations
- Reserved instance suggestions
- Spot instance opportunities
- Auto-shutdown for dev/test
```

## When to Use Frieza

- Deploying applications to production
- Setting up CI/CD pipelines
- Managing servers and infrastructure
- Configuring monitoring and alerting
- Handling database operations
- Managing SSL certificates
- Scaling infrastructure
- Infrastructure as Code (Terraform, etc.)
- Cloud resource management
- Disaster recovery planning

## When to Use Other Agents

- **Chizul**: For fixing application code bugs (Frieza handles infrastructure)
- **Klerik**: For reviewing infrastructure code quality
- **Kashi**: For writing deployment documentation
- **Senter**: For prioritizing which infrastructure tasks to handle first

---

*Part of the multi-agent fleet by SouthpawIN*
>>>>>>> 6da9959 (chore: auto-backup 2026-06-27T07:01:33Z)
