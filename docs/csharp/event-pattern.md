---
title: Standardní vzory událostí .NET
description: Přečtěte si o vzorcích událostí rozhraní .NET a o tom, jak vytvořit standardní zdroje událostí a přihlásit se k odběru a zpracování standardních událostí ve vašem kódu.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: dec516767e43a6bf4edfa555e34f3adcc21a46e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146138"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="a2fb9-103">Standardní vzory událostí .NET</span><span class="sxs-lookup"><span data-stu-id="a2fb9-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="a2fb9-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="a2fb9-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="a2fb9-105">.NET události obecně postupujte několik známých vzorů.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="a2fb9-106">Standardizace na tyto vzory znamená, že vývojáři mohou využít znalosti těchto standardních vzorů, které lze použít pro libovolný program událostí .NET.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="a2fb9-107">Projděme si tyto standardní vzory, abyste měli všechny znalosti, které potřebujete k vytvoření standardních zdrojů událostí a k odběru a zpracování standardních událostí ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="a2fb9-108">Podpisy delegátů událostí</span><span class="sxs-lookup"><span data-stu-id="a2fb9-108">Event Delegate Signatures</span></span>

<span data-ttu-id="a2fb9-109">Standardní podpis delegáta události .NET je:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="a2fb9-110">Návratový typ je void.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-110">The return type is void.</span></span> <span data-ttu-id="a2fb9-111">Události jsou založeny na delegátech a jsou vícesměrové delegáty.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="a2fb9-112">To podporuje více odběratelů pro jakýkoli zdroj událostí.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="a2fb9-113">Jedna vrácená hodnota z metody nelze škálovat na více předplatitelů událostí.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="a2fb9-114">Jakou vrácenou hodnotu vidí zdroj události po vyvolání události?</span><span class="sxs-lookup"><span data-stu-id="a2fb9-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="a2fb9-115">Dále v tomto článku uvidíte, jak vytvořit protokoly událostí, které podporují předplatitele událostí, kteří hlásí informace zdroji událostí.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="a2fb9-116">Seznam argumentů obsahuje dva argumenty: odesílatele a argumenty události.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="a2fb9-117">Typ času `sender` kompilace `System.Object`je , i když pravděpodobně znáte odvozenější typ, který by byl vždy správný.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="a2fb9-118">Podle konvence `object`použijte .</span><span class="sxs-lookup"><span data-stu-id="a2fb9-118">By convention, use `object`.</span></span>

