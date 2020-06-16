---
title: Asynchronní vzor založený na událostech (EAP)
description: Viz odkazy na články týkající se asynchronního vzoru založeného na událostech (EAP) v rozhraní .NET, jako je implementace, osvědčené postupy, implementace klienta EAP a další.
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 03b4d914d72b96b882c774565654c022b145b5f2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768869"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="060df-103">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="060df-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="060df-104">Existuje několik způsobů, jak vystavit asynchronní funkce pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="060df-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="060df-105">Asynchronní vzor založený na událostech předepisuje jeden způsob, jakým třídy představují asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="060df-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="060df-106">Počínaje .NET Framework 4 poskytuje úloha paralelní knihovna nový model pro asynchronní a paralelní programování.</span><span class="sxs-lookup"><span data-stu-id="060df-106">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="060df-107">Další informace naleznete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="060df-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="060df-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="060df-108">In This Section</span></span>

 [<span data-ttu-id="060df-109">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="060df-110">Popisuje, jak asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou v podstatě vícevláknového návrhu.</span><span class="sxs-lookup"><span data-stu-id="060df-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="060df-111">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-112">Popisuje standardizovaný způsob, jak zabalit třídu, která obsahuje asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="060df-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="060df-113">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-114">Popisuje požadavky pro vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="060df-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="060df-115">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-116">Popisuje, jak určit, kdy se má použít asynchronní vzor založený na událostech namísto <xref:System.IAsyncResult> vzoru reprezentovaného [asynchronním programovacím modelem (APM)](asynchronous-programming-model-apm.md) .</span><span class="sxs-lookup"><span data-stu-id="060df-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="060df-117">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-118">Popisuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="060df-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="060df-119">Je implementováno pomocí pomocných tříd z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů, který zajišťuje správné fungování komponenty v jakémkoli modelu aplikace.</span><span class="sxs-lookup"><span data-stu-id="060df-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="060df-120">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-121">Popisuje, jak vytvořit klienta, který používá komponentu, která implementuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="060df-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="060df-122">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="060df-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="060df-123">Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="060df-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="060df-124">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="060df-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="060df-125">Popisuje <xref:System.ComponentModel.AsyncOperation> třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="060df-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="060df-126">Popisuje <xref:System.ComponentModel.AsyncOperationManager> třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="060df-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="060df-127">Popisuje <xref:System.ComponentModel.BackgroundWorker> součást a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="060df-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="060df-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="060df-128">Related Sections</span></span>

 [<span data-ttu-id="060df-129">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="060df-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="060df-130">Popisuje programovací model pro asynchronní a paralelní operace.</span><span class="sxs-lookup"><span data-stu-id="060df-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="060df-131">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="060df-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="060df-132">Popisuje funkce multithreadingu v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="060df-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060df-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="060df-133">See also</span></span>

- [<span data-ttu-id="060df-134">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="060df-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="060df-135">Události</span><span class="sxs-lookup"><span data-stu-id="060df-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="060df-136">Vzory návrhu asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="060df-136">Asynchronous Programming Design Patterns</span></span>](index.md)
