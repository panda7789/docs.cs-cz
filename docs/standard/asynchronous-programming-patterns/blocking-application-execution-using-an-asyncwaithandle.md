---
title: "Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="0cbe7-102">Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="0cbe7-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="0cbe7-103">Aplikace, které nelze nadále provádět další činnosti při čekání na výsledky asynchronní operace musí blok, dokud se operace nedokončí.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="0cbe7-104">Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="0cbe7-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="0cbe7-105">Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít** *OperationName* metoda.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="0cbe7-106">Tento přístup je ukázáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="0cbe7-107">Volání asynchronní operaci **End** *OperationName* metoda.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-107">Call the asynchronous operation's **End** *OperationName* method.</span></span> <span data-ttu-id="0cbe7-108">Příklad, který představuje tuto metodu, najdete v části [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="0cbe7-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="0cbe7-109">Aplikace, které používají jeden nebo více <xref:System.Threading.WaitHandle> objekty, které chcete blokovat až do dokončení asynchronní operace bude obvykle volat **začít** *OperationName* metody provedení veškerou práci, kterou lze provést bez výsledky operace a potom blok dokud asynchronní operace dokončí.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="0cbe7-110">Aplikace můžete blokovat v rámci jedné operace mezi voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metod pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="0cbe7-111">Blokování při čekání na sadu na dokončení asynchronních operací, uložení přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a volání jednoho <xref:System.Threading.WaitHandle.WaitAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="0cbe7-112">Blokování při čekání na některého z sadu na dokončení asynchronních operací, uložení přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a volání jednoho <xref:System.Threading.WaitHandle.WaitAny%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cbe7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cbe7-113">Example</span></span>  
 <span data-ttu-id="0cbe7-114">Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS načíst informace o systému názvů domény pro počítač zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="0cbe7-115">Příklad ukazuje blokování pomocí <xref:System.Threading.WaitHandle> přidružené asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="0cbe7-116">Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je pro předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry protože tyto nejsou požadovány při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0cbe7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cbe7-117">See Also</span></span>  
 [<span data-ttu-id="0cbe7-118">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="0cbe7-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="0cbe7-119">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="0cbe7-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
