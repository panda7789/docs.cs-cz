---
title: "Použití delegáta AsyncCallback k ukončení asynchronní operace"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="9d246-102">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="9d246-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="9d246-103">Aplikace, které můžete provádět další činnosti při čekání na výsledky asynchronní operace by neměly blokovat, počkejte, až se dokončí.</span><span class="sxs-lookup"><span data-stu-id="9d246-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="9d246-104">Pokud chcete pokračovat v provádění pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="9d246-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="9d246-105">Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="9d246-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="9d246-106">Tento přístup je ukázáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9d246-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="9d246-107">Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít** *OperationName* metoda k určení, zda bude dokončena operace.</span><span class="sxs-lookup"><span data-stu-id="9d246-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="9d246-108">Příklad, který představuje tuto metodu, najdete v části [dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="9d246-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d246-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d246-109">Example</span></span>  
 <span data-ttu-id="9d246-110">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému DNS (Domain Name) pro počítače zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9d246-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="9d246-111">Tento příklad vytvoří <xref:System.AsyncCallback> delegáta, který odkazuje `ProcessDnsInformation` metoda.</span><span class="sxs-lookup"><span data-stu-id="9d246-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="9d246-112">Tato metoda je volána jednou pro každý asynchronní požadavek informace DNS.</span><span class="sxs-lookup"><span data-stu-id="9d246-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="9d246-113">Všimněte si, že je předán hostitele zadán uživatel <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametr.</span><span class="sxs-lookup"><span data-stu-id="9d246-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="9d246-114">Příklad, který ukazuje definování a používání složitější objekt stavu, naleznete v části [použití delegáta AsyncCallback a objekt stavu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="9d246-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9d246-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d246-115">See Also</span></span>  
 [<span data-ttu-id="9d246-116">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="9d246-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="9d246-117">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="9d246-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="9d246-118">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="9d246-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="9d246-119">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="9d246-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
