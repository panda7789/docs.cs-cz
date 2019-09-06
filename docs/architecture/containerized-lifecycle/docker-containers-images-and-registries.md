---
title: Registry, image a kontejnery Dockeru
description: Přečtěte si klíčovou roli, kterou Registry hrají celkově v Docker způsob nasazení aplikací.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295658"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="3ef0e-103">Registry, image a kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="3ef0e-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="3ef0e-104">Při použití Docker vytvoříte aplikaci nebo službu a zabalíte ji a její závislosti do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="3ef0e-105">Obrázek je statická reprezentace aplikace nebo služby a její konfigurace a závislosti.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="3ef0e-106">Pokud chcete spustit aplikaci nebo službu, vytvoří se instance image aplikace, aby se vytvořil kontejner, který se bude spouštět na hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="3ef0e-107">Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo v počítači.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="3ef0e-108">Obrázky ukládáte do registru, který funguje jako knihovna imagí.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="3ef0e-109">Při nasazování do produkčních orchestrací budete potřebovat registr.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="3ef0e-110">Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); Jiní dodavatelé poskytují registry pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="3ef0e-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="3ef0e-111">Podniky můžou případně mít privátní místní registr pro vlastní image Docker.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="3ef0e-112">Obrázek 1-4 ukazuje, jak obrázky a registry v Docker souvisejí s ostatními komponentami.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="3ef0e-113">Zobrazuje také více nabídek registru od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-113">It also shows the multiple registry offerings from vendors.</span></span>

![Základní taxonomie v Docker: Registr je jako Bookshelf, kde se ukládají image a jsou dostupné pro sestavení pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací.](./media/image4.png)

<span data-ttu-id="3ef0e-118">**Obrázek 1-4**.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-118">**Figure 1-4**.</span></span> <span data-ttu-id="3ef0e-119">Taxonomie podmínek a konceptů Docker</span><span class="sxs-lookup"><span data-stu-id="3ef0e-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="3ef0e-120">Vložením obrázků do registru můžete ukládat statické a neměnné bity aplikace, včetně všech jejich závislostí, na úrovni rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="3ef0e-121">Pak můžete nasazovat a nasazovat image ve více prostředích a poskytnout tak konzistentní jednotku nasazení.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="3ef0e-122">Registry privátních imagí, ať už hostované místně nebo v cloudu, se doporučují v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="3ef0e-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="3ef0e-123">Image se nesmí veřejně sdílet z důvodu důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="3ef0e-124">Chcete mít minimální latenci sítě mezi vašimi bitovými kopiemi a zvoleným prostředím nasazení.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="3ef0e-125">Pokud je například vaše provozní prostředí Azure, budete pravděpodobně chtít ukládat obrázky v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby latence sítě byla minimální.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="3ef0e-126">Podobným způsobem, pokud je vaše produkční prostředí v místním prostředí, možná budete mít k dispozici místní přístup k Docker, který je k dispozici ve stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="3ef0e-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3ef0e-127">[Předchozí](docker-terminology.md)Další
>[](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="3ef0e-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
