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
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186879"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Postupy: Otočení objektu použitím geometrické cesty
Tento příklad ukazuje, jak otočit (otočit) objekt podél geometrické cesty, která je definována objektem. <xref:System.Windows.Media.PathGeometry>  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> tři objekty k přesunutí obdélníku podél geometrické cesty.  
  
- První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje, <xref:System.Windows.Media.RotateTransform> který je použit na obdélník. Animace generuje hodnoty úhlu. To dělá obdélník otočit (pivot) podél obrysů cesty.  
  
- Ostatní dva objekty <xref:System.Windows.Media.TranslateTransform.X%2A> animovat <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> a hodnoty, které se aplikuje na obdélník. Obdélník se pohybuje vodorovně a svisle podél cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Dalším způsobem, jak otočit objekt pomocí geometrické <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> cesty, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je `true`použít objekt a nastavit jeho vlastnost na . Další informace a příklad viz [Otočení objektu pomocí geometrické cesty (Animace matice).](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)  
  
 Kompletní ukázku naleznete v tématu [Cesta animace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
