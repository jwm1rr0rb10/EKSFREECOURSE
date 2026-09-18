# Amazon EKS курс 2026: бесплатный курс по EKS и Kubernetes в AWS с нуля до production

![Amazon EKS](https://img.shields.io/badge/Amazon%20EKS-Kubernetes%201.36-FF9900?logo=amazonaws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1.36-326CE5?logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-cloud-orange?logo=amazonaws&logoColor=white)
![Курс на русском](https://img.shields.io/badge/язык-русский-red)
![Бесплатный курс](https://img.shields.io/badge/цена-бесплатно-brightgreen)
![Junior → Senior](https://img.shields.io/badge/уровень-junior%20%E2%86%92%20senior-orange)

> **Полный бесплатный курс по Amazon EKS на русском языке.** Kubernetes, AWS, VPC, IAM, EKS Auto Mode, Managed Node Groups, Pod Identity, EBS/EFS, ALB/NLB, HPA, Karpenter, NetworkPolicy, Secrets, observability, Helm, Terraform, GitOps, CI/CD, upgrades, troubleshooting, cost optimization и production-архитектура.
>
> Всё в одном README: теория, схемы, YAML, AWS CLI, `kubectl`, `eksctl`, Helm, Terraform, типичные ошибки, практические задания и вопросы для самопроверки.
>
> **Актуальность:** примеры ориентированы на Amazon EKS и Kubernetes **1.36**; на момент подготовки курса версии `1.36`, `1.35` и `1.34` находятся в standard support EKS. Перед лабораторной всегда проверяй актуальную матрицу поддерживаемых версий в официальной документации AWS.

> ⚠️ **Стоимость:** EKS, EC2, NAT Gateway, Load Balancer, EBS/EFS, CloudWatch и другие AWS-ресурсы могут тарифицироваться. Лаборатории с кластером запускай осознанно и удаляй ресурсы после практики.

⭐ Если курс полезен, поставь звезду репозиторию — так его найдут другие инженеры.

---

## Для кого этот курс по EKS

| Кто ты | Что получишь |
|---|---|
| **Новичок в Kubernetes** | Поймёшь Pods, Deployments, Services, ConfigMaps, Secrets, Ingress и RBAC на реальном AWS-кластере |
| **Backend-разработчик** | Научишься деплоить сервисы в EKS, подключать S3/RDS/Secrets и работать с autoscaling |
| **DevOps / Platform Engineer** | Поймёшь полный lifecycle EKS: networking, IAM, node groups, upgrades, add-ons, observability и security |
| **SRE** | Получишь практику HA, PDB, topology spread, HPA, Karpenter, диагностики и disaster recovery |
| **Cloud Engineer** | Свяжешь Kubernetes с VPC, IAM, ELB, EBS, EFS, KMS, Route 53, CloudWatch и ECR |
| **Terraform Engineer** | Построишь EKS как код и научишься отделять инфраструктуру от Kubernetes-манифестов |
| **Готовишься к собеседованию** | Получишь набор вопросов уровня junior / middle / senior и production-сценарии |
| **Архитектор / Tech Lead** | Научишься выбирать между Auto Mode, Managed Node Groups, Karpenter, ALB/NLB, EBS/EFS и разными моделями доступа |

## Что ты будешь уметь после курса

- объяснить архитектуру EKS: control plane, API server, etcd, scheduler, nodes, kubelet, controllers;
- объяснить, что AWS управляет в EKS, а что остаётся на стороне клиента;
- создать кластер через `eksctl` и понять, какие AWS-ресурсы были созданы;
- развернуть кластер в VPC с public/private subnets и несколькими Availability Zones;
- понимать работу Amazon VPC CNI и связь Kubernetes Pod IP с VPC;
- пользоваться EKS Auto Mode и понимать, чем он отличается от классической модели EKS;
- создавать и обновлять Managed Node Groups;
- деплоить приложения через Deployment, Service, ConfigMap и Secret;
- понимать `requests`, `limits`, probes, ReplicaSet и rollout;
- управлять доступом через EKS Access Entries, Kubernetes RBAC и IAM;
- выдавать AWS permissions Pod'ам через EKS Pod Identity и понимать legacy IRSA;
- подключать EBS CSI и EFS CSI для stateful workloads;
- публиковать сервисы через AWS Load Balancer Controller, ALB и NLB;
- понимать разницу между `ClusterIP`, `NodePort`, `LoadBalancer`, Ingress и Gateway;
- настраивать HPA и понимать связь autoscaling с metrics;
- использовать Karpenter и проектировать NodePool под реальные workload'ы;
- обеспечивать HA через PDB, topology spread, anti-affinity и multi-AZ deployment;
- строить NetworkPolicy и понимать границы между SG, NetworkPolicy и IAM;
- шифровать Kubernetes API data и Secrets с AWS KMS;
- собирать логи, метрики и трассировки через CloudWatch / Prometheus / OpenTelemetry;
- использовать Helm, Terraform, Kustomize и GitOps;
- строить CI/CD: GitHub Actions → ECR → EKS;
- выполнять безопасные upgrade'ы Kubernetes и node groups;
- диагностировать `Pending`, `CrashLoopBackOff`, `ImagePullBackOff`, DNS, CNI, IAM и LB-проблемы;
- оптимизировать стоимость и планировать capacity;
- проектировать production EKS-платформу с security, observability, autoscaling и DR.

---

## Содержание

- [Для кого этот курс по EKS](#для-кого-этот-курс-по-eks)
- [Что ты будешь уметь после курса](#что-ты-будешь-уметь-после-курса)
- [Как проходить курс](#как-проходить-курс)
- [Правила и переменные лабораторий](#правила-и-переменные-лабораторий)
- [Модуль 0. Что такое EKS и зачем он нужен](#модуль-0-что-такое-eks-и-зачем-он-нужен)
- [Модуль 1. Kubernetes внутри EKS](#модуль-1-kubernetes-внутри-eks)
- [Модуль 2. AWS CLI, eksctl, kubectl, Helm и Terraform](#модуль-2-aws-cli-eksctl-kubectl-helm-и-terraform)
- [Модуль 3. AWS networking: VPC, subnets, AZ и VPC CNI](#модуль-3-aws-networking-vpc-subnets-az-и-vpc-cni)
- [Модуль 4. Создание EKS: Auto Mode и классический EKS](#модуль-4-создание-eks-auto-mode-и-классический-eks)
- [Модуль 5. Workloads: Pod, Deployment, Service, ConfigMap, Secret](#модуль-5-workloads-pod-deployment-service-configmap-secret)
- [Модуль 6. IAM и доступ к кластеру: Access Entries и RBAC](#модуль-6-iam-и-доступ-к-кластеру-access-entries-и-rbac)
- [Модуль 7. IAM для Pod'ов: EKS Pod Identity и IRSA](#модуль-7-iam-для-подов-eks-pod-identity-и-irsa)
- [Модуль 8. Storage: EBS, EFS, PVC и Stateful workloads](#модуль-8-storage-ebs-efs-pvc-и-stateful-workloads)
- [Модуль 9. Networking приложений: Service, ALB, NLB и Ingress](#модуль-9-networking-приложений-service-alb-nlb-и-ingress)
- [Модуль 10. Scheduling: requests, limits, probes, taints, affinity](#модуль-10-scheduling-requests-limits-probes-taints-affinity)
- [Модуль 11. Scaling: HPA, Karpenter, Managed Node Groups и Auto Mode](#модуль-11-scaling-hpa-karpenter-managed-node-groups-и-auto-mode)
- [Модуль 12. High Availability и graceful disruptions](#модуль-12-high-availability-и-graceful-disruptions)
- [Модуль 13. Security: Pod Security, NetworkPolicy, SG, KMS](#модуль-13-security-pod-security-networkpolicy-sg-kms)
- [Модуль 14. Observability: logs, metrics, events, traces](#модуль-14-observability-logs-metrics-events-traces)
- [Модуль 15. Helm, Kustomize и GitOps](#модуль-15-helm-kustomize-и-gitops)
- [Модуль 16. CI/CD: GitHub Actions, ECR и deploy в EKS](#модуль-16-cicd-github-actions-ecr-и-deploy-в-eks)
- [Модуль 17. Lifecycle: add-ons, upgrades и node maintenance](#модуль-17-lifecycle-add-ons-upgrades-и-node-maintenance)
- [Модуль 18. Troubleshooting и production diagnostics](#модуль-18-troubleshooting-и-production-diagnostics)
- [Модуль 19. Production architecture и итоговый проект](#модуль-19-production-architecture-и-итоговый-проект)
- [Шпаргалка AWS CLI + EKS](#шпаргалка-aws-cli--eks)
- [Шпаргалка kubectl](#шпаргалка-kubectl)
- [Шпаргалка Helm](#шпаргалка-helm)
- [Шпаргалка диагностики](#шпаргалка-диагностики)
- [Вопросы на собеседовании по EKS](#вопросы-на-собеседовании-по-eks)
- [FAQ](#faq)
- [Глоссарий EKS](#глоссарий-eks)
- [Официальные источники](#официальные-источники)

---

## Как проходить курс

1. **Не пропускай Kubernetes-базу.** EKS — это managed Kubernetes, а не отдельная версия Kubernetes.
2. **Выполняй команды руками.** Один час лаборатории полезнее трёх часов чтения.
3. **Ломай кластер безопасно.** Удали Pod, уменьши replicas, сделай rollout, посади Pod в `Pending`, посмотри events.
4. **Проверяй, где заканчивается Kubernetes и начинается AWS.** Это главный навык EKS-инженера.
5. **Делай заметки по каждой ошибке.** Production-знания появляются из диагностики.
6. **Иди до итогового проекта.** В нём темы соединятся в одну архитектуру.

### Что нужно установить

Для Linux/macOS/WSL2:

- AWS CLI v2;
- `kubectl`;
- `eksctl`;
- Helm 3;
- Git;
- Docker;
- Terraform;
- `jq` желательно;
- IDE с YAML/Kubernetes поддержкой.

Официальный путь AWS для старта рекомендует подготовить AWS CLI, `kubectl`, `eksctl`, а Helm — как удобный package manager для Kubernetes-инструментов. https://docs.aws.amazon.com/eks/latest/userguide/setting-up.html

---

## Правила и переменные лабораторий

Во всех командах используем переменные:

```bash
export AWS_REGION=eu-central-1
export CLUSTER_NAME=eks-course
export AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query Account --output text)
```

Проверка:

```bash
aws sts get-caller-identity
aws eks list-clusters --region "$AWS_REGION"
eksctl version
kubectl version --client
helm version
terraform version
```

> `eu-central-1` выбран только как пример. Используй регион, доступный в твоём аккаунте, с нужными типами EC2 и EKS-функциями.

### Полезная привычка

Перед любой лабораторией сначала смотри контекст:

```bash
aws configure list
aws sts get-caller-identity
aws eks list-clusters --region "$AWS_REGION"
kubectl config current-context
```

Это спасает от классической ошибки: **«я удалил не тот кластер»**.

---

# Модуль 0. Что такое EKS и зачем он нужен

## 0.1 EKS простыми словами

Amazon Elastic Kubernetes Service — управляемый Kubernetes от AWS. AWS берёт на себя управление Kubernetes control plane, а клиент выбирает, как организовать data plane и инфраструктуру вокруг workload'ов. В текущем EKS доступны как классический EKS, так и EKS Auto Mode. https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html

Главная идея:

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

## 0.2 Что EKS решает

Без managed Kubernetes тебе нужно самостоятельно проектировать и обслуживать:

- control plane;
- etcd;
- API server;
- scheduler/controllers;
- certificates;
- upgrades control plane;
- часть security hardening;
- HA control plane.

С EKS AWS управляет control plane и интегрирует Kubernetes с AWS services.

## 0.3 EKS и обычный Kubernetes

| Объект | Vanilla Kubernetes | EKS |
|---|---|---|
| API Server | Ты управляешь | AWS управляет |
| etcd | Ты управляешь | AWS управляет |
| Scheduler | Ты управляешь | AWS управляет |
| Worker nodes | Ты управляешь | MNG / Auto Mode / self-managed и др. |
| IAM | Внешний к Kubernetes | Глубокая AWS-интеграция |
| VPC networking | зависит от CNI | AWS VPC CNI — основной AWS CNI |
| Load Balancer | зависит от облака | AWS Load Balancer Controller / Auto Mode |
| Storage | CSI drivers | EBS/EFS CSI и Auto Mode capabilities |

## 0.4 Главный принцип EKS

**Kubernetes отвечает за desired state. AWS отвечает за AWS-ресурсы, на которые Kubernetes опирается.**

Например:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: api
spec:
  type: LoadBalancer
```

Kubernetes создаёт объект Service, а controller превращает этот desired state в AWS Load Balancer.

## 0.5 Где EKS подходит плохо

EKS не обязательно нужен для:

- одного маленького приложения на одном сервере;
- простого cron workload;
- приложения, которое удобно запускать как AWS Lambda;
- сервиса без потребности в Kubernetes ecosystem.

Kubernetes ценен, когда нужны стандартизация deployment, self-healing, scheduling, autoscaling, service discovery и большая платформа для множества workload'ов.

### Практика

1. Нарисуй свою архитектуру приложения без Kubernetes.
2. Отметь, что тебе нужно для self-healing.
3. Отметь, что потребуется для rolling update.
4. Сравни это с возможностями Deployment + Service.

### Типичные ошибки

- считать EKS обычным EC2-сервером;
- думать, что AWS управляет всем Kubernetes workload'ом автоматически;
- забывать, что EC2/EBS/ELB/NAT могут стоить денег;
- не различать control plane и data plane.

### Вопросы

1. Что именно AWS управляет в control plane EKS?
2. Чем EKS отличается от запуска k3s на EC2?
3. Кто отвечает за приложение внутри Pod?
4. Что в EKS остаётся вашей зоной ответственности?

---

# Модуль 1. Kubernetes внутри EKS

## 1.1 Архитектура Kubernetes

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

## 1.2 Основные сущности

| Сущность | Для чего |
|---|---|
| Pod | минимальная единица запуска |
| Deployment | декларативное управление stateless Pod'ами |
| ReplicaSet | поддерживает количество Pod'ов |
| Service | стабильная сеть для набора Pod'ов |
| ConfigMap | конфигурация без секретов |
| Secret | чувствительные значения |
| Namespace | логическая изоляция |
| Job | одноразовая задача |
| CronJob | периодическая задача |
| DaemonSet | Pod на каждом подходящем node |
| StatefulSet | stateful workloads с identity и storage |
| Ingress | L7 HTTP routing |
| NetworkPolicy | L3/L4 ограничения между Pod'ами |

## 1.3 Desired state

Ты не говоришь Kubernetes:

> «запусти Pod сейчас».

Ты говоришь:

```yaml
replicas: 3
```

И контроллер постоянно сравнивает фактическое состояние с желаемым.

## 1.4 Self-healing

Если Deployment требует 3 Pod'а, а один исчез:

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

## 1.5 Лаборатория: увидеть Kubernetes

```bash
kubectl get nodes -o wide
kubectl get ns
kubectl get pods -A
kubectl get deployments -A
kubectl get svc -A
```

Посмотри labels:

```bash
kubectl get nodes --show-labels
```

Посмотри системные компоненты:

```bash
kubectl get pods -n kube-system
```

### Практика

1. Найди CoreDNS.
2. Найди `kube-proxy`, если он присутствует в твоей модели EKS.
3. Найди VPC CNI.
4. Удали один Pod приложения и посмотри, какой controller создаст замену.

### Вопросы

1. Почему Pod не является хорошей единицей долговременного deployment?
2. Что делает Deployment?
3. Зачем нужен Service, если Pod уже имеет IP?
4. Как Kubernetes понимает, что Pod unhealthy?

---

# Модуль 2. AWS CLI, eksctl, kubectl, Helm и Terraform

## 2.1 AWS CLI

Проверка identity:

```bash
aws sts get-caller-identity
```

Получаем account ID:

```bash
aws sts get-caller-identity --query Account --output text
```

Список EKS:

```bash
aws eks list-clusters --region "$AWS_REGION"
```

Описание кластера:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 2.2 eksctl

`eksctl` — CLI для работы с EKS, позволяющий создавать и управлять EKS-кластерами декларативно и через команды. AWS использует его в официальных getting started сценариях. https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

Проверка:

```bash
eksctl version
```

## 2.3 kubectl

Проверка клиента:

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

Helm полезен для сложных Kubernetes-приложений, но не должен скрывать понимание базовых YAML-манифестов.

## 2.5 Terraform

```bash
terraform version
terraform init
terraform fmt
terraform validate
terraform plan
```

Общее разделение:

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

### Практика

Создай файл `versions.sh`:

```bash
#!/usr/bin/env bash
set -euo pipefail

aws --version
eksctl version
kubectl version --client
helm version --short
terraform version
```

Запускай его перед лабораториями.

### Типичные ошибки

- `aws` смотрит не в тот профиль;
- `kubectl` подключён к другому cluster context;
- `eksctl` устарел;
- chart repository не обновлён;
- Terraform state хранится без стратегии locking/backup в production.

### Вопросы

1. Чем отличается `aws eks ...` от `kubectl ...`?
2. Когда использовать `eksctl`, а когда Terraform?
3. Что хранится в kubeconfig?
4. Почему Helm не заменяет понимание Kubernetes API?

---

# Модуль 3. AWS networking: VPC, subnets, AZ и VPC CNI

## 3.1 Почему EKS networking сложнее Docker networking

В AWS Pod может иметь IP-адрес из VPC благодаря Amazon VPC CNI. VPC CNI создаёт/использует ENI и выдаёт Pod'ам VPC addresses или prefixes. https://docs.aws.amazon.com/eks/latest/best-practices/vpc-cni.html

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

## 3.2 Public и private subnets

Типовая production-модель:

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

Не обязательно всё должно быть доступно из интернета.

## 3.3 Availability Zones

Для HA workload лучше планировать несколько AZ:

```text
              Region
     +----------+----------+
     |                     |
    AZ-a                  AZ-b
     |                     |
  nodes/pods            nodes/pods
```

Не надо размещать все replicas в одной AZ.

## 3.4 Cluster endpoint

EKS API server endpoint может быть public, private или комбинированно ограничен CIDR. AWS отдельно документирует private-only endpoint и private access внутри VPC. https://docs.aws.amazon.com/eks/latest/userguide/cluster-endpoint.html

Посмотреть настройки:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION" \
  --query 'cluster.resourcesVpcConfig.{endpointPublicAccess:endpointPublicAccess,endpointPrivateAccess:endpointPrivateAccess,publicAccessCidrs:publicAccessCidrs}'
```

## 3.5 CNI и IP exhaustion

Одна из типичных EKS-проблем:

```text
Pod не стартует
  |
  +--> Scheduler OK
  |
  +--> Node есть
  |
  +--> Но VPC CNI не может выдать IP
```

Проверки:

```bash
kubectl get pods -n kube-system -l k8s-app=aws-node
kubectl describe ds aws-node -n kube-system
kubectl get nodes -o wide
```

## 3.6 NetworkPolicy

По умолчанию межpod-traffic не ограничен обычной Kubernetes NetworkPolicy моделью. В EKS VPC CNI поддерживает native network policy при соответствующей конфигурации. https://aws.github.io/aws-eks-best-practices/security/docs/network/

Пример deny-by-default:

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

### Практика

1. Найди subnet'ы кластера.
2. Определи, какие subnet'ы public/private.
3. Посмотри IP nodes.
4. Сравни IP Pod и IP Node.
5. Сделай NetworkPolicy только для тестового namespace и проверь traffic.

### Вопросы

1. Почему EKS Pod networking связан с VPC?
2. Зачем private subnets для worker nodes?
3. Чем security group отличается от NetworkPolicy?
4. Что произойдёт при нехватке Pod IP?

---

# Модуль 4. Создание EKS: Auto Mode и классический EKS

## 4.1 Два подхода

Сегодня полезно уметь работать с обеими моделями:

| Модель | Что важно понять |
|---|---|
| **EKS Auto Mode** | AWS берёт на себя больше инфраструктурного lifecycle: compute, networking, load balancing, block storage и др. |
| **Standard EKS + Managed Node Groups** | Ты лучше понимаешь nodes, add-ons, scaling и традиционную операционную модель |

AWS описывает Auto Mode как расширение управления инфраструктурой Kubernetes; в документации он указан как рекомендуемый способ управления nodes для новых сценариев. https://docs.aws.amazon.com/eks/latest/userguide/automode.html

## 4.2 Auto Mode через eksctl

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

Создание:

```bash
eksctl create cluster -f auto-mode-cluster.yaml
```

`eksctl` поддерживает `autoModeConfig.enabled: true`; при включении Auto Mode AWS/EKS управляет compute, networking, load balancing и block storage capabilities расширенно. https://docs.aws.amazon.com/eks/latest/eksctl/auto-mode.html

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

Создание:

```bash
eksctl create cluster -f cluster.yaml
```

AWS подтверждает, что Managed Node Groups автоматизируют provisioning и lifecycle EC2 nodes, включая updates и draining. https://docs.aws.amazon.com/eks/latest/userguide/managed-node-groups.html

## 4.4 Что создать руками

После cluster creation проверь:

```bash
kubectl get nodes -o wide
kubectl get pods -A
aws eks describe-cluster --name "$CLUSTER_NAME" --region "$AWS_REGION"
```

Смотри CloudFormation stacks, VPC, subnets, security groups, IAM roles и EC2.

## 4.5 kubeconfig

```bash
aws eks update-kubeconfig \
  --region "$AWS_REGION" \
  --name "$CLUSTER_NAME"
```

Проверка:

```bash
kubectl get nodes
```

## 4.6 Add-ons

Amazon EKS Add-ons позволяют управлять поддерживающим software через EKS API; AWS валидирует curated add-ons и рекомендует managed add-ons вместо self-managed там, где это возможно. https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html

Посмотреть:

```bash
aws eks list-addons \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

Версии:

```bash
aws eks describe-addon-versions \
  --addon-name vpc-cni \
  --kubernetes-version 1.36
```

### Практика

1. Создай учебный Standard cluster.
2. Создай отдельный Auto Mode cluster, если бюджет позволяет.
3. Сравни node resources и add-ons.
4. Сравни, кто управляет compute lifecycle.
5. Удали оба кластера после лаборатории.

### Удаление

```bash
eksctl delete cluster --name "$CLUSTER_NAME" --region "$AWS_REGION"
```

> Перед удалением убедись в `kubectl config current-context` и AWS account.

### Вопросы

1. Чем Auto Mode отличается от Managed Node Groups?
2. Какие части платформы AWS может управлять в Auto Mode?
3. Почему полезно пройти Standard EKS перед production Auto Mode?
4. Какие AWS resources создаются вокруг EKS?

---

# Модуль 5. Workloads: Pod, Deployment, Service, ConfigMap, Secret

## 5.1 Первый Deployment

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

Применяем:

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

Проверка:

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

В Pod:

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

Использование:

```yaml
envFrom:
  - secretRef:
      name: db-secret
```

Не отправляй реальные secret values в Git.

## 5.5 Rollout

```bash
kubectl set image deployment/web web=nginx:1.27-alpine
kubectl rollout status deployment/web
kubectl rollout history deployment/web
kubectl rollout undo deployment/web
```

### Практика

1. Подними Deployment из 3 replicas.
2. Удали один Pod.
3. Обнови image.
4. Сделай rollback.
5. Добавь readiness и liveness.
6. Создай ConfigMap и Secret.

### Типичные ошибки

- нет `resources.requests`;
- неверный selector Service;
- liveness probe убивает ещё не стартовавшее приложение;
- секреты лежат в plain text Git repository;
- image без immutable tag/digest в production.

### Вопросы

1. Чем readiness отличается от liveness?
2. Почему Deployment лучше, чем ручное создание Pod?
3. Что делает selector Service?
4. Почему `latest` плохой production tag?

---

# Модуль 6. IAM и доступ к кластеру: Access Entries и RBAC

## 6.1 Два разных вопроса

Всегда разделяй:

```text
Кто может вызвать AWS API?
        |
       IAM
        |
        +-------------------+
                            |
                   Кто может делать
                   Kubernetes actions?
                            |
                           RBAC
```

В EKS есть интеграция IAM ↔ Kubernetes authentication/authorization.

## 6.2 EKS Access Entries

AWS сейчас рекомендует EKS Access Entries для предоставления IAM principals доступа к Kubernetes API. Старый `aws-auth` ConfigMap объявлен deprecated. https://docs.aws.amazon.com/eks/latest/userguide/access-entries.htmlhttps://docs.aws.amazon.com/eks/latest/userguide/auth-configmap.html

Посмотреть:

```bash
aws eks list-access-entries \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

Создание:

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

AWS access policies являются Kubernetes permissions templates, а не IAM permissions. Scope можно ограничить cluster-wide или namespace. https://docs.aws.amazon.com/eks/latest/userguide/access-policies.html

## 6.3 RBAC

Пример:

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

## 6.4 Минимальные права

Не выдавай:

```text
cluster-admin -> всем разработчикам
```

Используй:

```text
IAM role
   |
   +--> Access Entry
           |
           +--> View in namespace X
```

### Практика

1. Создай namespace `shop`.
2. Создай access entry для тестовой role.
3. Дай View Policy только на `shop`.
4. Проверь, что доступ к другому namespace запрещён.
5. Пройди тот же сценарий через Kubernetes Role/RoleBinding.

### Вопросы

1. Что такое Access Entry?
2. Чем IAM authorization отличается от Kubernetes RBAC?
3. Почему `aws-auth` уже не нужно делать фундаментом нового курса?
4. Что означает least privilege для EKS access?

---

# Модуль 7. IAM для Pod'ов: EKS Pod Identity и IRSA

## 7.1 Проблема

Представь Pod, который должен читать S3:

```text
Pod -> S3
```

Нельзя просто положить в image:

```text
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
```

Нужны временные credentials и least privilege.

## 7.2 EKS Pod Identity

EKS Pod Identity позволяет связать IAM role с Kubernetes ServiceAccount; AWS выдаёт Pod'у временные credentials через EKS Auth и Pod Identity Agent. AWS описывает это как способ дать workload'ам IAM permissions без хранения static credentials в контейнерах. https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html

## 7.3 Установка agent

Для Standard EKS:

```bash
eksctl create addon \
  --cluster "$CLUSTER_NAME" \
  --name eks-pod-identity-agent \
  --region "$AWS_REGION"
```

## 7.4 Association

Пример через AWS CLI:

```bash
aws eks create-pod-identity-association \
  --cluster-name "$CLUSTER_NAME" \
  --namespace shop \
  --service-account s3-reader \
  --role-arn arn:aws:iam::${AWS_ACCOUNT_ID}:role/ShopS3ReadRole \
  --region "$AWS_REGION"
```

AWS CLI документирует этот API как связь ServiceAccount ↔ IAM role; credentials для Pod являются временными и автоматически ротируются. https://docs.aws.amazon.com/cli/latest/reference/eks/create-pod-identity-association.html

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

IRSA = IAM Roles for Service Accounts. Это более старый и всё ещё используемый подход на существующих платформах. Он использует OIDC identity provider и trust policy IAM role.

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

Для legacy-кластеров и совместимости IRSA важно знать. Для новых архитектур стоит отдельно рассматривать EKS Pod Identity.

## 7.7 Least privilege

Плохо:

```text
AmazonS3FullAccess
```

Лучше:

```text
s3:GetObject
s3:ListBucket
```

и только нужный bucket/prefix.

### Практика

1. Создай S3 bucket для лаборатории.
2. Создай минимальную IAM policy на read.
3. Создай ServiceAccount.
4. Создай Pod Identity association.
5. Запусти Pod с AWS CLI.
6. Проверь `aws s3 ls`.
7. Удали association и убедись, что доступ пропал.

### Типичные ошибки

- использовать IAM user keys в Secret;
- дать node role слишком широкие permissions;
- забыть Pod Identity Agent в Standard EKS;
- доверять не тому IAM role;
- считать IAM и Kubernetes RBAC одной системой.

### Вопросы

1. Чем Pod Identity отличается от node IAM role?
2. Зачем ServiceAccount?
3. Почему static AWS credentials в Pod — антипаттерн?
4. В каких legacy-системах тебе встретится IRSA?

---

# Модуль 8. Storage: EBS, EFS, PVC и Stateful workloads

## 8.1 Persistent storage

Pod ephemeral. Поэтому:

```text
Pod restart
   |
   +--> container filesystem может исчезнуть
```

Для state используем PersistentVolume.

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

Проверка:

```bash
kubectl get pvc
kubectl get pv
kubectl get storageclass
```

## 8.3 EBS CSI

Amazon EBS CSI Driver управляет lifecycle EBS volumes для Kubernetes volumes. AWS рекомендует EBS CSI как EKS add-on; EBS не монтируется напрямую в Fargate Pod'ы. Auto Mode имеет отдельный storage integration. https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html

Посмотреть add-on:

```bash
aws eks describe-addon-versions \
  --addon-name aws-ebs-csi-driver \
  --kubernetes-version 1.36
```

Проверка:

```bash
kubectl get pods -n kube-system | grep ebs
```

## 8.4 EFS

EFS нужен, когда storage должен быть shared и доступен нескольким Pod'ам.

```text
Pod A ---+
         |
Pod B ---+--> EFS
         |
Pod C ---+
```

AWS EFS CSI driver позволяет использовать EFS как PersistentVolume; dynamic provisioning требует поддерживаемой версии driver и IAM permissions. https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html

## 8.5 EBS vs EFS

| Сценарий | EBS | EFS |
|---|---:|---:|
| RWO stateful app | ✅ | возможно |
| Shared filesystem | ❌ | ✅ |
| Несколько AZ одновременно | обычно через storage semantics, не shared RWO | ✅ |
| DB volume | ✅ | обычно нет |
| Shared uploads | нет | ✅ |

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

### Практика

1. Создай PVC.
2. Запиши файл в volume.
3. Перезапусти Pod.
4. Проверь persistence.
5. Разберись, какой EBS volume появился в AWS.
6. Сравни с EFS.

### Вопросы

1. Зачем CSI driver?
2. Когда использовать EBS, а когда EFS?
3. Почему БД не стоит автоматически помещать в Kubernetes только потому, что это возможно?
4. Чем StatefulSet отличается от Deployment?

---

# Модуль 9. Networking приложений: Service, ALB, NLB и Ingress

## 9.1 Service types

```text
ClusterIP   -> только cluster
NodePort    -> порт node
LoadBalancer -> external LB
```

## 9.2 AWS Load Balancer Controller

AWS Load Balancer Controller управляет AWS Elastic Load Balancers для Kubernetes. Ingress обычно создаёт ALB, а Service type LoadBalancer — NLB в современной схеме контроллера. https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html

AWS best practices рекомендуют AWS Load Balancer Controller вместо legacy Service Controller; в EKS Auto Mode соответствующие capabilities предоставляются автоматически. https://docs.aws.amazon.com/eks/latest/best-practices/load-balancing.html

## 9.3 NLB через Service

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

## 9.4 ALB через Ingress

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

Контроллер наблюдает за Kubernetes resource и создаёт AWS LB.

## 9.5 ALB vs NLB

| Характеристика | ALB | NLB |
|---|---|---|
| OSI | L7 | L4 |
| HTTP routing | ✅ | нет L7 routing |
| Host/path rules | ✅ | нет |
| TCP | ограниченно через features | ✅ |
| Web/API | ✅ | возможно |
| Static public IP | нет как основной сценарий | есть Elastic IP options в поддерживаемых режимах |

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

Сертификаты обычно лучше управлять через ACM, а secrets для приложений — через соответствующие secret management patterns.

### Практика

1. Подними ClusterIP.
2. Создай LoadBalancer service.
3. Посмотри, какой AWS LB появился.
4. Создай Ingress.
5. Настрой host/path routing.
6. Добавь health checks.

### Типичные ошибки

- неправильные subnet tags;
- не установлен/сломался controller;
- Security Group блокирует traffic;
- Ingress backend смотрит на неправильный Service port;
- DNS указывает не туда;
- приложение слушает `127.0.0.1`, а не Pod interface.

### Вопросы

1. Когда использовать ALB?
2. Когда нужен NLB?
3. Как Ingress становится AWS ALB?
4. Чем Service selector отличается от Ingress rule?

---

# Модуль 10. Scheduling: requests, limits, probes, taints, affinity

## 10.1 Resources

Scheduler ориентируется прежде всего на requests.

```yaml
resources:
  requests:
    cpu: 500m
    memory: 256Mi
  limits:
    cpu: "1"
    memory: 512Mi
```

Объяснение:

```text
requests -> сколько scheduler резервирует/учитывает
limits   -> верхняя граница runtime resource consumption
```

## 10.2 Pending Pod

Если Pod:

```text
Pending
```

Сначала:

```bash
kubectl describe pod <pod-name>
```

Ищи:

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

Для сложного scheduling используй node affinity и pod affinity/anti-affinity.

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

Это помогает не посадить все replicas в одну зону.

## 10.7 Probes

Readiness:

```text
Под жив
   |
   +--> но ещё не готов принимать traffic
```

Liveness:

```text
Под завис
   |
   +--> kubelet должен перезапустить container
```

Startup probe полезна для медленного startup, чтобы liveness не начал убивать приложение слишком рано.

### Практика

1. Создай Pod с завышенным memory request.
2. Получи `Pending`.
3. Найди причину через `describe`.
4. Создай tainted node.
5. Запусти Pod без toleration — получи `Pending`.
6. Добавь toleration.
7. Добавь topology spread.

### Вопросы

1. Как scheduler выбирает node?
2. Почему Pod может быть Pending при свободной CPU?
3. В чём разница taint и toleration?
4. Когда использовать affinity?

---

# Модуль 11. Scaling: HPA, Karpenter, Managed Node Groups и Auto Mode

## 11.1 Два уровня autoscaling

```text
           Workload
              |
             HPA
              |
        больше replicas
              |
       Scheduler asks:
         нужны nodes
              |
       Karpenter / MNG / Auto Mode
              |
         больше capacity
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

Проверка:

```bash
kubectl get hpa
kubectl describe hpa api
```

## 11.3 Ключевой момент

HPA без capacity scaling может привести к:

```text
HPA: replicas 2 -> 10
             |
Scheduler: 8 Pods Pending
             |
No new nodes
```

Поэтому нужен второй уровень.

## 11.4 Managed Node Groups scaling

Node group имеет min/desired/max. Для предсказуемых baseline workload это простой вариант.

## 11.5 Karpenter

Karpenter автоматически provisioning/deprovisioning nodes на основании unschedulable Pods и их constraints. AWS best practices отдельно рекомендуют pin tested AMIs в production и отмечают, что Karpenter хорошо подходит для изменчивой или разнообразной capacity потребности. https://aws.github.io/aws-eks-best-practices/karpenter/

Модель:

```text
Pending Pod
   |
Karpenter анализирует:
   - resources
   - zone
   - instance types
   - taints
   - affinity
   - architecture
   |
создаёт подходящий node
```

## 11.6 NodePool thinking

Ты задаёшь policy:

```text
NodePool:
  capacity-type = on-demand/spot
  architectures = amd64/arm64
  zones = ...
  instance-family = ...
  limits = ...
```

И workload через requests/constraints влияет на выбор capacity.

## 11.7 Auto Mode

Auto Mode расширяет automation compute infrastructure и включает capabilities для node provisioning, load balancing, storage и networking. https://docs.aws.amazon.com/eks/latest/userguide/automode.html

## 11.8 Когда что использовать

| Нагрузка | Подход |
|---|---|
| стабильный baseline | Managed Node Group |
| резкие пики | Karpenter / Auto Mode |
| сложная diversity instance types | Karpenter |
| минимум node management | Auto Mode |
| legacy operational model | MNG |

### Практика

1. Настрой Deployment на 2 replicas.
2. Подключи HPA.
3. Создай нагрузку.
4. Наблюдай рост replicas.
5. Убедись, хватает ли nodes.
6. На отдельном lab cluster попробуй Karpenter.

### Вопросы

1. Почему HPA не равен cluster autoscaler?
2. Что делает Karpenter?
3. Когда MNG проще?
4. Что берёт на себя Auto Mode?

---

# Модуль 12. High Availability и graceful disruptions

## 12.1 HA — не просто 3 replicas

Плохо:

```text
AZ-a
  pod-1
  pod-2
  pod-3
```

Лучше:

```text
AZ-a      AZ-b      AZ-c
pod-1     pod-2     pod-3
```

## 12.2 PDB

PodDisruptionBudget защищает минимальную доступность при добровольных disruptions.

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

Приложение должно:

1. перестать принимать новые requests;
2. дождаться текущих requests;
3. завершиться в пределах termination grace period.

```yaml
terminationGracePeriodSeconds: 30
```

## 12.5 Topology spread

Проверяй:

```bash
kubectl get pods -l app=api -o wide
```

И распределение по zone:

```bash
kubectl get nodes -L topology.kubernetes.io/zone
```

## 12.6 Availability зависит от приложения

Если Deployment HA, а база — один Pod без backup, система всё равно не HA.

```text
Frontend HA
   |
API HA
   |
DB single point of failure  <-- проблема
```

### Практика

1. Сделай 3 replicas.
2. Разнеси по AZ.
3. Добавь PDB.
4. Сделай rolling update.
5. Искусственно drain node в тестовой среде.
6. Проверь, сколько Pod остаётся доступно.

### Вопросы

1. Что защищает PDB?
2. Почему PDB не защищает от любой аварии?
3. Зачем topology spread?
4. Почему graceful shutdown важен за Load Balancer?

---

# Модуль 13. Security: Pod Security, NetworkPolicy, SG, KMS

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

Ни один слой не заменяет другой.

## 13.2 Pod Security

Не запускай всё как:

```yaml
securityContext:
  privileged: true
```

Базовый production mindset:

```yaml
securityContext:
  runAsNonRoot: true
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop: ["ALL"]
```

Не все приложения сразу совместимы с этими настройками — тестируй.

## 13.3 NetworkPolicy

Пример: разрешить backend только к frontend:

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

AWS best practices рекомендуют layered security: Kubernetes NetworkPolicy для cluster traffic и Security Groups для AWS/VPC-level traffic. https://aws.github.io/aws-eks-best-practices/security/docs/network/

## 13.4 Security Groups for Pods

EKS поддерживает security groups для отдельных Pod workloads через VPC CNI. Есть enforcing modes `strict` и `standard`; выбор режима влияет на networking semantics. https://docs.aws.amazon.com/eks/latest/best-practices/sgpp.html

## 13.5 Secrets encryption

Для EKS Kubernetes 1.28+ AWS предоставляет default envelope encryption для Kubernetes API data. При необходимости можно использовать customer-managed KMS key как дополнительный контроль. https://docs.aws.amazon.com/eks/latest/userguide/envelope-encryption.html

Проверять encryption:

```bash
aws eks describe-cluster \
  --name "$CLUSTER_NAME" \
  --region "$AWS_REGION" \
  --query 'cluster.encryptionConfig'
```

## 13.6 Secrets != password manager

Kubernetes Secret не означает автоматически:

```text
«секрет безопасно лежит в Git»
```

В GitOps production обычно нужны внешние secret management patterns: AWS Secrets Manager/Parameter Store + operator/controller или другой approved approach.

### Практика

1. Сделай non-root container.
2. Запусти read-only root filesystem.
3. Добавь deny-by-default NetworkPolicy.
4. Ограничь egress.
5. Проверь IAM permissions Pod'а.
6. Проверь KMS/encryption configuration.

### Вопросы

1. Почему IAM policy недостаточно?
2. Что ограничивает NetworkPolicy?
3. Когда SG for Pods полезен?
4. Что делает envelope encryption?

---

# Модуль 14. Observability: logs, metrics, events, traces

## 14.1 Три главных сигнала

```text
Logs    -> что произошло
Metrics -> сколько / насколько часто
Traces  -> где потерялось время
```

## 14.2 Kubernetes events

Самый дешёвый инструмент диагностики:

```bash
kubectl get events -A --sort-by=.lastTimestamp
```

Для Pod:

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

AWS предоставляет `amazon-cloudwatch-observability` add-on для CloudWatch Agent, Container Insights и Application Signals; для add-on поддерживается IAM через Pod Identity в современных сценариях. https://docs.aws.amazon.com/eks/latest/userguide/workloads-add-ons-available-eks.htmlhttps://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Observability-EKS-addon.html

Проверка:

```bash
aws eks list-addons \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 14.5 Prometheus

Ключевые Kubernetes metrics:

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

Плохо:

```text
CPU < 80%
```

Гораздо полезнее:

```text
availability = 99.9%
P95 latency < 300ms
5xx rate < 0.1%
```

## 14.7 Метрики EKS

Минимум для production:

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

### Практика

1. Сломай image tag и наблюдай `ImagePullBackOff`.
2. Найди причину через events.
3. Включи логирование приложений.
4. Собери CPU/memory metrics.
5. Сформулируй два SLO для итогового проекта.

### Вопросы

1. Чем logs отличаются от metrics?
2. Что первым смотреть при `Pending`?
3. Какие SLI реально отражают пользовательское качество?
4. Что такое error budget?

---

# Модуль 15. Helm, Kustomize и GitOps

## 15.1 Helm

Создание chart:

```bash
helm create shop-api
```

Основные элементы:

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

Плюсы: простой patching без templating engine.

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

Argo CD install пример:

```bash
kubectl create namespace argocd
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm upgrade --install argocd argo/argo-cd -n argocd
```

Для production используй pinning chart version и управляемую конфигурацию.

## 15.5 Что хранить в Git

Хорошо:

```text
Deployment manifests
Helm values
NetworkPolicies
RBAC
HPA
PDB
Ingress
```

Плохо:

```text
AWS secret keys
DB passwords
production tokens
```

### Практика

1. Упакуй сервис в Helm chart.
2. Создай dev/prod values.
3. Перенеси deployment в Git.
4. Подключи Argo CD.
5. Измени image tag в Git и наблюдай sync.

### Вопросы

1. Чем Helm отличается от Kustomize?
2. Почему GitOps уменьшает drift?
3. Что должен быть source of truth?
4. Как хранить secrets в GitOps?

---

# Модуль 16. CI/CD: GitHub Actions, ECR и deploy в EKS

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

Не используй long-lived AWS access keys, если можно применить OIDC federation / role assumption.

```text
GitHub Actions
     |
OIDC token
     |
AWS IAM Role
     |
ECR / EKS permissions
```

## 16.4 CD стратегии

| Подход | Плюс | Минус |
|---|---|---|
| `kubectl apply` из CI | просто | CI должен иметь cluster access |
| Helm from CI | удобно | всё ещё push-based |
| GitOps | audit + reconciliation | нужен GitOps controller |
| Progressive delivery | безопаснее rollout | сложнее |

### Практика

1. Собери Docker image.
2. Push в ECR.
3. Разверни через Helm.
4. Переведи deployment в GitOps.
5. Добавь rollback.
6. Запрети CI использовать admin credentials.

### Вопросы

1. Почему ECR лучше Docker Hub для AWS workloads в некоторых архитектурах?
2. Как GitHub Actions получает AWS credentials без static keys?
3. Чем push CD отличается от pull GitOps?
4. Где должна жить политика deploy permissions?

---

# Модуль 17. Lifecycle: add-ons, upgrades и node maintenance

## 17.1 Версии Kubernetes

На момент подготовки курса в EKS standard support доступны `1.36`, `1.35`, `1.34`; `1.33` и старше находятся в extended support по текущей таблице AWS. EKS позволяет более длительно оставаться на отдельных версиях за дополнительную стоимость, но рекомендуется планировать регулярные upgrades. https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html

## 17.2 Upgrade control plane

AWS рекомендует сначала тестировать приложение на новой версии; in-place upgrade после завершения может быть откатан к предыдущей minor version в течение 7 дней при выполнении соответствующих условий. https://docs.aws.amazon.com/eks/latest/userguide/update-cluster.html

Для `eksctl`:

```bash
eksctl upgrade cluster \
  --name "$CLUSTER_NAME" \
  --version 1.36 \
  --approve
```

Upgrades делай по одной minor version.

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

Версия VPC CNI:

```bash
aws eks describe-addon \
  --cluster-name "$CLUSTER_NAME" \
  --addon-name vpc-cni \
  --region "$AWS_REGION"
```

AWS Add-ons уменьшают операционную нагрузку и проходят validation/security patches. https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html

## 17.5 Node upgrades

Для Managed Node Groups AWS автоматизирует lifecycle и drain nodes в рамках обновлений. https://docs.aws.amazon.com/eks/latest/userguide/managed-node-groups.html

## 17.6 Upgrade checklist

Перед upgrade:

```bash
kubectl get nodes
kubectl get pods -A
kubectl get pdb -A
kubectl get crd
kubectl get ingress -A
kubectl get events -A --sort-by=.lastTimestamp
```

Сохрани:

- текущее version состояние;
- add-ons versions;
- deprecated APIs;
- backup critical data;
- rollback plan.

### Практика

1. Проверь текущую Kubernetes version.
2. Проверь add-ons.
3. Составь upgrade checklist.
4. Сделай upgrade на lab cluster.
5. Сравни `kubectl get nodes` до и после.

### Вопросы

1. Почему нельзя обновлять control plane и забывать про add-ons?
2. Зачем читать release notes?
3. Почему minor upgrades делают по одной версии?
4. Что проверять после upgrade?

---

# Модуль 18. Troubleshooting и production diagnostics

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

Проверяй:

- command/args;
- env;
- Secret;
- ConfigMap;
- liveness probe;
- OOMKilled;
- application startup.

## 18.3 ImagePullBackOff

Проверки:

```bash
kubectl describe pod <pod>
```

Причины:

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

Типичные причины:

- недостаток CPU/memory;
- taint;
- affinity;
- topology constraints;
- volume constraints;
- нет matching node;
- Karpenter/Auto Mode не может provision подходящий capacity.

## 18.5 Service не работает

```bash
kubectl get svc
kubectl get endpointslice -l kubernetes.io/service-name=api
kubectl get pods -l app=api
```

Проверь selector:

```bash
kubectl get svc api -o yaml
kubectl get pods --show-labels
```

## 18.6 DNS

```bash
kubectl get pods -n kube-system | grep coredns
kubectl logs -n kube-system -l k8s-app=kube-dns
```

Тест:

```bash
kubectl run dns-test --rm -it --restart=Never \
  --image=busybox:1.36 \
  -- nslookup kubernetes.default
```

## 18.7 IAM

Для Pod:

```bash
kubectl get sa -n shop
```

Для Pod Identity:

```bash
aws eks list-pod-identity-associations \
  --cluster-name "$CLUSTER_NAME" \
  --region "$AWS_REGION"
```

## 18.8 AWS Load Balancer

Сначала Kubernetes:

```bash
kubectl describe ingress <ingress>
kubectl describe svc <service>
```

Потом AWS:

- Load Balancer;
- Target Groups;
- Target health;
- Security Groups;
- subnet placement;
- controller logs.

### Практика: «сломай и почини»

Сделай 10 аварий:

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

Для каждой запиши:

```text
Symptom
Layer
Command
Evidence
Root cause
Fix
Prevention
```

### Вопросы

1. Почему `kubectl get pods` недостаточно для диагностики?
2. Что читать первым: logs или events?
3. Как отличить Kubernetes проблему от AWS проблемы?
4. Что должно быть в incident timeline?

---

# Модуль 19. Production architecture и итоговый проект

## 19.1 Финальный проект

Построй production-like платформу интернет-магазина:

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

## 19.2 Компоненты

### Namespace'ы

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
worker HPA по подходящей custom metric/queue depth
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
- S3 для object storage;
- EBS для stateful component, если он действительно нужен;
- EFS только там, где нужен shared filesystem.

### Delivery

```text
PR -> test -> build -> scan -> ECR -> GitOps -> EKS
```

## 19.3 Production checklist

### Infrastructure

- [ ] Terraform state защищён и имеет locking strategy
- [ ] VPC multi-AZ
- [ ] private subnets для worker capacity, где это соответствует архитектуре
- [ ] cluster endpoint access ограничен согласно модели доступа
- [ ] IAM roles вместо long-lived keys

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
- [ ] Load Balancer Controller или Auto Mode capabilities
- [ ] EBS/EFS CSI как требуется
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

## 19.4 Минимальные SLO

Для лаборатории выбери:

```text
Availability: 99.9%
API P95 latency: < 300ms
5xx rate: < 0.1%
Recovery objective: documented
```

Это не «правильные» универсальные значения — цель практики научиться выбирать SLO осознанно под workload.

## 19.5 Финальный экзамен

Ты готов, когда можешь без подсказки ответить:

```text
1. Что AWS управляет в EKS?
2. Как Pod получает AWS credentials?
3. Как Service находит Pod?
4. Как Ingress превращается в ALB?
5. Почему Pod Pending?
6. Чем HPA отличается от node autoscaling?
7. Что делает Karpenter?
8. Как ограничить Pod-to-Pod traffic?
9. Как сохранить данные после Pod restart?
10. Как обновить EKS без незапланированного downtime?
11. Как диагностировать CrashLoopBackOff?
12. Почему приложение может быть healthy, а пользователю всё равно плохо?
```

---

# Шпаргалка AWS CLI + EKS

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

# Шпаргалка kubectl

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

# Шпаргалка Helm

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

# Шпаргалка диагностики

| Симптом | Первые команды |
|---|---|
| `Pending` | `kubectl describe pod`, `kubectl get nodes` |
| `CrashLoopBackOff` | `kubectl logs`, `kubectl logs --previous`, `kubectl describe pod` |
| `ImagePullBackOff` | `kubectl describe pod`, ECR/IAM checks |
| Service не отвечает | `kubectl get svc`, `get endpointslice`, labels |
| Ingress не работает | `kubectl describe ingress`, controller logs, AWS LB |
| DNS не работает | CoreDNS pods/logs + `nslookup` |
| Pod не получает AWS access | ServiceAccount + Pod Identity + IAM role |
| Нет Pod IP | VPC CNI + subnet/IP capacity |
| Node NotReady | `kubectl describe node`, kubelet/system events |
| LB unhealthy | target health + app readiness + SG |
| HPA не масштабирует | metrics availability + requests + HPA status |

---

# Вопросы на собеседовании по EKS

## Junior

### 1. Что такое EKS?
Managed Kubernetes service AWS.

### 2. Что такое Pod?
Минимальная единица deployment в Kubernetes.

### 3. Зачем Service?
Даёт стабильный network endpoint поверх меняющихся Pod IP.

### 4. Что такое Deployment?
Controller для декларативного управления stateless Pod replicas и rollout.

### 5. Что делает `kubectl`?
Работает с Kubernetes API.

---

## Middle

### 6. В чём разница IAM и RBAC?
IAM отвечает за AWS identity/authorization, RBAC — за Kubernetes API permissions.

### 7. Что такое EKS Pod Identity?
Механизм выдачи IAM permissions workload'ам через связь ServiceAccount и IAM role.

### 8. Зачем VPC CNI?
Чтобы Pod networking интегрировался с AWS VPC.

### 9. Почему Pod Pending?
Недостаток ресурсов, constraints, taints, affinity, storage или отсутствие подходящего node capacity.

### 10. Чем HPA отличается от Karpenter?
HPA меняет количество Pod replicas, Karpenter может изменять node capacity.

### 11. ALB vs NLB?
ALB — L7 HTTP-aware load balancing; NLB — L4 network load balancing.

### 12. EBS vs EFS?
EBS — block storage, EFS — shared elastic file storage.

---

## Senior

### 13. Как спроектировать EKS multi-AZ?
Разместить capacity и replicas по AZ, использовать topology spread/PDB, проверить dependency topology и managed services.

### 14. Как закрыть Kubernetes API?
Использовать private endpoint или ограничить public CIDRs в соответствии с архитектурой доступа.

### 15. Как дать Pod доступ только к одному S3 prefix?
Отдельная IAM role через Pod Identity с минимальной policy и конкретным ARN/prefix.

### 16. Как расследовать high latency?
Разделить request path на ingress/LB, app, downstreams, DB, network и metrics/traces; проверить P95/P99, saturation и errors.

### 17. Что делает Karpenter?
Provisioning/disprovisioning nodes под unschedulable Pod requirements.

### 18. Как подготовить upgrade EKS?
Изучить release notes, проверить deprecated APIs/add-ons/CRDs, протестировать, обновить control plane, add-ons и nodes с наблюдаемостью и rollback plan.

### 19. Почему `requests` критичны?
Они влияют на scheduling и QoS, а также на корректную работу HPA/autoscaling и capacity planning.

### 20. Чем Auto Mode меняет операционную модель?
AWS берёт на себя больше cluster infrastructure lifecycle, уменьшая объём ручного управления compute/networking/storage/load balancing.

---

# FAQ

## Нужно ли сначала идеально знать Kubernetes?
Нет. Но базовые Pod, Deployment, Service, DNS, storage, scheduling и RBAC должны быть понятны.

## Можно ли учить EKS только через AWS Console?
Можно начать так, но для DevOps/Platform работы обязательно нужны CLI, YAML, `kubectl` и Infrastructure as Code.

## Нужен ли Terraform?
Для production platform — очень часто да. Для знакомства можно начать с `eksctl`.

## Обязательно ли использовать Karpenter?
Нет. Это один из вариантов autoscaling capacity.

## Нужно ли запускать БД внутри EKS?
Не обязательно. Сравни операционные последствия с managed database service.

## Надо ли использовать EKS Auto Mode?
Изучи Auto Mode и Standard EKS, затем выбирай модель по требованиям к управляемости, совместимости, контролю и operational model.

## Что важнее: Security или Cost?
Они обе важны, но trade-off определяется риском и business requirements. Цель production-платформы — не «минимальная стоимость», а предсказуемая стоимость при нужном уровне надёжности и безопасности.

---

# Глоссарий EKS

| Термин | Значение |
|---|---|
| EKS | Amazon Elastic Kubernetes Service |
| Control Plane | Kubernetes management components |
| Node | вычислительный узел |
| Pod | минимальная workload единица |
| Deployment | controller для stateless workloads |
| Service | стабильный network endpoint |
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
| GitOps | управление desired state через Git |
| SLO | Service Level Objective |
| SLI | Service Level Indicator |

---

# Официальные источники

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

# Финальное резюме курса

После этого курса ты должен смотреть на EKS не как на «кластер Kubernetes в AWS», а как на **платформу**, состоящую из нескольких слоёв:

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

Главный production-навык — не знать сто команд `kubectl`, а понимать **какой слой отвечает за проблему, где искать evidence и какое изменение минимально и безопасно исправляет ситуацию**.

---

## Лицензия

MIT — используй, изменяй, форкай и делись курсом.