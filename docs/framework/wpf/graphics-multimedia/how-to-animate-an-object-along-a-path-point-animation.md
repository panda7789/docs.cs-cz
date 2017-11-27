---
title: "Postupy: Animace objektu podél cesty (bodová animace)"
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
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47cafab505bcbab7008385393bbacf093e264cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Postupy: Animace objektu podél cesty (bodová animace)
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.PointAnimationUsingPath> objekt, který má animace <xref:System.Windows.Point> podél zakřivené cesty.  
  
## <a name="example"></a>Příklad  
 Následujícím příkladu se přesune <xref:System.Windows.Media.EllipseGeometry> podél cesty definované <xref:System.Windows.Media.PathGeometry>. Elipsy geometrie <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost, která přebírá <xref:System.Windows.Point> hodnotu, určuje pozici; přesunout elipsy geometry, můžete postupné animaci jeho <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost. V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci <xref:System.Windows.Media.EllipseGeometry> objektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, i když bylo použito pouze jeden animace. A <xref:System.Windows.Media.Animation.Storyboard> je často nejjednodušší způsob, jak použít více animací, protože tyto animace se dá nastavit podle stejné <xref:System.Windows.Media.Animation.Storyboard>. Snadný způsob, jak použít jeden animace do vlastnosti při použití kódu je však používat <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka animace cesta](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Postupy: témata cesta animace](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
