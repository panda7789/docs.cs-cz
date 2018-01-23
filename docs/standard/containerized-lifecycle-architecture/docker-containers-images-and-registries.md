---
title: Docker kontejnery, Image a registry
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cccead8833c63f19b359f830f555e7ff31daa1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="db501-104">Docker kontejnery, Image a registry</span><span class="sxs-lookup"><span data-stu-id="db501-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="db501-105">Když pomocí Docker, můžete vytvořit aplikaci nebo službu a balíček je a jeho závislosti do bitové kopie kontejneru.</span><span class="sxs-lookup"><span data-stu-id="db501-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="db501-106">Obrázek je statický reprezentace aplikace nebo služby a jeho konfigurace a závislostí.</span><span class="sxs-lookup"><span data-stu-id="db501-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="db501-107">Ke spuštění aplikace nebo služby, je vytvořit vytvořit kontejner, který bude spuštěn na hostiteli Docker instance image aplikace.</span><span class="sxs-lookup"><span data-stu-id="db501-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="db501-108">Kontejnery jsou původně testovány v prostředí pro vývoj nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="db501-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="db501-109">Ukládání imagí v registru, která funguje jako knihovny obrázků.</span><span class="sxs-lookup"><span data-stu-id="db501-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="db501-110">Při nasazení v produkčním orchestrators musíte registru.</span><span class="sxs-lookup"><span data-stu-id="db501-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="db501-111">Docker udržuje veřejné registru prostřednictvím [úložiště Docker Hub](https://hub.docker.com/); jiných dodavatelů registrech poskytovat pro různé kolekce obrázků.</span><span class="sxs-lookup"><span data-stu-id="db501-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="db501-112">Alternativně můžete podniků má privátní registru on-premises pro své vlastní imagí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="db501-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="db501-113">Obrázek 1 – 4 ukazuje, jak bitové kopie a registrech v Docker vztahují k ostatní součásti.</span><span class="sxs-lookup"><span data-stu-id="db501-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="db501-114">Také ukazuje několik registru nabídky od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="db501-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="db501-115">Obrázek 1 – 4: taxonomii Docker podmínky a koncepty</span><span class="sxs-lookup"><span data-stu-id="db501-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="db501-116">Vložením bitové kopie v registru můžete ukládat aplikace statické a neměnné bits, včetně všech jejich závislosti na úrovni framework.</span><span class="sxs-lookup"><span data-stu-id="db501-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="db501-117">Budete pak můžete verze a nasazení bitových kopií v prostředí s více a proto poskytují jednotky konzistentní nasazení.</span><span class="sxs-lookup"><span data-stu-id="db501-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="db501-118">Privátní image registrech hostovaný místně nebo v cloudu se doporučují pro následující případy:</span><span class="sxs-lookup"><span data-stu-id="db501-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="db501-119">Bitové kopie nesmí veřejně sdílené z důvodu utajení.</span><span class="sxs-lookup"><span data-stu-id="db501-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="db501-120">Chcete mít minimální latenci mezi vaší bitové kopie a prostředí pro vybrané nasazení.</span><span class="sxs-lookup"><span data-stu-id="db501-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="db501-121">Například pokud produkční prostředí Azure, pravděpodobně chcete ukládat obrázků v registru kontejner Azure tak, aby latence sítě bude minimální.</span><span class="sxs-lookup"><span data-stu-id="db501-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="db501-122">Podobným způsobem Pokud provozním prostředí je na místě, můžete chtít mít místní Docker důvěryhodné registru k dispozici v rámci stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="db501-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="db501-123">[Předchozí] (docker-terminology.md) [Další] (Docker-application-lifecycle/index.md)</span><span class="sxs-lookup"><span data-stu-id="db501-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
