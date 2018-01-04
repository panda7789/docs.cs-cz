---
title: "Iterátory"
description: "Zjistěte, jak používat integrované iterátory C# a jak vytvořit vlastní vlastní iterator metody."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 0a78fe3aa4d88cd5ea1c98f372e4d6672cff5236
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2017
---
# <a name="iterators"></a><span data-ttu-id="03b0a-104">Iterátory</span><span class="sxs-lookup"><span data-stu-id="03b0a-104">Iterators</span></span>

<span data-ttu-id="03b0a-105">Téměř všechny programy, které můžete psát bude mít některé potřeba iterace v kolekci.</span><span class="sxs-lookup"><span data-stu-id="03b0a-105">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="03b0a-106">Budete psát kód, který hledá každá položka v kolekci.</span><span class="sxs-lookup"><span data-stu-id="03b0a-106">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="03b0a-107">Pokud vytvoříte iterator metody, které jsou metody, které vytváří iterace pro elementy této třídy.</span><span class="sxs-lookup"><span data-stu-id="03b0a-107">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="03b0a-108">Ty lze použít pro:</span><span class="sxs-lookup"><span data-stu-id="03b0a-108">These can be used for:</span></span>

+ <span data-ttu-id="03b0a-109">Provedení akce na každou položku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="03b0a-109">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="03b0a-110">Vytváření výčtu vlastní kolekce.</span><span class="sxs-lookup"><span data-stu-id="03b0a-110">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="03b0a-111">Rozšíření [LINQ](linq/index.md) nebo jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="03b0a-111">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="03b0a-112">Vytváření kde data proudí efektivně prostřednictvím metody iterator datovém kanálu.</span><span class="sxs-lookup"><span data-stu-id="03b0a-112">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="03b0a-113">Jazyk C# poskytuje funkce pro oba tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="03b0a-113">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="03b0a-114">Tento článek obsahuje přehled těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="03b0a-114">This article provides an overview of those features.</span></span>

