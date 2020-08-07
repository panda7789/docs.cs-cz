---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Naučte se, jak nasadit aplikaci pomocí služby Azure Kubernetes.
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916091"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="a4547-103">Nasazení do služby Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="a4547-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="a4547-104">S nainstalovaným rozhraním příkazového řádku Azure (Azure CLI) můžete komunikovat s AKS pomocí preferovaného klientského operačního systému (Windows, macOS nebo Linux).</span><span class="sxs-lookup"><span data-stu-id="a4547-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="a4547-105">Další podrobnosti najdete v dokumentaci k rozhraní příkazového [řádku Azure CLI](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) a v [Průvodci instalací](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) pro dostupná prostředí.</span><span class="sxs-lookup"><span data-stu-id="a4547-105">For more details, refer [Azure CLI documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) and [Installation guide](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="a4547-106">Vytvoření prostředí AKS v Azure</span><span class="sxs-lookup"><span data-stu-id="a4547-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="a4547-107">Existuje několik způsobů, jak vytvořit prostředí AKS.</span><span class="sxs-lookup"><span data-stu-id="a4547-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="a4547-108">Můžete to provést pomocí příkazů rozhraní příkazového řádku Azure nebo pomocí Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="a4547-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="a4547-109">Tady můžete prozkoumat některé příklady pomocí Azure CLI a vytvořit tak cluster a Azure Portal ke kontrole výsledků.</span><span class="sxs-lookup"><span data-stu-id="a4547-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="a4547-110">Musíte mít také Kubectl a Docker ve vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="a4547-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="a4547-111">Vytvoření clusteru AKS</span><span class="sxs-lookup"><span data-stu-id="a4547-111">Create the AKS cluster</span></span>

<span data-ttu-id="a4547-112">Vytvořte cluster AKS pomocí tohoto příkazu (skupina prostředků musí existovat):</span><span class="sxs-lookup"><span data-stu-id="a4547-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="a4547-113">`--node-vm-size` `--node-count` Hodnoty parametrů a jsou dostatečně dobré pro ukázkovou/vývojářskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a4547-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="a4547-114">Po dokončení úlohy vytváření můžete zobrazit:</span><span class="sxs-lookup"><span data-stu-id="a4547-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="a4547-115">Cluster AKS se vytvořil v počáteční skupině prostředků.</span><span class="sxs-lookup"><span data-stu-id="a4547-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="a4547-116">Novou související skupinu prostředků, která obsahuje prostředky související s clusterem AKS, jak je znázorněno na následujících obrázcích.</span><span class="sxs-lookup"><span data-stu-id="a4547-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="a4547-117">Počáteční skupina prostředků s clusterem AKS:</span><span class="sxs-lookup"><span data-stu-id="a4547-117">The initial resource group, with the AKS cluster:</span></span>

![Zobrazení prohlížeče skupiny prostředků AKS.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="a4547-119">**Obrázek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="a4547-119">**Figure 4-17**.</span></span> <span data-ttu-id="a4547-120">AKS zobrazení skupiny prostředků z Azure.</span><span class="sxs-lookup"><span data-stu-id="a4547-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="a4547-121">Skupina prostředků clusteru AKS:</span><span class="sxs-lookup"><span data-stu-id="a4547-121">The AKS cluster resource group:</span></span>

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="a4547-123">**Obrázek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="a4547-123">**Figure 4-18**.</span></span> <span data-ttu-id="a4547-124">AKS zobrazení z Azure.</span><span class="sxs-lookup"><span data-stu-id="a4547-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4547-125">Obecně platí, že nebudete muset upravovat prostředky ve skupině prostředků clusteru AKS.</span><span class="sxs-lookup"><span data-stu-id="a4547-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="a4547-126">Například skupina prostředků se odstraní při odstranění clusteru AKS.</span><span class="sxs-lookup"><span data-stu-id="a4547-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="a4547-127">Můžete také zobrazit uzel vytvořený pomocí `Azure CLI` a `Kubectl` .</span><span class="sxs-lookup"><span data-stu-id="a4547-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="a4547-128">Nejdřív načítají se přihlašovací údaje:</span><span class="sxs-lookup"><span data-stu-id="a4547-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Výstup z konzoly z výše uvedeného příkazu: "prozkoumává-Docker-AKS" jako aktuální kontext v/Home/Miguel/.Kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="a4547-130">**Obrázek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="a4547-130">**Figure 4-19**.</span></span> <span data-ttu-id="a4547-131">`aks get-credentials`výsledek příkazu</span><span class="sxs-lookup"><span data-stu-id="a4547-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="a4547-132">A pak načítají uzly z Kubectl:</span><span class="sxs-lookup"><span data-stu-id="a4547-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Výstup konzoly z výše uvedeného příkazu: seznam uzlů se stavem, stáří (čas spuštění) a verze](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="a4547-134">**Obrázek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="a4547-134">**Figure 4-20**.</span></span> <span data-ttu-id="a4547-135">`kubectl get nodes`výsledek příkazu</span><span class="sxs-lookup"><span data-stu-id="a4547-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="a4547-136">[Předchozí](orchestrate-high-scalability-availability.md) 
>  [Další](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="a4547-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
