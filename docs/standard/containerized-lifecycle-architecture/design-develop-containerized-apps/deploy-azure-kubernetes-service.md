---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Zjistěte, jak nasadit aplikaci pomocí služby Azure Kubernetes Service.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 82a1cf7f3cc367bfb8b8f67a130600815f2a21c4
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664962"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="11f05-103">Nasazení do služby Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="11f05-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="11f05-104">Budete moct setkat s AKS pomocí upřednostňované klientské operační systémy, tady vám ukážeme, jak dělat s Microsoft Windows a vložené verzi ve Windows, Ubuntu Linux pomocí příkazů prostředí Bash.</span><span class="sxs-lookup"><span data-stu-id="11f05-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="11f05-105">Jsou požadavky, aby před použitím AKS:</span><span class="sxs-lookup"><span data-stu-id="11f05-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="11f05-106">Linux nebo Mac vývojovém počítači</span><span class="sxs-lookup"><span data-stu-id="11f05-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="11f05-107">Vývojovém počítači s Windows</span><span class="sxs-lookup"><span data-stu-id="11f05-107">Windows development machine</span></span>
  - <span data-ttu-id="11f05-108">Vývojářský režim povolen ve Windows</span><span class="sxs-lookup"><span data-stu-id="11f05-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="11f05-109">Subsystém Windows pro Linux</span><span class="sxs-lookup"><span data-stu-id="11f05-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="11f05-110">Nainstalované v Azure CLI [Windows, Mac nebo Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="11f05-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="11f05-111">Chcete-li si projít kompletní informace o:</span><span class="sxs-lookup"><span data-stu-id="11f05-111">To find complete information about:</span></span>
>
> <span data-ttu-id="11f05-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="11f05-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="11f05-113">Subsystém Windows pro Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="11f05-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="11f05-114">Vytvoření prostředí AKS v Azure</span><span class="sxs-lookup"><span data-stu-id="11f05-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="11f05-115">Existuje několik způsobů, jak vytvořit prostředí AKS.</span><span class="sxs-lookup"><span data-stu-id="11f05-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="11f05-116">To lze provést pomocí příkazů rozhraní příkazového řádku Azure nebo pomocí webu Azure portal.</span><span class="sxs-lookup"><span data-stu-id="11f05-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="11f05-117">Tady si můžete projít některé příklady použití Azure CLI k vytvoření clusteru a na webu Azure portal zkontrolujte výsledky.</span><span class="sxs-lookup"><span data-stu-id="11f05-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="11f05-118">Také musíte mít Kubectl a Dockeru ve vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="11f05-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="11f05-119">Vytvoření clusteru AKS</span><span class="sxs-lookup"><span data-stu-id="11f05-119">Create the AKS cluster</span></span>

<span data-ttu-id="11f05-120">Vytvoření clusteru AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="11f05-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="11f05-121">Po dokončení úlohy vytvoření se zobrazí AKS vytvořili na webu Azure Portal:</span><span class="sxs-lookup"><span data-stu-id="11f05-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="11f05-122">Skupina prostředků:</span><span class="sxs-lookup"><span data-stu-id="11f05-122">The resource group:</span></span>

![Zobrazit v prohlížeči skupiny prostředků pro Azure AKS.](media/aks-resource-group-view.png)

<span data-ttu-id="11f05-124">**Obrázek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="11f05-124">**Figure 4-17**.</span></span> <span data-ttu-id="11f05-125">Zobrazení skupiny prostředků pro AKS z Azure.</span><span class="sxs-lookup"><span data-stu-id="11f05-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="11f05-126">AKS cluster:</span><span class="sxs-lookup"><span data-stu-id="11f05-126">The AKS cluster:</span></span>

![Zobrazení prohlížeče s skupinu prostředků pro AKS.](media/aks-cluster-view.png)

<span data-ttu-id="11f05-128">**Obrázek 4 – 18**.</span><span class="sxs-lookup"><span data-stu-id="11f05-128">**Figure 4-18**.</span></span> <span data-ttu-id="11f05-129">AKS zobrazení z Azure.</span><span class="sxs-lookup"><span data-stu-id="11f05-129">AKS view from Azure.</span></span>

<span data-ttu-id="11f05-130">Můžete také zobrazit uzel vytvořené pomocí `Azure-CLI` a `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="11f05-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="11f05-131">Nejprve získání přihlašovacích údajů:</span><span class="sxs-lookup"><span data-stu-id="11f05-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Výstup z výše uvedeného příkazu konzoly: Sloučené "MsSampleK8Cluster jako aktuální kontext v /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="11f05-133">**Obrázek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="11f05-133">**Figure 4-19**.</span></span> <span data-ttu-id="11f05-134">`aks get-credentials` výsledek příkazu.</span><span class="sxs-lookup"><span data-stu-id="11f05-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="11f05-135">A pak získávání uzly z Kubectl:</span><span class="sxs-lookup"><span data-stu-id="11f05-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Výstup uvedeného příkazu konzoly: Seznam uzlů se stavem, stáří (čas spuštění) a verze](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="11f05-137">**Obrázek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="11f05-137">**Figure 4-20**.</span></span> <span data-ttu-id="11f05-138">`kubectl get nodes` výsledek příkazu.</span><span class="sxs-lookup"><span data-stu-id="11f05-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="11f05-139">[Předchozí](orchestrate-high-scalability-availability.md)
>[další](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="11f05-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
