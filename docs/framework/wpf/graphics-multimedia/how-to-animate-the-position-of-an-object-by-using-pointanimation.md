---
title: "Postupy: Animace umístění objektu použitím PointAnimation"
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
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6590c79ac6b6f104d9944a32da4c99318d334eec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Postupy: Animace umístění objektu použitím PointAnimation
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.PointAnimation> třídy animace objekt společně <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Příklad  
 Následujícím příkladu se přesune elipsy <xref:System.Windows.Shapes.Path> z jednoho místa na obrazovce do jiného. V příkladu animuje pozici <xref:System.Windows.Media.EllipseGeometry> pomocí <xref:System.Windows.Media.Animation.PointAnimation> pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [Animace a časování](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
