---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758829"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Volba výpočetních platforem Azure pro aplikace založené na kontejnerech

Protože jste si všimli po přečtení v předchozích částech, Azure je otevřete cloud, který nabízí více možností. Můžete použít nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o tom, jaký produkt/technologie byste měli použít pro své kontejnerizované aplikace.

Jako *výchozím* doporučení, tady je hlavním kritériem doporučení v tomto dokumentu:

- **Monolitické aplikace s jedním:** Zvolte Azure App Service
- **N-vrstvé aplikace:** Pokud máte jednu nebo několik back endovým službám, zvolte orchestrátorů, jako je Azure Kubernetes Service (AKS) nebo služby App Service
- **Mikroslužby Linux:** Zvolte AKS/Kubernetes
- **Mikroslužby Windows:** Zvolte Azure Web Apps for Containers
- **Funkce bez serveru a obslužné rutiny události:** Zvolte Azure Functions
- **Ve velkém měřítku Batch:** Zvolte Azure Batch

Toto doporučení by však provést s roztažením o hodnota salt, jako výběr produktu, bude záviset na konkrétní aplikaci požadavky a vlastnosti. Ne všechny aplikace jsou stejné, i když zpočátku může vypadat podobně jako typy.

Po dokončení hlubší analýzy potřeby aplikace mohou být odlišná vybranému produktu. Ale jako výchozí bod, je dobré si základní pokyny z kde začít, vyhodnocování a testování na základě určitých priority.

Následující obrázek můžete zobrazit rozpis různých druhů aplikací a jejich ideální hostování scénáře Azure.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
