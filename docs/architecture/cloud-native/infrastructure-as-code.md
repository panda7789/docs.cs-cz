---
title: Infrastruktura jako kód
description: Přechodu infrastruktura jako Code (IaC) s aplikacemi pro Cloud Native
ms.date: 05/12/2020
ms.openlocfilehash: 309dd8610ab3b72a6c6da5297f109f822520c5ff
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395351"
---
# <a name="infrastructure-as-code"></a>Infrastruktura jako kód

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Nativní systémy cloudu zadosahují mikroslužeb, kontejnerů a moderního návrhu systému, abyste dosáhli rychlosti a flexibility. Poskytují automatizované fáze sestavení a vydání, aby bylo zajištěno konzistentní a kvalitní kód. Ale to je jenom část tohoto scénáře. Jak můžete zřídit cloudová prostředí, na kterých se tyto systémy spouštějí?

Moderní cloudové aplikace přijímají široce přijatý postup [infrastruktury jako kódu](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)nebo `IaC` .  Pomocí IaC automatizujete zřizování platforem. V podstatě budete uplatňovat postupy softwarového inženýrství, jako je testování a správa verzí, a to v praxi DevOps. Vaše infrastruktura a nasazení jsou automatizované, konzistentní a opakované. Stejně jako průběžné doručování automatizuje tradiční model ručních nasazení, infrastruktura jako kód (IaC) vyvíjí způsob správy prostředí aplikace.

Nástroje, jako je Azure Resource Manager (ARM), Terraformu a rozhraní příkazového řádku Azure (CLI), umožňují deklarativní skriptování cloudové infrastruktury, kterou požadujete.

## <a name="azure-resource-manager-templates"></a>Šablony Azure Resource Manageru

ARM představuje [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/). Je to modul zřizování rozhraní API, který je integrovaný do Azure a vystavený jako služba API. ARM umožňuje nasazovat, aktualizovat, odstraňovat a spravovat prostředky obsažené ve skupině prostředků Azure v rámci jediné koordinované operace. Modul poskytnete šablonou založenou na formátu JSON, která určuje požadované prostředky a jejich konfiguraci. ARM automaticky orchestruje nasazení ve správném pořadí, v jakém jsou dodržovány závislosti. Modul zajišťuje idempotence. Pokud již existuje požadovaný prostředek se stejnou konfigurací, zřizování se bude ignorovat.

Šablony Azure Resource Manager představují jazyk založený na formátu JSON pro definování různých prostředků v Azure. Základní schéma vypadá přibližně jako obrázek 10-14.

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

**Obrázek 10-14** – schéma pro šablonu správce prostředků

V rámci této šablony může jedna definovat kontejner úložiště uvnitř oddílu prostředků, například takto:

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

**Obrázek 10-15** – příklad účtu úložiště definovaného v šabloně správce prostředků

Šablona ARM může být Parametrizovaná s dynamickým prostředím a informacemi o konfiguraci. Díky tomu se dá znovu použít k definování různých prostředí, jako je vývoj, QA nebo produkce. Šablona normálně vytvoří všechny prostředky v rámci jedné skupiny prostředků Azure. V případě potřeby je možné v jedné šabloně Správce prostředků definovat více skupin prostředků. Všechny prostředky v prostředí můžete odstranit odstraněním samotné skupiny prostředků. Analýza nákladů se dá spustit taky na úrovni skupiny prostředků, což umožňuje rychlé monitorování, kolik jednotlivých prostředí se účtuje podle nákladů.

