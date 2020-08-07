---
title: Registry, image a kontejnery Dockeru
description: Přečtěte si klíčovou roli, kterou Registry hrají celkově v Docker způsob nasazení aplikací.
ms.date: 08/06/2020
ms.openlocfilehash: 2ff6cf76b35777546b6e653d477a029296f8e496
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915242"
---
# <a name="docker-containers-images-and-registries"></a>Registry, image a kontejnery Dockeru

Při použití Docker vytvoříte aplikaci nebo službu a zabalíte ji a její závislosti do image kontejneru. Obrázek je statická reprezentace aplikace nebo služby a její konfigurace a závislosti.

Pokud chcete spustit aplikaci nebo službu, vytvoří se instance image aplikace, aby se vytvořil kontejner, který se bude spouštět na hostiteli Docker. Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo v počítači.

Obrázky můžete ukládat do registru, který funguje jako knihovna imagí. Při nasazování do produkčních orchestrací budete potřebovat registr. Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); Jiní dodavatelé poskytují registry pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Podniky můžou případně mít privátní místní registr pro vlastní image Docker.

Obrázek 1-4 ukazuje, jak obrázky a registry v Docker souvisejí s ostatními komponentami. Zobrazuje také více nabídek registru od dodavatelů.

![Diagram znázorňující základní taxonomii v Docker.](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

**Obrázek 1-4**. Taxonomie podmínek a konceptů Docker

Registr je jako Bookshelf, kde se ukládají image a jsou dostupné pro sestavení pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací. K dispozici jsou privátní Registry Docker místně a ve veřejném cloudu. Docker Hub je veřejný registr udržovaný prostřednictvím Docker, který je spolu s ním důvěryhodným úložištěm na podnikové úrovni. Azure nabízí Azure Container Registry. AWS, Google a další mají také Registry kontejnerů.

Vložením obrázků do registru můžete ukládat statické a neměnné bity aplikace, včetně všech jejich závislostí, na úrovni rozhraní. Pak můžete nasazovat a nasazovat image ve více prostředích a poskytnout tak konzistentní jednotku nasazení.

Registry privátních imagí, ať už hostované místně nebo v cloudu, se doporučují v těchto případech:

- Image se nesmí veřejně sdílet z důvodu důvěrnosti.

- Chcete mít minimální latenci sítě mezi vašimi bitovými kopiemi a zvoleným prostředím nasazení. Pokud je například vaše provozní prostředí Azure, budete pravděpodobně chtít ukládat obrázky v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby latence sítě byla minimální. Podobným způsobem, pokud je vaše produkční prostředí v místním prostředí, možná budete mít k dispozici místní přístup k Docker, který je k dispozici ve stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md) 
> [Další](road-to-modern-applications-based-on-containers.md)
