# AZ-900 – Criação de Máquinas Virtuais (VMs) no Microsoft Azure

Este material foi criado para **estudo da certificação AZ-900**, seguindo a **terminologia, conceitos e boas práticas da Microsoft**. O foco é entender **o que é**, **como funciona** e **quais erros são comuns** ao criar uma VM no Azure.

---

## 1. O que é uma Máquina Virtual no Azure?

Uma **Azure Virtual Machine (VM)** é um recurso de **computação sob demanda** que permite executar sistemas operacionais e aplicações na nuvem da Microsoft.

Características principais:
- Infraestrutura como Serviço (**IaaS**)
- Total controle do sistema operacional
- Escalável (vertical e horizontalmente)
- Cobrança baseada em **uso (pay-as-you-go)**

📌 **Cai muito na prova**: VM é IaaS, não PaaS.

---

## 2. Componentes envolvidos na criação de uma VM

Ao criar uma VM, o Azure **não cria apenas um recurso**, mas vários recursos associados:

- **Resource Group**
- **Virtual Machine**
- **Disco do sistema operacional (OS Disk)**
- **Discos de dados (opcional)**
- **Virtual Network (VNet)**
- **Subnet**
- **Network Interface (NIC)**
- **Network Security Group (NSG)**
- **Public IP Address** (opcional)

⚠️ Erro comum: achar que a VM é um recurso isolado.

---

## 3. Etapas de criação de uma VM no Azure Portal

### 3.1 Básico (Basics)

Configurações principais:
- **Subscription**
- **Resource Group**
- **Virtual machine name**
- **Region** (ex: Brazil South)
- **Availability options**
- **Image** (Windows Server, Ubuntu, etc.)
- **Size** (SKU da VM)
- **Authentication type** (senha ou SSH)

⚠️ Pontos de atenção:
- Região impacta **latência e custo**
- Nem todo tamanho de VM está disponível em todas as regiões

---

### 3.2 Discos (Disks)

Tipos de disco gerenciado:
- **Standard HDD** (mais barato)
- **Standard SSD**
- **Premium SSD** (alto desempenho)

📌 Na AZ-900, foque em:
- Diferença entre **custo x performance**

⚠️ Erro comum:
- Escolher Premium SSD sem necessidade → custo alto

---

### 3.3 Rede (Networking)

Configurações:
- Virtual Network (VNet)
- Subnet
- Public IP
- Network Security Group (NSG)

NSG controla:
- Tráfego **de entrada (Inbound)**
- Tráfego **de saída (Outbound)**

⚠️ Erros muito comuns:
- Criar VM sem liberar a porta correta (ex: 22 para Linux, 3389 para Windows)
- Expor portas públicas sem necessidade (falha de segurança)

---

### 3.4 Gerenciamento (Management)

Opções importantes:
- **Azure Monitor**
- **Boot diagnostics**
- **Auto-shutdown**

📌 Para prova:
- Auto-shutdown ajuda a **reduzir custos**

---

### 3.5 Avançado e Tags

- **Tags** são pares chave/valor
- Usadas para:
  - Organização
  - Custos
  - Governança

Exemplo:
```
Environment: Dev
Owner: TI
```

⚠️ Erro comum:
- Não usar tags e depois não conseguir rastrear custos

---

## 4. Disponibilidade e Resiliência

Opções de alta disponibilidade:
- **Availability Zones**
- **Availability Sets**

📌 AZ-900 cobra o conceito, não a implementação técnica.

⚠️ Atenção:
- Availability Zones **não estão disponíveis em todas as regiões**

---

## 5. Segurança na criação de VMs

Boas práticas da Microsoft:
- Usar **NSG** para controle de tráfego
- Evitar IP público quando possível
- Preferir autenticação por **SSH Key** (Linux)
- Aplicar **Least Privilege**

⚠️ Erros comuns em prova:
- Confundir NSG com Firewall do Azure
- Achar que VM já vem segura por padrão

---

## 6. Custos e Modelo de Cobrança

Você paga por:
- Tempo de execução da VM
- Tipo/tamanho da VM
- Tipo de disco
- Tráfego de saída

💡 Importante:
- VM **desligada (Stopped)** não cobra computação
- VM **alocada** continua gerando custo

⚠️ Pegadinha de prova:
- Deletar VM ≠ deletar discos

---

## 7. Erros mais comuns ao criar VMs (Resumo para prova)

❌ Escolher região errada
❌ Não liberar portas no NSG
❌ Expor VM diretamente à internet
❌ Escolher tamanho de VM maior que o necessário
❌ Esquecer custos de disco e IP público
❌ Confundir IaaS com PaaS

---

## 8. O que a AZ-900 mais cobra sobre VMs

