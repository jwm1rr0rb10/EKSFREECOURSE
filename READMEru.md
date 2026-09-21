# AWS EKS курс 2026: бесплатный курс по Kubernetes на AWS с нуля до продакшена на русском

Этот курс — практическое пошаговое погружение в Amazon EKS (Elastic Kubernetes Service): от объяснения "зачем это вообще нужно" до продакшен-архитектуры, автоскейлинга, безопасности и итогового проекта.

Курс написан так, чтобы его можно было проходить последовательно, модуль за модулем, копируя команды и запуская их у себя.

## Для кого этот курс по EKS

- Для бэкенд- и DevOps-инженеров, которые работают с Kubernetes, но ни разу не разворачивали его в AWS
- Для тех, кто уже знает `kubectl` и голый Kubernetes (kind/minikube), но не понимает, чем EKS отличается от "просто кластера"
- Для инженеров, которые администрируют self-managed Kubernetes и хотят разобраться, что EKS берёт на себя, а что остаётся на вас
- Для SRE, которым нужно быстро закрыть пробелы перед продакшен-эксплуатацией EKS
- Для тех, кто готовится к собеседованию, где спрашивают про EKS, IRSA, Karpenter, VPC CNI

Курс не рассчитан на людей, которые вообще не знакомы с Kubernetes и Docker — базовые понятия (под, деплоймент, сервис, namespace) здесь не объясняются с нуля.

## Что ты будешь уметь после курса

- Поднимать кластер EKS через `eksctl` и через Terraform, понимать, что создаётся под капотом
- Разбираться в архитектуре EKS: control plane, managed node groups, self-managed узлы, Fargate
- Настраивать сеть: VPC CNI, security groups для подов, Load Balancer Controller, Ingress
- Настраивать доступ подов к AWS-сервисам через IRSA и EKS Pod Identity — без ключей в коде
- Подключать постоянное хранилище через EBS CSI и EFS CSI драйверы
- Настраивать автоскейлинг узлов (Cluster Autoscaler, Karpenter) и подов (HPA, VPA)
- Строить observability: CloudWatch Container Insights, Prometheus + Grafana
- Настраивать CI/CD: ECR, GitHub Actions, ArgoCD (GitOps)
- Работать с секретами через Secrets Manager и External Secrets Operator
- Обновлять кластер без даунтайма и проводить disaster recovery через Velero
- Закрывать базовую безопасность: Pod Security Standards, Network Policies, GuardDuty for EKS
- Считать и оптимизировать стоимость кластера
- Понимать типичные вопросы с собеседований по EKS и уверенно на них отвечать

## Содержание

- Модуль 0. Что такое EKS и зачем он нужен
- Модуль 1. Архитектура EKS: control plane, узлы, VPC
- Модуль 2. Установка: eksctl, kubectl, первый кластер
- Модуль 3. Kubernetes-объекты глазами EKS: namespace, deployment, service
- Модуль 4. Node groups: Managed, Self-managed, Fargate
- Модуль 5. Сеть в EKS: VPC CNI, security groups, ENI
- Модуль 6. IAM и EKS: IRSA и Pod Identity
- Модуль 7. Хранилище: EBS CSI, EFS CSI, StorageClass
- Модуль 8. Автоскейлинг: Cluster Autoscaler, Karpenter, HPA/VPA
- Модуль 9. Ingress и балансировка: AWS Load Balancer Controller
- Модуль 10. Логи и метрики: CloudWatch, Prometheus, Grafana
- Модуль 11. CI/CD: ECR, GitHub Actions, ArgoCD
- Модуль 12. Секреты и конфигурация
- Модуль 13. Multi-cluster и мульти-аккаунт
- Модуль 14. Обновление и обслуживание кластера
- Модуль 15. Стоимость и оптимизация
- Модуль 16. Безопасность EKS
- Модуль 17. Disaster recovery и backup
- Модуль 18. EKS в продакшене: чек-лист
- Модуль 19. Итоговый проект: развёртывание микросервисного приложения
- Шпаргалка eksctl / kubectl / IAM
- Вопросы на собеседовании по EKS с ответами
- FAQ: частые вопросы про EKS
- Глоссарий EKS
- Официальные источники и что читать дальше

## Как проходить курс

1. Читай модуль целиком, не пропуская объяснения "зачем", а не только "как"
2. Выполняй команды из модуля в своём AWS-аккаунте (лучше в отдельном sandbox-аккаунте или с бюджетным алертом — EKS control plane платный)
3. Делай "Практику" в конце модуля — без неё материал не закрепится
4. Отвечай на "Вопросы для самопроверки", не подглядывая — если не получилось, вернись и перечитай раздел
5. Не пытайся выучить весь курс за один день — модуль в день/два вполне нормальный темп

---

# Модуль 0. Что такое EKS и зачем он нужен

## 0.1 Определение EKS простыми словами

Amazon EKS (Elastic Kubernetes Service) — это управляемый Kubernetes от AWS. AWS берёт на себя control plane: `kube-apiserver`, `etcd`, `kube-scheduler`, `kube-controller-manager` — разворачивает их в высокодоступной конфигурации, патчит, бэкапит `etcd`, следит, чтобы API сервер отвечал.

Вы, в свою очередь, отвечаете за:
- worker-узлы (если не используете Fargate) — их ОС, патчи, kubelet
- то, что вы на этот кластер накатываете — деплойменты, конфигурацию, сеть подов
- интеграцию с остальным AWS: IAM, VPC, ELB, EBS, CloudWatch

EKS — это не "свой Kubernetes", это "Kubernetes API, за инфраструктуру которого частично отвечает AWS".

## 0.2 Проблема, которую решает EKS

Если разворачивать Kubernetes самостоятельно (kubeadm на EC2), вам придётся отдельно решать:

- Как сделать `etcd` отказоустойчивым и научиться его бэкапить
- Как обновлять control plane без простоя API
- Как выдавать сертификаты и ротировать их
- Как интегрировать кластер с IAM, VPC, Load Balancer'ами AWS — вручную, через collections костылей
- Как патчить control plane при новых CVE в Kubernetes

Каждая из этих задач — не "один раз настроил и забыл", а постоянная операционная нагрузка. EKS снимает её с control plane и даёт готовую интеграцию с остальным AWS "из коробки" через официальные аддоны.

## 0.3 Как выглядит система без EKS и с EKS

**Без EKS (self-managed kubeadm-кластер на EC2):**

```
[Вы отвечаете за всё]
  EC2 (control plane x3) --- etcd (бэкапы, TLS, апгрейды — вручную)
  EC2 (worker nodes)     --- kubelet, CNI, патчи ОС — вручную
  Балансировщик до kube-apiserver — вручную
  Интеграция с IAM для подов — самописный webhook (kiam/kube2iam) или ничего
```

**С EKS:**

```
[AWS отвечает]                        [Вы отвечаете]
  Managed control plane                 Worker nodes (EC2) или Fargate
  Multi-AZ etcd, бэкапы, патчи          Приложения, манифесты
  Managed API endpoint + TLS            Аддоны, конфигурация сети
                                         IAM-роли для подов (IRSA)
```

Работа с кластером через `kubectl` не меняется — EKS отдаёт стандартный Kubernetes API. Разница именно в том, кто и что администрирует под капотом.

## 0.4 EKS vs самостоятельный Kubernetes vs ECS

| | EKS | Self-managed K8s | ECS |
|---|---|---|---|
| Control plane | Управляет AWS | Управляете вы | Нет control plane K8s вообще |
| API | Стандартный Kubernetes API | Стандартный Kubernetes API | Проприетарный API AWS |
| Переносимость | Высокая (портируемые манифесты) | Высокая | Только AWS |
| Экосистема | Весь helm/CNCF-стек | Весь helm/CNCF-стек | Только то, что сделал AWS |
| Порог входа | Нужно знать Kubernetes | Нужно знать Kubernetes + инфру control plane | Ниже, проще для простых сервисов |

EKS выбирают, когда команда уже инвестировала в Kubernetes-экосистему (Helm, операторы, CNCF-тулинг) и хочет портируемость между облаками, при этом не хочет самостоятельно тащить control plane.

## 0.5 Что такое control plane и data plane в терминах EKS

- **Control plane** — управляемая AWS часть: API server, etcd, scheduler, controller-manager. Живёт в отдельном AWS-managed VPC, вы её не видите как EC2-инстансы.
- **Data plane** — ваши worker-узлы (EC2 managed/self-managed node groups) или Fargate-поды. Именно здесь реально исполняются ваши контейнеры.

## 0.6 Что такое EKS Add-ons

EKS Add-ons — это официально поддерживаемые AWS компоненты кластера, которые устанавливаются и обновляются через EKS API, а не через `kubectl apply`/Helm вручную. Примеры: `vpc-cni`, `coredns`, `kube-proxy`, `aws-ebs-csi-driver`, `eks-pod-identity-agent`. Это снижает операционную нагрузку — AWS следит за совместимостью версий аддона и версии control plane.

## 0.7 EKS vs EKS Anywhere vs EKS on Outposts

- **EKS** — control plane в облаке AWS, узлы в облаке (или Fargate)
- **EKS Anywhere** — тот же Kubernetes-дистрибутив AWS, но control plane и узлы у вас на своём железе (on-prem, без обязательной связи с AWS control plane)
- **EKS on Outposts** — control plane в AWS, узлы физически стоят у вас (AWS Outposts), для сценариев с низкой задержкой или требованиями по локализации данных

В этом курсе речь именно про "классический" EKS в облаке AWS.

## 0.8 Где используют EKS: реальные сценарии

- Микросервисные бэкенды с десятками сервисов, где нужна гибкость Kubernetes-экосистемы (Helm-чарты, операторы для баз данных, service mesh)
- ML/AI пайплайны — обучение и инференс моделей на GPU-нодах с автоскейлингом
- Batch-обработка данных с Fargate или Karpenter под спот-инстансы
- Мультитенантные SaaS-платформы, где namespace + network policy изолируют клиентов
- Компании, которые хотят единый Kubernetes API поверх нескольких облаков/on-prem

## 0.9 Когда EKS не нужен

- У вас один простой монолитный сервис — дешевле и проще App Runner, Elastic Beanstalk или ECS Fargate
- Команда никогда не работала с Kubernetes, а сроки горят — кривая обучения Kubernetes сама по себе немаленькая, EKS её не убирает
- Бюджет крайне ограничен, а нагрузка низкая — постоянная плата за control plane (см. модуль 15) может быть неоправданна для одного маленького сервиса

## 0.10 Что EKS НЕ делает за вас

- Не патчит ОС ваших worker-узлов автоматически (если это не Fargate или Bottlerocket с managed-обновлениями через отдельный механизм)
- Не настраивает сеть подов и security groups за вас — базовые правила придётся продумать самим
- Не даёт автоскейлинг из коробки — Cluster Autoscaler/Karpenter и HPA нужно ставить и настраивать отдельно
- Не решает вопросы стоимости — легко получить кластер с overprovisioned узлами, если не следить

### Вопросы для самопроверки

1. Что именно берёт на себя AWS в модели EKS, а что остаётся на вас?
2. Чем EKS отличается от ECS с точки зрения API?
3. Что такое EKS Add-ons и зачем они нужны, если можно поставить то же самое через Helm?
4. В каком сценарии EKS — избыточное решение?

---

# Модуль 1. Архитектура EKS: control plane, узлы, VPC

## 1.1 Общая картина

```
                    ┌─────────────────────────────┐
                    │   EKS Control Plane (AWS)    │
                    │  kube-apiserver (multi-AZ)   │
                    │  etcd (managed, зашифрован)  │
                    │  scheduler / controller-mgr  │
                    └──────────────┬───────────────┘
                                   │ ENI в вашем VPC
                    ┌──────────────┴───────────────┐
                    │           Ваш VPC             │
        ┌───────────┴──────────┐      ┌────────────┴───────────┐
        │  Private subnets      │      │   Public subnets       │
        │  Managed node group   │      │   NAT Gateway,         │
        │  Fargate profile      │      │   Load Balancer'ы      │
        └────────────────────────┘      └─────────────────────────┘
```

Control plane физически живёт в AWS-managed VPC, но подключается к вашему VPC через Elastic Network Interfaces (ENI), которые EKS создаёт в указанных вами подсетях. Именно поэтому при создании кластера вы обязаны указать subnets — control plane должен дотянуться до узлов.

## 1.2 Основные компоненты кластера EKS

