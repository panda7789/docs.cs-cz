---
title: Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121430"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="ec332-102">Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="ec332-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="ec332-103">Aplikace, které nemohou pokračovat v jiné práci při čekání na výsledky asynchronní operace, musí blokovat, dokud nebude operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="ec332-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="ec332-104">Pomocí jedné z následujících možností zablokujte hlavní vlákno aplikace při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="ec332-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="ec332-105">Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost vrácené <xref:System.IAsyncResult> metodou **Begin**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ec332-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="ec332-106">Tento přístup je demonstrován v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ec332-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="ec332-107">Volání asynchronní operace **End**_OperationName_ metoda.</span><span class="sxs-lookup"><span data-stu-id="ec332-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="ec332-108">Příklad, který ukazuje tento přístup, naleznete [v tématu blokování spuštění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ec332-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="ec332-109">Aplikace, které používají <xref:System.Threading.WaitHandle> jeden nebo více objektů k zablokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName,_ provádějí jakoukoli práci, kterou lze provést bez výsledků operace, a poté blokují, dokud nebude dokončena asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ec332-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="ec332-110">Aplikace může blokovat na jednu operaci <xref:System.Threading.WaitHandle.WaitOne%2A> voláním <xref:System.IAsyncResult.AsyncWaitHandle%2A>jedné z metod pomocí .</span><span class="sxs-lookup"><span data-stu-id="ec332-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="ec332-111">Chcete-li blokovat při čekání na sadu asynchronních operací <xref:System.IAsyncResult.AsyncWaitHandle%2A> k dokončení, uložte <xref:System.Threading.WaitHandle.WaitAll%2A> přidružené objekty v poli a volání jedné z metod.</span><span class="sxs-lookup"><span data-stu-id="ec332-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="ec332-112">Chcete-li blokovat při čekání na některou ze sady asynchronních <xref:System.IAsyncResult.AsyncWaitHandle%2A> operací k dokončení, uložte přidružené objekty v poli a volání jedné z <xref:System.Threading.WaitHandle.WaitAny%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="ec332-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec332-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec332-113">Example</span></span>  
 <span data-ttu-id="ec332-114">Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS k načtení informací o systému DNS pro počítač zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ec332-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="ec332-115">Příklad ukazuje blokování pomocí <xref:System.Threading.WaitHandle> přidružené asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ec332-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="ec332-116">Všimněte `null` `Nothing` si, že (v <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` jazyce Visual Basic) je předán pro parametry a, `stateObject` protože tyto nejsou vyžadovány při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="ec332-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ec332-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec332-117">See also</span></span>

- [<span data-ttu-id="ec332-118">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="ec332-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="ec332-119">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="ec332-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
