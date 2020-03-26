---
title: Přehled vykreslování grafiky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 9d58aa973f7de6c073611e13f2889913ff26dd55
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111917"
---
# <a name="wpf-graphics-rendering-overview"></a>Přehled vykreslování grafiky WPF
Toto téma obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přehled vizuální vrstvy. Zaměřuje se na roli <xref:System.Windows.Media.Visual> třídy pro podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování v modelu.  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Role vizuálního objektu  
 Třída <xref:System.Windows.Media.Visual> je základní abstrakce, <xref:System.Windows.FrameworkElement> ze které každý objekt odvozuje. Slouží také jako vstupní bod pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zápis nových ovládacích prvků v aplikaci a v mnoha ohledech si jej lze vykládat jako popisovač okna (HWND) v aplikačním modelu Win32.  
  
 Objekt <xref:System.Windows.Media.Visual> je základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt, jehož primární úlohou je poskytovat podporu vykreslování. Ovládací prvky uživatelského <xref:System.Windows.Controls.TextBox>rozhraní, <xref:System.Windows.Media.Visual> například <xref:System.Windows.Controls.Button> a , odvozují z třídy a používají je k uchování jejich vykreslovacích dat. Objekt <xref:System.Windows.Media.Visual> poskytuje podporu pro:  
  
- Zobrazení výstupu: Vykreslení trvalého, serializovaného obsahu výkresu vizuálu.  
  
- Transformace: Provádění transformací na vizuálu.  
  
- Oříznutí: Poskytování podpory oblasti oříznutí pro vizuál.  
  
- Testování přístupů: Určení, zda je souřadnice nebo geometrie obsažena v mezích vizuálu.  
  
- Výpočty ohraničovacího rámečku: Určení ohraničovacího obdélníku vizuálu.  
  
 <xref:System.Windows.Media.Visual> Objekt však neobsahuje podporu pro funkce bez vykreslování, například:  
  
- Zpracování událostí  
  
- Rozložení  
  
- Styly  
  
- Datová vazba  
  