- **Control plane** — managed API server + etcd, endpoint приватный и/или публичный
- **Node groups** — группы worker-узлов (managed или self-managed EC2)
- **Fargate profiles** — бессерверные поды без EC2 вообще
- **VPC CNI** — плагин, который выдаёт подам реальные IP из VPC
- **CoreDNS** — DNS внутри кластера
- **kube-proxy** — правила маршрутизации для Service
- **IAM** — интеграция через OIDC provider кластера (для IRSA/Pod Identity)
- **EKS Add-ons** — управляемые версии всего вышеперечисленного

## 1.3 VPC требования для EKS

Кластеру нужен VPC с:
- Минимум 2 подсети в разных Availability Zones (рекомендуется 3)
- Публичные подсети — если нужен публичный доступ (NAT Gateway, публичные Load Balancer'ы)
- Приватные подсети — для worker-узлов (best practice: узлы не должны иметь публичные IP)
- Достаточным количеством свободных IP — VPC CNI выдаёт под реальный IP из подсети, поэтому при большом количестве подов IP-пространство может закончиться быстрее, чем ожидаете

## 1.4 Endpoint access: публичный, приватный, оба

Control plane endpoint (адрес, куда стучится `kubectl`) можно настроить тремя способами:

- **Public only** — доступ отовсюду по интернету (можно ограничить CIDR-блоками), узлы внутри VPC достают control plane через публичный интернет
- **Private only** — доступ только из VPC (через VPN/Direct Connect/bastion), максимально безопасно, но `kubectl` с ноутбука напрямую не подключится
- **Public + Private** — узлы общаются с control plane внутри VPC (низкая задержка, не через интернет), а разработчики подключаются через публичный endpoint (обычно ограниченный по IP)

Для продакшена почти всегда выбирают Public + Private с ограничением публичного доступа по allowlisted CIDR, либо чисто Private с доступом через VPN.

## 1.5 Availability Zones и отказоустойчивость

AWS размещает control plane как минимум в 2 AZ автоматически. Ваша задача — растянуть worker-узлы минимум на 2-3 AZ, чтобы при падении одной зоны кластер продолжил работать. Это настраивается на уровне node group (список subnet'ов из разных AZ).

## 1.6 Версии Kubernetes в EKS

AWS поддерживает несколько последних минорных версий Kubernetes (стандартная поддержка — около 14 месяцев с релиза, затем можно продлить через Extended Support за дополнительную плату). Важно понимать:

- Апгрейд control plane и апгрейд node group — раздельные операции
- Нельзя пропускать более одной минорной версии за раз при апгрейде (1.28 → 1.29 → 1.30, не 1.28 → 1.30 напрямую)
- Аддоны (VPC CNI, CoreDNS, kube-proxy) тоже привязаны к версии и их нужно обновлять synchронно с control plane

## 1.7 Ключевые лимиты кластера

- До 100 нод по умолчанию в managed node group (можно увеличить через service quota)
- Количество подов на узле ограничено типом инстанса (зависит от числа ENI и IP на ENI — это особенность VPC CNI, подробнее в модуле 5)
- IP-адреса — самый частый практический лимит: если VPC/подсеть маленькая, а подов много, кластер упрётся в нехватку IP раньше, чем в лимиты CPU/памяти

## 1.8 Аккаунты и мультитенантность внутри кластера

В одном EKS-кластере можно изолировать команды/окружения через:
- `Namespace` — базовая логическая изоляция
- `NetworkPolicy` — сетевая изоляция между namespace
- `ResourceQuota` / `LimitRange` — ограничение ресурсов на namespace
- IAM-роли через IRSA/Pod Identity — разные namespace получают разные права в AWS

Полная жёсткая изоляция (как отдельные "аккаунты" в NATS) в Kubernetes сложнее — обычно для сильной мультитенантности делают отдельные кластеры на команду/окружение, а не один общий.

## 1.9 Первая ментальная модель

Думайте про EKS так: "это Kubernetes API, за здоровье которого отвечает AWS, а за то, что на этот API накатывается — отвечаете вы". Всё, что вы знаете про голый Kubernetes, работает и здесь. Специфика EKS — это стык между Kubernetes и остальным AWS: сеть (VPC CNI), права (IAM/IRSA), балансировка (ALB Controller), хранилище (EBS/EFS CSI), логи (CloudWatch).

### Вопросы для самопроверки

1. Через что control plane EKS общается с вашими worker-узлами?
2. Чем отличается Public и Private endpoint access и когда какой выбирать?
3. Почему нельзя перепрыгнуть через минорную версию Kubernetes при апгрейде?
4. Какой ресурс в VPC чаще всего становится узким местом при масштабировании подов?

---

# Модуль 2. Установка: eksctl, kubectl, первый кластер

## 2.1 Что понадобится

- AWS CLI, настроенный с рабочими credentials (`aws configure`)
- `kubectl`
- `eksctl` — CLI-инструмент от Weaveworks/AWS, который оборачивает CloudFormation и сильно упрощает создание кластера

```bash
# macOS
brew install eksctl kubectl awscli

# Linux
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"
tar -xzf eksctl_Linux_amd64.tar.gz -C /tmp && sudo mv /tmp/eksctl /usr/local/bin

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

## 2.2 Самый быстрый способ поднять кластер

```bash
eksctl create cluster \
  --name demo-cluster \
  --region eu-central-1 \
  --version 1.30 \
  --nodegroup-name standard-workers \
  --node-type t3.medium \
  --nodes 2 \
  --nodes-min 1 \
  --nodes-max 4 \
  --managed
```

Эта одна команда создаст: VPC с публичными и приватными подсетями, control plane, managed node group на 2 EC2-инстанса, настроит IAM-роли, security groups и OIDC provider. Займёт это 15-20 минут — control plane разворачивается не мгновенно.

## 2.3 Создание кластера декларативно через конфиг-файл

В продакшене лучше не пользоваться флагами, а описывать кластер в YAML — это переиспользуемо и попадает в git.

```yaml
# cluster.yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: demo-cluster
  region: eu-central-1
  version: "1.30"

vpc:
  cidr: 10.0.0.0/16
  nat:
    gateway: Single

managedNodeGroups:
  - name: standard-workers
    instanceType: t3.medium
    minSize: 1
    maxSize: 4
    desiredCapacity: 2
    privateNetworking: true
    labels:
      role: worker
    tags:
      environment: dev

addons:
  - name: vpc-cni
  - name: coredns
  - name: kube-proxy
  - name: aws-ebs-csi-driver

iam:
  withOIDC: true
```

```bash
eksctl create cluster -f cluster.yaml
```

`withOIDC: true` — критично важная строчка: без OIDC provider не заработает IRSA (модуль 6).

## 2.4 Подключение kubectl к кластеру

```bash
aws eks update-kubeconfig --region eu-central-1 --name demo-cluster

kubectl get nodes
kubectl get pods -A
```

`update-kubeconfig` добавляет в `~/.kube/config` запись с exec-плагином `aws eks get-token`, который на лету генерирует краткоживущий токен аутентификации через IAM — отдельного пароля к кластеру нет, доступ полностью завязан на IAM.

## 2.5 Кто имеет доступ к кластеру

Доступ к Kubernetes API в EKS управляется через `aws-auth` ConfigMap (в старых кластерах) или через Access Entries (современный способ, рекомендуемый AWS):

```bash
# современный способ — Access Entries
aws eks create-access-entry \
  --cluster-name demo-cluster \
  --principal-arn arn:aws:iam::123456789012:user/jane \
  --type STANDARD

aws eks associate-access-policy \
  --cluster-name demo-cluster \
  --principal-arn arn:aws:iam::123456789012:user/jane \
  --access-scope type=cluster \
  --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSAdminPolicy
```

Важно: тот, кто создал кластер, получает доступ автоматически. Все остальные IAM-пользователи/роли — только через Access Entries (или устаревший `aws-auth` ConfigMap).

## 2.6 Самая частая ошибка запуска

`kubectl get nodes` ничего не возвращает или зависает — почти всегда одна из причин:
- Не выполнили `aws eks update-kubeconfig`, kubeconfig смотрит не туда
- IAM-принципал, под которым вы работаете, не добавлен в Access Entries/aws-auth
- Узлы ещё не присоединились к кластеру (проверить `eksctl get nodegroup`)
- Security group control plane не пускает узлы (если кластер создавался не через eksctl, а руками)

## 2.7 Где EKS хранит состояние

Само состояние Kubernetes (объекты, их статусы) — в managed `etcd`, который вы не видите напрямую. Единственный способ туда попасть — через Kubernetes API. Прямого доступа к `etcd`, снапшотов через AWS Console нет — бэкап состояния кластера делается на уровне ваших манифестов (держите их в git) и через инструменты вроде Velero (модуль 17), которые бэкапят объекты через API, а не сам etcd.

## 2.8 Первый деплоймент и первый Service

```bash
kubectl create deployment nginx --image=nginx:1.27 --replicas=2
kubectl expose deployment nginx --port=80 --type=LoadBalancer

kubectl get svc nginx -w
# дождитесь EXTERNAL-IP — это будет DNS-имя classic/network load balancer
```

Через минуту-две в поле `EXTERNAL-IP` появится DNS-имя ELB — AWS Load Balancer создался автоматически, потому что в кластере уже работает встроенный in-tree cloud provider (для полноценного управления ALB/NLB в продакшене используют AWS Load Balancer Controller, модуль 9).

### Практика

1. Поднимите кластер через `eksctl` с конфиг-файлом на 2 узла
2. Подключите `kubectl`, убедитесь, что видите узлы через `kubectl get nodes`
3. Задеплойте `nginx`, обнажите его через `Service` типа `LoadBalancer`, откройте в браузере
4. Добавьте второго IAM-пользователя через Access Entries с правами только на чтение (`AmazonEKSViewPolicy`), проверьте, что он не может удалять поды

---

# Модуль 3. Kubernetes-объекты глазами EKS

## 3.1 Что не меняется

Все стандартные объекты Kubernetes работают в EKS так же, как в любом другом дистрибутиве: `Pod`, `Deployment`, `StatefulSet`, `DaemonSet`, `Job`, `CronJob`, `ConfigMap`, `Secret`, `Namespace`, `Service`, `Ingress`. Если вы умеете писать манифесты для kind/minikube — 90% этого опыта переносится напрямую.

## 3.2 Что специфично для EKS в стандартных объектах

- `Service` типа `LoadBalancer` — создаёт реальный Classic/Network Load Balancer в AWS
- `Ingress` — по умолчанию ничего не делает, пока не поставлен ingress-контроллер (в EKS обычно AWS Load Balancer Controller, модуль 9)
- `StorageClass` — по умолчанию есть `gp2`/`gp3` через EBS CSI Driver (если аддон установлен)
- `ServiceAccount` — получает особый смысл через аннотацию `eks.amazonaws.com/role-arn` для IRSA (модуль 6)
- Метки узлов (`node.kubernetes.io/instance-type`, `topology.kubernetes.io/zone`) автоматически проставляются EKS и полезны для `nodeSelector`/`affinity`

## 3.3 Namespace как единица организации в EKS

```bash
kubectl create namespace payments
kubectl create namespace analytics

kubectl config set-context --current --namespace=payments
```

Типичная практика: namespace на команду или на окружение (`payments-dev`, `payments-staging`, `payments-prod`), с `ResourceQuota` на каждый:

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: payments-quota
  namespace: payments
spec:
  hard:
    requests.cpu: "10"
    requests.memory: 20Gi
    limits.cpu: "20"
    limits.memory: 40Gi
    pods: "50"
```

## 3.4 Deployment: базовый пример с requests/limits

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: payments-api
  namespace: payments
spec:
  replicas: 3
  selector:
    matchLabels:
      app: payments-api
  template:
    metadata:
      labels:
        app: payments-api
    spec:
      containers:
        - name: payments-api
          image: 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:1.4.2
          ports:
            - containerPort: 8080
          resources:
            requests:
              cpu: 250m
              memory: 256Mi
            limits:
              cpu: 500m
              memory: 512Mi
          readinessProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 5
          livenessProbe:
            httpGet:
              path: /health
              port: 8080
            initialDelaySeconds: 15
```

`requests` критичны в EKS не меньше, чем везде — именно по ним планировщик и Cluster Autoscaler/Karpenter решают, влезает ли под на узел (модуль 8).

## 3.5 Affinity и распределение по зонам

Чтобы приложение не легло целиком при падении одной AZ:

```yaml
spec:
  template:
    spec:
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          labelSelector:
            matchLabels:
              app: payments-api
```

## 3.6 Таргетирование Fargate vs EC2-узлов

Если в кластере есть и Fargate profile, и обычные node groups, под попадает на Fargate только если matches его selector'у (по namespace + опционально label). Иначе планировщик отправит его на обычный EC2-узел. Подробнее — модуль 4.

### Практика

1. Создайте namespace с ResourceQuota на 4 CPU / 8Gi
2. Задеплойте приложение с requests/limits и readiness/liveness пробами
3. Добавьте `topologySpreadConstraints`, задеплойте с 3 репликами, проверьте через `kubectl get pods -o wide`, что поды разъехались по разным зонам

### Вопросы для самопроверки

1. Что из стандартных Kubernetes-объектов в EKS "просто работает", а что требует дополнительных контроллеров/аддонов?
2. Зачем нужна аннотация `eks.amazonaws.com/role-arn` на ServiceAccount?
3. Как заставить Kubernetes не сажать все реплики деплоймента в одну AZ?

---

# Модуль 4. Node groups: Managed, Self-managed, Fargate

## 4.1 Три способа получить вычислительные мощности

| | Managed Node Group | Self-managed nodes | Fargate |
|---|---|---|---|
| Кто патчит ОС | AWS (по требованию, вы жмёте "обновить") | Вы сами | AWS полностью |
| Автоскейлинг узлов | Через ASG + Cluster Autoscaler/Karpenter | Через ASG + Cluster Autoscaler | Не нужен, под = своя "нода" |
| Кастомный AMI | Ограниченно | Полностью свой | Недоступно |
| DaemonSet | Работает | Работает | Не работает |
| hostNetwork/privileged | Работает | Работает | Не работает |
| Биллинг | За EC2-инстансы целиком | За EC2-инстансы целиком | За vCPU/память конкретного пода |

## 4.2 Managed Node Group

Самый частый выбор по умолчанию. AWS управляет Auto Scaling Group, обновлением AMI (когда вы инициируете), grace-full drain при обновлении узлов.

```bash
eksctl create nodegroup \
  --cluster demo-cluster \
  --name spot-workers \
  --instance-types t3.medium,t3a.medium \
  --spot \
  --nodes 2 --nodes-min 0 --nodes-max 10 \
  --node-private-networking
```

Смешивание нескольких типов инстансов (`--instance-types`) в spot-группе снижает риск одновременного вытеснения всех узлов при нехватке конкретного типа spot-инстансов.

## 4.3 Self-managed nodes

Нужны, когда требуется что-то, чего managed node group не даёт: специфичный кастомный AMI, нестандартный bootstrap-скрипт, интеграция с уже существующей ASG. Создаётся через launch template + собственную Auto Scaling Group, присоединяется к кластеру через `bootstrap.sh` в user-data:

```bash
#!/bin/bash
/etc/eks/bootstrap.sh demo-cluster \
  --kubelet-extra-args '--node-labels=role=custom'
```

Используйте self-managed, только если у вас реальная причина — иначе Managed Node Group отнимает меньше операционного времени.

## 4.4 Fargate profiles

```yaml
# добавка к cluster.yaml
fargateProfiles:
  - name: fp-batch
    selectors:
      - namespace: batch-jobs
        labels:
          run-on: fargate
```

```bash
eksctl create fargateprofile \
  --cluster demo-cluster \
  --name fp-batch \
  --namespace batch-jobs
```

Каждый под на Fargate получает изолированную "микро-ВМ" — под живёт как бы на собственном узле. Ограничения: нет `DaemonSet`, нет `hostPort`, нет `hostNetwork`, максимум 4 vCPU / 16 GB на под (на момент написания курса — проверяйте актуальные лимиты), нет GPU.

Fargate хорошо подходит для: batch-джобов с непредсказуемой нагрузкой, приложений с редкими всплесками, когда не хочется держать простаивающие EC2, и для случаев, когда вообще не хочется администрировать узлы.

## 4.5 Bottlerocket — специализированная ОС для узлов

AWS также предлагает Bottlerocket — минималистичный Linux-дистрибутив, заточенный именно под запуск контейнеров: меньше поверхность атаки, immutable root filesystem, автообновления через отдельный оператор.

```yaml
managedNodeGroups:
  - name: bottlerocket-workers
    amiFamily: Bottlerocket
    instanceType: m5.large
    desiredCapacity: 3
```

## 4.6 Taints и tolerations для разделения нагрузок

Чтобы GPU-узлы использовались только под ML-нагрузку, а не заняты случайным nginx:

```bash
kubectl taint nodes gpu-node-1 workload=ml:NoSchedule
```

```yaml
spec:
  tolerations:
    - key: "workload"
      operator: "Equal"
      value: "ml"
      effect: "NoSchedule"
  nodeSelector:
    workload-type: gpu
```

## 4.7 Как выбрать между managed EC2 и Fargate

- Стабильная, предсказуемая, долгоживущая нагрузка с DaemonSet'ами (логирование, мониторинг-агенты) → managed EC2
- Batch/cron задачи, спайковая нагрузка, желание вообще не думать про узлы → Fargate
- Смешанный кластер — обычная практика: часть namespace на Fargate, часть на managed node groups

### Практика

1. Добавьте в кластер вторую managed node group на spot-инстансах с несколькими типами инстансов
2. Создайте Fargate profile для namespace `batch-jobs` и задеплойте туда простой Job
3. Затейнтуйте один узел под конкретную нагрузку и убедитесь, что обычные поды туда не садятся

### Вопросы для самопроверки

1. Какие ограничения есть у Fargate, которых нет у managed node group?
2. Зачем указывать несколько `--instance-types` для spot node group?
3. В каком случае имеет смысл self-managed node group вместо managed?

---

# Модуль 5. Сеть в EKS: VPC CNI, security groups, ENI

## 5.1 Главная особенность: поды получают реальные IP из VPC

В отличие от многих self-managed Kubernetes-сетей (Calico с оверлеем, Flannel), стандартный AWS VPC CNI выдаёт каждому поду настоящий IP-адрес из вашей VPC-подсети. Это значит:
- Под виден в VPC напрямую, как обычный EC2-инстанс, к нему применяются VPC security groups и route tables
- Никакого NAT/оверлея между подами внутри кластера — трафик идёт напрямую по VPC
- Но: количество подов на узле ограничено количеством ENI и IP-адресов, которые может держать конкретный тип инстанса

## 5.2 Как VPC CNI резервирует IP

Каждый worker-узел резервирует пул IP-адресов заранее (через `ipamd`), чтобы под мог быстро подняться без ожидания выделения нового ENI. Формула лимита подов на узел зависит от типа инстанса:

```
Максимум подов = (число ENI на инстансе × (число IP на ENI − 1)) + 2
```

Например, `t3.medium` держит 3 ENI по 6 IP → около 17 подов максимум. Это частая причина, почему кластер "не может зашедулить под" при видимо свободном CPU/памяти — упёрлись в IP-лимит, а не в ресурсы.

## 5.3 Prefix Delegation — способ обойти лимит IP

Начиная с некоторой версии VPC CNI можно включить Prefix Delegation — тогда ENI резервирует не отдельные IP, а целые /28 префиксы (16 адресов разом), что резко увеличивает плотность подов на узле:

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_PREFIX_DELEGATION=true
```

## 5.4 Security groups для подов (Security Groups for Pods)

По умолчанию все поды на узле используют security group самого узла. Но иногда нужно, чтобы конкретный под (например, с доступом к RDS) имел собственные, более узкие правила:

```yaml
apiVersion: vpcresources.k8s.aws/v1beta1
kind: SecurityGroupPolicy
metadata:
  name: db-access
  namespace: payments
spec:
  podSelector:
    matchLabels:
      app: payments-api
  securityGroups:
    groupIds:
      - sg-0123456789abcdef0
```

Это позволяет не открывать RDS security group для всего узла целиком, а дать доступ точечно, только нужным подам.

## 5.5 Network Policy: изоляция трафика между подами

Сам по себе VPC CNI не блокирует трафик между подами (все поды видят друг друга по умолчанию). Чтобы включить `NetworkPolicy`, нужен либо встроенный network policy engine VPC CNI (можно включить флагом), либо Calico/Cilium поверх:

```bash
kubectl set env daemonset aws-node -n kube-system ENABLE_NETWORK_POLICY=true
```

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-from-other-namespaces
  namespace: payments
spec:
  podSelector: {}
  policyTypes: ["Ingress"]
  ingress:
    - from:
        - podSelector: {}
```

## 5.6 CoreDNS и внутрикластерный DNS

`payments-api.payments.svc.cluster.local` резолвится через CoreDNS — стандартный DaemonSet/Deployment, идущий аддоном EKS. При больших кластерах CoreDNS иногда становится узким местом — тогда включают `NodeLocal DNSCache` для снижения задержек резолва.

## 5.7 Выход в интернет: NAT Gateway

Узлы и поды в приватных подсетях выходят в интернет (скачать образ, обратиться к внешнему API) через NAT Gateway в публичной подсети. Один NAT Gateway на VPC — дешевле, но единая точка отказа при падении AZ; по одному NAT Gateway на AZ — надёжнее и дороже.

## 5.8 VPC Endpoints — трафик к AWS-сервисам без выхода в интернет

Чтобы поды могли обращаться к ECR, S3, Secrets Manager и т.д. не через NAT Gateway (дешевле и быстрее), настраивают VPC Endpoints:

```bash
aws ec2 create-vpc-endpoint \
  --vpc-id vpc-0123456789 \
  --service-name com.amazonaws.eu-central-1.ecr.api \
  --vpc-endpoint-type Interface \
  --subnet-ids subnet-aaa subnet-bbb \
  --security-group-ids sg-xxxxx
```

Особенно важно для приватного EKS-кластера (Private-only endpoint access) — без VPC endpoints к ECR/S3 узлы просто не смогут тянуть образы.

### Практика

1. Выясните формулу максимального числа подов для типа инстанса, который вы используете в кластере (`t3.medium` или другой)
2. Включите Prefix Delegation и сравните лимит подов на узле до/после
3. Создайте `SecurityGroupPolicy` для одного деплоймента, ограничив ему доступ отдельной security group
4. Настройте `NetworkPolicy`, запрещающую трафик между namespace `payments` и `analytics`

### Вопросы для самопроверки

1. Почему под в EKS может не запускаться, хотя на узле есть свободный CPU и память?
2. Что такое Prefix Delegation и какую проблему он решает?
3. Зачем нужны Security Groups for Pods, если есть security group самого узла?
4. Зачем настраивать VPC Endpoints, если уже есть NAT Gateway?

---

# Модуль 6. IAM и EKS: IRSA и Pod Identity

## 6.1 Проблема, которую решают IRSA и Pod Identity

Приложению в поде часто нужен доступ к AWS-сервисам — S3, DynamoDB, SQS. Наивные (плохие) варианты: зашить access key/secret key в переменные окружения, или дать всем узлам одну широкую IAM-роль, которую видят вообще все поды на узле. Оба варианта — дыра в безопасности.

Решение: дать конкретному Kubernetes `ServiceAccount` (а значит — конкретным подам) отдельную, узкую IAM-роль, без единого статического ключа.

## 6.2 IRSA (IAM Roles for Service Accounts) — как это работает

1. У кластера есть OIDC provider (включается флагом `withOIDC: true` при создании)
2. Создаётся IAM-роль с trust policy, разрешающей конкретному `ServiceAccount` в конкретном namespace её принимать
3. `ServiceAccount` в Kubernetes аннотируется ARN этой роли
4. Под, использующий этот `ServiceAccount`, при старте получает через mutating webhook переменные окружения и смонтированный токен, которые SDK (boto3, aws-sdk-go и т.д.) автоматически использует для `AssumeRoleWithWebIdentity`

```bash
eksctl create iamserviceaccount \
  --cluster demo-cluster \
  --namespace payments \
  --name payments-api-sa \
  --attach-policy-arn arn:aws:iam::123456789012:policy/PaymentsS3ReadOnly \
  --approve
```

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: payments-api-sa
  namespace: payments
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::123456789012:role/payments-api-role
```

```yaml
spec:
  template:
    spec:
      serviceAccountName: payments-api-sa
      containers:
        - name: payments-api
          image: ...
```

## 6.3 EKS Pod Identity — более новый и простой способ

EKS Pod Identity — механизм, пришедший на смену IRSA, проще в настройке и не требует "плясок" с OIDC trust policy на каждый ServiceAccount.

```bash
aws eks create-pod-identity-association \
  --cluster-name demo-cluster \
  --namespace payments \
  --service-account payments-api-sa \
  --role-arn arn:aws:iam::123456789012:role/payments-api-role
```

Роли достаточно доверять сервису `pods.eks.amazonaws.com`, без привязки к ARN конкретного OIDC provider кластера — это упрощает multi-cluster сценарии, где одна и та же роль используется в разных кластерах.

## 6.4 IRSA vs Pod Identity: когда что выбрать

| | IRSA | Pod Identity |
|---|---|---|
| Требует OIDC provider | Да | Нет |
| Настройка trust policy | На каждую роль отдельно, под конкретный кластер | Общая для сервиса `pods.eks.amazonaws.com` |
| Поддержка в старых кластерах | Везде | Только относительно новые версии EKS |
| Миграция между кластерами | Нужно переиздавать роли | Проще — роль не привязана к OIDC конкретного кластера |

Для новых кластеров AWS рекомендует начинать с Pod Identity, если версия EKS её поддерживает.

## 6.5 Принцип наименьших привилегий на практике

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject"],
      "Resource": "arn:aws:s3:::payments-invoices/*"
    }
  ]
}
```

Не давайте `s3:*` на `*` "чтобы не разбираться" — каждая роль пода должна иметь ровно те права, которые нужны конкретному сервису, не больше.

## 6.6 IAM-роли самих узлов vs роли подов

Узел (EC2-инстанс) имеет свою собственную node IAM role — минимально необходимую для работы kubelet (`AmazonEKSWorkerNodePolicy`, `AmazonEKS_CNI_Policy`, доступ к ECR на чтение). Эта роль НЕ должна содержать прав приложений — иначе любой под на узле сможет притвориться, что имеет эти права (через доступ к instance metadata service, если не защищён IMDSv2).

## 6.7 IMDSv2 — обязательно включайте

```bash
aws ec2 modify-instance-metadata-options \
  --instance-id i-0123456789 \
  --http-tokens required \
  --http-put-response-hop-limit 1
