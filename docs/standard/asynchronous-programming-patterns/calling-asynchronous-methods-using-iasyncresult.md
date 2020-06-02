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
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289912"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="ccb5e-102">Volání asynchronních metod pomocí rozhraní IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="ccb5e-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="ccb5e-103">Typy v .NET Framework a knihovny tříd třetích stran mohou poskytovat metody, které umožní aplikaci pokračovat v provádění při provádění asynchronních operací v jiných vláknech než v rámci hlavního vlákna aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccb5e-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="ccb5e-104">Následující části popisují a poskytují příklady kódu, které ukazují různé způsoby, jak můžete volat asynchronní metody, které používají <xref:System.IAsyncResult> návrhový vzor.</span><span class="sxs-lookup"><span data-stu-id="ccb5e-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="ccb5e-105">[Blokování provádění aplikace ukončením asynchronní operace](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ccb5e-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="ccb5e-106">[Blokování spuštění aplikace pomocí AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="ccb5e-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="ccb5e-107">[Cyklické dotazování na stav asynchronní operace](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ccb5e-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="ccb5e-108">[Použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ccb5e-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb5e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb5e-109">See also</span></span>

- [<span data-ttu-id="ccb5e-110">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="ccb5e-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="ccb5e-111">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="ccb5e-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
