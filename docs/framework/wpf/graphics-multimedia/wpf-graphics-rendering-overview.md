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
ms.openlocfilehash: 305af1025abb98950d90f46e75a9f261704a8ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566727"
---
# <a name="wpf-graphics-rendering-overview"></a>Přehled vykreslování grafiky WPF
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual vrstvy. Zaměřuje se na roli <xref:System.Windows.Media.Visual> třídy pro vykreslování podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Role Visual objektu  
 <xref:System.Windows.Media.Visual> Třída je základní abstrakci, ze kterého každých <xref:System.Windows.FrameworkElement> odvozuje objektu. Slouží také jako vstupní bod pro zápis nových ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a v mnoha směrech můžete představit jako popisovač okna (HWND) v modelu aplikace Win32.  
  
 <xref:System.Windows.Media.Visual> Objekt je jádro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt, jehož primární role je poskytovat podporu pro vykreslování. Ovládací prvky uživatelského rozhraní, jako například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TextBox>, jsou odvozeny od <xref:System.Windows.Media.Visual> třídy a použít jej pro zachování jejich datech pro vykreslení. <xref:System.Windows.Media.Visual> Objekt poskytuje podporu pro:  
  
-   Výstup zobrazení: vykreslování trvalý, serializovat kreslení obsah vizuál.  
  
-   Transformace: Provádění transformací na vizuál.  
  
-   Výstřižek: Poskytnutí výstřižek oblasti podpory pro zobrazení.  
  
-   Testování průchodu: určení, zda souřadnice nebo geometry je obsažena v hranice vizuál.  
  
-   Ohraničujícího pole výpočty: stanovení ohraničující obdélník zobrazení.  
  
 Ale <xref:System.Windows.Media.Visual> objekt nezahrnuje podporu jiných vykreslování funkcí, jako například:  
  
-   Zpracování událostí  
  
-   Rozložení  
  
-   Styly  
  
-   Datová vazba  
  
