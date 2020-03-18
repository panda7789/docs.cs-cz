---
title: Registry, image a kontejnery Dockeru
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Kontejnery, obrázky a registry dockeru
ms.date: 08/31/2018
ms.openlocfilehash: 3b643a3bf4ca3ce1b8ba3fc40cd2f3ad8bbe5ffb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73737767"
---
# <a name="docker-containers-images-and-registries"></a>Registry, image a kontejnery Dockeru

Při použití Dockeru vývojář vytvoří aplikaci nebo službu a zabalí ji a její závislosti do image kontejneru. Bitová kopie je statická reprezentace aplikace nebo služby a její konfigurace a závislostí.

Chcete-li spustit aplikaci nebo službu, image aplikace se vytvoří k vytvoření kontejneru, který bude spuštěn na hostiteli Dockeru. Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo PC.

Vývojáři by měli ukládat bitové kopie do registru, který funguje jako knihovna bitových kopií a je potřeba při nasazování do produkčních orchestrátorů. Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); jiní dodavatelé poskytují registry pro různé kolekce bitových kopií, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternativně podniky mohou mít soukromý registr místní pro své vlastní image Dockeru.

Obrázek 2-4 ukazuje, jak obrázky a registry v Dockeru souvisejí s jinými součástmi. Zobrazuje také více nabídek registru od dodavatelů.

![Diagram znázorňující základní taxonomii v Dockeru.](./media/docker-containers-images-registries/taxonomy-of-docker-terms-and-concepts.png)

**Obrázek 2-4**. Taxonomie dockerových termínů a konceptů

Registr je jako knihovna, kde jsou obrázky uloženy a k dispozici pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací. Existují privátní registry Dockeru v místním prostředí a ve veřejném cloudu. Docker Hub je veřejný registr spravovaný Dockerem, podél důvěryhodného registru Dockeru, řešení na podnikové úrovni, Azure nabízí Azure Container Registry. AWS, Google a další mají také kontejnerové registry.

Umístění bitů do registru umožňuje ukládat statické a neměnné bity aplikací, včetně všech jejich závislostí na úrovni architektury. Tyto bitové kopie pak mohou být verzí a nasazeny ve více prostředích a proto poskytují konzistentní jednotku nasazení.

Privátní registry obrázků, hostované místně nebo v cloudu, se doporučují, když:

- Vaše obrázky nesmí být sdíleny veřejně z důvodu důvěrnosti.

- Chcete mít minimální latenci sítě mezi bitovými kopiemi a zvoleným prostředím nasazení. Například pokud vaše produkční prostředí je Cloud Azure, pravděpodobně budete chtít uložit image v [registru kontejnerů Azure](https://azure.microsoft.com/services/container-registry/) tak, aby latence sítě bude minimální. Podobným způsobem, pokud vaše produkční prostředí je místní, můžete chtít mít místní Docker Trusted Registry k dispozici ve stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)
>[další](../net-core-net-framework-containers/index.md)
