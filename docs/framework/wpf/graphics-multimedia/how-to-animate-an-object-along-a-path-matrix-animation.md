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
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452906"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="03051-102">Postupy: Animace objektu podél cesty (animace matice)</span><span class="sxs-lookup"><span data-stu-id="03051-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="03051-103">Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k animaci objektu podél cesty, která je definována <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="03051-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03051-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="03051-104">Example</span></span>  
 <span data-ttu-id="03051-105">Následující příklad animuje objekt podél cesty následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="03051-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="03051-106">Aplikuje <xref:System.Windows.Media.MatrixTransform> objektu, aby jej bylo možné přesunout.</span><span class="sxs-lookup"><span data-stu-id="03051-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="03051-107">Definuje cestu pomocí <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="03051-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="03051-108">Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a použije ho k animaci <xref:System.Windows.Media.Matrix> vlastnosti <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="03051-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="03051-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> přebírá <xref:System.Windows.Media.PathGeometry> a používá ho ke generování <xref:System.Windows.Media.Matrix>ch hodnot.</span><span class="sxs-lookup"><span data-stu-id="03051-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="03051-110">Úplnou ukázku najdete v tématu [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="03051-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="03051-111">Další informace o geometrických cestách najdete v [přehledu geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="03051-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03051-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="03051-112">See also</span></span>

- [<span data-ttu-id="03051-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="03051-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="03051-114">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="03051-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="03051-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="03051-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
