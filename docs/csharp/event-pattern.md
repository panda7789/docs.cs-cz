---
title: Standardní vzory událostí .NET
description: Další informace o vzory událostí .NET a vytvoření zdroje událostí úrovně standard a odběru a zpracování standardní události ve vašem kódu.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 11755b4754b15070869adf12d5be409af99035d4
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201245"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="d8bef-103">Standardní vzory událostí .NET</span><span class="sxs-lookup"><span data-stu-id="d8bef-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="d8bef-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="d8bef-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="d8bef-105">Události .NET obvykle postupují podle několik známých vzorců.</span><span class="sxs-lookup"><span data-stu-id="d8bef-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="d8bef-106">Standardizují používáním těchto vzorců znamená, že vývojáři mohou využít znalost těchto standardní vzory, které lze použít u každého programu událost .NET.</span><span class="sxs-lookup"><span data-stu-id="d8bef-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="d8bef-107">Podívejme se tyto standardní vzory tak budou mít všechny znalosti potřebné k vytvoření zdroje událostí úrovně standard a odběru a zpracování standardní události ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="d8bef-108">Podpisy delegáta události</span><span class="sxs-lookup"><span data-stu-id="d8bef-108">Event Delegate Signatures</span></span>

<span data-ttu-id="d8bef-109">Standardní podpisu pro delegáta události .NET je:</span><span class="sxs-lookup"><span data-stu-id="d8bef-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="d8bef-110">Návratový typ je typ void.</span><span class="sxs-lookup"><span data-stu-id="d8bef-110">The return type is void.</span></span> <span data-ttu-id="d8bef-111">Události jsou založeny na delegáty a jsou vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="d8bef-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="d8bef-112">U každého zdroje událostí, která podporuje několik předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="d8bef-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="d8bef-113">Jednu návratovou hodnotu z metody neškáluje několika odběratelům události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="d8bef-114">Který vrátí hodnotu nemá viz zdroj událostí po vyvolání události?</span><span class="sxs-lookup"><span data-stu-id="d8bef-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="d8bef-115">Dále v tomto článku uvidíte, jak vytvořit tyto sestavy informace zdroje událostí protokoly událostí, které podporují odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="d8bef-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="d8bef-116">Seznam argumentů obsahuje dva argumenty: odesílatele a argumenty události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="d8bef-117">Typ času kompilace `sender` je `System.Object`, i když pravděpodobně znáte více odvozený typ, který by měl být vždy správná.</span><span class="sxs-lookup"><span data-stu-id="d8bef-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="d8bef-118">Podle konvence, použijte `object`.</span><span class="sxs-lookup"><span data-stu-id="d8bef-118">By convention, use `object`.</span></span>

