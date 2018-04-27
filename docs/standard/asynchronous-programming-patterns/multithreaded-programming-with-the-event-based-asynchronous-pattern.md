---
title: Vícevláknové programování s asynchronním vzorem založeným na událostech
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6d93e449877456e415ebd4d3490a7df99280e7e5
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="ae7dc-102">Vícevláknové programování s asynchronním vzorem založeným na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="ae7dc-103">Existuje několik způsobů, jak vystavit asynchronní funkce kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="ae7dc-104">Asynchronní vzor založený na událostech stanovuje doporučený způsob pro třídy nabídne asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae7dc-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ae7dc-105">In This Section</span></span>  
 [<span data-ttu-id="ae7dc-106">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="ae7dc-107">Popisuje, jak asynchronní vzor založený na událostech zpřístupní výhod vícevláknové aplikace při skrytí mnoho složitých problémů vyplývajících z více vláken návrhu.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="ae7dc-108">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ae7dc-109">Popisuje standardizovaného způsobu balíček třídy, která má asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="ae7dc-110">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ae7dc-111">Popisuje požadavky na vystavení asynchronní funkce podle asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="ae7dc-112">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ae7dc-113">Popisuje, jak určit, kdy by měl vybrat implementovat asynchronní vzor místo na základě událostí <xref:System.IAsyncResult> vzor.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="ae7dc-114">Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ae7dc-115">Ukazuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="ae7dc-116">Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, které zajišťuje, že součást funguje správně v rámci modelu všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="ae7dc-117">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="ae7dc-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ae7dc-118">Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ae7dc-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ae7dc-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="ae7dc-120">Popisuje <xref:System.ComponentModel.AsyncOperation> třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="ae7dc-121">Popisuje <xref:System.ComponentModel.AsyncOperationManager> třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ae7dc-122">Popisuje <xref:System.ComponentModel.BackgroundWorker> součásti a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ae7dc-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7dc-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae7dc-123">See Also</span></span>  
 [<span data-ttu-id="ae7dc-124">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="ae7dc-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="ae7dc-125">Události</span><span class="sxs-lookup"><span data-stu-id="ae7dc-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="ae7dc-126">Více vláken v součásti</span><span class="sxs-lookup"><span data-stu-id="ae7dc-126">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="ae7dc-127">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="ae7dc-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
