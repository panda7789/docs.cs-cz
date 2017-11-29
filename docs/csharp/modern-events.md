---
title: "Vzor aktualizované .NET Core událostí"
description: "Zjistěte, jak vzor událostí .NET Core umožňuje flexibilitu s zpětné kompatibility a jak implementovat zpracování událostí bezpečné s async odběratele."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="97b17-104">Vzor aktualizované .NET Core událostí</span><span class="sxs-lookup"><span data-stu-id="97b17-104">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="97b17-105">Předchozí</span><span class="sxs-lookup"><span data-stu-id="97b17-105">Previous</span></span>](event-pattern.md)

<span data-ttu-id="97b17-106">V předchozím článku popsané nejčastější události vzory.</span><span class="sxs-lookup"><span data-stu-id="97b17-106">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="97b17-107">.NET core má více volný vzor.</span><span class="sxs-lookup"><span data-stu-id="97b17-107">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="97b17-108">V této verzi `EventHandler<TEventArgs>` definice již obsahuje omezení, `TEventArgs` musí být třída odvozená z `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="97b17-108">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="97b17-109">To zvyšuje flexibilitu pro vás a je zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="97b17-109">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="97b17-110">Začněme flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="97b17-110">Let's start with the flexibility.</span></span> <span data-ttu-id="97b17-111">Třída System.EventArgs představuje jedno z těchto metod: `MemberwiseClone()`, která vytvoří kopii objektu bez podstruktury.</span><span class="sxs-lookup"><span data-stu-id="97b17-111">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="97b17-112">Zda metoda musí používat reflexe kvůli implementaci jeho funkce pro všechny třídy odvozené od `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="97b17-112">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="97b17-113">Které tuto funkci je snazší vytvářet konkrétní odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="97b17-113">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="97b17-114">To efektivně znamená, že odvozování z System.EventArgs je omezení, které omezuje návrhů, ale neposkytuje žádné další výhody.</span><span class="sxs-lookup"><span data-stu-id="97b17-114">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="97b17-115">Ve skutečnosti, můžete změny definice `FileFoundArgs` a `SearchDirectoryArgs` tak, aby není odvozena od `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="97b17-115">In fact, you can changes the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="97b17-116">Tento program bude fungovat stejně.</span><span class="sxs-lookup"><span data-stu-id="97b17-116">The program will work exactly the same.</span></span>

<span data-ttu-id="97b17-117">Můžete také změnit `SearchDirectoryArgs` do struktury, pokud jste provedli také jeden další změny:</span><span class="sxs-lookup"><span data-stu-id="97b17-117">You could also change the `SearchDirectoryArgs` to a struct, if you also make one more change:</span></span>

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

<span data-ttu-id="97b17-118">Další změnou je volat výchozí konstruktor před vstupem konstruktor, který inicializuje všechna pole.</span><span class="sxs-lookup"><span data-stu-id="97b17-118">The additional change is to call the default constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="97b17-119">Bez přidání by pravidla jazyka C# hlásit, že vlastnosti přistupuje předtím, než byla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="97b17-119">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="97b17-120">Byste neměli měnit `FileFoundArgs` z třídy (odkaz) za účelem struktury (typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="97b17-120">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="97b17-121">Je to způsobeno protokol pro zpracování Storno vyžaduje, že jsou argumenty událostí předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="97b17-121">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="97b17-122">Pokud jste provedli stejnou změnu, může třída vyhledávání souboru nikdy sledovat veškeré změny provedené žádné události odběratelů.</span><span class="sxs-lookup"><span data-stu-id="97b17-122">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="97b17-123">Novou kopii struktura se použije pro každý odběratele a tato kopie bude kopii jiný než ten, který pohledu hledání objektu soubor.</span><span class="sxs-lookup"><span data-stu-id="97b17-123">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="97b17-124">Dále zvažte, jak může být tato změna zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="97b17-124">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="97b17-125">Odebrání omezení nemá vliv na existující kód.</span><span class="sxs-lookup"><span data-stu-id="97b17-125">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="97b17-126">Všechny existující typy argumentů událostí stále odvozena od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="97b17-126">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="97b17-127">Zpětné kompatibility je jedním z hlavních důvodů proč budou i nadále odvozena od `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="97b17-127">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="97b17-128">Všechny existující události odběratelé nebudou odběratele, kteří mají na událost, která postupovali podle vzoru classic.</span><span class="sxs-lookup"><span data-stu-id="97b17-128">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="97b17-129">Všechny následující podobné logiku základy argumentu události vytvořen nyní neměli všechny odběratele v jakékoli existující kódu.</span><span class="sxs-lookup"><span data-stu-id="97b17-129">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="97b17-130">Nové typy událostí, které není odvozena od `System.EventArgs` není zalomení ty základy kódu.</span><span class="sxs-lookup"><span data-stu-id="97b17-130">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="97b17-131">Události se asynchronní odběratele</span><span class="sxs-lookup"><span data-stu-id="97b17-131">Events with Async subscribers</span></span>