<span data-ttu-id="d8bef-119">Druhý argument obvykle byl typ, který je odvozen z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="d8bef-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="d8bef-120">(Zobrazí se vám v [další části](modern-events.md) , který tato konvence je už nebudou vynucené.) Pokud váš typ události není nutné žádné další argumenty, se stále poskytovat oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="d8bef-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="d8bef-121">Je zvláštní hodnota `EventArgs.Empty` , používejte k označení, že události neobsahuje žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="d8bef-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="d8bef-122">Vytvořme třídu, která obsahuje seznam souborů v adresáři nebo některý z jeho podadresářů, které se řídí vzorem.</span><span class="sxs-lookup"><span data-stu-id="d8bef-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="d8bef-123">Tato součást vyvolává událost pro každý soubor nalezen odpovídající vzoru.</span><span class="sxs-lookup"><span data-stu-id="d8bef-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="d8bef-124">Použití modelu event obsahuje některé výhody návrhu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="d8bef-125">Můžete vytvořit víc naslouchacích procesů událostí, které provádí různé akce, když se najde soubor hledané kombinaci.</span><span class="sxs-lookup"><span data-stu-id="d8bef-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="d8bef-126">Kombinování různých naslouchacích procesů můžete vytvořit robustnější algoritmy.</span><span class="sxs-lookup"><span data-stu-id="d8bef-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="d8bef-127">Tady je počáteční událost deklaraci argumentu pro vyhledání souboru hledané kombinaci:</span><span class="sxs-lookup"><span data-stu-id="d8bef-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="d8bef-128">I v případě, že tento typ vypadá jako malé, pouze pro datový typ, by měl postupovat podle úmluvy a usnadňují odkaz (`class`) typu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="d8bef-129">To znamená, že objekt argument se předá odkazem a všechny aktualizace dat se můžou zobrazit všichni předplatitelé.</span><span class="sxs-lookup"><span data-stu-id="d8bef-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="d8bef-130">První verze je neměnný objekt.</span><span class="sxs-lookup"><span data-stu-id="d8bef-130">The first version is an immutable object.</span></span> <span data-ttu-id="d8bef-131">Měli dát přednost aby vlastnosti v váš typ argumentu události neměnné.</span><span class="sxs-lookup"><span data-stu-id="d8bef-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="d8bef-132">Tímto způsobem jednoho odběratele nelze změnit hodnoty, než je uvidí jiného předplatitele.</span><span class="sxs-lookup"><span data-stu-id="d8bef-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="d8bef-133">(Existují výjimky, jak uvidíte níže).</span><span class="sxs-lookup"><span data-stu-id="d8bef-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="d8bef-134">Dále musíme vytvořit deklaraci události ve třídě FileSearcher.</span><span class="sxs-lookup"><span data-stu-id="d8bef-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="d8bef-135">Využití `EventHandler<T>` typ znamená, že není nutné vytvořit další definici typu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="d8bef-136">Jednoduše použijte specializaci obecný.</span><span class="sxs-lookup"><span data-stu-id="d8bef-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="d8bef-137">Pojďme vyplňte FileSearcher třídy budou hledány soubory, které odpovídají vzoru a vyvolání správné události při zjištění shody.</span><span class="sxs-lookup"><span data-stu-id="d8bef-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="d8bef-138">Definování a vyvolávání událostí jako pole</span><span class="sxs-lookup"><span data-stu-id="d8bef-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="d8bef-139">Chcete-li tuto událost deklarovat jako veřejné pole, jako v předchozím příkladu je nejjednodušší způsob, jak přidat událost do vaší třídy:</span><span class="sxs-lookup"><span data-stu-id="d8bef-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="d8bef-140">Vypadá to na to je deklarace veřejné pole, které by se zdají být chybný postup objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="d8bef-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="d8bef-141">Chcete chránit přístup k datům prostřednictvím vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="d8bef-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="d8bef-142">Když to provést, vypadají, jako chybný postupem je kód generovaný kompilátorem vytváření obálek tak, aby objekty událostí lze přistupovat pouze v nouzovém způsoby.</span><span class="sxs-lookup"><span data-stu-id="d8bef-142">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="d8bef-143">Pouze operace dostupné na pole podobné události jsou přidat obslužnou rutinu:</span><span class="sxs-lookup"><span data-stu-id="d8bef-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="d8bef-144">a odebrat obslužnou rutinu:</span><span class="sxs-lookup"><span data-stu-id="d8bef-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="d8bef-145">Všimněte si, že je lokální proměnná pro obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="d8bef-146">Pokud jste použili tělo výrazu lambda, odebrat nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="d8bef-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="d8bef-147">To bude jinou instanci delegáta a tiše Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="d8bef-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="d8bef-148">Kód mimo třídy nemohou vyvolat události, ani provádět jiné operace.</span><span class="sxs-lookup"><span data-stu-id="d8bef-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="d8bef-149">Vrací hodnoty od odběratelů událostí</span><span class="sxs-lookup"><span data-stu-id="d8bef-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="d8bef-150">Jednoduchá verze funguje správně.</span><span class="sxs-lookup"><span data-stu-id="d8bef-150">Your simple version is working fine.</span></span> <span data-ttu-id="d8bef-151">Přidáme další funkce: Zrušení.</span><span class="sxs-lookup"><span data-stu-id="d8bef-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="d8bef-152">Při zvýšení nalezených událostí naslouchacích procesů měl zastaví další zpracování, pokud tento soubor je, že žádá o poslední z nich.</span><span class="sxs-lookup"><span data-stu-id="d8bef-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="d8bef-153">Obslužné rutiny událostí nesmí vracet hodnotu, proto musíte ke komunikaci, která jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d8bef-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="d8bef-154">Vzor standardních událostí používá objekt EventArgs pro zahrnutí polí, které odběratelů událostí můžete použít ke komunikaci Storno.</span><span class="sxs-lookup"><span data-stu-id="d8bef-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="d8bef-155">Existují dva různé vzorce, které mohou být využity, podle sémantiky smlouvy zrušit.</span><span class="sxs-lookup"><span data-stu-id="d8bef-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="d8bef-156">V obou případech přidáte pole boolean EventArguments nalezený soubor události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="d8bef-157">Jeden vzor by umožnilo jakékoli jednoho odběratele na zrušení operace.</span><span class="sxs-lookup"><span data-stu-id="d8bef-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="d8bef-158">Pro tento model je nové pole inicializovány na `false`.</span><span class="sxs-lookup"><span data-stu-id="d8bef-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="d8bef-159">Libovolný předplatitel lze změnit na `true`.</span><span class="sxs-lookup"><span data-stu-id="d8bef-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="d8bef-160">Po všichni předplatitelé viděli vyvolaná událost, součást FileSearcher prozkoumá logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="d8bef-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="d8bef-161">Druhý vzor by pouze zrušit operaci, pokud všichni předplatitelé operace byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="d8bef-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="d8bef-162">V tomto vzoru nové pole je inicializován do značí by měla operaci zrušit a libovolný předplatitel by mohl změnit označující, že by operace měla pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d8bef-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="d8bef-163">Po všichni předplatitelé viděli vyvolaná událost, součást FileSearcher prozkoumá logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="d8bef-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="d8bef-164">Existuje jeden další krok v tomto vzoru: součást potřebuje vědět, pokud jste viděli všechny předplatitele události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="d8bef-165">Pokud neexistují žádné předplatitele, pole by označoval zrušení nesprávně.</span><span class="sxs-lookup"><span data-stu-id="d8bef-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="d8bef-166">Můžeme implementovat první verzi pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="d8bef-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="d8bef-167">Je třeba přidat pole boolean s názvem `CancelRequested` k `FileFoundArgs` typu:</span><span class="sxs-lookup"><span data-stu-id="d8bef-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="d8bef-168">Toto nové pole je automaticky inicializován na `false`, výchozí hodnota pro pole Boolean, takže nezrušíte omylem.</span><span class="sxs-lookup"><span data-stu-id="d8bef-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="d8bef-169">Jediná další změna součást je kontrola příznak po vyvolání události pro zobrazení, pokud některý z odběratele odeslali žádost o zrušení:</span><span class="sxs-lookup"><span data-stu-id="d8bef-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="d8bef-170">Jednou z výhod tohoto modelu je, že to není zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="d8bef-171">Žádný odběratelů požadováno zrušení před a stále nejsou.</span><span class="sxs-lookup"><span data-stu-id="d8bef-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="d8bef-172">Žádný kód odběratele musí, aktualizaci, pokud chtějí podporují nový protokol Storno.</span><span class="sxs-lookup"><span data-stu-id="d8bef-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="d8bef-173">Je velmi volně vázány.</span><span class="sxs-lookup"><span data-stu-id="d8bef-173">It's very loosely coupled.</span></span>

