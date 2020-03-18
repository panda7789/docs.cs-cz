---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503849"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu

Dnešní podniky musí rychle inovovat, aby byly konkurenceschopné na trhu. Poskytování vysoce kvalitních a moderních aplikací vyžaduje nástroje a procesy DevOps, které jsou důležité pro implementaci tohoto konstantního cyklu inovací. Se správnými nástroji DevOps mohou vývojáři zefektivnit průběžné nasazování a rychleji dostat inovativní aplikace do rukou uživatelů.

Přestože jsou dobře zavedeny postupy průběžné integrace a nasazování, zavedení kontejnerů přináší nové aspekty, zejména při práci s aplikacemi s více kontejnery.

Služby Azure DevOps Services podporují průběžnou integraci a nasazování aplikací s více kontejnery do různých prostředí prostřednictvím oficiálních úloh nasazení služeb Azure DevOps:

- [Nasazení do Azure Web Appu pro kontejnery](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Nasazení do Azure Kubernetes Service](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ale můžete také nasadit do [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) nebo DC/OS pomocí úloh založených na skriptech Azure DevOps Services.

Chcete-li i nadále usnadnit flexibilitu nasazení, poskytují tyto nástroje vynikající prostředí pro nasazení od vývoje do provozu pro úlohy kontejnerů s možností výběru řešení pro vývoj a CI/CD.

Obrázek 4-12 znázorňuje kanál průběžného nasazení, který se nasazuje do clusteru Kubernetes ve službě Azure Container Service.

![Snímek obrazovky se službami Azure DevOps, které se nasazují do clusteru Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Obrázek 4-12.** Kanál průběžného nasazení služby Azure DevOps, nasazení do clusteru Kubernetes

>[!div class="step-by-step"]
>[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
>[další](migrate-to-hybrid-cloud-scenarios.md)
