---
title: Docker kontejnery, Image a registry
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Docker kontejnery, Image a registry"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79dccadfba066c673e8ef7ea5eaf1051a434ff3a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="0c8b9-104">Docker kontejnery, Image a registry</span><span class="sxs-lookup"><span data-stu-id="0c8b9-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="0c8b9-105">Při použití Docker, vytvoří vývojář aplikace nebo služby a balíčky ho a jeho závislosti do bitové kopie kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="0c8b9-106">Obrázek je statický reprezentace aplikace nebo služby a jeho konfigurace a závislostí.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="0c8b9-107">Ke spuštění aplikace nebo služby, je vytvořit vytvořit kontejner, který bude spuštěn na hostiteli Docker instance image aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="0c8b9-108">Kontejnery jsou původně testovány v prostředí pro vývoj nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="0c8b9-109">Vývojáři měli uložit bitové kopie v registru, který funguje jako knihovny obrázků a je potřeba při nasazení v produkčním orchestrators.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="0c8b9-110">Docker udržuje veřejné registru prostřednictvím [úložiště Docker Hub](https://hub.docker.com/); jiných dodavatelů registrech poskytovat pro různé kolekce obrázků.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="0c8b9-111">Alternativně můžete podniků má privátní registru on-premises pro své vlastní imagí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="0c8b9-112">Obrázek 2 – 4 ukazuje, jak bitové kopie a registrech v Docker vztahují k ostatní součásti.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="0c8b9-113">Také ukazuje několik registru nabídky od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="0c8b9-114">**Obrázek 2 – 4**.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-114">**Figure 2-4**.</span></span> <span data-ttu-id="0c8b9-115">Taxonomii Docker podmínky a koncepty</span><span class="sxs-lookup"><span data-stu-id="0c8b9-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="0c8b9-116">Vložení obrázků v registru umožňuje uložit bitů statické a neměnné aplikace, včetně jejich závislosti na úrovni framework.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="0c8b9-117">Tyto bitové kopie můžete poté by se verzí a nasazené v několika prostředích a proto zadejte jednotky konzistentní nasazení.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="0c8b9-118">Privátní image registrech buď hostované místně nebo v cloudu, se doporučuje při:</span><span class="sxs-lookup"><span data-stu-id="0c8b9-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="0c8b9-119">Bitové kopie nesmí veřejně sdílené z důvodu utajení.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="0c8b9-120">Chcete mít minimální latenci mezi vaší bitové kopie a prostředí pro vybrané nasazení.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="0c8b9-121">Například pokud produkční prostředí cloudu Azure, pravděpodobně chcete ukládat obrázků v registru kontejner Azure tak, aby latence sítě bude minimální.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="0c8b9-122">Podobným způsobem Pokud provozním prostředí je na místě, můžete chtít mít místní Docker důvěryhodné registru k dispozici v rámci stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="0c8b9-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0c8b9-123">[Předchozí] (docker-terminology.md) [Další] (.. /NET-Core-NET-Framework-Containers/index.MD)</span><span class="sxs-lookup"><span data-stu-id="0c8b9-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
