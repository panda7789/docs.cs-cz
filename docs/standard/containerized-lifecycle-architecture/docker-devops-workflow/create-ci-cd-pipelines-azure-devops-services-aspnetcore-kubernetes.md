---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644975"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="d9181-103">Vytváření kanálů CI/CD ve službě Azure DevOps Services pro aplikaci .NET Core 2.0 v kontejnerech a nasazení do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d9181-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="d9181-104">Obrázek 5 – 12 se zobrazí scénáře DevOps začátku do konce pokrývající správy kódu a kompilace kódu, sestavení Image Dockeru, nasdílet Image Dockeru do registru Dockeru a nakonec nasazení clusteru Kubernetes v Azure.</span><span class="sxs-lookup"><span data-stu-id="d9181-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Pracovní postup: Spustí ve vývojovém počítači.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="d9181-107">**Obrázek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="d9181-107">**Figure 5-12**.</span></span> <span data-ttu-id="d9181-108">CI/CD scénář vytvoření imagí Dockeru a nasazení do clusteru Kubernetes v Azure</span><span class="sxs-lookup"><span data-stu-id="d9181-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="d9181-109">Je důležité, abyste měli na očích, že dva kanály, sestavení a průběžná integrace a vydání/CD, jsou propojené prostřednictvím registru Dockeru (jako je například Docker Hubu nebo služby Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="d9181-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="d9181-110">Registr Dockeru je jedním z hlavních rozdílů v porovnání s tradičním procesu CI/CD bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="d9181-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="d9181-111">Jak je znázorněno v obrázek 5-13, je první fáze kanálu sestavení/CI.</span><span class="sxs-lookup"><span data-stu-id="d9181-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="d9181-112">Ve službě Azure DevOps Services můžete vytvářet kanály sestavení a průběžná integrace, které budou kompilaci kódu, vytvořte Image Dockeru a vložit je do registru Dockeru jako Docker Hubu nebo služby Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="d9181-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Zobrazení prohlížeče s Azure DevOps, definice úlohy procesu sestavení.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="d9181-114">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="d9181-114">**Figure 5-13**.</span></span> <span data-ttu-id="d9181-115">Sestavení a průběžná integrace kanál v Azure DevOps vytváření imagí Dockeru a nahráním Image do registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="d9181-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="d9181-116">Druhá fáze se k vytvoření kanálu nasazení a vydání.</span><span class="sxs-lookup"><span data-stu-id="d9181-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="d9181-117">Ve službě Azure DevOps Services můžete snadno vytvořit kanál nasazení cílí na Kubernetes cluster pomocí úloh Kubernetes pro Azure DevOps služby, jak je znázorněno v obrázek 5-14.</span><span class="sxs-lookup"><span data-stu-id="d9181-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Zobrazení prohlížeče s Azure DevOps, nasaďte do definice úlohy Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="d9181-119">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="d9181-119">**Figure 5-14**.</span></span> <span data-ttu-id="d9181-120">Kanál verze/CD v Azure DevOps služby nasazením do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d9181-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Návod]<span data-ttu-id="d9181-121"> eShopModernized nasazování do Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="d9181-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="d9181-122">Podrobný návod k kanály Azure DevOps CI/CD nasazování do Kubernetes, naleznete v tomto příspěvku: </span><span class="sxs-lookup"><span data-stu-id="d9181-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="d9181-123">[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[další](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="d9181-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
