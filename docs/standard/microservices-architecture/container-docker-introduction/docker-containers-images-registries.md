---
title: Registry, image a kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Kontejnery dockeru, obrázky a registry
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639911"
---
# <a name="docker-containers-images-and-registries"></a>Registry, image a kontejnery Dockeru

Při použití Dockeru, vytvoří vývojář aplikace nebo služby a balíčky a jeho závislosti do image kontejneru. Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.

Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru. Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.

Vývojáři by měly ukládat Image v registru, který funguje jako knihovny imagí a je potřeba při nasazení do produkčního prostředí orchestrátorů. Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.

Obrázek 2 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty. Také ukazuje několik nabídek registru od dodavatelů.

![Základní taxonomie v Dockeru: Registr je stejně jako bookshelf kde Image jsou uložené a k dispozici i pro vytváření kontejnerů ke spuštění služeb nebo webových aplikací. Existují privátní Docker registry v místním prostředí a ve veřejném cloudu. Docker Hubu je že veřejného registru udržuje Dockeru, podél Docker Trusted Registry podnikové řešení že Azure nabízí Azure Container Registry. AWS, Google a dalších také mít registry kontejnerů.](./media/image5.PNG)

**Obrázek 2 – 4**. Taxonomie služby Docker terminologie a koncepty

Vložení imagí v registru umožňuje ukládat bits statické a neměnné aplikace, včetně všech jeho závislostí na úrovni rozhraní framework. Tyto Image můžete pak se systémovou správou verzí a nasazených v různých prostředích a proto poskytují jednotku, konzistentní nasazování.

Privátní image registrů, buď hostovaný místně nebo v cloudu, se doporučuje při:

- Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.

- Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení. Například pokud vaše produkční prostředí cloudu Azure, pravděpodobně chcete ukládat Image v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, že bude minimální latence sítě. Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)
>[další](../net-core-net-framework-containers/index.md)
