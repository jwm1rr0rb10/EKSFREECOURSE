# Amazon EKS Course 2026: Free EKS and Kubernetes on AWS Course from Zero to Production

![Amazon EKS](https://img.shields.io/badge/Amazon%20EKS-Kubernetes%201.36-FF9900?logo=amazonaws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1.36-326CE5?logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-cloud-orange?logo=amazonaws&logoColor=white)
![Course in English](https://img.shields.io/badge/language-English-blue)
![Free Course](https://img.shields.io/badge/price-free-brightgreen)
![Junior → Senior](https://img.shields.io/badge/level-junior%20%E2%86%92%20senior-orange)

> **A complete free Amazon EKS course in English.** Kubernetes, AWS, VPC, IAM, EKS Auto Mode, Managed Node Groups, Pod Identity, EBS/EFS, ALB/NLB, HPA, Karpenter, NetworkPolicy, Secrets, observability, Helm, Terraform, GitOps, CI/CD, upgrades, troubleshooting, cost optimization, and production architecture.
>
> Everything in one README: theory, diagrams, YAML, AWS CLI, `kubectl`, `eksctl`, Helm, Terraform, common mistakes, hands-on tasks, and self-check questions.
>
> **Current scope:** examples target Amazon EKS and Kubernetes **1.36**; at the time this course was prepared, EKS versions `1.36`, `1.35`, and `1.34` are in standard support. Before each lab, always verify the current supported-version matrix in the official AWS documentation.

> ⚠️ **Cost:** EKS, EC2, NAT Gateway, Load Balancer, EBS/EFS, CloudWatch, and other AWS resources may incur charges. Run cluster labs deliberately and delete resources after practice.

⭐ If the course is useful, star the repository — it helps other engineers discover it.

---

## Who This EKS Course Is For

| Who you are | What you will get |
|---|---|
| **Kubernetes beginner** | Understand Pods, Deployments, Services, ConfigMaps, Secrets, Ingress, and RBAC on a real AWS cluster |
| **Backend developer** | Learn to deploy services to EKS, connect S3/RDS/Secrets, and work with autoscaling |
| **DevOps / Platform Engineer** | Understand the full EKS lifecycle: networking, IAM, node groups, upgrades, add-ons, observability, and security |
| **SRE** | Get hands-on experience with HA, PDB, topology spread, HPA, Karpenter, diagnostics, and disaster recovery |
| **Cloud Engineer** | Connect Kubernetes with VPC, IAM, ELB, EBS, EFS, KMS, Route 53, CloudWatch, and ECR |
| **Terraform Engineer** | Build EKS as code and learn to separate infrastructure from Kubernetes manifests |
| **Interview candidate** | Get junior / middle / senior-level questions and production scenarios |
| **Architect / Tech Lead** | Learn to choose between Auto Mode, Managed Node Groups, Karpenter, ALB/NLB, EBS/EFS, and different access models |

## What You Will Be Able to Do After the Course

- explain EKS architecture: control plane, API server, etcd, scheduler, nodes, kubelet, and controllers;
- explain what AWS manages in EKS and what remains the customer's responsibility;
- create a cluster with `eksctl` and understand which AWS resources were created;
- deploy a cluster into a VPC with public/private subnets and multiple Availability Zones;
- understand Amazon VPC CNI and how Kubernetes Pod IPs relate to the VPC;
- use EKS Auto Mode and understand how it differs from the traditional EKS model;
- create and update Managed Node Groups;
- deploy applications with Deployment, Service, ConfigMap, and Secret;
- understand `requests`, `limits`, probes, ReplicaSet, and rollout;
- manage access with EKS Access Entries, Kubernetes RBAC, and IAM;
- grant AWS permissions to Pods with EKS Pod Identity and understand legacy IRSA;
- connect EBS CSI and EFS CSI for stateful workloads;
- expose services through AWS Load Balancer Controller, ALB, and NLB;
- understand the difference between `ClusterIP`, `NodePort`, `LoadBalancer`, Ingress, and Gateway;
- configure HPA and understand how autoscaling relates to metrics;
- use Karpenter and design NodePools for real workloads;
- provide HA with PDB, topology spread, anti-affinity, and multi-AZ deployments;
- build NetworkPolicy and understand the boundaries between SG, NetworkPolicy, and IAM;
- encrypt Kubernetes API data and Secrets with AWS KMS;
- collect logs, metrics, and traces with CloudWatch / Prometheus / OpenTelemetry;
- use Helm, Terraform, Kustomize, and GitOps;
- build CI/CD: GitHub Actions → ECR → EKS;
- perform safe Kubernetes and node-group upgrades;
- diagnose `Pending`, `CrashLoopBackOff`, `ImagePullBackOff`, DNS, CNI, IAM, and LB issues;
- optimize cost and plan capacity;
- design a production EKS platform with security, observability, autoscaling, and DR.

---

## Contents

- [Who This EKS Course Is For](#who-this-eks-course-is-for)
- [What You Will Be Able to Do After the Course](#what-you-will-be-able-to-do-after-the-course)
- [How to Take the Course](#how-to-take-the-course)
- [Lab Rules and Variables](#lab-rules-and-variables)
- [Module 0. What Is EKS and Why Do You Need It?](#module-0-what-is-eks-and-why-do-you-need-it)
- [Module 1. Kubernetes Inside EKS](#module-1-kubernetes-inside-eks)
- [Module 2. AWS CLI, eksctl, kubectl, Helm, and Terraform](#module-2-aws-cli-eksctl-kubectl-helm-and-terraform)
- [Module 3. AWS Networking: VPC, Subnets, AZ, and VPC CNI](#module-3-aws-networking-vpc-subnets-az-and-vpc-cni)
- [Module 4. Creating EKS: Auto Mode and Classic EKS](#module-4-creating-eks-auto-mode-and-classic-eks)
- [Module 5. Workloads: Pod, Deployment, Service, ConfigMap, Secret](#module-5-workloads-pod-deployment-service-configmap-secret)
- [Module 6. IAM and Cluster Access: Access Entries and RBAC](#module-6-iam-and-cluster-access-access-entries-and-rbac)
- [Module 7. IAM for Pods: EKS Pod Identity and IRSA](#module-7-iam-for-pods-eks-pod-identity-and-irsa)
- [Module 8. Storage: EBS, EFS, PVC, and Stateful Workloads](#module-8-storage-ebs-efs-pvc-and-stateful-workloads)
- [Module 9. Application Networking: Service, ALB, NLB, and Ingress](#module-9-application-networking-service-alb-nlb-and-ingress)
- [Module 10. Scheduling: requests, limits, probes, taints, affinity](#module-10-scheduling-requests-limits-probes-taints-affinity)
- [Module 11. Scaling: HPA, Karpenter, Managed Node Groups, and Auto Mode](#module-11-scaling-hpa-karpenter-managed-node-groups-and-auto-mode)
- [Module 12. High Availability and Graceful Disruptions](#module-12-high-availability-and-graceful-disruptions)
- [Module 13. Security: Pod Security, NetworkPolicy, SG, KMS](#module-13-security-pod-security-networkpolicy-sg-kms)
- [Module 14. Observability: logs, metrics, events, traces](#module-14-observability-logs-metrics-events-traces)
- [Module 15. Helm, Kustomize, and GitOps](#module-15-helm-kustomize-and-gitops)
- [Module 16. CI/CD: GitHub Actions, ECR, and Deploying to EKS](#module-16-cicd-github-actions-ecr-and-deploying-to-eks)
- [Module 17. Lifecycle: add-ons, upgrades, and node maintenance](#module-17-lifecycle-add-ons-upgrades-and-node-maintenance)
- [Module 18. Troubleshooting and Production Diagnostics](#module-18-troubleshooting-and-production-diagnostics)
- [Module 19. Production Architecture and Final Project](#module-19-production-architecture-and-final-project)
- [AWS CLI + EKS Cheat Sheet](#aws-cli--eks-cheat-sheet)
- [kubectl Cheat Sheet](#kubectl-cheat-sheet)
- [Helm Cheat Sheet](#helm-cheat-sheet)
- [Troubleshooting Cheat Sheet](#troubleshooting-cheat-sheet)
- [EKS Interview Questions](#eks-interview-questions)
- [FAQ](#faq)
- [EKS Glossary](#eks-glossary)
- [Official Sources](#official-sources)

---

## How to Take the Course

1. **Do not skip the Kubernetes basics.** EKS is managed Kubernetes, not a separate version of Kubernetes.
2. **Run the commands yourself.** One hour of hands-on lab work is more useful than three hours of reading.
3. **Break the cluster safely.** Delete a Pod, reduce replicas, perform a rollout, put a Pod into `Pending`, and inspect events.
4. **Check where Kubernetes ends and AWS begins.** This is the key skill of an EKS engineer.
5. **Take notes on every error.** Production knowledge comes from troubleshooting.
6. **Complete the final project.** It connects the topics into one architecture.

### What You Need to Install

For Linux/macOS/WSL2:

- AWS CLI v2;
- `kubectl`;
- `eksctl`;
- Helm 3;
- Git;
- Docker;
- Terraform;
- `jq` recommended;
- an IDE with YAML/Kubernetes support.

AWS's official getting-started path recommends preparing AWS CLI, `kubectl`, and `eksctl`; Helm is a useful package manager for Kubernetes tooling. https://docs.aws.amazon.com/eks/latest/userguide/setting-up.html

---

## Lab Rules and Variables

Use these variables in all commands:

```bash
export AWS_REGION=eu-central-1
export CLUSTER_NAME=eks-course
export AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query Account --output text)
```

Verification:

```bash
aws sts get-caller-identity
aws eks list-clusters --region "$AWS_REGION"
eksctl version
kubectl version --client
helm version
terraform version
```

> `eu-central-1` is only an example. Use a region available in your account with the required EC2 instance types and EKS features.

### Good Habit

Before every lab, first inspect your context:

```bash
aws configure list
aws sts get-caller-identity
aws eks list-clusters --region "$AWS_REGION"
kubectl config current-context
```

This prevents the classic mistake: **"I deleted the wrong cluster."**

---

# Module 0. What Is EKS and Why Do You Need It?

## 0.1 EKS in Simple Terms

Amazon Elastic Kubernetes Service is managed Kubernetes from AWS. AWS manages the Kubernetes control plane, while the customer chooses how to organize the data plane and infrastructure around workloads. Current EKS supports both classic EKS and EKS Auto Mode. https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html

The main idea:

```text
                         AWS account
                              |
                    +---------+---------+
                    |                   |
             EKS control plane      Data plane
              managed by AWS        depends on mode
                    |                   |
        +-----------+-----------+      +----------------+
        | API server            |      | EC2 nodes       |
        | Scheduler             |      | or Auto Mode    |
        | Controllers            |      | compute         |
        | etcd                  |      +----------------+
        +-----------+-----------+
                    |
             Kubernetes API
                    |
             Pods / Services
```

## 0.2 What EKS Solves

Without managed Kubernetes, you need to design and operate the following yourself:

- control plane;
- etcd;
- API server;
- scheduler/controllers;
- certificates;
- upgrades control plane;
- part of the security hardening;
- HA control plane.

With EKS, AWS manages the control plane and integrates Kubernetes with AWS services.

## 0.3 EKS vs. Regular Kubernetes

| Object | Vanilla Kubernetes | EKS |
|---|---|---|
| API Server | You manage it | AWS manages it |
| etcd | You manage it | AWS manages it |
| Scheduler | You manage it | AWS manages it |
| Worker nodes | You manage them | MNG / Auto Mode / self-managed, etc. |
| IAM | External to Kubernetes | Deep AWS integration |
| VPC networking | Depends on the CNI | AWS VPC CNI — the primary AWS CNI |
| Load Balancer | Depends on the cloud | AWS Load Balancer Controller / Auto Mode |
| Storage | CSI drivers | EBS/EFS CSI and Auto Mode capabilities |

## 0.4 The Core EKS Principle

**Kubernetes manages desired state. AWS manages the AWS resources that Kubernetes relies on.**

For example:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: api
spec:
  type: LoadBalancer
```

Kubernetes creates a Service object, and the controller turns that desired state into an AWS Load Balancer.

## 0.5 Where EKS May Be a Poor Fit

EKS is not necessarily needed for:

- one small application on a single server;
- a simple cron workload;
- an application that is a better fit for AWS Lambda;
- a service with no need for the Kubernetes ecosystem.

Kubernetes is valuable when you need standardized deployments, self-healing, scheduling, autoscaling, service discovery, and a large platform for many workloads.

### Practice

1. Draw your application architecture without Kubernetes.
2. Mark what you need for self-healing.
3. Mark what you need for a rolling update.
4. Compare this with the capabilities of Deployment + Service.

### Common Mistakes

- treating EKS as a regular EC2 server;
- thinking AWS automatically manages the entire Kubernetes workload;
- forgetting that EC2/EBS/ELB/NAT can cost money;
- failing to distinguish the control plane from the data plane.

### Questions

1. What exactly does AWS manage in the EKS control plane?
2. How is EKS different from running k3s on EC2?
3. Who is responsible for the application inside a Pod?
4. What remains your responsibility in EKS?

---

# Module 1. Kubernetes Inside EKS

## 1.1 Kubernetes Architecture

```text
                 kubectl / CI / Argo CD
                          |
                          v
                   +-------------+
                   | API Server   |
                   +------+-------+
                          |
             +------------+------------+
             |                         |
        Scheduler                 Controllers
             |                         |
             +------------+------------+
                          |
                     desired state
                          |
                    +-----+-----+
                    |  kubelet  |
                    +-----+-----+
                          |
                       container
```

## 1.2 Core Resources

| Resource | Purpose |
|---|---|
| Pod | smallest execution unit |
| Deployment | declarative management of stateless Pods |
| ReplicaSet | maintains the number of Pods |
| Service | stable networking for a set of Pods |
| ConfigMap | non-secret configuration |
| Secret | sensitive values |
| Namespace | logical isolation |
| Job | one-time task |
| CronJob | recurring task |
| DaemonSet | a Pod on every eligible node |
| StatefulSet | stateful workloads with identity and storage |
| Ingress | L7 HTTP routing |
| NetworkPolicy | L3/L4 restrictions between Pods |

## 1.3 Desired state

You do not tell Kubernetes:

> "start a Pod right now."

You tell it:

```yaml
replicas: 3
```

And the controller continuously compares the actual state with the desired state.

## 1.4 Self-healing

If a Deployment requires 3 Pods and one disappears:

```text
desired = 3
actual  = 2
          |
          v
controller creates Pod
          |
desired = 3
actual  = 3
```

## 1.5 Lab: Inspect Kubernetes

```bash
kubectl get nodes -o wide
kubectl get ns
kubectl get pods -A
kubectl get deployments -A
kubectl get svc -A
```

Inspect labels:

```bash
kubectl get nodes --show-labels
```

Inspect system components:

```bash
kubectl get pods -n kube-system
```

### Practice

1. Find CoreDNS.
2. Find `kube-proxy`, if it is present in your EKS model.
3. Find the VPC CNI.
4. Delete one application Pod and see which controller creates its replacement.

### Questions

1. Why is a Pod not a good unit for long-lived deployment?
2. What does a Deployment do?
3. Why do you need a Service if a Pod already has an IP?
4. How does Kubernetes know that a Pod is unhealthy?

---

# Module 2. AWS CLI, eksctl, kubectl, Helm, and Terraform

## 2.1 AWS CLI

Verify identity:

```bash
aws sts get-caller-identity
```

Get the account ID:

```bash
aws sts get-caller-identity --query Account --output text
```

List EKS clusters:

```bash
aws eks list-clusters --region "$AWS_REGION"
```

Describe the cluster:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 2.2 eksctl

`eksctl` is a CLI for working with EKS that can create and manage EKS clusters declaratively and through commands. AWS uses it in official getting-started scenarios. https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

Verification:

```bash
eksctl version
```

## 2.3 kubectl

Client verification:

```bash
kubectl version --client
```

Context:

```bash
kubectl config get-contexts
kubectl config current-context
```

## 2.4 Helm

```bash
helm version
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

Helm is useful for complex Kubernetes applications, but it should not hide your understanding of basic YAML manifests.

## 2.5 Terraform

```bash
terraform version
terraform init
terraform fmt
terraform validate
terraform plan
```

The general separation is:

```text
Terraform
  |
  +--> VPC
  +--> IAM
  +--> EKS
  +--> ECR
  +--> KMS
  +--> RDS
  +--> S3

GitOps / kubectl / Helm
  |
  +--> Namespace
  +--> Deployment
  +--> Service
  +--> Ingress
  +--> HPA
```

### Practice

Create a `versions.sh` file:

```bash
#!/usr/bin/env bash
set -euo pipefail

aws --version
eksctl version
kubectl version --client
helm version --short
terraform version
```

Run it before labs.

### Common Mistakes

- `aws` is using the wrong profile;
- `kubectl` is connected to another cluster context;
- `eksctl` is outdated;
- the chart repository has not been updated;
- Terraform state is stored without a locking/backup strategy in production.

### Questions

1. What is the difference between `aws eks ...` and `kubectl ...`?
2. When should you use `eksctl` and when should you use Terraform?
3. What is stored in kubeconfig?
4. Why does Helm not replace an understanding of the Kubernetes API?

---

# Module 3. AWS Networking: VPC, Subnets, AZ, and VPC CNI

## 3.1 Why EKS Networking Is More Complex Than Docker Networking

In AWS, a Pod can have an IP address from the VPC thanks to Amazon VPC CNI. VPC CNI creates/uses ENIs and assigns VPC addresses or prefixes to Pods. https://docs.aws.amazon.com/eks/latest/best-practices/vpc-cni.html

```text
                     VPC 10.0.0.0/16
                           |
          +----------------+----------------+
          |                                 |
       AZ-a                              AZ-b
          |                                 |
  private subnet                      private subnet
          |                                 |
      EC2 node                          EC2 node
      10.0.1.10                         10.0.2.10
          |                                 |
      Pod 10.0.1.x                      Pod 10.0.2.x
```

## 3.2 Public and Private Subnets

A typical production model:

```text
Internet
   |
 IGW
   |
public subnets
   |
ALB / NAT Gateway
   |
private subnets
   |
EKS nodes + Pods
```

Not everything needs to be accessible from the internet.

## 3.3 Availability Zones

For HA workloads, it is better to plan for multiple AZs:

```text
              Region
     +----------+----------+
     |                     |
    AZ-a                  AZ-b
     |                     |
  nodes/pods            nodes/pods
```

Do not place all replicas in one AZ.

## 3.4 Cluster endpoint

The EKS API server endpoint can be public, private, or a combination with CIDR restrictions. AWS separately documents private-only endpoints and private access from within the VPC. https://docs.aws.amazon.com/eks/latest/userguide/cluster-endpoint.html

Inspect the settings:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION" \
  --query 'cluster.resourcesVpcConfig.{endpointPublicAccess:endpointPublicAccess,endpointPrivateAccess:endpointPrivateAccess,publicAccessCidrs:publicAccessCidrs}'
```

## 3.5 CNI and IP Exhaustion

One common EKS problem:

```text
The Pod does not start
  |
  +--> Scheduler OK
  |
  +--> The node exists
  |
  +--> But VPC CNI cannot allocate an IP
```

Checks:

```bash
kubectl get pods -n kube-system -l k8s-app=aws-node
kubectl describe ds aws-node -n kube-system
kubectl get nodes -o wide
```

## 3.6 NetworkPolicy

By default, inter-Pod traffic is not restricted by the standard Kubernetes NetworkPolicy model. In EKS, VPC CNI supports native network policy with the appropriate configuration. https://aws.github.io/aws-eks-best-practices/security/docs/network/

Example of deny-by-default:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-all-ingress
  namespace: shop
spec:
  podSelector: {}
  policyTypes:
    - Ingress
```

### Practice

1. Find the cluster subnets.
2. Determine which subnets are public/private.
3. Inspect node IPs.
4. Compare Pod IPs and node IPs.
5. Apply a NetworkPolicy only to a test namespace and verify traffic.

### Questions

1. Why is EKS Pod networking connected to the VPC?
2. Why use private subnets for worker nodes?
3. How is a security group different from a NetworkPolicy?
4. What happens when there are not enough Pod IPs?

---

# Module 4. Creating EKS: Auto Mode and Classic EKS

## 4.1 Two Approaches

Today, it is useful to know how to work with both models:

| Model | What matters to understand |
|---|---|
| **EKS Auto Mode** | AWS takes on more infrastructure lifecycle management: compute, networking, load balancing, block storage, and more |
| **Standard EKS + Managed Node Groups** | You gain a better understanding of nodes, add-ons, scaling, and the traditional operating model |

AWS describes Auto Mode as an extension of Kubernetes infrastructure management; the documentation presents it as the recommended way to manage nodes for new scenarios. https://docs.aws.amazon.com/eks/latest/userguide/automode.html

## 4.2 Auto Mode with eksctl

```yaml
# auto-mode-cluster.yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eks-auto-course
  region: eu-central-1

autoModeConfig:
  enabled: true
```

Creation:

```bash
eksctl create cluster -f auto-mode-cluster.yaml
```

`eksctl` supports `autoModeConfig.enabled: true`; when Auto Mode is enabled, AWS/EKS takes on broader management of compute, networking, load balancing, and block storage capabilities. https://docs.aws.amazon.com/eks/latest/eksctl/auto-mode.html

## 4.3 Standard EKS + Managed Node Groups

```yaml
# cluster.yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eks-course
  region: eu-central-1
  version: "1.36"

managedNodeGroups:
  - name: general
    instanceType: m6a.large
    minSize: 2
    desiredCapacity: 2
    maxSize: 4
    privateNetworking: true
    volumeSize: 50
```

Creation:

```bash
eksctl create cluster -f cluster.yaml
```

AWS confirms that Managed Node Groups automate provisioning and the lifecycle of EC2 nodes, including updates and draining. https://docs.aws.amazon.com/eks/latest/userguide/managed-node-groups.html

## 4.4 What to Create Manually

After cluster creation, check:

```bash
kubectl get nodes -o wide
kubectl get pods -A
aws eks describe-cluster --name "$CLUSTER_NAME" --region "$AWS_REGION"
```

Inspect CloudFormation stacks, VPC, subnets, security groups, IAM roles, and EC2.

## 4.5 kubeconfig

```bash
aws eks update-kubeconfig \
  --region "$AWS_REGION" \
  --name "$CLUSTER_NAME"
```

Verification:

```bash
kubectl get nodes
```

## 4.6 Add-ons

Amazon EKS Add-ons let you manage supporting software through the EKS API; AWS validates curated add-ons and recommends managed add-ons instead of self-managed ones where possible. https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html

Inspect:

```bash
aws eks list-addons \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

Versions:

```bash
aws eks describe-addon-versions \
  --addon-name vpc-cni \
  --kubernetes-version 1.36
```

### Practice

1. Create a training Standard cluster.
2. Create a separate Auto Mode cluster if your budget allows.
3. Compare node resources and add-ons.
4. Compare who manages the compute lifecycle.
5. Delete both clusters after the lab.

### Deletion

```bash
eksctl delete cluster --name "$CLUSTER_NAME" --region "$AWS_REGION"
```

> Before deleting anything, verify `kubectl config current-context` and the AWS account.

### Questions

1. How is Auto Mode different from Managed Node Groups?
2. Which parts of the platform can AWS manage in Auto Mode?
3. Why is it useful to learn Standard EKS before using Auto Mode in production?
4. Which AWS resources are created around EKS?

---

# Module 5. Workloads: Pod, Deployment, Service, ConfigMap, Secret

## 5.1 Your First Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: web
          image: nginx:alpine
          ports:
            - containerPort: 80
          resources:
            requests:
              cpu: 100m
              memory: 64Mi
            limits:
              cpu: 500m
              memory: 256Mi
          readinessProbe:
            httpGet:
              path: /
              port: 80
            initialDelaySeconds: 3
            periodSeconds: 5
          livenessProbe:
            httpGet:
              path: /
              port: 80
            initialDelaySeconds: 10
            periodSeconds: 10
```

Apply it:

```bash
kubectl apply -f deployment.yaml
kubectl get deploy
kubectl get pods -l app=web -o wide
```

## 5.2 Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: web
spec:
  selector:
    app: web
  ports:
    - port: 80
      targetPort: 80
  type: ClusterIP
```

Verification:

```bash
kubectl get svc web
kubectl get endpointslice -l kubernetes.io/service-name=web
```

## 5.3 ConfigMap

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: web-config
data:
  APP_ENV: "dev"
  LOG_LEVEL: "info"
```

Inside the Pod:

```yaml
envFrom:
  - configMapRef:
      name: web-config
```

## 5.4 Secret

```bash
kubectl create secret generic db-secret \
  --from-literal=DB_USER=app \
  --from-literal=DB_PASSWORD='change-me'
```

Usage:

```yaml
envFrom:
  - secretRef:
      name: db-secret
```

Do not commit real secret values to Git.

## 5.5 Rollout

```bash
kubectl set image deployment/web web=nginx:1.27-alpine
kubectl rollout status deployment/web
kubectl rollout history deployment/web
kubectl rollout undo deployment/web
```

### Practice

1. Run a Deployment with 3 replicas.
2. Delete one Pod.
3. Update the image.
4. Perform a rollback.
5. Add readiness and liveness probes.
6. Create a ConfigMap and Secret.

### Common Mistakes

- no `resources.requests`;
- incorrect Service selector;
- a liveness probe kills an application that has not started yet;
- secrets are stored in plain text in a Git repository;
- an image without an immutable tag/digest is used in production.

### Questions

1. What is the difference between readiness and liveness?
2. Why is a Deployment better than manually creating Pods?
3. What does a Service selector do?
4. Why is `latest` a poor production tag?

---

# Module 6. IAM and Cluster Access: Access Entries and RBAC

## 6.1 Two Different Questions

Always separate these two questions:

```text
Who can call the AWS API?
        |
       IAM
        |
        +-------------------+
                            |
                   Who can perform
                   Kubernetes actions?
                            |
                           RBAC
```

EKS provides IAM ↔ Kubernetes authentication/authorization integration.

## 6.2 EKS Access Entries

AWS currently recommends EKS Access Entries for granting IAM principals access to the Kubernetes API. The old `aws-auth` ConfigMap is deprecated. https://docs.aws.amazon.com/eks/latest/userguide/access-entries.htmlhttps://docs.aws.amazon.com/eks/latest/userguide/auth-configmap.html

Inspect:

```bash
aws eks list-access-entries \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

Creation:

```bash
aws eks create-access-entry \
  --cluster-name "$CLUSTER_NAME" \
  --principal-arn arn:aws:iam::${AWS_ACCOUNT_ID}:role/DeveloperRole \
  --region "$AWS_REGION"
```

Access Policy:

```bash
aws eks associate-access-policy \
  --cluster-name "$CLUSTER_NAME" \
  --principal-arn arn:aws:iam::${AWS_ACCOUNT_ID}:role/DeveloperRole \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSViewPolicy \
  --access-scope type=namespace,namespaces=shop \
  --region "$AWS_REGION"
```

AWS access policies are Kubernetes permission templates, not IAM permissions. The scope can be limited cluster-wide or to a namespace. https://docs.aws.amazon.com/eks/latest/userguide/access-policies.html

## 6.3 RBAC

Example:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: pod-reader
  namespace: shop
rules:
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["get", "list", "watch"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: pod-reader-binding
  namespace: shop
subjects:
  - kind: Group
    name: developers
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

## 6.4 Least Privilege

Do not grant:

```text
cluster-admin -> to all developers
```

Use:

```text
IAM role
   |
   +--> Access Entry
           |
           +--> View in namespace X
```

### Practice

1. Create the `shop` namespace.
2. Create an access entry for a test role.
3. Grant the View Policy only in `shop`.
4. Verify that access to another namespace is denied.
5. Repeat the same scenario with a Kubernetes Role/RoleBinding.

### Questions

1. What is an Access Entry?
2. How does IAM authorization differ from Kubernetes RBAC?
3. Why should `aws-auth` no longer be the foundation of a new course?
4. What does least privilege mean for EKS access?

---

# Module 7. IAM for Pods: EKS Pod Identity and IRSA

## 7.1 The Problem

Imagine a Pod that needs to read from S3:

```text
Pod -> S3
```

You must not simply put credentials into the image:

```text
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
```

You need temporary credentials and least privilege.

## 7.2 EKS Pod Identity

EKS Pod Identity lets you associate an IAM role with a Kubernetes ServiceAccount; AWS provides the Pod with temporary credentials through EKS Auth and the Pod Identity Agent. AWS describes this as a way to grant workload IAM permissions without storing static credentials in containers. https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html

## 7.3 Installing the Agent

For Standard EKS:

```bash
eksctl create addon \
  --cluster "$CLUSTER_NAME" \
  --name eks-pod-identity-agent \
  --region "$AWS_REGION"
```

## 7.4 Association

Example using the AWS CLI:

```bash
aws eks create-pod-identity-association \
  --cluster-name "$CLUSTER_NAME" \
  --namespace shop \
  --service-account s3-reader \
  --role-arn arn:aws:iam::${AWS_ACCOUNT_ID}:role/ShopS3ReadRole \
  --region "$AWS_REGION"
```

The AWS CLI documents this API as a ServiceAccount ↔ IAM role association; Pod credentials are temporary and automatically rotated. https://docs.aws.amazon.com/cli/latest/reference/eks/create-pod-identity-association.html

## 7.5 ServiceAccount

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: s3-reader
  namespace: shop
```

Deployment:

```yaml
spec:
  template:
    spec:
      serviceAccountName: s3-reader
      containers:
        - name: app
          image: public.ecr.aws/amazonlinux/amazonlinux:2023
          command: ["sh", "-c"]
          args: ["sleep 3600"]
```

## 7.6 IRSA

IRSA = IAM Roles for Service Accounts. This is an older approach that is still used on existing platforms. It uses an OIDC identity provider and an IAM role trust policy.

```text
Pod
 |
 ServiceAccount
 |
 OIDC
 |
 IAM Role
 |
 AWS API
```

For legacy clusters and compatibility, IRSA is important to know. For new architectures, EKS Pod Identity should be considered separately.

## 7.7 Least privilege

Poor approach:

```text
AmazonS3FullAccess
```

Better approach:

```text
s3:GetObject
s3:ListBucket
```

and only the required bucket/prefix.

### Practice

1. Create an S3 bucket for the lab.
2. Create a minimal read-only IAM policy.
3. Create a ServiceAccount.
4. Create a Pod Identity association.
5. Start a Pod with the AWS CLI.
6. Verify `aws s3 ls`.
7. Delete the association and verify that access is gone.

### Common Mistakes

- using IAM user keys in a Secret;
- giving the node role overly broad permissions;
- forgetting the Pod Identity Agent in Standard EKS;
- trusting the wrong IAM role;
- treating IAM and Kubernetes RBAC as one system.

### Questions

1. How is Pod Identity different from a node IAM role?
2. Why do you need a ServiceAccount?
3. Why are static AWS credentials in a Pod an anti-pattern?
4. In which legacy systems will you encounter IRSA?

---

# Module 8. Storage: EBS, EFS, PVC, and Stateful Workloads

## 8.1 Persistent storage

Pods are ephemeral. Therefore:

```text
Pod restart
   |
   +--> the container filesystem may disappear
```

For state, use a PersistentVolume.

## 8.2 PVC

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 20Gi
  storageClassName: gp3
```

Verification:

```bash
kubectl get pvc
kubectl get pv
kubectl get storageclass
```

## 8.3 EBS CSI

The Amazon EBS CSI Driver manages the lifecycle of EBS volumes for Kubernetes volumes. AWS recommends EBS CSI as an EKS add-on; EBS cannot be mounted directly into Fargate Pods. Auto Mode has a separate storage integration. https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html

Inspect the add-on:

```bash
aws eks describe-addon-versions \
  --addon-name aws-ebs-csi-driver \
  --kubernetes-version 1.36
```

Verification:

```bash
kubectl get pods -n kube-system | grep ebs
```

## 8.4 EFS

EFS is useful when storage must be shared and accessible by multiple Pods.

```text
Pod A ---+
         |
Pod B ---+--> EFS
         |
Pod C ---+
```

The AWS EFS CSI driver lets you use EFS as a PersistentVolume; dynamic provisioning requires a supported driver version and IAM permissions. https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html

## 8.5 EBS vs EFS

| Scenario | EBS | EFS |
|---|---:|---:|
| RWO stateful app | ✅ | possible |
| Shared filesystem | ❌ | ✅ |
| Multiple AZs simultaneously | usually through storage semantics, not shared RWO | ✅ |
| DB volume | ✅ | usually no |
| Shared uploads | no | ✅ |

## 8.6 StatefulSet

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: redis
spec:
  serviceName: redis
  replicas: 1
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
        - name: redis
          image: redis:7-alpine
          volumeMounts:
            - name: data
              mountPath: /data
  volumeClaimTemplates:
    - metadata:
        name: data
      spec:
        accessModes: ["ReadWriteOnce"]
        resources:
          requests:
            storage: 10Gi
```

### Practice

1. Create a PVC.
2. Write a file to the volume.
3. Restart the Pod.
4. Verify persistence.
5. Determine which EBS volume appeared in AWS.
6. Compare it with EFS.

### Questions

1. Why do you need a CSI driver?
2. When should you use EBS and when EFS?
3. Why should you not automatically put a database in Kubernetes just because it is possible?
4. How is StatefulSet different from Deployment?

---

# Module 9. Application Networking: Service, ALB, NLB, and Ingress

## 9.1 Service types

```text
ClusterIP   -> cluster only
NodePort    -> node port
LoadBalancer -> external LB
```

## 9.2 AWS Load Balancer Controller

AWS Load Balancer Controller manages AWS Elastic Load Balancers for Kubernetes. Ingress usually creates an ALB, while a LoadBalancer Service creates an NLB in the modern controller-based model. https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html

AWS best practices recommend AWS Load Balancer Controller instead of the legacy Service Controller; in EKS Auto Mode, the corresponding capabilities are provided automatically. https://docs.aws.amazon.com/eks/latest/best-practices/load-balancing.html

## 9.3 NLB Through a Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: api
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: ip
spec:
  type: LoadBalancer
  selector:
    app: api
  ports:
    - port: 80
      targetPort: 8080
```

## 9.4 ALB Through Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: shop
  annotations:
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip
spec:
  ingressClassName: alb
  rules:
    - host: shop.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: web
                port:
                  number: 80
```

The controller watches the Kubernetes resource and creates an AWS LB.

## 9.5 ALB vs NLB

| Characteristic | ALB | NLB |
|---|---|---|
| OSI | L7 | L4 |
| HTTP routing | ✅ | no L7 routing |
| Host/path rules | ✅ | no |
| TCP | limited through features | ✅ |
| Web/API | ✅ | possible |
| Static public IP | no as the primary scenario | Elastic IP options exist in supported modes |

## 9.6 TLS

Production:

```text
Client
  |
HTTPS
  |
ALB/NLB
  |
Target
```

Certificates are generally better managed through ACM, while application secrets should use appropriate secret-management patterns.

### Practice

1. Run a ClusterIP Service.
2. Create a LoadBalancer Service.
3. See which AWS LB was created.
4. Create an Ingress.
5. Configure host/path routing.
6. Add health checks.

### Common Mistakes

- incorrect subnet tags;
- the controller is not installed or has failed;
- the Security Group blocks traffic;
- the Ingress backend points to the wrong Service port;
- DNS points to the wrong place;
- the application listens on `127.0.0.1` instead of the Pod interface.

### Questions

1. When should you use ALB?
2. When do you need NLB?
3. How does Ingress become an AWS ALB?
4. How is a Service selector different from an Ingress rule?

---

# Module 10. Scheduling: requests, limits, probes, taints, affinity

## 10.1 Resources

The scheduler primarily considers requests.

```yaml
resources:
  requests:
    cpu: 500m
    memory: 256Mi
  limits:
    cpu: "1"
    memory: 512Mi
```

Explanation:

```text
requests -> how much the scheduler reserves/considers
limits   -> the upper bound for runtime resource consumption
```

## 10.2 Pending Pod

If a Pod:

```text
Pending
```

First:

```bash
kubectl describe pod <pod-name>
```

Look for:

```text
Events:
  FailedScheduling
```

## 10.3 Taints / tolerations

Node:

```bash
kubectl taint nodes node-1 workload=critical:NoSchedule
```

Pod:

```yaml
tolerations:
  - key: workload
    operator: Equal
    value: critical
    effect: NoSchedule
```

## 10.4 Node labels

```bash
kubectl label node <node-name> workload=compute
```

Pod:

```yaml
nodeSelector:
  workload: compute
```

## 10.5 Affinity

For complex scheduling, use node affinity and Pod affinity/anti-affinity.

## 10.6 Topology spread

```yaml
topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: topology.kubernetes.io/zone
    whenUnsatisfiable: DoNotSchedule
    labelSelector:
      matchLabels:
        app: api
```

This helps prevent all replicas from being placed in one zone.

## 10.7 Probes

Readiness:

```text
Pod is alive
   |
   +--> but not yet ready to accept traffic
```

Liveness:

```text
Pod is stuck
   |
   +--> kubelet should restart the container
```

A startup probe is useful for slow startup so that liveness does not begin killing the application too early.

### Practice

1. Create a Pod with an excessively high memory request.
2. Get it into `Pending`.
3. Find the reason with `describe`.
4. Create a tainted node.
5. Run a Pod without a toleration — get `Pending`.
6. Add the toleration.
7. Add topology spread.

### Questions

1. How does the scheduler choose a node?
2. Why can a Pod be Pending when CPU is available?
3. What is the difference between a taint and a toleration?
4. When should you use affinity?

---

# Module 11. Scaling: HPA, Karpenter, Managed Node Groups, and Auto Mode

## 11.1 Two Levels of Autoscaling

```text
           Workload
              |
             HPA
              |
        more replicas
              |
       Scheduler asks:
         nodes are needed
              |
       Karpenter / MNG / Auto Mode
              |
         more capacity
```

## 11.2 HPA

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: api
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: api
  minReplicas: 2
  maxReplicas: 10
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
```

Verification:

```bash
kubectl get hpa
kubectl describe hpa api
```

## 11.3 The Key Point

HPA without capacity scaling can lead to:

```text
HPA: replicas 2 -> 10
             |
Scheduler: 8 Pods Pending
             |
No new nodes
```

Therefore, a second level is needed.

## 11.4 Managed Node Groups scaling

A node group has min/desired/max. For predictable baseline workloads, this is a simple option.

## 11.5 Karpenter

Karpenter automatically provisions/deprovisions nodes based on unschedulable Pods and their constraints. AWS best practices specifically recommend pinning tested AMIs in production and note that Karpenter is well suited to changing or diverse capacity needs. https://aws.github.io/aws-eks-best-practices/karpenter/

Model:

```text
Pending Pod
   |
Karpenter analyzes:
   - resources
   - zone
   - instance types
   - taints
   - affinity
   - architecture
   |
creates a suitable node
```

## 11.6 NodePool thinking

You define a policy:

```text
NodePool:
  capacity-type = on-demand/spot
  architectures = amd64/arm64
  zones = ...
  instance-family = ...
  limits = ...
```

And the workload influences capacity selection through requests/constraints.

## 11.7 Auto Mode

Auto Mode expands compute-infrastructure automation and includes capabilities for node provisioning, load balancing, storage, and networking. https://docs.aws.amazon.com/eks/latest/userguide/automode.html

## 11.8 When to Use What

| Workload | Approach |
|---|---|
| stable baseline | Managed Node Group |
| sharp spikes | Karpenter / Auto Mode |
| complex instance-type diversity | Karpenter |
| minimal node management | Auto Mode |
| legacy operational model | MNG |

### Practice

1. Configure a Deployment with 2 replicas.
2. Connect HPA.
3. Generate load.
4. Observe replicas increasing.
5. Verify whether you have enough nodes.
6. Try Karpenter on a separate lab cluster.

### Questions

1. Why is HPA not the same as a cluster autoscaler?
2. What does Karpenter do?
3. When is MNG simpler?
4. What does Auto Mode take over?

---

# Module 12. High Availability and Graceful Disruptions

## 12.1 HA Is Not Just 3 Replicas

Bad:

```text
AZ-a
  pod-1
  pod-2
  pod-3
```

Better:

```text
AZ-a      AZ-b      AZ-c
pod-1     pod-2     pod-3
```

## 12.2 PDB

PodDisruptionBudget protects minimum availability during voluntary disruptions.

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: api
spec:
  minAvailable: 2
  selector:
    matchLabels:
      app: api
```

## 12.3 Deployment strategy

```yaml
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1
```

## 12.4 Graceful shutdown

The application should:

1. stop accepting new requests;
2. wait for current requests to finish;
3. terminate within the termination grace period.

```yaml
terminationGracePeriodSeconds: 30
```

## 12.5 Topology spread

Check:

```bash
kubectl get pods -l app=api -o wide
```

And distribution across zones:

```bash
kubectl get nodes -L topology.kubernetes.io/zone
```

## 12.6 Availability Depends on the Application

If the Deployment is HA but the database is a single Pod with no backup, the system is still not HA.

```text
Frontend HA
   |
API HA
   |
DB single point of failure  <-- problem
```

### Practice

1. Run 3 replicas.
2. Spread them across AZs.
3. Add a PDB.
4. Perform a rolling update.
5. Artificially drain a node in a test environment.
6. Check how many Pods remain available.

### Questions

1. What does a PDB protect?
2. Why does a PDB not protect against every failure?
3. Why do you need topology spread?
4. Why is graceful shutdown important behind a Load Balancer?

---

# Module 13. Security: Pod Security, NetworkPolicy, SG, KMS

## 13.1 Defense in depth

```text
AWS IAM
   |
EKS access
   |
RBAC
   |
Pod Security
   |
NetworkPolicy
   |
Security Groups
   |
Application auth
```

No layer replaces another.

## 13.2 Pod Security

Do not run everything as:

```yaml
securityContext:
  privileged: true
```

Basic production mindset:

```yaml
securityContext:
  runAsNonRoot: true
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop: ["ALL"]
```

Not all applications are immediately compatible with these settings — test them.

## 13.3 NetworkPolicy

Example: allow backend only to reach frontend:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-from-frontend
  namespace: shop
spec:
  podSelector:
    matchLabels:
      app: backend
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: frontend
      ports:
        - protocol: TCP
          port: 8080
```

AWS best practices recommend layered security: Kubernetes NetworkPolicy for cluster traffic and Security Groups for AWS/VPC-level traffic. https://aws.github.io/aws-eks-best-practices/security/docs/network/

## 13.4 Security Groups for Pods

EKS supports security groups for individual Pod workloads through VPC CNI. There are enforcing modes `strict` and `standard`; the choice of mode affects networking semantics. https://docs.aws.amazon.com/eks/latest/best-practices/sgpp.html

## 13.5 Secrets encryption

For EKS Kubernetes 1.28+, AWS provides default envelope encryption for Kubernetes API data. When needed, you can use a customer-managed KMS key as an additional control. https://docs.aws.amazon.com/eks/latest/userguide/envelope-encryption.html

Check encryption:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION" \
  --query 'cluster.encryptionConfig'
```

## 13.6 Secrets != password manager

A Kubernetes Secret does not automatically mean:

```text
"the secret is safely stored in Git"
```

In GitOps production, you usually need external secret-management patterns: AWS Secrets Manager/Parameter Store + an operator/controller or another approved approach.

### Practice

1. Run a non-root container.
2. Use a read-only root filesystem.
3. Add a deny-by-default NetworkPolicy.
4. Restrict egress.
5. Check the Pod's IAM permissions.
6. Check KMS/encryption configuration.

### Questions

1. Why is an IAM policy not enough?
2. What does NetworkPolicy restrict?
3. When are SGs for Pods useful?
4. What does envelope encryption do?

---

# Module 14. Observability: logs, metrics, events, traces

## 14.1 Three Main Signals

```text
Logs    -> what happened
Metrics -> how much / how often
Traces  -> where time was spent
```

## 14.2 Kubernetes events

The cheapest diagnostic tool is:

```bash
kubectl get events -A --sort-by=.lastTimestamp
```

For a Pod:

```bash
kubectl describe pod <pod>
```

## 14.3 Logs

```bash
kubectl logs deployment/api
kubectl logs deployment/api --previous
kubectl logs -f deployment/api
```

## 14.4 CloudWatch Observability add-on

AWS provides the `amazon-cloudwatch-observability` add-on for CloudWatch Agent, Container Insights, and Application Signals; modern scenarios support IAM for the add-on through Pod Identity. https://docs.aws.amazon.com/eks/latest/userguide/workloads-add-ons-available-eks.htmlhttps://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Observability-EKS-addon.html

Verification:

```bash
aws eks list-addons \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 14.5 Prometheus

Key Kubernetes metrics:

```text
CPU utilization
Memory working set
Pod restarts
HTTP request rate
HTTP latency
HTTP 5xx
HPA desired/current replicas
Node pressure
Disk usage
```

## 14.6 SLI/SLO mindset

Bad:

```text
CPU < 80%
```

Much more useful:

```text
availability = 99.9%
P95 latency < 300ms
5xx rate < 0.1%
```

## 14.7 EKS Metrics

Minimum for production:

- node CPU/memory;
- Pod restarts;
- Pending pods;
- HPA status;
- API latency/errors;
- LB target health;
- storage usage;
- DNS failures;
- CNI/IP pressure;
- application-level RED/USE metrics.

### Practice

1. Break the image tag and observe `ImagePullBackOff`.
2. Find the cause through events.
3. Enable application logging.
4. Collect CPU/memory metrics.
5. Define two SLOs for the final project.

### Questions

1. How are logs different from metrics?
2. What should you check first for `Pending`?
3. Which SLIs actually reflect user-perceived quality?
4. What is an error budget?

---

# Module 15. Helm, Kustomize, and GitOps

## 15.1 Helm

Create a chart:

```bash
helm create shop-api
```

Main elements:

```text
Chart.yaml
values.yaml
templates/
_helpers.tpl
```

Install:

```bash
helm upgrade --install shop-api ./shop-api \
  --namespace shop \
  --create-namespace
```

## 15.2 Values

```yaml
image:
  repository: 123456789012.dkr.ecr.eu-central-1.amazonaws.com/shop-api
  tag: "1.0.0"

replicaCount: 3
```

Production values:

```text
values-dev.yaml
values-stage.yaml
values-prod.yaml
```

## 15.3 Kustomize

```text
base/
  deployment.yaml
  service.yaml

overlays/
  dev/
  prod/
```

Pros: simple patching without a templating engine.

## 15.4 GitOps

```text
Developer
    |
   Git
    |
  Argo CD
    |
Kubernetes API
    |
  EKS
```

Argo CD install example:

```bash
kubectl create namespace argocd
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm upgrade --install argocd argo/argo-cd -n argocd
```

For production, pin the chart version and use managed configuration.

## 15.5 What to Store in Git

Good:

```text
Deployment manifests
Helm values
NetworkPolicies
RBAC
HPA
PDB
Ingress
```

Bad:

```text
AWS secret keys
DB passwords
production tokens
```

### Practice

1. Package the service into a Helm chart.
2. Create dev/prod values.
3. Move the deployment into Git.
4. Connect Argo CD.
5. Change the image tag in Git and observe the sync.

### Questions

1. How is Helm different from Kustomize?
2. Why does GitOps reduce drift?
3. What should be the source of truth?
4. How should secrets be stored in GitOps?

---

# Module 16. CI/CD: GitHub Actions, ECR, and Deploying to EKS

## 16.1 Pipeline

```text
Git push
   |
GitHub Actions
   |
+-- test
+-- build image
+-- scan
+-- push -> ECR
   |
update image tag / digest
   |
Argo CD
   |
EKS
```

## 16.2 ECR login

```bash
aws ecr get-login-password --region "$AWS_REGION" \
  | docker login \
      --username AWS \
      --password-stdin \
      "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com"
```

Repository:

```bash
aws ecr create-repository \
  --repository-name shop-api \
  --region "$AWS_REGION"
```

Build:

```bash
docker build -t shop-api:git-$GITHUB_SHA .

docker tag shop-api:git-$GITHUB_SHA \
  "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/shop-api:git-$GITHUB_SHA"

docker push \
  "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/shop-api:git-$GITHUB_SHA"
```

## 16.3 GitHub Actions identity

Do not use long-lived AWS access keys when OIDC federation / role assumption can be used.

```text
GitHub Actions
     |
OIDC token
     |
AWS IAM Role
     |
ECR / EKS permissions
```

## 16.4 CD Strategies

| Approach | Advantage | Disadvantage |
|---|---|---|
| `kubectl apply` from CI | simple | CI must have cluster access |
| Helm from CI | convenient | still push-based |
| GitOps | audit + reconciliation | requires a GitOps controller |
| Progressive delivery | safer rollout | more complex |

### Practice

1. Build a Docker image.
2. Push it to ECR.
3. Deploy with Helm.
4. Move the deployment to GitOps.
5. Add rollback.
6. Prevent CI from using admin credentials.

### Questions

1. Why can ECR be a better choice than Docker Hub for AWS workloads in some architectures?
2. How can GitHub Actions obtain AWS credentials without static keys?
3. How does push-based CD differ from pull-based GitOps?
4. Where should deploy permissions policy live?

---

# Module 17. Lifecycle: add-ons, upgrades, and node maintenance

## 17.1 Kubernetes Versions

At the time this course was prepared, EKS standard support includes `1.36`, `1.35`, and `1.34`; `1.33` and older versions are in extended support according to the current AWS table. EKS allows certain versions to remain available longer for an additional cost, but regular upgrades should be planned. https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html

## 17.2 Upgrade control plane

AWS recommends testing the application on the new version first; after an in-place upgrade completes, it may be possible to roll back to the previous minor version within 7 days when the relevant conditions are met. https://docs.aws.amazon.com/eks/latest/userguide/update-cluster.html

For `eksctl`:

```bash
eksctl upgrade cluster \
  --name "$CLUSTER_NAME" \
  --version 1.36 \
  --approve
```

Perform upgrades one minor version at a time.

## 17.3 Upgrade flow

```text
1. Read release notes
2. Test workloads
3. Upgrade control plane
4. Upgrade add-ons
5. Upgrade nodes
6. Validate workloads
7. Monitor errors
```

## 17.4 Add-ons

```bash
aws eks list-addons \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

VPC CNI version:

```bash
aws eks describe-addon \
  --cluster-name "$CLUSTER_NAME" \
  --addon-name vpc-cni \
  --region "$AWS_REGION"
```

AWS Add-ons reduce operational overhead and receive validation/security patches. https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html

## 17.5 Node upgrades

For Managed Node Groups, AWS automates lifecycle management and drains nodes as part of updates. https://docs.aws.amazon.com/eks/latest/userguide/managed-node-groups.html

## 17.6 Upgrade checklist

Before an upgrade:

```bash
kubectl get nodes
kubectl get pods -A
kubectl get pdb -A
kubectl get crd
kubectl get ingress -A
kubectl get events -A --sort-by=.lastTimestamp
```

Save:

- the current version state;
- add-ons versions;
- deprecated APIs;
- backup critical data;
- rollback plan.

### Practice

1. Check the current Kubernetes version.
2. Check the add-ons.
3. Prepare an upgrade checklist.
4. Perform an upgrade on a lab cluster.
5. Compare `kubectl get nodes` before and after.

### Questions

1. Why should you not upgrade the control plane and forget about add-ons?
2. Why should you read the release notes?
3. Why are minor upgrades done one version at a time?
4. What should you check after an upgrade?

---

# Module 18. Troubleshooting and Production Diagnostics

## 18.1 Universal debugging loop

```text
1. What changed?
2. What is broken?
3. At which layer?
4. What do Events say?
5. What do logs say?
6. What does AWS say?
7. Can I reproduce?
8. What is the smallest safe rollback?
```

## 18.2 CrashLoopBackOff

```bash
kubectl get pod
kubectl describe pod <pod>
kubectl logs <pod>
kubectl logs <pod> --previous
```

Check:

- command/args;
- env;
- Secret;
- ConfigMap;
- liveness probe;
- OOMKilled;
- application startup.

## 18.3 ImagePullBackOff

Checks:

```bash
kubectl describe pod <pod>
```

Causes:

```text
wrong image
wrong tag
private ECR access
IAM
network
registry outage
```

## 18.4 Pending

```bash
kubectl describe pod <pod>
kubectl get nodes
kubectl describe node <node>
```

Typical causes:

- insufficient CPU/memory;
- taint;
- affinity;
- topology constraints;
- volume constraints;
- no matching node;
- Karpenter/Auto Mode cannot provision suitable capacity.

## 18.5 Service Is Not Working

```bash
kubectl get svc
kubectl get endpointslice -l kubernetes.io/service-name=api
kubectl get pods -l app=api
```

Check the selector:

```bash
kubectl get svc api -o yaml
kubectl get pods --show-labels
```

## 18.6 DNS

```bash
kubectl get pods -n kube-system | grep coredns
kubectl logs -n kube-system -l k8s-app=kube-dns
```

Test:

```bash
kubectl run dns-test --rm -it --restart=Never \
  --image=busybox:1.36 \
  -- nslookup kubernetes.default
```

## 18.7 IAM

For the Pod:

```bash
kubectl get sa -n shop
```

For Pod Identity:

```bash
aws eks list-pod-identity-associations \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 18.8 AWS Load Balancer

Start with Kubernetes:

```bash
kubectl describe ingress <ingress>
kubectl describe svc <service>
```

Then AWS:

- Load Balancer;
- Target Groups;
- Target health;
- Security Groups;
- subnet placement;
- controller logs.

### Practice: "Break It and Fix It"

Create 10 failure scenarios:

```text
1. Wrong image tag
2. Wrong Service selector
3. Broken readiness probe
4. Too large resource request
5. Missing Secret
6. Wrong ConfigMap key
7. NetworkPolicy deny
8. Broken ingress annotation
9. IAM permission denied
10. Node taint without toleration
```

For each one, record:

```text
Symptom
Layer
Command
Evidence
Root cause
Fix
Prevention
```

### Questions

1. Why is `kubectl get pods` not enough for troubleshooting?
2. What should you read first: logs or events?
3. How do you distinguish a Kubernetes problem from an AWS problem?
4. What should be included in an incident timeline?

---

# Module 19. Production Architecture and Final Project

## 19.1 Final Project

Build a production-like platform for an online store:

```text
                          Internet
                              |
                         Route 53 / DNS
                              |
                        ACM / TLS
                              |
                         ALB / WAF
                              |
                         Ingress
                              |
               +--------------+--------------+
               |                             |
          frontend                         api
               |                             |
               |                         worker
               |                             |
               +-------------+---------------+
                             |
                       Kubernetes Services
                             |
          +------------------+------------------+
          |                  |                  |
         RDS             ElastiCache           S3
          |
       database

EKS:
  Control Plane -> AWS managed
  Compute -> Auto Mode or MNG + Karpenter
  IAM -> Access Entries + Pod Identity
  Storage -> EBS/EFS
  Security -> RBAC + NetworkPolicy + SG + KMS
  Observability -> CloudWatch / Prometheus / OTEL
  Delivery -> GitHub Actions + ECR + GitOps
```

## 19.2 Components

### Namespaces

```text
shop
observability
platform
```

### Workloads

```text
frontend Deployment: 3 replicas
api Deployment: 3 replicas
worker Deployment: 2 replicas
```

### Autoscaling

```text
frontend HPA
api HPA
worker HPA based on an appropriate custom metric/queue depth
```

### HA

- multi-AZ;
- topology spread;
- PDB;
- readiness/liveness/startup probes;
- graceful shutdown.

### Security

- Access Entries;
- Pod Identity;
- non-root containers;
- NetworkPolicy;
- least privilege IAM;
- KMS encryption;
- externalized secrets.

### Ingress

- ALB;
- HTTPS;
- health checks;
- host/path routing.

### Data

- RDS PostgreSQL;
- S3 for object storage;
- EBS for a stateful component, if it is actually needed;
- EFS only where a shared filesystem is required.

### Delivery

```text
PR -> test -> build -> scan -> ECR -> GitOps -> EKS
```

## 19.3 Production checklist

### Infrastructure

- [ ] Terraform state is protected and has a locking strategy
- [ ] VPC multi-AZ
- [ ] private subnets are used for worker capacity where appropriate for the architecture
- [ ] cluster endpoint access is restricted according to the access model
- [ ] IAM roles are used instead of long-lived keys

### Kubernetes

- [ ] resource requests/limits
- [ ] readiness/liveness/startup probes
- [ ] PDB
- [ ] topology spread
- [ ] NetworkPolicy
- [ ] Pod security context
- [ ] immutable image references

### AWS integration

- [ ] Pod Identity
- [ ] ECR
- [ ] Load Balancer Controller or Auto Mode capabilities
- [ ] EBS/EFS CSI as required
- [ ] KMS
- [ ] CloudWatch/metrics/traces

### Operations

- [ ] backups
- [ ] upgrade runbook
- [ ] rollback runbook
- [ ] incident runbook
- [ ] cost review
- [ ] capacity review
- [ ] access review

## 19.4 Minimum SLOs

For the lab, choose:

```text
Availability: 99.9%
API P95 latency: < 300ms
5xx rate: < 0.1%
Recovery objective: documented
```

These are not universally "correct" values — the goal is to learn to choose SLOs deliberately for the workload.

## 19.5 Final Exam

You are ready when you can answer these without hints:

```text
1. What does AWS manage in EKS?
2. How does a Pod get AWS credentials?
3. How does a Service find a Pod?
4. How does an Ingress become an ALB?
5. Why is a Pod Pending?
6. How does HPA differ from node autoscaling?
7. What does Karpenter do?
8. How do you restrict Pod-to-Pod traffic?
9. How do you preserve data after a Pod restart?
10. How do you upgrade EKS without unplanned downtime?
11. How do you troubleshoot CrashLoopBackOff?
12. Why can an application be healthy while the user experience is still poor?
```

---

# AWS CLI + EKS Cheat Sheet

```bash
# identity
aws sts get-caller-identity

# clusters
aws eks list-clusters --region "$AWS_REGION"
aws eks describe-cluster --name "$CLUSTER_NAME" --region "$AWS_REGION"

# kubeconfig
aws eks update-kubeconfig --name "$CLUSTER_NAME" --region "$AWS_REGION"

# add-ons
aws eks list-addons --cluster-name "$CLUSTER_NAME" --region "$AWS_REGION"
aws eks describe-addon-versions --addon-name vpc-cni --kubernetes-version 1.36

# nodes
aws eks list-nodegroups --cluster-name "$CLUSTER_NAME" --region "$AWS_REGION"
aws eks describe-nodegroup --cluster-name "$CLUSTER_NAME" --nodegroup-name general --region "$AWS_REGION"

# access entries
aws eks list-access-entries --cluster-name "$CLUSTER_NAME" --region "$AWS_REGION"
aws eks describe-access-entry --cluster-name "$CLUSTER_NAME" --principal-arn arn:aws:iam::${AWS_ACCOUNT_ID}:role/DeveloperRole --region "$AWS_REGION"

# pod identity
aws eks list-pod-identity-associations --cluster-name "$CLUSTER_NAME" --region "$AWS_REGION"

# ECR
aws ecr describe-repositories --region "$AWS_REGION"
aws ecr get-login-password --region "$AWS_REGION"

# KMS / encryption
aws eks describe-cluster --name "$CLUSTER_NAME" --region "$AWS_REGION" --query 'cluster.encryptionConfig'
```

---

# kubectl Cheat Sheet

```bash
# context
kubectl config get-contexts
kubectl config current-context
kubectl config use-context <context>

# cluster
kubectl get nodes -o wide
kubectl get nodes --show-labels
kubectl cluster-info

# namespaces
kubectl get ns
kubectl create ns shop

# workloads
kubectl get pods -A
kubectl get deploy -A
kubectl get ds -A
kubectl get sts -A
kubectl get jobs -A
kubectl get cronjobs -A

# service/network
kubectl get svc -A
kubectl get ingress -A
kubectl get endpointslice -A

# logs
kubectl logs <pod>
kubectl logs <pod> --previous
kubectl logs -f <pod>

# inspect
kubectl describe pod <pod>
kubectl describe node <node>
kubectl get pod <pod> -o yaml

# rollout
kubectl rollout status deployment/<name>
kubectl rollout history deployment/<name>
kubectl rollout undo deployment/<name>

# scaling
kubectl scale deployment/<name> --replicas=3
kubectl get hpa

# resources
kubectl top nodes
kubectl top pods -A

# events
kubectl get events -A --sort-by=.lastTimestamp

# storage
kubectl get pvc -A
kubectl get pv
kubectl get storageclass

# RBAC
kubectl auth can-i get pods
kubectl auth can-i create deployments -n shop

# network policy
kubectl get networkpolicy -A

# delete one resource
kubectl delete pod <pod>
```

---

# Helm Cheat Sheet

```bash
helm list -A
helm repo list
helm repo update
helm search repo <name>
helm show values <chart>
helm install <release> <chart> -n <namespace> --create-namespace
helm upgrade <release> <chart> -n <namespace>
helm upgrade --install <release> <chart> -n <namespace>
helm history <release> -n <namespace>
helm rollback <release> <revision> -n <namespace>
helm uninstall <release> -n <namespace>
```

---

# Troubleshooting Cheat Sheet

| Symptom | First commands |
|---|---|
| `Pending` | `kubectl describe pod`, `kubectl get nodes` |
| `CrashLoopBackOff` | `kubectl logs`, `kubectl logs --previous`, `kubectl describe pod` |
| `ImagePullBackOff` | `kubectl describe pod`, ECR/IAM checks |
| Service not responding | `kubectl get svc`, `get endpointslice`, labels |
| Ingress not working | `kubectl describe ingress`, controller logs, AWS LB |
| DNS not working | CoreDNS pods/logs + `nslookup` |
| Pod cannot get AWS access | ServiceAccount + Pod Identity + IAM role |
| No Pod IP | VPC CNI + subnet/IP capacity |
| Node NotReady | `kubectl describe node`, kubelet/system events |
| LB unhealthy | target health + app readiness + SG |
| HPA not scaling | metrics availability + requests + HPA status |

---

# EKS Interview Questions

## Junior

### 1. What Is EKS?
Managed Kubernetes service AWS.

### 2. What Is a Pod?
The smallest deployment unit in Kubernetes.

### 3. Why Do You Need a Service?
It provides a stable network endpoint over changing Pod IPs.

### 4. What Is a Deployment?
A controller for declaratively managing stateless Pod replicas and rollouts.

### 5. What Does `kubectl` Do?
It works with the Kubernetes API.

---

## Middle

### 6. What Is the Difference Between IAM and RBAC?
IAM handles AWS identity/authorization; RBAC handles Kubernetes API permissions.

### 7. What Is EKS Pod Identity?
A mechanism for granting IAM permissions to workloads by associating a ServiceAccount with an IAM role.

### 8. Why Do You Need VPC CNI?
So that Pod networking integrates with the AWS VPC.

### 9. Why Is a Pod Pending?
Insufficient resources, constraints, taints, affinity, storage, or lack of suitable node capacity.

### 10. How Does HPA Differ from Karpenter?
HPA changes the number of Pod replicas; Karpenter can change node capacity.

### 11. ALB vs NLB?
ALB — L7 HTTP-aware load balancing; NLB — L4 network load balancing.

### 12. EBS vs EFS?
EBS — block storage, EFS — shared elastic file storage.

---

## Senior

### 13. How Do You Design Multi-AZ EKS?
Spread capacity and replicas across AZs, use topology spread/PDB, and verify dependency topology and managed services.

### 14. How Do You Restrict the Kubernetes API?
Use a private endpoint or restrict public CIDRs according to the access architecture.

### 15. How Do You Give a Pod Access to Only One S3 Prefix?
Use a dedicated IAM role through Pod Identity with a minimal policy and a specific ARN/prefix.

### 16. How Do You Investigate High Latency?
Break the request path into ingress/LB, app, downstreams, DB, network, and metrics/traces; check P95/P99, saturation, and errors.

### 17. What Does Karpenter Do?
It provisions/deprovisions nodes for unschedulable Pod requirements.

### 18. How Do You Prepare an EKS Upgrade?
Study release notes, check deprecated APIs/add-ons/CRDs, test, upgrade the control plane, add-ons, and nodes with observability and a rollback plan.

### 19. Why Are `requests` Critical?
They affect scheduling and QoS, as well as correct HPA/autoscaling behavior and capacity planning.

### 20. How Does Auto Mode Change the Operating Model?
AWS takes on more of the cluster infrastructure lifecycle, reducing the amount of manual compute/networking/storage/load-balancing management.

---

# FAQ

## Do You Need to Know Kubernetes Perfectly First?
No. But the basics of Pod, Deployment, Service, DNS, storage, scheduling, and RBAC must be understood.

## Can You Learn EKS Only Through the AWS Console?
You can start that way, but DevOps/Platform work requires CLI, YAML, `kubectl`, and Infrastructure as Code.

## Do You Need Terraform?
For a production platform — very often yes. For getting started, you can begin with `eksctl`.

## Do You Have to Use Karpenter?
No. It is one option for autoscaling capacity.

## Should You Run a Database Inside EKS?
Not necessarily. Compare the operational consequences with a managed database service.

## Should You Use EKS Auto Mode?
Study Auto Mode and Standard EKS, then choose the model based on requirements for manageability, compatibility, control, and the operating model.

## What Matters More: Security or Cost?
Both matter, but the trade-off is determined by risk and business requirements. The goal of a production platform is not "minimum cost", but predictable cost at the required level of reliability and security.

---

# EKS Glossary

| Term | Meaning |
|---|---|
| EKS | Amazon Elastic Kubernetes Service |
| Control Plane | Kubernetes management components |
| Node | compute node |
| Pod | smallest workload unit |
| Deployment | controller for stateless workloads |
| Service | stable network endpoint |
| Ingress | HTTP routing API |
| ALB | Application Load Balancer |
| NLB | Network Load Balancer |
| CNI | Container Network Interface |
| VPC CNI | AWS networking plugin for Pods |
| MNG | Managed Node Group |
| Auto Mode | EKS infrastructure automation model |
| HPA | Horizontal Pod Autoscaler |
| Karpenter | node provisioning/autoscaling project |
| PDB | PodDisruptionBudget |
| RBAC | Kubernetes Role Based Access Control |
| Access Entry | IAM principal ↔ EKS cluster access mapping |
| Pod Identity | IAM permissions for Kubernetes workloads |
| IRSA | IAM Roles for Service Accounts |
| CSI | Container Storage Interface |
| PVC | PersistentVolumeClaim |
| EBS | Elastic Block Store |
| EFS | Elastic File System |
| ECR | Elastic Container Registry |
| KMS | Key Management Service |
| CRD | Custom Resource Definition |
| GitOps | managing desired state through Git |
| SLO | Service Level Objective |
| SLI | Service Level Indicator |

---

# Official Sources

## AWS EKS

- [Amazon EKS Documentation](https://docs.aws.amazon.com/eks/)
- [What is Amazon EKS?](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)
- [Getting started with EKS](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)
- [Learn EKS by example](https://docs.aws.amazon.com/eks/latest/userguide/learn-eks.html)
- [Kubernetes concepts for EKS](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-concepts.html)

## EKS versions and lifecycle

- [Kubernetes version lifecycle on EKS](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)
- [Kubernetes versions standard support](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions-standard.html)
- [Cluster lifecycle and configuration](https://docs.aws.amazon.com/eks/latest/userguide/clusters.html)
- [Cluster upgrades](https://docs.aws.amazon.com/eks/latest/userguide/update-cluster.html)

## EKS Auto Mode

- [Automate cluster infrastructure with EKS Auto Mode](https://docs.aws.amazon.com/eks/latest/userguide/automode.html)
- [EKS Auto Mode with eksctl](https://docs.aws.amazon.com/eks/latest/eksctl/auto-mode.html)
- [Auto Mode quickstart](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-automode.html)

## Networking

- [Amazon VPC CNI](https://docs.aws.amazon.com/eks/latest/best-practices/vpc-cni.html)
- [Cluster API endpoint](https://docs.aws.amazon.com/eks/latest/userguide/cluster-endpoint.html)
- [Network security best practices](https://aws.github.io/aws-eks-best-practices/security/docs/network/)
- [Security Groups for Pods](https://docs.aws.amazon.com/eks/latest/best-practices/sgpp.html)

## IAM and security

- [EKS Access Entries](https://docs.aws.amazon.com/eks/latest/userguide/access-entries.html)
- [EKS access policies](https://docs.aws.amazon.com/eks/latest/userguide/access-policies.html)
- [EKS Pod Identity](https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html)
- [IRSA / IAM service accounts](https://docs.aws.amazon.com/eks/latest/eksctl/iamserviceaccounts.html)
- [Envelope encryption](https://docs.aws.amazon.com/eks/latest/userguide/envelope-encryption.html)
- [EKS Security Best Practices](https://aws.github.io/aws-eks-best-practices/security/docs/)

## Load balancing and storage

- [AWS Load Balancer Controller](https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html)
- [AWS EKS Load Balancing best practices](https://docs.aws.amazon.com/eks/latest/best-practices/load-balancing.html)
- [EBS CSI](https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html)
- [EFS CSI](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html)
- [EKS Add-ons](https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html)

## Autoscaling and operations

- [EKS Best Practices](https://aws.github.io/aws-eks-best-practices/)
- [Karpenter Best Practices](https://aws.github.io/aws-eks-best-practices/karpenter/)
- [EKS managed node groups](https://docs.aws.amazon.com/eks/latest/userguide/managed-node-groups.html)
- [CloudWatch Observability add-on](https://docs.aws.amazon.com/eks/latest/userguide/workloads-add-ons-available-eks.html)

---

# Final Course Summary

After this course, you should see EKS not as a "Kubernetes cluster in AWS", but as a **platform** made up of several layers:

```text
                 +----------------------+
                 |     Applications     |
                 +----------+-----------+
                            |
                 +----------+-----------+
                 |   Kubernetes API     |
                 | Workloads / Services  |
                 +----------+-----------+
                            |
          +-----------------+-----------------+
          |                 |                 |
        Security       Observability       Delivery
          |                 |                 |
     IAM/RBAC/NP       logs/metrics       GitOps/CI
          |                 |                 |
          +-----------------+-----------------+
                            |
                  EKS infrastructure
                            |
       +--------------------+--------------------+
       |                    |                    |
      VPC               Compute              Storage
       |             Auto Mode / MNG        EBS/EFS
       |                 Karpenter              |
       +--------------------+--------------------+
                            |
                         AWS Cloud
```

The main production skill is not knowing one hundred `kubectl` commands, but understanding **which layer is responsible for the problem, where to look for evidence, and which change is the smallest and safest way to fix it**.

---

## License

MIT — use, modify, fork, and share the course.