-   Globalizace  
  
 <xref:System.Windows.Media.Visual> je k dispozici jako veřejné abstraktní třída, ze které musí být odvozen podřízenými třídami. Následující obrázek znázorňuje hierarchii vizuální objekty, které jsou zveřejněné v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagram třídy odvozené z Visual objektu](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Hierarchie tříd Visual  
  
### <a name="drawingvisual-class"></a>DrawingVisual – třída  
 <xref:System.Windows.Media.DrawingVisual> Představuje nenáročné, kreslení třídu, která se použije k vykreslení tvarů, Image nebo text. Tato třída se považuje za lightweight, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje výkon jeho modulu runtime. Z toho důvodu jsou ideální pro pozadí a vytvoříte čára. <xref:System.Windows.Media.DrawingVisual> Slouží k vytvoření vlastní vizuální objekt. Další informace najdete v tématu [pomocí objekty DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual – třída  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> Poskytuje most mezi 2D <xref:System.Windows.Media.Visual> a <xref:System.Windows.Media.Media3D.Visual3D> objekty. <xref:System.Windows.Media.Media3D.Visual3D> Třída je základní třída pro všechny 3D vizuální prvky. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Vyžaduje definování <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> hodnotu a <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> hodnotu. Kamera vám umožní zobrazit scény. Zobrazení určuje, kde projekce mapy na 2D plochu. Další informace o 3D v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [3D přehled grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>ContainerVisual – třída  
 <xref:System.Windows.Media.ContainerVisual> Třída slouží jako kontejner pro kolekci <xref:System.Windows.Media.Visual> objekty. <xref:System.Windows.Media.DrawingVisual> Třída odvozená z <xref:System.Windows.Media.ContainerVisual> třída, díky kterému jej tak, aby obsahovala kolekce visual objektů.  
  
### <a name="drawing-content-in-visual-objects"></a>Kreslení obsah vizuální objekty  
 A <xref:System.Windows.Media.Visual> objekt ukládá data vykreslení jako **vektorové grafiky instrukce seznamu**. Každá položka v seznamu instrukce představuje nízké úrovně sadu grafiky data a související prostředky v serializovaných formátu. Existují čtyři typy vykreslování data, která může obsahovat vykreslování obsahu.  
  
|Kreslení typ obsahu|Popis|  
|--------------------------|-----------------|  
|Vektorová grafika|Představuje vektorové grafiky data a všechny přidružené <xref:System.Windows.Media.Brush> a <xref:System.Windows.Media.Pen> informace.|  
|Image|Reprezentuje obrázek v oblasti definované <xref:System.Windows.Rect>.|  
|Glyfy|Představuje kreslení, který vykreslí <xref:System.Windows.Media.GlyphRun>, což je posloupnost glyfů z určeného písma prostředku. Toto je, jak je reprezentována text.|  
|Video|Představuje kreslení, který vykreslí videa.|  
  
 <xref:System.Windows.Media.DrawingContext> Umožňuje naplnit <xref:System.Windows.Media.Visual> s visual obsahem. Při použití <xref:System.Windows.Media.DrawingContext> příkazy kreslení objektu, ve skutečnosti ukládáte sadu vykreslování data, která se později použije systémem grafiky; nejsou kreslení na obrazovku v reálném čase.  
  
 Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řídit, například <xref:System.Windows.Controls.Button>, ovládacího prvku implicitně generuje vykreslování data pro kreslení sám sebe. Například nastavení <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> způsobí, že k uložení reprezentace glyf vykreslování ovládacího prvku.  
  
 A <xref:System.Windows.Media.Visual> popisuje jeho obsah jako jeden nebo více <xref:System.Windows.Media.Drawing> objekty obsažené v <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> také popisuje masky krytí, transformací, důsledky rastrového obrázku a jiné operace, které se použijí k jejímu obsahu. <xref:System.Windows.Media.DrawingGroup> operace se použijí v uvedeném pořadí při obsahu: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a potom <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující příklad uvádí pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> operací se používají při pořadí vykreslování.  
  
 ![Pořadí operací objektu DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup  
  
 Další informace najdete v tématu [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Kreslení obsahu ve vrstvě Visual  
 Nikdy přímo instance <xref:System.Windows.Media.DrawingContext>; můžete, ale získat kreslení kontext z některé metody, jako <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Následující příklad načte <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> a použije k vykreslení obdélníku.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Vytváření výčtu kreslení obsahu ve vrstvě Visual  
 Kromě jejich použití <xref:System.Windows.Media.Drawing> objekty také poskytují objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Při vytváření obsahu vizuálu jsou výčtu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní znázornění dat, vykreslení jako seznam vektorové grafiky instrukcí.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak vizuální objekty se používají k sestavení ovládacích prvků  
 Mnoho objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se skládají z jiné visual objekty, což znamená, mohou obsahovat různých hierarchií odvozené objekty. Mnoho uživatele prvky v rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jako je například ovládací prvky, se skládají z několika visual objektů, představuje různé typy elementům vykreslování. Například <xref:System.Windows.Controls.Button> ovládacího prvku může obsahovat několik jiné objekty, včetně <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, a <xref:System.Windows.Controls.TextBlock>.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.Button> prvek definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Pokud jste se vytvořit výčet vizuální objekty, které tvoří výchozí <xref:System.Windows.Controls.Button> řízení, by najít hierarchii vizuální objekty, které jsou znázorněné dole:  
  
 ![Diagram hierarchie vizuálním stromu](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
Diagram hierarchie vizuálním stromu  
  
 <xref:System.Windows.Controls.Button> Obsahuje ovládací prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který pak obsahuje <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element zodpovídá za ohraničení a pozadí pro kreslení <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Element zodpovídá za zobrazení obsahu <xref:System.Windows.Controls.Button>. V takovém případě od zobrazujete text, <xref:System.Windows.Controls.ContentPresenter> obsahuje element <xref:System.Windows.Controls.TextBlock> elementu. Fakt, <xref:System.Windows.Controls.Button> používá ovládací prvek <xref:System.Windows.Controls.ContentPresenter> znamená, že obsah může být reprezentovaný další prvky, jako <xref:System.Windows.Controls.Image> nebo geometry, například <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Šablon ovládacích prvků  
 Klíč k rozšiřování ovládacího prvku do hierarchie ovládacích prvků <xref:System.Windows.Controls.ControlTemplate>. Šablony správy Určuje výchozí visual hierarchie pro ovládací prvek. Když odkazujete explicitně ovládacího prvku, implicitně referenční visual hierarchii. Můžete přepsat výchozí hodnoty pro řízení šablonu pro vytvoření přizpůsobené vzhled ovládacího prvku. Například může změnit hodnotu barvy pozadí <xref:System.Windows.Controls.Button> řídit tak, aby používala lineární barva barevného přechodu hodnotu namísto hodnoty plnou barvou. Další informace najdete v tématu [styly tlačítek a šablony](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 Uživatel rozhraní elementu, například <xref:System.Windows.Controls.Button> řídit, obsahuje několik vektorové grafiky instrukce seznamy, které popisují definici celý vykreslování ovládacího prvku. Následující kód ukazuje <xref:System.Windows.Controls.Button> prvek definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Pokud byste chtěli vytvořit výčet vizuální objekty a vektorové grafiky instrukce seznamy, které tvoří <xref:System.Windows.Controls.Button> řízení, by najít hierarchii objektů, které jsou znázorněné dole:  
  
 ![Diagram vizuálním stromu a datech pro vykreslení](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Diagram vizuálním stromu a datech pro vykreslení  
  
 <xref:System.Windows.Controls.Button> Obsahuje ovládací prvek <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který pak obsahuje <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element zodpovídá za kreslení diskrétní grafické prvky, které tvoří ohraničení a pozadí tlačítka. <xref:System.Windows.Controls.ContentPresenter> Element zodpovídá za zobrazení obsahu <xref:System.Windows.Controls.Button>. V takovém případě od zobrazujete bitovou kopii, <xref:System.Windows.Controls.ContentPresenter> obsahuje element <xref:System.Windows.Controls.Image> elementu.  
  
 Existuje několik bodů, které je třeba o hierarchii vektorové grafiky instrukce seznamy a vizuální objekty:  
  
-   Řazení v hierarchii představuje pořadí vykreslování informací o vykreslování. Z kořenové visual elementu je provázán podřízené elementy zleva doprava, shora dolů. Pokud element má visual podřízené elementy, jsou provázán před elementu na stejné úrovni.  
  
-   Uzel typu non list elementy v hierarchii, například <xref:System.Windows.Controls.ContentPresenter>, se používají tak, aby obsahovala podřízené elementy – neobsahují instrukce seznamy.  
  
-   Pokud vizuální prvek obsahuje seznam vektorové grafiky instrukce i visual podřízené objekty, seznamu instrukce v nadřazeného elementu visual vykreslením před kresby v některém z visual podřízené objekty.  
  
-   Položky v seznamu vektorové grafiky instrukce jsou vykreslovány zprava doleva.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Vizuálním stromu  
 Vizuální strojové struktuře obsahuje všechny vizuální prvky používané v uživatelském rozhraní aplikace. Vzhledem k tomu, že vizuální prvek obsahuje trvalý informací o vykreslování, si můžete představit vizuálním stromu jako scény graf, obsahující všechny vykreslování informace potřebné k vytváření výstup do zobrazení zařízení. Tento strom je nahromadění všechny vizuální prvky, které jsou vytvořené přímo aplikace, zda v kódu nebo ve značkách. Vizuální strojové struktuře také obsahuje všechny vizuální prvky, které jsou vytvořené šablony rozšíření elementů, jako jsou ovládací prvky a datové objekty.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.StackPanel> element definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Pokud jste se vytvořit výčet vizuální objekty, které tvoří <xref:System.Windows.Controls.StackPanel> element v příkladu značek by najít hierarchii vizuální objekty, které jsou znázorněné dole:  
  
 ![Diagram hierarchie vizuálním stromu](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
Diagram hierarchie vizuálním stromu  
  
### <a name="rendering-order"></a>Pořadí vykreslování  
 Vizuální strojové struktuře určuje pořadí vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual a kreslení objektů. Pořadí traversal začíná kořenu visual, což je nejvyšší uzel ve vizuálním stromu. Podřízené kořenové visual je pak provázán, zleva doprava. Pokud zobrazení podřízených prvků, je před tento vizuál na stejné úrovni provázán své podřízené objekty. To znamená, že obsah visual podřízenou je vykreslen před visual na vlastní obsah.  
  
 ![Diagram pořadí vykreslování vizuálním stromu](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
Diagram pořadí vykreslování vizuálním stromu  
  
### <a name="root-visual"></a>Kořenové Visual  
 **Kořenové visual** je nejvyšší element v hierarchii vizuálním stromu. Ve většině aplikací, je základní třídu kořenu visual buď <xref:System.Windows.Window> nebo <xref:System.Windows.Navigation.NavigationWindow>. Pokud byly hostování vizuální objekty v aplikaci Win32, ale kořenu visual by visual nejvyšší, které byly hostování v okně Win32. Další informace najdete v tématu [kurz: hostování vizuální objekty v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Vztah k logickém stromu.  
 V logickém stromu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentuje elementy aplikace za běhu. I když tento strom zpracovávají není přímo, toto zobrazení aplikace je užitečné pro pochopení dědičnost vlastnosti a události směrování. Na rozdíl od vizuálním stromu logického stromu představují nevizuálních datové objekty, například <xref:System.Windows.Documents.ListItem>. V mnoha případech logického stromu mapuje velmi úzce definice kód aplikace. Následující kód ukazuje <xref:System.Windows.Controls.DockPanel> element definovaný v kódu.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Pokud jste se vytvořit výčet logické objekty, které tvoří <xref:System.Windows.Controls.DockPanel> element v příkladu značek by najít hierarchii logické objektů, které jsou znázorněné dole:  
  
 ![Stromového diagramu](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
Diagram logickém stromu.  
  
 Vizuálním stromu i logického stromu jsou synchronizovány s aktuální sadu elementů aplikace, které odráží všechny přidání, odstranění nebo úpravy elementů. Stromy však představují různá zobrazení aplikace. Na rozdíl od vizuálním stromu logického stromu nerozšiřuje ovládacího prvku <xref:System.Windows.Controls.ContentPresenter> elementu. To znamená, že neexistuje žádná přímá souvislosti mezi logického stromu a vizuálním stromu pro stejnou sadu objektů. Ve skutečnosti vyvolání **LogicalTreeHelper** objektu <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metoda a **VisualTreeHelper** objektu <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> pomocí stejného elementu, parametr dává odlišné výsledky – metoda .  
  
 Další informace o logickém stromu najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Zobrazení stromu Visual s aplikaci XamlPad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nástroj, aplikaci XamlPad, poskytuje možnost pro zobrazování a zkoumání visual stromové struktury, která odpovídá na aktuálně definovaný [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] obsah. Klikněte **zobrazit vizuálním stromu** tlačítka na panelu nabídek zobrazíte vizuálním stromu. Následující obrázek znázorňuje rozšíření [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] obsahu do vizuálním stromu uzlů v **Průzkumníka Visual stromu** panelu aplikaci XamlPad:  
  
 ![Visual panelu stromu Průzkumníka v aplikaci XamlPad](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
Visual panelu stromu Průzkumníka v aplikaci XamlPad  
  
 Všimněte si jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, a <xref:System.Windows.Controls.Button> hierarchie samostatné visual objektů v zobrazení ovládacích prvků každé **Průzkumníka Visual stromu** panelu aplikaci XamlPad. Důvodem je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají ovládací prvky <xref:System.Windows.Controls.ControlTemplate> , který obsahuje vizuální strojové struktuře tohoto ovládacího prvku. Když odkazujete explicitně ovládacího prvku, implicitně referenční visual hierarchii.  
  
### <a name="profiling-visual-performance"></a>Profilace výkonu Visual  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu nástrojů, které vám umožní analyzovat běhového chování vaší aplikace a zjistit typy optimalizací výkonu, která můžete použít na profilování výkonu. Tento nástroj Visual profileru nabízí bohaté a grafické zobrazení dat výkonu mapováním přímo do aplikace vizuálním stromu. Na tomto snímku obrazovky **využití procesoru** části Visual profileru vám dává přesné rozpis použití objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služby, jako je vykreslování a rozložení.  
  
 ![Visual profileru zobrazení výstupu](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Výstup zobrazení Visual profileru  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Chování Visual vykreslování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zavádí několik funkcí, které ovlivňují chování vykreslování vizuální objekty: uchovávají režimu grafiky, vektorová grafika a nezávislé grafiky zařízení.  
  
### <a name="retained-mode-graphics"></a>Udržení režimu grafiky  
 Jeden z klíčů k pochopení roli Visual objektu je pochopit rozdíl mezi **přímý režim** a **uchovávají režimu** grafické systémy. Standardní aplikace Win32 na základě GDI nebo GDI + používá systém grafiky přímý režim. To znamená, že aplikace je zodpovědná za překreslení část klientské oblasti, která je zrušena z důvodu akce, jako okno změnou velikosti, nebo změna jeho vzhled objektu.  
  
 ![Diagram pořadí vykreslování Win32](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Diagram pořadí vykreslování Win32  
  
 Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá systém udržených režimu. To znamená, že aplikace objekty, které mají vzhled definovat sadu serializovaná data kreslení. Po vykreslení dat je definován, systém je po tomto datu za reagovat na všechny požadavky na překreslit pro vykreslování objekty aplikací. I v době běhu můžete upravit nebo vytvořit objekty aplikací a stále závisí na systému neodpovídá na požadavky malovat požadavky. Výkon systému grafiky zachované režimu je, že kreslení informace je vždy uchovávané v serializovaný stav pomocí aplikace, ale zodpovědnost vykreslování zleva systému. Následující diagram znázorňuje, jak se aplikace spoléhá na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro zpracování požadavků pro malování.  
  
 ![Diagram pořadí vykreslování WPF](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
Diagram pořadí vykreslování WPF  
  
#### <a name="intelligent-redrawing"></a>Inteligentní překreslování  
 Jeden z největších výhod použití grafiky zachované režimu je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete efektivně optimalizovat co musí být překreslen v aplikaci. I v případě, že máte komplexní scény s různými úrovněmi krytí, obvykle není potřeba psát kód speciální za účelem optimalizace překreslování. Toto porovnání s programováním Win32, ve kterém chcete věnovat značnou část úsilí v optimalizace vaší aplikace pomocí minimalizace množství překreslování v oblasti aktualizací. V tématu [překreslování v oblasti aktualizací](https://msdn.microsoft.com/library/dd162909.aspx) příklad typu složitost součástí optimalizace překreslování v aplikace Win32.  
  
### <a name="vector-graphics"></a>Vektorová grafika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá **vektorové grafiky** jako formát dat vykreslování. Vektorové grafiky, mezi které patří škálovatelné grafiky SVG (Vector), Windows metasoubory (WMF) a TrueType – ukládání dat vykreslování a přenášet jako seznam pokyny, které popisují, jak znovu vytvořit bitovou kopii pomocí grafiky primitiv. Například písma TrueType jsou outline písma, která popisují sadu čar, křivek a příkazy, nikoli pole pixelů. Jeden z klíčových výhod vektorová grafika je schopnost škálování jakékoli velikosti a řešení.  
  
 Na rozdíl od vektorová grafika rastrový obrázek jako znázornění pixelů pomocí bitové kopie, před generovány pro konkrétní řešení úložiště datech pro vykreslení. Jedním z hlavní rozdílů mezi formáty rastrového obrázku a vektoru je věrnosti na bitovou kopii původního zdroje. Například při změně velikosti zdrojové bitové kopie rastrový obrázek grafické systémy stretch bitovou kopii, zatímco vektorové grafiky systémy škálování obrázku se zachováním přesnost bitové kopie.  
  
 Následující obrázek znázorňuje zdrojové bitové kopie, který má došlo ke změně velikosti 300 %. Všimněte si narušení, které se zobrazují, když Zdrojová bitová kopie je roztažen tak, jako rastrový obrázek grafiky spíše než škálovat jako obrázek na vektorové grafiky.  
  
 ![Rozdíly mezi rastrových a vektorová grafika](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Rozdíly mezi rastrových a vektorová grafika  
  
 Následující kód ukazuje dva <xref:System.Windows.Shapes.Path> prvky definované. Druhý element používá <xref:System.Windows.Media.ScaleTransform> ke změně velikosti kreslení pokynů první prvek 300 %. Všimněte si, že kreslení pokynů <xref:System.Windows.Shapes.Path> elementy zůstanou beze změny.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>O překlad IP adres a nezávislé na zařízení grafiky  
 Existují dvě systému faktory, které určit velikost textu a obrázků na obrazovce: překlad IP adres a DPI. Řešení popisuje počet pixelů, které se zobrazují na obrazovce. Jako řešení získá vyšší, získat menší způsobuje grafika a text, který se zobrazí menší pixelů. Grafika zobrazené na monitoru nastavena na 1024 × 768 zobrazí mnohem menší při řešení na hodnotu 1 600 × 1200.  
  
 Další nastavení systému, DPI, popisuje velikost obrazovka palec v pixelech. Většina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systémy mají DPI 96, což znamená obrazovka palec je 96 pixelů. Vyšší hodnoty DPI umožňuje větší; obrazovka palec snížení počtu bodů na PALEC díky obrazovka palec menší. To znamená, že není obrazovka palec stejnou velikost jako reálného palec; u většiny systémů je pravděpodobně není. Můžete zvýšit DPI, změní palec grafika a text větší, protože jste zvětšili velikost obrazovka palec. Zvýšení počtu bodů na PALEC můžete usnadnit čtení, zejména u vysokých rozlišení text.  
  
 Ne všechny aplikace jsou rozlišením DPI: některé pixelů hardwaru použít jako primární jednotka měření; Změna systému DPI nemá žádný vliv na tyto aplikace. Mnoho dalších aplikací používat palec jednotky popisují velikosti písem, ale slouží k popisu všem ostatním pixelů. Provádění DPI příliš malá nebo příliš velký může způsobit problémy rozložení pro tyto aplikace, protože aplikace text škáluje s nastavením DPI systému, ale nemá uživatelského rozhraní aplikace. Tento problém se odstranilo pro aplikace vyvinuté pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje automatické škálování pomocí nezávislé pixelů zařízení jako svůj primární jednotky měření místo hardwaru pixelů; Grafika a text škálovat správně bez další zátěže z vývojáře aplikace. Následující obrázek znázorňuje příklad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] textu a obrázků se zobrazí různá nastavení DPI.  
  
 ![Grafika a text v různých nastavení DPI](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika a text v různých nastavení DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper – třída  
 <xref:System.Windows.Media.VisualTreeHelper> Třída je statickou pomocnou třídu, která poskytuje nízké úrovně funkci pro programování na úrovni vizuální objekt, který je užitečný v velmi konkrétní scénáře, jako je například vývoj vlastních ovládacích prvků vysoce výkonné. Ve většině případů by vyšší úrovni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework objekty, jako například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.TextBlock>, nabízejí větší flexibilitu a snadné použití.  
  
### <a name="hit-testing"></a>Testování průchodu  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje metody pro testování v vizuální objekty, když výchozí průchodu testu podporu vstupů do nevyhovuje vašim potřebám. Můžete použít <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody v <xref:System.Windows.Media.VisualTreeHelper> třídu k určení, zda je hodnota souřadnic geometrie nebo bodu v rámci hranice daného objektu, například na ovládací prvek nebo grafický element. Například můžete použít přístupů testování k určení zda klikněte na tlačítko myši, v rámci ohraničující obdélník objekt spadá do geometry, které můžete také přepsat výchozí implementaci přístupů testování provést svůj vlastní test přístupů kruhu výpočty.  
  
 Další informace o počtu testování najdete v tématu [dosáhl testování ve vrstvě Visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Vytváření výčtu vizuálním stromu  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje funkce pro vytvoření výčtu členy vizuálním stromu. Chcete-li načíst nadřazené, volejte <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metoda. Načtení podřízené, nebo přímý následník objekt visual volání <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metoda. Tato metoda vrátí podřízenou <xref:System.Windows.Media.Visual> nadřazeného objektu v zadaném indexu.  
  
 Následující příklad ukazuje, jak vytvořit výčet všech potomků visual objektu, který je technika, který chcete použít, pokud jste byli zájem o serializaci všechny informace vykreslování hierarchie vizuální objekt.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Ve většině případů je logického stromu užitečnější reprezentace elementů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. I když měnit logického stromu přímo, toto zobrazení aplikace je užitečné pro pochopení dědičnost vlastnosti a události směrování. Na rozdíl od vizuálním stromu logického stromu představují nevizuálních datové objekty, například <xref:System.Windows.Documents.ListItem>. Další informace o logickém stromu najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Třída poskytuje metody pro vrácení ohraničující obdélník vizuální objekty. Můžete se vrátit ohraničující obdélník vizuální objekt voláním <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Můžete se vrátit ohraničující obdélník všech potomků visual objektu, včetně visual odkaz sám na sebe, voláním <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Následující kód ukazuje, jak by vypočítat ohraničující obdélník vizuální objekt a všechny jeho následníky.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 <xref:System.Windows.Media.DrawingVisual>  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Ověřování pozice ve vizuální vrstvě](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Použití objektů DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [Kurz: Hostování vizuální objektů v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
