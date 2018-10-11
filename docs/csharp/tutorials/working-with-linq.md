---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, Zapsat metody pro použití v dotazech LINQ a rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086749"
---
# <a name="working-with-linq"></a><span data-ttu-id="c1e16-103">Práce s jazykem LINQ</span><span class="sxs-lookup"><span data-stu-id="c1e16-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="c1e16-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="c1e16-104">Introduction</span></span>

<span data-ttu-id="c1e16-105">V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1e16-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="c1e16-106">Získáte informace:</span><span class="sxs-lookup"><span data-stu-id="c1e16-106">You’ll learn:</span></span>

*   <span data-ttu-id="c1e16-107">Jak vygenerovat pořadí s jazykem LINQ</span><span class="sxs-lookup"><span data-stu-id="c1e16-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="c1e16-108">Jak napsat metody, které můžete snadno použít v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="c1e16-109">Jak rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="c1e16-110">Vytvořením aplikace, která ukazuje jednu základní dovednosti jakékoli magician dozvíte těchto technik: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="c1e16-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="c1e16-111">Stručně řečeno náhodně faro je technika, kde rozdělit karet přesně na polovinu a pak shuffle předřadí jednotlivých karet z každého půl k opětovnému sestavení z původního balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="c1e16-112">Magicians tento postup použít, protože všechny karty je v zadaném umístění po jednotlivých shuffle a pořadí je s opakováním vzoru.</span><span class="sxs-lookup"><span data-stu-id="c1e16-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="c1e16-113">Pro naše účely je slabá hearted podívejte se na zpracování data sekvencí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="c1e16-114">Aplikace, kterou vytvoříte bude sestavení karet a pak proveďte posloupnost podle okolí posouvá, zápis si pokaždé, když je pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="c1e16-115">Budete také porovnat aktualizované aby původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="c1e16-116">V tomto kurzu má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="c1e16-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="c1e16-117">Po provedení každého kroku můžete spustit aplikaci a sledovat průběh.</span><span class="sxs-lookup"><span data-stu-id="c1e16-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="c1e16-118">Můžete zobrazit také [úplnou vzorovou](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti dotnet/samples GitHub.</span><span class="sxs-lookup"><span data-stu-id="c1e16-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="c1e16-119">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c1e16-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1e16-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1e16-120">Prerequisites</span></span>

<span data-ttu-id="c1e16-121">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="c1e16-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="c1e16-122">Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="c1e16-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="c1e16-123">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c1e16-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="c1e16-124">Bude potřeba nainstalovat váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="c1e16-125">Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru.</span><span class="sxs-lookup"><span data-stu-id="c1e16-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="c1e16-126">Ale můžete použít jakýkoli nástroje jste obeznámeni.</span><span class="sxs-lookup"><span data-stu-id="c1e16-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="c1e16-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="c1e16-127">Create the Application</span></span>

<span data-ttu-id="c1e16-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c1e16-128">The first step is to create a new application.</span></span> <span data-ttu-id="c1e16-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c1e16-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="c1e16-130">Ujistěte se, že do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1e16-130">Make that the current directory.</span></span> <span data-ttu-id="c1e16-131">Zadejte příkaz `dotnet new console` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="c1e16-132">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c1e16-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="c1e16-133">Pokud jste nikdy C#, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c1e16-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="c1e16-134">Může číst a pak se sem vraťte pro další informace o jazyku LINQ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="c1e16-135">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="c1e16-135">Creating the Data Set</span></span>

