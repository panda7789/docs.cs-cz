---
title: Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56dbd4a867e0f47d0f7e681d924584629d763f87
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD

Dnešní podnikům muset inovacemi. Zajistěte rychlé tempem být produktivní v marketplace. Poskytování vysoce kvalitních, moderní aplikace vyžaduje DevOps nástroje a procesy, které jsou důležité pro implementaci tohoto konstantní cyklu inovace. Správné nástroje DevOps vývojáři můžou zjednodušit průběžné nasazování a získat inovativní aplikace do rukou uživatelů rychleji.

I když jsou osvědčených postupů průběžnou integraci a nasazení, zavedení kontejnery zavádí nové aspekty, zejména při práci s aplikacemi s více kontejneru.

Visual Studio Team Services podporuje průběžnou integraci a nasazení aplikací služby kontejneru na celou řadu prostředí prostřednictvím oficiální úlohy nasazení Team Services:

-   [Nasazení na samostatný počítač hostitelů Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux nebo Windows Server 2016 nebo novější)

-   [Nasazení do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Nasazení do Azure Container Service – Kubernetes](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

Také můžete nasadit, ale [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí úloh založených na skriptech Team Services.

Chcete-li pokračovat, usnadnění nasazení flexibility, zadejte tyto nástroje vynikající dev na testovací na produkční nasazení dojde u kontejneru zatížení s volbou vývoj a CI/CD řešení.

Obrázek 4 – 12 znázorňuje průběžné nasazování kanál, který se nasadí do clusteru s podporou Kubernetes v Azure Container Service.

![Visual Studio Team Services průběžné nasazování kanálu, nasazení do clusteru s podporou Kubernetes](./media/image12.png)

> **Obrázek 4 – 12.** Visual Studio Team Services průběžné nasazování kanálu, nasazení do clusteru s podporou Kubernetes

>[!div class="step-by-step"]
[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
[další](migrate-to-hybrid-cloud-scenarios.md)
