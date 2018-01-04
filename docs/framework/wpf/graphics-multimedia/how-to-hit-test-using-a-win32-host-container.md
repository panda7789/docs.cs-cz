---
title: "Postupy: Spuštění testu použitím kontejneru hostitele Win32"
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
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142c2faa01c32ac6602e80eaef18779f93154aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="24c3c-102">Postupy: Spuštění testu použitím kontejneru hostitele Win32</span><span class="sxs-lookup"><span data-stu-id="24c3c-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="24c3c-103">Můžete vytvořit vizuální objekty v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno tím, že hostitel poskytuje okno kontejner pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="24c3c-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="24c3c-104">Zajistit pro obsažené objekty visual zpracování událostí při zpracování zpráv předávaných do kontejneru okno hostitele smyčka filtru zpráv.</span><span class="sxs-lookup"><span data-stu-id="24c3c-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="24c3c-105">Odkazovat na [kurz: hostování vizuální objekty v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) Další informace o tom, jak hostovat vizuální objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.</span><span class="sxs-lookup"><span data-stu-id="24c3c-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c3c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="24c3c-106">Example</span></span>  
 <span data-ttu-id="24c3c-107">Následující kód ukazuje, jak nastavit myši obslužných rutin událostí pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které slouží jako kontejner hostitele pro vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="24c3c-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="24c3c-108">Následující příklad ukazuje, jak nastavit přístupů testu v reakci na soutisku události konkrétní myši.</span><span class="sxs-lookup"><span data-stu-id="24c3c-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="24c3c-109"><xref:System.Windows.Interop.HwndSource> Objekt uvede [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno.</span><span class="sxs-lookup"><span data-stu-id="24c3c-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="24c3c-110">Hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objekt představuje nejvyšší uzel v hierarchii vizuálním stromu.</span><span class="sxs-lookup"><span data-stu-id="24c3c-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="24c3c-111">Je kompletní ukázka přístupů testování objekty pomocí kontejner Win32 hostitele, najdete v části [stiskněte tlačítko Test s ukázkou vzájemná spolupráce Win32](http://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="24c3c-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c3c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="24c3c-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="24c3c-113">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="24c3c-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="24c3c-114">Kurz: Hostování vizuální objektů v aplikaci Win32</span><span class="sxs-lookup"><span data-stu-id="24c3c-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