<span data-ttu-id="c1e16-136">Začněme vytvořením balíčku karet.</span><span class="sxs-lookup"><span data-stu-id="c1e16-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="c1e16-137">Můžete udělat pomocí dotazu LINQ, který má dva zdroje (jeden pro čtyři vyhovuje, jeden pro třináct hodnoty).</span><span class="sxs-lookup"><span data-stu-id="c1e16-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="c1e16-138">Tyto zdroje budete zkombinovat do 52 karet.</span><span class="sxs-lookup"><span data-stu-id="c1e16-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="c1e16-139">A `Console.WriteLine` výroku uvnitř `foreach` smyčky zobrazí karty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="c1e16-140">Tady je dotaz:</span><span class="sxs-lookup"><span data-stu-id="c1e16-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="c1e16-141">Násobek `from` klauzule vytvářejí `SelectMany`, vytváří jeden pořadí z kombinace každý prvek v první řadě se každý prvek v druhé pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="c1e16-142">Pořadí je důležité pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="c1e16-142">The order is important for our purposes.</span></span> <span data-ttu-id="c1e16-143">První prvek v první zdrojové sekvence (barvy) číslo zkombinuje s každý prvek v druhé pořadí (hodnoty).</span><span class="sxs-lookup"><span data-stu-id="c1e16-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="c1e16-144">Tímto se vytvoří všechny karty třináct první barvy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="c1e16-145">Tento proces se opakuje ke každému elementu v první řadě (barvy).</span><span class="sxs-lookup"><span data-stu-id="c1e16-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="c1e16-146">Konečný výsledek je balíčku karet seřazené podle barvy, za nímž následuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="c1e16-147">V dalším kroku budete muset sestavit Suits() a Ranks() metody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="c1e16-148">Začneme velmi jednoduchou sadu *iterátory* generují sekvenci, jako Výčtový objekt řetězce:</span><span class="sxs-lookup"><span data-stu-id="c1e16-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

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

<span data-ttu-id="c1e16-149">Tyto dvě metody jak využívat `yield return` syntaxi pro vytvoření sekvence za běhu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="c1e16-150">Kompilátor vytvoří objekt, který implementuje `IEnumerable<T>` a generuje posloupnost řetězců, jako jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="c1e16-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="c1e16-151">Pro tuto kompilaci je potřeba na začátek souboru přidejte následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="c1e16-151">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="c1e16-152">Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="c1e16-153">Zobrazí se všechny 52 karty z balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="c1e16-154">Může být pro vás velmi užitečné v ladicím programu sledovat tuto ukázku spustit jak `Suits()` a `Values()` provedení metody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="c1e16-155">Je jasně vidět, že každého řetězce v každé pořadí se vygeneruje pouze dle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c1e16-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konzoly aplikace výpisu 52 karet](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="c1e16-157">Manipulace s pořadí</span><span class="sxs-lookup"><span data-stu-id="c1e16-157">Manipulating the Order</span></span>

<span data-ttu-id="c1e16-158">V dalším kroku Vytvořme nástroj metodu, která můžete provést náhodné.</span><span class="sxs-lookup"><span data-stu-id="c1e16-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="c1e16-159">Prvním krokem je rozdělit z balíčku ve dvou.</span><span class="sxs-lookup"><span data-stu-id="c1e16-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="c1e16-160">`Take()` a `Skip()` metody, které jsou součástí rozhraní API LINQ poskytují tuto funkci pro nás:</span><span class="sxs-lookup"><span data-stu-id="c1e16-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="c1e16-161">Proto budete muset napsat vlastní metodou shuffle neexistuje ve standardní knihovně.</span><span class="sxs-lookup"><span data-stu-id="c1e16-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="c1e16-162">Tato nová metoda ukazuje několik technik, které budete používat s aplikacemi na základě LINQ, můžeme vysvětlit jednotlivých součástí metodu v krocích.</span><span class="sxs-lookup"><span data-stu-id="c1e16-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="c1e16-163">Podpis metody vytvoří *– metoda rozšíření*:</span><span class="sxs-lookup"><span data-stu-id="c1e16-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="c1e16-164">Metody rozšíření je zvláštní účely *statické metody.*</span><span class="sxs-lookup"><span data-stu-id="c1e16-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="c1e16-165">Zobrazí se přidání `this` modifikátor v prvním argumentu k metodě.</span><span class="sxs-lookup"><span data-stu-id="c1e16-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="c1e16-166">To znamená, že volání metody, jako by šlo o metodu člen typu prvního argumentu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="c1e16-167">Metody rozšíření lze deklarovat pouze uvnitř `static` třídy, můžeme vytvořit novou statickou třídu s názvem `extensions` pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c1e16-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="c1e16-168">Přidejte další metody rozšíření budete pokračovat v tomto kurzu, a ty budou umístěny ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="c1e16-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="c1e16-169">Tato metoda také následuje po deklaraci standardní idiom kde vstupní a výstupní typy jsou `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="c1e16-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="c1e16-170">Že postup umožňuje metody LINQ na možné zřetězit dohromady a provádět složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

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

