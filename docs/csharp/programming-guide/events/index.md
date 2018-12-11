---
title: Události - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 0745b0089de3b5fe9220f3ff2e0ccd4e2aba77f0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243566"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="bc936-102">Události (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bc936-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="bc936-103">Události umožňují [třída](../../../csharp/language-reference/keywords/class.md) nebo objektům upozornit ostatní třídy nebo objektů, dojde-li něco, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="bc936-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="bc936-104">Třída, která odesílá (nebo *vyvolá*) události je volána *vydavatele* a třídy, které přijímají (nebo *zpracování*) události se nazývají *předplatitele* .</span><span class="sxs-lookup"><span data-stu-id="bc936-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="bc936-105">V typické aplikaci C# Windows Forms nebo Web se přihlásíte k odběru události vyvolané službou ovládací prvky jako tlačítka a pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="bc936-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="bc936-106">Visual C# integrované vývojové prostředí (IDE) můžete procházet události, které publikuje ovládací prvek a vyberte ty, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="bc936-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="bc936-107">Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód, který se k události registrovat.</span><span class="sxs-lookup"><span data-stu-id="bc936-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="bc936-108">Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="bc936-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="bc936-109">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="bc936-109">Events Overview</span></span>  
 <span data-ttu-id="bc936-110">Události mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bc936-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="bc936-111">Vydavatel Určuje, kdy je vyvolána událost; předplatitele určit, jaká akce se provede v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="bc936-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="bc936-112">Událost může mít několik předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="bc936-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="bc936-113">Odběratele můžete zpracování více událostí z více vydavatelé.</span><span class="sxs-lookup"><span data-stu-id="bc936-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="bc936-114">Nikdy jsou vyvolány události, které mají žádné předplatitele.</span><span class="sxs-lookup"><span data-stu-id="bc936-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="bc936-115">Události se obvykle používají k signalizaci uživatelské akce, jako je kliknutí na tlačítko nebo nabídku v grafickém uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc936-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="bc936-116">Pokud má událost několik předplatitelů, obslužné rutiny událostí jsou vyvolala synchronně, když je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="bc936-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="bc936-117">K vyvolání události asynchronně, naleznete v tématu [voláním synchronní metody asynchronně](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="bc936-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="bc936-118">V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd, události jsou založeny na <xref:System.EventHandler> delegáta a <xref:System.EventArgs> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bc936-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bc936-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bc936-119">Related Sections</span></span>  
 <span data-ttu-id="bc936-120">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="bc936-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="bc936-121">Postupy: Přihlaste se k odběru a zrušit její odběr události</span><span class="sxs-lookup"><span data-stu-id="bc936-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="bc936-122">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="bc936-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="bc936-123">Postupy: Vyvolávání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="bc936-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="bc936-124">Postupy:  Implementace událostí rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc936-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="bc936-125">Postupy: Použití slovníku k Store instancí událostí</span><span class="sxs-lookup"><span data-stu-id="bc936-125">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="bc936-126">Postupy: Implementace vlastních přístupových objektů událostí</span><span class="sxs-lookup"><span data-stu-id="bc936-126">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bc936-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc936-127">C# Language Specification</span></span>  

<span data-ttu-id="bc936-128">Další informace najdete v tématu [události](~/_csharplang/spec/classes.md#events) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc936-128">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="bc936-129">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bc936-129">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="bc936-130">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="bc936-130">Featured Book Chapters</span></span>  
 <span data-ttu-id="bc936-131">[Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="bc936-131">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="bc936-132">[Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [učení C# 3.0: Hlavní základní informace o C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="bc936-132">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc936-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc936-133">See Also</span></span>

- <xref:System.EventHandler>  
- [<span data-ttu-id="bc936-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bc936-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bc936-135">Delegáti</span><span class="sxs-lookup"><span data-stu-id="bc936-135">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="bc936-136">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc936-136">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
