---
title: Práce s jazykem LINQ
description: Tento kurz vás naučí, jak generovat sekvence s LINQ, psát metody pro použití v dotazech LINQ a rozlišovat mezi dychtivé a opožděné hodnocení.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240012"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="1eaf1-103">Práce s dotazem integrovaným jazykem (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="1eaf1-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="1eaf1-104">Introduction</span></span>

<span data-ttu-id="1eaf1-105">Tento kurz vás naučí funkce v .NET Core a jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="1eaf1-106">Co se naučíte:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-106">You’ll learn how to:</span></span>

- <span data-ttu-id="1eaf1-107">Generovat sekvence s LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="1eaf1-108">Metody zápisu, které lze snadno použít v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="1eaf1-109">Rozlišujte mezi dychtivým a líným hodnocením.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="1eaf1-110">Naučíte se tyto techniky tím, že staví aplikace, která demonstruje jednu ze základních dovedností každého kouzelníka: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="1eaf1-111">Stručně řečeno, faro shuffle je technika, kde si rozdělit kartu palubu přesně na polovinu, pak shuffle prolomení každé jedné karty z každé poloviny přestavět původní balíček.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="1eaf1-112">Kouzelníci používají tuto techniku, protože každá karta je po každém náhodném přehrávání na známém místě a pořadí je opakující se vzor.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="1eaf1-113">Pro vaše účely je to lehký pohled na manipulaci s sekvencemi dat.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="1eaf1-114">Aplikace, kterou budete stavět, vytvoří balíček karet a pak provede sekvenci zamíchání a pokaždé zapíše sekvenci.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="1eaf1-115">Budete také porovnávat aktualizované pořadí s původní objednávkou.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="1eaf1-116">Tento kurz má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="1eaf1-117">Po každém kroku můžete spustit aplikaci a zobrazit průběh.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="1eaf1-118">Můžete také zobrazit [dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="1eaf1-119">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1eaf1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1eaf1-120">Prerequisites</span></span>

<span data-ttu-id="1eaf1-121">Budete muset nastavit počítač pro spuštění jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="1eaf1-122">Pokyny k instalaci naleznete na stránce [ke stažení jádra .NET.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="1eaf1-123">Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux nebo OS X nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="1eaf1-124">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="1eaf1-125">Níže uvedené popisy používají [Visual Studio Code,](https://code.visualstudio.com/) který je open source, cross-platformní editor.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="1eaf1-126">Nicméně, můžete použít bez ohledu na nástroje, které jsou pohodlné s.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1eaf1-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="1eaf1-127">Create the Application</span></span>

<span data-ttu-id="1eaf1-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-128">The first step is to create a new application.</span></span> <span data-ttu-id="1eaf1-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1eaf1-130">Ať je to aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-130">Make that the current directory.</span></span> <span data-ttu-id="1eaf1-131">Zadejte `dotnet new console` příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1eaf1-132">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="1eaf1-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="1eaf1-133">Pokud jste nikdy nepoužívali C# dříve, [tento kurz](console-teleprompter.md) vysvětluje strukturu programu Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="1eaf1-134">Můžete si přečíst, že a pak se vrátit sem se dozvíte více o LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="1eaf1-135">Vytvoření sady dat</span><span class="sxs-lookup"><span data-stu-id="1eaf1-135">Create the Data Set</span></span>

<span data-ttu-id="1eaf1-136">Než začnete, ujistěte se, že následující `Program.cs` řádky jsou `dotnet new console`v horní části souboru generovaného :</span><span class="sxs-lookup"><span data-stu-id="1eaf1-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="1eaf1-137">Pokud tyto tři`using` řádky (příkazy) nejsou v horní části souboru, náš program nebude kompilovat.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="1eaf1-138">Nyní, když máte všechny odkazy, které budete potřebovat, zvažte, co představuje balíček karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="1eaf1-139">Obvykle má balíček hracích karet čtyři barvy a každá barva má třináct hodnot.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="1eaf1-140">Za normálních okolností `Card` můžete zvážit vytvoření třídy hned bat `Card` a vyplnění kolekce objektů ručně.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="1eaf1-141">S LINQ, můžete být stručnější než obvyklý způsob, jak se vypořádat s vytvořením balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="1eaf1-142">Namísto vytvoření `Card` třídy můžete vytvořit dvě sekvence představující obleky a hodnosti.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="1eaf1-143">Vytvoříte opravdu jednoduchý pár [*iterátorových metod,*](../iterators.md#enumeration-sources-with-iterator-methods) které budou generovat <xref:System.Collections.Generic.IEnumerable%601>hodnosti a obleky jako s strun:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="1eaf1-144">Umístěte je `Main` pod metodu do `Program.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="1eaf1-145">Tyto dvě metody `yield return` oba využívají syntaxe k vytvoření sekvence při jejich spuštění.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="1eaf1-146">Kompilátor vytvoří objekt, který <xref:System.Collections.Generic.IEnumerable%601> implementuje a generuje posloupnost řetězců, jak jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="1eaf1-147">Nyní použijte tyto metody iterátoru k vytvoření balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="1eaf1-148">Dotaz LINQ umístíte do `Main` naší metody.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="1eaf1-149">Zde je pohled na to:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-149">Here's a look at it:</span></span>

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

<span data-ttu-id="1eaf1-150">Více `from` klauzulí vytvořit <xref:System.Linq.Enumerable.SelectMany%2A>, který vytvoří jednu sekvenci z kombinování každý prvek v první sekvenci s každým prvkem v druhé sekvenci.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="1eaf1-151">Objednávka je důležitá pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-151">The order is important for our purposes.</span></span> <span data-ttu-id="1eaf1-152">První prvek v první zdrojové sekvenci (Obleky) je kombinován s každým prvkem v druhé sekvenci (Ranky).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="1eaf1-153">Tím se vytvoří všech třináct karet první barvy.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="1eaf1-154">Tento proces se opakuje s každým prvkem v prvním pořadí (Obleky).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="1eaf1-155">Konečným výsledkem je balíček karet seřazených podle barev, následovaný hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="1eaf1-156">Je důležité mít na paměti, že ať už se rozhodnete napsat LINQ v syntaxi dotazu použité výše nebo použít syntaxi metody místo, je vždy možné přejít z jedné formy syntaxe do druhé.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="1eaf1-157">Výše uvedený dotaz napsaný v syntaxi dotazu lze zapsat v syntaxi metody jako:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="1eaf1-158">Kompilátor přeloží linq příkazy napsané se syntaxí dotazu do syntaxe volání ekvivalentní metody.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="1eaf1-159">Proto bez ohledu na volbu syntaxe dvě verze dotazu vytvořit stejný výsledek.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="1eaf1-160">Zvolte, která syntaxe je pro vaši situaci nejvhodnější: například pokud pracujete v týmu, kde někteří členové mají potíže se syntaxí metody, zkuste dát přednost použití syntaxe dotazu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="1eaf1-161">Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto bodě.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="1eaf1-162">Zobrazí se všech 52 karet v balíčku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="1eaf1-163">Může být velmi užitečné spustit tuto ukázku pod ladicím programem sledovat, jak `Suits()` a `Ranks()` metody spustit.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="1eaf1-164">Můžete jasně vidět, že každý řetězec v každé sekvenci je generován pouze podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konzoly zobrazující aplikaci, která vypisuje 52 karet.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="1eaf1-166">Manipulujte s řádem</span><span class="sxs-lookup"><span data-stu-id="1eaf1-166">Manipulate the Order</span></span>

<span data-ttu-id="1eaf1-167">Dále se zaměřte na to, jak budete míchat karty v balíčku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="1eaf1-168">Prvním krokem v každém dobrém shuffle je rozdělit palubu na dvě části.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="1eaf1-169">A <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> metody, které jsou součástí LINQ API poskytují tuto funkci pro vás.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="1eaf1-170">Umístěte je `foreach` pod smyčku:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="1eaf1-171">Ve standardní knihovně však neexistuje žádná metoda náhodného přehrávání, takže budete muset napsat vlastní.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="1eaf1-172">Metoda náhodného přehrávání, kterou vytvoříte, ilustruje několik technik, které budete používat s programy založenými na LINQ, takže každá část tohoto procesu bude vysvětlena v krocích.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="1eaf1-173">Chcete-li přidat některé funkce, jak <xref:System.Collections.Generic.IEnumerable%601> budete pracovat s dostanete zpět z linq dotazů, budete muset napsat některé speciální druhy metod nazývaných [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="1eaf1-174">Stručně řečeno, metoda rozšíření je speciální statický *způsob,* který přidává nové funkce již existující typ bez nutnosti měnit původní typ, který chcete přidat funkce.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="1eaf1-175">Pojmenujte metody rozšíření novým domovem přidáním nového `Extensions.cs` *statického* souboru třídy do programu s názvem a začněte vytvářet první metodu rozšíření:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="1eaf1-176">Podívejte se na podpis metody na chvíli, konkrétně parametry:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="1eaf1-177">Můžete vidět přidání modifikátoru `this` na první argument metody.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="1eaf1-178">To znamená, že volání metody, jako by byla člen metoda typu první argument.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="1eaf1-179">Tato deklarace metody také následuje standardní idiom, `IEnumerable<T>`kde jsou vstupní a výstupní typy .</span><span class="sxs-lookup"><span data-stu-id="1eaf1-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="1eaf1-180">Tato praxe umožňuje LINQ metody, které mají být zřetězené dohromady provádět složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="1eaf1-181">Samozřejmě, protože jste rozdělili palubu na poloviny, budete muset spojit tyto poloviny dohromady.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="1eaf1-182">V kódu to znamená, že budete vyjmenovat obě sekvence, <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> které jste *`interleaving`* získali prostřednictvím a najednou, prvky a vytvořit jednu sekvenci: nyní zamíchaný balíček karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="1eaf1-183">Psaní LINQ metoda, která pracuje se dvěma <xref:System.Collections.Generic.IEnumerable%601> sekvencemi vyžaduje, abyste pochopili, jak funguje.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="1eaf1-184">Rozhraní <xref:System.Collections.Generic.IEnumerable%601> má jednu <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>metodu: .</span><span class="sxs-lookup"><span data-stu-id="1eaf1-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="1eaf1-185">Objekt vrácený <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu přesunout na další prvek a vlastnost, která načte aktuální prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="1eaf1-186">Tyto dva členy použijete k vytvoření výčtu kolekce a vrácení prvků.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="1eaf1-187">Tato metoda Interleave bude metoda iterátoru, takže namísto vytváření kolekce a vrácení `yield return` kolekce použijete syntaxi uvedenou výše.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="1eaf1-188">Zde je implementace této metody:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="1eaf1-189">Nyní, když jste napsali tuto metodu, vraťte se k metodě `Main` a jednou zamíchejte balíček:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="1eaf1-190">Porovnání</span><span class="sxs-lookup"><span data-stu-id="1eaf1-190">Comparisons</span></span>

<span data-ttu-id="1eaf1-191">Kolik zamíchá, aby se paluba vrátila do původního pořadí?</span><span class="sxs-lookup"><span data-stu-id="1eaf1-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="1eaf1-192">Chcete-li zjistit, budete muset napsat metodu, která určuje, zda jsou dvě sekvence stejné.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="1eaf1-193">Poté, co budete mít tuto metodu, budete muset umístit kód, který zamíchá palubu ve smyčce, a zkontrolujte, kdy je balíček zpět v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="1eaf1-194">Psaní metody k určení, pokud jsou dvě sekvence stejné by měly být jednoduché.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="1eaf1-195">Je to podobná struktura jako metoda, kterou jste napsali, abyste zamíchali palubu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="1eaf1-196">Pouze tentokrát, namísto `yield return`ing každý prvek, budete porovnávat odpovídající prvky každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="1eaf1-197">Pokud byla celá sekvence výčtu, pokud každý prvek odpovídá, sekvence jsou stejné:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="1eaf1-198">To ukazuje druhý LINQ idiom: terminálové metody.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="1eaf1-199">Vezmou sekvenci jako vstup (nebo v tomto případě dvě sekvence) a vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="1eaf1-200">Při použití terminálových metod jsou vždy konečnou metodou v řetězci metod pro dotaz LINQ, odtud název "terminál".</span><span class="sxs-lookup"><span data-stu-id="1eaf1-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="1eaf1-201">Můžete to vidět v akci, když ji použijete k určení, kdy je balíček zpět v původním pořadí.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="1eaf1-202">Vložte kód náhodného přehrávání do smyčky a zastavte, když `SequenceEquals()` je sekvence zpět v původním pořadí použitím metody.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="1eaf1-203">Můžete vidět, že by vždy konečná metoda v libovolném dotazu, protože vrátí jednu hodnotu namísto sekvence:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="1eaf1-204">Spusťte kód, který máte tak daleko, a vzít na vědomí, jak paluba přeskupí na každém shuffle.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="1eaf1-205">Po 8 shuffles (iterací do-while smyčky), balíček se vrátí do původní konfigurace, ve které byl při prvním vytvoření z počátečního dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="1eaf1-206">Optimalizace</span><span class="sxs-lookup"><span data-stu-id="1eaf1-206">Optimizations</span></span>

<span data-ttu-id="1eaf1-207">Ukázka, kterou jste dosud vytvořili, provede *výběr*, kde horní a dolní karty zůstávají při každém běhu stejné.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="1eaf1-208">Udělejme jednu změnu: místo toho použijeme *zamíchanou,* kde změní pozici všech 52 karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="1eaf1-209">Pro shuffle, můžete proložit balíček tak, aby první karta v dolní polovině se stala první kartou v balíčku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="1eaf1-210">To znamená, že poslední karta v horní polovině se stane spodní kartou.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="1eaf1-211">Jedná se o jednoduchou změnu jednotného řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="1eaf1-212">Aktualizujte aktuální zamíchací <xref:System.Linq.Enumerable.Take%2A> dotaz <xref:System.Linq.Enumerable.Skip%2A>přepnutím pozic a .</span><span class="sxs-lookup"><span data-stu-id="1eaf1-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="1eaf1-213">Tím se změní pořadí horní a dolní poloviny paluby:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="1eaf1-214">Spusťte program znovu a uvidíte, že trvá 52 iterací pro balíček, aby se přizpůsobil.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="1eaf1-215">Budete také začít všímat některé závažné snížení výkonu jako program nadále běžet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="1eaf1-216">Existuje pro to řada důvodů.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-216">There are a number of reasons for this.</span></span> <span data-ttu-id="1eaf1-217">Můžete řešit jednu z hlavních příčin tohoto poklesu výkonu: neefektivní použití [*opožděné hodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1eaf1-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="1eaf1-218">Stručně řečeno, opožděné vyhodnocení uvádí, že vyhodnocení příkazu není provedeno, dokud není potřeba jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="1eaf1-219">LINQ dotazy jsou příkazy, které jsou vyhodnocovány líně.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="1eaf1-220">Sekvence jsou generovány pouze jako prvky jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="1eaf1-221">Obvykle, to je hlavní výhodou LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="1eaf1-222">Však v použití, jako je tento program, to způsobí exponenciální růst v době provádění.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="1eaf1-223">Nezapomeňte, že jsme vygenerovali původní balíček pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="1eaf1-224">Každý shuffle je generován provedením tří linq dotazů na předchozí palubě.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="1eaf1-225">Všechny tyto jsou prováděny líně.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-225">All these are performed lazily.</span></span> <span data-ttu-id="1eaf1-226">To také znamená, že jsou prováděny znovu pokaždé, když je požadována sekvence.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="1eaf1-227">V době, kdy se dostanete k 52.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="1eaf1-228">Pojďme napsat protokol demonstrovat toto chování.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="1eaf1-229">Tak to napravíš.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-229">Then, you'll fix it.</span></span>

<span data-ttu-id="1eaf1-230">Do `Extensions.cs` souboru zadejte nebo zkopírujte níže uvedenou metodu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="1eaf1-231">Tato metoda rozšíření vytvoří `debug.log` nový soubor svolaný v adresáři projektu a zaznamená, jaký dotaz je právě spuštěn do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="1eaf1-232">Tato metoda rozšíření lze připojit k libovolnému dotazu označit, že dotaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="1eaf1-233">Uvidíte červenou vlnovku pod `File`, což znamená, že neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="1eaf1-234">Nebude kompilovat, protože kompilátor neví, `File` co je.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="1eaf1-235">Chcete-li tento problém vyřešit, nezapomeňte přidat následující řádek `Extensions.cs`kódu pod úplně první řádek v :</span><span class="sxs-lookup"><span data-stu-id="1eaf1-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="1eaf1-236">To by mělo vyřešit problém a červená chyba zmizí.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="1eaf1-237">Dále instrumentujte definici každého dotazu zprávou protokolu:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-237">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="1eaf1-238">Všimněte si, že při každém přístupu k dotazu nezaznamenáváte.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="1eaf1-239">Protokolovat pouze při vytvoření původnídotaz.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-239">You log only when you create the original query.</span></span> <span data-ttu-id="1eaf1-240">Spuštění programu stále trvá dlouho, ale nyní vidíte proč.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="1eaf1-241">Pokud vám dojde trpělivost při běhu s vypnutým protokolováním, přepněte zpět na out shuffle.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="1eaf1-242">Stále uvidíte opožděné efekty hodnocení.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="1eaf1-243">V jednom spuštění provede 2592 dotazů, včetně všech generování hodnoty a obleku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="1eaf1-244">Můžete zlepšit výkon kódu zde snížit počet spuštění provedete.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="1eaf1-245">Jednoduchá oprava, kterou můžete provést, je ukládat výsledky původního dotazu LINQ do *mezipaměti,* který vytváří balíček karet.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="1eaf1-246">V současné době provádíte dotazy znovu a znovu pokaždé, když smyčka do-while prochází iterace, re-constructing balíček karet a reshuffling pokaždé.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="1eaf1-247">Chcete-li uložit balíček karet do mezipaměti, můžete využít metody <xref:System.Linq.Enumerable.ToArray%2A> LINQ a <xref:System.Linq.Enumerable.ToList%2A>; Když je připojíte k dotazům, provedou stejné akce, které jste jim řekli, ale teď budou výsledky ukládat do pole nebo seznamu v závislosti na tom, kterou metodu se rozhodnete volat.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="1eaf1-248">Připojte metodu <xref:System.Linq.Enumerable.ToArray%2A> LINQ k oběma dotazům a znovu spusťte program:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="1eaf1-249">Nyní out shuffle je až 30 dotazů.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="1eaf1-250">Spusťte znovu s shuffle a uvidíte podobná vylepšení: nyní provádí 162 dotazů.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="1eaf1-251">Vezměte prosím na vědomí, že tento příklad je **určen** ke zvýraznění případy použití, kde opožděné vyhodnocení může způsobit potíže s výkonem.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="1eaf1-252">I když je důležité zjistit, kde opožděné vyhodnocení může ovlivnit výkon kódu, je stejně důležité pochopit, že ne všechny dotazy by měly běžet dychtivě.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="1eaf1-253">Výkon hit vám vzniknou <xref:System.Linq.Enumerable.ToArray%2A> bez použití je proto, že každé nové uspořádání balíčku karet je postaven z předchozího uspořádání.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="1eaf1-254">Použití opožděné vyhodnocení znamená, že každá nová konfigurace balíčku je sestavena z původního balíčku, a to i při provádění kódu, který vytvořil `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="1eaf1-255">To způsobuje velké množství práce navíc.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="1eaf1-256">V praxi některé algoritmy běží dobře pomocí eager hodnocení a jiné spustit dobře pomocí opožděné hodnocení.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="1eaf1-257">Pro každodenní použití opožděné vyhodnocení je obvykle lepší volbou, pokud zdroj dat je samostatný proces, jako je databázový stroj.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="1eaf1-258">Pro databáze opožděné vyhodnocení umožňuje složitější dotazy spustit pouze jednu odezvu do procesu databáze a zpět do zbytku kódu.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="1eaf1-259">LINQ je flexibilní, ať už se rozhodnete využít líné nebo dychtivé hodnocení, takže změřte procesy a vyberte si, který druh hodnocení vám dává nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="1eaf1-260">Závěr</span><span class="sxs-lookup"><span data-stu-id="1eaf1-260">Conclusion</span></span>

<span data-ttu-id="1eaf1-261">V tomto projektu jste se zabývali:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-261">In this project, you covered:</span></span>

- <span data-ttu-id="1eaf1-262">použití dotazů LINQ k agregaci dat do smysluplné sekvence</span><span class="sxs-lookup"><span data-stu-id="1eaf1-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="1eaf1-263">psaní rozšiřující metody přidat vlastní funkce linq dotazy</span><span class="sxs-lookup"><span data-stu-id="1eaf1-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="1eaf1-264">lokalizace oblastí v našem kódu, kde naše linq dotazy mohou narazit na problémy s výkonem, jako je snížená rychlost</span><span class="sxs-lookup"><span data-stu-id="1eaf1-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="1eaf1-265">líné a dychtivé hodnocení s ohledem na dotazy LINQ a důsledky, které mohou mít na výkon dotazu</span><span class="sxs-lookup"><span data-stu-id="1eaf1-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="1eaf1-266">Kromě LINQ, jste se dozvěděli něco o technice kouzelníci používají pro karetní triky.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="1eaf1-267">Kouzelníci používají Faro shuffle, protože mohou kontrolovat, kde se každá karta pohybuje v balíčku.</span><span class="sxs-lookup"><span data-stu-id="1eaf1-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="1eaf1-268">Teď, když to víš, nezkaz to pro všechny ostatní!</span><span class="sxs-lookup"><span data-stu-id="1eaf1-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="1eaf1-269">Další informace o LINQ naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="1eaf1-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="1eaf1-270">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="1eaf1-271">Úvod do jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="1eaf1-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="1eaf1-272">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="1eaf1-273">Transformace dat s LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="1eaf1-274">Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1eaf1-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="1eaf1-275">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="1eaf1-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
