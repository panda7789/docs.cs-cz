---
title: Štětce – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186581"
---
# <a name="wpf-brushes-overview"></a>Přehled štětců WPF
Vše, co je na obrazovce viditelné, je viditelné, protože bylo namalováno štětcem. Stopa se například používá k popisu pozadí tlačítka, popředí textu a výplně obrazce. Toto téma představuje koncepty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] malování štětcem a poskytuje příklady. Stopy umožňují malovat [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objekty s čímkoli od jednoduchých plných barev až po složité sady vzorků a obrazů.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Malování štětcem  
 "Maluje" <xref:System.Windows.Media.Brush> oblast s jeho výstupem. Různé stopy mají různé typy výstupů. Některé stopy malují oblast plnou barvou, jiné přechodem, vzorkem, obrazem nebo výkresem. Následující obrázek znázorňuje příklady <xref:System.Windows.Media.Brush> jednotlivých typů.  
  
 ![Typy štětců](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Příklady stopy  
  
 Většina vizuálních objektů umožňuje určit, jak jsou malované. V následující tabulce jsou uvedeny některé běžné <xref:System.Windows.Media.Brush>objekty a vlastnosti, se kterými můžete použít .  
  
|Třída|Vlastnosti stopy|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Následující části popisují <xref:System.Windows.Media.Brush> různé typy a poskytují příklad každého z nich.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Malování plnou barvou  
 A <xref:System.Windows.Media.SolidColorBrush> maluje oblast <xref:System.Windows.Media.Color>s tělesem . Existuje celá řada způsobů, jak <xref:System.Windows.Media.SolidColorBrush.Color%2A> určit <xref:System.Windows.Media.SolidColorBrush>of: například můžete zadat jeho alfa, červená, modrá a zelená kanály nebo <xref:System.Windows.Media.Colors> použít jednu z předdefinovaných barev poskytovaných třídou.  
  
 Následující příklad používá <xref:System.Windows.Media.SolidColorBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník vybarvený pomocí solidcolorbrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Obdélník vyčesaný pomocí SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.SolidColorBrush> třídě naleznete v tématu [Malování plnými barvami a přechody Přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Malování lineárním přechodem  
 A <xref:System.Windows.Media.LinearGradientBrush> maluje oblast s lineárním přechodem. Lineární přechod prolne dvě nebo více barev přes čáru, osu přechodu. Objekty <xref:System.Windows.Media.GradientStop> se používají k určení barev v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.LinearGradientBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník vybarvený pomocí LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Obdélník vyčesaný pomocí LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.LinearGradientBrush> třídě naleznete v tématu [Malování plnými barvami a přechody Přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Malování radiálním přechodem  
 A <xref:System.Windows.Media.RadialGradientBrush> maluje oblast s radiálním přechodem. Kruhový přechod prolne dvě nebo více barev v kruhu. Stejně <xref:System.Windows.Media.LinearGradientBrush> jako u <xref:System.Windows.Media.GradientStop> třídy můžete pomocí objektů určit barvy v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník vybarvený pomocí RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Obdélník vybarvený pomocí RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.RadialGradientBrush> třídě naleznete v tématu [Malování plnými barvami a přechody Přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Malování obrazem  
 Vymaluje <xref:System.Windows.Media.ImageBrush> oblast <xref:System.Windows.Media.ImageSource>s .  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník malované ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Obdélník vybarvený pomocí obrázku  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> třídě naleznete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Malování výkresem  
 A <xref:System.Windows.Media.DrawingBrush> maluje oblast <xref:System.Windows.Media.Drawing>s . A <xref:System.Windows.Media.Drawing> může obsahovat obrazce, obrázky, text a média.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník namalovaný pomocí DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Obdélník malované pomocí DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.DrawingBrush> třídě naleznete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Malování vizuálním  
 A <xref:System.Windows.Media.VisualBrush> maluje oblast <xref:System.Windows.Media.Visual> s objektem. Příklady vizuálních <xref:System.Windows.Controls.Button>objektů: a <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> také umožňuje promítat obsah z jedné části aplikace do jiné oblasti; je to velmi užitečné pro vytváření reflexních efektů a zvětšování částí obrazovky.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaný obdélník.  
  
 ![Obdélník vybarvený pomocí VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Obdélník vybarvené pomocí VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.VisualBrush> třídě naleznete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Malování pomocí předdefinovaných a systémových štětců  
 Pro větší pohodlí poskytuje program Windows Presentation Foundation (WPF) sadu předdefinovaných a systémových stop, které lze použít k malování objektů.  
  
- Seznam dostupných předdefinovaných stop na <xref:System.Windows.Media.Brushes> stopy naleznete v části Třída. Příklad, který ukazuje, jak používat předdefinovanou stopu, najdete v [tématu Malování oblasti plnou barvou](how-to-paint-an-area-with-a-solid-color.md).  
  
- Seznam dostupných systémových štětců naleznete ve <xref:System.Windows.SystemColors> třídě. Příklad například viz [Malování oblasti systémovou stopou](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Běžné funkce štětce  
 <xref:System.Windows.Media.Brush>objekty <xref:System.Windows.Media.Brush.Opacity%2A> poskytují vlastnost, kterou lze použít k vytvoření průhledné stopy nebo částečně průhledné. Hodnota <xref:System.Windows.Media.Brush.Opacity%2A> 0 způsobí, že stopa <xref:System.Windows.Media.Brush.Opacity%2A> bude zcela průhledná, zatímco hodnota 1 způsobí, že stopa bude zcela neprůhledná. Následující příklad používá <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost, <xref:System.Windows.Media.SolidColorBrush> aby se 25 procent neprůhledné.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Pokud stopa obsahuje barvy, které jsou částečně průhledné, hodnota krytí barvy se zkombinuje pomocí násobení s hodnotou krytí stopy. Pokud má například stopa hodnotu krytí 0,5 a barva použitá ve stopě má také hodnotu krytí 0,5, má výstupní barva hodnotu krytí 0,25.  
  
> [!NOTE]
> Je efektivnější změnit hodnotu krytí stopy než změnit krytí celého prvku pomocí jeho vlastnosti. <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>  
  
 Obsah stopy můžete otáčet, měnit jejich velikost, <xref:System.Windows.Media.Brush.Transform%2A> zkosit a překládat pomocí jejích <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastností. Další informace naleznete v tématu [Přehled transformace štětce](brush-transformation-overview.md).  
  
 Protože se <xref:System.Windows.Media.Animation.Animatable> jedná <xref:System.Windows.Media.Brush> o objekty, mohou být objekty animovány. Další informace naleznete v [tématu Přehled animace](animation-overview.md).  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Zmrazitelné funkce  
 Vzhledem k tomu, že dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Brush> třída poskytuje několik speciálních funkcí: <xref:System.Windows.Media.Brush> objekty mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objektů a klonovány. Kromě toho všechny <xref:System.Windows.Media.Brush> typy <xref:System.Windows.Media.VisualBrush> kromě lze provést jen pro čtení ke zlepšení výkonu a z přístupu k vláknům.  
  
 Další informace o různých funkcích <xref:System.Windows.Freezable> poskytovaných objekty naleznete v tématu [Přehled mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
 Další informace o <xref:System.Windows.Media.VisualBrush> tom, proč nelze <xref:System.Windows.Media.VisualBrush> objekty zmrazit, naleznete na stránce typu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Ukázka štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [Ukázka imagebrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Ukázka visualbrushu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [Témata s postupy](brushes-how-to-topics.md)
- [Další doporučení k optimalizaci výkonu](../advanced/optimizing-performance-other-recommendations.md)
