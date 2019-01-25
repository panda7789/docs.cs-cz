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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd55bd62653ef64668c13eb791b10afd2013f5f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579508"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="ab738-102">Dotazování na stav asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="ab738-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="ab738-103">Aplikace, které můžete provádět další operace při čekání na výsledcích asynchronní operace by neměly blokovat čekání, až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="ab738-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="ab738-104">Má pokračovat provedením pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="ab738-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="ab738-105">Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operace **začít**_OperationName_ metodou ke zjištění, zda operace byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="ab738-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="ab738-106">Tento postup se označuje jako cyklického dotazování a je ukázáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ab738-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="ab738-107">Použití <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronních operací v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="ab738-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="ab738-108">Příklad, který ukazuje tento přístup, najdete v části [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ab738-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab738-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab738-109">Example</span></span>  
 <span data-ttu-id="ab738-110">Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy načíst informace o systému názvů domény pro počítače zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ab738-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="ab738-111">Tento příklad spustí asynchronní operaci a potom zobrazí období (".") v konzole až do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="ab738-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="ab738-112">Všimněte si, že **null** (**nic** v jazyce Visual Basic) je předán <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> a <xref:System.Object> parametry vzhledem k tomu, že tyto argumenty nejsou vyžadovány, při použití tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="ab738-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ab738-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab738-113">See also</span></span>

- [<span data-ttu-id="ab738-114">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="ab738-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="ab738-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="ab738-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