<span data-ttu-id="97b17-132">Máte jeden konečné vzor Další: jak napsat správně události odběratele, které volají asynchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="97b17-132">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="97b17-133">Na výzvu je popsána v článku na [async a operátoru await](async.md).</span><span class="sxs-lookup"><span data-stu-id="97b17-133">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="97b17-134">Asynchronní metody může mít typ vrácené hodnoty void, ale který se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="97b17-134">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="97b17-135">Pokud váš kód odběratele událostí volá asynchronní metody, máte žádná volba však vytvořit `async void` metoda.</span><span class="sxs-lookup"><span data-stu-id="97b17-135">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="97b17-136">Podpis obslužné rutiny událostí vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="97b17-136">The event handler signature requires it.</span></span>

<span data-ttu-id="97b17-137">Je třeba sjednotit dosáhnout návod.</span><span class="sxs-lookup"><span data-stu-id="97b17-137">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="97b17-138">Nějakým způsobem, je nutné vytvořit sejfu `async void` metoda.</span><span class="sxs-lookup"><span data-stu-id="97b17-138">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="97b17-139">Základní informace o vzor, který je nutné implementovat jsou níže:</span><span class="sxs-lookup"><span data-stu-id="97b17-139">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="97b17-140">Všimněte si nejprve, aby obslužná rutina je označen jako obslužné rutiny asynchronní.</span><span class="sxs-lookup"><span data-stu-id="97b17-140">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="97b17-141">Protože je právě přiřazován na obslužnou rutinu události typ delegáta, bude mít typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="97b17-141">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="97b17-142">To znamená, že musíte podle vzoru zobrazovaného v obslužné rutině a nepovolíte jakékoli výjimky vyvolání mimo kontext asynchronní obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="97b17-142">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="97b17-143">Protože nevrátí úlohu, není žádná úloha, která může hlásit chyby zadáním chybný stav.</span><span class="sxs-lookup"><span data-stu-id="97b17-143">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="97b17-144">Jelikož metodou, je asynchronní, nelze vyvolat metodu jednoduše výjimka.</span><span class="sxs-lookup"><span data-stu-id="97b17-144">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="97b17-145">(Volání metody pokračuje spuštění, protože je `async`.) Skutečné modul runtime chování budou jinak určené pro různá prostředí.</span><span class="sxs-lookup"><span data-stu-id="97b17-145">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="97b17-146">Ukončovat vlákno, ukončovat program nebo program může zanechat v neurčeném stavu.</span><span class="sxs-lookup"><span data-stu-id="97b17-146">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="97b17-147">Žádný z nich není funkční výstupy.</span><span class="sxs-lookup"><span data-stu-id="97b17-147">None of those are good outcomes.</span></span>

<span data-ttu-id="97b17-148">To je důvod, proč má obtékat příkaz await pro asynchronní úlohu v vlastní bloku try.</span><span class="sxs-lookup"><span data-stu-id="97b17-148">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="97b17-149">Pokud ho způsobit úlohu chybný, můžou přihlásit k chybě.</span><span class="sxs-lookup"><span data-stu-id="97b17-149">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="97b17-150">Jedná se o chybu, ze kterého nelze obnovit vaše aplikace, můžete ukončit program rychle a elegantně</span><span class="sxs-lookup"><span data-stu-id="97b17-150">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="97b17-151">Ty jsou hlavní aktualizace se vzorem událostí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="97b17-151">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="97b17-152">Zobrazí se mnoho příkladů starší verze v knihovnách, se kterými můžete pracovat.</span><span class="sxs-lookup"><span data-stu-id="97b17-152">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="97b17-153">Nicméně byste měli porozumět, co nejnovější vzory jsou také.</span><span class="sxs-lookup"><span data-stu-id="97b17-153">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="97b17-154">Další článek z této série umožňuje rozlišovat pomocí `delegates` a `events` v návrzích.</span><span class="sxs-lookup"><span data-stu-id="97b17-154">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="97b17-155">Jsou podobné koncepty a tento článek vám pomůže zajistit nejlepší rozhodnutí pro vaše programy.</span><span class="sxs-lookup"><span data-stu-id="97b17-155">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="97b17-156">Další</span><span class="sxs-lookup"><span data-stu-id="97b17-156">Next</span></span>](distinguish-delegates-events.md)
