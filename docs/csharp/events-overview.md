---
title: Úvod k událostem
description: Další informace o události v .NET Core a naše cíle návrhu jazyk pro události se v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 2a2230ea5fba1b0cd5b13319677965e7a776549e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213471"
---
# <a name="introduction-to-events"></a><span data-ttu-id="83300-103">Úvod k událostem</span><span class="sxs-lookup"><span data-stu-id="83300-103">Introduction to Events</span></span>

[<span data-ttu-id="83300-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="83300-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="83300-105">Události jsou jako delegáti, *pozdní vazby* mechanismus.</span><span class="sxs-lookup"><span data-stu-id="83300-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="83300-106">Ve skutečnosti události jsou postavené na jazyková podpora pro delegáti.</span><span class="sxs-lookup"><span data-stu-id="83300-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="83300-107">Události jsou způsob, jak k objektu pro všesměrové vysílání (pro všechny dotčené komponenty v systému), že něco došlo.</span><span class="sxs-lookup"><span data-stu-id="83300-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="83300-108">Všechny ostatní součásti, které se mohou přihlásit k události a být upozorněni, když je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="83300-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="83300-109">Pravděpodobně jste použili události v některé z vaší programování.</span><span class="sxs-lookup"><span data-stu-id="83300-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="83300-110">Mnoho grafické systémy mají model událostí k interakci s uživatelem sestavy.</span><span class="sxs-lookup"><span data-stu-id="83300-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="83300-111">Tyto události by sestavy pohybu myši, stisknutí tlačítek a podobné interakce.</span><span class="sxs-lookup"><span data-stu-id="83300-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="83300-112">Který je jedním nejběžnější, ale určitě ne jediný scénář, kdy se používá události.</span><span class="sxs-lookup"><span data-stu-id="83300-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="83300-113">Můžete definovat události, které by měl být aktivována pro vaše třídy.</span><span class="sxs-lookup"><span data-stu-id="83300-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="83300-114">Při práci s událostmi je, že existuje jedna důležitý aspekt nemusí být libovolný objekt zaregistrovat pro určitá událost.</span><span class="sxs-lookup"><span data-stu-id="83300-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="83300-115">Musíte napsat kód tak, aby nevyvolá události při žádné moduly pro naslouchání jsou nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="83300-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="83300-116">Odběr pro událost vytvoří také párování mezi dvěma objekty (zdroj události a jímky událostí).</span><span class="sxs-lookup"><span data-stu-id="83300-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="83300-117">Je potřeba zajistit, že jímky událostí odhlásí zdroj událostí, když už máte zájem o události.</span><span class="sxs-lookup"><span data-stu-id="83300-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="83300-118">Cíle návrhu pro podporu událostí</span><span class="sxs-lookup"><span data-stu-id="83300-118">Design Goals for Event Support</span></span>

<span data-ttu-id="83300-119">Návrh jazyk pro události cílem těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="83300-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="83300-120">Nejprve povolte minimálními párování mezi zdroje událostí a jímky událostí.</span><span class="sxs-lookup"><span data-stu-id="83300-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="83300-121">Tyto dvě součásti nemusí být zapsané ve stejné organizaci a může být aktualizován i na uvidíte úplně jiné plány.</span><span class="sxs-lookup"><span data-stu-id="83300-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="83300-122">Za druhé musí být velmi jednoduché k odběru události a zrušení této stejnou událost odběru.</span><span class="sxs-lookup"><span data-stu-id="83300-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="83300-123">A nakonec zdroje událostí by měly podporovat více odběrateli událostí.</span><span class="sxs-lookup"><span data-stu-id="83300-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="83300-124">Také by měly podporovat, s žádné události odběratele připojen.</span><span class="sxs-lookup"><span data-stu-id="83300-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="83300-125">Uvidíte, že cíle pro události jsou velmi podobné cíle pro delegáti.</span><span class="sxs-lookup"><span data-stu-id="83300-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="83300-126">To je důvod, proč jazyková podpora událostí je založen na jazyková podpora delegáta.</span><span class="sxs-lookup"><span data-stu-id="83300-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="83300-127">Jazyková podpora pro události</span><span class="sxs-lookup"><span data-stu-id="83300-127">Language Support for Events</span></span>

<span data-ttu-id="83300-128">Syntaxe pro definování události a přihlášení k odběru nebo Odhlašujete události je rozšíření syntaxe delegáti.</span><span class="sxs-lookup"><span data-stu-id="83300-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="83300-129">K definování událost použijete `event` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="83300-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="83300-130">Typ události (`EventHandler<FileListArgs>` v tomto příkladu), musí být typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="83300-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="83300-131">Existuje několik smluv, které byste měli postupovat při deklarování událost.</span><span class="sxs-lookup"><span data-stu-id="83300-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="83300-132">Obvykle má tento typ delegáta události void vrátit.</span><span class="sxs-lookup"><span data-stu-id="83300-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="83300-133">Deklarace událostí musí být operaci nebo frázi operaci.</span><span class="sxs-lookup"><span data-stu-id="83300-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="83300-134">Pokud událost sestavy něco, co se stalo, použijte minulost (jako v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="83300-134">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="83300-135">Použít operaci přítomném (například `Closing`) tak, aby odesílaly něco, co dojde.</span><span class="sxs-lookup"><span data-stu-id="83300-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="83300-136">Pomocí přítomném často označuje, že třídě podporuje nějaký druh přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="83300-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="83300-137">Jeden z nejběžnějších scénářů je podpora zrušení.</span><span class="sxs-lookup"><span data-stu-id="83300-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="83300-138">Například `Closing` události může zahrnovat argument, který může naznačovat, pokud by měl zavřít operace pokračovat, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="83300-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="83300-139">V jiných scénářích může povolit volající chcete upravit chování pomocí aktualizace vlastností argumenty událostí.</span><span class="sxs-lookup"><span data-stu-id="83300-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="83300-140">Může vyvolat událost označující navrhované další akci, kterou bude trvat algoritmu.</span><span class="sxs-lookup"><span data-stu-id="83300-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="83300-141">Obslužné rutiny události může vyžádá různé akce úpravou vlastnosti argumentu události.</span><span class="sxs-lookup"><span data-stu-id="83300-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="83300-142">Když chcete k vyvolání události, volání obslužných rutin událostí pomocí syntaxe vyvolání delegáta:</span><span class="sxs-lookup"><span data-stu-id="83300-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="83300-143">Jak je popsáno v části na [delegáti](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="83300-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="83300-144">operátor usnadňuje Ujistěte se, že nebude pokoušet o vyvolat událost, pokud nejsou žádné odběratele, kteří mají tuto událost.</span><span class="sxs-lookup"><span data-stu-id="83300-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="83300-145">Přihlášení k odběru události pomocí `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="83300-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="83300-146">Metoda obslužná rutina obvykle představuje předponu "Na" následuje název události, jako v příkladu nahoře.</span><span class="sxs-lookup"><span data-stu-id="83300-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="83300-147">Odhlásit pomocí `-=` operátor:</span><span class="sxs-lookup"><span data-stu-id="83300-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="83300-148">Je důležité si uvědomit, že I deklarovaný místní proměnné pro výraz, který představuje obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="83300-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="83300-149">Který zajišťuje odebere unsubscribe obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="83300-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="83300-150">Pokud jste použili tělo výrazu lambda, se pokoušíte odebrat obslužnou rutinu, která nikdy nebyl přidán, který se nic nestane.</span><span class="sxs-lookup"><span data-stu-id="83300-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="83300-151">V další článek budete Další informace o typických událostí vzory a různých změn v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="83300-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="83300-152">Next</span><span class="sxs-lookup"><span data-stu-id="83300-152">Next</span></span>](event-pattern.md)
