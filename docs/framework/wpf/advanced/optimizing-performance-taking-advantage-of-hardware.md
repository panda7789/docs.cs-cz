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
ms.openlocfilehash: eb790da63b4636e3dd6c25ea118075304702acc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimalizace výkonu: Využití výhod hardwaru
Interní architektury portálu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má dva vykreslování kanály, hardwaru a softwaru. Toto téma obsahuje informace o těchto kanálů vykreslování, který vám pomůže provádět rozhodnutí o optimalizací výkonu aplikací.  
  
## <a name="hardware-rendering-pipeline"></a>Hardware vykreslování kanálu  
 Jedním z nejdůležitějších faktory při určení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonu je, že je vázán vykreslení – další pixelů, máte k vykreslení, tím větší výkon náklady. Však může být další vykreslení, který přebírá [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], získají další výhody výkonu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kanálu vykreslování hardwaru aplikace plně využívá [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] funkcí na hardware, který podporuje minimálně [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] verze 7.0. Další optimalizace můžete získávají hardwarem, který podporuje [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] verze 7.0 a PixelShader 2.0 + funkce.  
  
## <a name="software-rendering-pipeline"></a>Software vykreslování kanálu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Softwaru vykreslování kanál je zcela procesoru vázána. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] trvá výhod pokyn SSE a SSE2 nastaví v procesoru k implementaci umožňuje optimalizované, plně vybavený softwaru. Přechod na software je bezproblémové kdykoli funkčnost aplikace nemůže být vykreslen pomocí kanálu vykreslování hardwaru.  
  
 Největší problémy s výkonem můžete narazit při vykreslování v režimu softwaru má vztah k vyplnění míra, která je definována jako počet pixelů, které jsou vykreslování. Pokud máte obavy o výkonu v režimu vykreslování softwaru, zkuste minimalizovat počet, kolikrát bude překreslen pixel. Například pokud máte aplikace s modré pozadí, které se pak vykreslí mírně průhledný obrázek, můžete vykreslí všechny pixelů v aplikaci dvakrát. V důsledku toho bude trvat dvakrát, pokud k vykreslení aplikace s bitovou kopií, než kdybyste pouze modré pozadí.  
  
### <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky  
 To může být velmi obtížné předpovědi v konfiguraci hardwaru, který vaše aplikace bude spuštěna v. Můžete ale chtít zvažte návrh, který umožňuje bezproblémově přepínač funkcí při spuštění na jiný hardware, tak, aby ho mohou využít výhod každý jiný hardware konfigurace vaší aplikace.  
  
 K tomuto účelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje funkce k určení schopností grafika systému za běhu. Funkce grafika je určen podle grafická karta jako jeden z tři vykreslování vrstev schopnosti kategorizaci. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpřístupní [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] aplikace k dotazování vrstvě vykreslování schopností, který umožňuje. Aplikace pak může trvat cesty jiný kódu v době běhu v závislosti na úrovni vykreslování hardwarem podporovanou.  
  
 Funkce hardwaru grafiky, aby většina vliv úrovně vrstvy vykreslování, jsou:  
  
-   **Video RAM** množství grafické paměti v grafickém hardwaru Určuje velikost a počet vyrovnávacích pamětí, které lze použít pro grafiky skládání.  
  
-   **Pixelů shaderu** je shaderu pixelů grafiky, zpracování funkce, která vypočítá účinky na základě za pixelů. V závislosti na řešení zobrazené grafiky může být několik mil. pixelů, které je třeba zpracovat pro každý snímek zobrazení.  
  
-   **Vrchol shaderu** vrchol shaderu je grafiky, funkce, která provádí matematické operace vrchol data objektu zpracování.  
  
-   **Podpora násobnou** násobnou podporu odkazuje na možnost použít dvě nebo více jedinečných textury během prolnutí operace u objektu 3D grafický. Stupeň multitexture podpory je určen podle počet multitexture jednotek na grafickém hardwaru.  
  
 Shaderu pixelů, vrchol shaderu a multitexture funkcí se používá k definování konkrétní [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] verze úrovně, které se pak slouží k definování různých vykreslování vrstvy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Funkce hardwaru grafiky určit možnosti vykreslování produktu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systému definuje vykreslování vrstev:  
  
-   **Vykreslování vrstvy 0** žádné grafiky hardwarovou akceleraci. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je nižší než verze 7.0.  
  
-   **Vykreslování vrstvy 1** částečné grafiky hardwarovou akceleraci. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úroveň verze je větší než nebo rovna hodnotě verze 7.0, a **menší** než verze 9.0.  
  
-   **Vykreslování vrstva 2** většinu funkcí grafiky použít hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovno verze 9.0.  
  
 Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování vrstev, najdete v části [vrstev vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
