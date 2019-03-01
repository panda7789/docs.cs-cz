---
title: 'Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: fe8775a15ce5149cf307879ab31e2ec0a8ba8f47
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965173"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="94e3f-102">Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94e3f-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="94e3f-103">Existují několika případech, kdy je důležité, že jedna obslužná rutina události nedochází k blokování obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="94e3f-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="94e3f-104">Vlastní události povolit událostí na asynchronní volání jeho obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="94e3f-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="94e3f-105">Ve výchozím nastavení je pole záložní úložiště pro deklaraci události vícesměrového vysílání delegát, který sériově kombinuje všechny obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="94e3f-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="94e3f-106">To znamená, že pokud jednu obslužnou rutinu trvá dlouhou dobu pro dokončení, zablokuje obslužné rutiny až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="94e3f-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="94e3f-107">(Které jsou v pořádku obslužné by měl provádět nikdy dlouhé nebo potenciálně blokující operace.)</span><span class="sxs-lookup"><span data-stu-id="94e3f-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="94e3f-108">Místo použití výchozí implementace události, které poskytuje Visual Basic, můžete použít vlastní událost obslužné rutiny událostí spustit asynchronně.</span><span class="sxs-lookup"><span data-stu-id="94e3f-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94e3f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="94e3f-109">Example</span></span>  
 <span data-ttu-id="94e3f-110">V tomto příkladu `AddHandler` přistupující objekt přidá delegáta pro každou obslužnou rutinu z `Click` události <xref:System.Collections.ArrayList> uložené v `EventHandlerList` pole.</span><span class="sxs-lookup"><span data-stu-id="94e3f-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="94e3f-111">Kódu vyvolá `Click` událostí, `RaiseEvent` přistupující objekt vyvolává Všichni delegáti obslužné rutiny události asynchronně pomocí <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="94e3f-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="94e3f-112">Tato metoda vyvolá každou obslužnou rutinu v pracovní podproces a vrátí hodnotu okamžitě, takže obslužné rutiny nelze blokovat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="94e3f-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="94e3f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94e3f-113">See also</span></span>
- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="94e3f-114">Události</span><span class="sxs-lookup"><span data-stu-id="94e3f-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="94e3f-115">Postupy: Deklarování vlastních událostí pro konzervaci paměti</span><span class="sxs-lookup"><span data-stu-id="94e3f-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
