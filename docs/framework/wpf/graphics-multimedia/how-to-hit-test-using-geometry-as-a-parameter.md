---
title: 'Postupy: Spuštění testu použitím geometrie jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 3d6f4190a5b5c8410a6be01d2645df9c123f9ac4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410612"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="80245-102">Postupy: Spuštění testu použitím geometrie jako parametru</span><span class="sxs-lookup"><span data-stu-id="80245-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="80245-103">Tento příklad ukazuje, jak provádět ověření pozice ve vizuální objekty pomocí <xref:System.Windows.Media.Geometry> jako nalezený testování parametru.</span><span class="sxs-lookup"><span data-stu-id="80245-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80245-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="80245-104">Example</span></span>  
 <span data-ttu-id="80245-105">Následující příklad ukazuje, jak nastavit ověření pozice pomocí <xref:System.Windows.Media.GeometryHitTestParameters> pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="80245-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="80245-106"><xref:System.Windows.Point> Hodnotu, která je předána `OnMouseDown` metoda se používá k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah průchodů testů.</span><span class="sxs-lookup"><span data-stu-id="80245-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="80245-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Vlastnost <xref:System.Windows.Media.GeometryHitTestResult> poskytuje informace o výsledcích přístupů test, který se používá <xref:System.Windows.Media.Geometry> jako nalezený testování parametru.</span><span class="sxs-lookup"><span data-stu-id="80245-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="80245-108">Následující ilustrace znázorňuje vztah mezi geometrie ověření pozice (modré circle) a vykreslený obsah visual cílový objekt (červený čtvereček).</span><span class="sxs-lookup"><span data-stu-id="80245-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 ![Diagram zobrazující průběh IntersectionDetail použitou v testování průchodu.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 <span data-ttu-id="80245-110">Následující příklad ukazuje, jak provádět ověření pozice zpětné volání při <xref:System.Windows.Media.Geometry> slouží jako parametr ověření pozice.</span><span class="sxs-lookup"><span data-stu-id="80245-110">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="80245-111">`result` Parametr přetypováno na <xref:System.Windows.Media.GeometryHitTestResult> k načtení hodnoty <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80245-111">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="80245-112">Hodnota vlastnosti umožňuje určit, jestli <xref:System.Windows.Media.Geometry> ověření pozice parametru je částečně nebo zcela obsažena v vykreslený obsah cíl ověření pozice.</span><span class="sxs-lookup"><span data-stu-id="80245-112">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="80245-113">V takovém případě ukázkový kód je pouze přidáním výsledky ověření pozice do seznamu pro vizuály, které jsou plně obsaženy v rámci hranic cíl.</span><span class="sxs-lookup"><span data-stu-id="80245-113">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="80245-114"><xref:System.Windows.Media.HitTestResult> Zpětného volání by neměla být volána po průniku podrobností <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="80245-114">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80245-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80245-115">See also</span></span>
- [<span data-ttu-id="80245-116">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="80245-116">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="80245-117">Ověření pozice objektu Geometry ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="80245-117">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
