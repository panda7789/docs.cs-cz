---
title: "Přehled štětců WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec7e566e6f56c215bbaeafdfb5c5e97cc0add0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-brushes-overview"></a>Přehled štětců WPF
Všechno viditelný na obrazovce je viditelný, protože byl vykresluje podle štětce. Například štětce se používá k popisu tlačítka, popředí textu a vyplnění obrazce na pozadí. Toto téma představuje koncepty Malování s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stopy a obsahuje příklady. Štětce umožňují malovat [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objekty s vše od jednoduchých, plné barvy pro komplexní skupiny vzory a bitové kopie.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Malování štětcem  
 A <xref:System.Windows.Media.Brush> "vybarví" oblast s její výstup. Různé štětce mají různé typy výstupu. Některé štětce malovat oblast, ostatní uživatelé se přechodu, vzor, image nebo kreslení plnou barvou. Následující obrázek znázorňuje příklady jednotlivých různými <xref:System.Windows.Media.Brush> typy.  
  
 ![Zdokonalit typy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Příklady štětce  
  
 Většina vizuální objekty umožňují určit, jakým způsobem se vykresluje. Následující tabulka uvádí některé běžné objekty a vlastností, pomocí kterých můžete použít <xref:System.Windows.Media.Brush>.  
  
|Třída|Vlastnosti štětce|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Následující části popisují různými <xref:System.Windows.Media.Brush> typy a uveďte příklad jednotlivých.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Malování plnou barvou  
 A <xref:System.Windows.Media.SolidColorBrush> vybarví oblast s ucelený <xref:System.Windows.Media.Color>. Existuje mnoho různých způsobů, jak zadat <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush>: například můžete určit jeho kanály alfa, červené, modré a zelenou nebo použijte jeden z předdefinovaných barvu poskytované <xref:System.Windows.Media.Colors> třídy.  
  
 Následující příklad používá <xref:System.Windows.Media.SolidColorBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Obdélníku vykresluje pomocí SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.SolidColorBrush> třídy najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Malování s lineárního přechodu  
 A <xref:System.Windows.Media.LinearGradientBrush> vybarví oblast s lineárního přechodu. Lineárního přechodu smíchá dvě nebo více barev více řádků, přechodu osy. Používáte <xref:System.Windows.Media.GradientStop> objekty, které chcete zadat barvy v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.LinearGradientBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Obdélníku vykresluje pomocí LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.LinearGradientBrush> třídy najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Malování s kruhového přechodu  
 A <xref:System.Windows.Media.RadialGradientBrush> vybarví oblast s kruhového přechodu. Kruhového přechodu smíchá dvě nebo více barev napříč kruh. Stejně jako u <xref:System.Windows.Media.LinearGradientBrush> třídy, použijete <xref:System.Windows.Media.GradientStop> objekty, které chcete zadat barvy v přechodu a jejich umístění.  
  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Obdélníku vykresluje pomocí RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.RadialGradientBrush> třídy najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Malování s bitovou kopií  
 <xref:System.Windows.Media.ImageBrush> Vybarví oblast s <xref:System.Windows.Media.ImageSource>.  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí objektu ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Obdélníku vykresluje pomocí bitové kopie  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> třídy najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Malování s výkresu  
 A <xref:System.Windows.Media.DrawingBrush> vybarví oblast s <xref:System.Windows.Media.Drawing>. A <xref:System.Windows.Media.Drawing> může obsahovat tvarů, obrázky, text a média.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí objektu DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Obdélníku vykresluje pomocí objektu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.DrawingBrush> třídy najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Malování s vizuál  
 A <xref:System.Windows.Media.VisualBrush> vybarví oblast s <xref:System.Windows.Media.Visual> objektu. Příklady vizuální objekty <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, a <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> také umožňuje projektu obsah z jednoho část vaší aplikace do jiné oblasti; je velmi užitečná pro reflexe důsledky vytváření a zvětšování části obrazovky.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Následující obrázek znázorňuje malovaného rámeček.  
  
 ![Obdélníku vykresluje pomocí VisualBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Obdélníku vykresluje pomocí VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.VisualBrush> třídy najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Malování pomocí předem definovaná a systému štětce  
 Pro usnadnění práce [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] poskytuje sadu předdefinovaných a systému stopy používané k vyplnění objekty.  
  
-   Seznam předdefinovaných štětce k dispozici, najdete v článku <xref:System.Windows.Media.Brushes> třídy. Příkladem zobrazujícím postup používání předdefinovaných štětce, najdete v části [malovat oblast plnou barvou](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).  
  
-   Seznam dostupných systémových štětce najdete v tématu <xref:System.Windows.SystemColors> třídy. Příklad, naleznete v části [malovat oblast štětcem systému](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Společné funkce štětce  
 <xref:System.Windows.Media.Brush>Zadejte objekty <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost, která lze použít k vytvoření štětce transparentní nebo částečně transparentní. <xref:System.Windows.Media.Brush.Opacity%2A> Hodnotě 0 je zcela transparentní, při štětce <xref:System.Windows.Media.Brush.Opacity%2A> hodnotu 1 bude štětce zcela neprůhledná. Následující příklad používá <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost, aby <xref:System.Windows.Media.SolidColorBrush> neprůhledného 25 procent.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Obsahuje-li stopy barev, které jsou částečně transparentní, je hodnota neprůhlednosti barvy kombinaci prostřednictvím násobení s hodnotou krytí štětce. Například pokud má hodnota krytí 0,5 štětce a barvu použitou v stopy má také hodnota krytí 0,5, barvu výstup má hodnota krytí 0,25.  
  
> [!NOTE]
>  Chcete-li změnit hodnotu krytí štětce, než se dá změnit krytí k celý elementu pomocí je efektivnější jeho <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> vlastnost.  
  
 Můžete otočit, škálovat, zkreslit a převede štětce obsah pomocí jeho <xref:System.Windows.Media.Brush.Transform%2A> nebo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnosti. Další informace najdete v tématu [štětce transformace přehled](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Protože jsou <xref:System.Windows.Media.Animation.Animatable> objekty, <xref:System.Windows.Media.Brush> objekty mohou být animace. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Zmrazitelné funkce  
 Protože dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Brush> třída poskytuje několik speciální funkce: <xref:System.Windows.Media.Brush> objekty lze deklarovat jako [prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md)sdílen více objektů a klonovat. Kromě toho všechny <xref:System.Windows.Media.Brush> typy s výjimkou <xref:System.Windows.Media.VisualBrush> může být jen pro čtení ke zlepšení výkonu a provedené bezpečné pro přístup z více vláken.  
  
 Další informace o různých funkcí poskytovaných <xref:System.Windows.Freezable> objekty, najdete v části [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Další informace o důvod, proč <xref:System.Windows.Media.VisualBrush> objekty nelze pozastaveny, najdete v článku <xref:System.Windows.Media.VisualBrush> typ stránky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Ukázka štětce](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Ukázka VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
