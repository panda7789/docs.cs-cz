---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 604e7a944579a284004817009b06c11b268d5daf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289431"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="41079-102">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="41079-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="41079-103">Existuje několik způsobů, jak vystavit asynchronní funkce pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="41079-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="41079-104">Asynchronní vzor založený na událostech předepisuje jeden způsob, jakým třídy představují asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="41079-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41079-105">Počínaje .NET Framework 4 poskytuje úloha paralelní knihovna nový model pro asynchronní a paralelní programování.</span><span class="sxs-lookup"><span data-stu-id="41079-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="41079-106">Další informace naleznete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="41079-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="41079-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="41079-107">In This Section</span></span>

 [<span data-ttu-id="41079-108">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="41079-109">Popisuje, jak asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou v podstatě vícevláknového návrhu.</span><span class="sxs-lookup"><span data-stu-id="41079-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="41079-110">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-111">Popisuje standardizovaný způsob, jak zabalit třídu, která obsahuje asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="41079-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="41079-112">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-113">Popisuje požadavky pro vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="41079-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="41079-114">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-115">Popisuje, jak určit, kdy se má použít asynchronní vzor založený na událostech namísto <xref:System.IAsyncResult> vzoru reprezentovaného [asynchronním programovacím modelem (APM)](asynchronous-programming-model-apm.md) .</span><span class="sxs-lookup"><span data-stu-id="41079-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="41079-116">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-117">Popisuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="41079-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="41079-118">Je implementováno pomocí pomocných tříd z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů, který zajišťuje správné fungování komponenty v jakémkoli modelu aplikace.</span><span class="sxs-lookup"><span data-stu-id="41079-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="41079-119">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-120">Popisuje, jak vytvořit klienta, který používá komponentu, která implementuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="41079-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="41079-121">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="41079-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="41079-122">Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="41079-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41079-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="41079-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="41079-124">Popisuje <xref:System.ComponentModel.AsyncOperation> třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="41079-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="41079-125">Popisuje <xref:System.ComponentModel.AsyncOperationManager> třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="41079-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="41079-126">Popisuje <xref:System.ComponentModel.BackgroundWorker> součást a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="41079-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41079-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="41079-127">Related Sections</span></span>

 [<span data-ttu-id="41079-128">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="41079-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="41079-129">Popisuje programovací model pro asynchronní a paralelní operace.</span><span class="sxs-lookup"><span data-stu-id="41079-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="41079-130">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="41079-130">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="41079-131">Popisuje funkce multithreadingu v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="41079-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41079-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="41079-132">See also</span></span>

- [<span data-ttu-id="41079-133">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="41079-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="41079-134">Události</span><span class="sxs-lookup"><span data-stu-id="41079-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="41079-135">Vzory návrhu asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="41079-135">Asynchronous Programming Design Patterns</span></span>](index.md)
