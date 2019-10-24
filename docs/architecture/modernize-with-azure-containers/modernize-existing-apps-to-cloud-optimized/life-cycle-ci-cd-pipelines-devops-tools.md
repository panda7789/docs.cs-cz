---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Modernizovat životní cyklus vaší aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396213"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="cc737-103">Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu</span><span class="sxs-lookup"><span data-stu-id="cc737-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="cc737-104">Dnešní firmy potřebují inovovat na rychlém tempu, aby byly na webu Marketplace konkurenční.</span><span class="sxs-lookup"><span data-stu-id="cc737-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="cc737-105">Poskytování vysoce kvalitních moderních aplikací vyžaduje nástroje DevOps a procesy, které jsou důležité pro implementaci tohoto stálého cyklu inovace.</span><span class="sxs-lookup"><span data-stu-id="cc737-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="cc737-106">Díky správným nástrojům DevOps můžou vývojáři zjednodušit průběžné nasazování a rychle získat inovativní aplikace do rukou uživatelů.</span><span class="sxs-lookup"><span data-stu-id="cc737-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="cc737-107">I když jsou dobře navázány postupy průběžné integrace a nasazování, zavedení kontejnerů přináší nové požadavky, zejména při práci s aplikacemi s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="cc737-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="cc737-108">Azure DevOps Services podporuje průběžnou integraci a nasazování aplikací s více kontejnery do celé řady prostředí prostřednictvím oficiálních úloh Azure DevOps Services nasazení:</span><span class="sxs-lookup"><span data-stu-id="cc737-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="cc737-109">Nasazení na Azure Web App for Containers</span><span class="sxs-lookup"><span data-stu-id="cc737-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="cc737-110">Nasazení do služby Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="cc737-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="cc737-111">Můžete ji ale také nasadit do [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí Azure DevOps Servicesch úloh založených na skriptech.</span><span class="sxs-lookup"><span data-stu-id="cc737-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="cc737-112">Aby bylo možné i nadále usnadnit flexibilitu nasazení, poskytují tyto nástroje vynikající prostředí pro vývoj a testování v produkčním prostředí pro úlohy kontejneru s možností vývoje a CI/CD.</span><span class="sxs-lookup"><span data-stu-id="cc737-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="cc737-113">Obrázek 4-12 ukazuje kanál průběžného nasazování, který se v Azure Container Service nasadí do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="cc737-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Snímek obrazovky Azure DevOps Services nasazení do clusteru Kubernetes](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="cc737-115">**Obrázek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="cc737-115">**Figure 4-12.**</span></span> <span data-ttu-id="cc737-116">Azure DevOps Services kanál průběžného nasazování, nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="cc737-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cc737-117">[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Další](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="cc737-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>