<span data-ttu-id="03b0a-115">V tomto kurzu má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="03b0a-115">This tutorial has multiple steps.</span></span> <span data-ttu-id="03b0a-116">Po dokončení každého kroku můžete aplikaci spustit a sledovat průběh.</span><span class="sxs-lookup"><span data-stu-id="03b0a-116">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="03b0a-117">Můžete také [zobrazení nebo stažení je hotová ukázka](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="03b0a-117">You can also [view or download the completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) for this topic.</span></span> <span data-ttu-id="03b0a-118">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="03b0a-118">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="03b0a-119">Iterace pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="03b0a-119">Iterating with foreach</span></span>

<span data-ttu-id="03b0a-120">Vytváření výčtu kolekce je jednoduchý: `foreach` – klíčové slovo zobrazí kolekci provádění embedded příkazu jednou pro každý prvek v kolekci:</span><span class="sxs-lookup"><span data-stu-id="03b0a-120">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="03b0a-121">To je všechno je k němu.</span><span class="sxs-lookup"><span data-stu-id="03b0a-121">That's all there is to it.</span></span> <span data-ttu-id="03b0a-122">Iterace nad veškerý obsah do kolekce `foreach` příkaz je vše, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="03b0a-122">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="03b0a-123">`foreach` Příkaz není magic, přestože.</span><span class="sxs-lookup"><span data-stu-id="03b0a-123">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="03b0a-124">Přitom spoléhá na dvě obecné rozhraní definované v základní knihovny .NET, pokud chcete generovat kód nezbytné k iteraci v kolekci: `IEnumerable<T>` a `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="03b0a-124">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="03b0a-125">Tento mechanismus je vysvětlené podrobněji níže.</span><span class="sxs-lookup"><span data-stu-id="03b0a-125">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="03b0a-126">Mají obě tato rozhraní taky neobecné protějšky: `IEnumerable` a `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="03b0a-126">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="03b0a-127">[Obecné](programming-guide/generics/index.md) verze jsou upřednostněny moderní kódu.</span><span class="sxs-lookup"><span data-stu-id="03b0a-127">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="03b0a-128">Výčet zdrojů pomocí metod iterátorů</span><span class="sxs-lookup"><span data-stu-id="03b0a-128">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="03b0a-129">Další skvělé funkcí jazyka C# umožňuje vytvoření metody, které vytvořte zdroj pro výčet.</span><span class="sxs-lookup"><span data-stu-id="03b0a-129">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="03b0a-130">Tyto jsou označovány jako *iterator metody*.</span><span class="sxs-lookup"><span data-stu-id="03b0a-130">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="03b0a-131">Metodu iterator definuje, jak vygenerovat objekty v pořadí vyžádání.</span><span class="sxs-lookup"><span data-stu-id="03b0a-131">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="03b0a-132">Můžete použít `yield return` kontextová klíčová slova k definování metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="03b0a-132">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="03b0a-133">Můžete napsat tuto metodu za účelem vytvoření posloupnost celých čísel od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="03b0a-133">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="03b0a-134">Výše uvedený kód ukazuje odlišné `yield return` příkazy, abyste měli na očích faktů, které můžete použít více diskrétní `yield return` příkazy v metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="03b0a-134">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="03b0a-135">Můžete (a často udělat) pomocí jiných jazykové konstrukty můžete zjednodušit kód metody iterator.</span><span class="sxs-lookup"><span data-stu-id="03b0a-135">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="03b0a-136">Následující metoda definice poskytne přesně stejnou sekvenci čísla:</span><span class="sxs-lookup"><span data-stu-id="03b0a-136">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="03b0a-137">Nemáte k rozhodování o jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="03b0a-137">You don't have to decide one or the other.</span></span> <span data-ttu-id="03b0a-138">Může mít jako mnoho `yield return` příkazy podle potřeby, aby vyhovovaly vaší metody:</span><span class="sxs-lookup"><span data-stu-id="03b0a-138">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="03b0a-139">To je základní syntaxe.</span><span class="sxs-lookup"><span data-stu-id="03b0a-139">That's the basic syntax.</span></span> <span data-ttu-id="03b0a-140">Pojďme se podívat v reálném světě příkladu, kde by zápis metody iterator.</span><span class="sxs-lookup"><span data-stu-id="03b0a-140">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="03b0a-141">Představte si jste v projektu IoT a snímače zařízení generovat velmi velký datový proud.</span><span class="sxs-lookup"><span data-stu-id="03b0a-141">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="03b0a-142">Podívat, pro data, může napíše metoda, která ukázky každých n-tou datový prvek.</span><span class="sxs-lookup"><span data-stu-id="03b0a-142">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="03b0a-143">Tato metoda malé iterator nemá efektu:</span><span class="sxs-lookup"><span data-stu-id="03b0a-143">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="03b0a-144">Neexistuje jeden důležité omezení iterator metody: nemůže mít obě `return` příkaz a `yield return` příkaz v stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="03b0a-144">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="03b0a-145">Kompilace nebude:</span><span class="sxs-lookup"><span data-stu-id="03b0a-145">The following will not compile:</span></span>

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

<span data-ttu-id="03b0a-146">Toto omezení obvykle není problém.</span><span class="sxs-lookup"><span data-stu-id="03b0a-146">This restriction normally isn't a problem.</span></span> <span data-ttu-id="03b0a-147">Máte možnost volby buď pomocí `yield return` v rámci metodu nebo metodu původní rozdělit do několika metod, některé pomocí `return`a některé pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="03b0a-147">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="03b0a-148">Můžete upravit jako poslední metodu mírně `yield return` everywhere:</span><span class="sxs-lookup"><span data-stu-id="03b0a-148">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="03b0a-149">V některých případech je pravé odpovědi metodu iterator rozdělit na dvě různé metody.</span><span class="sxs-lookup"><span data-stu-id="03b0a-149">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="03b0a-150">Ten, který používá `return`a druhou, která používá `yield return`.</span><span class="sxs-lookup"><span data-stu-id="03b0a-150">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="03b0a-151">Představte si situaci, kde můžete chtít vrátit prázdnou kolekci nebo prvních 5 liché čísla podle argumentem logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="03b0a-151">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="03b0a-152">Který může zapsat jako tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="03b0a-152">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="03b0a-153">Podívejte se na výše uvedené metody.</span><span class="sxs-lookup"><span data-stu-id="03b0a-153">Look at the methods above.</span></span> <span data-ttu-id="03b0a-154">První způsob využívá standardní `return` příkaz, který má vrátit prázdnou kolekci, nebo iterator vytvořené druhé metody.</span><span class="sxs-lookup"><span data-stu-id="03b0a-154">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="03b0a-155">Druhý způsob využívá `yield return` příkaz k vytvoření požadované pořadí.</span><span class="sxs-lookup"><span data-stu-id="03b0a-155">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="03b0a-156">Podrobnější prohlídku do`foreach`</span><span class="sxs-lookup"><span data-stu-id="03b0a-156">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="03b0a-157">`foreach` Příkaz rozšíří na standardní stylu, které používá `IEnumerable<T>` a `IEnumerator<T>` rozhraní k iteraci v rámci všechny elementy z kolekce.</span><span class="sxs-lookup"><span data-stu-id="03b0a-157">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="03b0a-158">Minimalizuje také chyb, které vývojáři, aby byly správně řízení zdrojů.</span><span class="sxs-lookup"><span data-stu-id="03b0a-158">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="03b0a-159">Kompilátor převádí `foreach` smyčky uvedené v prvním příkladu do něco podobného jako tento konstrukce:</span><span class="sxs-lookup"><span data-stu-id="03b0a-159">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="03b0a-160">Konstrukce výše představuje kód vygenerovaný kompilátor C# od verze 5 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="03b0a-160">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="03b0a-161">Starší než verze 5 `item` proměnná měl jiný rozsah:</span><span class="sxs-lookup"><span data-stu-id="03b0a-161">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="03b0a-162">To se změnit, protože starší chování může vést k jemně a těžko diagnostikovat chyby zahrnující výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="03b0a-162">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="03b0a-163">Projděte část o [výrazy lambda](lambda-expressions.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="03b0a-163">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="03b0a-164">Přesný kód vygenerovaný kompilátor je trochu složitější a zpracovává situacích, kde se objekt vrácený `GetEnumerator()` implementuje `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03b0a-164">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="03b0a-165">Plnou expanzí generuje kód další takto:</span><span class="sxs-lookup"><span data-stu-id="03b0a-165">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="03b0a-166">Způsob, ve kterém je odstraněn enumerátor závisí na vlastnosti typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="03b0a-166">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="03b0a-167">V případě Obecné `finally` klauzule zasahuje do:</span><span class="sxs-lookup"><span data-stu-id="03b0a-167">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="03b0a-168">Ale pokud typ `enumerator` je typu zapečetěné a neexistuje žádný implicitní převod z typu `enumerator` k `IDisposable`, `finally` klauzule zasahuje do bloku prázdný:</span><span class="sxs-lookup"><span data-stu-id="03b0a-168">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="03b0a-169">Pokud je implicitní převod z typu `enumerator` k `IDisposable`, a `enumerator` je typ hodnot neumožňující hodnotu Null, `finally` klauzule zasahuje do:</span><span class="sxs-lookup"><span data-stu-id="03b0a-169">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="03b0a-170">Naštěstí nemusíte pamatovat si tyto podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="03b0a-170">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="03b0a-171">`foreach` Příkaz zpracovává všechny tyto drobné odlišnosti za vás.</span><span class="sxs-lookup"><span data-stu-id="03b0a-171">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="03b0a-172">Kompilátor vygeneruje správný kód pro některý z těchto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="03b0a-172">The compiler will generate the correct code for any of these constructs.</span></span> 


