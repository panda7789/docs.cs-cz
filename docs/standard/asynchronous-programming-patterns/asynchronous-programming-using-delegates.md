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
ms.openlocfilehash: 82e0a57c3d8e180456aed48886e38ca466db16c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289964"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="6e45f-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="6e45f-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="6e45f-103">Delegáti umožňují volat synchronní metodu asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="6e45f-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="6e45f-104">Při synchronním volání delegáta `Invoke` metoda volá cílovou metodu přímo v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="6e45f-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="6e45f-105">Pokud `BeginInvoke` je metoda volána, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="6e45f-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="6e45f-106">Cílová metoda se volá asynchronně ve vlákně z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="6e45f-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="6e45f-107">Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou.</span><span class="sxs-lookup"><span data-stu-id="6e45f-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="6e45f-108">Pokud byla metoda zpětného volání určena při volání `BeginInvoke` metody, je volána metoda zpětného volání při ukončení cílové metody.</span><span class="sxs-lookup"><span data-stu-id="6e45f-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="6e45f-109">V metodě zpětného volání `EndInvoke` Metoda získá vrácenou hodnotu a všechny vstupní/výstupní nebo výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="6e45f-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="6e45f-110">Pokud při volání není zadána žádná metoda zpětného volání `BeginInvoke` , `EndInvoke` lze ji volat z vlákna, které je voláno `BeginInvoke` .</span><span class="sxs-lookup"><span data-stu-id="6e45f-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6e45f-111">Kompilátory by měly generovat třídy delegátů pomocí `Invoke` `BeginInvoke` metod, a `EndInvoke` pomocí podpisu delegáta zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6e45f-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="6e45f-112">`BeginInvoke`Metody a `EndInvoke` by měly být dekorované jako nativní.</span><span class="sxs-lookup"><span data-stu-id="6e45f-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="6e45f-113">Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy.</span><span class="sxs-lookup"><span data-stu-id="6e45f-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="6e45f-114">Zavaděč zajišťuje, že nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="6e45f-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e45f-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6e45f-115">In This Section</span></span>  
 [<span data-ttu-id="6e45f-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="6e45f-116">Calling Synchronous Methods Asynchronously</span></span>](calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="6e45f-117">Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="6e45f-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6e45f-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6e45f-118">Related Sections</span></span>  
 [<span data-ttu-id="6e45f-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="6e45f-119">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="6e45f-120">Popisuje asynchronní programování s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e45f-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e45f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e45f-121">See also</span></span>

- <xref:System.Delegate>
