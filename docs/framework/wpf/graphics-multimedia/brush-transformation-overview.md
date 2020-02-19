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
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453127"
---
# <a name="brush-transformation-overview"></a>Přehled transformace štětce
Třída štětce poskytuje dvě vlastnosti transformace: <xref:System.Windows.Media.Brush.Transform%2A> a <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Vlastnosti umožňují otáčet, škálovat, zkosit a překládat obsah štětce. Toto téma popisuje rozdíly mezi těmito dvěma vlastnostmi a poskytuje příklady jejich použití.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Předpoklady  
 Pro pochopení tohoto tématu byste měli pochopit funkce štětce, které transformují. <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>najdete v tématu [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md). <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>nebo <xref:System.Windows.Media.VisualBrush>, najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md). Měli byste se také seznámit s 2D transformacemi popsanými v [přehledu transformací](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Rozdíly mezi vlastnostmi Transform a funkci RelativeTransform  
 Když aplikujete transformaci na vlastnost <xref:System.Windows.Media.Brush.Transform%2A> štětce, je potřeba znát velikost oblasti namalované, pokud chcete transformovat obsah štětce o jeho středu. Předpokládejme, že oblast namalovaného zařízení je 200 nezávisle na velikosti zařízení 150, která je ve vysokém  Pokud jste použili <xref:System.Windows.Media.RotateTransform> k otočení výstupu štětce o 45 stupňů od jeho středu, získáte <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Když použijete transformaci na vlastnost <xref:System.Windows.Media.Brush.RelativeTransform%2A> štětce, tato transformace se aplikuje na štětec předtím, než se jeho výstup namapuje na oblast vykreslení. Následující seznam popisuje pořadí, ve kterém se obsah štětce zpracovává a transformuje.  
  
1. Zpracuje obsah štětce. Pro <xref:System.Windows.Media.GradientBrush>to znamená, že se určí oblast přechodu. Pro <xref:System.Windows.Media.TileBrush>je <xref:System.Windows.Media.TileBrush.Viewbox%2A> namapován na <xref:System.Windows.Media.TileBrush.Viewport%2A>. Toto se zobrazí jako výstup štětce.  
  
2. Promítnout výstup štětce do obdélníku transformace 1 x 1  
  
3. Použijte <xref:System.Windows.Media.Brush.RelativeTransform%2A>štětce, pokud má jednu z nich.  
  
4. Namalujte transformované výstupy na oblast, která se má malovat.  
  
5. Použijte <xref:System.Windows.Media.Transform>štětce, pokud má jednu z nich.  
  
 Vzhledem k tomu, že <xref:System.Windows.Media.Brush.RelativeTransform%2A> je použit, zatímco výstup štětce je namapován na 1 x 1 obdélník, hodnoty pro transformaci a posunutí se jeví jako relativní. Pokud jste například použili <xref:System.Windows.Media.RotateTransform> k otočení výstupu štětce 45 stupňů od jeho středu, získáte <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Následující ilustrace znázorňuje výstup několika štětců, které byly otočeny o 45 stupňů pomocí vlastností <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Vlastnosti funkci RelativeTransform a Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Použití funkci RelativeTransform s objektem TileBrush  
 Vzhledem k tomu, že štětce dlaždic jsou složitější než jiné štětce, může použití <xref:System.Windows.Media.Brush.RelativeTransform%2A> na jednu způsobit neočekávané výsledky. Například proveďte následující obrázek.  
  
 ![Zdrojový obrázek](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k vykreslení obdélníkové oblasti s předchozím obrázkem. Aplikuje <xref:System.Windows.Media.RotateTransform> na vlastnost <xref:System.Windows.Media.Brush.RelativeTransform%2A> objektu <xref:System.Windows.Media.ImageBrush> a nastaví jeho vlastnost <xref:System.Windows.Media.TileBrush.Stretch%2A> na <xref:System.Windows.Media.Stretch.UniformToFill>, která by měla zachovat poměr stran obrázku, když je roztažen tak, aby byl obdélník zcela vyplněn.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Tento příklad vytvoří následující výstup:  
  
 ![Transformovaný výstup](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Všimněte si, že obrázek je zkreslený, i když <xref:System.Windows.Media.TileBrush.Stretch%2A> štětce byl nastaven na <xref:System.Windows.Media.Stretch.UniformToFill>. To je proto, že se použije relativní transformace po namapování <xref:System.Windows.Media.TileBrush.Viewbox%2A> štětce na jeho <xref:System.Windows.Media.TileBrush.Viewport%2A>. Následující seznam popisuje jednotlivé kroky procesu:  
  
1. Promítnout obsah štětce (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na základní dlaždici (<xref:System.Windows.Media.TileBrush.Viewport%2A>) pomocí nastavení <xref:System.Windows.Media.TileBrush.Stretch%2A> štětce.  
  
     ![Roztáhnout Viewbox tak, aby odpovídala zobrazení](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Promítnout základní dlaždici na transformační obdélník 1 x 1  
  
     ![Mapování zobrazení na obdélník transformace](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Použijte <xref:System.Windows.Media.RotateTransform>.  
  
     ![Použít relativní transformaci](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Namalovat transformaci na základní dlaždici na oblast, která se má vykreslit.  
  
     ![Projekt transformované štětce do výstupní oblasti](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Příklad: otočení ImageBrush 45 stupňů  
 Následující příklad aplikuje <xref:System.Windows.Media.RotateTransform> na vlastnost <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.ImageBrush>. Vlastnosti objektu <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> jsou nastaveny na hodnotu 0,5, relativní souřadnice centrálního bodu obsahu. V důsledku toho se obsah štětce otočí o jeho středu.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Následující příklad také použije <xref:System.Windows.Media.RotateTransform> na <xref:System.Windows.Media.ImageBrush>, ale místo vlastnosti <xref:System.Windows.Media.Brush.RelativeTransform%2A> používá vlastnost <xref:System.Windows.Media.Brush.Transform%2A>. Pro otočení štětce o jeho středu musí být <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> objektu <xref:System.Windows.Media.RotateTransform> nastavena na absolutní souřadnice. Vzhledem k tomu, že obdélník, který je vykreslen štětcem, je 175 × 90 pixelů, jeho středový bod je (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Následující ilustrace znázorňuje štětec bez transformace, s transformací použitou na vlastnost <xref:System.Windows.Media.Brush.RelativeTransform%2A> a s transformací použitou na vlastnost <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Nastavení funkci RelativeTransform štětce a transformace](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Tento příklad je součástí většího vzorku. Úplnou ukázku najdete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Další informace o štětcích naleznete v [přehledu štětců WPF](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled transformace](transforms-overview.md)
