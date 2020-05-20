---
title: Infrastruktura jako kód
description: Přechodu infrastruktura jako Code (IaC) s aplikacemi pro Cloud Native
ms.date: 05/13/2020
ms.openlocfilehash: cfc9e1f0b2733048d5921de5a0400998c282b1fa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613951"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="123c7-103">Infrastruktura jako kód</span><span class="sxs-lookup"><span data-stu-id="123c7-103">Infrastructure as code</span></span>

<span data-ttu-id="123c7-104">Nativní systémy cloudu zadosahují mikroslužeb, kontejnerů a moderního návrhu systému, abyste dosáhli rychlosti a flexibility.</span><span class="sxs-lookup"><span data-stu-id="123c7-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="123c7-105">Poskytují automatizované fáze sestavení a vydání, aby bylo zajištěno konzistentní a kvalitní kód.</span><span class="sxs-lookup"><span data-stu-id="123c7-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="123c7-106">Ale to je jenom část tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="123c7-106">But, that's only part of the story.</span></span> <span data-ttu-id="123c7-107">Jak můžete zřídit cloudová prostředí, na kterých se tyto systémy spouštějí?</span><span class="sxs-lookup"><span data-stu-id="123c7-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="123c7-108">Moderní cloudové aplikace přijímají široce přijatý postup [infrastruktury jako kódu](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)nebo `IaC` .</span><span class="sxs-lookup"><span data-stu-id="123c7-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="123c7-109">Pomocí IaC automatizujete zřizování platforem.</span><span class="sxs-lookup"><span data-stu-id="123c7-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="123c7-110">V podstatě budete uplatňovat postupy softwarového inženýrství, jako je testování a správa verzí, a to v praxi DevOps.</span><span class="sxs-lookup"><span data-stu-id="123c7-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="123c7-111">Vaše infrastruktura a nasazení jsou automatizované, konzistentní a opakované.</span><span class="sxs-lookup"><span data-stu-id="123c7-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="123c7-112">Stejně jako průběžné doručování automatizuje tradiční model ručních nasazení, infrastruktura jako kód (IaC) vyvíjí způsob správy prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="123c7-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="123c7-113">Nástroje, jako je Azure Resource Manager (ARM), Terraformu a rozhraní příkazového řádku Azure (CLI), umožňují deklarativní skriptování cloudové infrastruktury, kterou požadujete.</span><span class="sxs-lookup"><span data-stu-id="123c7-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="123c7-114">Šablony Azure Resource Manageru</span><span class="sxs-lookup"><span data-stu-id="123c7-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="123c7-115">ARM představuje [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span><span class="sxs-lookup"><span data-stu-id="123c7-115">ARM stands for [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span></span> <span data-ttu-id="123c7-116">Je to modul zřizování rozhraní API, který je integrovaný do Azure a vystavený jako služba API.</span><span class="sxs-lookup"><span data-stu-id="123c7-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="123c7-117">ARM umožňuje nasazovat, aktualizovat, odstraňovat a spravovat prostředky obsažené ve skupině prostředků Azure v rámci jediné koordinované operace.</span><span class="sxs-lookup"><span data-stu-id="123c7-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="123c7-118">Modul poskytnete šablonou založenou na formátu JSON, která určuje požadované prostředky a jejich konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="123c7-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="123c7-119">ARM automaticky orchestruje nasazení ve správném pořadí, v jakém jsou dodržovány závislosti.</span><span class="sxs-lookup"><span data-stu-id="123c7-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="123c7-120">Modul zajišťuje idempotence.</span><span class="sxs-lookup"><span data-stu-id="123c7-120">The engine ensures idempotency.</span></span> <span data-ttu-id="123c7-121">Pokud již existuje požadovaný prostředek se stejnou konfigurací, zřizování se bude ignorovat.</span><span class="sxs-lookup"><span data-stu-id="123c7-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="123c7-122">Šablony Azure Resource Manager představují jazyk založený na formátu JSON pro definování různých prostředků v Azure.</span><span class="sxs-lookup"><span data-stu-id="123c7-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="123c7-123">Základní schéma vypadá přibližně jako obrázek 10-14.</span><span class="sxs-lookup"><span data-stu-id="123c7-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="123c7-124">**Obrázek 10-14** – schéma pro šablonu správce prostředků</span><span class="sxs-lookup"><span data-stu-id="123c7-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="123c7-125">V rámci této šablony může jedna definovat kontejner úložiště uvnitř oddílu prostředků, například takto:</span><span class="sxs-lookup"><span data-stu-id="123c7-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="123c7-126">**Obrázek 10-15** – příklad účtu úložiště definovaného v šabloně správce prostředků</span><span class="sxs-lookup"><span data-stu-id="123c7-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="123c7-127">Šablona ARM může být Parametrizovaná s dynamickým prostředím a informacemi o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="123c7-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="123c7-128">Díky tomu se dá znovu použít k definování různých prostředí, jako je vývoj, QA nebo produkce.</span><span class="sxs-lookup"><span data-stu-id="123c7-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="123c7-129">Šablona normálně vytvoří všechny prostředky v rámci jedné skupiny prostředků Azure.</span><span class="sxs-lookup"><span data-stu-id="123c7-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="123c7-130">V případě potřeby je možné v jedné šabloně Správce prostředků definovat více skupin prostředků.</span><span class="sxs-lookup"><span data-stu-id="123c7-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="123c7-131">Všechny prostředky v prostředí můžete odstranit odstraněním samotné skupiny prostředků.</span><span class="sxs-lookup"><span data-stu-id="123c7-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="123c7-132">Analýza nákladů se dá spustit taky na úrovni skupiny prostředků, což umožňuje rychlé monitorování, kolik jednotlivých prostředí se účtuje podle nákladů.</span><span class="sxs-lookup"><span data-stu-id="123c7-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="123c7-133">V projektu [šablon rychlého startu Azure](https://github.com/Azure/azure-quickstart-templates) na GitHubu je k dispozici mnoho příkladů nebo šablon ARM.</span><span class="sxs-lookup"><span data-stu-id="123c7-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="123c7-134">Můžou přispět k urychlení vytváření nové šablony nebo změně stávající.</span><span class="sxs-lookup"><span data-stu-id="123c7-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="123c7-135">Šablony Správce prostředků lze spustit mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="123c7-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="123c7-136">Možná je nejjednodušší způsob, jak je jednoduše vložit do Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="123c7-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="123c7-137">Pro experimentální nasazení může být tato metoda rychlá.</span><span class="sxs-lookup"><span data-stu-id="123c7-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="123c7-138">Můžete je také spustit jako součást procesu sestavení nebo vydání v Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="123c7-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="123c7-139">K dispozici jsou úlohy, které budou používat připojení do Azure ke spouštění šablon.</span><span class="sxs-lookup"><span data-stu-id="123c7-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="123c7-140">Změny šablon Správce prostředků se aplikují postupně, což znamená, že pokud chcete přidat nový prostředek, musíte ho jenom přidat do šablony.</span><span class="sxs-lookup"><span data-stu-id="123c7-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="123c7-141">Nástroje budou sjednotit rozdíly mezi aktuálními prostředky a definicemi uvedenými v šabloně.</span><span class="sxs-lookup"><span data-stu-id="123c7-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="123c7-142">Prostředky se pak vytvoří nebo změní, aby odpovídaly tomu, co je definováno v šabloně.</span><span class="sxs-lookup"><span data-stu-id="123c7-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="123c7-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="123c7-143">Terraform</span></span>

