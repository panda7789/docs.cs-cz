---
title: Přehled panelů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 9bd2af8cd74c32bcda3a6105f39af470f961289d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625715"
---
# <a name="panels-overview"></a>Přehled panelů
<xref:System.Windows.Controls.Panel> prvky jsou komponenty, které řídí vykreslování elementů, jejich velikost a rozměry, jejich pozice a uspořádání jejich podřízený obsah. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Poskytuje řadu předdefinovaných <xref:System.Windows.Controls.Panel> elementy jakož i možnost vytvořit vlastní <xref:System.Windows.Controls.Panel> elementy.  
  
 Toto téma obsahuje následující části.  
  
- [Třídy Panel](#Panels_view_from_10000_feet)  
  
- [Společné členy prvek panel](#Panels_declared_members)  
  
- [Prvky odvozených panelů](#Panels_derived_elements)  
  
- [Panely uživatelského rozhraní](#Panels_main_UI_elements)  
  
- [Panel vnořené elementy](#Panels_nested_panel_elements)  
  
- [Vlastní Panel elementy](#Panels_custom_panel_elements)  
  
- [Podpora lokalizace a globalizace](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Třídy Panel  
 <xref:System.Windows.Controls.Panel> je základní třídou pro všechny prvky, které poskytují rozložení podporu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Odvozené <xref:System.Windows.Controls.Panel> elementy se používají k pozice a uspořádání prvků v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zahrnuje komplexní sadu odvozených panelů implementace, které umožňují mnoho složitá rozložení. Tyto odvozené třídy vystavení vlastností a metod, které umožňují většina standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře. Vývojáři, kteří se nepodařilo najít chování uspořádání podřízených, které vyhovují jejich potřebám, můžete vytvořit nové rozložení tak, že přepíšete <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Další informace o chování vlastní rozložení, naleznete v tématu [vlastní elementy panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel společné členy  
 Všechny <xref:System.Windows.Controls.Panel> prvky podporují základní změny velikosti a polohování vlastnosti určené <xref:System.Windows.FrameworkElement>, včetně <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Další informace o vlastnosti určené umístění <xref:System.Windows.FrameworkElement>, naleznete v tématu [zarovnání, okrajů a odsazení přehled](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> poskytuje další vlastnosti, které jsou velmi důležité vysvětlující Princip fungování a pomocí rozložení. <xref:System.Windows.Controls.Panel.Background%2A> Vlastnost se používá k vyplnění oblasti mezi hranice elementu odvozené panelu s <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> představuje kolekci podřízených prvků, které <xref:System.Windows.Controls.Panel> se skládá z. <xref:System.Windows.Controls.Panel.InternalChildren%2A> reprezentuje obsah <xref:System.Windows.Controls.Panel.Children%2A> kolekce a tyto členy generované datové vazby. Obě jsou tvořeny <xref:System.Windows.Controls.UIElementCollection> z podřízených prvků, které jsou hostované v rámci nadřazené <xref:System.Windows.Controls.Panel>.  
  
 Panel taky zpřístupňuje <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> přidružená vlastnost, která slouží k zajištění vrstveného pořadí v odvozené <xref:System.Windows.Controls.Panel>. Členové panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce s vyšším <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnota zobrazí před těmi, které mají nižší <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnotu. To je užitečné hlavně pro panelů, jako <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.Grid> které umožňují sdílet stejnou souřadnicového prostoru podřízené objekty.  
  
 <xref:System.Windows.Controls.Panel> Definuje také <xref:System.Windows.Controls.Panel.OnRender%2A> metodu, která je možné přepsat výchozí chování prezentace <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Prvky odvozených panelů využívat rozsáhlé připojené vlastnosti. Připojená vlastnost je specializovaná forma vlastnost závislosti, která nemá konvenční [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost "zabezpečenou obálku". Připojené vlastnosti mají speciální syntaxe v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], které si můžete prohlédnout ve několik příkladů, které následují.  
  
 Jediný účel připojené vlastnosti je umožnit podřízené prvky k ukládání jedinečné hodnoty, který je ve skutečnosti definován nadřazený element vlastnosti. Má podřízené prvky nadřazeného informovat, jak chtějí uvedené v aplikaci tuto funkci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], což je velmi užitečné pro rozložení aplikace. Další informace najdete v tématu [přehled připojených vlastností](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Prvky odvozených panelů  
 Mnoho objektů jsou odvozeny z <xref:System.Windows.Controls.Panel>, ale ne všechny z nich jsou určeny k použití jako poskytovatelé kořenové rozložení. Existuje šest tříd definovaných panelu (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, a <xref:System.Windows.Controls.WrapPanel>), které jsou navrženy speciálně pro vytvoření aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Každý prvek panel zapouzdřuje vlastní speciální funkce, jak je znázorněno v následující tabulce.  
  
|Název elementu|Panely uživatelského rozhraní?|Popis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Ano|Vymezuje oblast, ve kterém můžete explicitně umísťovat podřízené prvky podle souřadnic vzhledem k <xref:System.Windows.Controls.Canvas> oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Ano|Vymezuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně vůči sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Ano|Definuje flexibilní oblast mřížky skládající se z sloupců a řádků. Podřízené prvky <xref:System.Windows.Controls.Grid> může být umístěné přesně pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.|  
|<xref:System.Windows.Controls.StackPanel>|Ano|Uspořádává podřízené prvky do jednoho řádku, který může být orientovaný vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Ne|Zpracovává rozložení tlačítek na kartě <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Ne|Uspořádá obsah v rámci <xref:System.Windows.Controls.ToolBar> ovládacího prvku.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Ne|<xref:System.Windows.Controls.Primitives.UniformGrid> umožňuje uspořádat podřízené položky v mřížce se všemi velikostmi rovná buňky.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Ne|Poskytuje základní třídu pro panely, které můžete "virtualizace" jejich podřízené kolekce.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Ano|Uspořádá a Virtualizuje obsah na jednom řádku orientovaný vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.WrapPanel>|Ano|<xref:System.Windows.Controls.WrapPanel> Umísťuje podřízené prvky do sekvenční Pozice zleva doprava, rozdělení obsahu na další řádek na okraji obsahujícího pole. Následné řazení se děje sekvenčně shora dolů nebo zprava doleva, závisí na hodnotě <xref:System.Windows.Controls.WrapPanel.Orientation%2A> vlastnost.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panely uživatelského rozhraní  
 Nejsou dostupné v šesti třídy panel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které jsou optimalizovány pro podporu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, a <xref:System.Windows.Controls.WrapPanel>. Tyto prvky panel se snadno používá, univerzální a dostatečně extensible pro většinu aplikací.  
  
 Každý odvozené <xref:System.Windows.Controls.Panel> element zpracovává omezení velikosti odlišně. Vysvětlení jak <xref:System.Windows.Controls.Panel> omezení obslužné rutiny ve vodorovném nebo svislém směru mohli rozložení předvídatelnější.  
  
|**Název panelu**|**x-Dimension**|**Dimenze y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Omezené na obsah|Omezené na obsah|  
|<xref:System.Windows.Controls.DockPanel>|Omezené|Omezené|  
|<xref:System.Windows.Controls.StackPanel> (Svislé orientaci)|Omezené|Omezené na obsah|  
|<xref:System.Windows.Controls.StackPanel> (Vodorovné orientaci)|Omezené na obsah|Omezené|  
|<xref:System.Windows.Controls.Grid>|Omezené|Omezené, s výjimkou případů, kdy <xref:System.Windows.GridUnitType.Auto> platí pro řádky a sloupce|  
|<xref:System.Windows.Controls.WrapPanel>|Omezené na obsah|Omezené na obsah|  
  
 Podrobnější popisy a příklady použití každé z těchto elementů najdete níže.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Plátno  
 <xref:System.Windows.Controls.Canvas> Element umožňuje umístění obsahu na základě absolutní *x -* a *y -* souřadnice. Elementy mohou vykreslen na jedinečné umístění; nebo, pokud prvky zabírají stejné souřadnice, pořadí, v jakém jsou uvedeny v kódu určuje pořadí, ve kterém jsou vykreslovány vedle prvky.  
  
 <xref:System.Windows.Controls.Canvas> poskytuje flexibilní podporu rozložení žádné <xref:System.Windows.Controls.Panel>. Vlastnosti výšky a šířky se používají k definování oblast na plátně a elementů v rámci jsou přiřazeny absolutní souřadnicích relativních k oblasti nadřazené <xref:System.Windows.Controls.Canvas>. Čtyři připojených vlastností, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, umožnit přesné řízení umístění objektu v rámci <xref:System.Windows.Controls.Canvas>, umožňuje vývojářům pozice a uspořádání prvků měly ve správnou chvíli na obrazovce.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds v rámci plátna  
 <xref:System.Windows.Controls.Canvas> podřízené prvky můžete umístit na libovolné pozici na obrazovce, dokonce i v souřadnic, které se nachází mimo svůj vlastní definované <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A>. Kromě toho <xref:System.Windows.Controls.Canvas> nemá vliv velikost jejích potomků. V důsledku toho je možné pro podřízený element pro overdraw další prvky mimo ohraničující obdélník nadřazené <xref:System.Windows.Controls.Canvas>. Výchozí chování <xref:System.Windows.Controls.Canvas> je umožnit podřízené objekty chcete kreslit mimo hranice nadřazené <xref:System.Windows.Controls.Canvas>. Pokud toto chování nežádoucí, <xref:System.Windows.UIElement.ClipToBounds%2A> nastavenou na `true`. To způsobí, že <xref:System.Windows.Controls.Canvas> do Galerie na svůj vlastní velikost. <xref:System.Windows.Controls.Canvas> je rozložení pouze element, který umožňuje podřízené objekty být vykreslován mimo jeho hranice.  
  
 Toto chování je znázorněn graficky v [ukázkové porovnání vlastnosti Šířka](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definování a použití plátna  
 A <xref:System.Windows.Controls.Canvas> dá vytvořit instance jednoduše tak, že pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Canvas> naprosto umístění obsahu. Tento kód vytvoří tři čtverce 100 pixelů. První čtverec je red a jeho levého horního rohu (*x, y*) pozice je zadána jako (0, 0). Druhý čtverec zelené a je jeho pozice levého horního rohu (100, 100), pod a napravo od prvního čtverce. Třetí čtverec je modré a jeho pozice levého horního rohu (50, 50), tedy včetně pravém kvadrantu první čtverec a do levého horního kvadrantu druhého. Vzhledem k tomu, že poslední rozložením třetí čtverec, zobrazí se bude o dvě pole – to znamená, překrývající se části se předpokládá barva třetím poli.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Typické Element Canvas. ](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Prvek používá <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost nastavená na podřízené prvky obsahu na umístění obsahu podél okrajů kontejneru. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.Dock.Top> nebo <xref:System.Windows.Controls.Dock.Bottom>, umístí podřízené prvky nad nebo pod mezi sebou. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.Dock.Left> nebo <xref:System.Windows.Controls.Dock.Right>, umístí podřízené prvky nalevo nebo napravo od sebe navzájem. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Vlastnost určuje umístění poslední prvek přidán jako podřízený objekt <xref:System.Windows.Controls.DockPanel>.  
  
 Můžete použít <xref:System.Windows.Controls.DockPanel> na pozici skupina souvisejících ovládacích prvků, jako je například sadu tlačítek. Alternativně můžete použít k vytvoření a "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobně jako nalezeným v [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Nastavení velikosti obsahu  
 Pokud jeho <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> nejsou zadané vlastnosti, <xref:System.Windows.Controls.DockPanel> velikosti na jeho obsah. Velikost můžete zvýšit nebo snížit tak, aby vyhovovaly velikosti jeho podřízené prvky. Ale pokud tyto vlastnosti jsou určené a není už místo pro další zadaný podřízený element, <xref:System.Windows.Controls.DockPanel> nezobrazuje tento podřízený element nebo další podřízené prvky a není měření následujících podřízených elementů.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> element "vyplní" zbývající volné místo. Pokud toto chování není požadováno, nastavte <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> vlastnost `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definování a použití objektu DockPanel  
 Následující příklad ukazuje, jak rozdělení prostoru pomocí <xref:System.Windows.Controls.DockPanel>. Pět <xref:System.Windows.Controls.Border> prvky jsou přidány jako podřízené objekty nadřazeného <xref:System.Windows.Controls.DockPanel>. Každá používá jiné vlastnosti umístění <xref:System.Windows.Controls.DockPanel> k rozdělení prostoru. Poslední prvek "vyplní" zbývající volné místo.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Typický scénář DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Mřížka  
 <xref:System.Windows.Controls.Grid> Funkce absolutní pozici a ovládacího prvku tabulky dat sloučí element. A <xref:System.Windows.Controls.Grid> vám umožní snadno pozice a elementy stylu. <xref:System.Windows.Controls.Grid> můžete zadat flexibilní řádků a sloupců seskupení a dokonce poskytuje mechanismus ke sdílení informací o velikosti mezi více <xref:System.Windows.Controls.Grid> elementy.  
  
#### <a name="how-is-grid-different-from-table"></a>Jak se liší mřížky z tabulky?  
 <xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každá je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určen pro použití v rámci plovoucího obsahu (naleznete v tématu [přehled toku dokumentů](../advanced/flow-document-overview.md) Další informace o toku obsahu). Mřížka je nejvhodnější používat uvnitř formuláře (v podstatě kdekoli mimo tok obsahu). V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje tok obsahu chování jako stránkování přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> nepodporuje. A <xref:System.Windows.Controls.Grid> na druhé straně je vhodné použít mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá prvky podle řádků a sloupců indexu, <xref:System.Windows.Documents.Table> nepodporuje. <xref:System.Windows.Controls.Grid> Element umožňuje vrstvení podřízený obsah, což více než jeden element existovat v jednom "buňky." <xref:System.Windows.Documents.Table> nepodporuje vrstvení. Podřízené prvky <xref:System.Windows.Controls.Grid> může být relativní k oblasti jejich "ohraničením" absolutně umístěné. <xref:System.Windows.Documents.Table> Tato funkce není podporována. A konečně <xref:System.Windows.Controls.Grid> světlejší váhy, než je <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Chování nastavení velikosti sloupců a řádků  
 Sloupců a řádků definované v rámci <xref:System.Windows.Controls.Grid> můžou těžit z výhod <xref:System.Windows.GridUnitType.Star> velikosti dala distribuovat proporcionálně zbývající místo. Když <xref:System.Windows.GridUnitType.Star> je zvolen jako výšku nebo šířku řádku nebo sloupce, že sloupec nebo řádek obdrží vážené podíl zbývající volné místo. To je v kontrastu s <xref:System.Windows.GridUnitType.Auto>, který bude distribuovat místo rovnoměrně podle velikosti obsahu v rámci sloupce nebo řádku. Tato hodnota je vyjádřena jako `*` nebo `2*` při použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. V prvním případě řádku nebo sloupce by přijímat jeden krát dostupného místa, ve druhém případě dvakrát a tak dále. Díky kombinaci tuto techniku k proporcionálně distribuovat prostoru se <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> hodnotu `Stretch` je možné místo rozložení oddílů podle procenta prostor na obrazovce. <xref:System.Windows.Controls.Grid> je pouze rozložení panelu, můžete distribuovat prostor tímto způsobem.  
  
#### <a name="defining-and-using-a-grid"></a>Definování a použití mřížky  
 Následující příklad ukazuje, jak vytvořit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobný nalezeným v dialogovém okně spuštění, která je k dispozici na [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nabídky Start.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Typické elementu mřížky. ](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umožňuje "zásobníku" prvky přiřazené směrem. Výchozí směr zásobníku je svislý. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Vlastnost lze použít k řízení toku obsahu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel – vs. DockPanel  
 I když <xref:System.Windows.Controls.DockPanel> může také "Seskupit" podřízené prvky <xref:System.Windows.Controls.DockPanel> a <xref:System.Windows.Controls.StackPanel> záměrně neprodukují obdobná výsledky v některých scénářích použití. Například pořadí podřízených prvků může ovlivnit jejich velikosti v <xref:System.Windows.Controls.DockPanel> , ale ne v <xref:System.Windows.Controls.StackPanel>. Důvodem je, že <xref:System.Windows.Controls.StackPanel> míry ve směru překrývání na <xref:System.Double.PositiveInfinity>, zatímco <xref:System.Windows.Controls.DockPanel> měří pouze dostupné velikosti.  
  
 Následující příklad ukazuje tento klíčovým rozdílem.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Rozdíl v chování vykreslování uvidíte na tomto obrázku.  
  
 ![Snímek obrazovky: StackPanel – vs. DockPanel – snímek obrazovky](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definování a použití objektu StackPanel  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.StackPanel> vytvořit sadu tlačítek ve svislém směru umístěn. Vodorovné umístění, nastavte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Typické elementu StackPanel. ](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje varianta <xref:System.Windows.Controls.StackPanel> element, který automaticky "Virtualizuje" vázané na data podřízený obsah. V tomto kontextu se toto slovo Virtualizovat odkazuje na technika, podle kterého jsou generovány podmnožiny prvků z větší počet datových položek na základě položky, které jsou viditelné na obrazovce. Je velmi náročná, jak z hlediska paměti a procesoru, ke generování velkého počtu prvků uživatelského rozhraní, pokud jen některé mohou být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel> (prostřednictvím funkce poskytované službou <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky a funguje s <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ListView>) pouze vytvořit prvky viditelné položky.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Element bude automaticky nastavena jako položky hostování pro ovládací prvky, jako <xref:System.Windows.Controls.ListBox>. Při hostování dat vázané kolekce, obsah se automaticky virtualizované, za předpokladu, že obsah je v rámci hranice <xref:System.Windows.Controls.ScrollViewer>. Tím se výrazně zlepšuje výkon při hostování za nástrojem mnoho podřízených položek.  
  
 Následující kód ukazuje, jak používat <xref:System.Windows.Controls.VirtualizingStackPanel> jako položky hostitele. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> Musí být připojená vlastnost nastavená na `true` (výchozí) pro virtualizaci dojde k.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> slouží k umísťovat podřízené prvky do sekvenční Pozice zleva doprava, rozděluje obsah na další řádek dosáhne okrajem jeho nadřazeného kontejneru. Obsah může být orientovaný vodorovně nebo svisle. <xref:System.Windows.Controls.WrapPanel> je užitečné pro jednoduchý tok [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře. To lze také použít jednotné určení velikosti na všechny jeho podřízené prvky.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.WrapPanel> zobrazíte <xref:System.Windows.Controls.Button> ovládací prvky, které balí když dosáhnou okraj svého kontejneru.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Prvek typické WrapPanel. ](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Panel vnořené elementy  
 <xref:System.Windows.Controls.Panel> elementy mohou být vnořené do jiné, aby bylo možné vytvářet složitá rozložení. To může být velmi užitečné v situacích, kde jeden <xref:System.Windows.Controls.Panel> je ideální pro část [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale nemusí splňovat požadavky jinou část [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Neexistuje žádný praktické omezení objemu vnoření, který podporuje aplikace, ale jsou obecně nejvhodnější pro omezení aplikace použít pouze tyto panely, které jsou skutečně nezbytná pro požadované rozložení. V mnoha případech <xref:System.Windows.Controls.Grid> elementu je možné použít místo vnořené panely z důvodu jeho flexibilitu jako kontejner rozložení. To může zvýšit výkon ve vaší aplikaci udržováním nepotřebných prvků ze stromu.  
  
 Následující příklad ukazuje, jak vytvořit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , využívá registrů vnořené <xref:System.Windows.Controls.Panel> prvky, abyste dosáhli specifické rozložení. V tomto konkrétním případě <xref:System.Windows.Controls.DockPanel> element slouží k poskytování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury a vnořené <xref:System.Windows.Controls.StackPanel> elementy, <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.Canvas> se používají k umístění podřízených elementů přesně v rámci nadřazené <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Kompilované aplikace vrací novou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , která vypadá takto.  
  
 ![Uživatelské rozhraní, který využívá vnořené panely. ](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Vlastní Panel elementy  
 Zatímco [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují celou řadu ovládacích prvků flexibilní rozložení, vlastní rozložení chování můžete také dosáhnout přepsáním <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Vlastní změny velikosti a polohování lze provést pomocí definice nové umístění chování v rámci těchto přepište metody.  
  
 Podobně, vlastní rozložení chování na základě odvozených třídách (například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.Grid>) lze definovat tak, že přepíšete jejich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
 Následující kód ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.Panel> elementu. Tato nová <xref:System.Windows.Controls.Panel>definovaná jako `PlotPanel`, podporuje umístění podřízených elementů pomocí pevně zakódovaného *x -* a *y -* souřadnice. V tomto příkladu <xref:System.Windows.Shapes.Rectangle> umisťovanému prvku (není vidět), v okamžiku vykreslení 50 (*x*) a 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Složitější vlastní panel implementaci najdete v tématu [vytvořením ukázkového Panel vlastní obsah zabalení](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Podpora lokalizace a globalizace  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje mnoho funkcí, které pomáhají při vytváření lokalizovatelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Všechny prvky panel nativně podporují <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost, která je možné dynamicky znovu tok obsahu podle nastavení národního prostředí nebo jazyk uživatele. Další informace naleznete v tématu <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Vlastnost poskytuje mechanismus, který vývojářům aplikací pro předvídání potřeb lokalizované [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Použití <xref:System.Windows.SizeToContent.WidthAndHeight> hodnota této vlastnosti nadřazený <xref:System.Windows.Window> vždy dynamicky velikosti podle obsahu a není omezená umělých omezení výšce nebo šířce.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, a <xref:System.Windows.Controls.StackPanel> jsou všechna vhodná rozhodnutí pro lokalizovatelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> je dobrou volbou, ale vzhledem k tomu, že ji umístí obsah rozhodně ztěžuje lokalizovat.  
  
 Další informace o vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací s lokalizovatelné [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, najdete v článku [přehled automatického rozložení pomocí](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Ukázky WPF rozložení galerie](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Rozložení](../advanced/layout.md)
- [Ukázková galerie ovládacích prvků WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Přehled zarovnání, okrajů a odsazení](../advanced/alignment-margins-and-padding-overview.md)
- [Vytvoření vlastního panelu ukázky zabalení obsahu](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Přehled přidružených vlastností](../advanced/attached-properties-overview.md)
- [Přehled automatického rozložení](../advanced/use-automatic-layout-overview.md)
- [Rozložení a návrh](../advanced/optimizing-performance-layout-and-design.md)
