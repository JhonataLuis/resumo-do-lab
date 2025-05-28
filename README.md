# resumo-do-lab
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do lab na DIO

Microsoft Azure é uma plataforma de computação em nuvem que oferece serviços como máquinas virtuais, bancos de dados gerenciados e soluções de IA. Ela permite executar aplicações em escala global com alta disponibilidade e segurança. Entre seus principais serviços estão Azure VMs (máquinas virtuais), Azure Kubernetes Service (AKS) para orquestração de containers e Azure Functions para serverless. Para armazenamento, destaca-se o Blob Storage (arquivos) e o Cosmos DB (NoSQL). Na área de redes, oferece Virtual Network e Load Balancer, enquanto em segurança, o Azure Active Directory gerencia autenticação. A plataforma também inclui ferramentas de IA, como Azure Machine Learning e Cognitive Services. Uma vantagem é a integração com produtos Microsoft, como Windows Server e Office 365. Para praticar, o Azure Lab Services permite criar ambientes de teste sob demanda, ideal para treinar sem custos elevados. Comparado à AWS, o Azure se destaca em cenários híbridos e para empresas já inseridas no ecossistema Microsoft. Certificações como AZ-900 (Fundamentos) e AZ-204 (Desenvolvedor) validam conhecimentos.

## Laboratório Prático: Criação de Máquina Virtual no Azure
Objetivo: Dominar a criação e gestão de VMs na Azure, documentando aprendizados em um repositório estruturado.
📝 Anotações & Dicas Essenciais
1. Antes de Começar
✔ Conta Gratuita: Use o Azure Free Tier (US$ 200 em créditos por 30 dias).
✔ Extensão "Azure Account" no VS Code: Gerencie recursos diretamente do editor.

🔧 Passo a Passo para Criar uma VM
Acesse o Portal Azure → "Máquinas Virtuais" → "Criar".

Configurações Básicas:

Sistema Operacional: Ubuntu 22.04 LTS (gratuito) ou Windows Server (custo adicional).

Tamanho da VM: B1s (1 vCPU, 1 GB RAM - elegível para free tier).

Autenticação: Para Linux, use SSH Key (mais seguro que senha).

Rede (NSG - Network Security Group):

Libere apenas as portas necessárias (ex.: SSH:22, RDP:3389).

Dica: Crie regras personalizadas para limitar acesso por IP.

Disco:

Use SSD Standard para balancear custo/performance.

Opcional: Adicione um disco de dados separado para armazenamento.

Conectando à VM:

Linux: ssh -i ~/.ssh/chave_azure.pem usuario@IP-publico

Windows: Use o RDP (baixe o arquivo .rdp gerado pelo Azure).

💡 Dicas de Otimização
Desligue a VM quando não usar para evitar custos (ou use VMs Spot para economizar até 90%).

Monitore custos em tempo real: Acesse "Cost Management + Billing" no portal.

Automatize com CLI:

bash
# Criar VM via Azure CLI
az vm create --resource-group MeuRG --name VM-Lab --image UbuntuLTS --admin-username azureuser --generate-ssh-keys

## 🚀 Próximos Desafios (Para Evoluir)
Adicione um Load Balancer para distribuir tráfego entre múltiplas VMs.

Configure Backups Automatizados com Azure Backup.

Explore IaC: Crie a VM usando Terraform ou Bicep.
