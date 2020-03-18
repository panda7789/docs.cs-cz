---
title: Registry, image a kontejnery Dockeru
description: Seznamte se s klíčovou rolí, kterou registry celkově hrají ve způsobu nasazování aplikací dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: bfef21cab7be89abaf33b89366d7cff2115a7cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72770920"
---
# <a name="docker-containers-images-and-registries"></a>Registry, image a kontejnery Dockeru

Při použití Dockeru vytvoříte aplikaci nebo službu a zabalíte ji a její závislosti do image kontejneru. Bitová kopie je statická reprezentace aplikace nebo služby a její konfigurace a závislostí.

Chcete-li spustit aplikaci nebo službu, image aplikace se vytvoří k vytvoření kontejneru, který bude spuštěn na hostiteli Dockeru. Kontejnery jsou zpočátku testovány ve vývojovém prostředí nebo PC.

Obrázky jsou ukládány do registru, který funguje jako knihovna bitových kopií. Při nasazování do produkčních orchestrátorů potřebujete registr. Docker udržuje veřejný registr přes [Docker Hub](https://hub.docker.com/); jiní dodavatelé poskytují registry pro různé kolekce bitových kopií, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternativně podniky mohou mít soukromý registr místní pro své vlastní image Dockeru.

Obrázek 1-4 ukazuje, jak obrázky a registry v Dockeru souvisejí s jinými součástmi. Zobrazuje také více nabídek registru od dodavatelů.

![Diagram znázorňující základní taxonomii v Dockeru.](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

**Obrázek 1-4**. Taxonomie dockerových termínů a konceptů

Registr je jako knihovna, kde jsou obrázky uloženy a k dispozici pro vytváření kontejnerů pro spouštění služeb nebo webových aplikací. Existují privátní registry Dockeru v místním prostředí a ve veřejném cloudu. Docker Hub je veřejný registr spravovaný Dockerem, podél důvěryhodného registru Dockeru, řešení na podnikové úrovni, Azure nabízí Azure Container Registry. AWS, Google a další mají také kontejnerové registry.

Umístěním bitů do registru můžete ukládat statické a neměnné bity aplikací, včetně všech jejich závislostí, na úrovni architektury. Potom můžete verze a nasazení bitových kopií ve více prostředích a tím poskytují konzistentní nasazení jednotky.

Privátní registry obrázků, hostované místně nebo v cloudu, se doporučují, když:

- Vaše obrázky nesmí být sdíleny veřejně z důvodu důvěrnosti.

- Chcete mít minimální latenci sítě mezi bitovými kopiemi a zvoleným prostředím nasazení. Například pokud vaše produkční prostředí je Azure, pravděpodobně budete chtít uložit vaše image v [registru kontejnerů Azure](https://azure.microsoft.com/services/container-registry/) tak, aby latence sítě je minimální. Podobným způsobem, pokud vaše produkční prostředí je místní, můžete chtít mít místní Docker Trusted Registry k dispozici ve stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)
>[další](road-to-modern-applications-based-on-containers.md)