```

`http-put-response-hop-limit 1` дополнительно мешает поду достучаться до IMDS узла через сетевой хоп — важная защита в комбинации с широкой node role.

### Практика

1. Создайте IAM-политику с доступом на чтение к одному конкретному S3 bucket
2. Настройте IRSA (или Pod Identity, если версия кластера позволяет) для одного деплоймента
3. Проверьте из пода (`aws s3 ls s3://ваш-бакет`) что доступ есть, а к другому бакету — нет
4. Убедитесь, что IMDSv2 включён на узлах, и `http-put-response-hop-limit` равен 1

### Вопросы для самопроверки

1. Почему статические AWS-ключи в переменных окружения пода — плохая практика?
2. В чём принципиальная разница между IRSA и Pod Identity?
3. Что произойдёт, если дать node IAM role права приложения вместо роли пода?
4. Зачем ограничивать hop limit для instance metadata service?

---

# Модуль 7. Хранилище: EBS CSI, EFS CSI, StorageClass

## 7.1 Два основных сценария хранения

- **EBS (Elastic Block Store)** — блочное хранилище, привязано к одной AZ, монтируется только в один под одновременно (`ReadWriteOnce`). Подходит для баз данных, очередей с персистентностью.
- **EFS (Elastic File System)** — сетевая файловая система, доступна из нескольких AZ и нескольких подов одновременно (`ReadWriteMany`). Подходит для общих файлов, загрузок пользователей, шаренных конфигов.

