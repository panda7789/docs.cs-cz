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
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452854"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="e788c-102">Postupy: Animace objektu podél cesty (dvojitá animace)</span><span class="sxs-lookup"><span data-stu-id="e788c-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="e788c-103">Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> k přesunutí objektu podél cesty definované <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e788c-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e788c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e788c-104">Example</span></span>  
 <span data-ttu-id="e788c-105">Následující příklad používá dva <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty pro přesunutí obdélníku podél geometrické cesty:</span><span class="sxs-lookup"><span data-stu-id="e788c-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="e788c-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> použité pro obdélník.</span><span class="sxs-lookup"><span data-stu-id="e788c-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="e788c-107">Tím se obdélník přesune vodorovně podél cesty.</span><span class="sxs-lookup"><span data-stu-id="e788c-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="e788c-108">Druhý <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> použité pro obdélník.</span><span class="sxs-lookup"><span data-stu-id="e788c-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="e788c-109">Tím se obdélník přesune svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="e788c-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="e788c-110">Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="e788c-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="e788c-111">Jiný způsob, jak přesunout objekt pomocí geometrické cesty, je použít objekt <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>.</span><span class="sxs-lookup"><span data-stu-id="e788c-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="e788c-112">Příklad naleznete v tématu [animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="e788c-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e788c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e788c-113">See also</span></span>

- [<span data-ttu-id="e788c-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="e788c-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e788c-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="e788c-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