<span data-ttu-id="d8bef-174">Umožňuje aktualizovat odběratele tak, aby požaduje zrušení, jakmile nalezne první spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="d8bef-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="d8bef-175">Přidání další deklarace událostí</span><span class="sxs-lookup"><span data-stu-id="d8bef-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="d8bef-176">Pojďme přidat jeden další funkce a ukazují další idiomy jazyk pro události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="d8bef-177">Přidejme přetížení `Search` metodu, která prochází přes všechny podadresáře při hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="d8bef-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="d8bef-178">To mohl být dlouhotrvající operace v adresáři s mnoha podadresáře.</span><span class="sxs-lookup"><span data-stu-id="d8bef-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="d8bef-179">Přidejme událost, která získá vyvolá, když začne každé nové prohledávání adresáře.</span><span class="sxs-lookup"><span data-stu-id="d8bef-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="d8bef-180">To umožňuje předplatitelům sledování průběhu a aktualizaci uživatele jde o průběhu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="d8bef-181">Všechny ukázky, které jste vytvořili zatím byly veřejné.</span><span class="sxs-lookup"><span data-stu-id="d8bef-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="d8bef-182">Vnitřní událost vytvoříme tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="d8bef-182">Let's make this one an internal event.</span></span> <span data-ttu-id="d8bef-183">To znamená, že můžete provést také typy používané pro interní argumenty také.</span><span class="sxs-lookup"><span data-stu-id="d8bef-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="d8bef-184">Začnete vytvořením nového EventArgs odvozené třídy pro vytváření sestav nový adresář a průběh.</span><span class="sxs-lookup"><span data-stu-id="d8bef-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="d8bef-185">Znovu postupujte podle doporučení pro nezměnitelný odkazový typ pro argumenty události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="d8bef-186">Dále definujte události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-186">Next, define the event.</span></span> <span data-ttu-id="d8bef-187">Tentokrát použijeme odlišnou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d8bef-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="d8bef-188">Kromě použití syntaxe pole, můžete explicitně vytvořit vlastnost, s přidat a odebrat obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="d8bef-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="d8bef-189">V této ukázce nebude potřebovat další kód v těchto obslužných rutinách, ale to ukazuje, jak by je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="d8bef-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="d8bef-190">V mnoha směrech kód, který napíšete zde zrcadlení, že kód, kompilátor vygeneruje pro definice pole událostí jste viděli dříve.</span><span class="sxs-lookup"><span data-stu-id="d8bef-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="d8bef-191">Vytvořit událost pomocí syntaxe velmi podobné, který používá pro [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="d8bef-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="d8bef-192">Všimněte si, že obslužných rutin mají odlišné názvy: `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="d8bef-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="d8bef-193">Nazývají se přihlášení k odběru události, nebo zrušit odběr události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="d8bef-194">Všimněte si, že je také třeba deklarovat privátní pomocné pole k uložení proměnné události.</span><span class="sxs-lookup"><span data-stu-id="d8bef-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="d8bef-195">Je inicializován na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d8bef-195">It is initialized to null.</span></span>