## 7.2 Установка EBS CSI Driver

```bash
eksctl create addon \
  --cluster demo-cluster \
  --name aws-ebs-csi-driver \
  --service-account-role-arn arn:aws:iam::123456789012:role/AmazonEKS_EBS_CSI_DriverRole
```

Драйверу нужна собственная IAM-роль (через IRSA/Pod Identity) с правами создавать/удалять/монтировать EBS-тома.

## 7.3 StorageClass для EBS

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp3
provisioner: ebs.csi.aws.com
parameters:
  type: gp3
  encrypted: "true"
volumeBindingMode: WaitForFirstConsumer
reclaimPolicy: Delete
```

`volumeBindingMode: WaitForFirstConsumer` важен: том создаётся не сразу при `PersistentVolumeClaim`, а только когда планировщик решил, в какой AZ будет под — иначе можно создать том в AZ, где нет свободных узлов.

## 7.4 PersistentVolumeClaim и StatefulSet

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: postgres
spec:
  serviceName: postgres
  replicas: 1
  selector:
    matchLabels:
      app: postgres
  template:
    metadata:
      labels:
        app: postgres
    spec:
      containers:
        - name: postgres
          image: postgres:16
          volumeMounts:
            - name: data
              mountPath: /var/lib/postgresql/data
  volumeClaimTemplates:
    - metadata:
        name: data
      spec:
        accessModes: ["ReadWriteOnce"]
        storageClassName: gp3
        resources:
          requests:
            storage: 20Gi
```

В продакшене для реальной СУБД чаще берут managed RDS/Aurora вместо StatefulSet с EBS — но для очередей, кэшей с персистентностью, self-hosted баз этот паттерн абсолютно рабочий.

## 7.5 EFS CSI Driver для ReadWriteMany

```bash
eksctl create addon \
  --cluster demo-cluster \
  --name aws-efs-csi-driver \
  --service-account-role-arn arn:aws:iam::123456789012:role/AmazonEKS_EFS_CSI_DriverRole
```

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: efs-sc
provisioner: efs.csi.aws.com
parameters:
  fileSystemId: fs-0123456789abcdef0
  directoryPerms: "700"
```

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: shared-uploads
spec:
  accessModes: ["ReadWriteMany"]
  storageClassName: efs-sc
  resources:
    requests:
      storage: 5Gi
```

EFS не тарифицируется по "запрошенному" объёму как EBS — платите за реально используемое место, и он автоматически масштабируется.

## 7.6 Снапшоты EBS-томов

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: postgres-snapshot
spec:
  volumeSnapshotClassName: csi-aws-vsc
  source:
    persistentVolumeClaimName: data-postgres-0
```

Снапшоты — основа стратегии бэкапов персистентных данных в EKS (в связке с CronJob, который создаёт их по расписанию, или с Velero, модуль 17).

### Практика

1. Установите EBS CSI Driver через IRSA
2. Задеплойте `StatefulSet` с PVC, положите туда тестовые данные
3. Удалите под, убедитесь, что данные не потерялись после пересоздания
4. Настройте `VolumeSnapshot` вручную и восстановите том из снапшота в новый PVC

### Вопросы для самопроверки

1. Когда выбирать EBS, а когда EFS?
2. Зачем нужен `volumeBindingMode: WaitForFirstConsumer`?
3. Почему для настоящей продакшен-БД чаще выбирают RDS, а не StatefulSet с EBS?

---

# Модуль 8. Автоскейлинг: Cluster Autoscaler, Karpenter, HPA/VPA

## 8.1 Два уровня автоскейлинга

- **Скейлинг подов** — сколько реплик приложения запущено (HPA, VPA)
- **Скейлинг узлов** — сколько EC2-инстансов есть в кластере, чтобы вместить все поды (Cluster Autoscaler, Karpenter)

Их часто путают, но это разные, дополняющие друг друга механизмы: HPA добавляет реплики → подам не хватает места на существующих узлах → Cluster Autoscaler/Karpenter добавляет новые узлы.

## 8.2 Horizontal Pod Autoscaler (HPA)

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: payments-api-hpa
  namespace: payments
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: payments-api
  minReplicas: 3
  maxReplicas: 20
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
```

Для метрик, отличных от CPU/памяти (длина очереди SQS, RPS), нужен `metrics-server` (для CPU/памяти он обязателен всегда) плюс адаптер вроде KEDA или Prometheus Adapter.

## 8.3 Vertical Pod Autoscaler (VPA)

VPA подбирает оптимальные `requests`/`limits` на основе фактического потребления, а не число реплик:

```yaml
apiVersion: autoscaling.k8s.io/v1
kind: VerticalPodAutoscaler
metadata:
  name: payments-api-vpa
spec:
  targetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: payments-api
  updatePolicy:
    updateMode: "Off"  # только рекомендации, без авто-применения
```

`updateMode: "Off"` — безопасный режим для начала: VPA просто показывает рекомендации, вы решаете сами. `Auto` пересоздаёт поды с новыми ресурсами — может быть рискованно вместе с HPA по CPU (не рекомендуется комбинировать VPA-Auto и HPA-по-CPU на одном объекте).

## 8.4 Cluster Autoscaler — классический подход

Работает поверх Auto Scaling Groups: смотрит на unschedulable поды и увеличивает `desiredCapacity` нужной ASG, либо уменьшает её, когда узлы простаивают.

```bash
helm install cluster-autoscaler autoscaler/cluster-autoscaler \
  --namespace kube-system \
  --set autoDiscovery.clusterName=demo-cluster \
  --set awsRegion=eu-central-1
```

Каждая managed node group должна быть помечена тегами для авто-обнаружения:

```
k8s.io/cluster-autoscaler/demo-cluster = owned
k8s.io/cluster-autoscaler/enabled = true
```

Ограничение Cluster Autoscaler: он думает в терминах "нод-групп" и заранее заданных типов инстансов — если под не влезает ни в одну существующую группу, он не поможет.

## 8.5 Karpenter — современная альтернатива

Karpenter не работает через ASG — он напрямую запускает EC2-инстансы нужного размера под конкретные unschedulable поды, выбирая оптимальный тип инстанса "на лету" из широкого пула.

```yaml
apiVersion: karpenter.sh/v1
kind: NodePool
metadata:
  name: default
spec:
  template:
    spec:
      requirements:
        - key: kubernetes.io/arch
          operator: In
          values: ["amd64"]
        - key: karpenter.sh/capacity-type
          operator: In
          values: ["spot", "on-demand"]
      nodeClassRef:
        group: karpenter.k8s.aws
        kind: EC2NodeClass
        name: default
  limits:
    cpu: 1000
  disruption:
    consolidationPolicy: WhenEmptyOrUnderutilized
    consolidateAfter: 30s
```

Karpenter умеет "консолидировать" узлы — объединять недогруженные поды на меньшее число узлов, экономя деньги, и делает это быстрее, чем классический Cluster Autoscaler (секунды, а не минуты для решения "какой инстанс поднять").

## 8.6 Cluster Autoscaler vs Karpenter

| | Cluster Autoscaler | Karpenter |
|---|---|---|
| Работает через | Auto Scaling Groups | Напрямую EC2 API |
| Гибкость выбора типа инстанса | Ограничена заранее созданными node group | Динамический выбор из широкого пула |
| Скорость реакции | Обычно медленнее | Обычно быстрее |
| Консолидация узлов | Ограниченная | Встроенная и гибкая |
| Зрелость/поддержка | Давно существует, предсказуем | Активно развивается, нативен для AWS |

Для новых кластеров AWS сейчас в целом рекомендует Karpenter, но Cluster Autoscaler остаётся валидным и хорошо изученным выбором, особенно если инфраструктура уже завязана на конкретные node group.

## 8.7 Scale to zero и cold start

И Karpenter, и Cluster Autoscaler могут увести `desiredCapacity`/число узлов в 0, когда нагрузки нет — но учитывайте cold start: новый узел поднимается не мгновенно (обычно 30-90 секунд), это стоит закладывать в SLA, если трафик может резко появиться.

### Практика

1. Настройте HPA по CPU для тестового деплоймента, нагрузите его через `kubectl run --image=busybox -- wget -O- ...` в цикле, понаблюдайте за скейлингом
2. Установите Cluster Autoscaler или Karpenter, специально создайте под, который не влезает по ресурсам, дождитесь появления нового узла
3. Настройте VPA в режиме `Off`, посмотрите на рекомендации через `kubectl describe vpa`

### Вопросы для самопроверки

1. Чем скейлинг подов принципиально отличается от скейлинга узлов?
2. Почему не рекомендуется совмещать VPA в режиме `Auto` с HPA по CPU?
3. В чём ключевое архитектурное отличие Karpenter от Cluster Autoscaler?

---

# Модуль 9. Ingress и балансировка: AWS Load Balancer Controller

## 9.1 Зачем отдельный контроллер, если Service уже умеет LoadBalancer

`Service` типа `LoadBalancer` в EKS по умолчанию (через встроенный in-tree провайдер) создаёт Classic Load Balancer — устаревший, менее гибкий тип. AWS Load Balancer Controller — отдельный компонент, который умеет создавать современные Network Load Balancer (NLB) и Application Load Balancer (ALB) с полной поддержкой `Ingress`, path-based роутинга, TLS-терминации и т.д.

## 9.2 Установка

```bash
eksctl create iamserviceaccount \
  --cluster demo-cluster \
  --namespace kube-system \
  --name aws-load-balancer-controller \
  --attach-policy-arn arn:aws:iam::123456789012:policy/AWSLoadBalancerControllerIAMPolicy \
  --approve

helm repo add eks https://aws.github.io/eks-charts
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  --namespace kube-system \
  --set clusterName=demo-cluster \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller
```

