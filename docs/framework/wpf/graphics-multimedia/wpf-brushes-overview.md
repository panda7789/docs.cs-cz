---
title: Přehled štětců WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 8a1d05ad48ce75ce67d21d5a4d508015fea879b2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458623"
---
# <a name="wpf-brushes-overview"></a>Přehled štětců WPF
Vše viditelné na obrazovce je viditelné, protože bylo vykresleno štětcem. Například štětce se používá k popisu pozadí tlačítka, popředí textu a výplně tvaru. Toto téma představuje koncepty malování pomocí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] štětce a obsahuje příklady. Štětce umožňují malovat [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objekty s cokoli od jednoduchých, plných barev až po složité sady vzorů a imagí.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Malování pomocí štětce  
 <xref:System.Windows.Media.Brush> "vykreslí" oblast s jejími výstupy. Různé štětce mají různé typy výstupu. Některé štětce vykreslí oblast s plnou barvou, ostatními pomocí přechodu, vzorku, obrázku nebo kresby. Následující ilustrace ukazuje příklady každého z různých typů <xref:System.Windows.Media.Brush>.  
  
 ![Typy štětců](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Příklady štětce  
  
 Většina vizuálních objektů vám umožní určit, jak se mají vykreslit. V následující tabulce jsou uvedeny některé běžné objekty a vlastnosti, se kterými můžete použít <xref:System.Windows.Media.Brush>.  
  
|Třída|Vlastnosti štětce|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A><xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A><xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Následující části popisují různé typy <xref:System.Windows.Media.Brush> a poskytují příklad každého z nich.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Malování plnou barvou  
 <xref:System.Windows.Media.SolidColorBrush> vykreslí oblast s plným <xref:System.Windows.Media.Color>. Existuje mnoho způsobů, jak určit <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>: můžete například zadat alfa, červené, modré a zelené kanály nebo použít jednu z předdefinovaných barev, kterou poskytuje třída <xref:System.Windows.Media.Colors>.  
  
 Následující příklad používá <xref:System.Windows.Media.SolidColorBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vykreslený pomocí SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Obdélník vykreslený pomocí SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.SolidColorBrush> naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Malování lineárním přechodem  
 <xref:System.Windows.Media.LinearGradientBrush> vykreslí oblast lineárním přechodem. Lineární přechod smíchá dvě nebo více barev v rámci čáry, osu přechodu. Pomocí <xref:System.Windows.Media.GradientStop> objektů můžete určit barvy v přechodu a jejich pozice.  
  
 Následující příklad používá <xref:System.Windows.Media.LinearGradientBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vykreslený pomocí LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Obdélník vykreslený pomocí LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.LinearGradientBrush> naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Malování paprskovým přechodem  
 <xref:System.Windows.Media.RadialGradientBrush> vykreslí oblast s paprskovým přechodem. Paprskový přechod prolíná dvě nebo více barev v kruhu. Stejně jako u <xref:System.Windows.Media.LinearGradientBrush> třídy lze pomocí objektů <xref:System.Windows.Media.GradientStop> určit barvy v přechodu a jejich pozice.  
  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vykreslený pomocí RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Obdélník vykreslený pomocí RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.RadialGradientBrush> naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Malování s použitím obrázku  
 <xref:System.Windows.Media.ImageBrush> vykreslí oblast s <xref:System.Windows.Media.ImageSource>.  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vybarvený ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Obdélník vykreslený pomocí obrázku  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.ImageBrush> najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Malování s kreslením  
 <xref:System.Windows.Media.DrawingBrush> vykreslí oblast s <xref:System.Windows.Media.Drawing>. <xref:System.Windows.Media.Drawing> může obsahovat tvary, obrázky, text a multimédia.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vykreslený pomocí prostředek DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Obdélník vykreslený pomocí prostředek DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.DrawingBrush> najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Malování pomocí vizuálu  
 <xref:System.Windows.Media.VisualBrush> vykreslí oblast s objektem <xref:System.Windows.Media.Visual>. Příklady vizuálních objektů zahrnují <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>a <xref:System.Windows.Controls.MediaElement>. <xref:System.Windows.Media.VisualBrush> také umožňuje projektovat obsah z jedné části aplikace do jiné oblasti. je velmi užitečné pro vytváření efektů odrazu a zvětšování částí obrazovky.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vykreslování <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Následující ilustrace znázorňuje namalované obdélník.  
  
 ![Obdélník vykreslený pomocí VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Obdélník vykreslený pomocí VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Další informace o třídě <xref:System.Windows.Media.VisualBrush> najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Malování pomocí předdefinovaných a systémových štětců  
 Pro usnadnění nabízí Windows Presentation Foundation (WPF) sadu předdefinovaných a systémových štětců, které můžete použít k malování objektů.  
  
- Seznam dostupných předdefinovaných štětců naleznete v tématu Třída <xref:System.Windows.Media.Brushes>. Příklad ukazující použití předdefinovaného štětce naleznete v tématu [vykreslení oblasti plnou barvou](how-to-paint-an-area-with-a-solid-color.md).  
  
- Seznam dostupných systémových štětců naleznete v tématu Třída <xref:System.Windows.SystemColors>. Příklad najdete v tématu [Malování oblasti pomocí systémového štětce](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Běžné funkce štětce  
 objekty <xref:System.Windows.Media.Brush> poskytují vlastnost <xref:System.Windows.Media.Brush.Opacity%2A>, která se dá použít k vytvoření štětce transparentního nebo částečně transparentního. <xref:System.Windows.Media.Brush.Opacity%2A> hodnota 0 provede štětec zcela transparentní, zatímco hodnota <xref:System.Windows.Media.Brush.Opacity%2A> 1 změní štětec zcela neprůhledný. Následující příklad používá vlastnost <xref:System.Windows.Media.Brush.Opacity%2A> k zajištění <xref:System.Windows.Media.SolidColorBrush> 25 procent neprůhledných.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Pokud štětec obsahuje barvy, které jsou částečně transparentní, hodnota neprůhlednosti barvy je kombinována po násobení s hodnotou neprůhlednosti štětce. Například pokud má štětec hodnotu neprůhlednosti 0,5 a barva použitá v štětci má také hodnotu neprůhlednosti 0,5, výstupní barva má hodnotu neprůhlednosti 0,25.  
  
> [!NOTE]
> Je efektivnější změnit hodnotu neprůhlednosti štětce, než je změna neprůhlednosti celého prvku pomocí jeho vlastnosti <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>.  
  
 Obsah štětce můžete otáčet, škálovat, zkosit a překládat ho pomocí jeho <xref:System.Windows.Media.Brush.Transform%2A> nebo vlastností <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Další informace najdete v tématu [Přehled transformace štětce](brush-transformation-overview.md).  
  
 Vzhledem k tomu, že jsou objekty <xref:System.Windows.Media.Animation.Animatable>, mohou být objekty <xref:System.Windows.Media.Brush> animovány. Další informace najdete v tématu [Přehled animací](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Funkce Freezable  
 Vzhledem k tomu, že dědí z třídy <xref:System.Windows.Freezable>, poskytuje <xref:System.Windows.Media.Brush> třídy několik speciálních funkcí: <xref:System.Windows.Media.Brush> objektů lze deklarovat jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílet mezi více objekty a klonovat. Kromě toho mohou být všechny typy <xref:System.Windows.Media.Brush> s výjimkou <xref:System.Windows.Media.VisualBrush> vytvořeny jen pro čtení, aby se zlepšil výkon a bylo bezpečné pro přístup z více vláken.  
  
 Další informace o různých funkcích poskytovaných <xref:System.Windows.Freezable> objekty naleznete v tématu [Freezable Objects Overview](../advanced/freezable-objects-overview.md).  
  
 Další informace o tom, proč <xref:System.Windows.Media.VisualBrush> objekty nemůžou být zmrazené, najdete na stránce typu <xref:System.Windows.Media.VisualBrush>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973)
- [Ukázka ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Ukázka VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
- [Témata s postupy](brushes-how-to-topics.md)
- [Další výkonnostní doporučení](../advanced/optimizing-performance-other-recommendations.md)
