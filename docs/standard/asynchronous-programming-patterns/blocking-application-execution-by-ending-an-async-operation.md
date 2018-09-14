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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: db8255e28818cc4def69e6dcd9da06eb7f9251a0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569343"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="98b8c-102">Blokování provádění aplikace ukončením asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="98b8c-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="98b8c-103">Aplikace, které nemůže pokračovat v další práci při čekání na výsledcích asynchronní operaci musí blokovat až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="98b8c-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="98b8c-104">Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="98b8c-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="98b8c-105">Volání asynchronních operací \**End \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="98b8c-105">Call the asynchronous operations \**End\*\*\*OperationName* method.</span></span> <span data-ttu-id="98b8c-106">Tento přístup je ukázáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="98b8c-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="98b8c-107">Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operace \**začít \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="98b8c-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method.</span></span> <span data-ttu-id="98b8c-108">Příklad, který ukazuje tento přístup, najdete v části [blokování aplikace spuštění pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="98b8c-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="98b8c-109">Aplikace, které používají \**koncové \*\*\* OperationName* obvykle bude volat metodu blokovat, dokud se asynchronní operace nebude dokončena \**začít \*\*\* OperationName* metody provádět každé dílo, které lze provést bez výsledky operace a poté zavolejte \**End \*\*\* OperationName*.</span><span class="sxs-lookup"><span data-stu-id="98b8c-109">Applications that use the \**End\*\*\*OperationName* method to block until an asynchronous operation is complete will typically call the \**Begin\*\*\*OperationName* method, perform any work that can be done without the results of the operation, and then call \**End\*\*\*OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98b8c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="98b8c-110">Example</span></span>  
 <span data-ttu-id="98b8c-111">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy načíst informace o systému názvů domény pro počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="98b8c-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="98b8c-112">Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry vzhledem k tomu, že tyto argumenty nejsou vyžadovány, při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="98b8c-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98b8c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98b8c-113">See also</span></span>

- [<span data-ttu-id="98b8c-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="98b8c-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="98b8c-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="98b8c-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
