---
title: "Dotazování na stav asynchronní operace"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="07de0-102">Dotazování na stav asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="07de0-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="07de0-103">Aplikace, které můžete provádět další činnosti při čekání na výsledky asynchronní operace by neměly blokovat, počkejte, až se dokončí.</span><span class="sxs-lookup"><span data-stu-id="07de0-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="07de0-104">Pokud chcete pokračovat v provádění pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="07de0-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="07de0-105">Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít** *OperationName* metoda k určení, zda bude dokončena operace.</span><span class="sxs-lookup"><span data-stu-id="07de0-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="07de0-106">Tento postup se označuje jako cyklického dotazování a je ukázáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="07de0-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="07de0-107">Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="07de0-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="07de0-108">Příklad, který představuje tuto metodu, najdete v části [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="07de0-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07de0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="07de0-109">Example</span></span>  
 <span data-ttu-id="07de0-110">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému názvů domény pro počítač zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="07de0-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="07de0-111">Tento příkaz spustí asynchronní operaci a potom zobrazí tečky (".") v konzole, dokud se nedokončí operaci.</span><span class="sxs-lookup"><span data-stu-id="07de0-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="07de0-112">Všimněte si, že **null** (**nic** v jazyce Visual Basic) byla předána pro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> a <xref:System.Object> parametry vzhledem k tomu, že tyto argumenty nejsou povinné, při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="07de0-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="07de0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="07de0-113">See Also</span></span>  
 [<span data-ttu-id="07de0-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="07de0-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="07de0-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="07de0-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
