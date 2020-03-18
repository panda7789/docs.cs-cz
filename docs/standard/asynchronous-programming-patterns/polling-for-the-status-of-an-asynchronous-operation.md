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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123965"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="fce2e-102">Dotazování na stav asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="fce2e-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="fce2e-103">Aplikace, které mohou dělat jinou práci při čekání na výsledky asynchronní operace by nemělblokovat čekání až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="fce2e-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="fce2e-104">Pomocí jedné z následujících možností pokračujte v provádění pokynů při čekání na dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="fce2e-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="fce2e-105">Pomocí <xref:System.IAsyncResult.IsCompleted%2A> vlastnosti <xref:System.IAsyncResult> vrácené metodou **Begin**_OperationName_ asynchronní operace určete, zda byla operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="fce2e-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="fce2e-106">Tento přístup se označuje jako dotazování a je demonstrován v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fce2e-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="fce2e-107">Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="fce2e-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="fce2e-108">Příklad, který ukazuje tento přístup, naleznete [v tématu použití AsyncCallback delegáta ukončit asynchronní operaci](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fce2e-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce2e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="fce2e-109">Example</span></span>  
 <span data-ttu-id="fce2e-110">Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací o systému DNS pro počítač zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="fce2e-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="fce2e-111">Tento příklad spustí asynchronní operaci a potom vytiskne tečky (".") v konzole, dokud nebude operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="fce2e-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="fce2e-112">Všimněte si, že **null** (**Nothing** v jazyce Visual Basic) je předán pro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> parametry a, <xref:System.Object> protože tyto argumenty nejsou vyžadovány při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="fce2e-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fce2e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fce2e-113">See also</span></span>

- [<span data-ttu-id="fce2e-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="fce2e-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="fce2e-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="fce2e-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
