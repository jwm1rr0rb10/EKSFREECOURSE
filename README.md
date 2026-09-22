# AWS EKS Course 2026: Free Amazon EKS and Kubernetes-on-AWS Course from Zero to Pro

![EKS 1.36](https://img.shields.io/badge/Amazon%20EKS-1.36-FF9900?logo=amazonwebservices&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-managed-326CE5?logo=kubernetes&logoColor=white)
![Karpenter](https://img.shields.io/badge/Karpenter-autoscaling-blueviolet)
![Free course](https://img.shields.io/badge/price-free-brightgreen)
![Junior to senior](https://img.shields.io/badge/level-junior%20→%20senior-orange)

> **A complete free Amazon EKS course.** Theory and practice, eksctl and Terraform, control plane and data plane, IAM and RBAC, access entries and Pod Identity, managed node groups, Fargate, EKS Auto Mode and Karpenter, VPC CNI and IP addressing, ALB/NLB and Gateway API, EBS/EFS/S3 CSI, secrets, add-ons, observability, security, GitOps, version upgrades, cost and optimization, multi-region and production architecture. All in one README, current for **Amazon EKS 1.36 (September 2026)**.

**EKS learning without filler:** every module gives you clear theory, diagrams, commands you can actually run, the mistakes people really make, and self-check questions. The course works whether you're learning EKS from scratch, preparing for a DevOps, SRE, platform or cloud engineering interview, or designing a production cluster that doesn't wreck your AWS bill.

⚠️ **Warning: EKS costs money.** A cluster is billed from the first minute even with zero workloads: **$0.10 per hour for the control plane** (≈$73/month) plus EC2, EBS, load balancers, NAT Gateway and cross-AZ traffic. Every lab in this course is designed to cost a few dollars at most, but **delete your clusters when you're done**. The teardown commands are at the end of each hands-on module.

⭐ If the course is useful, star the repo so other engineers can find it.

🇷🇺 Russian version: [READMEru.md](READMEru.md)

---

## Who this EKS course is for

| Who you are | What you get |
|---|---|
| **New** to Kubernetes and AWS | What EKS does for you and what it doesn't, and how to get a working cluster in 20 minutes |
| **DevOps / SRE** | Node groups, Karpenter, Auto Mode, zero-downtime upgrades, monitoring, alerts, troubleshooting |
| **Backend developer** | How to deploy a service properly: probes, requests/limits, HPA, Ingress, secrets, access to S3 and RDS without keys |
| **Platform engineer** | Multi-tenancy, GitOps, EKS Blueprints, Terraform modules, platform add-ons, a golden path for product teams |
| **Cloud / infrastructure engineer** | VPC design for EKS, IP addressing, private clusters, PrivateLink, hybrid nodes |
| **Security engineer** | IRSA vs Pod Identity, access entries, Pod Security Standards, network policy, IMDS, KMS, GuardDuty EKS Protection, audit |
| **FinOps / team lead** | Every line item on an EKS bill, Spot, Graviton, right-sizing, and extended support as a $4,380/year trap |
| **Architect** | When EKS, when ECS, when Fargate, when not Kubernetes at all; multi-region and DR |
| **Interview prep** | 40 EKS questions with junior, middle and senior level answers |

## What you'll be able to do after this course

- explain EKS architecture: control plane, data plane, VPC CNI, ENIs, add-ons, the shared responsibility model;
- create clusters three ways — `eksctl`, Terraform and the AWS Console — and understand what happens underneath;
- reason about authentication: IAM roles, **access entries**, the legacy `aws-auth` ConfigMap, `kubeconfig`, RBAC;
- choose compute deliberately: managed node groups, self-managed, Fargate, **EKS Auto Mode**, **Karpenter**;
- write `NodePool` and `NodeClass` for Karpenter, use Spot and Graviton, tune consolidation and disruption budgets;
- scale applications: HPA, metrics-server, KEDA, VPA, PDB, topology spread constraints;
- design networking: subnets, IP addressing, prefix delegation, pod-per-node limits, custom networking, IPv6, security groups for pods;
- expose services with the **AWS Load Balancer Controller** (ALB/NLB), Gateway API, ExternalDNS and ACM;
- attach storage: EBS CSI, EFS CSI, Mountpoint for S3, StorageClass, snapshots, multi-AZ StatefulSets;
- give applications AWS access without keys: **EKS Pod Identity** and IRSA, session policies;
- manage EKS add-ons and upgrade them without downtime;
- set up observability: CloudWatch Container Insights, control plane logs, ADOT/OpenTelemetry, Prometheus and Grafana;
- lock the cluster down: Pod Security Standards, network policies, private endpoint, IMDS blocking, image scanning, GuardDuty;
- build CI/CD and GitOps: ECR, Helm, Argo CD, Flux, EKS Capabilities;
- upgrade a cluster from 1.34 to 1.36 without downtime, using **cluster insights**;
- break down cluster cost line by line and cut it by half or more;
- design multi-AZ and multi-region architecture, DR, and an availability-zone failure plan;
- diagnose the classic failures: `Pending` pods, `ImagePullBackOff`, `CrashLoopBackOff`, `NotReady` nodes, IP exhaustion, `OOMKilled`.

---

## Table of contents

- [Who this EKS course is for](#who-this-eks-course-is-for)
- [What you'll be able to do after this course](#what-youll-be-able-to-do-after-this-course)
- [How to take this course](#how-to-take-this-course)
- [Module 0. What EKS is and why it exists](#module-0-what-eks-is-and-why-it-exists)
- [Module 1. EKS architecture: control plane, data plane, VPC](#module-1-eks-architecture-control-plane-data-plane-vpc)
- [Module 2. Your first cluster: eksctl, Terraform, Console](#module-2-your-first-cluster-eksctl-terraform-console)
- [Module 3. Cluster access: IAM, access entries, RBAC](#module-3-cluster-access-iam-access-entries-rbac)
- [Module 4. Compute: node groups, Fargate, Auto Mode](#module-4-compute-node-groups-fargate-auto-mode)
- [Module 5. Karpenter: node autoscaling done properly](#module-5-karpenter-node-autoscaling-done-properly)
- [Module 6. Scaling applications: HPA, KEDA, VPA, PDB](#module-6-scaling-applications-hpa-keda-vpa-pdb)
- [Module 7. EKS networking: VPC CNI, IP addressing, limits](#module-7-eks-networking-vpc-cni-ip-addressing-limits)
- [Module 8. Exposing services: ALB, NLB, Gateway API, DNS](#module-8-exposing-services-alb-nlb-gateway-api-dns)
- [Module 9. Storage: EBS, EFS, S3 and CSI drivers](#module-9-storage-ebs-efs-s3-and-csi-drivers)
- [Module 10. AWS access from pods: Pod Identity, IRSA, secrets](#module-10-aws-access-from-pods-pod-identity-irsa-secrets)
- [Module 11. EKS add-ons and their lifecycle](#module-11-eks-add-ons-and-their-lifecycle)
- [Module 12. Observability: logs, metrics, traces, alerts](#module-12-observability-logs-metrics-traces-alerts)
- [Module 13. EKS security: from PSS to GuardDuty](#module-13-eks-security-from-pss-to-guardduty)
- [Module 14. CI/CD and GitOps: ECR, Helm, Argo CD](#module-14-cicd-and-gitops-ecr-helm-argo-cd)
- [Module 15. Version upgrades: lifecycle, insights, strategy](#module-15-version-upgrades-lifecycle-insights-strategy)
- [Module 16. EKS cost and optimization](#module-16-eks-cost-and-optimization)
- [Module 17. Reliability, multi-region and DR](#module-17-reliability-multi-region-and-dr)
- [Module 18. EKS in production: architecture and operations](#module-18-eks-in-production-architecture-and-operations)
- [Module 19. Capstone project: a production-grade cluster](#module-19-capstone-project-a-production-grade-cluster)
- [EKS command cheat sheet](#eks-command-cheat-sheet)
- [Settings cheat sheet](#settings-cheat-sheet)
- [Cheat sheet: common failures and fixes](#cheat-sheet-common-failures-and-fixes)
- [EKS interview questions with answers](#eks-interview-questions-with-answers)
- [FAQ: common EKS questions](#faq-common-eks-questions)
- [EKS glossary](#eks-glossary)
- [Official sources and what to read next](#official-sources-and-what-to-read-next)

---

## How to take this course

1. **Go in order.** Modules 0-8 are the foundation: without understanding the control plane, IAM access, nodes, networking and load balancers, everything else is magic and "it works but I don't know why".
2. **Run every command.** EKS is learned with your hands. Reading about subnet IP exhaustion and seeing `failed to assign an IP address to container` in `kubectl describe pod` are different levels of understanding.
3. **Break the cluster.** Terminate nodes in the EC2 console, inflate `requests`, fill a subnet, break IAM permissions. That's how production experience appears.
4. **Watch the bill.** Set up an AWS Budget with a $20 alert. This is part of the job.
5. **Answer the self-check questions out loud**, as if you were in an interview.
6. **Do the capstone project.** It pulls every topic into one system.

**What to install:**

```bash
# AWS CLI v2
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip && unzip -q awscliv2.zip && sudo ./aws/install

# kubectl (within ±1 minor of your cluster version)
curl -LO "https://dl.k8s.io/release/v1.36.0/bin/linux/amd64/kubectl" && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

# eksctl
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz" | tar xz && sudo mv eksctl /usr/local/bin/

# helm
curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# optional, but they make life much easier
brew install kubectx k9s stern   # context switching, TUI, multi-pod logs
```

Check that the AWS CLI sees your account:

```bash
aws sts get-caller-identity
aws configure get region
```

**Versions:** this course targets Amazon EKS **1.36** (available since June 2026). As of September 2026, **1.34, 1.35 and 1.36** are in standard support; 1.33 has moved to extended support and costs $0.60 per hour. Every example works on 1.34+.

**Permissions:** you need an IAM user or role with access to EKS, EC2, VPC, IAM and CloudFormation. In a learning account the easiest path is `AdministratorAccess` — never do that in a real one.

---

# Module 0. What EKS is and why it exists

## 0.1 EKS in plain words

**Amazon EKS (Elastic Kubernetes Service)** is managed Kubernetes on AWS. AWS takes over the **control plane** — `kube-apiserver`, `etcd`, `kube-scheduler`, `kube-controller-manager` — runs it across three availability zones, patches it, backs it up and covers it with a 99.95% SLA (or 99.99% on Provisioned Control Plane). You get an HTTPS endpoint and talk to it with ordinary `kubectl`.

Three things to internalize immediately:

1. **EKS is real Kubernetes**, CNCF-certified. Your Helm charts, operators, CRDs and manifests work unchanged.
2. **AWS manages the control plane only.** Worker nodes, networking, storage, add-ons, applications and security are yours — unless you enable Auto Mode.
3. **EKS is deeply integrated with AWS.** Authentication through IAM, networking through the VPC (every pod gets a real VPC IP), load balancers through ALB/NLB, disks through EBS, service access through roles instead of keys.

An EKS cluster always lives **in your VPC** and **in your account**: AWS creates ENIs in your subnets so the control plane can reach kubelet.

## 0.2 The shared responsibility model

This is the most important table in the module. Half of all interview failures come from not knowing where AWS ends and you begin.

| Layer | Who owns it (regular EKS) | Who owns it (EKS Auto Mode) |
|---|---|---|
| `etcd`, etcd backups, encryption | AWS | AWS |
| `kube-apiserver`, scheduler, controller-manager | AWS | AWS |
| Upgrading the control plane to a new minor | **You trigger it, AWS performs it** | You trigger it, AWS performs it |
| Node AMIs, OS patches, kernel | **You** (managed node groups help) | AWS |
| Node provisioning and scaling | **You** (Cluster Autoscaler / Karpenter) | AWS |
| Core add-ons (CNI, CoreDNS, kube-proxy) | **You** (via EKS add-ons) | AWS |
| CSI drivers, Load Balancer Controller | **You** | AWS |
| VPC and subnet design, IP addressing | **You** | **You** |
| RBAC, network policy, Pod Security | **You** | **You** |
| Applications, images, resources, probes | **You** | **You** |
| Cost and its optimization | **You** | **You** (plus the Auto Mode premium) |

**Takeaway:** "managed Kubernetes" doesn't mean "Kubernetes you don't have to think about". EKS removes about 20% of the work — the nastiest 20%, running etcd — and leaves the other 80%.

## 0.3 The problem EKS solves

You can run Kubernetes on EC2 yourself (kubeadm, kOps, Talos). Then you own:

```
                  +--> etcd: 3 nodes, backups, compaction, defrag, restore
                  |
Your own K8s -----+--> apiserver: certificates, CA rotation, HA, upgrades
                  |
                  +--> scheduler and controller-manager: leader election, monitoring
                  |
                  +--> 24/7 on-call for all of the above
```

In practice a self-run control plane is roughly one full-time engineer plus the incidents people later write postmortems about. An etcd cluster that fell apart at 3am explains the value of EKS better than any marketing slide.

With EKS the picture is:

```
aws eks create-cluster  →  control plane across 3 AZs, ready in ~10 minutes
                           99.95% SLA, patches and backups on AWS
                           $0.10/hour

Your responsibility starts at the nodes:
  nodes → add-ons → applications → observability → security → the bill
```

## 0.4 EKS vs ECS vs Fargate vs self-managed Kubernetes

| Criterion | Amazon EKS | Amazon ECS | Self-managed k8s on EC2 | App Runner / Lambda |
|---|---|---|---|---|
| API | Real Kubernetes | AWS-proprietary | Real Kubernetes | None, PaaS/FaaS |
| Learning curve | Steep | Moderate | Very steep | Gentle |
| Control plane fee | $0.10/hour per cluster | None | Cost of master EC2 instances | None |
| Ecosystem (Helm, operators, CRDs) | Full | None | Full | None |
| Portability to another cloud | High | Zero | High | Zero |
| Who upgrades the control plane | AWS, on your command | AWS, transparently | You | AWS |
| When to choose it | You need Kubernetes: ecosystem, multi-cloud, complex workloads, a platform team | AWS only, simple services, no k8s expertise | Special requirements (custom scheduler, edge, regulated on-prem) | One service, HTTP, no infrastructure appetite |

**Being honest about ECS:** if you have 10 stateless services, you're AWS-only, and nobody on the team knows Kubernetes, ECS is cheaper to operate and will cause fewer incidents. EKS wins when you need the ecosystem (operators, Argo, Istio, Kubeflow), the team already knows Kubernetes, or portability matters.

**Fargate is not an alternative to EKS — it's a compute option inside it.** You can run EKS pods on Fargate (no nodes at all), on EC2, or mix both.

## 0.5 Three compute modes in EKS

```
                         EKS Cluster (control plane from AWS)
                                       |
        +------------------------------+------------------------------+
        |                              |                              |
  Managed node groups            AWS Fargate                   EKS Auto Mode
  EC2 in your account          pods without nodes,          AWS manages nodes
  you patch and scale          per-pod billing              ~12% premium on EC2
  maximum control              maximum simplicity           balance, less toil
```

We'll choose between them in Module 4, once we have the vocabulary for the conversation.

## 0.6 What EKS costs (short version; Module 16 has the full one)

| Bill line | Price (us-east-1, 2026) |
|---|---|
| Control plane, standard support | **$0.10/hour** ≈ $73/month per cluster |
| Control plane, extended support | **$0.60/hour** ≈ $438/month — the price of not upgrading |
| Provisioned Control Plane (XL...8XL) | **On top** of the base fee, for predictable API performance |
| EC2 nodes | Normal EC2 pricing, Spot up to −90% |
| EKS Auto Mode | EC2 + a **~12% premium** on managed instances |
| Fargate | ≈$0.04048 per vCPU-hour and ≈$0.004445 per GB-hour, per second, 1-minute minimum |
| EKS Hybrid Nodes | Per-vCPU fee for nodes outside AWS |
| NAT Gateway | $0.045/hour + $0.045/GB — often **more than the control plane** |
| ALB/NLB | ≈$0.0225/hour + LCUs |
| Cross-AZ traffic | $0.01/GB in each direction |
| EBS gp3 | ≈$0.08/GB-month |

**The classic beginner trap:** "EKS costs $73 a month". A small production cluster actually bills $300-600, and half of it isn't EKS at all — it's NAT Gateway, load balancers, disks and cross-AZ traffic.

## 0.7 Where EKS is used: real scenarios

| Scenario | How EKS is applied |
|---|---|
| **Microservices** | Dozens of services, one delivery path via Helm/Argo, autoscaling on traffic |
| **Monolith migration** | Lift-and-shift into a container, then decompose, ALB in front of the cluster |
| **Batch and data processing** | Spot nodes via Karpenter, Job/CronJob, Argo Workflows, Spark on Kubernetes |
| **AI/ML** | GPU nodes (P/G families), Trainium/Inferentia, Kubeflow, Ray, KServe, GPU sharing |
| **Multi-tenant platform** | Namespace-per-team, quotas, RBAC, golden paths and templates for product teams |
| **Multi-region SaaS** | One cluster per region, ECR replication, Route 53 with health checks |
| **Hybrid and edge** | EKS Hybrid Nodes: on-prem nodes driven by a control plane in AWS |
| **Replacing a hand-built cluster** | Moving off kubeadm clusters to stop being on-call for etcd |

## 0.8 When you don't need EKS

- **One or two stateless HTTP services.** Take ECS Fargate or App Runner: cheaper and simpler, no $73/month cluster idling in the background.
- **Nobody owns the platform.** An EKS estate without an owner becomes a set of clusters on different versions where nobody knows what's running.
- **Purely event-driven, infrequent workloads.** Lambda + SQS wins on both price and operations.
- **You need maximum savings at small scale.** Three dev clusters cost $219/month before a single pod. One cluster with a namespace per environment is cheaper.
- **You need full control of the control plane** (custom apiserver flags, your own scheduler on masters, unusual admission configuration): run your own cluster.

## 0.9 What EKS does NOT do for you

EKS gives you a managed control plane. You design whether the system actually works:

- **requests/limits and probes.** Without them the cluster fails beautifully and unpredictably.
- **VPC design and IP addressing.** A /27 subnet in production is an outage scheduled for next month.
- **IAM and RBAC.** By default the cluster creator is an admin and nobody else can see anything.
- **Version upgrades.** EKS will remind you and eventually force one, but you're the one who breaks API compatibility.
- **Application and PV backups.** AWS backs up etcd; your PersistentVolumes are not included (Velero, EBS snapshots).
- **Cost.** A cluster with no limits and `m5.4xlarge` nodes running three nginx pods will work fine. And bill accordingly.
- **Observability.** Control plane logs are **off by default**.

### Self-check questions

1. What exactly does AWS do for you in EKS, and what stays yours?
2. Why does a cluster cost money even with zero nodes and zero pods?
3. How does extended support differ from standard, and how much more does it cost?
4. When would you choose ECS over EKS?
5. Is Fargate an alternative to EKS or a part of it?

---

# Module 1. EKS architecture: control plane, data plane, VPC

## 1.1 The main diagram

```
                    AWS-managed VPC (invisible to you)
        +---------------------------------------------------------+
        |   kube-apiserver (HA, 3 AZs)   etcd (3 AZs, encrypted)  |
        |   scheduler   controller-manager                        |
        +----------------------------+----------------------------+
                                     |
                       EKS-owned ENIs in your subnets
                       (cross-account ENIs, sg: eks-cluster-sg-*)
                                     |
        ==================== your VPC ============================
        |                            |                           |
   +---------+                 +---------+                 +---------+
   |  AZ a   |                 |  AZ b   |                 |  AZ c   |
   | node 1  |                 | node 2  |                 | node 3  |
   | kubelet |                 | kubelet |                 | ...     |
   | kube-   |                 | ...     |                 |         |
   | proxy   |                 |         |                 |         |
   | VPC CNI |                 |         |                 |         |
   | pods w/ |                 |         |                 |         |
   | VPC IPs |                 |         |                 |         |
   +---------+                 +---------+                 +---------+
        |                            |                           |
   ALB/NLB, EBS, EFS, ECR, Secrets Manager, CloudWatch, S3 ...
```

Key facts about this picture:

- **The control plane lives in an AWS account**, not yours. You can't see those EC2 instances and you can't log into them.
- **The connection is bidirectional.** Your `kubectl` hits the public (or private) apiserver endpoint. The apiserver reaches kubelet (`kubectl logs`, `exec`, webhooks) through **EKS-owned ENIs** in your subnets. That's why EKS requires at least **two subnets in different AZs** at creation time.
- **Every pod gets a real IP from a VPC subnet** (that's the VPC CNI, Module 7). No overlay, no encapsulation by default. Hence all the upsides (performance, security groups, visibility in VPC Flow Logs) and the one big downside: IP addresses run out.

## 1.2 Components you should know by name

| Component | Where it lives | What it does |
|---|---|---|
| `kube-apiserver` | AWS | The single entry point; everything `kubectl` does is HTTP to it |
| `etcd` | AWS | Cluster state; encrypted and backed up by AWS |
| `kubelet` | Your node | Runs containers, reports node status |
| `kube-proxy` | Your node (DaemonSet) | iptables/nftables rules for ClusterIP services |
| **VPC CNI** (`aws-node`) | Your node (DaemonSet) | Gives pods real VPC IPs, manages ENIs |
| **CoreDNS** | Deployment | In-cluster DNS (`svc.cluster.local`) |
| **EKS Pod Identity Agent** | DaemonSet | Hands temporary AWS credentials to pods |
| **AWS Load Balancer Controller** | Deployment (you install it) | Creates ALBs/NLBs from Ingress and Service |
| **EBS/EFS CSI driver** | DaemonSet + controller | Mounts disks into pods |
| **Karpenter** or Cluster Autoscaler | Deployment | Adds and removes nodes |
| `metrics-server` | Deployment (you install it) | `kubectl top` and HPA |

Remember: **`metrics-server` is not installed in EKS by default.** That's the first trick question: "why does `kubectl top nodes` say `error: Metrics API not available`?"

## 1.3 Endpoint access: three modes

How `kubectl` and nodes reach the apiserver is one of the main architectural choices.

| Mode | What it means | When |
|---|---|---|
| **Public** (default) | Endpoint reachable from the internet, restricted by IAM + a CIDR allowlist | Learning, dev |
| **Public + Private** | Reachable from the internet; nodes and pods inside the VPC go privately | The most common production setup |
| **Private only** | Only from the VPC, VPN, Direct Connect or a bastion | Regulated environments, strict policies |

```bash
# restrict public access to your office IP and enable private access
aws eks update-cluster-config --name demo \
  --resources-vpc-config endpointPublicAccess=true,publicAccessCidrs=203.0.113.10/32,endpointPrivateAccess=true
```

**Classic outage:** a team flips the cluster to private-only while CI/CD and all the engineers sit on the internet. The cluster is alive and nobody can manage it. Before switching, prepare an access path: VPN, bastion, self-hosted runners in the VPC, or SSM port forwarding.

## 1.4 What `create-cluster` creates in your account

- **EKS-owned ENIs** in the subnets you passed (one or two per AZ).
- A **cluster security group** `eks-cluster-sg-<name>-<id>` that allows all traffic within itself. Nodes created by managed node groups join it automatically.
- An **OIDC provider** (optional, but required for IRSA).
- A **CloudWatch log group**, if control plane logging is enabled.
- **Access entries** for the cluster creator.

The cluster also gets a **cluster IAM role** — the identity EKS uses to manage resources in your account (ENIs, load balancer cleanup and so on). Nodes get a separate **node IAM role** with policies for ECR, the CNI and SSM.

## 1.5 VPC requirements worth knowing up front

- at least **two subnets in two AZs**; three for production;
- subnets must be big enough: **a /24 is not much for an m5.4xlarge node** (see Module 7);
- tag public subnets with `kubernetes.io/role/elb=1` and private ones with `kubernetes.io/role/internal-elb=1`, or the Load Balancer Controller won't know where to place load balancers;
- nodes need to reach ECR, S3, the EC2 API and the EKS API: either through a NAT Gateway or via **VPC endpoints** (cheaper and more private);
- `enableDnsSupport` and `enableDnsHostnames` enabled;
- don't reuse subnets where RDS, Lambda and ALBs already consume IPs: pods will eat the addresses and the subnet will run dry.

A typical production layout:

```
VPC 10.0.0.0/16
  public subnets    10.0.0.0/20,  10.0.16.0/20,  10.0.32.0/20   (ALBs, NAT GWs)
  private subnets   10.0.64.0/18, 10.0.128.0/18, 10.0.192.0/18  (nodes and pods)
```

The private subnets are deliberately huge: pods consume IPs by the dozens and hundreds.

## 1.6 The first mental model

```
IAM grants the right to talk to the apiserver  →  RBAC grants the right to do things in it
The apiserver schedules pods                   →  Karpenter/node groups supply nodes
VPC CNI gives pods IPs                         →  the subnet must have free IPs
A Service gives a stable ClusterIP             →  Ingress + LBC gives an ALB and a public address
CSI gives a pod a disk                         →  EBS lives in one AZ, never forget it
Pod Identity gives a pod AWS permissions       →  no static keys in secrets
```

Six lines that hold the whole course together. We'll return to each in its own module.

### Self-check questions

1. Why does EKS require at least two subnets in different AZs?
2. What is an EKS-owned ENI and why does it exist?
3. What's the difference between the cluster security group, the cluster IAM role and the node IAM role?
4. What breaks if you switch a cluster to private-only without preparation?
5. Why doesn't `kubectl top nodes` work on a fresh cluster?

---

# Module 2. Your first cluster: eksctl, Terraform, Console

## 2.1 Three ways to create a cluster

| Approach | Pros | Cons | Good for |
|---|---|---|---|
| **eksctl** | One YAML or one command, it just works | CloudFormation underneath, drift from your IaC | Learning, experiments, quick dev clusters |
| **Terraform** (`terraform-aws-modules/eks`) | One IaC story, code review, repeatability | More code, you need to understand dependencies | Production |
| **Console** | You see every field and its meaning | Not reproducible, "who created this?" six months later | Looking at it once with your own eyes |

This course's recommendation: build your first cluster with `eksctl` (to get a result in 20 minutes), your second with Terraform (to understand what it's made of), and go to production with IaC only.

## 2.2 The fastest cluster: EKS Auto Mode

Auto Mode brings up nodes, CSI drivers and the Load Balancer Controller for you. For a first cluster it's the best option: the fewest moving parts.

```bash
eksctl create cluster \
  --name demo-auto \
  --region eu-central-1 \
  --version 1.36 \
  --enable-auto-mode
```

Wait about 15 minutes. What just happened:

```bash
kubectl get nodes                     # empty: no nodes yet, because no pods yet
kubectl get nodepool                  # general-purpose and system, from Auto Mode
kubectl get pods -A
```

Nodes show up when the first pod does:

```bash
kubectl create deployment web --image=public.ecr.aws/nginx/nginx:1.27 --replicas=2
kubectl get pods -w                   # Pending → ContainerCreating → Running
kubectl get nodes                     # a node arrived on its own, in ~1 minute
```

That's the main effect of Auto Mode: **nodes follow pods**, not the other way around.

## 2.3 A classic cluster with a managed node group

This is the cluster you'll most often meet at work. `cluster.yaml`:

```yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: demo
  region: eu-central-1
  version: "1.36"

vpc:
  cidr: 10.0.0.0/16
  clusterEndpoints:
    publicAccess: true
    privateAccess: true
  nat:
    gateway: Single          # for learning: one NAT is cheaper than three

iam:
  withOIDC: true             # needed for IRSA, always turn it on

managedNodeGroups:
  - name: ng-general
    instanceTypes: ["m6i.large", "m6a.large", "m5.large"]
    amiFamily: AmazonLinux2023
    minSize: 2
    maxSize: 6
    desiredCapacity: 2
    volumeSize: 50
    volumeType: gp3
    privateNetworking: true
    labels:
      workload: general
    tags:
      Environment: demo
    iam:
      withAddonPolicies:
        ebs: true
        cloudWatch: true

addons:
  - name: vpc-cni
    version: latest
  - name: coredns
    version: latest
  - name: kube-proxy
    version: latest
  - name: aws-ebs-csi-driver
    version: latest
  - name: eks-pod-identity-agent
    version: latest
  - name: metrics-server
    version: latest

cloudWatch:
  clusterLogging:
    enableTypes: ["api", "audit", "authenticator"]
```

```bash
eksctl create cluster -f cluster.yaml
```

Note four things beginners forget: `withOIDC: true`, multiple `instanceTypes` (otherwise one day there will be no capacity in an AZ), `privateNetworking: true` (nodes shouldn't have public IPs), and an explicit add-on list including `metrics-server`.

## 2.4 The same cluster in Terraform

```hcl
terraform {
  required_version = ">= 1.6"
  required_providers {
    aws = { source = "hashicorp/aws", version = "~> 5.0" }
  }
}

provider "aws" {
  region = "eu-central-1"
}

locals {
  name = "demo-tf"
  tags = { Project = "eks-course", Environment = "demo" }
}

module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "~> 5.0"

  name = "${local.name}-vpc"
  cidr = "10.0.0.0/16"

  azs             = ["eu-central-1a", "eu-central-1b", "eu-central-1c"]
  public_subnets  = ["10.0.0.0/20", "10.0.16.0/20", "10.0.32.0/20"]
  private_subnets = ["10.0.64.0/18", "10.0.128.0/18", "10.0.192.0/18"]

  enable_nat_gateway = true
  single_nat_gateway = true          # production: false, one NAT per AZ

  # without these tags the Load Balancer Controller won't find the subnets
  public_subnet_tags  = { "kubernetes.io/role/elb" = 1 }
  private_subnet_tags = { "kubernetes.io/role/internal-elb" = 1 }

  tags = local.tags
}

module "eks" {
  source  = "terraform-aws-modules/eks/aws"
  version = "~> 20.0"

  cluster_name    = local.name
  cluster_version = "1.36"

  vpc_id     = module.vpc.vpc_id
  subnet_ids = module.vpc.private_subnets

  cluster_endpoint_public_access = true
  enable_irsa                    = true

  # the modern access path: access entries instead of aws-auth
  authentication_mode                      = "API_AND_CONFIG_MAP"
  enable_cluster_creator_admin_permissions = true

  cluster_addons = {
    vpc-cni                = { most_recent = true }
    coredns                = { most_recent = true }
    kube-proxy             = { most_recent = true }
    aws-ebs-csi-driver     = { most_recent = true }
    eks-pod-identity-agent = { most_recent = true }
    metrics-server         = { most_recent = true }
  }

  eks_managed_node_groups = {
    general = {
      instance_types = ["m6i.large", "m6a.large"]
      capacity_type  = "ON_DEMAND"
      ami_type       = "AL2023_x86_64_STANDARD"
      min_size       = 2
      max_size       = 6
      desired_size   = 2
      disk_size      = 50
      labels         = { workload = "general" }
    }
  }

  tags = local.tags
}

output "kubeconfig_command" {
  value = "aws eks update-kubeconfig --name ${module.eks.cluster_name} --region eu-central-1"
}
```

```bash
terraform init && terraform apply
```

## 2.5 Connecting to the cluster

```bash
aws eks update-kubeconfig --name demo --region eu-central-1
kubectl config current-context
kubectl get nodes -o wide
kubectl get pods -A
kubectl cluster-info
```

What `update-kubeconfig` actually does: it writes a context into `~/.kube/config` where the token is produced by calling `aws eks get-token`. In other words, **EKS authentication always goes through your AWS credentials**, not a static certificate.

```yaml
# fragment of ~/.kube/config
users:
- name: arn:aws:eks:eu-central-1:111122223333:cluster/demo
  user:
    exec:
      apiVersion: client.authentication.k8s.io/v1beta1
      command: aws
      args: ["--region", "eu-central-1", "eks", "get-token", "--cluster-name", "demo"]
```

The consequence: if you switch AWS profiles or your role session expires, `kubectl` starts answering `error: You must be logged in to the server (Unauthorized)` even though everything worked a minute ago.

## 2.6 Your first application, from empty cluster to a URL

```bash
kubectl create namespace demo
```

`app.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
  namespace: demo
spec:
  replicas: 3
  selector:
    matchLabels: { app: web }
  template:
    metadata:
      labels: { app: web }
    spec:
      containers:
        - name: nginx
          image: public.ecr.aws/nginx/nginx:1.27
          ports: [{ containerPort: 80 }]
          resources:
            requests: { cpu: 100m, memory: 128Mi }
            limits:   { memory: 256Mi }
          readinessProbe:
            httpGet: { path: /, port: 80 }
            initialDelaySeconds: 3
          livenessProbe:
            httpGet: { path: /, port: 80 }
            initialDelaySeconds: 10
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels: { app: web }
---
apiVersion: v1
kind: Service
metadata:
  name: web
  namespace: demo
spec:
  type: ClusterIP
  selector: { app: web }
  ports: [{ port: 80, targetPort: 80 }]
```

```bash
kubectl apply -f app.yaml
kubectl -n demo get pods -o wide            # note how pods spread across AZs
kubectl -n demo port-forward svc/web 8080:80
curl -s localhost:8080 | head -5
```

We'll give it a public address through an ALB in Module 8: that needs the Load Balancer Controller (or Auto Mode, where it's already there).

## 2.7 The most common day-one mistakes

| Symptom | Cause | What to do |
|---|---|---|
| `error: You must be logged in to the server (Unauthorized)` | A different IAM identity than the cluster creator, or expired credentials | `aws sts get-caller-identity`, then an access entry (Module 3) |
| Nodes never appear in `kubectl get nodes` | No route to the endpoint/internet, missing node role permissions, wrong security group | Check NAT/VPC endpoints and node role policies |
| Pods stuck `Pending` forever | No nodes, no resources, blocked by taints/affinity | `kubectl describe pod` and read the Events to the end |
| `ImagePullBackOff` from ECR | The node role lacks `AmazonEC2ContainerRegistryReadOnly`, or there's no path to ECR | Policy + VPC endpoints for ECR and S3 |
| `couldn't get current server API group list` | Wrong `kubectl` context, or the cluster is already gone | `kubectl config get-contexts` |
| CloudFormation stack `DELETE_FAILED` | Leftover ALBs/ENIs created by controllers | Delete Service type=LoadBalancer and Ingress first, then the cluster |

## 2.8 Deleting the cluster (do this every time)

```bash
# 1. first remove anything that created AWS resources outside the cluster
kubectl delete ingress --all -A
kubectl delete svc --all-namespaces --field-selector spec.type=LoadBalancer
kubectl delete pvc --all -A

# 2. then the cluster
eksctl delete cluster --name demo --region eu-central-1 --wait
# or
terraform destroy
```

Order matters: delete the cluster first and you're left with orphaned ALBs, ENIs and EBS volumes that keep billing, while VPC deletion fails with `DependencyViolation`.

```bash
# verify nothing is left behind
aws eks list-clusters
aws elbv2 describe-load-balancers --query 'LoadBalancers[].LoadBalancerName'
aws ec2 describe-volumes --filters Name=status,Values=available --query 'Volumes[].VolumeId'
```

### Practice

1. Create an Auto Mode cluster, deploy nginx, confirm a node appeared on its own, and time it.
2. Create a second cluster with Terraform and a managed node group, then compare what you had to describe by hand.
3. Break access on purpose: `export AWS_PROFILE=does-not-exist` and read the `kubectl` error text.
4. Delete both clusters and verify via the AWS CLI that no ALBs or volumes remain.

---
# Module 3. Cluster access: IAM, access entries, RBAC

## 3.1 Two permission systems you must keep separate

In EKS every request passes **two checks**:

```
kubectl get pods
   |
   |-- 1. AUTHENTICATION: who are you?  →  AWS IAM (sts, token from aws eks get-token)
   |                                        the apiserver maps an IAM ARN to a k8s identity
   |
   +-- 2. AUTHORIZATION: what may you do?  →  Kubernetes RBAC (Role/ClusterRole)
```

This is the source of the biggest beginner confusion: **`AdministratorAccess` in IAM grants nothing inside the cluster.** You can have the right to delete the entire cluster and still get `Forbidden` on `kubectl get pods`. The reverse also holds: `cluster-admin` in RBAC grants nothing in AWS.

## 3.2 Access entries: the modern way (use it)

The IAM → Kubernetes mapping used to live in the `aws-auth` ConfigMap, where a single typo could lock everyone out. Since 2023 there are **access entries** — a proper EKS API.

```bash
# see who has access
aws eks list-access-entries --cluster-name demo

# the cluster's authentication mode
aws eks describe-cluster --name demo --query 'cluster.accessConfig'
```

Modes (`authenticationMode`):

| Mode | What works |
|---|---|
| `CONFIG_MAP` | Only the old `aws-auth` (legacy) |
| `API_AND_CONFIG_MAP` | Both, access entries take precedence — the safe migration path |
| `API` | Access entries only (the goal) |

The switch is one-way: `CONFIG_MAP` → `API_AND_CONFIG_MAP` → `API`. You can't go back.

```bash
aws eks update-cluster-config --name demo \
  --access-config authenticationMode=API_AND_CONFIG_MAP
```

## 3.3 Granting access: three typical cases

**A platform administrator:**

```bash
aws eks create-access-entry --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/PlatformAdmin \
  --type STANDARD

aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/PlatformAdmin \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSClusterAdminPolicy \
  --access-scope type=cluster
```

**A developer, their own namespace only:**

```bash
aws eks create-access-entry --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/DevTeamA \
  --kubernetes-groups '[]' --type STANDARD

aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/DevTeamA \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy \
  --access-scope type=namespace,namespaces=team-a
```

**Read-only for an on-call engineer or auditor:**

```bash
aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/OnCallViewer \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSViewPolicy \
  --access-scope type=cluster
```

Built-in EKS access policies:

| Policy | What it grants |
|---|---|
| `AmazonEKSClusterAdminPolicy` | Full `cluster-admin` |
| `AmazonEKSAdminPolicy` | Admin, minus some cluster-scoped objects |
| `AmazonEKSEditPolicy` | Create and modify workloads |
| `AmazonEKSViewPolicy` | Read-only |
| `AmazonEKSAdminViewPolicy` | Read, including Secret metadata |
| `AmazonEKSAutoNodePolicy`, `AmazonEKSNetworkingClusterPolicy` and others | Service policies for Auto Mode and controllers |

If the built-ins aren't enough, map the IAM role into your own Kubernetes group and write the RBAC yourself:

```bash
aws eks create-access-entry --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/DataScience \
  --kubernetes-groups 'ds-team' --type STANDARD
```

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: ml
  name: ds-role
rules:
  - apiGroups: ["", "apps", "batch"]
    resources: ["pods", "pods/log", "jobs", "deployments"]
    verbs: ["get", "list", "watch", "create", "delete"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  namespace: ml
  name: ds-binding
subjects:
  - kind: Group
    name: ds-team
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: ds-role
  apiGroup: rbac.authorization.k8s.io
```

## 3.4 Terraform: access entries as code

```hcl
module "eks" {
  # ...
  authentication_mode = "API"

  access_entries = {
    platform_admin = {
      principal_arn = "arn:aws:iam::111122223333:role/PlatformAdmin"
      policy_associations = {
        admin = {
          policy_arn   = "arn:aws:eks::aws:cluster-access-policy/AmazonEKSClusterAdminPolicy"
          access_scope = { type = "cluster" }
        }
      }
    }
    dev_team_a = {
      principal_arn = "arn:aws:iam::111122223333:role/DevTeamA"
      policy_associations = {
        edit = {
          policy_arn   = "arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy"
          access_scope = { type = "namespace", namespaces = ["team-a"] }
        }
      }
    }
  }
}
```

## 3.5 Legacy: the aws-auth ConfigMap

You'll meet this on any cluster older than 2024.

```bash
kubectl -n kube-system get configmap aws-auth -o yaml
```

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: aws-auth
  namespace: kube-system
data:
  mapRoles: |
    - rolearn: arn:aws:iam::111122223333:role/eksctl-demo-nodegroup-ng-NodeInstanceRole
      username: system:node:{{EC2PrivateDNSName}}
      groups: ["system:bootstrappers", "system:nodes"]
    - rolearn: arn:aws:iam::111122223333:role/PlatformAdmin
      username: platform-admin
      groups: ["system:masters"]
  mapUsers: |
    - userarn: arn:aws:iam::111122223333:user/alice
      username: alice
      groups: ["system:masters"]
```

**Three rules for working with `aws-auth`:**

1. **Never edit it without a backup.** `kubectl -n kube-system get cm aws-auth -o yaml > aws-auth.bak.yaml`.
2. **Never delete the node role entry.** Nodes go `NotReady` immediately and won't come back.
3. If you broke it and locked everyone out, recover with an access entry using the IAM identity that created the cluster, or via `--principal-arn` of the creator.

Migration: enable `API_AND_CONFIG_MAP`, create access entries for everyone in `aws-auth`, verify access, empty the ConfigMap, switch to `API`.

## 3.6 Who am I and what can I do

```bash
aws sts get-caller-identity                       # who I am in IAM
kubectl auth whoami                               # who the apiserver thinks I am
kubectl auth can-i --list                         # the full permission list
kubectl auth can-i delete pods -n prod            # one specific check
kubectl auth can-i get secrets -n kube-system --as=system:serviceaccount:demo:default
```

`kubectl auth can-i --as` is the best RBAC debugging tool: it asks the apiserver instead of guessing.

## 3.7 Production access checklist

- `authenticationMode=API`, `aws-auth` empty or containing only node roles;
- no `mapUsers` at all: people come in through SSO roles (IAM Identity Center), not IAM users;
- `system:masters` belongs to at most one break-glass role, and its use is alerted on from CloudTrail;
- CI/CD has a role scoped to specific namespaces, not `cluster-admin`;
- control plane audit logs enabled (`audit`, `authenticator`);
- teams get ServiceAccounts with minimal permissions, and `automountServiceAccountToken: false` where the token isn't needed.

### Self-check questions

1. Why doesn't `AdministratorAccess` in IAM let you run `kubectl get pods`?
2. Why are access entries better than the `aws-auth` ConfigMap?
3. What happens if you delete the node role entry from `aws-auth`?
4. How do you verify a ServiceAccount can't read secrets in `kube-system`?
5. Why is the `authenticationMode` switch irreversible, and what follows from that?

---

# Module 4. Compute: node groups, Fargate, Auto Mode

## 4.1 Four places your pods can live

| Option | Who provisions | Who patches the OS | Billing granularity | Control |
|---|---|---|---|---|
| **Self-managed nodes** | You (ASG, launch template) | You | Per instance | Maximum: your AMI, userdata, kernel |
| **Managed node group** | EKS, from your description | You trigger it, AWS performs it | Per instance | High |
| **AWS Fargate** | AWS, per pod | AWS | **Per pod**, per second | Low: no DaemonSets, no privileged, no GPU |
| **EKS Auto Mode** | AWS (Karpenter inside) | AWS | Per instance + ~12% | Medium: no SSH, nodes live at most 21 days |

## 4.2 Managed node groups: the workhorse

```bash
eksctl create nodegroup \
  --cluster demo \
  --name ng-spot \
  --instance-types m6i.large,m6a.large,m5.large,m5a.large \
  --spot \
  --nodes-min 2 --nodes-max 10 --nodes 3 \
  --node-private-networking \
  --node-volume-type gp3 --node-volume-size 50
```

What a managed node group adds on top of a plain ASG:

- **Graceful drain on update and delete:** EKS cordons and drains the node itself, respecting PodDisruptionBudgets;
- **Automatic cluster join:** the node appears in `kubectl get nodes` without a hand-written `bootstrap.sh`;
- **Node health monitoring:** unhealthy nodes get replaced;
- **Labels and taints at the EKS API level**, visible in the console and Terraform;
- **Spot with multiple instance types and interruption handling.**

The key parameters and why they matter:

```yaml
managedNodeGroups:
  - name: ng-general
    instanceTypes: ["m6i.large", "m6a.large", "m5.large"]   # 3+ types, or you'll hit InsufficientInstanceCapacity one day
    amiFamily: AmazonLinux2023                              # AL2 is no longer built as of 1.33
    spot: false
    minSize: 3
    maxSize: 12
    desiredCapacity: 3
    volumeType: gp3
    volumeSize: 50
    volumeIOPS: 3000
    privateNetworking: true
    maxPodsPerNode: 110                                     # see Module 7 on ENI limits
    updateConfig:
      maxUnavailablePercentage: 25                          # rolling speed during updates
    labels:
      workload: general
    taints: []
    tags:
      k8s.io/cluster-autoscaler/enabled: "true"
```

## 4.3 Spot without the pain

Spot saves up to 90%, but an instance can be reclaimed with 2 minutes' notice. What makes that safe:

1. **Many instance types** (10+ per group) across several AZs — the chance of simultaneous interruption drops sharply;
2. **Workload separation:** stateless and batch on Spot; stateful and system components (CoreDNS, controllers) on On-Demand;
3. **A PodDisruptionBudget** on every important Deployment;
4. **`terminationGracePeriodSeconds`** and proper SIGTERM handling in the application;
5. **Node termination handling** — built into managed node groups and Karpenter; a hand-rolled ASG needs the AWS Node Termination Handler.

```yaml
# route workloads to Spot with labels, keep system components On-Demand
      nodeSelector:
        karpenter.sh/capacity-type: spot
      tolerations:
        - key: workload
          value: batch
          effect: NoSchedule
```

## 4.4 Graviton: 20-40% almost for free

ARM instances (`m7g`, `c7g`, `r7g`) give roughly 20-40% better price-performance. What you need:

```bash
# a multi-architecture image
docker buildx build --platform linux/amd64,linux/arm64 -t <acct>.dkr.ecr.eu-central-1.amazonaws.com/app:1.0 --push .
```

```yaml
      nodeSelector:
        kubernetes.io/arch: arm64
```

Check that all your sidecars, agents and base images have arm64 builds: that's the real migration blocker, not your application.

## 4.5 Fargate in EKS: when and why

Fargate runs **one pod per micro-VM**, with no nodes. You need a Fargate profile that says "pods from namespace X with labels Y go to Fargate":

```bash
eksctl create fargateprofile \
  --cluster demo \
  --name fp-jobs \
  --namespace batch \
  --labels runtime=fargate
```

The limitations that keep Fargate from replacing nodes:

- **no DaemonSets** (so logging and monitoring agents must be sidecars);
- no GPU, no privileged, no hostNetwork, no hostPath;
- roughly 16 vCPU and 120 GB maximum per pod, in fixed resource combinations;
- limited ephemeral storage (20 GB by default, expandable);
- slower pod startup (tens of seconds);
- on steady workloads it's **1.5-2× more expensive than EC2**.

Good fits: infrequent CronJobs, sharp bursts, isolating multi-tenant jobs, and small clusters where you'd rather have no nodes at all.

## 4.6 EKS Auto Mode: nodes as a service

Auto Mode (GA since December 2024) is AWS-packaged Karpenter plus a set of controllers:

- **compute:** provisions and consolidates nodes for unschedulable pods;
- **storage:** EBS CSI included, a `StorageClass` is created automatically;
- **networking:** the Load Balancer Controller is included, ALBs/NLBs are created from Ingress and Service;
- **identity:** the Pod Identity Agent is included;
- **maintenance:** a node lives **at most 21 days** and is replaced with a freshly patched AMI automatically.

```bash
# enable it on an existing cluster
aws eks update-cluster-config --name demo \
  --compute-config enabled=true,nodePools=general-purpose,system \
  --kubernetes-network-config '{"elasticLoadBalancing":{"enabled":true}}' \
  --storage-config '{"blockStorage":{"enabled":true}}'
```

A custom NodePool in Auto Mode (the API differs from stock Karpenter: `eks.amazonaws.com/v1`, not `karpenter.k8s.aws/v1`):

```yaml
apiVersion: eks.amazonaws.com/v1
kind: NodeClass
metadata:
  name: spot-class
spec:
  role: AutoModeNodeRole
  subnetSelectorTerms:
    - tags: { "kubernetes.io/role/internal-elb": "1" }
  securityGroupSelectorTerms:
    - tags: { "aws:eks:cluster-name": "demo" }
  ephemeralStorage:
    size: "80Gi"
    iops: 3000
---
apiVersion: karpenter.sh/v1
kind: NodePool
metadata:
  name: batch
spec:
  template:
    spec:
      nodeClassRef:
        group: eks.amazonaws.com
        kind: NodeClass
        name: spot-class
      requirements:
        - key: karpenter.sh/capacity-type
          operator: In
          values: ["spot"]
        - key: kubernetes.io/arch
          operator: In
          values: ["arm64", "amd64"]
        - key: eks.amazonaws.com/instance-category
          operator: In
          values: ["c", "m", "r"]
      taints:
        - key: workload
          value: batch
          effect: NoSchedule
  limits:
    cpu: "200"
  disruption:
    consolidationPolicy: WhenEmptyOrUnderutilized
    consolidateAfter: 1m
```

**What you give up with Auto Mode:**

- no SSH or SSM onto the node: diagnostics only through the Kubernetes API and logs;
- you can't pin the Karpenter version or enable experimental flags;
- you can't supply your own AMI or userdata;
- DaemonSets that need deep host access (some security agents) may not work;
- a ~12% premium on EC2 that **Savings Plans do not cover**;
- existing load balancers from a self-managed LBC don't transfer: you need a blue-green migration.

**When Auto Mode is the right choice:** a small team with no dedicated platform engineer; a new cluster; workloads that tolerate node replacement. Since July 2026 the GPU premium has been reduced (G family −35%, P family and Trainium −60%), which makes Auto Mode noticeably more attractive for ML.

**When not to choose it:** you already have Karpenter tuned, you need a custom AMI, you need full node control, or your fleet is large enough that 12% equals two engineers' salaries.

## 4.7 How to choose: a decision tree

```
Need a custom AMI / kernel / privileged host agents?
  └── yes → self-managed nodes
  └── no
       ├── Infrequent, isolated workloads with no DaemonSets?  → Fargate
       ├── No dedicated platform engineer, want less toil?     → Auto Mode
       ├── Large fleet, need precise cost and version control? → managed node groups + Karpenter
       └── Classic, simple workloads, small cluster?           → managed node groups
```

Real clusters are almost always a **mix**: an On-Demand managed node group for system components (CoreDNS, controllers, Argo), Karpenter or Auto Mode for applications, Fargate for occasional jobs.

## 4.8 Picking the right node size

| Too small (`t3.medium`) | Too large (`m6i.8xlarge`) |
|---|---|
| Few pods per node because of ENI limits | Losing one node loses a big share of capacity |
| High overhead share (kubelet, DaemonSets, reserved memory) | Poor scaling granularity |
| Burstable (`t`) instances in production cause mysterious slowdowns | Slow drains during upgrades |

A sane baseline: **`m6i.large` to `m6i.2xlarge`** for general purpose; `c` for CPU-bound, `r` for memory-bound, `m7g/c7g` to save money. And keep nodes in **more than one AZ**.

Remember that part of the node is reserved:

```bash
kubectl describe node <node> | grep -A6 "Allocatable"
# on m6i.large (2 vCPU / 8 GB) pods get roughly 1.9 vCPU and ~7 GB
```

## 4.9 Practical commands

```bash
eksctl get nodegroup --cluster demo
aws eks describe-nodegroup --cluster-name demo --nodegroup-name ng-general

# manual scaling
eksctl scale nodegroup --cluster demo --name ng-general --nodes 5

# update node AMIs (rolling, respects PDBs)
eksctl upgrade nodegroup --cluster demo --name ng-general

# take a node out of service
kubectl cordon ip-10-0-70-12.eu-central-1.compute.internal
kubectl drain ip-10-0-70-12.eu-central-1.compute.internal \
  --ignore-daemonsets --delete-emptydir-data --grace-period=60
kubectl uncordon ip-10-0-70-12.eu-central-1.compute.internal
```

### Practice

1. Create a Spot node group with 6+ instance types, deploy 10 replicas, terminate a node manually in the EC2 console and watch pods move.
2. Create a Fargate profile for the `batch` namespace, run a CronJob there, and compare pod startup time with an EC2 node.
3. Enable Auto Mode on a test cluster, create your own Spot+ARM NodePool, deploy a workload and inspect `kubectl get nodeclaims`.
4. Build a multi-arch image and run it on a Graviton node.

---

# Module 5. Karpenter: node autoscaling done properly

## 5.1 Cluster Autoscaler vs Karpenter

| | Cluster Autoscaler | Karpenter |
|---|---|---|
| How it works | Changes the `desired` count of an ASG | Creates EC2 instances directly |
| Instance selection | From the types in a node group | From hundreds of types, matched to the pods |
| Time to a node | Minutes | Tens of seconds |
| Bin-packing | Weak | Strong, with consolidation |
| Spot | Via ASG policies | Native, aware of interruption probability |
| Configuration | A node group per combination | 1-2 NodePools for the whole cluster |
| Verdict | Legacy, still around | The 2026 standard |

If an interviewer asks "how do you scale nodes", the right answer in 2026 is Karpenter (or Auto Mode, which is managed Karpenter).

## 5.2 Installation

```bash
export CLUSTER_NAME=demo
export KARPENTER_VERSION=1.8.0

helm upgrade --install karpenter oci://public.ecr.aws/karpenter/karpenter \
  --version "${KARPENTER_VERSION}" \
  --namespace kube-system \
  --set "settings.clusterName=${CLUSTER_NAME}" \
  --set "settings.interruptionQueue=${CLUSTER_NAME}" \
  --set controller.resources.requests.cpu=1 \
  --set controller.resources.requests.memory=1Gi \
  --wait
```

Karpenter needs: a controller IAM role (via Pod Identity or IRSA), a node IAM role, an SQS queue for Spot interruption events, and EventBridge rules. The easiest path is the ready-made Terraform module `terraform-aws-modules/eks/aws//modules/karpenter`.

Important: **Karpenter itself must not run on the nodes it creates.** Keep it on a small On-Demand managed node group or on Fargate, otherwise you get a chicken-and-egg problem when the whole fleet is recycled.

## 5.3 NodePool and EC2NodeClass

```yaml
apiVersion: karpenter.sh/v1
kind: NodePool
metadata:
  name: default
spec:
  template:
    metadata:
      labels:
        provisioned-by: karpenter
    spec:
      nodeClassRef:
        group: karpenter.k8s.aws
        kind: EC2NodeClass
        name: default
      requirements:
        - key: kubernetes.io/arch
          operator: In
          values: ["amd64", "arm64"]
        - key: karpenter.sh/capacity-type
          operator: In
          values: ["spot", "on-demand"]
        - key: karpenter.k8s.aws/instance-category
          operator: In
          values: ["c", "m", "r"]
        - key: karpenter.k8s.aws/instance-generation
          operator: Gt
          values: ["5"]            # 6th generation and newer only
        - key: topology.kubernetes.io/zone
          operator: In
          values: ["eu-central-1a", "eu-central-1b", "eu-central-1c"]
      expireAfter: 336h            # a node lives 14 days max: fresh AMI and patches
      terminationGracePeriod: 5m
  limits:
    cpu: "1000"
    memory: 1000Gi
  disruption:
    consolidationPolicy: WhenEmptyOrUnderutilized
    consolidateAfter: 30s
    budgets:
      - nodes: "10%"                       # never touch more than 10% of the fleet at once
      - nodes: "0"                         # and don't touch anything during peak hours
        schedule: "0 9 * * mon-fri"
        duration: 10h
  weight: 10
```

```yaml
apiVersion: karpenter.k8s.aws/v1
kind: EC2NodeClass
metadata:
  name: default
spec:
  amiFamily: AL2023
  amiSelectorTerms:
    - alias: al2023@latest
  role: "KarpenterNodeRole-demo"
  subnetSelectorTerms:
    - tags: { "karpenter.sh/discovery": "demo" }
  securityGroupSelectorTerms:
    - tags: { "karpenter.sh/discovery": "demo" }
  blockDeviceMappings:
    - deviceName: /dev/xvda
      ebs:
        volumeSize: 80Gi
        volumeType: gp3
        iops: 3000
        throughput: 125
        encrypted: true
        deleteOnTermination: true
  metadataOptions:
    httpTokens: required           # IMDSv2 mandatory
    httpPutResponseHopLimit: 1     # pods must not reach the node role
  tags:
    Environment: prod
    ManagedBy: karpenter
```

**The `karpenter.sh/discovery` tags on subnets and security groups are mandatory** — without them Karpenter won't know where to launch nodes and will just log that it found no subnets.

## 5.4 How Karpenter thinks

```
1. There are unschedulable (Pending) pods → read their requests, nodeSelector, affinity, topology, taints
2. Compute which instance combination covers them most cheaply
3. Create a NodeClaim → EC2 RunInstances → node joins the cluster (~40 seconds)
4. Periodically: can the workload be packed tighter and nodes removed/replaced (consolidation)
5. Catch Spot interruption events from SQS → drain the node ahead of time
6. Nodes older than expireAfter → replaced gracefully
```

An important consequence: **Karpenter plans against `requests`, not actual usage.** If a service requests 2 CPU and uses 0.3, Karpenter buys hardware for 2 CPU. Most "Karpenter doesn't save money" complaints are inflated requests, not the autoscaler (Modules 6 and 16).

## 5.5 Multiple NodePools for different workloads

```yaml
# expensive steady workloads: On-Demand only
apiVersion: karpenter.sh/v1
kind: NodePool
metadata: { name: system }
spec:
  template:
    spec:
      nodeClassRef: { group: karpenter.k8s.aws, kind: EC2NodeClass, name: default }
      requirements:
        - { key: karpenter.sh/capacity-type, operator: In, values: ["on-demand"] }
        - { key: karpenter.k8s.aws/instance-size, operator: In, values: ["large", "xlarge"] }
      taints:
        - { key: workload, value: system, effect: NoSchedule }
  weight: 100
---
# batch: Spot only, aggressive consolidation
apiVersion: karpenter.sh/v1
kind: NodePool
metadata: { name: batch }
spec:
  template:
    spec:
      nodeClassRef: { group: karpenter.k8s.aws, kind: EC2NodeClass, name: default }
      requirements:
        - { key: karpenter.sh/capacity-type, operator: In, values: ["spot"] }
      taints:
        - { key: workload, value: batch, effect: NoSchedule }
  disruption:
    consolidationPolicy: WhenEmptyOrUnderutilized
    consolidateAfter: 15s
```

`weight` sets priority: the higher it is, the earlier Karpenter tries that pool.

## 5.6 Diagnostics

```bash
kubectl logs -n kube-system deploy/karpenter -f | grep -v "found provisionable pod"
kubectl get nodeclaims
kubectl get nodepools -o wide
kubectl describe nodeclaim <name>

# why a pod isn't scheduling
kubectl describe pod <pod> | sed -n '/Events/,$p'
```

| Symptom | Common cause |
|---|---|
| No nodes created at all | Missing `karpenter.sh/discovery` tags, missing controller role permissions, pool `limits` exhausted |
| `Insufficient capacity` on Spot | Requirements too narrow: add types, generations, AZs |
| Nodes created and immediately deleted | Pods can't start for another reason (image, PVC in another AZ) |
| Nodes replaced too often | Aggressive `consolidateAfter`, no PDBs, short `expireAfter` |
| One node per pod | The pod has huge requests or `requiredDuringScheduling` anti-affinity |

## 5.7 Rules for safe consolidation

- **A PodDisruptionBudget on every important Deployment** — otherwise consolidation can remove all replicas at once;
- **disruption budgets in the NodePool**: no more than 10-20% of the fleet at once, and `nodes: "0"` during peak hours;
- `do-not-disrupt` for special pods:

```yaml
metadata:
  annotations:
    karpenter.sh/do-not-disrupt: "true"
```

- `terminationGracePeriodSeconds` in applications longer than the time needed to finish in-flight requests;
- for stateful workloads on EBS, remember the disk is AZ-bound and add `topology.kubernetes.io/zone` to node requirements.

### Practice

1. Install Karpenter, create a `NodePool` with Spot and ARM, deploy 30 nginx replicas, and inspect which instances it picked and why.
2. Scale down to 2 replicas and watch consolidation: how many nodes went away, and how fast.
3. Add a PDB with `minAvailable: 80%` and repeat: did behaviour change?
4. Set `expireAfter: 30m` and watch nodes get gracefully replaced with fresh ones.
5. Create a pod with `requests.cpu: 6` and find in the Karpenter logs which instance it chose.

---

# Module 6. Scaling applications: HPA, KEDA, VPA, PDB

## 6.1 Four levels of scaling

```
Level 4: multiple clusters / regions   (Module 17)
Level 3: nodes    → Karpenter / Auto Mode / Cluster Autoscaler  (Module 5)
Level 2: pod replicas → HPA, KEDA
Level 1: pod resources → requests/limits, VPA, right-sizing
```

Work from the bottom up. Scaling a misconfigured pod just multiplies the problem.

## 6.2 requests and limits: the four numbers that matter

```yaml
resources:
  requests:
    cpu: 200m        # guarantee and scheduling basis: the scheduler and Karpenter use this
    memory: 256Mi    # memory guarantee
  limits:
    memory: 512Mi    # exceeding it → OOMKilled
    # cpu: deliberately unset
```

Practical rules:

- **Set `requests.cpu`** close to real p50-p70 usage, not "×5 just in case". Inflated requests are the number one cause of an expensive cluster.
- **Better not to set `limits.cpu` at all** for latency-sensitive services: CFS quota throttling produces mysterious latency spikes. The exception is a multi-tenant cluster where you need noisy-neighbour protection.
- **Always set `limits.memory`**, close to `requests.memory`: memory isn't compressible, and without a limit one leaking pod eats the node.
- **`requests.memory == limits.memory`** gives the `Guaranteed` class — the most protected from eviction.

```bash
kubectl top pods -n demo --containers        # actual usage
kubectl -n demo describe pod <pod> | grep -i -A3 "Last State"   # was it OOMKilled?
```

## 6.3 metrics-server: HPA doesn't work without it

```bash
aws eks create-addon --cluster-name demo --addon-name metrics-server
kubectl top nodes
kubectl top pods -A
```

## 6.4 HPA: scaling on CPU and memory

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: web
  namespace: demo
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: web
  minReplicas: 3
  maxReplicas: 30
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70        # percent of requests.cpu, not of a node core
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 0
      policies:
        - type: Percent
          value: 100
          periodSeconds: 30             # may double every 30 seconds
    scaleDown:
      stabilizationWindowSeconds: 300   # scale down slowly to avoid flapping
      policies:
        - type: Percent
          value: 25
          periodSeconds: 60
```

```bash
kubectl -n demo get hpa -w
kubectl -n demo describe hpa web        # read Events and Conditions
```

**The trap:** `averageUtilization: 70` is measured against `requests.cpu`. If requests are inflated 5×, the HPA will never scale the service, no matter the load.

Load test it:

```bash
kubectl -n demo run load --rm -it --image=williamyeh/hey -- \
  -z 120s -c 100 http://web.demo.svc.cluster.local/
```

## 6.5 KEDA: scaling on external events

HPA understands CPU and memory. Real load is usually measured by SQS queue depth, Kafka lag or message counts. That's KEDA.

```bash
helm repo add kedacore https://kedacore.github.io/charts && helm repo update
helm install keda kedacore/keda --namespace keda --create-namespace
```

```yaml
apiVersion: keda.sh/v1alpha1
kind: ScaledObject
metadata:
  name: worker
  namespace: demo
spec:
  scaleTargetRef:
    name: worker
  minReplicaCount: 0                 # scale-to-zero, which HPA can't do
  maxReplicaCount: 50
  pollingInterval: 15
  cooldownPeriod: 120
  triggers:
    - type: aws-sqs-queue
      authenticationRef:
        name: keda-aws-creds
      metadata:
        queueURL: https://sqs.eu-central-1.amazonaws.com/111122223333/jobs
        queueLength: "20"            # one replica per 20 messages
        awsRegion: eu-central-1
```

KEDA supports dozens of sources: SQS, Kafka, RabbitMQ, a Prometheus query, a CloudWatch metric, cron, a Postgres query. For batch workloads, `minReplicaCount: 0` plus Karpenter on Spot is the cheapest combination in EKS.

## 6.6 VPA and right-sizing

VPA picks `requests` for you. Careful: in `Auto` mode it **recreates pods**, which isn't always acceptable.

```yaml
apiVersion: autoscaling.k8s.io/v1
kind: VerticalPodAutoscaler
metadata:
  name: web
  namespace: demo
spec:
  targetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: web
  updatePolicy:
    updateMode: "Off"        # start with recommendations, no auto-apply
```

```bash
kubectl -n demo describe vpa web | sed -n '/Recommendation/,$p'
```

A pragmatic path: keep VPA in `Off` mode as an advisor and decide on `requests` yourself (or via a CI check). Kubernetes 1.33+ has **in-place pod resize** (beta), which will eventually remove the need for restarts.

## 6.7 PodDisruptionBudget: protection during any node replacement

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: web
  namespace: demo
spec:
  minAvailable: 2          # or maxUnavailable: 1 / minAvailable: 80%
  selector:
    matchLabels: { app: web }
```

PDBs affect everything that drains: node group upgrades, Karpenter consolidation, node replacement in Auto Mode, Spot interruption handling. **Without PDBs in EKS you don't get to claim your service is fault-tolerant.**

Be careful with a `minAvailable` equal to the replica count: then drain can't evict any pod and node upgrades hang forever.

## 6.8 Spreading pods across zones and nodes

```yaml
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          labelSelector:
            matchLabels: { app: web }
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels: { app: web }
```

The rule: `DoNotSchedule` across zones (otherwise an AZ failure takes the service down), `ScheduleAnyway` across nodes (otherwise pods sit `Pending` for lack of nodes).

Remember the cost: cross-AZ traffic is $0.01/GB in each direction. For chatty services consider `trafficDistribution: PreferSameZone` (stable since 1.36) on the Service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: api
spec:
  trafficDistribution: PreferSameZone
  selector: { app: api }
  ports: [{ port: 80 }]
```

## 6.9 Probes, without which scaling is meaningless

```yaml
          startupProbe:                 # for slow starts (JVM and friends)
            httpGet: { path: /healthz, port: 8080 }
            failureThreshold: 30
            periodSeconds: 5
          readinessProbe:               # ready to take traffic
            httpGet: { path: /readyz, port: 8080 }
            periodSeconds: 5
            timeoutSeconds: 2
          livenessProbe:                # hung, needs a restart
            httpGet: { path: /healthz, port: 8080 }
            periodSeconds: 10
            failureThreshold: 3
```

Three rules: readiness is always mandatory (without it the ALB pours traffic into unready pods); liveness should check only "the process is alive", never dependencies (otherwise a database outage restarts every application in the cluster); use startupProbe instead of a giant `initialDelaySeconds`.

### Practice

1. Set `requests.cpu: 1000m` on a service that uses 50m, enable an HPA at 70%, and confirm it never scales under load. Fix the requests and repeat.
2. Configure KEDA against SQS, push 1000 messages, and watch replicas rise from zero while Karpenter adds nodes.
3. Add a PDB with `minAvailable: 100%` and try `kubectl drain` on a node: confirm it hangs. Fix it to `maxUnavailable: 1`.
4. Remove the readinessProbe and watch 5xx appear in the ALB target group during a deploy.

---
# Module 7. EKS networking: VPC CNI, IP addressing, limits

## 7.1 The main difference from "regular" Kubernetes

In most clusters pods live in an overlay network (Flannel, Calico VXLAN) with their own address space. In EKS the default is the **Amazon VPC CNI**, and every pod gets a **real IP from a subnet in your VPC**.

```
An m6i.large node:
  ENI #1 (primary)   10.0.70.12   → node IP + up to 9 pod IPs
  ENI #2             10.0.70.45   → up to 10 pod IPs
  ENI #3             10.0.70.98   → up to 10 pod IPs
  ...
  pods are directly visible in the VPC: 10.0.70.31, 10.0.70.55 ...
```

| Pros | Cons |
|---|---|
| No encapsulation: near-zero overhead | **Subnet IP addresses run out** |
| Pods reachable from the VPC, RDS, on-prem via Direct Connect | Pods per node depend on the instance type |
| VPC Flow Logs and security groups for pods work | You need a deliberate CIDR design up front |
| No "magic" when debugging the network | Redoing addressing later is very expensive |

## 7.2 How many pods fit on a node: the ENI formula

```
max_pods = (number of ENIs × (IPs per ENI − 1)) + 2
```

| Instance | ENIs | IPs per ENI | max pods |
|---|---|---|---|
| `t3.small` | 3 | 4 | 11 |
| `t3.medium` | 3 | 6 | 17 |
| `m6i.large` | 3 | 10 | **29** |
| `m6i.xlarge` | 4 | 15 | 58 |
| `m6i.2xlarge` | 4 | 15 | 58 |
| `m6i.4xlarge` | 8 | 30 | 234 (capped at 110 by the k8s recommendation) |

```bash
# exact value for an instance type
curl -s https://raw.githubusercontent.com/awslabs/amazon-eks-ami/master/templates/shared/runtime/eni-max-pods.txt | grep '^m6i.large'
kubectl describe node <node> | grep -i "pods:"
```

**The conclusion that saves you grief:** a `t3.medium` with 17 pods means 6-8 system DaemonSets and almost no room for applications. For real work start at `large` and above.

## 7.3 Prefix delegation: more pods, fewer wasted IPs

With IPv4 prefix delegation an ENI receives **/28 prefixes** (16 addresses) instead of individual IPs.

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_PREFIX_DELEGATION=true
kubectl set env daemonset aws-node -n kube-system WARM_PREFIX_TARGET=1
kubectl rollout status daemonset aws-node -n kube-system
```

The effect: `m6i.large` goes from 29 to 110 pods. The cost: prefixes are allocated whole, so the subnet needs **contiguous /28 blocks**. On a fragmented subnet allocation will fail. Better to enable it on a fresh cluster than on a busy live one.

## 7.4 When you really do run out of IPs

The symptom in `kubectl describe pod`:

```
Warning  FailedCreatePodSandBox  ... failed to assign an IP address to container
```

and in the `aws-node` logs: `InsufficientCidrBlocks` or `no available IP addresses`.

What to do, in ascending order of effort:

1. **Free some up**: delete unused ENIs, lower `WARM_IP_TARGET`/`WARM_ENI_TARGET` (fewer reserved "warm" addresses).
2. **Add a secondary CIDR to the VPC** (for example `100.64.0.0/16` from the CG-NAT reserved range) and move pods there with **custom networking**:

```bash
kubectl set env daemonset aws-node -n kube-system AWS_VPC_K8S_CNI_CUSTOM_NETWORK_CFG=true
kubectl set env daemonset aws-node -n kube-system ENI_CONFIG_LABEL_DEF=topology.kubernetes.io/zone
```

```yaml
apiVersion: crd.k8s.amazonaws.com/v1alpha1
kind: ENIConfig
metadata:
  name: eu-central-1a
spec:
  subnet: subnet-0aaa111            # a subnet from the secondary CIDR
  securityGroups:
    - sg-0cluster
```

With custom networking the node's primary ENI no longer supplies pod IPs, so `max_pods` drops: recalculate and set it explicitly.

3. **Enable prefix delegation** (above) — it also reduces pressure on the EC2 API.
4. **Move to an IPv6 cluster**: addresses are effectively unlimited, and IPv4 remains only for egress via NAT64/DNS64. Limitation: it's a create-time decision, and some legacy tooling isn't ready.
5. As a last resort, **an alternative CNI** (Cilium in overlay mode) — but then you lose some AWS integrations and take on network ownership yourself.

## 7.5 CoreDNS and typical DNS problems

```bash
kubectl -n kube-system get deploy coredns
kubectl -n kube-system logs -l k8s-app=kube-dns --tail=50
```

What actually breaks in the field:

- **CoreDNS at 2 replicas with 200 nodes.** Scale it: roughly one replica per 30-50 nodes, or install the `cluster-proportional-autoscaler`.
- **`ndots: 5`** in the pod's `/etc/resolv.conf`: a query for `api.example.com` first walks several internal suffixes. For chatty services a `dnsConfig` with `ndots: 2` or a trailing-dot FQDN helps.
- **DNS throttling on the node**: enable NodeLocal DNSCache at high query volumes.
- **CoreDNS on Spot nodes** that keep going away. Keep it on On-Demand.

```yaml
      dnsConfig:
        options:
          - name: ndots
            value: "2"
```

## 7.6 Security groups for pods

Sometimes you need a specific pod, not the whole node, to have access to an RDS instance protected by a security group.

```yaml
apiVersion: vpcresources.k8s.aws/v1beta1
kind: SecurityGroupPolicy
metadata:
  name: db-access
  namespace: demo
spec:
  podSelector:
    matchLabels: { role: db-client }
  securityGroups:
    groupIds: ["sg-0rds-client"]
```

It requires `ENABLE_POD_ENI=true` on the VPC CNI and supported (Nitro) instances. Such pods get a **branch ENI**, and their density per node is more limited. Use it surgically, not as a general approach.

## 7.7 Network policies

The VPC CNI supports native network policy (no Calico needed):

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_NETWORK_POLICY=true
```

```yaml
# deny all ingress in a namespace
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
  namespace: demo
spec:
  podSelector: {}
  policyTypes: ["Ingress"]
---
# allow only the frontend to reach api on 8080
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-frontend-to-api
  namespace: demo
spec:
  podSelector:
    matchLabels: { app: api }
  policyTypes: ["Ingress"]
  ingress:
    - from:
        - podSelector:
            matchLabels: { app: frontend }
      ports:
        - protocol: TCP
          port: 8080
```

In 2026 EKS added **Admin Policies** and **Application Network Policies**: the platform team can set cluster-wide rules that product teams can't override with their own NetworkPolicies. That's the right tool for a multi-tenant cluster.

Don't forget egress: without it a pod can reach anything on the internet.

```yaml
# egress: DNS and internal services only
spec:
  podSelector: { matchLabels: { app: api } }
  policyTypes: ["Egress"]
  egress:
    - to: [{ namespaceSelector: { matchLabels: { kubernetes.io/metadata.name: kube-system } } }]
      ports: [{ protocol: UDP, port: 53 }, { protocol: TCP, port: 53 }]
    - to: [{ podSelector: { matchLabels: { app: db } } }]
      ports: [{ protocol: TCP, port: 5432 }]
```

## 7.8 VPC endpoints: privacy and NAT savings

Nodes constantly talk to ECR (images), S3 (image layers), the EC2 API, STS and CloudWatch. Through a NAT Gateway that's $0.045 per gigabyte. Through VPC endpoints it's cheaper and never leaves the AWS network.

A minimal set for a private cluster:

```
Gateway endpoints (free):  s3, dynamodb
Interface endpoints:       ecr.api, ecr.dkr, ec2, sts, elasticloadbalancing,
                           logs, ssm, ssmmessages, ec2messages, eks, eks-auth,
                           autoscaling, secretsmanager, kms
```

```bash
aws ec2 create-vpc-endpoint --vpc-id vpc-0abc --service-name com.amazonaws.eu-central-1.s3 \
  --route-table-ids rtb-0priv1 rtb-0priv2 rtb-0priv3
```

Interface endpoints cost about $0.01/hour each per AZ, so do the math: at low traffic NAT may be cheaper, at high traffic endpoints win decisively.

## 7.9 Network diagnostics

```bash
# DNS from inside the cluster
kubectl run -it --rm netshoot --image=nicolaka/netshoot --restart=Never -- bash
  nslookup web.demo.svc.cluster.local
  dig +short api.example.com
  curl -sv http://web.demo.svc.cluster.local

# how many IPs are left in a subnet
aws ec2 describe-subnets --subnet-ids subnet-0aaa \
  --query 'Subnets[].{Cidr:CidrBlock,Free:AvailableIpAddressCount}'

# CNI state on a node
kubectl -n kube-system logs -l k8s-app=aws-node --tail=100
kubectl -n kube-system exec ds/aws-node -- /app/grpc-health-probe -addr localhost:50051
```

### Self-check questions

1. Why does a pod in EKS get a real VPC IP, and what two consequences follow?
2. How do you compute max pods for `m6i.xlarge`, and what does prefix delegation change?
3. What five options do you have when a subnet runs out of IPs?
4. Why would you use security groups for pods, and what does it cost you?
5. What do VPC endpoints give you besides privacy?

---

# Module 8. Exposing services: ALB, NLB, Gateway API, DNS

## 8.1 Three ways to let traffic in

| Approach | What gets created in AWS | Layer | When |
|---|---|---|---|
| `Service type=LoadBalancer` | **NLB** (L4) | TCP/UDP | gRPC, TCP services, maximum performance, static IPs |
| `Ingress` | **ALB** (L7) | HTTP/HTTPS | Web, path/host routing, WAF, Cognito auth |
| `Gateway API` | ALB or NLB | L4/L7 | The modern standard, the Ingress successor, role separation |

Plain ClusterIP stays for internal service-to-service calls.

## 8.2 The AWS Load Balancer Controller

Without it, `Ingress` in EKS does nothing (in Auto Mode it's already built in).

```bash
# 1. IAM policy
curl -o iam-policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/main/docs/install/iam_policy.json
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam-policy.json

# 2. ServiceAccount + Pod Identity (or IRSA, see Module 10)
eksctl create podidentityassociation \
  --cluster demo \
  --namespace kube-system \
  --service-account-name aws-load-balancer-controller \
  --permission-policy-arns arn:aws:iam::111122223333:policy/AWSLoadBalancerControllerIAMPolicy \
  --role-name AmazonEKSLoadBalancerControllerRole

# 3. Helm
helm repo add eks https://aws.github.io/eks-charts && helm repo update
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=demo \
  --set serviceAccount.create=true \
  --set serviceAccount.name=aws-load-balancer-controller

kubectl -n kube-system get deploy aws-load-balancer-controller
```

## 8.3 Ingress with an ALB: a working example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web
  namespace: demo
  annotations:
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip                 # straight to pods, bypassing NodePort
    alb.ingress.kubernetes.io/listen-ports: '[{"HTTP":80},{"HTTPS":443}]'
    alb.ingress.kubernetes.io/ssl-redirect: "443"
    alb.ingress.kubernetes.io/certificate-arn: arn:aws:acm:eu-central-1:111122223333:certificate/xxxx
    alb.ingress.kubernetes.io/healthcheck-path: /healthz
    alb.ingress.kubernetes.io/healthcheck-interval-seconds: "10"
    alb.ingress.kubernetes.io/success-codes: "200"
    alb.ingress.kubernetes.io/load-balancer-attributes: idle_timeout.timeout_seconds=60
    alb.ingress.kubernetes.io/wafv2-acl-arn: arn:aws:wafv2:...:regional/webacl/prod/xxxx
    alb.ingress.kubernetes.io/group.name: shared-prod         # many Ingresses on one ALB
    alb.ingress.kubernetes.io/tags: Environment=prod,Team=web
spec:
  ingressClassName: alb
  rules:
    - host: app.example.com
      http:
        paths:
          - path: /api
            pathType: Prefix
            backend:
              service: { name: api, port: { number: 80 } }
          - path: /
            pathType: Prefix
            backend:
              service: { name: web, port: { number: 80 } }
```

```bash
kubectl -n demo get ingress web
kubectl -n demo describe ingress web            # controller errors show up here
```

Three annotations worth memorizing:

- **`target-type: ip`** — traffic goes straight to pods. Fewer hops, readiness gates work, no `NodePort` needed. Almost always the right choice.
- **`group.name`** — merges Ingresses from different namespaces into one ALB. Saves $16+/month per Ingress and simplifies DNS.
- **`scheme`** — `internet-facing` (public subnets) or `internal` (private subnets). Hence the subnet tagging requirement.

If the ALB isn't created, check in order: subnet `kubernetes.io/role/elb` tags, controller IAM permissions, `ingressClassName: alb`, controller logs.

## 8.4 NLB through a Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: grpc-api
  namespace: demo
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-type: external
    service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: ip
    service.beta.kubernetes.io/aws-load-balancer-scheme: internet-facing
    service.beta.kubernetes.io/aws-load-balancer-cross-zone-load-balancing-enabled: "true"
    service.beta.kubernetes.io/aws-load-balancer-healthcheck-protocol: tcp
spec:
  type: LoadBalancer
  selector: { app: grpc-api }
  ports:
    - port: 443
      targetPort: 8443
```

Remember: **cross-zone load balancing is off by default on NLBs**, and enabling it makes cross-AZ traffic billable. Without it balancing happens within a zone only, so uneven pod distribution across zones produces skew.

## 8.5 Gateway API: where everything is heading

Ingress-NGINX was retired upstream in March 2026, and the Gateway API became the primary way to describe cluster ingress.

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: prod-gw
  namespace: infra
spec:
  gatewayClassName: alb                 # or amazon-vpc-lattice
  listeners:
    - name: https
      protocol: HTTPS
      port: 443
      tls:
        mode: Terminate
        options:
          alb.ingress.kubernetes.io/certificate-arn: arn:aws:acm:...
      allowedRoutes:
        namespaces: { from: Selector, selector: { matchLabels: { gateway-access: "true" } } }
---
apiVersion: gateway.networking.k8s.io/v1
kind: HTTPRoute
metadata:
  name: api
  namespace: demo
spec:
  parentRefs: [{ name: prod-gw, namespace: infra }]
  hostnames: ["app.example.com"]
  rules:
    - matches: [{ path: { type: PathPrefix, value: /api } }]
      backendRefs:
        - name: api
          port: 80
          weight: 90
        - name: api-canary
          port: 80
          weight: 10
```

The main advantage is **role separation**. The platform team owns the `Gateway`, product teams own their `HTTPRoute`s, and they don't need access to a shared Ingress. Plus canary weights, traffic mirroring and timeouts live in the spec instead of annotations.

If you're on Ingress-NGINX today: the plan is Gateway API or ALB Ingress, and it's not a drop-in replacement — budget engineering time.

## 8.6 DNS and certificates

```bash
# ExternalDNS: creates Route 53 records from Ingress and Service objects
helm repo add external-dns https://kubernetes-sigs.github.io/external-dns
helm install external-dns external-dns/external-dns -n kube-system \
  --set provider=aws \
  --set policy=sync \
  --set txtOwnerId=demo-cluster \
  --set domainFilters[0]=example.com
```

```yaml
metadata:
  annotations:
    external-dns.alpha.kubernetes.io/hostname: app.example.com
```

Certificates: **don't keep TLS secrets in the cluster** when you can get a free ACM certificate and terminate TLS on the ALB/NLB. DNS validation, free auto-renewal, and the private key never leaves AWS.

## 8.7 Deploying without 5xx

Even with a perfect readinessProbe you can serve errors during a deploy: the ALB still holds the pod in its target group while Kubernetes has already removed it. Three things fix this:

```yaml
# 1. readiness gate: a pod is Ready only once the ALB confirms registration
# enabled on the namespace:
#   kubectl label namespace demo elbv2.k8s.aws/pod-readiness-gate-inject=enabled

# 2. a preStop pause so the ALB can take the pod out of rotation
          lifecycle:
            preStop:
              exec:
                command: ["sh", "-c", "sleep 15"]
      terminationGracePeriodSeconds: 60

# 3. a deployment strategy without capacity dips
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1
```

```yaml
# plus a Service/Ingress annotation for faster deregistration
    alb.ingress.kubernetes.io/target-group-attributes: deregistration_delay.timeout_seconds=30
```

## 8.8 What it costs

| Resource | Price |
|---|---|
| ALB | ~$0.0225/hour (≈$16/month) + LCUs (≈$0.008/LCU-hour) |
| NLB | ~$0.0225/hour + NLCUs |
| Every Ingress without `group.name` | **its own ALB, its own $16/month** |
| Cross-zone traffic through the LB | $0.01/GB |

Hence the rule: **merge Ingresses with `group.name`**, don't create one load balancer per service.

### Practice

1. Install the Load Balancer Controller and expose two services through a single ALB using `group.name`.
2. Add an ACM certificate and `ssl-redirect`, then verify `curl -I http://...` returns 301.
3. Do the same with the Gateway API using 90/10 canary weights and confirm the request split.
4. Deploy under load (`hey -z 60s`) first without preStop and readiness gates, then with them, and compare the 5xx count.
5. Wire up ExternalDNS and confirm the record appears in Route 53.

---

# Module 9. Storage: EBS, EFS, S3 and CSI drivers

## 9.1 Which to choose

| Option | Access mode | AZ scope | Latency | Price (ballpark) | Use for |
|---|---|---|---|---|---|
| **EBS (gp3)** | ReadWriteOnce, one pod | **One AZ only** | Very low | ~$0.08/GB-month | Databases, Kafka, Elasticsearch, any StatefulSet |
| **EFS** | ReadWriteMany, many pods and AZs | Regional | Medium | ~$0.30/GB-month (+ throughput) | Shared files, uploads, legacy apps needing a shared disk |
| **Mountpoint for S3** | Many pods, read and append | Regional | High | ~$0.023/GB-month | Datasets, models, artifacts, logs |
| **FSx for Lustre** | ReadWriteMany, high bandwidth | AZ | Low | Expensive | HPC, ML training |
| **emptyDir / local NVMe** | Pod/node only | Node | Minimal | Included in instance price | Cache, temp files, scratch |

**EBS rule number one:** the disk exists in a single availability zone. A pod with that PVC can only be scheduled **in that AZ**. That's the source of every "the pod is Pending but there are nodes" story.

## 9.2 EBS CSI: StorageClass and PVC

```bash
aws eks create-addon --cluster-name demo --addon-name aws-ebs-csi-driver
```

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp3
  annotations:
    storageclass.kubernetes.io/is-default-class: "true"
provisioner: ebs.csi.aws.com
volumeBindingMode: WaitForFirstConsumer      # critical: the disk is created in the pod's AZ, not at random
allowVolumeExpansion: true
reclaimPolicy: Delete                        # often Retain in production
parameters:
  type: gp3
  iops: "3000"
  throughput: "125"
  encrypted: "true"
  kmsKeyId: arn:aws:kms:eu-central-1:111122223333:key/xxxx
```

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data
  namespace: demo
spec:
  accessModes: ["ReadWriteOnce"]
  storageClassName: gp3
  resources:
    requests:
      storage: 20Gi
```

**`volumeBindingMode: WaitForFirstConsumer` is the single most important line in this module.** With `Immediate` the disk is created in a random AZ and the pod may later find no nodes there.

Expanding a volume live:

```bash
kubectl -n demo patch pvc data -p '{"spec":{"resources":{"requests":{"storage":"50Gi"}}}}'
kubectl -n demo get pvc data -w      # FileSystemResizePending → Bound
```

Shrinking isn't possible — create a new PVC and copy the data.

## 9.3 StatefulSets and storage

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: pg
  namespace: demo
spec:
  serviceName: pg
  replicas: 3
  selector: { matchLabels: { app: pg } }
  template:
    metadata:
      labels: { app: pg }
    spec:
      terminationGracePeriodSeconds: 120
      containers:
        - name: pg
          image: postgres:17
          volumeMounts:
            - { name: data, mountPath: /var/lib/postgresql/data }
          resources:
            requests: { cpu: 500m, memory: 2Gi }
            limits:   { memory: 2Gi }
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          labelSelector: { matchLabels: { app: pg } }
  volumeClaimTemplates:
    - metadata: { name: data }
      spec:
        accessModes: ["ReadWriteOnce"]
        storageClassName: gp3
        resources: { requests: { storage: 100Gi } }
```

Things to remember:

- each replica gets **its own** PVC, pinned to its AZ forever;
- deleting a StatefulSet **leaves the PVCs** behind (data protection, but also a source of forgotten charges);
- Kubernetes 1.32+ can automatically clean up StatefulSet-created PVCs on deletion;
- you can't simply replace such a node in another AZ: Karpenter must be given the zone requirement.

**And the real question:** do you need a database in Kubernetes at all? AWS has RDS, Aurora, ElastiCache, MSK and OpenSearch. Running stateful systems in-cluster makes sense when there's a mature operator and a team that can operate it. Otherwise a managed service is cheaper in total cost, even if the list price looks higher.

## 9.4 EFS: shared access across AZs

```bash
aws eks create-addon --cluster-name demo --addon-name aws-efs-csi-driver
```

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: efs
provisioner: efs.csi.aws.com
parameters:
  provisioningMode: efs-ap            # an access point per PVC
  fileSystemId: fs-0abc123
  directoryPerms: "700"
  uid: "1000"
  gid: "1000"
reclaimPolicy: Retain
```

```yaml
spec:
  accessModes: ["ReadWriteMany"]
  storageClassName: efs
  resources: { requests: { storage: 5Gi } }   # a formality for EFS, it's elastic
```

EFS needs a security group allowing NFS (2049) from the nodes and a mount target in every AZ. Mind the price: EFS Standard is 3-4× the cost of EBS per gigabyte, so enable Lifecycle Management (tiering to Infrequent Access).

## 9.5 Mountpoint for Amazon S3

```bash
aws eks create-addon --cluster-name demo --addon-name aws-mountpoint-s3-csi-driver
```

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: models
spec:
  capacity: { storage: 1200Gi }
  accessModes: ["ReadWriteMany"]
  csi:
    driver: s3.csi.aws.com
    volumeHandle: models-volume
    volumeAttributes:
      bucketName: my-ml-models
      mountOptions: "allow-delete,region eu-central-1"
```

This is not a general-purpose filesystem: no partial file overwrites, no `rename` in the usual sense, and high latency. Ideal for "read a dataset or a model", bad for "a database or logs with fsync".

## 9.6 Snapshots and backups

```bash
# the CSI snapshotter has to be installed separately in EKS
kubectl apply -k "github.com/kubernetes-csi/external-snapshotter/client/config/crd"
kubectl apply -k "github.com/kubernetes-csi/external-snapshotter/deploy/kubernetes/snapshot-controller"
```

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshotClass
metadata: { name: ebs-snapclass }
driver: ebs.csi.aws.com
deletionPolicy: Retain
---
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata: { name: data-2026-09-21, namespace: demo }
spec:
  volumeSnapshotClassName: ebs-snapclass
  source: { persistentVolumeClaimName: data }
```

For full cluster backups (manifests plus PVs) use **Velero** or **AWS Backup**:

```bash
velero install --provider aws --bucket my-velero-bucket \
  --backup-location-config region=eu-central-1 \
  --snapshot-location-config region=eu-central-1 \
  --plugins velero/velero-plugin-for-aws:v1.10.0

velero backup create prod-daily --include-namespaces prod --wait
velero restore create --from-backup prod-daily
```

**AWS backs up etcd; your data is not included.** That distinction is worth saying out loud in an interview.

## 9.7 Common storage problems

| Symptom | Cause | Fix |
|---|---|---|
| Pod `Pending` with `volume node affinity conflict` in Events | PVC in one AZ, free nodes in another | `WaitForFirstConsumer`, nodes in all AZs, zone topology in the NodePool |
| PVC stuck `Pending` | No CSI driver, missing driver role permissions, no StorageClass | `kubectl get sc`, check `ebs-csi-controller` logs |
| `Multi-Attach error` | Someone is attaching an EBS volume to two pods | EBS is RWO; use EFS or a single pod |
| Volume won't expand | `allowVolumeExpansion: false` | Fix the StorageClass (existing PVs must be recreated) |
| Forgotten volumes on the bill | `reclaimPolicy: Retain` plus deleted namespaces | `aws ec2 describe-volumes --filters Name=status,Values=available` |

### Practice

1. Create a `gp3 StorageClass` with `WaitForFirstConsumer`, run a 3-replica Postgres StatefulSet, and check which AZs the disks landed in.
2. Deliberately set `volumeBindingMode: Immediate`, remove nodes in one AZ, and produce a `volume node affinity conflict`.
3. Expand a PVC from 20 to 40 GB without restarting the pod.
4. Take a VolumeSnapshot, delete the PVC, and restore the data from the snapshot.
5. Mount EFS and run two pods in different AZs writing to the same file.

---

# Module 10. AWS access from pods: Pod Identity, IRSA, secrets

## 10.1 Three ways to give a pod AWS permissions

| Approach | How it works | Status |
|---|---|---|
| **Node role (instance profile)** | The pod takes node credentials from IMDS | **Anti-pattern**: every pod gets all node permissions |
| **IRSA** (IAM Roles for Service Accounts) | Cluster OIDC provider, `AssumeRoleWithWebIdentity`, an annotation on the ServiceAccount | Works, mature, still needed for cross-account cases |
| **EKS Pod Identity** | An agent DaemonSet and an association at the EKS API level | **The recommended default** since 2023 |

## 10.2 EKS Pod Identity: the modern path

```bash
aws eks create-addon --cluster-name demo --addon-name eks-pod-identity-agent
```

A role with a trust policy for the `pods.eks.amazonaws.com` service:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Principal": { "Service": "pods.eks.amazonaws.com" },
    "Action": ["sts:AssumeRole", "sts:TagSession"]
  }]
}
```

```bash
aws iam create-role --role-name AppS3Role \
  --assume-role-policy-document file://trust.json

aws iam attach-role-policy --role-name AppS3Role \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# associate the role with a ServiceAccount
aws eks create-pod-identity-association \
  --cluster-name demo \
  --namespace demo \
  --service-account app-sa \
  --role-arn arn:aws:iam::111122223333:role/AppS3Role
```

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: app-sa
  namespace: demo
# no annotations needed, unlike IRSA
```

Verify from a pod:

```bash
kubectl -n demo run aws-cli --rm -it --image=public.ecr.aws/aws-cli/aws-cli \
  --overrides='{"spec":{"serviceAccountName":"app-sa"}}' -- sts get-caller-identity
```

Why Pod Identity beats IRSA:

- one role works across **multiple clusters**, with no OIDC issuer list in the trust policy;
- no OIDC provider and no provider ARN in every role;
- no ServiceAccount annotations: the link lives in the EKS API and is visible via `aws eks list-pod-identity-associations`;
- supports **session policies** — you can narrow one association's permissions without creating a new role;
- session tags: policies can use `eks-cluster-name`, `kubernetes-namespace`, `kubernetes-service-account`.

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::my-bucket/*",
    "Condition": {
      "StringEquals": { "aws:PrincipalTag/kubernetes-namespace": "prod" }
    }
  }]
}
```

## 10.3 IRSA: when it's still required

```bash
eksctl utils associate-iam-oidc-provider --cluster demo --approve

eksctl create iamserviceaccount \
  --cluster demo \
  --namespace demo \
  --name app-sa \
  --attach-policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess \
  --approve
```

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: app-sa
  namespace: demo
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::111122223333:role/AppS3Role
```

An IRSA trust policy is tied to a specific OIDC provider and `sub`:

```json
{
  "Condition": {
    "StringEquals": {
      "oidc.eks.eu-central-1.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE:sub":
        "system:serviceaccount:demo:app-sa"
    }
  }
}
```

IRSA is still needed: for Fargate pods (you can't run the Pod Identity Agent DaemonSet there), for accessing **another AWS account** from the cluster, and for compatibility with older charts.

## 10.4 Blocking pod access to the node role

As long as a pod can reach IMDS, it can steal the node's permissions. Close it:

```yaml
# in the EC2NodeClass (Karpenter) or the launch template
  metadataOptions:
    httpTokens: required            # IMDSv2
    httpPutResponseHopLimit: 1      # a request from a container won't get through
    httpEndpoint: enabled
```

And verify IMDS doesn't answer from a pod:

```bash
kubectl run t --rm -it --image=curlimages/curl -- \
  curl -s --max-time 3 http://169.254.169.254/latest/meta-data/iam/security-credentials/
# expect a timeout
```

## 10.5 Secrets: where to keep them

| Option | Pros | Cons |
|---|---|---|
| Kubernetes Secret | Simple, works everywhere | base64, not encryption; lives in etcd; must never reach Git |
| **Secrets Store CSI + AWS provider** | Secret mounted as a file, rotation, nothing in etcd | Needs the driver; the app reads a file |
| **External Secrets Operator** | Secrets Manager/SSM values synced into K8s Secrets | The secret does end up in etcd |
| Reading Secrets Manager from app code | Full control | Requires the AWS SDK in the application |

Enable etcd envelope encryption with your own KMS key at cluster creation:

```bash
aws eks create-cluster ... \
  --encryption-config '[{"resources":["secrets"],"provider":{"keyArn":"arn:aws:kms:eu-central-1:111122223333:key/xxxx"}}]'
```

**Secrets Store CSI:**

```bash
helm repo add secrets-store-csi-driver https://kubernetes-sigs.github.io/secrets-store-csi-driver/charts
helm install csi-secrets-store secrets-store-csi-driver/secrets-store-csi-driver -n kube-system \
  --set syncSecret.enabled=true --set enableSecretRotation=true
kubectl apply -f https://raw.githubusercontent.com/aws/secrets-store-csi-driver-provider-aws/main/deployment/aws-provider-installer.yaml
```

```yaml
apiVersion: secrets-store.csi.x-k8s.io/v1
kind: SecretProviderClass
metadata:
  name: app-secrets
  namespace: demo
spec:
  provider: aws
  parameters:
    objects: |
      - objectName: "prod/db/credentials"
        objectType: "secretsmanager"
        jmesPath:
          - path: "username"
            objectAlias: "DB_USER"
          - path: "password"
            objectAlias: "DB_PASS"
---
# in the pod
      volumes:
        - name: secrets
          csi:
            driver: secrets-store.csi.k8s.io
            readOnly: true
            volumeAttributes:
              secretProviderClass: app-secrets
      containers:
        - name: app
          volumeMounts:
            - { name: secrets, mountPath: /mnt/secrets, readOnly: true }
```

**External Secrets Operator:**

```yaml
apiVersion: external-secrets.io/v1beta1
kind: SecretStore
metadata: { name: aws-sm, namespace: demo }
spec:
  provider:
    aws:
      service: SecretsManager
      region: eu-central-1
      auth:
        jwt:
          serviceAccountRef: { name: eso-sa }
---
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata: { name: db, namespace: demo }
spec:
  refreshInterval: 1h
  secretStoreRef: { name: aws-sm, kind: SecretStore }
  target: { name: db-secret }
  data:
    - secretKey: password
      remoteRef: { key: prod/db/credentials, property: password }
```

## 10.6 AWS access checklist

- not a single `AWS_ACCESS_KEY_ID` in manifests, charts or environment variables;
- Pod Identity (or IRSA) for every service that needs AWS, **each with its own role**, not one shared role;
- least-privilege policies: specific actions, specific ARNs, namespace conditions;
- `httpPutResponseHopLimit: 1` and IMDSv2 on every node;
- etcd secret encryption with your own KMS key;
- `automountServiceAccountToken: false` for pods that never call the Kubernetes API;
- secret rotation in Secrets Manager and `enableSecretRotation` in the CSI driver.

### Practice

1. Create a role and a Pod Identity association, then read an S3 object from a pod without any keys.
2. Add an `aws:PrincipalTag/kubernetes-namespace` condition to the policy and confirm a pod in another namespace gets `AccessDenied`.
3. Block IMDS (`hopLimit: 1`) and verify the pod can no longer see node credentials.
4. Install the Secrets Store CSI driver and mount a Secrets Manager secret as a file.
5. Do the same thing with IRSA and write down how the trust policies differed.

---
# Module 11. EKS add-ons and their lifecycle

## 11.1 What an EKS add-on is

An add-on is a cluster component whose version is managed by the EKS API rather than your Helm releases. AWS builds it, tests compatibility with the Kubernetes version, patches CVEs, and can upgrade it without touching your charts.

```bash
# what's available
aws eks describe-addon-versions --kubernetes-version 1.36 \
  --query 'addons[].addonName' --output table

# what's installed
aws eks list-addons --cluster-name demo
aws eks describe-addon --cluster-name demo --addon-name vpc-cni
```

| Add-on | Required | What it does |
|---|---|---|
| `vpc-cni` | Yes | Pod networking |
| `coredns` | Yes | DNS |
| `kube-proxy` | Yes | Service rules |
| `eks-pod-identity-agent` | Practically yes | AWS credentials for pods |
| `aws-ebs-csi-driver` | If you use PVCs | EBS volumes |
| `aws-efs-csi-driver` | As needed | Shared file volumes |
| `metrics-server` | Practically yes | `kubectl top`, HPA |
| `amazon-cloudwatch-observability` | Recommended | Container Insights, logs, the agent |
| `aws-mountpoint-s3-csi-driver` | As needed | S3 as a volume |
| `snapshot-controller` | If you need snapshots | VolumeSnapshot |
| `adot` (OpenTelemetry) | As needed | Metrics and traces |
| `aws-guardduty-agent` | Recommended in production | Runtime threat monitoring |
| `cert-manager`, `external-dns`, Argo CD and others | Marketplace add-ons | Some are already available as EKS add-ons |

## 11.2 Installation and configuration

```bash
aws eks create-addon --cluster-name demo --addon-name vpc-cni \
  --addon-version v1.20.0-eksbuild.1 \
  --resolve-conflicts OVERWRITE \
  --pod-identity-associations 'serviceAccount=aws-node,roleArn=arn:aws:iam::111122223333:role/VpcCniRole'
```

Add-on configuration is set with JSON, not `kubectl set env` (otherwise an add-on upgrade will overwrite your edits):

```bash
aws eks update-addon --cluster-name demo --addon-name vpc-cni \
  --configuration-values '{
    "env": {
      "ENABLE_PREFIX_DELEGATION": "true",
      "WARM_PREFIX_TARGET": "1",
      "ENABLE_POD_ENI": "true",
      "ENABLE_NETWORK_POLICY": "true"
    },
    "nodeAgent": { "enablePolicyEventLogs": "true" }
  }' \
  --resolve-conflicts PRESERVE
```

```bash
# inspect the allowed configuration schema
aws eks describe-addon-configuration --addon-name vpc-cni \
  --addon-version v1.20.0-eksbuild.1 --query configurationSchema --output text | jq .
```

`--resolve-conflicts`:

- `NONE` — fail on conflict (safe, but requires manual work);
- `OVERWRITE` — replace your manual edits with AWS values;
- `PRESERVE` — keep the fields you changed.

## 11.3 Add-on upgrade order

The correct sequence during a cluster upgrade:

```
1. Upgrade the control plane (1.35 → 1.36)
2. Upgrade add-ons to versions compatible with 1.36
   order: kube-proxy → vpc-cni → coredns → CSI → the rest
3. Upgrade nodes (AMIs for 1.36)
4. Verify applications
```

`kube-proxy` must not be newer than the control plane and not more than two minors behind the nodes. Upgrade `vpc-cni` before the nodes: a new CNI on an old kernel is usually fine, an old CNI on new nodes is not.

```bash
# which versions are compatible
aws eks describe-addon-versions --kubernetes-version 1.36 --addon-name coredns \
  --query 'addons[].addonVersions[].{v:addonVersion,default:compatibilities[0].defaultVersion}'

aws eks update-addon --cluster-name demo --addon-name coredns \
  --addon-version v1.12.4-eksbuild.1 --resolve-conflicts PRESERVE

aws eks wait addon-active --cluster-name demo --addon-name coredns
```

## 11.4 Add-on or Helm: how to choose

| Take an EKS add-on | Take Helm |
|---|---|
| The component is on the add-on list | You need a specific version that add-ons don't offer |
| You want AWS to track CVEs and compatibility | You need chart settings the schema doesn't expose |
| You want versions in one place (`list-addons`) | The component belongs in your GitOps repo |
| You'd rather not keep values in Git | You need a custom image or patches |

A pragmatic compromise: base infrastructure (CNI, CoreDNS, kube-proxy, CSI, Pod Identity, metrics-server) as add-ons via Terraform; everything application-adjacent (controllers, Argo, monitoring) via Helm and GitOps.

## 11.5 EKS Capabilities: a managed platform

Since late 2025 AWS offers **EKS Capabilities** — fully managed platform components:

- **Argo CD** — continuous delivery, with AWS handling upgrades and scaling;
- **ACK (AWS Controllers for Kubernetes)** — creating AWS resources (S3, RDS, SQS) from Kubernetes manifests;
- **kro (Kubernetes Resource Orchestrator)** — composing reusable infrastructure templates as your own APIs.

Convenient if your platform team is small: you don't have to run Argo CD in HA yourself. The downside is an extra bill line and less control over versions. Enable it deliberately and keep a feature flag in your IaC defaulting to `false` so it never gets turned on by accident.

## 11.6 Terraform for add-ons

```hcl
resource "aws_eks_addon" "vpc_cni" {
  cluster_name             = module.eks.cluster_name
  addon_name               = "vpc-cni"
  addon_version            = "v1.20.0-eksbuild.1"
  resolve_conflicts_on_update = "PRESERVE"

  configuration_values = jsonencode({
    env = {
      ENABLE_PREFIX_DELEGATION = "true"
      WARM_PREFIX_TARGET       = "1"
      ENABLE_NETWORK_POLICY    = "true"
    }
  })
}
```

Pin add-on versions explicitly (`addon_version`) rather than `most_recent = true` if you want predictable production upgrades.

### Self-check questions

1. How does an EKS add-on differ from the same component installed with Helm?
2. What will `--resolve-conflicts OVERWRITE` do to your `kubectl set env` edits?
3. In what order do you upgrade the control plane, add-ons and nodes?
4. Why install `metrics-server` if it isn't required?
5. When should you take EKS Capabilities instead of your own Argo CD?

---

# Module 12. Observability: logs, metrics, traces, alerts

## 12.1 Four data streams

```
Control plane logs   → CloudWatch Logs   (OFF by default)
Application logs     → CloudWatch / OpenSearch / Loki
Metrics              → CloudWatch Container Insights / Prometheus (AMP)
Traces               → X-Ray / Tempo / Jaeger via OpenTelemetry
Kubernetes events    → a separate stream, usually forgotten, and pure gold during an incident
```

## 12.2 Control plane logs: turn these on first

```bash
aws eks update-cluster-config --name demo \
  --logging '{"clusterLogging":[{"types":["api","audit","authenticator","controllerManager","scheduler"],"enabled":true}]}'
```

| Type | Why you need it |
|---|---|
| `api` | Requests to the apiserver, errors, slow requests |
| `audit` | Who did what: the primary source during a security incident |
| `authenticator` | Why someone got `Unauthorized` |
| `controllerManager` | Why objects aren't being created, controller problems |
| `scheduler` | Why a pod isn't being scheduled |

Audit logs are voluminous and cost money in CloudWatch. Practice: always enable `api`, `audit` and `authenticator`, set a 30-90 day retention, and export to S3 for long-term storage.

A useful CloudWatch Logs Insights query — "who deleted the Deployment":

```
fields @timestamp, user.username, verb, objectRef.resource, objectRef.name, responseStatus.code
| filter verb = "delete" and objectRef.resource = "deployments"
| sort @timestamp desc
| limit 50
```

Who is getting 403s:

```
fields @timestamp, user.username, verb, objectRef.resource
| filter responseStatus.code = 403
| stats count() by user.username, objectRef.resource
```

## 12.3 CloudWatch Container Insights

```bash
aws eks create-addon --cluster-name demo \
  --addon-name amazon-cloudwatch-observability \
  --pod-identity-associations 'serviceAccount=cloudwatch-agent,roleArn=arn:aws:iam::111122223333:role/CWAgentRole'
```

What you get: node, pod and container metrics, container logs in CloudWatch Logs, a service map, and optionally Application Signals (APM). You pay for metrics and log volume; on a large cluster that's noticeable, so filter what you ship.

## 12.4 Prometheus and Grafana

Two paths:

**Managed:** Amazon Managed Service for Prometheus (AMP) plus Amazon Managed Grafana (AMG). No need to think about storage or HA.

```bash
aws amp create-workspace --alias demo
# scraping via an ADOT collector or the agentless AMP scraper
aws amp create-scraper \
  --source eksConfiguration="{clusterArn=$CLUSTER_ARN,securityGroupIds=[sg-0x],subnetIds=[subnet-0a]}" \
  --destination ampConfiguration="{workspaceArn=$AMP_ARN}" \
  --scrape-configuration configurationBlob=$(base64 -w0 scrape.yaml)
```

**Self-hosted:** kube-prometheus-stack in the cluster.

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install kps prometheus-community/kube-prometheus-stack -n monitoring --create-namespace \
  --set prometheus.prometheusSpec.retention=15d \
  --set prometheus.prometheusSpec.storageSpec.volumeClaimTemplate.spec.storageClassName=gp3 \
  --set prometheus.prometheusSpec.storageSpec.volumeClaimTemplate.spec.resources.requests.storage=100Gi \
  --set grafana.enabled=true
```

Cheaper in dollars, more expensive in operations: Prometheus itself becomes a stateful service you have to look after.

## 12.5 What to alert on (the minimum set)

| Alert | Condition | Why it matters |
|---|---|---|
| Node `NotReady` | `kube_node_status_condition{condition="Ready",status="true"} == 0` for 5 minutes | Lost capacity |
| Pod in `CrashLoopBackOff` | `rate(kube_pod_container_status_restarts_total[15m]) > 0` | The application is failing |
| Pod `Pending` for over 10 minutes | `kube_pod_status_phase{phase="Pending"} == 1` | No nodes, no IPs, no PVC |
| Low free IPs in a subnet | CloudWatch `AvailableIpAddressCount` < 10% | Pods will soon stop starting |
| Node disk filling up | `node_filesystem_avail_bytes / node_filesystem_size_bytes < 0.15` | `DiskPressure` and pod eviction |
| apiserver 5xx errors | `apiserver_request_total{code=~"5.."}` rising | Control plane or webhook problems |
| etcd / apiserver latency | `apiserver_request_duration_seconds` p99 | Overloaded control plane |
| HPA at max | `kube_horizontalpodautoscaler_status_current_replicas == spec_max_replicas` | Load above design capacity |
| Version support ending | EKS Health event | $0.60/hour instead of $0.10 |
| ACM certificate expiring | CloudWatch on ACM | HTTPS outage |
| Node `expireAfter` not working | Node age above the limit | OS patches aren't being applied |
| Bill growth | AWS Budgets on the cluster tag | FinOps |

## 12.6 Traces with OpenTelemetry

```bash
aws eks create-addon --cluster-name demo --addon-name adot
```

```yaml
apiVersion: opentelemetry.io/v1beta1
kind: OpenTelemetryCollector
metadata: { name: otel, namespace: observability }
spec:
  mode: deployment
  config:
    receivers:
      otlp:
        protocols: { grpc: {}, http: {} }
    processors:
      batch: {}
    exporters:
      awsxray: {}
      prometheusremotewrite:
        endpoint: "https://aps-workspaces.eu-central-1.amazonaws.com/workspaces/ws-xxxx/api/v1/remote_write"
        auth: { authenticator: sigv4auth }
    service:
      pipelines:
        traces:  { receivers: [otlp], processors: [batch], exporters: [awsxray] }
        metrics: { receivers: [otlp], processors: [batch], exporters: [prometheusremotewrite] }
```

## 12.7 Everyday on-call commands

```bash
# the big picture
kubectl get nodes -o wide
kubectl get pods -A --field-selector=status.phase!=Running
kubectl get events -A --sort-by='.lastTimestamp' | tail -40
kubectl top nodes && kubectl top pods -A --sort-by=cpu

# a specific pod
kubectl -n prod describe pod <pod>
kubectl -n prod logs <pod> --previous --tail=200     # logs of the crashed container
kubectl -n prod logs -l app=api --all-containers -f --max-log-requests=20
stern -n prod api                                     # nicer for many pods

# a node
kubectl describe node <node> | sed -n '/Conditions/,/Events/p'
kubectl get pods -A -o wide --field-selector spec.nodeName=<node>

# what's eating resources
kubectl top pods -A --sort-by=memory | head -20

# node debugging without SSH
kubectl debug node/<node> -it --image=public.ecr.aws/amazonlinux/amazonlinux:2023
kubectl debug -it <pod> --image=nicolaka/netshoot --target=<container>

# EKS resource state
aws eks describe-cluster --name demo --query 'cluster.{status:status,version:version,health:health}'
aws eks list-insights --cluster-name demo
```

## 12.8 The EKS Dashboard and Health events

The EKS console has a consolidated dashboard across all clusters in an account or organization: versions, support windows, add-ons, insights. On top of that, AWS Health emits events about version support ending. Subscribe to them via EventBridge → Slack: it's cheap insurance against a surprise $0.60/hour.

```json
{
  "source": ["aws.health"],
  "detail": { "service": ["EKS"], "eventTypeCategory": ["scheduledChange"] }
}
```

### Practice

1. Enable all five control plane log types, run `kubectl delete deployment`, and find yourself in the audit log via Logs Insights.
2. Install kube-prometheus-stack, open Grafana, and find the node dashboard.
3. Configure an alert for pods `Pending` longer than 10 minutes and trigger it artificially (request 100 CPU).
4. Install ADOT, send a trace from a test application, and find it in X-Ray.
5. Create an EventBridge rule for AWS Health EKS events.

---

# Module 13. EKS security: from PSS to GuardDuty

## 13.1 Threat map and responses

| Threat | Response in EKS |
|---|---|
| Anyone can reach the apiserver | Private endpoint, `publicAccessCidrs`, IAM |
| Overly broad human permissions | Namespace-scoped access entries, no `system:masters` |
| A pod obtained node permissions | IMDSv2 + `hopLimit: 1`, Pod Identity |
| Containers running as root or privileged | Pod Security Standards, admission policies |
| Unrestricted traffic between namespaces | NetworkPolicy, Admin Policies |
| A vulnerable image | ECR scanning, image signing, base image updates |
| Plaintext secrets | KMS etcd encryption, Secrets Manager, CSI |
| Runtime compromise | GuardDuty EKS Runtime Monitoring |
| No trace of actions | Control plane audit logs, CloudTrail |
| Configuration drift | GitOps, policy as code (Kyverno/OPA) |

## 13.2 Pod Security Standards

`PodSecurityPolicy` is long gone; today the built-in Pod Security Admission works per namespace.

```bash
kubectl label namespace prod \
  pod-security.kubernetes.io/enforce=restricted \
  pod-security.kubernetes.io/enforce-version=v1.36 \
  pod-security.kubernetes.io/audit=restricted \
  pod-security.kubernetes.io/warn=restricted
```

| Level | What's allowed |
|---|---|
| `privileged` | Everything (system namespaces only) |
| `baseline` | Clearly dangerous things are blocked: privileged, hostNetwork, hostPID |
| `restricted` | Plus mandatory non-root, `readOnlyRootFilesystem`, dropped capabilities, seccomp |

A pod that passes `restricted`:

```yaml
    spec:
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001
        seccompProfile: { type: RuntimeDefault }
      containers:
        - name: app
          image: <acct>.dkr.ecr.eu-central-1.amazonaws.com/app:1.2.3@sha256:abc...
          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities: { drop: ["ALL"] }
          volumeMounts:
            - { name: tmp, mountPath: /tmp }
      volumes:
        - name: tmp
          emptyDir: {}
```

Start with `warn` and `audit`, see what breaks, and only then turn on `enforce`.

## 13.3 Policy as code

PSS doesn't cover everything: "block images from outside our ECR", "require labels", "require requests". That's Kyverno or OPA Gatekeeper.

```yaml
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata: { name: require-ecr-images }
spec:
  validationFailureAction: Enforce
  rules:
    - name: only-our-registry
      match:
        any:
          - resources: { kinds: ["Pod"] }
      validate:
        message: "Images must come from our ECR"
        pattern:
          spec:
            containers:
              - image: "111122223333.dkr.ecr.eu-central-1.amazonaws.com/*"
---
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata: { name: require-requests }
spec:
  validationFailureAction: Audit
  rules:
    - name: resources-required
      match: { any: [{ resources: { kinds: ["Pod"] } }] }
      validate:
        message: "requests.cpu and requests.memory are required"
        pattern:
          spec:
            containers:
              - resources:
                  requests:
                    cpu: "?*"
                    memory: "?*"
```

Careful: an admission webhook sits on the critical path of pod creation. If it goes down while configured with `failurePolicy: Fail`, the cluster stops accepting deployments. Run it in HA and exclude `kube-system`.

## 13.4 Images: ECR and scanning

```bash
# a repository with immutable tags and scanning
aws ecr create-repository --repository-name app \
  --image-tag-mutability IMMUTABLE \
  --image-scanning-configuration scanOnPush=true \
  --encryption-configuration encryptionType=KMS

# enhanced scanning (Inspector): continuous re-evaluation of findings
aws ecr put-registry-scanning-configuration --scan-type ENHANCED \
  --rules '[{"scanFrequency":"CONTINUOUS_SCAN","repositoryFilters":[{"filter":"*","filterType":"WILDCARD"}]}]'

# lifecycle policy: don't pay for 500 stale images
aws ecr put-lifecycle-policy --repository-name app --lifecycle-policy-text '{
  "rules":[{"rulePriority":1,"description":"keep last 30","selection":{"tagStatus":"any","countType":"imageCountMoreThan","countNumber":30},"action":{"type":"expire"}}]}'
```

Image hygiene rules:

- **never `:latest` in production**, only a tag plus the `@sha256:` digest;
- `IMMUTABLE` tags, so the same tag can't be swapped underneath you;
- minimal base images (distroless, `alpine`, `amazonlinux-minimal`);
- builds with no secrets baked into layers (`--secret`, multi-stage);
- signing and verification (`cosign` + Kyverno `verifyImages`).

## 13.5 GuardDuty EKS Protection

```bash
aws guardduty update-detector --detector-id <id> \
  --features '[{"Name":"EKS_AUDIT_LOGS","Status":"ENABLED"},
               {"Name":"RUNTIME_MONITORING","Status":"ENABLED",
                "AdditionalConfiguration":[{"Name":"EKS_ADDON_MANAGEMENT","Status":"ENABLED"}]}]'
```

It gives you two layers: audit log analysis (suspicious API calls, anonymous access, privilege escalation) and a runtime agent on nodes (shells opened in containers, miners, calls to suspicious domains). Enable both in production.

## 13.6 Private clusters and the network perimeter

```bash
aws eks update-cluster-config --name prod \
  --resources-vpc-config endpointPublicAccess=false,endpointPrivateAccess=true
```

Pre-flight checklist: VPN or bastion, CI runners in the VPC, VPC endpoints for ECR/S3/STS/EKS/logs, and an access recovery plan.

Additionally:

- nodes **without public IPs**, private subnets only;
- node security group: inbound only from the cluster SG and load balancers;
- a `default deny` NetworkPolicy in every application namespace;
- egress filtering for sensitive services.

## 13.7 Multi-tenancy: isolating teams in one cluster

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: team-a
  labels:
    pod-security.kubernetes.io/enforce: restricted
---
apiVersion: v1
kind: ResourceQuota
metadata: { name: quota, namespace: team-a }
spec:
  hard:
    requests.cpu: "50"
    requests.memory: 100Gi
    limits.memory: 200Gi
    persistentvolumeclaims: "20"
    count/services.loadbalancers: "2"
    pods: "200"
---
apiVersion: v1
kind: LimitRange
metadata: { name: defaults, namespace: team-a }
spec:
  limits:
    - type: Container
      default: { cpu: 500m, memory: 512Mi }
      defaultRequest: { cpu: 100m, memory: 128Mi }
      max: { cpu: "4", memory: 8Gi }
```

Plus: namespace-scoped access entries, a `default deny` NetworkPolicy, dedicated tainted NodePools for noisy teams, and a load balancer quota (otherwise one team will create 30 ALBs).

An honest caveat: **a namespace is not a VM-grade security boundary.** For hostile multi-tenancy you need separate clusters, Fargate, or per-team node isolation.

## 13.8 Production security checklist

- `authenticationMode=API`, no IAM users, SSO roles only;
- private endpoint (or a strict `publicAccessCidrs`);
- audit logs enabled, retention set, exported to S3;
- KMS encryption for secrets, encrypted node EBS volumes;
- IMDSv2 + `hopLimit: 1`;
- Pod Identity per service, least-privilege policies, namespace conditions;
- PSS `restricted` in every application namespace;
- NetworkPolicy `default deny` for ingress and egress;
- ECR: `IMMUTABLE`, enhanced scanning, external images blocked via Kyverno;
- GuardDuty EKS Protection (audit + runtime);
- regular Kubernetes version upgrades (Module 15);
- application and PV backups (Velero / AWS Backup) with verified restores;
- separate clusters for prod and non-prod.

### Self-check questions

1. Why is `hopLimit: 1` more important than it looks?
2. How does `restricted` differ from `baseline` in PSS?
3. What happens if an admission webhook with `failurePolicy: Fail` goes down?
4. Is a namespace a security boundary? Why not?
5. What two modes does GuardDuty EKS Protection provide?

---

# Module 14. CI/CD and GitOps: ECR, Helm, Argo CD

## 14.1 Push vs pull: two delivery models

```
Push (classic CI):
  git push → CI builds an image → CI has cluster access → kubectl apply / helm upgrade
  pro: simple, familiar
  con: CI needs cluster permissions, drift between Git and cluster goes unnoticed

Pull (GitOps):
  git push → CI builds the image and bumps the tag in manifests → Argo CD/Flux in-cluster pulls it
  pro: the cluster needs no inbound access, drift is visible and auto-corrected
  con: one more component, the team must accept "Git is the source of truth"
```

For a single service, push is fine. For a platform with dozens of services and several clusters, GitOps is the right answer.

## 14.2 Building and publishing to ECR

```bash
ACCOUNT=111122223333
REGION=eu-central-1
REPO=$ACCOUNT.dkr.ecr.$REGION.amazonaws.com/app

aws ecr get-login-password --region $REGION | docker login --username AWS --password-stdin $ACCOUNT.dkr.ecr.$REGION.amazonaws.com

docker buildx build --platform linux/amd64,linux/arm64 \
  -t $REPO:$(git rev-parse --short HEAD) \
  --provenance=true --sbom=true --push .
```

GitHub Actions with no static keys (OIDC → IAM role):

```yaml
name: build-and-deploy
on:
  push: { branches: [main] }

permissions:
  id-token: write        # OIDC doesn't work without this
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: arn:aws:iam::111122223333:role/GitHubActionsECRPush
          aws-region: eu-central-1

      - uses: aws-actions/amazon-ecr-login@v2
        id: ecr

      - name: Build and push
        run: |
          IMAGE=${{ steps.ecr.outputs.registry }}/app:${GITHUB_SHA::7}
          docker build -t $IMAGE .
          docker push $IMAGE
          echo "IMAGE=$IMAGE" >> $GITHUB_ENV

      - name: Bump tag in GitOps repo
        run: |
          yq -i ".image.tag = \"${GITHUB_SHA::7}\"" deploy/prod/values.yaml
          git config user.name ci && git config user.email ci@example.com
          git commit -am "deploy: ${GITHUB_SHA::7}" && git push
```

Note that this workflow **has no cluster access at all**. It only pushes an image and changes a tag in Git. Argo CD does the deployment.

## 14.3 Argo CD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d
```

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: web-prod
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/acme/deploy.git
    targetRevision: main
    path: charts/web
    helm:
      valueFiles: ["values-prod.yaml"]
  destination:
    server: https://kubernetes.default.svc
    namespace: prod
  syncPolicy:
    automated:
      prune: true
      selfHeal: true            # manual in-cluster edits get reverted
    syncOptions:
      - CreateNamespace=true
      - ApplyOutOfSyncOnly=true
    retry:
      limit: 5
      backoff: { duration: 10s, factor: 2, maxDuration: 3m }
```

For multiple environments and clusters, use an `ApplicationSet`:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet
metadata: { name: web, namespace: argocd }
spec:
  generators:
    - list:
        elements:
          - { env: dev,  cluster: https://dev.eks,  replicas: "1" }
          - { env: prod, cluster: https://prod.eks, replicas: "6" }
  template:
    metadata: { name: 'web-{{env}}' }
    spec:
      project: default
      source:
        repoURL: https://github.com/acme/deploy.git
        targetRevision: main
        path: charts/web
        helm:
          parameters:
            - { name: replicaCount, value: '{{replicas}}' }
      destination: { server: '{{cluster}}', namespace: '{{env}}' }
      syncPolicy: { automated: { prune: true, selfHeal: true } }
```

## 14.4 Helm: an application chart layout

```
charts/web/
  Chart.yaml
  values.yaml          # defaults
  values-dev.yaml
  values-prod.yaml
  templates/
    deployment.yaml
    service.yaml
    ingress.yaml
    hpa.yaml
    pdb.yaml
    serviceaccount.yaml
    networkpolicy.yaml
```

```yaml
# values-prod.yaml
replicaCount: 6
image:
  repository: 111122223333.dkr.ecr.eu-central-1.amazonaws.com/app
  tag: "a1b2c3d"                 # changed by CI, not by a human
resources:
  requests: { cpu: 200m, memory: 256Mi }
  limits:   { memory: 512Mi }
hpa: { enabled: true, minReplicas: 6, maxReplicas: 40, targetCPU: 70 }
pdb: { enabled: true, minAvailable: "80%" }
ingress:
  enabled: true
  host: app.example.com
  group: shared-prod
serviceAccount:
  create: true
  name: web
topologySpread: true
```

```bash
helm template web charts/web -f charts/web/values-prod.yaml | kubectl apply --dry-run=server -f -
helm diff upgrade web charts/web -f charts/web/values-prod.yaml    # the helm-diff plugin is mandatory
```

## 14.5 Canary and blue-green deployments

```yaml
# Argo Rollouts: a canary gated on metrics
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata: { name: web, namespace: prod }
spec:
  replicas: 10
  strategy:
    canary:
      canaryService: web-canary
      stableService: web-stable
      trafficRouting:
        alb:
          ingress: web
          servicePort: 80
      steps:
        - setWeight: 10
        - pause: { duration: 5m }
        - analysis:
            templates: [{ templateName: success-rate }]
        - setWeight: 50
        - pause: { duration: 10m }
        - setWeight: 100
  selector: { matchLabels: { app: web } }
  template:
    metadata: { labels: { app: web } }
    spec:
      containers: [{ name: app, image: <ecr>/app:a1b2c3d }]
---
apiVersion: argoproj.io/v1alpha1
kind: AnalysisTemplate
metadata: { name: success-rate, namespace: prod }
spec:
  metrics:
    - name: success-rate
      interval: 1m
      successCondition: result[0] >= 0.99
      failureLimit: 2
      provider:
        prometheus:
          address: http://kps-prometheus.monitoring:9090
          query: |
            sum(rate(http_requests_total{app="web",code!~"5.."}[2m]))
            / sum(rate(http_requests_total{app="web"}[2m]))
```

This is mature-platform territory: the deployment rolls itself back when the error rate rises.

## 14.6 CI checks that prevent incidents

```bash
# validate manifests against the cluster schema
kubeconform -strict -kubernetes-version 1.36.0 -summary manifests/

# static security analysis
trivy config .
trivy image --severity HIGH,CRITICAL --exit-code 1 $IMAGE

# policy as code before the cluster ever sees it
kyverno apply policies/ --resource manifests/

# check for resource deletions
helm diff upgrade web charts/web -f values-prod.yaml | grep -E '^-' | head
```

## 14.7 Delivery anti-patterns

- **Hand-run `kubectl apply` in production.** A month later nobody knows what's in the cluster.
- **A CI role with `cluster-admin`** on every cluster. Compromise CI, compromise everything.
- **`:latest` plus `imagePullPolicy: Always`** as a versioning strategy. There's nothing to roll back to.
- **Secrets in values.yaml** in Git. Even a private repo is not a secret store.
- **One Git repo for everything** with no environment structure: staged rollouts become impossible.
- **Skipping `helm diff`** before an upgrade: surprises like "the PVC got deleted".

### Practice

1. Set up GitHub Actions with an OIDC role and push an image to ECR with no static keys.
2. Install Argo CD, create an Application for your chart, enable `selfHeal`, then edit the Deployment by hand and watch it revert.
3. Create an ApplicationSet for two environments with different replica counts.
4. Add `trivy image --exit-code 1` to CI and confirm a vulnerable image is blocked.
5. Configure Argo Rollouts with a 10% canary and Prometheus-based analysis.

---
# Module 15. Version upgrades: lifecycle, insights, strategy

## 15.1 The EKS version lifecycle

```
Release in EKS  ──14 months──>  end of standard support ($0.10/hour)
                                    |
                                    +──12 months──>  end of extended support ($0.60/hour)
                                                          |
                                                          +─> AWS upgrades the cluster BY FORCE
```

That's **26 months** per version in total. As of September 2026 the picture is:

| Version | EKS release | Status |
|---|---|---|
| **1.36** | June 2026 | Standard support |
| **1.35** | January 2026 | Standard support |
| **1.34** | October 2025 | Standard support |
| 1.33 | May 2025 | **Extended support** (standard ended 29 July 2026) — $0.60/hour |
| 1.32 and older | earlier | Extended support or no longer supported |

One cluster in extended support costs **an extra $4,380 per year** compared to standard support. For the same cluster. It's the most expensive technical debt in EKS.

**Practical rule:** upgrade every 6-9 months, roughly one or two minors at a time. Then you're always in standard support and never chasing three versions at once.

## 15.2 Cluster insights: the pre-flight check

EKS analyzes the cluster and tells you what will break.

```bash
aws eks list-insights --cluster-name demo
aws eks describe-insight --cluster-name demo --id <insight-id>

# problems only
aws eks list-insights --cluster-name demo \
  --query 'insights[?insightStatus.status!=`PASSING`].{name:name,status:insightStatus.status,reason:insightStatus.reason}'
```

Insights catch: use of removed APIs (`policy/v1beta1`, old CRDs), incompatible add-on versions, missing EKS permissions, kube-proxy issues, stale AMIs.

Check removed APIs yourself as well:

```bash
# what in the cluster still calls deprecated APIs (from the audit log)
# CloudWatch Logs Insights on /aws/eks/<cluster>/cluster
fields @timestamp, userAgent, requestURI
| filter requestURI like /v1beta1/
| stats count() by userAgent, requestURI

# static manifest analysis
pluto detect-files -d ./manifests --target-versions k8s=v1.36.0
kubent                                   # kube-no-trouble
```

## 15.3 Upgrade order

```bash
# 0. Backup: manifests and PVs
velero backup create pre-upgrade-1-36 --include-namespaces prod --wait

# 1. Check insights and add-on compatibility
aws eks list-insights --cluster-name demo

# 2. Control plane (one minor at a time, NO rollback)
aws eks update-cluster-version --name demo --kubernetes-version 1.36
aws eks wait cluster-active --name demo        # 10-25 minutes

# 3. Add-ons
for a in kube-proxy vpc-cni coredns aws-ebs-csi-driver; do
  V=$(aws eks describe-addon-versions --kubernetes-version 1.36 --addon-name $a \
      --query 'addons[0].addonVersions[?compatibilities[0].defaultVersion==`true`].addonVersion' --output text)
  aws eks update-addon --cluster-name demo --addon-name $a --addon-version $V --resolve-conflicts PRESERVE
  aws eks wait addon-active --cluster-name demo --addon-name $a
done

# 4. Nodes
eksctl upgrade nodegroup --cluster demo --name ng-general     # rolling, respects PDBs
# or with Karpenter: nodes replace themselves via expireAfter / drift

# 5. kubectl on your own machine
kubectl version
```

**Three iron rules:**

1. **One minor at a time.** 1.34 → 1.36 directly is not allowed.
2. **No rollback.** The control plane upgrades one way only. The only "rollback" is a new cluster on the old version.
3. **Skew between control plane and nodes** is allowed up to 3 minors down (nodes never newer than the control plane). Don't get comfortable, though: add-ons and CSI drivers often demand freshness sooner.

## 15.4 What usually breaks

| What | Why | How to catch it early |
|---|---|---|
| Removed APIs | Upstream drops `v1beta1` versions | `pluto`, `kubent`, audit logs |
| Old Helm charts | They use removed kinds | `helm template \| kubectl apply --dry-run=server` |
| Ingress-NGINX | Retired upstream in March 2026 | Migrate to Gateway API / ALB |
| AL2 AMIs | Not built since 1.33 | Move to AL2023 or Bottlerocket |
| cgroup v1 | kubelet refuses to start as of 1.35 | Check custom AMIs |
| IPVS in kube-proxy | Removed in 1.36 | Switch to iptables/nftables |
| Your own admission webhooks | They don't know new API versions | Update them, check `failurePolicy` |
| Operators (Postgres, Kafka) | They lag behind Kubernetes versions | Upgrade the operator BEFORE the cluster |
| PDBs that block drain | `minAvailable` equal to the replica count | Review `kubectl get pdb -A` |

## 15.5 Blue-green cluster upgrades

When the risk is unacceptable (regulated environment, critical service), you move traffic instead of the cluster:

```
Cluster A (1.34, prod)  ←── 100% of traffic via Route 53 / ALB
Cluster B (1.36, new)   ←── 0%

1. Stand up B from the same IaC on the newer version
2. Roll out the same applications through GitOps
3. Run smoke tests
4. Shift traffic: 10% → 50% → 100% (weighted Route 53 or a shared ALB)
5. Keep A for a day as the rollback path
6. Delete A
```

Expensive (double billing during the migration) but fully reversible. It pairs beautifully with GitOps: "stand up an identical cluster" is one `terraform apply` and one `ApplicationSet`.

## 15.6 Automation and reminders

```bash
# EventBridge → Slack for AWS Health EKS events
aws events put-rule --name eks-version-events \
  --event-pattern '{"source":["aws.health"],"detail":{"service":["EKS"]}}'

# a version report for every cluster in the account
for c in $(aws eks list-clusters --query 'clusters[]' --output text); do
  aws eks describe-cluster --name $c --query "cluster.{name:name,version:version,status:status}" --output text
done
```

In an organization with dozens of clusters, use the EKS Dashboard: it consolidates versions and support windows across accounts.

### Self-check questions

1. How long does a minor version live in EKS, and what does being late cost?
2. Can you go from 1.33 straight to 1.36, and can you roll back?
3. In what order do control plane, add-ons and nodes go, and why that order?
4. How do you find out in advance that applications use removed APIs?
5. When is a blue-green whole-cluster upgrade justified?

---

# Module 16. EKS cost and optimization

## 16.1 The full bill breakdown

| Line | Price (us-east-1, 2026) | Comment |
|---|---|---|
| Control plane (standard) | $0.10/hour = **$73/month** | Per cluster, always |
| Control plane (extended) | $0.60/hour = **$438/month** | The price of not paying attention |
| Provisioned Control Plane | On top, per tier (XL...8XL) | Only for ultra-scale and the 99.99% SLA |
| EC2 nodes | EC2 list price | Usually the **largest** line |
| Auto Mode | EC2 + **≈12%** | Savings Plans don't cover the premium |
| Fargate | ≈$0.04048/vCPU-hour, ≈$0.004445/GB-hour | More expensive than EC2 on steady load |
| EBS (gp3) | ≈$0.08/GB-month + IOPS above baseline | Plus forgotten volumes |
| EBS snapshots | ≈$0.05/GB-month | They accumulate quietly |
| ALB/NLB | ≈$16/month + LCUs | Each one, if you skip `group.name` |
| **NAT Gateway** | $0.045/hour + **$0.045/GB** | Often more than the control plane |
| Cross-AZ traffic | $0.01/GB each direction | The disease of chatty microservices |
| Internet egress | from $0.09/GB | |
| CloudWatch Logs | ≈$0.50/GB ingest + storage | Audit logs bite on large clusters |
| CloudWatch metrics | $0.30/metric-month (custom) | Container Insights on 1000 pods is real money |
| ECR | $0.10/GB-month | Grows forever without a lifecycle policy |
| Public IPv4 addresses | $0.005/hour each | On nodes in public subnets |
| EKS Capabilities | Per capability pricing | Argo CD/ACK/kro as a service |

**A typical small production cluster:** control plane $73 + three `m6i.large` $220 + ALB $20 + NAT $35-100 + EBS $30 + logs $30 ≈ **$400-500/month**. Only $73 of that is "EKS" proper.

## 16.2 Seeing where the money goes

```bash
# enable per-cluster cost separation: tags on every resource
# (Karpenter and Auto Mode apply them automatically if set in the NodeClass/launch template)

# Cost Explorer by tag
aws ce get-cost-and-usage \
  --time-period Start=2026-08-01,End=2026-09-01 \
  --granularity MONTHLY --metrics UnblendedCost \
  --group-by Type=TAG,Key=eks:cluster-name
```

Inside the cluster, use **OpenCost / Kubecost**: a breakdown by namespace, deployment and team.

```bash
helm repo add opencost https://opencost.github.io/opencost-helm-chart
helm install opencost opencost/opencost -n opencost --create-namespace
```

The rule: without a per-namespace breakdown, "who is spending this" becomes an argument. With one, teams start fixing their own requests.

## 16.3 Eight levers, in order of effectiveness

1. **Right-size requests.** Average cluster CPU utilization sits in the single digits because requests are inflated many times over. This is lever number one: correct requests often shrink the fleet by 30-50% with no architectural change. Tools: VPA in recommendation mode, Kubecost, Goldilocks.
2. **Spot.** Up to −90%. Batch, dev, stateless. Through Karpenter, with interruption handling included.
3. **Graviton (ARM).** 20-40% better price-performance. Needs multi-arch images.
4. **Node consolidation.** Karpenter's `WhenEmptyOrUnderutilized` packs workloads tighter and removes half-empty nodes.
5. **Savings Plans / Reserved.** For the steady baseline: Compute Savings Plans are the most flexible. Remember they don't cover the Auto Mode premium.
6. **Fewer clusters.** Three dev clusters cost $219/month in control plane fees alone. One cluster with a namespace per environment saves money and attention. Keep production separate anyway.
7. **Remove surplus load balancers.** `group.name` on ALB Ingress merges dozens of Ingresses into one ALB.
8. **Networking.** One NAT Gateway per AZ is needed for availability, but VPC endpoints for S3/ECR take the bulk of traffic out of NAT. `PreferSameZone` and topology-aware routing reduce cross-AZ.

## 16.4 A quick audit: what you'll almost always find

```bash
# unattached EBS volumes
aws ec2 describe-volumes --filters Name=status,Values=available \
  --query 'Volumes[].{id:VolumeId,size:Size,az:AvailabilityZone}' --output table

# load balancers with no targets
for lb in $(aws elbv2 describe-load-balancers --query 'LoadBalancers[].LoadBalancerArn' --output text); do
  aws elbv2 describe-target-groups --load-balancer-arn $lb --query 'TargetGroups[].TargetGroupName' --output text | \
    xargs -r -n1 echo "$lb"
done

# unassociated Elastic IPs
aws ec2 describe-addresses --query 'Addresses[?AssociationId==null].PublicIp'

# old snapshots
aws ec2 describe-snapshots --owner-ids self \
  --query 'Snapshots[?StartTime<=`2026-01-01`].{id:SnapshotId,size:VolumeSize}' --output table

# the biggest pods by requests vs actual usage
kubectl get pods -A -o custom-columns='NS:.metadata.namespace,POD:.metadata.name,CPU_REQ:.spec.containers[*].resources.requests.cpu,MEM_REQ:.spec.containers[*].resources.requests.memory'
kubectl top pods -A --sort-by=cpu | head -20
```

## 16.5 Budgets and alerts

```bash
aws budgets create-budget --account-id 111122223333 --budget '{
  "BudgetName":"eks-prod","BudgetLimit":{"Amount":"1500","Unit":"USD"},
  "TimeUnit":"MONTHLY","BudgetType":"COST",
  "CostFilters":{"TagKeyValue":["user:eks:cluster-name$prod"]}}' \
  --notifications-with-subscribers '[{"Notification":{"NotificationType":"ACTUAL","ComparisonOperator":"GREATER_THAN","Threshold":80},"Subscribers":[{"SubscriptionType":"EMAIL","Address":"platform@example.com"}]}]'
```

Plus a `ResourceQuota` per namespace: it's not only about security, it's also about one team not launching 200 pods at 4 CPU each overnight.

## 16.6 Cost anti-patterns

- **A cluster per service.** Five services, five clusters, $365/month in control plane fees alone.
- **Dev clusters running 24/7.** Shut nodes down on a schedule: `eksctl scale nodegroup --nodes 0` at night and on weekends (or KEDA cron plus Karpenter).
- **Requests set "×5 to be safe"** without measurement.
- **All logs to CloudWatch with no filtering.** Debug logs from 1000 pods can cost more than the nodes.
- **A separate ALB per Ingress.**
- **Forgotten PVCs with `reclaimPolicy: Retain`** after namespaces are deleted.
- **Public IPv4 addresses on nodes** that don't need them.
- **Extended support as a strategy.** Saving on upgrades turns into a 6× cluster fee.

### Practice

1. Tag every cluster resource with `eks:cluster-name` and build a Cost Explorer report.
2. Install OpenCost and find the three most expensive namespaces.
3. Find a service with inflated requests (compare `kubectl top` with requests), reduce them, and see how many nodes disappear after Karpenter consolidation.
4. Move batch workloads to Spot + ARM and calculate the difference.
5. Create a $50 Budget and receive the email.

---

# Module 17. Reliability, multi-region and DR

## 17.1 What can break and what to do about it

| Failure | Consequence without preparation | Preparation |
|---|---|---|
| A single pod | Some requests error out | ≥2-3 replicas, readiness, PDB |
| A single node | Capacity dip, restart lag | Several nodes, topology spread, spare capacity |
| **A whole AZ** | A third or more of the workload is down, EBS unreachable | 3 AZs, `DoNotSchedule` across zones, DB replicas in other AZs |
| The control plane (99.95% SLA) | You can't deploy or change anything; **running pods keep running** | Don't tie runtime to the apiserver; be ready to "freeze and don't touch" |
| A region | Full outage | Multi-region, a DR plan, data replication |
| A bad deployment | All replicas die at once | Canary, `maxUnavailable: 0`, automatic rollback |
| IP or quota exhaustion | Pods won't start | Monitor subnets and quotas, keep headroom |
| A human deleting a cluster or namespace | Loss of configuration and data | GitOps, Velero, `prevent_destroy` in Terraform, SCP policies |

An important EKS fact: **a control plane outage doesn't kill running pods.** Kubelet keeps containers alive, kube-proxy keeps its rules, the ALB keeps serving traffic. What breaks is management: deployments, autoscaling, recreating failed pods. Understand this and don't panic.

## 17.2 Multi-AZ as the baseline

```yaml
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          minDomains: 3
          labelSelector: { matchLabels: { app: web } }
```

Plus:

- nodes in all three AZs, Karpenter with zone requirements;
- a NAT Gateway per AZ (a single NAT means its AZ failure cuts egress for the whole cluster);
- `cross-zone` on NLBs if even distribution matters more than savings;
- stateful replicas in different AZs; remember EBS doesn't move between zones;
- spare capacity: if the surviving nodes have no room when an AZ fails, an AZ failure becomes a service failure.

## 17.3 Testing an AZ failure

```bash
# find nodes in one AZ and take them out of service
Z=eu-central-1b
NODES=$(kubectl get nodes -l topology.kubernetes.io/zone=$Z -o name)
kubectl cordon $NODES
kubectl drain $NODES --ignore-daemonsets --delete-emptydir-data --force

# watch what happened
kubectl get pods -A -o wide | grep -c Running
kubectl get pods -A --field-selector=status.phase=Pending
```

If the service stayed available during this exercise and pods relocated, multi-AZ is configured. If `Pending` pods and 5xx appeared, you found the problem before your customers did.

## 17.4 Multi-region: three models

```
1. Active-Passive (pilot light)
   Region A: full production.  Region B: a minimal cluster + data replica
   Failover: Route 53 failover, scale B up
   RTO: tens of minutes, RPO: minutes.  Cost: moderate

2. Active-Active
   Both regions serve traffic, Route 53 latency routing / Global Accelerator
   Data: Aurora Global Database, DynamoDB Global Tables, S3 CRR
   RTO: seconds, RPO: near zero.  Cost: double, complexity high

3. Backup & Restore
   IaC only plus Velero backups in S3 with replication
   RTO: hours.  Cost: minimal
```

The hard part isn't the clusters, it's the **data**: the Kubernetes layer is reproducible from Git in 30 minutes, a stateful database is not. Start DR design with the data.

```bash
# replicate images between regions
aws ecr put-replication-configuration --replication-configuration '{
  "rules":[{"destinations":[{"region":"eu-west-1","registryId":"111122223333"}]}]}'
```

## 17.5 Route 53 and traffic failover

```bash
# a health check on the production endpoint
aws route53 create-health-check --caller-reference $(date +%s) \
  --health-check-config Type=HTTPS,FullyQualifiedDomainName=app.example.com,ResourcePath=/healthz,RequestInterval=10,FailureThreshold=3
```

Failover records: primary pointing at region A's ALB with a health check, secondary at region B's ALB. Plus a short TTL (60 seconds), otherwise failover stretches across hours of DNS caching.

The alternative without DNS delays is **AWS Global Accelerator**: anycast IPs and network-level failover.

## 17.6 Backups you've actually verified

```bash
# a Velero schedule
velero schedule create daily-prod --schedule="0 2 * * *" \
  --include-namespaces prod --ttl 720h --snapshot-volumes

# test the restore (into a separate namespace!)
velero restore create test-restore --from-backup daily-prod-20260921020000 \
  --namespace-mappings prod:prod-restore-test
kubectl -n prod-restore-test get pods,pvc
```

**A backup you've never restored is not a backup.** Once a quarter, run a drill: stand up a cluster from IaC, restore applications from Velero, and measure the real RTO.

## 17.7 Chaos engineering

```bash
# AWS Fault Injection Service: kill a percentage of cluster nodes
aws fis create-experiment-template --cli-input-json file://eks-node-failure.json
aws fis start-experiment --experiment-template-id EXT123
```

Worth running regularly: random node termination, AZ failure, CPU exhaustion on a node, network latency to RDS, IP exhaustion in a subnet, loss of ECR access.

### Self-check questions

1. What happens to running pods when the control plane is unavailable?
2. Why is one NAT Gateway per VPC an availability risk?
3. Why does an EBS volume prevent rescheduling a pod into another AZ?
4. How do pilot light and active-active differ in RTO and cost?
5. How do you verify your backups actually work?

---

# Module 18. EKS in production: architecture and operations

## 18.1 Reference architecture

```
AWS Organizations
  ├── shared-services account:  ECR, Route 53, CI runners, central logs
  ├── dev account:              dev cluster (namespace per team)
  ├── staging account:          staging cluster (a smaller copy of prod)
  └── prod account:
        VPC 10.0.0.0/16, 3 AZs
          public subnets:    ALBs, NAT GWs (one per AZ)
          private subnets:   /18 per AZ for nodes and pods
          VPC endpoints:     s3, ecr.api, ecr.dkr, sts, logs, eks, ssm, secretsmanager
        EKS prod (1.36)
          endpoint: private + a narrow public CIDR list
          authenticationMode: API, access entries from IaC
          audit logs → CloudWatch → S3
          KMS encryption for secrets
          ├── managed node group "system" (On-Demand, 3 nodes, taint=system)
          │     CoreDNS, Karpenter, LBC, Argo CD, monitoring
          ├── Karpenter NodePool "apps"  (On-Demand + Spot, multi-arch)
          └── Karpenter NodePool "batch" (Spot, taint=batch)
        Data: RDS/Aurora Multi-AZ, ElastiCache, S3 (not in the cluster)
        Delivery: Argo CD (pull), images from the shared-services ECR
        Observability: AMP + AMG or kube-prometheus-stack, Container Insights
```

Four principles behind this layout: **prod in its own account**, **system workloads separated from application workloads**, **data outside the cluster**, **everything described in IaC**.

## 18.2 Sizing: where to start

| Scale | Nodes | What matters |
|---|---|---|
| Up to 10 pods | 2-3 × `m6i.large` | One node group is enough; the key thing is 3 AZs |
| 50-200 pods | 5-15 nodes, Karpenter | Split system and apps, PDBs everywhere, prefix delegation |
| 500-2000 pods | Dozens of nodes | Scale CoreDNS, watch subnets and EC2 quotas, add-on resource limits |
| 5000+ pods / 1000+ nodes | Many NodePools | Provisioned Control Plane, sharding across clusters, apiserver watch load, an etcd budget |

Practical reference points:

- **110 pods per node** is the recommended ceiling (even if ENIs allow more);
- one cluster comfortably handles a few thousand nodes, but you'll hit subnets, EC2 quotas and your own operational capacity first;
- CoreDNS: 2 replicas to start, then one per 30-50 nodes;
- if the apiserver starts lagging at peaks (many watches, many Jobs, thousands of pods per second), that's a candidate for Provisioned Control Plane.

## 18.3 An IaC structure that won't collapse

```
infra/
  modules/
    eks-cluster/          # a wrapper around terraform-aws-modules/eks
    eks-addons/           # add-ons and platform controllers
    vpc/
  envs/
    dev/main.tf           # module "cluster" { source = "../../modules/eks-cluster" ... }
    staging/main.tf
    prod/main.tf
deploy/                   # the GitOps repo (or a separate one)
  clusters/
    prod/
      apps/               # ApplicationSets, charts, values
      platform/           # monitoring, Argo, policies
```

Rules:

- the same module for every environment, differences only in `tfvars`;
- `prevent_destroy = true` on the production cluster and its state;
- remote state in S3 with locking, separate state per environment;
- provider and module versions pinned;
- add-on versions pinned explicitly;
- `terraform plan` in every PR, mandatory review for production.

## 18.4 Day-to-day operations

```bash
# the morning round
kubectl get nodes | grep -v " Ready"
kubectl get pods -A --field-selector=status.phase!=Running | grep -v Completed
kubectl get events -A --sort-by='.lastTimestamp' | tail -30
aws eks list-insights --cluster-name prod --query 'insights[?insightStatus.status!=`PASSING`]'
kubectl get pdb -A                                # is anything blocking drain?
kubectl get certificates -A 2>/dev/null           # if you run cert-manager

# before the weekend
aws eks describe-cluster --name prod --query 'cluster.version'
aws ec2 describe-subnets --filters Name=tag:kubernetes.io/role/internal-elb,Values=1 \
  --query 'Subnets[].{az:AvailabilityZone,free:AvailableIpAddressCount}'
```

What to automate first: a version report for clusters and add-ons, an alert on free subnet IPs, an alert on node age, and a nightly backup verification.

## 18.5 Production checklist

**Cluster**

- version in standard support, with an upgrade date on the calendar;
- 3 AZs, private nodes, private endpoint (or a narrow CIDR list);
- `authenticationMode=API`, access entries from IaC;
- audit logs enabled, KMS encryption for secrets;
- everything created through IaC, no manual changes.

**Compute**

- system workloads on On-Demand with a taint, application workloads separate;
- Karpenter or Auto Mode, with NodePool limits set;
- `expireAfter` for regular replacement with fresh AMIs;
- IMDSv2 and `hopLimit: 1`;
- several instance types and AZs; Spot only where it's acceptable.

**Applications**

- `requests` measured, `limits.memory` set;
- readiness + liveness (+ startup for slow starters);
- a PDB per service;
- topology spread across zones;
- `maxUnavailable: 0` during rollouts, preStop and graceful shutdown;
- HPA or KEDA configured and load-tested.

**Security**

- PSS `restricted`, NetworkPolicy `default deny`;
- Pod Identity with a dedicated role per service;
- images from your own ECR, immutable tags, scanning, signatures;
- GuardDuty EKS Protection;
- secrets in Secrets Manager, not in Git.

**Operations**

- the dashboards and alerts from Module 12;
- application and PV backups with verified restores;
- a runbook for the usual failures;
- budgets and a per-namespace cost breakdown;
- separate accounts for prod and non-prod.

## 18.6 EKS anti-patterns

- **One cluster for everything: prod, dev and experiments.** One bad webhook or CRD takes down everything at once.
- **A cluster built by hand in the console.** A year later it can't be reproduced and nobody dares change anything.
- **`cluster-admin` for everyone.** Later it's impossible to tell who deleted the Deployment (and without audit logs, literally impossible).
- **No `requests`/`limits`.** The cluster works right up until one pod eats a node.
- **No PDBs.** Any drain, consolidation or Spot interruption becomes an incident.
- **A database in the cluster "because it's modern"**, with no operator, no backups and nobody who can restore it.
- **Ingress-NGINX in 2026** with no migration plan.
- **Ignoring end-of-support** and getting a forced upgrade from AWS at the worst possible moment.
- **Monitoring that means "we look at CloudWatch when people complain".**
- **Microservices chatting across AZs** for no reason: you pay for every gigabyte twice.
- **Manual `kubectl edit` in production** instead of Git.
- **Secrets in ConfigMaps.** Yes, this happens more often than you'd like.

### Self-check questions

1. Why do people put system workloads on a separate On-Demand node group?
2. How many pods per node should you plan for, and why not the ENI maximum?
3. What belongs in IaC, and what's acceptable in Helm/GitOps?
4. What five things would you check first on an unfamiliar production cluster?
5. Name three anti-patterns you've seen or will see in a real project.

---

# Module 19. Capstone project: a production-grade cluster

## 19.1 What we're building

A platform for a small production environment with two services and a background worker, entirely from code.

```
                      Route 53 (app.example.com)
                              |
                         ALB (shared-prod group, ACM, WAF)
                              |
              +---------------+---------------+
              |                               |
        web (3-20 replicas)            api (3-30 replicas)
              |                               |
              +-------------> Redis (ElastiCache)
                              |
                         Aurora PostgreSQL (Multi-AZ)
                              |
        worker (0-50 replicas, KEDA on SQS, Spot+ARM)
                              |
                         S3 (artifacts, accessed via Pod Identity)

EKS 1.36 cluster, 3 AZs
  node group "system" (On-Demand, taint=system): CoreDNS, Karpenter, LBC, Argo CD, monitoring
  NodePool "apps"  (On-Demand + Spot, amd64 + arm64)
  NodePool "batch" (Spot only, taint=batch)
Delivery: Argo CD from Git, images from ECR
Observability: kube-prometheus-stack + Container Insights + audit logs
```

## 19.2 Requirements

**Infrastructure**

1. Everything is created from scratch with `terraform apply`: VPC, 3 AZs, private nodes, VPC endpoints, EKS 1.36.
2. `authenticationMode=API` with three access entries: admin (cluster), dev (namespace `apps`, edit), viewer (cluster, view).
3. Pinned add-on versions: vpc-cni with prefix delegation and network policy, coredns, kube-proxy, pod-identity-agent, ebs-csi, metrics-server.
4. Karpenter with two NodePools, `expireAfter: 336h`, a 10% disruption budget.
5. Audit logs in CloudWatch with 30-day retention, KMS encryption for secrets.

**Applications**

6. Three services in the `apps` namespace: `web`, `api`, `worker`; a Helm chart with per-environment values.
7. All of them have measured `requests`, a `limits.memory`, readiness/liveness probes, a PDB and zone topology spread.
8. `web` and `api` share one ALB (`group.name: shared-prod`), HTTPS via ACM, HTTP redirected.
9. An HPA on `api` (CPU 70%, 3-30) and KEDA on `worker` by SQS depth (0-50, Spot+ARM).
10. `api` reads Aurora credentials from Secrets Manager via the CSI driver and writes to S3 via Pod Identity. Not a single static key.

**Security**

11. PSS `restricted` on the `apps` namespace, every container non-root with `readOnlyRootFilesystem`.
12. NetworkPolicy: `default deny` for ingress and egress; only web→api, api→Aurora/Redis/DNS, worker→SQS/S3/DNS allowed.
13. ECR with immutable tags and enhanced scanning; Kyverno blocks non-ECR images and `:latest`.
14. IMDSv2 and `hopLimit: 1` on every node.

**Delivery and observability**

15. GitHub Actions with OIDC: builds a multi-arch image, pushes to ECR, bumps the tag in the GitOps repo. CI has no cluster access.
16. Argo CD with `automated.prune` and `selfHeal`, an ApplicationSet for dev and prod.
17. A dashboard and at least six alerts from Module 12.
18. Velero: a daily backup of the `apps` namespace including volumes, with a verified restore.
19. Cost tags on every resource and a Budget with an alert.

## 19.3 Stages

| Stage | What you do | Done when |
|---|---|---|
| 1 | VPC, EKS, add-ons in Terraform | `kubectl get nodes` shows nodes in 3 AZs |
| 2 | Access entries, RBAC | The dev role sees `apps` but not `kube-system` |
| 3 | Karpenter, two NodePools | 30 replicas bring up nodes; 2 replicas trigger consolidation |
| 4 | LBC, ALB, ACM, ExternalDNS | `curl https://app.example.com` returns 200 |
| 5 | Application charts, PDBs, probes | `kubectl drain` on any node produces no 5xx |
| 6 | Pod Identity, Secrets Manager CSI | Zero keys in manifests; `sts get-caller-identity` from a pod shows the service role |
| 7 | HPA and KEDA | `hey` load scales api; 1000 SQS messages scale worker from zero |
| 8 | PSS, NetworkPolicy, Kyverno | A root pod is rejected; `curl` from web to the database fails |
| 9 | CI + Argo CD | `git push` reaches the cluster with no human in the loop |
| 10 | Observability, alerts, backups | An alert fires on an artificial failure; a restore is verified |
| 11 | An upgrade | A minor version upgrade with no service downtime |
| 12 | An AZ failure | Drain a whole zone: the service survives, no `Pending` pods |

## 19.4 How to verify it worked

```bash
# 1. load and autoscaling
kubectl -n apps run load --rm -it --image=williamyeh/hey -- -z 300s -c 200 https://app.example.com/api/health
watch -n2 'kubectl -n apps get hpa,pods | head -30; kubectl get nodes | wc -l'

# 2. an AZ failure under load
Z=eu-central-1b
kubectl drain $(kubectl get nodes -l topology.kubernetes.io/zone=$Z -o name) \
  --ignore-daemonsets --delete-emptydir-data --force
# expect: zero errors in ALB metrics, pods relocated, no Pending

# 3. deploying under load
git commit --allow-empty -m "deploy test" && git push
# expect: zero 5xx in the target group, Argo CD Synced within minutes

# 4. security
kubectl -n apps run bad --image=nginx --overrides='{"spec":{"containers":[{"name":"bad","image":"nginx","securityContext":{"runAsUser":0,"privileged":true}}]}}'
# expect: rejected by Pod Security Admission

kubectl -n apps run bad2 --image=docker.io/library/nginx:latest
# expect: rejected by Kyverno (not our ECR, plus the latest tag)

kubectl -n apps exec deploy/web -- curl -s --max-time 3 http://169.254.169.254/latest/meta-data/
# expect: a timeout

# 5. restore
velero restore create check --from-backup $(velero backup get -o name | head -1) \
  --namespace-mappings apps:apps-restore
kubectl -n apps-restore get pods,pvc

# 6. cost
aws ce get-cost-and-usage --time-period Start=$(date -d '7 days ago' +%F),End=$(date +%F) \
  --granularity DAILY --metrics UnblendedCost \
  --group-by Type=TAG,Key=eks:cluster-name
```

If all of that passes, you know EKS at the level expected from a senior DevOps engineer. And don't forget:

```bash
terraform destroy
```

---
# EKS command cheat sheet

```bash
# ---------- AWS CLI: clusters ----------
aws eks list-clusters
aws eks describe-cluster --name demo
aws eks describe-cluster --name demo --query 'cluster.{v:version,status:status,ep:endpoint,health:health}'
aws eks update-kubeconfig --name demo --region eu-central-1 --alias demo
aws eks update-cluster-version --name demo --kubernetes-version 1.36
aws eks wait cluster-active --name demo
aws eks list-insights --cluster-name demo
aws eks describe-insight --cluster-name demo --id <id>

# endpoint and logging
aws eks update-cluster-config --name demo \
  --resources-vpc-config endpointPublicAccess=true,publicAccessCidrs=203.0.113.0/24,endpointPrivateAccess=true
aws eks update-cluster-config --name demo \
  --logging '{"clusterLogging":[{"types":["api","audit","authenticator"],"enabled":true}]}'

# ---------- access ----------
aws eks list-access-entries --cluster-name demo
aws eks create-access-entry --cluster-name demo --principal-arn <role-arn> --type STANDARD
aws eks associate-access-policy --cluster-name demo --principal-arn <role-arn> \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy \
  --access-scope type=namespace,namespaces=apps
aws eks list-associated-access-policies --cluster-name demo --principal-arn <role-arn>

# ---------- nodes ----------
aws eks list-nodegroups --cluster-name demo
aws eks describe-nodegroup --cluster-name demo --nodegroup-name ng-general
aws eks update-nodegroup-version --cluster-name demo --nodegroup-name ng-general
eksctl get nodegroup --cluster demo
eksctl scale nodegroup --cluster demo --name ng-general --nodes 5 --nodes-min 2 --nodes-max 10
eksctl upgrade nodegroup --cluster demo --name ng-general

# ---------- add-ons ----------
aws eks list-addons --cluster-name demo
aws eks describe-addon --cluster-name demo --addon-name vpc-cni
aws eks describe-addon-versions --kubernetes-version 1.36 --addon-name coredns
aws eks create-addon --cluster-name demo --addon-name metrics-server
aws eks update-addon --cluster-name demo --addon-name vpc-cni \
  --configuration-values '{"env":{"ENABLE_PREFIX_DELEGATION":"true"}}' --resolve-conflicts PRESERVE
aws eks wait addon-active --cluster-name demo --addon-name vpc-cni

# ---------- Pod Identity ----------
aws eks list-pod-identity-associations --cluster-name demo
aws eks create-pod-identity-association --cluster-name demo \
  --namespace apps --service-account api --role-arn <role-arn>
eksctl create podidentityassociation --cluster demo --namespace apps \
  --service-account-name api --permission-policy-arns <policy-arn>

# ---------- eksctl ----------
eksctl create cluster -f cluster.yaml
eksctl create cluster --name demo --enable-auto-mode --version 1.36
eksctl get cluster
eksctl utils describe-stacks --cluster demo
eksctl utils associate-iam-oidc-provider --cluster demo --approve
eksctl create fargateprofile --cluster demo --name fp --namespace batch
eksctl delete cluster --name demo --wait

# ---------- kubectl: basics ----------
kubectl config get-contexts && kubectl config use-context demo
kubectl get nodes -o wide --label-columns=topology.kubernetes.io/zone,node.kubernetes.io/instance-type
kubectl get pods -A -o wide --field-selector=status.phase!=Running
kubectl get events -A --sort-by='.lastTimestamp' | tail -40
kubectl api-resources | grep -i <what-im-looking-for>
kubectl explain deployment.spec.strategy --recursive

# ---------- kubectl: debugging ----------
kubectl -n apps describe pod <pod>
kubectl -n apps logs <pod> --previous --tail=200
kubectl -n apps logs -l app=api --all-containers -f --max-log-requests=20
kubectl -n apps exec -it <pod> -- sh
kubectl debug -it <pod> --image=nicolaka/netshoot --target=<container>
kubectl debug node/<node> -it --image=public.ecr.aws/amazonlinux/amazonlinux:2023
kubectl -n apps port-forward svc/api 8080:80
kubectl auth can-i --list -n apps
kubectl auth can-i get secrets -n kube-system --as=system:serviceaccount:apps:api
kubectl auth whoami

# ---------- kubectl: maintenance ----------
kubectl cordon <node>
kubectl drain <node> --ignore-daemonsets --delete-emptydir-data --grace-period=60
kubectl uncordon <node>
kubectl -n apps rollout restart deploy/api
kubectl -n apps rollout status deploy/api --timeout=5m
kubectl -n apps rollout undo deploy/api
kubectl -n apps scale deploy/api --replicas=6
kubectl top nodes && kubectl top pods -A --sort-by=cpu

# ---------- Karpenter ----------
kubectl get nodepools,ec2nodeclasses
kubectl get nodeclaims -o wide
kubectl describe nodeclaim <name>
kubectl logs -n kube-system deploy/karpenter -f
kubectl annotate node <node> karpenter.sh/do-not-disrupt=true

# ---------- ECR ----------
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin <acct>.dkr.ecr.eu-central-1.amazonaws.com
aws ecr create-repository --repository-name app --image-tag-mutability IMMUTABLE --image-scanning-configuration scanOnPush=true
aws ecr describe-images --repository-name app --query 'sort_by(imageDetails,&imagePushedAt)[-5:].imageTags'
aws ecr describe-image-scan-findings --repository-name app --image-id imageTag=1.2.3

# ---------- networking and AWS-side diagnostics ----------
aws ec2 describe-subnets --filters Name=tag:kubernetes.io/role/internal-elb,Values=1 \
  --query 'Subnets[].{az:AvailabilityZone,cidr:CidrBlock,free:AvailableIpAddressCount}' --output table
aws elbv2 describe-load-balancers --query 'LoadBalancers[].{n:LoadBalancerName,dns:DNSName,scheme:Scheme}' --output table
aws ec2 describe-volumes --filters Name=status,Values=available --query 'Volumes[].VolumeId'
aws ec2 describe-instances --filters Name=tag:eks:cluster-name,Values=demo \
  --query 'Reservations[].Instances[].{id:InstanceId,type:InstanceType,az:Placement.AvailabilityZone,life:InstanceLifecycle}' --output table

# ---------- helm ----------
helm repo add eks https://aws.github.io/eks-charts && helm repo update
helm search repo aws-load-balancer-controller --versions | head
helm upgrade --install <rel> <chart> -n <ns> -f values.yaml --atomic --timeout 10m
helm diff upgrade <rel> <chart> -f values.yaml
helm history <rel> -n <ns> && helm rollback <rel> <rev> -n <ns>
helm template <rel> <chart> -f values.yaml | kubectl apply --dry-run=server -f -
```

---

# Settings cheat sheet

**Cluster (production):**

```
version: in standard support (1.34+ as of September 2026)
endpointPrivateAccess: true
endpointPublicAccess: false  (or a narrow publicAccessCidrs)
authenticationMode: API
logging: api, audit, authenticator (+ scheduler, controllerManager when debugging)
encryptionConfig: secrets → your own KMS key
subnets: 3 private /18-/20 subnets across three AZs
```

**Managed node group (system):**

```
capacityType: ON_DEMAND
instanceTypes: [m6i.large, m6a.large, m5.large]   # 3+ types
amiFamily: AL2023
min/desired/max: 3 / 3 / 6
volumeType: gp3, size: 50-80Gi, encrypted: true
privateNetworking: true
taints: [{key: workload, value: system, effect: NoSchedule}]
updateConfig.maxUnavailablePercentage: 25
```

**Karpenter NodePool (applications):**

```
capacity-type: [spot, on-demand]
instance-category: [c, m, r], instance-generation > 5
arch: [amd64, arm64]
zones: all three AZs
expireAfter: 336h            # a node lives 2 weeks max
consolidationPolicy: WhenEmptyOrUnderutilized
consolidateAfter: 30s-1m
disruption.budgets: 10% (and 0 during peak hours)
limits: cpu/memory set explicitly
metadataOptions: httpTokens=required, hopLimit=1
```

**Deployment (a typical service):**

```
replicas: ≥3
requests.cpu: measured p50-p70 (not "×5 to be safe")
requests.memory = limits.memory
limits.cpu: leave unset (except in multi-tenant clusters)
readinessProbe: mandatory
livenessProbe: "is the process alive" only, no dependency checks
startupProbe: for slow starts
strategy: RollingUpdate, maxUnavailable: 0, maxSurge: 1
terminationGracePeriodSeconds: 60, preStop sleep 15
topologySpreadConstraints: zone DoNotSchedule, host ScheduleAnyway
PDB: minAvailable 80% or maxUnavailable 1
securityContext: runAsNonRoot, readOnlyRootFilesystem, drop ALL, seccomp RuntimeDefault
image: tag + @sha256, from your own ECR
serviceAccount: dedicated, with Pod Identity
```

**Ingress (ALB):**

```
target-type: ip
group.name: shared per environment
listen-ports: HTTP 80 + HTTPS 443, ssl-redirect: 443
certificate-arn: from ACM
healthcheck-path: /healthz
deregistration_delay.timeout_seconds: 30
readiness gate on the namespace: elbv2.k8s.aws/pod-readiness-gate-inject=enabled
```

**StorageClass (EBS):**

```
provisioner: ebs.csi.aws.com
volumeBindingMode: WaitForFirstConsumer     # mandatory
allowVolumeExpansion: true
type: gp3, iops: 3000, throughput: 125, encrypted: true
reclaimPolicy: Retain for production data
```

**VPC CNI:**

```
ENABLE_PREFIX_DELEGATION: true     # enable it on new clusters
WARM_PREFIX_TARGET: 1
ENABLE_NETWORK_POLICY: true
ENABLE_POD_ENI: only if you need security groups for pods
```

---

# Cheat sheet: common failures and fixes

| Symptom / message | Likely cause | What to do |
|---|---|---|
| `You must be logged in to the server (Unauthorized)` | No access entry for your IAM identity, expired credentials, wrong profile | `aws sts get-caller-identity`, `aws eks list-access-entries`, create an access entry |
| `error: You must be logged in` after switching roles | `kubeconfig` points at a different profile | `aws eks update-kubeconfig --profile <p>` |
| Pod `Pending`, `0/3 nodes are available: insufficient cpu` | No room, inflated requests | Review requests, let nodes scale up, `kubectl describe node` |
| Pod `Pending`, `untolerated taint` | Nodes are tainted, the pod has no toleration | Add a toleration or use another NodePool |
| Pod `Pending`, `volume node affinity conflict` | PVC in one AZ, nodes in another | `WaitForFirstConsumer`, nodes in all AZs |
| `FailedCreatePodSandBox: failed to assign an IP address` | Subnet IPs exhausted or ENI limit reached | Prefix delegation, secondary CIDR, custom networking |
| `ImagePullBackOff` / `no basic auth credentials` | Node role lacks ECR permissions, or no path to ECR | `AmazonEC2ContainerRegistryReadOnly`, VPC endpoints ecr.api/ecr.dkr/s3 |
| `ImagePullBackOff: manifest unknown` | Wrong tag or wrong architecture | Check the tag and `--platform` |
| `CrashLoopBackOff` | The application fails at startup | `kubectl logs --previous`, check config and secrets |
| `OOMKilled` in `Last State` | `limits.memory` exceeded | Raise the limit or fix the leak; compare with `kubectl top` |
| Node `NotReady` | kubelet, disk, network, or a deleted `aws-auth` entry | `kubectl describe node`, SSM onto the node, check CNI and `aws-auth` |
| `DiskPressure`, pods evicted | Node disk full (images, logs) | Bigger disk, prune images, cap log volume |
| No ALB created for an Ingress | No LBC, missing subnet tags, missing permissions | `aws-load-balancer-controller` logs, `kubernetes.io/role/elb` tags |
| 5xx during deployments | No readiness gate, no preStop, `maxUnavailable > 0` | Section 8.7 |
| `no endpoints available for service` | No pod is Ready | `kubectl get endpoints`, check readinessProbe and selectors |
| DNS timeouts, slow requests | Too few CoreDNS replicas, `ndots`, throttling | Scale CoreDNS, NodeLocal DNSCache, `dnsConfig` |
| `Multi-Attach error for volume` | An EBS volume attached to two pods | EBS is RWO; use EFS |
| HPA targets show `unknown` | No metrics-server | `aws eks create-addon --addon-name metrics-server` |
| HPA doesn't scale under load | Inflated `requests.cpu` | Bring requests in line with reality |
| `drain` hangs forever | A PDB blocks eviction | `kubectl get pdb -A`, fix `minAvailable` |
| Karpenter creates no nodes | Missing `karpenter.sh/discovery` tags, limits, permissions | Karpenter logs, `kubectl describe nodepool` |
| CloudFormation/Terraform can't delete the VPC | Leftover ENIs, ALBs, security groups from controllers | Delete Ingress/LoadBalancer Services/PVCs first, then the cluster |
| The bill suddenly jumped | Extended support, forgotten ALBs and volumes, cross-AZ, logs | Module 16, resource audit |
| A webhook blocks all deployments | An admission webhook with `failurePolicy: Fail` is down | Restore the webhook or temporarily remove its rule |

---

# EKS interview questions with answers

**Junior**

1. **What does AWS manage in EKS, and what do you?** AWS manages the control plane (apiserver, etcd, scheduler, controller-manager), its patching and backups. You manage nodes, networking, add-ons, applications, security and cost.
2. **What does an EKS cluster cost with no workloads?** $0.10 per hour for the control plane, about $73 a month, plus everything else separately.
3. **Why does `kubectl get pods` return `Unauthorized` even though I have `AdministratorAccess`?** IAM handles authentication; in-cluster permissions come from RBAC via an access entry or `aws-auth`. Two different systems.
4. **Why does EKS need at least two subnets in different AZs?** For control plane HA and for the EKS-owned ENIs the apiserver uses to reach kubelet.
5. **How does a managed node group differ from self-managed nodes?** EKS creates the ASG, registers nodes, performs graceful drains on updates, and monitors node health.
6. **What is Fargate in EKS?** A compute mode where each pod runs in its own micro-VM with no nodes. No DaemonSets, no GPUs, no privileged containers.
7. **Why doesn't `kubectl top nodes` work on a new cluster?** `metrics-server` isn't installed; it doesn't ship with the cluster.
8. **What does `aws eks update-kubeconfig` do?** It writes a context where the token comes from `aws eks get-token`, so authentication uses your AWS credentials.
9. **Which three add-ons are mandatory?** `vpc-cni`, `coredns`, `kube-proxy`.
10. **Why do you need a readinessProbe?** So traffic (including from an ALB) never reaches a pod that isn't ready to serve requests.

**Middle**

11. **How does a pod get an IP in EKS, and what's the catch?** Through the VPC CNI a pod gets a real subnet address. The catch: subnet IPs run out, and pods per node are limited by ENIs.
12. **How do you compute max pods per node and how do you raise it?** `(ENIs × (IPs per ENI − 1)) + 2`; prefix delegation raises it (`m6i.large`: 29 → 110).
13. **What do you do when a subnet runs out of IPs?** Prefix delegation, a secondary CIDR with custom networking, an IPv6 cluster, lower warm targets, and as a last resort a different CNI.
14. **Why are access entries better than `aws-auth`?** They're an EKS API: versioned in IaC, no risk of locking everyone out with a ConfigMap typo, with built-in access policies and namespace scoping.
15. **Pod Identity or IRSA?** Pod Identity by default: one role across many clusters, no OIDC in the trust policy, no annotations, plus session policies and tags. IRSA for Fargate and cross-account access.
16. **How do you stop pods from using the node role?** IMDSv2 (`httpTokens: required`) and `httpPutResponseHopLimit: 1`, plus dedicated roles through Pod Identity.
17. **Why is Karpenter better than Cluster Autoscaler?** It creates instances directly and matches types to pods, works in tens of seconds, consolidates workloads, handles Spot natively, and needs 1-2 NodePools instead of dozens of node groups.
18. **Why does Karpenter "not save money"?** It plans against `requests`. Inflated requests mean hardware you bought and don't use.
19. **ALB or NLB, and why?** ALB for HTTP/HTTPS with routing, WAF and authentication; NLB for TCP/UDP, gRPC, static IPs and minimal latency.
20. **What does `target-type: ip` give you on an ALB Ingress?** Traffic goes straight to pods, bypassing NodePort: fewer hops, working readiness gates, better balancing.
21. **How do you deploy without 5xx?** `maxUnavailable: 0`, a readiness gate, a preStop pause, a short deregistration delay, and proper SIGTERM handling.
22. **Why does an EBS volume prevent moving a pod?** EBS exists in a single AZ, so the pod can only be scheduled there; with `Immediate` binding that produces `volume node affinity conflict`.
23. **When EFS instead of EBS?** When you need ReadWriteMany from multiple pods and AZs; price and latency are higher.
24. **Why a PodDisruptionBudget?** It limits voluntary evictions: node group upgrades, Karpenter consolidation, node replacement, drains on Spot interruption.
25. **What does `topologySpreadConstraints` with `DoNotSchedule` across zones do?** It forces replicas to spread across AZs so a single zone failure doesn't take the whole service down.
26. **How does HPA differ from KEDA?** HPA scales on CPU/memory and custom metrics and can't reach zero; KEDA scales on external events (SQS, Kafka, Prometheus) and supports scale-to-zero.
27. **How do you enable network policy without a third-party CNI?** `ENABLE_NETWORK_POLICY=true` on the VPC CNI; since 2026 there are also cluster-level Admin Policies.
28. **What is an EKS add-on and how does it differ from a Helm install?** Its version is managed by the EKS API, AWS owns compatibility and CVEs, configuration goes through `configuration-values`, and manual edits can be overwritten with `OVERWRITE`.
29. **Which control plane logs do you enable and why?** `api`, `audit`, `authenticator` at minimum: without them you can't investigate an incident or find out who deleted what.
30. **What happens to running pods if the control plane is unavailable?** They keep running: kubelet holds the containers, kube-proxy the rules, the ALB the traffic. What breaks is management: deployments, autoscaling, recreating pods.

**Senior**

31. **How would you design a VPC for a 2000-pod cluster?** Three AZs, /18 private subnets for nodes and pods, /20 public subnets for ALBs and NAT, prefix delegation from day one, headroom for a secondary CIDR (`100.64.0.0/16`), VPC endpoints for ECR/S3/STS/logs, and the LBC subnet tags. Separately, verify EC2 and ENI quotas.
32. **What's your version upgrade strategy?** Upgrade every 6-9 months, one minor at a time; before each one run cluster insights and `pluto`/`kubent` and upgrade operators; order is control plane → add-ons → nodes; in critical environments do blue-green clusters. Monitor AWS Health and stay in standard support so you never pay $0.60/hour.
33. **Auto Mode or your own Karpenter?** Auto Mode if the team is small, the cluster is new and minimum toil is the goal; your own Karpenter if you need a custom AMI, precise version control, node SSH access, special security agents, or the fleet is big enough that the 12% premium exceeds the engineering time it saves. Savings Plans don't cover the premium.
34. **How would you cut a cluster's bill in half?** Start with right-sizing requests (usually the biggest source), then Spot and Graviton through Karpenter with consolidation, merge Ingresses onto one ALB, move traffic out of NAT into VPC endpoints, reduce cross-AZ chatter, trim logs and metrics, consolidate dev clusters, buy Savings Plans for the baseline, and get off extended support.
35. **How do you do multi-tenancy?** Namespaces with PSS `restricted`, `ResourceQuota` and `LimitRange`, `default deny` NetworkPolicies, namespace-scoped access entries, dedicated tainted NodePools, a load balancer quota, Kyverno policies, and cost attribution. And say honestly that a namespace isn't a security boundary: hostile tenants need separate clusters.
36. **One big cluster or many small ones?** Many small: better failure isolation, easier upgrades, smaller blast radius; more expensive in control plane fees and harder to operate. One big: cheaper and simpler platform-wise, but a bad webhook, CRD or CNI affects everyone. Usually: prod separate from non-prod, then split by domain or regulatory boundary.
37. **How do you design DR?** Start with data: Aurora Global Database or DynamoDB Global Tables, S3 CRR, ECR replication. The cluster is reproducible from IaC plus GitOps in minutes, so pilot light is typical: a minimal cluster in a second region, Route 53 failover with health checks, regular restore drills and a measured real RTO/RPO.
38. **What do you do when the apiserver lags at peaks?** Look at `apiserver_request_duration_seconds`, find the sources of watches and list-all calls (badly behaved controllers and operators), reduce polling frequency, add caching, enable Provisioned Control Plane at the right tier, and shard workloads across clusters if needed.
39. **How do you move a cluster to private-only without losing access?** Beforehand: VPC endpoints (eks, ecr, sts, logs, ssm), CI runners in the VPC, VPN or SSM port forwarding, a bastion, and a break-glass role with an access entry. Verify the access paths, switch, verify again. Keep an access recovery plan.
40. **How would you take over an unfamiliar production cluster?** Check the version and support window, audit logs, who has access (access entries and `aws-auth`), endpoint access, whether services have PDBs and probes, add-on state and versions, free subnet IPs, where deployments come from (is there drift from Git), backups and whether they're verified, dashboards and alerts, and cost attribution. Everything you find goes into a backlog prioritized by risk.

---

# FAQ: common EKS questions

**Is it true that EKS costs $73 a month?**
That's the control plane only. A real small production bill is $300-600: nodes, NAT Gateway, load balancers, disks, logs and cross-AZ traffic.

**Can I run a cluster with no nodes at all?**
Yes, on Fargate or Auto Mode: nodes appear only for pods (on Fargate there are no nodes at all). The control plane fee applies regardless.

**What happens if I never upgrade the version?**
After 14 months the cluster enters extended support at $0.60/hour instead of $0.10. Twelve months later AWS upgrades it by force.

**Does EKS upgrade nodes for me?**
In Auto Mode, yes, and a node lives at most 21 days. In a managed node group you trigger the AMI update (`update-nodegroup-version`) and EKS does a rolling replacement respecting PDBs. With Karpenter nodes are replaced by `expireAfter` and on AMI drift.

**Do I need Cluster Autoscaler if I have Karpenter?**
No, they solve the same problem. Karpenter is the modern choice.

**Auto Mode and Karpenter at the same time?**
You can mix Auto Mode nodes with regular node groups in one cluster, but never run two node autoscalers against the same workload: that's a conflict.

**Why does a pod get a VPC IP instead of an overlay address?**
That's how the Amazon VPC CNI works. Upsides: performance, VPC visibility, security groups for pods. Downside: subnet IPs are finite.

**How many pods fit on a `t3.medium`?**
17, a significant share of which goes to DaemonSets. For real work use `large` or bigger.

**Is `aws-auth` mandatory?**
No. Use access entries and `API` mode. Older clusters still have `aws-auth`, but it's legacy.

**Can I grant cluster access without IAM?**
No: EKS authentication goes through IAM (or the cluster OIDC provider for service tokens). Humans get access through SSO roles.

**Where should secrets live?**
In AWS Secrets Manager or SSM Parameter Store, mounted through the Secrets Store CSI driver or synced with External Secrets. Enable KMS etcd encryption for Kubernetes Secrets and never keep them in Git.

**Should I run a database in the cluster?**
Usually no: RDS/Aurora is cheaper in total cost and more reliable without a dedicated team. In-cluster databases make sense when there's a mature operator and people who can restore data.

**What do I do about Ingress-NGINX?**
Upstream retired it in March 2026. Plan a migration to the Gateway API or ALB Ingress; there's no drop-in replacement, it's real engineering work.

**Can I move a cluster to another VPC or region?**
No. A cluster is created in a specific VPC and region. "Moving" means a new cluster and a workload migration (which, conveniently, is exactly what GitOps makes easy).

**Can I change an existing cluster's subnets?**
You can add subnets for nodes; you can't change the control plane subnet set. Plan addressing up front.

**Does EKS work with on-prem?**
Yes: **EKS Hybrid Nodes** attach your own servers (or edge hardware) to a control plane in AWS, billed per vCPU. There's also EKS Anywhere for fully local clusters.

**How do I find out who deleted a Deployment?**
Only from control plane audit logs. If they weren't enabled, you won't. Enable them today.

**Why is a pod `Pending` when there are nodes?**
Five common causes: insufficient CPU/memory against `requests`, a taint with no toleration, a PVC in another AZ, exhausted IPs, or a `DoNotSchedule` topology spread that can't be satisfied. The answer is always in `kubectl describe pod`.

**EKS or ECS for a new project?**
If you need the Kubernetes ecosystem, portability, or you already have the expertise — EKS. If it's a handful of simple services and AWS-only, ECS will be cheaper to operate.

**How many clusters should I run?**
At least two: prod and non-prod, in separate accounts. Beyond that, as needed: regulation, regions, team isolation.

---

# EKS glossary

| Term | Meaning |
|---|---|
| **Control plane** | The AWS-managed part: apiserver, etcd, scheduler, controller-manager |
| **Data plane** | Your nodes and pods |
| **EKS-owned ENI** | A network interface in your subnet that the control plane uses to reach kubelet |
| **Cluster SG** | The `eks-cluster-sg-*` security group tying the cluster and nodes together |
| **Cluster IAM role** | The identity EKS uses to manage resources in your account |
| **Node IAM role** | The node instance role (ECR, CNI, SSM) |
| **Access entry** | An EKS API record binding an IAM principal to cluster permissions |
| **Access policy** | A built-in EKS permission set (`AmazonEKSClusterAdminPolicy` and others) |
| **aws-auth** | The legacy ConfigMap mapping IAM to Kubernetes |
| **authenticationMode** | `CONFIG_MAP`, `API_AND_CONFIG_MAP` or `API` |
| **IRSA** | IAM Roles for Service Accounts via the cluster OIDC provider |
| **EKS Pod Identity** | The modern way to give a pod an IAM role, via an agent and an association |
| **Session policy** | Narrowing a specific Pod Identity association without a new role |
| **Managed node group** | A node group EKS manages (ASG + drain + health) |
| **Self-managed node** | A node in your own ASG that you register and patch yourself |
| **Fargate profile** | The rule deciding which namespace/labels land on Fargate |
| **EKS Auto Mode** | A mode where AWS manages nodes, storage, load balancing and identity |
| **Karpenter** | A node autoscaler that creates EC2 instances directly for pending pods |
| **NodePool / EC2NodeClass** | Karpenter rules: which nodes, and what to build them from |
| **NodeClaim** | Karpenter's request for a specific node |
| **Consolidation** | Packing workloads tighter and removing surplus nodes |
| **Drift** | A node diverging from the desired configuration (a new AMI, for example) |
| **Disruption budget** | A cap on how many nodes may be disrupted at once |
| **VPC CNI** | The network plugin giving pods real VPC IPs |
| **Prefix delegation** | Assigning /28 blocks to an ENI instead of individual IPs |
| **Custom networking** | Placing pods in separate subnets (a secondary CIDR) via ENIConfig |
| **Security groups for pods** | A branch ENI with a dedicated SG for a specific pod |
| **max pods** | The per-node pod limit derived from ENIs and IPs |
| **AWS Load Balancer Controller** | The controller creating ALBs from Ingress and NLBs from Service |
| **Target type: ip** | Registering pods directly in a target group |
| **Readiness gate** | A pod readiness condition based on ALB confirmation |
| **Gateway API** | The modern Ingress successor with role separation |
| **EBS CSI / EFS CSI / Mountpoint S3** | Storage drivers |
| **WaitForFirstConsumer** | Binding mode where the volume is created in the pod's AZ |
| **VolumeSnapshot** | A PV snapshot through CSI |
| **PSS (Pod Security Standards)** | The `privileged`, `baseline` and `restricted` namespace levels |
| **NetworkPolicy** | Rules for network access between pods |
| **Admin Policy** | A cluster-level network policy that outranks user policies |
| **EKS add-on** | A component whose version is managed by the EKS API |
| **EKS Capabilities** | Managed platform components (Argo CD, ACK, kro) |
| **Provisioned Control Plane** | Pre-provisioned control plane performance tiers (XL...8XL), 99.99% SLA |
| **EKS Hybrid Nodes** | Nodes outside AWS driven by an EKS control plane |
| **Cluster insights** | Automated upgrade-readiness checks |
| **Standard / Extended support** | 14 months at $0.10/hour, then 12 more at $0.60/hour |
| **Platform version** | The internal EKS revision (`eks.5`) within a Kubernetes minor |
| **Container Insights** | Cluster metrics and logs in CloudWatch |
| **ADOT** | The AWS Distro for OpenTelemetry |
| **AMP / AMG** | Amazon Managed Prometheus and Managed Grafana |
| **GuardDuty EKS Protection** | Audit log analysis plus runtime threat monitoring |
| **Velero** | A tool for backing up and restoring Kubernetes objects and PVs |

---

# Official sources and what to read next

- **EKS documentation** — https://docs.aws.amazon.com/eks/latest/userguide/
- **EKS Best Practices Guides** (required reading: security, reliability, cost, networking) — https://docs.aws.amazon.com/eks/latest/best-practices/
- **Version calendar and lifecycle** — https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html
- **EKS pricing** — https://aws.amazon.com/eks/pricing/
- **EKS Workshop** (the best hands-on lab from AWS) — https://www.eksworkshop.com
- **eksctl** — https://eksctl.io
- **Terraform EKS module** — https://github.com/terraform-aws-modules/terraform-eks
- **EKS Blueprints** — https://github.com/aws-ia/terraform-aws-eks-blueprints
- **Karpenter** — https://karpenter.sh
- **AWS Load Balancer Controller** — https://kubernetes-sigs.github.io/aws-load-balancer-controller/
- **Amazon VPC CNI** — https://github.com/aws/amazon-vpc-cni-k8s
- **EKS-optimized AMIs** — https://github.com/awslabs/amazon-eks-ami
- **AWS Containers blog** — https://aws.amazon.com/blogs/containers/
- **What's new in EKS** — https://aws.amazon.com/about-aws/whats-new/containers/
- **Kubernetes documentation** — https://kubernetes.io/docs/
- **Gateway API** — https://gateway-api.sigs.k8s.io
- **Argo CD** — https://argo-cd.readthedocs.io
- **KEDA** — https://keda.sh
- **Velero** — https://velero.io
- **Kyverno** — https://kyverno.io
- **OpenCost** — https://www.opencost.io

---

## How to contribute

Found an error, an inaccuracy or an outdated setting? Open an issue or send a pull request. Especially welcome:

- real EKS incident write-ups and postmortems;
- examples in CDK, Pulumi and CloudFormation alongside Terraform and eksctl;
- corrections for new EKS, add-on and Karpenter versions;
- cost numbers from real bills (with details anonymized).

⭐ If this course helped, leave a star so other engineers can find it.

**License:** the course materials are freely distributable — use them for learning, internal workshops and interview preparation.

**Disclaimer:** prices are for us-east-1 as of September 2026 and are indicative only — always check current values on the AWS pricing page. Verify Kubernetes versions and support windows against the official EKS version calendar.
