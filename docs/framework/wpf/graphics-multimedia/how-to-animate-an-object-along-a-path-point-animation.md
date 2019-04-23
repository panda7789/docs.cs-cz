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
ms.openlocfilehash: 4ef28118975d02500916676ca50e0f9622c7a3e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129582"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Postupy: Animace objektu podél cesty (bodová animace)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci objektu <xref:System.Windows.Point> podél zakřivené cesty.  
  
## <a name="example"></a>Příklad  
 Následujícím příkladu se přesune <xref:System.Windows.Media.EllipseGeometry> cestě určené <xref:System.Windows.Media.PathGeometry>. Geometrie Elipsa <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost, která přijímá <xref:System.Windows.Point> hodnoty, určuje pozici; přesunout geometrie tři tečky, je animovat jeho <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost. V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci <xref:System.Windows.Media.EllipseGeometry> objektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, přestože byl nastaven pouze jedné animace. A <xref:System.Windows.Media.Animation.Storyboard> často je nejjednodušší způsob, jak použít více animace, protože tyto animace budete mohou být řízena stejné <xref:System.Windows.Media.Animation.Storyboard>. Snadný způsob, jak použít jeden animace do vlastnosti při použití kódu je však použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
