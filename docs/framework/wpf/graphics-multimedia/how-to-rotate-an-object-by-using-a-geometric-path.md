---
title: 'Postupy: Otočení objektu použitím geometrické cesty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 6d6d21f3f7b609cb2933093a6990425deb39d4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398145"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Postupy: Otočení objektu použitím geometrické cesty
Tento příklad ukazuje, jak otočit (pivot) objektu podél geometrické cesty, který je definován <xref:System.Windows.Media.PathGeometry> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá tři <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty přesunout obdélník podél geometrické cesty.  
  
-   První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> , která je použita na obdélníku. Animace generuje úhel hodnoty. Díky obdélník otočit (pivot) podél obrysy cesty.  
  
-   Tyto dva objekty animace <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> hodnoty <xref:System.Windows.Media.TranslateTransform> , která je použita na obdélníku. Využívají obdélník přesunout vodorovně a svisle podél cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Dalším způsobem, jak otočení objektu použitím geometrické cesty je použít <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu a nastavte jeho <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost `true`. Další informace a příklad najdete v tématu [otočení objektu použitím geometrické cesty (animace matice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ukázka animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Postupy: Témata animace cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