<span data-ttu-id="c1e16-171">Budete výčet obou pořadí najednou, prokládání prvky a vytvoření jednoho objektu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="c1e16-172">Zápis LINQ metodu, která funguje s dvěma sekvencemi vyžaduje pochopit, jak `IEnumerable` funguje.</span><span class="sxs-lookup"><span data-stu-id="c1e16-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="c1e16-173">`IEnumerable` Rozhraní má jednu metodu: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="c1e16-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="c1e16-174">Objekt vrácený rutinou `GetEnumerator()` má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="c1e16-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="c1e16-175">Tyto dva členy použije k vytvoření výčtu kolekce a vrátí prvky.</span><span class="sxs-lookup"><span data-stu-id="c1e16-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="c1e16-176">Tato metoda prokládání bude metodu iterátoru, místo vytváření kolekce a vrátí kolekci, které použijete `yield return` syntaxe uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="c1e16-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="c1e16-177">Tady je implementace této metody:</span><span class="sxs-lookup"><span data-stu-id="c1e16-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="c1e16-178">Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a shuffle jednou z balíčku:</span><span class="sxs-lookup"><span data-stu-id="c1e16-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="c1e16-179">Porovnání</span><span class="sxs-lookup"><span data-stu-id="c1e16-179">Comparisons</span></span>

<span data-ttu-id="c1e16-180">Podívejme se, kolik podle okolí posouvá trvá, než k nastavení z balíčku zpět do její původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="c1e16-181">Musíte se napíše metoda, která určuje, jestli dvě sekvence jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="c1e16-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="c1e16-182">Jakmile budete mít tuto metodu, budete muset umístěte kód, který posouvá z balíčku ve smyčce a zkontrolujte, pokud je balíček zpět v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="c1e16-183">Zápis metodou ke zjištění, jestli dané dvě sekvence jsou stejné by měl být jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c1e16-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="c1e16-184">Je podobné struktury metody, který jste napsali přesouvat z balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="c1e16-185">Jenom tento čas namísto yield vrácení každého prvku, budete porovnáte odpovídajících prvků každé posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="c1e16-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="c1e16-186">Když celé sekvenci vytvoření výčtu, pokud každý prvek odpovídá, sekvencí jsou stejné:</span><span class="sxs-lookup"><span data-stu-id="c1e16-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="c1e16-187">Zobrazí se druhé idiom Linq: terminálu metody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="c1e16-188">Přijmout sekvenci jako vstup (nebo v tomto případě dvou sekvencí) a vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="c1e16-189">Tyto metody, když se používají, jsou vždy poslední metodu dotazu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="c1e16-190">(Tedy název).</span><span class="sxs-lookup"><span data-stu-id="c1e16-190">(Hence the name).</span></span> 

<span data-ttu-id="c1e16-191">Vidíte to v akci při použití pro určení, kdy z balíčku je zpět do její původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="c1e16-192">Shuffle kód uvnitř smyčky a zastavit, když sekvence je zpět do její původní pořadí s použitím `SequenceEquals()` metody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="c1e16-193">Vidíte, že by měl být vždy finální metoda každého dotazu, protože se vrací jedinou hodnotu místo sekvenci:</span><span class="sxs-lookup"><span data-stu-id="c1e16-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="c1e16-194">Spusťte ukázku a zjistěte, jak z balíčku uspořádá na každý shuffle, dokud se vrátí do původní konfigurace po 8 iteracích.</span><span class="sxs-lookup"><span data-stu-id="c1e16-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="c1e16-195">Optimalizace</span><span class="sxs-lookup"><span data-stu-id="c1e16-195">Optimizations</span></span>

