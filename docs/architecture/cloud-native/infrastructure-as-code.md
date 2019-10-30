---
title: Infrastruktura jako kód
description: Architekt cloudových nativních aplikací .NET pro Azure | Infrastruktura jako kód
ms.date: 06/30/2019
ms.openlocfilehash: 3957da68ac28774f899f49fb181a29c2435902f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087247"
---
# <a name="infrastructure-as-code"></a>Infrastruktura jako kód

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Nativní aplikace v cloudu umožňují využívat nejrůznější součásti fantastická Platform as a Service (PaaS). Na cloudové platformě, jako je Azure, můžou tyto komponenty zahrnovat například úložiště, Service Bus a službu Signal. V případě, že aplikace jsou složitější, je možné, že počet používaných služeb se bude zvětšovat. Stejně jako jak průběžné doručování podařilo přerušit tradiční model nasazení do prostředí ručně, rychlé tempo změny také podařilo přerušit model, který má centralizovanou skupinu IT spravovat prostředí.

Sestavování prostředí může a také být automatizované. Existuje celá řada dobře vymyšlených nástrojů, které mohou zjednodušit proces.

## <a name="azure-resource-manager-templates"></a>Šablony Azure Resource Manager

Šablony Azure Resource Manager představují jazyk založený na formátu JSON pro definování různých prostředků v Azure. Základní schéma vypadá přibližně jako obrázek 11-10.

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

**Obrázek 11-10** – schéma pro šablonu správce prostředků

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

**Obrázek 11-11** – příklad účtu úložiště definovaného v šabloně správce prostředků

Šablony lze parametrizovaně, takže jednu šablonu lze znovu použít s různými nastaveními k definování vývojového, QA a produkčního prostředí. To pomáhá eliminovat překvapením při migraci do vyššího prostředí, které je nastavené jinak než v dolních prostředích. Prostředky definované v šabloně se většinou vytvářejí v rámci jedné skupiny prostředků v Azure (je možné definovat několik skupin prostředků v jedné Správce prostředků šabloně, ale neobvyklá). To umožňuje velmi jednoduché odstranění prostředí pouhým odstraněním skupiny prostředků jako celku. Analýza nákladů se dá spustit taky na úrovni skupiny prostředků, což umožňuje rychlé monitorování, kolik jednotlivých prostředí se účtuje podle nákladů.

V projektu [šablon rychlého startu Azure](https://github.com/Azure/azure-quickstart-templates) na GitHubu je definovaný spousta vzorových šablon, které při spuštění nové šablony nebo přidání do existující šablony povedou k prvnímu.

Šablony Správce prostředků lze spouštět různými způsoby. Možná je nejjednodušší způsob, jak je jednoduše vložit do Azure Portal. Pro experimentální nasazení může být tato metoda velmi rychlá. Můžete je také spustit jako součást procesu sestavení nebo vydání v Azure DevOps. K dispozici jsou úlohy, které budou používat připojení do Azure ke spouštění šablon. Změny šablon Správce prostředků se aplikují postupně, což znamená, že pokud chcete přidat nový prostředek, musíte ho jenom přidat do šablony. Nástroj bude zpracovávat rozdíl mezi aktuální skupinou prostředků a požadovanou skupinou prostředků definovanou v šabloně. Prostředky se pak vytvoří nebo změní, aby odpovídaly tomu, co je definováno v šabloně.  

## <a name="terraform"></a>Terraformu

Napozorovaná nevýhody Správce prostředků šablon je, že jsou specifická pro cloud Azure. Nezvykle vytvářet aplikace, které zahrnují prostředky z více než jednoho cloudu, ale v případě, že podnik spoléhá na Spectacular dobu provozu, může to mít za následek i náklady na podporu více cloudů. Pokud by existoval jeden šablonování jazyk, který by se mohl použít v každém cloudu, měl by taky zajistit, aby byly dovednosti pro vývojáře mnohem lépe přenosné.

Existuje několik technologií, které to dělají jenom teď! Nejaktivnější nabídka v tomto prostoru se označuje jako [terraformu](https://www.terraform.io/). Terraformu podporuje všechny hlavní cloudové přehrávače, jako je Azure, Google Cloud Platform, AWS a AliCloud, a podporuje také desítky vedlejších hráčů, jako je Heroku a DigitalOcean. Místo použití formátu JSON jako jazyka definice šablony používá poněkud více stručný YAML.

Příklad souboru Terraformu, který se shoduje s předchozí šablonou Správce prostředků (obrázek 11-11), je znázorněn na obrázku 11-12:

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

**Obrázek 11-12** – příklad šablony Správce prostředků

Terraformu zajišťuje lepší úlohu poskytování chybových zpráv rozumné, když prostředek nejde nasadit kvůli chybě v šabloně. Toto je oblast, kde Správce prostředků šablony obsahují nějaké probíhající problémy. K dispozici je také velmi praktický úkol ověřování, který lze použít ve fázi sestavení k předčasnému zachycení chyb šablon.

Stejně jako u šablon Správce prostředků jsou k dispozici nástroje příkazového řádku, které lze použít k nasazení šablon Terraformu. V Azure Pipelines existují i úkoly vytvořené komunitou, které mohou ověřovat a používat šablony Terraformu.

V případě, že šablona Terraformu nebo Správce prostředků vypisuje zajímavé hodnoty, jako je například připojovací řetězec do nově vytvořené databáze, mohou být zachyceny v kanálu sestavení a použity v následujících úlohách.

>[!div class="step-by-step"]
>[Předchozí](devops.md)
>[Další](application-bundles.md)
