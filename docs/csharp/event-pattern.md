---
title: Standardní vzory událostí .NET
description: Přečtěte si o vzorech událostí .NET a o tom, jak vytvořit standardní zdroje událostí a přihlásit se k odběru a zpracovávat standardní události ve vašem kódu.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 517e46ffec163a9bd49baa58fc0b37b54b2b2809
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239856"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="caa3b-103">Standardní vzory událostí .NET</span><span class="sxs-lookup"><span data-stu-id="caa3b-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="caa3b-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="caa3b-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="caa3b-105">Události .NET obecně následují několik známých vzorů.</span><span class="sxs-lookup"><span data-stu-id="caa3b-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="caa3b-106">Standardizace těchto vzorů znamená, že vývojáři mohou využít znalosti těchto standardních vzorů, které lze použít na jakýkoli program událostí .NET.</span><span class="sxs-lookup"><span data-stu-id="caa3b-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="caa3b-107">Pojďme si projít tyto standardní vzory, abyste měli všechny znalosti, které potřebujete k vytvoření standardních zdrojů událostí, a přihlásit se k odběru a zpracovávat standardní události v kódu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="caa3b-108">Signatury delegátů událostí</span><span class="sxs-lookup"><span data-stu-id="caa3b-108">Event Delegate Signatures</span></span>

<span data-ttu-id="caa3b-109">Standardní signatura pro delegáta události .NET je:</span><span class="sxs-lookup"><span data-stu-id="caa3b-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="caa3b-110">Návratový typ je void.</span><span class="sxs-lookup"><span data-stu-id="caa3b-110">The return type is void.</span></span> <span data-ttu-id="caa3b-111">Události jsou založené na delegátech a jsou delegáti vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="caa3b-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="caa3b-112">Který podporuje více předplatitelů pro libovolný zdroj události.</span><span class="sxs-lookup"><span data-stu-id="caa3b-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="caa3b-113">Jediná návratová hodnota z metody se neškáluje na více odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="caa3b-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="caa3b-114">Jakou návratovou hodnotu zdroj události uvidí po vyvolání události?</span><span class="sxs-lookup"><span data-stu-id="caa3b-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="caa3b-115">Později v tomto článku se dozvíte, jak vytvořit protokoly událostí, které podporují předplatitele událostí, které oznamují informace do zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="caa3b-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="caa3b-116">Seznam argumentů obsahuje dva argumenty: odesílatel a argumenty události.</span><span class="sxs-lookup"><span data-stu-id="caa3b-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="caa3b-117">Typ doby kompilace `sender` je `System.Object`, i když pravděpodobně znáte více odvozeného typu, který by byl vždy správný.</span><span class="sxs-lookup"><span data-stu-id="caa3b-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="caa3b-118">Podle konvence použijte `object`.</span><span class="sxs-lookup"><span data-stu-id="caa3b-118">By convention, use `object`.</span></span>

