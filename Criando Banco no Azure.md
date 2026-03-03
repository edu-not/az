# AZ-900 – Criação de Banco de Dados no Azure (Aula Passo a Passo)

Este material foi estruturado como **aula prática + visão de prova**, focado na certificação **AZ-900**.

Objetivo da aula:
- Entender os tipos de banco no Azure
- Criar um banco passo a passo pelo Portal
- Aprender boas práticas
- Evitar erros comuns de prova e de ambiente real

---

# 1. Entendendo Banco de Dados no Azure (Antes de Criar)

No Azure, você NÃO cria apenas “um banco”.
Você escolhe um **modelo de serviço**.

Os principais para AZ-900 são:

## 1.1 Azure SQL Database
Modelo: PaaS  
Gerenciamento: Microsoft gerencia infraestrutura e SO  
Você gerencia: Dados e permissões

Ideal para:
- Aplicações modernas
- APIs
- Sistemas web

---

## 1.2 SQL Server em Máquina Virtual
Modelo: IaaS  
Você gerencia: Tudo (SO, patches, banco)

Ideal para:
- Sistemas legados
- Necessidade de controle total

---

## 1.3 Azure Cosmos DB
Banco NoSQL totalmente gerenciado

Ideal para:
- Alta escalabilidade global
- Aplicações distribuídas

---

# 2. Aula Prática – Criando um Azure SQL Database (Passo a Passo)

Vamos criar o serviço mais comum cobrado na AZ-900: **Azure SQL Database (PaaS)**.

---

## Passo 1 – Acessar o Portal

1. Acesse portal.azure.com
2. Clique em “Create a resource”
3. Pesquise por “SQL Database”
4. Clique em Create

---

## Passo 2 – Configuração Básica (Basics)

Preencher:

- Subscription
- Resource Group (crie um novo se necessário)
- Database name
- Server (criar novo servidor)

Ao criar o servidor você define:
- Nome do servidor
- Região
- Login administrador
- Senha

Dica importante:
A região impacta latência e custo.

Erro comum:
Criar servidor em uma região diferente da aplicação.

---

## Passo 3 – Compute + Storage

Escolher modelo de compra:

- DTU (modelo antigo, mais simples)
- vCore (modelo recomendado pela Microsoft)

Para AZ-900, lembre:

DTU = modelo simplificado  
vCore = mais flexível e recomendado

Dica de custo:
Comece com camada Basic ou General Purpose para testes.

Erro comum:
Escolher camada muito alta sem necessidade → custo elevado.

---

## Passo 4 – Networking

Escolher:

- Public endpoint
- Private endpoint

Para laboratório, pode usar público com firewall configurado.

Muito importante:
Adicionar seu IP em “Set server firewall”.

Erro clássico:
Criar banco corretamente e depois não conseguir conectar por não liberar o IP.

---

## Passo 5 – Segurança

Opções importantes:

- Defender for SQL
- Transparent Data Encryption (TDE) – já vem habilitado por padrão

Para prova:
Azure SQL Database já possui criptografia em repouso habilitada.

---

## Passo 6 – Review + Create

Revisar configurações
Clicar em Create
Aguardar deploy

Após criado:
Ir em “Query editor” ou conectar via SSMS/Azure Data Studio.

---

# 3. Conceitos Importantes para AZ-900

## 3.1 PaaS x IaaS no Banco

SQL Database = PaaS  
SQL Server VM = IaaS

Se a questão falar:
- “Menos gerenciamento” → PaaS
- “Controle total do SO” → IaaS

---

## 3.2 Alta Disponibilidade

Azure SQL Database já possui:
- Backup automático
- Alta disponibilidade embutida

Você não precisa configurar cluster manualmente.

---

## 3.3 Backup

Azure SQL Database realiza:
- Backup automático
- Point-in-time restore

Erro comum de prova:
Achar que precisa configurar backup manualmente.

---

# 4. Custos Envolvidos

Você paga por:

- Compute
- Storage
- Backup adicional (retenção estendida)

Dica:
Banco continua cobrando mesmo sem conexão ativa.

---

# 5. Erros Mais Comuns (Vida Real + Prova)

- Não liberar IP no firewall
- Criar servidor na região errada
- Confundir SQL Database com SQL Server em VM
- Escolher camada muito cara
- Achar que precisa gerenciar sistema operacional no PaaS

---

# 6. Resumo Final da Aula

Se você quer:

Controle total → SQL Server em VM  
Menos gerenciamento → Azure SQL Database  
Escala global NoSQL → Cosmos DB

Frase para memorizar:

Banco PaaS = Microsoft gerencia infraestrutura  
Banco IaaS = Você gerencia tudo

---

Se quiser, posso complementar com:
- Mapa mental de bancos no Azure
- Tabela comparativa SQL vs Cosmos DB
- Questões estilo AZ-900 sobre bancos
- Aula sobre criação via CLI ou PowerShell

