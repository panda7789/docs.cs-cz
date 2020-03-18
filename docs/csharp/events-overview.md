---
title: Úvod do událostí
description: Další informace o událostech v .NET Core a našich cílech návrhu jazyka pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146111"
---
# <a name="introduction-to-events"></a><span data-ttu-id="4b36c-103">Úvod do událostí</span><span class="sxs-lookup"><span data-stu-id="4b36c-103">Introduction to events</span></span>

[<span data-ttu-id="4b36c-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="4b36c-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="4b36c-105">Události jsou, stejně jako delegáti, *pozdní vazebný* mechanismus.</span><span class="sxs-lookup"><span data-stu-id="4b36c-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="4b36c-106">Ve skutečnosti jsou události postaveny na jazykové podpoře delegátů.</span><span class="sxs-lookup"><span data-stu-id="4b36c-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="4b36c-107">Události jsou způsob, jak objekt vysílat (pro všechny zúčastněné součásti v systému), že se něco stalo.</span><span class="sxs-lookup"><span data-stu-id="4b36c-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="4b36c-108">K odběru události se může přihlásit jakákoli jiná součást a být upozorněna, když je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="4b36c-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="4b36c-109">Pravděpodobně jste použili události v některých vašich programů.</span><span class="sxs-lookup"><span data-stu-id="4b36c-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="4b36c-110">Mnoho grafických systémů má model událostí pro hlášení interakce uživatele.</span><span class="sxs-lookup"><span data-stu-id="4b36c-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="4b36c-111">Tyto události by hlásit pohyb myši, stisknutí tlačítka a podobné interakce.</span><span class="sxs-lookup"><span data-stu-id="4b36c-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="4b36c-112">To je jeden z nejběžnějších, ale rozhodně ne jediný scénář, kde se používají události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="4b36c-113">Můžete definovat události, které by měly být vyvolány pro vaše třídy.</span><span class="sxs-lookup"><span data-stu-id="4b36c-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="4b36c-114">Jedním z důležitých úvah při práci s událostmi je, že nemusí být žádný objekt registrován pro konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="4b36c-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="4b36c-115">Je nutné napsat kód tak, aby nevyvolá události, když jsou nakonfigurovány žádné naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="4b36c-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="4b36c-116">Přihlášení k odběru události také vytvoří spojení mezi dvěma objekty (zdroj události a jímka událostí).</span><span class="sxs-lookup"><span data-stu-id="4b36c-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="4b36c-117">Je třeba zajistit, že jímky události odhlásí ze zdroje událostí, když již zájem o události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="4b36c-118">Cíle návrhu pro podporu událostí</span><span class="sxs-lookup"><span data-stu-id="4b36c-118">Design goals for event support</span></span>

<span data-ttu-id="4b36c-119">Návrh jazyka pro události cílí na tyto cíle:</span><span class="sxs-lookup"><span data-stu-id="4b36c-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="4b36c-120">Povolte velmi minimální párování mezi zdrojem událostí a jímkou událostí.</span><span class="sxs-lookup"><span data-stu-id="4b36c-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="4b36c-121">Tyto dvě součásti nemusí být napsány stejnou organizací a mohou být dokonce aktualizovány v úplně odlišných plánech.</span><span class="sxs-lookup"><span data-stu-id="4b36c-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="4b36c-122">Mělo by být velmi jednoduché přihlásit se k odběru události, a odhlásit se z tésamé události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="4b36c-123">Zdroje událostí by měly podporovat více odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="4b36c-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="4b36c-124">Měla by také podporovat bez připojených odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="4b36c-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="4b36c-125">Můžete vidět, že cíle pro události jsou velmi podobné cíle pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="4b36c-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="4b36c-126">Proto je podpora jazyka událostí postavena na jazykové podpoře delegáta.</span><span class="sxs-lookup"><span data-stu-id="4b36c-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="4b36c-127">Jazyková podpora pro akce</span><span class="sxs-lookup"><span data-stu-id="4b36c-127">Language support for events</span></span>

<span data-ttu-id="4b36c-128">Syntaxe pro definování událostí a přihlášení nebo odhlášení z událostí je rozšíření syntaxe pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="4b36c-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="4b36c-129">Chcete-li definovat událost, kterou použijete `event` klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="4b36c-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="4b36c-130">Typ události (`EventHandler<FileListArgs>` v tomto příkladu) musí být typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="4b36c-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="4b36c-131">Existuje několik konvencí, které byste měli dodržovat při deklarování události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="4b36c-132">Typ delegáta události má obvykle neplatné vrácení.</span><span class="sxs-lookup"><span data-stu-id="4b36c-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="4b36c-133">Deklarace událostí by měla být sloveso nebo slovesná fráze.</span><span class="sxs-lookup"><span data-stu-id="4b36c-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="4b36c-134">Pokud událost nahlásí něco, co se stalo, použijte minulý čas.</span><span class="sxs-lookup"><span data-stu-id="4b36c-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="4b36c-135">Pomocí aktuálního slovesa `Closing`(například) nahlaste něco, co se má stát.</span><span class="sxs-lookup"><span data-stu-id="4b36c-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="4b36c-136">Často pomocí přítomný čas označuje, že vaše třída podporuje nějaký druh přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="4b36c-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="4b36c-137">Jedním z nejběžnějších scénářů je podpora zrušení.</span><span class="sxs-lookup"><span data-stu-id="4b36c-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="4b36c-138">`Closing` Událost může například obsahovat argument, který by naznačoval, zda má operace zavřít pokračovat, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="4b36c-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="4b36c-139">Jiné scénáře mohou umožnit volajícím změnit chování aktualizací vlastností argumentů události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="4b36c-140">Můžete vyvolat událost označující navrhovanou další akci, kterou algoritmus provede.</span><span class="sxs-lookup"><span data-stu-id="4b36c-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="4b36c-141">Obslužná rutina události může nařídit jinou akci změnou vlastností argumentu události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="4b36c-142">Pokud chcete vyvolat událost, volání obslužné rutiny události pomocí syntaxe vyvolání delegáta:</span><span class="sxs-lookup"><span data-stu-id="4b36c-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="4b36c-143">Jak je popsáno v sekci o [delegátech](delegates-patterns.md), ?.</span><span class="sxs-lookup"><span data-stu-id="4b36c-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="4b36c-144">operátor usnadňuje zajistit, že se nepokusíte vyvolat událost, pokud neexistují žádné předplatitele této události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>

<span data-ttu-id="4b36c-145">K odběru události se `+=` přihlásíte pomocí operátoru:</span><span class="sxs-lookup"><span data-stu-id="4b36c-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="4b36c-146">Metoda obslužné rutiny má obvykle předponu "On" následovanou názvem události, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="4b36c-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="4b36c-147">Z odběru se `-=` odhlásíte pomocí operátora:</span><span class="sxs-lookup"><span data-stu-id="4b36c-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="4b36c-148">Je důležité si uvědomit, že jsem deklaroval místní proměnnou pro výraz, který představuje obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="4b36c-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="4b36c-149">Tím zajistíte, že odhlášení odebere obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="4b36c-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="4b36c-150">Pokud jste místo toho použili tělo výrazu lambda, pokoušíte se odebrat obslužnou rutinu, která nebyla nikdy připojena, což neprovede nic.</span><span class="sxs-lookup"><span data-stu-id="4b36c-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="4b36c-151">V dalším článku se dozvíte více o vzorcích typických událostí a různých variantách v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4b36c-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="4b36c-152">Další</span><span class="sxs-lookup"><span data-stu-id="4b36c-152">Next</span></span>](event-pattern.md)
