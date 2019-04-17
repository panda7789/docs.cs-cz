---
title: Iterátory
description: Zjistěte, jak použít integrovaný C# iterátory a jak vytvořit vlastní vlastní iterátory.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: e816af698a39a4b44aefa92017efdbc9e3c8cc1d
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613431"
---
# <a name="iterators"></a><span data-ttu-id="412ce-103">Iterátory</span><span class="sxs-lookup"><span data-stu-id="412ce-103">Iterators</span></span>

<span data-ttu-id="412ce-104">Téměř každá program, který napíšete bude mít některé nutnost opakování v kolekci.</span><span class="sxs-lookup"><span data-stu-id="412ce-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="412ce-105">Budete psát kód, který ověřuje, zda každá položka v kolekci.</span><span class="sxs-lookup"><span data-stu-id="412ce-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="412ce-106">Také vytvoříte metody iterátoru, které jsou metody, které vytvoří iterátor pro elementy třídy.</span><span class="sxs-lookup"><span data-stu-id="412ce-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="412ce-107">Ty je možné použít pro:</span><span class="sxs-lookup"><span data-stu-id="412ce-107">These can be used for:</span></span>

+ <span data-ttu-id="412ce-108">Provést akci pro každou položku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="412ce-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="412ce-109">Vytváření výčtu vlastní kolekce.</span><span class="sxs-lookup"><span data-stu-id="412ce-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="412ce-110">Rozšíření [LINQ](linq/index.md) nebo jiných knihoven.</span><span class="sxs-lookup"><span data-stu-id="412ce-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="412ce-111">Vytvoření datového kanálu, kde data protékají efektivně iterátory.</span><span class="sxs-lookup"><span data-stu-id="412ce-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="412ce-112">C# Jazyk poskytuje funkce pro oba tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="412ce-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="412ce-113">Tento článek obsahuje přehled těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="412ce-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="412ce-114">V tomto kurzu má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="412ce-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="412ce-115">Po provedení každého kroku můžete spustit aplikaci a sledovat průběh.</span><span class="sxs-lookup"><span data-stu-id="412ce-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="412ce-116">Můžete také [zobrazení nebo stažení je hotová ukázka](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="412ce-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="412ce-117">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="412ce-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="412ce-118">Iterace pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="412ce-118">Iterating with foreach</span></span>

<span data-ttu-id="412ce-119">Vytvoření výčtu kolekce je jednoduchý: `foreach` – Klíčové slovo vytvoří výčet kolekce, provádění vloženým příkazem jednou pro každý prvek v kolekci:</span><span class="sxs-lookup"><span data-stu-id="412ce-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="412ce-120">To je všechno je to.</span><span class="sxs-lookup"><span data-stu-id="412ce-120">That's all there is to it.</span></span> <span data-ttu-id="412ce-121">K iteraci přes veškerý obsah kolekce `foreach` příkaz je všechno, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="412ce-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="412ce-122">`foreach` Příkazu není magic, i když.</span><span class="sxs-lookup"><span data-stu-id="412ce-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="412ce-123">Spoléhá na dvě obecné rozhraní definované v knihovně .NET core k vygenerování kódu potřebného k iteraci v kolekci: `IEnumerable<T>` a `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="412ce-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="412ce-124">Tento mechanismus je podrobněji vysvětleny níže.</span><span class="sxs-lookup"><span data-stu-id="412ce-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="412ce-125">Obě tato rozhraní mají také jejich obecné protějšky: `IEnumerable` a `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="412ce-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="412ce-126">[Obecný](programming-guide/generics/index.md) verze jsou upřednostněny moderní kód.</span><span class="sxs-lookup"><span data-stu-id="412ce-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="412ce-127">Výčet zdrojů s iterátory</span><span class="sxs-lookup"><span data-stu-id="412ce-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="412ce-128">Další skvělou funkcí služby C# jazyka vám umožní sestavovat metody, které vytvoří zdroj pro výčet.</span><span class="sxs-lookup"><span data-stu-id="412ce-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="412ce-129">Tyto jsou označovány jako *iterátory*.</span><span class="sxs-lookup"><span data-stu-id="412ce-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="412ce-130">Metodu iterátoru definuje, jak generovat objekty v posloupnosti na požádání.</span><span class="sxs-lookup"><span data-stu-id="412ce-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="412ce-131">Můžete použít `yield return` kontextová klíčová slova, chcete-li definovat metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="412ce-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="412ce-132">Můžete napsat tuto metodu za účelem vytvoření sekvence celých čísel od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="412ce-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="412ce-133">Výše uvedený kód ukazuje různé `yield return` příkazy, abyste měli na očích faktů, které můžete použít více samostatných `yield return` příkazy v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="412ce-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="412ce-134">Můžete (a často tomu) pomocí jiných objektů, které jazyk můžete zjednodušit kód metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="412ce-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="412ce-135">Následující definici metody vytvoří přesně stejnou sekvenci čísel:</span><span class="sxs-lookup"><span data-stu-id="412ce-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="412ce-136">Není nutné se rozhodnout, jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="412ce-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="412ce-137">Můžete mít kolik `yield return` příkazy podle potřeby pro potřeby metodu:</span><span class="sxs-lookup"><span data-stu-id="412ce-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    index = 100;
    while (index++ < 110)
        yield return index;
}
```

<span data-ttu-id="412ce-138">To je základní syntaxe.</span><span class="sxs-lookup"><span data-stu-id="412ce-138">That's the basic syntax.</span></span> <span data-ttu-id="412ce-139">Pojďme se na příklad reálného světa, kde by zapisovat metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="412ce-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="412ce-140">Představte si jste na IoT projektu a generovat velmi velké datový proud s daty senzorů zařízení.</span><span class="sxs-lookup"><span data-stu-id="412ce-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="412ce-141">Chcete-li získat představu pro data, můžete například napsat metodu, která ukázky každý element n-tý data.</span><span class="sxs-lookup"><span data-stu-id="412ce-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="412ce-142">Tato metoda malé iterátoru provede trik, jak zajistit:</span><span class="sxs-lookup"><span data-stu-id="412ce-142">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="412ce-143">Existuje jedna důležitá omezení iterátory: nemůže mít oba `return` příkaz a `yield return` příkaz v stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="412ce-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="412ce-144">Nebude kompilovat následující:</span><span class="sxs-lookup"><span data-stu-id="412ce-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

<span data-ttu-id="412ce-145">Toto omezení se obvykle problém.</span><span class="sxs-lookup"><span data-stu-id="412ce-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="412ce-146">Máte možnost buď pomocí `yield return` v rámci metody nebo oddělení původní metody do více metod, pomocí některé `return`a některé pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="412ce-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="412ce-147">Můžete upravit poslední metody mírně pro použití `yield return` všude:</span><span class="sxs-lookup"><span data-stu-id="412ce-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

<span data-ttu-id="412ce-148">V některých případech je správná odpověď metody iterátoru rozdělit na dvě různé metody.</span><span class="sxs-lookup"><span data-stu-id="412ce-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="412ce-149">Ten, který používá `return`a druhý, který používá `yield return`.</span><span class="sxs-lookup"><span data-stu-id="412ce-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="412ce-150">Představte si situaci, kde můžete chtít vrátit prázdnou kolekci nebo prvních 5 lichých čísel podle logický argument.</span><span class="sxs-lookup"><span data-stu-id="412ce-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="412ce-151">Který může zapsat jako tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="412ce-151">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```

