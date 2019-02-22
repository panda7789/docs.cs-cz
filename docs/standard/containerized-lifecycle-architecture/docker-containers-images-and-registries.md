---
title: Kontejnery dockeru, obrázky a registry
description: Další klíčovou roli, že registry přehrát celkové Docker způsobem nasazení aplikace.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e69490734a03cf58bf8534bc9e31110a11d44c58
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583313"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="b6017-103">Kontejnery dockeru, obrázky a registry</span><span class="sxs-lookup"><span data-stu-id="b6017-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="b6017-104">Pokud používáte Docker, vytvoříte aplikace nebo služby a balíček a jeho závislosti do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b6017-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="b6017-105">Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.</span><span class="sxs-lookup"><span data-stu-id="b6017-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="b6017-106">Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b6017-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="b6017-107">Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.</span><span class="sxs-lookup"><span data-stu-id="b6017-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="b6017-108">Ukládání imagí v registru, který funguje jako knihovny imagí.</span><span class="sxs-lookup"><span data-stu-id="b6017-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="b6017-109">Budete potřebovat registru při nasazení do produkčního prostředí orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="b6017-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="b6017-110">Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="b6017-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="b6017-111">Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b6017-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="b6017-112">Obrázek 1 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty.</span><span class="sxs-lookup"><span data-stu-id="b6017-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="b6017-113">Také ukazuje několik nabídek registru od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="b6017-113">It also shows the multiple registry offerings from vendors.</span></span>

![Základní taxonomie v Dockeru: Registr je stejně jako bookshelf kde Image jsou uložené a k dispozici i pro vytváření kontejnerů ke spuštění služeb nebo webových aplikací.](./media/image4.png)

<span data-ttu-id="b6017-118">**Obrázek 1 – 4**.</span><span class="sxs-lookup"><span data-stu-id="b6017-118">**Figure 1-4**.</span></span> <span data-ttu-id="b6017-119">Taxonomie služby Docker terminologie a koncepty</span><span class="sxs-lookup"><span data-stu-id="b6017-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="b6017-120">Vložením imagí v registru můžete ukládat bits statické a neměnné aplikace, včetně všechny závislé na úrovni rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="b6017-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="b6017-121">Můžete pak můžete verzí a nasazení bitových kopií v různých prostředích a proto poskytují jednotku, konzistentní nasazování.</span><span class="sxs-lookup"><span data-stu-id="b6017-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="b6017-122">Privátní image registrů, buď hostovaný místně nebo v cloudu, se doporučuje při:</span><span class="sxs-lookup"><span data-stu-id="b6017-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="b6017-123">Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="b6017-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="b6017-124">Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení.</span><span class="sxs-lookup"><span data-stu-id="b6017-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="b6017-125">Například pokud vaše produkční prostředí Azure, pravděpodobně chcete ukládat Image v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby byla minimální latence sítě.</span><span class="sxs-lookup"><span data-stu-id="b6017-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="b6017-126">Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="b6017-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b6017-127">[Předchozí](docker-terminology.md)
>[další](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="b6017-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
