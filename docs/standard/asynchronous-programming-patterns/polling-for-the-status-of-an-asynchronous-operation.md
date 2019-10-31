---
title: Dotazování na stav asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123965"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="777b7-102">Dotazování na stav asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="777b7-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="777b7-103">Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="777b7-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="777b7-104">Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="777b7-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="777b7-105">K určení, zda byla operace dokončena, použijte vlastnost <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> vrácenou metodou **Begin**_OperationName_ asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="777b7-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="777b7-106">Tento přístup se označuje jako cyklické dotazování a je znázorněno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="777b7-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="777b7-107">Použijte delegáta <xref:System.AsyncCallback> pro zpracování výsledků asynchronní operace v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="777b7-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="777b7-108">Příklad, který demonstruje tento přístup, najdete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="777b7-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="777b7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="777b7-109">Example</span></span>  
 <span data-ttu-id="777b7-110">Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací o systému názvů domén pro uživatelem zadaný počítač.</span><span class="sxs-lookup"><span data-stu-id="777b7-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="777b7-111">Tento příklad spustí asynchronní operaci a poté vytiskne tečky (".") v konzole nástroje, dokud není operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="777b7-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="777b7-112">Všimněte si, že **hodnota null** (**Nothing** v Visual Basic) se předává pro <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> a parametry <xref:System.Object>, protože tyto argumenty se při použití tohoto přístupu nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="777b7-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="777b7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="777b7-113">See also</span></span>

- [<span data-ttu-id="777b7-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="777b7-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="777b7-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="777b7-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
