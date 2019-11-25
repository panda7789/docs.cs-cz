---
title: Seznámení s událostmi
description: Přečtěte si o událostech v .NET Core a cílech návrhu jazyka pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: ceae2b9319a1de9f01102987735c7db2c2883f18
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138515"
---
# <a name="introduction-to-events"></a><span data-ttu-id="f48b3-103">Seznámení s událostmi</span><span class="sxs-lookup"><span data-stu-id="f48b3-103">Introduction to events</span></span>

[<span data-ttu-id="f48b3-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="f48b3-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="f48b3-105">Události jsou, jako delegáti, *pozdní vazba* mechanismu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="f48b3-106">Ve skutečnosti jsou události postaveny na jazykové podpoře pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="f48b3-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="f48b3-107">Události představují způsob, jak objekt vysílat (všem zúčastněným součástem v systému), ke kterému došlo něco.</span><span class="sxs-lookup"><span data-stu-id="f48b3-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="f48b3-108">Kterákoli další součást se může přihlásit k odběru události a upozornit, až se událost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f48b3-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="f48b3-109">V některém z vašich programování jste pravděpodobně použili události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="f48b3-110">Mnoho grafických systémů má model událostí, který by mohl nahlásit interakci uživatele.</span><span class="sxs-lookup"><span data-stu-id="f48b3-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="f48b3-111">Tyto události by mohly vykazovat pohyb myši, stisknutí tlačítek a podobné interakce.</span><span class="sxs-lookup"><span data-stu-id="f48b3-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="f48b3-112">To je jeden z nejběžnějších, ale určitě ne jediným scénářem, kdy se události používají.</span><span class="sxs-lookup"><span data-stu-id="f48b3-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="f48b3-113">Můžete definovat události, které by měly být vyvolány pro vaše třídy.</span><span class="sxs-lookup"><span data-stu-id="f48b3-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="f48b3-114">Jedním z důležitých aspektů při práci s událostmi je, že pro konkrétní událost nemusí být registrován žádný objekt.</span><span class="sxs-lookup"><span data-stu-id="f48b3-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="f48b3-115">Je nutné napsat kód tak, aby nevyvolávají události, pokud nejsou nakonfigurovány naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="f48b3-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="f48b3-116">Přihlášení k odběru události také vytvoří propojení mezi dvěma objekty (zdrojem událostí a jímkou událostí).</span><span class="sxs-lookup"><span data-stu-id="f48b3-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="f48b3-117">Je nutné zajistit, aby jímka událostí odhlásila odběr ze zdroje událostí, pokud již nebude zajímat události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="f48b3-118">Cíle návrhu pro podporu událostí</span><span class="sxs-lookup"><span data-stu-id="f48b3-118">Design goals for event support</span></span>

<span data-ttu-id="f48b3-119">Návrh jazyka pro události, které cílí na tyto cíle:</span><span class="sxs-lookup"><span data-stu-id="f48b3-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="f48b3-120">Povoluje velmi minimální spojení mezi zdrojem událostí a jímkou událostí.</span><span class="sxs-lookup"><span data-stu-id="f48b3-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="f48b3-121">Tyto dvě komponenty možná nebudou zapsány stejnou organizací a mohou být aktualizovány i na zcela různých plánech.</span><span class="sxs-lookup"><span data-stu-id="f48b3-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="f48b3-122">Mělo by být velmi jednoduché přihlásit se k odběru události a zrušit odběr této události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="f48b3-123">Zdroje událostí by měly podporovat více odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="f48b3-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="f48b3-124">Měla by také podporovat nepřipojené předplatitele událostí.</span><span class="sxs-lookup"><span data-stu-id="f48b3-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="f48b3-125">Můžete vidět, že cíle pro události jsou velmi podobné cílům pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="f48b3-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="f48b3-126">To je důvod, proč je podpora jazyka událostí založená na podpoře jazyka delegáta.</span><span class="sxs-lookup"><span data-stu-id="f48b3-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="f48b3-127">Jazyková podpora pro události</span><span class="sxs-lookup"><span data-stu-id="f48b3-127">Language support for events</span></span>

<span data-ttu-id="f48b3-128">Syntaxe pro definování událostí a přihlášení k odběru nebo odhlášení z událostí je rozšířením syntaxe pro delegáty.</span><span class="sxs-lookup"><span data-stu-id="f48b3-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="f48b3-129">Chcete-li definovat událost, kterou použijete klíčové slovo `event`:</span><span class="sxs-lookup"><span data-stu-id="f48b3-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="f48b3-130">Typ události (v tomto příkladu `EventHandler<FileListArgs>`) musí být typu delegát.</span><span class="sxs-lookup"><span data-stu-id="f48b3-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="f48b3-131">Při deklaraci události byste měli dodržovat několik konvencí.</span><span class="sxs-lookup"><span data-stu-id="f48b3-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="f48b3-132">Typ delegáta události obvykle má návratovou hodnotu void.</span><span class="sxs-lookup"><span data-stu-id="f48b3-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="f48b3-133">Deklarace události by měly být slovesem nebo slovesovou frází.</span><span class="sxs-lookup"><span data-stu-id="f48b3-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="f48b3-134">V případě, že událost nahlásí něco, co se stalo, použijte dřívější vhodné.</span><span class="sxs-lookup"><span data-stu-id="f48b3-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="f48b3-135">K hlášení toho, co se stane, použijte stávající vhodné příkaz (například `Closing`).</span><span class="sxs-lookup"><span data-stu-id="f48b3-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="f48b3-136">Často se pomocí současných vhodné značí, že vaše třída podporuje nějaký druh chování přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="f48b3-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="f48b3-137">Jedním z nejběžnějších scénářů je podpora zrušení.</span><span class="sxs-lookup"><span data-stu-id="f48b3-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="f48b3-138">Například událost `Closing` může zahrnovat argument, který by označoval, zda by měla operace zavřít pokračovat, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="f48b3-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="f48b3-139">V jiných scénářích může volající změnit chování aktualizací vlastností argumentů události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="f48b3-140">Můžete vyvolat událost, která indikuje navrženou další akci, kterou algoritmus provede.</span><span class="sxs-lookup"><span data-stu-id="f48b3-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="f48b3-141">Obslužná rutina události může pověřit jinou akci úpravou vlastností argumentu události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="f48b3-142">Pokud chcete vyvolat událost, zavolejte obslužné rutiny události pomocí syntaxe vyvolání delegáta:</span><span class="sxs-lookup"><span data-stu-id="f48b3-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="f48b3-143">Jak je popsáno v části [Delegáti](delegates-patterns.md),?.</span><span class="sxs-lookup"><span data-stu-id="f48b3-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="f48b3-144">operátor usnadňuje zajištění, že se nepokoušíte vyvolat událost, pokud k této události neexistují žádní předplatitelé.</span><span class="sxs-lookup"><span data-stu-id="f48b3-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="f48b3-145">Přihlásíte se k odběru události pomocí operátoru `+=`:</span><span class="sxs-lookup"><span data-stu-id="f48b3-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="f48b3-146">Metoda obslužné rutiny má obvykle předponu "on" následovaný názvem události, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="f48b3-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="f48b3-147">Pomocí operátoru `-=` se odhlásíte k odběru:</span><span class="sxs-lookup"><span data-stu-id="f48b3-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="f48b3-148">Je důležité si uvědomit, že jsem deklaroval místní proměnnou pro výraz, který představuje obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="f48b3-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="f48b3-149">To zajišťuje, že zrušení odběru odebere obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="f48b3-150">Pokud místo toho jste použili tělo výrazu lambda, pokoušíte se odebrat obslužnou rutinu, která nebyla nikdy připojena, což nedělá nic.</span><span class="sxs-lookup"><span data-stu-id="f48b3-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="f48b3-151">V dalším článku se dozvíte víc o typických vzorcích událostí a o různých variacích v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="f48b3-152">Next</span><span class="sxs-lookup"><span data-stu-id="f48b3-152">Next</span></span>](event-pattern.md)
