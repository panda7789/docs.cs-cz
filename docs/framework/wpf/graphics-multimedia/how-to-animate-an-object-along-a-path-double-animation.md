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
ms.openlocfilehash: 3dcdf6cfe8631ae0b7b1472e22d027cf9288a1db
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386219"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="48989-102">Postupy: Animace objektu podél cesty (dvojitá animace)</span><span class="sxs-lookup"><span data-stu-id="48989-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="48989-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> třídy přesunutí objektu podél cesty určené <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="48989-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48989-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="48989-104">Example</span></span>  
 <span data-ttu-id="48989-105">Následující příklad používá dva <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty přesunout obdélník podél geometrické cesty:</span><span class="sxs-lookup"><span data-stu-id="48989-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="48989-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> z <xref:System.Windows.Media.TranslateTransform> u obdélníku.</span><span class="sxs-lookup"><span data-stu-id="48989-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="48989-107">Díky obdélník přesunout vodorovně na cestě.</span><span class="sxs-lookup"><span data-stu-id="48989-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="48989-108">Druhá <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> z <xref:System.Windows.Media.TranslateTransform> u obdélníku.</span><span class="sxs-lookup"><span data-stu-id="48989-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="48989-109">Díky obdélník přesunout svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="48989-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="48989-110">Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="48989-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="48989-111">Jiný způsob, jak přesunout objektu pomocí geometrické cesty je použít <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu.</span><span class="sxs-lookup"><span data-stu-id="48989-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="48989-112">Příklad najdete v tématu [animace objektu podél cesty (animace matice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="48989-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48989-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="48989-113">See Also</span></span>  
 [<span data-ttu-id="48989-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="48989-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="48989-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="48989-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
