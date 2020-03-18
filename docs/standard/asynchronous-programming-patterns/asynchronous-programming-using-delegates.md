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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121736"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="8f7db-102">Asynchronní programování pomocí delegátů</span><span class="sxs-lookup"><span data-stu-id="8f7db-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="8f7db-103">Delegáti umožňují volat synchronní metodu asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="8f7db-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="8f7db-104">Při volání delegáta synchronně `Invoke` metoda volá cílovou metodu přímo v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="8f7db-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="8f7db-105">`BeginInvoke` Pokud je metoda volána, clr (CLR) společného jazyka zařadí požadavek do fronty a okamžitě se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="8f7db-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="8f7db-106">Cílová metoda se nazývá asynchronně ve vlákně z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8f7db-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="8f7db-107">Původní vlákno, které odeslal požadavek, je volně pokračovat v provádění souběžně s cílovou metodou.</span><span class="sxs-lookup"><span data-stu-id="8f7db-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="8f7db-108">Pokud byla ve volání `BeginInvoke` metody zadána metoda zpětného volání, je při ukončení cílové metody volána metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8f7db-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="8f7db-109">V metodě zpětného `EndInvoke` volání metoda získá vrácenou hodnotu a všechny parametry input/output nebo pouze pro výstup.</span><span class="sxs-lookup"><span data-stu-id="8f7db-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="8f7db-110">Pokud při volání `BeginInvoke`není zadána `EndInvoke` žádná metoda zpětného `BeginInvoke`volání , lze volat z vlákna, které volalo .</span><span class="sxs-lookup"><span data-stu-id="8f7db-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f7db-111">Kompilátory by měly vyzařovat delegované třídy s `Invoke`, `BeginInvoke`a `EndInvoke` metodami pomocí podpisu delegáta určeného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8f7db-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="8f7db-112">Metody `BeginInvoke` `EndInvoke` a by měly být dekorovány jako nativní.</span><span class="sxs-lookup"><span data-stu-id="8f7db-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="8f7db-113">Vzhledem k tomu, že tyto metody jsou označeny jako nativní, CLR automaticky poskytuje implementaci v době načítání třídy.</span><span class="sxs-lookup"><span data-stu-id="8f7db-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="8f7db-114">Nakladač zajišťuje, že nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="8f7db-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f7db-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8f7db-115">In This Section</span></span>  
 [<span data-ttu-id="8f7db-116">Asynchronní volání synchronních metod</span><span class="sxs-lookup"><span data-stu-id="8f7db-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="8f7db-117">Popisuje použití delegátů provést asynchronní volání běžné metody a poskytuje jednoduché příklady kódu, které ukazují čtyři způsoby čekání na asynchronní volání vrátit.</span><span class="sxs-lookup"><span data-stu-id="8f7db-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f7db-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8f7db-118">Related Sections</span></span>  
 [<span data-ttu-id="8f7db-119">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="8f7db-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="8f7db-120">Popisuje asynchronní programování pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f7db-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7db-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f7db-121">See also</span></span>

- <xref:System.Delegate>
