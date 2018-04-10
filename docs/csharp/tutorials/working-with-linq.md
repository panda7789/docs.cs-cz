---
title: Práce s dotazy LINQ
description: V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, zápis metody pro použití v dotazech LINQ a rozlišovat přes a opožděné vyhodnocení.
keywords: Rozhraní .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ce6ed278c4e5a9583a827e8c3ff941c2f25bf182
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="9b5f1-104">Práce s dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="9b5f1-104">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="9b5f1-105">Úvod</span><span class="sxs-lookup"><span data-stu-id="9b5f1-105">Introduction</span></span>

<span data-ttu-id="9b5f1-106">V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="9b5f1-107">Naučíte:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-107">You’ll learn:</span></span>

*   <span data-ttu-id="9b5f1-108">Jak vygenerovat pořadí s dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="9b5f1-108">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="9b5f1-109">Jak napsat metody, které lze snadno použít v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-109">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="9b5f1-110">Postup rozlišovat přes a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-110">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="9b5f1-111">Tyto postupy získáte informace podle budovy aplikaci, která představuje jednu základní dovednosti žádné magician: [faro náhodně](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-111">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="9b5f1-112">Stručně řečeno náhodně faro jde o techniku, kde rozdělení karet přesně v polovině a pak náhodně interleaves každou kartu jeden z každého půl znovu sestavit v původní podlaží.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-112">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="9b5f1-113">Magicians použijte tento postup, protože každou kartu, je v zadaném umístění po každé náhodně a pořadí je opakující se vzorek.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-113">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="9b5f1-114">Pro naše účely je slabá hearted podívejte se na manipulace s posloupností data.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-114">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="9b5f1-115">Aplikace, kterou budete sestavení bude vytvořit karet a poté proveďte posloupnost podle okolí posouvá, zápis pořadí se pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-115">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="9b5f1-116">Budete také porovnat aktualizované pořadí, které se původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-116">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="9b5f1-117">V tomto kurzu má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-117">This tutorial has multiple steps.</span></span> <span data-ttu-id="9b5f1-118">Po dokončení každého kroku můžete aplikaci spustit a sledovat průběh.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-118">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="9b5f1-119">Můžete také zjistit [hotová ukázka](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti GitHub dotnet nebo ukázky.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-119">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="9b5f1-120">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b5f1-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b5f1-121">Prerequisites</span></span>

<span data-ttu-id="9b5f1-122">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-122">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="9b5f1-123">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="9b5f1-124">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-124">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="9b5f1-125">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="9b5f1-126">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="9b5f1-127">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-127">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="9b5f1-128">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="9b5f1-128">Create the Application</span></span>

<span data-ttu-id="9b5f1-129">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-129">The first step is to create a new application.</span></span> <span data-ttu-id="9b5f1-130">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="9b5f1-131">Nastavit aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-131">Make that the current directory.</span></span> <span data-ttu-id="9b5f1-132">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="9b5f1-133">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="9b5f1-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="9b5f1-134">Pokud jste nepoužívali C# před, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v C#.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-134">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="9b5f1-135">Můžete číst a pak se vraťte sem Další informace o LINQ.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-135">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="9b5f1-136">Vytváření v datové sadě</span><span class="sxs-lookup"><span data-stu-id="9b5f1-136">Creating the Data Set</span></span>

<span data-ttu-id="9b5f1-137">Začněme vytvořením balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-137">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="9b5f1-138">Můžete to udělat pomocí LINQ dotazu, který má dva zdroje (jeden pro čtyři vyhovuje, jeden pro třináct hodnoty).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-138">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="9b5f1-139">Tyto zdroje budete zkombinovat do 52 karet.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-139">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="9b5f1-140">A `Console.WriteLine` příkaz uvnitř `foreach` smyčky zobrazí kartách.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-140">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="9b5f1-141">Zde je dotaz:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-141">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="9b5f1-142">Násobek `from` klauzule vytvořit `SelectMany`, která vytvoří jeden pořadí z kombinace každý prvek v první pořadí s každý prvek v druhé pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-142">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="9b5f1-143">Pořadí je důležité pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-143">The order is important for our purposes.</span></span> <span data-ttu-id="9b5f1-144">Prvním elementem v první zdrojové sekvence (sady) spolu s každý element v druhé pořadí (hodnoty).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-144">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="9b5f1-145">To vytváří všechny třináct karty první barvy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-145">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="9b5f1-146">Tento postup se opakuje se každý prvek v první pořadí (sady).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-146">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="9b5f1-147">Konečný výsledek je balíčku karet seřazené podle sady, za nímž následuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-147">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="9b5f1-148">Potom budete muset vytvořit metody Suits() a Ranks().</span><span class="sxs-lookup"><span data-stu-id="9b5f1-148">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="9b5f1-149">Začneme skutečně jednoduchou sadou *iterator metody* , generovat pořadí, jako Výčtový řetězce:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-149">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
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

<span data-ttu-id="9b5f1-150">Tyto dvě metody jak využívat `yield return` syntaxe vytvořit sekvenci při spuštění.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-150">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="9b5f1-151">Kompilátor vytvoří objekt, který implementuje `IEnumerable<T>` a generuje pořadí řetězce podle jejich požadavku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-151">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="9b5f1-152">Pokračovat a spustit ukázku, kterou jste vytvořili v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="9b5f1-153">Zobrazí všechny 52 karet z balíčku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="9b5f1-154">Může být velmi užiteční při spuštění této ukázce v rámci ladicího sledovat jak `Suits()` a `Values()` spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="9b5f1-155">Uvidíte je zřejmé, že každý řetězec v každé pořadí je vygenerováno, pouze když jej potřebuje.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konzoly zobrazující aplikace zápis se 52 karet](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="9b5f1-157">Manipulace s pořadí</span><span class="sxs-lookup"><span data-stu-id="9b5f1-157">Manipulating the Order</span></span>

<span data-ttu-id="9b5f1-158">V dalším kroku Vytvořme nástroj metodu, která můžete provádět náhodně.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="9b5f1-159">Prvním krokem je rozdělit podlaží vede ke dvěma.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="9b5f1-160">`Take()` a `Skip()` metody, které jsou součástí rozhraní API LINQ zadejte tuto funkci pro nás:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="9b5f1-161">Metoda náhodně neexistuje v knihovně standardní, budete muset napsat vlastní.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="9b5f1-162">Tato nová metoda znázorňuje několik technik, které budete používat s aplikací založených na LINQ můžeme vysvětlují jednotlivých součástí metodu v krocích.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="9b5f1-163">Vytvoří podpis metody *metoda rozšíření*:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="9b5f1-164">Metody rozšíření je zvláštní účely *statickou metodu.*</span><span class="sxs-lookup"><span data-stu-id="9b5f1-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="9b5f1-165">Uvidíte přidání `this` modifikátor na první argument pro metodu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="9b5f1-166">To znamená, že zavoláte metodu, jako by šlo metodou member typu prvního argumentu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="9b5f1-167">Rozšiřující metody lze deklarovat pouze uvnitř `static` třídy, takže umožňuje vytvořit novou statickou třídu s názvem `extensions` pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="9b5f1-168">Jak budete pokračovat v tomto kurzu, a ty budou umístěny ve stejné třídě přidáte další metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="9b5f1-169">Následuje také tuto deklaraci metoda standardní stylu, kde jsou typy vstupní a výstupní `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="9b5f1-170">Aby postup umožňuje LINQ metody možné zřetězit dohromady a provádět složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="9b5f1-171">Budete se vytváření výčtu obě pořadí najednou, prokládání elementy a jeden objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="9b5f1-172">Zápis LINQ metoda, která funguje s dvěma pořadí vyžaduje, že chápete, jak `IEnumerable` funguje.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="9b5f1-173">`IEnumerable` Rozhraní má jedno z těchto metod: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="9b5f1-174">Objekt vrácený `GetEnumerator()` má metodu pro přesun na další prvek a vlastnosti, která načte aktuálního elementu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="9b5f1-175">Tyto dva členy použije výčet kolekce a vrátíte se elementy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="9b5f1-176">Tato metoda prokládání bude metodu iterator tak místo vytváření kolekce a vrácení kolekce, které budete používat `yield return` syntaxe uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="9b5f1-177">Tady je implementace této metody:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="9b5f1-178">Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a náhodně jednou z balíčku:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
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

## <a name="comparisons"></a><span data-ttu-id="9b5f1-179">Porovnání</span><span class="sxs-lookup"><span data-stu-id="9b5f1-179">Comparisons</span></span>

<span data-ttu-id="9b5f1-180">Podívejme se, kolik podle okolí posouvá trvá nastavit z balíčku zpět na jeho původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="9b5f1-181">Budete potřebovat napíše metoda, která určuje, jestli jsou dvě pořadí stejné.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="9b5f1-182">Až budete mít dané metody, musíte umístit kód, který posouvá podlaží v smyčky a zkontrolujte, pokud je balíček zpět v pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="9b5f1-183">Zápis metoda k určení, jestli jsou stejné dvě pořadí by měl být přehledné.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="9b5f1-184">Je podobnou strukturou metodě, který jste napsali náhodný výběr balíčku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="9b5f1-185">Pouze tentokrát místo yield vrácení každý prvek, je budete porovnat odpovídající elementy každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="9b5f1-186">Když byl výčet celého pořadí, pokud odpovídá každý element, pořadí jsou stejné:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="9b5f1-187">Zobrazí se druhé stylu Linq: terminálu metody.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="9b5f1-188">Trvat pořadí jako vstup (nebo v tomto případě dvě pořadí) a vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="9b5f1-189">Tyto metody, pokud se používají, jsou vždy poslední metodu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="9b5f1-190">(Proto název).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-190">(Hence the name).</span></span> 

<span data-ttu-id="9b5f1-191">Uvidíte to v praxi při použití k určení, kdy je z balíčku zpět v jeho původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="9b5f1-192">Vložte kód náhodně uvnitř smyčky a zastavit, když je pořadí je zpět v jeho původní pořadí s použitím `SequenceEquals()` metoda.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="9b5f1-193">Vidíte, že by měl být vždy poslední metodu ve všech dotazu, protože vrátí jednu hodnotu namísto sekvenci:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="9b5f1-194">Spustit ukázku a v tématu jak z balíčku Přeuspořádá na každý náhodně, dokud se vrátí do původní konfigurace po 8 iterací.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="9b5f1-195">Optimalizace</span><span class="sxs-lookup"><span data-stu-id="9b5f1-195">Optimizations</span></span>

<span data-ttu-id="9b5f1-196">Ukázka, když jste sestavili dosavadní provede *v náhodně*, kde karty horní a dolní zůstaly stejné při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-196">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="9b5f1-197">Pojďme si ho změnit a spusťte *se náhodně*, kde všechny 52 karty změní pozici.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-197">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="9b5f1-198">Pro mimo náhodného, můžete interleave z balíčku tak, aby první karty v dolní polovinu stane první karty v balíčku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-198">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="9b5f1-199">To znamená, že poslední karty v horní polovině se změní na spodní kartu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="9b5f1-200">To je právě změnu jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-200">That's just a one line change.</span></span> <span data-ttu-id="9b5f1-201">Volání náhodný výběr chcete-li změnit pořadí horní a dolní polovina podlaží aktualizace:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="9b5f1-202">Program spusťte znovu a uvidíte, že trvá 52 iterace pro balíček ke změně pořadí sám sebe.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="9b5f1-203">Budete také spustit Všimněte některé závažné výkonu degradations program stále spouštět.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="9b5f1-204">Existuje několik důvodů pro tento.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-204">There are a number of reasons for this.</span></span> <span data-ttu-id="9b5f1-205">Pojďme jednou z hlavních příčin tohoto problému: neefektivní používání *opožděné vyhodnocení*.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="9b5f1-206">LINQ dotazů jsou vyhodnocovány líné.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="9b5f1-207">Pořadí jsou generovány pouze jako elementy jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="9b5f1-208">Obvykle, který je hlavní výhodou LINQ.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="9b5f1-209">Ale používá jako je tento program, to způsobí, že exponenciální růst v dobu provádění.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="9b5f1-210">Původní podlaží byl vygenerován pomocí dotaz LINQ.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="9b5f1-211">Každý náhodně je generován provádění tři dotazů LINQ v předchozí podlaží.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="9b5f1-212">Všechny tyto líné probíhají.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-212">All these are performed lazily.</span></span> <span data-ttu-id="9b5f1-213">To také znamená, že je prováděna znovu pokaždé, když je požadovaný sekvenci.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="9b5f1-214">Podle času, které máte k 52nd iterace můžete se znovu vygenerovat. původní podlaží mnoho, kolikrát.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="9b5f1-215">Můžete napsat protokolu k předvedení toto chování.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="9b5f1-216">Budete pak, opravte ji.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-216">Then, you'll fix it.</span></span>

<span data-ttu-id="9b5f1-217">Zde je metoda protokolu, která může být přidán k jakýkoli dotaz k označení, že dotaz spustit.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="9b5f1-218">V dalším kroku instrumentace definici každý dotaz s zprávu protokolu:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-218">Next, instrument the definition of each query with a log message:</span></span>

```csharp
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
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
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

<span data-ttu-id="9b5f1-219">Všimněte si, že nemáte protokolu pokaždé, když přistupujete k dotazu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="9b5f1-220">Přihlášení jenom v případě, že vytvoříte původní dotaz.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-220">You log only when you create the original query.</span></span> <span data-ttu-id="9b5f1-221">Program stále trvá dlouhou dobu spuštění, ale nyní můžete zobrazit důvod, proč.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="9b5f1-222">Pokud spouštíte systému trpělivost systémem vnější náhodně s zapnout protokolování, přepněte zpět na vnitřní náhodně.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-222">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="9b5f1-223">Stále se zobrazí důsledky opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="9b5f1-224">V prvního spuštění se provede 2592 dotazů, včetně všech generování hodnota a barvy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="9b5f1-225">Je snadný způsob, jak aktualizovat Vyhněte se všechny tyto spuštění tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="9b5f1-226">Způsoby LINQ `ToArray()` a `ToList()` , způsobit dotaz pro spouštění a ukládání výsledků do pole nebo seznam, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="9b5f1-227">Tyto metody slouží k mezipaměti dat výsledků dotazu než zdrojový dotaz spustit znovu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="9b5f1-228">Připojit dotazy, které generují balíčky karet pomocí volání `ToArray()` a spusťte dotaz znovu:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="9b5f1-229">Spusťte znovu a vnitřní náhodně je dolů 30 dotazy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-229">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="9b5f1-230">Znovu spustit s vnější náhodně a zobrazí se podobné vylepšení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-230">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="9b5f1-231">(Je nyní provádí 162 dotazy).</span><span class="sxs-lookup"><span data-stu-id="9b5f1-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="9b5f1-232">Nemáte nesprávně interpretovat v tomto příkladu důkladným, který by se měl například spouštět všechny dotazy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="9b5f1-233">V tomto příkladu je určena pro zvýrazněte případy použití, kde opožděné vyhodnocení může způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="9b5f1-234">Je to způsobeno každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="9b5f1-235">Pomocí opožděné vyhodnocení znamená každou novou konfiguraci podlaží vychází z původní balíčku, i provádění kódu, který postavený `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="9b5f1-236">Které způsobí, že velké množství další práci.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="9b5f1-237">V praxi některé algoritmy spustit mnohem lepší pomocí přes vyhodnocení a jiné systém mnohem lepší pomocí opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="9b5f1-238">(Obecně platí, opožděné vyhodnocení je mnohem lepší volbou, pokud zdroj dat je samostatný proces, jako je databázový stroj.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="9b5f1-239">V takových případech opožděné vyhodnocení umožňuje složitější dotazy provést pouze jednu dobu odezvy pro proces databáze.) LINQ umožňuje opožděné i přes vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="9b5f1-240">Měření a vybrat nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="9b5f1-241">Příprava pro nové funkce</span><span class="sxs-lookup"><span data-stu-id="9b5f1-241">Preparing for New Features</span></span>

<span data-ttu-id="9b5f1-242">Kód, které jste vytvořili pro tato ukázka je příklad vytvoření jednoduchého prototyp, která provádí úlohy.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="9b5f1-243">Toto je skvělý způsob, jak prozkoumat problém místa, a pro mnoho funkcí, může být nejlepším řešením trvalé.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="9b5f1-244">Jste využít *anonymní typy* pro kartách a každou kartu je reprezentována řetězce.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="9b5f1-245">*Anonymní typy* mají mnoho výhod produktivitu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="9b5f1-246">Nemusíte definovat třídu sami, abyste představují úložiště.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="9b5f1-247">Kompilátor generuje typ za vás.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-247">The compiler generates the type for you.</span></span> <span data-ttu-id="9b5f1-248">Typ kompilátoru generované využívá řadu osvědčené postupy pro jednoduché datové objekty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="9b5f1-249">Má *neměnné*, což znamená, že žádný z jeho vlastnosti lze změnit po byla vytvořená.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="9b5f1-250">Anonymní typy jsou interní sestavení, takže nevidí jako součást veřejné rozhraní API pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="9b5f1-251">Anonymní typy také obsahují přepsání `ToString()` metoda, která vrací řetězec formátovaný s jednotlivých hodnot.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="9b5f1-252">Anonymní typy mít také nevýhody.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="9b5f1-253">Nemají přístupné názvy, takže je nejde používat jako návratové hodnoty nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="9b5f1-254">Můžete si všimnout, že obecné metody, které všechny metody vyšší použít tyto anonymní typy jsou.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="9b5f1-255">Přepsané `ToString()` nemusí být co chcete použít víc funkcí růstem aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="9b5f1-256">Ukázka také používá řetězce pro barvy a pořadí každou kartu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="9b5f1-257">Které je poměrně otevřít zakončeno.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-257">That's quite open ended.</span></span> <span data-ttu-id="9b5f1-258">Systém typů jazyka C# můžete Pomozte nám lepší kód s využitím `enum` typy pro tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="9b5f1-259">Začněte sady.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-259">Start with the suits.</span></span> <span data-ttu-id="9b5f1-260">Toto je ideální čas sloužící `enum`:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="9b5f1-261">`Suits()` Metoda také změní typ a implementace:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="9b5f1-262">V dalším kroku stejné změnit s pořadí karet:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="9b5f1-263">A metoda, která generuje je:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="9b5f1-264">Jako jeden konečné čištění provedeme typu představují karty, aniž byste museli spoléhat na anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="9b5f1-265">Anonymní typy jsou velmi vhodné pro typy lightweight, místní, ale v tomto příkladu herní karta je jedním z hlavní koncepty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="9b5f1-266">To by měla být konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="9b5f1-267">Tento typ používá *automaticky implementované vlastnosti jen pro čtení* které se nastavují v konstruktoru a pak nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="9b5f1-268">Je také využívá [řetězec interpolace](../language-reference/tokens/interpolated.md) funkce, která usnadňuje výstupní řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-268">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="9b5f1-269">Aktualizace dotazu, který generuje počáteční podlaží používat nový typ:</span><span class="sxs-lookup"><span data-stu-id="9b5f1-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="9b5f1-270">Kompilace a znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-270">Compile and run again.</span></span> <span data-ttu-id="9b5f1-271">Výstupem je trochu čisticí a kód je trochu trochu objasnit a lze snadno rozšířit.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="9b5f1-272">Závěr</span><span class="sxs-lookup"><span data-stu-id="9b5f1-272">Conclusion</span></span>

<span data-ttu-id="9b5f1-273">Tato ukázka vám ukázal, můžete některé metody použité v technologii LINQ, jak vytvořit vlastní metody, které se snadno používat s dotazy LINQ povoleno kódu.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="9b5f1-274">Je také ukázal rozdíly mezi opožděné a přes vyhodnocení a o tom, že rozhodnutí může mít na výkon.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="9b5f1-275">Jste se dozvěděli o něco o jeden magician techniku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="9b5f1-276">Magicians pomocí náhodně faro, protože můžou řídit, kdy každou kartu přesune z balíčku.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="9b5f1-277">V některých triky magician má člena cílové skupiny umístit karty nad z balíčku a posouvá několikrát, zároveň budete vědět, kde přejde karty.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="9b5f1-278">Další illusions vyžadují z balíčku nastavte určitým způsobem.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="9b5f1-279">Magician nastaví podlaží před provedením podvodné.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="9b5f1-280">Pak se bude náhodně podlaží 5krát pomocí vnitřní náhodně.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-280">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="9b5f1-281">Na fázi Jana můžete zobrazit, jak vypadá náhodných balíčku, náhodný výběr 3 vícekrát a mít podlaží nastavit, přesně jak chce.</span><span class="sxs-lookup"><span data-stu-id="9b5f1-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
