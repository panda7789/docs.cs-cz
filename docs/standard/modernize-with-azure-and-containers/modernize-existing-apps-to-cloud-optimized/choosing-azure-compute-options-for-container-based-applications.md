---
title: Výběr platformy výpočtů Azure pro aplikace založené na kontejneru
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Výběr platformy výpočtů Azure pro aplikace založené na kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Výběr platformy výpočtů Azure pro aplikace založené na kontejneru

Jste si všimli po přečtení předchozí části, je Azure otevřete cloudu, která nabízí více možností. Můžete použít bude nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o jaké produkt nebo technologii byste měli použít pro kontejnerové aplikace.

Jako *výchozím* doporučení, toto je hlavní kritéria doporučení v tomto návodu:

  - **Jedna monolitický aplikace:** zvolte Azure App Service
  - **Vícevrstvé aplikace:** orchestrators například Azure Kubernetes služby (AKS), Service Fabric n nebo služby App Service zvolte, pokud máte jeden nebo několik back endové služby
  - **Linux mikroslužeb:** zvolte AKS/Kubernetes
  - **Windows mikroslužeb:** zvolte Service Fabric
  - **Bez serveru funkce & obslužné rutiny událostí:** zvolte Azure Functions
  - **Ve velkém měřítku Batch:** zvolte Azure Batch

Toto doporučení však by měla být provedena s roztahováním salt, protože produktu výběr bude záviset na konkrétní aplikaci požadavky a vlastnosti. Ne všechny aplikace jsou stejné i v případě začátku může vypadat podobně jako typy.

Po dokončení hlubší analýzy potřebám aplikace může být produktu vybrané jiné. Ale, jako výchozí bod, je vhodné mít počáteční pokyny, ze které můžete spustit vyhodnocování a testování podle určité priority.

V následující obrázek můžete analyzovat více globální při podrobné rozhodovací tabulky.

![](./media/image8.5.png)

Všimněte si jak základní operační systém (Windows vs. Linux) může být také rozhodnutí faktor jsou některé orchestrators vyspělá kontejnerům Linux a dalších kontejnerům systému Windows. Pro instanci kontejnery Linux jsou velmi vyspělá v Kubernetes (AKS v Azure) ale méně vyspělá v Service Fabric. Na druhé straně kontejnery Windows jsou víc vyspělých v Service Fabric (vydané v květnu 2017) a méně vyspělá v AKS.

Ale tyto rozdíly v dospělosti operačního systému bude v budoucnu objevovat a více platforem budou mít porovnatelný z hlediska vyspělosti operačního systému a rozhodnutí budou obsahovat další informace o předvolby podle konkrétních příznaků, může být nutné aplikaci nebo v závislosti na každou platformu ekosystém z důvodů.


>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
