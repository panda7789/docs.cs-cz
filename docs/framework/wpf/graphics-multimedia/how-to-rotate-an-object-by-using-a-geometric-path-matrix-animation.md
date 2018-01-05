---
title: "Postupy: Otočení objektu použitím geometrické cesty (animace matice)"
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
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c001c0969e42c1eaadad6c029ae86009176b9eb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="25b72-102">Postupy: Otočení objektu použitím geometrické cesty (animace matice)</span><span class="sxs-lookup"><span data-stu-id="25b72-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="25b72-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> a <xref:System.Windows.Media.MatrixTransform> otočení (pivot) objekt podél geometrickou cesty definované <xref:System.Windows.Media.PathGeometry> objektu.</span><span class="sxs-lookup"><span data-stu-id="25b72-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25b72-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="25b72-104">Example</span></span>  
 <span data-ttu-id="25b72-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt, který má animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="25b72-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="25b72-106"><xref:System.Windows.Media.MatrixTransform> Se použije pro tlačítko a způsobí, že ho přesunout společně zakřivené cesty.</span><span class="sxs-lookup"><span data-stu-id="25b72-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="25b72-107">Protože <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je nastavena na `true`, rámeček otáčí společně tangens cestu.</span><span class="sxs-lookup"><span data-stu-id="25b72-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="25b72-108">Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="25b72-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="25b72-109">Verze kódu v předchozím příkladu používá <xref:System.Windows.Media.Animation.Storyboard> pro animaci <xref:System.Windows.Media.EllipseGeometry>, i když bylo použito pouze jeden animace.</span><span class="sxs-lookup"><span data-stu-id="25b72-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="25b72-110">Snadný způsob, jak použít jeden animace do vlastnosti v kódu se má používat <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="25b72-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="25b72-111">Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="25b72-111">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b72-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="25b72-112">See Also</span></span>  
 [<span data-ttu-id="25b72-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="25b72-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="25b72-114">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="25b72-114">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [<span data-ttu-id="25b72-115">Ukázka animace cesta</span><span class="sxs-lookup"><span data-stu-id="25b72-115">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)
