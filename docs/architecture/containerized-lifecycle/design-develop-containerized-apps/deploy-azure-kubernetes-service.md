---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Přečtěte si, jak nasadit aplikaci pomocí služby Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182368"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="1ea5b-103">Nasazení do služby Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="1ea5b-104">Můžete komunikovat s AKS pomocí preferovaného klientského operačního systému, zde vám ukážeme, jak to udělat s Microsoft Windows a vestavěnou verzí Ubuntu Linux v systému Windows pomocí příkazů Bash.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="1ea5b-105">Předpoklady, které je třeba mít před použitím AKS, jsou:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="1ea5b-106">Vývojový stroj pro Linux nebo Mac</span><span class="sxs-lookup"><span data-stu-id="1ea5b-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="1ea5b-107">Vývojový počítač systému Windows</span><span class="sxs-lookup"><span data-stu-id="1ea5b-107">Windows development machine</span></span>
  - <span data-ttu-id="1ea5b-108">Režim pro vývojáře v systému Windows</span><span class="sxs-lookup"><span data-stu-id="1ea5b-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="1ea5b-109">Windows Subsystem for Linux</span><span class="sxs-lookup"><span data-stu-id="1ea5b-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="1ea5b-110">Azure-CLI nainstalované na [Windows, Mac nebo Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="1ea5b-111">Chcete-li najít úplné informace o:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-111">To find complete information about:</span></span>
>
> <span data-ttu-id="1ea5b-112">Azure-CLI:<https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="1ea5b-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="1ea5b-113">Windows Subsystem pro Linux:<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="1ea5b-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="1ea5b-114">Vytvoření prostředí AKS v Azure</span><span class="sxs-lookup"><span data-stu-id="1ea5b-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="1ea5b-115">Prostředí AKS lze vytvořit několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="1ea5b-116">Dá se to provést pomocí příkazů Azure-CLI nebo pomocí portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="1ea5b-117">Tady si můžete prohlédnout některé příklady pomocí Azure-CLI k vytvoření clusteru a portálu Azure ke kontrole výsledků.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="1ea5b-118">Také musíte mít Kubectl a Docker ve vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="1ea5b-119">Vytvoření clusteru AKS</span><span class="sxs-lookup"><span data-stu-id="1ea5b-119">Create the AKS cluster</span></span>

<span data-ttu-id="1ea5b-120">Vytvořte cluster AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="1ea5b-121">Po dokončení úlohy vytvoření uvidíte AKS vytvořené na webu Azure Portal:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="1ea5b-122">Skupina prostředků:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-122">The resource group:</span></span>

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/aks-resource-group-view.png)

<span data-ttu-id="1ea5b-124">**Obrázek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-124">**Figure 4-17**.</span></span> <span data-ttu-id="1ea5b-125">Zobrazení Skupiny prostředků AKS z Azure.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="1ea5b-126">Cluster AKS:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-126">The AKS cluster:</span></span>

![Zobrazení prohlížeče skupiny prostředků AKS.](media/aks-cluster-view.png)

<span data-ttu-id="1ea5b-128">**Obrázek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-128">**Figure 4-18**.</span></span> <span data-ttu-id="1ea5b-129">Zobrazení AKS z Azure.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-129">AKS view from Azure.</span></span>

<span data-ttu-id="1ea5b-130">Můžete také zobrazit uzel vytvořený `Azure-CLI` `Kubectl`pomocí a .</span><span class="sxs-lookup"><span data-stu-id="1ea5b-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="1ea5b-131">Za prvé, získání pověření:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Výstup konzoly z výše uvedeného příkazu: Sloučený "MsSampleK8Cluster jako aktuální kontext v /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="1ea5b-133">**Obrázek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-133">**Figure 4-19**.</span></span> <span data-ttu-id="1ea5b-134">`aks get-credentials`výsledek příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="1ea5b-135">A pak, jak se uzly z Kubectl:</span><span class="sxs-lookup"><span data-stu-id="1ea5b-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Výstup konzoly z výše uvedeného příkazu: Seznam uzlů se stavem, věkem (běžícím časem) a verzí](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="1ea5b-137">**Obrázek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-137">**Figure 4-20**.</span></span> <span data-ttu-id="1ea5b-138">`kubectl get nodes`výsledek příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ea5b-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ea5b-139">[Předchozí](orchestrate-high-scalability-availability.md)
>[další](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="1ea5b-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
