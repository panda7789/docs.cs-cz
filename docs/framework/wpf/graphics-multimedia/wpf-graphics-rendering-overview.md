---
title: Přehled vykreslování grafiky WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: a0400ce32dc6dab2585a8d5e76ff8d416fae24c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764977"
---
# <a name="wpf-graphics-rendering-overview"></a>Přehled vykreslování grafiky WPF
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální vrstvy. Zaměřuje se na roli <xref:System.Windows.Media.Visual> třídy pro vykreslování podpora v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu.  

<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Role vizuální objekty  
 <xref:System.Windows.Media.Visual> Třída je základní abstrakce, ze kterých každý <xref:System.Windows.FrameworkElement> objekt je odvozen. Slouží také jako vstupní bod pro vytváření nových ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a v mnoha způsoby, jak si lze představit jako popisovač okna (HWND) v modelu aplikací Win32.  
  
 <xref:System.Windows.Media.Visual> Objekt je základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt, jehož primární role je poskytnout podporu vykreslování. Ovládací prvky uživatelského rozhraní, jako například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TextBox>, odvozovat <xref:System.Windows.Media.Visual> třídy a použít jej pro zachování jejich datech pro vykreslení. <xref:System.Windows.Media.Visual> Objekt, který poskytuje podporu pro:  
  
- Zobrazení výstupu: Vykreslování trvalý, serializovat výkresu vykreslovaného vizuálního obsahu.  
  
- Transformace: Provádění transformací ve vizuálu.  
  
- Omezení: Poskytuje podporu oblasti výstřižek vizuálu.  
  
- Testování průchodu: Určení, zda souřadnice nebo geometrie je obsažen v mezích vizuálu.  
  
- Ohraničující pole výpočty: Určení ohraničující obdélník vizuálu.  
  
 Ale <xref:System.Windows.Media.Visual> objekt nezahrnuje podporu pro jiné vykreslovací funkce, jako například:  
  
- Zpracování událostí  
  
- Rozložení  
  
- Styly  
  
- Vytváření datových vazeb  
  
