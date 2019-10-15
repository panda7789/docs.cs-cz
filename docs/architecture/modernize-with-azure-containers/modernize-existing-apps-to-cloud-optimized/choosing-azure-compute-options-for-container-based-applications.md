---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Výběr platforem Azure COMPUTE pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318669"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Volba výpočetních platforem Azure pro aplikace založené na kontejnerech

Jakmile jste si všimli, že jste si přečetli předchozí části, je Azure otevřeným cloudem, který nabízí víc možností. Pro vaše potřeby můžete použít nejvhodnější, ale také si vyřadíme otázky týkající se produktu nebo technologie, které byste měli použít pro své aplikace v kontejneru.

V rámci *výchozího* doporučení jsou tady uvedená hlavní kritéria, která jsou doporučena v těchto pokynech:

- **Jedna aplikace monolitické:** Zvolit Azure App Service
- **N-vrstvá aplikace:** Vyberte orchestrace, jako je Azure Kubernetes Service (AKS), nebo App Service, pokud máte jednu nebo několik back-endové služeb.
- **Mikroslužby:** Výběr AKS nebo Azure Web Apps pro kontejnery
- **Funkce bez serveru & obslužné rutiny událostí:** Zvolit Azure Functions
- **Velká škála dávek:** Zvolit Azure Batch

Toto doporučení je ale potřeba vzít s gesto roztažení prstůou sůl, protože výběr produktu bude záviset na potřebách a vlastnostech konkrétní aplikace. Ne všechny aplikace jsou stejné, i když zpočátku můžou vypadat podobné typy.

Po hlubší analýze potřeb aplikace může být vybraný produkt jiný. Ale jako výchozí bod je dobré mít počáteční pokyny, ze kterých můžete začít vyhodnocovat a testovat na základě určité priority.

Na obrázku 1 vidíte rozpis různých druhů aplikací a jejich ideální scénáře hostování Azure.

![Obrázek 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
