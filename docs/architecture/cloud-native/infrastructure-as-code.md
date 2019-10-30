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
# <a name="infrastructure-as-code"></a><span data-ttu-id="ff949-103">Infrastruktura jako kód</span><span class="sxs-lookup"><span data-stu-id="ff949-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ff949-104">Nativní aplikace v cloudu umožňují využívat nejrůznější součásti fantastická Platform as a Service (PaaS).</span><span class="sxs-lookup"><span data-stu-id="ff949-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="ff949-105">Na cloudové platformě, jako je Azure, můžou tyto komponenty zahrnovat například úložiště, Service Bus a službu Signal.</span><span class="sxs-lookup"><span data-stu-id="ff949-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="ff949-106">V případě, že aplikace jsou složitější, je možné, že počet používaných služeb se bude zvětšovat.</span><span class="sxs-lookup"><span data-stu-id="ff949-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="ff949-107">Stejně jako jak průběžné doručování podařilo přerušit tradiční model nasazení do prostředí ručně, rychlé tempo změny také podařilo přerušit model, který má centralizovanou skupinu IT spravovat prostředí.</span><span class="sxs-lookup"><span data-stu-id="ff949-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="ff949-108">Sestavování prostředí může a také být automatizované.</span><span class="sxs-lookup"><span data-stu-id="ff949-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="ff949-109">Existuje celá řada dobře vymyšlených nástrojů, které mohou zjednodušit proces.</span><span class="sxs-lookup"><span data-stu-id="ff949-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="ff949-110">Šablony Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="ff949-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="ff949-111">Šablony Azure Resource Manager představují jazyk založený na formátu JSON pro definování různých prostředků v Azure.</span><span class="sxs-lookup"><span data-stu-id="ff949-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="ff949-112">Základní schéma vypadá přibližně jako obrázek 11-10.</span><span class="sxs-lookup"><span data-stu-id="ff949-112">The basic schema looks something like Figure 11-10.</span></span>

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

<span data-ttu-id="ff949-113">**Obrázek 11-10** – schéma pro šablonu správce prostředků</span><span class="sxs-lookup"><span data-stu-id="ff949-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="ff949-114">V rámci této šablony může jedna definovat kontejner úložiště uvnitř oddílu prostředků, například takto:</span><span class="sxs-lookup"><span data-stu-id="ff949-114">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="ff949-115">**Obrázek 11-11** – příklad účtu úložiště definovaného v šabloně správce prostředků</span><span class="sxs-lookup"><span data-stu-id="ff949-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="ff949-116">Šablony lze parametrizovaně, takže jednu šablonu lze znovu použít s různými nastaveními k definování vývojového, QA a produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="ff949-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="ff949-117">To pomáhá eliminovat překvapením při migraci do vyššího prostředí, které je nastavené jinak než v dolních prostředích.</span><span class="sxs-lookup"><span data-stu-id="ff949-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="ff949-118">Prostředky definované v šabloně se většinou vytvářejí v rámci jedné skupiny prostředků v Azure (je možné definovat několik skupin prostředků v jedné Správce prostředků šabloně, ale neobvyklá).</span><span class="sxs-lookup"><span data-stu-id="ff949-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="ff949-119">To umožňuje velmi jednoduché odstranění prostředí pouhým odstraněním skupiny prostředků jako celku.</span><span class="sxs-lookup"><span data-stu-id="ff949-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="ff949-120">Analýza nákladů se dá spustit taky na úrovni skupiny prostředků, což umožňuje rychlé monitorování, kolik jednotlivých prostředí se účtuje podle nákladů.</span><span class="sxs-lookup"><span data-stu-id="ff949-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="ff949-121">V projektu [šablon rychlého startu Azure](https://github.com/Azure/azure-quickstart-templates) na GitHubu je definovaný spousta vzorových šablon, které při spuštění nové šablony nebo přidání do existující šablony povedou k prvnímu.</span><span class="sxs-lookup"><span data-stu-id="ff949-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="ff949-122">Šablony Správce prostředků lze spouštět různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ff949-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="ff949-123">Možná je nejjednodušší způsob, jak je jednoduše vložit do Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="ff949-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="ff949-124">Pro experimentální nasazení může být tato metoda velmi rychlá.</span><span class="sxs-lookup"><span data-stu-id="ff949-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="ff949-125">Můžete je také spustit jako součást procesu sestavení nebo vydání v Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="ff949-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="ff949-126">K dispozici jsou úlohy, které budou používat připojení do Azure ke spouštění šablon.</span><span class="sxs-lookup"><span data-stu-id="ff949-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="ff949-127">Změny šablon Správce prostředků se aplikují postupně, což znamená, že pokud chcete přidat nový prostředek, musíte ho jenom přidat do šablony.</span><span class="sxs-lookup"><span data-stu-id="ff949-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="ff949-128">Nástroj bude zpracovávat rozdíl mezi aktuální skupinou prostředků a požadovanou skupinou prostředků definovanou v šabloně.</span><span class="sxs-lookup"><span data-stu-id="ff949-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="ff949-129">Prostředky se pak vytvoří nebo změní, aby odpovídaly tomu, co je definováno v šabloně.</span><span class="sxs-lookup"><span data-stu-id="ff949-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="ff949-130">Terraformu</span><span class="sxs-lookup"><span data-stu-id="ff949-130">Terraform</span></span>

