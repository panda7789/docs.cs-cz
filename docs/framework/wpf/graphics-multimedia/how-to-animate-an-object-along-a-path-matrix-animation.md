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
ms.openlocfilehash: c0c4f1fad5ab6b8d30e6809aa866b4629d08af23
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363732"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Postupy: Animace objektu podél cesty (animace matice)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třídy animace objektu podél cesty, který je definován <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje objektu podél cesty následujícím způsobem:  
  
-   Se vztahuje <xref:System.Windows.Media.MatrixTransform> na objekt, aby bylo možné přesunout.  
  
-   Definuje cestu s využitím <xref:System.Windows.Media.PathGeometry>.  
  
-   Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a použije ho k animace <xref:System.Windows.Media.Matrix> vlastnost <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Přijímá <xref:System.Windows.Media.PathGeometry> a použije ho k vygenerování <xref:System.Windows.Media.Matrix> hodnoty.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028). Další informace o geometrické cesty, najdete v článku [přehled geometrie](geometry-overview.md).  
  
## <a name="see-also"></a>Viz také:
- [Přehled animace](animation-overview.md)
- [Ukázka animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
