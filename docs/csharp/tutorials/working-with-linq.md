---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte generovat sekvence pomocí LINQ, metody zápisu pro použití v dotazech LINQ a rozlišovat mezi Eager a opožděným hodnocením.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 3cbafbb6aeed3abdd6d83ead613b29de738d5604
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587175"
---
# <a name="working-with-linq"></a><span data-ttu-id="64ef9-103">Práce s jazykem LINQ</span><span class="sxs-lookup"><span data-stu-id="64ef9-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="64ef9-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="64ef9-104">Introduction</span></span>

<span data-ttu-id="64ef9-105">V tomto kurzu se naučíte funkcemi v .NET Core a C# v jazyce.</span><span class="sxs-lookup"><span data-stu-id="64ef9-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="64ef9-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="64ef9-106">You’ll learn:</span></span>

- <span data-ttu-id="64ef9-107">Jak generovat sekvence pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="64ef9-108">Jak zapisovat metody, které lze snadno použít v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="64ef9-109">Jak rozlišovat mezi Eager a opožděným hodnocením.</span><span class="sxs-lookup"><span data-stu-id="64ef9-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="64ef9-110">Tyto techniky se naučíte vytvořením aplikace, která předvádí jednu ze základních dovedností libovolného Magician: Faro se [náhodně](https://en.wikipedia.org/wiki/Faro_shuffle)rozhodnou.</span><span class="sxs-lookup"><span data-stu-id="64ef9-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="64ef9-111">Stručně je Faro náhodné, když rozdělíte balíček karet přesně na polovinu, pak se náhodně ponechá každou jednu kartu od poloviny a znovu sestaví původní balíček.</span><span class="sxs-lookup"><span data-stu-id="64ef9-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="64ef9-112">Magicians tento postup použijte, protože každá karta je ve známém umístění po každém náhodném umístění a pořadí je opakující se vzor.</span><span class="sxs-lookup"><span data-stu-id="64ef9-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="64ef9-113">Pro vaše účely je to světle srdce, které se používá při manipulaci s sekvencemi dat.</span><span class="sxs-lookup"><span data-stu-id="64ef9-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="64ef9-114">Aplikace, kterou sestavíte, vytvoří balíček karet a pak provede sekvenci přepisování a pokaždé zapíše sekvenci.</span><span class="sxs-lookup"><span data-stu-id="64ef9-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="64ef9-115">Také porovnáte aktualizované pořadí s původní objednávkou.</span><span class="sxs-lookup"><span data-stu-id="64ef9-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="64ef9-116">V tomto kurzu se používá několik kroků.</span><span class="sxs-lookup"><span data-stu-id="64ef9-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="64ef9-117">Po každém kroku můžete spustit aplikaci a zobrazit průběh.</span><span class="sxs-lookup"><span data-stu-id="64ef9-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="64ef9-118">V úložišti GitHub/Samples můžete také zobrazit [ukázku dokončeno](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) .</span><span class="sxs-lookup"><span data-stu-id="64ef9-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="64ef9-119">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="64ef9-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64ef9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64ef9-120">Prerequisites</span></span>

