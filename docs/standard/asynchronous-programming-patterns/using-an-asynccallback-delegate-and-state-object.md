---
title: "Použití delegáta AsyncCallback a stavového objektu"
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb0cdc9e98dcaf3c9f9879359eff0b31c8435773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="d0d49-102">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="d0d49-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="d0d49-103">Když použijete <xref:System.AsyncCallback> delegovat ke zpracování výsledků asynchronní operace v samostatné vlákno, můžete použít objekt stavu k předávání informací mezi zpětná volání a k načítání konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="d0d49-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="d0d49-104">Toto téma ukazuje, že postup rozšířením v příkladu v [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="d0d49-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0d49-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0d49-105">Example</span></span>  
 <span data-ttu-id="d0d49-106">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému DNS (Domain Name) pro počítače zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="d0d49-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="d0d49-107">Tento příklad definuje a používá `HostRequest` třídu pro ukládání informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="d0d49-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="d0d49-108">A `HostRequest` objekt se vytvoří pro každý název počítače zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="d0d49-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="d0d49-109">Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d0d49-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="d0d49-110">`ProcessDnsInformation` Metoda je volána při každém dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="d0d49-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="d0d49-111">`HostRequest` Objekt je načíst pomocí <xref:System.IAsyncResult.AsyncState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d0d49-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="d0d49-112">`ProcessDnsInformation` Metoda používá `HostRequest` objekt pro uložení <xref:System.Net.IPHostEntry> vrácených požadavkem nebo <xref:System.Net.Sockets.SocketException> vyvolané žádosti.</span><span class="sxs-lookup"><span data-stu-id="d0d49-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="d0d49-113">Po dokončení všech požadavků aplikace iteruje nad `HostRequest` objekty a zobrazí informace o DNS nebo <xref:System.Net.Sockets.SocketException> chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="d0d49-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d0d49-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d49-114">See Also</span></span>  
 [<span data-ttu-id="d0d49-115">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="d0d49-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="d0d49-116">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="d0d49-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="d0d49-117">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="d0d49-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