<span data-ttu-id="412ce-152">Podívejte se na metod uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="412ce-152">Look at the methods above.</span></span> <span data-ttu-id="412ce-153">První způsob využívá standardní `return` příkaz vrátit prázdnou kolekci nebo vytvořené pomocí druhé metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="412ce-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="412ce-154">Druhá metoda používá `yield return` příkaz pro vytvoření požadovaného pořadí.</span><span class="sxs-lookup"><span data-stu-id="412ce-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="412ce-155">Prozkoumejte podrobněji `foreach`</span><span class="sxs-lookup"><span data-stu-id="412ce-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="412ce-156">`foreach` Příkaz rozšíří na standardní idiom, který používá `IEnumerable<T>` a `IEnumerator<T>` rozhraní k iteraci v rámci všech prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="412ce-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="412ce-157">Také minimalizuje chyb, které vývojář podá tím, že není správně spravuje prostředky.</span><span class="sxs-lookup"><span data-stu-id="412ce-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="412ce-158">Kompilátor překládá `foreach` smyčky do něco podobného pro tento konstruktor je znázorněno v prvním příkladu:</span><span class="sxs-lookup"><span data-stu-id="412ce-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="412ce-159">Konstrukce výše představuje kód vygenerovaný C# kompilátoru od verze 5 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="412ce-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="412ce-160">Starší než verze 5 `item` proměnná měla jiného oboru:</span><span class="sxs-lookup"><span data-stu-id="412ce-160">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="412ce-161">To se změnit, protože starší chování může vést k nejnenápadnější a těžko Diagnostikujte chyby týkající se výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="412ce-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="412ce-162">Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="412ce-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="412ce-163">Přesný kód generovaný kompilátorem je o něco složitější a zpracovává situacích, kde objekt vrácený `GetEnumerator()` implementuje `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="412ce-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="412ce-164">Plnou expanzí generuje kód další takto:</span><span class="sxs-lookup"><span data-stu-id="412ce-164">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="412ce-165">Způsob, ve kterém je enumerátor odstraněny závisí na vlastnosti typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="412ce-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="412ce-166">V tomto obecném případě `finally` klauzule rozšíří na:</span><span class="sxs-lookup"><span data-stu-id="412ce-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="412ce-167">Nicméně pokud typu `enumerator` je zapečetěný typ a neexistuje žádný implicitní převod z typu `enumerator` k `IDisposable`, `finally` klauzule rozšíří na prázdný blok:</span><span class="sxs-lookup"><span data-stu-id="412ce-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="412ce-168">Pokud je implicitní převod z typu `enumerator` k `IDisposable`, a `enumerator` je typ hodnoty Null, `finally` klauzule rozšíří na:</span><span class="sxs-lookup"><span data-stu-id="412ce-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="412ce-169">Naštěstí nemusíte pamatovat si tyto podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="412ce-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="412ce-170">`foreach` Příkaz zpracuje za vás tyto drobné rozdíly.</span><span class="sxs-lookup"><span data-stu-id="412ce-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="412ce-171">Bude kompilátor generovat správný kód pro některý z těchto konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="412ce-171">The compiler will generate the correct code for any of these constructs.</span></span>
