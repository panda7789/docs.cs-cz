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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce77e57eb049c031ed506e8812fff59ba97a978e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950865"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="0b172-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="0b172-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="0b172-103">Delegáti umožňují volat synchronní metodu asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="0b172-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="0b172-104">Při synchronním `Invoke` volání delegáta metoda volá cílovou metodu přímo v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="0b172-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="0b172-105">Pokud je `BeginInvoke` metoda volána, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0b172-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="0b172-106">Cílová metoda se volá asynchronně ve vlákně z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="0b172-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="0b172-107">Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou.</span><span class="sxs-lookup"><span data-stu-id="0b172-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="0b172-108">Pokud byla metoda zpětného volání určena při volání `BeginInvoke` metody, je volána metoda zpětného volání při ukončení cílové metody.</span><span class="sxs-lookup"><span data-stu-id="0b172-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="0b172-109">V metodě `EndInvoke` zpětného volání metoda získá vrácenou hodnotu a všechny vstupní/výstupní nebo výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="0b172-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="0b172-110">Pokud při volání `BeginInvoke`není zadána žádná metoda zpětného `EndInvoke` volání, lze ji volat z vlákna, `BeginInvoke`které je voláno.</span><span class="sxs-lookup"><span data-stu-id="0b172-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0b172-111">Kompilátory by měly generovat třídy delegátů pomocí `Invoke`metod `EndInvoke` , `BeginInvoke`a pomocí podpisu delegáta zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0b172-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="0b172-112">Metody `BeginInvoke` a`EndInvoke` by měly být dekorované jako nativní.</span><span class="sxs-lookup"><span data-stu-id="0b172-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="0b172-113">Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy.</span><span class="sxs-lookup"><span data-stu-id="0b172-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="0b172-114">Zavaděč zajišťuje, že nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="0b172-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b172-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0b172-115">In This Section</span></span>  
 [<span data-ttu-id="0b172-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="0b172-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="0b172-117">Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="0b172-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b172-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0b172-118">Related Sections</span></span>  
 [<span data-ttu-id="0b172-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="0b172-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="0b172-120">Popisuje asynchronní programování s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b172-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b172-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b172-121">See also</span></span>

- <xref:System.Delegate>