## 9.3 ALB через Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: payments-ingress
  namespace: payments
  annotations:
    kubernetes.io/ingress.class: alb
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip
    alb.ingress.kubernetes.io/certificate-arn: arn:aws:acm:eu-central-1:123456789012:certificate/abc-123
    alb.ingress.kubernetes.io/listen-ports: '[{"HTTPS":443}]'
spec:
  rules:
    - host: api.example.com
      http:
        paths:
          - path: /payments
            pathType: Prefix
            backend:
              service:
                name: payments-api
                port:
                  number: 80
```

`target-type: ip` направляет трафик от ALB напрямую на IP подов (через VPC CNI), минуя kube-proxy — это снижает лишний хоп и даёт более точную балансировку, чем `target-type: instance`.

## 9.4 NLB через Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: payments-tcp
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-type: nlb
    service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: ip
spec:
  type: LoadBalancer
  selector:
    app: payments-api
  ports:
    - port: 5432
      targetPort: 5432
```

NLB выбирают, когда нужна работа на уровне L4 (TCP/UDP), крайне низкая задержка, или статические IP-адреса для whitelisting клиентами.

## 9.5 ALB vs NLB: когда что

| | ALB | NLB |
|---|---|---|
| Уровень | L7 (HTTP/HTTPS) | L4 (TCP/UDP) |
| Path/host-based роутинг | Да | Нет |
| TLS-терминация | Да, с ACM | Есть TLS passthrough/termination, но проще на ALB |
| Задержка | Чуть выше | Минимальная |
| Статический IP | Нет (через Elastic IP можно частично) | Да |

## 9.6 Внешний DNS через external-dns

Чтобы не создавать записи в Route 53 вручную после каждого создания Ingress:

```bash
helm install external-dns external-dns/external-dns \
  --namespace kube-system \
  --set provider=aws \
  --set txtOwnerId=demo-cluster
```

С аннотацией `external-dns.alpha.kubernetes.io/hostname: api.example.com` на `Ingress`/`Service` DNS-запись создастся и обновится автоматически.

### Практика

1. Установите AWS Load Balancer Controller через Helm с IRSA
2. Создайте `Ingress` с ALB для двух разных сервисов по path-based роутингу (`/payments`, `/analytics`)
3. Привяжите TLS-сертификат из ACM
4. Установите `external-dns` и убедитесь, что запись в Route 53 создаётся автоматически

### Вопросы для самопроверки

1. Чем ALB через AWS Load Balancer Controller лучше стандартного Service типа LoadBalancer?
2. Когда выбрать NLB вместо ALB?
3. Что делает `target-type: ip` и почему это обычно лучше, чем `instance`?

---

# Модуль 10. Логи и метрики: CloudWatch, Prometheus, Grafana

## 10.1 Два основных подхода к observability в EKS

- **Нативный AWS-стек**: CloudWatch Container Insights + CloudWatch Logs — минимум настройки, платите за AWS
- **CNCF-стек**: Prometheus + Grafana (+ Loki для логов) — больше контроля и гибкости, обычно дешевле при больших объёмах, но требует эксплуатации самим

Многие продакшен-кластеры используют оба: CloudWatch для базового алертинга и логов, Prometheus/Grafana — для детальных дашбордов и продвинутого алертинга.

## 10.2 CloudWatch Container Insights

```bash
aws eks create-addon \
  --cluster-name demo-cluster \
  --addon-name amazon-cloudwatch-observability
```

Этот аддон разворачивает CloudWatch Agent как DaemonSet, автоматически собирает метрики по узлам/подам/контейнерам и присылает их в CloudWatch, плюс логи через Fluent Bit.

## 10.3 Логи через Fluent Bit в CloudWatch Logs

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: fluent-bit-config
  namespace: amazon-cloudwatch
data:
  output.conf: |
    [OUTPUT]
        Name cloudwatch_logs
        Match *
        region eu-central-1
        log_group_name /aws/eks/demo-cluster/application
        log_stream_prefix from-fluent-bit-
        auto_create_group true
```

## 10.4 Prometheus + Grafana через Helm

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack \
  --namespace monitoring --create-namespace
```

Этот чарт разом ставит Prometheus, Alertmanager, Grafana и набор готовых дашбордов/правил для базовых Kubernetes-метрик (использование CPU/памяти по подам/узлам, здоровье control plane метрик через kube-state-metrics и node-exporter).

## 10.5 Managed Prometheus и Managed Grafana от AWS

Если не хочется эксплуатировать Prometheus/Grafana самим — AWS предлагает Amazon Managed Service for Prometheus (AMP) и Amazon Managed Grafana (AMG), совместимые с open-source экосистемой, но без забот об их инфраструктуре и HA.

## 10.6 Метрики control plane

EKS даёт доступ к метрикам самого control plane (API server request latency, etcd-related метрики) через CloudWatch — включается отдельно:

```bash
aws eks update-cluster-config \
  --name demo-cluster \
  --logging '{"clusterLogging":[{"types":["api","audit","authenticator","controllerManager","scheduler"],"enabled":true}]}'
```

Включайте только нужные типы логов — `audit` логи особенно объёмные и платные при большом кластере.

## 10.7 Алертинг

```yaml
apiVersion: monitoring.coreos.com/v1
kind: PrometheusRule
metadata:
  name: payments-alerts
  namespace: monitoring
spec:
  groups:
    - name: payments
      rules:
        - alert: HighErrorRate
          expr: rate(http_requests_total{status=~"5.."}[5m]) > 0.05
          for: 10m
          labels:
            severity: critical
          annotations:
            summary: "Высокий процент 5xx у payments-api"
```

### Практика

1. Включите `amazon-cloudwatch-observability` аддон, посмотрите на дашборды Container Insights
2. Установите `kube-prometheus-stack`, откройте Grafana, найдите дашборд по использованию ресурсов кластера
3. Включите control plane логирование только для `api` и `audit`, посмотрите записи в CloudWatch Logs
4. Настройте один алерт правило в Prometheus на превышение error rate

### Вопросы для самопроверки

1. Какие плюсы у CNCF-стека (Prometheus/Grafana) по сравнению с CloudWatch Container Insights?
2. Почему стоит включать не все типы control plane логов подряд?
3. Зачем нужны Managed Prometheus/Grafana, если можно поставить их самим через Helm?

---

# Модуль 11. CI/CD: ECR, GitHub Actions, ArgoCD

## 11.1 ECR — реестр образов

```bash
aws ecr create-repository --repository-name payments-api

aws ecr get-login-password --region eu-central-1 | \
  docker login --username AWS --password-stdin 123456789012.dkr.ecr.eu-central-1.amazonaws.com

docker build -t payments-api .
docker tag payments-api:latest 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:1.4.2
docker push 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:1.4.2
```

Включите сканирование образов на уязвимости прямо в ECR:

```bash
aws ecr put-image-scanning-configuration \
  --repository-name payments-api \
  --image-scanning-configuration scanOnPush=true
```

## 11.2 Два подхода к деплою: push-based и GitOps (pull-based)

- **Push-based**: CI-пайплайн сам вызывает `kubectl apply`/`helm upgrade` в конце сборки
- **GitOps (pull-based)**: CI только собирает образ и обновляет манифест в git-репозитории; отдельный контроллер в кластере (ArgoCD/Flux) сам вытягивает изменения и применяет их

GitOps считается более безопасным и предсказуемым для продакшена: у CI-раннера не должно быть прямого доступа к кластеру, вся история изменений — в git, откат — это `git revert`.

## 11.3 GitHub Actions: сборка и push в ECR

```yaml
name: build-and-push
on:
  push:
    branches: [main]

permissions:
  id-token: write
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: arn:aws:iam::123456789012:role/github-actions-ecr-push
          aws-region: eu-central-1
      - name: Login to ECR
        run: aws ecr get-login-password | docker login --username AWS --password-stdin 123456789012.dkr.ecr.eu-central-1.amazonaws.com
      - name: Build and push
        run: |
          docker build -t payments-api:${{ github.sha }} .
          docker tag payments-api:${{ github.sha }} 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:${{ github.sha }}
          docker push 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:${{ github.sha }}
```

Обратите внимание: `role-to-assume` через OIDC — не статические AWS-ключи в секретах GitHub. GitHub Actions поддерживает OIDC federation с IAM так же, как поды поддерживают IRSA.

## 11.4 ArgoCD: GitOps-деплой

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: payments-api
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/your-org/payments-manifests.git
    targetRevision: main
    path: overlays/prod
  destination:
    server: https://kubernetes.default.svc
    namespace: payments
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```

`selfHeal: true` значит: если кто-то вручную поменяет что-то в кластере через `kubectl edit` в обход git, ArgoCD автоматически откатит это обратно к состоянию в репозитории — единственный источник правды остаётся git.

## 11.5 Канареечные и blue/green деплои

Для более плавного раската — Argo Rollouts поверх ArgoCD:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: payments-api
spec:
  strategy:
    canary:
      steps:
        - setWeight: 10
        - pause: { duration: 5m }
        - setWeight: 50
        - pause: { duration: 5m }
        - setWeight: 100
```

### Практика

1. Настройте ECR-репозиторий со сканированием при push
2. Соберите пайплайн GitHub Actions с OIDC-доступом (без статических ключей) до ECR
3. Установите ArgoCD, подключите Application, указывающий на git-репозиторий с манифестами
4. Вручную измените что-то в кластере через `kubectl edit` и убедитесь, что ArgoCD откатывает изменение обратно (`selfHeal: true`)

### Вопросы для самопроверки

1. В чём разница между push-based и pull-based (GitOps) деплоем?
2. Зачем использовать OIDC federation для GitHub Actions вместо статических AWS-ключей?
3. Что делает `selfHeal: true` в ArgoCD Application?

---

# Модуль 12. Секреты и конфигурация

## 12.1 Проблема голого Kubernetes Secret

Стандартный `Secret` в Kubernetes хранится в `etcd` в base64 (не шифрование, а просто кодирование) — если etcd не зашифрован at-rest, секреты фактически лежат почти открытым текстом. У EKS есть встроенное шифрование etcd через KMS, но даже с ним секреты, попавшие в git как plain YAML — постоянный риск.

## 12.2 Encryption at rest через KMS для секретов

```bash
eksctl utils enable-secrets-encryption \
  --cluster demo-cluster \
  --key-arn arn:aws:kms:eu-central-1:123456789012:key/abc-123
```

Это дополнительный слой поверх дефолтного шифрования EBS/etcd — секреты Kubernetes шифруются envelope-encryption через ваш собственный KMS-ключ, а не только встроенным AWS-managed ключом.

## 12.3 AWS Secrets Manager + External Secrets Operator

Правильный паттерн: секреты живут в AWS Secrets Manager (с ротацией, аудитом через CloudTrail), а в Kubernetes попадают через оператор, который синхронизирует их в обычный `Secret` объект.

```bash
helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets external-secrets/external-secrets \
  --namespace external-secrets --create-namespace
```

```yaml
apiVersion: external-secrets.io/v1beta1
kind: SecretStore
metadata:
  name: aws-secrets-manager
  namespace: payments
spec:
  provider:
    aws:
      service: SecretsManager
      region: eu-central-1
      auth:
        jwt:
          serviceAccountRef:
            name: payments-api-sa
```

```yaml
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata:
  name: payments-db-credentials
  namespace: payments
spec:
  secretStoreRef:
    name: aws-secrets-manager
    kind: SecretStore
  target:
    name: payments-db-credentials
  data:
    - secretKey: password
      remoteRef:
        key: prod/payments/db
        property: password
```

Обратите внимание: `SecretStore` использует тот же `ServiceAccount` с IRSA/Pod Identity — доступ к Secrets Manager получается через IAM, без отдельных credentials для самого оператора.

## 12.4 AWS Systems Manager Parameter Store как альтернатива

Для менее чувствительной конфигурации (не секретов, а просто параметров, которые меняются между окружениями) часто используют SSM Parameter Store — он бесплатнее для стандартных параметров, чем Secrets Manager с его ротацией.

## 12.5 ConfigMap для обычной конфигурации

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: payments-api-config
  namespace: payments
data:
  LOG_LEVEL: "info"
  FEATURE_NEW_CHECKOUT: "true"
```

```yaml
envFrom:
  - configMapRef:
      name: payments-api-config
  - secretRef:
      name: payments-db-credentials