<span data-ttu-id="caa3b-119">Druhý argument byl obvykle typ, který je odvozen od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="caa3b-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="caa3b-120">(Uvidíte v [Další části](modern-events.md) , že tato konvence už není vynutila.) Pokud váš typ události nepotřebuje žádné další argumenty, budete přesto poskytovat oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="caa3b-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="caa3b-121">Existuje zvláštní hodnota `EventArgs.Empty`, kterou byste měli použít k označení, že vaše událost neobsahuje žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="caa3b-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="caa3b-122">Pojďme sestavit třídu, která obsahuje seznam souborů v adresáři, nebo některé z jeho podadresářů, které následují vzor.</span><span class="sxs-lookup"><span data-stu-id="caa3b-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="caa3b-123">Tato komponenta vyvolá událost pro každý nalezený soubor, který odpovídá vzoru.</span><span class="sxs-lookup"><span data-stu-id="caa3b-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="caa3b-124">Použití modelu událostí poskytuje některé výhody návrhu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="caa3b-125">Můžete vytvořit několik posluchačů událostí, které při nalezení hledaného souboru provádějí různé akce.</span><span class="sxs-lookup"><span data-stu-id="caa3b-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="caa3b-126">Kombinování různých posluchačů může vytvářet robustnější algoritmy.</span><span class="sxs-lookup"><span data-stu-id="caa3b-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="caa3b-127">Tady je počáteční deklarace argumentu události pro vyhledání hledaného souboru:</span><span class="sxs-lookup"><span data-stu-id="caa3b-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="caa3b-128">I když tento typ vypadá jako malý, pouze datový typ, měli byste postupovat podle konvence a vytvořit z něj referenční (`class`) typ.</span><span class="sxs-lookup"><span data-stu-id="caa3b-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="caa3b-129">To znamená, že objekt argumentu bude předán odkazem a všechny aktualizace dat budou zobrazeny všemi předplatiteli.</span><span class="sxs-lookup"><span data-stu-id="caa3b-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="caa3b-130">První verze je neproměnlivý objekt.</span><span class="sxs-lookup"><span data-stu-id="caa3b-130">The first version is an immutable object.</span></span> <span data-ttu-id="caa3b-131">Měli byste raději nastavit vlastnosti v argumentu události typ unmutableed.</span><span class="sxs-lookup"><span data-stu-id="caa3b-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="caa3b-132">Jeden předplatitel pak nemůže změnit hodnoty předtím, než je uvidí jiný odběratel.</span><span class="sxs-lookup"><span data-stu-id="caa3b-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="caa3b-133">(V takovém případě jsou k dispozici výjimky, jak vidíte níže.)</span><span class="sxs-lookup"><span data-stu-id="caa3b-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="caa3b-134">Dále je potřeba vytvořit deklaraci události ve třídě hledání ve službě.</span><span class="sxs-lookup"><span data-stu-id="caa3b-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="caa3b-135">Využití `EventHandler<T>`ho typu znamená, že ještě nemusíte vytvářet jinou definici typu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="caa3b-136">Jednoduše použijete obecnou specializaci.</span><span class="sxs-lookup"><span data-stu-id="caa3b-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="caa3b-137">Pojďme vyplňovat třídu hledání souborů, aby bylo možné vyhledávat soubory, které odpovídají vzoru, a vyvolat správnou událost při zjištění shody.</span><span class="sxs-lookup"><span data-stu-id="caa3b-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="caa3b-138">Definování a vyvolávání událostí podobných poli</span><span class="sxs-lookup"><span data-stu-id="caa3b-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="caa3b-139">Nejjednodušší způsob, jak přidat událost do vaší třídy, je deklarovat tuto událost jako veřejné pole, jako v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="caa3b-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="caa3b-140">Vypadá to, že deklaruje veřejné pole, což by znamenalo špatný objektově orientovaný postup.</span><span class="sxs-lookup"><span data-stu-id="caa3b-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="caa3b-141">Chcete chránit přístup k datům prostřednictvím vlastností nebo metod.</span><span class="sxs-lookup"><span data-stu-id="caa3b-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="caa3b-142">Přestože to může vypadat jako špatný postup, kód generovaný kompilátorem vytvoří obálky, aby k objektům událostí bylo možné získávat přístup pouze bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="caa3b-142">While this may look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="caa3b-143">Jediné operace dostupné v události podobné poli jsou přidání obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="caa3b-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="caa3b-144">a odebrat obslužnou rutinu:</span><span class="sxs-lookup"><span data-stu-id="caa3b-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="caa3b-145">Všimněte si, že pro obslužnou rutinu je k dispozici místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="caa3b-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="caa3b-146">Pokud jste použili tělo lambda, odebrání by nefungovalo správně.</span><span class="sxs-lookup"><span data-stu-id="caa3b-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="caa3b-147">By to byla jiná instance delegáta a tiše nedělá nic.</span><span class="sxs-lookup"><span data-stu-id="caa3b-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="caa3b-148">Kód mimo třídu nemůže vyvolat událost, ani nemůže provádět žádné jiné operace.</span><span class="sxs-lookup"><span data-stu-id="caa3b-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="caa3b-149">Vracení hodnot od odběratelů událostí</span><span class="sxs-lookup"><span data-stu-id="caa3b-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="caa3b-150">Vaše jednoduchá verze funguje správně.</span><span class="sxs-lookup"><span data-stu-id="caa3b-150">Your simple version is working fine.</span></span> <span data-ttu-id="caa3b-151">Pojďme přidat další funkci: zrušení.</span><span class="sxs-lookup"><span data-stu-id="caa3b-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="caa3b-152">Pokud vyvoláte nalezenou událost, naslouchací procesy by měly být schopné zastavit další zpracování, pokud je tento soubor ten, který byl naposledy vyžádán.</span><span class="sxs-lookup"><span data-stu-id="caa3b-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="caa3b-153">Obslužné rutiny událostí nevrací hodnotu, takže je třeba komunikovat jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="caa3b-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="caa3b-154">Standardní vzor události používá objekt EventArgs k zahrnutí polí, které mohou předplatitelé události použít ke sdělení zrušení.</span><span class="sxs-lookup"><span data-stu-id="caa3b-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="caa3b-155">Existují dva různé vzory, které by mohly být použity na základě sémantiky zrušení smlouvy.</span><span class="sxs-lookup"><span data-stu-id="caa3b-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="caa3b-156">V obou případech přidáte pole Boolean do EventArguments pro událost nalezeného souboru.</span><span class="sxs-lookup"><span data-stu-id="caa3b-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="caa3b-157">Jeden ze vzorů umožní jednomu předplatiteli zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="caa3b-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="caa3b-158">Pro tento model je nové pole inicializováno na `false`.</span><span class="sxs-lookup"><span data-stu-id="caa3b-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="caa3b-159">Každý předplatitel ho může změnit na `true`.</span><span class="sxs-lookup"><span data-stu-id="caa3b-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="caa3b-160">Poté, co všichni předplatitelé viděli vyvolanou událost, ověří Tato komponenta logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="caa3b-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="caa3b-161">Druhý vzor by tuto operaci zrušil jenom v případě, že všichni předplatitelé chtěli operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="caa3b-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="caa3b-162">V tomto modelu se nové pole inicializuje, aby označovalo, že operace se má zrušit, a každý předplatitel ho může změnit, aby označoval, že operace by měla pokračovat.</span><span class="sxs-lookup"><span data-stu-id="caa3b-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="caa3b-163">Poté, co všichni předplatitelé viděli vyvolanou událost, vyhledá součást hledání v Boolean logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="caa3b-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="caa3b-164">Tento model obsahuje ještě jeden krok navíc: součást musí zjistit, jestli se událost objevila pro nějaké předplatitele.</span><span class="sxs-lookup"><span data-stu-id="caa3b-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="caa3b-165">Pokud žádné předplatitelé neexistují, pole by znamenalo nesprávné zrušení.</span><span class="sxs-lookup"><span data-stu-id="caa3b-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="caa3b-166">Pojďme implementovat první verzi této ukázky.</span><span class="sxs-lookup"><span data-stu-id="caa3b-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="caa3b-167">Do typu `FileFoundArgs` musíte přidat pole Boolean s názvem `CancelRequested`:</span><span class="sxs-lookup"><span data-stu-id="caa3b-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="caa3b-168">Toto nové pole se automaticky inicializuje na `false`, což je výchozí hodnota pro pole Boolean, takže nebudete nic rušit.</span><span class="sxs-lookup"><span data-stu-id="caa3b-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="caa3b-169">Jedinou jinou změnou součásti je zkontrolování příznaku po vyvolání události, aby bylo možné zjistit, zda některý z předplatitelů požadoval zrušení:</span><span class="sxs-lookup"><span data-stu-id="caa3b-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="caa3b-170">Jednou z výhod tohoto vzoru je, že se nejedná o zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="caa3b-171">Žádný z předplatitelů požádal o zrušení před a ještě není.</span><span class="sxs-lookup"><span data-stu-id="caa3b-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="caa3b-172">Žádný z kódů předplatitele není potřeba aktualizovat, pokud nechtějí podporovat nový protokol zrušení.</span><span class="sxs-lookup"><span data-stu-id="caa3b-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="caa3b-173">Je velmi volně spojená.</span><span class="sxs-lookup"><span data-stu-id="caa3b-173">It's very loosely coupled.</span></span>

