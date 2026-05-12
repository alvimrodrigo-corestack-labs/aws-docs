# 🏗️ Cloud & DevOps Engineering Lab

Bem-vindo ao meu laboratório de engenharia de infraestrutura. Este ecossistema foi projetado para demonstrar padrões de produção em arquiteturas **Multi-Cloud (AWS & Azure)**, utilizando práticas rigorosas de **GitOps**, **IaC** e **FinOps**.

## 🎯 Objetivo do Projeto
O objetivo desta organização é simular um ambiente corporativo de alta maturidade, onde a infraestrutura é tratada como software, com foco em:
*   **Segurança:** Autenticação via OIDC (Keyless) e gerenciamento de identidades (IRSA/Workload Identity).
*   **Escalabilidade:** Orquestração de containers com EKS e AKS utilizando instâncias Spot e Fargate.
*   **Eficiência de Custo:** Monitoramento de gastos via Infracost e ciclos de vida de recursos efêmeros.
*   **Padronização:** Módulos Terraform versionados e reutilizáveis.

---

## 🗺️ Mapa da Infraestrutura

### 1. Camada de Fundação (IaC)
*   **tf-aws-modules** : Módulos Terraform customizados e versionados para VPC, EKS, RDS e IAM.
*   **tf-aws-resources** : Gerenciamento de estados e ambientes (Dev/Prod) utilizando **Terragrunt**.
*   **tf-state** : Provisionamento inicial do Backend (S3/DynamoDB) para Remote State.

### 2. Orquestração e GitOps
*   **cluster-management** : Configuração do plano de controle do EKS/AKS e instalação do **ArgoCD**.
*   **k8s-library-charts** : Repositório de Helm Charts padronizados para a organização.

### 3. Aplicações & Entrega
*   **fullstack-app-gitops** : Aplicação de demonstração com Ingress, SSL, monitoramento e integração com serviços gerenciados da nuvem.

---

## 🛠️ Stack Tecnológica

| Categoria | Tecnologias |
| :--- | :--- |
| **Cloud Providers** | AWS, Azure |
| **Infrastructure as Code** | Terraform, Terragrunt |
| **CI/CD & GitOps** | GitHub Actions, ArgoCD |
| **Orquestração** | Kubernetes (EKS/AKS), Helm |
| **Observabilidade** | Prometheus, Grafana, CloudWatch |
| **Security & FinOps** | OIDC, Infracost, AWS Secrets Manager |

---

## 🚀 Fluxo de Trabalho (GitOps Flow)
1.  Mudanças de infraestrutura são propostas via **Pull Request**.
2.  O **GitHub Actions** executa o `terragrunt plan` e posta o custo estimado via **Infracost**.
3.  Após o merge, o deploy é realizado automaticamente no ambiente de destino.
4.  O **ArgoCD** sincroniza o estado dos clusters Kubernetes com os repositórios de manifestos.

---
> 💡 **Nota:** Para otimização de custos (Free Tier), os recursos são provisionados sob demanda e destruídos após a validação. Os logs e evidências de execução podem ser encontrados na aba **Actions** de cada repositório.

---