```

## 12.6 Ротация секретов

Secrets Manager умеет автоматически ротировать секреты (например, пароли RDS) через Lambda-функцию по расписанию. External Secrets Operator при этом периодически перечитывает значение из Secrets Manager (`refreshInterval`) и обновляет Kubernetes `Secret` — но приложение должно уметь подхватывать новый секрет без перезапуска, либо нужен механизм рестарта пода при смене секрета (например, Reloader).

### Практика

1. Включите шифрование секретов через собственный KMS-ключ
2. Создайте секрет в AWS Secrets Manager
3. Установите External Secrets Operator и синхронизируйте секрет в Kubernetes `Secret` через IRSA
4. Настройте `refreshInterval` и проверьте, что изменение значения в Secrets Manager подтягивается автоматически

### Вопросы для самопроверки

1. Почему стандартный Kubernetes `Secret` без дополнительных мер — не полноценная защита?
2. Зачем нужен External Secrets Operator, если можно просто класть секреты напрямую как Kubernetes `Secret`?
3. Чем Parameter Store отличается от Secrets Manager по назначению?

---

# Модуль 13. Multi-cluster и мульти-аккаунт

## 13.1 Зачем несколько кластеров вместо одного большого

- Изоляция окружений (dev/staging/prod) — ошибка в staging не должна физически задевать prod
- Изоляция по географии/региону — latency и требования резидентности данных
- Blast radius — если один кластер полностью выйдет из строя, не должны упасть все сервисы компании разом
- Ограничения масштабирования одного control plane при очень большом числе объектов

## 13.2 Паттерн "один аккаунт AWS на окружение"

Частая практика: отдельный AWS-аккаунт под `dev`, `staging`, `prod` — root-уровневая изоляция биллинга, IAM, лимитов. Управляется через AWS Organizations, доступ между аккаунтами — через cross-account IAM роли, а не через шаринг credentials.

## 13.3 Terraform для мульти-кластерной инфраструктуры

```hcl
module "eks_prod" {
  source          = "terraform-aws-modules/eks/aws"
  cluster_name    = "prod-cluster"
  cluster_version = "1.30"
  vpc_id          = module.vpc_prod.vpc_id
  subnet_ids      = module.vpc_prod.private_subnets

  eks_managed_node_groups = {
    default = {
      instance_types = ["m5.large"]
      min_size       = 3
      max_size       = 10
      desired_size   = 3
    }
  }
}
```

Terraform-модуль `terraform-aws-modules/eks/aws` — фактический стандарт для управления EKS-инфраструктурой как кодом, если команда предпочитает Terraform вместо `eksctl`.

## 13.4 Централизованный доступ через Access Entries на несколько кластеров

Если у команды несколько кластеров, разумно унифицировать управление доступом: единая IAM-роль на "SRE-инженера" привязывается через Access Entries к каждому кластеру с соответствующим уровнем прав, а не заводится россыпь локальных пользователей.

## 13.5 Service mesh между кластерами (кратко)

Для взаимодействия сервисов из разных кластеров (например, prod в двух регионах) используют service mesh с multi-cluster поддержкой (Istio, App Mesh) или API Gateway между кластерами. Это отдельная большая тема, выходящая за рамки вводного курса — важно на этом этапе просто понимать, что "один сервис — один кластер" не масштабируется без явного связующего слоя.

## 13.6 Общий Terraform state и модульность

Отдельный `tfstate` на каждый кластер/окружение — стандартная практика, чтобы ошибка в dev не могла случайно повлиять на state прод-кластера. Удалённый backend (S3 + DynamoDB для locking, либо Terraform Cloud) обязателен при командной работе.

### Практика

1. Опишите инфраструктуру двух окружений (`dev`, `prod`) через Terraform-модуль `terraform-aws-modules/eks/aws` с раздельными state-файлами
2. Настройте Access Entries так, чтобы один и тот же IAM-принципал имел разные права в `dev` (admin) и `prod` (read-only)

### Вопросы для самопроверки

1. Какие причины есть заводить несколько кластеров вместо одного большого?
2. Зачем разделять AWS-аккаунты по окружениям, а не просто namespace внутри одного кластера?
3. Почему важно держать раздельный Terraform state для разных кластеров?

---

# Модуль 14. Обновление и обслуживание кластера

## 14.1 Что обновляется раздельно

1. Control plane (версия Kubernetes)
2. Node groups (версия Kubernetes на узлах + AMI)
3. EKS Add-ons (vpc-cni, coredns, kube-proxy, ebs-csi и т.д.)

Все три обновляются отдельными операциями и должны обновляться в правильном порядке.

## 14.2 Обновление control plane

```bash
eksctl upgrade cluster --name demo-cluster --version 1.31 --approve
```

Control plane обновляется без простоя API (AWS делает rolling upgrade managed control plane), но это не значит, что можно прыгать через версии — только последовательно, на одну минорную версию за раз.

## 14.3 Обновление узлов

```bash
eksctl upgrade nodegroup \
  --cluster demo-cluster \
  --name standard-workers \
  --kubernetes-version 1.31
```

Managed node group при апгрейде делает rolling replacement узлов: поднимает новые с новой версией, аккуратно `cordon`+`drain` старые, ждёт готовности подов на новых узлах перед тем как убить старый. Важно, чтобы у приложений были настроены `PodDisruptionBudget`, иначе drain может увести в down сразу все реплики:

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: payments-api-pdb
  namespace: payments
spec:
  minAvailable: 2
  selector:
    matchLabels:
      app: payments-api
```

## 14.4 Обновление аддонов

```bash
aws eks update-addon \
  --cluster-name demo-cluster \
  --addon-name vpc-cni \
  --addon-version v1.18.1-eksbuild.1 \
  --resolve-conflicts OVERWRITE
```

`--resolve-conflicts OVERWRITE` нужен, если вы вручную меняли конфигурацию аддона (например, переменные окружения VPC CNI) — иначе обновление может остановиться на конфликте.

## 14.5 Порядок безопасного обновления

```
1. проверить состояние кластера (health, деплойменты все Running)
2. обновить control plane на одну минорную версию
3. обновить EKS Add-ons до совместимых версий
4. обновить node groups (по одной, не все разом, если групп несколько)
5. проверить, что приложения по-прежнему здоровы
6. повторить для следующей минорной версии, если нужно продвинуться дальше
```

## 14.6 Blue/green апгрейд узлов вместо in-place

Вместо upgrade существующей node group иногда безопаснее создать новую node group с новой версией, постепенно перевести на неё нагрузку (через `cordon` старой + скейлинг новой), а затем удалить старую — даёт возможность быстро откатиться, просто раскейлив старую группу обратно.

## 14.7 Deprecated API при апгрейде

Каждая минорная версия Kubernetes может убирать устаревшие API (классика — `extensions/v1beta1` для Ingress в далёком прошлом). Перед апгрейдом обязательно проверяйте манифесты и Helm-чарты на использование deprecated/removed API:

```bash
kubectl-convert -f old-manifest.yaml --output-version apps/v1
```

Или используйте специализированные инструменты вроде `kubent` (kube-no-trouble) для сканирования всего кластера на использование устаревших API перед апгрейдом.

### Практика

1. Настройте `PodDisruptionBudget` для тестового деплоймента
2. Обновите node group на одну минорную версию, понаблюдайте за rolling replacement через `kubectl get nodes -w`
3. Проверьте манифесты кластера на использование deprecated API перед условным будущим апгрейдом

### Вопросы для самопроверки

1. В каком порядке безопасно обновлять control plane, аддоны и node groups?
2. Зачем нужен `PodDisruptionBudget` именно во время апгрейда узлов?
3. Почему нельзя перепрыгивать через минорные версии Kubernetes при апгрейде?

---

# Модуль 15. Стоимость и оптимизация

## 15.1 Из чего складывается счёт за EKS

- Плата за control plane — фиксированная почасовая ставка за каждый кластер
- EC2-инстансы worker-узлов (или vCPU/память Fargate-подов)
- EBS-тома, снапшоты
- Load Balancer'ы (ALB/NLB) — почасовая плата + плата за обработанный трафик
- NAT Gateway — почасовая плата + плата за трафик через него (часто недооценённая статья расходов)
- Исходящий трафик (data transfer) между AZ и наружу
- CloudWatch Logs/метрики при большом объёме

## 15.2 Самые частые причины раздутого счёта

- Overprovisioned `requests` — приложение просит 2 CPU "на всякий случай", реально использует 200m, а Cluster Autoscaler/Karpenter честно держит под это лишние узлы
- Отсутствие HPA — держат фиксированное большое число реплик под пиковую нагрузку круглосуточно
- Один NAT Gateway на AZ вместо экономии через VPC Endpoints для трафика к AWS-сервисам
- Дублирующиеся Load Balancer'ы вместо одного Ingress с path-based роутингом на несколько сервисов
- Логи "на всякий случай" без retention policy — CloudWatch Logs копятся бесконечно

## 15.3 Spot-инстансы для несрочных нагрузок

```yaml
managedNodeGroups:
  - name: spot-workers
    instanceTypes: ["t3.medium", "t3a.medium", "t3.large"]
    spot: true
    minSize: 0
    maxSize: 20
```

Spot-инстансы стоят на 60-90% дешевле on-demand, но могут быть вытеснены AWS с уведомлением за 2 минуты. Подходят для: batch-джобов, stateless-сервисов с достаточным числом реплик, CI-раннеров. Не подходят для: одиночных stateful-подов без репликации.

## 15.4 Karpenter consolidation для экономии

Как упоминалось в модуле 8, Karpenter умеет активно "сжимать" число узлов, переселяя поды на меньшее количество более полно загруженных инстансов — это прямой способ снизить счёт без ручного вмешательства.

## 15.5 Savings Plans и Reserved Instances для базовой нагрузки

Если у кластера есть предсказуемый "пол" нагрузки (минимум узлов, которые точно всегда нужны) — на них стоит взять Compute Savings Plans или Reserved Instances, а поверх — spot/on-demand для переменной части.

## 15.6 Right-sizing через VPA-рекомендации

VPA в режиме `Off` (модуль 8) даёт честную картину, сколько ресурсов реально нужно приложению — используйте эти рекомендации, чтобы не гадать с `requests`/`limits`.

## 15.7 AWS Cost Explorer + Kubecost

Для детальной разбивки "какой namespace/деплоймент сколько стоит" (Cost Explorer сам по себе не знает про Kubernetes-объекты) используют Kubecost или встроенный AWS Split Cost Allocation Data для EKS, который умеет разбивать счёт по namespace/label.

```bash
helm install kubecost cost-analyzer/cost-analyzer \
  --namespace kubecost --create-namespace \
  --set kubecostToken="<token>"
```

### Практика

1. Настройте VPC Endpoints для ECR/S3, отключите (или сравните трафик до/после) прохождение через NAT Gateway
2. Найдите в кластере деплойменты с явно завышенными `requests` через VPA-рекомендации
3. Переведите некритичную нагрузку (например, batch-джобы) на spot node group
4. Установите Kubecost и посмотрите разбивку стоимости по namespace

### Вопросы для самопроверки

1. Какие статьи расходов в EKS чаще всего оказываются неожиданно большими?
2. Почему overprovisioned `requests` напрямую увеличивают счёт, даже если реальной утилизации CPU почти нет?
3. Для какого типа нагрузки spot-инстансы не подходят и почему?

---

# Модуль 16. Безопасность EKS

## 16.1 Модель разделённой ответственности

AWS отвечает за безопасность control plane (патчи, изоляция, шифрование etcd). Вы отвечаете за: безопасность образов, конфигурацию сети внутри кластера, IAM-права подов, патчи ОС узлов (если не Fargate), политики допуска подов.

## 16.2 Pod Security Standards

Начиная с Kubernetes 1.25 `PodSecurityPolicy` заменён на `Pod Security Standards`, применяемые через labels на namespace:

```bash
kubectl label namespace payments \
  pod-security.kubernetes.io/enforce=restricted \
  pod-security.kubernetes.io/audit=restricted
```

`restricted` запрещает privileged-контейнеры, требует непривилегированного пользователя, запрещает hostNetwork/hostPID и т.д. — базовая гигиена для продакшен-namespace.

## 16.3 Ограничение контейнера на уровне манифеста

```yaml
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
  capabilities:
    drop: ["ALL"]
```

## 16.4 GuardDuty for EKS

```bash
aws guardduty create-detector --enable
aws guardduty update-detector \
  --detector-id <id> \
  --features '[{"Name":"EKS_AUDIT_LOGS","Status":"ENABLED"},{"Name":"EKS_RUNTIME_MONITORING","Status":"ENABLED"}]'
```

GuardDuty анализирует Kubernetes audit logs и рантайм-поведение подов, ищет аномалии: попытки эскалации привилегий, подозрительные API-вызовы, коммуникацию с известными вредоносными IP.

