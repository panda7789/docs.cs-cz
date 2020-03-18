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
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="c861c-103">Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c861c-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="c861c-104">Na obrázku 5-12 uvidíte scénář end-to-end DevOps zahrnující správu kódu, kompilaci kódu, sestavení icloudů Dockeru, iimage Dockeru push do registru Dockeru a nakonec nasazení do clusteru Kubernetes v Azure.</span><span class="sxs-lookup"><span data-stu-id="c861c-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Pracovní postup: Spustí se ve vývojovém stroji.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="c861c-107">**Obrázek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="c861c-107">**Figure 5-12**.</span></span> <span data-ttu-id="c861c-108">Scénář CI/CD vytváření ibi Dockeru a nasazování do clusteru Kubernetes v Azure</span><span class="sxs-lookup"><span data-stu-id="c861c-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="c861c-109">Je důležité zdůraznit, že dva kanály, sestavení/CI a uvolnění nebo CD, jsou propojeny prostřednictvím registru Docker (například Docker Hub nebo Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="c861c-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="c861c-110">Registr Dockeru je jedním z hlavních rozdílů ve srovnání s tradičním procesem CI/CD bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c861c-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="c861c-111">Jak je znázorněno na obrázku 5-13, první fáze je potrubí sestavení/CI.</span><span class="sxs-lookup"><span data-stu-id="c861c-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="c861c-112">Ve službách Azure DevOps můžete vytvořit kanály sestavení nebo CI, které zkompilují kód, vytvoří ibi Dockeru a zatlačí je do registru Dockeru, jako je Docker Hub nebo Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="c861c-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Zobrazení prohlížeče Azure DevOps, Vytvoření definice úlohy procesu.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="c861c-114">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="c861c-114">**Figure 5-13**.</span></span> <span data-ttu-id="c861c-115">Kanál sestavení a ci v Azure DevOps buduje ibi Dockeru a vysune image Dockeru do registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c861c-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="c861c-116">Druhou fází je vytvoření kanálu nasazení a vydání.</span><span class="sxs-lookup"><span data-stu-id="c861c-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="c861c-117">Ve službách Azure DevOps můžete snadno vytvořit kanál nasazení zaměřený na cluster Kubernetes pomocí úloh Kubernetes pro služby Azure DevOps, jak je znázorněno na obrázku 5-14.</span><span class="sxs-lookup"><span data-stu-id="c861c-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Zobrazení prohlížeče Azure DevOps, nasazení do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="c861c-119">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="c861c-119">**Figure 5-14**.</span></span> <span data-ttu-id="c861c-120">Kanál vydání nebo disku CD ve službě Azure DevOps, který se nasazuje do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c861c-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Návod]<span data-ttu-id="c861c-121"> Nasazení eShopuModernizované na Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="c861c-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="c861c-122">Podrobný návod k kanálům Azure DevOps CI/CD, které se nasazují do Kubernetes, najdete v tomto příspěvku: </span><span class="sxs-lookup"><span data-stu-id="c861c-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="c861c-123">[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[další](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="c861c-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
