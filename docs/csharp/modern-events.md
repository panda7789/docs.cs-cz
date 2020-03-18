---
title: Aktualizovaný vzor události jádra .NET
description: Zjistěte, jak vzor událostí .NET Core umožňuje flexibilitu se zpětnou kompatibilitou a jak implementovat bezpečné zpracování událostí s asynchronními odběrateli.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170433"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="a20b3-103">Aktualizovaný vzor události jádra .NET</span><span class="sxs-lookup"><span data-stu-id="a20b3-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="a20b3-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="a20b3-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="a20b3-105">V předchozím článku se diskutovalo o nejběžnější vzory událostí.</span><span class="sxs-lookup"><span data-stu-id="a20b3-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="a20b3-106">.NET Core má uvolněnější vzor.</span><span class="sxs-lookup"><span data-stu-id="a20b3-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="a20b3-107">V této verzi `EventHandler<TEventArgs>` definice již nemá `TEventArgs` omezení, které musí `System.EventArgs`být třídy odvozené z .</span><span class="sxs-lookup"><span data-stu-id="a20b3-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="a20b3-108">To zvyšuje flexibilitu pro vás a je zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="a20b3-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="a20b3-109">Začněme s flexibilitou.</span><span class="sxs-lookup"><span data-stu-id="a20b3-109">Let's start with the flexibility.</span></span> <span data-ttu-id="a20b3-110">Třída System.EventArgs zavádí jednu `MemberwiseClone()`metodu: , která vytvoří mělkou kopii objektu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="a20b3-111">Tato metoda musí použít reflexe za účelem implementace `EventArgs`jeho funkce pro všechny třídy odvozené z .</span><span class="sxs-lookup"><span data-stu-id="a20b3-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="a20b3-112">Tato funkce je jednodušší vytvořit v konkrétní odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="a20b3-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="a20b3-113">To skutečně znamená, že vyplývající z System.EventArgs je omezení, které omezuje vaše návrhy, ale neposkytuje žádné další výhody.</span><span class="sxs-lookup"><span data-stu-id="a20b3-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="a20b3-114">Ve skutečnosti můžete změnit definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby nebyly `EventArgs`odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="a20b3-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="a20b3-115">Program bude fungovat úplně stejně.</span><span class="sxs-lookup"><span data-stu-id="a20b3-115">The program will work exactly the same.</span></span>

<span data-ttu-id="a20b3-116">Můžete také změnit `SearchDirectoryArgs` na strukturu, pokud provedete ještě jednu změnu:</span><span class="sxs-lookup"><span data-stu-id="a20b3-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

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

