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
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="b7f27-103">Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b7f27-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="b7f27-104">Na obrázku 5-12 se můžete podívat na celý scénář DevOps, který pokrývá správu kódu, kompilaci kódu, buildy Docker images, Docker images push do registru Docker a nakonec nasazení do clusteru Kubernetes v Azure.</span><span class="sxs-lookup"><span data-stu-id="b7f27-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Pracovního postupu Spustí se ve vývojovém počítači.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="b7f27-107">**Obrázek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="b7f27-107">**Figure 5-12**.</span></span> <span data-ttu-id="b7f27-108">Scénář CI/CD vytváření imagí Docker a nasazení do clusteru Kubernetes v Azure</span><span class="sxs-lookup"><span data-stu-id="b7f27-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="b7f27-109">Je důležité zdůraznit, že dva kanály, sestavení/CI a Release/CD jsou připojené prostřednictvím registru Docker (například Docker Hub nebo Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="b7f27-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="b7f27-110">Registr Docker je jedním z hlavních rozdílů v porovnání s tradičním procesem CI/CD bez Docker.</span><span class="sxs-lookup"><span data-stu-id="b7f27-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="b7f27-111">Jak je znázorněno na obrázku 5-13, první fází je kanál sestavení/CI.</span><span class="sxs-lookup"><span data-stu-id="b7f27-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="b7f27-112">V Azure DevOps Services můžete vytvořit kanály sestavení/CI, které budou kompilovat kód, vytvořit image Docker a vložit je do registru Docker, jako je Docker Hub nebo Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="b7f27-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Zobrazení prohlížeče Azure DevOps, definice úlohy procesu sestavení.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="b7f27-114">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="b7f27-114">**Figure 5-13**.</span></span> <span data-ttu-id="b7f27-115">Vytvoření kanálu sestavení/CI ve službě Azure DevOps vytváření imagí Docker a vkládání imagí do registru Docker</span><span class="sxs-lookup"><span data-stu-id="b7f27-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="b7f27-116">Druhou fází je vytvořit kanál nasazení nebo vydání.</span><span class="sxs-lookup"><span data-stu-id="b7f27-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="b7f27-117">V Azure DevOps Services můžete snadno vytvořit kanál nasazení cílící na cluster Kubernetes pomocí úloh Kubernetes pro Azure DevOps Services, jak je znázorněno na obrázku 5-14.</span><span class="sxs-lookup"><span data-stu-id="b7f27-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Zobrazení prohlížeče Azure DevOps, nasazení do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="b7f27-119">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="b7f27-119">**Figure 5-14**.</span></span> <span data-ttu-id="b7f27-120">Kanál vydaných verzí/CD v Azure DevOps Services nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b7f27-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Návod]<span data-ttu-id="b7f27-121"> nasazení eShopModernized do Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="b7f27-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="b7f27-122">Podrobný návod pro kanály CI/CD Azure DevOps, které se nasazují do Kubernetes, najdete v tomto příspěvku: </span><span class="sxs-lookup"><span data-stu-id="b7f27-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="b7f27-123">[Předchozí](docker-application-outer-loop-devops-workflow.md)Další
>[](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="b7f27-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
