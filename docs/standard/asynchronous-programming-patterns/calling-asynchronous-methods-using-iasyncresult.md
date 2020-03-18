---
title: Volání asynchronních metod pomocí rozhraní IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121316"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="2afa0-102">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2afa0-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="2afa0-103">Typy v rozhraní .NET Framework a knihovnách tříd třetích stran mohou poskytovat metody, které umožňují aplikaci pokračovat v provádění při provádění asynchronních operací v jiných vláknech než v hlavním vlákně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2afa0-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="2afa0-104">Následující části popisují a poskytují příklady kódu, které ukazují různé způsoby, <xref:System.IAsyncResult> jak můžete volat asynchronní metody, které používají návrhový vzor.</span><span class="sxs-lookup"><span data-stu-id="2afa0-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="2afa0-105">[Blokování spuštění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2afa0-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="2afa0-106">[Blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="2afa0-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="2afa0-107">[Dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2afa0-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="2afa0-108">[Použití asyncCallback delegáta ukončit asynchronní operaci](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2afa0-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afa0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2afa0-109">See also</span></span>

- [<span data-ttu-id="2afa0-110">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="2afa0-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="2afa0-111">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="2afa0-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
