---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e11c9ec61ea7d5131595f01ce76b5bb810bb70c0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063304"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes

Obrázek 5 – 12 se zobrazí scénáře DevOps začátku do konce pokrývající správy kódu a kompilace kódu, sestavení Image Dockeru, nasdílet Image Dockeru do registru Dockeru a nakonec nasazení clusteru Kubernetes v Azure.

![Pracovní postup: Spustí ve vývojovém počítači. Úloha sestavení/průběžná integrace pomocí vlastní image, která získá nahrány do registru Docker a potom se používají v úloha nasazení/CD, nakonec doručením (push) do AKS doručením (push) do úložiště začne.](media/docker-workflow-ci-cd-aks.png)

**Obrázek 5 – 12**. CI/CD scénář vytvoření imagí Dockeru a nasazení do clusteru Kubernetes v Azure

Je důležité, abyste měli na očích, že dva kanály, sestavení a průběžná integrace a vydání/CD, jsou propojené prostřednictvím registru Dockeru (jako je například Docker Hubu nebo služby Azure Container Registry). Registr Dockeru je jedním z hlavních rozdílů v porovnání s tradičním procesu CI/CD bez Dockeru.

Jak je znázorněno v obrázek 5-13, je první fáze kanálu sestavení/CI. Ve službě Azure DevOps Services můžete vytvářet kanály sestavení a průběžná integrace, které budou kompilaci kódu, vytvořte Image Dockeru a vložit je do registru Dockeru jako Docker Hubu nebo služby Azure Container Registry.

![Zobrazení prohlížeče s Azure DevOps, definice úlohy procesu sestavení.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Obrázek 5-13**. Sestavení a průběžná integrace kanál v Azure DevOps vytváření imagí Dockeru a nahráním Image do registru Dockeru

Druhá fáze se k vytvoření kanálu nasazení a vydání. Ve službě Azure DevOps Services můžete snadno vytvořit kanál nasazení cílí na Kubernetes cluster pomocí úloh Kubernetes pro Azure DevOps služby, jak je znázorněno v obrázek 5-14.

![Zobrazení prohlížeče s Azure DevOps, nasaďte do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Obrázek 5-14**. Kanál verze/CD v Azure DevOps služby nasazením do clusteru Kubernetes

> [! Návod] eShopModernized nasazování do Kubernetes:
>
> Podrobný návod k kanály Azure DevOps CI/CD nasazování do Kubernetes, naleznete v tomto příspěvku: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[další](../run-manage-monitor-docker-environments/index.md)