V projektu [šablon rychlého startu Azure](https://github.com/Azure/azure-quickstart-templates) na GitHubu je k dispozici mnoho příkladů nebo šablon ARM. Můžou přispět k urychlení vytváření nové šablony nebo změně stávající.

Šablony Správce prostředků lze spustit mnoha způsoby. Možná je nejjednodušší způsob, jak je jednoduše vložit do Azure Portal. Pro experimentální nasazení může být tato metoda rychlá. Můžete je také spustit jako součást procesu sestavení nebo vydání v Azure DevOps. K dispozici jsou úlohy, které budou používat připojení do Azure ke spouštění šablon. Změny šablon Správce prostředků se aplikují postupně, což znamená, že pokud chcete přidat nový prostředek, musíte ho jenom přidat do šablony. Nástroje budou sjednotit rozdíly mezi aktuálními prostředky a definicemi uvedenými v šabloně. Prostředky se pak vytvoří nebo změní, aby odpovídaly tomu, co je definováno v šabloně.  

## <a name="terraform"></a>Terraform

Nativní aplikace v cloudu jsou často vytvořené jako `cloud agnostic` . To znamená, že aplikace není pevně spojená s konkrétním dodavatelem cloudu a je možné ji nasadit do libovolného veřejného cloudu.

[Terraformu](https://www.terraform.io/) je komerční Nástroj pro šablonování, který umožňuje zřídit nativní cloudové aplikace napříč všemi hlavními přehrávači cloudu: Azure, Google Cloud Platform, AWS a AliCloud. Místo použití formátu JSON jako jazyka definice šablony používá poněkud více stručný YAML.

Příklad souboru Terraformu, který se shoduje s předchozí šablonou Správce prostředků (obrázek 10-15), je znázorněn na obrázku 10-16:

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

**Obrázek 10-16** – příklad šablony Správce prostředků

Terraformu také poskytuje intuitivní chybové zprávy pro šablony problémů. K dispozici je také praktická úloha ověření, kterou lze použít ve fázi sestavení k předčasnému zachycení chyb šablon.

Stejně jako u šablon Správce prostředků jsou k dispozici nástroje příkazového řádku pro nasazení šablon Terraformu. V Azure Pipelines existují i úkoly vytvořené komunitou, které mohou ověřovat a používat šablony Terraformu.

V některých případech Terraformu a ARM vytváří výstup smysluplných hodnot, jako je například připojovací řetězec k nově vytvořené databázi. Tyto informace mohou být zachyceny v kanálu sestavení a použity v následujících úlohách.

## <a name="azure-cli-scripts-and-tasks"></a>Skripty a úlohy Azure CLI

Nakonec můžete využít rozhraní příkazového [řádku Azure](https://docs.microsoft.com/cli/azure/) pro deklarativní skriptování cloudové infrastruktury. Skripty Azure CLI je možné vytvořit, najít a sdílet a zřídit a nakonfigurovat skoro jakýkoli prostředek Azure. Rozhraní příkazového řádku je jednoduché pro použití s mírným výukovou křivkou. Skripty se spouštějí buď v PowerShellu, nebo v bash. Jsou také jednoduché pro ladění, zejména při porovnání se šablonami ARM.

Skripty Azure CLI fungují dobře, když potřebujete vytrhnout a znovu nasadit infrastrukturu. Aktualizace stávajícího prostředí může být obtížné. Mnoho příkazů rozhraní příkazového řádku není idempotentní. To znamená, že při každém spuštění znovu vytvoří prostředek, a to i v případě, že prostředek už existuje. Je vždy možné přidat kód, který kontroluje existenci každého prostředku před jeho vytvořením. Ale v takovém případě se váš skript může stát bloated a obtížně spravovat.

Tyto skripty můžou být v kanálech Azure DevOps také vložené jako `Azure CLI tasks` . Spuštění kanálu vyvolá skript.

Obrázek 10-17 ukazuje fragment kódu YAML, který obsahuje verzi rozhraní příkazového řádku Azure CLI a podrobnosti o předplatném. Všimněte si, jak jsou příkazy rozhraní příkazového řádku Azure zahrnuty ve vloženém skriptu.

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

**Obrázek 10-17** – skript Azure CLI

V článku [co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), vytváření Sam Guckenheimer popisuje, jak "týmy, které implementují IAC, můžou doručovat stabilní prostředí rychle a ve velkém měřítku. Týmy zabraňují ruční konfiguraci prostředí a vynutily konzistenci tím, že představují požadovaný stav prostředí prostřednictvím kódu. Nasazení infrastruktury s IaC se opakují a zabraňují problémům za běhu způsobeným posunem konfigurace nebo chybějícími závislostmi. Týmy DevOps můžou spolupracovat s jednotným sadou postupů a nástrojů a rychle a spolehlivě doručovat aplikace a jejich podpůrnou infrastrukturu. "

>[!div class="step-by-step"]
>[Předchozí](feature-flags.md) 
> [Další](application-bundles.md)
