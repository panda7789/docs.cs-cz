---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Modernizovat životní cyklus vaší aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72396213"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu

Dnešní firmy potřebují inovovat na rychlém tempu, aby byly na webu Marketplace konkurenční. Poskytování vysoce kvalitních moderních aplikací vyžaduje nástroje DevOps a procesy, které jsou důležité pro implementaci tohoto stálého cyklu inovace. Díky správným nástrojům DevOps můžou vývojáři zjednodušit průběžné nasazování a rychle získat inovativní aplikace do rukou uživatelů.

I když jsou dobře navázány postupy průběžné integrace a nasazování, zavedení kontejnerů přináší nové požadavky, zejména při práci s aplikacemi s více kontejnery.

Azure DevOps Services podporuje průběžnou integraci a nasazování aplikací s více kontejnery do celé řady prostředí prostřednictvím oficiálních úloh Azure DevOps Services nasazení:

- [Nasazení na Azure Web App for Containers](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Nasazení do služby Azure Kubernetes](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Můžete ji ale také nasadit do [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí Azure DevOps Servicesch úloh založených na skriptech.

Aby bylo možné i nadále usnadnit flexibilitu nasazení, poskytují tyto nástroje vynikající prostředí pro vývoj a testování v produkčním prostředí pro úlohy kontejneru s možností vývoje a CI/CD.

Obrázek 4-12 ukazuje kanál průběžného nasazování, který se v Azure Container Service nasadí do clusteru Kubernetes.

![Snímek obrazovky Azure DevOps Services nasazení do clusteru Kubernetes](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Obrázek 4-12.** Azure DevOps Services kanál průběžného nasazování, nasazení do clusteru Kubernetes

>[!div class="step-by-step"]
>[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Další](migrate-to-hybrid-cloud-scenarios.md)
