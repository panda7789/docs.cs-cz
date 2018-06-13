---
title: 'Postupy: Vyvolávání a zpracovávání událostí'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efeed61c5748a0a6ac731cdcfce1a110982b2941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572720"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="6ebaa-102">Postupy: Vyvolávání a zpracovávání událostí</span><span class="sxs-lookup"><span data-stu-id="6ebaa-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="6ebaa-103">V příkladech v tomto tématu ukazují, jak pracovat s událostmi.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="6ebaa-104">Patří mezi ně příklady <xref:System.EventHandler> delegovat, <xref:System.EventHandler%601> delegáta a vlastní delegáta, ke znázornění událostí s i bez data.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="6ebaa-105">Příklady použití konceptů popsaných v [události](../../../docs/standard/events/index.md) článku.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ebaa-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ebaa-106">Example</span></span>  
 <span data-ttu-id="6ebaa-107">V prvním příkladu ukazuje, jak vyvolávání a zpracovávání událost, která nemá data.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="6ebaa-108">Obsahuje třídy s názvem `Counter` s událost s názvem `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="6ebaa-109">Tato událost se vyvolá, když hodnota čítače se rovná nebo překračuje prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="6ebaa-110"><xref:System.EventHandler> Delegát je přidruženo k události, protože je k dispozici žádná data.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="6ebaa-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ebaa-111">Example</span></span>  
 <span data-ttu-id="6ebaa-112">Další příklad ukazuje, jak vyvolávání a zpracovávání událost, který poskytuje data.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="6ebaa-113"><xref:System.EventHandler%601> Delegát je přidruženo k události, a je k dispozici instance objektu dat vlastní události.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="6ebaa-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ebaa-114">Example</span></span>  
 <span data-ttu-id="6ebaa-115">Další příklad ukazuje, jak delegáta pro událost deklarovat.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="6ebaa-116">Delegát jmenuje `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="6ebaa-117">Toto je právě obrázek.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-117">This is just an illustration.</span></span> <span data-ttu-id="6ebaa-118">Obvykle není nutné deklarovat delegát pro událost, protože můžete použít buď <xref:System.EventHandler> nebo <xref:System.EventHandler%601> delegovat.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="6ebaa-119">Delegát pouze ve výjimečných případech, například zpřístupnění třídě starší verze kódu, které nemůže používat obecné typy by měly deklarovat.</span><span class="sxs-lookup"><span data-stu-id="6ebaa-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="6ebaa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ebaa-120">See Also</span></span>  
 [<span data-ttu-id="6ebaa-121">Události</span><span class="sxs-lookup"><span data-stu-id="6ebaa-121">Events</span></span>](../../../docs/standard/events/index.md)