<span data-ttu-id="64ef9-121">Budete muset nastavit počítač, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64ef9-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="64ef9-122">Pokyny k instalaci najdete na stránce [.NET Core](https://www.microsoft.com/net/core) .</span><span class="sxs-lookup"><span data-stu-id="64ef9-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="64ef9-123">Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux, OS X nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="64ef9-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="64ef9-124">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="64ef9-125">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/) , což je Open Source Editor pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="64ef9-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="64ef9-126">Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.</span><span class="sxs-lookup"><span data-stu-id="64ef9-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="64ef9-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="64ef9-127">Create the Application</span></span>

<span data-ttu-id="64ef9-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="64ef9-128">The first step is to create a new application.</span></span> <span data-ttu-id="64ef9-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="64ef9-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="64ef9-130">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="64ef9-130">Make that the current directory.</span></span> <span data-ttu-id="64ef9-131">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="64ef9-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="64ef9-132">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="64ef9-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="64ef9-133">Pokud jste to ještě nikdy C# nepoužili, [Tento kurz](console-teleprompter.md) vysvětluje strukturu C# programu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="64ef9-134">Můžete si ho přečíst a pak se sem vrátit a získat další informace o LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="64ef9-135">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="64ef9-135">Creating the Data Set</span></span>

<span data-ttu-id="64ef9-136">Než začnete, ujistěte se, že jsou na začátku `Program.cs` souboru `dotnet new console`vygenerovaného na začátku následující řádky:</span><span class="sxs-lookup"><span data-stu-id="64ef9-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="64ef9-137">Pokud tyto tři řádky (`using` příkazy) nejsou v horní části souboru, náš program nebude zkompilován.</span><span class="sxs-lookup"><span data-stu-id="64ef9-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="64ef9-138">Teď, když máte všechny odkazy, které budete potřebovat, zvažte, co představuje balíček karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="64ef9-139">Balíčky hracích karet běžně obsahují čtyři barvy a každá z nich má třináct hodnot.</span><span class="sxs-lookup"><span data-stu-id="64ef9-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="64ef9-140">Za normálních okolností můžete zvážit vytvoření `Card` třídy přímo z bat a naplnění `Card` kolekce objektů ručně.</span><span class="sxs-lookup"><span data-stu-id="64ef9-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="64ef9-141">Pomocí LINQ můžete být výstižnější, než obvyklý způsob, jak řešit vytváření balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="64ef9-142">Namísto vytváření `Card` třídy můžete vytvořit dvě sekvence, které reprezentují barvy a pořadí.</span><span class="sxs-lookup"><span data-stu-id="64ef9-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="64ef9-143">Vytvoříte skutečně jednoduchou dvojici [*metod iterátoru*](../iterators.md#enumeration-sources-with-iterator-methods) , které budou generovat pořadí a obleky jako <xref:System.Collections.Generic.IEnumerable%601>s řetězci:</span><span class="sxs-lookup"><span data-stu-id="64ef9-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="64ef9-144">Umístěte je `Main` pod metodu `Program.cs` do souboru.</span><span class="sxs-lookup"><span data-stu-id="64ef9-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="64ef9-145">Tyto dvě metody používají `yield return` syntaxi k vytvoření sekvence při jejich spuštění.</span><span class="sxs-lookup"><span data-stu-id="64ef9-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="64ef9-146">Kompilátor vytvoří objekt, který implementuje <xref:System.Collections.Generic.IEnumerable%601> a vygeneruje posloupnost řetězců podle požadavků.</span><span class="sxs-lookup"><span data-stu-id="64ef9-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="64ef9-147">Nyní tyto metody iterátoru použijte k vytvoření balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="64ef9-148">Dotaz LINQ umístíte do naší `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="64ef9-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="64ef9-149">Tady se můžete podívat na:</span><span class="sxs-lookup"><span data-stu-id="64ef9-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="64ef9-150">Vícenásobné `from` klauzule <xref:System.Linq.Enumerable.SelectMany%2A>vytvoří, což vytvoří jednu sekvenci z kombinace každého elementu v první sekvenci s každým prvkem v druhé sekvenci.</span><span class="sxs-lookup"><span data-stu-id="64ef9-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="64ef9-151">Pořadí je důležité pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="64ef9-151">The order is important for our purposes.</span></span> <span data-ttu-id="64ef9-152">První prvek v první zdrojové sekvenci (barev) je kombinován s každým prvkem v druhé sekvenci (pořadí).</span><span class="sxs-lookup"><span data-stu-id="64ef9-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="64ef9-153">Tím se vytvoří všechny třinácté karty první barvy.</span><span class="sxs-lookup"><span data-stu-id="64ef9-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="64ef9-154">Tento proces se opakuje s každým prvkem v prvním pořadí (obleky).</span><span class="sxs-lookup"><span data-stu-id="64ef9-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="64ef9-155">Konečný výsledek je balíček karet seřazený podle obleku a za ním hodnoty.</span><span class="sxs-lookup"><span data-stu-id="64ef9-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="64ef9-156">Je důležité mít na paměti, že pokud se rozhodnete napsat svůj LINQ v syntaxi dotazu použitou výše, nebo místo toho použít syntaxi metody, je vždy možné přejít z jedné formy syntaxe do druhé.</span><span class="sxs-lookup"><span data-stu-id="64ef9-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="64ef9-157">Výše uvedený dotaz napsaný v syntaxi dotazu může být zapsaný v syntaxi metody jako:</span><span class="sxs-lookup"><span data-stu-id="64ef9-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="64ef9-158">Kompilátor překládá příkazy LINQ napsané pomocí syntaxe dotazu do ekvivalentní syntaxe volání metody.</span><span class="sxs-lookup"><span data-stu-id="64ef9-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="64ef9-159">Bez ohledu na zvolenou syntaxi si proto dvě verze dotazu vytvoří stejný výsledek.</span><span class="sxs-lookup"><span data-stu-id="64ef9-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="64ef9-160">Vyberte, která syntaxe je nejvhodnější pro vaši situaci: například pokud pracujete v týmu, kde někteří členové mají potíže se syntaxí metody, zkuste preferovat použití syntaxe dotazu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="64ef9-161">Pokračujte a spusťte ukázku, kterou jste v tomto okamžiku vytvořili.</span><span class="sxs-lookup"><span data-stu-id="64ef9-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="64ef9-162">V balíčku se zobrazí všechny karty 52.</span><span class="sxs-lookup"><span data-stu-id="64ef9-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="64ef9-163">Může být užitečné spustit tuto ukázku v rámci ladicího programu, aby bylo možné sledovat, `Suits()` jak `Ranks()` metody a jsou spouštěny.</span><span class="sxs-lookup"><span data-stu-id="64ef9-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="64ef9-164">Můžete jasně vidět, že každý řetězec v každé sekvenci je vygenerovaný pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="64ef9-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konzoly zobrazující, že aplikace vypisuje 52 karet.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="64ef9-166">Manipulace s objednávkou</span><span class="sxs-lookup"><span data-stu-id="64ef9-166">Manipulating the Order</span></span>

<span data-ttu-id="64ef9-167">V dalším kroku se zaměřte na to, jak se budou karty v balíčku přemíchat.</span><span class="sxs-lookup"><span data-stu-id="64ef9-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="64ef9-168">Prvním krokem v jakémkoli dobrým náhodném případě je rozdělení balíčku na dvě.</span><span class="sxs-lookup"><span data-stu-id="64ef9-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="64ef9-169">Metody <xref:System.Linq.Enumerable.Take%2A> a<xref:System.Linq.Enumerable.Skip%2A> , které jsou součástí rozhraní API LINQ, poskytují tuto funkci za vás.</span><span class="sxs-lookup"><span data-stu-id="64ef9-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="64ef9-170">Umístěte je pod `foreach` smyčku:</span><span class="sxs-lookup"><span data-stu-id="64ef9-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="64ef9-171">Neexistuje však žádná nepřesná metoda, která by se mohla využít ve standardní knihovně, takže budete muset napsat vlastní.</span><span class="sxs-lookup"><span data-stu-id="64ef9-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="64ef9-172">Metoda náhodně, kterou budete vytvářet, znázorňuje několik postupů, které budete používat s aplikacemi založenými na technologii LINQ, takže všechny části tohoto procesu budou vysvětleny v krocích.</span><span class="sxs-lookup"><span data-stu-id="64ef9-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="64ef9-173">Aby bylo možné přidat některé funkce k interakci s tím <xref:System.Collections.Generic.IEnumerable%601> , že se vrátíte z dotazů LINQ, budete muset napsat některé speciální druhy metod označované jako [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="64ef9-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="64ef9-174">Krátké metody rozšíření je *statická metoda* pro zvláštní účely, která přidává novou funkci do již existujícího typu bez nutnosti upravovat původní typ, do kterého chcete přidat funkci.</span><span class="sxs-lookup"><span data-stu-id="64ef9-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="64ef9-175">Poskytněte rozšiřující metody novému domu přidáním nového souboru *statické* třídy do programu s názvem `Extensions.cs`a pak začněte sestavovat první metodu rozšíření:</span><span class="sxs-lookup"><span data-stu-id="64ef9-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="64ef9-176">Podívejte se na signaturu metody za chvilku, konkrétně parametry:</span><span class="sxs-lookup"><span data-stu-id="64ef9-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="64ef9-177">Můžete zobrazit přidání `this` modifikátoru u prvního argumentu do metody.</span><span class="sxs-lookup"><span data-stu-id="64ef9-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="64ef9-178">To znamená, že zavoláte metodu, jako by šlo o členskou metodu typu prvního argumentu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="64ef9-179">Tato deklarace metody také následuje po standardním idiom, kde jsou `IEnumerable<T>`vstupní a výstupní typy.</span><span class="sxs-lookup"><span data-stu-id="64ef9-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="64ef9-180">Tento postup umožňuje zřetězení metod LINQ společně provádět složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="64ef9-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="64ef9-181">Přirozeně, vzhledem k tomu, že balíček rozdělíte na poloviny, budete muset spojit tyto poloviny dohromady.</span><span class="sxs-lookup"><span data-stu-id="64ef9-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="64ef9-182">V kódu to znamená, že budete vytvářet výčet obou sekvencí, které jste získali prostřednictvím <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> najednou, *`interleaving`* prvky a vytvořit jednu sekvenci: právě náhodně vytvořenou sadu karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="64ef9-183">Zápis metody LINQ, která funguje se dvěma sekvencemi, vyžaduje, abyste <xref:System.Collections.Generic.IEnumerable%601> pochopili, jak funguje.</span><span class="sxs-lookup"><span data-stu-id="64ef9-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="64ef9-184">Rozhraní má jednu metodu: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="64ef9-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="64ef9-185">Objekt vrácený funkcí <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="64ef9-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="64ef9-186">Tyto dva členy použijete k vytvoření výčtu kolekce a vrácení prvků.</span><span class="sxs-lookup"><span data-stu-id="64ef9-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="64ef9-187">Tato metoda prokládání bude metodou iterátoru, takže namísto sestavování kolekce a vrácení kolekce se použije `yield return` syntaxe uvedená výše.</span><span class="sxs-lookup"><span data-stu-id="64ef9-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="64ef9-188">Toto je implementace této metody:</span><span class="sxs-lookup"><span data-stu-id="64ef9-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="64ef9-189">Teď, když jste tuto metodu napsali, se vraťte do `Main` metody a náhodně ji zapněte:</span><span class="sxs-lookup"><span data-stu-id="64ef9-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="64ef9-190">Porovnání</span><span class="sxs-lookup"><span data-stu-id="64ef9-190">Comparisons</span></span>

<span data-ttu-id="64ef9-191">Kolik přeřazení trvá pro nastavení balíčku zpátky na původní objednávku?</span><span class="sxs-lookup"><span data-stu-id="64ef9-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="64ef9-192">Chcete-li zjistit, je nutné napsat metodu, která určuje, zda jsou dvě sekvence stejné.</span><span class="sxs-lookup"><span data-stu-id="64ef9-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="64ef9-193">Až tuto metodu použijete, budete muset umístit kód, který přeskočí balíček ve smyčce, a zkontrolujte, jestli je balíček zase v pořádku.</span><span class="sxs-lookup"><span data-stu-id="64ef9-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="64ef9-194">Zápis metody pro určení, zda jsou dvě sekvence stejné, by měly být jednoduché.</span><span class="sxs-lookup"><span data-stu-id="64ef9-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="64ef9-195">Je to podobná struktura jako metoda, kterou jste napsali pro přemístění balíčku.</span><span class="sxs-lookup"><span data-stu-id="64ef9-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="64ef9-196">Pouze tento čas, místo navýšení `yield return`každého prvku, porovnáte vyhovující prvky každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="64ef9-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="64ef9-197">Po vytvoření výčtu celé sekvence, pokud každý prvek odpovídá, jsou sekvence stejné:</span><span class="sxs-lookup"><span data-stu-id="64ef9-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="64ef9-198">To ukazuje druhou metodu LINQ idiom: Terminal.</span><span class="sxs-lookup"><span data-stu-id="64ef9-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="64ef9-199">Přebírají sekvenci jako vstup (nebo v tomto případě dvě sekvence) a vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="64ef9-200">Při použití metod terminálu jsou vždy poslední metodou v řetězci metod pro dotaz LINQ, tedy název "Terminal".</span><span class="sxs-lookup"><span data-stu-id="64ef9-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="64ef9-201">Tuto akci můžete zobrazit v akci, když ji použijete k určení, kdy se balíček vrátí v původním pořadí.</span><span class="sxs-lookup"><span data-stu-id="64ef9-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="64ef9-202">Vložte náhodně kód do smyčky a zastavte, když je sekvence zpět v původním pořadí `SequenceEquals()` , použitím metody.</span><span class="sxs-lookup"><span data-stu-id="64ef9-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="64ef9-203">Můžete vidět, že by to byla vždy konečná metoda v jakémkoli dotazu, protože vrací jednu hodnotu namísto sekvence:</span><span class="sxs-lookup"><span data-stu-id="64ef9-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="64ef9-204">Spusťte kód, který zatím máte, a poznamenejte si, jak se v každé náhodném uspořádání balíčku mění.</span><span class="sxs-lookup"><span data-stu-id="64ef9-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="64ef9-205">Po osmi přesunech (iterace smyčky do-while) se balíček vrátí do původní konfigurace, ve které byl při prvním vytvoření dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="64ef9-206">Optimalizace</span><span class="sxs-lookup"><span data-stu-id="64ef9-206">Optimizations</span></span>

<span data-ttu-id="64ef9-207">Ukázka, kterou jste sestavili tak daleko, se vykoná *náhodně*, kde karty Top a Bottom zůstanou stejné při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="64ef9-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="64ef9-208">Pojďme udělat jednu změnu: místo toho budeme používat *náhodně* , kde se na všech kartách 52 mění pozice.</span><span class="sxs-lookup"><span data-stu-id="64ef9-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="64ef9-209">V případě náhodného seřadíte balíček tak, že první karta v dolní polovině se bude první kartou v balíčku.</span><span class="sxs-lookup"><span data-stu-id="64ef9-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="64ef9-210">To znamená, že poslední karta v horní polovině se stala spodní kartou.</span><span class="sxs-lookup"><span data-stu-id="64ef9-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="64ef9-211">Toto je jednoduchá změna v jednotném řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="64ef9-212">Aktualizuje aktuální náhodný dotaz tak, že přepnete pozice <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="64ef9-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="64ef9-213">Tím se změní pořadí horních a dolních polovin balíčku:</span><span class="sxs-lookup"><span data-stu-id="64ef9-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="64ef9-214">Spusťte program znovu a uvidíte, že pro balíček bude trvat 52 iterací, aby se mohla změnit jejich uspořádání.</span><span class="sxs-lookup"><span data-stu-id="64ef9-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="64ef9-215">Začnete také všimnout některých vážných snížení výkonu, protože program pokračuje v běhu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="64ef9-216">To je několik důvodů.</span><span class="sxs-lookup"><span data-stu-id="64ef9-216">There are a number of reasons for this.</span></span> <span data-ttu-id="64ef9-217">Jedním z hlavních příčin tohoto poklesu výkonu můžete řešit: neefektivní použití [*opožděného vyhodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="64ef9-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="64ef9-218">Stručné a opožděné vyhodnocení uvádí, že vyhodnocení příkazu není provedeno, dokud není nutné zadat jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="64ef9-219">Dotazy LINQ jsou příkazy, které jsou vyhodnocovány laxně vytvářená.</span><span class="sxs-lookup"><span data-stu-id="64ef9-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="64ef9-220">Sekvence se generují pouze v případě, že jsou požadovány elementy.</span><span class="sxs-lookup"><span data-stu-id="64ef9-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="64ef9-221">Obvykle je to hlavní výhodou LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="64ef9-222">V takovém případě, jako je například tento program, způsobuje exponenciální nárůst v době spuštění.</span><span class="sxs-lookup"><span data-stu-id="64ef9-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="64ef9-223">Pamatujte na to, že jsme původní balíček vygenerovali pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="64ef9-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="64ef9-224">Každé náhodné volání je vygenerováno pomocí tří dotazů LINQ na předchozí palubě.</span><span class="sxs-lookup"><span data-stu-id="64ef9-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="64ef9-225">Všechny tyto kroky jsou prováděny laxně vytvářená.</span><span class="sxs-lookup"><span data-stu-id="64ef9-225">All these are performed lazily.</span></span> <span data-ttu-id="64ef9-226">To také znamená, že budou provedeny znovu při každém vyžádání sekvence.</span><span class="sxs-lookup"><span data-stu-id="64ef9-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="64ef9-227">V době, kdy se dostanete k iteraci 52nd, znovu vygenerujete původní balíček spoustou mnohokrát.</span><span class="sxs-lookup"><span data-stu-id="64ef9-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="64ef9-228">Pojďme napsat protokol, který demonstruje toto chování.</span><span class="sxs-lookup"><span data-stu-id="64ef9-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="64ef9-229">Pak ho opravíte.</span><span class="sxs-lookup"><span data-stu-id="64ef9-229">Then, you'll fix it.</span></span>

<span data-ttu-id="64ef9-230">`Extensions.cs` Do souboru zadejte nebo zkopírujte níže uvedenou metodu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="64ef9-231">Tato metoda rozšíření vytvoří nový soubor nazvaný `debug.log` v adresáři projektu a zaznamená, který dotaz je aktuálně prováděn do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="64ef9-232">Tato metoda rozšíření se dá připojit k libovolnému dotazu a označit tak, že se dotaz spustil.</span><span class="sxs-lookup"><span data-stu-id="64ef9-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="64ef9-233">V části `File`se zobrazí červená vlnovka, což znamená, že neexistuje.</span><span class="sxs-lookup"><span data-stu-id="64ef9-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="64ef9-234">Nebude zkompilován, protože kompilátor neví, co `File` je.</span><span class="sxs-lookup"><span data-stu-id="64ef9-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="64ef9-235">Chcete-li tento problém vyřešit, nezapomeňte přidat následující řádek kódu do prvního řádku v `Extensions.cs`:</span><span class="sxs-lookup"><span data-stu-id="64ef9-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="64ef9-236">To by mělo vyřešit problém a červená chyba zmizí.</span><span class="sxs-lookup"><span data-stu-id="64ef9-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="64ef9-237">V dalším kroku Instrumentujte definici každého dotazu pomocí zprávy protokolu:</span><span class="sxs-lookup"><span data-stu-id="64ef9-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="64ef9-238">Všimněte si, že při každém přístupu k dotazu nechcete protokolovat.</span><span class="sxs-lookup"><span data-stu-id="64ef9-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="64ef9-239">Protokolujte pouze v případě, že vytvoříte původní dotaz.</span><span class="sxs-lookup"><span data-stu-id="64ef9-239">You log only when you create the original query.</span></span> <span data-ttu-id="64ef9-240">Spuštění programu trvá delší dobu, ale nyní můžete zjistit, proč.</span><span class="sxs-lookup"><span data-stu-id="64ef9-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="64ef9-241">Pokud vyčerpáte z služby trpělivost s zapnutým protokolováním, přepněte zpět na náhodné.</span><span class="sxs-lookup"><span data-stu-id="64ef9-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="64ef9-242">Pořád se zobrazí efekty opožděného vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="64ef9-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="64ef9-243">V jednom spuštění se spustí 2592 dotazů, včetně veškeré generace hodnot a barev.</span><span class="sxs-lookup"><span data-stu-id="64ef9-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="64ef9-244">Můžete zvýšit výkon kódu zde, abyste snížili počet provedených provedení.</span><span class="sxs-lookup"><span data-stu-id="64ef9-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="64ef9-245">Jednoduchá oprava, kterou můžete udělat, je *Uložit do mezipaměti* výsledky původního dotazu LINQ, který sestaví balíček karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="64ef9-246">V současné době spouštíte dotazy znovu a znovu pokaždé, když smyčka do-while projde iterací, znovu se vytvoří balíček karet a znovu se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="64ef9-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="64ef9-247">Chcete-li uložit balíčky karet do mezipaměti, můžete využít metody <xref:System.Linq.Enumerable.ToArray%2A> LINQ a <xref:System.Linq.Enumerable.ToList%2A>; když je připojíte k dotazům, provedou stejné akce, které jste jim přihlásili, ale nyní uloží výsledky do pole nebo seznamu, podle toho, jakou metodu zvolíte volání.</span><span class="sxs-lookup"><span data-stu-id="64ef9-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="64ef9-248">Přidejte metodu <xref:System.Linq.Enumerable.ToArray%2A> LINQ do obou dotazů a spusťte program znovu:</span><span class="sxs-lookup"><span data-stu-id="64ef9-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="64ef9-249">Teď je vypínání na více než 30 dotazů.</span><span class="sxs-lookup"><span data-stu-id="64ef9-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="64ef9-250">Spusťte znovu s náhodným a uvidíte podobná vylepšení: teď spustí 162 dotazů.</span><span class="sxs-lookup"><span data-stu-id="64ef9-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="64ef9-251">Upozorňujeme, že tento příklad je **navržený** tak, aby zvýraznili případy použití, kdy může opožděné vyhodnocení způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="64ef9-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="64ef9-252">I když je důležité zjistit, kde opožděné hodnocení může ovlivnit výkon kódu, je stejně důležité pochopit, že ne všechny dotazy by měly běžet eagerly.</span><span class="sxs-lookup"><span data-stu-id="64ef9-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="64ef9-253">Dosažení výkonu, které jste provedete, nemusíte použít <xref:System.Linq.Enumerable.ToArray%2A> , protože každé nové uspořádání balíčku karet je sestavené z předchozího uspořádání.</span><span class="sxs-lookup"><span data-stu-id="64ef9-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="64ef9-254">Pomocí opožděného vyhodnocení znamená, že každá nová konfigurace balíčku je sestavena z původní balíčky, dokonce i v případě `startingDeck`, že je spuštěn kód, který vytvořil.</span><span class="sxs-lookup"><span data-stu-id="64ef9-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="64ef9-255">To způsobuje velké množství dodatečné práce.</span><span class="sxs-lookup"><span data-stu-id="64ef9-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="64ef9-256">V praxi některé algoritmy dobře fungují s využitím vyhodnocení Eager a jiné fungují i s opožděným hodnocením.</span><span class="sxs-lookup"><span data-stu-id="64ef9-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="64ef9-257">Pro každodenní použití je opožděné vyhodnocování obvykle lepší volbou, pokud je zdroj dat samostatným procesem, jako je databázový stroj.</span><span class="sxs-lookup"><span data-stu-id="64ef9-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="64ef9-258">Pro databáze, opožděné vyhodnocení umožňuje složitějším dotazům spustit pouze jednu zpáteční cestu k procesu databáze a vrátit se do zbytku kódu.</span><span class="sxs-lookup"><span data-stu-id="64ef9-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="64ef9-259">LINQ je flexibilní bez ohledu na to, jestli se rozhodnete používat opožděné nebo Eager vyhodnocení, takže Změřte své procesy a vyberte si, který typ hodnocení vám dává nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="64ef9-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="64ef9-260">Závěr</span><span class="sxs-lookup"><span data-stu-id="64ef9-260">Conclusion</span></span>

<span data-ttu-id="64ef9-261">V tomto projektu jste pokryli:</span><span class="sxs-lookup"><span data-stu-id="64ef9-261">In this project, you covered:</span></span>
- <span data-ttu-id="64ef9-262">použití dotazů LINQ k agregaci dat do smysluplné sekvence</span><span class="sxs-lookup"><span data-stu-id="64ef9-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="64ef9-263">zápis metod rozšíření pro přidání naší vlastní funkcionality do dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="64ef9-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="64ef9-264">Vyhledání oblastí v našem kódu, kde se můžou dotazy LINQ povést k problémům s výkonem, jako je snížená rychlost</span><span class="sxs-lookup"><span data-stu-id="64ef9-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="64ef9-265">opožděné a Eager vyhodnocení v souvislosti s dotazy LINQ a důsledky, které mohou mít při výkonu dotazů</span><span class="sxs-lookup"><span data-stu-id="64ef9-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="64ef9-266">Kromě technologie LINQ jste se dozvěděli o magicians techniky použití pro štychy karet.</span><span class="sxs-lookup"><span data-stu-id="64ef9-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="64ef9-267">Magicians použít Faro náhodně, protože může určovat, kde se každá karta v balíčku pohybuje.</span><span class="sxs-lookup"><span data-stu-id="64ef9-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="64ef9-268">Teď už víte, že si ho nevyřadíte pro všechny ostatní.</span><span class="sxs-lookup"><span data-stu-id="64ef9-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="64ef9-269">Další informace o LINQ najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="64ef9-269">For more information on LINQ, see:</span></span>
- [<span data-ttu-id="64ef9-270">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="64ef9-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="64ef9-271">Úvod do jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="64ef9-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="64ef9-272">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="64ef9-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [<span data-ttu-id="64ef9-273">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="64ef9-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [<span data-ttu-id="64ef9-274">Syntaxe dotazu a syntaxe metody v LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="64ef9-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [<span data-ttu-id="64ef9-275">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="64ef9-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
