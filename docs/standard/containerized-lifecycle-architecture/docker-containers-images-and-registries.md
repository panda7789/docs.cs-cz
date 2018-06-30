---
title: Docker kontejnery, Image a registry
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ff5a1f3e4b09ac9f7ea600d3f127523b96fcce55
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106360"
---
# <a name="docker-containers-images-and-registries"></a>Docker kontejnery, Image a registry

Když pomocí Docker, můžete vytvořit aplikaci nebo službu a balíček je a jeho závislosti do bitové kopie kontejneru. Obrázek je statický reprezentace aplikace nebo služby a jeho konfigurace a závislostí.

Ke spuštění aplikace nebo služby, je vytvořit vytvořit kontejner, který bude spuštěn na hostiteli Docker instance image aplikace. Kontejnery jsou původně testovány v prostředí pro vývoj nebo počítači.

Ukládání imagí v registru, která funguje jako knihovny obrázků. Při nasazení v produkčním orchestrators musíte registru. Docker udržuje veřejné registru prostřednictvím [úložiště Docker Hub](https://hub.docker.com/); jiných dodavatelů registrech poskytovat pro různé kolekce obrázků. Alternativně můžete podniků má privátní registru on-premises pro své vlastní imagí Dockeru.

Obrázek 1 – 4 ukazuje, jak bitové kopie a registrech v Docker vztahují k ostatní součásti. Také ukazuje několik registru nabídky od dodavatelů.

![](./media/image4.png)

Obrázek 1 – 4: taxonomii Docker podmínky a koncepty

Vložením bitové kopie v registru můžete ukládat aplikace statické a neměnné bits, včetně všech jejich závislosti na úrovni framework. Budete pak můžete verze a nasazení bitových kopií v prostředí s více a proto poskytují jednotky konzistentní nasazení.

Privátní image registrech hostovaný místně nebo v cloudu se doporučují pro následující případy:

-   Bitové kopie nesmí veřejně sdílené z důvodu utajení.

-   Chcete mít minimální latenci mezi vaší bitové kopie a prostředí pro vybrané nasazení. Například pokud produkční prostředí Azure, pravděpodobně chcete ukládat obrázků v registru kontejner Azure tak, aby latence sítě bude minimální. Podobným způsobem Pokud provozním prostředí je na místě, můžete chtít mít místní Docker důvěryhodné registru k dispozici v rámci stejné místní síti.

>[!div class="step-by-step"]
[Předchozí](docker-terminology.md)
[další](Docker-application-lifecycle/index.md)
