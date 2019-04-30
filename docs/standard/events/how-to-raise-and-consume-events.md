---
title: 'Postupy: Vyvolání a zpracování událostí'
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
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778687"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="40cec-102">Postupy: Vyvolání a zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="40cec-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="40cec-103">Příklady v tomto tématu ukazují, jak pracovat s událostmi.</span><span class="sxs-lookup"><span data-stu-id="40cec-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="40cec-104">Obsahují příklady <xref:System.EventHandler> delegovat, <xref:System.EventHandler%601> delegáta a vlastního delegáta pro ilustraci událostí, s daty a bez nich.</span><span class="sxs-lookup"><span data-stu-id="40cec-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="40cec-105">Příklady používají pojmy, které jsou popsané v [události](../../../docs/standard/events/index.md) článku.</span><span class="sxs-lookup"><span data-stu-id="40cec-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40cec-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40cec-106">Example</span></span>  
 <span data-ttu-id="40cec-107">První příklad ukazuje, jak vyvolat a zpracovat událost, která neobsahuje data.</span><span class="sxs-lookup"><span data-stu-id="40cec-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="40cec-108">Obsahuje třídu s názvem `Counter` , která má událost s názvem `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="40cec-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="40cec-109">Tato událost je aktivována, když hodnota čítače rovná nebo překračuje prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40cec-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="40cec-110"><xref:System.EventHandler> Delegát je přidruženo k události, protože nejsou k dispozici žádná data události.</span><span class="sxs-lookup"><span data-stu-id="40cec-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="40cec-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="40cec-111">Example</span></span>  
 <span data-ttu-id="40cec-112">Následující příklad ukazuje, jak vyvolat a zpracovat událost, která poskytuje data.</span><span class="sxs-lookup"><span data-stu-id="40cec-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="40cec-113"><xref:System.EventHandler%601> Delegát je přidruženo k události, a je k dispozici instance datového objektu vlastní události.</span><span class="sxs-lookup"><span data-stu-id="40cec-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="40cec-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="40cec-114">Example</span></span>  
 <span data-ttu-id="40cec-115">Následující příklad ukazuje, jak deklarovat delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="40cec-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="40cec-116">Delegát se nazývá `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="40cec-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="40cec-117">Jde jen o ukázku.</span><span class="sxs-lookup"><span data-stu-id="40cec-117">This is just an illustration.</span></span> <span data-ttu-id="40cec-118">Obvykle není nutné deklarovat delegáta pro událost, protože můžete použít buď <xref:System.EventHandler> nebo <xref:System.EventHandler%601> delegovat.</span><span class="sxs-lookup"><span data-stu-id="40cec-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="40cec-119">By měla deklarovat delegáta pouze ve výjimečných případech, jako je například zpřístupnění vaší třídy staršímu kódu, který nemůže používat obecné typy.</span><span class="sxs-lookup"><span data-stu-id="40cec-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="40cec-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40cec-120">See also</span></span>

- [<span data-ttu-id="40cec-121">Události</span><span class="sxs-lookup"><span data-stu-id="40cec-121">Events</span></span>](../../../docs/standard/events/index.md)
