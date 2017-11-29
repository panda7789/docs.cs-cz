---
title: "Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="32546-102">Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32546-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="32546-103">Existují několika případech, kdy je důležité, že jedna obslužná rutina není blokovat obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="32546-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="32546-104">Vlastní události povolit události na asynchronní volání jeho obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="32546-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="32546-105">Ve výchozím nastavení je pole úložiště zálohování pro deklaraci události vícesměrového vysílání delegáta, který sériově kombinuje všechny obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="32546-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="32546-106">To znamená, že pokud jeden obslužná rutina trvá dlouhou dobu pro dokončení, zablokuje ostatních obslužných rutin až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="32546-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="32546-107">(Které jsou v pořádku obslužných rutin by měl provést nikdy zdlouhavé nebo potenciálně blokování operací.)</span><span class="sxs-lookup"><span data-stu-id="32546-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="32546-108">Místo použití výchozí implementace událostí, které poskytuje jazyka Visual Basic, můžete použít vlastní události asynchronně spuštění obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="32546-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32546-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="32546-109">Example</span></span>  
 <span data-ttu-id="32546-110">V tomto příkladu `AddHandler` přistupujícího objektu přidá delegát pro každou obslužnou rutinu `Click` událost, která má <xref:System.Collections.ArrayList> uložené v `EventHandlerList` pole.</span><span class="sxs-lookup"><span data-stu-id="32546-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="32546-111">Pokud kód vyvolá `Click` událostí, `RaiseEvent` všechny delegátů obslužných rutin událostí pomocí asynchronně vyvolá přístupového objektu <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="32546-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="32546-112">Dané metody vyvolá každé obslužné rutiny na pracovní vlákno a vrátí okamžitě, takže obslužné rutiny nelze blokovat jednu na druhou.</span><span class="sxs-lookup"><span data-stu-id="32546-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="32546-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="32546-113">See Also</span></span>  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [<span data-ttu-id="32546-114">Události</span><span class="sxs-lookup"><span data-stu-id="32546-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="32546-115">Postupy: deklarování vlastních událostí pro konzervaci paměti</span><span class="sxs-lookup"><span data-stu-id="32546-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
