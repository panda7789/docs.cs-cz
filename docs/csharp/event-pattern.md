---
title: Standardní vzory událostí rozhraní .NET
description: Další informace o události vzory .NET a postup vytvoření zdroje Standardní událostí a přihlášení k odběru a zpracování standardních událostí v kódu.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 9bd9f71726647966dd1e4426b260484decb048c6
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827245"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="ad8f6-103">Standardní vzory událostí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="ad8f6-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="ad8f6-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="ad8f6-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="ad8f6-105">Události rozhraní .NET obecně podle několik známé vzorce.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="ad8f6-106">Standardizace na tyto vzory znamená, že vývojáři můžou využít znalosti o tyto standardní vzorce, které lze použít pro žádné program událostí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="ad8f6-107">Přejděte přes tyto standardní vzory, budete mít všechny znalostní báze, které potřebujete k vytvoření zdroje Standardní událostí a přihlášení k odběru a zpracování standardních událostí v kódu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="ad8f6-108">Podpisy delegáta událostí</span><span class="sxs-lookup"><span data-stu-id="ad8f6-108">Event Delegate Signatures</span></span>

<span data-ttu-id="ad8f6-109">Standardní podpis pro delegáta události .NET je:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="ad8f6-110">Návratový typ je neplatné.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-110">The return type is void.</span></span> <span data-ttu-id="ad8f6-111">Události jsou založené na Delegáti a jsou vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="ad8f6-112">U každého zdroje událostí, která podporuje více odběrateli.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="ad8f6-113">Jeden návratovou hodnotu z metody nemá škálování víc odběratelům událostí.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="ad8f6-114">Které návratová hodnota nemá najdete zdroje událostí po vyvolání události?</span><span class="sxs-lookup"><span data-stu-id="ad8f6-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="ad8f6-115">Později v tomto článku uvidíte, jak vytvořit událost protokoly, které podporují událostí Odběratelé, kteří tyto informace sestav ke zdroji událostí.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="ad8f6-116">Seznam argumentů obsahuje dva argumenty: odesílatel a argumenty událostí.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="ad8f6-117">Typ doba kompilace `sender` je `System.Object`, i když znáte pravděpodobně více odvozený typ, který by měl být vždy správný.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="ad8f6-118">Podle konvence, použijte `object`.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-118">By convention, use `object`.</span></span>

