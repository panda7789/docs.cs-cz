---
title: 'Postupy: Transformace štětce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187340"
---
# <a name="how-to-transform-a-brush"></a>Postupy: Transformace štětce
Tento příklad ukazuje, <xref:System.Windows.Media.Brush> jak transformovat objekty <xref:System.Windows.Media.Brush.RelativeTransform%2A> pomocí <xref:System.Windows.Media.Brush.Transform%2A>jejich dvou vlastností transformace: a .  
  
 Následující příklady používají <xref:System.Windows.Media.RotateTransform> k otočení obsahu <xref:System.Windows.Media.ImageBrush> o 45 stupňů.  
  
 Následující obrázek <xref:System.Windows.Media.ImageBrush> znázorňuje <xref:System.Windows.Media.RotateTransform>bez <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> , s aplikovanou vlastností a s <xref:System.Windows.Media.RotateTransform> aplikovanou vlastností. <xref:System.Windows.Media.Brush.Transform%2A>  
  
 ![Nastavení Relativní transformace stopy a transformace](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Příklad  
 První příklad platí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> pro vlastnost <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> Vlastnosti <xref:System.Windows.Media.RotateTransform.CenterY%2A> a <xref:System.Windows.Media.RotateTransform> objektu jsou nastaveny na 0,5, což je relativní souřadnice středového bodu tohoto obsahu. V důsledku toho <xref:System.Windows.Media.ImageBrush> se obsah otáčí kolem svého středu.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Druhý příklad platí také <xref:System.Windows.Media.RotateTransform> pro <xref:System.Windows.Media.ImageBrush>; v tomto příkladu <xref:System.Windows.Media.Brush.Transform%2A> však <xref:System.Windows.Media.Brush.RelativeTransform%2A> používá vlastnost namísto vlastnosti.  
  
 Chcete-li otočit stopu kolem jejího <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> středu, <xref:System.Windows.Media.RotateTransform> příklad nastaví vlastnosti a objektu na absolutní souřadnice. Vzhledem k tomu, že štětec maluje obdélník, který je 175 x 90 pixelů, středový bod obdélníku je (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Popis fungování <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastností <xref:System.Windows.Media.Brush.Transform%2A> a naleznete v tématu [Přehled transformace stopy](brush-transformation-overview.md).  
  
 Úplný vzorek naleznete v tématu [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Další informace o stopách naleznete v [tématu Malování plnými barvami a přechody – přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled transformace štětce](brush-transformation-overview.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Přehled transformace](transforms-overview.md)
