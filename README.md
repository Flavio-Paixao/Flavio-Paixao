# Olá, eu sou o Flávio Paixão

![Terraform](https://img.shields.io/badge/-Terraform-black?style=flat-square&logo=terraform) ![AWS](https://img.shields.io/badge/-AWS-black?style=flat-square&logo=amazonaws) ![Python](https://img.shields.io/badge/-Python-black?style=flat-square&logo=python) ![GitHub Actions](https://img.shields.io/badge/-GitHub_Actions-black?style=flat-square&logo=githubactions) ![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-black?style=flat-square&logo=postgresql) ![DynamoDB](https://img.shields.io/badge/-DynamoDB-black?style=flat-square&logo=amazondynamodb) ![Jira](https://img.shields.io/badge/-Jira-black?style=flat-square&logo=jira) ![Git](https://img.shields.io/badge/-Git-black?style=flat-square&logo=git)

## Sobre Mim

Construo infraestrutura na AWS com Terraform e documento o porquê de cada decisão: o que usei, o que não usei e o que o `plan` não prova. Meu portfólio são 3 cases de arquitetura, cada um com módulos, CI, análise de custo e documentação.

🎓 Cursando Engenharia de Software (Ampli/Anhanguera, conclusão em 2028)
🎯 Objetivo: Cloud Engineer · DevOps Engineer · Python Developer (CLT remoto)
📜 Em preparação: AWS Certified Cloud Practitioner, depois Solutions Architect Associate

---

## ☁️ Cases de Arquitetura AWS com Terraform

> **Projetos de estudo.** Validados com `terraform fmt`, `validate` e `plan`. Nenhum deles foi aplicado (`apply`) em uma conta AWS, então não afirmo números de disponibilidade, latência nem custo real.

| Case | Padrão | Stack | Tamanho | Repositório |
|---|---|---|---|---|
| 🛡️ Seguros Horizonte | 3 camadas, seguro e resiliente | Terraform · VPC · ALB · EC2 Auto Scaling · Aurora PostgreSQL · KMS · IAM · Secrets Manager · S3 | 6 módulos · `plan` com 69 recursos | [Ver repositório](https://github.com/Flavio-Paixao/seguros-horizonte-aws) |
| 🛍️ Vitrine Modas | Serverless e orientado a eventos | Terraform · Python · Lambda · API Gateway · DynamoDB · Cognito · EventBridge · SQS · SNS · CloudFront · S3 · KMS | 9 módulos · 5 funções Lambda | [Ver repositório](https://github.com/Flavio-Paixao/vitrine-modas-aws) |
| 🏦 Banco Rio | Alta disponibilidade e DR em 2 regiões | Terraform · Aurora Global Database · KMS multi-region · S3 com replicação · ALB · ACM · WAF · Route 53 · CloudTrail · Config · GuardDuty · Security Hub · AWS Backup | 13 módulos · `plan` com 166 recursos | [Ver repositório](https://github.com/Flavio-Paixao/banco-rio-aws) |

### O que cada case mostra

**🛡️ Seguros Horizonte:** rede em 2 zonas de disponibilidade, Security Groups em cadeia (internet, ALB, aplicação, banco), chaves KMS próprias, IAM de privilégio mínimo e senha do banco gerenciada pelo Secrets Manager. Os alertas do checkov viraram correções documentadas.

**🛍️ Vitrine Modas:** pedido e baixa de estoque na mesma transação do DynamoDB, preço sempre vindo do catálogo, Streams alimentando o EventBridge, login com Cognito e testes das funções com pytest e moto.

**🏦 Banco Rio:** os mesmos módulos usados em duas regiões, failover de DNS por health check (e o que ele não faz), backup com Vault Lock e camadas de auditoria e detecção. RPO e RTO são metas de projeto, não resultados medidos, e não afirmo conformidade com BACEN, LGPD, PCI-DSS ou SOX.

Em todos: CI no GitHub Actions (fmt, validate, tflint e checkov), tickets no Jira e documentação em `README`, `ARCHITECTURE`, `DECISIONS` e `COST-ANALYSIS`.

---

## 🛠️ Tecnologias & Ferramentas dos Cases

**Infraestrutura como código:** Terraform (módulos, múltiplas regiões, plan e validate)

**AWS, rede e borda:** VPC · ALB · CloudFront · Route 53 · ACM · WAF

**AWS, computação e integração:** EC2 Auto Scaling · Lambda · API Gateway · EventBridge · SQS · SNS

**AWS, dados:** Aurora PostgreSQL (incluindo Global Database) · DynamoDB · S3 · AWS Backup

**AWS, segurança e auditoria:** IAM · KMS · Cognito · Secrets Manager · CloudTrail · AWS Config · GuardDuty · Security Hub

**AWS, observabilidade e custo:** CloudWatch · X-Ray · AWS Budgets

**CI/CD e qualidade:** GitHub Actions · Git · GitHub · Jira · tflint · checkov · pytest · moto

**Linguagens:** Python · HCL

---

## 🌐 Conecte-se Comigo

[LinkedIn](https://www.linkedin.com/in/fl%C3%A1vio-paix%C3%A3o-083bb3415) · [GitHub](https://github.com/Flavio-Paixao) · [Portfólio](https://flaviopaixao.dev)
 
