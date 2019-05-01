---
title: 'Postupy: Ověřování pozice pomocí kontejneru hostitele Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: ac5cae5bcd94dc8bf80ff95b8971914e1fa5ba2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025103"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="233ed-102">Postupy: Ověřování pozice pomocí kontejneru hostitele Win32</span><span class="sxs-lookup"><span data-stu-id="233ed-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="233ed-103">Můžete vytvořit vizuální objekty v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno tím, že hostitel poskytuje okno kontejneru pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="233ed-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="233ed-104">Kvůli omezením vizuální objekty zpracování událostí zpracování zpráv předávaných do smyčky filtru zprávy okna kontejneru hostitele.</span><span class="sxs-lookup"><span data-stu-id="233ed-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="233ed-105">Odkazovat na [kurzu: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) Další informace o tom, k hostování vizuální objektů v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="233ed-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="233ed-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="233ed-106">Example</span></span>  
 <span data-ttu-id="233ed-107">Následující kód ukazuje, jak nastavit myš obslužné rutiny událostí pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které slouží jako kontejner hostitele pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="233ed-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="233ed-108">Následující příklad ukazuje, jak nastavit pozice v reakci na soutisku události konkrétní myši.</span><span class="sxs-lookup"><span data-stu-id="233ed-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="233ed-109"><xref:System.Windows.Interop.HwndSource> Objekt představuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsah [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="233ed-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="233ed-110">Hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objekt představuje nejvyšší uzel v hierarchii vizuálního stromu.</span><span class="sxs-lookup"><span data-stu-id="233ed-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="233ed-111">Úplnou ukázku na přístupů testování objektů pomocí kontejneru hostitele Win32, najdete v části [spuštění testu s ukázkou vzájemná spolupráce grafického subsystému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="233ed-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233ed-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="233ed-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="233ed-113">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="233ed-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="233ed-114">Kurz: Hostování vizuální objektů v aplikaci Win32</span><span class="sxs-lookup"><span data-stu-id="233ed-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
