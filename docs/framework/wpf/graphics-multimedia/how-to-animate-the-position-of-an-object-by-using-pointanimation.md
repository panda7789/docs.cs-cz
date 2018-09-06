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
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="e01dc-102">Postupy: Animace umístění objektu použitím PointAnimation</span><span class="sxs-lookup"><span data-stu-id="e01dc-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="e01dc-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimation> třídy animace objektu podél <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="e01dc-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e01dc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e01dc-104">Example</span></span>  
 <span data-ttu-id="e01dc-105">V následujícím příkladu se přesune Elipsa <xref:System.Windows.Shapes.Path> z jednoho místa na jiné obrazovce.</span><span class="sxs-lookup"><span data-stu-id="e01dc-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="e01dc-106">V příkladu animuje pozici <xref:System.Windows.Media.EllipseGeometry> pomocí <xref:System.Windows.Media.Animation.PointAnimation> pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e01dc-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e01dc-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="e01dc-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="e01dc-108">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="e01dc-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e01dc-109">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="e01dc-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="e01dc-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e01dc-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="e01dc-111">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="e01dc-111">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="e01dc-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e01dc-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