<span data-ttu-id="a20b3-117">Další změnou je volání konstruktoru bez parametrů před zadáním konstruktoru, který inicializuje všechna pole.</span><span class="sxs-lookup"><span data-stu-id="a20b3-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="a20b3-118">Bez tohoto přidání by pravidla jazyka C# hlásila, že vlastnosti jsou přístupné před jejich přiřazením.</span><span class="sxs-lookup"><span data-stu-id="a20b3-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="a20b3-119">Neměli `FileFoundArgs` byste měnit z třídy (typ odkazu) na strukturu (typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="a20b3-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="a20b3-120">Je to proto, že protokol pro zpracování cancel vyžaduje, aby argumenty události byly předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="a20b3-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="a20b3-121">Pokud jste provedli stejnou změnu, třída vyhledávání souborů nikdy nemohla sledovat žádné změny provedené žádným z odběratelů události.</span><span class="sxs-lookup"><span data-stu-id="a20b3-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="a20b3-122">Pro každého odběratele by se použila nová kopie struktury a tato kopie by byla jinou kopií, než kterou viděl objekt hledání souboru.</span><span class="sxs-lookup"><span data-stu-id="a20b3-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="a20b3-123">Dále zvažme, jak může být tato změna zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="a20b3-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="a20b3-124">Odebrání omezení nemá vliv na existující kód.</span><span class="sxs-lookup"><span data-stu-id="a20b3-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="a20b3-125">Všechny existující typy argumentů `System.EventArgs`události stále odvozují z .</span><span class="sxs-lookup"><span data-stu-id="a20b3-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="a20b3-126">Zpětná kompatibilita je jedním z hlavních `System.EventArgs`důvodů, proč budou i nadále odvodit z .</span><span class="sxs-lookup"><span data-stu-id="a20b3-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="a20b3-127">Všechny existující předplatitelé událostí budou předplatiteli události, která následovala klasický vzor.</span><span class="sxs-lookup"><span data-stu-id="a20b3-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="a20b3-128">Podle podobné logiky by žádný typ argumentu události vytvořený nyní neměl žádné předplatitele v existujících základech kódu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="a20b3-129">Nové typy událostí, které `System.EventArgs` nejsou odvozeny z nepřeruší tyto základy kódu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="a20b3-130">Události s odběrateli aplikace Async</span><span class="sxs-lookup"><span data-stu-id="a20b3-130">Events with Async subscribers</span></span>

<span data-ttu-id="a20b3-131">Máte jeden konečný vzor se učit: Jak správně psát předplatitele událostí, které volají asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="a20b3-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="a20b3-132">Výzva je popsána v článku o [asynchronní a čekají](async.md).</span><span class="sxs-lookup"><span data-stu-id="a20b3-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="a20b3-133">Asynchronní metody mohou mít prázdný návratový typ, ale to se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="a20b3-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="a20b3-134">Když váš kód účastníka události volá asynchronní metodu, nemáte jinou možnost než vytvořit metodu. `async void`</span><span class="sxs-lookup"><span data-stu-id="a20b3-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="a20b3-135">Podpis obslužné rutiny události to vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="a20b3-135">The event handler signature requires it.</span></span>

<span data-ttu-id="a20b3-136">Musíte se smířit s tímto protichůdným vedením.</span><span class="sxs-lookup"><span data-stu-id="a20b3-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="a20b3-137">Nějak musíte vytvořit bezpečnou `async void` metodu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="a20b3-138">Základy vzoru, které je třeba implementovat, jsou níže:</span><span class="sxs-lookup"><span data-stu-id="a20b3-138">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="a20b3-139">Nejprve si všimněte, že obslužná rutina je označena jako asynchronní obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="a20b3-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="a20b3-140">Vzhledem k tomu, že je přiřazen k typu delegáta obslužné rutiny události, bude mít prázdný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a20b3-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="a20b3-141">To znamená, že je nutné sledovat vzor uvedený v obslužné rutině a nepovolit žádné výjimky, které mají být vyvolány z kontextu obslužné rutiny asynchronní.</span><span class="sxs-lookup"><span data-stu-id="a20b3-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="a20b3-142">Vzhledem k tomu, že nevrátí úkol, neexistuje žádný úkol, který může hlásit chybu zadáním chybového stavu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="a20b3-143">Vzhledem k tomu, že metoda je asynchronní, metoda nemůže jednoduše vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="a20b3-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="a20b3-144">(Volající metoda pokračovala v provádění, `async`protože je .) Skutečné chování za běhu bude definováno odlišně pro různá prostředí.</span><span class="sxs-lookup"><span data-stu-id="a20b3-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="a20b3-145">Může ukončit vlákno nebo proces, který vlastní vlákno, nebo ponechat proces v neurčitém stavu.</span><span class="sxs-lookup"><span data-stu-id="a20b3-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="a20b3-146">Všechny tyto potenciální výsledky jsou velmi nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="a20b3-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="a20b3-147">To je důvod, proč byste měli zabalit příkaz await pro asynchronní úlohu ve vlastním bloku try.</span><span class="sxs-lookup"><span data-stu-id="a20b3-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="a20b3-148">Pokud to způsobí chybnou úlohu, můžete chybu protokolovat.</span><span class="sxs-lookup"><span data-stu-id="a20b3-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="a20b3-149">Pokud se jedná o chybu, ze které se aplikace nemůže zotavit, můžete program rychle a elegantně ukončit.</span><span class="sxs-lookup"><span data-stu-id="a20b3-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="a20b3-150">Jedná se o hlavní aktualizace vzoru událostí .NET.</span><span class="sxs-lookup"><span data-stu-id="a20b3-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="a20b3-151">Zobrazí se mnoho příkladů starších verzí v knihovnách, se kterými pracujete.</span><span class="sxs-lookup"><span data-stu-id="a20b3-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="a20b3-152">Měli byste však také pochopit, jaké jsou nejnovější vzory.</span><span class="sxs-lookup"><span data-stu-id="a20b3-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="a20b3-153">Další článek v této sérii vám `delegates` `events` pomůže rozlišovat mezi použitím a ve vašich návrzích.</span><span class="sxs-lookup"><span data-stu-id="a20b3-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="a20b3-154">Jsou to podobné koncepty, a že článek vám pomůže učinit nejlepší rozhodnutí pro vaše programy.</span><span class="sxs-lookup"><span data-stu-id="a20b3-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="a20b3-155">Další</span><span class="sxs-lookup"><span data-stu-id="a20b3-155">Next</span></span>](distinguish-delegates-events.md)
