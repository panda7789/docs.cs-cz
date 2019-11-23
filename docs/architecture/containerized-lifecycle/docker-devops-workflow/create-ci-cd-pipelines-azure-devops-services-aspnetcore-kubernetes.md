---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295778"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes

Na obrázku 5-12 se můžete podívat na celý scénář DevOps, který pokrývá správu kódu, kompilaci kódu, buildy Docker images, Docker images push do registru Docker a nakonec nasazení do clusteru Kubernetes v Azure.

![Pracovní postup: spustí se ve vývojovém počítači. Nahrávání do úložiště spustí úlohu sestavení/CI s použitím vlastní image, která se načte do registru Docker, a pak ji pomocí úlohy CD/nasazení vyřadí do AKS.](media/docker-workflow-ci-cd-aks.png)

**Obrázek 5-12**. Scénář CI/CD vytváření imagí Docker a nasazení do clusteru Kubernetes v Azure

Je důležité zdůraznit, že dva kanály, sestavení/CI a Release/CD jsou připojené prostřednictvím registru Docker (například Docker Hub nebo Azure Container Registry). Registr Docker je jedním z hlavních rozdílů v porovnání s tradičním procesem CI/CD bez Docker.

Jak je znázorněno na obrázku 5-13, první fází je kanál sestavení/CI. V Azure DevOps Services můžete vytvořit kanály sestavení/CI, které budou kompilovat kód, vytvořit image Docker a vložit je do registru Docker, jako je Docker Hub nebo Azure Container Registry.

![Zobrazení prohlížeče Azure DevOps, definice úlohy procesu sestavení.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Obrázek 5-13**. Vytvoření kanálu sestavení/CI ve službě Azure DevOps vytváření imagí Docker a vkládání imagí do registru Docker

Druhou fází je vytvořit kanál nasazení nebo vydání. V Azure DevOps Services můžete snadno vytvořit kanál nasazení cílící na cluster Kubernetes pomocí úloh Kubernetes pro Azure DevOps Services, jak je znázorněno na obrázku 5-14.

![Zobrazení prohlížeče Azure DevOps, nasazení do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Obrázek 5-14**. Kanál vydaných verzí/CD v Azure DevOps Services nasazení do clusteru Kubernetes

> [! Návod] nasazení eShopModernized do Kubernetes:
>
> Podrobný návod pro kanály CI/CD Azure DevOps, které se nasazují do Kubernetes, najdete v tomto příspěvku: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[Další](../run-manage-monitor-docker-environments/index.md)
