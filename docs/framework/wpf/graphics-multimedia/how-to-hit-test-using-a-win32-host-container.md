---
title: 'Postupy: Spuštění testu použitím kontejneru hostitele Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452802"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="cc9c6-102">Postupy: Spuštění testu použitím kontejneru hostitele Win32</span><span class="sxs-lookup"><span data-stu-id="cc9c6-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="cc9c6-103">Můžete vytvořit vizuální objekty v okně Win32 tím, že poskytnete kontejner hostitelského okna pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="cc9c6-104">Chcete-li zajistit zpracování událostí pro obsažené vizuální objekty, které zpracovávají zprávy předané do smyčky filtru zpráv kontejneru hostitelského okna.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="cc9c6-105">Další informace o tom, jak hostovat vizuální objekty v okně Win32, najdete [v tématu Kurz: hostování vizuálních objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) .</span><span class="sxs-lookup"><span data-stu-id="cc9c6-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc9c6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc9c6-106">Example</span></span>  
 <span data-ttu-id="cc9c6-107">Následující kód ukazuje, jak nastavit obslužné rutiny událostí myši pro okno Win32, které se používá jako kontejner hostitele pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="cc9c6-108">Následující příklad ukazuje, jak nastavit test přístupů v reakci na přesahy konkrétních událostí myši.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="cc9c6-109">Objekt <xref:System.Windows.Interop.HwndSource> prezentuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu v rámci okna Win32.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="cc9c6-110">Hodnota vlastnosti <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource> představuje uzel nejvyšší úrovně v hierarchii vizuálního stromu.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="cc9c6-111">Kompletní ukázku pro testování objektů pomocí kontejneru hostitele Win32 naleznete v tématu [test volání s ukázkovou meziprovozu](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)Win32.</span><span class="sxs-lookup"><span data-stu-id="cc9c6-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9c6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc9c6-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="cc9c6-113">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="cc9c6-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="cc9c6-114">Kurz: Hostování vizuální objektů v aplikaci Win32</span><span class="sxs-lookup"><span data-stu-id="cc9c6-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
