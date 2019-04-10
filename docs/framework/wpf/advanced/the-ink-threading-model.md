---
title: Model vláken inkoustu
ms.date: 03/30/2017
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
ms.openlocfilehash: 80e7ef202c46a23069766512cf4e67bb21a49564
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335313"
---
# <a name="the-ink-threading-model"></a>Model vláken inkoustu
Jednou z výhod rukopis na Tablet PC je, že se zdá mnohem zápis s regulární perem na papír.  K tomu shromažďuje pera vstupní data mnohem vyšší rychlostí než myši nemá a vykreslí rukopis jako uživatelské zápisy.  Vlákně uživatelského rozhraní (UI) aplikace není dostatečná pro shromažďování dat pera a vykreslení inkoustu, protože budou blokované.  K řešení, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace používá dvě další vlákna, když uživatel zapíše rukopisu.  
  
 Následující seznam popisuje vláken, která účastnit shromažďování a vykreslování digitálních inkoust:  
  
-   Vlákno pera - vlákno trvá vstupu z pera.  (Ve skutečnosti jde fondu vláken, ale toto téma se označuje jako vlákno pera.)  
  
-   Vlákno uživatelského rozhraní aplikace - vlákna, která řídí uživatelské rozhraní aplikace.  
  
-   Dynamické vykreslování vlákna - podproces, který vykreslí rukopis zatímco uživatel kreslení tah. Dynamické vykreslování vlákna se liší od vlákna, která vykresluje další prvky uživatelského rozhraní pro aplikace, jak je uvedeno ve Windows Presentation Foundation [Model vláken](threading-model.md).  
  
 Rukopisu modelu je stejný, ať už aplikace používá <xref:System.Windows.Controls.InkCanvas> nebo vlastního ovládacího prvku obrazovku v [vytvoření ovládacího prvku vstupu inkoustu](creating-an-ink-input-control.md).  I když toto téma popisuje dělení na vlákna z hlediska <xref:System.Windows.Controls.InkCanvas>, stejné koncepty platí i při vytváření vlastního ovládacího prvku.  
  
## <a name="threading-overview"></a>Přehled dělení na vlákna  
 Následující obrázek znázorňuje model vláken, pokud uživatel nakreslí tah:  
  
 ![Model vláken při kreslení tah. ](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1. Akce, ke kterým dochází, když uživatel nakreslí tahu  
  
    1.  Až uživatel nakreslí tah, vraťte se stylus body na vlákno pera.  Stylus modulů plug-in, včetně <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>přijměte stylus bodů na vlákno pera a mít možnost upravit je před <xref:System.Windows.Controls.InkCanvas> je obdrží.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vykreslí stylus bodů na dynamické vykreslování vlákna. K tomu dojde ve stejnou dobu jako v předchozím kroku.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> Obdrží stylus bodů na vlákně UI.  
  
2. Akce, ke kterým dochází, až uživatel skončí tahu  
  
    1.  Po dokončení uživatel kreslení tahu <xref:System.Windows.Controls.InkCanvas> vytvoří <xref:System.Windows.Ink.Stroke> objektu a přidá jej do <xref:System.Windows.Controls.InkPresenter>, která staticky vykreslí.  
  
    2.  Upozornění na vlákna uživatelského rozhraní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vykreslený tahu staticky, takže <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odebere jeho vizuální reprezentaci objektu stroke.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Kolekce inkoustů a moduly plug-in pera  
 Každý <xref:System.Windows.UIElement> má <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Objekty v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> přijmout a můžete upravit stylus bodů na vlákno pera. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Objekty přijímat stylus body podle jejich pořadí v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Následující diagram ukazuje hypotetické situace kde <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce <xref:System.Windows.UIElement> obsahuje `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, a `stylusPlugin2`v tomto pořadí.  
  
 ![Pořadí modulů plug-in Stylus vliv výstup. ](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Na předchozím obrázku toto chování probíhá:  
  
1. `StylusPlugin1` změní hodnoty x a y.  
  
2. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obdrží upravené stylus bodů a vykreslí na dynamické vykreslování vlákna.  
  
3. `StylusPlugin2` obdrží upravené stylus bodů a další změní hodnoty x a y.  
  
4. Aplikace shromažďuje stylus body a až se uživatel dokončí tahu staticky vykreslí stroke.  
  
 Předpokládejme, že `stylusPlugin1` omezuje body stylus obdélníku a `stylusPlugin2` přeloží stylus odkazuje na pravé straně.  V předchozím scénáři <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obdrží body stylus s omezeným přístupem, ale ne body přeložené stylus.  Když uživatel nakreslí tahu, tahu se vykreslí v mezích obdélníku, ale tahu nezobrazí k převodu, dokud uživatel zruší pera.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Provádění operací pomocí modulu Plug-in na vlákně UI při pera  
 Protože přesné spuštění testu nemůže být proveden na vlákno pera, některé prvky může čas od času zobrazit tužkou určené pro ostatní prvky. Pokud je potřeba Ujistěte se, že vstup, byla směrována správně před provedením operace, přihlaste se k odběru a operaci v <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, nebo <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> metody. Tyto metody jsou vyvolány vlákna aplikace po provedení přesné spuštění testu. K odběru těchto metod, zavolejte <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> metody do metody, která probíhá na vlákno pera.  
  
 Následující diagram znázorňuje vztah mezi vlákno pera a vlákna uživatelského rozhraní s ohledem na stylus událostí <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Modely vláken rukopisu &#40;uživatelského rozhraní a pera&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Vykreslení inkoustu  
 Jako uživatel nakreslí tah, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vykreslí rukopis na samostatném vlákně, takže inkoustových "tok" z pera i v případě, že je zaneprázdněná vlákna uživatelského rozhraní.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vizuální strom vychází dynamické vykreslování vlákna shromažďuje stylus body.  Když uživatel dokončí tahu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> dotazem, která vás upozorní, když aplikace provádí další pass vykreslování.  Po dokončení další vykreslování průchodu aplikaci <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vyčistí jeho vizuálního stromu.  Následující diagram znázorňuje tento proces.  
  
 ![Práce s vlákny diagram inkoustu](./media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1. Uživatel začne stroke.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vytvoří vizuálního stromu.  
  
2. Uživatel je kreslení stroke.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Sestavení vizuálního stromu.  
  
3. Uživatel končí stroke.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Přidá tahu jeho vizuálního stromu.  
  
    2.  Vrstva integrace média (MIL) staticky vykreslí strokes.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vyčistí vizuály.
