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
ms.openlocfilehash: bb175e0f8aeb126b7f7fa85d5af1c4afcf5bea61
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482016"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="c6776-102">Postupy: Spuštění testu použitím kontejneru hostitele Win32</span><span class="sxs-lookup"><span data-stu-id="c6776-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="c6776-103">Můžete vytvořit vizuální objekty v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno tím, že hostitel poskytuje okno kontejneru pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="c6776-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="c6776-104">Kvůli omezením vizuální objekty zpracování událostí zpracování zpráv předávaných do smyčky filtru zprávy okna kontejneru hostitele.</span><span class="sxs-lookup"><span data-stu-id="c6776-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="c6776-105">Odkazovat na [kurz: hostování vizuální objektů v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) Další informace o tom, k hostování vizuální objektů v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="c6776-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6776-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6776-106">Example</span></span>  
 <span data-ttu-id="c6776-107">Následující kód ukazuje, jak nastavit myš obslužné rutiny událostí pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které slouží jako kontejner hostitele pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="c6776-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="c6776-108">Následující příklad ukazuje, jak nastavit pozice v reakci na soutisku události konkrétní myši.</span><span class="sxs-lookup"><span data-stu-id="c6776-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="c6776-109"><xref:System.Windows.Interop.HwndSource> Objekt představuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsah [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="c6776-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="c6776-110">Hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objekt představuje nejvyšší uzel v hierarchii vizuálního stromu.</span><span class="sxs-lookup"><span data-stu-id="c6776-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="c6776-111">Úplnou ukázku na přístupů testování objektů pomocí kontejneru hostitele Win32, najdete v části [spuštění testu s ukázkou vzájemná spolupráce grafického subsystému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="c6776-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6776-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6776-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="c6776-113">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="c6776-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="c6776-114">Kurz: Hostování vizuální objektů v aplikaci Win32</span><span class="sxs-lookup"><span data-stu-id="c6776-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
