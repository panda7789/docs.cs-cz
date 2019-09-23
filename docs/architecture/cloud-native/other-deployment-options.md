---
title: Další možnosti nasazení kontejnerů
description: Další možnosti nasazení kontejnerů pomocí Azure
ms.date: 06/30/2019
ms.openlocfilehash: 892514417cb8650c28b7491315f767758278ad6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184881"
---
# <a name="other-container-deployment-options"></a><span data-ttu-id="4845b-103">Další možnosti nasazení kontejnerů</span><span class="sxs-lookup"><span data-stu-id="4845b-103">Other container deployment options</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4845b-104">Kromě nasazení na AKS můžete také nasadit kontejnery pro Azure App Service kontejnerů a Azure Container Instances.</span><span class="sxs-lookup"><span data-stu-id="4845b-104">In addition to deploying to AKS, you can also deploy containers to Azure App Service for Containers and Azure Container Instances.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="4845b-105">Kdy má smysl nasadit do App Service pro kontejnery?</span><span class="sxs-lookup"><span data-stu-id="4845b-105">When does it make sense to deploy to App Service for Containers?</span></span>

<span data-ttu-id="4845b-106">Jednoduché provozní aplikace, které nevyžadují orchestraci, jsou vhodné pro Azure App Service pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="4845b-106">Simple production applications that don't require orchestration are well-suited to Azure App Service for Containers.</span></span>

## <a name="how-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="4845b-107">Postup nasazení na App Service pro kontejnery</span><span class="sxs-lookup"><span data-stu-id="4845b-107">How to deploy to App Service for Containers</span></span>

