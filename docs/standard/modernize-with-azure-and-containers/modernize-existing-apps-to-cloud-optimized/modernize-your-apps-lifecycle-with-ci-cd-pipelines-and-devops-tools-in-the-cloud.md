---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4d3eaa50f6c7645c954ca65bf42c6c1eab3a68d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070783"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu

Dnešní firmy potřebují inovace rychlým tempem, chcete-li být konkurenceschopní na webu Marketplace. Poskytování vysoce kvalitních moderních aplikací vyžaduje procesy, které jsou nezbytné k implementaci tohoto konstantní cyklu inovace a nástroje DevOps. Ty správné nástroje DevOps mohou vývojáři zefektivnit průběžné nasazování a inovativní aplikace do rukou uživatelů rychleji získat.

I když jsou dobře zavedený postupy průběžné integrace a nasazování, úvod kontejnery zavádí nové informace o nastaveních, zejména při práci s vícekontejnerových aplikací.

Služby Azure DevOps podporují průběžnou integraci a nasazení vícekontejnerových aplikací do různých prostředí pomocí oficiální úlohy nasazení služby Azure DevOps:

-   [Nasazení samostatného virtuálního počítače hostitele Docker](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux nebo Windows Server 2016 nebo novější)

-   [Nasazení do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Nasazení do služby Azure Container Service – Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Také můžete nasadit, ale [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí služby Azure DevOps založených na skriptech úloh.

Chcete-li pokračovat, usnadnění nasazení flexibilitu, tyto nástroje umožňují vynikající dev na test – k – produkčního nasazení prostředí pro úlohy kontejneru a řadu řešení CI/CD a vývoj.

Obrázek 4-12 znázorňuje kanál průběžného nasazování, který se nasadí do clusteru Kubernetes ve službě Azure Container Service.

![Azure kanálu průběžného nasazování služby DevOps nasazením do clusteru Kubernetes](./media/image12.png)

> **Obrázek 4 – 12.** Azure kanálu průběžného nasazování služby DevOps nasazením do clusteru Kubernetes

>[!div class="step-by-step"]
[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
[další](migrate-to-hybrid-cloud-scenarios.md)
