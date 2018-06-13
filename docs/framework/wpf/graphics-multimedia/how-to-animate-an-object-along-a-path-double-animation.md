---
title: 'Postupy: Animace objektu podél cesty (dvojitá animace)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: ebe24f060a342633a93b778d5e8030173970029c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559902"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="75a64-102">Postupy: Animace objektu podél cesty (dvojitá animace)</span><span class="sxs-lookup"><span data-stu-id="75a64-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="75a64-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> třída přesunout objekt podél cesty definované <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="75a64-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a64-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="75a64-104">Example</span></span>  
 <span data-ttu-id="75a64-105">Následující příklad používá dva <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty, které chcete přesunout obdélníku podél geometrickou cesty:</span><span class="sxs-lookup"><span data-stu-id="75a64-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="75a64-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> z <xref:System.Windows.Media.TranslateTransform> u rámeček.</span><span class="sxs-lookup"><span data-stu-id="75a64-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="75a64-107">Umožňuje rámeček přesunout vodorovně v cestě.</span><span class="sxs-lookup"><span data-stu-id="75a64-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="75a64-108">Druhý <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> z <xref:System.Windows.Media.TranslateTransform> u rámeček.</span><span class="sxs-lookup"><span data-stu-id="75a64-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="75a64-109">Umožňuje rámeček přesunout svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="75a64-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="75a64-110">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="75a64-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="75a64-111">Jiný způsob, jak přesunout objekt, který používá geometrickou cesty se má používat <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu.</span><span class="sxs-lookup"><span data-stu-id="75a64-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="75a64-112">Příklad, naleznete v části [animace cesta k objektu společně (matice animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="75a64-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a64-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="75a64-113">See Also</span></span>  
 [<span data-ttu-id="75a64-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="75a64-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="75a64-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="75a64-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
