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
# <a name="docker-containers-images-and-registries"></a>Kontejnery dockeru, obrázky a registry

Pokud používáte Docker, vytvoříte aplikace nebo služby a balíček a jeho závislosti do image kontejneru. Bitovou je statických reprezentace aplikace nebo služby a jeho konfiguraci a závislostech.

Ke spuštění aplikace nebo služby, je vytvořena instance aplikace image k vytvoření kontejneru, který bude spuštěn na hostitele Dockeru. Kontejnery jsou zpočátku testovat ve vývojovém prostředí nebo PC.

Ukládání imagí v registru, který se chová jako knihovna obrázků. Budete potřebovat registru při nasazení do produkčního prostředí orchestrátorů. Udržuje prostřednictvím veřejného registru docker [Docker Hubu](https://hub.docker.com/); ostatní dodavatelé poskytují registrů pro různé kolekce imagí. Alternativně můžete podniky mají privátního registru on-premises pro vlastní Image Dockeru.

Obrázek 1 – 4 zobrazuje obrázky a registry v Dockeru vztah k jiné komponenty. Také ukazuje několik nabídek registru od dodavatelů.

![](./media/image4.png)

Obrázek 1 – 4: Taxonomie služby Docker terminologie a koncepty

Vložením imagí v registru můžete ukládat bits statické a neměnné aplikace, včetně všechny závislé na úrovni rozhraní framework. Můžete pak můžete verzí a nasazení bitových kopií v různých prostředích a proto poskytují jednotku, konzistentní nasazování.

Privátní image registrů, hostovaný místně nebo v cloudu, se doporučuje v následujících scénářích:

-   Bitové kopie nesmí veřejně sdílené z důvodu důvěrnost.

-   Chcete mít minimální latence mezi vašich imagí a prostředí pro vybrané nasazení. Například pokud vaše produkční prostředí Azure, pravděpodobně chcete ukládat Image ve službě Azure Container Registry, aby se bude minimální latence sítě. Podobným způsobem Pokud je v místním prostředí produkčního prostředí můžete chtít mít místní Docker Trusted Registry k dispozici v rámci stejné místní síti.

>[!div class="step-by-step"]
>[Předchozí](docker-terminology.md)
>[další](road-to-modern-applications-based-on-containers.md)
