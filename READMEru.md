# AWS EKS курс 2026: бесплатный курс по Amazon EKS и Kubernetes в AWS с нуля до профи на русском

![EKS 1.36](https://img.shields.io/badge/Amazon%20EKS-1.36-FF9900?logo=amazonwebservices&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-managed-326CE5?logo=kubernetes&logoColor=white)
![Karpenter](https://img.shields.io/badge/Karpenter-autoscaling-blueviolet)
![Курс на русском](https://img.shields.io/badge/язык-русский-red)
![Бесплатный курс](https://img.shields.io/badge/цена-бесплатно-brightgreen)
![От junior до senior](https://img.shields.io/badge/уровень-junior%20→%20senior-orange)

> **Полный бесплатный курс по Amazon EKS на русском языке.** Теория, практика, eksctl и Terraform, control plane и data plane, IAM и RBAC, access entries и Pod Identity, managed node groups, Fargate, EKS Auto Mode и Karpenter, VPC CNI и IP-адресация, ALB/NLB и Gateway API, EBS/EFS/S3 CSI, секреты, аддоны, наблюдаемость, безопасность, GitOps, обновление версий, стоимость и оптимизация, мультирегион и production-архитектура. Всё в одном README, актуально для **Amazon EKS 1.36 (сентябрь 2026)**.

**EKS обучение без воды:** каждый модуль состоит из понятной теории, схем, команд, которые можно запустить у себя, типичных ошибок и вопросов для самопроверки. Курс подходит, чтобы выучить EKS с нуля, подготовиться к собеседованию на DevOps, SRE, platform или cloud-инженера и спроектировать надёжный кластер в продакшене, не разорившись на счёте AWS.

⚠️ **Внимание: EKS стоит денег.** Кластер тарифицируется с первой минуты, даже без нагрузки: **$0.10 в час за control plane** (≈$73/месяц) плюс EC2, EBS, балансировщики, NAT Gateway и трафик между AZ. Все практики в курсе построены так, чтобы их можно было пройти за несколько долларов, но **удаляй кластеры после занятий**. Команда для удаления есть в конце каждого модуля с практикой.

⭐ Если курс полезен, поставь звезду репозиторию: так его найдут другие инженеры.

---

## Для кого этот курс по EKS

| Кто ты | Что получишь |
|---|---|
| **Новичок** в Kubernetes и AWS | Понимание, что EKS делает за тебя, а что нет, и как поднять рабочий кластер за 20 минут |
| **DevOps / SRE** | Node groups, Karpenter, Auto Mode, обновления версий без простоя, мониторинг, алерты, troubleshooting |
| **Backend-разработчик** | Как правильно задеплоить сервис: probes, requests/limits, HPA, Ingress, секреты, доступ к S3 и RDS без ключей |
| **Platform engineer** | Multi-tenancy, GitOps, EKS Blueprints, Terraform-модули, платформенные аддоны, golden path для команд |
| **Cloud / infrastructure engineer** | VPC-дизайн под EKS, IP-адресация, private cluster, PrivateLink, гибридные узлы |
| **Security-инженер** | IRSA vs Pod Identity, access entries, Pod Security Standards, network policy, IMDS, KMS, GuardDuty EKS Protection, аудит |
| **FinOps / тимлид** | Все строки счёта EKS, Spot, Graviton, right-sizing, extended support как ловушка на $4 380 в год |
| **Архитектор** | Когда EKS, когда ECS, когда Fargate, когда вообще не Kubernetes; мультирегион и DR |
| **Готовишься к собеседованию** | 40 вопросов по EKS с ответами уровня junior, middle и senior |

## Что ты будешь уметь после курса

- объяснить архитектуру EKS: control plane, data plane, VPC CNI, ENI, аддоны, модель разделённой ответственности;
- создавать кластеры тремя способами: `eksctl`, Terraform и AWS Console, и понимать, что происходит под капотом;
- разбираться в аутентификации: IAM-роли, **access entries**, устаревший `aws-auth` ConfigMap, `kubeconfig`, RBAC;
- выбирать compute осознанно: managed node groups, self-managed, Fargate, **EKS Auto Mode**, **Karpenter**;
- писать `NodePool` и `NodeClass` для Karpenter, использовать Spot и Graviton, настраивать consolidation и disruption budgets;
- масштабировать приложения: HPA, metrics-server, KEDA, VPA, PDB, topology spread constraints;
- проектировать сеть: подсети, IP-адресация, prefix delegation, лимиты pod на узел, custom networking, IPv6, security groups for pods;
- публиковать сервисы через **AWS Load Balancer Controller** (ALB/NLB), Gateway API, ExternalDNS и ACM;
- подключать хранилище: EBS CSI, EFS CSI, Mountpoint for S3, StorageClass, snapshot, StatefulSet в нескольких AZ;
- давать приложениям доступ к AWS без ключей: **EKS Pod Identity** и IRSA, session policies;
- управлять аддонами EKS и обновлять их без простоя;
- настраивать наблюдаемость: CloudWatch Container Insights, control plane logs, ADOT/OpenTelemetry, Prometheus и Grafana;
- закрывать кластер: Pod Security Standards, network policies, приватный endpoint, блокировка IMDS, сканирование образов, GuardDuty;
- строить CI/CD и GitOps: ECR, Helm, Argo CD, Flux, EKS Capabilities;
- обновлять кластер с 1.34 до 1.36 без простоя, читая **cluster insights**;
- считать стоимость кластера построчно и урезать её в два-три раза;
- проектировать multi-AZ и мультирегиональную архитектуру, DR и план отказа зоны;
- диагностировать типовые аварии: `Pending` pod, `ImagePullBackOff`, `CrashLoopBackOff`, `NotReady` node, исчерпание IP, `OOMKilled`.

---

## Содержание

- [Для кого этот курс по EKS](#для-кого-этот-курс-по-eks)
- [Что ты будешь уметь после курса](#что-ты-будешь-уметь-после-курса)
- [Как проходить курс](#как-проходить-курс)
- [Модуль 0. Что такое EKS и зачем он нужен](#модуль-0-что-такое-eks-и-зачем-он-нужен)
- [Модуль 1. Архитектура EKS: control plane, data plane, VPC](#модуль-1-архитектура-eks-control-plane-data-plane-vpc)
- [Модуль 2. Первый кластер: eksctl, Terraform, Console](#модуль-2-первый-кластер-eksctl-terraform-console)
- [Модуль 3. Доступ к кластеру: IAM, access entries, RBAC](#модуль-3-доступ-к-кластеру-iam-access-entries-rbac)
- [Модуль 4. Compute: node groups, Fargate, Auto Mode](#модуль-4-compute-node-groups-fargate-auto-mode)
- [Модуль 5. Karpenter: автомасштабирование узлов по-взрослому](#модуль-5-karpenter-автомасштабирование-узлов-по-взрослому)
- [Модуль 6. Масштабирование приложений: HPA, KEDA, VPA, PDB](#модуль-6-масштабирование-приложений-hpa-keda-vpa-pdb)
- [Модуль 7. Сеть EKS: VPC CNI, IP-адресация, лимиты](#модуль-7-сеть-eks-vpc-cni-ip-адресация-лимиты)
- [Модуль 8. Публикация сервисов: ALB, NLB, Gateway API, DNS](#модуль-8-публикация-сервисов-alb-nlb-gateway-api-dns)
- [Модуль 9. Хранилище: EBS, EFS, S3 и CSI-драйверы](#модуль-9-хранилище-ebs-efs-s3-и-csi-драйверы)
- [Модуль 10. Доступ к AWS из pod: Pod Identity, IRSA, секреты](#модуль-10-доступ-к-aws-из-pod-pod-identity-irsa-секреты)
- [Модуль 11. Аддоны EKS и их жизненный цикл](#модуль-11-аддоны-eks-и-их-жизненный-цикл)
- [Модуль 12. Наблюдаемость: логи, метрики, трейсы, алерты](#модуль-12-наблюдаемость-логи-метрики-трейсы-алерты)
- [Модуль 13. Безопасность EKS: от PSS до GuardDuty](#модуль-13-безопасность-eks-от-pss-до-guardduty)
- [Модуль 14. CI/CD и GitOps: ECR, Helm, Argo CD](#модуль-14-cicd-и-gitops-ecr-helm-argo-cd)
- [Модуль 15. Обновление версий: lifecycle, insights, стратегия](#модуль-15-обновление-версий-lifecycle-insights-стратегия)
- [Модуль 16. Стоимость EKS и оптимизация](#модуль-16-стоимость-eks-и-оптимизация)
- [Модуль 17. Надёжность, мультирегион и DR](#модуль-17-надёжность-мультирегион-и-dr)
- [Модуль 18. EKS в продакшене: архитектура и эксплуатация](#модуль-18-eks-в-продакшене-архитектура-и-эксплуатация)
- [Модуль 19. Итоговый проект: production-grade кластер](#модуль-19-итоговый-проект-production-grade-кластер)
- [Шпаргалка команд EKS](#шпаргалка-команд-eks)
- [Шпаргалка важных настроек](#шпаргалка-важных-настроек)
- [Шпаргалка: типовые ошибки и что делать](#шпаргалка-типовые-ошибки-и-что-делать)
- [Вопросы на собеседовании по EKS с ответами](#вопросы-на-собеседовании-по-eks-с-ответами)
- [FAQ: частые вопросы про EKS](#faq-частые-вопросы-про-eks)
- [Глоссарий EKS](#глоссарий-eks)
- [Официальные источники и что читать дальше](#официальные-источники-и-что-читать-дальше)

---

## Как проходить курс

1. **Иди по порядку.** Модули 0-8 это фундамент: без понимания control plane, IAM-доступа, узлов, сети и балансировщиков всё остальное будет магией и «работает, но не знаю почему».
2. **Запускай каждую команду.** EKS учится руками. Прочитать про исчерпание IP-адресов в подсети и увидеть `failed to assign an IP address to container` в `kubectl describe pod` — разные уровни понимания.
3. **Ломай кластер.** Убивай узлы через EC2 Console, выкручивай `requests`, заполняй подсеть, ломай IAM-права. Именно так появляется production-опыт.
4. **Следи за счётом.** Включи AWS Budgets с алертом на $20. Это часть профессии.
5. **Отвечай на вопросы в конце модуля** вслух, как на собеседовании.
6. **Сделай итоговый проект.** Он собирает все темы в одну систему.

**Что нужно установить:**

```bash
# AWS CLI v2
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip && unzip -q awscliv2.zip && sudo ./aws/install

# kubectl (версия ±1 минор от версии кластера)
curl -LO "https://dl.k8s.io/release/v1.36.0/bin/linux/amd64/kubectl" && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

# eksctl
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz" | tar xz && sudo mv eksctl /usr/local/bin/

# helm
curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# по желанию, но сильно облегчает жизнь
brew install kubectx k9s stern   # переключение контекстов, TUI, логи из нескольких pod
```

Проверь, что AWS CLI видит твой аккаунт:

```bash
aws sts get-caller-identity
aws configure get region
```

**Версии:** курс написан для Amazon EKS **1.36** (доступна с июня 2026). На сентябрь 2026 в стандартной поддержке находятся **1.34, 1.35, 1.36**; версия 1.33 ушла в extended support и стоит $0.60 в час. Все примеры проверяемы на 1.34+.

**Права:** для прохождения курса нужен IAM-пользователь или роль с правами на EKS, EC2, VPC, IAM, CloudFormation. В учебном аккаунте проще всего дать `AdministratorAccess`, в рабочем — никогда так не делай.

---

# Модуль 0. Что такое EKS и зачем он нужен

## 0.1 Определение EKS простыми словами

**Amazon EKS (Elastic Kubernetes Service)** это управляемый Kubernetes в AWS. AWS берёт на себя **control plane** — то есть `kube-apiserver`, `etcd`, `kube-scheduler`, `kube-controller-manager` — разворачивает его в трёх зонах доступности, патчит, бэкапит и держит под SLA 99.95% (или 99.99% на Provisioned Control Plane). Ты получаешь один HTTPS-эндпоинт и работаешь с ним обычным `kubectl`.

Три вещи, которые нужно понять сразу:

1. **EKS это настоящий Kubernetes**, прошедший CNCF-сертификацию. Твои Helm-чарты, операторы, CRD и манифесты работают без изменений.
2. **AWS управляет только control plane.** Узлы (worker nodes), сеть, хранилище, аддоны, приложения и безопасность — твоя ответственность, если ты не включил Auto Mode.
3. **EKS глубоко интегрирован с AWS.** Аутентификация через IAM, сеть через VPC (каждый pod получает настоящий VPC-IP), балансировщики через ALB/NLB, диски через EBS, доступ к сервисам через роли, а не через ключи.

Кластер EKS всегда живёт **в твоём VPC** и **в твоём аккаунте**: AWS создаёт ENI (сетевые интерфейсы) в твоих подсетях, чтобы control plane мог дотянуться до kubelet.

## 0.2 Модель разделённой ответственности

Это самая важная таблица модуля. Половина провалов на собеседовании — непонимание, где заканчивается AWS и начинаешься ты.

| Слой | Кто отвечает (обычный EKS) | Кто отвечает (EKS Auto Mode) |
|---|---|---|
| `etcd`, бэкапы etcd, шифрование | AWS | AWS |
| `kube-apiserver`, scheduler, controller-manager | AWS | AWS |
| Обновление control plane на новый минор | **Ты запускаешь, AWS выполняет** | Ты запускаешь, AWS выполняет |
| AMI узлов, патчи ОС, ядро | **Ты** (managed node group упрощает) | AWS |
| Провижининг и масштабирование узлов | **Ты** (Cluster Autoscaler / Karpenter) | AWS |
| Базовые аддоны (CNI, CoreDNS, kube-proxy) | **Ты** (через EKS add-ons) | AWS |
| CSI-драйверы, Load Balancer Controller | **Ты** | AWS |
| Дизайн VPC и подсетей, IP-адресация | **Ты** | **Ты** |
| RBAC, network policy, Pod Security | **Ты** | **Ты** |
| Приложения, образы, ресурсы, probes | **Ты** | **Ты** |
| Стоимость и её оптимизация | **Ты** | **Ты** (плюс наценка Auto Mode) |

**Вывод:** «managed Kubernetes» не значит «Kubernetes, о котором не надо думать». EKS снимает 20% работы (самую неприятную — etcd) и оставляет 80%.

## 0.3 Проблема, которую решает EKS

Ты можешь развернуть Kubernetes на EC2 самостоятельно (kubeadm, kOps, Talos). Тогда на тебе:

```
                 +--> etcd: 3 узла, бэкапы, compaction, defrag, восстановление
                 |
Свой Kubernetes -+--> apiserver: сертификаты, ротация CA, HA, апгрейды
                 |
                 +--> scheduler и controller-manager: leader election, мониторинг
                 |
                 +--> дежурство 24/7 за всё это
```

Практика показывает: самостоятельный control plane — это примерно один инженер на полную занятость, плюс аварии, о которых потом пишут постмортемы. `etcd`, который развалился в 3 часа ночи, объясняет ценность EKS убедительнее любого маркетинга.

С EKS картинка такая:

```
aws eks create-cluster  →  control plane в 3 AZ, готов через ~10 минут
                           SLA 99.95%, патчи и бэкапы на AWS
                           $0.10/час

Твоя зона ответственности начинается с узлов:
  узлы → аддоны → приложения → наблюдаемость → безопасность → счёт
```

## 0.4 EKS vs ECS vs Fargate vs самостоятельный Kubernetes

| Критерий | Amazon EKS | Amazon ECS | Self-managed k8s на EC2 | AWS App Runner / Lambda |
|---|---|---|---|---|
| API | Настоящий Kubernetes | Проприетарный AWS | Настоящий Kubernetes | Нет, PaaS/FaaS |
| Порог входа | Высокий | Средний | Очень высокий | Низкий |
| Плата за control plane | $0.10/час на кластер | Нет | Стоимость EC2 под мастера | Нет |
| Экосистема (Helm, операторы, CRD) | Полная | Нет | Полная | Нет |
| Переносимость в другой облако | Высокая | Нулевая | Высокая | Нулевая |
| Кто обновляет control plane | AWS (по твоей команде) | AWS, прозрачно | Ты | AWS |
| Когда выбирать | Нужен Kubernetes: экосистема, мультиоблако, сложные workload, команда платформы | Только AWS, простые сервисы, нет k8s-компетенции | Особые требования (кастомный scheduler, edge, regulated on-prem) | Один сервис, HTTP, не хочется инфраструктуры |

**Честно про ECS:** если у тебя 10 stateless-сервисов, только AWS и нет человека, который знает Kubernetes, ECS дешевле в эксплуатации и даст меньше инцидентов. EKS выигрывает, когда нужна экосистема (операторы, Argo, Istio, Kubeflow), команда уже знает Kubernetes или нужна переносимость.

**Fargate это не альтернатива EKS, а вариант compute внутри EKS.** Ты можешь запускать pod EKS на Fargate (без узлов вообще), на EC2 или смешивать.

## 0.5 Три режима compute в EKS

```
                         EKS Cluster (control plane от AWS)
                                       |
        +------------------------------+------------------------------+
        |                              |                              |
  Managed node groups            AWS Fargate                   EKS Auto Mode
  EC2 в твоём аккаунте        pod без узлов, per-pod         AWS управляет узлами
  ты патчишь и масштабируешь   дорого на длинных задачах       наценка ~12% к EC2
  максимум контроля            максимум простоты               баланс и меньше тоила
```

Выбирать будем в модуле 4, когда появится язык для разговора.

## 0.6 Сколько стоит EKS (коротко, подробно в модуле 16)

| Строка счёта | Цена (us-east-1, 2026) |
|---|---|
| Control plane, стандартная поддержка | **$0.10/час** ≈ $73/мес на кластер |
| Control plane, extended support | **$0.60/час** ≈ $438/мес — цена за то, что не обновился |
| Provisioned Control Plane (XL...8XL) | **Сверху** к базовой цене, за предсказуемую производительность API |
| Узлы EC2 | Обычная цена EC2, Spot до −90% |
| EKS Auto Mode | EC2 + **наценка ≈12%** за управляемые инстансы |
| Fargate | ≈$0.04048 за vCPU-час и ≈$0.004445 за ГБ-час, посекундно, минимум 1 минута |
| EKS Hybrid Nodes | Плата за vCPU узлов вне AWS |
| NAT Gateway | $0.045/час + $0.045/ГБ — часто **дороже control plane** |
| ALB/NLB | ≈$0.0225/час + LCU |
| Трафик между AZ | $0.01/ГБ в каждую сторону |
| EBS gp3 | ≈$0.08/ГБ-мес |

**Главная ловушка новичка:** «EKS стоит $73 в месяц». Реальный счёт маленького продакшен-кластера — $300-600, и половина его — не EKS, а NAT Gateway, балансировщики, диски и трафик между зонами.

## 0.7 Где EKS используют: реальные сценарии

| Сценарий | Как применяется EKS |
|---|---|
| **Микросервисы** | Десятки сервисов, единый деплой через Helm/Argo, автоскейлинг по трафику |
| **Миграция монолита** | Lift-and-shift в контейнер, затем распил, ALB перед кластером |
| **Batch и data-обработка** | Spot-узлы через Karpenter, Job/CronJob, Argo Workflows, Spark на Kubernetes |
| **AI/ML** | GPU-узлы (P/G-серии), Trainium/Inferentia, Kubeflow, Ray, KServe, шаринг GPU |
| **Мультитенантная платформа** | Namespace-per-team, квоты, RBAC, golden path и шаблоны для продуктовых команд |
| **SaaS с несколькими регионами** | Кластер на регион, ECR-репликация, Route 53 с health checks |
| **Гибрид и edge** | EKS Hybrid Nodes: узлы on-prem под управлением control plane в AWS |
| **Замена самописного k8s** | Уход от kubeadm-кластеров, чтобы перестать дежурить за etcd |

## 0.8 Когда EKS не нужен

- **Один-два стейтлес-сервиса на HTTP.** Возьми ECS Fargate или App Runner: дешевле и проще, кластер за $73/мес в фоне не нужен.
- **Нет человека, который отвечает за платформу.** EKS без владельца через полгода превращается в набор кластеров разных версий, где никто не знает, что там крутится.
- **Строго событийная нагрузка, редкие вызовы.** Lambda + SQS выиграет и по цене, и по эксплуатации.
- **Нужна максимальная экономия на маленьком масштабе.** Три dev-кластера — это $219/мес ещё до единого pod. Один кластер с namespace на окружение дешевле.
- **Требуется полный контроль над control plane** (кастомные флаги apiserver, свой scheduler в мастерах, особые admission-конфиги на уровне apiserver): бери самостоятельный кластер.

## 0.9 Что EKS НЕ делает за тебя

EKS даёт управляемый control plane. Работоспособность системы проектируешь ты:

- **requests/limits и probes.** Без них кластер будет падать красиво и непредсказуемо.
- **Дизайн VPC и IP-адресация.** Подсеть на /27 в продакшене — это авария, отложенная на месяц.
- **IAM и RBAC.** По умолчанию создатель кластера — администратор, а больше никто ничего не видит.
- **Обновление версий.** EKS напомнит и в крайнем случае обновит принудительно, но ломать совместимость API будешь ты.
- **Бэкапы приложений и PV.** etcd бэкапит AWS, твои PersistentVolume — нет (Velero, EBS snapshots).
- **Стоимость.** Кластер без лимитов и с `m5.4xlarge` под три nginx будет работать. И стоить.
- **Наблюдаемость.** Логи control plane по умолчанию **выключены**.

### Вопросы для самопроверки

1. Что именно AWS делает за тебя в EKS, а что остаётся на тебе?
2. Почему кластер стоит денег, даже если в нём ноль узлов и ноль pod?
3. Чем extended support отличается от стандартного и во сколько раз дороже?
4. В каких случаях ты выберешь ECS вместо EKS?
5. Что такое Fargate в контексте EKS: альтернатива EKS или его часть?

---

# Модуль 1. Архитектура EKS: control plane, data plane, VPC

## 1.1 Главная схема

```
                    AWS-управляемый VPC (ты его не видишь)
        +---------------------------------------------------------+
        |   kube-apiserver (HA, 3 AZ)   etcd (3 AZ, шифрование)  |
        |   scheduler   controller-manager                        |
        +----------------------------+----------------------------+
                                     |
                       EKS-owned ENI в твоих подсетях
                       (cross-account ENI, sg: eks-cluster-sg-*)
                                     |
        ==================== твой VPC ============================
        |                            |                           |
   +---------+                 +---------+                 +---------+
   |  AZ a   |                 |  AZ b   |                 |  AZ c   |
   | node 1  |                 | node 2  |                 | node 3  |
   | kubelet |                 | kubelet |                 | kubelet |
   | kube-   |                 | ...     |                 | ...     |
   | proxy   |                 |         |                 |         |
   | VPC CNI |                 |         |                 |         |
   | pods с  |                 |         |                 |         |
   | VPC-IP  |                 |         |                 |         |
   +---------+                 +---------+                 +---------+
        |                            |                           |
   ALB/NLB, EBS, EFS, ECR, Secrets Manager, CloudWatch, S3 ...
```

Ключевые факты по этой схеме:

- **Control plane живёт в аккаунте AWS**, не в твоём. Ты не видишь эти EC2 и не можешь на них зайти.
- **Связь двусторонняя.** Твой `kubectl` идёт на публичный (или приватный) эндпоинт apiserver. Apiserver идёт к kubelet (`kubectl logs`, `exec`, webhooks) через **EKS-owned ENI** в твоих подсетях. Поэтому EKS требует минимум **две подсети в разных AZ** при создании кластера.
- **Каждый pod получает реальный IP из подсети VPC** (это VPC CNI, модуль 7). Никакого overlay и инкапсуляции по умолчанию. Отсюда все плюсы (производительность, security groups, видимость в VPC Flow Logs) и главный минус — IP-адреса кончаются.

## 1.2 Компоненты, которые нужно знать по именам

| Компонент | Где живёт | Зачем |
|---|---|---|
| `kube-apiserver` | AWS | Единственная точка входа; всё, что делает `kubectl` — HTTP к нему |
| `etcd` | AWS | Состояние кластера; шифруется, бэкапится AWS |
| `kubelet` | Твой узел | Запускает контейнеры, отчитывается о состоянии узла |
| `kube-proxy` | Твой узел (DaemonSet) | Правила iptables/nftables для ClusterIP-сервисов |
| **VPC CNI** (`aws-node`) | Твой узел (DaemonSet) | Выдаёт pod настоящие VPC-IP, управляет ENI |
| **CoreDNS** | Deployment | DNS внутри кластера (`svc.cluster.local`) |
| **EKS Pod Identity Agent** | DaemonSet | Отдаёт pod временные AWS-креденшелы |
| **AWS Load Balancer Controller** | Deployment (ты ставишь) | Создаёт ALB/NLB по Ingress и Service |
| **EBS/EFS CSI driver** | DaemonSet + controller | Монтирует диски в pod |
| **Karpenter** или Cluster Autoscaler | Deployment | Добавляет и удаляет узлы |
| `metrics-server` | Deployment (ты ставишь) | `kubectl top` и HPA |

Запомни: **`metrics-server` в EKS не установлен по умолчанию**. Это первый вопрос-ловушка: «почему `kubectl top nodes` отвечает `error: Metrics API not available`».

## 1.3 Endpoint access: три режима

Как `kubectl` и узлы достают apiserver — один из главных архитектурных выборов.

| Режим | Что значит | Когда |
|---|---|---|
| **Public** (по умолчанию) | Эндпоинт доступен из интернета, доступ ограничен IAM + CIDR-списком | Учёба, dev |
| **Public + Private** | Из интернета можно, узлы и pod внутри VPC ходят приватно | Самый частый прод-вариант |
| **Private only** | Только из VPC, VPN, Direct Connect или через bastion | Регулируемые среды, строгие политики |

```bash
# ограничить публичный доступ своим офисным IP и включить приватный
aws eks update-cluster-config --name demo \
  --resources-vpc-config endpointPublicAccess=true,publicAccessCidrs=203.0.113.10/32,endpointPrivateAccess=true
```

**Классическая авария:** переключили кластер в private-only, а CI/CD и инженеры сидят в интернете. Кластер живой, управлять им никто не может. Перед переключением подготовь путь доступа: VPN, bastion, self-hosted runner в VPC или SSM-порт-форвардинг.

## 1.4 Что создаётся при `create-cluster` в твоём аккаунте

- **EKS-owned ENI** в переданных подсетях (по одной-двум на AZ).
- **Cluster security group** `eks-cluster-sg-<name>-<id>`: разрешает весь трафик внутри себя. Узлы, созданные managed node group, попадают в неё автоматически.
- **OIDC-провайдер** (опционально, но нужен для IRSA).
- **Log group** в CloudWatch, если включены логи control plane.
- **Access entries** для создателя кластера.

Кластер также получает **cluster IAM role** — роль, от имени которой EKS управляет ресурсами в твоём аккаунте (ENI, балансировщики при удалении и так далее). Узлы получают **node IAM role** — отдельную, с политиками на ECR, CNI и SSM.

## 1.5 Требования к VPC, которые важно знать заранее

- минимум **две подсети в двух AZ**; для прода — три;
- подсети должны быть достаточно большими: **/24 это мало для узла на m5.4xlarge** (см. модуль 7);
- тег `kubernetes.io/role/elb=1` на публичных подсетях и `kubernetes.io/role/internal-elb=1` на приватных — иначе Load Balancer Controller не поймёт, где создавать балансировщик;
- узлам нужен выход к ECR, S3, EC2 API и EKS API: либо через NAT Gateway, либо через **VPC endpoints** (дешевле и приватнее);
- `enableDnsSupport` и `enableDnsHostnames` включены;
- не используй подсети, где IP уже расходуют RDS, Lambda и ALB: pod съедят адреса и подсеть кончится.

Типовой прод-дизайн:

```
VPC 10.0.0.0/16
  публичные подсети   10.0.0.0/20,  10.0.16.0/20,  10.0.32.0/20   (ALB, NAT GW)
  приватные подсети   10.0.64.0/18, 10.0.128.0/18, 10.0.192.0/18  (узлы и pod)
```

Приватные подсети специально огромные: pod едят IP-адреса из них десятками и сотнями.

## 1.6 Первая ментальная модель

```
IAM даёт право говорить с apiserver  →  RBAC даёт право что-то в нём делать
apiserver планирует pod              →  Karpenter/node group даёт узлы
VPC CNI даёт pod IP                  →  подсеть должна иметь свободные IP
Service даёт стабильный ClusterIP    →  Ingress + LBC даёт ALB и публичный адрес
CSI даёт pod диск                    →  EBS живёт в одной AZ, помни об этом
Pod Identity даёт pod права в AWS    →  никаких статических ключей в секретах
```

Шесть строк, на которых держится весь курс. К каждой вернёмся в своём модуле.

### Вопросы для самопроверки

1. Почему EKS требует минимум две подсети в разных AZ?
2. Что такое EKS-owned ENI и зачем оно нужно?
3. Чем отличаются cluster security group, cluster IAM role и node IAM role?
4. Что сломается, если переключить кластер в private-only, не подготовившись?
5. Почему `kubectl top nodes` не работает на свежем кластере?

---

# Модуль 2. Первый кластер: eksctl, Terraform, Console

## 2.1 Три способа создать кластер

| Способ | Плюсы | Минусы | Для чего |
|---|---|---|---|
| **eksctl** | Один YAML или одна команда, всё «просто работает» | Под капотом CloudFormation, дрейф от твоего IaC | Учёба, эксперименты, быстрый dev |
| **Terraform** (`terraform-aws-modules/eks`) | Единый IaC, code review, повторяемость | Больше кода, надо понимать зависимости | Продакшен |
| **Console** | Видно все поля и их смысл | Невоспроизводимо, «кто это создал?» через полгода | Один раз посмотреть глазами |

Рекомендация курса: первый кластер сделай `eksctl` (чтобы получить результат за 20 минут), второй — Terraform (чтобы понять, из чего он состоит), в продакшен иди только с IaC.

## 2.2 Самый быстрый кластер: EKS Auto Mode

Auto Mode сам поднимает узлы, CSI-драйверы и Load Balancer Controller. Для старта это лучший вариант: меньше всего движущихся частей.

```bash
eksctl create cluster \
  --name demo-auto \
  --region eu-central-1 \
  --version 1.36 \
  --enable-auto-mode
```

Ждать примерно 15 минут. Что произошло:

```bash
kubectl get nodes                     # пока пусто: узлов нет, пока нет pod
kubectl get nodepool                  # general-purpose и system от Auto Mode
kubectl get pods -A
```

Узлы появятся, когда появится первый pod:

```bash
kubectl create deployment web --image=public.ecr.aws/nginx/nginx:1.27 --replicas=2
kubectl get pods -w                   # Pending → ContainerCreating → Running
kubectl get nodes                     # узел приехал сам, за ~1 минуту
```

Это и есть главный эффект Auto Mode: **узлы следуют за pod**, а не наоборот.

## 2.3 Классический кластер с managed node group

Так выглядит кластер, который ты чаще всего встретишь на работе. Файл `cluster.yaml`:

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
    gateway: Single          # для учёбы: один NAT дешевле трёх

iam:
  withOIDC: true             # нужно для IRSA, включай всегда

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

Обрати внимание на четыре вещи, которые новички забывают: `withOIDC: true`, несколько `instanceTypes` (иначе однажды не будет capacity в AZ), `privateNetworking: true` (узлы не должны иметь публичный IP) и явный список аддонов, включая `metrics-server`.

## 2.4 Тот же кластер на Terraform

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
  single_nat_gateway = true          # в проде: false, по одному NAT на AZ

  # без этих тегов Load Balancer Controller не найдёт подсети
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

  # современный способ доступа: access entries вместо aws-auth
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

## 2.5 Подключаемся к кластеру

```bash
aws eks update-kubeconfig --name demo --region eu-central-1
kubectl config current-context
kubectl get nodes -o wide
kubectl get pods -A
kubectl cluster-info
```

Что именно делает `update-kubeconfig`: он записывает в `~/.kube/config` контекст, в котором токен получается вызовом `aws eks get-token`. То есть **аутентификация в EKS всегда идёт через твои AWS-креденшелы**, а не через статический сертификат.

```yaml
# фрагмент ~/.kube/config
users:
- name: arn:aws:eks:eu-central-1:111122223333:cluster/demo
  user:
    exec:
      apiVersion: client.authentication.k8s.io/v1beta1
      command: aws
      args: ["--region", "eu-central-1", "eks", "get-token", "--cluster-name", "demo"]
```

Отсюда следствие: если ты сменил AWS-профиль или у роли истёк доступ, `kubectl` начнёт отвечать `error: You must be logged in to the server (Unauthorized)`, хотя ещё минуту назад всё работало.

## 2.6 Первое приложение от пустого кластера до URL

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
kubectl -n demo get pods -o wide            # обрати внимание: pod разложены по AZ
kubectl -n demo port-forward svc/web 8080:80
curl -s localhost:8080 | head -5
```

Публичный адрес через ALB сделаем в модуле 8: для него нужен Load Balancer Controller (или Auto Mode, где он уже есть).

## 2.7 Самые частые ошибки первого дня

| Симптом | Причина | Что делать |
|---|---|---|
| `error: You must be logged in to the server (Unauthorized)` | Другая IAM-личность, чем создатель кластера, или истекли креденшелы | `aws sts get-caller-identity`, затем access entry (модуль 3) |
| Узлы не появляются в `kubectl get nodes` | Нет выхода в интернет/endpoint, нет прав у node role, не тот security group | Проверь NAT/VPC endpoints и политики node role |
| Pod вечно `Pending` | Нет узлов, нет ресурсов, не проходит по taint/affinity | `kubectl describe pod` и читай Events до конца |
| `ImagePullBackOff` из ECR | У node role нет `AmazonEC2ContainerRegistryReadOnly` или нет пути к ECR | Политика + VPC endpoint для ECR и S3 |
| `couldn't get current server API group list` | Не тот контекст `kubectl` или кластер уже удалён | `kubectl config get-contexts` |
| CloudFormation-стек `DELETE_FAILED` | Остались ALB/ENI, созданные контроллерами | Удаляй сначала Service type=LoadBalancer и Ingress, потом кластер |

## 2.8 Удаление кластера (делай это каждый раз)

```bash
# 1. сначала снести то, что создало AWS-ресурсы за пределами кластера
kubectl delete ingress --all -A
kubectl delete svc --all-namespaces --field-selector spec.type=LoadBalancer
kubectl delete pvc --all -A

# 2. потом кластер
eksctl delete cluster --name demo --region eu-central-1 --wait
# или
terraform destroy
```

Порядок важен: если снести кластер первым, останутся «сиротские» ALB, ENI и EBS-диски, которые продолжат тарифицироваться, а удаление VPC будет падать с `DependencyViolation`.

```bash
# проверка, что ничего не осталось
aws eks list-clusters
aws elbv2 describe-load-balancers --query 'LoadBalancers[].LoadBalancerName'
aws ec2 describe-volumes --filters Name=status,Values=available --query 'Volumes[].VolumeId'
```

### Практика

1. Создай кластер с Auto Mode, задеплой nginx, убедись, что узел появился сам, замерь время.
2. Создай второй кластер на Terraform с managed node group и сравни: что тебе пришлось описать руками.
3. Сломай доступ намеренно: `export AWS_PROFILE=нет-такого` и посмотри текст ошибки `kubectl`.
4. Удали кластеры и проверь через AWS CLI, что не осталось ни ALB, ни томов.

---
# Модуль 3. Доступ к кластеру: IAM, access entries, RBAC

## 3.1 Две системы прав, которые нужно различать

В EKS каждый запрос проходит **два контроля**:

```
kubectl get pods
   |
   |-- 1. АУТЕНТИФИКАЦИЯ: кто ты?  →  AWS IAM (sts, токен от aws eks get-token)
   |                                   apiserver превращает IAM ARN в k8s-личность
   |
   +-- 2. АВТОРИЗАЦИЯ: что тебе можно?  →  Kubernetes RBAC (Role/ClusterRole)
```

Это источник главной путаницы новичков: **`AdministratorAccess` в IAM не даёт прав внутри кластера.** Ты можешь иметь право удалить кластер целиком и при этом получать `Forbidden` на `kubectl get pods`. Наоборот тоже верно: `cluster-admin` в RBAC не даёт прав в AWS.

## 3.2 Access entries: современный способ (используй его)

Раньше маппинг IAM → Kubernetes жил в ConfigMap `aws-auth`, и одна опечатка в нём отрезала доступ всем. С 2023 года есть **access entries** — полноценный API EKS.

```bash
# посмотреть, кто имеет доступ
aws eks list-access-entries --cluster-name demo

# режим аутентификации кластера
aws eks describe-cluster --name demo --query 'cluster.accessConfig'
```

Режимы (`authenticationMode`):

| Режим | Что работает |
|---|---|
| `CONFIG_MAP` | Только старый `aws-auth` (legacy) |
| `API_AND_CONFIG_MAP` | Оба, приоритет у access entries — безопасный путь миграции |
| `API` | Только access entries (цель) |

Переключение только в одну сторону: `CONFIG_MAP` → `API_AND_CONFIG_MAP` → `API`. Обратно нельзя.

```bash
aws eks update-cluster-config --name demo \
  --access-config authenticationMode=API_AND_CONFIG_MAP
```

## 3.3 Даём доступ роли: три типовых случая

**Администратор платформы:**

```bash
aws eks create-access-entry --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/PlatformAdmin \
  --type STANDARD

aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/PlatformAdmin \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSClusterAdminPolicy \
  --access-scope type=cluster
```

**Разработчик, только своё namespace:**

```bash
aws eks create-access-entry --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/DevTeamA \
  --kubernetes-groups '[]' --type STANDARD

aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/DevTeamA \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy \
  --access-scope type=namespace,namespaces=team-a
```

**Read-only для дежурного или аудитора:**

```bash
aws eks associate-access-policy --cluster-name demo \
  --principal-arn arn:aws:iam::111122223333:role/OnCallViewer \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSViewPolicy \
  --access-scope type=cluster
```

Готовые EKS access policies:

| Политика | Что даёт |
|---|---|
| `AmazonEKSClusterAdminPolicy` | Полный `cluster-admin` |
| `AmazonEKSAdminPolicy` | Админ, но без некоторых кластерных объектов |
| `AmazonEKSEditPolicy` | Создавать и менять workload |
| `AmazonEKSViewPolicy` | Только чтение |
| `AmazonEKSAdminViewPolicy` | Чтение, включая Secret-метаданные |
| `AmazonEKSAutoNodePolicy`, `AmazonEKSNetworkingClusterPolicy` и другие | Служебные, для Auto Mode и контроллеров |

Если готовых политик мало — маппишь IAM-роль в свою Kubernetes-группу и пишешь RBAC сам:

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

## 3.4 Terraform: access entries как код

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

## 3.5 Legacy: aws-auth ConfigMap

Встретишь на любом кластере старше 2024 года.

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

**Три правила работы с `aws-auth`:**

1. **Никогда не редактируй его без бэкапа.** `kubectl -n kube-system get cm aws-auth -o yaml > aws-auth.bak.yaml`.
2. **Не удаляй строку с node role.** Узлы мгновенно уйдут в `NotReady` и не вернутся.
3. Если сломал и потерял доступ всем — восстанавливай через access entry той IAM-личностью, которая создавала кластер, или через `--principal-arn` создателя.

Миграция: включи `API_AND_CONFIG_MAP`, создай access entries для всех, кто есть в `aws-auth`, проверь доступ, вычисти ConfigMap, переключись на `API`.

## 3.6 Кто я и что мне можно

```bash
aws sts get-caller-identity                       # кто я в IAM
kubectl auth whoami                               # кем меня видит apiserver
kubectl auth can-i --list                         # полный список прав
kubectl auth can-i delete pods -n prod            # конкретная проверка
kubectl auth can-i get secrets -n kube-system --as=system:serviceaccount:demo:default
```

`kubectl auth can-i --as` — лучший инструмент отладки RBAC: он спрашивает apiserver, а не догадки.

## 3.7 Чек-лист прав в продакшене

- `authenticationMode=API`, `aws-auth` пуст или содержит только node roles;
- нет ни одного `mapUsers`: люди ходят через SSO-роли (IAM Identity Center), а не через IAM-пользователей;
- `system:masters` есть максимум у одной break-glass роли, вход по ней алертится в CloudTrail;
- у CI/CD роль с правами на конкретные namespace, а не `cluster-admin`;
- аудит-логи control plane включены (`audit`, `authenticator`);
- у команд ServiceAccount с минимальными правами, `automountServiceAccountToken: false` там, где токен не нужен.

### Вопросы для самопроверки

1. Почему `AdministratorAccess` в IAM не даёт права на `kubectl get pods`?
2. Чем access entries лучше `aws-auth` ConfigMap?
3. Что произойдёт, если удалить из `aws-auth` запись node role?
4. Как проверить, что ServiceAccount не может читать секреты в `kube-system`?
5. Почему переключение `authenticationMode` необратимо и что из этого следует?

---

# Модуль 4. Compute: node groups, Fargate, Auto Mode

## 4.1 Четыре варианта, где живут твои pod

| Вариант | Кто провижинит | Кто патчит ОС | Гранулярность оплаты | Контроль |
|---|---|---|---|---|
| **Self-managed nodes** | Ты (ASG, Launch Template) | Ты | За инстанс | Максимальный: свой AMI, userdata, ядро |
| **Managed node group** | EKS по твоему описанию | Ты запускаешь, AWS выполняет | За инстанс | Высокий |
| **AWS Fargate** | AWS, на каждый pod | AWS | **За pod**, посекундно | Низкий: нет DaemonSet, нет привилегий, нет GPU |
| **EKS Auto Mode** | AWS (Karpenter внутри) | AWS | За инстанс + ~12% | Средний: нет SSH, узел живёт максимум 21 день |

## 4.2 Managed node group: рабочая лошадка

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

Что даёт managed node group поверх обычной ASG:

- **Graceful drain при обновлении и удалении:** EKS сам cordon/drain узла, уважая PodDisruptionBudget;
- **Автоматическая привязка к кластеру:** узел появится в `kubectl get nodes` без ручного `bootstrap.sh`;
- **Node health monitoring:** узел с проблемой заменяется;
- **Метки и taint на уровне API EKS**, видимые в консоли и Terraform;
- **Spot с несколькими типами инстансов и обработкой прерываний.**

Ключевые параметры и почему они важны:

```yaml
managedNodeGroups:
  - name: ng-general
    instanceTypes: ["m6i.large", "m6a.large", "m5.large"]   # ≥3 типа: иначе однажды InsufficientInstanceCapacity
    amiFamily: AmazonLinux2023                              # AL2 больше не выпускается с 1.33
    spot: false
    minSize: 3
    maxSize: 12
    desiredCapacity: 3
    volumeType: gp3
    volumeSize: 50
    volumeIOPS: 3000
    privateNetworking: true
    maxPodsPerNode: 110                                     # см. модуль 7 про лимиты ENI
    updateConfig:
      maxUnavailablePercentage: 25                          # скорость роллинга при обновлении
    labels:
      workload: general
    taints: []
    tags:
      k8s.io/cluster-autoscaler/enabled: "true"
```

## 4.3 Spot без боли

Spot экономит до 90%, но инстанс могут забрать за 2 минуты. Что нужно, чтобы это было безопасно:

1. **Много типов инстансов** (10+ в одной группе) и несколько AZ — вероятность одновременного прерывания падает;
2. **Разделение нагрузки:** stateless и batch на Spot, stateful и системное (CoreDNS, контроллеры) на On-Demand;
3. **PodDisruptionBudget** на каждый важный Deployment;
4. **`terminationGracePeriodSeconds`** и корректная обработка SIGTERM в приложении;
5. **Node termination handling** — в managed node group и Karpenter уже встроено, самописному ASG нужен AWS Node Termination Handler.

```yaml
# нагрузку на Spot отправляем метками, системное держим на On-Demand
      nodeSelector:
        karpenter.sh/capacity-type: spot
      tolerations:
        - key: workload
          value: batch
          effect: NoSchedule
```

## 4.4 Graviton: почти бесплатные 20-40%

ARM-инстансы (`m7g`, `c7g`, `r7g`) дают примерно на 20-40% лучшую цену за производительность. Что нужно:

```bash
# многоархитектурный образ
docker buildx build --platform linux/amd64,linux/arm64 -t <acct>.dkr.ecr.eu-central-1.amazonaws.com/app:1.0 --push .
```

```yaml
      nodeSelector:
        kubernetes.io/arch: arm64
```

Проверь, что все твои сайдкары, агенты и базовые образы имеют arm64-сборки: это главный блокер миграции, а не само приложение.

## 4.5 Fargate в EKS: когда и почему

Fargate запускает **один pod на один микро-VM**, без узлов. Нужен Fargate profile, который говорит «pod из namespace X с метками Y попадают на Fargate»:

```bash
eksctl create fargateprofile \
  --cluster demo \
  --name fp-jobs \
  --namespace batch \
  --labels runtime=fargate
```

Ограничения, из-за которых Fargate не заменяет узлы:

- **нет DaemonSet** (значит, агенты логов и мониторинга — только сайдкарами);
- нет GPU, нет privileged, нет hostNetwork и hostPath;
- максимум ~16 vCPU и 120 ГБ на pod, фиксированные комбинации ресурсов;
- эфемерное хранилище ограничено (по умолчанию 20 ГБ, расширяемо);
- pod стартует медленнее (десятки секунд);
- на постоянной нагрузке **дороже EC2** примерно в 1.5-2 раза.

Хорошие сценарии: редкие CronJob, быстрые всплески, изоляция мультитенантных задач, маленький кластер, где не хочется вообще иметь узлы.

## 4.6 EKS Auto Mode: узлы как сервис

Auto Mode (GA с декабря 2024) — это упакованный AWS-ом Karpenter плюс набор контроллеров:

- **compute:** провижинит и консолидирует узлы под неразмещённые pod;
- **storage:** EBS CSI уже внутри, `StorageClass` создаётся автоматически;
- **networking:** Load Balancer Controller внутри, ALB/NLB создаются по Ingress и Service;
- **identity:** Pod Identity Agent внутри;
- **обслуживание:** узел живёт **максимум 21 день** и заменяется на свежий AMI автоматически.

```bash
# включить на существующем кластере
aws eks update-cluster-config --name demo \
  --compute-config enabled=true,nodePools=general-purpose,system \
  --kubernetes-network-config '{"elasticLoadBalancing":{"enabled":true}}' \
  --storage-config '{"blockStorage":{"enabled":true}}'
```

Свой NodePool в Auto Mode (API отличается от обычного Karpenter: `eks.amazonaws.com/v1`, а не `karpenter.k8s.aws/v1`):

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

**Что теряешь с Auto Mode:**

- нет SSH и SSM на узел: диагностика только через Kubernetes API и логи;
- нельзя закрепить версию Karpenter или включить экспериментальные флаги;
- нельзя поставить свой AMI и свой userdata;
- DaemonSet с глубоким доступом к хосту (некоторые security-агенты) могут не работать;
- наценка ~12% к цене EC2, и Savings Plans её **не покрывают**;
- существующие балансировщики от self-managed LBC не переезжают: нужна blue-green миграция.

**Когда Auto Mode — правильный выбор:** маленькая команда без выделенного platform-инженера; новый кластер; нагрузка, которая нормально переживает замену узлов. С июля 2026 наценка на GPU-инстансы снижена (G-серия −35%, P-серия и Trainium −60%), что делает Auto Mode заметно привлекательнее для ML.

**Когда не выбирать:** уже есть отлаженный Karpenter, нужен свой AMI, нужен полный контроль над узлом, или парк настолько велик, что 12% — это зарплата двух инженеров.

## 4.7 Как выбирать: дерево решений

```
Нужен свой AMI / ядро / privileged-агенты?
  └── да → self-managed nodes
  └── нет
       ├── Нагрузка редкая, изолированная, без DaemonSet?  → Fargate
       ├── Нет выделенного platform-инженера, хочется меньше тоила?  → Auto Mode
       ├── Большой парк, нужен точный контроль расходов и версий?  → managed node groups + Karpenter
       └── Классика, простая нагрузка, небольшой кластер?  → managed node groups
```

В реальных кластерах почти всегда **смесь**: On-Demand managed node group под системное (CoreDNS, контроллеры, Argo), Karpenter или Auto Mode под приложения, Fargate под редкие job.

## 4.8 Правильный размер узла

| Слишком маленькие (`t3.medium`) | Слишком большие (`m6i.8xlarge`) |
|---|---|
| Мало pod на узел из-за лимитов ENI | Падение одного узла = потеря большой доли capacity |
| Высокая доля накладных расходов (kubelet, DaemonSet, зарезервированная память) | Плохая гранулярность масштабирования |
| Burst-инстансы (`t`) на проде — источник загадочных тормозов | Долгий drain при обновлении |

Разумная база: **`m6i.large` - `m6i.2xlarge`** для общего назначения; `c` для CPU-bound, `r` для памяти, `m7g/c7g` для экономии. И держи узлы **не в одном AZ**.

Не забывай, что часть ресурсов узла резервируется:

```bash
kubectl describe node <node> | grep -A6 "Allocatable"
# на m6i.large (2 vCPU / 8 ГБ) под pod остаётся ~1.9 vCPU и ~7 ГБ
```

## 4.9 Практические команды

```bash
eksctl get nodegroup --cluster demo
aws eks describe-nodegroup --cluster-name demo --nodegroup-name ng-general

# масштабирование вручную
eksctl scale nodegroup --cluster demo --name ng-general --nodes 5

# обновить AMI узлов (rolling, с уважением PDB)
eksctl upgrade nodegroup --cluster demo --name ng-general

# вывести узел из работы
kubectl cordon ip-10-0-70-12.eu-central-1.compute.internal
kubectl drain ip-10-0-70-12.eu-central-1.compute.internal \
  --ignore-daemonsets --delete-emptydir-data --grace-period=60
kubectl uncordon ip-10-0-70-12.eu-central-1.compute.internal
```

### Практика

1. Создай Spot node group из 6+ типов инстансов, задеплой 10 реплик, вручную terminate узел в EC2 Console и посмотри, как переезжают pod.
2. Сделай Fargate profile для namespace `batch`, запусти там CronJob, сравни время старта pod с EC2-узлом.
3. Включи Auto Mode на тестовом кластере, создай свой NodePool на Spot+ARM, задеплой нагрузку и посмотри `kubectl get nodeclaims`.
4. Собери многоархитектурный образ и запусти его на Graviton-узле.

---

# Модуль 5. Karpenter: автомасштабирование узлов по-взрослому

## 5.1 Cluster Autoscaler vs Karpenter

| | Cluster Autoscaler | Karpenter |
|---|---|---|
| Как работает | Меняет `desired` у ASG | Создаёт EC2-инстансы напрямую |
| Выбор инстанса | Из заданных в node group | Из сотен типов, подбирает под pod |
| Скорость узла | Минуты | Десятки секунд |
| Bin-packing | Слабый | Сильный, с консолидацией |
| Spot | Через ASG-политики | Нативно, с учётом вероятности прерывания |
| Конфигурация | Node group на каждую комбинацию | 1-2 NodePool на весь кластер |
| Итог | Legacy, всё ещё встречается | Стандарт 2026 года |

Если на собеседовании спрашивают «чем масштабируете узлы» — правильный ответ в 2026 году это Karpenter (или Auto Mode, который и есть управляемый Karpenter).

## 5.2 Установка

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

Karpenter нужны: IAM-роль контроллера (через Pod Identity или IRSA), IAM-роль для узлов, SQS-очередь для событий прерывания Spot и правила EventBridge. Проще всего взять готовый Terraform-модуль `terraform-aws-modules/eks/aws//modules/karpenter`.

Важно: **сам Karpenter должен работать не на тех узлах, которые он создаёт.** Держи его на небольшой On-Demand managed node group или на Fargate, иначе получишь курицу и яйцо при полном пересоздании парка.

## 5.3 NodePool и EC2NodeClass

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
          values: ["5"]            # только 6-е поколение и новее
        - key: topology.kubernetes.io/zone
          operator: In
          values: ["eu-central-1a", "eu-central-1b", "eu-central-1c"]
      expireAfter: 336h            # узлу максимум 14 дней: свежий AMI и патчи
      terminationGracePeriod: 5m
  limits:
    cpu: "1000"
    memory: 1000Gi
  disruption:
    consolidationPolicy: WhenEmptyOrUnderutilized
    consolidateAfter: 30s
    budgets:
      - nodes: "10%"                       # не трогать больше 10% парка одновременно
      - nodes: "0"                         # и вообще не трогать в часы пик
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
    httpTokens: required           # IMDSv2 обязательно
    httpPutResponseHopLimit: 1     # pod не должны достать роль узла
  tags:
    Environment: prod
    ManagedBy: karpenter
```

**Теги `karpenter.sh/discovery` на подсетях и security groups обязательны** — без них Karpenter не поймёт, где запускать узлы, и будет писать в логи, что не нашёл подсети.

## 5.4 Как Karpenter думает

```
1. Есть неразмещённые pod (Pending) → читает их requests, nodeSelector, affinity, topology, taints
2. Считает, какая комбинация инстансов покроет их дешевле всего
3. Создаёт NodeClaim → EC2 RunInstances → узел регистрируется в кластере (~40 секунд)
4. Периодически: можно ли уплотнить нагрузку и удалить/заменить узлы (consolidation)
5. Ловит событие прерывания Spot из SQS → заранее drain узла
6. Узел старше expireAfter → мягко заменяется на свежий
```

Отсюда важное следствие: **Karpenter планирует по `requests`, а не по фактическому потреблению.** Если сервис просит 2 CPU, а потребляет 0.3, Karpenter купит железо под 2 CPU. Большинство «Karpenter не экономит» — это проблема завышенных requests, а не автоскейлера (модуль 6 и 16).

## 5.5 Несколько NodePool под разную нагрузку

```yaml
# дорогая стабильная нагрузка: только On-Demand
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
# batch: только Spot, агрессивная консолидация
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

`weight` определяет приоритет: чем больше, тем раньше Karpenter пробует этот пул.

## 5.6 Диагностика

```bash
kubectl logs -n kube-system deploy/karpenter -f | grep -v "found provisionable pod"
kubectl get nodeclaims
kubectl get nodepools -o wide
kubectl describe nodeclaim <name>

# почему pod не размещается
kubectl describe pod <pod> | sed -n '/Events/,$p'
```

| Симптом | Частая причина |
|---|---|
| Узлы не создаются вообще | Нет тегов `karpenter.sh/discovery`, нет прав у роли контроллера, `limits` пула исчерпаны |
| `Insufficient capacity` на Spot | Слишком узкие requirements: добавь типы, поколения, AZ |
| Узлы создаются и сразу удаляются | Pod не может стартовать по другой причине (образ, PVC в другой AZ) |
| Слишком частая замена узлов | Агрессивный `consolidateAfter`, нет PDB, короткий `expireAfter` |
| Один узел на один pod | У pod огромные requests или anti-affinity `requiredDuringScheduling` |

## 5.7 Правила безопасной консолидации

- **PodDisruptionBudget на каждый важный Deployment** — иначе консолидация может убрать все реплики сразу;
- **disruption budgets в NodePool**: не больше 10-20% парка одновременно, и `nodes: "0"` в часы пиковой нагрузки;
- `do-not-disrupt` для особых pod:

```yaml
metadata:
  annotations:
    karpenter.sh/do-not-disrupt: "true"
```

- `terminationGracePeriodSeconds` в приложениях больше, чем время корректного завершения запросов;
- stateful-нагрузка с EBS: помни, что диск привязан к AZ, и добавь `topology.kubernetes.io/zone` в requirements узлов.

### Практика

1. Установи Karpenter, создай `NodePool` со Spot и ARM, задеплой 30 реплик nginx и посмотри, какие инстансы он выбрал и почему.
2. Уменьши реплики до 2 и наблюдай консолидацию: сколько узлов ушло и за сколько секунд.
3. Добавь PDB `minAvailable: 80%` и повтори: изменилось ли поведение.
4. Выставь `expireAfter: 30m` и посмотри плавную замену узлов на свежие.
5. Создай pod с `requests.cpu: 6` и найди в логах Karpenter, какой инстанс он подобрал.

---

# Модуль 6. Масштабирование приложений: HPA, KEDA, VPA, PDB

## 6.1 Четыре уровня масштабирования

```
Уровень 4: несколько кластеров / регионов      (модуль 17)
Уровень 3: узлы          → Karpenter / Auto Mode / Cluster Autoscaler  (модуль 5)
Уровень 2: реплики pod   → HPA, KEDA
Уровень 1: ресурсы pod   → requests/limits, VPA, right-sizing
```

Работать нужно снизу вверх. Масштабировать неправильно сконфигурированный pod — значит умножать проблему.

## 6.2 requests и limits: главные четыре числа

```yaml
resources:
  requests:
    cpu: 200m        # гарантия и основа планирования: по этому числу считает scheduler и Karpenter
    memory: 256Mi    # гарантия памяти
  limits:
    memory: 512Mi    # превышение → OOMKilled
    # cpu: специально не задан
```

Практические правила:

- **`requests.cpu`** ставь близко к реальному p50-p70 потреблению, не «на глазок ×5». Завышенные requests — главная причина дорогого кластера.
- **`limits.cpu` лучше не ставить вовсе** для латентно-чувствительных сервисов: CPU throttling из-за CFS quota даёт загадочные всплески задержки. Исключение — мультитенантный кластер, где нужна защита от шумного соседа.
- **`limits.memory` ставь всегда** и близко к `requests.memory`: память не сжимается, и без лимита один pod с утечкой съест узел.
- **`requests.memory == limits.memory`** даёт класс `Guaranteed` — самый защищённый от вытеснения.

```bash
kubectl top pods -n demo --containers        # фактическое потребление
kubectl -n demo describe pod <pod> | grep -i -A3 "Last State"   # был ли OOMKilled
```

## 6.3 metrics-server: без него HPA не работает

```bash
aws eks create-addon --cluster-name demo --addon-name metrics-server
kubectl top nodes
kubectl top pods -A
```

## 6.4 HPA: масштабирование по CPU и памяти

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
          averageUtilization: 70        # процент от requests.cpu, а не от ядра узла
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 0
      policies:
        - type: Percent
          value: 100
          periodSeconds: 30             # можно удваиваться каждые 30 секунд
    scaleDown:
      stabilizationWindowSeconds: 300   # вниз медленно, чтобы не дёргаться
      policies:
        - type: Percent
          value: 25
          periodSeconds: 60
```

```bash
kubectl -n demo get hpa -w
kubectl -n demo describe hpa web        # смотри Events и Conditions
```

**Ловушка:** `averageUtilization: 70` считается от `requests.cpu`. Если requests завышены в 5 раз, HPA не отмасштабирует сервис никогда, даже под нагрузкой.

Проверка нагрузкой:

```bash
kubectl -n demo run load --rm -it --image=williamyeh/hey -- \
  -z 120s -c 100 http://web.demo.svc.cluster.local/
```

## 6.5 KEDA: масштабирование по внешним событиям

HPA умеет CPU и память. Реальная нагрузка обычно измеряется длиной очереди SQS, лагом Kafka или числом сообщений. Это KEDA.

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
  minReplicaCount: 0                 # scale-to-zero, чего HPA не умеет
  maxReplicaCount: 50
  pollingInterval: 15
  cooldownPeriod: 120
  triggers:
    - type: aws-sqs-queue
      authenticationRef:
        name: keda-aws-creds
      metadata:
        queueURL: https://sqs.eu-central-1.amazonaws.com/111122223333/jobs
        queueLength: "20"            # одна реплика на каждые 20 сообщений
        awsRegion: eu-central-1
```

KEDA умеет десятки источников: SQS, Kafka, RabbitMQ, Prometheus-запрос, CloudWatch-метрика, cron, Postgres-запрос. Для batch-нагрузки `minReplicaCount: 0` плюс Karpenter на Spot — самая экономная комбинация в EKS.

## 6.6 VPA и right-sizing

VPA подбирает `requests` автоматически. Осторожно: в режиме `Auto` он **пересоздаёт pod**, что не всегда приемлемо.

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
    updateMode: "Off"        # начни с рекомендаций, без автоприменения
```

```bash
kubectl -n demo describe vpa web | sed -n '/Recommendation/,$p'
```

Практичный путь: держи VPA в режиме `Off` как советчика, а решение о `requests` принимай сам (или через CI-проверку). В Kubernetes 1.33+ есть **in-place pod resize** (beta), который со временем уберёт необходимость в перезапуске.

## 6.7 PodDisruptionBudget: защита при любых заменах узлов

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: web
  namespace: demo
spec:
  minAvailable: 2          # или maxUnavailable: 1 / minAvailable: 80%
  selector:
    matchLabels: { app: web }
```

PDB влияет на всё, что делает drain: обновление node group, консолидация Karpenter, замена узла в Auto Mode, обработка Spot-прерывания. **Без PDB в EKS ты не имеешь права говорить, что сервис отказоустойчив.**

Осторожно с `minAvailable`, равным числу реплик: тогда drain не сможет вытеснить ни один pod, и обновление узлов встанет навсегда.

## 6.8 Раскладывание pod по зонам и узлам

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

Правило: по зонам — `DoNotSchedule` (иначе отказ одной AZ уложит сервис), по узлам — `ScheduleAnyway` (иначе pod будут висеть в `Pending` из-за нехватки узлов).

Помни про стоимость: трафик между AZ стоит $0.01/ГБ в каждую сторону. Для чатливых сервисов рассмотри `trafficDistribution: PreferSameZone` (стабильно с 1.36) на Service:

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

## 6.9 Probes, без которых масштабирование бессмысленно

```yaml
          startupProbe:                 # для медленных стартов (JVM и подобное)
            httpGet: { path: /healthz, port: 8080 }
            failureThreshold: 30
            periodSeconds: 5
          readinessProbe:               # готов принимать трафик
            httpGet: { path: /readyz, port: 8080 }
            periodSeconds: 5
            timeoutSeconds: 2
          livenessProbe:                # завис, нужно перезапустить
            httpGet: { path: /healthz, port: 8080 }
            periodSeconds: 10
            failureThreshold: 3
```

Три правила: readiness обязателен всегда (без него ALB будет лить трафик в неготовый pod); liveness проверяет только «процесс жив», а не зависимости (иначе падение базы перезапустит весь кластер приложений); startupProbe вместо огромного `initialDelaySeconds`.

### Практика

1. Поставь `requests.cpu: 1000m` сервису, который потребляет 50m, включи HPA на 70% и убедись, что он не масштабируется под нагрузкой. Исправь requests и повтори.
2. Настрой KEDA на SQS, налей 1000 сообщений, посмотри, как реплики поднимаются с нуля, а Karpenter добавляет узлы.
3. Добавь PDB `minAvailable: 100%` и попробуй `kubectl drain` узла: убедись, что он висит. Исправь на `maxUnavailable: 1`.
4. Убери readinessProbe и посмотри в логах ALB Target Group 5xx во время деплоя.

---
# Модуль 7. Сеть EKS: VPC CNI, IP-адресация, лимиты

## 7.1 Главное отличие EKS от «обычного» Kubernetes

В большинстве кластеров pod живут в overlay-сети (Flannel, Calico VXLAN) со своими адресами. В EKS по умолчанию работает **Amazon VPC CNI**, и каждый pod получает **настоящий IP из подсети твоего VPC**.

```
Узел m6i.large:
  ENI #1 (primary)   10.0.70.12   → IP узла + до 9 IP для pod
  ENI #2             10.0.70.45   → до 10 IP для pod
  ENI #3             10.0.70.98   → до 10 IP для pod
  ...
  pod видны в VPC напрямую: 10.0.70.31, 10.0.70.55 ...
```

| Плюсы | Минусы |
|---|---|
| Нет инкапсуляции: почти нулевой оверхед | **IP-адреса из подсети кончаются** |
| Pod видны из VPC, RDS, on-prem через Direct Connect | Лимит pod на узел зависит от типа инстанса |
| Работают VPC Flow Logs, security groups для pod | Нужен продуманный дизайн CIDR заранее |
| Никакой «магии» при отладке сети | Переделать адресацию потом очень дорого |

## 7.2 Сколько pod влезет на узел: формула ENI

```
max_pods = (число ENI × (IP на ENI − 1)) + 2
```

| Инстанс | ENI | IP на ENI | max pods |
|---|---|---|---|
| `t3.small` | 3 | 4 | 11 |
| `t3.medium` | 3 | 6 | 17 |
| `m6i.large` | 3 | 10 | **29** |
| `m6i.xlarge` | 4 | 15 | 58 |
| `m6i.2xlarge` | 4 | 15 | 58 |
| `m6i.4xlarge` | 8 | 30 | 234 (ограничивается 110 по рекомендации k8s) |

```bash
# точное значение для инстанса
curl -s https://raw.githubusercontent.com/awslabs/amazon-eks-ami/master/templates/shared/runtime/eni-max-pods.txt | grep '^m6i.large'
kubectl describe node <node> | grep -i "pods:"
```

**Вывод, который экономит нервы:** `t3.medium` с 17 pod — это 6-8 системных DaemonSet и почти нет места под приложения. Для реальной работы бери от `large` и выше.

## 7.3 Prefix delegation: больше pod и меньше расход IP

С IPv4 prefix delegation ENI получает не отдельные IP, а **/28-префиксы** (16 адресов).

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_PREFIX_DELEGATION=true
kubectl set env daemonset aws-node -n kube-system WARM_PREFIX_TARGET=1
kubectl rollout status daemonset aws-node -n kube-system
```

Эффект: `m6i.large` поднимается с 29 до 110 pod. Цена: префиксы выделяются целиком, поэтому подсеть должна иметь **непрерывные блоки /28**. На фрагментированной подсети выделение будет падать. Включать лучше сразу на новом кластере, а не на живом заполненном.

## 7.4 Когда IP всё-таки кончились

Симптом в `kubectl describe pod`:

```
Warning  FailedCreatePodSandBox  ... failed to assign an IP address to container
```

и в логах `aws-node`: `InsufficientCidrBlocks` или `no available IP addresses`.

Что делать, по возрастанию сложности:

1. **Освободить**: удалить неиспользуемые ENI, уменьшить `WARM_IP_TARGET`/`WARM_ENI_TARGET` (меньше зарезервированных «тёплых» адресов).
2. **Добавить secondary CIDR в VPC** (например, `100.64.0.0/16` из зарезервированного диапазона CG-NAT) и вынести pod туда через **custom networking**:

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
  subnet: subnet-0aaa111            # подсеть из secondary CIDR
  securityGroups:
    - sg-0cluster
```

При custom networking primary ENI узла больше не даёт IP под pod, поэтому `max_pods` уменьшается: пересчитай и задай явно.

3. **Включить prefix delegation** (см. выше) — это ещё и снижает давление на API EC2.
4. **Перейти на IPv6-кластер**: адресов фактически бесконечно, IPv4 остаётся только для egress через NAT64/DNS64. Ограничение: решается только при создании кластера, и часть legacy-инструментов не готова.
5. В крайнем случае — **альтернативный CNI** (Cilium в overlay-режиме), но тогда теряешь часть интеграций AWS и берёшь на себя сопровождение сети.

## 7.5 CoreDNS и типичные проблемы с DNS

```bash
kubectl -n kube-system get deploy coredns
kubectl -n kube-system logs -l k8s-app=kube-dns --tail=50
```

Что ломается в реальности:

- **CoreDNS на 2 реплики при 200 узлах.** Масштабируй: ориентир — по реплике на каждые 30-50 узлов, либо поставь `cluster-proportional-autoscaler`.
- **`ndots: 5`** в `/etc/resolv.conf` pod: запрос `api.example.com` сначала перебирает несколько внутренних суффиксов. Для чатливых сервисов помогает `dnsConfig` с `ndots: 2` или FQDN с точкой на конце.
- **Throttling DNS на узле**: включи NodeLocal DNSCache при большом объёме запросов.
- **CoreDNS на Spot-узлах**, которые постоянно уезжают. Держи его на On-Demand.

```yaml
      dnsConfig:
        options:
          - name: ndots
            value: "2"
```

## 7.6 Security groups for pods

Иногда нужно, чтобы конкретный pod, а не весь узел, имел доступ к RDS с security group.

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

Требует `ENABLE_POD_ENI=true` у VPC CNI и поддерживаемых инстансов (nitro). Такие pod получают **branch ENI**, и их плотность на узле ограничена сильнее. Используй точечно, а не как общий подход.

## 7.7 Network policies

VPC CNI умеет native network policy (не нужен Calico):

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_NETWORK_POLICY=true
```

```yaml
# deny all входящего в namespace
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
  namespace: demo
spec:
  podSelector: {}
  policyTypes: ["Ingress"]
---
# разрешить только фронту ходить в api на 8080
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

В 2026 году EKS добавил **Admin Policies** и **Application Network Policies**: платформенная команда может задать правила уровня кластера, которые продуктовые команды не переопределят своими NetworkPolicy. Это правильный инструмент для мультитенантного кластера.

Не забудь про egress: без него pod может ходить куда угодно в интернет.

```yaml
# egress: только DNS и внутренние сервисы
spec:
  podSelector: { matchLabels: { app: api } }
  policyTypes: ["Egress"]
  egress:
    - to: [{ namespaceSelector: { matchLabels: { kubernetes.io/metadata.name: kube-system } } }]
      ports: [{ protocol: UDP, port: 53 }, { protocol: TCP, port: 53 }]
    - to: [{ podSelector: { matchLabels: { app: db } } }]
      ports: [{ protocol: TCP, port: 5432 }]
```

## 7.8 VPC endpoints: приватность и экономия на NAT

Узлы постоянно ходят в ECR (образы), S3 (слои образов), EC2 API, STS, CloudWatch. Через NAT Gateway это $0.045 за гигабайт. Через VPC endpoints — дешевле и без выхода в интернет.

Минимальный набор для приватного кластера:

```
Gateway endpoints (бесплатно):  s3, dynamodb
Interface endpoints:            ecr.api, ecr.dkr, ec2, sts, elasticloadbalancing,
                                logs, ssm, ssmmessages, ec2messages, eks, eks-auth,
                                autoscaling, secretsmanager, kms
```

```bash
aws ec2 create-vpc-endpoint --vpc-id vpc-0abc --service-name com.amazonaws.eu-central-1.s3 \
  --route-table-ids rtb-0priv1 rtb-0priv2 rtb-0priv3
```

Interface endpoints стоят ~$0.01/час каждый на AZ, так что считай: при малом трафике NAT может быть дешевле, при большом — endpoints выигрывают с разгромом.

## 7.9 Диагностика сети

```bash
# DNS изнутри кластера
kubectl run -it --rm netshoot --image=nicolaka/netshoot --restart=Never -- bash
  nslookup web.demo.svc.cluster.local
  dig +short api.example.com
  curl -sv http://web.demo.svc.cluster.local

# сколько IP занято в подсети
aws ec2 describe-subnets --subnet-ids subnet-0aaa \
  --query 'Subnets[].{Cidr:CidrBlock,Free:AvailableIpAddressCount}'

# состояние CNI на узле
kubectl -n kube-system logs -l k8s-app=aws-node --tail=100
kubectl -n kube-system exec ds/aws-node -- /app/grpc-health-probe -addr localhost:50051
```

### Вопросы для самопроверки

1. Почему у pod в EKS реальный IP из VPC и какие два последствия из этого вытекают?
2. Как посчитать max pods для `m6i.xlarge` и что меняет prefix delegation?
3. Какие пять вариантов есть, когда в подсети кончились IP-адреса?
4. Зачем нужны security groups for pods и какова их цена?
5. Что дают VPC endpoints кроме приватности?

---

# Модуль 8. Публикация сервисов: ALB, NLB, Gateway API, DNS

## 8.1 Три способа впустить трафик

| Способ | Что создаётся в AWS | Уровень | Когда |
|---|---|---|---|
| `Service type=LoadBalancer` | **NLB** (L4) | TCP/UDP | gRPC, TCP-сервисы, максимальная производительность, статические IP |
| `Ingress` | **ALB** (L7) | HTTP/HTTPS | Веб, маршрутизация по path/host, WAF, Cognito-аутентификация |
| `Gateway API` | ALB или NLB | L4/L7 | Современный стандарт, замена Ingress, ролевое разделение |

Классический ClusterIP остаётся для внутренних вызовов между сервисами.

## 8.2 AWS Load Balancer Controller

Без него `Ingress` в EKS не делает ничего (в Auto Mode он уже встроен).

```bash
# 1. IAM-политика
curl -o iam-policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/main/docs/install/iam_policy.json
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam-policy.json

# 2. ServiceAccount + Pod Identity (или IRSA, см. модуль 10)
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

## 8.3 Ingress с ALB: рабочий пример

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web
  namespace: demo
  annotations:
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip                 # прямо в pod, минуя NodePort
    alb.ingress.kubernetes.io/listen-ports: '[{"HTTP":80},{"HTTPS":443}]'
    alb.ingress.kubernetes.io/ssl-redirect: "443"
    alb.ingress.kubernetes.io/certificate-arn: arn:aws:acm:eu-central-1:111122223333:certificate/xxxx
    alb.ingress.kubernetes.io/healthcheck-path: /healthz
    alb.ingress.kubernetes.io/healthcheck-interval-seconds: "10"
    alb.ingress.kubernetes.io/success-codes: "200"
    alb.ingress.kubernetes.io/load-balancer-attributes: idle_timeout.timeout_seconds=60
    alb.ingress.kubernetes.io/wafv2-acl-arn: arn:aws:wafv2:...:regional/webacl/prod/xxxx
    alb.ingress.kubernetes.io/group.name: shared-prod         # несколько Ingress на один ALB
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
kubectl -n demo describe ingress web            # тут ищи ошибки контроллера
```

Три аннотации, которые нужно знать наизусть:

- **`target-type: ip`** — трафик идёт прямо в pod. Меньше хопов, работает readiness gate, не нужен `NodePort`. Почти всегда правильный выбор.
- **`group.name`** — объединяет Ingress разных namespace в один ALB. Экономит $16+/мес на каждом Ingress и упрощает DNS.
- **`scheme`** — `internet-facing` (в публичные подсети) или `internal` (в приватные). Отсюда требование тегов на подсетях.

Если ALB не создаётся, проверь по порядку: теги `kubernetes.io/role/elb` на подсетях, права IAM-роли контроллера, `ingressClassName: alb`, логи контроллера.

## 8.4 NLB через Service

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

Помни: **cross-zone для NLB по умолчанию выключен** и включение делает трафик между AZ платным. Без него балансировка идёт только внутри зоны, и при неравномерном числе pod по зонам получится перекос.

## 8.5 Gateway API: то, к чему всё идёт

Ingress-NGINX был снят с поддержки апстримом в марте 2026 года, и Gateway API стал основным способом описывать вход в кластер.

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: prod-gw
  namespace: infra
spec:
  gatewayClassName: alb                 # или amazon-vpc-lattice
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

Главное преимущество: **ролевое разделение**. Платформенная команда владеет `Gateway`, продуктовые — своими `HTTPRoute`, и им не нужен доступ к общему Ingress. Плюс канареечные веса, зеркалирование трафика и таймауты — в спецификации, а не в аннотациях.

Если ты сейчас на Ingress-NGINX: план миграции — Gateway API либо ALB Ingress, и это не drop-in замена, закладывай инженерное время.

## 8.6 DNS и сертификаты

```bash
# ExternalDNS: сам создаёт записи в Route 53 по Ingress и Service
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

Сертификаты: **не держи TLS-секреты в кластере**, если можно взять бесплатный сертификат в ACM и терминировать TLS на ALB/NLB. Валидация через DNS, автопродление бесплатно, приватный ключ не покидает AWS.

## 8.7 Деплой без 5xx

Даже при идеальном readinessProbe при деплое можно получить ошибки: ALB ещё держит pod в target group, а Kubernetes его уже удалил. Лечится тремя вещами:

```yaml
# 1. readiness gate: pod считается Ready только когда ALB подтвердил регистрацию
# включается на namespace:
#   kubectl label namespace demo elbv2.k8s.aws/pod-readiness-gate-inject=enabled

# 2. preStop-пауза, чтобы ALB успел вывести pod из ротации
          lifecycle:
            preStop:
              exec:
                command: ["sh", "-c", "sleep 15"]
      terminationGracePeriodSeconds: 60

# 3. стратегия деплоя без просадки
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1
```

```yaml
# и аннотация на Service/Ingress для быстрого дерегистрации
    alb.ingress.kubernetes.io/target-group-attributes: deregistration_delay.timeout_seconds=30
```

## 8.8 Сколько это стоит

| Ресурс | Цена |
|---|---|
| ALB | ~$0.0225/час (≈$16/мес) + LCU (≈$0.008/LCU-час) |
| NLB | ~$0.0225/час + NLCU |
| Каждый Ingress без `group.name` | **свой ALB, свои $16/мес** |
| Cross-zone трафик через LB | $0.01/ГБ |

Отсюда правило: **объединяй Ingress через `group.name`**, не создавай по балансировщику на сервис.

### Практика

1. Поставь Load Balancer Controller, опубликуй два сервиса через один ALB с помощью `group.name`.
2. Добавь ACM-сертификат и `ssl-redirect`, проверь `curl -I http://...` → 301.
3. Сделай то же через Gateway API с канареечными весами 90/10 и убедись в распределении запросов.
4. Устрой деплой под нагрузкой (`hey -z 60s`) сначала без preStop и readiness gate, потом с ними, сравни число 5xx.
5. Подключи ExternalDNS и проверь появление записи в Route 53.

---

# Модуль 9. Хранилище: EBS, EFS, S3 и CSI-драйверы

## 9.1 Что выбрать

| Вариант | Тип доступа | AZ | Задержка | Цена (ориентир) | Для чего |
|---|---|---|---|---|---|
| **EBS (gp3)** | ReadWriteOnce, один pod | **Только одна AZ** | Очень низкая | ~$0.08/ГБ-мес | БД, Kafka, Elasticsearch, любой StatefulSet |
| **EFS** | ReadWriteMany, много pod и AZ | Регион | Средняя | ~$0.30/ГБ-мес (+ throughput) | Общие файлы, uploads, legacy с shared-диском |
| **Mountpoint for S3** | Много pod, чтение и запись-append | Регион | Высокая | ~$0.023/ГБ-мес | Датасеты, модели, артефакты, логи |
| **FSx for Lustre** | ReadWriteMany, высокая полоса | AZ | Низкая | Дорого | HPC, ML-тренировки |
| **emptyDir / локальный NVMe** | Только pod/узел | Узел | Минимальная | Внутри цены инстанса | Кэш, временные файлы, scratch |

**Правило №1 про EBS:** диск живёт в одной зоне доступности. Pod с этим PVC может быть запланирован **только в эту AZ**. Отсюда все истории про «pod висит в Pending, а узлы есть».

## 9.2 EBS CSI: StorageClass и PVC

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
volumeBindingMode: WaitForFirstConsumer      # критично: диск создаётся в AZ pod, а не наугад
allowVolumeExpansion: true
reclaimPolicy: Delete                        # для прода часто Retain
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

**`volumeBindingMode: WaitForFirstConsumer` — самая важная строка модуля.** С `Immediate` диск создастся в случайной AZ, а pod потом может не найти там узла.

Расширение диска на живую:

```bash
kubectl -n demo patch pvc data -p '{"spec":{"resources":{"requests":{"storage":"50Gi"}}}}'
kubectl -n demo get pvc data -w      # FileSystemResizePending → Bound
```

Уменьшить нельзя — только создать новый PVC и скопировать данные.

## 9.3 StatefulSet и хранилище

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

Что нужно помнить:

- каждая реплика получает **свой** PVC, привязанный к своей AZ навсегда;
- при удалении StatefulSet PVC **остаются** (это защита данных, но и источник забытых счетов);
- с Kubernetes 1.32+ есть автоматическая очистка PVC, созданных StatefulSet, при удалении;
- узел с таким pod нельзя просто заменить в другой AZ: Karpenter должен получить требование по зоне.

**И главный вопрос:** нужна ли тебе база в Kubernetes? В AWS есть RDS, Aurora, ElastiCache, MSK, OpenSearch. Держать в кластере stateful-системы стоит тогда, когда есть зрелый оператор и команда, которая умеет его обслуживать. Иначе managed-сервис дешевле по совокупным затратам, даже если по прайсу дороже.

## 9.4 EFS: общий доступ из нескольких AZ

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
  provisioningMode: efs-ap            # access point на каждый PVC
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
  resources: { requests: { storage: 5Gi } }   # для EFS это формальность, он эластичный
```

EFS нужен security group, разрешающий NFS (2049) с узлов, и mount target в каждой AZ. Помни про цену: EFS Standard в 3-4 раза дороже EBS за гигабайт, поэтому включай Lifecycle Management (перенос в Infrequent Access).

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

Это не файловая система общего назначения: нет частичной перезаписи файла, нет `rename` в обычном смысле, и задержка высокая. Идеально для «прочитать датасет или модель», плохо для «БД или логи с fsync».

## 9.6 Снапшоты и бэкапы

```bash
# CSI snapshotter (в EKS его надо поставить отдельно)
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

Для полноценных бэкапов кластера (манифесты + PV) используй **Velero** или **AWS Backup**:

```bash
velero install --provider aws --bucket my-velero-bucket \
  --backup-location-config region=eu-central-1 \
  --snapshot-location-config region=eu-central-1 \
  --plugins velero/velero-plugin-for-aws:v1.10.0

velero backup create prod-daily --include-namespaces prod --wait
velero restore create --from-backup prod-daily
```

**etcd бэкапит AWS, твои данные — нет.** Это разграничение стоит проговорить на собеседовании.

## 9.7 Типовые проблемы с хранилищем

| Симптом | Причина | Решение |
|---|---|---|
| Pod `Pending`, в Events `volume node affinity conflict` | PVC в одной AZ, свободные узлы в другой | `WaitForFirstConsumer`, узлы во всех AZ, topology в NodePool |
| PVC вечно `Pending` | Нет CSI-драйвера, нет прав у его роли, нет StorageClass | `kubectl get sc`, логи `ebs-csi-controller` |
| `Multi-Attach error` | Пытаются подключить EBS к двум pod | EBS это RWO; нужен EFS или один pod |
| Диск не расширяется | `allowVolumeExpansion: false` | Поправь StorageClass (уже созданный PV придётся пересоздать) |
| Забытые тома в счёте | `reclaimPolicy: Retain` и удалённые namespace | `aws ec2 describe-volumes --filters Name=status,Values=available` |

### Практика

1. Создай `StorageClass gp3` с `WaitForFirstConsumer`, подними StatefulSet Postgres на 3 реплики, проверь, в каких AZ оказались диски.
2. Специально поставь `volumeBindingMode: Immediate`, удали узлы в одной AZ и получи `volume node affinity conflict`.
3. Расширь PVC с 20 до 40 ГБ без перезапуска pod.
4. Сделай VolumeSnapshot, удали PVC и восстанови данные из снапшота.
5. Подключи EFS и запусти два pod в разных AZ, которые пишут в один файл.

---

# Модуль 10. Доступ к AWS из pod: Pod Identity, IRSA, секреты

## 10.1 Три способа дать pod права в AWS

| Способ | Как работает | Статус |
|---|---|---|
| **Роль узла (instance profile)** | Pod через IMDS берёт креденшелы узла | **Антипаттерн**: любой pod получает все права узла |
| **IRSA** (IAM Roles for Service Accounts) | OIDC-провайдер кластера, `AssumeRoleWithWebIdentity`, аннотация на ServiceAccount | Работает, зрелый, нужен для кросс-аккаунтных сценариев |
| **EKS Pod Identity** | Агент-DaemonSet и association на уровне EKS API | **Рекомендуемый по умолчанию** с 2023 года |

## 10.2 EKS Pod Identity: современный путь

```bash
aws eks create-addon --cluster-name demo --addon-name eks-pod-identity-agent
```

Роль с trust policy на сервис `pods.eks.amazonaws.com`:

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

# связать роль с ServiceAccount
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
# ничего аннотировать не нужно, в отличие от IRSA
```

Проверка из pod:

```bash
kubectl -n demo run aws-cli --rm -it --image=public.ecr.aws/aws-cli/aws-cli \
  --overrides='{"spec":{"serviceAccountName":"app-sa"}}' -- sts get-caller-identity
```

Почему Pod Identity лучше IRSA:

- одна роль работает в **нескольких кластерах**, не нужно перечислять OIDC-issuer в trust policy;
- не нужен OIDC-провайдер и его ARN в каждой роли;
- нет аннотаций на ServiceAccount: связь живёт в EKS API и видна через `aws eks list-pod-identity-associations`;
- поддерживает **session policies** — можно сузить права конкретной связи без создания новой роли;
- session tags: в политиках доступны `eks-cluster-name`, `kubernetes-namespace`, `kubernetes-service-account`.

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

## 10.3 IRSA: когда всё ещё нужен

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

Trust policy IRSA привязана к конкретному OIDC-провайдеру и `sub`:

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

IRSA остаётся нужен: для Fargate-pod (там Pod Identity Agent как DaemonSet не запустить), для доступа из кластера в **другой AWS-аккаунт** и для совместимости со старыми чартами.

## 10.4 Блокируем доступ pod к роли узла

Пока pod может дойти до IMDS, он может украсть права узла. Закрываем:

```yaml
# в EC2NodeClass (Karpenter) или launch template
  metadataOptions:
    httpTokens: required            # IMDSv2
    httpPutResponseHopLimit: 1      # запрос из контейнера не дойдёт
    httpEndpoint: enabled
```

И проверяем, что из pod IMDS не отвечает:

```bash
kubectl run t --rm -it --image=curlimages/curl -- \
  curl -s --max-time 3 http://169.254.169.254/latest/meta-data/iam/security-credentials/
# ожидаем таймаут
```

## 10.5 Секреты: где хранить

| Вариант | Плюсы | Минусы |
|---|---|---|
| Kubernetes Secret | Просто, работает везде | base64, не шифрование; лежит в etcd; в Git попадать не должен |
| **Secrets Store CSI + AWS provider** | Секрет монтируется файлом, ротация, ничего в etcd | Нужен драйвер, приложение читает файл |
| **External Secrets Operator** | Секреты из Secrets Manager/SSM синхронизируются в K8s Secret | Секрет всё же появляется в etcd |
| Переменные окружения из Secrets Manager в коде | Полный контроль | Нужна библиотека AWS SDK в приложении |

Включи шифрование etcd своим KMS-ключом (envelope encryption) при создании кластера:

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
# в pod
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

## 10.6 Чек-лист доступа к AWS

- ни одного `AWS_ACCESS_KEY_ID` в манифестах, чартах и переменных окружения;
- Pod Identity (или IRSA) на каждый сервис, которому нужен AWS, **со своей ролью**, а не одной общей;
- политики по принципу минимума: конкретные действия, конкретные ARN, условия по namespace;
- `httpPutResponseHopLimit: 1` и IMDSv2 на всех узлах;
- шифрование секретов в etcd своим KMS-ключом;
- `automountServiceAccountToken: false` для pod, которые не обращаются к API Kubernetes;
- ротация секретов в Secrets Manager и `enableSecretRotation` в CSI.

### Практика

1. Создай роль и Pod Identity association, из pod прочитай объект из S3 без ключей.
2. Добавь в политику условие по `aws:PrincipalTag/kubernetes-namespace` и убедись, что pod из другого namespace получает `AccessDenied`.
3. Заблокируй IMDS (`hopLimit: 1`) и проверь, что pod больше не видит креденшелы узла.
4. Подключи Secrets Store CSI и смонтируй секрет из Secrets Manager файлом.
5. Сравни: то же самое через IRSA. Запиши, чем отличались trust policy.

---
# Модуль 11. Аддоны EKS и их жизненный цикл

## 11.1 Что такое EKS add-on

Аддон — это компонент кластера, версией которого управляет EKS API, а не твой Helm. AWS собирает, тестирует на совместимость с версией Kubernetes, патчит CVE и умеет обновлять без твоих чартов.

```bash
# что вообще есть
aws eks describe-addon-versions --kubernetes-version 1.36 \
  --query 'addons[].addonName' --output table

# что стоит в кластере
aws eks list-addons --cluster-name demo
aws eks describe-addon --cluster-name demo --addon-name vpc-cni
```

| Аддон | Обязателен | Что делает |
|---|---|---|
| `vpc-cni` | Да | Сеть pod |
| `coredns` | Да | DNS |
| `kube-proxy` | Да | Сервисные правила |
| `eks-pod-identity-agent` | Практически да | Креденшелы AWS для pod |
| `aws-ebs-csi-driver` | Если есть PVC | Диски EBS |
| `aws-efs-csi-driver` | По необходимости | Общие файловые тома |
| `metrics-server` | Практически да | `kubectl top`, HPA |
| `amazon-cloudwatch-observability` | Рекомендуется | Container Insights, логи, агент |
| `aws-mountpoint-s3-csi-driver` | По необходимости | S3 как том |
| `snapshot-controller` | Если нужны снапшоты | VolumeSnapshot |
| `adot` (OpenTelemetry) | По необходимости | Метрики и трейсы |
| `aws-guardduty-agent` | Рекомендуется в проде | Runtime-мониторинг угроз |
| `cert-manager`, `external-dns`, Argo CD и другие | Marketplace-аддоны | Часть уже доступна как EKS add-on |

## 11.2 Установка и конфигурация

```bash
aws eks create-addon --cluster-name demo --addon-name vpc-cni \
  --addon-version v1.20.0-eksbuild.1 \
  --resolve-conflicts OVERWRITE \
  --pod-identity-associations 'serviceAccount=aws-node,roleArn=arn:aws:iam::111122223333:role/VpcCniRole'
```

Конфигурация аддона задаётся JSON, а не `kubectl set env` (иначе обновление аддона перезапишет твои правки):

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
# посмотреть допустимую схему конфигурации
aws eks describe-addon-configuration --addon-name vpc-cni \
  --addon-version v1.20.0-eksbuild.1 --query configurationSchema --output text | jq .
```

`--resolve-conflicts`:

- `NONE` — упасть при конфликте (безопасно, но требует ручной работы);
- `OVERWRITE` — перезаписать твои ручные правки значениями AWS;
- `PRESERVE` — сохранить твои правки полей, которые ты менял.

## 11.3 Порядок обновления аддонов

Правильная последовательность при апгрейде кластера:

```
1. Обновить control plane (1.35 → 1.36)
2. Обновить аддоны до версий, совместимых с 1.36
   порядок: kube-proxy → vpc-cni → coredns → CSI → остальные
3. Обновить узлы (AMI под 1.36)
4. Проверить приложения
```

`kube-proxy` должен быть не новее control plane и не старше узлов на два минора. `vpc-cni` обновляй до узлов: новая версия CNI на старом ядре обычно нормальна, старая CNI на новых узлах — нет.

```bash
# какие версии совместимы
aws eks describe-addon-versions --kubernetes-version 1.36 --addon-name coredns \
  --query 'addons[].addonVersions[].{v:addonVersion,default:compatibilities[0].defaultVersion}'

aws eks update-addon --cluster-name demo --addon-name coredns \
  --addon-version v1.12.4-eksbuild.1 --resolve-conflicts PRESERVE

aws eks wait addon-active --cluster-name demo --addon-name coredns
```

## 11.4 Аддон или Helm: как выбрать

| Бери EKS add-on | Бери Helm |
|---|---|
| Компонент в списке аддонов | Нужна конкретная версия, которой нет в аддонах |
| Хочешь, чтобы AWS следил за CVE и совместимостью | Нужны тонкие настройки чарта, которых нет в схеме |
| Хочешь видеть версии в одном месте (`list-addons`) | Компонент — часть твоего GitOps-репозитория |
| Не хочешь хранить values в Git | Нужен свой образ или патчи |

Практичный компромисс: базовая инфраструктура (CNI, CoreDNS, kube-proxy, CSI, Pod Identity, metrics-server) — аддонами через Terraform; всё прикладное (контроллеры, Argo, мониторинг) — Helm через GitOps.

## 11.5 EKS Capabilities: управляемая платформа

С конца 2025 года AWS предлагает **EKS Capabilities** — полностью управляемые платформенные компоненты:

- **Argo CD** — continuous delivery, AWS отвечает за апгрейды и масштабирование;
- **ACK (AWS Controllers for Kubernetes)** — создание AWS-ресурсов (S3, RDS, SQS) через Kubernetes-манифесты;
- **kro (Kubernetes Resource Orchestrator)** — сборка переиспользуемых шаблонов инфраструктуры как своих API.

Это удобно, если платформенная команда маленькая: не надо самим держать Argo CD в HA. Минус — это дополнительная строка в счёте и меньше контроля над версиями. Включай осознанно и держи фича-флаг в IaC со значением по умолчанию `false`, чтобы не включить случайно.

## 11.6 Terraform для аддонов

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

Фиксируй версии аддонов явно (`addon_version`), а не `most_recent = true`, если хочешь предсказуемых апгрейдов в проде.

### Вопросы для самопроверки

1. Чем EKS add-on отличается от того же компонента, поставленного Helm?
2. Что сделает `--resolve-conflicts OVERWRITE` с твоими `kubectl set env` правками?
3. В каком порядке обновлять control plane, аддоны и узлы?
4. Зачем `metrics-server`, если он не обязателен?
5. Когда стоит брать EKS Capabilities вместо своего Argo CD?

---

# Модуль 12. Наблюдаемость: логи, метрики, трейсы, алерты

## 12.1 Четыре потока данных

```
Логи control plane      → CloudWatch Logs   (по умолчанию ВЫКЛЮЧЕНЫ)
Логи приложений         → CloudWatch / OpenSearch / Loki
Метрики                 → CloudWatch Container Insights / Prometheus (AMP)
Трейсы                  → X-Ray / Tempo / Jaeger через OpenTelemetry
События Kubernetes      → отдельный поток, часто забывают, а это золото при разборе аварий
```

## 12.2 Логи control plane: включи первым делом

```bash
aws eks update-cluster-config --name demo \
  --logging '{"clusterLogging":[{"types":["api","audit","authenticator","controllerManager","scheduler"],"enabled":true}]}'
```

| Тип | Зачем нужен |
|---|---|
| `api` | Запросы к apiserver, ошибки, медленные запросы |
| `audit` | Кто что сделал: главный источник при инциденте безопасности |
| `authenticator` | Почему кто-то получил `Unauthorized` |
| `controllerManager` | Почему не создаются объекты, проблемы контроллеров |
| `scheduler` | Почему pod не размещается |

Аудит-логи объёмные и стоят денег в CloudWatch. Практика: включи `api`, `audit`, `authenticator` всегда, поставь retention 30-90 дней и выгрузку в S3 для долгого хранения.

Полезный запрос в CloudWatch Logs Insights — «кто удалил Deployment»:

```
fields @timestamp, user.username, verb, objectRef.resource, objectRef.name, responseStatus.code
| filter verb = "delete" and objectRef.resource = "deployments"
| sort @timestamp desc
| limit 50
```

Кто получает 403:

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

Что получаешь: метрики узлов, pod и контейнеров, логи контейнеров в CloudWatch Logs, карту сервисов, при включении — Application Signals (APM). Платишь за метрики и объём логов; на большом кластере это ощутимо, поэтому фильтруй, что отправляешь.

## 12.4 Prometheus и Grafana

Два пути:

**Managed:** Amazon Managed Service for Prometheus (AMP) + Amazon Managed Grafana (AMG). Не надо думать о хранении и HA.

```bash
aws amp create-workspace --alias demo
# сбор метрик через ADOT-коллектор или agentless scraper AMP
aws amp create-scraper \
  --source eksConfiguration="{clusterArn=$CLUSTER_ARN,securityGroupIds=[sg-0x],subnetIds=[subnet-0a]}" \
  --destination ampConfiguration="{workspaceArn=$AMP_ARN}" \
  --scrape-configuration configurationBlob=$(base64 -w0 scrape.yaml)
```

**Self-hosted:** kube-prometheus-stack в кластере.

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install kps prometheus-community/kube-prometheus-stack -n monitoring --create-namespace \
  --set prometheus.prometheusSpec.retention=15d \
  --set prometheus.prometheusSpec.storageSpec.volumeClaimTemplate.spec.storageClassName=gp3 \
  --set prometheus.prometheusSpec.storageSpec.volumeClaimTemplate.spec.resources.requests.storage=100Gi \
  --set grafana.enabled=true
```

Дешевле в деньгах, дороже в эксплуатации: Prometheus сам становится stateful-сервисом, за которым надо следить.

## 12.5 Что алертить (минимальный набор)

| Алерт | Условие | Почему важно |
|---|---|---|
| Узел `NotReady` | `kube_node_status_condition{condition="Ready",status="true"} == 0` 5 минут | Потеря capacity |
| Pod в `CrashLoopBackOff` | `rate(kube_pod_container_status_restarts_total[15m]) > 0` | Приложение падает |
| Pod `Pending` дольше 10 минут | `kube_pod_status_phase{phase="Pending"} == 1` | Нет узлов, нет IP, нет PVC |
| Мало свободных IP в подсети | CloudWatch по `AvailableIpAddressCount` < 10% | Скоро pod перестанут стартовать |
| Заполнение диска узла | `node_filesystem_avail_bytes / node_filesystem_size_bytes < 0.15` | `DiskPressure` и вытеснение pod |
| Ошибки apiserver 5xx | `apiserver_request_total{code=~"5.."}` растёт | Проблемы control plane или webhook |
| Задержка etcd / apiserver | `apiserver_request_duration_seconds` p99 | Перегруженный control plane |
| HPA на максимуме | `kube_horizontalpodautoscaler_status_current_replicas == spec_max_replicas` | Нагрузка выше расчётной |
| Приближение конца поддержки версии | EKS Health event | $0.60/час вместо $0.10 |
| Сертификат ACM истекает | CloudWatch по ACM | Падение HTTPS |
| Просроченный `expireAfter` узлов не работает | Возраст узла > лимита | Патчи ОС не применяются |
| Рост счёта | AWS Budgets на кластерный тег | FinOps |

## 12.6 Трейсы через OpenTelemetry

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

## 12.7 Повседневные команды дежурного

```bash
# общая картина
kubectl get nodes -o wide
kubectl get pods -A --field-selector=status.phase!=Running
kubectl get events -A --sort-by='.lastTimestamp' | tail -40
kubectl top nodes && kubectl top pods -A --sort-by=cpu

# конкретный pod
kubectl -n prod describe pod <pod>
kubectl -n prod logs <pod> --previous --tail=200     # логи упавшего контейнера
kubectl -n prod logs -l app=api --all-containers -f --max-log-requests=20
stern -n prod api                                     # удобнее для нескольких pod

# узел
kubectl describe node <node> | sed -n '/Conditions/,/Events/p'
kubectl get pods -A -o wide --field-selector spec.nodeName=<node>

# что жрёт ресурсы
kubectl top pods -A --sort-by=memory | head -20

# отладка на узле без SSH
kubectl debug node/<node> -it --image=public.ecr.aws/amazonlinux/amazonlinux:2023
kubectl debug -it <pod> --image=nicolaka/netshoot --target=<container>

# состояние EKS-ресурсов
aws eks describe-cluster --name demo --query 'cluster.{status:status,version:version,health:health}'
aws eks list-insights --cluster-name demo
```

## 12.8 EKS Dashboard и Health

В консоли EKS есть сводный дашборд по всем кластерам аккаунта или организации: версии, срок поддержки, аддоны, insights. Плюс AWS Health рассылает события о конце поддержки версий. Подпишись на них через EventBridge → Slack: это дешёвая страховка от внезапного $0.60/час.

```json
{
  "source": ["aws.health"],
  "detail": { "service": ["EKS"], "eventTypeCategory": ["scheduledChange"] }
}
```

### Практика

1. Включи все пять типов логов control plane, сделай `kubectl delete deployment` и найди себя в аудит-логе через Logs Insights.
2. Поставь kube-prometheus-stack, открой Grafana, найди дашборд по узлам.
3. Настрой алерт на pod в `Pending` дольше 10 минут и вызови его искусственно (запроси 100 CPU).
4. Установи ADOT, отправь трейс из тестового приложения, найди его в X-Ray.
5. Настрой правило EventBridge на события AWS Health про EKS.

---

# Модуль 13. Безопасность EKS: от PSS до GuardDuty

## 13.1 Карта угроз и ответов

| Угроза | Ответ в EKS |
|---|---|
| Кто угодно достучался до apiserver | Приватный endpoint, `publicAccessCidrs`, IAM |
| Слишком широкие права человека | Access entries с namespace-scope, отказ от `system:masters` |
| Pod получил права узла | IMDSv2 + `hopLimit: 1`, Pod Identity |
| Контейнер с root и privileged | Pod Security Standards, admission-политики |
| Свободный трафик между namespace | NetworkPolicy, Admin Policies |
| Уязвимый образ | Сканирование в ECR, подпись образов, обновления базовых образов |
| Секреты в открытом виде | KMS-шифрование etcd, Secrets Manager, CSI |
| Компромисс в рантайме | GuardDuty EKS Runtime Monitoring |
| Нет следов действий | Аудит-логи control plane, CloudTrail |
| Дрейф конфигурации | GitOps, политики как код (Kyverno/OPA) |

## 13.2 Pod Security Standards

`PodSecurityPolicy` удалён давно; сейчас работает встроенный Pod Security Admission на уровне namespace.

```bash
kubectl label namespace prod \
  pod-security.kubernetes.io/enforce=restricted \
  pod-security.kubernetes.io/enforce-version=v1.36 \
  pod-security.kubernetes.io/audit=restricted \
  pod-security.kubernetes.io/warn=restricted
```

| Уровень | Что разрешено |
|---|---|
| `privileged` | Всё (только для системных namespace) |
| `baseline` | Запрещены явно опасные вещи: privileged, hostNetwork, hostPID |
| `restricted` | Плюс обязательны non-root, `readOnlyRootFilesystem`, drop capabilities, seccomp |

Pod, который проходит `restricted`:

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

Начинай с `warn` и `audit`, смотри, что сломается, и только потом включай `enforce`.

## 13.3 Политики как код

PSS не покрывает всё: «запретить образы не из нашего ECR», «требовать labels», «требовать requests». Для этого Kyverno или OPA Gatekeeper.

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
        message: "Образы только из нашего ECR"
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
        message: "Нужны requests.cpu и requests.memory"
        pattern:
          spec:
            containers:
              - resources:
                  requests:
                    cpu: "?*"
                    memory: "?*"
```

Осторожно: admission-webhook — это компонент на критическом пути создания pod. Если он упадёт и настроен как `failurePolicy: Fail`, кластер перестанет принимать деплои. Держи его в HA и исключай `kube-system`.

## 13.4 Образы: ECR и сканирование

```bash
# репозиторий с неизменяемыми тегами и сканированием
aws ecr create-repository --repository-name app \
  --image-tag-mutability IMMUTABLE \
  --image-scanning-configuration scanOnPush=true \
  --encryption-configuration encryptionType=KMS

# enhanced scanning (Inspector): постоянный пересмотр найденных CVE
aws ecr put-registry-scanning-configuration --scan-type ENHANCED \
  --rules '[{"scanFrequency":"CONTINUOUS_SCAN","repositoryFilters":[{"filter":"*","filterType":"WILDCARD"}]}]'

# lifecycle policy: не платить за 500 старых образов
aws ecr put-lifecycle-policy --repository-name app --lifecycle-policy-text '{
  "rules":[{"rulePriority":1,"description":"keep last 30","selection":{"tagStatus":"any","countType":"imageCountMoreThan","countNumber":30},"action":{"type":"expire"}}]}'
```

Правила гигиены образов:

- **никогда `:latest` в продакшене**, только тег + дайджест `@sha256:`;
- `IMMUTABLE` теги, чтобы один и тот же тег не подменился;
- минимальные базовые образы (distroless, `alpine`, `amazonlinux-minimal`);
- сборка без секретов в слоях (`--secret`, multi-stage);
- подпись и проверка (`cosign` + Kyverno `verifyImages`).

## 13.5 GuardDuty EKS Protection

```bash
aws guardduty update-detector --detector-id <id> \
  --features '[{"Name":"EKS_AUDIT_LOGS","Status":"ENABLED"},
               {"Name":"RUNTIME_MONITORING","Status":"ENABLED",
                "AdditionalConfiguration":[{"Name":"EKS_ADDON_MANAGEMENT","Status":"ENABLED"}]}]'
```

Даёт два уровня: анализ аудит-логов (подозрительные API-вызовы, анонимный доступ, эскалация прав) и runtime-агент на узлах (запуск шелла в контейнере, майнеры, обращения к подозрительным доменам). В проде включай оба.

## 13.6 Приватный кластер и сетевой периметр

```bash
aws eks update-cluster-config --name prod \
  --resources-vpc-config endpointPublicAccess=false,endpointPrivateAccess=true
```

Чек-лист перед переключением: VPN или bastion, CI-раннеры в VPC, VPC endpoints для ECR/S3/STS/EKS/logs, план восстановления доступа.

Дополнительно:

- узлы **без публичных IP**, только приватные подсети;
- security group узлов: входящий трафик только от cluster SG и балансировщиков;
- `default deny` NetworkPolicy в каждом прикладном namespace;
- egress-фильтрация для чувствительных сервисов.

## 13.7 Multi-tenancy: изоляция команд в одном кластере

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

Плюс: access entry с `type=namespace`, `default deny` NetworkPolicy, отдельные NodePool с taint для «шумных» команд, и лимит на балансировщики (иначе одна команда создаст 30 ALB).

Честная оговорка: **namespace это не граница безопасности уровня VM.** Для враждебной мультитенантности нужны отдельные кластеры, Fargate или узлы с изоляцией по командам.

## 13.8 Чек-лист безопасности продакшена

- `authenticationMode=API`, никаких IAM-пользователей, только SSO-роли;
- приватный endpoint (или жёсткий `publicAccessCidrs`);
- аудит-логи включены, retention задан, выгрузка в S3;
- шифрование секретов KMS, шифрование EBS-томов узлов;
- IMDSv2 + `hopLimit: 1`;
- Pod Identity на каждый сервис, минимальные политики, условия по namespace;
- PSS `restricted` во всех прикладных namespace;
- NetworkPolicy `default deny` ingress и egress;
- ECR: `IMMUTABLE`, enhanced scanning, запрет образов извне через Kyverno;
- GuardDuty EKS Protection (аудит + runtime);
- регулярное обновление версии Kubernetes (см. модуль 15);
- бэкапы приложений и PV (Velero / AWS Backup), проверенное восстановление;
- отдельные кластеры для prod и non-prod.

### Вопросы для самопроверки

1. Почему `hopLimit: 1` важнее, чем кажется?
2. Чем `restricted` отличается от `baseline` в PSS?
3. Что случится, если admission-webhook с `failurePolicy: Fail` упадёт?
4. Является ли namespace границей безопасности? Почему нет?
5. Какие два режима даёт GuardDuty EKS Protection?

---

# Модуль 14. CI/CD и GitOps: ECR, Helm, Argo CD

## 14.1 Push vs Pull: две модели доставки

```
Push (обычный CI):
  git push → CI собирает образ → CI имеет доступ в кластер → kubectl apply / helm upgrade
  плюс: просто, привычно
  минус: CI нужны права в кластере, дрейф между Git и кластером незаметен

Pull (GitOps):
  git push → CI собирает образ и меняет тег в манифестах → Argo CD/Flux в кластере сам подтягивает
  плюс: кластеру не нужны внешние доступы, дрейф виден и лечится автоматически
  минус: ещё один компонент, нужно приучить команду к «Git как источник истины»
```

Для одного сервиса хватит push. Для платформы с десятками сервисов и несколькими кластерами правильный ответ — GitOps.

## 14.2 Сборка и публикация в ECR

```bash
ACCOUNT=111122223333
REGION=eu-central-1
REPO=$ACCOUNT.dkr.ecr.$REGION.amazonaws.com/app

aws ecr get-login-password --region $REGION | docker login --username AWS --password-stdin $ACCOUNT.dkr.ecr.$REGION.amazonaws.com

docker buildx build --platform linux/amd64,linux/arm64 \
  -t $REPO:$(git rev-parse --short HEAD) \
  --provenance=true --sbom=true --push .
```

GitHub Actions без статических ключей (OIDC → IAM-роль):

```yaml
name: build-and-deploy
on:
  push: { branches: [main] }

permissions:
  id-token: write        # без этого OIDC не работает
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

Обрати внимание: workflow **не имеет доступа в кластер вообще**. Он только пушит образ и меняет тег в Git. Деплой делает Argo CD.

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
      selfHeal: true            # правки руками в кластере откатываются
    syncOptions:
      - CreateNamespace=true
      - ApplyOutOfSyncOnly=true
    retry:
      limit: 5
      backoff: { duration: 10s, factor: 2, maxDuration: 3m }
```

Для нескольких окружений и кластеров — `ApplicationSet`:

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

## 14.4 Helm: структура чарта приложения

```
charts/web/
  Chart.yaml
  values.yaml          # значения по умолчанию
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
  tag: "a1b2c3d"                 # меняет CI, а не человек
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
helm diff upgrade web charts/web -f charts/web/values-prod.yaml    # плагин helm-diff, обязателен
```

## 14.5 Канареечные и blue-green деплои

```yaml
# Argo Rollouts: канарейка с проверкой метрик
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

Это уже уровень зрелой платформы: деплой откатывается сам, если доля ошибок вырастет.

## 14.6 Проверки в CI, которые экономят инциденты

```bash
# валидация манифестов против схемы кластера
kubeconform -strict -kubernetes-version 1.36.0 -summary manifests/

# статический анализ безопасности
trivy config .
trivy image --severity HIGH,CRITICAL --exit-code 1 $IMAGE

# политики как код ещё до кластера
kyverno apply policies/ --resource manifests/

# проверка на удаление ресурсов
helm diff upgrade web charts/web -f values-prod.yaml | grep -E '^-' | head
```

## 14.7 Антипаттерны доставки

- **`kubectl apply` руками в продакшен.** Через месяц никто не знает, что в кластере.
- **CI-роль с `cluster-admin`** на все кластеры. Взлом CI = взлом всего.
- **`:latest` и `imagePullPolicy: Always`** как стратегия версионирования. Откатиться некуда.
- **Секреты в values.yaml** в Git. Даже приватный репозиторий это не секрет-хранилище.
- **Один Git-репозиторий на всё** без структуры окружений: невозможно раскатывать поэтапно.
- **Отсутствие `helm diff`** перед апгрейдом: сюрпризы вроде «удалился PVC».

### Практика

1. Настрой GitHub Actions с OIDC-ролью, собери и запушь образ в ECR без статических ключей.
2. Поставь Argo CD, заведи Application на свой чарт, включи `selfHeal` и попробуй изменить Deployment руками — посмотри, как откатится.
3. Сделай ApplicationSet на два окружения с разным числом реплик.
4. Добавь в CI `trivy image --exit-code 1` и убедись, что уязвимый образ не проходит.
5. Настрой Argo Rollouts с канарейкой 10% и анализом по Prometheus.

---
# Модуль 15. Обновление версий: lifecycle, insights, стратегия

## 15.1 Жизненный цикл версии EKS

```
Релиз в EKS  ──14 месяцев──>  конец стандартной поддержки ($0.10/час)
                                  |
                                  +──12 месяцев──>  конец extended support ($0.60/час)
                                                        |
                                                        +─> AWS обновит кластер ПРИНУДИТЕЛЬНО
```

Итого версия живёт **26 месяцев**. На сентябрь 2026 картина такая:

| Версия | Релиз в EKS | Статус |
|---|---|---|
| **1.36** | июнь 2026 | Стандартная поддержка |
| **1.35** | январь 2026 | Стандартная поддержка |
| **1.34** | октябрь 2025 | Стандартная поддержка |
| 1.33 | май 2025 | **Extended support** (закончилась стандартная 29 июля 2026) — $0.60/час |
| 1.32 и ниже | ранее | Extended support или уже нет поддержки |

Один кластер в extended support — это **+$4 380 в год** по сравнению со стандартной поддержкой. За тот же кластер. Это самый дорогой технический долг в EKS.

**Практическое правило:** обновляйся раз в 6-9 месяцев, то есть примерно раз в 1-2 минора. Тогда ты всегда в стандартной поддержке и никогда не догоняешь три версии разом.

## 15.2 Cluster insights: проверка перед обновлением

EKS сам анализирует кластер и говорит, что сломается.

```bash
aws eks list-insights --cluster-name demo
aws eks describe-insight --cluster-name demo --id <insight-id>

# только проблемы
aws eks list-insights --cluster-name demo \
  --query 'insights[?insightStatus.status!=`PASSING`].{name:name,status:insightStatus.status,reason:insightStatus.reason}'
```

Insights ловят: использование удалённых API (`policy/v1beta1`, старые CRD), несовместимые версии аддонов, отсутствие EKS-прав, проблемы с kube-proxy, устаревшие AMI.

Дополнительно проверь удалённые API руками:

```bash
# что в кластере ещё обращается к устаревшим API (в аудит-логе)
# CloudWatch Logs Insights по /aws/eks/<cluster>/cluster
fields @timestamp, userAgent, requestURI
| filter requestURI like /v1beta1/
| stats count() by userAgent, requestURI

# статический анализ манифестов
pluto detect-files -d ./manifests --target-versions k8s=v1.36.0
kubent                                   # kube-no-trouble
```

## 15.3 Порядок обновления

```bash
# 0. Бэкап: манифесты и PV
velero backup create pre-upgrade-1-36 --include-namespaces prod --wait

# 1. Проверка insights и совместимости аддонов
aws eks list-insights --cluster-name demo

# 2. Control plane (один минор за раз, откатиться НЕЛЬЗЯ)
aws eks update-cluster-version --name demo --kubernetes-version 1.36
aws eks wait cluster-active --name demo        # 10-25 минут

# 3. Аддоны
for a in kube-proxy vpc-cni coredns aws-ebs-csi-driver; do
  V=$(aws eks describe-addon-versions --kubernetes-version 1.36 --addon-name $a \
      --query 'addons[0].addonVersions[?compatibilities[0].defaultVersion==`true`].addonVersion' --output text)
  aws eks update-addon --cluster-name demo --addon-name $a --addon-version $V --resolve-conflicts PRESERVE
  aws eks wait addon-active --cluster-name demo --addon-name $a
done

# 4. Узлы
eksctl upgrade nodegroup --cluster demo --name ng-general     # rolling, уважает PDB
# или для Karpenter: узлы заменятся сами по expireAfter / drift

# 5. kubectl на своей машине
kubectl version
```

**Три железных правила:**

1. **Только один минор за раз.** 1.34 → 1.36 напрямую нельзя.
2. **Откатиться нельзя.** Control plane обновляется в одну сторону. Единственный «откат» — новый кластер старой версии.
3. **Skew между control plane и узлами** допускается на 3 минора вниз (узлы не новее control plane). Но не расслабляйся: аддоны и CSI могут требовать свежести раньше.

## 15.4 Что обычно ломается

| Что | Почему | Как поймать заранее |
|---|---|---|
| Удалённые API | Апстрим удаляет `v1beta1`-версии | `pluto`, `kubent`, аудит-логи |
| Старые Helm-чарты | Используют удалённые kinds | `helm template \| kubectl apply --dry-run=server` |
| Ingress-NGINX | Снят с поддержки в марте 2026 | Миграция на Gateway API / ALB |
| AL2 AMI | Не выпускаются с 1.33 | Перейти на AL2023 или Bottlerocket |
| cgroup v1 | kubelet не стартует с 1.35 | Проверить кастомные AMI |
| IPVS в kube-proxy | Удалён в 1.36 | Переключиться на iptables/nftables |
| Свои admission-webhook | Не знают новых версий API | Обновить, проверить `failurePolicy` |
| Операторы (Postgres, Kafka) | Отстают от версий Kubernetes | Обновить оператор ДО кластера |
| PDB, которые блокируют drain | `minAvailable` = числу реплик | Проверить `kubectl get pdb -A` |

## 15.5 Blue-green обновление кластера

Когда риск неприемлем (регулируемая среда, критичный сервис), обновляют не кластер, а трафик:

```
Кластер A (1.34, prod)  ←── 100% трафика через Route 53 / ALB
Кластер B (1.36, новый) ←── 0%

1. Поднять B из того же IaC, версия новее
2. Раскатать те же приложения через GitOps
3. Прогнать smoke-тесты
4. Переключить трафик: 10% → 50% → 100% (weighted Route 53 или общий ALB)
5. Подержать A сутки как путь отката
6. Удалить A
```

Дорого (двойной счёт на время миграции), но полностью обратимо. Хорошо сочетается с GitOps: «поднять такой же кластер» — это один `terraform apply` и один `ApplicationSet`.

## 15.6 Автоматизация и напоминания

```bash
# EventBridge → Slack на события AWS Health про EKS
aws events put-rule --name eks-version-events \
  --event-pattern '{"source":["aws.health"],"detail":{"service":["EKS"]}}'

# отчёт по версиям всех кластеров аккаунта
for c in $(aws eks list-clusters --query 'clusters[]' --output text); do
  aws eks describe-cluster --name $c --query "cluster.{name:name,version:version,status:status}" --output text
done
```

В организации из десятков кластеров смотри EKS Dashboard: он сводит версии и сроки поддержки по всем аккаунтам.

### Вопросы для самопроверки

1. Сколько живёт минорная версия в EKS и сколько стоит просрочка?
2. Можно ли обновиться с 1.33 сразу на 1.36 и откатиться назад?
3. В каком порядке идут control plane, аддоны, узлы и почему именно так?
4. Как заранее узнать, что приложения используют удалённые API?
5. Когда оправдан blue-green апгрейд целого кластера?

---

# Модуль 16. Стоимость EKS и оптимизация

## 16.1 Полный разбор счёта

| Строка | Цена (us-east-1, 2026) | Комментарий |
|---|---|---|
| Control plane (стандарт) | $0.10/час = **$73/мес** | На кластер, всегда |
| Control plane (extended) | $0.60/час = **$438/мес** | Цена невнимательности |
| Provisioned Control Plane | Сверху, по тарифу тира (XL...8XL) | Только для ультра-масштаба и 99.99% SLA |
| EC2-узлы | Прайс EC2 | Обычно **самая большая** строка |
| Auto Mode | EC2 + **≈12%** | Savings Plans не покрывают наценку |
| Fargate | ≈$0.04048/vCPU-час, ≈$0.004445/ГБ-час | Дороже EC2 на постоянной нагрузке |
| EBS (gp3) | ≈$0.08/ГБ-мес + IOPS выше базовых | Плюс забытые тома |
| Снапшоты EBS | ≈$0.05/ГБ-мес | Копятся незаметно |
| ALB/NLB | ≈$16/мес + LCU | На каждый, если нет `group.name` |
| **NAT Gateway** | $0.045/час + **$0.045/ГБ** | Часто дороже control plane |
| Трафик между AZ | $0.01/ГБ в каждую сторону | Болезнь чатливых микросервисов |
| Egress в интернет | от $0.09/ГБ | |
| CloudWatch Logs | ≈$0.50/ГБ приём + хранение | Аудит-логи на больших кластерах кусаются |
| CloudWatch метрики | $0.30/метрика-мес (custom) | Container Insights на 1000 pod — это деньги |
| ECR | $0.10/ГБ-мес | Без lifecycle policy растёт вечно |
| Публичные IPv4 | $0.005/час за адрес | На узлах в публичных подсетях |
| EKS Capabilities | По тарифу возможности | Argo CD/ACK/kro как сервис |

**Типичный маленький прод-кластер:** control plane $73 + три `m6i.large` $220 + ALB $20 + NAT $35-100 + EBS $30 + логи $30 ≈ **$400-500/мес**. И только $73 из них — это собственно «EKS».

## 16.2 Как увидеть, куда уходят деньги

```bash
# включить разделение затрат по кластерам: теги на всех ресурсах
# (Karpenter и Auto Mode проставляют их сами, если задать в NodeClass/launch template)

# Cost Explorer по тегу
aws ce get-cost-and-usage \
  --time-period Start=2026-08-01,End=2026-09-01 \
  --granularity MONTHLY --metrics UnblendedCost \
  --group-by Type=TAG,Key=eks:cluster-name
```

Внутрь кластера — **OpenCost / Kubecost**: разбивка по namespace, deployment и команде.

```bash
helm repo add opencost https://opencost.github.io/opencost-helm-chart
helm install opencost opencost/opencost -n opencost --create-namespace
```

Правило: без разбивки по namespace разговор «кто тратит» превращается в спор. С разбивкой команды сами начинают править requests.

## 16.3 Восемь рычагов экономии по эффективности

1. **Right-sizing requests.** Средняя утилизация CPU в кластерах — единицы процентов, потому что requests завышены в разы. Это рычаг №1: правильные requests часто сокращают парк узлов на 30-50%, не меняя ничего в архитектуре. Инструменты: VPA в режиме рекомендаций, Kubecost, Goldilocks.
2. **Spot.** До −90%. Batch, dev, stateless. Через Karpenter — с автоматической обработкой прерываний.
3. **Graviton (ARM).** −20-40% цены за производительность. Нужны multi-arch образы.
4. **Консолидация узлов.** Karpenter `WhenEmptyOrUnderutilized` уплотняет нагрузку и убирает полупустые узлы.
5. **Savings Plans / Reserved.** На стабильную базовую нагрузку: Compute Savings Plans гибче всего. Помни: наценку Auto Mode они не покрывают.
6. **Меньше кластеров.** Три dev-кластера = $219/мес только за control plane. Один кластер с namespace на окружение экономит и деньги, и внимание. Прод при этом держи отдельно.
7. **Убрать лишние балансировщики.** `group.name` в ALB Ingress объединяет десятки Ingress в один ALB.
8. **Сеть.** Один NAT Gateway на AZ нужен для отказоустойчивости, но VPC endpoints для S3/ECR убирают из NAT главный объём трафика. `PreferSameZone` и topology-aware routing уменьшают cross-AZ.

## 16.4 Быстрый аудит: что найдётся почти всегда

```bash
# свободные (никем не используемые) EBS-тома
aws ec2 describe-volumes --filters Name=status,Values=available \
  --query 'Volumes[].{id:VolumeId,size:Size,az:AvailabilityZone}' --output table

# балансировщики без целей
for lb in $(aws elbv2 describe-load-balancers --query 'LoadBalancers[].LoadBalancerArn' --output text); do
  aws elbv2 describe-target-groups --load-balancer-arn $lb --query 'TargetGroups[].TargetGroupName' --output text | \
    xargs -r -n1 echo "$lb"
done

# незанятые Elastic IP
aws ec2 describe-addresses --query 'Addresses[?AssociationId==null].PublicIp'

# старые снапшоты
aws ec2 describe-snapshots --owner-ids self \
  --query 'Snapshots[?StartTime<=`2026-01-01`].{id:SnapshotId,size:VolumeSize}' --output table

# самые жирные pod по requests против фактического потребления
kubectl get pods -A -o custom-columns='NS:.metadata.namespace,POD:.metadata.name,CPU_REQ:.spec.containers[*].resources.requests.cpu,MEM_REQ:.spec.containers[*].resources.requests.memory'
kubectl top pods -A --sort-by=cpu | head -20
```

## 16.5 Бюджеты и алерты

```bash
aws budgets create-budget --account-id 111122223333 --budget '{
  "BudgetName":"eks-prod","BudgetLimit":{"Amount":"1500","Unit":"USD"},
  "TimeUnit":"MONTHLY","BudgetType":"COST",
  "CostFilters":{"TagKeyValue":["user:eks:cluster-name$prod"]}}' \
  --notifications-with-subscribers '[{"Notification":{"NotificationType":"ACTUAL","ComparisonOperator":"GREATER_THAN","Threshold":80},"Subscribers":[{"SubscriptionType":"EMAIL","Address":"platform@example.com"}]}]'
```

Плюс `ResourceQuota` на namespace: это не только про безопасность, но и про то, что одна команда не запустит 200 pod по 4 CPU за ночь.

## 16.6 Антипаттерны стоимости

- **Кластер на каждый сервис.** Пять сервисов — пять кластеров — $365/мес только control plane.
- **Dev-кластеры 24/7.** Гаси узлы по расписанию: `eksctl scale nodegroup --nodes 0` ночью и на выходных (или KEDA cron + Karpenter).
- **`requests` «с запасом ×5»** без измерения.
- **Логи всё-в-CloudWatch без фильтров.** Debug-логи в CloudWatch на 1000 pod могут стоить больше узлов.
- **Отдельный ALB на каждый Ingress.**
- **Забытые PVC с `reclaimPolicy: Retain`** после удаления namespace.
- **Публичные IPv4 на узлах**, которым он не нужен.
- **Extended support как стратегия.** Экономия на апгрейде оборачивается шестикратной ценой кластера.

### Практика

1. Проставь тег `eks:cluster-name` на всех ресурсах кластера и построй отчёт в Cost Explorer.
2. Поставь OpenCost и найди три самых дорогих namespace.
3. Найди сервис с завышенными requests (сравни `kubectl top` и requests), уменьши и посмотри, сколько узлов ушло после консолидации Karpenter.
4. Переведи batch-нагрузку на Spot + ARM, посчитай разницу.
5. Настрой Budget на $50 и получи письмо.

---

# Модуль 17. Надёжность, мультирегион и DR

## 17.1 Что может сломаться и что с этим делать

| Отказ | Последствие без подготовки | Подготовка |
|---|---|---|
| Один pod | Часть запросов в ошибку | ≥2-3 реплики, readiness, PDB |
| Один узел | Просадка capacity, лаг перезапуска | Несколько узлов, topology spread, запас capacity |
| **Одна AZ** | Треть или больше нагрузки лежит, EBS недоступен | 3 AZ, `DoNotSchedule` по зонам, реплики БД в других AZ |
| Control plane (SLA 99.95%) | Нельзя деплоить и менять; **работающие pod продолжают работать** | Не завязывать runtime на apiserver, готовность к «замри и не трогай» |
| Регион | Полный простой | Мультирегион, DR-план, репликация данных |
| Ошибка деплоя | Все реплики упали одновременно | Канарейка, `maxUnavailable: 0`, автоматический откат |
| Исчерпание IP / квот | Pod не стартуют | Мониторинг подсетей и квот, запас |
| Удаление кластера или namespace человеком | Потеря конфигурации и данных | GitOps, Velero, `terraform` с `prevent_destroy`, SCP-политики |

Важный факт про EKS: **падение control plane не убивает работающие pod.** Kubelet продолжает держать контейнеры, kube-proxy — правила, ALB — трафик. Ломается управление: деплои, автоскейлинг, замена упавших pod. Это стоит понимать и не паниковать.

## 17.2 Multi-AZ как база

```yaml
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          minDomains: 3
          labelSelector: { matchLabels: { app: web } }
```

Плюс:

- узлы во всех трёх AZ, Karpenter с требованием по зонам;
- NAT Gateway в каждой AZ (один NAT = отказ его AZ рвёт egress всему кластеру);
- `cross-zone` на NLB, если важнее равномерность, чем экономия;
- реплики stateful-систем в разных AZ; помни, что EBS не переезжает между зонами;
- запас capacity: если при отказе AZ на оставшихся узлах нет места, отказ зоны превратится в отказ сервиса.

## 17.3 Проверка отказа зоны

```bash
# найти узлы в одной AZ и вывести их из работы
Z=eu-central-1b
NODES=$(kubectl get nodes -l topology.kubernetes.io/zone=$Z -o name)
kubectl cordon $NODES
kubectl drain $NODES --ignore-daemonsets --delete-emptydir-data --force

# смотреть, что произошло
kubectl get pods -A -o wide | grep -c Running
kubectl get pods -A --field-selector=status.phase=Pending
```

Если при этом упражнении сервис остался доступен, а pod переехали — multi-AZ настроен. Если появились `Pending` и 5xx — нашёл проблему до того, как её нашёл клиент.

## 17.4 Мультирегион: три модели

```
1. Active-Passive (pilot light)
   Регион A: полный прод.  Регион B: кластер минимального размера + реплика данных
   Переключение: Route 53 failover, масштабирование B
   RTO: десятки минут, RPO: минуты.  Цена: умеренная

2. Active-Active
   Оба региона обслуживают трафик, Route 53 latency routing / Global Accelerator
   Данные: Aurora Global Database, DynamoDB Global Tables, S3 CRR
   RTO: секунды, RPO: близко к нулю.  Цена: двойная, сложность высокая

3. Backup & Restore
   Только IaC + Velero-бэкапы в S3 с репликацией
   RTO: часы.  Цена: минимальная
```

Главный вопрос не в кластерах, а в **данных**: Kubernetes-часть воспроизводится из Git за 30 минут, а вот база с состоянием — нет. Начинай проектирование DR с данных.

```bash
# репликация образов между регионами
aws ecr put-replication-configuration --replication-configuration '{
  "rules":[{"destinations":[{"region":"eu-west-1","registryId":"111122223333"}]}]}'
```

## 17.5 Route 53 и переключение трафика

```bash
# health check на прод-эндпоинт
aws route53 create-health-check --caller-reference $(date +%s) \
  --health-check-config Type=HTTPS,FullyQualifiedDomainName=app.example.com,ResourcePath=/healthz,RequestInterval=10,FailureThreshold=3
```

Failover-записи: primary на ALB региона A с health check, secondary на ALB региона B. Плюс короткий TTL (60 секунд), иначе переключение растянется на часы кэша DNS.

Альтернатива без DNS-задержек — **AWS Global Accelerator**: anycast-IP и переключение на уровне сети.

## 17.6 Бэкапы, которые проверены

```bash
# расписание Velero
velero schedule create daily-prod --schedule="0 2 * * *" \
  --include-namespaces prod --ttl 720h --snapshot-volumes

# проверка восстановления (в отдельный namespace!)
velero restore create test-restore --from-backup daily-prod-20260921020000 \
  --namespace-mappings prod:prod-restore-test
kubectl -n prod-restore-test get pods,pvc
```

**Бэкап, который не проверяли восстановлением, — не бэкап.** Раз в квартал делай учения: подними кластер из IaC, восстанови приложения из Velero и замерь реальное RTO.

## 17.7 Хаос-инженерия

```bash
# AWS Fault Injection Service: убить процент узлов кластера
aws fis create-experiment-template --cli-input-json file://eks-node-failure.json
aws fis start-experiment --experiment-template-id EXT123
```

Что стоит прогонять регулярно: терминирование случайных узлов, отказ AZ, исчерпание CPU на узле, задержки сети до RDS, исчерпание IP в подсети, потеря доступа к ECR.

### Вопросы для самопроверки

1. Что произойдёт с работающими pod при недоступности control plane?
2. Почему один NAT Gateway на весь VPC — это риск доступности?
3. Почему EBS-том мешает перепланировать pod в другую AZ?
4. Чем отличаются pilot light и active-active по RTO и цене?
5. Как проверить, что бэкапы действительно работают?

---

# Модуль 18. EKS в продакшене: архитектура и эксплуатация

## 18.1 Референсная архитектура

```
AWS Organizations
  ├── Аккаунт shared-services:  ECR, Route 53, CI-раннеры, центральные логи
  ├── Аккаунт dev:              кластер dev (namespace на команду)
  ├── Аккаунт staging:          кластер staging (копия прода меньшего размера)
  └── Аккаунт prod:
        VPC 10.0.0.0/16, 3 AZ
          публичные подсети:   ALB, NAT GW (по одному на AZ)
          приватные подсети:   /18 на AZ под узлы и pod
          VPC endpoints:       s3, ecr.api, ecr.dkr, sts, logs, eks, ssm, secretsmanager
        EKS prod (1.36)
          endpoint: private + узкий публичный список CIDR
          authenticationMode: API, access entries из IaC
          аудит-логи → CloudWatch → S3
          KMS-шифрование секретов
          ├── managed node group "system" (On-Demand, 3 узла, taint=system)
          │     CoreDNS, Karpenter, LBC, Argo CD, мониторинг
          ├── Karpenter NodePool "apps"  (On-Demand + Spot, multi-arch)
          └── Karpenter NodePool "batch" (Spot, taint=batch)
        Данные: RDS/Aurora Multi-AZ, ElastiCache, S3 (не в кластере)
        Доставка: Argo CD (pull), образы из ECR shared-services
        Наблюдаемость: AMP + AMG или kube-prometheus-stack, Container Insights
```

Четыре принципа этой схемы: **prod в отдельном аккаунте**, **системная нагрузка отдельно от прикладной**, **данные вне кластера**, **всё описано в IaC**.

## 18.2 Sizing: от чего отталкиваться

| Масштаб | Узлы | Что важно |
|---|---|---|
| До 10 pod | 2-3 × `m6i.large` | Хватит одной node group; главное — 3 AZ |
| 50-200 pod | 5-15 узлов, Karpenter | Разделить system и apps, PDB везде, prefix delegation |
| 500-2000 pod | Десятки узлов | CoreDNS масштабировать, следить за подсетями и квотами EC2, лимиты аддонов |
| 5000+ pod / 1000+ узлов | Много NodePool | Provisioned Control Plane, шардирование по кластерам, watch-нагрузка на apiserver, отдельный etcd-бюджет |

Практические ориентиры:

- **110 pod на узел** — рекомендуемый максимум (даже если ENI позволяет больше);
- один кластер спокойно держит несколько тысяч узлов, но раньше упрётся в подсети, квоты EC2 и твою способность его обслуживать;
- CoreDNS: 2 реплики на старте, дальше по реплике на 30-50 узлов;
- если apiserver начинает тормозить на пиках (много watch, много Job, тысячи pod в секунду) — это кандидат на Provisioned Control Plane.

## 18.3 IaC-структура, которая не развалится

```
infra/
  modules/
    eks-cluster/          # обёртка над terraform-aws-modules/eks
    eks-addons/           # аддоны и платформенные контроллеры
    vpc/
  envs/
    dev/main.tf           # module "cluster" { source = "../../modules/eks-cluster" ... }
    staging/main.tf
    prod/main.tf
deploy/                   # GitOps-репозиторий (или отдельный репо)
  clusters/
    prod/
      apps/               # ApplicationSet, чарты, values
      platform/           # мониторинг, Argo, политики
```

Правила:

- один и тот же модуль на все окружения, различия только в `tfvars`;
- `prevent_destroy = true` на прод-кластере и его state;
- remote state в S3 с блокировкой, отдельный state на окружение;
- версии провайдеров и модулей зафиксированы;
- версии аддонов зафиксированы явно;
- `terraform plan` в PR и обязательный ревью для прода.

## 18.4 Ежедневная эксплуатация

```bash
# утренний обход
kubectl get nodes | grep -v " Ready"
kubectl get pods -A --field-selector=status.phase!=Running | grep -v Completed
kubectl get events -A --sort-by='.lastTimestamp' | tail -30
aws eks list-insights --cluster-name prod --query 'insights[?insightStatus.status!=`PASSING`]'
kubectl get pdb -A                                # не блокирует ли что-то drain
kubectl get certificates -A 2>/dev/null           # если cert-manager

# перед пятницей
aws eks describe-cluster --name prod --query 'cluster.version'
aws ec2 describe-subnets --filters Name=tag:kubernetes.io/role/internal-elb,Values=1 \
  --query 'Subnets[].{az:AvailabilityZone,free:AvailableIpAddressCount}'
```

Что стоит автоматизировать в первую очередь: отчёт по версиям кластеров и аддонов, алерт по свободным IP в подсетях, алерт по возрасту узлов, еженощная проверка бэкапов.

## 18.5 Чек-лист продакшена

**Кластер**

- версия в стандартной поддержке, план апгрейда в календаре;
- 3 AZ, приватные узлы, endpoint private (или узкий CIDR);
- `authenticationMode=API`, access entries из IaC;
- аудит-логи включены, KMS-шифрование секретов;
- всё создано через IaC, ручных изменений нет.

**Compute**

- системная нагрузка на On-Demand с taint, прикладная отдельно;
- Karpenter или Auto Mode, лимиты в NodePool заданы;
- `expireAfter` для регулярной замены узлов на свежие AMI;
- IMDSv2 и `hopLimit: 1`;
- несколько типов инстансов и AZ, Spot только там, где допустимо.

**Приложения**

- `requests` измерены, `limits.memory` задан;
- readiness + liveness (+ startup для медленных);
- PDB на каждый сервис;
- topology spread по зонам;
- `maxUnavailable: 0` при роллинге, preStop и graceful shutdown;
- HPA или KEDA настроены и протестированы нагрузкой.

**Безопасность**

- PSS `restricted`, NetworkPolicy `default deny`;
- Pod Identity со своей ролью на сервис;
- образы из своего ECR, immutable теги, сканирование, подписи;
- GuardDuty EKS Protection;
- секреты в Secrets Manager, не в Git.

**Эксплуатация**

- дашборды и алерты из модуля 12;
- бэкапы приложений и PV, проверенное восстановление;
- runbook на типовые аварии;
- бюджеты и разбивка затрат по namespace;
- отдельные аккаунты prod и non-prod.

## 18.6 Антипаттерны EKS

- **Один кластер на всё: prod, dev и эксперименты.** Один неудачный webhook или CRD ломает всё сразу.
- **Кластер, созданный руками в консоли.** Через год его нельзя воспроизвести, и никто не решается ничего менять.
- **`cluster-admin` всем.** Потом невозможно понять, кто удалил Deployment (если не включены аудит-логи — вообще невозможно).
- **Никаких `requests`/`limits`.** Кластер работает, пока один pod не съест узел.
- **Нет PDB.** Любой drain, консолидация или Spot-прерывание превращается в инцидент.
- **База данных в кластере «потому что так модно»** без оператора, бэкапов и человека, который умеет её восстанавливать.
- **Ingress-NGINX в 2026-м** без плана миграции.
- **Игнорирование конца поддержки версии** и внезапный принудительный апгрейд от AWS в неудобный момент.
- **Мониторинг «мы смотрим в CloudWatch, когда жалуются».**
- **Микросервисы, болтающие через AZ** без нужды: платишь за каждый гигабайт дважды.
- **Ручные `kubectl edit`** в проде вместо Git.
- **Секреты в ConfigMap.** Да, это встречается чаще, чем хотелось бы.

### Вопросы для самопроверки

1. Почему системную нагрузку выносят на отдельную On-Demand node group?
2. Сколько pod на узел разумно планировать и почему не по максимуму ENI?
3. Что должно быть в IaC, а что допустимо в Helm/GitOps?
4. Какие пять пунктов ты проверишь первым делом на незнакомом прод-кластере?
5. Назови три антипаттерна, которые видел или встретишь в реальном проекте.

---

# Модуль 19. Итоговый проект: production-grade кластер

## 19.1 Что строим

Платформу для небольшого продакшена с двумя сервисами и фоновым воркером, полностью из кода.

```
                      Route 53 (app.example.com)
                              |
                         ALB (shared-prod group, ACM, WAF)
                              |
              +---------------+---------------+
              |                               |
        web (3-20 реплик)              api (3-30 реплик)
              |                               |
              +-------------> Redis (ElastiCache)
                              |
                         Aurora PostgreSQL (Multi-AZ)
                              |
        worker (0-50 реплик, KEDA по SQS, Spot+ARM)
                              |
                         S3 (артефакты, доступ через Pod Identity)

Кластер EKS 1.36, 3 AZ
  node group "system" (On-Demand, taint=system): CoreDNS, Karpenter, LBC, Argo CD, мониторинг
  NodePool "apps"  (On-Demand + Spot, amd64 + arm64)
  NodePool "batch" (только Spot, taint=batch)
Доставка: Argo CD из Git, образы из ECR
Наблюдаемость: kube-prometheus-stack + Container Insights + аудит-логи
```

## 19.2 Требования

**Инфраструктура**

1. Всё создаётся `terraform apply` с нуля: VPC, 3 AZ, приватные узлы, VPC endpoints, EKS 1.36.
2. `authenticationMode=API`, три access entry: admin (cluster), dev (namespace `apps`, edit), viewer (cluster, view).
3. Аддоны фиксированных версий: vpc-cni с prefix delegation и network policy, coredns, kube-proxy, pod-identity-agent, ebs-csi, metrics-server.
4. Karpenter с двумя NodePool, `expireAfter: 336h`, disruption budget 10%.
5. Аудит-логи в CloudWatch с retention 30 дней, KMS-шифрование секретов.

**Приложения**

6. Три сервиса в namespace `apps`: `web`, `api`, `worker`; чарт Helm с окружениями.
7. У всех: измеренные `requests`, `limits.memory`, readiness/liveness, PDB, topology spread по зонам.
8. `web` и `api` через один ALB (`group.name: shared-prod`), HTTPS с ACM, редирект с HTTP.
9. HPA на `api` (CPU 70%, 3-30), KEDA на `worker` по длине SQS (0-50, Spot+ARM).
10. `api` читает креденшелы Aurora из Secrets Manager через CSI, пишет в S3 через Pod Identity. Ни одного статического ключа.

**Безопасность**

11. PSS `restricted` на namespace `apps`, все контейнеры non-root с `readOnlyRootFilesystem`.
12. NetworkPolicy: `default deny` ingress и egress; разрешено только web→api, api→Aurora/Redis/DNS, worker→SQS/S3/DNS.
13. ECR с immutable-тегами и enhanced scanning, Kyverno запрещает образы не из своего ECR и `:latest`.
14. IMDSv2 и `hopLimit: 1` на всех узлах.

**Доставка и наблюдаемость**

15. GitHub Actions с OIDC: собирает multi-arch образ, пушит в ECR, обновляет тег в GitOps-репозитории. Доступа в кластер у CI нет.
16. Argo CD с `automated.prune` и `selfHeal`, ApplicationSet на dev и prod.
17. Дашборд и минимум шесть алертов из модуля 12.
18. Velero: ежедневный бэкап namespace `apps` с томами, проверенный restore.
19. Теги затрат на всех ресурсах, Budget с алертом.

## 19.3 Этапы

| Этап | Что делаешь | Критерий готовности |
|---|---|---|
| 1 | VPC, EKS, аддоны в Terraform | `kubectl get nodes` показывает узлы в 3 AZ |
| 2 | Access entries, RBAC | dev-роль видит `apps`, но не `kube-system` |
| 3 | Karpenter, два NodePool | 30 реплик поднимают узлы, 2 реплики — консолидация |
| 4 | LBC, ALB, ACM, ExternalDNS | `curl https://app.example.com` отвечает 200 |
| 5 | Чарты приложений, PDB, probes | `kubectl drain` любого узла не даёт 5xx |
| 6 | Pod Identity, Secrets Manager CSI | в манифестах ноль ключей, `sts get-caller-identity` из pod показывает роль сервиса |
| 7 | HPA и KEDA | нагрузка `hey` масштабирует api; 1000 сообщений в SQS поднимают worker с нуля |
| 8 | PSS, NetworkPolicy, Kyverno | pod с root не создаётся; `curl` из web в БД не проходит |
| 9 | CI + Argo CD | `git push` доезжает до кластера без участия человека |
| 10 | Наблюдаемость, алерты, бэкапы | алерт срабатывает на искусственной аварии, restore проверен |
| 11 | Апгрейд | обновление минорной версии без простоя сервиса |
| 12 | Отказ AZ | drain всей зоны: сервис жив, `Pending` нет |

## 19.4 Как проверить, что получилось

```bash
# 1. нагрузка и автомасштабирование
kubectl -n apps run load --rm -it --image=williamyeh/hey -- -z 300s -c 200 https://app.example.com/api/health
watch -n2 'kubectl -n apps get hpa,pods | head -30; kubectl get nodes | wc -l'

# 2. отказ зоны во время нагрузки
Z=eu-central-1b
kubectl drain $(kubectl get nodes -l topology.kubernetes.io/zone=$Z -o name) \
  --ignore-daemonsets --delete-emptydir-data --force
# ожидаем: ноль ошибок в ALB-метриках, pod переехали, Pending нет

# 3. деплой под нагрузкой
git commit --allow-empty -m "deploy test" && git push
# ожидаем: ноль 5xx в TargetGroup, Argo CD Synced за минуты

# 4. безопасность
kubectl -n apps run bad --image=nginx --overrides='{"spec":{"containers":[{"name":"bad","image":"nginx","securityContext":{"runAsUser":0,"privileged":true}}]}}'
# ожидаем: отказ от Pod Security Admission

kubectl -n apps run bad2 --image=docker.io/library/nginx:latest
# ожидаем: отказ от Kyverno (не наш ECR, плюс тег latest)

kubectl -n apps exec deploy/web -- curl -s --max-time 3 http://169.254.169.254/latest/meta-data/
# ожидаем: таймаут

# 5. восстановление
velero restore create check --from-backup $(velero backup get -o name | head -1) \
  --namespace-mappings apps:apps-restore
kubectl -n apps-restore get pods,pvc

# 6. стоимость
aws ce get-cost-and-usage --time-period Start=$(date -d '7 days ago' +%F),End=$(date +%F) \
  --granularity DAILY --metrics UnblendedCost \
  --group-by Type=TAG,Key=eks:cluster-name
```

Если всё это проходит — ты умеешь EKS на уровне, который ждут от senior DevOps-инженера. И не забудь:

```bash
terraform destroy
```

---
# Шпаргалка команд EKS

```bash
# ---------- AWS CLI: кластеры ----------
aws eks list-clusters
aws eks describe-cluster --name demo
aws eks describe-cluster --name demo --query 'cluster.{v:version,status:status,ep:endpoint,health:health}'
aws eks update-kubeconfig --name demo --region eu-central-1 --alias demo
aws eks update-cluster-version --name demo --kubernetes-version 1.36
aws eks wait cluster-active --name demo
aws eks list-insights --cluster-name demo
aws eks describe-insight --cluster-name demo --id <id>

# endpoint и логи
aws eks update-cluster-config --name demo \
  --resources-vpc-config endpointPublicAccess=true,publicAccessCidrs=203.0.113.0/24,endpointPrivateAccess=true
aws eks update-cluster-config --name demo \
  --logging '{"clusterLogging":[{"types":["api","audit","authenticator"],"enabled":true}]}'

# ---------- доступ ----------
aws eks list-access-entries --cluster-name demo
aws eks create-access-entry --cluster-name demo --principal-arn <role-arn> --type STANDARD
aws eks associate-access-policy --cluster-name demo --principal-arn <role-arn> \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSEditPolicy \
  --access-scope type=namespace,namespaces=apps
aws eks list-associated-access-policies --cluster-name demo --principal-arn <role-arn>

# ---------- узлы ----------
aws eks list-nodegroups --cluster-name demo
aws eks describe-nodegroup --cluster-name demo --nodegroup-name ng-general
aws eks update-nodegroup-version --cluster-name demo --nodegroup-name ng-general
eksctl get nodegroup --cluster demo
eksctl scale nodegroup --cluster demo --name ng-general --nodes 5 --nodes-min 2 --nodes-max 10
eksctl upgrade nodegroup --cluster demo --name ng-general

# ---------- аддоны ----------
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

# ---------- kubectl: базовое ----------
kubectl config get-contexts && kubectl config use-context demo
kubectl get nodes -o wide --label-columns=topology.kubernetes.io/zone,node.kubernetes.io/instance-type
kubectl get pods -A -o wide --field-selector=status.phase!=Running
kubectl get events -A --sort-by='.lastTimestamp' | tail -40
kubectl api-resources | grep -i <что-ищу>
kubectl explain deployment.spec.strategy --recursive

# ---------- kubectl: отладка ----------
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

# ---------- kubectl: обслуживание ----------
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

# ---------- сеть и диагностика AWS ----------
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

# Шпаргалка важных настроек

**Кластер (прод):**

```
version: в стандартной поддержке (1.34+ на сентябрь 2026)
endpointPrivateAccess: true
endpointPublicAccess: false  (или узкий publicAccessCidrs)
authenticationMode: API
logging: api, audit, authenticator (+ scheduler, controllerManager при отладке)
encryptionConfig: secrets → свой KMS-ключ
subnets: 3 приватные подсети /18-/20 в трёх AZ
```

**Managed node group (система):**

```
capacityType: ON_DEMAND
instanceTypes: [m6i.large, m6a.large, m5.large]   # 3+ типа
amiFamily: AL2023
min/desired/max: 3 / 3 / 6
volumeType: gp3, size: 50-80Gi, encrypted: true
privateNetworking: true
taints: [{key: workload, value: system, effect: NoSchedule}]
updateConfig.maxUnavailablePercentage: 25
```

**Karpenter NodePool (приложения):**

```
capacity-type: [spot, on-demand]
instance-category: [c, m, r], instance-generation > 5
arch: [amd64, arm64]
zones: все три AZ
expireAfter: 336h            # узлу максимум 2 недели
consolidationPolicy: WhenEmptyOrUnderutilized
consolidateAfter: 30s-1m
disruption.budgets: 10% (и 0 в часы пик)
limits: cpu/memory заданы явно
metadataOptions: httpTokens=required, hopLimit=1
```

**Deployment (типовой сервис):**

```
replicas: ≥3
requests.cpu: измеренный p50-p70 (не «с запасом ×5»)
requests.memory = limits.memory
limits.cpu: не задавать (кроме мультитенантных кластеров)
readinessProbe: обязательно
livenessProbe: только «процесс жив», без проверки зависимостей
startupProbe: для медленного старта
strategy: RollingUpdate, maxUnavailable: 0, maxSurge: 1
terminationGracePeriodSeconds: 60, preStop sleep 15
topologySpreadConstraints: зона DoNotSchedule, хост ScheduleAnyway
PDB: minAvailable 80% или maxUnavailable 1
securityContext: runAsNonRoot, readOnlyRootFilesystem, drop ALL, seccomp RuntimeDefault
образ: тег + @sha256, из своего ECR
serviceAccount: свой, с Pod Identity
```

**Ingress (ALB):**

```
target-type: ip
group.name: общий на окружение
listen-ports: HTTP 80 + HTTPS 443, ssl-redirect: 443
certificate-arn: из ACM
healthcheck-path: /healthz
deregistration_delay.timeout_seconds: 30
readiness gate на namespace: elbv2.k8s.aws/pod-readiness-gate-inject=enabled
```

**StorageClass (EBS):**

```
provisioner: ebs.csi.aws.com
volumeBindingMode: WaitForFirstConsumer     # обязательно
allowVolumeExpansion: true
type: gp3, iops: 3000, throughput: 125, encrypted: true
reclaimPolicy: Retain для прод-данных
```

**VPC CNI:**

```
ENABLE_PREFIX_DELEGATION: true     # включай на новом кластере
WARM_PREFIX_TARGET: 1
ENABLE_NETWORK_POLICY: true
ENABLE_POD_ENI: только если нужны security groups for pods
```

---

# Шпаргалка: типовые ошибки и что делать

| Симптом / сообщение | Вероятная причина | Что делать |
|---|---|---|
| `You must be logged in to the server (Unauthorized)` | Нет access entry для твоей IAM-личности, истекли креденшелы, не тот профиль | `aws sts get-caller-identity`, `aws eks list-access-entries`, создать access entry |
| `error: You must be logged in` после смены роли | `kubeconfig` ссылается на другой профиль | `aws eks update-kubeconfig --profile <p>` |
| Pod `Pending`, `0/3 nodes are available: insufficient cpu` | Нет места, завышенные requests | Проверить requests, дать узлам вырасти, `kubectl describe node` |
| Pod `Pending`, `untolerated taint` | Taint на узлах, у pod нет toleration | Добавить toleration или другой NodePool |
| Pod `Pending`, `volume node affinity conflict` | PVC в одной AZ, узлы в другой | `WaitForFirstConsumer`, узлы во всех AZ |
| `FailedCreatePodSandBox: failed to assign an IP address` | Кончились IP в подсети или лимит ENI | Prefix delegation, secondary CIDR, custom networking |
| `ImagePullBackOff` / `no basic auth credentials` | Нет прав на ECR у node role, нет пути к ECR | `AmazonEC2ContainerRegistryReadOnly`, VPC endpoints ecr.api/ecr.dkr/s3 |
| `ImagePullBackOff: manifest unknown` | Неверный тег или архитектура образа | Проверить тег и `--platform` |
| `CrashLoopBackOff` | Приложение падает при старте | `kubectl logs --previous`, проверить конфиг и секреты |
| `OOMKilled` в `Last State` | Превышен `limits.memory` | Поднять лимит или починить утечку; сравнить с `kubectl top` |
| Узел `NotReady` | kubelet, диск, сеть, удалена запись в `aws-auth` | `kubectl describe node`, SSM на узел, проверить CNI и `aws-auth` |
| `DiskPressure`, вытеснение pod | Заполнен диск узла (образы, логи) | Увеличить диск, чистить образы, ограничить логи |
| ALB не создаётся по Ingress | Нет LBC, нет тегов на подсетях, нет прав | Логи `aws-load-balancer-controller`, теги `kubernetes.io/role/elb` |
| 5xx во время деплоя | Нет readiness gate, нет preStop, `maxUnavailable > 0` | Раздел 8.7 |
| `no endpoints available for service` | Ни один pod не Ready | `kubectl get endpoints`, проверить readinessProbe и селекторы |
| DNS-таймауты, медленные запросы | Мало реплик CoreDNS, `ndots`, throttling | Масштабировать CoreDNS, NodeLocal DNSCache, `dnsConfig` |
| `Multi-Attach error for volume` | EBS пытаются подключить к двум pod | EBS это RWO; нужен EFS |
| HPA `unknown` в целях | Нет metrics-server | `aws eks create-addon --addon-name metrics-server` |
| HPA не масштабирует под нагрузкой | Завышенные `requests.cpu` | Привести requests к реальности |
| `drain` висит вечно | PDB не позволяет вытеснить | `kubectl get pdb -A`, исправить `minAvailable` |
| Karpenter не создаёт узлы | Нет тегов `karpenter.sh/discovery`, лимиты, права | Логи Karpenter, `kubectl describe nodepool` |
| CloudFormation/Terraform не удаляет VPC | Остались ENI, ALB, security groups от контроллеров | Сначала удалить Ingress/Service LB/PVC, потом кластер |
| Внезапно вырос счёт | Extended support, забытые ALB и тома, cross-AZ, логи | Модуль 16, аудит ресурсов |
| Webhook блокирует все деплои | Упал admission-webhook с `failurePolicy: Fail` | Поднять webhook или временно снять его правило |

---

# Вопросы на собеседовании по EKS с ответами

**Junior**

1. **Что AWS управляет в EKS, а что ты?** AWS — control plane (apiserver, etcd, scheduler, controller-manager), его патчи и бэкапы. Ты — узлы, сеть, аддоны, приложения, безопасность и стоимость.
2. **Сколько стоит кластер EKS без нагрузки?** $0.10 в час за control plane, около $73 в месяц, плюс всё остальное отдельно.
3. **Почему `kubectl get pods` возвращает `Unauthorized`, хотя у меня `AdministratorAccess`?** IAM отвечает за аутентификацию, а права внутри кластера даёт RBAC через access entry или `aws-auth`. Это две разные системы.
4. **Зачем EKS нужны минимум две подсети в разных AZ?** Для HA control plane и для EKS-owned ENI, через которые apiserver ходит к kubelet.
5. **Чем managed node group отличается от self-managed?** EKS сам создаёт ASG, регистрирует узлы, делает graceful drain при обновлении и следит за здоровьем узлов.
6. **Что такое Fargate в EKS?** Режим compute, где каждый pod запускается в отдельной микро-VM без узлов. Нет DaemonSet, GPU и privileged.
7. **Почему `kubectl top nodes` не работает на новом кластере?** Не установлен `metrics-server`, он не входит в кластер по умолчанию.
8. **Что делает `aws eks update-kubeconfig`?** Прописывает контекст, где токен получается через `aws eks get-token`, то есть аутентификация идёт по твоим AWS-креденшелам.
9. **Какие три аддона обязательны?** `vpc-cni`, `coredns`, `kube-proxy`.
10. **Зачем нужен readinessProbe?** Чтобы трафик (в том числе от ALB) не шёл в pod, который ещё не готов обслуживать запросы.

**Middle**

11. **Как pod получает IP в EKS и в чём подвох?** Через VPC CNI pod получает реальный адрес из подсети VPC. Подвох — IP-адреса в подсети кончаются, и число pod на узел ограничено ENI.
12. **Как посчитать максимум pod на узел и как его увеличить?** `(ENI × (IP на ENI − 1)) + 2`; увеличивается prefix delegation (`m6i.large`: с 29 до 110).
13. **Что делать, когда в подсети кончились IP?** Prefix delegation, secondary CIDR с custom networking, IPv6-кластер, уменьшение warm-таргетов, в крайнем случае другой CNI.
14. **Чем access entries лучше `aws-auth`?** Это API EKS: версионируется в IaC, нет риска сломать доступ всем одной опечаткой в ConfigMap, есть готовые access policies и scope на namespace.
15. **Pod Identity или IRSA?** Pod Identity по умолчанию: одна роль для многих кластеров, без OIDC в trust policy, без аннотаций, с session policies и tags. IRSA — для Fargate и кросс-аккаунтного доступа.
16. **Как запретить pod пользоваться ролью узла?** IMDSv2 (`httpTokens: required`) и `httpPutResponseHopLimit: 1`, плюс собственные роли через Pod Identity.
17. **Чем Karpenter лучше Cluster Autoscaler?** Создаёт инстансы напрямую и подбирает тип под pod, работает за десятки секунд, консолидирует нагрузку, нативно дружит со Spot, конфигурируется 1-2 NodePool вместо десятков node group.
18. **Почему Karpenter «не экономит»?** Он планирует по `requests`. Завышенные requests — это купленное железо, которое не используется.
19. **ALB или NLB и почему?** ALB для HTTP/HTTPS с маршрутизацией, WAF, аутентификацией; NLB для TCP/UDP, gRPC, статических IP и минимальной задержки.
20. **Что даёт `target-type: ip` в ALB Ingress?** Трафик идёт прямо в pod, минуя NodePort: меньше хопов, работает readiness gate, корректнее балансировка.
21. **Как задеплоить без 5xx?** `maxUnavailable: 0`, readiness gate, preStop-пауза, короткий deregistration delay, корректная обработка SIGTERM.
22. **Почему EBS-том мешает переносу pod?** EBS существует в одной AZ, поэтому pod может быть запланирован только в эту зону; с `Immediate` binding это приводит к `volume node affinity conflict`.
23. **Когда EFS вместо EBS?** Когда нужен ReadWriteMany из нескольких pod и AZ; цена и задержка выше.
24. **Зачем PodDisruptionBudget?** Он ограничивает добровольные вытеснения: обновление node group, консолидацию Karpenter, замену узлов, drain при Spot-прерывании.
25. **Что делает `topologySpreadConstraints` с `DoNotSchedule` по зонам?** Заставляет раскладывать реплики по AZ, чтобы отказ одной зоны не уносил весь сервис.
26. **Чем HPA отличается от KEDA?** HPA масштабирует по CPU/памяти и кастомным метрикам и не умеет в ноль; KEDA масштабирует по внешним событиям (SQS, Kafka, Prometheus) и умеет scale-to-zero.
27. **Как включить network policy без сторонних CNI?** `ENABLE_NETWORK_POLICY=true` у VPC CNI; с 2026 года есть ещё Admin Policies уровня кластера.
28. **Что такое EKS add-on и чем отличается от Helm-установки?** Версией управляет EKS API, AWS отвечает за совместимость и CVE; конфигурация задаётся `configuration-values`, а ручные правки могут быть перезаписаны при `OVERWRITE`.
29. **Какие логи control plane включать и почему?** `api`, `audit`, `authenticator` обязательно: без них невозможно разобрать инцидент и понять, кто что удалил.
30. **Что происходит с работающими pod, если control plane недоступен?** Они продолжают работать: kubelet держит контейнеры, kube-proxy — правила, ALB — трафик. Ломается управление: деплои, автоскейлинг, пересоздание pod.

**Senior**

31. **Как ты спроектируешь VPC под кластер на 2000 pod?** Три AZ, приватные подсети по /18 под узлы и pod, публичные /20 под ALB и NAT, prefix delegation с первого дня, запас под secondary CIDR (`100.64.0.0/16`), VPC endpoints для ECR/S3/STS/logs, теги для LBC. Отдельно проверить квоты EC2 и ENI.
32. **Стратегия обновления версий?** Апгрейд раз в 6-9 месяцев, по одному минору; перед каждым — cluster insights, `pluto`/`kubent`, апдейт операторов; порядок control plane → аддоны → узлы; в критичных средах blue-green кластерами. Мониторить AWS Health и держать версию в стандартной поддержке, чтобы не платить $0.60/час.
33. **Auto Mode или свой Karpenter?** Auto Mode, если команда маленькая, кластер новый и нужен минимум тоила; свой Karpenter, если нужен свой AMI, точный контроль версий, SSH-доступ к узлам, специальные security-агенты или парк настолько большой, что 12% наценки дороже инженерного времени. Savings Plans наценку не покрывают.
34. **Как урезать счёт кластера вдвое?** Начать с right-sizing requests (обычно главный источник), затем Spot и Graviton через Karpenter с консолидацией, объединить Ingress в один ALB, вынести трафик из NAT в VPC endpoints, сократить cross-AZ, обрезать логи и метрики, консолидировать dev-кластеры, взять Savings Plans на базовую нагрузку и убрать extended support.
35. **Как обеспечить мультитенантность?** Namespace с PSS `restricted`, `ResourceQuota` и `LimitRange`, `default deny` NetworkPolicy, access entries со scope на namespace, отдельные NodePool с taint, лимит на балансировщики, Kyverno-политики, разбивка затрат. И честно сказать, что namespace — не граница безопасности: для враждебных тенантов нужны отдельные кластеры.
36. **Один большой кластер или много маленьких?** Много маленьких: лучше изоляция отказов, проще апгрейды, меньше blast radius; дороже по control plane и сложнее эксплуатировать. Один большой: дешевле и проще платформенно, но любой сбой webhook, CRD или CNI задевает всех. Обычно: prod отдельно от non-prod, дальше по домену или регуляторике.
37. **Как спроектировать DR?** Начать с данных: Aurora Global Database или DynamoDB Global Tables, S3 CRR, ECR-репликация. Кластер воспроизводится из IaC + GitOps за минуты, поэтому обычно pilot light: минимальный кластер во втором регионе, Route 53 failover с health checks, регулярные учения восстановления и замер реального RTO/RPO.
38. **Что делать, если apiserver тормозит на пиках?** Посмотреть `apiserver_request_duration_seconds`, найти источники watch и list-all (плохие контроллеры и операторы), уменьшить частоту опросов, добавить кэширование, включить Provisioned Control Plane нужного тира, при необходимости шардировать нагрузку по кластерам.
39. **Как перевести кластер в private-only без потери доступа?** Заранее: VPC endpoints (eks, ecr, sts, logs, ssm), CI-раннеры в VPC, VPN или SSM-порт-форвардинг, bastion, break-glass роль с access entry. Проверить пути доступа, переключить, проверить снова. Иметь план восстановления доступа.
40. **Как ты примешь незнакомый прод-кластер?** Проверить версию и срок поддержки, аудит-логи, кто имеет доступ (access entries и `aws-auth`), endpoint access, наличие PDB и probes у сервисов, состояние аддонов и их версии, свободные IP в подсетях, откуда приходят деплои (есть ли дрейф от Git), бэкапы и их проверяемость, дашборды и алерты, разбивку затрат. Всё найденное — в бэклог с приоритетом по риску.

---

# FAQ: частые вопросы про EKS

**Правда, что EKS стоит $73 в месяц?**
Только control plane. Реальный счёт маленького прод-кластера — $300-600: узлы, NAT Gateway, балансировщики, диски, логи и трафик между AZ.

**Можно ли сделать кластер без узлов вообще?**
Да, на Fargate или Auto Mode: узлы появятся только под pod (в Fargate узлов нет вообще). Плата за control plane всё равно идёт.

**Что произойдёт, если не обновлять версию?**
После 14 месяцев кластер уходит в extended support и стоит $0.60/час вместо $0.10. Ещё через 12 месяцев AWS обновит его принудительно.

**EKS сам обновляет узлы?**
В Auto Mode — да, и узел живёт максимум 21 день. В managed node group обновление AMI запускаешь ты (`update-nodegroup-version`), EKS делает rolling с уважением PDB. С Karpenter узлы заменяются по `expireAfter` и при дрейфе AMI.

**Нужен ли Cluster Autoscaler, если есть Karpenter?**
Нет, они решают одну задачу. Karpenter — современный выбор.

**Auto Mode и Karpenter одновременно?**
Можно смешивать Auto Mode-узлы с обычными node group в одном кластере, но два автоскейлера узлов на одну и ту же нагрузку не ставят: это конфликт.

**Почему pod получает IP из VPC, а не из overlay?**
Так работает Amazon VPC CNI. Плюсы: производительность, видимость в VPC, security groups для pod. Минус: IP-адреса подсети конечны.

**Сколько pod влезет на `t3.medium`?**
17, из которых значительная часть уйдёт на DaemonSet. Для реальной работы бери инстансы от `large`.

**Обязателен ли `aws-auth`?**
Нет. Используй access entries и режим `API`. В старых кластерах `aws-auth` ещё встречается, но это legacy.

**Можно ли дать доступ к кластеру без IAM?**
Нет: аутентификация в EKS идёт через IAM (или через OIDC-провайдера кластера для сервисных токенов). Людям доступ выдают через SSO-роли.

**Где хранить секреты?**
В AWS Secrets Manager или SSM Parameter Store, монтируя через Secrets Store CSI или синхронизируя через External Secrets. Kubernetes Secret включай в KMS-шифрование etcd и никогда не держи в Git.

**Надо ли держать базу в кластере?**
Обычно нет: RDS/Aurora дешевле по совокупным затратам и надёжнее без выделенной команды. В кластере держат БД, когда есть зрелый оператор и люди, которые умеют восстанавливать данные.

**Что делать с Ingress-NGINX?**
Апстрим снял его с поддержки в марте 2026 года. Планируй миграцию на Gateway API или ALB Ingress; drop-in замены нет, это инженерная работа.

**Кластер можно перенести в другой VPC или регион?**
Нет. Кластер создаётся в конкретном VPC и регионе. «Перенос» — это новый кластер и миграция нагрузки (что как раз хорошо получается при GitOps).

**Можно ли поменять подсети существующего кластера?**
Добавить подсети для узлов можно; сменить набор подсетей control plane — нет. Планируй адресацию заранее.

**Работает ли EKS с on-prem?**
Да: **EKS Hybrid Nodes** подключают твои серверы (или edge-железо) к control plane в AWS, оплата за vCPU. Есть также EKS Anywhere для полностью локальных кластеров.

**Как понять, кто удалил Deployment?**
Только по аудит-логам control plane. Если они не были включены — не узнаешь. Включи их сегодня.

**Почему pod висит в `Pending`, хотя узлы есть?**
Пять частых причин: не хватает CPU/памяти по `requests`, taint без toleration, PVC в другой AZ, кончились IP, не проходит topology spread с `DoNotSchedule`. Ответ всегда в `kubectl describe pod`.

**EKS или ECS для нового проекта?**
Если нужна экосистема Kubernetes, переносимость или уже есть компетенция — EKS. Если несколько простых сервисов и только AWS — ECS будет дешевле в эксплуатации.

**Сколько кластеров держать?**
Минимум два: prod и non-prod, в разных аккаунтах. Дальше по мере надобности: регуляторика, регионы, изоляция команд.

---

# Глоссарий EKS

| Термин | Значение |
|---|---|
| **Control plane** | Управляемая AWS часть: apiserver, etcd, scheduler, controller-manager |
| **Data plane** | Твои узлы и pod |
| **EKS-owned ENI** | Сетевой интерфейс в твоей подсети, через который control plane ходит к kubelet |
| **Cluster SG** | Security group `eks-cluster-sg-*`, объединяющая кластер и узлы |
| **Cluster IAM role** | Роль, от имени которой EKS управляет ресурсами в твоём аккаунте |
| **Node IAM role** | Роль инстанса узла (ECR, CNI, SSM) |
| **Access entry** | Запись EKS API, связывающая IAM-принципала с правами в кластере |
| **Access policy** | Готовый набор прав EKS (`AmazonEKSClusterAdminPolicy` и другие) |
| **aws-auth** | Устаревший ConfigMap маппинга IAM → Kubernetes |
| **authenticationMode** | `CONFIG_MAP`, `API_AND_CONFIG_MAP` или `API` |
| **IRSA** | IAM Roles for Service Accounts через OIDC-провайдер кластера |
| **EKS Pod Identity** | Современный способ выдать pod IAM-роль, через агент и association |
| **Session policy** | Сужение прав конкретной Pod Identity association без новой роли |
| **Managed node group** | Группа узлов, которой управляет EKS (ASG + drain + health) |
| **Self-managed node** | Узел в твоей ASG, который ты сам регистрируешь и патчишь |
| **Fargate profile** | Правило, по которому pod из namespace/меток попадают на Fargate |
| **EKS Auto Mode** | Режим, где AWS управляет узлами, storage, LB и идентичностью |
| **Karpenter** | Автоскейлер узлов, создающий EC2 напрямую под неразмещённые pod |
| **NodePool / EC2NodeClass** | Правила Karpenter: что за узлы и из чего их собирать |
| **NodeClaim** | Запрос Karpenter на конкретный узел |
| **Consolidation** | Уплотнение нагрузки и удаление лишних узлов |
| **Drift** | Расхождение узла с желаемой конфигурацией (например, новый AMI) |
| **Disruption budget** | Лимит на число одновременно нарушаемых узлов |
| **VPC CNI** | Плагин сети, выдающий pod реальные IP из VPC |
| **Prefix delegation** | Выдача ENI блоков /28 вместо отдельных IP |
| **Custom networking** | Размещение pod в отдельных подсетях (secondary CIDR) через ENIConfig |
| **Security groups for pods** | Branch ENI с отдельной SG для конкретного pod |
| **max pods** | Лимит pod на узел, зависящий от ENI и IP |
| **AWS Load Balancer Controller** | Контроллер, создающий ALB по Ingress и NLB по Service |
| **Target type: ip** | Регистрация pod в target group напрямую |
| **Readiness gate** | Условие готовности pod по подтверждению от ALB |
| **Gateway API** | Современная замена Ingress с ролевым разделением |
| **EBS CSI / EFS CSI / Mountpoint S3** | Драйверы хранилищ |
| **WaitForFirstConsumer** | Режим, при котором том создаётся в AZ pod |
| **VolumeSnapshot** | Снапшот PV через CSI |
| **PSS (Pod Security Standards)** | Уровни `privileged`, `baseline`, `restricted` на namespace |
| **NetworkPolicy** | Правила сетевого доступа между pod |
| **Admin Policy** | Сетевая политика уровня кластера, приоритетнее пользовательских |
| **EKS add-on** | Компонент, версией которого управляет EKS API |
| **EKS Capabilities** | Управляемые платформенные компоненты (Argo CD, ACK, kro) |
| **Provisioned Control Plane** | Предоплаченные тиры производительности control plane (XL...8XL), SLA 99.99% |
| **EKS Hybrid Nodes** | Узлы вне AWS под управлением control plane EKS |
| **Cluster insights** | Автоматические проверки готовности к апгрейду |
| **Standard / Extended support** | 14 месяцев по $0.10/час и ещё 12 по $0.60/час |
| **Platform version** | Внутренняя версия EKS (`eks.5`) внутри минора Kubernetes |
| **Container Insights** | Метрики и логи кластера в CloudWatch |
| **ADOT** | Дистрибутив OpenTelemetry от AWS |
| **AMP / AMG** | Managed Prometheus и Managed Grafana |
| **GuardDuty EKS Protection** | Анализ аудит-логов и runtime-мониторинг угроз |
| **Velero** | Инструмент бэкапа и восстановления объектов Kubernetes и PV |

---

# Официальные источники и что читать дальше

- **Документация EKS** — https://docs.aws.amazon.com/eks/latest/userguide/
- **EKS Best Practices Guides** (обязательно к прочтению: security, reliability, cost, networking) — https://docs.aws.amazon.com/eks/latest/best-practices/
- **Календарь версий и lifecycle** — https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html
- **Цены EKS** — https://aws.amazon.com/eks/pricing/
- **EKS Workshop** (лучший практикум от AWS) — https://www.eksworkshop.com
- **eksctl** — https://eksctl.io
- **Terraform EKS module** — https://github.com/terraform-aws-modules/terraform-eks
- **EKS Blueprints** — https://github.com/aws-ia/terraform-aws-eks-blueprints
- **Karpenter** — https://karpenter.sh
- **AWS Load Balancer Controller** — https://kubernetes-sigs.github.io/aws-load-balancer-controller/
- **Amazon VPC CNI** — https://github.com/aws/amazon-vpc-cni-k8s
- **EKS-optimized AMI** — https://github.com/awslabs/amazon-eks-ami
- **Containers-блог AWS** — https://aws.amazon.com/blogs/containers/
- **Что нового в EKS** — https://aws.amazon.com/about-aws/whats-new/containers/
- **Документация Kubernetes** — https://kubernetes.io/docs/
- **Gateway API** — https://gateway-api.sigs.k8s.io
- **Argo CD** — https://argo-cd.readthedocs.io
- **KEDA** — https://keda.sh
- **Velero** — https://velero.io
- **Kyverno** — https://kyverno.io
- **OpenCost** — https://www.opencost.io

---

## Как помочь проекту

Нашёл ошибку, неточность или устаревшую настройку? Открывай issue или присылай pull request. Особенно ценны:

- разборы реальных инцидентов в EKS и постмортемы;
- примеры на CDK, Pulumi, CloudFormation в дополнение к Terraform и eksctl;
- уточнения по новым версиям EKS, аддонов и Karpenter;
- цифры по стоимости из реальных счетов (с обезличенными деталями).

⭐ Если курс помог, поставь звезду: так его найдут другие инженеры.

**Лицензия:** материалы курса распространяются свободно, используй их для обучения, внутренних воркшопов и подготовки к собеседованиям.

**Дисклеймер:** цены указаны для региона us-east-1 на сентябрь 2026 года и служат ориентиром — всегда проверяй актуальные значения на странице цен AWS. Версии Kubernetes и сроки поддержки сверяй с официальным календарём версий EKS.
