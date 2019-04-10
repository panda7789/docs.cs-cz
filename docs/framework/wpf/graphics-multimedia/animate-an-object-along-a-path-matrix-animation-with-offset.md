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
ms.openlocfilehash: 3e7b892e2a2215d26512850477844d71bce7fe09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207367"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třídy animace objektu podél cesty a animace accumulate posun hodnoty, jak bude správce opakovat.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu pro animaci <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> použitý pro tlačítko. V důsledku toho tlačítko přesune podél zakřivené cesty.  
  
 Kromě toho v příkladu je nastavena <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnost `true`, což způsobí, že posun animovaný matici nashromáždí během animace se opakuje. Protože nahromadí posun přesune na tlačítko dále napříč obrazovku, když je animace se opakuje, nikoli resetování na počáteční pozici.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Všimněte si, že i když <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnosti způsobí, že hodnoty posunu k shromažďování přes opakování, nezpůsobí otočení hodnoty pro shromažďování. Aby otočení hodnoty accumulate, nastavení se animace <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> vlastností `true`.  
  
 Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028). Příklad ukazuje, jak animovat <xref:System.Windows.Media.Matrix> hodnoty podél cesty bez akumulací posunu, naleznete v tématu [animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