## 16.5 Сканирование образов

Уже упоминалось в модуле 11 — включайте `scanOnPush` в ECR. Для более глубокого сканирования (не только известные CVE, но и политика допустимости) используют Trivy или AWS Inspector for ECR:

```bash
trivy image 123456789012.dkr.ecr.eu-central-1.amazonaws.com/payments-api:1.4.2 --severity CRITICAL,HIGH
```

## 16.6 Admission control: OPA Gatekeeper / Kyverno

Чтобы физически не дать задеплоить нарушающий политику манифест (например, образ не из вашего приватного ECR, или под без `resources.limits`):

```yaml
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: require-resource-limits
spec:
  validationFailureAction: Enforce
  rules:
    - name: check-resources
      match:
        resources:
          kinds: ["Pod"]
      validate:
        message: "Каждый контейнер должен иметь resources.limits"
        pattern:
          spec:
            containers:
              - resources:
                  limits:
                    memory: "?*"
                    cpu: "?*"
```

## 16.7 Network Policy как обязательный слой (напоминание из модуля 5)

Без `NetworkPolicy` любой скомпрометированный под может достучаться до любого другого пода в кластере. Deny-by-default с явными allow-правилами — стандарт для продакшена.

## 16.8 Секреты и аудит (напоминание из модуля 12)

KMS-шифрование etcd для секретов + External Secrets Operator + включённые `audit` control plane логи — базовый набор для соответствия большинству compliance-требований (SOC2, ISO 27001 и т.д.).

## 16.9 Чек-лист базовой безопасности EKS

```
[ ] Private (или Public+Private с allowlist) control plane endpoint
[ ] IMDSv2 обязателен на всех узлах, hop-limit = 1
[ ] Узлы в приватных подсетях, без публичных IP
[ ] Pod Security Standards хотя бы на baseline/restricted для prod namespace
[ ] Node IAM role минимальна, права приложений — через IRSA/Pod Identity
[ ] Секреты через External Secrets Operator + KMS-шифрование etcd
[ ] Network Policy: deny-by-default
[ ] Сканирование образов включено (ECR scanOnPush + Trivy/Inspector)
[ ] GuardDuty for EKS включён
[ ] Control plane audit-логи собираются и хранятся
```

### Практика

1. Примените `restricted` Pod Security Standard к тестовому namespace, попробуйте задеплоить privileged-под — убедитесь, что он отклонён
2. Включите GuardDuty EKS protection
3. Установите Kyverno/OPA Gatekeeper и напишите политику, запрещающую поды без `resources.limits`
4. Пройдитесь по чек-листу из 16.9 и отметьте, что уже сделано в вашем кластере

### Вопросы для самопроверки

1. Что из безопасности EKS — зона ответственности AWS, а что — ваша?
2. Зачем нужны admission-контроллеры вроде Kyverno, если можно просто написать правильные манифесты вручную?
3. Почему `NetworkPolicy` считается обязательным элементом, а не опциональным улучшением?

---

# Модуль 17. Disaster recovery и backup

## 17.1 Что нужно бэкапить в EKS

- Состояние Kubernetes-объектов (манифесты, конфигурация) — в первую очередь должно жить в git, это ваш основной "бэкап"
- Персистентные данные (EBS-тома со StatefulSet) — снапшоты
- Секреты и конфигурация вне git (если что-то создавалось руками, а не через GitOps)
- Сам факт "как был устроен кластер" — Terraform/eksctl-конфиг тоже должен быть в git

## 17.2 Velero — стандарт для бэкапа Kubernetes-объектов и томов

```bash
velero install \
  --provider aws \
  --plugins velero/velero-plugin-for-aws:v1.10.0 \
  --bucket velero-backups-demo-cluster \
  --backup-location-config region=eu-central-1 \
  --snapshot-location-config region=eu-central-1 \
  --secret-file ./credentials-velero
```

```bash
velero backup create payments-backup --include-namespaces payments
velero schedule create daily-backup --schedule="0 3 * * *" --include-namespaces payments
```

Velero бэкапит и объекты Kubernetes (в S3 как JSON), и делает EBS-снапшоты персистентных томов — восстановление воспроизводит и манифесты, и данные.

## 17.3 Восстановление

```bash
velero restore create --from-backup payments-backup
```

Регулярно тестируйте восстановление в отдельном (не продакшен) кластере — бэкап, который ни разу не восстанавливался, нельзя считать рабочим.

## 17.4 Multi-region disaster recovery

Для критичных систем одного кластера в одном регионе может быть недостаточно. Паттерны:

- **Pilot light** — минимальный резервный кластер в другом регионе, масштабируется при аварии основного
- **Warm standby** — второй кластер работает постоянно с меньшей нагрузкой, готов принять весь трафик
- **Active-active** — оба кластера в проде одновременно, трафик балансируется через Route 53 или Global Accelerator

Выбор зависит от RTO/RPO требований бизнеса — чем ближе к active-active, тем дороже и сложнее, но тем меньше времени простоя при аварии.

## 17.5 RTO и RPO применительно к EKS

- **RPO (Recovery Point Objective)** — сколько данных допустимо потерять; определяется частотой снапшотов/бэкапов Velero и репликацией БД
- **RTO (Recovery Time Objective)** — как быстро нужно восстановиться; определяется скоростью пересоздания кластера (Terraform/eksctl) + временем восстановления Velero + временем прогрева узлов

Держите Terraform/eksctl конфигурацию кластера актуальной и протестированной — в критичной ситуации "поднять новый кластер с нуля за 20 минут по коду" намного надёжнее, чем разбираться, что настраивалось руками полгода назад.

## 17.6 Резервирование control plane и multi-AZ по умолчанию

Напомним из модуля 1: AWS уже размещает control plane в нескольких AZ автоматически — ваша ответственность именно за worker-узлы (растянуть по AZ) и за данные (снапшоты, реплики БД).

### Практика

1. Установите Velero, настройте ежедневный бэкап по расписанию для одного namespace
2. Удалите тестовый namespace целиком и восстановите его из бэкапа Velero
3. Опишите (хотя бы на бумаге) RTO/RPO для вашего гипотетического продакшен-приложения и выберите подходящий DR-паттерн

### Вопросы для самопроверки

1. Почему манифесты в git считаются "основным бэкапом" состояния кластера?
2. Что бэкапит Velero — только объекты Kubernetes или ещё и данные в томах?
3. В чём разница между pilot light, warm standby и active-active DR-паттернами?

---

# Модуль 18. EKS в продакшене: чек-лист

## 18.1 Референсная архитектура продакшен-кластера

```
                         Route 53
                            │
                     ALB (internet-facing)
                            │
        ┌───────────────────┴───────────────────┐
        │              EKS Cluster                │
        │  Control plane: Public+Private endpoint │
        │  (публичный доступ ограничен по CIDR)   │
        │                                          │
        │  Managed Node Groups (on-demand, ≥3 AZ) │
        │  + Karpenter NodePool (spot, batch)     │
        │  + Fargate profile (namespace: batch)   │
        │                                          │
        │  Namespaces: prod-api, prod-workers,    │
        │              monitoring, argocd          │
        └──────────────────────────────────────────┘
                            │
         RDS (multi-AZ)  EBS/EFS   Secrets Manager
```

## 18.2 Sizing control plane и node groups

Control plane масштабируется AWS автоматически — вам не нужно думать про его "размер". Для узлов: начинайте с нескольких умеренных инстансов (например, `m5.large`) в managed node group на on-demand для базовой нагрузки, добавьте Karpenter для эластичной части.

## 18.3 Kubernetes-манифесты как единый источник правды

Весь продакшен-конфиг — в git, применяется только через GitOps (ArgoCD/Flux). Прямые `kubectl apply`/`kubectl edit` в прод-кластере — исключение, а не норма (и должны триггерить `selfHeal` откат, как обсуждали в модуле 11).

## 18.4 Чек-лист продакшена

```
Сеть:
[ ] Узлы в приватных подсетях, минимум 3 AZ
[ ] VPC Endpoints для ECR/S3/Secrets Manager
[ ] Security Groups for Pods для чувствительных сервисов
[ ] NetworkPolicy deny-by-default

Доступ:
[ ] Access Entries вместо расшаренных IAM-пользователей
[ ] Публичный control plane endpoint ограничен по CIDR (или Private-only + VPN)
[ ] IMDSv2 обязателен

Workload:
[ ] requests/limits заданы у всех контейнеров
[ ] readiness/liveness пробы у всех сервисов
[ ] PodDisruptionBudget у критичных деплойментов
[ ] topologySpreadConstraints между AZ

Автоскейлинг:
[ ] HPA настроен по релевантной метрике
[ ] Karpenter/Cluster Autoscaler с разумными лимитами

Хранилище и данные:
[ ] EBS-тома шифрованы
[ ] Регулярные снапшоты/Velero-бэкапы
[ ] Восстановление из бэкапа протестировано хотя бы раз

Безопасность:
[ ] Pod Security Standards restricted/baseline
[ ] Секреты через External Secrets Operator
[ ] Сканирование образов включено
[ ] GuardDuty for EKS включён

Observability:
[ ] Логи агрегируются (CloudWatch или Loki)
[ ] Дашборды на ключевые метрики приложения и кластера
[ ] Алерты настроены и доходят до дежурного

Эксплуатация:
[ ] Инфраструктура кластера в Terraform/eksctl-конфиге, в git
[ ] Деплой через GitOps
[ ] Документирован процесс апгрейда control plane/узлов/аддонов
[ ] RTO/RPO определены, DR-план описан
```

## 18.5 Антипаттерны

- Один большой namespace `default` для всего прод-приложения — нет изоляции, сложно считать стоимость
- Широкая IAM-роль на всю node group "чтобы не разбираться с IRSA" — прямой путь к инциденту безопасности
- Отсутствие `PodDisruptionBudget` — любой апгрейд узла может положить сервис целиком
- Ручные изменения в прод-кластере в обход git — теряется единый источник правды, сложно понять, "что реально задеплоено"
- Игнорирование deprecated API warnings годами — апгрейд превращается в квест в последний момент

### Практика

Пройдитесь по чек-листу 18.4 применительно к своему (или тестовому) кластеру, отметьте невыполненные пункты и составьте план их закрытия с приоритетами.

---

# Модуль 19. Итоговый проект: развёртывание микросервисного приложения

## 19.1 Что строим

Простое, но реалистичное приложение из трёх сервисов:
- `api-gateway` — принимает HTTP-запросы, за Ingress/ALB
- `orders-service` — обрабатывает заказы, пишет в RDS Postgres
- `notifications-worker` — читает из SQS, шлёт уведомления, работает на spot-узлах/Fargate

## 19.2 Требования

- Все три сервиса в отдельных Deployment с requests/limits и пробами
- `api-gateway` доступен снаружи через ALB Ingress с TLS
- `orders-service` подключается к RDS через пароль из Secrets Manager (External Secrets Operator), доступ к RDS ограничен через Security Groups for Pods
- `notifications-worker` имеет права на чтение SQS только через IRSA/Pod Identity, задеплоен в Fargate profile
- HPA настроен на `orders-service` по CPU
- Все три сервиса имеют `PodDisruptionBudget`
- Деплой происходит через ArgoCD из git-репозитория
- Базовые дашборды и алерты в Prometheus/Grafana или CloudWatch

## 19.3 Этапы

1. Поднимите кластер с managed node group + Fargate profile для namespace `notifications`
2. Настройте VPC Endpoints, security groups, RDS Postgres в приватной подсети
3. Настройте IRSA/Pod Identity: роль для `orders-service` (Secrets Manager read), роль для `notifications-worker` (SQS read)
4. Установите AWS Load Balancer Controller, External Secrets Operator, ArgoCD, kube-prometheus-stack
5. Опишите манифесты всех трёх сервисов в git-репозитории, подключите через ArgoCD Application
6. Настройте HPA на `orders-service`, `PodDisruptionBudget` на все три сервиса
7. Проведите нагрузочный тест на `api-gateway`, понаблюдайте за автоскейлингом через HPA и Karpenter/Cluster Autoscaler
8. Настройте алерт на рост latency/error rate, специально сломайте `orders-service`, убедитесь, что алерт срабатывает

## 19.4 Как проверить, что получилось

```bash
# нагрузка
hey -z 5m -c 50 https://api.example.com/orders

# во время нагрузки
kubectl get hpa -w
kubectl get pods -n orders -w

# проверка идемпотентности secrets sync
kubectl exec -n orders deploy/orders-service -- env | grep DB_PASSWORD

# проверка отказоустойчивости
kubectl delete pod -n orders -l app=orders-service --force
# приложение не должно уйти в полный даунтайм благодаря нескольким репликам и PDB
```

