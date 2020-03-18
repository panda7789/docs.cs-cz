---
title: Použití delegáta AsyncCallback k ukončení asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130927"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="7e794-102">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="7e794-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="7e794-103">Aplikace, které mohou dělat jinou práci při čekání na výsledky asynchronní operace by nemělblokovat čekání až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="7e794-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="7e794-104">Pomocí jedné z následujících možností pokračujte v provádění pokynů při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="7e794-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="7e794-105">Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="7e794-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="7e794-106">Tento přístup je demonstrován v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7e794-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="7e794-107">Pomocí <xref:System.IAsyncResult.IsCompleted%2A> vlastnosti <xref:System.IAsyncResult> vrácené metodou **Begin**_OperationName_ asynchronní operace určete, zda byla operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="7e794-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="7e794-108">Příklad, který ukazuje tento přístup, naleznete [v tématu dotazování pro stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7e794-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e794-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e794-109">Example</span></span>  
 <span data-ttu-id="7e794-110">Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací DNS (Domain Name System) pro počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7e794-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="7e794-111">Tento příklad <xref:System.AsyncCallback> vytvoří delegáta, `ProcessDnsInformation` který odkazuje na metodu.</span><span class="sxs-lookup"><span data-stu-id="7e794-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="7e794-112">Tato metoda je volána jednou pro každý asynchronní požadavek na informace DNS.</span><span class="sxs-lookup"><span data-stu-id="7e794-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="7e794-113">Všimněte si, že hostitel zadaný uživatelem je předán parametru. <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="7e794-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="7e794-114">Příklad, který ukazuje definování a použití složitější objekt stavu, naleznete [v tématu použití AsyncCallback delegate a state Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="7e794-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7e794-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e794-115">See also</span></span>

- [<span data-ttu-id="7e794-116">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="7e794-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="7e794-117">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="7e794-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="7e794-118">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="7e794-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="7e794-119">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="7e794-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
