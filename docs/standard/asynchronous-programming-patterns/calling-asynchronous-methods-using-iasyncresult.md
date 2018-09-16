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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23fa927dcdb91fb3905f1cbe845450751de91157
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668649"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="cc7b1-102">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="cc7b1-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="cc7b1-103">Typy v rozhraní .NET Framework a knihovny tříd třetích stran můžou poskytovat metody, které umožňují aplikace má pokračovat provedením při provádění asynchronní operace ve vláknech než hlavního vlákna aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7b1-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="cc7b1-104">Následující části popisují a poskytnout příklady kódu, které ukazují různé způsoby, jak můžete volat asynchronní metody, které používají <xref:System.IAsyncResult> vzoru návrhu.</span><span class="sxs-lookup"><span data-stu-id="cc7b1-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="cc7b1-105">[Blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="cc7b1-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="cc7b1-106">[Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="cc7b1-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="cc7b1-107">[Dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="cc7b1-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="cc7b1-108">[Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="cc7b1-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7b1-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc7b1-109">See also</span></span>

- [<span data-ttu-id="cc7b1-110">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="cc7b1-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="cc7b1-111">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="cc7b1-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
