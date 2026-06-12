# ☁️ Arquitetura Cloud AWS para E-commerce

### Estudo de Caso — MegaStore BR · Foco em Monitoramento e observabilidade.

---

## Sobre este projeto:

Este estudo de caso documenta a proposta de arquitetura cloud AWS para a **MegaStore BR**, um e-commerce ficticio que enfrentava problemas de escalabilidade, sobrecarga de banco de dados e ausência de monitoramento preventivo durante picos de acesso sazonais.

O objetivo foi analisar os desafios do negócio e propor, com justificativa técnica, os serviços AWS mais adequados para cada problema identificado em **monitoramento e observabilidade**.

---

## 🏗️ Arquitetura proposta

Para cada desafio foi selecionado o serviço AWS mais adequado, com justificativa técnica explícita:

| Cenário | Solução AWS | Justificativa |
|---|---|---|
| Escalabilidade limitada | EC2 + Auto Scaling + ALB | Criação e remoção automática de instâncias conforme a demanda |
| Banco sobrecarregado | RDS Aurora + Read Replica + ElastiCache Redis | Reduz carga nas consultas e melhora tempo de resposta com cache |
| Conteúdo lento | S3 + CloudFront | Entrega arquivos estáticos pela borda da rede, reduzindo latência |
| Monitoramento reativo | CloudWatch + SNS | Métricas, logs e alertas preventivos com notificação imediata da equipe |

---

![Diagrama de Arquitetura MegaStore BR](docs/images/arquitetura%20monitoramento.png)

> *Fluxo completo:  usuários → Route 53 → CloudFront → ALB → Auto Scaling Group (EC2) → ElastiCache + RDS Aurora, com monitoramento via CloudWatch + SNS.*

---

## Foco: Monitoramento com Amazon CloudWatch

Como o foco deste estudo foi **observabilidade**, o CloudWatch foi detalhado como serviço central da solução:

```
CloudWatch Metrics  →  CloudWatch Alarms  →  Amazon SNS  →  Equipe de TI
(CPU, requisições)     (thresholds)           (alertas)      (Discord/Slack/e-mail)
```

- **CloudWatch Metrics** — monitoramento de CPU, requisições e métricas customizadas em tempo real
- **CloudWatch Alarms** — alertas automáticos baseados em thresholds configuráveis
- **Amazon SNS**  — envio de notificações para a equipe via Discord, Slack ou e-mail

---

## ✅ Resultados
Com a arquitetura proposta, a MegaStore BR passa de um modelo **reativo** para uma infraestrutura **preparada para variações de demanda**:

- ✔️ Maior disponibilidade durante picos com Auto Scaling automático
- ✔️ Redução de gargalos no banco com Read Replicas e ElastiCache Redis
- ✔️ Melhor desempenho na entrega de conteúdo estático via CloudFront
- ✔️ Detecção antecipada de incidentes com alertas automatizados


---

## As próximas camadas planejadas para esta arquitetura:

- [ ] **Segurança de rede** — VPC com subnets públicas/privadas, IAM, Security Groups, WAF
- [ ] **Automação de infraestrutura** — IaC com Terraform ou AWS CloudFormation
- [ ] **Disaster Recovery** — estratégias de backup, RTO e RPO
- [ ] **Otimização de custos** — análise com AWS Cost Explorer e Savings Plans

##  Aprendizados
> *"Durante o estudo de caso, compreendi que uma arquitetura em nuvem não deve ser construída apenas com foco em desempenho. Foi necessário analisar o equilíbrio entre escalabilidade, disponibilidade, monitoramento e custo para selecionar os serviços mais adequados para cada problema — garantindo que a solução permaneça sustentável à medida que a empresa cresce."*

---

## 📁 Estrutura do repositório

```
📦 Megastore-br
 ┣ 📄 README.md
 ┣ 📄 estudo-de-caso.pdf        
 ┗ 📁 docs/images/                      ← documento técnico completo
    ┗ 🖼️ arquitetura monitoramento.png  ← diagrama de arquitetura AWS
```
---
## 🛠️ Serviços AWS abordados

![EC2](https://docs.aws.amazon.com/pt_br/ec2/)
![Auto Scaling](https://docs.aws.amazon.com/pt_br/autoscaling/ec2/userguide/launch-templates.html)
![RDS](https://www.youtube.com/watch?v=etSqI7XkJ28)
![ElastiCache](https://docs.aws.amazon.com/pt_br/AmazonElastiCache/latest/dg/WhatIs.corecomponents.html)
![S3](https://aws.amazon.com/pt/s3/storage-classes/?nc=sn&loc=3)
![CloudFront](https://docs.aws.amazon.com/pt_br/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
![CloudWatch](https://docs.aws.amazon.com/pt_br/AmazonCloudWatch/latest/monitoring/Investigations.html)
![SNS](https://docs.aws.amazon.com/pt_br/iot/latest/developerguide/sns-rule-action.html)
![Route 53](https://aws.amazon.com/pt/route53/)

---
 **Luana Silva** 
 Estudante de Cloud Computing · EDN · AWS Re/Start - Gaduated

![LinkedIn](https://www.linkedin.com/in/luanasilva-lu-nas)


---

*Estudo técnico de arquitetura em nuvem · 2026*
