---
title: 'Postupy: Animace umístění objektu použitím PointAnimation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 91447685988d91dfe86707c2cf265deabeb717b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036662"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Postupy: Animace umístění objektu použitím PointAnimation
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimation> třídy animace objektu podél <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se přesune Elipsa <xref:System.Windows.Shapes.Path> z jednoho místa na jiné obrazovce. V příkladu animuje pozici <xref:System.Windows.Media.EllipseGeometry> pomocí <xref:System.Windows.Media.Animation.PointAnimation> pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [Animace a časování](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
