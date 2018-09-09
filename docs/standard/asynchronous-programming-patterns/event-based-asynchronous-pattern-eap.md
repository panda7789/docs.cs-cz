---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be4935d74affa227386aa6c63dad13e7e2f7d3dd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227906"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="818aa-102">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="818aa-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="818aa-103">Existuje mnoho způsobů, jak vystavení asynchronních funkcí pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="818aa-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="818aa-104">Asynchronní vzor založený na událostech předepisuje jedním ze způsobů pro třídy zobrazíte asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="818aa-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="818aa-105">Od verze rozhraní .NET Framework 4, poskytuje Task Parallel Library nový model pro asynchronní a paralelní programování.</span><span class="sxs-lookup"><span data-stu-id="818aa-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="818aa-106">Další informace najdete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [úkolově orientovanou asynchronní vzor (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="818aa-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="818aa-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="818aa-107">In This Section</span></span>

 [<span data-ttu-id="818aa-108">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="818aa-109">Popisuje, jak asynchronního vzoru založeného na událostech zpřístupní výhody vícevláknové aplikace při skrytí mnoho složitých problémů vyplývající vícevláknový návrhu.</span><span class="sxs-lookup"><span data-stu-id="818aa-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="818aa-110">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-111">Popisuje standardizovaný způsob balíček třídu, která obsahuje asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="818aa-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="818aa-112">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-113">Popisuje požadavky na vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="818aa-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="818aa-114">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-115">Popisuje, jak určit, kdy měli byste implementovat asynchronní vzor místo založený na událostech <xref:System.IAsyncResult> reprezentována vzor [asynchronního programovacího modelu (APM)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="818aa-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="818aa-116">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-117">Popisuje, jak vytvořit komponentu, která implementuje asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="818aa-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="818aa-118">Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, který zajistí, že součást správně funguje v jakékoli aplikačního modelu.</span><span class="sxs-lookup"><span data-stu-id="818aa-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="818aa-119">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-120">Popisuje, jak vytvořit klienta, který používá komponenty, která implementuje asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="818aa-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="818aa-121">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="818aa-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="818aa-122">Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="818aa-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="818aa-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="818aa-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="818aa-124">Popisuje <xref:System.ComponentModel.AsyncOperation> třída a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="818aa-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="818aa-125">Popisuje <xref:System.ComponentModel.AsyncOperationManager> třída a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="818aa-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="818aa-126">Popisuje <xref:System.ComponentModel.BackgroundWorker> komponenty a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="818aa-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="818aa-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="818aa-127">Related Sections</span></span>

 [<span data-ttu-id="818aa-128">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="818aa-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="818aa-129">Popisuje programovací model pro asynchronní a paralelní operace.</span><span class="sxs-lookup"><span data-stu-id="818aa-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="818aa-130">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="818aa-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="818aa-131">Popisuje funkce pro multithreading v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="818aa-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818aa-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="818aa-132">See also</span></span>

- [<span data-ttu-id="818aa-133">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="818aa-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)  
- [<span data-ttu-id="818aa-134">Události</span><span class="sxs-lookup"><span data-stu-id="818aa-134">Events</span></span>](../events/index.md)  
- [<span data-ttu-id="818aa-135">Návrhové vzory asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="818aa-135">Asynchronous Programming Design Patterns</span></span>](index.md)
