---
title: "Přehled panelů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d25c6d9e4e6d067ad2107df2374329d84300c015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="panels-overview"></a>Přehled panelů
<xref:System.Windows.Controls.Panel>elementy jsou komponenty, které řídí vykreslování elementů – jejich velikost a dimenzí, jejich umístění a uspořádání obsahu jejich podřízené. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Poskytuje řadu předdefinovaných <xref:System.Windows.Controls.Panel> elementy a také možnost vytvořit vlastní <xref:System.Windows.Controls.Panel> elementy.  
  
 Toto téma obsahuje následující části.  
  
-   [Panel – třída](#Panels_view_from_10000_feet)  
  
-   [Panel prvek běžné členy](#Panels_declared_members)  
  
-   [Prvky odvozené panelů](#Panels_derived_elements)  
  
-   [Panely uživatelského rozhraní](#Panels_main_UI_elements)  
  
-   [Vnořené panely elementy](#Panels_nested_panel_elements)  
  
-   [Vlastní panely elementy](#Panels_custom_panel_elements)  
  
-   [Podpora lokalizace/globalizace](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Panel – třída  
 <xref:System.Windows.Controls.Panel>je základní třída pro všechny elementy, které poskytují rozložení podporovat v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Odvozené <xref:System.Windows.Controls.Panel> prvky se používají k pozice a uspořádat prvky v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kód.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zahrnuje komplexní sadu implementací odvozené panely, které povolit mnoho složitých rozložení. Tyto odvozené třídy vystavit vlastnosti a metody, které umožní většina standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře. Vývojáři, kteří se nepodařilo najít chování uspořádání podřízených, který jim vyhovuje můžete vytvořit nové rozložení přepsáním <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Další informace o chování vlastní rozložení najdete v tématu [vlastní elementy panely](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel běžné členy  
 Všechny <xref:System.Windows.Controls.Panel> elementy podporují základní změny velikosti a rozmístění vlastnosti definované <xref:System.Windows.FrameworkElement>, včetně <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Další informace o vlastnosti definované umístění <xref:System.Windows.FrameworkElement>, najdete v části [zarovnání, okraje a odsazení přehled](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>zpřístupní další vlastnosti, které jsou velmi důležité vysvětlující Princip fungování a pomocí rozložení. <xref:System.Windows.Controls.Panel.Background%2A> Vlastnost se používá k vyplnění oblasti mezi hranice odvozené panel prvek s <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A>představuje kolekci podřízených elementů, <xref:System.Windows.Controls.Panel> se skládá z. <xref:System.Windows.Controls.Panel.InternalChildren%2A>reprezentuje obsah <xref:System.Windows.Controls.Panel.Children%2A> kolekce plus těmto členům generované datové vazby. Skládají ze <xref:System.Windows.Controls.UIElementCollection> podřízených elementů hostovaným v rámci nadřazeného <xref:System.Windows.Controls.Panel>.  
  
 Panelu taky zpřístupňuje <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> přidružená vlastnost, která lze použít k dosažení vrstveného pořadí v odvozené <xref:System.Windows.Controls.Panel>. Členy panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce s vyšším <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnota zobrazí před akcemi s nižší <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnotu. To je užitečné zejména pro panelů jako <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.Grid> které umožňují sdílet stejnou souřadnicového prostoru podřízené objekty.  
  
 <xref:System.Windows.Controls.Panel>Definuje také <xref:System.Windows.Controls.Panel.OnRender%2A> metodu, která je možné přepsat výchozí chování prezentace <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Prvky odvozené panelů využívají rozsáhlé přidružené vlastnosti. – Přidružená vlastnost je specializovaná forma vlastnost závislosti, který nemá konvenční [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost "obálku". Přidružené vlastnosti mít speciální syntaxe v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], který si můžete prohlédnout ve několik příkladů, které následují.  
  
 Jediný účel přidružená vlastnost je umožnit podřízené elementy pro uložení jedinečné hodnoty vlastnosti, která je ve skutečnosti definován nadřazený element. Aplikace tato funkce má nadřazený informovat, jak si přejí uvedené v podřízených elementů [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], což je velmi užitečné pro rozložení aplikace. Další informace najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Prvky odvozené panelů  
 Mnoho objektů jsou odvozeny od <xref:System.Windows.Controls.Panel>, ale ne všechny z nich jsou určeny k použití jako poskytovatelé kořenové rozložení. Existují šest tříd definovaných panel (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, a <xref:System.Windows.Controls.WrapPanel>) určené pro vytvoření aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Každý panel prvek zapouzdří vlastní speciální funkce, jak je vidět v následující tabulce.  
  
|Název elementu|Panely uživatelského rozhraní?|Popis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Ano|Definuje oblast, ve kterém můžete explicitně umístit podřízené elementy souřadnicích vzhledem k <xref:System.Windows.Controls.Canvas> oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Ano|Definuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně k sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Ano|Definuje flexibilní mřížky oblast, který se skládá z sloupců a řádků. Podřízených elementů <xref:System.Windows.Controls.Grid> může být umístěný přesněji pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.|  
|<xref:System.Windows.Controls.StackPanel>|Ano|Podřízené elementy jsou uspořádány jeden řádek, který může být orientované vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Ne|Zpracovává rozložení Karta tlačítka v <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Ne|Uspořádá obsahu v rámci <xref:System.Windows.Controls.ToolBar> ovládacího prvku.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Ne|<xref:System.Windows.Controls.Primitives.UniformGrid>slouží k uspořádání podřízené položky v mřížce s všech velikostí rovna buňky.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Ne|Poskytuje základní třídu pro panely, které můžete "virtualizace" jejich podřízené kolekce.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Ano|Uspořádá a Virtualizuje obsah na jeden řádek zaměřené na konkrétní vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.WrapPanel>|Ano|<xref:System.Windows.Controls.WrapPanel>umisťuje podřízených elementů v sekvenčních pozici zleva doprava, nejnovější obsah na další řádek na hranici obsahujícího pole. Následné řazení se stane postupně shora dolů nebo zprava doleva, v závislosti na hodnotě <xref:System.Windows.Controls.WrapPanel.Orientation%2A> vlastnost.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panely uživatelského rozhraní  
 Nejsou k dispozici v šesti třídy panely [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , jsou optimalizované pro podporu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, a <xref:System.Windows.Controls.WrapPanel>. Tyto prvky panel se snadno použitelný, univerzální a dostatečně extensible pro většinu aplikací.  
  
 Všechny odvozené <xref:System.Windows.Controls.Panel> element zpracovává omezení velikosti odlišně. Pochopení jak <xref:System.Windows.Controls.Panel> omezení obslužných rutin v vodorovné nebo svislé směru může stát rozložení předvídatelnější.  
  
|**Název panelu**|**Dimenze x**|**y dimenze**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Omezená na obsah|Omezená na obsah|  
|<xref:System.Windows.Controls.DockPanel>|Omezené|Omezené|  
|<xref:System.Windows.Controls.StackPanel>(Vertikální orientace)|Omezené|Omezená na obsah|  
|<xref:System.Windows.Controls.StackPanel>(Vodorovné orientaci)|Omezená na obsah|Omezené|  
|<xref:System.Windows.Controls.Grid>|Omezené|Omezené, s výjimkou případů, kdy <xref:System.Windows.GridUnitType.Auto> týkají řádků a sloupců|  
|<xref:System.Windows.Controls.WrapPanel>|Omezená na obsah|Omezená na obsah|  
  
 Podrobnější popisy a příklady použití každé z těchto elementů naleznete níže.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Plátno  
 <xref:System.Windows.Controls.Canvas> Prvek umožní umístění obsahu na základě absolutní *x -* a *y -*souřadnice. Elementy lze rozlišovat v jedinečné umístění; nebo, pokud elementy zabírají stejné souřadnice, určuje pořadí, ve kterém se zobrazí v značek pořadí, ve kterém jsou vykreslovány elementy.  
  
 <xref:System.Windows.Controls.Canvas>poskytuje flexibilní podporu rozložení všech <xref:System.Windows.Controls.Panel>. Vlastností výšky a šířky slouží k určení oblasti na plátno a elementy uvnitř přiřazené absolutní souřadnicích relativních k oblasti nadřazené <xref:System.Windows.Controls.Canvas>. Čtyři přidružené vlastnosti, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, povolit jemné řízení umístění objektu v rámci <xref:System.Windows.Controls.Canvas>, vývojáři je pozice a uspořádat prvky přesněji na obrazovce.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds v rámci na plátno  
 <xref:System.Windows.Controls.Canvas>podřízené prvky lze umístit na všechny pozici na obrazovce, i na souřadnice, které jsou mimo svůj vlastní definované <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A>. Kromě toho <xref:System.Windows.Controls.Canvas> nemá vliv velikost jeho podřízených položek. V důsledku toho je možné pro podřízený element pro overdraw další prvky mimo ohraničující obdélník nadřazené <xref:System.Windows.Controls.Canvas>. Výchozí chování <xref:System.Windows.Controls.Canvas> je umožnit podřízené objekty, které se mají vykreslovat mimo hranice nadřazené <xref:System.Windows.Controls.Canvas>. Pokud je toto chování žádoucí, <xref:System.Windows.UIElement.ClipToBounds%2A> může být nastavena `true`. To způsobí, že <xref:System.Windows.Controls.Canvas> klip vlastní velikost. <xref:System.Windows.Controls.Canvas>je pouze rozložení elementu, který umožňuje podřízené objekty, které se mají vykreslovat mimo jeho hranice.  
  
 Toto chování je graficky ukazuje [šířka vlastnosti porovnání ukázkové](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definování a používání na plátno  
 A <xref:System.Windows.Controls.Canvas> může být vytvořena instance jednoduše pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Canvas> k absolutně umístění obsahu. Tento kód vytvoří tři čtverce 100 pixelů. První hranaté je red a jeho levého horního (*x, y*) pozice je zadána jako (0, 0). Druhý hranaté je zelená a jeho pozice levého horního (100, 100), pod a doprava první buňky. Je třetí hranaté modré a jeho pozice levého horního (50, 50), tedy zahrnující pravém dolním kvadrantu první buňky a levém horním kvadrantu druhý. Protože třetí hranaté rozložená poslední, se zdá, že se nad dva čtverce – to znamená, překrývající se části předpokládají barva třetím poli.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Typické Element Canvas. ] (../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Element používá <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost nastavená na podřízené elementy obsahu na pozici obsah podél okrajů kontejner. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastaven na <xref:System.Windows.Controls.Dock.Top> nebo <xref:System.Windows.Controls.Dock.Bottom>, ho umisťuje podřízené elementy nad nebo pod navzájem. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastaven na <xref:System.Windows.Controls.Dock.Left> nebo <xref:System.Windows.Controls.Dock.Right>, ho umisťuje podřízené elementy vlevo nebo vpravo od sebe navzájem. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Vlastnost určuje pozici konečné přidána jako podřízený element <xref:System.Windows.Controls.DockPanel>.  
  
 Můžete použít <xref:System.Windows.Controls.DockPanel> na pozici skupinu související ovládací prvky, jako je například sadu tlačítek. Alternativně můžete použít k vytvoření a "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobná najít v [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Nastavení velikosti obsahu  
 Pokud jeho <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> nejsou zadané vlastnosti, <xref:System.Windows.Controls.DockPanel> velikosti na jeho obsah. Velikost můžete zvýšit nebo snížit na dokázala pojmout velikost její podřízené elementy. Ale když tyto vlastnosti jsou určené a není již prostor pro další zadaný podřízený element <xref:System.Windows.Controls.DockPanel> nezobrazí tento podřízený element nebo následné podřízené elementy a není měřit následné podřízené elementy.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> element "naplní" zbývající volné místo. Pokud není toto chování žádoucí, nastavte <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> vlastnost `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definování a používání DockPanel  
 Následující příklad ukazuje, jak rozdělit na oddíly pomocí místa <xref:System.Windows.Controls.DockPanel>. Pět <xref:System.Windows.Controls.Border> prvky jsou přidány jako podřízené objekty nadřazený <xref:System.Windows.Controls.DockPanel>. Každá používá jiné umísťovací vlastnost <xref:System.Windows.Controls.DockPanel> do prostoru oddílu. Poslední element "doplní" zbývající, nepřiděleného místa.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Typický scénář DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Mřížka  
 <xref:System.Windows.Controls.Grid> Element sloučí funkce absolutní umístění a tabulkový ovládací prvek. A <xref:System.Windows.Controls.Grid> vám umožňuje snadno elementy pozice a stylu. <xref:System.Windows.Controls.Grid>Umožňuje definovat flexibilní řádků a sloupců seskupení a i poskytuje mechanismus pro sdílejí informace o nastavení velikosti mezi několika <xref:System.Windows.Controls.Grid> elementy.  
  
#### <a name="how-is-grid-different-from-table"></a>Jak se liší mřížky z tabulky?  
 <xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určená pro použití v rámci toku obsahu (najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md) Další informace o toku obsahu). Mřížky jsou nejvhodnější uvnitř forms (v podstatě kamkoli mimo toku obsahu). V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje toku obsahu chování jako stránkování, přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> neexistuje. A <xref:System.Windows.Controls.Grid> na druhé straně je nejvhodnější mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá elementy podle řádků a sloupců index, <xref:System.Windows.Documents.Table> neexistuje. <xref:System.Windows.Controls.Grid> Element umožňuje rozvrstvení podřízené obsahu, povolení více než jeden element existovat v jednom "buňky." <xref:System.Windows.Documents.Table>nepodporuje rozvrstvení. Podřízených elementů <xref:System.Windows.Controls.Grid> možné absolutně umístit relativně k oblasti hranic jejich "buňky". <xref:System.Windows.Documents.Table>Tato funkce není podporována. Nakonec <xref:System.Windows.Controls.Grid> světlejší váhy, než je <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Chování nastavení velikosti řádků a sloupců  
 Sloupce a řádky, které jsou definované v rámci <xref:System.Windows.Controls.Grid> můžete využít výhod <xref:System.Windows.GridUnitType.Star> nastavení velikosti k distribuci úměrně zbývající místo. Když <xref:System.Windows.GridUnitType.Star> je vybrán jako výška nebo šířka řádku nebo sloupce, že sloupec nebo řádek obdrží vyvážené podíl zbývající volné místo. To je rozdíl k <xref:System.Windows.GridUnitType.Auto>, které provede distribuci prostor rovnoměrně založený na velikost obsahu v rámci sloupce nebo řádku. Tato hodnota je vyjádřena jako `*` nebo `2*` při použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. V prvním případě sloupce či řádku by přijímat jeden časy dostupného místa, ve druhém případě dvakrát a tak dále. Tato technika úměrně distribuovat prostor s kombinací <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> hodnota `Stretch` je možné místo rozložení oddílů v procentech místa na obrazovce. <xref:System.Windows.Controls.Grid>je pouze rozložení panelu, můžete distribuovat místo tímto způsobem.  
  
#### <a name="defining-and-using-a-grid"></a>Definování a používání mřížka  
 Následující příklad ukazuje, jak vytvořit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobná nalezeno na dialogu Spustit na k dispozici [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nabídky Start.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Element typické mřížky. ] (../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umožňuje "zásobníku" elementy v přiřazené směru. Výchozí směr zásobníku je svislý. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Vlastnost lze použít k řízení toku obsahu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 I když <xref:System.Windows.Controls.DockPanel> můžete také "zásobníku" podřízené elementy <xref:System.Windows.Controls.DockPanel> a <xref:System.Windows.Controls.StackPanel> neposkytují podobá výsledky v některých scénářích použití. Například pořadí podřízených elementů může ovlivnit jejich velikost v <xref:System.Windows.Controls.DockPanel> , ale ne v <xref:System.Windows.Controls.StackPanel>. Důvodem je, že <xref:System.Windows.Controls.StackPanel> míry ve směru překrývání v <xref:System.Double.PositiveInfinity>, zatímco <xref:System.Windows.Controls.DockPanel> měří pouze dostupné velikosti.  
  
 Následující příklad ukazuje tento klíčovým rozdílem.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Rozdíl v chování vykreslování si můžete prohlédnout ve tuto bitovou kopii.  
  
 ![Snímek obrazovky: StackPanel vs. Snímek obrazovky DockPanel](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definování a používání StackPanel  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.StackPanel> vytvořit sadu svisle umístěný tlačítka. Pro vodorovné umístění, nastavte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Typické StackPanel elementu. ] (../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje varianta <xref:System.Windows.Controls.StackPanel> element, který automaticky "Virtualizuje" obsah podřízené vázané na data. V tomto kontextu slovo Virtualizovat odkazuje na techniku, pomocí kterého se generují podmnožinu elementy větší počet datových položek, které jsou na základě položek, které jsou viditelné na obrazovce. Je náročné, jak z hlediska paměti a procesoru k vygenerování velkého počtu prvky uživatelského rozhraní při jen několik může být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel>(prostřednictvím funkce poskytované službou <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky a funguje s <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ListView>) pouze vytvořit elementů pro položky viditelné.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Element bude automaticky nastavena jako položky hostitele pro ovládací prvky, jako <xref:System.Windows.Controls.ListBox>. Při hostování data vázaná kolekce obsahu je automaticky virtualizované, tak dlouho, dokud je obsah v rámci hranice <xref:System.Windows.Controls.ScrollViewer>. To výrazně zvyšuje výkon při hostování mnoho podřízené položky.  
  
 Následující kód ukazuje, jak používat <xref:System.Windows.Controls.VirtualizingStackPanel> jako hostitele položky. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty%2A?displayProperty=nameWithType> Musí být připojená vlastnost nastavená na `true` (výchozí) pro virtualizaci proběhnout.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>slouží k umístění podřízených elementů v sekvenčních pozici zleva doprava, nejnovější obsah na další řádek, když se dosáhne hrany jeho nadřazený kontejner. Obsah může být orientované vodorovně nebo svisle. <xref:System.Windows.Controls.WrapPanel>je užitečné pro jednoduché předávaných [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře. Ho lze také použít uniform nastavení velikosti pro všechny její podřízené elementy.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.WrapPanel> zobrazíte <xref:System.Windows.Controls.Button> ovládací prvky, které balí po uplynutí hrany jejich kontejneru.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Element typické WrapPanel. ] (../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Vnořené panely elementy  
 <xref:System.Windows.Controls.Panel>prvky můžete začlenit do jiné, aby bylo možné vytvořit komplexní rozložení. To může být velmi užitečné v situacích, kde jeden <xref:System.Windows.Controls.Panel> je ideální pro část [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale nemusí vyhovovat potřebám jinou část [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Neexistuje žádné praktické omezení množství vnoření, kterou vaše aplikace může podporovat, ale obecně je nejvhodnější pro omezení aplikace použít pouze tyto panely, které jsou ve skutečnosti nezbytné pro požadované rozložení. V mnoha případech <xref:System.Windows.Controls.Grid> elementu lze použít místo vnořené panely z důvodu jeho flexibilitu jako kontejner rozložení. To může zvýšit výkon v aplikaci udržováním nepotřebné elementy mimo stromu.  
  
 Následující příklad ukazuje, jak vytvořit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , trvá výhod vnořené <xref:System.Windows.Controls.Panel> elementy, aby bylo možné dosáhnout konkrétní rozložení. V tomto konkrétním případě <xref:System.Windows.Controls.DockPanel> element slouží k poskytování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury a vnořené <xref:System.Windows.Controls.StackPanel> prvky, <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.Canvas> se používají na pozici podřízených elementů přesněji v rámci nadřazeného <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Kompilované aplikace vypočítá nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vypadá podobně jako tento.  
  
 ![Uživatelské rozhraní, které využívá vnořené panely. ] (../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Vlastní panely elementy  
 Při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje pole, flexibilní rozložení ovládacích prvků, vlastní rozložení chování lze také dosáhnout přepsáním <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Vlastní změny velikosti a rozmístění lze provést pomocí definice nové umístění chování v rámci těchto přepsání metody.  
  
 Podobně vlastní rozložení chování na základě odvozených třídách (například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.Grid>) lze definovat přepsáním jejich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
 Následující kód ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.Panel> elementu. Tento nový <xref:System.Windows.Controls.Panel>definovaná jako `PlotPanel`, podporuje umístění podřízených elementů prostřednictvím pevně *x -* a *y -*souřadnice. V tomto příkladu <xref:System.Windows.Shapes.Rectangle> – element (není vidět) je nastavený na vykreslení bodu 50 (*x*) až 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Složitější implementace vlastní panel, naleznete v tématu [vytvořit vlastní obsahu zabalení panely vzorek](http://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Podpora lokalizace/globalizace  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje celou řadu funkcí, které pomáhají při vytváření lokalizovatelný [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Všechny elementy panely nativně podporují <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnosti, která umožňuje dynamicky znovu toku obsahu na základě nastavení národního prostředí a jazyka uživatele. Další informace naleznete v tématu <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Vlastnost poskytuje mechanismus, který umožňuje vývojáři aplikace odhadnout potřeby lokalizované [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pomocí <xref:System.Windows.SizeToContent.WidthAndHeight> hodnota této vlastnosti nadřazené <xref:System.Windows.Window> vždy dynamicky velikosti podle obsahu a není omezené umělé omezení výšky a šířky.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, a <xref:System.Windows.Controls.StackPanel> se všechny velmi dobře hodí lokalizovatelný [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas>je však není vhodná, protože ho umisťuje obsah absolutně, a může ztížit lokalizovat.  
  
 Další informace o vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace s lokalizovatelný [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, najdete v článku [použití automatického rozložení přehled](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Ukázka Galerie rozložení WPF](http://go.microsoft.com/fwlink/?LinkID=160054)  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
 [Ukázka galerie ovládacích prvků grafického subsystému WPF](http://go.microsoft.com/fwlink/?LinkID=160053)  
 [Přehled zarovnání, okrajů a odsazení](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Vytvořit vlastní vzorek panely obsah zabalení](http://go.microsoft.com/fwlink/?LinkID=159979)  
 [Přehled přidružených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Přehled automatického rozložení](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
