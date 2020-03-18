---
title: Použití delegáta AsyncCallback a stavového objektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094607"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="50f11-102">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="50f11-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="50f11-103">Při použití <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně, můžete použít objekt stavu předat informace mezi zpětná volání a načíst konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="50f11-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="50f11-104">Toto téma ukazuje, že praxe rozbalením příklad u [použití AsyncCallback delegát a ukončit asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="50f11-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50f11-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="50f11-105">Example</span></span>  
 <span data-ttu-id="50f11-106">Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací DNS (Domain Name System) pro počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="50f11-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="50f11-107">Tento příklad definuje a `HostRequest` používá třídu k ukládání informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="50f11-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="50f11-108">Objekt `HostRequest` bude vytvořen pro každý název počítače zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="50f11-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="50f11-109">Tento objekt je <xref:System.Net.Dns.BeginGetHostByName%2A> předán metodě.</span><span class="sxs-lookup"><span data-stu-id="50f11-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="50f11-110">Metoda `ProcessDnsInformation` je volána při každém dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="50f11-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="50f11-111">Objekt `HostRequest` je načten pomocí <xref:System.IAsyncResult.AsyncState%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50f11-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="50f11-112">Metoda `ProcessDnsInformation` používá `HostRequest` objekt k <xref:System.Net.IPHostEntry> uložení vrácené požadavek nebo <xref:System.Net.Sockets.SocketException> vyvolána požadavek.</span><span class="sxs-lookup"><span data-stu-id="50f11-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="50f11-113">Po dokončení všech požadavků aplikace iterates `HostRequest` přes objekty a <xref:System.Net.Sockets.SocketException> zobrazí informace DNS nebo chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="50f11-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="50f11-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f11-114">See also</span></span>

- [<span data-ttu-id="50f11-115">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="50f11-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="50f11-116">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="50f11-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="50f11-117">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="50f11-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
