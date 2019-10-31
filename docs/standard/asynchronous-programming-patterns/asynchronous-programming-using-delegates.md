---
title: Asynchronní programování pomocí delegátů
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121736"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="b2e6c-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="b2e6c-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="b2e6c-103">Delegáti umožňují volat synchronní metodu asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="b2e6c-104">Při synchronním volání delegáta volá metoda `Invoke` cílovou metodu přímo v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="b2e6c-105">Pokud je volána metoda `BeginInvoke`, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="b2e6c-106">Cílová metoda se volá asynchronně ve vlákně z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="b2e6c-107">Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="b2e6c-108">Pokud byla metoda zpětného volání určena při volání metody `BeginInvoke`, je volána metoda zpětného volání při ukončení cílové metody.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="b2e6c-109">V metodě zpětného volání získá metoda `EndInvoke` návratovou hodnotu a všechny vstupně-výstupní nebo výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="b2e6c-110">Pokud není zadána žádná metoda zpětného volání při volání `BeginInvoke`, `EndInvoke` lze volat z vlákna, které se nazývá `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2e6c-111">Kompilátory by měly generovat třídy delegátů pomocí `Invoke`, `BeginInvoke`a `EndInvoke` metod pomocí podpisu delegáta zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="b2e6c-112">Metody `BeginInvoke` a `EndInvoke` by měly být dekorované jako nativní.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="b2e6c-113">Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="b2e6c-114">Zavaděč zajišťuje, že nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2e6c-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b2e6c-115">In This Section</span></span>  
 [<span data-ttu-id="b2e6c-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="b2e6c-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="b2e6c-117">Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2e6c-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b2e6c-118">Related Sections</span></span>  
 [<span data-ttu-id="b2e6c-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="b2e6c-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="b2e6c-120">Popisuje asynchronní programování s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e6c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2e6c-121">See also</span></span>

- <xref:System.Delegate>
