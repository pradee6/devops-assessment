# V7 AI Solutions LLP - DevOps Technical Assessment

## Project

Docker-Based Virtual Infrastructure with Ansible Automation and a Hardened Nginx Reverse Proxy.

## Candidate

Pradeep

## Submission Status

**Partial Submission**

## Objective

The objective was to create three Ubuntu Docker containers:

* vm1
* vm2
* vm3

and configure them using:

* Docker
* Custom Docker networking
* SSH
* Firewall rules
* Ansible
* Nginx
* HTTPS/TLS
* Reverse proxy
* Load balancing
* Failover testing

## Planned Architecture

```text
                    Client
                      |
                      v
                 +---------+
                 |   vm1   |
                 |  Nginx  |
                 |  HTTPS  |
                 +----+----+
                      |
               +------+------+
               |             |
               v             v
          +---------+   +---------+
          |   vm2   |   |   vm3   |
          |  Nginx  |   |  Nginx  |
          +---------+   +---------+
```

## Planned Docker Network

Network:

`devops-network`

Subnet:

`172.28.0.0/24`

Planned IP addresses:

```text
vm1 = 172.28.0.11
vm2 = 172.28.0.12
vm3 = 172.28.0.13
```

## Planned Ansible Configuration

Ansible was planned to manage all three containers using SSH key authentication.

The planned roles were:

* common
* ssh
* nginx

Ansible Vault was also planned for sensitive information.

## Planned Nginx Configuration

vm1 would act as the reverse proxy.

Planned endpoints:

```text
/vm2
/vm3
/app
```

The `/app` endpoint would load balance traffic between vm2 and vm3.

## Planned Failover Test

vm2 would be stopped while continuous requests were sent through vm1.

The expected test would verify that traffic continued through vm3.

After restarting vm2, it would be verified that vm2 returned to the service.

## Technical Challenge

Docker Desktop could not start because hardware virtualization support was not detected.

Docker displayed:

> Virtualization support not detected.

Therefore, the Docker containers could not be started and the runtime portions of the assessment could not be completed.

## Evidence

Evidence of the Docker virtualization issue is available in:

`evidence/docker-virtualization-error.png`

## Documentation

The complete implementation approach, planned configuration, progress, and technical limitation are documented in:

`Assessment-Completion-Explanation.docx`

## Important Note

This submission does not claim runtime tests that could not be performed because of the Docker virtualization issue.
