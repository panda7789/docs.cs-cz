---
title: 'Postupy: Otočení objektu použitím geometrické cesty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186879"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="c6597-102">Postupy: Otočení objektu použitím geometrické cesty</span><span class="sxs-lookup"><span data-stu-id="c6597-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="c6597-103">Tento příklad ukazuje, jak otočit (otočit) objekt podél geometrické cesty, která je definována objektem. <xref:System.Windows.Media.PathGeometry></span><span class="sxs-lookup"><span data-stu-id="c6597-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6597-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6597-104">Example</span></span>  
 <span data-ttu-id="c6597-105">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> tři objekty k přesunutí obdélníku podél geometrické cesty.</span><span class="sxs-lookup"><span data-stu-id="c6597-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="c6597-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje, <xref:System.Windows.Media.RotateTransform> který je použit na obdélník.</span><span class="sxs-lookup"><span data-stu-id="c6597-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="c6597-107">Animace generuje hodnoty úhlu.</span><span class="sxs-lookup"><span data-stu-id="c6597-107">The animation generates angle values.</span></span> <span data-ttu-id="c6597-108">To dělá obdélník otočit (pivot) podél obrysů cesty.</span><span class="sxs-lookup"><span data-stu-id="c6597-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="c6597-109">Ostatní dva objekty <xref:System.Windows.Media.TranslateTransform.X%2A> animovat <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> a hodnoty, které se aplikuje na obdélník.</span><span class="sxs-lookup"><span data-stu-id="c6597-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="c6597-110">Obdélník se pohybuje vodorovně a svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="c6597-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="c6597-111">Dalším způsobem, jak otočit objekt pomocí geometrické <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> cesty, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je `true`použít objekt a nastavit jeho vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="c6597-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="c6597-112">Další informace a příklad viz [Otočení objektu pomocí geometrické cesty (Animace matice).](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)</span><span class="sxs-lookup"><span data-stu-id="c6597-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="c6597-113">Kompletní ukázku naleznete v tématu [Cesta animace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="c6597-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6597-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6597-114">See also</span></span>

- [<span data-ttu-id="c6597-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="c6597-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c6597-116">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="c6597-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="c6597-117">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="c6597-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
