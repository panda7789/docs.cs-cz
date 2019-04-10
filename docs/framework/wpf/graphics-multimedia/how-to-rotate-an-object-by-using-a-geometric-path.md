---
title: 'Postupy: Otočení objektu pomocí geometrické cesty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 3e35169da7297ec62e0114ab21f4ba81c0a656ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229209"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="8b875-102">Postupy: Otočení objektu pomocí geometrické cesty</span><span class="sxs-lookup"><span data-stu-id="8b875-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="8b875-103">Tento příklad ukazuje, jak otočit (pivot) objektu podél geometrické cesty, který je definován <xref:System.Windows.Media.PathGeometry> objektu.</span><span class="sxs-lookup"><span data-stu-id="8b875-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b875-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b875-104">Example</span></span>  
 <span data-ttu-id="8b875-105">Následující příklad používá tři <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty přesunout obdélník podél geometrické cesty.</span><span class="sxs-lookup"><span data-stu-id="8b875-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="8b875-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> , která je použita na obdélníku.</span><span class="sxs-lookup"><span data-stu-id="8b875-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8b875-107">Animace generuje úhel hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8b875-107">The animation generates angle values.</span></span> <span data-ttu-id="8b875-108">Díky obdélník otočit (pivot) podél obrysy cesty.</span><span class="sxs-lookup"><span data-stu-id="8b875-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="8b875-109">Tyto dva objekty animace <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> hodnoty <xref:System.Windows.Media.TranslateTransform> , která je použita na obdélníku.</span><span class="sxs-lookup"><span data-stu-id="8b875-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8b875-110">Využívají obdélník přesunout vodorovně a svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="8b875-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="8b875-111">Dalším způsobem, jak otočení objektu použitím geometrické cesty je použít <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu a nastavte jeho <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="8b875-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="8b875-112">Další informace a příklad najdete v tématu [otočení objektu použitím geometrické cesty (animace matice)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="8b875-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="8b875-113">Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="8b875-113">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b875-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b875-114">See also</span></span>

- [<span data-ttu-id="8b875-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="8b875-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="8b875-116">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="8b875-116">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="8b875-117">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="8b875-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
