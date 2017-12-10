---
title: "Události (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ab40de46bf198cf683ec4847a42d88b3d4807e0
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="776e0-102">Události (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="776e0-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="776e0-103">Povolit události [třídy](../../../csharp/language-reference/keywords/class.md) nebo objekt, který chcete upozornit jiné třídy nebo objekty něco zájmu případě.</span><span class="sxs-lookup"><span data-stu-id="776e0-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="776e0-104">Třídu, která odešle (nebo *vyvolá*) událost se nazývá *vydavatele* a třídy, které přijímají (nebo *zpracování*) se označují jako událost *odběratele* .</span><span class="sxs-lookup"><span data-stu-id="776e0-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="776e0-105">V typické aplikaci Windows Forms C# nebo webové přihlášení k odběru události vyvolané ovládacími prvky, jako jsou tlačítka a seznamy.</span><span class="sxs-lookup"><span data-stu-id="776e0-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="776e0-106">Můžete použít [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrované vývojové prostředí (IDE) a procházejte události, které publikuje ovládacího prvku a vyberte ty, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="776e0-106">You can use the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="776e0-107">Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód k odběru události.</span><span class="sxs-lookup"><span data-stu-id="776e0-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="776e0-108">Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="776e0-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="776e0-109">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="776e0-109">Events Overview</span></span>  
 <span data-ttu-id="776e0-110">Události mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="776e0-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="776e0-111">Vydavatel Určuje, kdy je vyvolána událost; odběratele určit, jaké akce se provede v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="776e0-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="776e0-112">Událost může mít více odběrateli.</span><span class="sxs-lookup"><span data-stu-id="776e0-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="776e0-113">Odběratel může zpracovat více událostí z více vydavatele.</span><span class="sxs-lookup"><span data-stu-id="776e0-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="776e0-114">Události, které mají žádné Odběratelé, kteří jsou nikdy vyvolána.</span><span class="sxs-lookup"><span data-stu-id="776e0-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="776e0-115">Události jsou obvykle používány signál uživatele akcí, například kliknutí na tlačítko nebo nabídky výběrů v grafickém uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="776e0-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="776e0-116">Událost má více odběrateli, obslužné rutiny událostí jsou vyvolány synchronně, když událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="776e0-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="776e0-117">Vyvolání událostí asynchronně, najdete v tématu [volání synchronních metod asynchronně](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="776e0-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="776e0-118">V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd události jsou založené na <xref:System.EventHandler> delegovat a <xref:System.EventArgs> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="776e0-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="776e0-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="776e0-119">Related Sections</span></span>  
 <span data-ttu-id="776e0-120">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="776e0-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="776e0-121">Postupy: přihlášení a odhlášení odběru událostí</span><span class="sxs-lookup"><span data-stu-id="776e0-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="776e0-122">Postupy: publikování událostí odpovídajících směrnicím rozhraní .NET Framework pokyny</span><span class="sxs-lookup"><span data-stu-id="776e0-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="776e0-123">Postupy: vyvolávání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="776e0-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="776e0-124">Postupy: implementace událostí rozhraní</span><span class="sxs-lookup"><span data-stu-id="776e0-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="776e0-125">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="776e0-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="776e0-126">Postupy: použití slovníku k ukládání instancí událostí</span><span class="sxs-lookup"><span data-stu-id="776e0-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="776e0-127">Postupy: implementace vlastních přístupových objektů událostí</span><span class="sxs-lookup"><span data-stu-id="776e0-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="776e0-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="776e0-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="776e0-129">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="776e0-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="776e0-130">[Výrazy Lambda, delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195395) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v jazyce C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="776e0-130">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="776e0-131">[Delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195418) v [Learning C# 3.0: Master Základy C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="776e0-131">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776e0-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="776e0-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="776e0-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="776e0-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="776e0-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="776e0-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="776e0-135">Vytváření obslužných rutin událostí v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776e0-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="776e0-136">Vícevláknové programování s asynchronním vzorem založený na událostech</span><span class="sxs-lookup"><span data-stu-id="776e0-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
