---
title: Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: 20d8899d404ec72e3b1b9c2471524133a6428c44
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125493"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech

Protože jste si všimli po přečtení v předchozích částech, Azure je otevřete cloud, který nabízí více možností. Můžete použít nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o tom, jaký produkt/technologie byste měli použít pro své kontejnerizované aplikace.

Jako *výchozím* doporučení, tady je hlavním kritériem doporučení v tomto dokumentu:

  - **Monolitické aplikace s jedním:** Zvolte Azure App Service
  - **N-vrstvé aplikace:** Pokud máte jednu nebo několik back endovým službám, zvolte orchestrátorů, jako je například Azure Kubernetes Service (AKS), Service Fabric (SF) nebo služby App Service
  - **Mikroslužby Linux:** Zvolte AKS/Kubernetes
  - **Mikroslužby Windows:** Zvolte Service Fabric
  - **Funkce bez serveru a obslužné rutiny události:** Zvolte Azure Functions
  - **Ve velkém měřítku Batch:** Zvolte Azure Batch

Toto doporučení by však provést s roztažením o hodnota salt, jako výběr produktu, bude záviset na konkrétní aplikaci požadavky a vlastnosti. Ne všechny aplikace jsou stejné, i když zpočátku může vypadat podobně jako typy.

Po dokončení hlubší analýzy potřeby aplikace mohou být odlišná vybranému produktu. Ale jako výchozí bod, je dobré si základní pokyny z kde začít, vyhodnocování a testování na základě určitých priority.

Následující obrázek můžete analyzovat více globální při podrobné rozhodovací tabulky.

![](./media/image8.5.png)

Všimněte si, že jak základní operační systém (Windows vs. Linux) může být také faktor rozhodnutí jsou některé zvolené orchestrátory až po zralé kontejnerům Linuxu a dalších v kontejnerech Windows. Například kontejnery Linuxu jsou velmi až po zralé v Kubernetes (AKS v Azure) ale méně až po zralé na platformě Service Fabric. Na druhé straně jsou kontejnery Windows vyspělejší v Service Fabric (vydané spolu. května 2017) a méně až po zralé ve službě AKS.

Však bude v budoucnu fade těchto rozdílů v OS vyspělosti a více platforem budou mít srovnatelné vyspělosti operačního systému a rozhodnutí budou obsahovat další informace o předvolby podle konkrétních příznaků, které vaše aplikace může být nutné nebo založené na každou platformu ekosystém z důvodů.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)