<span data-ttu-id="c1e16-196">Ukázka, začlenění zatím provede *si shuffle*, kde horní a dolní části karty zůstat stejná při každém běhu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-196">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="c1e16-197">Pojďme si ho změnit a spusťte *v shuffle*, kde všechny 52 karty změní pozici.</span><span class="sxs-lookup"><span data-stu-id="c1e16-197">Let's make one change, and run an *in shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="c1e16-198">Pro v náhodně, můžete prokládání z balíčku tak, aby první karta v dolní polovině stane první karta balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-198">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="c1e16-199">To znamená, že poslední karty v horní polovině stane dolní části karty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="c1e16-200">To je jen jeden řádek změnit.</span><span class="sxs-lookup"><span data-stu-id="c1e16-200">That's just a one line change.</span></span> <span data-ttu-id="c1e16-201">Volání přesouvat, chcete-li změnit pořadí horní a dolní polovinami z balíčku aktualizace:</span><span class="sxs-lookup"><span data-stu-id="c1e16-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="c1e16-202">Spusťte program znovu, a uvidíte, že trvá 52 iterací z balíčku můžete změnit pořadí samotný.</span><span class="sxs-lookup"><span data-stu-id="c1e16-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="c1e16-203">Budete také začít Všimněte si, že některé jak výkon jako program nadále běží.</span><span class="sxs-lookup"><span data-stu-id="c1e16-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="c1e16-204">Existuje několik důvodů.</span><span class="sxs-lookup"><span data-stu-id="c1e16-204">There are a number of reasons for this.</span></span> <span data-ttu-id="c1e16-205">Pojďme zodpovědět jednou z hlavních příčin: neefektivní používání šablon *opožděné vyhodnocení*.</span><span class="sxs-lookup"><span data-stu-id="c1e16-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="c1e16-206">Laxně vyhodnocují dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="c1e16-207">Sekvence jsou generovány pouze v případě, že prvky jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="c1e16-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="c1e16-208">Který je obvykle hlavní výhodou LINQ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="c1e16-209">Ale používá jako je například tento program, to způsobí, že exponenciální růst v čase spuštění.</span><span class="sxs-lookup"><span data-stu-id="c1e16-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="c1e16-210">Z původního balíčku byl vygenerován pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="c1e16-211">Každý shuffle je generována pomocí provádí tři LINQ dotazy na předchozí balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="c1e16-212">Všechny tyto laxně probíhají.</span><span class="sxs-lookup"><span data-stu-id="c1e16-212">All these are performed lazily.</span></span> <span data-ttu-id="c1e16-213">To také znamená, že se že provádějí se znovu pokaždé, když je požadováno sekvence.</span><span class="sxs-lookup"><span data-stu-id="c1e16-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="c1e16-214">Podle času, který jste získali 52nd iteraci můžete se znova se generuje z původního balíčku mnoho, v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="c1e16-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="c1e16-215">Napíšeme protokolu demonstrují toto chování.</span><span class="sxs-lookup"><span data-stu-id="c1e16-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="c1e16-216">Nakonec vám to vyřešíme.</span><span class="sxs-lookup"><span data-stu-id="c1e16-216">Then, you'll fix it.</span></span>