<span data-ttu-id="ad8f6-119">Druhý argument obvykle byl typ, který je odvozený od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="ad8f6-120">(Se zobrazí v [další části](modern-events.md) už vynucované touto konvencí.) Pokud váš typ události není nutné žádné další argumenty, bude stále zadat oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="ad8f6-121">Speciální hodnotu, `EventArgs.Empty` že se mají používat k označení, že vaše události neobsahuje žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="ad8f6-122">Umožňuje vytvořit třídu, která obsahuje soubory v adresáři, nebo libovolná z jejích podadresářů využívajících vzor.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="ad8f6-123">Tato součást se vyvolá událost pro každý soubor nalezeny, který odpovídá vzorku.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="ad8f6-124">Pomocí model událostí obsahuje některé výhody návrhu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="ad8f6-125">Můžete vytvořit víc naslouchacích procesů událostí, které provádět různé akce, když se najde soubor hledané kombinaci.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="ad8f6-126">Kombinování různých naslouchací procesy můžete vytvářet robustnější algoritmy.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="ad8f6-127">Tady je deklaraci argument počáteční události pro hledání hledané kombinaci souboru:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="ad8f6-128">I když tento typ vypadá jako typ malé, pouze data, by měl postupovat podle konvence a nastavit jej jako odkaz (`class`) typu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="ad8f6-129">To znamená, že se předají objekt argument odkazem a všechny aktualizace dat, bude zobrazit všechny odběratele.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="ad8f6-130">První verze je objekt neměnné.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-130">The first version is an immutable object.</span></span> <span data-ttu-id="ad8f6-131">By měla přednost zkontrolujte vlastnosti ve vaší typ argumentu události neměnné.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="ad8f6-132">Tímto způsobem jednoho odběratele nelze změnit hodnoty, než jiné odběratele uvidí je.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="ad8f6-133">(Existují výjimky, jak se zobrazí níže).</span><span class="sxs-lookup"><span data-stu-id="ad8f6-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="ad8f6-134">Dále je potřeba vytvořit deklaraci události ve třídě FileSearcher.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="ad8f6-135">Využití `EventHandler<T>` typ znamená, že nemusíte vytvářet ještě jiné definice typu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="ad8f6-136">Jednoduše použijte obecné specializace.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="ad8f6-137">Umožňuje vyplnit třídu FileSearcher k vyhledávání souborů, které odpovídají vzorku a vygenerovat správný událostí při zjištění shody.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="ad8f6-138">Definining a aktivaci událostí jako pole</span><span class="sxs-lookup"><span data-stu-id="ad8f6-138">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="ad8f6-139">Nejjednodušší způsob, jak přidat událost do vaší třídy je pro tuto událost deklarovat jako veřejné pole, jako v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="ad8f6-140">To vypadá ho je deklarace veřejné pole, které by se zdají být chybný postup objektově orientované.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="ad8f6-141">Chcete chránit přístup k datům prostřednictvím vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="ad8f6-142">Když to zkontrolujte vypadat jako chybný postup kód vygenerovaný kompilátor vytváření obálek tak, aby objektů událostí lze přistupovat pouze bezpečné způsoby.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-142">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="ad8f6-143">K dispozici jenom operace na pole podobné události jsou přidejte obslužnou rutinu:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="ad8f6-144">a obslužné rutiny odebírání:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="ad8f6-145">Všimněte si, že je místní proměnná pro obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="ad8f6-146">Pokud jste použili text argument lambda, odebrat nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="ad8f6-147">By být jinou instanci delegáta a bezobslužně Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="ad8f6-148">Kód mimo třídy nemohou vyvolat události, ani můžete provádět žádné jiné operace.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="ad8f6-149">Vrácení hodnoty z události odběratele</span><span class="sxs-lookup"><span data-stu-id="ad8f6-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="ad8f6-150">Vaše jednoduché verze funguje bez problémů.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-150">Your simple version is working fine.</span></span> <span data-ttu-id="ad8f6-151">Umožňuje přidat další funkcí: zrušení.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="ad8f6-152">Když zvýšíte nachází události, moduly pro naslouchání byste měli mít k zastavení další zpracování, pokud tento soubor je, že poslední Hledat.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="ad8f6-153">Obslužné rutiny událostí nevrátí hodnotu, takže potřebujete komunikovat, jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="ad8f6-154">Vzor standardní událostí používá objekt EventArgs pro zahrnutí polí, které události odběratele používat ke komunikaci Storno.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="ad8f6-155">Existují dva různé vzorce, které by mohly být použity, podle sémantika kontrakt Storno.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="ad8f6-156">V obou případech přidáte logická pole EventArguments pro událost nalezený soubor.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="ad8f6-157">Jeden vzor by umožnilo žádné jednoho odběratele na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="ad8f6-158">Pro tento vzor, je inicializováno nové pole `false`.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="ad8f6-159">Všechny odběratele lze změnit na `true`.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="ad8f6-160">Po všech Odběratelé, kteří mají vidět vyvolaná událost, komponentu FileSearcher prozkoumá logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="ad8f6-161">Druhý vzor by pouze zrušte operaci, pokud všechny Odběratelé, kteří chtěli operace byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="ad8f6-162">V tomto vzoru se inicializovat nové pole označíte, má-li zrušit operaci, a všechny odběratele může změnit se indikovat, že by měl v operaci pokračovat.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="ad8f6-163">Po všech Odběratelé, kteří mají vidět vyvolaná událost, komponentu FileSearcher prověří logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="ad8f6-164">V tomto vzoru je jeden další krok: součást musí vědět, pokud žádné Odběratelé, kteří mají vidět události.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="ad8f6-165">Pokud neexistují žádné odběratele, pole by nesprávně indikovat Storno.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="ad8f6-166">Umožňuje implementovat první verzi pro tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="ad8f6-167">Je nutné přidat pole boolean s názvem `CancelRequested` k `FileFoundArgs` typu:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="ad8f6-168">Toto nové pole je automaticky inicializován na `false`, výchozí hodnota pro pole Boolean, tak nejsou omylem zrušit.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="ad8f6-169">Jediná další změna součást je kontrola příznak po vyvolání události pro zobrazení, pokud žádné z odběratele, kteří odeslali žádost o zrušení:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="ad8f6-170">Jednou z výhod tohoto vzoru je, že to není narušující změně.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="ad8f6-171">Žádná z odběratele požadovaný zrušení před, a stále nejsou.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="ad8f6-172">Žádný kód odběratele musí, aktualizaci, pokud chtějí nový protokol Storno.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="ad8f6-173">Je velmi volně vázány.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-173">It's very loosely coupled.</span></span>

