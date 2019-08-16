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
ms.openlocfilehash: 4f54596e1ce3ed40f3a029ea6703147a97be992f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545266"
---
# <a name="panels-overview"></a>Přehled panelů
<xref:System.Windows.Controls.Panel>prvky jsou komponenty, které řídí vykreslování prvků – jejich velikost a rozměry, jejich umístění a uspořádání jejich podřízeného obsahu. Poskytuje řadu předdefinovaných <xref:System.Windows.Controls.Panel> prvků, jakož i možnost vytvářet vlastní <xref:System.Windows.Controls.Panel> prvky. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]  
  
 Toto téma obsahuje následující části.  
  
- [Třída panel](#Panels_view_from_10000_feet)  
  
- [Společné členy elementu panel](#Panels_declared_members)  
  
- [Elementy odvozeného panelu](#Panels_derived_elements)  
  
- [Panely uživatelského rozhraní](#Panels_main_UI_elements)  
  
- [Prvky vnořeného panelu](#Panels_nested_panel_elements)  
  
- [Vlastní prvky panelu](#Panels_custom_panel_elements)  
  
- [Podpora lokalizace/globalizace](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Třída panel  
 <xref:System.Windows.Controls.Panel>je základní třídou pro všechny prvky, které poskytují podporu rozložení [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]v. Odvozené <xref:System.Windows.Controls.Panel> elementy slouží k umístění a uspořádání prvků v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kódu a.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsahuje komplexní sadu implementací odvozeného panelu, které umožňují mnoho složitých rozložení. Tyto odvozené třídy zveřejňují vlastnosti a metody, které povolují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] většinu standardních scénářů. Vývojáři, kteří nemůžou najít podřízené chování uspořádání, které splňuje jejich potřeby, mohou vytvořit nová rozložení přepsáním <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a. Další informace o chování vlastních rozložení najdete v tématu [vlastní prvky panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Společné členy panelu  
 Všechny <xref:System.Windows.Controls.Panel> elementy podporují základní vlastnosti velikosti a umístění <xref:System.Windows.FrameworkElement>definované, včetně <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Další informace o umístění vlastností definovaných nástrojem <xref:System.Windows.FrameworkElement>najdete v tématu [Přehled zarovnání, okrajů a odsazení](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>zpřístupňuje další vlastnosti, které mají zásadní význam pro porozumění a používání rozložení. Vlastnost slouží k vyplnění oblasti mezi hranicemi elementu odvozeného panelu <xref:System.Windows.Media.Brush>s. <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel.Children%2A>představuje podřízenou kolekci prvků, ze kterých <xref:System.Windows.Controls.Panel> se skládá. <xref:System.Windows.Controls.Panel.InternalChildren%2A>představuje obsah <xref:System.Windows.Controls.Panel.Children%2A> kolekce včetně těch členů generovaných datovou vazbou. Oba se <xref:System.Windows.Controls.UIElementCollection> skládají z podřízených prvků hostovaných v rámci <xref:System.Windows.Controls.Panel>nadřazeného objektu.  
  
 Panel také zpřístupňuje <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> připojenou vlastnost, která může být použita k dosažení vrstveného pořadí v <xref:System.Windows.Controls.Panel>odvozeném. Členy <xref:System.Windows.Controls.Panel.Children%2A> kolekce panelu s vyšší <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnotou se zobrazí před hodnotami s nižší <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> hodnotou. To je zvlášť užitečné pro panely, jako <xref:System.Windows.Controls.Canvas> jsou <xref:System.Windows.Controls.Grid> a, které umožňují dětem sdílet stejný prostor souřadnic.  
  
 <xref:System.Windows.Controls.Panel>také definuje <xref:System.Windows.Controls.Panel.OnRender%2A> metodu, která může být použita k přepsání výchozího chování <xref:System.Windows.Controls.Panel>prezentace.  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Elementy odvozeného panelu mají rozsáhlou práci s připojenými vlastnostmi. Připojená vlastnost je specializovaná forma vlastnosti závislosti, která neobsahuje konvenční vlastnost Common Language Runtime (CLR) typu "Obálka". Připojené vlastnosti mají specializovanou syntaxi v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], která se může zobrazit v několika příkladech, které následují.  
  
 Jedním z účel připojených vlastností je povolení podřízeným elementům ukládat jedinečné hodnoty vlastnosti, která je skutečně definována nadřazeným elementem. Aplikace této funkce má podřízené prvky [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], které informují rodiče o tom, jak chtějí být prezentovány v, což je pro rozložení aplikace velmi užitečné. Další informace najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementy odvozeného panelu  
 Mnoho objektů je odvozeno z <xref:System.Windows.Controls.Panel>, ale ne všechny jsou určené pro použití jako poskytovatelé kořenového rozložení. Existuje šest definovaných<xref:System.Windows.Controls.Canvas>tříd panelů (, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>a <xref:System.Windows.Controls.WrapPanel>), které jsou navrženy specificky pro vytváření aplikací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Jednotlivé prvky panelu zapouzdřují své vlastní zvláštní funkce, jak je vidět v následující tabulce.  
  
|Název elementu|Panel uživatelského rozhraní?|Popis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Ano|Definuje oblast, ve které můžete explicitně umístit podřízené prvky souřadnicemi relativními k <xref:System.Windows.Controls.Canvas> oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Ano|Definuje oblast, ve které můžete uspořádat podřízené prvky buď vodorovně, nebo svisle, relativně k sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Ano|Definuje flexibilní oblast mřížky sestávající ze sloupců a řádků. Podřízené prvky prvku <xref:System.Windows.Controls.Grid> lze přesně umístit <xref:System.Windows.FrameworkElement.Margin%2A> pomocí vlastnosti.|  
|<xref:System.Windows.Controls.StackPanel>|Ano|Uspořádá podřízené prvky na jeden řádek, který může být orientovaný vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Ne|Zpracovává rozložení tlačítek na kartě v <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Ne|Uspořádá obsah v rámci <xref:System.Windows.Controls.ToolBar> ovládacího prvku.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Ne|<xref:System.Windows.Controls.Primitives.UniformGrid>slouží k uspořádání podřízených objektů v mřížce se všemi stejnými velikostmi buněk.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Ne|Poskytuje základní třídu pro panely, které mohou "virtualizovat" jejich podřízenou kolekci.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Ano|Uspořádá a virtualizuje obsah na jednom řádku orientovaném vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.WrapPanel>|Ano|<xref:System.Windows.Controls.WrapPanel>umístí podřízené prvky v sekvenčním umístění zleva doprava a oddělí obsah na další řádek na okraji obsahujícího pole. Následné řazení probíhá postupně shora dolů nebo zprava doleva v závislosti na hodnotě <xref:System.Windows.Controls.WrapPanel.Orientation%2A> vlastnosti.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panely uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] V nástroji jsou k dispozici šest tříd panelů, které jsou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] optimalizované pro podporu <xref:System.Windows.Controls.Grid>scénářů <xref:System.Windows.Controls.VirtualizingStackPanel>: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.WrapPanel> <xref:System.Windows.Controls.DockPanel>,, <xref:System.Windows.Controls.StackPanel>, a. Tyto prvky panelu lze snadno používat, univerzální a dostatečně rozšiřitelné pro většinu aplikací.  
  
 Každý odvozený <xref:System.Windows.Controls.Panel> element zpracovává omezení velikosti odlišně. Porozumět, <xref:System.Windows.Controls.Panel> jak omezení pro zpracování v horizontálním nebo svislém směru může udělat větší předvídatelný vzhled.  
  
|**Název panelu**|**x – dimenze**|**y – dimenze**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Omezené na obsah|Omezené na obsah|  
|<xref:System.Windows.Controls.DockPanel>|Omezené|Omezené|  
|<xref:System.Windows.Controls.StackPanel>(Svislá orientace)|Omezené|Omezené na obsah|  
|<xref:System.Windows.Controls.StackPanel>(Horizontální orientace)|Omezené na obsah|Omezené|  
|<xref:System.Windows.Controls.Grid>|Omezené|Omezeno, s výjimkou případů, <xref:System.Windows.GridUnitType.Auto> kdy platí pro řádky a sloupce|  
|<xref:System.Windows.Controls.WrapPanel>|Omezené na obsah|Omezené na obsah|  
  
 Podrobnější popisy a příklady použití jednotlivých prvků najdete níže.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Plátno  
 Element <xref:System.Windows.Controls.Canvas> umožňuje umísťování obsahu v závislosti na absolutních souřadnicích *x* a *y*. Prvky lze vykreslit v jedinečném umístění; nebo, pokud prvky zabírají stejné souřadnice, pořadí, ve kterém jsou uvedeny v označení, určuje pořadí, ve kterém jsou prvky vykreslovány.  
  
 <xref:System.Windows.Controls.Canvas>poskytuje nejpružnější podporu rozložení pro všechny <xref:System.Windows.Controls.Panel>. Vlastnosti Height a Width slouží k definování oblasti plátna a prvky uvnitř jsou přiřazeny absolutní souřadnice vzhledem k oblasti nadřazeného objektu <xref:System.Windows.Controls.Canvas>. Čtyři připojené vlastnosti, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas>, a umožňují<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>přesné řízení umístění objektu v rámci, aby vývojář mohl umístit a uspořádat prvky na obrazovce přesně. <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds na plátně  
 <xref:System.Windows.Controls.Canvas>může umístit podřízené prvky na libovolné místo na obrazovce, a to i v souřadnicích, které jsou mimo vlastní <xref:System.Windows.FrameworkElement.Height%2A> definované <xref:System.Windows.FrameworkElement.Width%2A>a. Kromě toho <xref:System.Windows.Controls.Canvas> nemá vliv na velikost svých podřízených objektů. V důsledku toho je možné, že podřízený prvek překreslí jiné prvky mimo ohraničující obdélník nadřazeného objektu <xref:System.Windows.Controls.Canvas>. Výchozím chováním <xref:System.Windows.Controls.Canvas> je umožnění vykreslování podřízených objektů mimo hranice nadřazené položky <xref:System.Windows.Controls.Canvas>. Pokud je toto chování nežádoucí, <xref:System.Windows.UIElement.ClipToBounds%2A> vlastnost může být nastavena na `true`hodnotu. To způsobí <xref:System.Windows.Controls.Canvas> , že bude oříznuta na svou vlastní velikost. <xref:System.Windows.Controls.Canvas>je jediným prvkem rozložení, který umožňuje vykreslit podřízené objekty mimo hranice.  
  
 Toto chování je graficky znázorněné v [ukázce porovnání vlastností šířky](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definování a použití plátna  
 Lze vytvořit instanci jednoduše pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. <xref:System.Windows.Controls.Canvas> Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.Canvas> k naprostou polohu obsahu. Tento kód vytváří čtverce o velikosti 3 100 pixelů. První čtverec je červenou a pozice v levém horním rohu (*x, y*) je zadaná jako (0, 0). Druhý čtverec je zelený a jeho pozice v levém horním rohu je (100, 100), bezprostředně pod a vpravo od prvního čtverce. Třetí čtverec je modrý a jeho pozice v levém horním rohu je (50, 50), takže zahrnuje pravý dolní kvadrant prvního čtverce a levého horního kvadrantu druhého. Vzhledem k tomu, že se třetí čtverec nahlásilo jako poslední, zdá se, že se nachází na dalších dvou čtvercích – to znamená, že překrývající se části předpokládají barvu třetího pole.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Typický prvek plátna.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Element<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> používá připojenou vlastnost jako nastavenou v podřízených prvcích obsahu k umístění obsahu podél okrajů kontejneru. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastaveno na <xref:System.Windows.Controls.Dock.Top> nebo <xref:System.Windows.Controls.Dock.Bottom>, umístí podřízené prvky nad nebo pod sebou. Když <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je nastavené <xref:System.Windows.Controls.Dock.Left> na <xref:System.Windows.Controls.Dock.Right>nebo, umístí podřízené prvky vlevo nebo napravo od sebe. Vlastnost určuje pozici posledního elementu, který byl přidán jako podřízený <xref:System.Windows.Controls.DockPanel>objekt. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>  
  
 Můžete použít <xref:System.Windows.Controls.DockPanel> k umístění skupiny souvisejících ovládacích prvků, například sady tlačítek. Alternativně můžete pomocí něj vytvořit "podokna" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobně jako v aplikaci Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Změna velikosti obsahu  
 Pokud nejsou zadány vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DockPanel>aa jejich obsah, budou velikosti. <xref:System.Windows.FrameworkElement.Height%2A> Velikost se může zvětšit nebo zmenšit, aby se vešla velikost jejích podřízených prvků. Nicméně pokud jsou tyto vlastnosti zadány a již není místo pro další zadaný podřízený element, <xref:System.Windows.Controls.DockPanel> nezobrazuje tento podřízený element ani následné podřízené prvky a neměří následné podřízené prvky.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Ve výchozím nastavení bude poslední podřízená položka <xref:System.Windows.Controls.DockPanel> elementu "Fill" zbývající, nepřidělené místo. Pokud se toto chování nepožaduje, nastavte <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> vlastnost na. `false`  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definování a použití DockPanel  
 Následující příklad ukazuje, jak rozdělit prostor pomocí <xref:System.Windows.Controls.DockPanel>. Pět <xref:System.Windows.Controls.Border> prvků je přidáno jako podřízených objektů nadřazené <xref:System.Windows.Controls.DockPanel>položky. Každá z <xref:System.Windows.Controls.DockPanel> nich používá jinou vlastnost umístění k rozdělení prostoru na oddíly. Poslední prvek "vyplní" zbývající, nepřidělené místo.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Typický scénář DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Mřížka  
 <xref:System.Windows.Controls.Grid> Prvek slučuje funkce absolutního umístění a ovládacího prvku tabulkových dat. A <xref:System.Windows.Controls.Grid> umožňuje snadno umístit prvky a styl. <xref:System.Windows.Controls.Grid>umožňuje definovat flexibilní seskupení řádků a sloupců a dokonce poskytuje mechanismus pro sdílení informací o velikosti mezi více <xref:System.Windows.Controls.Grid> prvky.  
  
#### <a name="how-is-grid-different-from-table"></a>Jak se mřížka liší od tabulky?  
 <xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílejte některé běžné funkce, ale každá z nich nejlépe vyhovuje různým scénářům. Je navržený pro použití v rámci obsahu toku (Další informace o obsahu toku najdete v tématu [Přehled dokumentů flowu](../advanced/flow-document-overview.md) ). <xref:System.Windows.Documents.Table> Mřížky se nejlépe používají ve formulářích (v podstatě kdekoli mimo obsah toku). V nástroji podporuje <xref:System.Windows.Documents.Table> chování toku obsahu, jako jsou stránkování, přetékání sloupců <xref:System.Windows.Controls.Grid> a výběr obsahu ,zatímconení.<xref:System.Windows.Documents.FlowDocument> A <xref:System.Windows.Controls.Grid> na druhé straně se nejlépe využije mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů, včetně <xref:System.Windows.Controls.Grid> Přidání prvků založených na indexu řádků a sloupců, <xref:System.Windows.Documents.Table> ale ne. <xref:System.Windows.Controls.Grid> Prvek umožňuje vrstvení podřízeného obsahu, což umožňuje, aby v jedné "buňce" existoval více než jeden prvek. <xref:System.Windows.Documents.Table>nepodporuje vrstvení. Podřízené elementy objektu <xref:System.Windows.Controls.Grid> mohou být absolutně umístěny relativně k oblasti jejich hranic "buňka". <xref:System.Windows.Documents.Table>Tato funkce nepodporuje. Nakonec a <xref:System.Windows.Controls.Grid> je světlejší tloušťka <xref:System.Windows.Documents.Table>než.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Chování sloupců a řádků podle velikosti  
 Sloupce a řádky, které jsou <xref:System.Windows.Controls.Grid> definovány v rámci, <xref:System.Windows.GridUnitType.Star> můžou využít výhod velikosti, aby bylo možné rozdělit zbývající prostor proporcionálně. Když <xref:System.Windows.GridUnitType.Star> je vybrána možnost jako výška nebo šířka řádku nebo sloupce, obdrží tento sloupec nebo řádek vážený poměr zbývající dostupné místo. To je na rozdíl od <xref:System.Windows.GridUnitType.Auto>, což rozšíří prostor rovnoměrně na základě velikosti obsahu v rámci sloupce nebo řádku. Tato hodnota je vyjádřena `*` jako `2*` nebo při [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]použití. V prvním případě by se řádek nebo sloupec dostal vícekrát k dostupnému místu, ve druhém případě dvakrát a tak dále. Kombinací této techniky k rozdělení prostoru s <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotou `Stretch` a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> je možné rozdělit prostor na rozložení podle procenta místa na obrazovce. <xref:System.Windows.Controls.Grid>je jediným panelem rozložení, který může distribuovat místo tímto způsobem.  
  
#### <a name="defining-and-using-a-grid"></a>Definování a použití mřížky  
 Následující příklad ukazuje, jak vytvořit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobný příkaz, který najdete v dialogovém okně Spustit, který je k dispozici [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] v nabídce Start.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Typický element Grid.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umožňuje prvky "Stack" v přiřazeném směru. Výchozí směr zásobníku je svislý. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Vlastnost lze použít k řízení toku obsahu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 I <xref:System.Windows.Controls.DockPanel> když mohou také podřízené <xref:System.Windows.Controls.DockPanel> prvky "Stack" a <xref:System.Windows.Controls.StackPanel> nevytvářet podobné výsledky v některých scénářích použití. Například pořadí podřízených prvků může mít vliv na jejich velikost v <xref:System.Windows.Controls.DockPanel> , ale ne <xref:System.Windows.Controls.StackPanel>v. Důvodem je <xref:System.Windows.Controls.StackPanel> to, že <xref:System.Windows.Controls.DockPanel> míry ve směru skládání na <xref:System.Double.PositiveInfinity>, které měří pouze dostupnou velikost.  
  
 Následující příklad ukazuje tento klíčový rozdíl.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Rozdíl v chování vykreslování lze zobrazit v tomto obrázku.  
  
 ![– StackPanel vs. DockPanel snímek]obrazovky(./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definování a použití StackPanel  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.StackPanel> k vytvoření sady svislě umístěných tlačítek. Pro horizontální umístění nastavte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost na <xref:System.Windows.Controls.Orientation.Horizontal>hodnotu.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Typický element StackPanel.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje variaci prvku, <xref:System.Windows.Controls.StackPanel> který automaticky "virtualizuje" podřízený obsah vázaný na data. V tomto kontextu slovo Virtualization odkazuje na techniku, podle které je vygenerována podmnožina prvků z většího počtu datových položek na základě toho, které položky jsou viditelné na obrazovce. Je náročné, a to jak z paměti, tak i procesoru, aby vygeneroval velký počet prvků uživatelského rozhraní, když na obrazovce v daném okamžiku může být jenom pár. <xref:System.Windows.Controls.VirtualizingStackPanel>(díky funkcím, <xref:System.Windows.Controls.VirtualizingPanel>které poskytuje) vypočítá viditelné položky a pracuje <xref:System.Windows.Controls.ItemContainerGenerator> s <xref:System.Windows.Controls.ListBox> z <xref:System.Windows.Controls.ItemsControl> a (například nebo <xref:System.Windows.Controls.ListView>), aby bylo možné vytvářet pouze prvky pro viditelné položky.  
  
 Prvek je automaticky nastaven jako hostitel položky pro ovládací prvky, jako je <xref:System.Windows.Controls.ListBox>například. <xref:System.Windows.Controls.VirtualizingStackPanel> Při hostování kolekce vázané na data se obsah automaticky virtualizuje, pokud se obsah nachází v mezích <xref:System.Windows.Controls.ScrollViewer>. Tím se výrazně zvyšuje výkon při hostování mnoha podřízených položek.  
  
 Následující kód ukazuje, jak používat <xref:System.Windows.Controls.VirtualizingStackPanel> jako hostitele položek. Aby bylo možné provést virtualizaci, `true` musí být připojenávlastnostnastavenána(výchozí).<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>slouží k umístění podřízených prvků v sekvenčním umístění zleva doprava, při přerušení obsahu na další řádek, když dosáhne okraje svého nadřazeného kontejneru. Obsah může být orientovaný vodorovně nebo svisle. <xref:System.Windows.Controls.WrapPanel>je užitečné při jednoduchých [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénářích toku. Dá se použít i k aplikování jednotné velikosti na všechny jeho podřízené prvky.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.WrapPanel> , chcete-li zobrazit <xref:System.Windows.Controls.Button> ovládací prvky, které se zabalí, když dosáhnou okraje jejich kontejneru.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Typický element objektu WrapPanel.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Prvky vnořeného panelu  
 <xref:System.Windows.Controls.Panel>prvky mohou být vnořeny do sebe navzájem, aby se vytvořila složitá rozložení. To může být velmi užitečné v situacích, kdy <xref:System.Windows.Controls.Panel> je jedna ideální pro část a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale nemusí splňovat požadavky jiné části [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Neexistuje žádné praktické omezení na množství vnoření, které může vaše aplikace podporovat, ale obecně je vhodné omezit aplikaci tak, aby používala pouze ty panely, které jsou opravdu nezbytné pro požadované rozložení. V mnoha případech <xref:System.Windows.Controls.Grid> lze prvek použít místo vnořených panelů z důvodu jeho flexibility jako kontejneru rozložení. To může zvýšit výkon aplikace tím, že zachová nepotřebné prvky mimo strom.  
  
 Následující příklad ukazuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jak vytvořit, který využívá vnořené <xref:System.Windows.Controls.Panel> prvky, aby bylo možné dosáhnout konkrétního rozložení. <xref:System.Windows.Controls.DockPanel> V tomto konkrétním případě je element použit k poskytnutí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury <xref:System.Windows.Controls.Grid>a vnořené <xref:System.Windows.Controls.StackPanel> prvky, a, a <xref:System.Windows.Controls.Canvas> slouží k přesnému umístění podřízených elementů v rámci nadřazeného objektu <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Kompilovaná aplikace má za důsledek nový [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který vypadá nějak takto.  
  
 ![Uživatelské rozhraní, které využívá výhod vnořených panelů.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Vlastní prvky panelu  
 Zatímco [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje pole flexibilních ovládacích prvků rozložení, chování vlastního rozložení lze také dosáhnout <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> přepsáním metod a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> . Vlastní nastavení velikosti a umístění je možné dosáhnout definováním nového chování umístění v rámci těchto metod přepsání.  
  
 Podobně vlastní chování rozložení založené na odvozených třídách (například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.Grid>) lze definovat přepsáním jejich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod a <xref:System.Windows.FrameworkElement.MeasureOverride%2A> .  
  
 Následující kód ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.Panel> element. Tento nový <xref:System.Windows.Controls.Panel>, definovaný jako `PlotPanel`, podporuje umístění podřízených elementů prostřednictvím použití pevně zakódovaných souřadnic *x* a *y*. V tomto příkladu <xref:System.Windows.Shapes.Rectangle> je prvek (nezobrazený) umístěn v bodu vykreslování 50 (*x*) a 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Chcete-li zobrazit složitější vlastní implementaci panelu, přečtěte si téma [Vytvoření vlastního obsahu – ukázka panelu](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Podpora lokalizace/globalizace  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje řadu funkcí, které pomáhají při vytváření lokalizovatelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Všechny prvky panelu nativně podporují <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost, která se dá použít k dynamickému přetečení obsahu na základě národního prostředí nebo nastavení jazyka uživatele. Další informace naleznete v tématu <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Vlastnost poskytuje mechanismus, který vývojářům aplikací umožňuje předvídání potřeb lokalizovaných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Window.SizeToContent%2A> Při použití <xref:System.Windows.Window> hodnoty této vlastnosti nadřazené položky vždycky dynamicky přizpůsobí obsah a neomezuje se na umělá omezení výšky nebo šířky. <xref:System.Windows.SizeToContent.WidthAndHeight>  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.StackPanel> jsou všechny[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]dobré možnosti, které lze lokalizovat. <xref:System.Windows.Controls.Canvas>není vhodným výběrem, protože umisťuje obsah absolutně, což ztěžuje jeho lokalizaci.  
  
 Další informace o vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací s možností [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]lokalizace najdete v tématu [Přehled použití automatického rozložení](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Ukázka Galerie rozložení WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Rozložení](../advanced/layout.md)
- [Ukázka galerie ovládacích prvků WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Přehled zarovnání, okrajů a odsazení](../advanced/alignment-margins-and-padding-overview.md)
- [Vytvoření vlastního vzorku panelu pro vybalení obsahu](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Přehled přidružených vlastností](../advanced/attached-properties-overview.md)
- [Přehled automatického rozložení](../advanced/use-automatic-layout-overview.md)
- [Rozložení a návrh](../advanced/optimizing-performance-layout-and-design.md)
