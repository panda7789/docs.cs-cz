---
title: Události (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 5b844b20ac62b4cbc2a73931eecab95f22b4b1de
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199440"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="0d0d9-102">Události (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0d0d9-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="0d0d9-103">Události umožňují [třída](../../../csharp/language-reference/keywords/class.md) nebo objektům upozornit ostatní třídy nebo objektů, dojde-li něco, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="0d0d9-104">Třída, která odesílá (nebo *vyvolá*) události je volána *vydavatele* a třídy, které přijímají (nebo *zpracování*) události se nazývají *předplatitele* .</span><span class="sxs-lookup"><span data-stu-id="0d0d9-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="0d0d9-105">V typické aplikaci C# Windows Forms nebo Web se přihlásíte k odběru události vyvolané službou ovládací prvky jako tlačítka a pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="0d0d9-106">Visual C# integrované vývojové prostředí (IDE) můžete procházet události, které publikuje ovládací prvek a vyberte ty, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="0d0d9-107">Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód, který se k události registrovat.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="0d0d9-108">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="0d0d9-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="0d0d9-109">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="0d0d9-109">Events Overview</span></span>  
 <span data-ttu-id="0d0d9-110">Události mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0d0d9-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="0d0d9-111">Vydavatel Určuje, kdy je vyvolána událost; předplatitele určit, jaká akce se provede v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="0d0d9-112">Událost může mít několik předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="0d0d9-113">Odběratele můžete zpracování více událostí z více vydavatelé.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="0d0d9-114">Nikdy jsou vyvolány události, které mají žádné předplatitele.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="0d0d9-115">Události se obvykle používají k signalizaci uživatelské akce, jako je kliknutí na tlačítko nebo nabídku v grafickém uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="0d0d9-116">Pokud má událost několik předplatitelů, obslužné rutiny událostí jsou vyvolala synchronně, když je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="0d0d9-117">K vyvolání události asynchronně, naleznete v tématu [voláním synchronní metody asynchronně](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="0d0d9-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="0d0d9-118">V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd, události jsou založeny na <xref:System.EventHandler> delegáta a <xref:System.EventArgs> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0d0d9-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d0d9-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0d0d9-119">Related Sections</span></span>  
 <span data-ttu-id="0d0d9-120">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="0d0d9-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0d0d9-121">Postupy: Přihlášení a odhlášení odběru událostí</span><span class="sxs-lookup"><span data-stu-id="0d0d9-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="0d0d9-122">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d0d9-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="0d0d9-123">Postupy: Vyvolávání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="0d0d9-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="0d0d9-124">Postupy: implementace událostí rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d0d9-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="0d0d9-125">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="0d0d9-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="0d0d9-126">Postupy: Použití slovníku k ukládání instancí událostí</span><span class="sxs-lookup"><span data-stu-id="0d0d9-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="0d0d9-127">Postupy: Implementace vlastních přístupových objektů událostí</span><span class="sxs-lookup"><span data-stu-id="0d0d9-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="0d0d9-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d0d9-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="0d0d9-129">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="0d0d9-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="0d0d9-130">[Delegáty, události a výrazy Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="0d0d9-130">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="0d0d9-131">[Delegáti a události](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) v [Learning C# 3.0: Master Základy C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="0d0d9-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0d9-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d0d9-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="0d0d9-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0d0d9-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0d0d9-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="0d0d9-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="0d0d9-135">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d0d9-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="0d0d9-136">Vícevláknové programování s asynchronním vzorem založeným na událostech</span><span class="sxs-lookup"><span data-stu-id="0d0d9-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
