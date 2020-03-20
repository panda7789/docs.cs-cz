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
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187583"
---
# <a name="panels-overview"></a>Přehled panelů
<xref:System.Windows.Controls.Panel>prvky jsou součásti, které řídí vykreslování prvků – jejich velikost a rozměry, jejich umístění a uspořádání jejich podřízeného obsahu. Poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] řadu předdefinovaných <xref:System.Windows.Controls.Panel> prvků, stejně jako <xref:System.Windows.Controls.Panel> schopnost vytvářet vlastní prvky.  
  
 Toto téma obsahuje tyto části:  
  
- [Třída panelu](#Panels_view_from_10000_feet)  
  
- [Panelový prvek Společné členy](#Panels_declared_members)  
  
- [Odvozené prvky panelu](#Panels_derived_elements)  
  
- [Panely uživatelského rozhraní](#Panels_main_UI_elements)  
  
- [Vnořené prvky panelu](#Panels_nested_panel_elements)  
  
- [Vlastní prvky panelu](#Panels_custom_panel_elements)  
  
- [Podpora lokalizace/globalizace](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>Třída panelu  
 <xref:System.Windows.Controls.Panel>je základní třída pro všechny prvky, které poskytují podporu rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Odvozené <xref:System.Windows.Controls.Panel> prvky se používají k [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] umístění a uspořádání prvků a kódu.  
  
 Obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komplexní sadu odvozených implementací panelu, které umožňují mnoho složitých rozložení. Tyto odvozené třídy zveřejňují vlastnosti a metody, které umožňují většinu standardních [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénářů. Vývojáři, kteří nejsou schopni najít chování podřízené uspořádání, které splňuje <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> jejich potřeby můžete vytvořit nové rozložení přepsáním a metody. Další informace o vlastním chování rozložení naleznete v [tématu Vlastní prvky panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Členové panelu  
 Všechny <xref:System.Windows.Controls.Panel> prvky podporují základní velikosti a <xref:System.Windows.FrameworkElement>polohování vlastnosti definované , včetně <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Další informace o vlastnostech <xref:System.Windows.FrameworkElement>umístění definovaných v tématu Přehled [zarovnání, Okraje a Odsazení](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>poskytuje další vlastnosti, které mají zásadní význam pro pochopení a použití rozložení. Vlastnost <xref:System.Windows.Controls.Panel.Background%2A> se používá k vyplnění oblasti mezi hranicemi odvozeného <xref:System.Windows.Media.Brush>prvku panelu s . <xref:System.Windows.Controls.Panel.Children%2A>představuje podřízenou kolekci <xref:System.Windows.Controls.Panel> prvků, ze kterých se skládá. <xref:System.Windows.Controls.Panel.InternalChildren%2A>představuje obsah <xref:System.Windows.Controls.Panel.Children%2A> kolekce plus členy generované datové vazby. Oba se <xref:System.Windows.Controls.UIElementCollection> skládají z podřízených <xref:System.Windows.Controls.Panel>prvků hostovaných v nadřazeném objektu .  
  
 Panel také zpřístupňuje <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> připojené vlastnosti, které lze použít k <xref:System.Windows.Controls.Panel>dosažení vrstvené pořadí v odvozené . Členové <xref:System.Windows.Controls.Panel.Children%2A> kolekce panelu s vyšší <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnotou se zobrazí před <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> členy s nižší hodnotou. To je užitečné zejména <xref:System.Windows.Controls.Canvas> pro <xref:System.Windows.Controls.Grid> panely, jako jsou a které umožňují dětem sdílet stejný souřadnicový prostor.  
  
 <xref:System.Windows.Controls.Panel>definuje také <xref:System.Windows.Controls.Panel.OnRender%2A> metodu, kterou lze použít k přepsání <xref:System.Windows.Controls.Panel>výchozího chování prezentace aplikace .  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Odvozené prvky panelu rozsáhle využívají připojené vlastnosti. Připojená vlastnost je specializovaná forma vlastnosti závislosti, která nemá vlastnost "obálka" konvenčního běžného jazyka runtime (CLR). Připojené vlastnosti mají specializovanou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]syntaxi v , která může být viděna v několika příkladech, které následují.  
  
 Jedním z účelů připojené vlastnosti je umožnit podřízeným prvkům ukládat jedinečné hodnoty vlastnosti, která je ve skutečnosti definována nadřazeným prvkem. Aplikace této funkce má podřízené prvky informovat nadřazený, jak chtějí být prezentovány v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], což je velmi užitečné pro rozložení aplikace. Další informace naleznete v [tématu Přehled připojených vlastností](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Odvozené prvky panelu  
 Mnoho objektů <xref:System.Windows.Controls.Panel>je odvozeno z , ale ne všechny jsou určeny pro použití jako zprostředkovatelé kořenového rozložení. Existuje šest definovaných<xref:System.Windows.Controls.Canvas>tříd <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>panelu <xref:System.Windows.Controls.VirtualizingStackPanel>( <xref:System.Windows.Controls.WrapPanel>, , , <xref:System.Windows.Controls.StackPanel>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]a ), které jsou navrženy speciálně pro vytváření aplikace .  
  
 Každý prvek panelu zapouzdřuje své vlastní speciální funkce, jak je vidět v následující tabulce.  
  
|Název prvku|Panel ui?|Popis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Ano|Definuje oblast, ve které můžete explicitně umístit podřízené <xref:System.Windows.Controls.Canvas> prvky podle souřadnic vzhledem k oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Ano|Definuje oblast, ve které můžete uspořádat podřízené prvky vodorovně nebo svisle, vzhledem k sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Ano|Definuje flexibilní oblast mřížky skládající se ze sloupců a řádků. Podřízené prvky <xref:System.Windows.Controls.Grid> může být <xref:System.Windows.FrameworkElement.Margin%2A> umístěn přesně pomocí vlastnosti.|  
|<xref:System.Windows.Controls.StackPanel>|Ano|Uspořádá podřízené prvky do jedné čáry, která může být orientována vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Ne|Zpracovává rozložení tlačítek tabulátorů v rozhraní . <xref:System.Windows.Controls.TabControl>|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Ne|Uspořádá obsah <xref:System.Windows.Controls.ToolBar> v rámci ovládacího prvku.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Ne|<xref:System.Windows.Controls.Primitives.UniformGrid>slouží k uspořádání podřízených dětí v mřížce se všemi stejnými velikostmi buněk.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Ne|Poskytuje základní třídu pro panely, které můžete "virtualizovat" jejich kolekce podřízených.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Ano|Uspořádá a virtualizuje obsah na jedné čáře orientované vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.WrapPanel>|Ano|<xref:System.Windows.Controls.WrapPanel>umístí podřízené prvky do sekvenční polohy zleva doprava a přeruší obsah na další řádek na okraji obsahujícího pole. Následné řazení se stane postupně shora dolů nebo zprava doleva, v závislosti na hodnotě vlastnosti. <xref:System.Windows.Controls.WrapPanel.Orientation%2A>|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Panely uživatelského rozhraní  
 K dispozici je šest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tříd panelu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] které <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel>jsou <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel>optimalizovány pro podporu scénářů: , , , <xref:System.Windows.Controls.VirtualizingStackPanel>, a <xref:System.Windows.Controls.WrapPanel>. Tyto prvky panelu jsou snadno použitelné, všestranné a dostatečně rozšiřitelné pro většinu aplikací.  
  
 Každý odvozený <xref:System.Windows.Controls.Panel> prvek zachází s omezeními velikosti odlišně. Pochopení, <xref:System.Windows.Controls.Panel> jak zpracovává omezení ve vodorovném nebo svislém směru může rozložení předvídatelnější.  
  
|**Název panelu**|**x-Dimenze**|**y-Rozměr**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Omezená na obsah|Omezená na obsah|  
|<xref:System.Windows.Controls.DockPanel>|Omezeny|Omezeny|  
|<xref:System.Windows.Controls.StackPanel>(Svislá orientace)|Omezeny|Omezená na obsah|  
|<xref:System.Windows.Controls.StackPanel>(Vodorovná orientace)|Omezená na obsah|Omezeny|  
|<xref:System.Windows.Controls.Grid>|Omezeny|Omezené, s výjimkou případů, kdy <xref:System.Windows.GridUnitType.Auto> se vztahují na řádky a sloupce|  
|<xref:System.Windows.Controls.WrapPanel>|Omezená na obsah|Omezená na obsah|  
  
 Podrobnější popisy a příklady použití každého z těchto prvků naleznete níže.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Plátno  
 Prvek <xref:System.Windows.Controls.Canvas> umožňuje umístění obsahu podle absolutních souřadnic *x* a *y.* Prvky lze kreslit v jedinečném umístění; nebo pokud prvky zabírají stejné souřadnice, pořadí, ve kterém jsou uvedeny ve značkách určuje pořadí, ve kterém jsou prvky nakresleny.  
  
 <xref:System.Windows.Controls.Canvas>poskytuje nejflexibilnější <xref:System.Windows.Controls.Panel>podporu rozvržení ze všech . Výška a šířka vlastnosti se používají k definování oblasti plátna a prvky <xref:System.Windows.Controls.Canvas>uvnitř jsou přiřazeny absolutní souřadnice vzhledem k oblasti nadřazené . Čtyři připojené vlastnosti <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, a , umožňují <xref:System.Windows.Controls.Canvas>jemné řízení umístění objektu v rámci , což umožňuje vývojáři umístit a uspořádat prvky přesně na obrazovce.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds uvnitř plátna  
 <xref:System.Windows.Controls.Canvas>může umístit podřízené prvky na libovolné pozici na obrazovce, a <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A>to i na souřadnicích, které jsou mimo jeho vlastní definované a . Kromě toho <xref:System.Windows.Controls.Canvas> není ovlivněna velikostí svých dětí. V důsledku toho je možné pro podřízený prvek překreslit jiné prvky <xref:System.Windows.Controls.Canvas>mimo ohraničující obdélník nadřazené . Výchozí chování <xref:System.Windows.Controls.Canvas> a je umožnit dětem kreslit mimo hranice <xref:System.Windows.Controls.Canvas>nadřazené . Pokud toto chování je <xref:System.Windows.UIElement.ClipToBounds%2A> nežádoucí, vlastnost `true`může být nastavena na . To <xref:System.Windows.Controls.Canvas> způsobí, že klip na vlastní velikost. <xref:System.Windows.Controls.Canvas>je jediný prvek rozložení, který umožňuje podřízené soubory mimo jeho hranice.  
  
 Toto chování je graficky znázorněno v [ukázce porovnání vlastností šířky](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
#### <a name="defining-and-using-a-canvas"></a>Definování a používání základní stránky  
 A <xref:System.Windows.Controls.Canvas> lze vytvořit instanci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jednoduše pomocí nebo kód. Následující příklad ukazuje, jak <xref:System.Windows.Controls.Canvas> použít absolutně umístění obsahu. Tento kód vytvoří tři čtverce o 100 pixelech. První čtverec je červený a jeho pozice vlevo nahoře (*x, y*) je určena jako (0, 0). Druhý čtverec je zelený a jeho poloha vlevo nahoře je (100, 100), těsně pod a vpravo od prvního čtverce. Třetí čtverec je modrý a jeho poloha vlevo nahoře je (50, 50), čímž zahrnuje pravý dolní kvadrant prvního čtverce a levý horní kvadrant druhého. Vzhledem k tomu, že třetí čtverec je rozložen jako poslední, zdá se, že je nad ostatními dvěma čtverečky – to znamená, že překrývající se části předpokládají barvu třetího pole.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![Typický element plátna.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 Prvek <xref:System.Windows.Controls.DockPanel> používá <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojené vlastnosti jako nastavené v podřízených elementech obsahu k umístění obsahu podél okrajů kontejneru. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je <xref:System.Windows.Controls.Dock.Top> nastavena na nebo <xref:System.Windows.Controls.Dock.Bottom>, umístí podřízené prvky nad nebo pod sebou. Pokud <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je <xref:System.Windows.Controls.Dock.Left> nastavena na nebo <xref:System.Windows.Controls.Dock.Right>, umístí podřízené prvky na levé nebo pravé straně sebe. Vlastnost <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> určuje pozici konečného prvku přidaného jako podřízený <xref:System.Windows.Controls.DockPanel>.  
  
 Můžete umístit <xref:System.Windows.Controls.DockPanel> skupinu souvisejících ovládacích prvků, například sadu tlačítek. Alternativně jej můžete použít k vytvoření "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobně jako v aplikaci Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Změna velikosti podle obsahu  
 Pokud <xref:System.Windows.FrameworkElement.Height%2A> jeho <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.Controls.DockPanel> nejsou zadány, velikosti jeho obsahu. Velikost může zvětšit nebo zmenšit tak, aby vyhovovala velikosti podřízených prvků. Však pokud jsou zadány tyto vlastnosti a již není <xref:System.Windows.Controls.DockPanel> prostor pro další zadaný podřízený prvek, nezobrazí tento podřízený prvek nebo následné podřízené prvky a neměří následné podřízené prvky.  
  
#### <a name="lastchildfill"></a>Lastchildfill  
 Ve výchozím nastavení poslední <xref:System.Windows.Controls.DockPanel> podřízená část prvku "vyplní" zbývající nepřidělené místo. Pokud toto chování není <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> žádoucí, `false`nastavte vlastnost .  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definování a používání dockpanelu  
 Následující příklad ukazuje, jak rozdělit <xref:System.Windows.Controls.DockPanel>prostor pomocí . Pět <xref:System.Windows.Controls.Border> prvků jsou přidány jako <xref:System.Windows.Controls.DockPanel>podřízené položky rodiče . Každý používá jinou vlastnost <xref:System.Windows.Controls.DockPanel> umístění na oddíl prostoru. Poslední prvek "vyplní" zbývající, nepřidělené místo.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![Typický scénář DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Mřížka  
 Prvek <xref:System.Windows.Controls.Grid> slučuje funkce absolutní umístění a tabulkových dat řízení. A <xref:System.Windows.Controls.Grid> umožňuje snadno umístit a styl prvky. <xref:System.Windows.Controls.Grid>umožňuje definovat flexibilní seskupení řádků a sloupců a dokonce poskytuje mechanismus <xref:System.Windows.Controls.Grid> pro sdílení informací o velikosti mezi více prvky.  
  
#### <a name="how-is-grid-different-from-table"></a>Jak se mřížka liší od tabulky?  
 <xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určen pro použití v rámci obsahu toku (viz [Přehled toku dokumentu](../advanced/flow-document-overview.md) pro další informace o obsahu toku). Mřížky se nejlépe používají uvnitř formulářů (v podstatě kdekoli mimo obsah toku). V <xref:System.Windows.Documents.FlowDocument>rámci <xref:System.Windows.Documents.Table> , podporuje chování obsahu toku, jako je stránkování, přeformátování sloupců a výběr obsahu, zatímco <xref:System.Windows.Controls.Grid> a není. A <xref:System.Windows.Controls.Grid> na druhé straně se nejlépe <xref:System.Windows.Documents.FlowDocument> používá mimo <xref:System.Windows.Controls.Grid> z mnoha důvodů, včetně <xref:System.Windows.Documents.Table> přidá prvky založené na řádku a sloupec index, není. Prvek <xref:System.Windows.Controls.Grid> umožňuje vrstvení podřízeného obsahu, což umožňuje více než jeden prvek existovat v rámci jedné "buňky". <xref:System.Windows.Documents.Table>nepodporuje vrstvení. Podřízené <xref:System.Windows.Controls.Grid> prvky může být absolutně umístěn vzhledem k oblasti jejich "buňky" hranice. <xref:System.Windows.Documents.Table>nepodporuje tuto funkci. Konečně, <xref:System.Windows.Controls.Grid> a je <xref:System.Windows.Documents.Table>lehčí než .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Chování při změny velikosti sloupců a řádků  
 Sloupce a řádky <xref:System.Windows.Controls.Grid> definované v <xref:System.Windows.GridUnitType.Star> rámci můžete využít velikosti za účelem rozdělení zbývající místo proporcionálně. Pokud <xref:System.Windows.GridUnitType.Star> je vybrána jako výška nebo šířka řádku nebo sloupce, tento sloupec nebo řádek obdrží vážený podíl zbývajícího dostupného místa. To je na <xref:System.Windows.GridUnitType.Auto>rozdíl od , který bude distribuovat prostor rovnoměrně na základě velikosti obsahu ve sloupci nebo řádku. Tato hodnota je `*` vyjádřena jako nebo `2*` při použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. V prvním případě by řádek nebo sloupec obdrží jeden krát volné místo, ve druhém případě dvakrát a tak dále. Kombinací této techniky proporcionálně <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> distribuovat <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> prostor `Stretch` s a hodnotu je možné rozdělit rozložení prostoru podle procenta místa na obrazovce. <xref:System.Windows.Controls.Grid>je jediný panel rozvržení, který může tímto způsobem distribuovat prostor.  
  
#### <a name="defining-and-using-a-grid"></a>Definování a používání mřížky  
 Následující příklad ukazuje, jak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvořit podobný jako v dialogovém okně Spustit k dispozici v nabídce Start systému Windows.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![Typický element mřížky.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umožňuje "stohovat" prvky v přiřazeném směru. Výchozí směr zásobníku je svislý. Vlastnost <xref:System.Windows.Controls.StackPanel.Orientation%2A> lze použít k řízení toku obsahu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Ačkoli <xref:System.Windows.Controls.DockPanel> může také "zásobník" <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel> podřízené prvky a nevytvářejí podobné výsledky v některých scénářích použití. Například pořadí podřízených prvků může ovlivnit <xref:System.Windows.Controls.DockPanel> jejich velikost <xref:System.Windows.Controls.StackPanel>v , ale ne v . Je to <xref:System.Windows.Controls.StackPanel> proto, že měří <xref:System.Double.PositiveInfinity>ve směru <xref:System.Windows.Controls.DockPanel> stohování v , zatímco měří pouze dostupnou velikost.  
  
 Následující příklad ukazuje tento klíčový rozdíl.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Rozdíl v chování vykreslování lze vidět v tomto obrázku.  
  
 ![Snímek obrazovky: StackPanel vs. DockPanel – snímek obrazovky](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definování a používání panelu StackPanel  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.StackPanel> použít sadu svisle umístěných tlačítek. Pro vodorovné umístění <xref:System.Windows.Controls.StackPanel.Orientation%2A> nastavte <xref:System.Windows.Controls.Orientation.Horizontal>vlastnost na .  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![Typický StackPanel prvek.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>Virtualizingstackpanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje variantu <xref:System.Windows.Controls.StackPanel> prvku, který automaticky "virtualizuje" podřízený obsah vázaný na data. V tomto kontextu slovo virtualizovat odkazuje na techniku, kterou podmnožina prvků jsou generovány z většího počtu datových položek na základě položek, které jsou viditelné na obrazovce. Je intenzivní, a to jak z hlediska paměti a procesoru, generovat velké množství prvků uživatelského rozhraní, když pouze několik může být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel>(prostřednictvím funkce poskytované <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky <xref:System.Windows.Controls.ItemContainerGenerator> a <xref:System.Windows.Controls.ItemsControl> pracuje <xref:System.Windows.Controls.ListBox> s <xref:System.Windows.Controls.ListView>z (například nebo ) vytvořit pouze prvky pro viditelné položky.  
  
 Prvek <xref:System.Windows.Controls.VirtualizingStackPanel> je automaticky nastaven jako hostitel položek <xref:System.Windows.Controls.ListBox>pro ovládací prvky, jako je například . Při hostování kolekce vázané na data je obsah automaticky virtualizován, pokud je <xref:System.Windows.Controls.ScrollViewer>obsah v rámci souboru . To výrazně zlepšuje výkon při hostování mnoha podřízených položek.  
  
 Následující značky ukazují, jak <xref:System.Windows.Controls.VirtualizingStackPanel> používat jako hostitele položek. Připojené <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> vlastnosti musí být `true` nastavena na (výchozí) pro virtualizaci dojít.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>slouží k umístění podřízených prvků v sekvenční poloze zleva doprava, rozdělení obsahu na další řádek, když dosáhne okraje nadřazeného kontejneru. Obsah může být orientován vodorovně nebo svisle. <xref:System.Windows.Controls.WrapPanel>je užitečné pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jednoduché tekoucí scénáře. Může být také použit k použití jednotného dimenzování na všechny podřízené prvky.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.WrapPanel> vytvořit <xref:System.Windows.Controls.Button> ovládací prvky, které obtékají, když dosáhnou okraje jejich kontejneru.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![Typický WrapPanel Element.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>Vnořené prvky panelu  
 <xref:System.Windows.Controls.Panel>prvky mohou být vnořeny do sebe, aby bylo možné vytvořit komplexní rozložení. To se může ukázat jako <xref:System.Windows.Controls.Panel> velmi užitečné v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]situacích, kdy je ideální pro část [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale nemusí splňovat potřeby jiné části .  
  
 Neexistuje žádné praktické omezení množství vnoření, které vaše aplikace může podporovat, ale je obecně nejlepší omezit aplikaci používat pouze ty panely, které jsou skutečně nezbytné pro požadované rozložení. V mnoha případech <xref:System.Windows.Controls.Grid> lze prvek použít místo vnořených panelů kvůli jeho flexibilitě jako kontejnerrozložení. To může zvýšit výkon v aplikaci udržováním nepotřebné prvky ze stromu.  
  
 Následující příklad ukazuje, jak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvořit, který využívá <xref:System.Windows.Controls.Panel> vnořené prvky k dosažení určité rozložení. V tomto konkrétním <xref:System.Windows.Controls.DockPanel> případě prvek se [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] používá k <xref:System.Windows.Controls.StackPanel> poskytnutí struktury <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.Canvas> vnořené prvky , <xref:System.Windows.Controls.DockPanel>a a se používají k umístění podřízených prvků přesně v nadřazené .  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Zkompilovaná aplikace poskytuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nový, který vypadá takto.  
  
 ![UI, které využívá vnořené panely.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Vlastní prvky panelu  
 Zatímco [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu flexibilní ovládací prvky rozložení, vlastní rozložení chování <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> lze také dosáhnout přepsáním a metody. Vlastní velikost i umístění lze provést definováním nové chování umístění v rámci těchto metod přepsání.  
  
 Podobně vlastní rozložení chování založené na odvozené <xref:System.Windows.Controls.Canvas> třídy (například nebo <xref:System.Windows.Controls.Grid> <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ) <xref:System.Windows.FrameworkElement.MeasureOverride%2A> lze definovat přepsáníjejich a metody.  
  
 Následující značky ukazují, jak vytvořit <xref:System.Windows.Controls.Panel> vlastní prvek. Tento <xref:System.Windows.Controls.Panel>nový , `PlotPanel`definovaný jako , podporuje umístění podřízených prvků pomocí pevně zakódovaných souřadnic *x* a *y.* V tomto příkladu <xref:System.Windows.Shapes.Rectangle> je prvek (není zobrazen) umístěn v bodě vykreslení 50 (*x*) a 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Chcete-li zobrazit složitější vlastní implementaci panelu, přečtěte si informace [o vytvoření ukázky panelu zalamování vlastního obsahu](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Podpora lokalizace/globalizace  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje řadu funkcí, které pomáhají při vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lokalizovatelných .  
  
 Všechny prvky panelu <xref:System.Windows.FrameworkElement.FlowDirection%2A> nativně podporují vlastnost, kterou lze použít k dynamickému opětovnému natírkování obsahu na základě národního prostředí uživatele nebo nastavení jazyka. Další informace naleznete v tématu <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Vlastnost <xref:System.Windows.Window.SizeToContent%2A> poskytuje mechanismus, který umožňuje vývojářům aplikací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]předvídat potřeby lokalizované . Pomocí <xref:System.Windows.SizeToContent.WidthAndHeight> hodnoty této vlastnosti <xref:System.Windows.Window> se nadřazený objekt vždy dynamicky mění tak, aby odpovídal obsahu, a není omezen omezeními umělé výšky nebo šířky.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.StackPanel> jsou všechny dobré volby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]pro lokalizovatelné . <xref:System.Windows.Controls.Canvas>není dobrá volba, nicméně, protože pozice obsah absolutně, takže je obtížné lokalizovat.  
  
 Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytváření aplikací pomocí lokalizovatelných uživatelských rozhraní naleznete v [tématu Použití přehledu automatického rozložení](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Ukázka galerie rozložení WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Rozložení](../advanced/layout.md)
- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Přehled zarovnání, okrajů a odsazení](../advanced/alignment-margins-and-padding-overview.md)
- [Vytvoření ukázky vlastního panelu obtékání obsahu](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Přehled přidružených vlastností](../advanced/attached-properties-overview.md)
- [Přehled automatického rozložení](../advanced/use-automatic-layout-overview.md)
- [Rozložení a návrh](../advanced/optimizing-performance-layout-and-design.md)