<span data-ttu-id="d8bef-196">V dalším kroku přidejme přetížení `Search` metodu, která prochází přes podadresářů a vyvolává obou událostí.</span><span class="sxs-lookup"><span data-stu-id="d8bef-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="d8bef-197">Nejjednodušší způsob, jak to provést, je výchozí argument použít k určení, zda chcete vyhledávat všechny adresáře:</span><span class="sxs-lookup"><span data-stu-id="d8bef-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="d8bef-198">V tomto okamžiku spustíte aplikaci volání přetížení pro vyhledávání všech podadresářích.</span><span class="sxs-lookup"><span data-stu-id="d8bef-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="d8bef-199">Nejsou žádné předplatitele na novém `ChangeDirectory` události, ale používat `?.Invoke()` idiom zajistí, že to funguje správně.</span><span class="sxs-lookup"><span data-stu-id="d8bef-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="d8bef-200">Přidejme obslužnou rutinu zapsat řádek, který zobrazuje průběh v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="d8bef-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="d8bef-201">Už víte, vzorů, které jsou použity v celém ekosystému .NET.</span><span class="sxs-lookup"><span data-stu-id="d8bef-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="d8bef-202">Podle studijního tyto vzory a konvence, budete psát idiomatickou C# a .NET rychle.</span><span class="sxs-lookup"><span data-stu-id="d8bef-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="d8bef-203">V dalším kroku se zobrazí některé změny v tyto vzory v nejnovější verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d8bef-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="d8bef-204">Next</span><span class="sxs-lookup"><span data-stu-id="d8bef-204">Next</span></span>](modern-events.md)
