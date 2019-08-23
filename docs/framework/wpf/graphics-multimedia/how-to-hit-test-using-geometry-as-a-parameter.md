---
title: 'Postupy: Ověřování pozice pomocí objektu Geometry jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923409"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="4c905-102">Postupy: Ověřování pozice pomocí objektu Geometry jako parametru</span><span class="sxs-lookup"><span data-stu-id="4c905-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="4c905-103">Tento příklad ukazuje, jak provést test přístupů na vizuální objekt pomocí <xref:System.Windows.Media.Geometry> parametru jako parametr testu volání.</span><span class="sxs-lookup"><span data-stu-id="4c905-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c905-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c905-104">Example</span></span>  
 <span data-ttu-id="4c905-105">Následující příklad ukazuje, jak nastavit test přístupů pomocí <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c905-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="4c905-106">Hodnota, která je předána `OnMouseDown` metodě, slouží k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah testu přístupů. <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="4c905-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="4c905-107">Vlastnost poskytuje informace o výsledcích testu <xref:System.Windows.Media.Geometry> volání, který používá jako parametr testu volání. <xref:System.Windows.Media.GeometryHitTestResult> <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A></span><span class="sxs-lookup"><span data-stu-id="4c905-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="4c905-108">Následující ilustrace znázorňuje vztah mezi geometrií testu přístupů (modrý kroužek) a vykresleným obsahem cílového vizuálního objektu (červené čtverce).</span><span class="sxs-lookup"><span data-stu-id="4c905-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 ![Diagram, který zobrazuje IntersectionDetail používaný při testování přístupů.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 <span data-ttu-id="4c905-110">Následující příklad ukazuje, jak implementovat volání testu volání, když <xref:System.Windows.Media.Geometry> se používá jako parametr testu volání.</span><span class="sxs-lookup"><span data-stu-id="4c905-110">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="4c905-111">Parametr je přetypování <xref:System.Windows.Media.GeometryHitTestResult> na hodnotu, aby se <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> načetla hodnota vlastnosti. `result`</span><span class="sxs-lookup"><span data-stu-id="4c905-111">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="4c905-112">Hodnota vlastnosti umožňuje určit, zda <xref:System.Windows.Media.Geometry> je parametr testu volání plně nebo částečně obsažen v rámci vykresleného obsahu cíle testu volání.</span><span class="sxs-lookup"><span data-stu-id="4c905-112">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="4c905-113">V tomto případě vzorový kód přidává pouze výsledky testů přístupů do seznamu pro vizuály, které jsou plně obsaženy v cílové hranici.</span><span class="sxs-lookup"><span data-stu-id="4c905-113">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> <span data-ttu-id="4c905-114">Zpětné volání by nemělo být voláno, když je <xref:System.Windows.Media.IntersectionDetail.Empty>detail průniku. <xref:System.Windows.Media.HitTestResult></span><span class="sxs-lookup"><span data-stu-id="4c905-114">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c905-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c905-115">See also</span></span>

- [<span data-ttu-id="4c905-116">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="4c905-116">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="4c905-117">Ověření pozice objektu Geometry ve vizuálním objektu</span><span class="sxs-lookup"><span data-stu-id="4c905-117">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
