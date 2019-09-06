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
# <a name="docker-containers-images-and-registries"></a>Registry, image a kontejnery Dockeru

Při použití Docker vytvoří vývojář aplikaci nebo službu a zabalí ji a její závislosti do image kontejneru. Obrázek je statická reprezentace aplikace nebo služby a její konfigurace a závislosti.

Pokud chcete spustit aplikaci nebo službu, vytvoří se instance image aplikace, aby se vytvořil kontejner, který se bude spouštět na hostiteli Docker. Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo v počítači.

Vývojáři by měli ukládat image do registru, který funguje jako knihovna imagí, a je potřeba při nasazení do orchestrace v produkčním prostředí. Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); Jiní dodavatelé poskytují registry pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Podniky můžou případně mít privátní místní registr pro vlastní image Docker.

Obrázek 2-4 ukazuje, jak obrázky a registry v Docker souvisejí s ostatními komponentami. Zobrazuje také více nabídek registru od dodavatelů.

![Základní taxonomie v Docker: Registr je jako Bookshelf, kde se ukládají image a jsou dostupné pro sestavení pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací. Existují privátní Registry Docker v-Prem a ve veřejném cloudu. Docker Hub je veřejný registr udržovaný prostřednictvím Docker, který je spolu s ním důvěryhodným úložištěm na podnikové úrovni. Azure nabízí Azure Container Registry. AWS, Google a další mají také Registry kontejnerů.](./media/image5.PNG)

**Obrázek 2-4**. Taxonomie podmínek a konceptů Docker

Vložení imagí do registru vám umožní ukládat statické a neměnné bity aplikace, včetně všech jejich závislostí na úrovni rozhraní. Tyto Image je pak možné nasazovat a nasazovat ve více prostředích a zajistit tak konzistentní jednotku nasazení.

Registry privátních imagí, ať už hostované místně nebo v cloudu, se doporučují v těchto případech:

- Image se nesmí veřejně sdílet z důvodu důvěrnosti.

- Chcete mít minimální latenci sítě mezi vašimi bitovými kopiemi a zvoleným prostředím nasazení. Pokud je například vaše produkční prostředí Azure Cloud, budete pravděpodobně chtít ukládat obrázky v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, že bude latence sítě minimální. Podobným způsobem, pokud je vaše produkční prostředí v místním prostředí, možná budete mít k dispozici místní přístup k Docker, který je k dispozici ve stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)Další
>[](../net-core-net-framework-containers/index.md)
