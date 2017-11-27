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
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="e45c8-102">Postupy: Animace objektu podél cesty (bodová animace)</span><span class="sxs-lookup"><span data-stu-id="e45c8-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="e45c8-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.PointAnimationUsingPath> objekt, který má animace <xref:System.Windows.Point> podél zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="e45c8-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e45c8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e45c8-104">Example</span></span>  
 <span data-ttu-id="e45c8-105">Následujícím příkladu se přesune <xref:System.Windows.Media.EllipseGeometry> podél cesty definované <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e45c8-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e45c8-106">Elipsy geometrie <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost, která přebírá <xref:System.Windows.Point> hodnotu, určuje pozici; přesunout elipsy geometry, můžete postupné animaci jeho <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e45c8-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="e45c8-107">V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci <xref:System.Windows.Media.EllipseGeometry> objektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e45c8-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="e45c8-108">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="e45c8-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="e45c8-109">Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, i když bylo použito pouze jeden animace.</span><span class="sxs-lookup"><span data-stu-id="e45c8-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="e45c8-110">A <xref:System.Windows.Media.Animation.Storyboard> je často nejjednodušší způsob, jak použít více animací, protože tyto animace se dá nastavit podle stejné <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="e45c8-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="e45c8-111">Snadný způsob, jak použít jeden animace do vlastnosti při použití kódu je však používat <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e45c8-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="e45c8-112">Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="e45c8-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45c8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e45c8-113">See Also</span></span>  
 [<span data-ttu-id="e45c8-114">Ukázka animace cesta</span><span class="sxs-lookup"><span data-stu-id="e45c8-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="e45c8-115">Animace – přehled</span><span class="sxs-lookup"><span data-stu-id="e45c8-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e45c8-116">Postupy: témata cesta animace</span><span class="sxs-lookup"><span data-stu-id="e45c8-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
