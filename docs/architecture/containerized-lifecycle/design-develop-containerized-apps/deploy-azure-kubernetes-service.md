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
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Nasazení do služby Azure Kubernetes Service (AKS)

Můžete komunikovat s AKS pomocí preferovaného klientského operačního systému, zde vám ukážeme, jak to udělat s Microsoft Windows a vestavěnou verzí Ubuntu Linux v systému Windows pomocí příkazů Bash.

Předpoklady, které je třeba mít před použitím AKS, jsou:

- Vývojový stroj pro Linux nebo Mac
- Vývojový počítač systému Windows
  - Režim pro vývojáře v systému Windows
  - Windows Subsystem for Linux
- Azure-CLI nainstalované na [Windows, Mac nebo Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)

> [!NOTE]
> Chcete-li najít úplné informace o:
>
> Azure-CLI:<https://docs.microsoft.com/cli/azure/index>
>
> Windows Subsystem pro Linux:<https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Vytvoření prostředí AKS v Azure

Prostředí AKS lze vytvořit několika způsoby. Dá se to provést pomocí příkazů Azure-CLI nebo pomocí portálu Azure.

Tady si můžete prohlédnout některé příklady pomocí Azure-CLI k vytvoření clusteru a portálu Azure ke kontrole výsledků. Také musíte mít Kubectl a Docker ve vývojovém počítači.  

## <a name="create-the-aks-cluster"></a>Vytvoření clusteru AKS

Vytvořte cluster AKS pomocí tohoto příkazu:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Po dokončení úlohy vytvoření uvidíte AKS vytvořené na webu Azure Portal:

Skupina prostředků:

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/aks-resource-group-view.png)

**Obrázek 4-17**. Zobrazení Skupiny prostředků AKS z Azure.

Cluster AKS:

![Zobrazení prohlížeče skupiny prostředků AKS.](media/aks-cluster-view.png)

**Obrázek 4-18**. Zobrazení AKS z Azure.

Můžete také zobrazit uzel vytvořený `Azure-CLI` `Kubectl`pomocí a .

Za prvé, získání pověření:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Výstup konzoly z výše uvedeného příkazu: Sloučený "MsSampleK8Cluster jako aktuální kontext v /root/.kube/config.](media/get-credentials-command-result.png)

**Obrázek 4-19**. `aks get-credentials`výsledek příkazu.

A pak, jak se uzly z Kubectl:

```console
kubectl get nodes
```

![Výstup konzoly z výše uvedeného příkazu: Seznam uzlů se stavem, věkem (běžícím časem) a verzí](media/kubectl-get-nodes-command-result.png)

**Obrázek 4-20**. `kubectl get nodes`výsledek příkazu.

>[!div class="step-by-step"]
>[Předchozí](orchestrate-high-scalability-availability.md)
>[další](docker-apps-development-environment.md)
