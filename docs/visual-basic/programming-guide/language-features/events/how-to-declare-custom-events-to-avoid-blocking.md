---
title: 'Postupy: Deklarování vlastních událostí k zabránění blokování'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345137"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="72ca7-102">Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72ca7-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="72ca7-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span><span class="sxs-lookup"><span data-stu-id="72ca7-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="72ca7-104">Custom events allow the event to call its event handlers asynchronously.</span><span class="sxs-lookup"><span data-stu-id="72ca7-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="72ca7-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span><span class="sxs-lookup"><span data-stu-id="72ca7-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="72ca7-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span><span class="sxs-lookup"><span data-stu-id="72ca7-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="72ca7-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span><span class="sxs-lookup"><span data-stu-id="72ca7-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="72ca7-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span><span class="sxs-lookup"><span data-stu-id="72ca7-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ca7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="72ca7-109">Example</span></span>  
 <span data-ttu-id="72ca7-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span><span class="sxs-lookup"><span data-stu-id="72ca7-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="72ca7-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span><span class="sxs-lookup"><span data-stu-id="72ca7-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="72ca7-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span><span class="sxs-lookup"><span data-stu-id="72ca7-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="72ca7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72ca7-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="72ca7-114">Události</span><span class="sxs-lookup"><span data-stu-id="72ca7-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="72ca7-115">Postupy: Deklarování vlastních událostí pro konzervaci paměti</span><span class="sxs-lookup"><span data-stu-id="72ca7-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
