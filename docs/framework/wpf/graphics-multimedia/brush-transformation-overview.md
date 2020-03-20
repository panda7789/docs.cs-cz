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
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186517"
---
# <a name="brush-transformation-overview"></a>Přehled transformace štětce
Třída Brush poskytuje dvě <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti transformace: a <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Vlastnosti umožňují otáčet, měnit velikost, zkosit a překládat obsah stopy. Toto téma popisuje rozdíly mezi těmito dvěma vlastnostmi a poskytuje příklady jejich použití.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste pochopit vlastnosti štětce, které transformujete. Pro <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>a , viz [Přehled malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md). Informace <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>o <xref:System.Windows.Media.VisualBrush>aplikaci , nebo [.](painting-with-images-drawings-and-visuals.md) Měli byste být také obeznámeni s 2D transformace popsané v [Přehled transformací](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Rozdíly mezi vlastnostmi Transformace a RelativeTransform  
 Když aplikujete transformaci na <xref:System.Windows.Media.Brush.Transform%2A> vlastnost stopy, musíte znát velikost malované oblasti, pokud chcete transformovat obsah stopy kolem jejího středu. Předpokládejme, že malovaná oblast je 200 pixelů nezávislých na zařízení a 150 vysokých.  Pokud jste <xref:System.Windows.Media.RotateTransform> použili otočit stopy výstup 45 stupňů kolem jeho <xref:System.Windows.Media.RotateTransform> středu, měli byste dát <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 a <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Když aplikujete transformaci na <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost stopy, tato transformace se aplikuje na stopu před jeho výstup je mapován na malované oblasti. Následující seznam popisuje pořadí, ve kterém jsou zpracovány a transformovány obsah stopy.  
  
1. Zpracujte obsah štětce. Pro <xref:System.Windows.Media.GradientBrush>, to znamená určení oblasti přechodu. V <xref:System.Windows.Media.TileBrush>a <xref:System.Windows.Media.TileBrush.Viewbox%2A> , je mapována na <xref:System.Windows.Media.TileBrush.Viewport%2A>. To se stane výstupem stopy.  
  
2. Promítat výstup stopy na obdélník transformace 1 x 1.  
  
3. Naneste štětec <xref:System.Windows.Media.Brush.RelativeTransform%2A>, pokud má jeden.  
  
4. Promítne transformovaný výstup na oblast, kterou chcete malovat.  
  
5. Naneste štětec <xref:System.Windows.Media.Transform>, pokud má jeden.  
  
 Vzhledem <xref:System.Windows.Media.Brush.RelativeTransform%2A> k tomu, že se použije, když je výstup stopy mapován na obdélník 1 x 1, hodnoty středu transformace a odsazení se zdají být relativní. Pokud jste například <xref:System.Windows.Media.RotateTransform> použili a otočit výstup stopy o 45 stupňů <xref:System.Windows.Media.RotateTransform> kolem <xref:System.Windows.Media.RotateTransform.CenterX%2A> jeho středu, <xref:System.Windows.Media.RotateTransform.CenterY%2A> dali byste 0,5 a 0,5.  
  
 Následující obrázek znázorňuje výstup několika stop, které byly otočeny o 45 stupňů pomocí vlastností <xref:System.Windows.Media.Brush.RelativeTransform%2A> a. <xref:System.Windows.Media.Brush.Transform%2A>  
  
 ![Vlastnosti RelativeTransform a Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>Použití RelativeTransform s TileBrush  
 Vzhledem k tomu, že stopy dlaždic <xref:System.Windows.Media.Brush.RelativeTransform%2A> jsou složitější než jiné stopy, může použití a na jeden způsobit neočekávané výsledky. Vezměte například následující obrázek.  
  
 ![Zdrojový obrázek](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> a malovat obdélníkovou oblast s předchozím obrazem. Aplikuje a <xref:System.Windows.Media.RotateTransform> na <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost objektu a <xref:System.Windows.Media.TileBrush.Stretch%2A> nastaví <xref:System.Windows.Media.Stretch.UniformToFill>jeho vlastnost na , což by mělo zachovat poměr stran obrazu, když je roztažen, aby zcela vyplnil obdélník.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Tento příklad vytváří následující výstup:  
  
 ![Transformovaný výstup](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Všimněte si, že obraz je zkreslený, i když byl stopový <xref:System.Windows.Media.TileBrush.Stretch%2A> kontakt nastaven na <xref:System.Windows.Media.Stretch.UniformToFill>. Je to proto, že relativní transformace je <xref:System.Windows.Media.TileBrush.Viewbox%2A> použita po <xref:System.Windows.Media.TileBrush.Viewport%2A>štětec je mapován na jeho . Následující seznam popisuje každý krok procesu:  
  
1. Promítat obsah stopy (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na<xref:System.Windows.Media.TileBrush.Viewport%2A>jeho základní dlaždici ( ) pomocí nastavení stopy. <xref:System.Windows.Media.TileBrush.Stretch%2A>  
  
     ![Roztažení viewboxu tak, aby se vešel do výřezu](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Promítnouzákladní dlaždici na obdélník transformace 1 x 1.  
  
     ![Mapování výřezu na transformační obdélník](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Použít <xref:System.Windows.Media.RotateTransform>.  
  
     ![Použít relativní transformaci](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Promítat transformovnou základní dlaždici na oblast, kterou chcete malovat.  
  
     ![Promítání transformovanéstopy na výstupní oblast](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Příklad: Otočení imageBrush 45 stupňů  
 Následující příklad platí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> pro vlastnost <xref:System.Windows.Media.ImageBrush>. Vlastnosti <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> objektu <xref:System.Windows.Media.RotateTransform.CenterY%2A> a vlastnosti jsou nastaveny na 0,5, relativní souřadnice středového bodu obsahu. V důsledku toho se obsah stopy otáčí kolem jeho středu.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Další příklad také platí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.ImageBrush>na , <xref:System.Windows.Media.Brush.Transform%2A> ale používá <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost namísto vlastnosti. Chcete-li otočit stopu <xref:System.Windows.Media.RotateTransform> kolem jejího <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> středu, musí být objekt a musí být nastaveny na absolutní souřadnice. Vzhledem k tomu, že obdélník malovaný stopou je 175 x 90 pixelů, jeho středový bod je (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Následující obrázek znázorňuje stopu bez transformace, <xref:System.Windows.Media.Brush.RelativeTransform%2A> s transformací aplikovanou na vlastnost a s transformací aplikovanou na <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.  
  
 ![Nastavení Relativní transformace stopy a transformace](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Tento příklad je součástí větší ukázky. Úplný vzorek naleznete v části [Ukázka štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Další informace o stopách naleznete v přehledu [stop wpf](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled transformace](transforms-overview.md)
