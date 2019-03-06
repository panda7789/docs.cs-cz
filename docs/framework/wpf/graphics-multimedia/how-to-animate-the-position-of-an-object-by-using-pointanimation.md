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
ms.openlocfilehash: 04dbcfdb64525e6231ecf33c8ac5ecf2a2d2cb7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357924"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="4b15e-102">Postupy: Animace umístění objektu použitím PointAnimation</span><span class="sxs-lookup"><span data-stu-id="4b15e-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="4b15e-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimation> třídy animace objektu podél <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="4b15e-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b15e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b15e-104">Example</span></span>  
 <span data-ttu-id="4b15e-105">V následujícím příkladu se přesune Elipsa <xref:System.Windows.Shapes.Path> z jednoho místa na jiné obrazovce.</span><span class="sxs-lookup"><span data-stu-id="4b15e-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="4b15e-106">V příkladu animuje pozici <xref:System.Windows.Media.EllipseGeometry> pomocí <xref:System.Windows.Media.Animation.PointAnimation> pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b15e-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4b15e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b15e-107">See also</span></span>
- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [<span data-ttu-id="4b15e-108">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="4b15e-108">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4b15e-109">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="4b15e-109">Graphics and Multimedia</span></span>](index.md)
- [<span data-ttu-id="4b15e-110">Postupy: témata grafiky</span><span class="sxs-lookup"><span data-stu-id="4b15e-110">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="4b15e-111">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="4b15e-111">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
