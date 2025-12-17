# Azure Tags & Policy Automation (PowerShell + AZ CLI)

Script em **PowerShell** para **aplicar tags em Resource Groups** e **criar Policy Assignments com remediação automática** no **Microsoft Azure**, utilizando a **Azure CLI (az)**.

Ideal para padronização de governança, controle de custos e aplicação automática de tags herdadas nos recursos.

---

## 🚀 Funcionalidades

* Seleção interativa de **Assinatura Azure**
* Seleção interativa de **Resource Group**
* Aplicação de múltiplas **tags no Resource Group**:

  * `environment`
  * `cost-center`
  * `application`
  * `cost-owner`
* Criação automática de **Policy Assignments** para herança de tags
* Criação de **Remediações** para corrigir recursos já existentes
* Tratamento elegante de **erros e warnings do AZ CLI**
* Compatível com ambientes corporativos (governança e compliance)

---

## 🧱 Policy Utilizada

O script utiliza a policy built-in do Azure:

* **ID:** `cd3aa116-8754-49c9-a813-ad46512ece54`
* **Nome:** *Inherit a tag from the resource group if missing*

Essa policy garante que **todo recurso criado sem as tags definidas herde automaticamente as tags do Resource Group**. Além disso, a remediação aplica as tags também em recursos já existentes que estejam em não conformidade.

---

## 📋 Pré-requisitos

Antes de executar o script, certifique-se de que você possui:

* **Windows PowerShell 7+** ou **PowerShell Core**
* **Azure CLI** instalada
* Login realizado no Azure:

  ```powershell
  az login
  ```
* Permissões mínimas:

  * **Contributor** no escopo do Resource Group (ou superior)
  * Permissão para criar **Policy Assignments** e **Managed Identities**

---

## ▶️ Como Executar

1. Clone o repositório:

   ```bash
   git clone https://github.com/seu-usuario/seu-repo.git
   ```

2. Acesse a pasta do script:

   ```powershell
   cd seu-repo
   ```

3. Execute o script:

   ```powershell
   .\aplica-tags-policy.ps1
   ```

4. Siga o passo a passo interativo:

   * Escolha a **assinatura**
   * Escolha o **Resource Group**
   * Informe os valores das tags

---

## 🏷️ Tags Aplicadas

As seguintes tags serão aplicadas diretamente no **Resource Group** e herdadas pelos recursos:

| Tag         | Descrição                     |
| ----------- | ----------------------------- |
| environment | Ambiente (ex: dev, hml, prod) |
| cost-center | Centro de custo               |
| application | Nome da aplicação             |
| cost-owner  | Responsável pelo custo        |

---

## 🏗️ O que o Script Cria

Para **cada tag**, o script cria:

* 1 **Policy Assignment** no escopo do Resource Group
* 1 **Managed Identity** associada ao assignment
* 1 **Remediação** para aplicar a tag em recursos existentes

Os nomes são automaticamente ajustados para respeitar o limite de **64 caracteres do Azure**.

---

## ⚠️ Observações Importantes

* O script **não remove** tags existentes nos recursos
* Caso a tag já exista no recurso, **ela não será sobrescrita**
* A remediação pode levar alguns minutos dependendo da quantidade de recursos

---

## 🧪 Testado em

* PowerShell 7.x
* Azure CLI 2.x
* Azure Subscription corporativa

---

## 📄 Licença

Este projeto é de uso livre para fins educacionais e corporativos internos.

Sinta-se à vontade para adaptar, melhorar e reutilizar 🚀

---

## 🤝 Contribuições

Pull requests são bem-vindos!
Para grandes mudanças, abra primeiro uma issue para discussão.

---

## ✨ Autor

Criado para automação de governança e padronização no Azure.