<span data-ttu-id="ff949-131">Napozorovaná nevýhody Správce prostředků šablon je, že jsou specifická pro cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="ff949-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="ff949-132">Nezvykle vytvářet aplikace, které zahrnují prostředky z více než jednoho cloudu, ale v případě, že podnik spoléhá na Spectacular dobu provozu, může to mít za následek i náklady na podporu více cloudů.</span><span class="sxs-lookup"><span data-stu-id="ff949-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="ff949-133">Pokud by existoval jeden šablonování jazyk, který by se mohl použít v každém cloudu, měl by taky zajistit, aby byly dovednosti pro vývojáře mnohem lépe přenosné.</span><span class="sxs-lookup"><span data-stu-id="ff949-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="ff949-134">Existuje několik technologií, které to dělají jenom teď!</span><span class="sxs-lookup"><span data-stu-id="ff949-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="ff949-135">Nejaktivnější nabídka v tomto prostoru se označuje jako [terraformu](https://www.terraform.io/).</span><span class="sxs-lookup"><span data-stu-id="ff949-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="ff949-136">Terraformu podporuje všechny hlavní cloudové přehrávače, jako je Azure, Google Cloud Platform, AWS a AliCloud, a podporuje také desítky vedlejších hráčů, jako je Heroku a DigitalOcean.</span><span class="sxs-lookup"><span data-stu-id="ff949-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="ff949-137">Místo použití formátu JSON jako jazyka definice šablony používá poněkud více stručný YAML.</span><span class="sxs-lookup"><span data-stu-id="ff949-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="ff949-138">Příklad souboru Terraformu, který se shoduje s předchozí šablonou Správce prostředků (obrázek 11-11), je znázorněn na obrázku 11-12:</span><span class="sxs-lookup"><span data-stu-id="ff949-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

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

<span data-ttu-id="ff949-139">**Obrázek 11-12** – příklad šablony Správce prostředků</span><span class="sxs-lookup"><span data-stu-id="ff949-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="ff949-140">Terraformu zajišťuje lepší úlohu poskytování chybových zpráv rozumné, když prostředek nejde nasadit kvůli chybě v šabloně.</span><span class="sxs-lookup"><span data-stu-id="ff949-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="ff949-141">Toto je oblast, kde Správce prostředků šablony obsahují nějaké probíhající problémy.</span><span class="sxs-lookup"><span data-stu-id="ff949-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="ff949-142">K dispozici je také velmi praktický úkol ověřování, který lze použít ve fázi sestavení k předčasnému zachycení chyb šablon.</span><span class="sxs-lookup"><span data-stu-id="ff949-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="ff949-143">Stejně jako u šablon Správce prostředků jsou k dispozici nástroje příkazového řádku, které lze použít k nasazení šablon Terraformu.</span><span class="sxs-lookup"><span data-stu-id="ff949-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="ff949-144">V Azure Pipelines existují i úkoly vytvořené komunitou, které mohou ověřovat a používat šablony Terraformu.</span><span class="sxs-lookup"><span data-stu-id="ff949-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="ff949-145">V případě, že šablona Terraformu nebo Správce prostředků vypisuje zajímavé hodnoty, jako je například připojovací řetězec do nově vytvořené databáze, mohou být zachyceny v kanálu sestavení a použity v následujících úlohách.</span><span class="sxs-lookup"><span data-stu-id="ff949-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ff949-146">[Předchozí](devops.md)
>[Další](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="ff949-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