<span data-ttu-id="a2fb9-119">Druhý argument byl obvykle typ, který je `System.EventArgs`odvozen od .</span><span class="sxs-lookup"><span data-stu-id="a2fb9-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="a2fb9-120">(V [další části](modern-events.md) uvidíte, že tato konvence již není vynucena.) Pokud váš typ události nepotřebuje žádné další argumenty, budete stále poskytovat oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="a2fb9-121">Existuje zvláštní hodnota, `EventArgs.Empty` kterou byste měli použít k označení, že událost neobsahuje žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="a2fb9-122">Pojďme vytvořit třídu, která uvádí soubory v adresáři nebo některé z jeho podadresářů, které následují vzor.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="a2fb9-123">Tato součást vyvolá událost pro každý nalezený soubor, který odpovídá vzoru.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="a2fb9-124">Použití modelu událostí poskytuje některé výhody návrhu.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="a2fb9-125">Můžete vytvořit více posluchačů událostí, které provádějí různé akce při nalezení hleby souboru.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="a2fb9-126">Kombinace různých naslouchacích procesech můžete vytvořit robustnější algoritmy.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="a2fb9-127">Zde je počáteční argument události prohlášení pro nalezení hledaný soubor:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-127">Here is the initial event argument declaration for finding a sought file:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="a2fb9-128">I když tento typ vypadá jako malý typ pouze pro data, měli`class`byste dodržovat konvenci a vytvořit typ odkazu ( ).</span><span class="sxs-lookup"><span data-stu-id="a2fb9-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="a2fb9-129">To znamená, že argument objekt bude předán odkazem a všechny aktualizace dat budou zobrazeny všemi odběrateli.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="a2fb9-130">První verze je neměnný objekt.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-130">The first version is an immutable object.</span></span> <span data-ttu-id="a2fb9-131">Měli byste dát přednost tomu, aby vlastnosti v typu argumentu události byly neměnné.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="a2fb9-132">Tímto způsobem jeden odběratel nemůže změnit hodnoty dříve, než jiný odběratel vidí.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="a2fb9-133">(Existují výjimky, jak uvidíte níže.)</span><span class="sxs-lookup"><span data-stu-id="a2fb9-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="a2fb9-134">Dále musíme vytvořit deklaraci události ve třídě FileSearcher.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="a2fb9-135">Využití `EventHandler<T>` typu znamená, že není nutné vytvářet další definici typu.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="a2fb9-136">Jednoduše použijte obecnou specializaci.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="a2fb9-137">Vyplníme třídu FileSearcher a vyhledáme soubory, které odpovídají vzoru, a vyvoláme správnou událost, když je zjištěna shoda.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="a2fb9-138">Definování a zvyšování událostí podobných polím</span><span class="sxs-lookup"><span data-stu-id="a2fb9-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="a2fb9-139">Nejjednodušší způsob, jak přidat událost do třídy, je deklarovat tuto událost jako veřejné pole, jako v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="a2fb9-140">Vypadá to, že vyhlašuje veřejné pole, což se zdá být špatná objektově orientovaná praxe.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="a2fb9-141">Chcete chránit přístup k datům prostřednictvím vlastností nebo metod.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="a2fb9-142">I když to může vypadat jako špatný postup, kód generovaný kompilátorem vytvoří obálky tak, aby objekty událostí lze přistupovat pouze bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-142">While this may look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="a2fb9-143">Jediné operace, které jsou k dispozici na události podobné poli, jsou přidání obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="a2fb9-144">a odstranit obslužnou rutinu:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="a2fb9-145">Všimněte si, že je místní proměnná pro obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="a2fb9-146">Pokud jste použili tělo lambda, odstranění nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="a2fb9-147">Bylo by jiné instance delegáta a tiše nedělat nic.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="a2fb9-148">Kód mimo třídu nemůže vyvolat událost, ani nemůže provádět žádné jiné operace.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="a2fb9-149">Vrácení hodnot od odběratelů událostí</span><span class="sxs-lookup"><span data-stu-id="a2fb9-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="a2fb9-150">Vaše jednoduchá verze funguje dobře.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-150">Your simple version is working fine.</span></span> <span data-ttu-id="a2fb9-151">Přidáme další funkci: Zrušení.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="a2fb9-152">Při zvýšení nalezené události, posluchači by měl být schopen zastavit další zpracování, pokud tento soubor je, že poslední hledal.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="a2fb9-153">Obslužné rutiny události nevracejí hodnotu, takže je třeba komunikovat, že jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="a2fb9-154">Standardní vzor události používá EventArgs objekt zahrnout pole, která odběratelé událostí můžete použít ke komunikaci cancel.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="a2fb9-155">Existují dva různé vzory, které by mohly být použity na základě sémantiky smlouvy Zrušit.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="a2fb9-156">V obou případech přidáte logické pole do eventarguments pro událost nalezeného souboru.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span>

<span data-ttu-id="a2fb9-157">Jeden vzor by umožnil jednomu odběrateli zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="a2fb9-158">Pro tento vzor je nové pole `false`inicializováno na .</span><span class="sxs-lookup"><span data-stu-id="a2fb9-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="a2fb9-159">Každý odběratel jej `true`může změnit na .</span><span class="sxs-lookup"><span data-stu-id="a2fb9-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="a2fb9-160">Poté, co všichni odběratelé viděli událost aktivována, fileSearcher komponenty zkontroluje logickou hodnotu a provede akci.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="a2fb9-161">Druhý vzor by pouze zrušit operaci, pokud všichni předplatitelé chtěli operaci zrušena.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="a2fb9-162">V tomto vzoru je inicializováno nové pole označující, že operace by měla být zrušena, a každý odběratel by jej mohl změnit a označit tak, že by operace měla pokračovat.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="a2fb9-163">Poté, co všichni odběratelé viděli událost aktivována, fileSearcher komponenty zkontroluje logické a provede akci.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="a2fb9-164">Je jeden další krok v tomto vzoru: komponenta potřebuje vědět, pokud všichni předplatitelé viděli událost.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="a2fb9-165">Pokud neexistují žádné odběratelé, pole by znamenat zrušení nesprávně.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="a2fb9-166">Pojďme implementovat první verzi pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="a2fb9-167">Do `FileFoundArgs` typu je třeba přidat `CancelRequested` logické pole s názvem:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="a2fb9-168">Toto nové pole je `false`automaticky inicializováno na výchozí hodnotu logického pole, takže se nezrušíte omylem.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="a2fb9-169">Jedinou další změnou komponenty je zkontrolovat příznak po zvýšení události, abyste zjistili, zda některý z účastníků požádal o zrušení:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="a2fb9-170">Jednou z výhod tohoto vzoru je, že to není zásadní změna.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="a2fb9-171">Žádný z účastníků požádal o zrušení dříve, a stále nejsou.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="a2fb9-172">Žádný z kódu odběratele potřebuje aktualizaci, pokud chtějí podporovat nový protokol zrušení.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="a2fb9-173">Je to velmi volně svázané.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-173">It's very loosely coupled.</span></span>

