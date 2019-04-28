---
title: Vzor události aktualizované rozhraní .NET Core
description: Zjistěte, jak vzor události .NET Core umožňuje flexibilitu s zpětné kompatibility a jak implementovat zpracování bezpečné událostí s asynchronní odběrateli.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 5c7b9b4cb9bc22a73b865c45e225ce5c382380b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652036"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="dde99-103">Vzor události aktualizované rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="dde99-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="dde99-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="dde99-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="dde99-105">Předchozí článek byl věnován nejběžnější vzory událostí.</span><span class="sxs-lookup"><span data-stu-id="dde99-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="dde99-106">.NET core má více volný vzor.</span><span class="sxs-lookup"><span data-stu-id="dde99-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="dde99-107">V této verzi `EventHandler<TEventArgs>` definice již obsahuje omezení, která `TEventArgs` musí být třída odvozená z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="dde99-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="dde99-108">To zvyšuje flexibilitu pro vás a je zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="dde99-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="dde99-109">Začněme s flexibilitou.</span><span class="sxs-lookup"><span data-stu-id="dde99-109">Let's start with the flexibility.</span></span> <span data-ttu-id="dde99-110">Třída System.EventArgs představuje jednu metodu: `MemberwiseClone()`, která vytvoří Mělkou kopii objektu.</span><span class="sxs-lookup"><span data-stu-id="dde99-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="dde99-111">Že metoda musí používat reflexe kvůli implementaci jeho funkce pro všechny třídy odvozené z `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="dde99-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="dde99-112">Je snazší vytvářet v konkrétní odvozené třídy, které tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="dde99-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="dde99-113">Který efektivně znamená, že odvozený od System.EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.</span><span class="sxs-lookup"><span data-stu-id="dde99-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="dde99-114">Ve skutečnosti může změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby není odvozen od `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="dde99-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="dde99-115">Program bude fungovat stejně.</span><span class="sxs-lookup"><span data-stu-id="dde99-115">The program will work exactly the same.</span></span>

<span data-ttu-id="dde99-116">Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud jste provedli jednu další změny:</span><span class="sxs-lookup"><span data-stu-id="dde99-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

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

