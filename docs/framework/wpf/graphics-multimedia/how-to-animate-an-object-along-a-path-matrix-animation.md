---
title: 'Postupy: Animace objektu podél cesty (animace matice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 836f61e062b921c7e51166a35d8169f903fcbab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738297"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="68fe2-102">Postupy: Animace objektu podél cesty (animace matice)</span><span class="sxs-lookup"><span data-stu-id="68fe2-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="68fe2-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třídy animace objektu podél cesty, který je definován <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="68fe2-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fe2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="68fe2-104">Example</span></span>  
 <span data-ttu-id="68fe2-105">Následující příklad animuje objektu podél cesty následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="68fe2-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="68fe2-106">Se vztahuje <xref:System.Windows.Media.MatrixTransform> na objekt, aby bylo možné přesunout.</span><span class="sxs-lookup"><span data-stu-id="68fe2-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="68fe2-107">Definuje cestu s využitím <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="68fe2-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="68fe2-108">Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a použije ho k animace <xref:System.Windows.Media.Matrix> vlastnost <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="68fe2-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="68fe2-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Přijímá <xref:System.Windows.Media.PathGeometry> a použije ho k vygenerování <xref:System.Windows.Media.Matrix> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="68fe2-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="68fe2-110">Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="68fe2-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="68fe2-111">Další informace o geometrické cesty, najdete v článku [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="68fe2-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fe2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68fe2-112">See also</span></span>
- [<span data-ttu-id="68fe2-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="68fe2-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="68fe2-114">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="68fe2-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="68fe2-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="68fe2-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
