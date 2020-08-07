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
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Nasazení do služby Azure Kubernetes Service (AKS)

S nainstalovaným rozhraním příkazového řádku Azure (Azure CLI) můžete komunikovat s AKS pomocí preferovaného klientského operačního systému (Windows, macOS nebo Linux). Další podrobnosti najdete v dokumentaci k rozhraní příkazového [řádku Azure CLI](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) a v [Průvodci instalací](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) pro dostupná prostředí.

## <a name="create-the-aks-environment-in-azure"></a>Vytvoření prostředí AKS v Azure

Existuje několik způsobů, jak vytvořit prostředí AKS. Můžete to provést pomocí příkazů rozhraní příkazového řádku Azure nebo pomocí Azure Portal.

Tady můžete prozkoumat některé příklady pomocí Azure CLI a vytvořit tak cluster a Azure Portal ke kontrole výsledků. Musíte mít také Kubectl a Docker ve vývojovém počítači.

## <a name="create-the-aks-cluster"></a>Vytvoření clusteru AKS

Vytvořte cluster AKS pomocí tohoto příkazu (skupina prostředků musí existovat):

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> `--node-vm-size` `--node-count` Hodnoty parametrů a jsou dostatečně dobré pro ukázkovou/vývojářskou aplikaci.

Po dokončení úlohy vytváření můžete zobrazit:

- Cluster AKS se vytvořil v počáteční skupině prostředků.
- Novou související skupinu prostředků, která obsahuje prostředky související s clusterem AKS, jak je znázorněno na následujících obrázcích.

Počáteční skupina prostředků s clusterem AKS:

![Zobrazení prohlížeče skupiny prostředků AKS.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

**Obrázek 4-17**. AKS zobrazení skupiny prostředků z Azure.

Skupina prostředků clusteru AKS:

![Zobrazení prohlížeče skupiny prostředků Azure AKS.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

**Obrázek 4-18**. AKS zobrazení z Azure.

> [!IMPORTANT]
> Obecně platí, že nebudete muset upravovat prostředky ve skupině prostředků clusteru AKS. Například skupina prostředků se odstraní při odstranění clusteru AKS.

Můžete také zobrazit uzel vytvořený pomocí `Azure CLI` a `Kubectl` .

Nejdřív načítají se přihlašovací údaje:

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Výstup z konzoly z výše uvedeného příkazu: "prozkoumává-Docker-AKS" jako aktuální kontext v/Home/Miguel/.Kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

**Obrázek 4-19**. `aks get-credentials`výsledek příkazu

A pak načítají uzly z Kubectl:

```console
kubectl get nodes
```

![Výstup konzoly z výše uvedeného příkazu: seznam uzlů se stavem, stáří (čas spuštění) a verze](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

**Obrázek 4-20**. `kubectl get nodes`výsledek příkazu

> [!div class="step-by-step"]
> [Předchozí](orchestrate-high-scalability-availability.md) 
>  [Další](docker-apps-development-environment.md)
