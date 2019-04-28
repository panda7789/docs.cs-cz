---
title: 'Postupy: Animace umístění objektu pomocí PointAnimation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 1ef3f77e551affaa7e61d2aabf95f10c29275417
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651347"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Postupy: Animace umístění objektu pomocí PointAnimation
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimation> třídy animace objektu podél <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se přesune Elipsa <xref:System.Windows.Shapes.Path> z jednoho místa na jiné obrazovce. V příkladu animuje pozici <xref:System.Windows.Media.EllipseGeometry> pomocí <xref:System.Windows.Media.Animation.PointAnimation> pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [Přehled animace](animation-overview.md)
- [Grafika a multimédia](index.md)
- [Postupy: témata grafiky](graphics-how-to-topics.md)
- [Animace a časování témata s postupy](animation-and-timing-how-to-topics.md)
