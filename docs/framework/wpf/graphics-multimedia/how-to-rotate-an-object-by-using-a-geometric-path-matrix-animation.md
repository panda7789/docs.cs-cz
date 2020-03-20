---
title: 'Postupy: Otočení objektu použitím geometrické cesty (animace matice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187415"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="4e5dc-102">Postupy: Otočení objektu použitím geometrické cesty (animace matice)</span><span class="sxs-lookup"><span data-stu-id="4e5dc-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="4e5dc-103">Tento příklad ukazuje, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> jak <xref:System.Windows.Media.MatrixTransform> použít a a otočit (otočit) objekt <xref:System.Windows.Media.PathGeometry> podél geometrické cesty definované objektem.</span><span class="sxs-lookup"><span data-stu-id="4e5dc-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e5dc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e5dc-104">Example</span></span>  
 <span data-ttu-id="4e5dc-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci <xref:System.Windows.Media.MatrixTransform>vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="4e5dc-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="4e5dc-106">Použije <xref:System.Windows.Media.MatrixTransform> se na tlačítko a způsobí, že se pohybuje po zakřivené cestě.</span><span class="sxs-lookup"><span data-stu-id="4e5dc-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="4e5dc-107">Vzhledem <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> k tomu, že vlastnost je nastavena na `true`, obdélník se otáčí podél tečny cesty.</span><span class="sxs-lookup"><span data-stu-id="4e5dc-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="4e5dc-108">Kompletní ukázku naleznete v tématu [Cesta animace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="4e5dc-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="4e5dc-109">Verze kódu předchozí ukázky slouží <xref:System.Windows.Media.Animation.Storyboard> k animaci <xref:System.Windows.Media.EllipseGeometry>, i když byla použita pouze jedna animace.</span><span class="sxs-lookup"><span data-stu-id="4e5dc-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="4e5dc-110">Jednodušší způsob, jak použít jednu animaci na <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> vlastnost v kódu je použít metodu.</span><span class="sxs-lookup"><span data-stu-id="4e5dc-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="4e5dc-111">Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="4e5dc-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5dc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e5dc-112">See also</span></span>

- [<span data-ttu-id="4e5dc-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="4e5dc-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4e5dc-114">Postupy: Témata animace cesty</span><span class="sxs-lookup"><span data-stu-id="4e5dc-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="4e5dc-115">Ukázka animace cesty</span><span class="sxs-lookup"><span data-stu-id="4e5dc-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