<span data-ttu-id="123c7-144">Nativní aplikace v cloudu jsou často vytvořené jako `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="123c7-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="123c7-145">To znamená, že aplikace není pevně spojená s konkrétním dodavatelem cloudu a je možné ji nasadit do libovolného veřejného cloudu.</span><span class="sxs-lookup"><span data-stu-id="123c7-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="123c7-146">[Terraformu](https://www.terraform.io/) je komerční Nástroj pro šablonování, který umožňuje zřídit nativní cloudové aplikace napříč všemi hlavními přehrávači cloudu: Azure, Google Cloud Platform, AWS a AliCloud.</span><span class="sxs-lookup"><span data-stu-id="123c7-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="123c7-147">Místo použití formátu JSON jako jazyka definice šablony používá poněkud více stručný YAML.</span><span class="sxs-lookup"><span data-stu-id="123c7-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="123c7-148">Příklad souboru Terraformu, který se shoduje s předchozí šablonou Správce prostředků (obrázek 10-15), je znázorněn na obrázku 10-16:</span><span class="sxs-lookup"><span data-stu-id="123c7-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="123c7-149">**Obrázek 10-16** – příklad šablony Správce prostředků</span><span class="sxs-lookup"><span data-stu-id="123c7-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="123c7-150">Terraformu také poskytuje intuitivní chybové zprávy pro šablony problémů.</span><span class="sxs-lookup"><span data-stu-id="123c7-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="123c7-151">K dispozici je také praktická úloha ověření, kterou lze použít ve fázi sestavení k předčasnému zachycení chyb šablon.</span><span class="sxs-lookup"><span data-stu-id="123c7-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="123c7-152">Stejně jako u šablon Správce prostředků jsou k dispozici nástroje příkazového řádku pro nasazení šablon Terraformu.</span><span class="sxs-lookup"><span data-stu-id="123c7-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="123c7-153">V Azure Pipelines existují i úkoly vytvořené komunitou, které mohou ověřovat a používat šablony Terraformu.</span><span class="sxs-lookup"><span data-stu-id="123c7-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="123c7-154">V některých případech Terraformu a ARM vytváří výstup smysluplných hodnot, jako je například připojovací řetězec k nově vytvořené databázi.</span><span class="sxs-lookup"><span data-stu-id="123c7-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="123c7-155">Tyto informace mohou být zachyceny v kanálu sestavení a použity v následujících úlohách.</span><span class="sxs-lookup"><span data-stu-id="123c7-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="123c7-156">Skripty a úlohy Azure CLI</span><span class="sxs-lookup"><span data-stu-id="123c7-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="123c7-157">Nakonec můžete využít rozhraní příkazového [řádku Azure](https://docs.microsoft.com/cli/azure/) pro deklarativní skriptování cloudové infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="123c7-157">Finally, you can leverage [Azure CLI](https://docs.microsoft.com/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="123c7-158">Skripty Azure CLI je možné vytvořit, najít a sdílet a zřídit a nakonfigurovat skoro jakýkoli prostředek Azure.</span><span class="sxs-lookup"><span data-stu-id="123c7-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="123c7-159">Rozhraní příkazového řádku je jednoduché pro použití s mírným výukovou křivkou.</span><span class="sxs-lookup"><span data-stu-id="123c7-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="123c7-160">Skripty se spouštějí buď v PowerShellu, nebo v bash.</span><span class="sxs-lookup"><span data-stu-id="123c7-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="123c7-161">Jsou také jednoduché pro ladění, zejména při porovnání se šablonami ARM.</span><span class="sxs-lookup"><span data-stu-id="123c7-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="123c7-162">Skripty Azure CLI fungují dobře, když potřebujete vytrhnout a znovu nasadit infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="123c7-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="123c7-163">Aktualizace stávajícího prostředí může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="123c7-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="123c7-164">Mnoho příkazů rozhraní příkazového řádku není idempotentní.</span><span class="sxs-lookup"><span data-stu-id="123c7-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="123c7-165">To znamená, že při každém spuštění znovu vytvoří prostředek, a to i v případě, že prostředek už existuje.</span><span class="sxs-lookup"><span data-stu-id="123c7-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="123c7-166">Je vždy možné přidat kód, který kontroluje existenci každého prostředku před jeho vytvořením.</span><span class="sxs-lookup"><span data-stu-id="123c7-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="123c7-167">Ale v takovém případě se váš skript může stát bloated a obtížně spravovat.</span><span class="sxs-lookup"><span data-stu-id="123c7-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="123c7-168">Tyto skripty můžou být v kanálech Azure DevOps také vložené jako `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="123c7-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="123c7-169">Spuštění kanálu vyvolá skript.</span><span class="sxs-lookup"><span data-stu-id="123c7-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="123c7-170">Obrázek 10-17 ukazuje fragment kódu YAML, který obsahuje verzi rozhraní příkazového řádku Azure CLI a podrobnosti o předplatném.</span><span class="sxs-lookup"><span data-stu-id="123c7-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="123c7-171">Všimněte si, jak jsou příkazy rozhraní příkazového řádku Azure zahrnuty ve vloženém skriptu.</span><span class="sxs-lookup"><span data-stu-id="123c7-171">Note how Azure CLI commands are included in an inline script.</span></span>

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

<span data-ttu-id="123c7-172">**Obrázek 10-17** – skript Azure CLI</span><span class="sxs-lookup"><span data-stu-id="123c7-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="123c7-173">V článku [co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), vytváření Sam Guckenheimer popisuje, jak "týmy, které implementují IAC, můžou doručovat stabilní prostředí rychle a ve velkém měřítku.</span><span class="sxs-lookup"><span data-stu-id="123c7-173">In the article, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="123c7-174">Týmy zabraňují ruční konfiguraci prostředí a vynutily konzistenci tím, že představují požadovaný stav prostředí prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="123c7-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="123c7-175">Nasazení infrastruktury s IaC se opakují a zabraňují problémům za běhu způsobeným posunem konfigurace nebo chybějícími závislostmi.</span><span class="sxs-lookup"><span data-stu-id="123c7-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="123c7-176">Týmy DevOps můžou spolupracovat s jednotným sadou postupů a nástrojů a rychle a spolehlivě doručovat aplikace a jejich podpůrnou infrastrukturu. "</span><span class="sxs-lookup"><span data-stu-id="123c7-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="123c7-177">[Předchozí](feature-flags.md) 
> [Další](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="123c7-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
