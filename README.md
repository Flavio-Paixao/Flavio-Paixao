Olá, eu sou o Flávio Paixão
 
 
 
 
 
 
 
 
 
 
 

Sobre Mim
Construo infraestrutura na AWS com Terraform e documento o porquê de cada decisão: o que usei, o que não usei e o que o plan não prova. Meu portfólio são 3 cases de arquitetura AWS, cada um com módulos, CI, análise de custo e documentação, e um case de containers: um serviço em Go com Docker e Kubernetes.

🎓 Cursando Engenharia de Software (Ampli/Anhanguera, conclusão em 2028)

🎯 Objetivo: Cloud Engineer · DevOps Engineer · Python Developer (CLT remoto)

📜 AWS Certified Cloud Practitioner (CLF-C02, novembro de 2026) · Próximo passo: Solutions Architect Associate

☁️ Cases de Arquitetura AWS com Terraform
Projetos de estudo. Validados com terraform fmt, validate e plan. Nenhum deles foi aplicado (apply) em uma conta AWS, então não afirmo números de disponibilidade, latência nem custo real.

Case	Padrão	Stack	Tamanho	Repositório
🛡️ Seguros Horizonte	3 camadas, seguro e resiliente	Terraform · VPC · ALB · EC2 Auto Scaling · Aurora PostgreSQL · KMS · IAM · Secrets Manager · S3	6 módulos · plan com 69 recursos	Ver repositório
🛍️ Vitrine Modas	Serverless e orientado a eventos	Terraform · Python · Lambda · API Gateway · DynamoDB · Cognito · EventBridge · SQS · SNS · CloudFront · S3 · KMS	9 módulos · plan com 108 recursos · 5 funções Lambda	Ver repositório
🏦 Banco Rio	Alta disponibilidade e DR em 2 regiões	Terraform · Aurora Global Database · KMS multi-region · S3 com replicação · ALB · ACM · WAF · Route 53 · CloudTrail · Config · GuardDuty · Security Hub · AWS Backup	13 módulos · plan com 166 recursos	Ver repositório
O que cada case mostra
🛡️ Seguros Horizonte: rede em 2 zonas de disponibilidade, Security Groups em cadeia (internet, ALB, aplicação, banco), chaves KMS próprias, IAM de privilégio mínimo e senha do banco gerenciada pelo Secrets Manager. Os alertas do checkov viraram correções documentadas.

🛍️ Vitrine Modas: pedido e baixa de estoque na mesma transação do DynamoDB, preço sempre vindo do catálogo, Streams alimentando o EventBridge, login com Cognito e testes das funções com pytest e moto.

🏦 Banco Rio: os mesmos módulos usados em duas regiões, failover de DNS por health check (e o que ele não faz), backup com Vault Lock e camadas de auditoria e detecção. RPO e RTO são metas de projeto, não resultados medidos, e não afirmo conformidade com BACEN, LGPD, PCI-DSS ou SOX.

Em todos: CI no GitHub Actions (fmt, validate, tflint e checkov), tickets no Jira e documentação em README, ARCHITECTURE, DECISIONS e COST-ANALYSIS.

🐳 Case de Containers com Go, Docker e Kubernetes
Projeto de estudo. Roda localmente num cluster Kind, com custo zero. Nada foi publicado em nuvem, então não afirmo números de disponibilidade nem de carga.

Case	Padrão	Stack	Tamanho	Repositório
📡 StatusHub	Microsserviço containerizado no Kubernetes	Go · Docker (multi-stage, distroless) · Kubernetes · Kind · ConfigMap · GitHub Actions	2 réplicas · imagem de 4,88 MB compactada · 4 alvos monitorados	Ver repositório
O que o case mostra
📡 StatusHub: verificação de sites e APIs em paralelo com goroutines, timeout por alvo e resultados protegidos por sync.RWMutex. Imagem distroless sem shell, rodando como não-root (UID 65532). Deployment com 2 réplicas, liveness e readiness probes, requests/limits e lista de alvos num ConfigMap. No cluster, testei escalar réplicas, autocura de Pods, rollout restart depois de mudar o ConfigMap e rollback de um deploy quebrado sem derrubar o serviço. Os limites (verificações duplicadas por réplica, acesso só por port-forward) estão no DECISIONS.

CI no GitHub Actions (gofmt, go vet, go test -race e docker build), tickets no Jira e documentação em README, ARCHITECTURE, DECISIONS e RUNBOOK.

🛠️ Tecnologias & Ferramentas dos Cases
Infraestrutura como código: Terraform (módulos, múltiplas regiões, plan e validate)

AWS, rede e borda: VPC · ALB · CloudFront · Route 53 · ACM · WAF

AWS, computação e integração: EC2 Auto Scaling · Lambda · API Gateway · EventBridge · SQS · SNS

AWS, dados: Aurora PostgreSQL (incluindo Global Database) · DynamoDB · S3 · AWS Backup

AWS, segurança e auditoria: IAM · KMS · Cognito · Secrets Manager · CloudTrail · AWS Config · GuardDuty · Security Hub

AWS, observabilidade e custo: CloudWatch · X-Ray · AWS Budgets

Containers e orquestração: Docker (multi-stage, distroless, não-root) · Kubernetes (Deployments, Services, ConfigMaps, probes, rollout e rollback) · Kind · kubectl

CI/CD e qualidade: GitHub Actions · Git · GitHub · Jira · tflint · checkov · pytest · moto

Linguagens: Python · Go · HCL

🌐 Conecte-se Comigo
LinkedIn · GitHub · Portfólio
