---
title: "Asynchronní programování pomocí delegátů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e84c004c8efc58c6d6ad55674470bec13fc0bab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="05998-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="05998-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="05998-103">Delegáti umožňují volání v asynchronním režimu synchronní metody.</span><span class="sxs-lookup"><span data-stu-id="05998-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="05998-104">Při volání delegáta synchronně, `Invoke` metoda volá metodu cíl přímo na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="05998-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="05998-105">Pokud `BeginInvoke` metoda je volána, common language runtime (CLR) zařadí do fronty požadavek a vrátí okamžitě volajícímu.</span><span class="sxs-lookup"><span data-stu-id="05998-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="05998-106">Cílové metody se asynchronně volá na vlákno z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="05998-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="05998-107">Původní podproces, který odeslal požadavek, je zdarma chcete pokračovat v provádění paralelně s cílové metody.</span><span class="sxs-lookup"><span data-stu-id="05998-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="05998-108">Pokud metoda zpětného volání byla zadána ve volání `BeginInvoke` metoda, metoda zpětného volání je volána při ukončení cílové metody.</span><span class="sxs-lookup"><span data-stu-id="05998-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="05998-109">Metoda zpětného volání `EndInvoke` metoda získá návratovou hodnotu a vstupu a výstupu nebo jen výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="05998-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="05998-110">Pokud žádná metoda zpětného volání je zadána při volání metody `BeginInvoke`, `EndInvoke` lze volat z vlákna, která se nazývá `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="05998-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05998-111">Kompilátory by měl emitování delegát třídy s `Invoke`, `BeginInvoke`, a `EndInvoke` metod pomocí delegáta specifikovaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="05998-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="05998-112">`BeginInvoke` a `EndInvoke` metody by měla být dekorované jako nativní.</span><span class="sxs-lookup"><span data-stu-id="05998-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="05998-113">Protože tyto metody jsou označeny jako nativní, modul CLR automaticky poskytuje implementaci při načítání, třída.</span><span class="sxs-lookup"><span data-stu-id="05998-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="05998-114">Zavaděč zajistí, že nejsou přepsat.</span><span class="sxs-lookup"><span data-stu-id="05998-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05998-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="05998-115">In This Section</span></span>  
 [<span data-ttu-id="05998-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="05998-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="05998-117">Popisuje použití delegátů pro asynchronní volání do metody obyčejnou a obsahuje příklady jednoduchého kódu, které se zobrazí čtyři způsoby čekání na asynchronní volání vrátit.</span><span class="sxs-lookup"><span data-stu-id="05998-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05998-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="05998-118">Related Sections</span></span>  
 [<span data-ttu-id="05998-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="05998-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="05998-120">Popisuje asynchronní programování s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05998-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05998-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="05998-121">See Also</span></span>  
 <xref:System.Delegate>