## 19.5 Что можно улучшить дальше

- Добавить canary-деплой через Argo Rollouts
- Настроить multi-region DR через Velero + второй кластер
- Внедрить service mesh (App Mesh/Istio) для mTLS между сервисами
- Настроить Kyverno-политики для admission control
- Подключить Kubecost для разбивки стоимости по сервису

---

# Шпаргалка eksctl / kubectl / IAM

```bash
# кластеры
eksctl create cluster -f cluster.yaml
eksctl get cluster
eksctl delete cluster --name demo-cluster
eksctl upgrade cluster --name demo-cluster --version 1.31 --approve

# node groups
eksctl create nodegroup --cluster demo-cluster --name workers --nodes 3
eksctl get nodegroup --cluster demo-cluster
eksctl scale nodegroup --cluster demo-cluster --name workers --nodes 5
eksctl delete nodegroup --cluster demo-cluster --name workers

# kubeconfig
aws eks update-kubeconfig --region eu-central-1 --name demo-cluster

# доступ
aws eks create-access-entry --cluster-name demo-cluster --principal-arn <arn> --type STANDARD
aws eks associate-access-policy --cluster-name demo-cluster --principal-arn <arn> \
  --access-scope type=cluster --policy-arn arn:aws:eks::aws:cluster-access-policy/AmazonEKSAdminPolicy
aws eks list-access-entries --cluster-name demo-cluster

# IRSA / Pod Identity
eksctl create iamserviceaccount --cluster demo-cluster --namespace ns --name sa \
  --attach-policy-arn <policy-arn> --approve
aws eks create-pod-identity-association --cluster-name demo-cluster \
  --namespace ns --service-account sa --role-arn <role-arn>

# addons
aws eks list-addons --cluster-name demo-cluster
aws eks update-addon --cluster-name demo-cluster --addon-name vpc-cni --addon-version <v>

# базовые kubectl
kubectl get nodes -o wide
kubectl get pods -A
kubectl describe pod <pod> -n <ns>
kubectl logs -f <pod> -n <ns>
kubectl exec -it <pod> -n <ns> -- sh
kubectl top nodes
kubectl top pods -n <ns>
kubectl rollout restart deployment <name> -n <ns>
kubectl rollout status deployment <name> -n <ns>
kubectl drain <node> --ignore-daemonsets --delete-emptydir-data
kubectl cordon <node>
kubectl uncordon <node>
```

---

# Вопросы на собеседовании по EKS с ответами

**Что берёт на себя AWS в EKS, а что остаётся на пользователе?**
AWS управляет control plane (API server, etcd, scheduler, controller-manager) — их доступностью, патчами, масштабированием, шифрованием etcd. Пользователь отвечает за worker-узлы (если не Fargate), сетевую конфигурацию, IAM-права подов, сами приложения и их конфигурацию.

**Чем IRSA отличается от Pod Identity?**
Оба дают подам доступ к AWS через IAM-роль без статических ключей. IRSA работает через OIDC provider кластера и требует прописывать trust policy под конкретный кластер в каждой роли. Pod Identity — более новый механизм, роль доверяет общему сервису `pods.eks.amazonaws.com`, не привязана к OIDC конкретного кластера, что упрощает настройку и перенос между кластерами.

**Почему под может не запускаться, хотя на узле есть свободные CPU и память?**
Часто причина — нехватка IP-адресов на узле. VPC CNI выдаёт подам реальные IP из VPC, и число IP, которое может держать узел, ограничено типом инстанса (количеством ENI и IP на ENI). Решение — Prefix Delegation или инстанс большего размера/типа.

**В чём разница между Cluster Autoscaler и Karpenter?**
Cluster Autoscaler работает через Auto Scaling Groups заранее заданных node groups и реагирует на unschedulable поды, увеличивая/уменьшая desired capacity нужной ASG. Karpenter обходится без ASG, напрямую запускает EC2-инстансы оптимального размера под конкретные поды и умеет активно консолидировать недогруженные узлы для экономии.

**Зачем нужен `PodDisruptionBudget` в контексте EKS?**
При апгрейде node group (или scale-down от Cluster Autoscaler/Karpenter) узлы получают `cordon`+`drain`. Без PDB это может одновременно снять с работы слишком много реплик одного сервиса. PDB гарантирует минимальное число доступных подов во время добровольных disruption-событий.

**Как устроена сеть подов в EKS по умолчанию?**
Через AWS VPC CNI: каждый под получает реальный IP-адрес из VPC-подсети (не оверлейную сеть). Это даёт прямую совместимость с VPC security groups и route tables, но ограничивает плотность подов на узле числом доступных IP.

**Как обеспечить доступ пода к RDS без статических паролей "на глазок"?**
Пароль хранится в AWS Secrets Manager, синхронизируется в Kubernetes `Secret` через External Secrets Operator, у которого свой `ServiceAccount` с IRSA/Pod Identity ролью, дающей доступ только на чтение конкретного секрета. Доступ пода к самой RDS ограничивается security group (в идеале — Security Group for Pods, а не общая для узла).

**Чем ALB через AWS Load Balancer Controller отличается от Service типа LoadBalancer по умолчанию?**
Стандартный `Service type=LoadBalancer` в EKS через in-tree провайдер создаёт устаревший Classic Load Balancer. AWS Load Balancer Controller умеет создавать современные ALB (L7, path/host-based роутинг, TLS через ACM) через `Ingress` и NLB (L4) через аннотации на `Service`.

**Что произойдёт, если пропустить обновление аддона VPC CNI при апгрейде control plane?**
Может возникнуть несовместимость версий — новый control plane может ожидать возможности, которых старая версия аддона не поддерживает, что приведёт к сетевым сбоям у подов. AWS явно рекомендует держать версии аддонов совместимыми с версией control plane.

**Как в EKS реализовать multi-tenancy на уровне одного кластера?**
Через комбинацию: `Namespace` для логической изоляции, `ResourceQuota`/`LimitRange` для ограничения ресурсов, `NetworkPolicy` для сетевой изоляции между тенантами, разные IAM-роли через IRSA/Pod Identity для разных namespace, и Pod Security Standards. Для сильной изоляции (регуляторные требования, недоверенные тенанты) чаще заводят отдельные кластеры, а не полагаются только на namespace-изоляцию.

---

# FAQ: частые вопросы про EKS

**Можно ли использовать EKS бесплатно?**
Control plane тарифицируется почасово с первой минуты — бесплатного тарифа на него нет (в отличие от некоторых managed сервисов с free tier). Реально "бесплатно" можно поэкспериментировать только в рамках краткосрочного AWS free trial кредита, аккуратно удаляя ресурсы после экспериментов.

**Нужно ли знать голый Kubernetes, чтобы работать с EKS?**
Да, обязательно. EKS не абстрагирует Kubernetes API — вы работаете с теми же `kubectl`, Deployment, Service, что и в любом другом дистрибутиве. EKS облегчает именно эксплуатацию control plane и интеграцию с AWS-сервисами, а не сам Kubernetes.

**В чём разница между `eksctl` и Terraform для создания кластера?**
`eksctl` — специализированный CLI, обёртка над CloudFormation, быстрый старт, меньше boilerplate. Terraform — универсальный IaC-инструмент, лучше подходит, когда EKS — часть большой инфраструктуры (VPC, RDS, IAM уже управляются Terraform), даёт больше контроля и переиспользуемости через модули.

**Можно ли мигрировать с self-managed Kubernetes на EKS без даунтайма?**
В общем случае нет прямой "миграции control plane" — вы создаёте новый EKS-кластер и постепенно переносите нагрузку (через blue/green: DNS-переключение между старым и новым кластером после проверки). Полностью бесшовно (без хотя бы краткого окна) мигрировать между control plane разных дистрибутивов невозможно.

**Что произойдёт с приложениями, если control plane временно недоступен?**
Уже запущенные поды продолжат работать — kubelet на узлах не зависит от постоянной доступности API server для поддержания уже запущенных контейнеров. Но новые деплои, скейлинг, восстановление упавших подов остановятся до восстановления API. AWS держит SLA на доступность control plane именно поэтому.

**Нужен ли отдельный кластер для каждого микросервиса?**
Нет, это избыточно. Обычно один кластер на окружение (dev/staging/prod), внутри — множество namespace на команды/сервисы. Отдельные кластеры заводят по причинам изоляции (compliance, blast radius), а не "один сервис — один кластер".

**Чем EKS Fargate отличается от AWS Fargate для ECS?**
Технология похожая (бессерверные контейнеры без управления EC2), но EKS Fargate работает через стандартный Kubernetes API (Fargate profile определяет, какие поды туда попадают), а Fargate для ECS — через проприетарный ECS API. Это разные продукты с общим "движком" бессерверных контейнеров под капотом.

**Как понять, что кластер стал слишком большим и пора его разделить?**
Явных жёстких лимитов немного, но сигналы: заметно возросшая задержка API server, сложности с апгрейдом (слишком много различных приложений с разными требованиями к деprecated API), команды начинают конфликтовать за ресурсы/имена, требования к изоляции стали жёстче, чем даёт namespace-разделение.

---

# Глоссарий EKS

- **Control plane** — управляемая AWS часть Kubernetes-кластера: API server, etcd, scheduler, controller-manager
- **Data plane** — worker-узлы (EC2) или Fargate-поды, где реально исполняются контейнеры
- **Managed Node Group** — группа worker-узлов, управляемая AWS через Auto Scaling Group с упрощённым апгрейдом/масштабированием
- **Fargate profile** — конфигурация, определяющая, какие поды (по namespace/label) запускаются бессерверно на AWS Fargate
- **VPC CNI** — сетевой плагин Kubernetes от AWS, выдающий подам реальные IP-адреса из VPC
- **IRSA (IAM Roles for Service Accounts)** — механизм выдачи подам AWS IAM-прав через OIDC federation, привязанный к Kubernetes ServiceAccount
- **EKS Pod Identity** — более новый механизм выдачи подам IAM-прав, не требующий привязки к OIDC provider конкретного кластера
- **EKS Add-on** — компонент кластера (vpc-cni, coredns, kube-proxy, ebs-csi и т.д.), версией и установкой которого управляет EKS API
- **Karpenter** — контроллер автоскейлинга узлов, напрямую запускающий EC2-инстансы оптимального размера под unschedulable поды
- **Cluster Autoscaler** — классический контроллер автоскейлинга узлов, работающий через Auto Scaling Groups
- **AWS Load Balancer Controller** — контроллер, создающий ALB/NLB на основе Kubernetes Ingress/Service
- **Security Groups for Pods** — механизм назначения security group конкретным подам, а не всему узлу
- **Access Entries** — современный способ управления доступом IAM-принципалов к Kubernetes API кластера (замена `aws-auth` ConfigMap)
- **Bottlerocket** — специализированная минималистичная ОС AWS для запуска контейнеров на worker-узлах
- **Prefix Delegation** — режим VPC CNI, резервирующий целые IP-префиксы вместо отдельных адресов, увеличивая плотность подов на узле
- **PodDisruptionBudget (PDB)** — объект Kubernetes, ограничивающий, сколько реплик может быть недоступно одновременно при добровольных disruption-событиях (апгрейд, drain)
- **GitOps** — модель деплоя, при которой git-репозиторий — единственный источник истины, а контроллер в кластере (ArgoCD/Flux) сам подтягивает изменения
- **Velero** — инструмент бэкапа/восстановления объектов Kubernetes и связанных персистентных томов
- **External Secrets Operator** — контроллер, синхронизирующий секреты из внешних хранилищ (Secrets Manager, SSM Parameter Store) в Kubernetes `Secret`

---

# Официальные источники и что читать дальше

- Документация Amazon EKS — https://docs.aws.amazon.com/eks/
- eksctl — https://eksctl.io/
- AWS Load Balancer Controller — https://kubernetes-sigs.github.io/aws-load-balancer-controller/
- Karpenter — https://karpenter.sh/
- Amazon EKS Best Practices Guides — https://docs.aws.amazon.com/eks/latest/best-practices/introduction.html
- terraform-aws-modules/eks — https://github.com/terraform-aws-modules/terraform-aws-eks
- External Secrets Operator — https://external-secrets.io/
- Velero — https://velero.io/
- ArgoCD — https://argo-cd.readthedocs.io/

## Как помочь проекту

Если материал был полезен — поставьте звезду репозиторию, поделитесь с коллегами, которые начинают работу с EKS, и открывайте issue/pull request с исправлениями или дополнениями по мере того, как AWS обновляет сервис.
