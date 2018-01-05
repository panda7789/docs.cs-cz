---
title: "Kreslení pomocí obrázků, kreseb a vizuálních objektů"
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
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01939eb8735e6764e0f0cba811091c7fdbd6797f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="painting-with-images-drawings-and-visuals"></a>Kreslení pomocí obrázků, kreseb a vizuálních objektů
Toto téma popisuje postup použití <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> objekty k vyplnění oblast s bitovou kopii, <xref:System.Windows.Media.Drawing>, nebo <xref:System.Windows.Media.Visual>.  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s různými typy štětce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje a jejich základní funkce. Úvod najdete v článku [WPF štětce přehled](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Vykreslení obrázku v oblasti  
 <xref:System.Windows.Media.ImageBrush> Vybarví oblast s <xref:System.Windows.Media.ImageSource>. Nejběžnějším typem <xref:System.Windows.Media.ImageSource> pro použití s <xref:System.Windows.Media.ImageBrush> je <xref:System.Windows.Media.Imaging.BitmapImage>, který popisuje obrázek bitové mapy. Můžete použít <xref:System.Windows.Media.DrawingImage> k vyplnění pomocí <xref:System.Windows.Media.Drawing> objektu, ale je jednodušší použít <xref:System.Windows.Media.DrawingBrush> místo. Další informace o <xref:System.Windows.Media.ImageSource> objekty, najdete [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 K malování <xref:System.Windows.Media.ImageBrush>, vytvoření <xref:System.Windows.Media.Imaging.BitmapImage> a použít ho k načtení obsahu rastrového obrázku. Potom použít <xref:System.Windows.Media.Imaging.BitmapImage> nastavit <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. Nakonec se vztahují <xref:System.Windows.Media.ImageBrush> k objektu, který chcete malovat.  V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete také stačí nastavit <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost <xref:System.Windows.Media.ImageBrush> s cestou bitovou kopii načíst.  
  
 Všechny jako <xref:System.Windows.Media.Brush> objekty, <xref:System.Windows.Media.ImageBrush> může být použita k vyplnění objekty například tvary, panelů, ovládací prvky a text. Následující obrázek znázorňuje některé účinky, které lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Objekt ImageBrush výstup příklady](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objekty, které vykresluje pomocí objektu ImageBrush  
  
 Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> úsecích jeho bitovou kopii do úplně vyplnil celou oblast se vykresluje, pravděpodobně narušují bitovou kopii, pokud oblasti malovaného má jiný poměr stran než image. Toto chování můžete změnit změnou <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí hodnotu <xref:System.Windows.Media.Stretch.Fill> k <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, nebo <xref:System.Windows.Media.Stretch.UniformToFill>. Protože <xref:System.Windows.Media.ImageBrush> je typ <xref:System.Windows.Media.TileBrush>, můžete zadat přesně jak štětce image vyplní celé oblasti výstup a i vytvořte vzorky. Další informace o pokročilé <xref:System.Windows.Media.TileBrush> funkce, najdete [TileBrush přehled](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Příklad: Malování objektů s rastrový obrázek  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vyplnění <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Vyplnění oblasti kresbou  
 A <xref:System.Windows.Media.DrawingBrush> umožňuje malovat oblast s tvary, text, obrázky a video. Tvary uvnitř kreslení štětce může sami se vykresluje s plnou barvou, přechodu, image, nebo i jiné <xref:System.Windows.Media.DrawingBrush>. Následující obrázek ukazuje některé použití <xref:System.Windows.Media.DrawingBrush>.  
  
 ![DrawingBrush výstup příklady](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objekty, které vykresluje podle DrawingBrush  
  
 A <xref:System.Windows.Media.DrawingBrush> vybarví oblast s <xref:System.Windows.Media.Drawing> objektu. A <xref:System.Windows.Media.Drawing> objekt popisuje viditelný obsah, například obrazce, rastrového obrázku, videa nebo na řádku textu. Různé typy výkresů popisují různé typy obsahu. Následuje seznam s různými typy kreslení objektů.  
  
-   <xref:System.Windows.Media.GeometryDrawing>– Kreslení obrazce.  
  
-   <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>– Nevykresluje text.  
  
-   <xref:System.Windows.Media.VideoDrawing>– Hraje soubor zvuku a videa.  
  
-   <xref:System.Windows.Media.DrawingGroup>– Nevykresluje kresby na další. Použijte skupinu kreslení kombinovat jiné kresby do jedné složené kreslení.  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 Například <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> roztahovány jeho <xref:System.Windows.Media.DrawingBrush.Drawing%2A> k vyplnění oblasti jeho výstup. Toto chování můžete přepsat tak, že změníte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí nastavení <xref:System.Windows.Media.Stretch.Fill>. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Příklad: Malování objektů s výkresu  
 Následující příklad ukazuje, jak k vyplnění objekt s kreslení tři výpustky. A <xref:System.Windows.Media.GeometryDrawing> se používá k popisu na symbol tří teček.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Vykreslení vizuálního objektu v oblasti  
 Flexibilní a efektivní všechny stop <xref:System.Windows.Media.VisualBrush> vybarví oblast s <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> je nízké úrovně grafické typ, který slouží jako nadřazeného mnoho užitečné grafické součásti. Například <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.Controls.Control> třídy jsou všechny typy <xref:System.Windows.Media.Visual> objekty. Použití <xref:System.Windows.Media.VisualBrush>, můžete malovat oblasti s téměř jakoukoli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafického objektu.  
  
> [!NOTE]
>  I když <xref:System.Windows.Media.VisualBrush> je typ <xref:System.Windows.Freezable> objektu nemůže být pozastaveny (jen pro čtení) při jeho <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost nastavena na hodnotu než `null`.  
  
 Existují dva způsoby, jak zadat <xref:System.Windows.Media.VisualBrush.Visual%2A> obsah <xref:System.Windows.Media.VisualBrush>.  
  
-   Vytvořte novou <xref:System.Windows.Media.Visual> a použít ho nastavit <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>. Příklad, naleznete v části [příklad: malování objektů s vizuál](#examplevisualbrush1) následující části.  
  
-   Použijte existující <xref:System.Windows.Media.Visual>, který vytváří duplicitní bitovou kopii cíle <xref:System.Windows.Media.Visual>. Pak můžete použít <xref:System.Windows.Media.VisualBrush> vytvořit zajímavé důsledky, jako je například reflexe a zvětšení. Příklad, naleznete v části [příklad: vytvoření odraz](#examplevisualbrush2) části.  
  
 Když definujete novou <xref:System.Windows.Media.VisualBrush.Visual%2A> pro <xref:System.Windows.Media.VisualBrush> a že <xref:System.Windows.Media.Visual> je <xref:System.Windows.UIElement> (například panelu nebo ovládací prvek), rozložení systému běží na <xref:System.Windows.UIElement> a její podřízené elementy při <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> je nastavena na `true`. Ale kořenu <xref:System.Windows.UIElement> je v podstatě izolované od zbytku systému: styly a externí rozložení nelze navrhovaný pro SVS zahrnuje tuto hranici. Proto musí být explicitně určovat velikost kořenu <xref:System.Windows.UIElement>, protože je nadřazené pouze <xref:System.Windows.Media.VisualBrush> a proto ji nelze velikost automaticky sama do oblasti se vykresluje. Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], najdete v článku [rozložení](../../../../docs/framework/wpf/advanced/layout.md).  
  
 Jako <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> roztahovány jeho obsah k vyplnění oblasti jeho výstup. Toto chování můžete přepsat tak, že změníte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z jeho výchozí nastavení <xref:System.Windows.Media.Stretch.Fill>. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Příklad: Malování objektů s vizuál  
 V následujícím příkladu několik ovládacích prvků a panelu se používají k vyplnění obdélníku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Příklad: Vytvoření reflexe  
 Předchozí příklad ukázal, jak vytvořit nový <xref:System.Windows.Media.Visual> pro použití jako pozadí. Můžete použít také <xref:System.Windows.Media.VisualBrush> zobrazíte existující visual; tato funkce umožňuje vytvořit zajímavé vizuální efekty, jako je například odrazů a zvětšení. Následující příklad používá <xref:System.Windows.Media.VisualBrush> vytvořit odraz <xref:System.Windows.Controls.Border> obsahující několik elementy. Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.  
  
 ![A projeví vizuální objekt](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Zrcadlený vizuální objekt  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Další příklady, které ukazují, jak zvětšit části obrazovky a postup vytvoření odrazů najdete v tématu [VisualBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Funkce TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> jsou typy <xref:System.Windows.Media.TileBrush> objekty. <xref:System.Windows.Media.TileBrush>objekty nabízejí značnou část ovládat, jak je pomocí bitové kopie, kreslení nebo visual vykresluje oblast. Například místo právě vykreslování oblast s jedné roztažené image, můžete malovat oblast s řadou dlaždice obrázků, které vytvářejí se vzorem.  
  
 A <xref:System.Windows.Media.TileBrush> má tři hlavní komponenty: obsahu, dlaždice a oblasti výstup.  
  
 ![Součásti TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součástí TileBrush se jedna dlaždice  
  
 ![Součástí Objekt TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součástí TileBrush s více dlaždice  
  
 Další informace o funkcích dlaždice <xref:System.Windows.Media.TileBrush> objekty, najdete [TileBrush přehled](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
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
 [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Ukázka VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)
