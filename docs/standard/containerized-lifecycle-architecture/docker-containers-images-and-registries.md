---
title: Kontejnery dockeru, obrázky a registry
description: Další klíčovou roli, že registry přehrát celkové Docker způsobem nasazení aplikace.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a2e20e09561a5cc91aa29059fb8d19a14205bb5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221196"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="37d2d-103">Kontejnery dockeru, obrázky a registry</span><span class="sxs-lookup"><span data-stu-id="37d2d-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="37d2d-104">Pokud používáte Docker, vytvoříte aplikace nebo služby a balíček a jeho závislosti do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="37d2d-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="37d2d-105">Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.</span><span class="sxs-lookup"><span data-stu-id="37d2d-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="37d2d-106">Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="37d2d-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="37d2d-107">Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.</span><span class="sxs-lookup"><span data-stu-id="37d2d-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="37d2d-108">Ukládání imagí v registru, který se chová jako knihovna obrázků.</span><span class="sxs-lookup"><span data-stu-id="37d2d-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="37d2d-109">Budete potřebovat registru při nasazení do produkčního prostředí orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="37d2d-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="37d2d-110">Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí.</span><span class="sxs-lookup"><span data-stu-id="37d2d-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="37d2d-111">Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="37d2d-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="37d2d-112">Obrázek 1 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty.</span><span class="sxs-lookup"><span data-stu-id="37d2d-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="37d2d-113">Také ukazuje několik nabídek registru od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="37d2d-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="37d2d-114">Obrázek 1 – 4: Taxonomie služby Docker terminologie a koncepty</span><span class="sxs-lookup"><span data-stu-id="37d2d-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="37d2d-115">Vložením imagí v registru můžete ukládat bits statické a neměnné aplikace, včetně všechny závislé na úrovni rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="37d2d-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="37d2d-116">Můžete pak můžete verzí a nasazení bitových kopií v různých prostředích a proto poskytují jednotku, konzistentní nasazování.</span><span class="sxs-lookup"><span data-stu-id="37d2d-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="37d2d-117">Privátní image registrů, hostovaný místně nebo v cloudu, se doporučuje v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="37d2d-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="37d2d-118">Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="37d2d-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="37d2d-119">Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení.</span><span class="sxs-lookup"><span data-stu-id="37d2d-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="37d2d-120">Například pokud vaše produkční prostředí Azure, pravděpodobně chcete ukládat Image ve službě Azure Container Registry, aby se bude minimální latence sítě.</span><span class="sxs-lookup"><span data-stu-id="37d2d-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="37d2d-121">Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="37d2d-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="37d2d-122">[Předchozí](docker-terminology.md)
>[další](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="37d2d-122">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
