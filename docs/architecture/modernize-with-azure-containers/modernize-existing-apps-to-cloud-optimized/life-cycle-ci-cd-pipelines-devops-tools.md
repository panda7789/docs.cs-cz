---
title: Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: afb7bae7780a766329ca604d192b2d7353e32bf5
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739163"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="13840-103">Modernizace životního cyklu aplikace pomocí kanálů CI/CD a nástrojů DevOps v cloudu</span><span class="sxs-lookup"><span data-stu-id="13840-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="13840-104">Dnešní podniky musí rychle inovovat, aby byly konkurenceschopné na trhu.</span><span class="sxs-lookup"><span data-stu-id="13840-104">Today's businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="13840-105">Poskytování vysoce kvalitních a moderních aplikací vyžaduje nástroje a procesy DevOps, které jsou důležité pro implementaci tohoto konstantního cyklu inovací.</span><span class="sxs-lookup"><span data-stu-id="13840-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="13840-106">Se správnými nástroji DevOps mohou vývojáři zefektivnit průběžné nasazování a rychleji dostat inovativní aplikace do rukou uživatelů.</span><span class="sxs-lookup"><span data-stu-id="13840-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="13840-107">Přestože jsou dobře zavedeny postupy průběžné integrace a nasazování, zavedení kontejnerů přináší nové aspekty, zejména při práci s aplikacemi s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="13840-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="13840-108">Služby Azure DevOps Services podporují průběžnou integraci a nasazování aplikací s více kontejnery do různých prostředí prostřednictvím oficiálních úloh nasazení služeb Azure DevOps:</span><span class="sxs-lookup"><span data-stu-id="13840-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="13840-109">Nasazení do Azure Web Appu pro kontejnery</span><span class="sxs-lookup"><span data-stu-id="13840-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="13840-110">Nasazení do Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="13840-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="13840-111">Ale můžete také nasadit do [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) nebo DC/OS pomocí úloh založených na skriptech Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="13840-111">But you can also deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="13840-112">Chcete-li i nadále usnadnit flexibilitu nasazení, poskytují tyto nástroje vynikající prostředí pro nasazení od vývoje do provozu pro úlohy kontejnerů s možností výběru řešení pro vývoj a CI/CD.</span><span class="sxs-lookup"><span data-stu-id="13840-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="13840-113">Obrázek 4-12 znázorňuje kanál průběžného nasazení, který se nasazuje do clusteru Kubernetes ve službě Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="13840-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Snímek obrazovky se službami Azure DevOps, které se nasazují do clusteru Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="13840-115">**Obrázek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="13840-115">**Figure 4-12.**</span></span> <span data-ttu-id="13840-116">Kanál průběžného nasazení služby Azure DevOps, nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="13840-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="13840-117">[Předchozí](modernize-your-apps-with-monitoring-and-telemetry.md)
>[další](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="13840-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
