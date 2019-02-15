---
title: 'Postupy: Animace obdélníku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: dbff015bdc5f9ce56d2c366e0d348429efb7f4b5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305152"
---
# <a name="how-to-animate-a-rectangle"></a>Postupy: Animace obdélníku
Tento příklad ukazuje, jak animace změn velikosti a pozici obdélníku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá instanci <xref:System.Windows.Media.Animation.RectAnimation> třídy pro animaci <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>, která animuje změny velikosti a pozici obdélníku.  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Postupy: témata grafiky](graphics-how-to-topics.md)
- [Animace a časování témata s postupy](animation-and-timing-how-to-topics.md)
