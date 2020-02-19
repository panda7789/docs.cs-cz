---
title: 'Postupy: Animace objektu podél cesty (dvojitá animace)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452854"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Postupy: Animace objektu podél cesty (dvojitá animace)
Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> k přesunutí objektu podél cesty definované <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty pro přesunutí obdélníku podél geometrické cesty:  
  
- První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> použité pro obdélník. Tím se obdélník přesune vodorovně podél cesty.  
  
- Druhý <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> použité pro obdélník. Tím se obdélník přesune svisle podél cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Jiný způsob, jak přesunout objekt pomocí geometrické cesty, je použít objekt <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>. Příklad naleznete v tématu [animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
