---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: cc991bba5df3a9cd972d9a172c1a8f1035ce8c58
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758649"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="74f85-103">Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu</span><span class="sxs-lookup"><span data-stu-id="74f85-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="74f85-104">Dnešní firmy potřebují inovace rychlým tempem, chcete-li být konkurenceschopní na webu Marketplace.</span><span class="sxs-lookup"><span data-stu-id="74f85-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="74f85-105">Poskytování vysoce kvalitních moderních aplikací vyžaduje procesy, které jsou nezbytné k implementaci tohoto konstantní cyklu inovace a nástroje DevOps.</span><span class="sxs-lookup"><span data-stu-id="74f85-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="74f85-106">Ty správné nástroje DevOps mohou vývojáři zefektivnit průběžné nasazování a inovativní aplikace do rukou uživatelů rychleji získat.</span><span class="sxs-lookup"><span data-stu-id="74f85-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="74f85-107">I když jsou dobře zavedený postupy průběžné integrace a nasazování, úvod kontejnery zavádí nové informace o nastaveních, zejména při práci s vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="74f85-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="74f85-108">Služby Azure DevOps podporují průběžnou integraci a nasazení vícekontejnerových aplikací do různých prostředí pomocí oficiální úlohy nasazení služby Azure DevOps:</span><span class="sxs-lookup"><span data-stu-id="74f85-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- <span data-ttu-id="74f85-109">[Nasazení samostatného virtuálního počítače hostitele Docker](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux nebo Windows Server 2016 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="74f85-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

- [<span data-ttu-id="74f85-110">Nasazení do služby Azure Container Service – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="74f85-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="74f85-111">Také můžete nasadit, ale [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) nebo DC/OS pomocí služby Azure DevOps založených na skriptech úloh.</span><span class="sxs-lookup"><span data-stu-id="74f85-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="74f85-112">Chcete-li pokračovat, usnadnění nasazení flexibilitu, tyto nástroje umožňují vynikající dev na test – k – produkčního nasazení prostředí pro úlohy kontejneru a řadu řešení CI/CD a vývoj.</span><span class="sxs-lookup"><span data-stu-id="74f85-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="74f85-113">Obrázek 4-12 znázorňuje kanál průběžného nasazování, který se nasadí do clusteru Kubernetes ve službě Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="74f85-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure kanálu průběžného nasazování služby DevOps nasazením do clusteru Kubernetes](./media/image12.png)

> <span data-ttu-id="74f85-115">**Obrázek 4 – 12.**</span><span class="sxs-lookup"><span data-stu-id="74f85-115">**Figure 4-12.**</span></span> <span data-ttu-id="74f85-116">Azure kanálu průběžného nasazování služby DevOps nasazením do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="74f85-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="74f85-117">[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
>[další](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="74f85-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
