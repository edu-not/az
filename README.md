# Guia: Como realizar buscas de serviços no Azure Portal

Este README explica, de forma simples e direta, como localizar qualquer serviço no **Azure Portal**, ideal para novos usuários ou para padronizar procedimentos internos.

---

## 📌 1. Acessar o Azure Portal

1. Abra o navegador.
2. Acesse: [https://portal.azure.com](https://portal.azure.com)
3. Faça login com sua conta corporativa.

---

## 🔍 2. Usando a barra de busca principal

A forma mais rápida de localizar qualquer recurso ou serviço.

1. No topo da página, localize a **barra de busca**.
2. Digite o nome do serviço, por exemplo:

   * **Virtual Machines**
   * **Storage Accounts**
   * **Virtual Network**
   * **Key Vault**
   * **App Services**
3. O Azure mostrará:

   * Serviços
   * Recursos existentes
   * Documentação
4. Clique no item desejado.

> 💡 Dica: Mesmo busca parcial funciona — por exemplo, digitar **vm** já mostra *Virtual Machines*.

---

## 🗂️ 3. Navegar pelos serviços no menu lateral

Se você não souber exatamente o nome do serviço:

1. No canto esquerdo, clique em **All services (Todos os serviços)**.
2. Use os filtros por categoria, como:

   * **Compute** (VMs, Scale Sets, Functions)
   * **Networking** (VNet, Subnets, Load Balancer, Firewall)
   * **Storage** (Blob Storage, File Shares, Disks)
   * **Security** (Defender, Key Vault)
3. Localize o serviço na lista ou use a barra de busca dentro da página.

> 💡 Dica: Marque o serviço com ★ para deixá-lo em **Favorites** e aparecer no menu inicial.

---

## 🧭 4. Usando o Resource Graph Explorer (opcional)

Para buscas avançadas, como listar recursos por assinatura, tags ou grupos de recurso.

1. Busque por **Resource Graph Explorer**.
2. Execute consultas como:

   ```kusto
   Resources
   | where type =~ "Microsoft.Compute/virtualMachines"
   ```
3. Filtre recursos por região, tag ou tipo.

---

## 🗄️ 5. Buscando diretamente seus recursos

O Azure também oferece buscas contextuais:

### 🟦 Buscar por Grupo de Recursos

1. No menu esquerdo, clique em **Resource groups**.
2. Use a barra de busca para localizar o grupo.
3. Clique no grupo para ver todos os recursos dentro dele.

### 🟩 Buscar por Assinatura

1. Vá em **Subscriptions**.
2. Escolha a assinatura correta.
3. Use a aba **Resources** para listar tudo.

---

## 🧪 6. Problemas comuns ao buscar serviços

| Problema            | Causa                          | Solução                                        |
| ------------------- | ------------------------------ | ---------------------------------------------- |
| Serviço não aparece | Filtro de assinatura incorreto | Troque a assinatura no topo do portal          |
| Recursos sumiram    | RBAC sem permissão             | Peça ao admin permissão de pelo menos *Reader* |
| Serviço renomeado   | Microsoft atualiza nomes       | Verifique o nome atual no All Services         |

---

## 📎 7. Conclusão

Com esses métodos, você conseguirá localizar qualquer serviço ou recurso dentro do Azure Portal, seja por navegação, filtros ou buscas rápidas.

Se quiser, posso adicionar **capturas de tela**, **vídeos**, ou adaptar o README para um padrão corporativo da sua empr
