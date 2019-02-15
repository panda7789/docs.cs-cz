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
# <a name="how-to-animate-a-rectangle"></a><span data-ttu-id="143a7-102">Postupy: Animace obdélníku</span><span class="sxs-lookup"><span data-stu-id="143a7-102">How to: Animate a Rectangle</span></span>
<span data-ttu-id="143a7-103">Tento příklad ukazuje, jak animace změn velikosti a pozici obdélníku.</span><span class="sxs-lookup"><span data-stu-id="143a7-103">This example shows how to animate changes to the size and position of a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="143a7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="143a7-104">Example</span></span>  
 <span data-ttu-id="143a7-105">Následující příklad používá instanci <xref:System.Windows.Media.Animation.RectAnimation> třídy pro animaci <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>, která animuje změny velikosti a pozici obdélníku.</span><span class="sxs-lookup"><span data-stu-id="143a7-105">The following example uses an instance of the <xref:System.Windows.Media.Animation.RectAnimation> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>, which animates changes to the size and position of the rectangle.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="143a7-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="143a7-106">See also</span></span>
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [<span data-ttu-id="143a7-107">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="143a7-107">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="143a7-108">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="143a7-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="143a7-109">Postupy: témata grafiky</span><span class="sxs-lookup"><span data-stu-id="143a7-109">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="143a7-110">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="143a7-110">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
