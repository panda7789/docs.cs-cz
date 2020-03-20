---
title: 'Postupy: Otočení objektu použitím geometrické cesty (animace matice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187415"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Postupy: Otočení objektu použitím geometrické cesty (animace matice)
Tento příklad ukazuje, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> jak <xref:System.Windows.Media.MatrixTransform> použít a a otočit (otočit) objekt <xref:System.Windows.Media.PathGeometry> podél geometrické cesty definované objektem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci <xref:System.Windows.Media.MatrixTransform>vlastnosti . Použije <xref:System.Windows.Media.MatrixTransform> se na tlačítko a způsobí, že se pohybuje po zakřivené cestě. Vzhledem <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> k tomu, že vlastnost je nastavena na `true`, obdélník se otáčí podél tečny cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Kompletní ukázku naleznete v tématu [Cesta animace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Verze kódu předchozí ukázky slouží <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.EllipseGeometry>, i když byla použita pouze jedna animace. Jednodušší způsob, jak použít jednu animaci na <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> vlastnost v kódu je použít metodu. Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
- [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
