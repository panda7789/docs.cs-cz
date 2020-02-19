---
title: 'Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453101"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)
Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animaci objektu podél cesty a k tomu, aby animace nashromáždila hodnoty posunutí při opakování.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá objekt <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animování vlastnosti <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform> použité pro tlačítko. V důsledku toho se tlačítko přesune podél zakřivené cesty.  
  
 Kromě toho příklad nastavuje vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> na `true`, což způsobí, že posun animované matice se nashromáždí jako opakování animace. Vzhledem k tomu, že posunování se sestavuje, tlačítko se při opakování animace místo resetování na počáteční pozici přesune přes obrazovku na obrazovce.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Všimněte si, že i když vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> způsobí, že hodnoty posunutí budou v průběhu opakování shromažďovány, nezpůsobí nahromadění hodnot rotace. Chcete-li nashromáždit hodnoty rotace, nastavte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> animace a vlastnosti <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> na `true`.  
  
 Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Příklad ukazující postup animace <xref:System.Windows.Media.Matrix> hodnoty podél cesty bez akumulace posunu naleznete v tématu [animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
