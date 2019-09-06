---
title: Registry, image a kontejnery Dockeru
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Kontejnery, image a Registry Docker
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296199"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="18bce-103">Registry, image a kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="18bce-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="18bce-104">Při použití Docker vytvoří vývojář aplikaci nebo službu a zabalí ji a její závislosti do image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="18bce-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="18bce-105">Obrázek je statická reprezentace aplikace nebo služby a její konfigurace a závislosti.</span><span class="sxs-lookup"><span data-stu-id="18bce-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="18bce-106">Pokud chcete spustit aplikaci nebo službu, vytvoří se instance image aplikace, aby se vytvořil kontejner, který se bude spouštět na hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="18bce-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="18bce-107">Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo v počítači.</span><span class="sxs-lookup"><span data-stu-id="18bce-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="18bce-108">Vývojáři by měli ukládat image do registru, který funguje jako knihovna imagí, a je potřeba při nasazení do orchestrace v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="18bce-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="18bce-109">Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); Jiní dodavatelé poskytují registry pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="18bce-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="18bce-110">Podniky můžou případně mít privátní místní registr pro vlastní image Docker.</span><span class="sxs-lookup"><span data-stu-id="18bce-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="18bce-111">Obrázek 2-4 ukazuje, jak obrázky a registry v Docker souvisejí s ostatními komponentami.</span><span class="sxs-lookup"><span data-stu-id="18bce-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="18bce-112">Zobrazuje také více nabídek registru od dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="18bce-112">It also shows the multiple registry offerings from vendors.</span></span>

![Základní taxonomie v Docker: Registr je jako Bookshelf, kde se ukládají image a jsou dostupné pro sestavení pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací.](./media/image5.PNG)

<span data-ttu-id="18bce-117">**Obrázek 2-4**.</span><span class="sxs-lookup"><span data-stu-id="18bce-117">**Figure 2-4**.</span></span> <span data-ttu-id="18bce-118">Taxonomie podmínek a konceptů Docker</span><span class="sxs-lookup"><span data-stu-id="18bce-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="18bce-119">Vložení imagí do registru vám umožní ukládat statické a neměnné bity aplikace, včetně všech jejich závislostí na úrovni rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18bce-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="18bce-120">Tyto Image je pak možné nasazovat a nasazovat ve více prostředích a zajistit tak konzistentní jednotku nasazení.</span><span class="sxs-lookup"><span data-stu-id="18bce-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="18bce-121">Registry privátních imagí, ať už hostované místně nebo v cloudu, se doporučují v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="18bce-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="18bce-122">Image se nesmí veřejně sdílet z důvodu důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="18bce-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="18bce-123">Chcete mít minimální latenci sítě mezi vašimi bitovými kopiemi a zvoleným prostředím nasazení.</span><span class="sxs-lookup"><span data-stu-id="18bce-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="18bce-124">Pokud je například vaše produkční prostředí Azure Cloud, budete pravděpodobně chtít ukládat obrázky v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, že bude latence sítě minimální.</span><span class="sxs-lookup"><span data-stu-id="18bce-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="18bce-125">Podobným způsobem, pokud je vaše produkční prostředí v místním prostředí, možná budete mít k dispozici místní přístup k Docker, který je k dispozici ve stejné místní síti.</span><span class="sxs-lookup"><span data-stu-id="18bce-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18bce-126">[Předchozí](docker-terminology.md)Další
>[](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="18bce-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
