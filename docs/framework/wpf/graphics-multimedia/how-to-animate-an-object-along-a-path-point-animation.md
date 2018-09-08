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
ms.openlocfilehash: d6dc79cd7a15aef2a4168fffb293c5e1f33cde08
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197112"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="a3cfc-102">Postupy: Animace objektu podél cesty (bodová animace)</span><span class="sxs-lookup"><span data-stu-id="a3cfc-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="a3cfc-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci objektu <xref:System.Windows.Point> podél zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3cfc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3cfc-104">Example</span></span>  
 <span data-ttu-id="a3cfc-105">Následujícím příkladu se přesune <xref:System.Windows.Media.EllipseGeometry> cestě určené <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a3cfc-106">Geometrie Elipsa <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost, která přijímá <xref:System.Windows.Point> hodnoty, určuje pozici; přesunout geometrie tři tečky, je animovat jeho <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="a3cfc-107">V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci <xref:System.Windows.Media.EllipseGeometry> objektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="a3cfc-108">Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="a3cfc-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="a3cfc-109">Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, přestože byl nastaven pouze jedné animace.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="a3cfc-110">A <xref:System.Windows.Media.Animation.Storyboard> často je nejjednodušší způsob, jak použít více animace, protože tyto animace budete mohou být řízena stejné <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a3cfc-111">Snadný způsob, jak použít jeden animace do vlastnosti při použití kódu je však použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a3cfc-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="a3cfc-112">Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="a3cfc-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cfc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3cfc-113">See Also</span></span>  
 [<span data-ttu-id="a3cfc-114">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="a3cfc-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="a3cfc-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a3cfc-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a3cfc-116">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="a3cfc-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