<span data-ttu-id="caa3b-174">Pojďme předplatitele aktualizovat, aby po nalezení prvního spustitelného souboru vyžádal zrušení.</span><span class="sxs-lookup"><span data-stu-id="caa3b-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="caa3b-175">Přidání další deklarace události</span><span class="sxs-lookup"><span data-stu-id="caa3b-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="caa3b-176">Pojďme přidat další funkci a předvést pro události idiomy další jazyky.</span><span class="sxs-lookup"><span data-stu-id="caa3b-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="caa3b-177">Pojďme přidat přetížení metody `Search`, která projde všechny podadresáře při hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="caa3b-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="caa3b-178">Může se jednat o zdlouhavou operaci v adresáři s mnoha podadresáři.</span><span class="sxs-lookup"><span data-stu-id="caa3b-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="caa3b-179">Pojďme přidat událost, která se aktivuje při každém zahájení hledání nového adresáře.</span><span class="sxs-lookup"><span data-stu-id="caa3b-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="caa3b-180">To umožňuje předplatitelům sledovat průběh a aktualizovat uživatele jako průběh.</span><span class="sxs-lookup"><span data-stu-id="caa3b-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="caa3b-181">Všechny ukázky, které jste dosud vytvořili, jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="caa3b-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="caa3b-182">Pojďme udělat tuto interní událost.</span><span class="sxs-lookup"><span data-stu-id="caa3b-182">Let's make this one an internal event.</span></span> <span data-ttu-id="caa3b-183">To znamená, že můžete také nastavit typy používané pro interní argumenty.</span><span class="sxs-lookup"><span data-stu-id="caa3b-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="caa3b-184">Začnete vytvořením nové odvozené třídy EventArgs pro vytváření sestav nového adresáře a postupu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="caa3b-185">Znovu můžete postupovat podle doporučení a nastavit pro argumenty události neměnný typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="caa3b-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="caa3b-186">Dále definujte událost.</span><span class="sxs-lookup"><span data-stu-id="caa3b-186">Next, define the event.</span></span> <span data-ttu-id="caa3b-187">Tentokrát použijete jinou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="caa3b-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="caa3b-188">Kromě použití syntaxe pole můžete explicitně vytvořit vlastnost s obslužnými rutinami přidat a odebrat.</span><span class="sxs-lookup"><span data-stu-id="caa3b-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="caa3b-189">V této ukázce nebudete v těchto obslužných rutinách potřebovat další kód, ale ukazuje, jak byste je vytvořili.</span><span class="sxs-lookup"><span data-stu-id="caa3b-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="caa3b-190">V mnoha způsobech kód, který sem píšete, zrcadlí kód, který kompilátor generuje pro definice událostí pole, které jste viděli dříve.</span><span class="sxs-lookup"><span data-stu-id="caa3b-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="caa3b-191">Vytvoříte událost pomocí syntaxe, která je velmi podobná jako vlastnost použitá pro [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="caa3b-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="caa3b-192">Všimněte si, že obslužné rutiny mají jiné názvy: `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="caa3b-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="caa3b-193">Jsou volány k přihlášení k odběru události nebo k odhlášení odběru události.</span><span class="sxs-lookup"><span data-stu-id="caa3b-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="caa3b-194">Všimněte si, že je také nutné deklarovat soukromé pole zálohování pro uložení proměnné události.</span><span class="sxs-lookup"><span data-stu-id="caa3b-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="caa3b-195">Je inicializována na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="caa3b-195">It is initialized to null.</span></span>