<span data-ttu-id="c1e16-217">Tady je protokol metody, která může být přidán do jakéhokoli dotazu k označení, že dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="c1e16-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="c1e16-218">V dalším kroku instrumentace definici každého dotazu s zprávu protokolu:</span><span class="sxs-lookup"><span data-stu-id="c1e16-218">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="c1e16-219">Všimněte si, že není přihlásíte pokaždé, když se přístup k dotazu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="c1e16-220">Přihlášení jenom při vytváření původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-220">You log only when you create the original query.</span></span> <span data-ttu-id="c1e16-221">Program stále trvá dlouhou dobu pro spuštění, ale teď se zobrazí důvod, proč.</span><span class="sxs-lookup"><span data-stu-id="c1e16-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="c1e16-222">Pokud spustíte navýšení kapacity o trpělivost spuštění vnitřního shuffle s zapnout protokolování, přepněte zpátky na vnější náhodně.</span><span class="sxs-lookup"><span data-stu-id="c1e16-222">If you run out of patience running the inner shuffle with logging turned on, switch back to the outer shuffle.</span></span> <span data-ttu-id="c1e16-223">Dál uvidíte účinky opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="c1e16-224">Během jednoho spuštění se provede 2592 dotazů, včetně všech generování hodnoty a barvy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="c1e16-225">Je snadný způsob, jak aktualizovat, aby všechny tyto spuštění tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="c1e16-226">Způsoby LINQ `ToArray()` a `ToList()` , který způsobit spustit dotaz a výsledky uložíme v poli, nebo seznam, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1e16-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="c1e16-227">Pomocí těchto metod místo znovu provést dotaz na zdroj dat výsledků dotazu do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c1e16-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="c1e16-228">Připojit dotazy, které generují balíčky karet pomocí volání `ToArray()` a spusťte dotaz znovu:</span><span class="sxs-lookup"><span data-stu-id="c1e16-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="c1e16-229">Spusťte znovu a vnější shuffle je až 30 dotazy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-229">Run again, and the outer shuffle is down to 30 queries.</span></span> <span data-ttu-id="c1e16-230">Spusťte znovu s vnitřní shuffle a zobrazí se vám podobná vylepšení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-230">Run again with the inner shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="c1e16-231">(Je nyní spuštěn 162 dotazy).</span><span class="sxs-lookup"><span data-stu-id="c1e16-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="c1e16-232">V tomto příkladu není interpretuje důkladným, který by měly být například spuštěny všechny dotazy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="c1e16-233">V tomto příkladu je navržen pro zvýraznění případy použití, pokud opožděné vyhodnocení může způsobit potíže s výkonem.</span><span class="sxs-lookup"><span data-stu-id="c1e16-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="c1e16-234">Důvodem je, každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání.</span><span class="sxs-lookup"><span data-stu-id="c1e16-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="c1e16-235">Použití opožděné vyhodnocení znamená každou novou konfiguraci balíčku je sestaven z původního balíčku, i spouští kód, který založená `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="c1e16-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="c1e16-236">Který způsobí, že velké množství práce navíc.</span><span class="sxs-lookup"><span data-stu-id="c1e16-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="c1e16-237">V praxi některé algoritmy spustit mnohem lepší pomocí nemůžou dočkat, až hodnocení a jiné systém mnohem lepší pomocí opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="c1e16-238">(Obecně platí, opožděné vyhodnocení je mnohem lepší volbou, pokud je zdroj dat jako samostatný proces, jako je databázový stroj.</span><span class="sxs-lookup"><span data-stu-id="c1e16-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="c1e16-239">V takových případech opožděné vyhodnocení umožňuje složitější dotazy provádět jenom jednu výměnu zpráv pro proces databáze.) LINQ umožňuje opožděné a nemůžou dočkat, až hodnocení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="c1e16-240">Měřte a vybrat nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="c1e16-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="c1e16-241">Příprava pro nové funkce</span><span class="sxs-lookup"><span data-stu-id="c1e16-241">Preparing for New Features</span></span>

