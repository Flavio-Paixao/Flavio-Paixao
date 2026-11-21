Olá, eu sou o Flávio Paixão

Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem Mostrar imagem

Sobre Mim

Construo infraestrutura na AWS com Terraform e documento o porquê de cada decisão: o que usei, o que não usei e o que o plan não prova. Meu portfólio são 3 cases de arquitetura, cada um com módulos, CI, análise de custo e documentação, e o StatusHub, um serviço em Go que empacotei com Docker e operei em Kubernetes.

🎓 Cursando Engenharia de Software (Ampli/Anhanguera, conclusão em 2028) 🎯 Objetivo: Cloud Engineer · DevOps Engineer · Python Developer (CLT remoto) 

📜 AWS Certified Cloud Practitioner (CLF-C02, novembro de 2026) · Próximo passo: Solutions Architect Associate

☁️ Cases de Arquitetura AWS com Terraform

Projetos de estudo. Validados com terraform fmt, validate e plan. Nenhum deles foi aplicado (apply) em uma conta AWS, então não afirmo números de disponibilidade, latência nem custo real.

Case	Padrão	Stack	Tamanho	Repositório

🛡️ Seguros Horizonte	3 camadas, seguro e resiliente	Terraform · VPC · ALB · EC2 Auto Scaling · Aurora PostgreSQL · KMS · IAM · Secrets Manager · S3	6 módulos · plan com 69 recursos	Ver repositório

🛍️ Vitrine Modas	Serverless e orientado a eventos	Terraform · Python · Lambda · API Gateway · DynamoDB · Cognito · EventBridge · SQS · SNS · CloudFront · S3 · KMS	9 módulos · 5 funções Lambda	Ver repositório

🏦 Banco Rio	Alta disponibilidade e DR em 2 regiões	Terraform · Aurora Global Database · KMS multi-region · S3 com replicação · ALB · ACM · WAF · Route 53 · CloudTrail · Config · GuardDuty · Security Hub · AWS Backup	13 módulos · plan com 166 recursos	Ver repositório
O que cada case mostra

🛡️ Seguros Horizonte: rede em 2 zonas de disponibilidade, Security Groups em cadeia (internet, ALB, aplicação, banco), chaves KMS próprias, IAM de privilégio mínimo e senha do banco gerenciada pelo Secrets Manager. Os alertas do checkov viraram correções documentadas.

🛍️ Vitrine Modas: pedido e baixa de estoque na mesma transação do DynamoDB, preço sempre vindo do catálogo, Streams alimentando o EventBridge, login com Cognito e testes das funções com pytest e moto.

🏦 Banco Rio: os mesmos módulos usados em duas regiões, failover de DNS por health check (e o que ele não faz), backup com Vault Lock e camadas de auditoria e detecção. RPO e RTO são metas de projeto, não resultados medidos, e não afirmo conformidade com BACEN, LGPD, PCI-DSS ou SOX.

Em todos: CI no GitHub Actions (fmt, validate, tflint e checkov), tickets no Jira e documentação em README, ARCHITECTURE, DECISIONS e COST-ANALYSIS.

🐳 Go, Docker e Kubernetes

Projeto de estudo. Roda em Kubernetes local (cluster Kind), sem custo de nuvem. Os números abaixo são os que medi na minha máquina.

Projeto	O que faz	Stack	Destaques	Repositório
📡 StatusHub	Verifica de tempos em tempos se uma lista de sites está no ar e mostra o resultado numa página HTML e numa API JSON	Go · Docker · Kubernetes (Kind) · kubectl · GitHub Actions · Jira	Imagem de 4,88 MB compactada · 2 réplicas · probes · rollback testado	Ver repositório

📡 StatusHub:

Go: uma goroutine por alvo com sync.WaitGroup, resultados protegidos por RWMutex, http.Client com timeout de 5 s e graceful shutdown com signal.NotifyContext.
Docker: Dockerfile multi-stage, binário estático e imagem final distroless com usuário não-root, sem shell. O build caiu de 107 s para 6,7 s com o cache de camadas.
Kubernetes: Deployment com 2 réplicas, Service ClusterIP, probes de liveness (/healthz) e readiness (/readyz), requests e limits de CPU e memória e a lista de alvos num ConfigMap.
Operação: escalei réplicas, apaguei Pods para ver a autocura e simulei um deploy quebrado. O serviço continuou no ar e voltei com rollout undo.
CI e documentação: GitHub Actions com gofmt, go vet, go test -race e docker build, mais ARCHITECTURE, DECISIONS e RUNBOOK.
🛠️ Tecnologias & Ferramentas dos Projetos

Infraestrutura como código: Terraform (módulos, múltiplas regiões, plan e validate)

AWS, rede e borda: VPC · ALB · CloudFront · Route 53 · ACM · WAF

AWS, computação e integração: EC2 Auto Scaling · Lambda · API Gateway · EventBridge · SQS · SNS

AWS, dados: Aurora PostgreSQL (incluindo Global Database) · DynamoDB · S3 · AWS Backup

AWS, segurança e auditoria: IAM · KMS · Cognito · Secrets Manager · CloudTrail · AWS Config · GuardDuty · Security Hub

AWS, observabilidade e custo: CloudWatch · X-Ray · AWS Budgets

Containers e orquestração: Docker (multi-stage, distroless) · Kubernetes · Kind · kubectl

CI/CD e qualidade: GitHub Actions · Git · GitHub · Jira · tflint · checkov · pytest · moto · go test (com -race) · go vet

Linguagens: Python · Go · HCL

🌐 Conecte-se Comigo

LinkedIn · GitHub · Portfólio
