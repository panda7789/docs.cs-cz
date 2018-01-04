---
title: "Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)"
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
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5259e930060a8ac6118d232f08d02193a6a1b300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="6c887-102">Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)</span><span class="sxs-lookup"><span data-stu-id="6c887-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="6c887-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třída animace objekt podél cesty a že animace hromadit její posun hodnoty jako opakuje.</span><span class="sxs-lookup"><span data-stu-id="6c887-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c887-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c887-104">Example</span></span>  
 <span data-ttu-id="6c887-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt, který má animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> použít tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6c887-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="6c887-106">V důsledku toho tlačítko přesune podél zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="6c887-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="6c887-107">Kromě toho v příkladu je nastaven <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnost `true`, což způsobí, že posun animovaný matici nashromáždí během animace se opakuje.</span><span class="sxs-lookup"><span data-stu-id="6c887-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="6c887-108">Protože posun shromažďuje, přesune tlačítko dále napříč obrazovky při animace se opakuje, nikoli resetovat na výchozí pozici.</span><span class="sxs-lookup"><span data-stu-id="6c887-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="6c887-109">Všimněte si, že, i když <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnost způsobí, že hodnoty posunutí hromadit přes opakování, nezpůsobuje otočení hodnoty pro shromažďování.</span><span class="sxs-lookup"><span data-stu-id="6c887-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="6c887-110">Chcete-li hodnoty otočení hromadit, nastavení animace <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> vlastnosti, které chcete `true`.</span><span class="sxs-lookup"><span data-stu-id="6c887-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="6c887-111">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="6c887-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="6c887-112">Příklad znázorňující animace <xref:System.Windows.Media.Matrix> hodnoty podél cesty bez posunutí akumulace najdete v tématu [animace cesta k objektu společně (matice animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="6c887-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c887-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c887-113">See Also</span></span>  
 [<span data-ttu-id="6c887-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="6c887-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="6c887-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="6c887-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
