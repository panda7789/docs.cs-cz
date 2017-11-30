---
title: "Přehled transformace štětce"
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
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b57c5ee36c9ed9c89fc8ca1bfb7ea265c2460c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="brush-transformation-overview"></a>Přehled transformace štětce
Třída štětce poskytuje dvě vlastnosti transformace: <xref:System.Windows.Media.Brush.Transform%2A> a <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Vlastnosti umožňují otočit, škálování, zkreslit a převede štětce obsah. Toto téma popisuje rozdíly mezi tyto dvě vlastnosti a obsahuje příklady jejich využití.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit v tomto tématu byste měli porozumět funkce štětce, která jsou transformace. Pro <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>, najdete v článku [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Pro <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush>, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Měli byste také se seznámit s 2D transformace popsané v [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Rozdíly mezi transformace a RelativeTransform vlastnosti  
 Při použití transformace štětce <xref:System.Windows.Media.Brush.Transform%2A> vlastnost, musíte znát velikost oblasti malovaného Pokud budete chtít transformace štětce obsah o jeho center. Předpokládejme, že malovaného oblast je 200 zařízení nezávislé pixelů a 150 talovat.  Pokud jste použili <xref:System.Windows.Media.RotateTransform> otočení stopy výstupu 45 stupňů o jeho center, by poskytnout <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Při použití transformace štětce <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost použita této transformace stopy před jeho výstup je namapována na malovaného oblasti. Následující seznam popisuje pořadí, ve kterém jsou obsah štětce zpracovat a transformovat.  
  
1.  Zpracovat stopy obsah. Pro <xref:System.Windows.Media.GradientBrush>, to znamená, že určení oblasti přechodu. Pro <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> je namapována na <xref:System.Windows.Media.TileBrush.Viewport%2A>. To se stane stopy výstup.  
  
2.  Projekt stopy výstupu do obdélníku 1 × 1 transformace.  
  
3.  Použít stopy <xref:System.Windows.Media.Brush.RelativeTransform%2A>, pokud jej obsahuje.  
  
4.  Projekt do oblasti pro malování transformovaných výstup.  
  
5.  Použít stopy <xref:System.Windows.Media.Transform>, pokud jej obsahuje.  
  
 Protože <xref:System.Windows.Media.Brush.RelativeTransform%2A> se použije při stopy výstup je namapovaná na obdélníku 1 × 1 transformace center a hodnoty posunutí zobrazí jako relativní. Například, pokud jste použili <xref:System.Windows.Media.RotateTransform> otočení stopy výstupu 45 stupňů o jeho center, by poskytnout <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Následující obrázek ukazuje výstup několik štětce, které byly otáčet o 45 stupňů pomocí <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti.  
  
 ![Vlastnosti RelativeTransform a Transform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Pomocí RelativeTransform Objekt TileBrush  
 Protože dlaždice štětce složitější než ostatní štětce, použití <xref:System.Windows.Media.Brush.RelativeTransform%2A> na jednu může vést k neočekávaným výsledkům. Například trvat na následujícím obrázku.  
  
 ![Zdrojová bitová kopie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vyplnění obdélníkovou oblast s předchozí obrázek. Se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.ImageBrush> objektu <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a nastaví její <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost, která má <xref:System.Windows.Media.Stretch.UniformToFill>, při je roztažen tak, aby úplně vyplnění rámeček, který by měl zachovat poměr stran obrázku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Tento příklad vytvoří následující výstup:  
  
 ![Output transformované](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Všimněte si, že obrázek je narušena, i když štětce <xref:System.Windows.Media.TileBrush.Stretch%2A> byla nastavena na <xref:System.Windows.Media.Stretch.UniformToFill>. Je to způsobeno relativní transformace použijí po stopy <xref:System.Windows.Media.TileBrush.Viewbox%2A> je namapována na jeho <xref:System.Windows.Media.TileBrush.Viewport%2A>. Následující seznam popisuje jednotlivých kroků procesu:  
  
1.  Projekt obsah štětce (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) do jeho základní dlaždice (<xref:System.Windows.Media.TileBrush.Viewport%2A>) pomocí štětce <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení.  
  
     ![Funkce Stretch zobrazení na celé zobrazení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projekt základní dlaždice do obdélníku 1 × 1 transformace.  
  
     ![Mapování zobrazení k transformaci rámeček](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Použít <xref:System.Windows.Media.RotateTransform>.  
  
     ![Použití relativní transformace](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projektu do oblasti pro malování transformovaných základní dlaždice.  
  
     ![Projekt transformovaných štětce do oblasti výstup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Příklad: Otočit ImageBrush 45 stupňů  
 Následující příklad se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Objektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti jsou obě nastaveny na 0,5, bodů relativních souřadnicích center k obsahu. V důsledku toho štětce obsah otáčejí o jeho center.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 V dalším příkladu platí také <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.ImageBrush>, ale používá <xref:System.Windows.Media.Brush.Transform%2A> vlastnost místo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost. Obměna štětce o jeho center <xref:System.Windows.Media.RotateTransform> objektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> musí být nastavená na absolutní souřadnice. Protože rámeček se vykresluje podle stopy 175 o 90 pixelů, je jeho středový bod (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Následující obrázek znázorňuje štětce bez transformace, s transformace použít <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a u transformace použít <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.  
  
 ![Zdokonalit RelativeTransform a transformace nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Tato ukázka je součástí větší ukázky. Kompletní příklad, najdete v článku [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973). Další informace o štětce najdete v tématu [WPF štětce přehled](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [Malování s plnou barvy a přechody – přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Transformuje – přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
