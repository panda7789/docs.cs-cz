---
title: Aktualizovaný vzor událostí .NET Core
description: Přečtěte si, jak vzor událostí .NET Core umožňuje flexibilitu proti zpětné kompatibilitě a implementaci bezpečného zpracování událostí s využitím asynchronních předplatitelů.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: a916a09b622f8df9bf99fafe52f35c706220f484
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039793"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="4a7f5-103">Aktualizovaný vzor událostí .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a7f5-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="4a7f5-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="4a7f5-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="4a7f5-105">Předchozí článek pojednává o nejběžnějších vzorech událostí.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="4a7f5-106">.NET Core má uvolněný vzor.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="4a7f5-107">V této verzi již definice `EventHandler<TEventArgs>` nemá omezení, které `TEventArgs` musí být třída odvozená z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="4a7f5-108">Tím se zvyšuje flexibilita a je zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="4a7f5-109">Pojďme začít s flexibilitou.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-109">Let's start with the flexibility.</span></span> <span data-ttu-id="4a7f5-110">Třída System. EventArgs zavádí jednu z metod: `MemberwiseClone()`, která vytvoří kopii objektu bez podstruktury.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="4a7f5-111">Tato metoda musí použít reflexi pro implementaci své funkce pro jakoukoliv třídu odvozenou z `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="4a7f5-112">Tuto funkci je snazší vytvořit v konkrétní odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="4a7f5-113">To efektivně znamená, že odvozený od System. EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="4a7f5-114">Ve skutečnosti můžete změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, že nejsou odvozeny od `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="4a7f5-115">Program bude fungovat přesně stejně.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-115">The program will work exactly the same.</span></span>

<span data-ttu-id="4a7f5-116">Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud uděláte jednu změnu:</span><span class="sxs-lookup"><span data-stu-id="4a7f5-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="4a7f5-117">Další změnou je volat konstruktor bez parametrů před vstupem do konstruktoru, který inicializuje všechna pole.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="4a7f5-118">Bez toho, aby se tato pravidla C# přidala, se před přiřazením k vlastnostem hlásí, že se k nim přistupovaly.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="4a7f5-119">Neměňte `FileFoundArgs` z třídy (typu odkazu) na strukturu (typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="4a7f5-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="4a7f5-120">Důvodem je, že protokol pro zpracování zrušení vyžaduje, aby byly argumenty události předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="4a7f5-121">Pokud jste provedli stejnou změnu, třída hledání souborů nemůže nikdy sledovat žádné změny provedené u žádného odběratele události.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="4a7f5-122">Pro každého předplatitele by se použila nová kopie struktury a tato kopie by byla jinou kopií než ta, kterou vyhledává objekt hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="4a7f5-123">Nyní zvažte, jak tato změna může být zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="4a7f5-124">Odebrání omezení neovlivní žádný existující kód.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="4a7f5-125">Všechny existující typy argumentů události jsou stále odvozeny od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="4a7f5-126">Zpětná kompatibilita je jedním z hlavních důvodů, proč se budou nadále odvozovat z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="4a7f5-127">Všechna stávající předplatitelé událostí budou předplatitelé události, která následovala za klasickým vzorem.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="4a7f5-128">Po podobné logice by jakýkoli typ argumentu události, který teď vytvořil, neměl žádné předplatitele v existujících základech kódu.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="4a7f5-129">Nové typy událostí, které nejsou odvozeny od `System.EventArgs`, nebudou tyto základy kódu přerušit.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="4a7f5-130">Události s asynchronními předplatiteli</span><span class="sxs-lookup"><span data-stu-id="4a7f5-130">Events with Async subscribers</span></span>

<span data-ttu-id="4a7f5-131">Máte jeden finální vzor k získání informací o tom, jak správně napsat předplatitele událostí volající asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="4a7f5-132">Tato výzva je popsaná v článku o [Async a await](async.md).</span><span class="sxs-lookup"><span data-stu-id="4a7f5-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="4a7f5-133">Asynchronní metody mohou mít návratový typ void, ale to se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="4a7f5-134">Když kód předplatitele události volá asynchronní metodu, nemáte žádnou volbu, ale chcete vytvořit metodu `async void`.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="4a7f5-135">Podpis obslužné rutiny události vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-135">The event handler signature requires it.</span></span>

<span data-ttu-id="4a7f5-136">Je nutné sjednotit tyto protichůdné doprovodné materiály.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="4a7f5-137">V některých případech je nutné vytvořit bezpečnou `async void` metodu.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="4a7f5-138">Níže je uveden seznam základních principů, které je třeba implementovat:</span><span class="sxs-lookup"><span data-stu-id="4a7f5-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="4a7f5-139">Nejprve si všimněte, že obslužná rutina je označena jako asynchronní obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="4a7f5-140">Protože je přiřazen k typu delegáta události, bude mít návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="4a7f5-141">To znamená, že je nutné postupovat podle vzoru zobrazeného v obslužné rutině a neumožňovat vyvolání výjimek z kontextu asynchronní obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="4a7f5-142">Protože nevrací úlohu, není k dispozici žádná úloha, která by mohla ohlásit chybu zadáním chybového stavu.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="4a7f5-143">Vzhledem k tomu, že metoda je asynchronní, metoda nemůže jednoduše vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="4a7f5-144">(Metoda volání pokračuje v provádění, protože je `async`.) Skutečné chování za běhu bude definováno pro různá prostředí odlišně.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="4a7f5-145">Může ukončit vlákno nebo proces, který vlastní vlákno, nebo nechat proces v neurčitém stavu.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="4a7f5-146">Všechny tyto potenciální výsledky jsou vysoce nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="4a7f5-147">To je důvod, proč byste měli zabalit příkaz await pro asynchronní úlohu ve vlastním bloku try.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="4a7f5-148">Pokud dojde k selhání úlohy, můžete chybu zaznamenat.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="4a7f5-149">Pokud se jedná o chybu, ze které se aplikace nemůže zotavit, můžete rychle a řádně ukončit program.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="4a7f5-150">Ty jsou hlavní aktualizace pro vzorek událostí .NET.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="4a7f5-151">V knihovnách, ve kterých pracujete, se zobrazí mnoho příkladů předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="4a7f5-152">Měli byste se ale seznámit s tím, co mají i nejnovější vzory.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="4a7f5-153">Další článek v této sérii vám pomůže rozlišovat mezi používáním `delegates` a `events` v návrzích.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="4a7f5-154">Jsou to podobné koncepty a tento článek vám pomůže udělat si nejlepší rozhodnutí pro vaše programy.</span><span class="sxs-lookup"><span data-stu-id="4a7f5-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="4a7f5-155">Next</span><span class="sxs-lookup"><span data-stu-id="4a7f5-155">Next</span></span>](distinguish-delegates-events.md)
