---
title: "Model vláken inkoustu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8eb0cf9f1cbb1be688f228b7bbd10a3a3ca6ed0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="the-ink-threading-model"></a>Model vláken inkoustu
Jednou z výhod rukopisu v Tablet PC je, že ho dojem mnoho zápis s regulární pera a dokumentu.  K tomu, shromažďuje pera vstupní data mnohem vyšší rychlostí než myš nemá a vykreslí rukopisu jako uživatelské zápisy.  Aplikace uživatelské rozhraní (UI) vlákno není dostatečná pro shromažďování dat pera a vykreslování rukopisu, protože se zablokuje.  K řešení, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používá dva další vlákna, pokud uživatel zapíše rukopisu.  
  
 Následující seznam popisuje vláken, která účastnit shromažďování a vykreslování digitální rukopisu:  
  
-   Vlákno pera - podproces, který přebírá vstup z pera.  (Ve skutečnosti jde fondu vláken, ale toto téma se označuje jako podproces pera.)  
  
-   Aplikace uživatelské rozhraní vlákno - vlákno, které řídí uživatelské rozhraní aplikace.  
  
-   Dynamické vykreslování vlákno - vláken, který vykreslí element ink při uživatele nevykresluje tah. Dynamické vykreslování vlákno se liší od vláken, který vykreslí další prvky uživatelského rozhraní pro aplikace, jak je uvedeno v okně Presentation Foundation [Model podprocesů](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
 Model rukopisu je stejný, ať aplikace používá <xref:System.Windows.Controls.InkCanvas> nebo vlastního ovládacího prvku podobnou té v [vytvoření ovládacího prvku rukopisu vstup](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  I když toto téma popisuje dělení na vlákna z hlediska <xref:System.Windows.Controls.InkCanvas>, koncepty použity při vytváření vlastního ovládacího prvku.  
  
## <a name="threading-overview"></a>Dělení na vlákna – přehled  
 Následující obrázek znázorňuje model podprocesů, pokud uživatel nevykresluje tahu:  
  
 ![Model vláken při kreslení tahu. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  Akce, ke kterým dochází, když uživatel nevykresluje tahu  
  
    1.  Když uživatel nakreslí tah, pera body mají ve vlákně pera.  Pera moduly plug-in, včetně <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>přijměte body pera ve vlákně pera a máte možnost upravit je před <xref:System.Windows.Controls.InkCanvas> je obdrží.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vykreslí body pera ve vlákně dynamické vykreslování. K tomu dochází ve stejnou dobu jako v předchozím kroku.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> Obdrží pera bodů ve vlákně UI.  
  
2.  Akce, ke kterým dochází po skončení tahu uživatele  
  
    1.  Pokud uživatel dokončí kreslení tahu, <xref:System.Windows.Controls.InkCanvas> vytvoří <xref:System.Windows.Ink.Stroke> objektu a přidává ji k <xref:System.Windows.Controls.InkPresenter>, který staticky vykreslí.  
  
    2.  Výstrahy vlákna uživatelského rozhraní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vykreslený tahu staticky, proto <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odebere jeho vizuální znázornění tahu.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Rozpoznávání rukopisu a moduly plug-in pera  
 Každý <xref:System.Windows.UIElement> má <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Objekty v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> přijímat a můžete upravit body pera ve vlákně pera. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Obdrží objekty pera body podle jejich pořadí v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Následující diagram znázorňuje hypotetické situaci kde <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce <xref:System.Windows.UIElement> obsahuje `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, a `stylusPlugin2`, v tomto pořadí.  
  
 ![Pořadí modulů plug-in pera vliv výstup. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Na předchozím obrázku toto chování probíhá:  
  
1.  `StylusPlugin1`změní hodnoty x a y.  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>obdrží bodů upravené pera a vykreslí je ve vlákně dynamické vykreslování.  
  
3.  `StylusPlugin2`obdrží bodů upravené pera a další upraví hodnoty x a y.  
  
4.  Aplikace shromažďuje body pera a když uživatel dokončí tahu, staticky vykreslí tahu.  
  
 Předpokládat, že `stylusPlugin1` omezuje body pera obdélníku a `stylusPlugin2` překládá body pera vpravo.  V předchozím scénáři <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obdrží body s omezeným přístupem pera, ale není přeložený pera body.  Když uživatel nakreslí tahu, tahu je vykreslen v rámci hranice rámeček, ale k převodu, dokud uživatel zruší pera se nezobrazí tahu.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Provádění operací pomocí modulu Plug-in ve vlákně UI pera  
 Protože přesné testování podle nelze provést na vlákno pera, některé prvky může občas zobrazit pera vstup určený pro další prvky. Pokud potřebujete nasměruje vstupu byla správně před provedením operace, přihlášení k odběru a proveďte operaci v <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, nebo <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> metoda. Tyto metody jsou vyvolány vlákno aplikace po přesné testování podle byla provedena. K odběru těchto metod, volání <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> metoda v metodě proběhne pera vlákno.  
  
 Následující diagram znázorňuje vztah mezi vlákno pera a vlákna uživatelského rozhraní s ohledem na události pera <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Ink modely vláken u &#40; Uživatelské rozhraní a pera &#41; ] (../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Vykreslování rukopisu  
 Jako uživatel nevykresluje tah, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vykreslí rukopisu v samostatných vlákna tak rukopisu se zobrazí "tok" mezi pera i v případě, že vlákna uživatelského rozhraní je zaneprázdněný.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vizuálním stromu vychází vlákno dynamické vykreslování jako shromáždí pera body.  Po dokončení tahu, uživatel <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> požádá chcete být upozorněni, když aplikace nemá další průchodu vykreslování.  Po dokončení další průchodu vykreslování, aplikace <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vyčistí jeho vizuálním stromu.  Následující diagram znázorňuje tento proces.  
  
 ![Dělení na vlákna diagram rukopisu](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  Uživatel začne tahu.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vytvoří vizuálním stromu.  
  
2.  Uživatel je kreslení tahu.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Sestavení vizuálním stromu.  
  
3.  Uživatel ukončí tahu.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Přidá tahu do jeho vizuálním stromu.  
  
    2.  Vrstva integrace média (MIL) staticky vykreslí tahy.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vyčistí vizuálech.
