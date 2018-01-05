---
title: "Postupy: Otočení objektu použitím geometrické cesty (animace matice)"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c001c0969e42c1eaadad6c029ae86009176b9eb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Postupy: Otočení objektu použitím geometrické cesty (animace matice)
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a <xref:System.Windows.Media.MatrixTransform> otočení (pivot) objekt podél geometrickou cesty definované <xref:System.Windows.Media.PathGeometry> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt, který má animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Se použije pro tlačítko a způsobí, že ho přesunout společně zakřivené cesty. Protože <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je nastavena na `true`, rámeček otáčí společně tangens cestu.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, i když bylo použito pouze jeden animace. Snadný způsob, jak použít jeden animace do vlastnosti v kódu se má používat <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Postupy: Témata animace cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Ukázka animace cesta](http://go.microsoft.com/fwlink/?LinkID=160028)