<span data-ttu-id="ad8f6-174">Umožňuje aktualizovat odběratele tak, aby požadavků zrušení, jakmile najde první spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="ad8f6-175">Přidání jiného deklarace událostí</span><span class="sxs-lookup"><span data-stu-id="ad8f6-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="ad8f6-176">Umožňuje přidat jeden další funkce a ukažte, ostatní idioms jazyk pro události.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="ad8f6-177">Přidejme přetížení `Search()` metoda, který prochází skrz všechny podadresáře při hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-177">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="ad8f6-178">To může získat být časově náročná operace v adresáři s mnoha podadresářů.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="ad8f6-179">Přidejme událost, která se získá vyvolá, když začne každou nové vyhledávání v adresáři.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="ad8f6-180">To umožňuje odběratele, kteří mají sledování postupu a aktualizovat uživatele o průběhu.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="ad8f6-181">Všechny ukázky, které jste vytvořili, pokud jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="ad8f6-182">Provedeme tato interní událost.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-182">Let's make this one an internal event.</span></span> <span data-ttu-id="ad8f6-183">To znamená, že můžete provést také typy používané pro interní argumenty také.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="ad8f6-184">Spusťte tak, že vytvoříte novou třídu odvozenou EventArgs pro vytváření sestav nový adresář a průběh.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="ad8f6-185">Znovu postupujte podle doporučení pro neměnné odkaz pro argumenty událostí.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="ad8f6-186">V dalším kroku definujte událost.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-186">Next, define the event.</span></span> <span data-ttu-id="ad8f6-187">Tentokrát budete používat jinou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="ad8f6-188">Kromě použití syntaxe pole, můžete explicitně vytvořit vlastnosti s přidat a odebrat obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="ad8f6-189">V této ukázce nebude potřebovat další kód v těchto obslužných rutin, ale to ukazuje, jak by je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="ad8f6-190">V mnoha směrech kód napsaný v tomto poli zrcadlení, že kód kompilátor generuje pro definice pole událostí Seznámili jste se dříve.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="ad8f6-191">Vytvoření událostí pomocí syntaxe velmi podobná používá pro [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="ad8f6-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="ad8f6-192">Všimněte si, že obslužných rutin mají odlišné názvy: `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="ad8f6-193">Toto nastavení se nazývá k přihlášení k odběru události nebo odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="ad8f6-194">Všimněte si, že také musíte deklarovat privátní základní pole pro uložení proměnné události.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="ad8f6-195">Inicializací na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-195">It is initialized to null.</span></span>

<span data-ttu-id="ad8f6-196">V dalším kroku přidejme přetížení metody Search(), který prochází podadresáře a vyvolá obou události.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-196">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="ad8f6-197">Nejjednodušší způsob, jak tomu se má používat výchozí argument k určení, zda chcete vyhledávat všechny adresáře:</span><span class="sxs-lookup"><span data-stu-id="ad8f6-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="ad8f6-198">V tomto okamžiku můžete spustit aplikace volání přetížení pro vyhledávání všech dílčí adresářů.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="ad8f6-199">Neexistují žádné odběratele na nové `ChangeDirectory` událostí, ale pomocí `?.Invoke()` stylu zajistí, že to funguje správně.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="ad8f6-200">Přidejme obslužnou rutinu k zápisu řádku, který zobrazuje průběh v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="ad8f6-201">Seznámili jste se vzorů, které je třeba v rámci ekosystému .NET.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="ad8f6-202">Podle informací tyto vzory a konvence, budete psát idiomatickou C# a .NET rychle.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="ad8f6-203">V dalším kroku se zobrazí některé změny v tyto vzory v nejnovější verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ad8f6-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="ad8f6-204">Next</span><span class="sxs-lookup"><span data-stu-id="ad8f6-204">Next</span></span>](modern-events.md)
