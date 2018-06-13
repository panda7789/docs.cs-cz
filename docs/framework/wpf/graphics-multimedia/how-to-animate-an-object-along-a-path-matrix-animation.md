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
ms.openlocfilehash: 03e1e40f8ee6840558ad7b712d96e63d9e2bf15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559000"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="9fe3e-102">Postupy: Animace objektu podél cesty (animace matice)</span><span class="sxs-lookup"><span data-stu-id="9fe3e-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="9fe3e-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třídy animace objekt společně na cestu, která je definována <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9fe3e-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fe3e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fe3e-104">Example</span></span>  
 <span data-ttu-id="9fe3e-105">Následující příklad animuje objekt podél cesty následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9fe3e-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="9fe3e-106">Se vztahuje <xref:System.Windows.Media.MatrixTransform> k objektu, aby bylo možné přesunout ho.</span><span class="sxs-lookup"><span data-stu-id="9fe3e-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="9fe3e-107">Definuje cestu pomocí <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9fe3e-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="9fe3e-108">Vytvoří <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a pomocí něj použije animaci <xref:System.Windows.Media.Matrix> vlastnost <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="9fe3e-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="9fe3e-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Trvá <xref:System.Windows.Media.PathGeometry> a používá ke generování <xref:System.Windows.Media.Matrix> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9fe3e-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="9fe3e-110">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="9fe3e-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="9fe3e-111">Další informace o geometrickou cesty, najdete v článku [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9fe3e-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe3e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fe3e-112">See Also</span></span>  
 [<span data-ttu-id="9fe3e-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="9fe3e-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9fe3e-114">Ukázka animace cesta</span><span class="sxs-lookup"><span data-stu-id="9fe3e-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="9fe3e-115">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="9fe3e-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
