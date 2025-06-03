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

## 1. Criar um Banco de dados Azure
Acesse portal.azure.com e faça login com sua conta Microsoft.

2. Criar um Novo Banco de Dados
Opção A: Azure SQL Database (Recomendado para SQL Server)
No menu, clique em "Criar um recurso" > "Bancos de Dados" > "SQL Database".

Preencha os campos:

Assinatura: Selecione sua assinatura.

Grupo de recursos: Crie um novo (ex: lab-banco-dados).

Nome do banco de dados: meu-banco-sql.

Servidor: Clique em "Criar novo" e defina:

Nome do servidor: meu-servidor-sql (deve ser único globalmente).

Localização: "Sudeste do Brasil" (ou mais próximo de você).

Método de autenticação: "Usar autenticação do SQL".

Login de administrador: admin-lab (defina uma senha segura).

Tipo de computação: "Uso geral" (mais barato para testes).

Armazenamento: 5 GB (suficiente para laboratório).

Clique em "Revisar + criar" e depois em "Criar".

Opção B: Azure Database for MySQL/PostgreSQL
No menu, clique em "Criar um recurso" > "Bancos de Dados" > "Azure Database for MySQL" (ou PostgreSQL).

Preencha os campos:

Nome do servidor: meu-servidor-mysql.

Tipo de servidor: "Flexível" (mais econômico).

Usuário/senha do administrador: Defina credenciais seguras.

Tamanho do armazenamento: 20 GB (mínimo recomendado).

Clique em "Revisar + criar" > "Criar".

Adicionado assunto sobre identidade, acesso e segurança com Azure.

## NPL

Resumo do Desafio de Azure Speech & Language Studio
Objetivo:
Desenvolver habilidades práticas em IA de voz e linguagem natural usando ferramentas do Azure.

Entregável:
Repositório organizado com anotações e insights das práticas.

Passos Essenciais para o Laboratório
1. Configuração Inicial
Crie recursos no Azure:

Speech Service (para análise de fala)

Language Service (para NLP)

Acesse os estúdios:

Azure Speech Studio

Azure Language Studio

2. Azure Speech Studio (Foco em Voz)
Conversão Fala-Texto:

Grave ou envie áudios para transcrição automática.

Teste idiomas diferentes (ex: PT-BR, EN-US).

Conversão Texto-Fala:

Crie vozes sintéticas personalizadas (ajuste tom, velocidade, emoções).

Identificação de Locutor:

Diferencie falantes em um diálogo.

3. Language Studio (Foco em NLP)
Análise de Sentimentos:

Avalie emoções em textos (positivo/neutro/negativo).

Reconhecimento de Entidades:

Identifique pessoas, locais, datas em textos.

Extração de Palavras-Chave:

Detecte termos relevantes em documentos.

4. Cenário Integrado (Exemplo Prático)
Transcreva um áudio de atendimento ao cliente (Speech Studio).

Analise sentimentos e extraia reclamações (Language Studio).

Gere insights automáticos:

Exemplo: "Cliente insatisfeito com prazo de entrega".

✨ Dicas Adicionais
Documente:

Precisão por idioma (ex: PT-BR vs. inglês).

Limitações encontradas (ex: termos técnicos).

Integração: Use Python SDK para automatizar fluxos.

Monitore custos no Azure para evitar gastos inesperados.

Estrutura de Repositório Sugerida:

plaintext
📁 Lab_Azure-Speech-Language/
├── 📄 README.md
├── 📁 speech-studio/     # Testes de transcrição, síntese de voz
├── 📁 language-studio/   # Análises de sentimentos/entidades
└── 📁 integracao/        # Fluxos combinados (ex: áudio → texto → insights)

## Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados
### Objetivo Principal:
Aplicar técnicas de organização e pesquisa de documentos utilizando inteligência artificial.

Passos Fundamentais:

Ingestão de Conteúdo para IA:

Coleta e preparação de dados/documentos para processamento por ferramentas de IA.

Criação de Índices Inteligentes:

Indexação automatizada dos documentos, permitindo busca eficiente através de metadados ou conteúdo semântico gerado por IA.

Exploração Prática dos Dados:

Utilização dos índices criados para realizar pesquisas, análises e recuperação inteligente da informação organizada.

Conclusão:
O laboratório focou na integração de IA para transformar dados brutos em informações estruturadas e acessíveis, capacitando os participantes a implementar fluxos de organização e recuperação documental automatizados.

## Explorando os Recursos de IA Generativa com Copilot e OpenAI
### Objetivo Principal:
Explorar as funcionalidades do Copilot e ferramentas da OpenAI, com foco em filtros de conteúdo e recursos de criação assistida por IA.

Elementos-Chave Abordados:

Filtros de Conteúdo:

Mecanismos para controle e adequação de saídas geradas pela IA, garantindo conformidade com diretrizes éticas e de segurança.

Criação Assistida por IA:

Utilização de prompts estratégicos para gerar textos, códigos, análises e outros conteúdos com apoio das ferramentas.

Entregável Concreto:

Repositório organizado contendo:

Exemplos práticos de uso das ferramentas.

Prompts aplicados em diferentes contextos.

Anotações documentando aprendizados e observações.

Conclusão:
O laboratório capacitou os participantes a aplicar recursos avançados de IA (Copilot/OpenAI) na criação de conteúdo controlado e eficiente, resultando em um repositório estruturado para consulta futura e compartilhamento de conhecimento.


