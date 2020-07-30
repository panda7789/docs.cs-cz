---
title: Události – Průvodce programováním v C#
description: Další informace o událostech. Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 3160d1e381c6cb3af0f017538f9555b3fded9910
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302071"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="cb70d-104">Události (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cb70d-104">Events (C# Programming Guide)</span></span>
<span data-ttu-id="cb70d-105">Události umožňují [třídě](../../language-reference/keywords/class.md) nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu.</span><span class="sxs-lookup"><span data-stu-id="cb70d-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="cb70d-106">Třída, která odesílá (nebo *vyvolává*) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo *zpracovávají*) událost se nazývají *předplatitelé*.</span><span class="sxs-lookup"><span data-stu-id="cb70d-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="cb70d-107">V typické model Windows Forms v C# nebo webové aplikaci se přihlásíte k odběru událostí vyvolaných ovládacími prvky, jako jsou tlačítka a seznamy.</span><span class="sxs-lookup"><span data-stu-id="cb70d-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="cb70d-108">Pomocí integrovaného vývojového prostředí (IDE) jazyka Visual C# můžete procházet události, které ovládací prvek publikuje, a vybrat ty, které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="cb70d-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="cb70d-109">Rozhraní IDE poskytuje snadný způsob, jak automaticky přidat prázdnou metodu obslužné rutiny události a kód pro přihlášení k odběru události.</span><span class="sxs-lookup"><span data-stu-id="cb70d-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="cb70d-110">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](./how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="cb70d-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="cb70d-111">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="cb70d-111">Events Overview</span></span>  
 <span data-ttu-id="cb70d-112">Události mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cb70d-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="cb70d-113">Vydavatel určí, kdy se událost vyvolá; Předplatitelé určují, jakou akci provádí v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="cb70d-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="cb70d-114">Událost může mít více odběratelů.</span><span class="sxs-lookup"><span data-stu-id="cb70d-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="cb70d-115">Předplatitel může zpracovávat více událostí od více vydavatelů.</span><span class="sxs-lookup"><span data-stu-id="cb70d-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="cb70d-116">Události, které nemají žádné předplatitele, nejsou nikdy vyvolány.</span><span class="sxs-lookup"><span data-stu-id="cb70d-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="cb70d-117">Události se obvykle používají k signalizaci uživatelských akcí, jako například kliknutí na tlačítko nebo výběry nabídky v grafickém uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cb70d-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="cb70d-118">Pokud má událost více odběratelů, obslužné rutiny události jsou vyvolány synchronně při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="cb70d-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="cb70d-119">Chcete-li vyvolat události asynchronně, přečtěte si téma [asynchronní volání synchronních metod](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="cb70d-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="cb70d-120">V knihovně tříd .NET Framework jsou události založeny na <xref:System.EventHandler> delegátu a <xref:System.EventArgs> základní třídě.</span><span class="sxs-lookup"><span data-stu-id="cb70d-120">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cb70d-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cb70d-121">Related Sections</span></span>  
 <span data-ttu-id="cb70d-122">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="cb70d-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="cb70d-123">Jak přihlásit a odhlásit odběr událostí</span><span class="sxs-lookup"><span data-stu-id="cb70d-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="cb70d-124">Jak publikovat události, které jsou v souladu s pokyny pro .NET</span><span class="sxs-lookup"><span data-stu-id="cb70d-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="cb70d-125">Jak vyvolávat události základní třídy v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="cb70d-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="cb70d-126">Jak implementovat události rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb70d-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="cb70d-127">Jak implementovat vlastní přístupové objekty událostí</span><span class="sxs-lookup"><span data-stu-id="cb70d-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="cb70d-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb70d-128">C# Language Specification</span></span>  

<span data-ttu-id="cb70d-129">Další informace naleznete v tématu [události](~/_csharplang/spec/classes.md#events) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="cb70d-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="cb70d-130">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cb70d-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="cb70d-131">Doporučené kapitoly knihy</span><span class="sxs-lookup"><span data-stu-id="cb70d-131">Featured Book Chapters</span></span>  
 <span data-ttu-id="cb70d-132">[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [C# 3,0 kuchařka, třetí edice: více než 250 řešení pro c# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="cb70d-132">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="cb70d-133">[Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [kurzu C# 3,0: hlavní základy jazyka c# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="cb70d-133">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb70d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb70d-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="cb70d-135">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="cb70d-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cb70d-136">Delegáti</span><span class="sxs-lookup"><span data-stu-id="cb70d-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="cb70d-137">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb70d-137">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
