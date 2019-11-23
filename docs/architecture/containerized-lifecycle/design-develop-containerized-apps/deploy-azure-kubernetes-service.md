---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Naučte se, jak nasadit aplikaci pomocí služby Azure Kubernetes.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182368"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Nasazení do služby Azure Kubernetes Service (AKS)

S AKS můžete komunikovat s použitím preferovaného klientského operačního systému, v tomto článku se dozvíte, jak to udělat s Windows, a s vloženou verzí Ubuntu Linux v systému Windows pomocí příkazů bash.

Předpoklady pro použití AKS jsou:

- Počítač pro vývoj pro Linux nebo Mac
- Počítač pro vývoj ve Windows
  - Režim pro vývojáře povolený ve Windows
  - Subsystém Windows pro Linux
- Azure – rozhraní příkazového řádku nainstalované v [systémech Windows, Mac nebo Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)

> [!NOTE]
> Podrobné informace o:
>
> Azure-CLI: <https://docs.microsoft.com/cli/azure/index>
>
> Subsystém Windows pro Linux: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Vytvoření prostředí AKS v Azure

Existuje několik způsobů, jak vytvořit prostředí AKS. Dá se to udělat pomocí příkazů Azure-CLI nebo pomocí Azure Portal.

Tady můžete prozkoumat některé příklady pomocí Azure-CLI a vytvořit tak cluster a Azure Portal ke kontrole výsledků. Musíte mít také Kubectl a Docker ve vývojovém počítači.  

## <a name="create-the-aks-cluster"></a>Vytvoření clusteru AKS

Vytvořte cluster AKS pomocí tohoto příkazu:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Po dokončení úlohy vytváření se můžete podívat na AKS vytvořený v Azure Portal:

Skupina prostředků:

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/aks-resource-group-view.png)

**Obrázek 4-17**. AKS zobrazení skupiny prostředků z Azure.

Cluster AKS:

![Zobrazení prohlížeče skupiny prostředků AKS.](media/aks-cluster-view.png)

**Obrázek 4-18**. AKS zobrazení z Azure.

Můžete také zobrazit uzel vytvořený pomocí `Azure-CLI` a `Kubectl`.

Nejdřív načítají se přihlašovací údaje:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Výstup z konzoly z výše uvedeného příkazu: sloučený MsSampleK8Cluster jako aktuální kontext v/root/.Kube/config.](media/get-credentials-command-result.png)

**Obrázek 4-19**. výsledek `aks get-credentials` příkazu

A pak načítají uzly z Kubectl:

```console
kubectl get nodes
```

![Výstup na konzole z výše uvedeného příkazu: seznam uzlů se stavem, stáří (čas spuštění) a verze](media/kubectl-get-nodes-command-result.png)

**Obrázek 4-20**. výsledek `kubectl get nodes` příkazu

>[!div class="step-by-step"]
>[Předchozí](orchestrate-high-scalability-availability.md)
>[Další](docker-apps-development-environment.md)
