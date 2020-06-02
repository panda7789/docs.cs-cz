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
ms.openlocfilehash: 8766e64c52688e820d0eb6a259e39926555d97bd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276346"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="1fad6-102">Použití delegáta AsyncCallback k ukončení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="1fad6-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="1fad6-103">Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="1fad6-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="1fad6-104">Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="1fad6-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="1fad6-105">Použijte <xref:System.AsyncCallback> delegáta pro zpracování výsledků asynchronní operace v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="1fad6-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="1fad6-106">Tento přístup je znázorněný v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1fad6-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="1fad6-107"><xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> K určení, zda byla operace dokončena, použijte vlastnost vrácenou metodou **Begin**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="1fad6-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="1fad6-108">Příklad, který demonstruje tento přístup, najdete v tématu [cyklické dotazování na stav asynchronní operace](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fad6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fad6-109">Example</span></span>  
 <span data-ttu-id="1fad6-110">Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému DNS (Domain Name System) pro uživatelem definované počítače.</span><span class="sxs-lookup"><span data-stu-id="1fad6-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="1fad6-111">Tento příklad vytvoří <xref:System.AsyncCallback> delegáta, který odkazuje na `ProcessDnsInformation` metodu.</span><span class="sxs-lookup"><span data-stu-id="1fad6-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="1fad6-112">Tato metoda se volá jednou pro každý asynchronní požadavek na informace DNS.</span><span class="sxs-lookup"><span data-stu-id="1fad6-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="1fad6-113">Všimněte si, že zadaný uživatel je předán <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru.</span><span class="sxs-lookup"><span data-stu-id="1fad6-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="1fad6-114">Příklad, který ukazuje definování a použití složitějšího objektu stavu, naleznete v tématu [použití delegáta AsyncCallback a objektu State](using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1fad6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fad6-115">See also</span></span>

- [<span data-ttu-id="1fad6-116">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="1fad6-116">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="1fad6-117">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="1fad6-117">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="1fad6-118">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="1fad6-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="1fad6-119">Použití delegáta AsyncCallback a stavového objektu</span><span class="sxs-lookup"><span data-stu-id="1fad6-119">Using an AsyncCallback Delegate and State Object</span></span>](using-an-asynccallback-delegate-and-state-object.md)
