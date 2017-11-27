---
title: "Úvod k událostem"
description: "Další informace o události v .NET Core a naše cíle návrhu jazyk pro události se v tomto přehledu."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: f81c2d9fc2ec69c295485fe06029b5de65335db0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-events"></a><span data-ttu-id="6e738-104">Úvod k událostem</span><span class="sxs-lookup"><span data-stu-id="6e738-104">Introduction to Events</span></span>

[<span data-ttu-id="6e738-105">Předchozí</span><span class="sxs-lookup"><span data-stu-id="6e738-105">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="6e738-106">Události jsou jako delegáti, *pozdní vazby* mechanismus.</span><span class="sxs-lookup"><span data-stu-id="6e738-106">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="6e738-107">Ve skutečnosti události jsou postavené na jazyková podpora pro delegáti.</span><span class="sxs-lookup"><span data-stu-id="6e738-107">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="6e738-108">Události jsou způsob, jak k objektu pro všesměrové vysílání (pro všechny dotčené komponenty v systému), že něco došlo.</span><span class="sxs-lookup"><span data-stu-id="6e738-108">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="6e738-109">Všechny ostatní součásti, které se mohou přihlásit k události a být upozorněni, když je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="6e738-109">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="6e738-110">Pravděpodobně jste použili události v některé z vaší programování.</span><span class="sxs-lookup"><span data-stu-id="6e738-110">You've probably used events in some of your programming.</span></span> <span data-ttu-id="6e738-111">Mnoho grafické systémy mají model událostí k interakci s uživatelem sestavy.</span><span class="sxs-lookup"><span data-stu-id="6e738-111">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="6e738-112">Tyto události by sestavy pohybu myši, stisknutí tlačítek a podobné interakce.</span><span class="sxs-lookup"><span data-stu-id="6e738-112">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="6e738-113">Který je jedním nejběžnější, ale určitě ne jediný scénář, kdy se používá události.</span><span class="sxs-lookup"><span data-stu-id="6e738-113">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="6e738-114">Můžete definovat události, které by měl být aktivována pro vaše třídy.</span><span class="sxs-lookup"><span data-stu-id="6e738-114">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="6e738-115">Při práci s událostmi je, že existuje jedna důležitý aspekt nemusí být libovolný objekt zaregistrovat pro určitá událost.</span><span class="sxs-lookup"><span data-stu-id="6e738-115">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="6e738-116">Musíte napsat kód tak, aby nevyvolá události při žádné moduly pro naslouchání jsou nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="6e738-116">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="6e738-117">Odběr pro událost vytvoří také párování mezi dvěma objekty (zdroj události a jímky událostí).</span><span class="sxs-lookup"><span data-stu-id="6e738-117">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="6e738-118">Je potřeba zajistit, že jímky událostí odhlásí zdroj událostí, když už máte zájem o události.</span><span class="sxs-lookup"><span data-stu-id="6e738-118">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="6e738-119">Cíle návrhu pro podporu událostí</span><span class="sxs-lookup"><span data-stu-id="6e738-119">Design Goals for Event Support</span></span>

<span data-ttu-id="6e738-120">Návrh jazyk pro události cílem těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="6e738-120">The language design for events targets these goals.</span></span>

<span data-ttu-id="6e738-121">Nejprve povolte minimálními párování mezi zdroje událostí a jímky událostí.</span><span class="sxs-lookup"><span data-stu-id="6e738-121">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="6e738-122">Tyto dvě součásti nemusí být zapsané ve stejné organizaci a může být aktualizován i na uvidíte úplně jiné plány.</span><span class="sxs-lookup"><span data-stu-id="6e738-122">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="6e738-123">Za druhé musí být velmi jednoduché k odběru události a zrušení této stejnou událost odběru.</span><span class="sxs-lookup"><span data-stu-id="6e738-123">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="6e738-124">A nakonec zdroje událostí by měly podporovat více odběrateli událostí.</span><span class="sxs-lookup"><span data-stu-id="6e738-124">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="6e738-125">Také by měly podporovat, s žádné události odběratele připojen.</span><span class="sxs-lookup"><span data-stu-id="6e738-125">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="6e738-126">Uvidíte, že cíle pro události jsou velmi podobné cíle pro delegáti.</span><span class="sxs-lookup"><span data-stu-id="6e738-126">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="6e738-127">To je důvod, proč jazyková podpora událostí je založen na jazyková podpora delegáta.</span><span class="sxs-lookup"><span data-stu-id="6e738-127">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="6e738-128">Jazyková podpora pro události</span><span class="sxs-lookup"><span data-stu-id="6e738-128">Language Support for Events</span></span>

<span data-ttu-id="6e738-129">Syntaxe pro definování události a přihlášení k odběru nebo Odhlašujete události je rozšíření syntaxe delegáti.</span><span class="sxs-lookup"><span data-stu-id="6e738-129">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="6e738-130">K definování událost použijete `event` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="6e738-130">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="6e738-131">Typ události (`EventHandler<FileListArgs>` v tomto příkladu), musí být typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="6e738-131">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="6e738-132">Existuje několik smluv, které byste měli postupovat při deklarování událost.</span><span class="sxs-lookup"><span data-stu-id="6e738-132">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="6e738-133">Obvykle má tento typ delegáta události void vrátit.</span><span class="sxs-lookup"><span data-stu-id="6e738-133">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="6e738-134">Deklarace událostí musí být operaci nebo frázi operaci.</span><span class="sxs-lookup"><span data-stu-id="6e738-134">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="6e738-135">Pokud událost sestavy něco, co se stalo, použijte minulost (jako v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="6e738-135">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="6e738-136">Použít operaci přítomném (například `Closing`) tak, aby odesílaly něco, co dojde.</span><span class="sxs-lookup"><span data-stu-id="6e738-136">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="6e738-137">Pomocí přítomném často označuje, že třídě podporuje nějaký druh přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="6e738-137">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="6e738-138">Jeden z nejběžnějších scénářů je podpora zrušení.</span><span class="sxs-lookup"><span data-stu-id="6e738-138">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="6e738-139">Například `Closing` události může zahrnovat argument, který může naznačovat, pokud by měl zavřít operace pokračovat, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6e738-139">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="6e738-140">V jiných scénářích může povolit volající chcete upravit chování pomocí aktualizace vlastností argumenty událostí.</span><span class="sxs-lookup"><span data-stu-id="6e738-140">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="6e738-141">Může vyvolat událost označující navrhované další akci, kterou bude trvat algoritmu.</span><span class="sxs-lookup"><span data-stu-id="6e738-141">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="6e738-142">Obslužné rutiny události může vyžádá různé akce úpravou vlastnosti argumentu události.</span><span class="sxs-lookup"><span data-stu-id="6e738-142">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="6e738-143">Když chcete k vyvolání události, volání obslužných rutin událostí pomocí syntaxe vyvolání delegáta:</span><span class="sxs-lookup"><span data-stu-id="6e738-143">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="6e738-144">Jak je popsáno v části na [delegáti](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="6e738-144">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="6e738-145">operátor usnadňuje Ujistěte se, že nebude pokoušet o vyvolat událost, pokud nejsou žádné odběratele, kteří mají tuto událost.</span><span class="sxs-lookup"><span data-stu-id="6e738-145">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="6e738-146">Přihlášení k odběru události pomocí `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6e738-146">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="6e738-147">Metoda obslužná rutina obvykle představuje předponu "Na" následuje název události, jako v příkladu nahoře.</span><span class="sxs-lookup"><span data-stu-id="6e738-147">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="6e738-148">Odhlásit pomocí `-=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6e738-148">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="6e738-149">Je důležité si uvědomit, že I deklarovaný místní proměnné pro výraz, který představuje obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6e738-149">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="6e738-150">Který zajišťuje odebere unsubscribe obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="6e738-150">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="6e738-151">Pokud jste použili tělo výrazu lambda, se pokoušíte odebrat obslužnou rutinu, která nikdy nebyl přidán, který se nic nestane.</span><span class="sxs-lookup"><span data-stu-id="6e738-151">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="6e738-152">V další článek budete Další informace o typických událostí vzory a různých změn v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6e738-152">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="6e738-153">Další</span><span class="sxs-lookup"><span data-stu-id="6e738-153">Next</span></span>](event-pattern.md)
