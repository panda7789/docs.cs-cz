---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295778"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes

Na obrázku 5-12 uvidíte scénář end-to-end DevOps zahrnující správu kódu, kompilaci kódu, sestavení icloudů Dockeru, iimage Dockeru push do registru Dockeru a nakonec nasazení do clusteru Kubernetes v Azure.

![Pracovní postup: Spustí se ve vývojovém stroji. Odeslání do repo zahájí úlohu sestavení nebo CI pomocí vlastní bitové kopie, která se posune do registru Dockeru a pak je použita úlohou CD/deploy k nakonec odeslání do AKS.](media/docker-workflow-ci-cd-aks.png)

**Obrázek 5-12**. Scénář CI/CD vytváření ibi Dockeru a nasazování do clusteru Kubernetes v Azure

Je důležité zdůraznit, že dva kanály, sestavení/CI a uvolnění nebo CD, jsou propojeny prostřednictvím registru Docker (například Docker Hub nebo Azure Container Registry). Registr Dockeru je jedním z hlavních rozdílů ve srovnání s tradičním procesem CI/CD bez Dockeru.

Jak je znázorněno na obrázku 5-13, první fáze je potrubí sestavení/CI. Ve službách Azure DevOps můžete vytvořit kanály sestavení nebo CI, které zkompilují kód, vytvoří ibi Dockeru a zatlačí je do registru Dockeru, jako je Docker Hub nebo Azure Container Registry.

![Zobrazení prohlížeče Azure DevOps, Vytvoření definice úlohy procesu.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Obrázek 5-13**. Kanál sestavení a ci v Azure DevOps buduje ibi Dockeru a vysune image Dockeru do registru Dockeru

Druhou fází je vytvoření kanálu nasazení a vydání. Ve službách Azure DevOps můžete snadno vytvořit kanál nasazení zaměřený na cluster Kubernetes pomocí úloh Kubernetes pro služby Azure DevOps, jak je znázorněno na obrázku 5-14.

![Zobrazení prohlížeče Azure DevOps, nasazení do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Obrázek 5-14**. Kanál vydání nebo disku CD ve službě Azure DevOps, který se nasazuje do clusteru Kubernetes

> [! Návod] Nasazení eShopuModernizované na Kubernetes:
>
> Podrobný návod k kanálům Azure DevOps CI/CD, které se nasazují do Kubernetes, najdete v tomto příspěvku: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[další](../run-manage-monitor-docker-environments/index.md)