<span data-ttu-id="caa3b-196">Nyní přidáme přetížení metody `Search`, která projde podadresáři a vyvolá obě události.</span><span class="sxs-lookup"><span data-stu-id="caa3b-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="caa3b-197">Nejjednodušší způsob, jak to provést, je použít výchozí argument k určení, že chcete prohledávat všechny adresáře:</span><span class="sxs-lookup"><span data-stu-id="caa3b-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="caa3b-198">V tomto okamžiku můžete spustit aplikaci, která volá metodu Overload pro hledání všech podadresářů.</span><span class="sxs-lookup"><span data-stu-id="caa3b-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="caa3b-199">K nové události `ChangeDirectory` neexistují žádní předplatitelé, ale použití `?.Invoke()` idiom zajišťuje správné fungování.</span><span class="sxs-lookup"><span data-stu-id="caa3b-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="caa3b-200">Pojďme přidat obslužnou rutinu pro zápis řádku, který ukazuje průběh v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="caa3b-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="caa3b-201">Viděli jste vzory, které jsou následovány v rámci ekosystému .NET.</span><span class="sxs-lookup"><span data-stu-id="caa3b-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="caa3b-202">Díky učení těchto vzorů a konvencí budete rychle psát idiomatickou C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="caa3b-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="caa3b-203">Dále uvidíte některé změny v těchto vzorech v nejnovější verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="caa3b-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="caa3b-204">Next</span><span class="sxs-lookup"><span data-stu-id="caa3b-204">Next</span></span>](modern-events.md)
