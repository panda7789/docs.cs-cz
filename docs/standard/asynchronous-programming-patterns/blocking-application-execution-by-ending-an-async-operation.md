---
title: Blokování provádění aplikace ukončením asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121331"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="f1c84-102">Blokování provádění aplikace ukončením asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="f1c84-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="f1c84-103">Aplikace, které nemohou pokračovat v provádění jiné práce při čekání na výsledky asynchronní operace musí blokovat až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="f1c84-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="f1c84-104">Použijte jednu z následujících možností k blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="f1c84-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="f1c84-105">Zavolejte metodu **End**_operace_ pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f1c84-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="f1c84-106">Tento přístup je znázorněný v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f1c84-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="f1c84-107">Použijte vlastnost <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> vrácená metodou **Begin**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f1c84-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="f1c84-108">Příklad, který demonstruje tento přístup, naleznete v tématu [blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="f1c84-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="f1c84-109">Aplikace, které používají metodu **End**_OperationName_ k blokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName_ , provádějí všechny práce, které lze provést bez výsledků operaci a potom zavolejte **End**_NázevOperace_.</span><span class="sxs-lookup"><span data-stu-id="f1c84-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1c84-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1c84-110">Example</span></span>  
 <span data-ttu-id="f1c84-111">Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací o systému názvů domén pro uživatelem zadaný počítač.</span><span class="sxs-lookup"><span data-stu-id="f1c84-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="f1c84-112">Všimněte si, že `null` (`Nothing` v Visual Basic) se předává pro parametry <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` a `stateObject`, protože při použití tohoto přístupu se tyto argumenty nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="f1c84-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f1c84-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1c84-113">See also</span></span>

- [<span data-ttu-id="f1c84-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="f1c84-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="f1c84-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="f1c84-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
