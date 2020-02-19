---
title: 'Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453101"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="d3f4b-102">Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)</span><span class="sxs-lookup"><span data-stu-id="d3f4b-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="d3f4b-103">Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animaci objektu podél cesty a k tomu, aby animace nashromáždila hodnoty posunutí při opakování.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f4b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3f4b-104">Example</span></span>  
 <span data-ttu-id="d3f4b-105">Následující příklad používá objekt <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animování vlastnosti <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform> použité pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="d3f4b-106">V důsledku toho se tlačítko přesune podél zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="d3f4b-107">Kromě toho příklad nastavuje vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> na `true`, což způsobí, že posun animované matice se nashromáždí jako opakování animace.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="d3f4b-108">Vzhledem k tomu, že posunování se sestavuje, tlačítko se při opakování animace místo resetování na počáteční pozici přesune přes obrazovku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="d3f4b-109">Všimněte si, že i když vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> způsobí, že hodnoty posunutí budou v průběhu opakování shromažďovány, nezpůsobí nahromadění hodnot rotace.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="d3f4b-110">Chcete-li nashromáždit hodnoty rotace, nastavte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> animace a vlastnosti <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d3f4b-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="d3f4b-111">Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="d3f4b-111">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="d3f4b-112">Příklad ukazující postup animace <xref:System.Windows.Media.Matrix> hodnoty podél cesty bez akumulace posunu naleznete v tématu [animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="d3f4b-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f4b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3f4b-113">See also</span></span>

- [<span data-ttu-id="d3f4b-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="d3f4b-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d3f4b-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="d3f4b-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
