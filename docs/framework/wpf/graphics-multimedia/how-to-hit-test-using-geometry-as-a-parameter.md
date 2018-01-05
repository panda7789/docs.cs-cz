---
title: "Postupy: Spuštění testu použitím geometrie jako parametru"
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
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b5c5bb47e3f435419bcf3c472f052260adec7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="bdf06-102">Postupy: Spuštění testu použitím geometrie jako parametru</span><span class="sxs-lookup"><span data-stu-id="bdf06-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="bdf06-103">Tento příklad ukazuje, jak chcete provést test přístupů na visual objekt pomocí <xref:System.Windows.Media.Geometry> jako stiskněte klávesu testovací parametr.</span><span class="sxs-lookup"><span data-stu-id="bdf06-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdf06-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdf06-104">Example</span></span>  
 <span data-ttu-id="bdf06-105">Následující příklad ukazuje, jak nastavit přístupů testu pomocí <xref:System.Windows.Media.GeometryHitTestParameters> pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="bdf06-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="bdf06-106"><xref:System.Windows.Point> Hodnotu, která je předána `OnMouseDown` metoda se používá k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah přístupů testu.</span><span class="sxs-lookup"><span data-stu-id="bdf06-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="bdf06-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Vlastnost <xref:System.Windows.Media.GeometryHitTestResult> poskytuje informace o výsledky testu přístupů, které používá <xref:System.Windows.Media.Geometry> jako stiskněte klávesu testovací parametr.</span><span class="sxs-lookup"><span data-stu-id="bdf06-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="bdf06-108">Následující obrázek znázorňuje vztah mezi geometry ověření pozice (modré kruhu) a vykreslené obsah cílového objektu visual (červený čtvereček).</span><span class="sxs-lookup"><span data-stu-id="bdf06-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="bdf06-109">![Testování průchodu diagram IntersectionDetail použít v](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="bdf06-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="bdf06-110">Průnik mezi přístupů geometrie a cíle visual objekt testu</span><span class="sxs-lookup"><span data-stu-id="bdf06-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="bdf06-111">Následující příklad ukazuje, jak implementovat přístupů test zpětné volání při <xref:System.Windows.Media.Geometry> slouží jako parametr přístupů testu.</span><span class="sxs-lookup"><span data-stu-id="bdf06-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="bdf06-112">`result` Parametr přetypovat <xref:System.Windows.Media.GeometryHitTestResult> Chcete-li načíst hodnotu <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bdf06-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="bdf06-113">Hodnota vlastnosti umožňuje zjistit, jestli <xref:System.Windows.Media.Geometry> přístupů testovací parametr je úplně nebo částečně obsažené v vykreslené obsah cílového počtu testu.</span><span class="sxs-lookup"><span data-stu-id="bdf06-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="bdf06-114">V takovém případě ukázkový kód je jenom přidávání výsledky ověření pozice v seznamu vizuální prvky, které jsou zcela zahrnutá v rámci hranice cíl.</span><span class="sxs-lookup"><span data-stu-id="bdf06-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="bdf06-115"><xref:System.Windows.Media.HitTestResult> Zpětného volání by neměl být volán při průniku podrobností <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="bdf06-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf06-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdf06-116">See Also</span></span>  
 [<span data-ttu-id="bdf06-117">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="bdf06-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="bdf06-118">Ověření pozice objektu Geometry ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="bdf06-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
