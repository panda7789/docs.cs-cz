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
ms.openlocfilehash: 6184e52c3f6e39e452331af27b83520e498062aa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289925"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="e30f3-102">Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="e30f3-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="e30f3-103">Aplikace, které nemohou pokračovat v provádění jiné práce při čekání na výsledky asynchronní operace musí blokovat až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="e30f3-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="e30f3-104">Použijte jednu z následujících možností k blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="e30f3-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="e30f3-105">Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácenou metodou **Begin**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="e30f3-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="e30f3-106">Tento přístup je znázorněný v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e30f3-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="e30f3-107">Zavolejte metodu **End**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="e30f3-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="e30f3-108">Příklad, který demonstruje tento přístup, naleznete v tématu [blokování provádění aplikace ukončením asynchronní operace](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e30f3-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="e30f3-109">Aplikace, které používají jeden nebo více <xref:System.Threading.WaitHandle> objektů k blokování, dokud není dokončena asynchronní operace, obvykle zavolají metodu **Begin**_OperationName_ , provádějí všechny práce, které lze provést bez výsledků operace, a poté zablokují až po dokončení asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="e30f3-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="e30f3-110">Aplikace může zablokovat jednotlivé operace voláním jedné z <xref:System.Threading.WaitHandle.WaitOne%2A> metod pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A> .</span><span class="sxs-lookup"><span data-stu-id="e30f3-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="e30f3-111">Chcete-li blokovat při čekání na dokončení sady asynchronních operací, uložte přidružené <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a zavolejte jednu z <xref:System.Threading.WaitHandle.WaitAll%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="e30f3-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="e30f3-112">Chcete-li blokovat při čekání na dokončení některé ze sady asynchronních operací, uložte přidružené <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a zavolejte jednu z <xref:System.Threading.WaitHandle.WaitAny%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="e30f3-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30f3-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e30f3-113">Example</span></span>  
 <span data-ttu-id="e30f3-114">Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS k načtení informací o systému názvů domén pro uživatelem zadaný počítač.</span><span class="sxs-lookup"><span data-stu-id="e30f3-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="e30f3-115">Příklad ukazuje blokování pomocí elementu <xref:System.Threading.WaitHandle> přidruženého k asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="e30f3-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="e30f3-116">Všimněte si, že `null` ( `Nothing` v Visual Basic) je předán pro <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` parametry a, `stateObject` protože nejsou při použití tohoto přístupu vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="e30f3-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e30f3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e30f3-117">See also</span></span>

- [<span data-ttu-id="e30f3-118">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="e30f3-118">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e30f3-119">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="e30f3-119">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
