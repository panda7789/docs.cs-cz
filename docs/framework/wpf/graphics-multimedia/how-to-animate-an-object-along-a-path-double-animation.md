---
title: "Postupy: Animace objektu podél cesty (dvojitá animace)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a461b741675a18ac1e3544b17a9bbe9a8d18547
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Postupy: Animace objektu podél cesty (dvojitá animace)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> třída přesunout objekt podél cesty definované <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty, které chcete přesunout obdélníku podél geometrickou cesty:  
  
-   První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> z <xref:System.Windows.Media.TranslateTransform> u rámeček. Umožňuje rámeček přesunout vodorovně v cestě.  
  
-   Druhý <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> z <xref:System.Windows.Media.TranslateTransform> u rámeček. Umožňuje rámeček přesunout svisle podél cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Jiný způsob, jak přesunout objekt, který používá geometrickou cesty se má používat <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu. Příklad, naleznete v části [animace cesta k objektu společně (matice animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Viz také  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Postupy: témata cesta animace](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
