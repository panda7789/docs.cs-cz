---
title: "Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 668c48b64cab964da65625ef5326fb75e133b3b9
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="a999e-103">Modernizovat životního cyklu vaší aplikace pomocí nástrojů DevOps v cloudu a kanály CI/CD</span><span class="sxs-lookup"><span data-stu-id="a999e-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="a999e-104">Dnešní podnikům muset inovacemi. Zajistěte rychlé tempem být produktivní v marketplace.</span><span class="sxs-lookup"><span data-stu-id="a999e-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="a999e-105">Poskytování vysoce kvalitních, moderní aplikace vyžaduje DevOps nástroje a procesy, které jsou důležité pro implementaci tohoto konstantní cyklu inovace.</span><span class="sxs-lookup"><span data-stu-id="a999e-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="a999e-106">Správné nástroje DevOps vývojáři můžou zjednodušit průběžné nasazování a získat inovativní aplikace do rukou uživatelů rychleji.</span><span class="sxs-lookup"><span data-stu-id="a999e-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="a999e-107">I když jsou osvědčených postupů průběžnou integraci a nasazení, zavedení kontejnery zavádí nové aspekty, zejména při práci s aplikacemi s více kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a999e-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="a999e-108">Visual Studio Team Services podporuje průběžnou integraci a nasazení aplikací služby kontejneru na celou řadu prostředí prostřednictvím oficiální úlohy nasazení Team Services:</span><span class="sxs-lookup"><span data-stu-id="a999e-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="a999e-109">[Nasazení na samostatný počítač hostitelů Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux nebo Windows Server 2016 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="a999e-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="a999e-110">Nasazení do Service Fabric</span><span class="sxs-lookup"><span data-stu-id="a999e-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="a999e-111">Nasazení do Azure Container Service – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a999e-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="a999e-112">Také můžete nasadit, ale [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí úloh založených na skriptech Team Services.</span><span class="sxs-lookup"><span data-stu-id="a999e-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="a999e-113">Chcete-li pokračovat, usnadnění nasazení flexibility, zadejte tyto nástroje vynikající dev na testovací na produkční nasazení dojde u kontejneru zatížení s volbou vývoj a CI/CD řešení.</span><span class="sxs-lookup"><span data-stu-id="a999e-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="a999e-114">Obrázek 4 – 12 znázorňuje průběžné nasazování kanál, který se nasadí do clusteru s podporou Kubernetes v Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="a999e-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services průběžné nasazování kanálu, nasazení do clusteru s podporou Kubernetes](./media/image12.png)

> <span data-ttu-id="a999e-116">**Obrázek 4 – 12.**</span><span class="sxs-lookup"><span data-stu-id="a999e-116">**Figure 4-12.**</span></span> <span data-ttu-id="a999e-117">Visual Studio Team Services průběžné nasazování kanálu, nasazení do clusteru s podporou Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a999e-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a999e-118">[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
[další](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a999e-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