<span data-ttu-id="c1e16-242">Kód, který jste zadali pro tuto ukázku je příklad vytvoření jednoduchého prototyp, která provádí úlohy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="c1e16-243">To je skvělý způsob, jak prozkoumat problém místa, a pro mnoho funkcí, může být nejlepším řešením trvalé.</span><span class="sxs-lookup"><span data-stu-id="c1e16-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="c1e16-244">Jste využít *anonymní typy* pro karty a každá karta představuje řetězce.</span><span class="sxs-lookup"><span data-stu-id="c1e16-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="c1e16-245">*Anonymní typy* mají mnoho výhod produktivitu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="c1e16-246">Není nutné definovat třídu sami sebe k reprezentaci úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1e16-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="c1e16-247">Kompilátor generuje typ za vás.</span><span class="sxs-lookup"><span data-stu-id="c1e16-247">The compiler generates the type for you.</span></span> <span data-ttu-id="c1e16-248">Typ generovaný kompilátorem využívá mnoho osvědčených postupů pro jednoduché datové objekty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="c1e16-249">Má *neměnné*, což znamená, že žádná z její vlastnosti lze změnit poté, co byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c1e16-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="c1e16-250">Anonymní typy jsou interní v sestavení, takže nejsou uvedené jako součást veřejné rozhraní API pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1e16-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="c1e16-251">Anonymní typy také obsahují přepsání `ToString()` metodu, která vrací formátovaný řetězec s všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="c1e16-252">Anonymní typy mají také nevýhody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="c1e16-253">Nemají dostupné názvy, abyste je nelze používat jako návratové hodnoty nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="c1e16-254">Můžete si všimnout, že všechny metody výše, které používají tyto anonymní typy jsou obecné metody.</span><span class="sxs-lookup"><span data-stu-id="c1e16-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="c1e16-255">Přepsané `ToString()` nemusí být žádoucí podle rozšiřování aplikace přidané další funkce.</span><span class="sxs-lookup"><span data-stu-id="c1e16-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="c1e16-256">Ukázka také používá řetězce pro barvu a řazení jednotlivé karty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="c1e16-257">Který je poměrně otevřete byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="c1e16-257">That's quite open ended.</span></span> <span data-ttu-id="c1e16-258">Systém typů jazyka C# nám můžete pomoct dokumenty lepší kód s využitím `enum` typy pro tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="c1e16-259">Začněte barvy.</span><span class="sxs-lookup"><span data-stu-id="c1e16-259">Start with the suits.</span></span> <span data-ttu-id="c1e16-260">To je ten správný čas určený `enum`:</span><span class="sxs-lookup"><span data-stu-id="c1e16-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="c1e16-261">`Suits()` Metoda také změní typ a implementace:</span><span class="sxs-lookup"><span data-stu-id="c1e16-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="c1e16-262">V dalším kroku proveďte stejnou změnu s pořadí karet:</span><span class="sxs-lookup"><span data-stu-id="c1e16-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="c1e16-263">A metoda, která generuje je:</span><span class="sxs-lookup"><span data-stu-id="c1e16-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="c1e16-264">Jako jeden konečný vyčištění vytvoříme typ pro reprezentaci karty, aniž byste museli spoléhat na anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="c1e16-265">Anonymní typy se skvěle hodí pro lightweight, místní typy, ale v tomto příkladu hrací karty je jedním z hlavní koncepty.</span><span class="sxs-lookup"><span data-stu-id="c1e16-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="c1e16-266">Ji by měl být konkrétního typu implementujícího typ.</span><span class="sxs-lookup"><span data-stu-id="c1e16-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="c1e16-267">Tento typ používá *automaticky implementované vlastnosti jen pro čtení* se nastavují v konstruktoru a následně nelze upravit.</span><span class="sxs-lookup"><span data-stu-id="c1e16-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="c1e16-268">Je také využívá [interpolace](../language-reference/tokens/interpolated.md) funkce, která usnadňuje výstupní řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-268">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="c1e16-269">Aktualizujte dotaz, který generuje výchozí balíček použít nový typ:</span><span class="sxs-lookup"><span data-stu-id="c1e16-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="c1e16-270">Zkompilujte a spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-270">Compile and run again.</span></span> <span data-ttu-id="c1e16-271">Výstup je trochu čisticího modulu a kód je o něco trochu objasnit a je možné snadno rozšířit.</span><span class="sxs-lookup"><span data-stu-id="c1e16-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="c1e16-272">Závěr</span><span class="sxs-lookup"><span data-stu-id="c1e16-272">Conclusion</span></span>

<span data-ttu-id="c1e16-273">Tuto ukázku jsme si ukázali, můžete některé z metod používaných v LINQ, jak vytvořit vlastní metody, které se snadno používat s dotazy LINQ povoleno kódu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="c1e16-274">Je také ukázal rozdíly mezi opožděné a nemůžou dočkat, až hodnocení a rozhodnutí může mít na výkon vliv.</span><span class="sxs-lookup"><span data-stu-id="c1e16-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="c1e16-275">Jste se dozvěděli něco o jedné magician technika.</span><span class="sxs-lookup"><span data-stu-id="c1e16-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="c1e16-276">Magicians faro shuffle použít, protože můžete určit, kde prochází všechny karty z balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1e16-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="c1e16-277">V některé tipy magician má členem cílové skupiny umístit karta na balíčku a uspořádá několikrát, znalost, kdy dostane tuto kartu.</span><span class="sxs-lookup"><span data-stu-id="c1e16-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="c1e16-278">Další illusions vyžadovat z balíčku sady určitým způsobem.</span><span class="sxs-lookup"><span data-stu-id="c1e16-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="c1e16-279">Magician nastaví z balíčku před provedením zdvih.</span><span class="sxs-lookup"><span data-stu-id="c1e16-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="c1e16-280">Pak si bude náhodně z balíčku pomocí 5krát vnější shuffle.</span><span class="sxs-lookup"><span data-stu-id="c1e16-280">Then she will shuffle the deck 5 times using an outer shuffle.</span></span> <span data-ttu-id="c1e16-281">Na fázi může zobrazit, jak vypadá náhodné balíčku, náhodný výběr 3 víckrát a z balíčku nastavte přesně jak chce mít.</span><span class="sxs-lookup"><span data-stu-id="c1e16-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
