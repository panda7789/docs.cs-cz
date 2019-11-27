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
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="624f3-102">Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="624f3-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="624f3-103">Je-li důležité, aby jedna obslužná rutina události neblokovala následné obslužné rutiny událostí, existuje několik okolností.</span><span class="sxs-lookup"><span data-stu-id="624f3-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="624f3-104">Vlastní události umožňují, aby událost volala své obslužné rutiny událostí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="624f3-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="624f3-105">Ve výchozím nastavení je zálohovacím polem pro deklaraci události delegát vícesměrového vysílání, který pomocí sériového kombinování všech obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="624f3-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="624f3-106">To znamená, že pokud dokončení jedné obslužné rutiny trvá dlouhou dobu, blokuje ostatní obslužné rutiny až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="624f3-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="624f3-107">(Správně fungující obslužné rutiny událostí by nikdy neměly provádět zdlouhavé nebo potenciálně blokující operace.)</span><span class="sxs-lookup"><span data-stu-id="624f3-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="624f3-108">Namísto použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní událost k asynchronnímu spuštění obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="624f3-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="624f3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="624f3-109">Example</span></span>  
 <span data-ttu-id="624f3-110">V tomto příkladu přistupující objekt `AddHandler` přidá delegáta pro každou obslužnou rutinu události `Click` na <xref:System.Collections.ArrayList> uloženou v poli `EventHandlerList`.</span><span class="sxs-lookup"><span data-stu-id="624f3-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="624f3-111">Když kód vyvolá událost `Click`, přistupující objekt `RaiseEvent` vyvolá veškerou delegáta obslužné rutiny události asynchronně pomocí metody <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="624f3-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="624f3-112">Tato metoda vyvolá každou obslužnou rutinu v pracovním vlákně a vrátí ji okamžitě, takže obslužné rutiny nemohou jiné blokovat.</span><span class="sxs-lookup"><span data-stu-id="624f3-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="624f3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="624f3-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="624f3-114">Události</span><span class="sxs-lookup"><span data-stu-id="624f3-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="624f3-115">Postupy: Deklarování vlastních událostí pro konzervaci paměti</span><span class="sxs-lookup"><span data-stu-id="624f3-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