- Globalizace  
  
 <xref:System.Windows.Media.Visual> je vystavena jako veřejné abstraktní třída, ze kterého musí být podřízené třídy odvozeny. Následující obrázek znázorňuje hierarchii vizuální objekty, které jsou vystaveny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagram tříd odvozených z vizuální objekty](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>DrawingVisual Class  
 <xref:System.Windows.Media.DrawingVisual> Představuje jednoduché kreslení třídu, která se použije k vykreslení obrazce, Image nebo text. Tato třída se považuje za jednoduché, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje výkon modulu runtime. Z tohoto důvodu jsou ideální pro pozadí a klipart kreslení. <xref:System.Windows.Media.DrawingVisual> Slouží k vytvoření vlastní vizuální objekty. Další informace najdete v tématu [použití objektů DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Třída Viewport3DVisual  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> Představuje most mezi 2D <xref:System.Windows.Media.Visual> a <xref:System.Windows.Media.Media3D.Visual3D> objekty. <xref:System.Windows.Media.Media3D.Visual3D> Třída je základní třída pro všechny 3D vizuální prvky. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Vyžaduje definování <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> hodnotu a <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> hodnotu. Fotoaparátu/kamery vám umožní zobrazit scénu. Zobrazení stanoví, kde 2D surface mapuje projekce. Další informace o 3D v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [přehled 3D grafiky](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Třída ContainerVisual  
 <xref:System.Windows.Media.ContainerVisual> Třída se používá jako kontejner pro kolekci <xref:System.Windows.Media.Visual> objekty. <xref:System.Windows.Media.DrawingVisual> Třída odvozena z <xref:System.Windows.Media.ContainerVisual> třídy, díky kterému jej tak, aby obsahovala sadu vizuální objekty.  
  
### <a name="drawing-content-in-visual-objects"></a>Obsahu v vizuálních objektů  
 A <xref:System.Windows.Media.Visual> ukládá svoje data vykreslení jako **seznam instrukcí vektorové grafiky**. Každá položka v seznamu instrukce představuje nízké úrovně sadu daty grafiky a přidružené prostředky v serializovaný formát. Existují čtyři různé typy vykreslení dat, který může obsahovat vykreslování obsahu.  
  
|Typ obsahu kreslení|Popis|  
|--------------------------|-----------------|  
|Vektorová grafika|Představuje vektorové grafiky data a všechny přidružené <xref:System.Windows.Media.Brush> a <xref:System.Windows.Media.Pen> informace.|  
|Image|Představuje image v oblasti určené <xref:System.Windows.Rect>.|  
|Piktogram|Představuje výkresu, který vykreslí <xref:System.Windows.Media.GlyphRun>, což je posloupnost glyfy z určené písmo prostředku. To je, jak je text reprezentován.|  
|Video|Představuje výkresu, který vykreslí videa.|  
  
 <xref:System.Windows.Media.DrawingContext> Umožňuje naplnit <xref:System.Windows.Media.Visual> s vizuální obsah. Při použití <xref:System.Windows.Media.DrawingContext> příkazy vykreslování objektu, jsou ve skutečnosti ukládání sadu vykreslování data, která se později použije systém grafiky; nejsou kreslení na obrazovku v reálném čase.  
  
 Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, například <xref:System.Windows.Controls.Button>, ovládací prvek implicitně generuje vykreslování data pro kreslení samotný. Například nastavení <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> způsobí, že ovládací prvek pro uložení vykreslování reprezentace piktogram.  
  
 A <xref:System.Windows.Media.Visual> popisuje jeho obsah jako jednu či více <xref:System.Windows.Media.Drawing> objektů obsažených v rámci <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> také popisuje masky krytí, transformace, bitmapových efektů a další operace, které se použijí k jejímu obsahu. <xref:System.Windows.Media.DrawingGroup> operace se použijí v uvedeném pořadí, v případě, že obsah se vykreslí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a potom <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující obrázek znázorňuje pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> operací se použijí během pořadí vykreslování.  
  
 ![DrawingGroup – pořadí operací](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup –  
  
 Další informace najdete v tématu [kreslení objekty – přehled](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Obsahu ve vizuální vrstvě  
 Jste nikdy přímo vytvořit instanci <xref:System.Windows.Media.DrawingContext>; můžete však získat výkresu kontext z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Následující příklad načte <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> a použije ho k vykreslení obdélníku.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Výčet obsahu ve vizuální vrstvě  
 Kromě jejich použití <xref:System.Windows.Media.Drawing> objekty také neposkytuje objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Když jsou výčet obsah vizuálu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní reprezentace dat vykreslení jako seznam vektorové grafiky instrukce.  
  
 V následujícím příkladu <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak vizuálních objektů se používají k vytvoření ovládacích prvků  
 Mnoho objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se skládá z jiných vizuálních objektů, což znamená, které obsahují různé hierarchie odvozené objekty. Mnoho uživatele prvky v rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jako je například ovládací prvky, se skládá z několika vizuální objekty, které představují různé druhy elementům vykreslování. Například <xref:System.Windows.Controls.Button> ovládacího prvku může obsahovat řadu jiných objektů, včetně <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, a <xref:System.Windows.Controls.TextBlock>.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.Button> prvek definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Pokud byste chtěli vytvořit výčet vizuální objekty, které tvoří výchozí <xref:System.Windows.Controls.Button> ovládací prvek, jehož ekvivalent byste našli hierarchie vizuální objekty znázorněno níže:  
  
 ![Diagram hierarchie vizuální strom](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 <xref:System.Windows.Controls.Button> Obsahuje ovládací prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který zase obsahuje <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element je zodpovědné za vykreslování ohraničení a pozadí <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Element je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button>. V takovém případě od té doby zobrazujete text, <xref:System.Windows.Controls.ContentPresenter> obsahuje element <xref:System.Windows.Controls.TextBlock> elementu. Skutečnost, který <xref:System.Windows.Controls.Button> používá ovládací prvek <xref:System.Windows.Controls.ContentPresenter> znamená, že obsah může být reprezentována další prvky, jako <xref:System.Windows.Controls.Image> nebo geometrie, například <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Šablony ovládacích prvků  
 Je klíčem k rozbalení ovládacího prvku do hierarchie ovládacích prvků <xref:System.Windows.Controls.ControlTemplate>. Šablony ovládacího prvku určuje výchozí hierarchii visual pro ovládací prvek. Když explicitně odkazovat na ovládací prvek, je implicitně odkazovat hierarchii visual. Můžete přepsat výchozí hodnoty pro šablonu ovládacího prvku k vytvoření vlastní vzhled ovládacího prvku. Můžete například změnit hodnotu barvy pozadí <xref:System.Windows.Controls.Button> řídit tak, aby používala hodnotu lineárního přechodu barvy místo hodnoty barvy. Další informace najdete v tématu [styly a šablony tlačítek](../controls/button-styles-and-templates.md).  
  
 Uživatel rozhraní element, jako například <xref:System.Windows.Controls.Button> řídit, obsahuje několik vektorové grafiky instrukce seznamy, které popisují definici celý vykreslování ovládacího prvku. Následující kód ukazuje <xref:System.Windows.Controls.Button> prvek definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Pokud byste chtěli vytvořit výčet vizuální objekty a vektorové grafiky instrukce seznamy, které tvoří <xref:System.Windows.Controls.Button> ovládací prvek, jehož ekvivalent byste našli hierarchii objektů znázorněno níže:  
  
 ![Diagram vizuální strom a datech pro vykreslení](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 <xref:System.Windows.Controls.Button> Obsahuje ovládací prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který zase obsahuje <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element je zodpovědné za vykreslování všechny samostatné grafické prvky, které tvoří ohraničení a pozadí tlačítka. <xref:System.Windows.Controls.ContentPresenter> Element je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button>. V tomto případě od té doby zobrazujete bitové kopie, <xref:System.Windows.Controls.ContentPresenter> obsahuje element <xref:System.Windows.Controls.Image> elementu.  
  
 Existuje několik bodů byste měli znát hierarchie vizuální objekty a vektorové grafiky instrukce seznamy:  
  
- Řazení v hierarchii představuje pořadí vykreslování informací o vykreslování. Z kořenové vizuální prvek jsou podřízené prvky procházet zleva doprava a shora dolů. Pokud má element visual podřízené elementy, jsou vyčerpán před elementu na stejné úrovni.  
  
- Elementy bez listový uzel v hierarchii, jako například <xref:System.Windows.Controls.ContentPresenter>, se používají k obsahovat podřízené elementy – neobsahují instrukce seznamy.  
  
- Pokud vizuální prvek obsahuje seznam vektorové grafiky instrukce a podřazené prvky prvku visual, seznamu instrukce v nadřazeného prvku visual je vykreslen před kreslení v některém z visual podřízené objekty.  
  
- Položky v seznamu instrukce vektorové grafiky jsou vykreslovány zleva doprava.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Vizuální strom  
 Vizuální strom obsahuje všechny vizuální prvky, které jsou použity v uživatelském rozhraní aplikace. Protože vizuální prvek obsahuje informace o trvalý kreslení, si můžete představit vizuálního stromu jako graf scén, obsahující všechny vykreslit informace potřebné k vytváření výstup do zobrazení zařízení. Tento strom je akumulací všech vizuálních prvků vytvořených přímo aplikací, ať už v kódu nebo v kódu. Vizuální strom obsahuje také všech vizuálních prvků vytvořených rozšířením šablony elementů, jako je například ovládací prvky a datové objekty.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.StackPanel> element definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Pokud byste chtěli vytvořit výčet vizuální objekty, které tvoří <xref:System.Windows.Controls.StackPanel> element v příkladu kódu, jehož ekvivalent byste našli hierarchie vizuální objekty znázorněno níže:  
  
 ![Diagram hierarchie vizuální strom](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Pořadí vykreslování  
 Vizuální strom určuje pořadí vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual a vykreslení objektů. Pořadí procházení začíná vizuál, root, což je nejvyšší uzel ve vizuálním stromu. Podřízené kořenové vizuálu je pak provázán, zleva doprava. Pokud má vizuál podřízené položky, je před vizuálu na stejné úrovni provázán své podřízené objekty. To znamená, že obsah pro podřízenou položku visual je vykreslen před vizuálu vlastní obsah.  
  
 ![Diagram pořadí vykreslování vizuální strom](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>Kořenové Vizuálu  
 **Kořenové visual** je nejvyšší element v hierarchii vizuálního stromu. Ve většině aplikací základní třídy visual kořenový adresář je buď <xref:System.Windows.Window> nebo <xref:System.Windows.Navigation.NavigationWindow>. Pokud byly hostování vizuální objektů v aplikaci Win32, ale kořenové visual by vizuálu úplně nahoře, které byly hostování v okně Win32. Další informace najdete v tématu [kurzu: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relaci logického stromu  
 V logickém stromu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] představuje prvky aplikace v době běhu. I když není tento strom manipulovat přímo, je důležité pochopit vlastnosti a směrování událostí toto zobrazení aplikace. Na rozdíl od vizuálního stromu, Logická stromová struktura představují nevizuálních datové objekty, jako například <xref:System.Windows.Documents.ListItem>. V mnoha případech Logická stromová struktura úzce mapuje na definice kódu aplikace. Následující kód ukazuje <xref:System.Windows.Controls.DockPanel> element definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Pokud byste chtěli vytvořit výčet logické objekty, které tvoří <xref:System.Windows.Controls.DockPanel> element v příkladu kódu, jehož ekvivalent byste našli hierarchie logické objekty znázorněno níže:  
  
 ![Diagram stromu](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram logického stromu  
  
 Vizuální strom i Logická stromová struktura jsou synchronizovány s aktuální sadu elementů aplikace odráží všechny přidání, odstranění ani změnu prvků. Stromy však k dispozici různá zobrazení aplikace. Na rozdíl od vizuální strom logického stromu Nerozbaluje ovládacího prvku <xref:System.Windows.Controls.ContentPresenter> elementu. To znamená, že neexistuje žádná shoda mezi logického stromu a vizuální strom pro stejnou sadu objektů s přímým přístupem. Ve skutečnosti volání **LogicalTreeHelper** objektu <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metoda a **VisualTreeHelper** objektu <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metodu pomocí stejného elementu jako parametr vrací odlišné výsledky .  
  
 Další informace o logickém stromu, naleznete v tématu [stromy v subsystému WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Zobrazení s nástroj XamlPad vizuální strom  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nástroj, nástroj XamlPad, poskytuje možnost pro zobrazením a koumáním vizuálního stromu, který odpovídá na aktuálně definovaných [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] obsah. Klikněte na tlačítko **zobrazit vizuální strom** tlačítko na panelu nabídek, chcete-li zobrazit ve vizuálním stromu. Následující obrázek znázorňuje rozšíření [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do vizuálního stromu uzlů v obsahu **vizuální stromové struktury Průzkumníka** panel ovládacího prvku nástroj XamlPad:  
  
 ![Panel Průzkumníka vizuálního stromu v nástroj XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Všimněte si, že jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, a <xref:System.Windows.Controls.Button> hierarchie samostatné vizuální objekty v zobrazení ovládacích prvků každé **vizuální stromové struktury Průzkumníka** panel ovládacího prvku nástroj XamlPad. Důvodem je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mají <xref:System.Windows.Controls.ControlTemplate> vizuálním stromu ovládacího prvku, který obsahuje. Když explicitně odkazovat na ovládací prvek, je implicitně odkazovat hierarchii visual.  
  
### <a name="profiling-visual-performance"></a>Profilace výkonu Visual  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu nástrojů, které vám umožní analyzovat chování za běhu aplikace a určete typy optimalizace výkonu, které můžete použít profilování výkonu. Tento nástroj Visual Profiler nabízí bohatě vybaveným a grafické zobrazení dat výkonu mapováním přímo do vaší aplikace vizuálního stromu. Na tomto snímku obrazovky **využití procesoru** části Visual Profiler je rozpis přesné použití objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služby, jako je vykreslování a rozložení.  
  
 ![Zobrazení výstupu Visual Profiler](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Zobrazit výstup Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Chování Visual vykreslování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zavádí několik funkcí, které ovlivňují chování vykreslování vizuálních objektů: uchovávají režimu grafiky, vektorovou grafiku a nezávislé grafiky zařízení.  
  
### <a name="retained-mode-graphics"></a>Zachované režimu grafiky  
 Jeden z klíčů k pochopení roli Visual objektu je pochopit rozdíl mezi **přímý režim** a **uchovávají režimu** grafické systémy. Standardní aplikace Win32 na základě GDI nebo rozhraní GDI + používá systém grafiky přímý režim. To znamená, že aplikace je zodpovědná za překreslení část oblasti klienta, která je zrušena z důvodu akce, jako je časové období, během změny velikosti, nebo objekt změnou jeho vizuálního vzhledu.  
  
 ![Diagram pořadí vykreslování Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] využívá uchovanou režimu systém. To znamená, že objekty aplikací, které mají vizuálního vzhledu definovat sadu výkresu serializovaná data. Po vykreslení dat je definován, systém je po tomto datu za reagovat na všechny požadavky na repaint pro vykreslení objektů aplikace. I v době běhu můžete upravit nebo vytvořit objekty aplikací a stále spoléhají na systém pro reakce na žádosti vykreslení. Výkon systému grafiky uchovanou režimu je, že kreslení informace je vždy trvale uložen v serializovaný stav aplikace, ale vykreslování odpovědnost ponecháno na systém. Následující diagram znázorňuje, jak aplikace spoléhá na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro zpracování požadavků k vykreslení.  
  
 ![Diagram pořadí vykreslování WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentní překreslování  
 Jeden z největších výhod použití uchovanou režimu grafiky je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete efektivně optimalizovat, co je potřeba se měl překreslit v aplikaci. I v případě, že máte komplexní scény s různými úrovněmi krytí, obvykle není potřeba psát kód speciální optimalizovat překreslení. Porovnejte s programování Win32, ve kterém strávíte spoustu úsilí v optimalizaci aplikace minimalizací množství překreslování v oblasti aktualizací. Zobrazit [překreslování v oblasti aktualizací](/windows/desktop/gdi/redrawing-in-the-update-region) příklad typu složitost součástí optimalizace překreslování v aplikacích Win32.  
  
### <a name="vector-graphics"></a>Vektorová grafika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá **vektorové grafiky** jako jeho formát vykreslování data. Vektorové grafiky, mezi které patří grafiky SVG (Scalable Vector), Windows metasoubory (WMF) a písma TrueType – ukládání datech pro vykreslení a předá je jako seznam pokyny, které popisují, jak znovu vytvořit image pomocí grafiky primitiv. Písma TrueType jsou například osnovy písma, která popisují sadu čar, křivek a příkazy, nikoli pole v pixelech. Jednou z klíčových výhod vektorové grafiky je schopnost škálovat na jakékoli velikosti a řešení.  
  
 Na rozdíl od vektorovou grafiku ukládat rastrový obrázek datech pro vykreslení jako reprezentace – obrazový bitové kopie, které jsou předem vykreslené pro konkrétní řešení. Jedním z hlavní rozdíly mezi rastrového obrázku a vektorové grafické formáty je věrností na původní zdroj image. Například při změně velikosti zdrojového obrazu grafické systémy rastrový obrázek roztáhnout obrázek, zatímco vektorové grafiky systémy změna měřítka obrázku, zachovat věrnost bitové kopie.  
  
 Následující obrázek znázorňuje zdrojového obrazu, který 300 % se změnila. Všimněte si, že narušení, které se zobrazí při zdrojového obrázku je roztažení jako rastrový obrázek grafiky spíše než škálování jako vektorovou grafiku.  
  
 ![Rozdíly mezi rastrové a vektorové grafiky](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Následující kód ukazuje dva <xref:System.Windows.Shapes.Path> prvky definované. Druhý prvek používá <xref:System.Windows.Media.ScaleTransform> ke změně velikosti vykreslování pokynů prvního prvku 300 %. Všimněte si, že vykreslování pokynů <xref:System.Windows.Shapes.Path> prvky zůstanou beze změny.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Informace o řešení a nezávislé na zařízení grafiky  
 Existují dva faktory systému, které určují velikost textu a grafiky na obrazovce: překlad IP adres a DPI. Rozlišení popisuje počet pixelů, které se zobrazí na obrazovce. Protože řešení získá vyšší, získat menší, způsobí grafiku a text, který má být menší pixelů. Řešení se změní na 1600 × 1200 zobrazí obrázek zobrazené na monitoru nastavena na 1024 × 768 mnohem menší.  
  
 Další nastavení systému, DPI, popisuje, velikost obrazovky palec v pixelech. Většina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systémy mají DPI 96, což znamená, že palec obrazovky je 96 pixelů. Zvýšení nastavení DPI díky obrazovky palec větší; snížení počtu bodů na PALEC díky palec obrazovky menší. To znamená, že obrazovka palce není stejné velikosti jako reálné palec; ve většině systémů je pravděpodobně není. Zvyšuje DPI stát rozlišením DPI grafiku a text větší, protože mimo jiné zvětšili velikost palec obrazovky. Zvýšení počtu bodů na PALEC může usnadnit textu pro čtení, zejména na vysoké rozlišení.  
  
 Ne všechny aplikace jsou s ohledem na DPI: některé pixely hardwaru používají jako primární jednotka měření; Změna systému DPI nemá žádný vliv na tyto aplikace. Mnoho dalších aplikací s ohledem na DPI jednotky můžete popisují velikosti písma, ale pixelů použít k podrobnému popisu, všechno ostatní. Nastavení DPI příliš malá nebo moc velký může způsobovat problémy rozložení pro tyto aplikace, protože aplikace text škáluje s nastavením DPI v systému, ale nikoli uživatelského rozhraní aplikace. Tento problém se odstranilo u aplikací vyvinutých pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje automatické škálování s využitím nezávislé pixelů zařízení jako její primární jednotka měření, namísto hardwaru pixelů Grafika a text škálování správně bez další práce z vývojář aplikace. Následující obrázek znázorňuje příklad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] textu a grafiky se zobrazí na různá nastavení DPI.  
  
 ![Grafika a textu v jiné nastavení DPI](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika a textu v jiné nastavení DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Třída VisualTreeHelper  
 <xref:System.Windows.Media.VisualTreeHelper> Třídu je statickou pomocnou třídu, která poskytuje pro programování na úrovni vizuální objekty, což je užitečné v konkrétních situacích, jako je například vývoj vlastních ovládacích prvků výkonné funkce nízké úrovně. Ve většině případů by vyšší úrovni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework objekty, jako například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.TextBlock>, nabízejí větší flexibilitu a snadnost použití.  
  
### <a name="hit-testing"></a>Testování průchodu  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje metody pro přístupů k testování pro vizuální objekty, pokud výchozí spuštění testu podporu nevyhovuje vašim potřebám. Můžete použít <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody v <xref:System.Windows.Media.VisualTreeHelper> třídu k určení, zda je geometrie nebo bod souřadnic hodnota v rámci hranice daný objekt, jako je například ovládací prvek nebo grafický element. Například můžete použít volání testování k určení, zda kliknutí myší v rámci ohraničující obdélník objektu spadá do geometrie kruh, které můžete také přepsat výchozí implementaci přístupů testování provádět vlastní test přístupů výpočty.  
  
 Další informace o volání testování, najdete v části [spuštění testování ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Vytváření výčtu vizuální strom  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje funkce pro vytváření výčtu členů vizuálního stromu. Chcete-li získat nadřazenou položku, zavolejte <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metody. K načtení podřízených nebo přímé následník objektu visual volání <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody. Tato metoda vrátí podřízený <xref:System.Windows.Media.Visual> nadřazeného prvku na zadaném indexu.  
  
 Následující příklad ukazuje, jak vytvořit výčet všech potomků visual objektu, který je technika, kterou chcete použít, pokud by vás zajímaly serializaci všechny informace vykreslení hierarchie vizuální objekty.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Ve většině případů je logická stromová struktura užitečnější reprezentace prvky v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. I když Logická stromová struktura neprovádějte žádné změny přímo, je důležité pochopit vlastnosti a směrování událostí toto zobrazení aplikace. Na rozdíl od vizuálního stromu, Logická stromová struktura představují nevizuálních datové objekty, jako například <xref:System.Windows.Documents.ListItem>. Další informace o logickém stromu, naleznete v tématu [stromy v subsystému WPF](../advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje metody pro vrácení ohraničující obdélník vizuální objekty. Může vrátit ohraničující obdélník visual objektu voláním <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Můžete se vrátit ohraničující obdélník všechny následníky vizuální objekty, třeba visual objektu samotného, tak, že volání <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Následující kód ukazuje, jak by vypočítat ohraničující obdélník vizuální objekty a všech jejích potomků.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Použití objektů DrawingVisual](using-drawingvisual-objects.md)
- [Kurz: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optimalizace výkonu aplikace WPF](../advanced/optimizing-wpf-application-performance.md)