<span data-ttu-id="dde99-117">Další změnou je volat konstruktor bez parametrů před zadáním konstruktor, který inicializuje všechna pole.</span><span class="sxs-lookup"><span data-stu-id="dde99-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="dde99-118">Bez tohoto přidání pravidel C# zasílat zprávy, že vlastnosti přistupuje předtím, než jí byla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="dde99-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="dde99-119">Byste neměli měnit `FileFoundArgs` ze třídy (odkaz) na strukturu (typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="dde99-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="dde99-120">Důvodem je, protokol pro zpracování zrušení vyžaduje, aby událost argumenty jsou předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="dde99-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="dde99-121">Pokud jste provedli stejnou změnu, třída hledání souborů může nikdy sledovat všechny změny provedené ve všech odběratelů událostí.</span><span class="sxs-lookup"><span data-stu-id="dde99-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="dde99-122">Novou kopii struktura se použije pro každý předplatitel, a tuto kopii by kopii jiný než ten, který viděli vyhledávací objektem file.</span><span class="sxs-lookup"><span data-stu-id="dde99-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="dde99-123">Dále zvažte, jak tato změna může být zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="dde99-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="dde99-124">Odebrání omezení nemá vliv na žádný existující kód.</span><span class="sxs-lookup"><span data-stu-id="dde99-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="dde99-125">Všechny existující typy argumentů události stále odvozovat `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="dde99-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="dde99-126">Zpětné kompatibility je jeden hlavní důvod, proč budou i nadále odvozovat `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="dde99-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="dde99-127">Všechny existující události předplatitelé budou mít Odběratelé událost, která a Klasický model.</span><span class="sxs-lookup"><span data-stu-id="dde99-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="dde99-128">Po každém podobnou logiku základů kódu vytvořen nyní nemusí všechny předplatitele v jakékoli existující argumentu události.</span><span class="sxs-lookup"><span data-stu-id="dde99-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="dde99-129">Nové typy událostí, které nejsou odvozeny od `System.EventArgs` není konec ty základů kódu.</span><span class="sxs-lookup"><span data-stu-id="dde99-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="dde99-130">Události Async předplatitele</span><span class="sxs-lookup"><span data-stu-id="dde99-130">Events with Async subscribers</span></span>

<span data-ttu-id="dde99-131">Máte jeden poslední vzorek se dozvíte: Jak správně psát odběratelů událostí, které volají asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="dde99-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="dde99-132">Na výzvu je popsaný v článku na [async a operátoru await](async.md).</span><span class="sxs-lookup"><span data-stu-id="dde99-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="dde99-133">Asynchronní metody může mít návratový typ void, ale je důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="dde99-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="dde99-134">Po události odběratele kód volá asynchronní metodu, budete mít žádná volba ale k vytvoření `async void` metody.</span><span class="sxs-lookup"><span data-stu-id="dde99-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="dde99-135">To vyžaduje podpisu obsluhy události.</span><span class="sxs-lookup"><span data-stu-id="dde99-135">The event handler signature requires it.</span></span>

<span data-ttu-id="dde99-136">Je potřeba sloučit tyto dosáhnout doprovodné materiály.</span><span class="sxs-lookup"><span data-stu-id="dde99-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="dde99-137">Nějakým způsobem, je nutné vytvořit bezpečný `async void` metody.</span><span class="sxs-lookup"><span data-stu-id="dde99-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="dde99-138">Základní informace, které potřebujete k implementaci vzoru jsou níže:</span><span class="sxs-lookup"><span data-stu-id="dde99-138">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="dde99-139">Napřed si všimněte, že obslužná rutina je označen jako asynchronní obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="dde99-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="dde99-140">Protože se přiřazuje k obslužné rutině události typ delegáta, bude mít typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="dde99-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="dde99-141">To znamená musí postupovat podle vzor, uvedený v obslužné rutině a, aby všechny výjimky, která je vyvolána mimo kontext asynchronní obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="dde99-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="dde99-142">Protože úloha nevrací, neexistuje žádný úkol, který můžete nahlásit chybu tak, že zadáte chybovém stavu.</span><span class="sxs-lookup"><span data-stu-id="dde99-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="dde99-143">Vzhledem k tomu, že je metoda asynchronní, nelze metodu jednoduše vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="dde99-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="dde99-144">(Volání metody pokračuje provádění, protože je `async`.) Chování skutečné za běhu bude být definovány rozdílně pro různá prostředí.</span><span class="sxs-lookup"><span data-stu-id="dde99-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="dde99-145">Ho může ukončit vlákno, se může ukončit program nebo program může zanechat v neurčeném stavu.</span><span class="sxs-lookup"><span data-stu-id="dde99-145">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="dde99-146">Žádná z nich jsou dobré výsledky.</span><span class="sxs-lookup"><span data-stu-id="dde99-146">None of those are good outcomes.</span></span>

<span data-ttu-id="dde99-147">To je důvod, proč zalamován příkazu await pro asynchronní úlohy ve vlastním bloku try.</span><span class="sxs-lookup"><span data-stu-id="dde99-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="dde99-148">Pokud to způsobit chybnou úloh, můžete protokolovat chyby.</span><span class="sxs-lookup"><span data-stu-id="dde99-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="dde99-149">Jedná se o chybu, ze kterého nelze obnovit vaše aplikace, můžete ukončit program snadno a bez výpadku</span><span class="sxs-lookup"><span data-stu-id="dde99-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="dde99-150">Toto jsou hlavní aktualizace vzor události .NET.</span><span class="sxs-lookup"><span data-stu-id="dde99-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="dde99-151">Mnoho příkladů z dřívějších verzí knihoven, které při práci s se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="dde99-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="dde99-152">Nicméně byste měli rozumět, co nejnovější vzory jsou také.</span><span class="sxs-lookup"><span data-stu-id="dde99-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="dde99-153">Další článek v této sérii umožňuje rozlišit mezi použitím `delegates` a `events` v návrzích.</span><span class="sxs-lookup"><span data-stu-id="dde99-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="dde99-154">Jsou podobné koncepty a tento článek vám pomůže vytvořit nejlepší rozhodnutí pro vaše programy.</span><span class="sxs-lookup"><span data-stu-id="dde99-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="dde99-155">Next</span><span class="sxs-lookup"><span data-stu-id="dde99-155">Next</span></span>](distinguish-delegates-events.md)
