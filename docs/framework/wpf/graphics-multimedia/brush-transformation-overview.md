---
title: Přehled transformace štětce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: 2cfa796d40fad35077c3d7b55e36bc7336c5d26b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562762"
---
# <a name="brush-transformation-overview"></a>Přehled transformace štětce
Třída štětce poskytuje dvě vlastnosti transformace: <xref:System.Windows.Media.Brush.Transform%2A> a <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Vlastnosti umožňují otočit, škálování a zkosení a převede štětec obsah. Toto téma popisuje rozdíly mezi těmito dvěma vlastnostmi a poskytuje příklady jejich použití.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste porozumět funkce štětec, který je transformace. Pro <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>, najdete v článku [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Pro <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush>, naleznete v tématu [Malování pomocí obrázků, kreseb a vizuálních](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Také by měl být obeznámeni s 2D transformace podle [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Rozdíly mezi transformace a RelativeTransform vlastnosti  
 Při použití transformace štětec <xref:System.Windows.Media.Brush.Transform%2A> vlastnost, musíte znát velikosti oblasti malovaného Pokud budete chtít transformace štětce obsah o jeho střed. Předpokládejme, že malovaného oblast je 200 zařízení nezávislé pixelů na šířku a výšku 150.  Pokud jste použili <xref:System.Windows.Media.RotateTransform> otočit štětec výstup 45 stupňů o jeho střed, by dáte <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Při použití transformace štětec <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost, že je použita transformace štětce před jeho výstupu se mapuje na oblasti malovaného. Následující seznam popisuje pořadí, ve kterém se zpracovat a transformovat štětec obsah.  
  
1.  Zpracovat obsah na stopu. Pro <xref:System.Windows.Media.GradientBrush>, to znamená, že určující oblasti přechodu. Pro <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> je namapována na <xref:System.Windows.Media.TileBrush.Viewport%2A>. To se stane stopy výstup.  
  
2.  Nástroj štětec výstupu projektu do obdélníku 1 × 1 transformace.  
  
3.  Použití štětce společnosti <xref:System.Windows.Media.Brush.RelativeTransform%2A>, má-li nějaký.  
  
4.  Transformovaný výstup projektu do oblasti pro vykreslení.  
  
5.  Použití štětce společnosti <xref:System.Windows.Media.Transform>, má-li nějaký.  
  
 Vzhledem k tomu, <xref:System.Windows.Media.Brush.RelativeTransform%2A> se použije při stopy výstup je namapovaná na 1 × 1 obdélníku, center transformace a posunutí hodnoty se zdají být relativní. Například, pokud jste použili <xref:System.Windows.Media.RotateTransform> otočit štětec výstup 45 stupňů o jeho střed, by dáte <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Následující obrázek znázorňuje výstup několik štětců, které byly otočit o 45 stupňů pomocí <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti.  
  
 ![Vlastnosti RelativeTransform a transformace](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Funkci RelativeTransform pomocí TileBrush  
 Vzhledem k tomu dlaždice štětce složitější než ostatní štětce, použití <xref:System.Windows.Media.Brush.RelativeTransform%2A> do jednoho může vést k neočekávaným výsledkům. Jako příklad může posloužit na následujícím obrázku.  
  
 ![Zdroj image](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> má Vymalovat obdélníkovou oblast s předchozím obrázku. Se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.ImageBrush> objektu <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a nastaví jeho <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.Stretch.UniformToFill>, který mělo zachovat poměr stran obrázku je mohla pro úplně naplnění obdélníku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Tento příklad vytvoří následující výstup:  
  
 ![Transformovaný výstup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Všimněte si, že na obrázku je zkreslený, i když na stopu <xref:System.Windows.Media.TileBrush.Stretch%2A> byl nastaven na <xref:System.Windows.Media.Stretch.UniformToFill>. Důvodem je, že je relativní transformace použita po stopy <xref:System.Windows.Media.TileBrush.Viewbox%2A> je namapována na jeho <xref:System.Windows.Media.TileBrush.Viewport%2A>. Následující seznam popisuje jednotlivé kroky procesu:  
  
1.  Projekt na stopu obsah (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na jeho základní dlaždice (<xref:System.Windows.Media.TileBrush.Viewport%2A>) štětec pomocí <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení.  
  
     ![Roztažení Viewbox přizpůsobit zobrazení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projekt základní dlaždice na 1 × 1 transformace obdélník.  
  
     ![Zobrazení mapy na obdélník transformace](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Použít <xref:System.Windows.Media.RotateTransform>.  
  
     ![Umožňuje aplikovat relativní transformaci](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projekt transformovaný základní dlaždice do oblasti pro vykreslení.  
  
     ![Transformovaný štětce projektu do výstupní oblasti](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Příklad: Otočit ImageBrush 45 stupňů  
 Následující příklad se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Objektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti jsou obě nastaveny na 0,5, bod relativních souřadnicích center obsah. V důsledku toho jsou otočeny stopy obsah o jeho střed.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 V dalším příkladu platí také <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, ale používá <xref:System.Windows.Media.Brush.Transform%2A> vlastnost místo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost. Otočit štětec o jeho střed <xref:System.Windows.Media.RotateTransform> objektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> musí být nastavena na absolutní souřadnice. Vzhledem k tomu, že obdélník se kresleno štětec je 175 o 90 pixelů, je jeho středového bodu (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Následující obrázek znázorňuje štětce bez transformace, s transformací, která se použije k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a s transformací, která se použije k <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.  
  
 ![Štětec RelativeTransform workflow a transformovat nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 V tomto příkladu je součástí větší ukázky. Úplnou ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o štětcích, najdete v článku [přehled štětců WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
