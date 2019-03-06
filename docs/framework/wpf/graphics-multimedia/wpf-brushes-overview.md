---
title: Přehled štětců WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 12671c62a887f863bfb423cf67d7a25eed4118b2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362601"
---
# <a name="wpf-brushes-overview"></a>Přehled štětců WPF
Všechno, co viditelný na obrazovce je viditelné, protože byl kresleno štětce. Například štětce slouží k popisu tlačítka, text popředí a vyplnění obrazce na pozadí. Toto téma představuje koncepty Malování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stopy a příklady. Štětce umožňují vykreslení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objekty se vše od jednoduchých, plné barvy pro komplexní sady vzorce a Image.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Kreslení štětcem  
 A <xref:System.Windows.Media.Brush> "jsou vykreslovány" v oblasti svůj výstup. Různé štětce mají různé typy výstupu. Některé štětce vykreslení oblasti plnou barvou, s přechodem, vzor, image nebo kreslení. Následující obrázek znázorňuje příklady různých <xref:System.Windows.Media.Brush> typy.  
  
 ![Štětec typy](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Příklady štětce  
  
 Většina vizuálních objektů umožňují určit, jak jsou překreslit. Následující tabulka uvádí některé běžné objektů a vlastností, pomocí kterých můžete použít <xref:System.Windows.Media.Brush>.  
  
|Třída|Vlastnosti štětce|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Následující části popisují různé <xref:System.Windows.Media.Brush> typů a uveďte příklad každého.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Malování plnou barvou  
 A <xref:System.Windows.Media.SolidColorBrush> jsou vykreslovány v oblasti ucelený <xref:System.Windows.Media.Color>. Existuje řada různých způsobů, jak zadat <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush>: například můžete určit jeho alfa, červená, modrá a zelená kanály nebo použijte jednu z předdefinované barvy poskytované <xref:System.Windows.Media.Colors> třídy.  
  
 Následující příklad používá <xref:System.Windows.Media.SolidColorBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník překreslit pomocí štětce SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Obdélník překreslit pomocí štětce SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.SolidColorBrush> najdete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Malování pomocí lineárního přechodu  
 A <xref:System.Windows.Media.LinearGradientBrush> jsou vykreslovány v oblasti lineárním přechodem. Lineární přechod prolnutí více řádků, osa přechodu dvě nebo více barev. Použijete <xref:System.Windows.Media.GradientStop> objekty k určení barvy v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.LinearGradientBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník překreslit pomocí LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Obdélník překreslit pomocí LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.LinearGradientBrush> najdete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Malování s paprskového přechodu  
 A <xref:System.Windows.Media.RadialGradientBrush> jsou vykreslovány v oblasti paprskového přechodu. Paprskový přechod prolnutí dvě nebo více barev v kruhu. Stejně jako u <xref:System.Windows.Media.LinearGradientBrush> třídy, je použít <xref:System.Windows.Media.GradientStop> objekty k určení barvy v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník překreslit pomocí RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Obdélník překreslit pomocí RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.RadialGradientBrush> najdete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Malování s obrázkem  
 <xref:System.Windows.Media.ImageBrush> Jsou vykreslovány v oblasti <xref:System.Windows.Media.ImageSource>.  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník kresleno ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Obdélník překreslit pomocí bitové kopie  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Malování s kresby  
 A <xref:System.Windows.Media.DrawingBrush> jsou vykreslovány v oblasti <xref:System.Windows.Media.Drawing>. A <xref:System.Windows.Media.Drawing> může obsahovat tvary, obrázky, text a média.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník překreslit pomocí objektu DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Obdélník překreslit pomocí objektu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.DrawingBrush> najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Malování s Vizuálem  
 A <xref:System.Windows.Media.VisualBrush> jsou vykreslovány v oblasti <xref:System.Windows.Media.Visual> objektu. Příklady vizuální objekty <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, a <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> můžete použít k projekci obsahu z jedné části vaší aplikace do jiné oblasti, je velmi užitečná pro vytváření efektů a zvětšování části obrazovky.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného obdélník.  
  
 ![Obdélník překreslit pomocí VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Obdélník překreslit pomocí VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.VisualBrush> najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Malování pomocí předdefinované a systémových štětců  
 Pro usnadnění práce Windows Presentation Foundation (WPF) poskytuje sadu předdefinovaných a stopy systému, můžete použít k vykreslení objektů.  
  
-   Seznam dostupných předdefinovaných štětce, najdete v článku <xref:System.Windows.Media.Brushes> třídy. Příklad ukazuje, jak použít předdefinované štětce, naleznete v tématu [vykreslení oblasti plnou barvou](how-to-paint-an-area-with-a-solid-color.md).  
  
-   Seznam dostupných systémových štětců, najdete v článku <xref:System.Windows.SystemColors> třídy. Příklad najdete v tématu [vykreslení oblasti systémovým štětcem](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Společné funkce štětce  
 <xref:System.Windows.Media.Brush> objekty poskytují <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost, která je možné provádět štětce průhledného nebo částečně. <xref:System.Windows.Media.Brush.Opacity%2A> Hodnota 0 vytvoří štětce zcela transparentní, při <xref:System.Windows.Media.Brush.Opacity%2A> hodnoty 1 provede štětce stane zcela neprůhledný. V následujícím příkladu <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost, aby <xref:System.Windows.Media.SolidColorBrush> 25 procent neprůhledné.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Obsahuje-li štětec barvy, které jsou částečně transparentní, je hodnota neprůhlednosti barvy sloučené přes násobení hodnotou neprůhlednost štětce. Například pokud štětce má hodnotu neprůhlednosti 0,5 a barvu použitou při štětec má také hodnotu neprůhlednosti 0,5, výstupní barva má hodnotu neprůhlednosti 0,25.  
  
> [!NOTE]
>  Je mnohem efektivnější, chcete-li změnit hodnotu krytí štětce, než je změna neprůhlednost celý prvek pomocí jeho <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> vlastnost.  
  
 Můžete otočit, škálovat, zkosení a převede obsah štětec pomocí jeho <xref:System.Windows.Media.Brush.Transform%2A> nebo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnosti. Další informace najdete v tématu [přehled transformace štětce](brush-transformation-overview.md).  
  
 Protože jde o <xref:System.Windows.Media.Animation.Animatable> objekty, <xref:System.Windows.Media.Brush> objekty lze animovat. Další informace najdete v tématu [přehled animace](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable – funkce  
 Protože dědí sám od <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Brush> třída poskytuje několik speciální funkce: <xref:System.Windows.Media.Brush> objekty mohou být deklarovány jako [prostředky](../advanced/xaml-resources.md)sdílet mezi více objektů a klonování. Kromě toho všechny <xref:System.Windows.Media.Brush> typy s výjimkou <xref:System.Windows.Media.VisualBrush> můžete být jen pro čtení ke zlepšení výkonu a bezpečné pro vlákna.  
  
 Další informace o různých funkcí poskytovaných službou <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../advanced/freezable-objects-overview.md).  
  
 Další informace o důvod, proč <xref:System.Windows.Media.VisualBrush> objekty nelze zmrazené, najdete v článku <xref:System.Windows.Media.VisualBrush> typ stránky.  
  
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
