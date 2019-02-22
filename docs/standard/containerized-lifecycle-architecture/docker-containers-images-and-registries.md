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
# <a name="docker-containers-images-and-registries"></a>Kontejnery dockeru, obrázky a registry

Pokud používáte Docker, vytvoříte aplikace nebo služby a balíček a jeho závislosti do image kontejneru. Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.

Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru. Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.

Ukládání imagí v registru, který funguje jako knihovny imagí. Budete potřebovat registru při nasazení do produkčního prostředí orchestrátorů. Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí, včetně [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.

Obrázek 1 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty. Také ukazuje několik nabídek registru od dodavatelů.

![Základní taxonomie v Dockeru: Registr je stejně jako bookshelf kde Image jsou uložené a k dispozici i pro vytváření kontejnerů ke spuštění služeb nebo webových aplikací. Existují privátní Docker registry místní a ve veřejném cloudu. Docker Hubu je že veřejného registru udržuje Dockeru, podél Docker Trusted Registry podnikové řešení že Azure nabízí Azure Container Registry. AWS, Google a dalších také mít registry kontejnerů.](./media/image4.png)

**Obrázek 1 – 4**. Taxonomie služby Docker terminologie a koncepty

Vložením imagí v registru můžete ukládat bits statické a neměnné aplikace, včetně všechny závislé na úrovni rozhraní framework. Můžete pak můžete verzí a nasazení bitových kopií v různých prostředích a proto poskytují jednotku, konzistentní nasazování.

Privátní image registrů, buď hostovaný místně nebo v cloudu, se doporučuje při:

- Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.

- Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení. Například pokud vaše produkční prostředí Azure, pravděpodobně chcete ukládat Image v [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby byla minimální latence sítě. Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)
>[další](road-to-modern-applications-based-on-containers.md)
