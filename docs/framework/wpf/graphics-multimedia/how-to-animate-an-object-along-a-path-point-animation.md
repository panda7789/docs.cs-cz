---
title: 'Postupy: Animace objektu podél cesty (bodová animace)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452893"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Postupy: Animace objektu podél cesty (bodová animace)
Tento příklad ukazuje, jak použít objekt <xref:System.Windows.Media.Animation.PointAnimationUsingPath> k animaci <xref:System.Windows.Point> podél zakřivené cesty.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune <xref:System.Windows.Media.EllipseGeometry> podél cesty definované <xref:System.Windows.Media.PathGeometry>. Vlastnost <xref:System.Windows.Media.EllipseGeometry.Center%2A> geometrie pro tři tečky, která přebírá hodnotu <xref:System.Windows.Point>, určuje její polohu; Chcete-li přesunout geometrii elipsy, animaci jeho vlastnosti <xref:System.Windows.Media.EllipseGeometry.Center%2A>. V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> k animaci vlastnosti <xref:System.Windows.Media.EllipseGeometry.Center%2A> objektu <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Verze kódu předchozí ukázky použila <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.EllipseGeometry>, i když byla použita pouze jedna animace. <xref:System.Windows.Media.Animation.Storyboard> je často nejjednodušší způsob, jak použít více animací, protože tyto animace lze ovládat stejným <xref:System.Windows.Media.Animation.Storyboard>. Nicméně jednodušší způsob, jak použít jedinou animaci na vlastnost při použití kódu, je použít metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>. Příklad naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
