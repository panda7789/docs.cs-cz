---
title: Kreslení pomocí obrázků, kreseb a vizuálních objektů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: 0d860062814a447830e1237f4fc2c1ae0d223e9e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510021"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Kreslení pomocí obrázků, kreseb a vizuálních objektů
Toto téma popisuje způsob použití <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> objekty k vykreslení oblasti obrázkem, <xref:System.Windows.Media.Drawing>, nebo <xref:System.Windows.Media.Visual>.  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste se seznámit s různými typy štětce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje a jejich základní funkce. Úvodní informace najdete v tématu [přehled štětců WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Vykreslení obrázku v oblasti  
 <xref:System.Windows.Media.ImageBrush> Jsou vykreslovány v oblasti <xref:System.Windows.Media.ImageSource>. Nejběžnějším typem <xref:System.Windows.Media.ImageSource> pomocí <xref:System.Windows.Media.ImageBrush> je <xref:System.Windows.Media.Imaging.BitmapImage>, vystihuje rastrový obrázek rastrový obrázek. Můžete použít <xref:System.Windows.Media.DrawingImage> má Vymalovat pomocí <xref:System.Windows.Media.Drawing> objektu, ale je jednodušší použít <xref:System.Windows.Media.DrawingBrush> místo. Další informace o <xref:System.Windows.Media.ImageSource> objekty, najdete [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 Malování s <xref:System.Windows.Media.ImageBrush>, vytvořit <xref:System.Windows.Media.Imaging.BitmapImage> a použít ho k načtení obsahu rastrového obrázku. Potom použijte <xref:System.Windows.Media.Imaging.BitmapImage> nastavit <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. Nakonec se vztahují <xref:System.Windows.Media.ImageBrush> k objektu, který má pro vykreslení.  V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete nastavit také pouze <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost <xref:System.Windows.Media.ImageBrush> s cestou k načtení obrázku.  
  
 Stejně jako všechny <xref:System.Windows.Media.Brush> objekty, <xref:System.Windows.Media.ImageBrush> slouží k vykreslení objektů, jako je například obrazce, panely, ovládací prvky a text. Následující obrázek znázorňuje některé efekty, které lze nastavit pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Příklady výstup ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objekty kresleno ImageBrush  
  
 Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> úsecích jeho image pro úplně naplnění oblasti se překreslit, pravděpodobně narušují bitovou kopii, pokud malovaného oblast má odlišný poměr stran než image. Toto chování můžete změnit pomocí změny <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí hodnotu <xref:System.Windows.Media.Stretch.Fill> k <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, nebo <xref:System.Windows.Media.Stretch.UniformToFill>. Protože <xref:System.Windows.Media.ImageBrush> je typ <xref:System.Windows.Media.TileBrush>, můžete zadat, přesně jak obrázkový štětec vyplní výstupní oblasti a dokonce vytvářet vzorce. Další informace o pokročilých <xref:System.Windows.Media.TileBrush> funkce, najdete v článku [TileBrush – přehled](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Příklad: Vykreslení objektu s rastrový obrázek  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vykreslení <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Vyplnění oblasti kresbou  
 A <xref:System.Windows.Media.DrawingBrush> umožňuje vykreslení oblasti tvary, text, obrázky a video. Tvary uvnitř kreslicího štětce mohou sami má namalovat s plnou barvou, přechod, image, nebo dokonce pro jiný <xref:System.Windows.Media.DrawingBrush>. Následující obrázek ukazuje některá použití <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Příklady výstup DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objekty kresleno DrawingBrush  
  
 A <xref:System.Windows.Media.DrawingBrush> jsou vykreslovány v oblasti <xref:System.Windows.Media.Drawing> objektu. A <xref:System.Windows.Media.Drawing> objektu popisuje viditelného obsahu, jako je tvar, rastrový obrázek, video nebo řádek textu. Různé druhy drawings popisují různé typy obsahu. Následuje seznam typy vykreslení objektů.  
  
-   <xref:System.Windows.Media.GeometryDrawing> – Nakreslí obrazec.  
  
-   <xref:System.Windows.Media.ImageDrawing> – Kreslení obrázku.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – Kreslení textu.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Přehraje zvuk nebo video soubor.  
  
-   <xref:System.Windows.Media.DrawingGroup> – Kreslení jiných kreslení. Pomocí vykreslení skupiny můžete kombinovat další drawings do jednoho kompozitní kresby.  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 Stejně jako <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> roztáhne, aby jeho <xref:System.Windows.Media.DrawingBrush.Drawing%2A> tak, aby vyplnil jeho výstupní oblasti. Toto chování můžete přepsat tak, že změníte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí nastavení <xref:System.Windows.Media.Stretch.Fill>. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Příklad: Vykreslení objektu kresbou  
 Následující příklad ukazuje, jak se má Vymalovat objekt kresbou tři symbol tří teček. A <xref:System.Windows.Media.GeometryDrawing> se používá k popisu na tři tečky.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Vykreslení vizuálního objektu v oblasti  
 Flexibilní a výkonné všechny štětců, <xref:System.Windows.Media.VisualBrush> jsou vykreslovány v oblasti <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> nízké úrovně grafické typ, který slouží jako předchůdce mnoho užitečných grafické komponent. Například <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.Controls.Control> třídy jsou všechny typy <xref:System.Windows.Media.Visual> objekty. Použití <xref:System.Windows.Media.VisualBrush>, můžete vykreslení oblasti s téměř jakoukoli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafický objekt.  
  
> [!NOTE]
>  I když <xref:System.Windows.Media.VisualBrush> k typu <xref:System.Windows.Freezable> objektu nelze zmrazit (jen pro čtení) při jeho <xref:System.Windows.Media.VisualBrush.Visual%2A> je nastavena na hodnotu jiné než `null`.  
  
 Existují dva způsoby, jak zadat <xref:System.Windows.Media.VisualBrush.Visual%2A> obsah <xref:System.Windows.Media.VisualBrush>.  
  
-   Vytvořte nový <xref:System.Windows.Media.Visual> a použít ho nastavit <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>. Příklad najdete v tématu [příklad: vykreslení vizuálního objektu](#examplevisualbrush1) v následující části.  
  
-   Použijte existující <xref:System.Windows.Media.Visual>, která vytvoří duplicitní image cíle <xref:System.Windows.Media.Visual>. Pak můžete použít <xref:System.Windows.Media.VisualBrush> vytvoření zajímavých efektů, jako je například reflexe a zvětšení. Příklad najdete v tématu [příklad: vytvoření reflexe](#examplevisualbrush2) oddílu.  
  
 Při definování nového <xref:System.Windows.Media.VisualBrush.Visual%2A> pro <xref:System.Windows.Media.VisualBrush> a že <xref:System.Windows.Media.Visual> je <xref:System.Windows.UIElement> (například panel nebo ovládací prvek), poběží systém rozložení <xref:System.Windows.UIElement> a jeho podřízené prvky při <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> je nastavena na `true`. Ale kořenové <xref:System.Windows.UIElement> je v podstatě izolovaný od zbytku systému: styly a externí rozložení nejde navrhovaný pro SVS zahrnuje tuto hranici. Proto by měly explicitně zadat velikost kořenové <xref:System.Windows.UIElement>, protože je jeho nadřazeným pouze <xref:System.Windows.Media.VisualBrush> a proto ji nelze přizpůsobovat svou velikost automaticky do oblasti se překreslit. Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], najdete v článku [rozložení](../../../../docs/framework/wpf/advanced/layout.md).  
  
 Stejně jako <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> roztáhne, aby její obsah tak, aby vyplnil jeho výstupní oblasti. Toto chování můžete přepsat tak, že změníte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí nastavení <xref:System.Windows.Media.Stretch.Fill>. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Příklad: Vykreslení vizuálního objektu  
 V následujícím příkladu několik ovládacích prvků a panel slouží k vykreslení obdélníku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Příklad: Vytvoření reflexe  
 Předchozí příklad ukázal, jak vytvořit nový <xref:System.Windows.Media.Visual> pro použití na pozadí. Můžete také použít <xref:System.Windows.Media.VisualBrush> zobrazíte existujícího vizuálu; díky této vlastnosti můžete vytvářet zajímavé vizuální efekty, jako je například odrazů a zvětšení. Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vytvoření obrazu <xref:System.Windows.Controls.Border> , která obsahuje několik elementů. Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![A odráží vizuální objekty](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Reflektovaný vizuální objekty  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Další příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazů, najdete v článku [VisualBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush – funkce  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> typů <xref:System.Windows.Media.TileBrush> objekty. <xref:System.Windows.Media.TileBrush> objekty poskytují vám s velkou kontrolu nad jak se oblast vybarvené obrázek, kreslení nebo vizuál. Například namísto pouze Malování imagi roztažené jeden v oblasti, můžete vykreslení oblasti řadu dlaždic bitové kopie, které společně tvoří masku.  
  
 A <xref:System.Windows.Media.TileBrush> má tři hlavní komponenty: obsah, dlaždice a výstupní oblasti.  
  
 ![TileBrush – komponenty](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součásti s jednu dlaždici TileBrush  
  
 ![Součástí Objekt TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součástí TileBrush s víc dlaždic  
  
 Další informace o funkcích dělení do bloků <xref:System.Windows.Media.TileBrush> objekty, najdete [TileBrush – přehled](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [TileBrush – přehled](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Přehled štětců WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled masek neprůhlednosti](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Ukázka ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)  
 [Ukázka VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
