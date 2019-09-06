---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Naučte se, jak nasadit aplikaci pomocí služby Azure Kubernetes.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295375"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="bacd4-103">Nasazení do služby Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="bacd4-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="bacd4-104">S AKS můžete komunikovat s použitím preferovaného klientského operačního systému, v tomto článku se dozvíte, jak to udělat s Windows, a s vloženou verzí Ubuntu Linux v systému Windows pomocí příkazů bash.</span><span class="sxs-lookup"><span data-stu-id="bacd4-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="bacd4-105">Předpoklady pro použití AKS jsou:</span><span class="sxs-lookup"><span data-stu-id="bacd4-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="bacd4-106">Počítač pro vývoj pro Linux nebo Mac</span><span class="sxs-lookup"><span data-stu-id="bacd4-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="bacd4-107">Počítač pro vývoj ve Windows</span><span class="sxs-lookup"><span data-stu-id="bacd4-107">Windows development machine</span></span>
  - <span data-ttu-id="bacd4-108">Režim pro vývojáře povolený ve Windows</span><span class="sxs-lookup"><span data-stu-id="bacd4-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="bacd4-109">Subsystém Windows pro Linux</span><span class="sxs-lookup"><span data-stu-id="bacd4-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="bacd4-110">Azure – rozhraní příkazového řádku nainstalované v [systémech Windows, Mac nebo Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="bacd4-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="bacd4-111">Podrobné informace o:</span><span class="sxs-lookup"><span data-stu-id="bacd4-111">To find complete information about:</span></span>
>
> <span data-ttu-id="bacd4-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="bacd4-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="bacd4-113">Subsystém Windows pro Linux:<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="bacd4-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="bacd4-114">Vytvoření prostředí AKS v Azure</span><span class="sxs-lookup"><span data-stu-id="bacd4-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="bacd4-115">Existuje několik způsobů, jak vytvořit prostředí AKS.</span><span class="sxs-lookup"><span data-stu-id="bacd4-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="bacd4-116">Dá se to udělat pomocí příkazů Azure-CLI nebo pomocí Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="bacd4-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="bacd4-117">Tady můžete prozkoumat některé příklady pomocí Azure-CLI a vytvořit tak cluster a Azure Portal ke kontrole výsledků.</span><span class="sxs-lookup"><span data-stu-id="bacd4-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="bacd4-118">Musíte mít také Kubectl a Docker ve vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="bacd4-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="bacd4-119">Vytvoření clusteru AKS</span><span class="sxs-lookup"><span data-stu-id="bacd4-119">Create the AKS cluster</span></span>

<span data-ttu-id="bacd4-120">Vytvořte cluster AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="bacd4-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="bacd4-121">Po dokončení úlohy vytváření se můžete podívat na AKS vytvořený v Azure Portal:</span><span class="sxs-lookup"><span data-stu-id="bacd4-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="bacd4-122">Skupina prostředků:</span><span class="sxs-lookup"><span data-stu-id="bacd4-122">The resource group:</span></span>

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/aks-resource-group-view.png)

<span data-ttu-id="bacd4-124">**Obrázek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="bacd4-124">**Figure 4-17**.</span></span> <span data-ttu-id="bacd4-125">AKS zobrazení skupiny prostředků z Azure.</span><span class="sxs-lookup"><span data-stu-id="bacd4-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="bacd4-126">Cluster AKS:</span><span class="sxs-lookup"><span data-stu-id="bacd4-126">The AKS cluster:</span></span>

![Zobrazení prohlížeče skupiny prostředků AKS.](media/aks-cluster-view.png)

<span data-ttu-id="bacd4-128">**Obrázek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="bacd4-128">**Figure 4-18**.</span></span> <span data-ttu-id="bacd4-129">AKS zobrazení z Azure.</span><span class="sxs-lookup"><span data-stu-id="bacd4-129">AKS view from Azure.</span></span>

<span data-ttu-id="bacd4-130">Můžete také zobrazit uzel vytvořený pomocí `Azure-CLI` a. `Kubectl`</span><span class="sxs-lookup"><span data-stu-id="bacd4-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="bacd4-131">Nejdřív načítají se přihlašovací údaje:</span><span class="sxs-lookup"><span data-stu-id="bacd4-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Výstup z konzoly z výše uvedeného příkazu: Sloučí se MsSampleK8Cluster jako aktuální kontext v/root/.Kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="bacd4-133">**Obrázek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="bacd4-133">**Figure 4-19**.</span></span> <span data-ttu-id="bacd4-134">`aks get-credentials`výsledek příkazu</span><span class="sxs-lookup"><span data-stu-id="bacd4-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="bacd4-135">A pak načítají uzly z Kubectl:</span><span class="sxs-lookup"><span data-stu-id="bacd4-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Výstup z konzoly z výše uvedeného příkazu: Seznam uzlů se stavem, stáří (čas spuštění) a verzí](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="bacd4-137">**Obrázek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="bacd4-137">**Figure 4-20**.</span></span> <span data-ttu-id="bacd4-138">`kubectl get nodes`výsledek příkazu</span><span class="sxs-lookup"><span data-stu-id="bacd4-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bacd4-139">[Předchozí](orchestrate-high-scalability-availability.md)Další
>[](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="bacd4-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