<span data-ttu-id="a2fb9-174">Pojďme aktualizovat odběratele tak, aby požaduje zrušení, jakmile najde první spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="a2fb9-175">Přidání další deklarace události</span><span class="sxs-lookup"><span data-stu-id="a2fb9-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="a2fb9-176">Přidáme ještě jednu funkci a předvedeme další jazykové idiomy pro události.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="a2fb9-177">Přidáme přetížení `Search` metody, která prochází všechny podadresáře při hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="a2fb9-178">To by mohlo být zdlouhavé operace v adresáři s mnoha podadresářů.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="a2fb9-179">Přidáme událost, která se načte, když začne každé nové hledání adresáře.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="a2fb9-180">To umožňuje odběratelům sledovat průběh a aktualizovat uživatele, jak postupovat.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="a2fb9-181">Všechny vzorky, které jste zatím vytvořili, jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="a2fb9-182">Udělejme z toho vnitřní událost.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-182">Let's make this one an internal event.</span></span> <span data-ttu-id="a2fb9-183">To znamená, že můžete také vytvořit typy použité pro argumenty interní také.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="a2fb9-184">Začnete vytvořením nové třídy EventArgs odvozené pro hlášení nového adresáře a průběhu.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span>

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="a2fb9-185">Opět můžete postupovat podle doporučení, aby se neměnný typ odkazu pro argumenty události.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="a2fb9-186">Dále definujte událost.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-186">Next, define the event.</span></span> <span data-ttu-id="a2fb9-187">Tentokrát použijete jinou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="a2fb9-188">Kromě použití syntaxe pole můžete explicitně vytvořit vlastnost pomocí přidávejte a odeberte obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="a2fb9-189">V této ukázce nebudete potřebovat další kód v těchto obslužných rutin, ale to ukazuje, jak byste je vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="a2fb9-190">V mnoha ohledech kód, který zde napíšete, odráží kód, který kompilátor generuje pro definice událostí pole, které jste viděli dříve.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="a2fb9-191">Událost vytvoříte pomocí syntaxe velmi podobné syntaxi používané pro [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="a2fb9-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="a2fb9-192">Všimněte si, že obslužné rutiny mají různé názvy: `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="a2fb9-193">Ty jsou volány k odběru události, nebo odhlásit z akce.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="a2fb9-194">Všimněte si, že je také nutné deklarovat soukromé záložní pole pro uložení proměnné události.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="a2fb9-195">Je inicializován na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-195">It is initialized to null.</span></span>

<span data-ttu-id="a2fb9-196">Dále přidáme přetížení `Search` metody, která prochází podadresáře a vyvolává obě události.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="a2fb9-197">Nejjednodušší způsob, jak toho dosáhnout, je použít výchozí argument k určení, že chcete prohledávat všechny adresáře:</span><span class="sxs-lookup"><span data-stu-id="a2fb9-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="a2fb9-198">V tomto okamžiku můžete spustit aplikaci, která volá přetížení pro vyhledávání ve všech podadresářích.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="a2fb9-199">Na nové `ChangeDirectory` události nejsou žádní odběratelé, ale pomocí `?.Invoke()` idiomu zajistíte, že to funguje správně.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="a2fb9-200">Přidáme obslužnou rutinu k napsání řádku, který zobrazuje průběh v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-200">Let's add a handler to write a line that shows the progress in the console window.</span></span>

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="a2fb9-201">Viděli jste vzory, které jsou dodržovány v celém ekosystému .NET.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="a2fb9-202">Učením tyto vzory a konvence, budete psát idiomatické C# a .NET rychle.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="a2fb9-203">Dále uvidíte některé změny v těchto vzorcích v nejnovější verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a2fb9-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="a2fb9-204">Další</span><span class="sxs-lookup"><span data-stu-id="a2fb9-204">Next</span></span>](modern-events.md)
