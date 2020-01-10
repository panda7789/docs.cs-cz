---
title: Události – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712309"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="873d7-102">Události (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="873d7-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="873d7-103">Události umožňují [třídě](../../language-reference/keywords/class.md) nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu.</span><span class="sxs-lookup"><span data-stu-id="873d7-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="873d7-104">Třída, která odesílá (nebo *vyvolává*) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo *zpracovávají*) událost se nazývají *předplatitelé*.</span><span class="sxs-lookup"><span data-stu-id="873d7-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="873d7-105">V typické C# model Windows Forms nebo webové aplikaci se přihlásíte k odběru událostí vyvolaných ovládacími prvky, jako jsou tlačítka a seznamy.</span><span class="sxs-lookup"><span data-stu-id="873d7-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="873d7-106">Pomocí integrovaného vývojového C# prostředí (IDE) jazyka Visual můžete procházet události, které ovládací prvek publikuje, a vybrat ty, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="873d7-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="873d7-107">Rozhraní IDE poskytuje snadný způsob, jak automaticky přidat prázdnou metodu obslužné rutiny události a kód pro přihlášení k odběru události.</span><span class="sxs-lookup"><span data-stu-id="873d7-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="873d7-108">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](./how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="873d7-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="873d7-109">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="873d7-109">Events Overview</span></span>  
 <span data-ttu-id="873d7-110">Události mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="873d7-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="873d7-111">Vydavatel určí, kdy se událost vyvolá; Předplatitelé určují, jakou akci provádí v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="873d7-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="873d7-112">Událost může mít více odběratelů.</span><span class="sxs-lookup"><span data-stu-id="873d7-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="873d7-113">Předplatitel může zpracovávat více událostí od více vydavatelů.</span><span class="sxs-lookup"><span data-stu-id="873d7-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="873d7-114">Události, které nemají žádné předplatitele, nejsou nikdy vyvolány.</span><span class="sxs-lookup"><span data-stu-id="873d7-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="873d7-115">Události se obvykle používají k signalizaci uživatelských akcí, jako například kliknutí na tlačítko nebo výběry nabídky v grafickém uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="873d7-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="873d7-116">Pokud má událost více odběratelů, obslužné rutiny události jsou vyvolány synchronně při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="873d7-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="873d7-117">Chcete-li vyvolat události asynchronně, přečtěte si téma [asynchronní volání synchronních metod](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="873d7-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="873d7-118">V knihovně tříd .NET Framework jsou události založeny na delegátu <xref:System.EventHandler> a základní třídě <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="873d7-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="873d7-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="873d7-119">Related Sections</span></span>  
 <span data-ttu-id="873d7-120">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="873d7-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="873d7-121">Přihlášení a odhlášení odběru událostí</span><span class="sxs-lookup"><span data-stu-id="873d7-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="873d7-122">Jak publikovat události, které jsou v souladu s pokyny pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="873d7-122">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="873d7-123">Postup vyvolání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="873d7-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="873d7-124">Postup implementace událostí rozhraní</span><span class="sxs-lookup"><span data-stu-id="873d7-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="873d7-125">Implementace vlastních přístupových objektů událostí</span><span class="sxs-lookup"><span data-stu-id="873d7-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="873d7-126">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="873d7-126">C# Language Specification</span></span>  

<span data-ttu-id="873d7-127">Další informace najdete v tématu [události](~/_csharplang/spec/classes.md#events) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="873d7-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="873d7-128">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="873d7-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="873d7-129">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="873d7-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="873d7-130">[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: více než 250 řešení pro C# 3,0 programátorů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="873d7-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="873d7-131">[Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) ve [studiu C# 3,0: hlavní základy pro C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="873d7-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873d7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="873d7-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="873d7-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="873d7-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="873d7-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="873d7-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="873d7-135">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="873d7-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
