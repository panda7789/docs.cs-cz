---
title: 'Optimalizace výkonu: Využití výhod hardwaru'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 13812fa5429bbe33341e51e4b3be14fbbcb361cb
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238454"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimalizace výkonu: Využití výhod hardwaru
Interní architektury portálu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má dvě vykreslování kanály, hardware a software. Toto téma obsahuje informace o těchto kanálech vykreslování můžete rozhodovat o optimalizaci výkonu vašich aplikací.  
  
## <a name="hardware-rendering-pipeline"></a>Kanál hardwarového vykreslení  
 Jedním z nejdůležitějších faktorů při určování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonu je, že se jedná o vykreslování vázán – více pixelů, je nutné vykreslit, tím větší výkon, náklady. Však můžete více vykreslování, která přebírá [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], můžete získat více výhod výkonu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aplikací kanál hardwarového vykreslení plně využívá [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] funkcí na hardwaru, který podporuje alespoň [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] verze 7.0. Další optimalizace může být díky hardwaru, který podporuje [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] verze 7.0 a u objektu Shadereffect 2.0 + funkce.  
  
## <a name="software-rendering-pipeline"></a>Kanál softwarového vykreslení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kanál softwarového vykreslení je zcela závislá na procesoru. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] využívá registrů instrukce SSE a SSE2 nastaví v procesoru pro implementaci rasterizéru optimalizovaný, plně funkční software. Nouzového řešení ověření pomocí softwaru je bezproblémové pokaždé, když funkčnost aplikace nemůže být vykreslen pomocí kanál hardwarového vykreslení.  
  
 Největším problémem výkonu můžete narazit při vykreslování v režimu software má vztah k vyplnění sazba, která je definována jako počet pixelů, které jsou vykreslování. Pokud máte obavy o výkonu v režimu vykreslování software, zkuste minimalizovat počet pokusů, které se překreslí pixel. Například pokud máte aplikace s modrým pozadím, který pak vykreslí mírně průhledný obrázek nad ním, můžete se vykreslit všechny pixely aplikace dvakrát. Díky tomu bude trvat dvakrát tak dlouho k vykreslení aplikace s imagí, než kdybyste pouze modré pozadí.  
  
### <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky  
 Může být velmi obtížné odhadnout, vaše aplikace poběží na konfiguraci hardwaru. Můžete však chtít zvažte návrh, který umožňuje vaší aplikaci bez problémů přepínač funkce při spuštění na jiný hardware, tak, aby ho využívat všech výhod každou konfiguraci jiný hardware.  
  
 Chcete-li toho dosáhnout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje funkce určující grafické možnosti systému v době běhu. Grafické možnosti se určuje podle kategorizace grafická karta jako jeden ze tří vykreslování funkce úrovně. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpřístupňuje rozhraní API, které umožňuje aplikaci k dotazování na úrovni funkce vykreslování. Aplikace pak můžou cesty odlišný kód za běhu v závislosti na úrovni vykreslování podporovaný hardware.  
  
 Funkce, že mají největší dopad na úrovně vrstvy vykreslování grafiky hardware patří:  
  
- **Video RAM** množství grafické paměti na hardwarovou akceleraci Určuje velikost a počet vyrovnávacích pamětí, které lze použít pro skládání grafiky.  
  
- **Pixel Shader** pixel shader je grafických funkce, která vypočítá účinky na základě jednotlivých pixelů. V závislosti na řešení zobrazených grafiky může být několik milionů pixelů, které potřebují ke zpracování pro každý snímek pro zobrazení.  
  
- **Vertex Shader** vertex shader je grafických funkce, která provádí matematických operací s daty vrcholu objektu.  
  
- **Podpora násobnou** násobnou podporu odkazuje na možnost použít dva nebo více jedinečných textury během prolnutí operace u objektu 3D grafiky. Stupeň multitexture podpory se určuje podle počtu jednotek multitexture na hardwarovou akceleraci.  
  
 Pixel shader, vertex shaderu a multitexture funkce se používají k definování zvláštní [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] úrovně, verze, která zase slouží k určení vrstvy různých vykreslování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Funkce hardwarovou akceleraci definují možností vykreslování objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systém definuje tři vrstvy vykreslování:  
  
- **Vykreslování vrstvy 0** žádné hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je starší než verze 7.0.  
  
- **Vykreslování vrstvy 1** hardwarovou akceleraci grafiky částečné. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovna verzi 7.0, a **menší** než verze 9.0.  
  
- **Vykreslování vrstva 2** většinu funkcí grafiky použít hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovna verzi 9.0.  
  
 Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování úrovně, naleznete v tématu [vrstvy vykreslování grafiky](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
