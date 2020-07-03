---
title: Přehled vykreslování grafiky
description: Přečtěte si o roli základní třídy vykreslování grafiky, ze které jsou všechny objekty odvozeny v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 96a7ea999f27e89dc22c10329214de7e3fa60341
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853635"
---
# <a name="wpf-graphics-rendering-overview"></a>Přehled vykreslování grafiky WPF
Toto téma poskytuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální vrstvy. Zaměřuje se na roli <xref:System.Windows.Media.Visual> třídy pro podporu vykreslování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu.  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Role vizuálního objektu  
 <xref:System.Windows.Media.Visual>Třída je základní abstrakcí, ze které jsou <xref:System.Windows.FrameworkElement> odvozeny všechny objekty. Slouží také jako vstupní bod pro zápis nových ovládacích prvků v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a v mnoha ohledech lze považovat za popisovač okna (HWND) v modelu aplikace Win32.  
  
 <xref:System.Windows.Media.Visual>Objekt je základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt, jehož primární role má poskytnout podporu vykreslování. Ovládací prvky uživatelského rozhraní, například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TextBox> , jsou odvozeny z <xref:System.Windows.Media.Visual> třídy a používají je pro uchování jejich dat vykreslování. <xref:System.Windows.Media.Visual>Objekt poskytuje podporu pro:  
  
- Zobrazení výstupu: vykreslení trvalého a serializovaného obsahu vykreslování vizuálu.  
  
- Transformace: provádění transformací na vizuálu.  
  
- Oříznutí: poskytuje podporu oblasti oříznutí pro vizuál.  
  
- Testování přístupů: určení, zda je souřadnice nebo geometrie obsažena v mezích vizuálu.  
  
- Výpočty ohraničovacího rámečku: určení ohraničujícího obdélníku vizuálu.  
  
 Objekt však neobsahuje <xref:System.Windows.Media.Visual> podporu pro funkce, které nevykreslují, například:  
  
- Zpracování událostí  
  
- Layout  
  
- Styly  
  
- Datová vazba  
  