- Globalizace  
  
 <xref:System.Windows.Media.Visual>je vystavena jako veřejné abstraktní třídy, ze kterého musí být odvozenpodřízené třídy. Následující obrázek znázorňuje hierarchii vizuálních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objektů, které jsou vystaveny v aplikaci .  
  
 ![Diagram tříd odvozených z objektu Visual](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>KresleníVizuální třída  
 Jedná <xref:System.Windows.Media.DrawingVisual> se o zjednodušenou třídu výkresu, která slouží k vykreslení obrazců, obrázků nebo textu. Tato třída je považována za zjednodušenou, protože neposkytuje rozložení nebo zpracování událostí, což zlepšuje jeho výkon za běhu. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty. Slouží <xref:System.Windows.Media.DrawingVisual> k vytvoření vlastního vizuálního objektu. Další informace naleznete [v tématu Použití objektů DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual třída  
 Poskytuje <xref:System.Windows.Media.Media3D.Viewport3DVisual> most mezi <xref:System.Windows.Media.Visual> 2D <xref:System.Windows.Media.Media3D.Visual3D> a objekty. Třída <xref:System.Windows.Media.Media3D.Visual3D> je základní třídou pro všechny 3D vizuální prvky. Vyžaduje, <xref:System.Windows.Media.Media3D.Viewport3DVisual> abyste definovali hodnotu <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> a hodnotu. <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> Kamera umožňuje zobrazit scénu. Výřez stanoví, kde se projekce mapuje na 2D povrch. Další informace o 3D v tématu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Přehled [3D grafiky](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Kontejnervizuální třída  
 Třída <xref:System.Windows.Media.ContainerVisual> se používá jako kontejner pro <xref:System.Windows.Media.Visual> kolekci objektů. Třída <xref:System.Windows.Media.DrawingVisual> je odvozena <xref:System.Windows.Media.ContainerVisual> od třídy, což umožňuje obsahovat kolekci vizuálních objektů.  
  
### <a name="drawing-content-in-visual-objects"></a>Kreslení obsahu ve vizuálních objektech  
 Objekt <xref:System.Windows.Media.Visual> ukládá data vykreslení jako **seznam instrukcí vektorové grafiky**. Každá položka v seznamu instrukcí představuje nízkoúrovňovou sadu grafických dat a přidružených prostředků v serializovaném formátu. Existují čtyři různé typy dat vykreslení, které mohou obsahovat obsah výkresu.  
  
|Typ obsahu výkresu|Popis|  
|--------------------------|-----------------|  
|Vektorová grafika|Představuje vektorová grafická <xref:System.Windows.Media.Brush> data <xref:System.Windows.Media.Pen> a všechny přidružené a informace.|  
|Image|Představuje obrázek v rámci <xref:System.Windows.Rect>oblasti definované .|  
|Glyfů|Představuje výkres, který <xref:System.Windows.Media.GlyphRun>vykreslí , což je posloupnost glyfů ze zadaného prostředku písma. Takto je reprezentován text.|  
|Video|Představuje výkres, který vykresluje video.|  
  
 Umožňuje <xref:System.Windows.Media.DrawingContext> naplnit <xref:System.Windows.Media.Visual> vizuální obsah. Při použití <xref:System.Windows.Media.DrawingContext> příkazy kreslení objektu ve skutečnosti ukládáte sadu dat vykreslení, která bude později použita grafickým systémem; nekreslíte na obrazovku v reálném čase.  
  
 Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku, <xref:System.Windows.Controls.Button>například , ovládací prvek implicitně generuje vykreslovat data pro kreslení sám. Například nastavení <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti <xref:System.Windows.Controls.Button> způsobí, že ovládací prvek uložit reprezentaci vykreslování glyfu.  
  
 A <xref:System.Windows.Media.Visual> popisuje jeho obsah jako <xref:System.Windows.Media.Drawing> jeden nebo <xref:System.Windows.Media.DrawingGroup>více objektů obsažených v . A <xref:System.Windows.Media.DrawingGroup> také popisuje masky krytí, transformace, bitmapové efekty a další operace, které jsou použity na jeho obsah. <xref:System.Windows.Media.DrawingGroup>operace jsou použity v následujícím pořadí <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>při <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>vykreslení <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>obsahu: <xref:System.Windows.Media.DrawingGroup.Transform%2A>, , <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, , , a potom .  
  
 Následující obrázek znázorňuje <xref:System.Windows.Media.DrawingGroup> pořadí, ve kterém jsou operace použity během sekvence vykreslování.  
  
 ![Pořadí operací skupiny drawinggroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup  
  
 Další informace naleznete v [tématu Přehled objektů kreslení](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Obsah kreslení ve vizuální vrstvě  
 Nikdy přímo konkretizovat <xref:System.Windows.Media.DrawingContext>; Kontext výkresu však můžete získat z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Následující příklad načte <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> a a používá jej k nakreslení obdélníku.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Výčet obsahu výkresu ve vizuální vrstvě  
 Kromě jejich další použití, <xref:System.Windows.Media.Drawing> objekty také poskytují objektový model pro <xref:System.Windows.Media.Visual>výčet obsahu .  
  
> [!NOTE]
> Při výčtu obsahu vizuálu načítáte <xref:System.Windows.Media.Drawing> objekty a nikoli základní reprezentaci dat vykreslení jako seznam instrukcí vektorové grafiky.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu <xref:System.Windows.Media.DrawingGroup> k načtení hodnoty <xref:System.Windows.Media.Visual> a výčet.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak se vizuální objekty používají k vytváření ovládacích prvků  
 Mnoho objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci se skládá z jiných vizuálních objektů, což znamená, že mohou obsahovat různé hierarchie potomků objektů. Mnoho prvků uživatelského [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rozhraní v aplikaci , například ovládací prvky, se skládá z více vizuálních objektů představujících různé typy prvků vykreslování. <xref:System.Windows.Controls.Button> Ovládací prvek může například obsahovat řadu <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>dalších objektů, včetně , <xref:System.Windows.Controls.ContentPresenter>a <xref:System.Windows.Controls.TextBlock>.  
  
 Následující kód zobrazuje <xref:System.Windows.Controls.Button> ovládací prvek definovaný ve značkách.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Pokud byste měli vytvořit výčet vizuálních objektů, <xref:System.Windows.Controls.Button> které tvoří výchozí ovládací prvek, najdete hierarchii vizuálních objektů znázorněnou níže:  
  
 ![Diagram hierarchie vizuálních stromů](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 Ovládací <xref:System.Windows.Controls.Button> prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> obsahuje prvek, který zase <xref:System.Windows.Controls.ContentPresenter> obsahuje prvek. Prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> je zodpovědný za kreslení ohraničení <xref:System.Windows.Controls.Button>a pozadí pro rozhraní . Prvek <xref:System.Windows.Controls.ContentPresenter> je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button>. V tomto případě vzhledem k tomu, že zobrazujete text, <xref:System.Windows.Controls.ContentPresenter> prvek obsahuje <xref:System.Windows.Controls.TextBlock> prvek. Skutečnost, že <xref:System.Windows.Controls.Button> ovládací <xref:System.Windows.Controls.ContentPresenter> prvek používá znamená, že obsah může být <xref:System.Windows.Controls.Image> reprezentován jinými prvky, jako je například nebo geometrie, například <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Šablony ovládacích prvků  
 Klíčem k rozšíření ovládacího prvku do hierarchie <xref:System.Windows.Controls.ControlTemplate>ovládacích prvků je . Šablona ovládacího prvku určuje výchozí vizuální hierarchii ovládacího prvku. Když explicitně odkazujete na ovládací prvek, implicitně odkazujete na jeho vizuální hierarchii. Můžete přepsat výchozí hodnoty šablony ovládacího prvku a vytvořit tak vlastní vizuální vzhled ovládacího prvku. Můžete například upravit hodnotu barvy <xref:System.Windows.Controls.Button> pozadí ovládacího prvku tak, aby místo hodnoty plné barvy unavoval hodnotu barvy lineárního přechodu. Další informace naleznete [v tématu Button Styles and Templates](../controls/button-styles-and-templates.md).  
  
 Prvek uživatelského rozhraní, <xref:System.Windows.Controls.Button> například ovládací prvek, obsahuje několik seznamů instrukcí vektorové grafiky, které popisují celou definici vykreslování ovládacího prvku. Následující kód zobrazuje <xref:System.Windows.Controls.Button> ovládací prvek definovaný ve značkách.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Pokud byste měli vytvořit výčet vizuálníobjekty a seznamy <xref:System.Windows.Controls.Button> instrukcí vektorové grafiky, které obsahují ovládací prvek, najdete hierarchii objektů znázorněnou níže:  
  
 ![Diagram vizuálních stromových a vykreslovacích dat](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Ovládací <xref:System.Windows.Controls.Button> prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> obsahuje prvek, který zase <xref:System.Windows.Controls.ContentPresenter> obsahuje prvek. Prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> je zodpovědný za kreslení všech samostatných grafických prvků, které tvoří ohraničení a pozadí tlačítka. Prvek <xref:System.Windows.Controls.ContentPresenter> je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button>. V tomto případě, protože se zobrazuje <xref:System.Windows.Controls.ContentPresenter> obrázek, <xref:System.Windows.Controls.Image> prvek obsahuje prvek.  
  
 Existuje několik bodů, které je třeba poznamenat o hierarchii vizuálních objektů a seznamů instrukcí vektorové grafiky:  
  
- Pořadí v hierarchii představuje pořadí vykreslování informací výkresu. Z kořenového vizuálního prvku jsou podřízené prvky provázány zleva doprava, shora dolů. Pokud prvek má vizuální podřízené prvky, jsou provázány před na stejné úrovni elementu.  
  
- Prvky uzlu bez listu v hierarchii, například <xref:System.Windows.Controls.ContentPresenter>, se používají k obsahují podřízené prvky – neobsahují seznamy instrukcí.  
  
- Pokud vizuální prvek obsahuje seznam instrukcí vektorové grafiky i vizuální podřízené položky, je seznam instrukcí v nadřazeném vizuálním prvku vykreslen před výkresy v některém z vizuálních podřízených objektů.  
  
- Položky v seznamu instrukcí vektorové grafiky jsou vykresleny zleva doprava.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Vizuální strom  
 Vizuální strom obsahuje všechny vizuální prvky používané v uživatelském rozhraní aplikace. Vzhledem k tomu, že vizuální prvek obsahuje trvalé informace o výkresu, můžete si vizuální strom představit jako graf scény, který obsahuje všechny informace o vykreslení potřebné k vytvoření výstupu do zobrazovacího zařízení. Tento strom je akumulace všech vizuálních prvků vytvořených přímo aplikací, ať už v kódu nebo ve značkách. Vizuální strom také obsahuje všechny vizuální prvky vytvořené rozšíření šablony prvků, jako jsou ovládací prvky a datové objekty.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.StackPanel> prvek definovaný ve značkách.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Pokud byste měli vytvořit výčet vizuálních objektů, které tvoří <xref:System.Windows.Controls.StackPanel> prvek v příkladu značek, najdete hierarchii vizuálních objektů znázorněnou níže:  
  
 ![Diagram hierarchie vizuálních stromů](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Pořadí vykreslování  
 Vizuální strom určuje pořadí vykreslování vizuálních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a nakreslených objektů. Pořadí průchodu začíná kořenovým vizuálem, což je uzel nejvíce nahoře ve vizuálním stromu. Podřízené prvky kořenového jazyka jsou pak prohledány zleva doprava. Pokud má vizuál podřízené děti, jeho podřízené děti jsou procházet před vizuální sourozence. To znamená, že obsah podřízeného vizuálu je vykreslen před vlastním obsahem vizuálu.  
  
 ![Diagram pořadí vykreslování vizuálního stromu](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Kořenový obraz  
 **Kořenový vizuál** je prvek zcela nahoře v hierarchii vizuálního stromu. Ve většině aplikací je základní třída kořenového vizuálu buď <xref:System.Windows.Window> nebo <xref:System.Windows.Navigation.NavigationWindow>. Pokud jste však hostovali vizuální objekty v aplikaci Win32, kořenový vizuál by byl nejvrchní vizuál, který jste hostovali v okně Win32. Další informace naleznete v [tématu Výuka: Hostování vizuálních objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Vztah k logickému stromu  
 Logický strom [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v představuje prvky aplikace za běhu. I když nepracujete s tímto stromem přímo, toto zobrazení aplikace je užitečné pro pochopení dědičnosti vlastností a směrování událostí. Na rozdíl od vizuálního stromu může logický strom <xref:System.Windows.Documents.ListItem>představovat nevizuální datové objekty, například . V mnoha případech se logický strom mapuje velmi úzce na definice značek aplikace. Následující kód ukazuje <xref:System.Windows.Controls.DockPanel> prvek definovaný ve značkách.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Pokud byste měli vytvořit výčet logických objektů, které tvoří <xref:System.Windows.Controls.DockPanel> prvek v příkladu značky, najdete hierarchii logických objektů znázorněnou níže:  
  
 ![Stromový diagram](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram logického stromu  
  
 Vizuální strom i logický strom jsou synchronizovány s aktuální sadou prvků aplikace, což odráží jakékoli přidání, odstranění nebo úpravy prvků. Stromy však představují různá zobrazení aplikace. Na rozdíl od vizuálního stromu logický strom <xref:System.Windows.Controls.ContentPresenter> nerozbalí prvek ovládacího prvku. To znamená, že neexistuje přímá korespondence 1:1 mezi logickým stromem a vizuálním stromem pro stejnou sadu objektů. Ve skutečnosti vyvolání <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metody objektu **LogicalTreeHelper** a <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody objektu **VisualTreeHelper** pomocí stejného prvku jako parametr dává odlišné výsledky.  
  
 Další informace o logickém stromu naleznete v tématu [Stromy v WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Zobrazení vizuálního stromu pomocí xamlpadu  
 Nástroj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XamlPad poskytuje možnost pro zobrazení a prozkoumání vizuálního stromu, který odpovídá aktuálně definovanému obsahu XAML. Kliknutím na tlačítko **Zobrazit vizuální strom** na řádku nabídek zobrazíte vizuální strom. Následující ilustruje rozšíření obsahu XAML do uzlin vizuálního stromu v panelu **Průzkumník vizuálního stromu** na XamlPadu:  
  
 ![Panel Průzkumník a stromu v XamlPadu](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Všimněte <xref:System.Windows.Controls.Label>si, jak aplikace , <xref:System.Windows.Controls.TextBox>a <xref:System.Windows.Controls.Button> ovládací prvky zobrazují samostatnou hierarchii vizuálních objektů v panelu Průzkumník a vizuální **strom** na panelu XamlPad. Důvodem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je, <xref:System.Windows.Controls.ControlTemplate> že ovládací prvky mají, který obsahuje vizuální strom tohoto ovládacího prvku. Když explicitně odkazujete na ovládací prvek, implicitně odkazujete na jeho vizuální hierarchii.  
  
### <a name="profiling-visual-performance"></a>Profilování vizuálního výkonu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje sadu nástrojů pro profilování výkonu, které umožňují analyzovat chování aplikace za běhu a určit typy optimalizace výkonu, které můžete použít. Nástroj Vizuální profiler poskytuje bohaté grafické zobrazení dat o výkonu mapováním přímo do vizuálního stromu aplikace. V tomto snímku obrazovky využití **procesoru** části Visual Profiler poskytuje přesné rozpis u objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použití služeb, jako je například vykreslování a rozložení.  
  
 ![Výstup zobrazení vizuálního profileru](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Výstup zobrazení vizuálního profileru  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Chování vizuálního vykreslování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zavádí několik funkcí, které ovlivňují chování vykreslování vizuálních objektů: grafiku v zachovaném režimu, vektorovou grafiku a grafiku nezávislou na zařízení.  
  
### <a name="retained-mode-graphics"></a>Grafika zachovaného režimu  
 Jedním z klíčů k pochopení role Visual objektu je pochopit rozdíl mezi **okamžitý režim** a **zachovaný režim** grafické systémy. Standardní aplikace Win32 založená na GDI nebo GDI+ používá grafický systém v okamžitém režimu. To znamená, že aplikace je zodpovědná za překreslení části oblasti klienta, která je zrušena, z důvodu akce, jako je například velikost okna nebo objekt, který mění svůj vizuální vzhled.  
  
 ![Diagram sekvence vykreslení Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá systém se zachovaných režimů. To znamená, že aplikační objekty, které mají vizuální vzhled, definují sadu serializovaných kreslicích dat. Jakmile jsou data výkresu definována, systém je poté zodpovědný za odpověď na všechny požadavky na překreslení pro vykreslení aplikačních objektů. I za běhu můžete upravit nebo vytvořit aplikační objekty a stále spoléhat na systém pro odpovědi na požadavky na malování. Napájení v grafickém systému zachovaného režimu spočívá v tom, že informace o kreslení jsou vždy v serializovaném stavu aplikací, ale odpovědnost za vykreslování je ponechána systému. Následující diagram znázorňuje, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace závisí na odpovědi na požadavky na malování.  
  
 ![Diagram sekvence vykreslení WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentní překreslování  
 Jednou z největších výhod při používání grafiky v zachovaném režimu je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lze efektivně optimalizovat to, co je třeba překreslit v aplikaci. I v případě, že máte složitou scénu s různou úrovní krytí, obvykle není nutné psát speciální kód pro optimalizaci překreslování. Porovnejte to s win32 programování, ve kterém můžete vynaložit velké úsilí při optimalizaci aplikace minimalizací množství překreslování v oblasti aktualizace. Viz [Překreslování v oblasti aktualizace](/windows/desktop/gdi/redrawing-in-the-update-region) příklad typu složitosti, která se týká optimalizace překreslování v aplikacích win32.  
  
### <a name="vector-graphics"></a>Vektorová grafika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá **vektorovou grafiku** jako formát renderování dat. Vektorová grafika – která zahrnuje škálovatelnou vektorovou grafiku (SVG), metasoubory systému Windows (.wmf) a písma TrueType – ukládá data vykreslování a přenáší je jako seznam pokynů, které popisují, jak znovu vytvořit obraz pomocí grafických primitiv. Písma TrueType jsou například písma osnovy, která popisují sadu čar, křivek a příkazů, nikoli pole obrazových bodů. Jednou z klíčových výhod vektorové grafiky je možnost škálování na libovolnou velikost a rozlišení.  
  
 Na rozdíl od vektorové grafiky bitmapová grafika ukládá data vykreslení jako obrazovou reprezentaci obrazu, předem vykreslenou pro určité rozlišení. Jedním z klíčových rozdílů mezi bitmapovými a vektorovými grafickými formáty je věrnost původnímu zdrojovému obrazu. Pokud je například změněna velikost zdrojového obrazu, bitmapové grafické systémy obraz roztáhnou, zatímco vektorové grafické systémy změní velikost obrazu a zachová věrnost obrazu.  
  
 Následující obrázek znázorňuje zdrojový obrázek, jehož velikost byla změněna o 300 %. Všimněte si deformací, které se objevují, když je zdrojový obraz roztažen jako bitmapový grafický obraz, nikoli jako vektorový grafický obraz.  
  
 ![Rozdíly mezi rastrovou a vektorovou grafikou](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Následující značky ukazují <xref:System.Windows.Shapes.Path> dva definované prvky. Druhý prvek používá <xref:System.Windows.Media.ScaleTransform> ke změně velikosti výkresu pokyny prvního prvku o 300%. Všimněte si, že <xref:System.Windows.Shapes.Path> pokyny k výkresu v prvcích zůstávají nezměněny.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>O rozlišení a nezávislé grafiky zařízení  
 Velikost textu a grafiky na obrazovce určují dva systémové faktory: rozlišení a DPI. Rozlišení popisuje počet pixelů, které se zobrazí na obrazovce. Jak se rozlišení zvyšuje, obrazové body se zmenšují, což způsobuje, že grafika a text vypadají menší. Grafika zobrazená na monitoru nastavená na 1024 x 768 se při změně rozlišení na 1600 x 1200 zobrazí mnohem menší.  
  
 Jiné nastavení systému, DPI, popisuje velikost obrazovky palce v pixelech. Většina systémů Windows má DPI 96, což znamená, že obrazovka palec je 96 pixelů. Zvýšením nastavení DPI se obrazovka zvětší; snížením dpi zmenší obrazovku. To znamená, že palec obrazovky nemá stejnou velikost jako palec reálného světa; na většině systémů, to asi není. Jak zvýšíte DPI, grafika a text podporující DPI se zvětšují, protože jste zvětšili velikost obrazovky. Zvýšení dpi může usnadnit čtení textu, zejména při vysokém rozlišení.  
  
 Ne všechny aplikace jsou podporující DPI: některé používají hardwarové pixely jako primární měrnou jednotku; změna systému DPI nemá žádný vliv na tyto aplikace. Mnoho jiných aplikací používá jednotky podporující DPI k popisu velikosti písma, ale používá obrazové body k popisu všeho ostatního. Vytvoření dpi příliš malé nebo příliš velké může způsobit problémy s rozložením pro tyto aplikace, protože text aplikací se škáluje s nastavením DPI systému, ale uživatelské rozhraní aplikací není. Tento problém byl odstraněn pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace vyvinuté pomocí .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje automatické škálování pomocí pixelu nezávislého na zařízení jako primární měrné jednotky namísto hardwarových pixelů; grafika a text měřítko správně bez jakékoli další práci od vývojáře aplikace. Následující obrázek znázorňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příklad zobrazení textu a grafiky v různých nastaveních DPI.  
  
 ![Grafika a text v různých nastaveních DPI](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika a text v různých nastaveních DPI  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>Třída VisualTreeHelper  
 Třída <xref:System.Windows.Media.VisualTreeHelper> je statická pomocná třída, která poskytuje funkce nižší úrovně pro programování na úrovni vizuálních objektů, což je užitečné ve velmi specifických scénářích, jako je například vývoj vysoce výkonných vlastních ovládacích prvků. Ve většině případů objekty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] architektury vyšší <xref:System.Windows.Controls.Canvas> úrovně, jako jsou například a <xref:System.Windows.Controls.TextBlock>, nabízejí větší flexibilitu a snadné použití.  
  
### <a name="hit-testing"></a>Testování přístupů  
 Třída <xref:System.Windows.Media.VisualTreeHelper> poskytuje metody pro testování přístupů na vizuální objekty, když výchozí podpora testu přístupů nesplňuje vaše potřeby. Metody ve <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> <xref:System.Windows.Media.VisualTreeHelper> třídě můžete použít k určení, zda je hodnota souřadnice geometrie nebo bodu v mezích daného objektu, například ovládacího prvku nebo grafického prvku. Můžete například použít testování přístupů k určení, zda klepnutí myší v ohraničujícím obdélníku objektu spadá do geometrie kruhu: Můžete také přepsat výchozí implementaci testování přístupů k provedení vlastního testu přístupů Výpočty.  
  
 Další informace o testování přístupů naleznete [v tématu Testování přístupů ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Výčet vizuálního stromu  
 Třída <xref:System.Windows.Media.VisualTreeHelper> poskytuje funkce pro výčet členů vizuální strom. Chcete-li načíst <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> nadřazenou položku, zavolejte metodu. Chcete-li načíst podřízené nebo přímé potomek <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> vizuální objekt, volání metody. Tato metoda vrátí <xref:System.Windows.Media.Visual> podřízený nadřazený na zadaný index.  
  
 Následující příklad ukazuje, jak vytvořit výčet všech potomků vizuálního objektu, což je technika, kterou můžete chtít použít, pokud jste měli zájem o serializaci všech informací o vykreslování hierarchie vizuálních objektů.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Ve většině případů je logický strom užitečnější reprezentací prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci. Přestože neupravujete logický strom přímo, toto zobrazení aplikace je užitečné pro pochopení dědičnosti vlastností a směrování událostí. Na rozdíl od vizuálního stromu může logický strom <xref:System.Windows.Documents.ListItem>představovat nevizuální datové objekty, například . Další informace o logickém stromu naleznete v tématu [Stromy v WPF](../advanced/trees-in-wpf.md).  
  
 Třída <xref:System.Windows.Media.VisualTreeHelper> poskytuje metody pro vrácení ohraničující obdélník vizuální objekty. Ohraničovací obdélník vizuálního objektu <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>můžete vrátit voláním . Ohraničující obdélník všech potomků vizuálního objektu, včetně samotného <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>vizuálního objektu, můžete vrátit voláním . Následující kód ukazuje, jak byste vypočítali ohraničující obdélník vizuálního objektu a všech jeho potomků.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Použití objektů DrawingVisual](using-drawingvisual-objects.md)
- [Kurz: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optimalizace výkonu aplikace WPF](../advanced/optimizing-wpf-application-performance.md)