<span data-ttu-id="4845b-108">Aby bylo možné nasadit [Azure App Service pro kontejnery](https://azure.microsoft.com/services/app-service/containers/), je nutné nakonfigurovat Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní.</span><span class="sxs-lookup"><span data-stu-id="4845b-108">To deploy to [Azure App Service for Containers](https://azure.microsoft.com/services/app-service/containers/), you need to have configured an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="4845b-109">Nahrajte kontejner, který máte v úmyslu hostovat do registru, aby bylo možné ho načíst do svého Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="4845b-109">Push the container you intend to host to the registry so it's available to pull into your Azure App Service.</span></span> <span data-ttu-id="4845b-110">Po vytvoření můžete aplikaci nakonfigurovat pro průběžné nasazování, která bude automaticky nasazovat aktualizace do aplikace vždy, když aktualizujete odpovídající obrázek v ACR.</span><span class="sxs-lookup"><span data-stu-id="4845b-110">Once created, you can configure the app for Continuous Deployment, which will automatically deploy updates to the app whenever you update its corresponding image in ACR.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a><span data-ttu-id="4845b-111">Kdy má smysl nasadit do Azure Container Instances?</span><span class="sxs-lookup"><span data-stu-id="4845b-111">When does it make sense to deploy to Azure Container Instances?</span></span>

<span data-ttu-id="4845b-112">Azure Container Instances se nejlépe používají pro testovací scénáře.</span><span class="sxs-lookup"><span data-stu-id="4845b-112">Azure Container Instances are best used for testing scenarios.</span></span> <span data-ttu-id="4845b-113">Poskytují rychlý a jednoduchý způsob, jak nasadit aplikaci do instance kontejneru hostovaného v cloudu.</span><span class="sxs-lookup"><span data-stu-id="4845b-113">They provide a fast, simple way to deploy an application to a cloud-hosted container instance.</span></span> <span data-ttu-id="4845b-114">Použijte je k testování nebo demo aplikací, pokud nepotřebujete funkce škálování a orchestrace nabízené službou Azure Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="4845b-114">Use them to test or demo applications when you don't require scaling and orchestration features offered by Azure Kubernetes Service.</span></span>

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a><span data-ttu-id="4845b-115">Jak nasadit aplikaci do Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="4845b-115">How to deploy an app to Azure Container Instances</span></span>

<span data-ttu-id="4845b-116">K nasazení na [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)je nutné nakonfigurovat Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní.</span><span class="sxs-lookup"><span data-stu-id="4845b-116">To deploy to [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/), you need to have configured an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="4845b-117">Je také potřeba, abyste image kontejneru vložili do registru, takže je možné je načíst do ACI.</span><span class="sxs-lookup"><span data-stu-id="4845b-117">You must also have previously pushed your container image to the registry, so it's available to pull into ACI.</span></span> <span data-ttu-id="4845b-118">Můžete pracovat s ACI pomocí rozhraní příkazového řádku Azure nebo prostřednictvím portálu.</span><span class="sxs-lookup"><span data-stu-id="4845b-118">You can work with ACI using the Azure CLI or through the portal.</span></span> <span data-ttu-id="4845b-119">Služby Azure Container Registry usnadňují nasazení jednotlivých instancí kontejnerů do ACI přímo v rámci registru, jak je znázorněno na obrázku 3-14.</span><span class="sxs-lookup"><span data-stu-id="4845b-119">Azure Container Registries make it easy to deploy individual container instances to ACI directly from within the registry, as shown in Figure 3-14.</span></span>

![Instance spuštění Azure Container Registry](./media/acr-runinstance-contextmenu.png)

<span data-ttu-id="4845b-121">**Obrázek 3-14**.</span><span class="sxs-lookup"><span data-stu-id="4845b-121">**Figure 3-14**.</span></span> <span data-ttu-id="4845b-122">Instance spuštění Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="4845b-122">Azure Container Registry Run Instance</span></span>

<span data-ttu-id="4845b-123">Vytvořením instance kontejneru z registru stačí zadat obvyklá nastavení Azure (název, předplatné, skupinu prostředků a umístění), kolik paměti se má přidělit kontejneru, a port, na kterém by měl naslouchat.</span><span class="sxs-lookup"><span data-stu-id="4845b-123">Creating a container instance from the registry just requires you to specify the usual Azure settings (name, subscription, resource group, and location), how much memory to allocate to the container, and which port it should listen on.</span></span> <span data-ttu-id="4845b-124">[V tomto rychlém startu se dozvíte, jak nasadit instanci kontejneru pro ACI pomocí Azure Portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).</span><span class="sxs-lookup"><span data-stu-id="4845b-124">This [quickstart shows how to deploy a container instance to ACI using the Azure portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).</span></span>

<span data-ttu-id="4845b-125">Jakmile se nasazení dokončí, najděte nově nasazenou IP adresu kontejneru a pomocí portu, který jste zadali, nahlaste s ním komunikaci.</span><span class="sxs-lookup"><span data-stu-id="4845b-125">Once the deployment completes, find the newly deployed container's IP address and communicate with it over the port you specified.</span></span>

<span data-ttu-id="4845b-126">Azure Container Instances nabízí nejrychlejší a nejjednodušší způsob spouštění kontejneru v Azure.</span><span class="sxs-lookup"><span data-stu-id="4845b-126">Azure Container Instances offers the fastest, simplest way to run a container in Azure.</span></span> <span data-ttu-id="4845b-127">Není nutné konfigurovat službu App Service ani produkt Orchestrator ani řešit virtuální počítače.</span><span class="sxs-lookup"><span data-stu-id="4845b-127">There's no need to configure an app service or an orchestrator or to deal with virtual machines.</span></span> <span data-ttu-id="4845b-128">Z důvodu zjednodušení by se však ACI měl primárně použít pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="4845b-128">However, because of its simplicity, ACI should primarily be used for testing purposes.</span></span> <span data-ttu-id="4845b-129">Pokud vaše aplikace vyžaduje automatickou škálovatelnost, je pro hostování vaší aplikace k dispozici více kontejnerů, které jsou nakonfigurovány tak, aby spolupracovaly, případně i jakékoli další komplexní funkce.</span><span class="sxs-lookup"><span data-stu-id="4845b-129">If your application requires automatic scalability, multiple containers configured to work together, or any additional complex features, there are other better-suited Azure services available to host your app.</span></span>

## <a name="references"></a><span data-ttu-id="4845b-130">Odkazy</span><span class="sxs-lookup"><span data-stu-id="4845b-130">References</span></span>

- [<span data-ttu-id="4845b-131">Azure Container Instances docs</span><span class="sxs-lookup"><span data-stu-id="4845b-131">Azure Container Instances Docs</span></span>](https://docs.microsoft.com/azure/container-instances/)
- [<span data-ttu-id="4845b-132">Nasadit instanci kontejneru z ACR</span><span class="sxs-lookup"><span data-stu-id="4845b-132">Deploy Container Instance from ACR</span></span>](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
><span data-ttu-id="4845b-133">[Předchozí](scale-containers-serverless.md)
>[Další](communication-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="4845b-133">[Previous](scale-containers-serverless.md)
[Next](communication-patterns.md)</span></span> <!-- Next Chapter -->
