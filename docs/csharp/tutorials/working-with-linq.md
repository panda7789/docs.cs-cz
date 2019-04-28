---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, Zapsat metody pro použití v dotazech LINQ a rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: d6dbe158c5f9b474dbd2cc61982ab8e23e584ec7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675609"
---
# <a name="working-with-linq"></a><span data-ttu-id="cd3cc-103">Práce s jazykem LINQ</span><span class="sxs-lookup"><span data-stu-id="cd3cc-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="cd3cc-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="cd3cc-104">Introduction</span></span>

<span data-ttu-id="cd3cc-105">V tomto kurzu se naučíte, funkce v .NET Core a C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="cd3cc-106">Získáte informace:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-106">You’ll learn:</span></span>

- <span data-ttu-id="cd3cc-107">Jak vygenerovat pořadí pomocí jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="cd3cc-108">Jak napsat metody, které můžete snadno použít v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="cd3cc-109">Jak rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="cd3cc-110">Vytvořením aplikace, která ukazuje jednu základní dovednosti jakékoli magician dozvíte těchto technik: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="cd3cc-111">Stručně řečeno náhodně faro je technika, kde rozdělit karet přesně na polovinu a pak shuffle předřadí jednotlivých karet z každého půl k opětovnému sestavení z původního balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="cd3cc-112">Magicians tento postup použít, protože všechny karty je v zadaném umístění po jednotlivých shuffle a pořadí je s opakováním vzoru.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="cd3cc-113">Pro účely je slabá hearted podívejte se na zpracování data sekvencí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="cd3cc-114">Aplikace, kterou vytvoříte bude sestavení karet a pak proveďte posloupnost podle okolí posouvá, zápis si pokaždé, když je pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="cd3cc-115">Budete také porovnat aktualizované aby původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="cd3cc-116">V tomto kurzu má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="cd3cc-117">Po provedení každého kroku můžete spustit aplikaci a sledovat průběh.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="cd3cc-118">Můžete zobrazit také [úplnou vzorovou](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti dotnet/samples GitHub.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="cd3cc-119">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd3cc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd3cc-120">Prerequisites</span></span>

<span data-ttu-id="cd3cc-121">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="cd3cc-122">Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="cd3cc-123">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="cd3cc-124">Bude potřeba nainstalovat váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="cd3cc-125">Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="cd3cc-126">Ale můžete použít jakýkoli nástroje jste obeznámeni.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="cd3cc-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="cd3cc-127">Create the Application</span></span>

<span data-ttu-id="cd3cc-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-128">The first step is to create a new application.</span></span> <span data-ttu-id="cd3cc-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="cd3cc-130">Ujistěte se, že do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-130">Make that the current directory.</span></span> <span data-ttu-id="cd3cc-131">Zadejte příkaz `dotnet new console` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="cd3cc-132">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="cd3cc-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="cd3cc-133">Pokud jste nikdy C#, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="cd3cc-134">Může číst a pak se sem vraťte pro další informace o jazyku LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="cd3cc-135">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="cd3cc-135">Creating the Data Set</span></span>

<span data-ttu-id="cd3cc-136">Než začnete, ujistěte se, že v horní části jsou následující řádky `Program.cs` soubor generovaný nástrojem `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="cd3cc-137">Pokud tyto tři řádky (`using` příkazy) nejsou v horní části souboru, nebude kompilovat náš program.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="cd3cc-138">Teď, když máte všechny odkazy, které budete potřebovat, vezměte v úvahu informace o tom, co balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="cd3cc-139">Běžně balíčku hracích kartách obsahuje čtyři barvy a každou barvu má třináct hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="cd3cc-140">Za normálních okolností zvažte vytvoření `Card` třídy přímo vypnuto bat a naplnění kolekce `Card` objekty ručně.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="cd3cc-141">S dotazy LINQ může být stručnější než obvyklým způsobem řešení problémů s vytvořením balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="cd3cc-142">Místo vytváření `Card` třídy, můžete vytvořit dvěma sekvencemi k reprezentaci sady a pořadí, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-142">Instead of creating a `Card` class, you can create two sequences to represent suites and ranks, respectively.</span></span> <span data-ttu-id="cd3cc-143">Vytvoříte opravdu jednoduchý dvojici [ *iterátory* ](../iterators.md#enumeration-sources-with-iterator-methods) , který bude generovat pořadí a barvy jako <xref:System.Collections.Generic.IEnumerable%601>s řetězců:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="cd3cc-144">Tyto pod umístit `Main` metoda ve vaší `Program.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="cd3cc-145">Tyto dvě metody jak využívat `yield return` syntaxi pro vytvoření sekvence za běhu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="cd3cc-146">Kompilátor vytvoří objekt, který implementuje <xref:System.Collections.Generic.IEnumerable%601> a generuje posloupnost řetězců, jako jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="cd3cc-147">Tyto metody iterátoru teď použijte k vytvoření balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="cd3cc-148">Umístíte dotazu LINQ v našich `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="cd3cc-149">Tady se můžete podívat na to:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-149">Here's a look at it:</span></span>

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

<span data-ttu-id="cd3cc-150">Násobek `from` klauzule vytvářejí <xref:System.Linq.Enumerable.SelectMany%2A>, vytváří jeden pořadí z kombinace každý prvek v první řadě se každý prvek v druhé pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="cd3cc-151">Pořadí je důležité pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-151">The order is important for our purposes.</span></span> <span data-ttu-id="cd3cc-152">První prvek v první zdrojové sekvence (barvy) číslo zkombinuje s každý prvek v druhé pořadí (pořadí).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="cd3cc-153">Tímto se vytvoří všechny karty třináct první barvy.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="cd3cc-154">Tento proces se opakuje ke každému elementu v první řadě (barvy).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="cd3cc-155">Konečný výsledek je balíčku karet seřazené podle barvy, za nímž následuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="cd3cc-156">Je důležité mít na paměti, že ať rozhodnout pro zápis LINQ v syntaxi dotazů využité nad nebo použití syntaxe využívající metody místo toho, je vždy možné přejít z jednu formu syntaxe na druhý.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="cd3cc-157">Výše uvedené dotazy napsané v syntaxi dotazů je možné psát v syntaxe využívající metody jako:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="cd3cc-158">Kompilátor překládá příkazy LINQ, které jsou napsané v syntaxi dotazů v syntaxi volání ekvivalentní metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="cd3cc-159">Bez ohledu na vaši volbu syntaxe proto dvě verze dotaz přinesou stejný výsledek.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="cd3cc-160">Zvolte, které syntaxe je nejvhodnější pro vaši situaci: pro instanci, pokud pracujete v týmu, kde některé členy mají potíže s syntaxe využívající metody, zkuste raději pomocí syntaxe dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="cd3cc-161">Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="cd3cc-162">Zobrazí se všechny 52 karty z balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="cd3cc-163">Může být pro vás velmi užitečné v ladicím programu sledovat tuto ukázku spustit jak `Suits()` a `Ranks()` provedení metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="cd3cc-164">Je jasně vidět, že každého řetězce v každé pořadí se vygeneruje pouze dle potřeby.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okna konzoly zobrazuje aplikaci výpisu 52 karet.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="cd3cc-166">Manipulace s pořadí</span><span class="sxs-lookup"><span data-stu-id="cd3cc-166">Manipulating the Order</span></span>

<span data-ttu-id="cd3cc-167">V dalším kroku se zaměřují na způsob se chystáte shuffle karty z balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="cd3cc-168">Prvním krokem při libovolné vhodné shuffle je rozdělit z balíčku ve dvou.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="cd3cc-169"><xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> metody, které jsou součástí rozhraní API LINQ poskytují tuto funkci za vás.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="cd3cc-170">Je pod umístit `foreach` smyčka:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="cd3cc-171">Neexistuje však žádná metoda shuffle výhod ve standardní knihovně, proto budete muset napsat vlastní.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="cd3cc-172">Shuffle metodu, kterou vytvoříte ukazuje několik technik, které budete používat s aplikací založených na LINQ, každá součást tohoto procesu bude popsanou v krocích.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="cd3cc-173">Chcete-li přidat některé funkce, jak pracovat <xref:System.Collections.Generic.IEnumerable%601> získáte zpět z dotazů LINQ, budete muset napsat nějakou zvláštní druhy metod volá [rozšiřující metody](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="cd3cc-174">Stručně řečeno, rozšiřující metoda je zvláštní účely *statickou metodu* , který přidává nové funkce na typ, který již existuje bez nutnosti upravovat původní typ, který chcete přidat funkce.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="cd3cc-175">Rozšiřující metody poskytují nový domov tak, že přidáte nový *statické* soubor třídy do vaší aplikace s názvem `Extensions.cs`a pak začít vytvářet out první – metoda rozšíření:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="cd3cc-176">Podívejte se na podpis metody na chvíli zastavíme, konkrétně parametry:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="cd3cc-177">Zobrazí se přidání `this` modifikátor v prvním argumentu k metodě.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="cd3cc-178">To znamená, že volání metody, jako by šlo o metodu člen typu prvního argumentu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="cd3cc-179">Tato metoda také následuje po deklaraci standardní idiom kde vstupní a výstupní typy jsou `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="cd3cc-180">Že postup umožňuje metody LINQ na možné zřetězit dohromady a provádět složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="cd3cc-181">Přirozeně protože rozdělení z balíčku na polovina se uloží, bude potřeba připojit k těmto polovina se uloží společně.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="cd3cc-182">V kódu, to znamená, že je budete výčet, obě sekvencí, které jste získali prostřednictvím <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> najednou, *`interleaving`* elementy a vytvoření jednoho pořadí: vaše nyní – které se náhodně pomíchají balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="cd3cc-183">Zápis LINQ metodu, která funguje s dvěma sekvencemi vyžaduje pochopit, jak <xref:System.Collections.Generic.IEnumerable%601> funguje.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="cd3cc-184"><xref:System.Collections.Generic.IEnumerable%601> Rozhraní má jednu metodu: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="cd3cc-185">Objekt vrácený rutinou <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="cd3cc-186">Tyto dva členy použije k vytvoření výčtu kolekce a vrátí prvky.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="cd3cc-187">Tato metoda prokládání bude metodu iterátoru, místo vytváření kolekce a vrátí kolekci, které použijete `yield return` syntaxe uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="cd3cc-188">Tady je implementace této metody:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="cd3cc-189">Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a shuffle jednou z balíčku:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="cd3cc-190">Porovnání</span><span class="sxs-lookup"><span data-stu-id="cd3cc-190">Comparisons</span></span>

<span data-ttu-id="cd3cc-191">Kolik podle okolí posouvá trvá, než k nastavení z balíčku zpět na jeho původní pořadí?</span><span class="sxs-lookup"><span data-stu-id="cd3cc-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="cd3cc-192">Chcete-li zjistit, budete potřebovat napíše metoda, která určuje, jestli dvě sekvence jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="cd3cc-193">Jakmile budete mít tuto metodu, budete muset umístěte kód, který posouvá z balíčku ve smyčce a zkontrolujte, pokud je balíček zpět v pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="cd3cc-194">Zápis metodou ke zjištění, jestli dané dvě sekvence jsou stejné by měl být jednoduché.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="cd3cc-195">Je podobné struktury metody, který jste napsali přesouvat z balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="cd3cc-196">Pouze to čas, namísto `yield return`ing každý prvek budete porovnávat odpovídajících prvků každé posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="cd3cc-197">Když celé sekvenci vytvoření výčtu, pokud každý prvek odpovídá, sekvencí jsou stejné:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="cd3cc-198">Zobrazí se druhé idiom LINQ: terminálu metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="cd3cc-199">Přijmout sekvenci jako vstup (nebo v tomto případě dvou sekvencí) a vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="cd3cc-200">Při použití terminálu metody, jsou vždy finální metoda v řetězci metody pro LINQ dotaz, tedy název "terminálu".</span><span class="sxs-lookup"><span data-stu-id="cd3cc-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="cd3cc-201">Vidíte to v akci při použití pro určení, kdy z balíčku je zpět do její původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="cd3cc-202">Shuffle kód uvnitř smyčky a zastavit, když sekvence je zpět do její původní pořadí s použitím `SequenceEquals()` metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="cd3cc-203">Vidíte, že by měl být vždy finální metoda každého dotazu, protože se vrací jedinou hodnotu místo sekvenci:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="cd3cc-204">Spusťte kód nechte zatím a poznamenejte si hodnotu jak z balíčku uspořádá na každý náhodně.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="cd3cc-205">Po 8 podle okolí posouvá (iterací provést-smyčku while), balíček vrátí původní konfiguraci, v jaké byl při jeho prvním vytvoření počátečního dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="cd3cc-206">Optimalizace</span><span class="sxs-lookup"><span data-stu-id="cd3cc-206">Optimizations</span></span>

<span data-ttu-id="cd3cc-207">Ukázka, začlenění zatím provede *si shuffle*, kde horní a dolní části karty zůstat stejná při každém běhu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="cd3cc-208">Vytvoříme jednu změnu: použijeme *v shuffle* místo, kde všechny 52 karty změní pozici.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="cd3cc-209">Pro v náhodně, můžete prokládání z balíčku tak, aby první karta v dolní polovině stane první karta balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="cd3cc-210">To znamená, že poslední karty v horní polovině stane dolní části karty.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="cd3cc-211">Jedná se o jednoduchou změnu singulární řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="cd3cc-212">Aktualizovat aktuální dotaz shuffle díky přepínání podle polohy <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="cd3cc-213">Tím se změní pořadí horní a dolní polovinami z balíčku:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="cd3cc-214">Spusťte program znovu, a uvidíte, že trvá 52 iterací z balíčku můžete změnit pořadí samotný.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="cd3cc-215">Budete také začít Všimněte si, že některé jak výkon jako program nadále běží.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="cd3cc-216">Existuje několik důvodů.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-216">There are a number of reasons for this.</span></span> <span data-ttu-id="cd3cc-217">Můžete řešit jeden z hlavních příčin toto snížení výkonu: neefektivní používání šablon [ *opožděné vyhodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd3cc-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="cd3cc-218">Stručně řečeno opožděné vyhodnocení uvádí, že se neprovádí vyhodnocení výrazu, dokud jeho hodnota je potřeba.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="cd3cc-219">Dotazy LINQ jsou příkazy, které jsou vyhodnocovány laxně.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="cd3cc-220">Sekvence jsou generovány pouze v případě, že prvky jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="cd3cc-221">Který je obvykle hlavní výhodou LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="cd3cc-222">Ale používá jako je například tento program, to způsobí, že exponenciální růst v čase spuštění.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="cd3cc-223">Mějte na paměti, že jsme generována z původního balíčku pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="cd3cc-224">Každý shuffle je generována pomocí provádí tři LINQ dotazy na předchozí balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="cd3cc-225">Všechny tyto laxně probíhají.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-225">All these are performed lazily.</span></span> <span data-ttu-id="cd3cc-226">To také znamená, že se že provádějí se znovu pokaždé, když je požadováno sekvence.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="cd3cc-227">Podle času, který jste získali 52nd iteraci můžete se znova se generuje z původního balíčku mnoho, v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="cd3cc-228">Napíšeme protokolu demonstrují toto chování.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="cd3cc-229">Nakonec vám to vyřešíme.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-229">Then, you'll fix it.</span></span>

<span data-ttu-id="cd3cc-230">Ve vaší `Extensions.cs` soubor, zadejte nebo zkopírujte následující metody.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="cd3cc-231">Tato metoda rozšíření vytvoří nový soubor s názvem `debug.log` v adresáři projektu a záznamů je právě prováděna jaký dotaz do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="cd3cc-232">Tato metoda rozšíření může být přidán k jakýkoli dotaz k označení, že dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="cd3cc-233">V dalším kroku instrumentace definici každého dotazu s zprávu protokolu:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-233">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="cd3cc-234">Všimněte si, že není přihlásíte pokaždé, když se přístup k dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-234">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="cd3cc-235">Přihlášení jenom při vytváření původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-235">You log only when you create the original query.</span></span> <span data-ttu-id="cd3cc-236">Program stále trvá dlouhou dobu pro spuštění, ale teď se zobrazí důvod, proč.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-236">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="cd3cc-237">Pokud vyčerpáte trpělivost s protokolování zapnuté, přepínač mimo shuffle v náhodně.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-237">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="cd3cc-238">Dál uvidíte účinky opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-238">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="cd3cc-239">Během jednoho spuštění se provede 2592 dotazů, včetně všech generování hodnoty a barvy.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-239">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="cd3cc-240">Můžete zvýšit výkon kódu tady ke snížení počtu spuštění, které provedete.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-240">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="cd3cc-241">Můžete provést jednoduché opravy je *mezipaměti* výsledky původního dotazu LINQ, který Konstruuje balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-241">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="cd3cc-242">V současné době provedete dotazy znovu a znovu pokaždé, když – smyčky prochází iterace, opětovné vytváření balíčku karet a promísení ho pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-242">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="cd3cc-243">Pro ukládání do mezipaměti balíčku karet, můžete využít metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> a <xref:System.Linq.Enumerable.ToList%2A>; Pokud připojit dotazů, že budete provádět stejné akce, které jim má, ale teď budete ukládají výsledky v poli, nebo seznam, v závislosti na tom, jakou metodu můžete volat.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-243">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="cd3cc-244">Append – metoda LINQ <xref:System.Linq.Enumerable.ToArray%2A> na dotazy a znovu spustit program:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-244">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="cd3cc-245">Nyní je mimo shuffle až 30 dotazy.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-245">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="cd3cc-246">Spusťte znovu s v shuffle a zobrazí se vám podobná vylepšení: teď provede 162 dotazy.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-246">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="cd3cc-247">Upozorňujeme, že v tomto příkladu je **navržené** zvýrazněte případy použití, pokud opožděné vyhodnocení může způsobit potíže s výkonem.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-247">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="cd3cc-248">I když je důležité, pokud chcete zobrazit, pokud opožděné vyhodnocení může mít vliv na výkon kódu, je stejně důležité, abyste pochopili, že ne všechny dotazy vykonat například.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-248">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="cd3cc-249">Výkon přístupů, které se vám účtovat bez použití <xref:System.Linq.Enumerable.ToArray%2A> je vzhledem k tomu, že každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-249">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="cd3cc-250">Použití opožděné vyhodnocení znamená každou novou konfiguraci balíčku je sestaven z původního balíčku, i spouští kód, který založená `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-250">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="cd3cc-251">Který způsobí, že velké množství práce navíc.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-251">That causes a large amount of extra work.</span></span>

<span data-ttu-id="cd3cc-252">V praxi některé algoritmy spustit také pomocí nemůžou dočkat, až hodnocení a jiné systém dobře při používání opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-252">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="cd3cc-253">Za denní využití opožděné vyhodnocení je obvykle lepší volbou, pokud je zdroj dat jako samostatný proces, jako je databázový stroj.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-253">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="cd3cc-254">Pro databáze opožděné vyhodnocení umožňuje vytvářet složitější dotazy spuštění pouze jedné odezvy k procesu databáze a zpět do zbytku kódu.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-254">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="cd3cc-255">LINQ je flexibilní, jestli rozhodnete využívat opožděné nebo nemůžou dočkat, až hodnocení, tak měření vašich procesů a vyberte si libovolný typ vyhodnocení poskytuje nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-255">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="cd3cc-256">Závěr</span><span class="sxs-lookup"><span data-stu-id="cd3cc-256">Conclusion</span></span>

<span data-ttu-id="cd3cc-257">V tomto projektu pro vás řešení:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-257">In this project, you covered:</span></span>
- <span data-ttu-id="cd3cc-258">pomocí dotazů LINQ pro agregovaná data na smysluplné sekvenci</span><span class="sxs-lookup"><span data-stu-id="cd3cc-258">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="cd3cc-259">zápis rozšiřující metody pro přidání našich vlastních funkcí do dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="cd3cc-259">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="cd3cc-260">Vyhledání oblastí v našem kódu, kde náš dotazů LINQ narazit na problémy s výkonem, jako je snížení rychlosti</span><span class="sxs-lookup"><span data-stu-id="cd3cc-260">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="cd3cc-261">opožděné a nemůžou dočkat, až hodnocení související s dotazy LINQ a důsledky mohou mít na výkon dotazů</span><span class="sxs-lookup"><span data-stu-id="cd3cc-261">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="cd3cc-262">Kromě LINQ jste se dozvěděli něco o použití magicians techniku pro triky karty.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-262">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="cd3cc-263">Magicians Faro shuffle použít, protože můžete určit, kde prochází všechny karty z balíčku.</span><span class="sxs-lookup"><span data-stu-id="cd3cc-263">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="cd3cc-264">Když teď víte, nemusíte ho znehodnotit pro všechny ostatní!</span><span class="sxs-lookup"><span data-stu-id="cd3cc-264">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="cd3cc-265">Další informace o LINQ naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="cd3cc-265">For more information on LINQ, see:</span></span>
- [<span data-ttu-id="cd3cc-266">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="cd3cc-266">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="cd3cc-267">Úvod do jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="cd3cc-267">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/introduction-to-linq.md)
  - [<span data-ttu-id="cd3cc-268">Začínáme s dotazy LINQ vC#</span><span class="sxs-lookup"><span data-stu-id="cd3cc-268">Getting Started With LINQ in C#</span></span>](../programming-guide/concepts/linq/getting-started-with-linq.md)
    - [<span data-ttu-id="cd3cc-269">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="cd3cc-269">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
    - [<span data-ttu-id="cd3cc-270">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="cd3cc-270">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
    - [<span data-ttu-id="cd3cc-271">Syntaxe využívající dotazy a syntaxe využívající metody v technologii LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="cd3cc-271">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
    - [<span data-ttu-id="cd3cc-272">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="cd3cc-272">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
