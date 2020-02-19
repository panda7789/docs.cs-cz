---
title: 'Postupy: Animace objektu podél cesty (animace matice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452906"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Postupy: Animace objektu podél cesty (animace matice)
Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animaci objektu podél cesty, která je definována <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje objekt podél cesty následujícím způsobem:  
  
- Aplikuje <xref:System.Windows.Media.MatrixTransform> objektu, aby jej bylo možné přesunout.  
  
- Definuje cestu pomocí <xref:System.Windows.Media.PathGeometry>.  
  
- Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a použije ho k animaci <xref:System.Windows.Media.Matrix> vlastnosti <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> přebírá <xref:System.Windows.Media.PathGeometry> a používá ho ke generování <xref:System.Windows.Media.Matrix>ch hodnot.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Další informace o geometrických cestách najdete v [přehledu geometrie](geometry-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
