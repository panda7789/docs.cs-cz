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
ms.openlocfilehash: 4d0b24b8a6f1b914745d819b90b973752e32447c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279955"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="d7416-102">Postupy: Vyvolávání a zpracovávání událostí</span><span class="sxs-lookup"><span data-stu-id="d7416-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="d7416-103">Příklady v tomto tématu ukazují, jak pracovat s událostmi.</span><span class="sxs-lookup"><span data-stu-id="d7416-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="d7416-104">Obsahují příklady <xref:System.EventHandler> delegáta, <xref:System.EventHandler%601> delegáta a vlastního delegáta pro ilustraci událostí s daty a bez nich.</span><span class="sxs-lookup"><span data-stu-id="d7416-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="d7416-105">Příklady používají koncepty popsané v článku [události](index.md) .</span><span class="sxs-lookup"><span data-stu-id="d7416-105">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7416-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7416-106">Example</span></span>  
 <span data-ttu-id="d7416-107">První příklad ukazuje, jak vyvolat a zpracovat událost, která nemá data.</span><span class="sxs-lookup"><span data-stu-id="d7416-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="d7416-108">Obsahuje třídu s názvem `Counter` , která má událost s názvem `ThresholdReached` .</span><span class="sxs-lookup"><span data-stu-id="d7416-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="d7416-109">Tato událost se vyvolá, když je hodnota čítače rovna nebo přesahuje prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d7416-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="d7416-110"><xref:System.EventHandler>Delegát je přidružen k události, protože nejsou k dispozici žádná data události.</span><span class="sxs-lookup"><span data-stu-id="d7416-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="d7416-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7416-111">Example</span></span>  
 <span data-ttu-id="d7416-112">Další příklad ukazuje, jak vyvolat a zpracovat událost, která poskytuje data.</span><span class="sxs-lookup"><span data-stu-id="d7416-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="d7416-113"><xref:System.EventHandler%601>Delegát je přidružen k události a je k dispozici instance vlastního datového objektu události.</span><span class="sxs-lookup"><span data-stu-id="d7416-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="d7416-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7416-114">Example</span></span>  
 <span data-ttu-id="d7416-115">Další příklad ukazuje, jak deklarovat delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="d7416-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="d7416-116">Delegát má název `ThresholdReachedEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="d7416-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="d7416-117">Tohle je jenom ilustrace.</span><span class="sxs-lookup"><span data-stu-id="d7416-117">This is just an illustration.</span></span> <span data-ttu-id="d7416-118">Obvykle není nutné deklarovat delegáta pro událost, protože můžete použít buď <xref:System.EventHandler> <xref:System.EventHandler%601> delegáta, nebo.</span><span class="sxs-lookup"><span data-stu-id="d7416-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="d7416-119">Delegáta byste měli deklarovat pouze ve výjimečných případech, jako je například zpřístupnění třídy staršímu kódu, který nemůže používat obecné typy.</span><span class="sxs-lookup"><span data-stu-id="d7416-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d7416-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7416-120">See also</span></span>

- [<span data-ttu-id="d7416-121">Události</span><span class="sxs-lookup"><span data-stu-id="d7416-121">Events</span></span>](index.md)