- Conceito de VM
- Diferença entre IaaS, PaaS e SaaS
- Componentes básicos
- Segurança e custos
- Alta disponibilidade (conceito)

---

## 9. Resumo rápido – AZ-900 (para revisão antes da prova)

### Azure Virtual Machines – em 1 página

- Azure VM = **IaaS**
- Usuário gerencia:
  - Sistema operacional
  - Patches
  - Aplicações
- Azure gerencia:
  - Hardware físico
  - Datacenter
  - Rede física

**Principais pontos cobrados:**
- VM é escalável
- Cobra por uso
- Depende de vários recursos (disco, rede, NSG)

**Custos:**
- Compute (tempo ligada)
- Disco (continua cobrando mesmo desligada)
- IP público
- Tráfego de saída

**Segurança:**
- NSG controla tráfego
- Não vem “segura por padrão”
- Evitar IP público

**Alta disponibilidade (conceito):**
- Availability Sets
- Availability Zones

⚠️ Pegadinhas frequentes:
- Confundir Stopped com Deallocated
- Achar que deletar VM apaga discos
- Confundir NSG com Azure Firewall

---

## 10. Comparação: VM x App Service x Containers (estilo prova AZ-900)

### 10.1 Azure Virtual Machine (VM)

**Modelo:** IaaS  
**Controle:** Total do SO  
**Uso típico:**
- Sistemas legados
- Aplicações que precisam de controle do SO
- Ambientes personalizados

✅ Vantagens:
- Flexível
- Compatível com qualquer aplicação

❌ Desvantagens:
- Mais gerenciamento
- Mais responsabilidade do cliente

---

### 10.2 Azure App Service

**Modelo:** PaaS  
**Controle:** Apenas da aplicação  
**Uso típico:**
- APIs
- Aplicações web
- Backends

Azure gerencia:
- SO
- Runtime
- Atualizações

✅ Vantagens:
- Menos gerenciamento
- Escala automática

❌ Desvantagens:
- Menos controle
- Limitado a certos runtimes

---

### 10.3 Containers (Azure Container Instances / AKS – conceito)

**Modelo:** Entre IaaS e PaaS  
**Controle:** Aplicação + container  
**Uso típico:**
- Microsserviços
- Apps portáveis

✅ Vantagens:
- Leves
- Portáveis

❌ Desvantagens:
- Complexidade maior que App Service

---

### 10.4 Tabela comparativa (muito cobrada)

| Serviço | Modelo | Gerencia SO? | Escala | Complexidade |
|-------|------|--------------|--------|-------------|
| VM | IaaS | Cliente | Manual/Auto | Alta |
| App Service | PaaS | Azure | Automática | Baixa |
| Containers | Misto | Parcial | Alta | Média |

---

## 11. Dicas finais para a AZ-900

- Se a questão fala em **controle total**, pense em VM
- Se fala em **menos gerenciamento**, pense em App Service
- Se fala em **portabilidade**, pense em Containers
- AZ-900 cobra **conceito**, não configuração técnica

👉 Se quiser, posso criar:
- Questões comentadas estilo prova
- Flashcards prontos
- Um mapa mental em MD


---

## 12. Mapa Mental – Compute no Azure (AZ-900)

> Use este mapa mental para **memorizar rapidamente** e **identificar a resposta certa na prova**.

```
                        COMPUTE NO AZURE
                               │
        ┌──────────────────────┼──────────────────────┐
        │                      │                      │
       VM                 App Service             Containers
    (IaaS)                  (PaaS)                 (Misto)
        │                      │                      │
 ┌──────┼──────┐         ┌─────┼─────┐        ┌───────┼────────┐
 │      │      │         │     │     │        │       │        │
Controle Custos Segurança Código Escala SO   Portável  Leve   Orquestração
 Total  PayGo   NSG     Apenas App Auto   Gerenciado  Docker   AKS
 │
 │
 Usuário gerencia:
 - Sistema Operacional
 - Patches
 - Aplicações

 Azure gerencia:
 - Hardware físico
 - Datacenter
 - Rede física
```

---

### Como usar esse mapa mental na prova

- 🧠 **Apareceu “controle total” → VM (IaaS)**
- 🧠 **Apareceu “menos gerenciamento” → App Service (PaaS)**
- 🧠 **Apareceu “portabilidade / Docker” → Containers**

---

### Pegadinhas clássicas ligadas ao mapa mental

- ❌ VM não é PaaS
- ❌ App Service não dá acesso ao SO
- ❌ Containers não eliminam totalmente gerenciamento
- ❌ NSG ≠ Azure Firewall

---

### Técnica de memorização rápida (dica de prova)

👉 Repita mentalmente:

- **VM = Controle**
- **App Service = Simplicidade**
- **Container = Portabilidade**