- Globalizace  
  
 <xref:System.Windows.Media.Visual>je zveřejněn jako veřejná abstraktní třída, ze které musí být odvozené podřízené třídy. Následující ilustrace znázorňuje hierarchii vizuálních objektů, které jsou vystaveny v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 ![Diagram tříd odvozený z vizuálního objektu](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>DrawingVisual – třída  
 <xref:System.Windows.Media.DrawingVisual>Je zjednodušená třída pro kreslení, která se používá k vykreslování tvarů, obrázků nebo textu. Tato třída je považována za odlehčenou, protože neposkytuje rozložení nebo zpracování událostí, což zvyšuje výkon modulu runtime. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty. <xref:System.Windows.Media.DrawingVisual>Lze použít k vytvoření vlastního vizuálního objektu. Další informace najdete v tématu [použití objektů DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual – třída  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual>Poskytuje most mezi 2D <xref:System.Windows.Media.Visual> a <xref:System.Windows.Media.Media3D.Visual3D> objekty. <xref:System.Windows.Media.Media3D.Visual3D>Třída je základní třídou pro všechny 3D prvky vizuálu. <xref:System.Windows.Media.Media3D.Viewport3DVisual>Vyžaduje, abyste definovali <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> hodnotu a <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> hodnotu. Fotoaparát umožňuje zobrazit scénu. Zobrazení určuje, kde se projekce mapuje na 2D plochu. Další informace o 3D v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najdete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>ContainerVisual – třída  
 <xref:System.Windows.Media.ContainerVisual>Třída se používá jako kontejner pro kolekci <xref:System.Windows.Media.Visual> objektů. <xref:System.Windows.Media.DrawingVisual>Třída je odvozena z <xref:System.Windows.Media.ContainerVisual> třídy a umožňuje tak, aby obsahovala kolekci vizuálních objektů.  
  
### <a name="drawing-content-in-visual-objects"></a>Kreslení obsahu v vizuálních objektech  
 <xref:System.Windows.Media.Visual>Objekt ukládá data vykreslení jako **seznam instrukcí pro vektorovou grafiku**. Každá položka v seznamu instrukcí představuje sadu grafických dat a přidružených prostředků v serializovaném formátu na nižší úrovni. Existují čtyři různé typy dat vykreslování, které mohou obsahovat vykreslení obsahu.  
  
|Typ obsahu vykreslování|Popis|  
|--------------------------|-----------------|  
|Vektorová grafika|Představuje data vektorové grafiky a všechny přidružené <xref:System.Windows.Media.Brush> a <xref:System.Windows.Media.Pen> informace.|  
|Image|Představuje obrázek v rámci oblasti definované <xref:System.Windows.Rect> .|  
|Zobrazovat|Představuje vykreslení, které vykresluje <xref:System.Windows.Media.GlyphRun> , což je sekvence glyfů z určeného prostředku písma. To je způsob reprezentace textu.|  
|Video|Představuje vykreslování, který vykresluje video.|  
  
 <xref:System.Windows.Media.DrawingContext>Umožňuje naplnit <xref:System.Windows.Media.Visual> vizuální obsah. Použijete-li <xref:System.Windows.Media.DrawingContext> příkazy pro vykreslení objektu, ukládáte ve skutečnosti sadu dat vykreslování, která budou později používána grafickým systémem. nebudete kreslit na obrazovku v reálném čase.  
  
 Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku, jako je <xref:System.Windows.Controls.Button> , ovládací prvek implicitně generuje data vykreslování pro vykreslení. Například nastavením <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti <xref:System.Windows.Controls.Button> ovládacího prvku způsobí, že ovládací prvek bude ukládat prezentaci glyfů.  
  
 <xref:System.Windows.Media.Visual>Popisuje jeho obsah jako jeden nebo více <xref:System.Windows.Media.Drawing> objektů obsažených v rámci <xref:System.Windows.Media.DrawingGroup> . <xref:System.Windows.Media.DrawingGroup>Také popisuje masky neprůhlednosti, transformace, efekty Bitmap a další operace, které jsou aplikovány na její obsah. <xref:System.Windows.Media.DrawingGroup>operace se při vygenerování obsahu vykreslí v následujícím pořadí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> , <xref:System.Windows.Media.DrawingGroup.Opacity%2A> , <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> , <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> , <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> a pak <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 Následující ilustrace znázorňuje pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> jsou operace aplikovány během sekvence vykreslování.  
  
 ![Pořadí vykreslování operací](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací vykreslování  
  
 Další informace najdete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Kreslení obsahu ve vizuální vrstvě  
 Nikdy přímo nevytvoříte instanci a. <xref:System.Windows.Media.DrawingContext> můžete ale získat kontext vykreslování z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> . Následující příklad načte <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> a a použije ho k nakreslení obdélníku.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Vytváření výčtu obsahu kreslení ve vizuální vrstvě  
 Kromě jiných použití <xref:System.Windows.Media.Drawing> objekty poskytují také objektový model pro vytváření výčtu obsahu <xref:System.Windows.Media.Visual> .  
  
> [!NOTE]
> Při vytváření výčtu obsahu vizuálu načítáte <xref:System.Windows.Media.Drawing> objekty, a ne základní reprezentace dat vykreslování jako seznam instrukcí pro vektorovou grafiku.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu k načtení <xref:System.Windows.Media.DrawingGroup> hodnoty <xref:System.Windows.Media.Visual> a k jejímu vytvoření.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Způsob vytváření ovládacích prvků pomocí vizuálních objektů  
 Mnohé z objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se skládají z jiných vizuálních objektů, což znamená, že mohou obsahovat různé hierarchie potomků objektů. Mnohé prvky uživatelského rozhraní v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , jako jsou například ovládací prvky, se skládají z více vizuálních objektů, které představují různé typy prvků vykreslování. Například <xref:System.Windows.Controls.Button> ovládací prvek může obsahovat řadu dalších objektů, včetně <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> , <xref:System.Windows.Controls.ContentPresenter> a <xref:System.Windows.Controls.TextBlock> .  
  
 Následující kód ukazuje <xref:System.Windows.Controls.Button> ovládací prvek definovaný v označení.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Pokud jste chtěli vytvořit výčet vizuálních objektů, které tvoří výchozí <xref:System.Windows.Controls.Button> ovládací prvek, měli byste najít hierarchii vizuálních objektů, které jsou znázorněny níže:  
  
 ![Diagram hierarchie vizuálního stromu](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 <xref:System.Windows.Controls.Button>Ovládací prvek obsahuje <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který zase obsahuje <xref:System.Windows.Controls.ContentPresenter> element. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>Prvek je zodpovědný za vykreslení ohraničení a pozadí pro <xref:System.Windows.Controls.Button> . <xref:System.Windows.Controls.ContentPresenter>Prvek je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button> . V tomto případě, vzhledem k tomu, že zobrazujete text, <xref:System.Windows.Controls.ContentPresenter> element obsahuje <xref:System.Windows.Controls.TextBlock> element. Skutečnost, že <xref:System.Windows.Controls.Button> ovládací prvek používá, <xref:System.Windows.Controls.ContentPresenter> znamená, že obsah může být reprezentován jinými prvky, jako je například <xref:System.Windows.Controls.Image> nebo geometrie, jako je například <xref:System.Windows.Media.EllipseGeometry> .  
  
### <a name="control-templates"></a>Šablony ovládacích prvků  
 Klíčem k rozšíření ovládacího prvku do hierarchie ovládacích prvků je <xref:System.Windows.Controls.ControlTemplate> . Šablona ovládacího prvku určuje výchozí vizuální hierarchii ovládacího prvku. Pokud explicitně odkazujete na ovládací prvek, implicitně odkazujete na jeho vizuální hierarchii. Můžete přepsat výchozí hodnoty pro šablonu ovládacího prvku a vytvořit tak přizpůsobený vizuální vzhled ovládacího prvku. Můžete například změnit hodnotu barvy pozadí <xref:System.Windows.Controls.Button> ovládacího prvku tak, aby místo hodnoty Solid Color používala hodnotu barvy lineárního přechodu. Další informace naleznete v tématu [styly a šablony tlačítek](../controls/button-styles-and-templates.md).  
  
 Prvek uživatelského rozhraní, jako je například <xref:System.Windows.Controls.Button> ovládací prvek, obsahuje několik seznamů instrukcí pro vektorovou grafiku, které popisují celou definici vykreslování ovládacího prvku. Následující kód ukazuje <xref:System.Windows.Controls.Button> ovládací prvek definovaný v označení.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Pokud jste chtěli vytvořit výčet seznamů instrukcí pro vizuální objekty a vektorová grafika, které tvoří <xref:System.Windows.Controls.Button> ovládací prvek, měli byste najít hierarchii objektů, které jsou znázorněny níže:  
  
 ![Diagram vizuálního stromu a vykreslování dat](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 <xref:System.Windows.Controls.Button>Ovládací prvek obsahuje <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, který zase obsahuje <xref:System.Windows.Controls.ContentPresenter> element. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>Prvek je zodpovědný za vykreslení všech diskrétních grafických prvků, které tvoří ohraničení a pozadí tlačítka. <xref:System.Windows.Controls.ContentPresenter>Prvek je zodpovědný za zobrazení obsahu <xref:System.Windows.Controls.Button> . V tomto případě, vzhledem k tomu, že zobrazujete obrázek, <xref:System.Windows.Controls.ContentPresenter> element obsahuje <xref:System.Windows.Controls.Image> element.  
  
 Existuje několik bodů, které si poznamenejte v hierarchii vizuálních objektů a seznamů instrukcí vektorové grafiky:  
  
- Řazení v hierarchii představuje pořadí vykreslování informací o výkresu. Z kořenového vizuálního prvku jsou podřízené prvky procházeny zleva doprava, shora dolů. Pokud má element vizuální podřízené prvky, jsou přecházet před elementy na stejné úrovni.  
  
- Prvky uzlu mimo uzel v hierarchii, například <xref:System.Windows.Controls.ContentPresenter> , jsou použity k označení podřízených prvků – neobsahují seznamy instrukcí.  
  
- Pokud vizuální prvek obsahuje seznam instrukcí pro vektorovou grafiku i vizuální podřízené prvky, seznam instrukcí v nadřazeném vizuálním elementu je vykreslen před výkresy v libovolném z prvků vizuálního podřízeného objektu.  
  
- Položky v seznamu instrukcí pro vektorovou grafiku jsou vykresleny zleva doprava.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Vizuální strom  
 Vizuální strom obsahuje všechny vizuální prvky, které se používají v uživatelském rozhraní aplikace. Vzhledem k tomu, že vizuální prvek obsahuje trvalé informace o kreslení, můžete si představit vizuální strom jako graf scény obsahující všechny informace o vykreslování potřebné k vytvoření výstupu do zobrazovacího zařízení. Tento strom je akumulací všech vizuálních prvků vytvořených přímo aplikací, ať už v kódu, nebo v označení. Vizuální strom také obsahuje všechny vizuální prvky, které byly vytvořeny rozšířením šablony prvků, jako jsou ovládací prvky a datové objekty.  
  
 Následující kód ukazuje <xref:System.Windows.Controls.StackPanel> element definovaný v označení.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Pokud jste chtěli vytvořit výčet vizuálních objektů, které tvoří <xref:System.Windows.Controls.StackPanel> prvek v příkladu kódu, měli byste najít hierarchii vizuálních objektů, které jsou znázorněny níže:  
  
 ![Diagram hierarchie vizuálního stromu](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Pořadí vykreslování  
 Vizuální strom určuje pořadí vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuálních a nakreslených objektů. Pořadí průchodu začíná kořenovým vizuálem, což je nejvyšší uzel ve vizuálním stromu. Podřízené prvky kořenového vizuálu se pak přesměrují zleva doprava. Pokud má vizuál podřízené objekty, jejich podřízené položky jsou procházeny před prvky na stejné úrovni. To znamená, že obsah podřízeného vizuálu je vykreslen před vlastním obsahem vizuálu.  
  
 ![Diagram pořadí vykreslování vizuálního stromu](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Kořenová vizuálu  
 **Kořenový vizuál** je prvek nejvyšší úrovně v hierarchii vizuálního stromu. Ve většině aplikací je základní třída kořenového vizuálu buď <xref:System.Windows.Window> nebo <xref:System.Windows.Navigation.NavigationWindow> . Pokud jste však hostitelem vizuálních objektů v aplikaci Win32, kořenový vizuál by byl nejvyšší vizuál, který jste hostovat v okně Win32. Další informace najdete v tématu [kurz: hostování vizuálních objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Vztah k logickému stromu  
 Logický strom v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] představuje prvky aplikace v době běhu. I když nepracujete přímo s tímto stromem, toto zobrazení aplikace je užitečné pro porozumění dědičnosti vlastností a směrování událostí. Na rozdíl od vizuálního stromu může logický strom představovat nevizuální datové objekty, jako například <xref:System.Windows.Documents.ListItem> . V mnoha případech je logický strom přesně namapován na definice značek aplikace. Následující kód ukazuje <xref:System.Windows.Controls.DockPanel> element definovaný v označení.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Pokud jste chtěli vytvořit výčet logických objektů, které tvoří <xref:System.Windows.Controls.DockPanel> element v příkladu kódu, naleznete hierarchii logických objektů, které jsou znázorněny níže:  
  
 ![Stromový diagram](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram logického stromu  
  
 Vizuální strom i logický strom jsou synchronizovány s aktuální sadou prvků aplikace a odráží jakékoli přidání, odstranění nebo úpravu prvků. Stromy ale obsahují různá zobrazení aplikace. Na rozdíl od vizuálního stromu nerozšíří logický strom element ovládacího prvku <xref:System.Windows.Controls.ContentPresenter> . To znamená, že mezi logickým stromem a vizuální stromovou strukturou pro stejnou sadu objektů není přímá korespondence 1:1. Ve skutečnosti voláním metody objektu **LogicalTreeHelper** <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> a metody objektu **VisualTreeHelper** pomocí stejného prvku, který je výsledkem <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> parametru, se liší výsledky.  
  
 Další informace o logickém stromu naleznete v tématu [stromy v](../advanced/trees-in-wpf.md)subsystému WPF.  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Zobrazení vizuálního stromu pomocí XamlPad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Nástroj XamlPad poskytuje možnost zobrazení a průzkumu vizuálního stromu, který odpovídá aktuálně definovanému obsahu XAML. Kliknutím na tlačítko **Zobrazit vizuální strom** na řádku nabídek zobrazíte vizuální strom. Následující příklad ukazuje rozšíření obsahu XAML na uzly vizuálního stromu na panelu **Průzkumníka vizuálního stromu** XamlPad:  
  
 ![Panel Průzkumníka vizuálního stromu v XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Všimněte si <xref:System.Windows.Controls.Label> , jak <xref:System.Windows.Controls.TextBox> ovládací prvky, a a <xref:System.Windows.Controls.Button> každý zobrazuje samostatné hierarchie vizuálních objektů na panelu **Průzkumníka vizuálního stromu** XamlPad. Důvodem je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , že ovládací prvky obsahují <xref:System.Windows.Controls.ControlTemplate> vizuální strom tohoto ovládacího prvku. Pokud explicitně odkazujete na ovládací prvek, implicitně odkazujete na jeho vizuální hierarchii.  
  
### <a name="profiling-visual-performance"></a>Profilace vizuálního výkonu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu nástrojů pro profilaci výkonu, které umožňují analyzovat chování aplikace za běhu a určují typy optimalizací výkonu, které můžete použít. Nástroj vizuálního profileru poskytuje bohatě a grafické zobrazení údajů o výkonu mapováním přímo na vizuální strom aplikace. V tomto snímku obrazovky nabízí část **využití CPU** ve vizuálním profileru přesný rozpis používání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služeb, jako je například vykreslování a rozložení.  
  
 ![Výstup zobrazení vizuálního profileru](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Výstup zobrazení vizuálního profileru  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Chování vizuálního vykreslování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zavádí několik funkcí, které mají vliv na chování vykreslování vizuálních objektů: režim GIF, vektorová grafika a grafika nezávislá na zařízení.  
  
### <a name="retained-mode-graphics"></a>Grafika režimu zadržované  
 Jedním z klíčů pro pochopení role vizuálního objektu je pochopit rozdíl mezi **přímým režimem** a grafickými systémy v **režimu uchování** . Standardní aplikace Win32 založená na GDI nebo GDI+ používá systém grafiky přímo v režimu. To znamená, že aplikace zodpovídá za překreslení části klienta, u které došlo k neplatnosti, kvůli akci, jako je například změna velikosti okna nebo objekt měnící jeho vizuální vzhled.  
  
 ![Diagram sekvence vykreslování v systému Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Na rozdíl od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá systém v režimu zached. To znamená, že objekty aplikace, které mají vizuální vzhled, definují sadu serializovaných dat vykreslování. Po definování dat výkresu je systém zodpovědný za odpověď na všechny žádosti o překreslování pro vykreslování objektů aplikace. Dokonce i v době běhu můžete upravovat nebo vytvářet aplikační objekty a pořád spoléhat na systém, který reaguje na požadavky na malování. Napájení v režimu grafiky v zachované soustavě je, že informace o kreslení jsou vždycky trvale uložené v serializovaném stavu aplikace, ale vykreslování zůstává zodpovědností do systému. Následující diagram ukazuje, jak aplikace spoléhá na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] požadavky na malování.  
  
 ![Diagram sekvence vykreslování WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentní překreslení  
 Jednou z největších výhod v používání uložených grafických objektů je, že je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možné efektivně optimalizovat, co je potřeba v aplikaci znovu vykreslit. I v případě, že máte složitou scénu s různou úrovní neprůhlednosti, obecně není nutné psát kód speciálního účelu pro optimalizaci opětovného vykreslení. Porovnejte je s programováním v systému Win32, ve kterém se můžete věnovat skvělému úsilí při optimalizaci aplikace minimalizací velikosti překreslení v oblasti aktualizace. Příklad typu složitosti související s optimalizací překreslení v aplikacích Win32 najdete [v tématu překreslení v oblasti aktualizace](/windows/desktop/gdi/redrawing-in-the-update-region) .  
  
### <a name="vector-graphics"></a>Vektorová grafika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá jako formát dat vykreslování **vektorovou grafiku** . Vektorová grafika, která zahrnuje škálovatelné vektorové grafiky (SVG), metasoubory Windows (. WMF) a písma TrueType – ukládají data vykreslování a přenáší je jako seznam instrukcí, které popisují, jak znovu vytvořit Image pomocí grafických primitiv. Například písma TrueType jsou obrysová písma, která popisují sadu řádků, křivek a příkazů místo pole pixelů. Jednou z klíčových výhod vektorové grafiky je schopnost škálování na libovolnou velikost a rozlišení.  
  
 Na rozdíl od vektorové grafiky úložiště rastrového obrázku v obrazovém obrazu vykreslí data jako reprezentaci obrázku podle pixelu, předem vykreslenou pro konkrétní rozlišení. Jeden z klíčových rozdílů mezi bitmapami a vektorovými grafickými formáty je věrný od původní zdrojové image. Například když se upraví velikost zdrojového obrázku, grafické systémy rastrového obrázku roztáhnou obrázek, zatímco vektorové grafické systémy škálují obrázek a zachovává věrnost obrázku.  
  
 Následující obrázek znázorňuje zdrojovou image, jejíž velikost změnila velikost o 300%. Všimněte si zkreslení, které se zobrazí, když je zdrojový obrázek roztažen jako obrázek obrázku grafiky, nikoli jako obrázek s vektorovou grafikou.  
  
 ![Rozdíly mezi rastrovou a vektorovou grafikou](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Následující kód ukazuje dva <xref:System.Windows.Shapes.Path> prvky, které jsou definovány. Druhý prvek používá <xref:System.Windows.Media.ScaleTransform> pro změnu velikosti instrukcí pro kreslení prvního prvku o 300%. Všimněte si, že pokyny pro kreslení v <xref:System.Windows.Shapes.Path> prvcích zůstanou beze změny.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>O rozlišení a grafiky nezávislé na zařízení  
 Existují dva systémové faktory, které určují velikost textu a grafiky na obrazovce: rozlišení a DPI. Řešení popisuje počet pixelů, které se zobrazí na obrazovce. Vzhledem k vyššímu rozlišení jsou pixely menší, což způsobí, že grafika a text budou menší. Obrázek zobrazený na monitoru, který je nastaven na 1024 × 768, bude v případě změny rozlišení na 1600 × 1200 pravděpodobně mnohem menší.  
  
 Další nastavení systému, DPI, popisuje velikost obrazovky palce v pixelech. Většina systémů Windows má rozlišení DPI 96, což znamená, že je obrazovka palce na 96 pixelů. Zvýšení nastavení DPI zvětší velikost obrazovky. snížením úrovně DPI se obrazovka zmenší. To znamená, že obrazovka palce nemá stejnou velikost jako reálné palce. ve většině systémů to pravděpodobně není. Při zvětšení rozlišení DPI, grafiky a textu s rozlišením DPI budou větší, protože jste zvýšili velikost obrazovky. Zvýšením úrovně DPI můžete usnadnit čtení textu, zejména při vysokém rozlišení.  
  
 Ne všechny aplikace podporují rozlišení DPI: některé jako primární měrnou jednotku používají pixely hardwaru; Změna systémového rozlišení DPI nemá na tyto aplikace žádný vliv. Mnoho dalších aplikací používá k popisu velikosti písem jednotky s podporou DPI, ale k popsání všech ostatních použijte pixely. Změna rozlišení DPI je příliš malá nebo příliš velká může způsobit problémy s rozložením pro tyto aplikace, protože text aplikace se škáluje s nastavením DPI systému, ale uživatelské rozhraní aplikace ne. Tento problém se vyloučil pro aplikace vyvíjené pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje automatické škálování pomocí nezávislého pixelu zařízení jako primární jednotky měření namísto hardwarových pixelů. bez jakékoli další práce z vývojářů aplikací je správně škálovatelná grafika a text. Následující ilustrace znázorňuje příklad způsobu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zobrazení textu a grafiky v různých nastaveních dpi.  
  
 ![Grafika a text v různých nastaveních DPI](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika a text v různých nastaveních DPI  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>VisualTreeHelper – třída  
 <xref:System.Windows.Media.VisualTreeHelper>Třída je statická pomocná třída, která poskytuje funkce nízké úrovně pro programování na úrovni vizuálních objektů, která je užitečná ve scénářích s vysokým výkonem, jako je například vývoj vysoce výkonného vlastního ovládacího prvku. Ve většině případů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty architektury vyšší úrovně, například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.TextBlock> , nabízejí větší flexibilitu a snadné použití.  
  
### <a name="hit-testing"></a>Testování přístupů  
 <xref:System.Windows.Media.VisualTreeHelper>Třída poskytuje metody pro testování přístupů na vizuální objekty, když výchozí podpora testů přístupů nevyhovuje vašim potřebám. Můžete použít <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody ve <xref:System.Windows.Media.VisualTreeHelper> třídě k určení, zda je hodnota geometrie nebo souřadnice bodu v rámci hranice daného objektu, jako je například ovládací prvek nebo grafický prvek. Například můžete použít testování volání k určení, zda kliknutí myší v ohraničujícím obdélníku objektu spadá do geometrie kružnice. můžete také zvolit přepsání výchozí implementace testování přístupů, aby bylo možné provádět vlastní výpočty testů přístupů.  
  
 Další informace o testování přístupů naleznete v tématu [testování přístupů ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Vytváření výčtu vizuálního stromu  
 <xref:System.Windows.Media.VisualTreeHelper>Třída poskytuje funkce pro vytváření výčtu členů vizuálního stromu. Chcete-li načíst nadřazený objekt, zavolejte <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metodu. Pro načtení podřízeného nebo přímého následníka z vizuálního objektu volejte <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metodu. Tato metoda vrací podřízenou položku <xref:System.Windows.Media.Visual> nadřazené položky v zadaném indexu.  
  
 Následující příklad ukazuje, jak vytvořit výčet všech následníků vizuálního objektu, což je technika, kterou můžete chtít použít, pokud jste zajímáte o serializaci všech informací o vykreslování hierarchie vizuálních objektů.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Ve většině případů je logický strom lépe užitečnou reprezentací prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci. I když logický strom neupravíte přímo, toto zobrazení aplikace je užitečné pro porozumění dědičnosti vlastností a směrování událostí. Na rozdíl od vizuálního stromu může logický strom představovat nevizuální datové objekty, jako například <xref:System.Windows.Documents.ListItem> . Další informace o logickém stromu naleznete v tématu [stromy v](../advanced/trees-in-wpf.md)subsystému WPF.  
  
 <xref:System.Windows.Media.VisualTreeHelper>Třída poskytuje metody pro vrácení ohraničujícího obdélníku vizuálních objektů. Můžete vrátit ohraničující obdélník vizuálního objektu voláním <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A> . Můžete vrátit ohraničující obdélník všech následníků vizuálního objektu, včetně samotného vizuálního objektu, voláním <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A> . Následující kód ukazuje, jak byste měli vypočítat ohraničující obdélník vizuálního objektu a všech jeho potomků.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Spuštění testování ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Použití objektů DrawingVisual](using-drawingvisual-objects.md)
- [Kurz: Hostování vizuálních objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optimalizace výkonu aplikace WPF](../advanced/optimizing-wpf-application-performance.md)
