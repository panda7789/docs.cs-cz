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
ms.openlocfilehash: e52ed550510253aba9401931c0f612211c7d1bf5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276423"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="caf25-102">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="caf25-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="caf25-103">Použijete-li <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně, můžete použít objekt stavu k předání informací mezi zpětnými voláními a k načtení konečného výsledku.</span><span class="sxs-lookup"><span data-stu-id="caf25-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="caf25-104">Toto téma ukazuje tento postup rozbalením příkladu v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="caf25-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="caf25-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="caf25-105">Example</span></span>  
 <span data-ttu-id="caf25-106">Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému DNS (Domain Name System) pro uživatelem definované počítače.</span><span class="sxs-lookup"><span data-stu-id="caf25-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="caf25-107">Tento příklad definuje a používá `HostRequest` třídu k ukládání informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="caf25-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="caf25-108">Vytvoří se `HostRequest` objekt pro každý název počítače zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="caf25-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="caf25-109">Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="caf25-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="caf25-110">`ProcessDnsInformation`Metoda je volána pokaždé, když je požadavek dokončen.</span><span class="sxs-lookup"><span data-stu-id="caf25-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="caf25-111">`HostRequest`Objekt je načten pomocí <xref:System.IAsyncResult.AsyncState%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="caf25-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="caf25-112">`ProcessDnsInformation`Metoda používá `HostRequest` objekt k uložení <xref:System.Net.IPHostEntry> vráceného požadavkem nebo <xref:System.Net.Sockets.SocketException> vyvolaným požadavkem.</span><span class="sxs-lookup"><span data-stu-id="caf25-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="caf25-113">Po dokončení všech požadavků aplikace provede iteraci `HostRequest` objektů a zobrazí informace DNS nebo <xref:System.Net.Sockets.SocketException> chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="caf25-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="caf25-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="caf25-114">See also</span></span>

- [<span data-ttu-id="caf25-115">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="caf25-115">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="caf25-116">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="caf25-116">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="caf25-117">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="caf25-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
