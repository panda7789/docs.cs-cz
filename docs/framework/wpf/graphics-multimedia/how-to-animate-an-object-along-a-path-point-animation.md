---
title: 'Postupy: Animace objektu podél cesty (bodová animace)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452893"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="b08e0-102">Postupy: Animace objektu podél cesty (bodová animace)</span><span class="sxs-lookup"><span data-stu-id="b08e0-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="b08e0-103">Tento příklad ukazuje, jak použít objekt <xref:System.Windows.Media.Animation.PointAnimationUsingPath> k animaci <xref:System.Windows.Point> podél zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="b08e0-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b08e0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b08e0-104">Example</span></span>  
 <span data-ttu-id="b08e0-105">Následující příklad přesune <xref:System.Windows.Media.EllipseGeometry> podél cesty definované <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="b08e0-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="b08e0-106">Vlastnost <xref:System.Windows.Media.EllipseGeometry.Center%2A> geometrie pro tři tečky, která přebírá hodnotu <xref:System.Windows.Point>, určuje její polohu; Chcete-li přesunout geometrii elipsy, animaci jeho vlastnosti <xref:System.Windows.Media.EllipseGeometry.Center%2A>.</span><span class="sxs-lookup"><span data-stu-id="b08e0-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="b08e0-107">V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> k animaci vlastnosti <xref:System.Windows.Media.EllipseGeometry.Center%2A> objektu <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="b08e0-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="b08e0-108">Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="b08e0-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="b08e0-109">Verze kódu předchozí ukázky použila <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.EllipseGeometry>, i když byla použita pouze jedna animace.</span><span class="sxs-lookup"><span data-stu-id="b08e0-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="b08e0-110"><xref:System.Windows.Media.Animation.Storyboard> je často nejjednodušší způsob, jak použít více animací, protože tyto animace lze ovládat stejným <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="b08e0-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="b08e0-111">Nicméně jednodušší způsob, jak použít jedinou animaci na vlastnost při použití kódu, je použít metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>.</span><span class="sxs-lookup"><span data-stu-id="b08e0-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="b08e0-112">Příklad naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="b08e0-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08e0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b08e0-113">See also</span></span>

- [<span data-ttu-id="b08e0-114">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="b08e0-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="b08e0-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="b08e0-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b08e0-116">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="b08e0-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
