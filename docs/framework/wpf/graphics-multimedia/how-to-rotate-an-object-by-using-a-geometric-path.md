---
title: "Postupy: Otočení objektu použitím geometrické cesty"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e4963d174f889ac51087356b042bc5b06990593
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="95e1f-102">Postupy: Otočení objektu použitím geometrické cesty</span><span class="sxs-lookup"><span data-stu-id="95e1f-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="95e1f-103">Tento příklad ukazuje, jak otočit (pivot) objekt podél geometrickou cestu, která je definována <xref:System.Windows.Media.PathGeometry> objektu.</span><span class="sxs-lookup"><span data-stu-id="95e1f-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95e1f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="95e1f-104">Example</span></span>  
 <span data-ttu-id="95e1f-105">Následující příklad používá tři <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objekty, které chcete přesunout obdélníku podél geometrickou cesty.</span><span class="sxs-lookup"><span data-stu-id="95e1f-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="95e1f-106">První <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> který se použije pro rámeček.</span><span class="sxs-lookup"><span data-stu-id="95e1f-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="95e1f-107">Animace vygeneruje hodnoty úhel.</span><span class="sxs-lookup"><span data-stu-id="95e1f-107">The animation generates angle values.</span></span> <span data-ttu-id="95e1f-108">Umožňuje rámeček otočit (pivot) podél obrysy cesty.</span><span class="sxs-lookup"><span data-stu-id="95e1f-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="95e1f-109">Tyto dva objekty animace <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> hodnoty <xref:System.Windows.Media.TranslateTransform> který se použije pro rámeček.</span><span class="sxs-lookup"><span data-stu-id="95e1f-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="95e1f-110">Provádění rámeček přesunout vodorovně a svisle podél cesty.</span><span class="sxs-lookup"><span data-stu-id="95e1f-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="95e1f-111">Jiný způsob, jak otočení objektu pomocí cesty geometrickou je použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu a nastavit jeho <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="95e1f-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="95e1f-112">Další informace a příklady naleznete v tématu [otočení objektu pomocí cesty geometrickou (matice animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="95e1f-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="95e1f-113">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="95e1f-113">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e1f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="95e1f-114">See Also</span></span>  
 [<span data-ttu-id="95e1f-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="95e1f-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="95e1f-116">Ukázka animace cesta</span><span class="sxs-lookup"><span data-stu-id="95e1f-116">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="95e1f-117">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="95e1f-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
