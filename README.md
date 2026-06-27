# Frieza — Server Management & Infrastructure Automation

![Frieza](https://v3b.fal.media/files/b/0a9fe83f/oPyTPsN9teym-gErpPOI4_T9KeejHs.png)

## What Frieza Does
- **Deploys** containers and services to Coolify infrastructure
- **Provisions** virtual machines, databases, and compute resources
- **Manages** infrastructure through GitOps (Terraform, Ansible workflows)
- **Monitors** system health and performance
- **Automates** repetitive infrastructure tasks

## Quick Start

### Install
```bash
hermes profile install https://github.com/SouthpawIN/frieza
```

### Verify
```bash
hermes profile list
```

### Run
```bash
hermes chat --profile frieza
```

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
