---
title: Kroky v postupu DevOps vnější smyčky pro aplikaci v Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a98c34bfdbbdc9b34a04c891ca031f454ac4396
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221391"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="13710-103">Vytváření kanálů CI/CD ve službách Azure DevOps pro aplikace .NET Core 2.0 na kontejnerech a nasazením do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="13710-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="13710-104">Obrázek 5 – 12 se zobrazí scénáře DevOps začátku do konce pokrývající správy kódu a kompilace kódu, sestavení Image Dockeru, nasdílet Image Dockeru do registru Dockeru a nakonec nasazení clusteru Kubernetes v Azure.</span><span class="sxs-lookup"><span data-stu-id="13710-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Pracovní postup: Spustí ve vývojovém počítači.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="13710-107">**Obrázek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="13710-107">**Figure 5-12**.</span></span> <span data-ttu-id="13710-108">CI/CD scénář vytvoření imagí Dockeru a nasazení do clusteru Kubernetes v Azure</span><span class="sxs-lookup"><span data-stu-id="13710-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="13710-109">Je důležité, abyste měli na očích, že dva kanály, sestavení a průběžná integrace a vydání/CD, jsou propojené prostřednictvím registru Dockeru (jako je například Docker Hubu nebo služby Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="13710-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="13710-110">Registr Dockeru je jedním z hlavních rozdílů v porovnání s tradičním procesu CI/CD bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="13710-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="13710-111">Jak je znázorněno v obrázek 5-13, je první fáze kanálu sestavení/CI.</span><span class="sxs-lookup"><span data-stu-id="13710-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="13710-112">Ve službách Azure DevOps můžete vytvořit kanály sestavení/CD, které budou kompilaci kódu, vytvořte Image Dockeru a vložit je do registru Dockeru jako Docker Hubu nebo služby Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="13710-112">In Azure DevOps Services you can create build/CD pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="13710-113">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="13710-113">**Figure 5-13**.</span></span> <span data-ttu-id="13710-114">Sestavení a průběžná integrace kanál v Azure DevOps vytváření imagí Dockeru a nahráním Image do registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="13710-114">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="13710-115">Druhá fáze se k vytvoření kanálu nasazení a vydání.</span><span class="sxs-lookup"><span data-stu-id="13710-115">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="13710-116">Ve službě Azure DevOps Services můžete snadno vytvořit kanál nasazení cílí na Kubernetes cluster pomocí úloh Kubernetes pro Azure DevOps služby, jak je znázorněno v obrázek 5-14.</span><span class="sxs-lookup"><span data-stu-id="13710-116">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Nasazení MVC](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="13710-118">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="13710-118">**Figure 5-14**.</span></span> <span data-ttu-id="13710-119">Kanál verze/CD v Azure DevOps služby nasazením do clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="13710-119">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Návod]<span data-ttu-id="13710-120"> eShopModernized nasazování do Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="13710-120"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="13710-121">Podrobný návod k kanály Azure DevOps CI/CD nasazování do Kubernetes, naleznete v tomto příspěvku: \\</span><span class="sxs-lookup"><span data-stu-id="13710-121">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
>[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

>[!div class="step-by-step"]
><span data-ttu-id="13710-122">[Předchozí](docker-application-outer-loop-devops-workflow.md)
>[další](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="13710-122">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
