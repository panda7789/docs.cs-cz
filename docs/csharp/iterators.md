---
title: Iterátory
description: Naučte se používat integrované c# iterátory a jak vytvořit vlastní metody iterátoru.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 1933ecf83e9fa234f9b88c815d8ab527997c97f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399614"
---
# <a name="iterators"></a><span data-ttu-id="1e507-103">Iterátory</span><span class="sxs-lookup"><span data-stu-id="1e507-103">Iterators</span></span>

<span data-ttu-id="1e507-104">Téměř každý program, který napíšete, bude mít nějakou potřebu iterate přes sbírku.</span><span class="sxs-lookup"><span data-stu-id="1e507-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="1e507-105">Napíšete kód, který zkoumá každou položku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1e507-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="1e507-106">Budete také vytvořit iterátor metody, které jsou metody, které vytváří iterátor pro prvky této třídy.</span><span class="sxs-lookup"><span data-stu-id="1e507-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="1e507-107">Ty mohou být použity pro:</span><span class="sxs-lookup"><span data-stu-id="1e507-107">These can be used for:</span></span>

+ <span data-ttu-id="1e507-108">Provedení akce pro každou položku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1e507-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="1e507-109">Výčet vlastní kolekce.</span><span class="sxs-lookup"><span data-stu-id="1e507-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="1e507-110">Rozšíření [LINQ](linq/index.md) nebo jiných knihoven.</span><span class="sxs-lookup"><span data-stu-id="1e507-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="1e507-111">Vytvoření datového kanálu, kde data efektivně proudí prostřednictvím metod iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1e507-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="1e507-112">Jazyk C# poskytuje funkce pro oba tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="1e507-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="1e507-113">Tento článek obsahuje přehled těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="1e507-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="1e507-114">Tento kurz má několik kroků.</span><span class="sxs-lookup"><span data-stu-id="1e507-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="1e507-115">Po každém kroku můžete spustit aplikaci a zobrazit průběh.</span><span class="sxs-lookup"><span data-stu-id="1e507-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="1e507-116">Můžete také [zobrazit nebo stáhnout dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="1e507-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="1e507-117">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1e507-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="1e507-118">Iterace s foreach</span><span class="sxs-lookup"><span data-stu-id="1e507-118">Iterating with foreach</span></span>

<span data-ttu-id="1e507-119">Výčet kolekce je jednoduchý: `foreach` Klíčové slovo vyjmenovává kolekci a jednou provede vložený příkaz pro každý prvek v kolekci:</span><span class="sxs-lookup"><span data-stu-id="1e507-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="1e507-120">A to je vše.</span><span class="sxs-lookup"><span data-stu-id="1e507-120">That's all there is to it.</span></span> <span data-ttu-id="1e507-121">Chcete-li iterate přes veškerý obsah `foreach` kolekce, prohlášení je vše, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="1e507-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="1e507-122">To `foreach` prohlášení ale není kouzelné.</span><span class="sxs-lookup"><span data-stu-id="1e507-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="1e507-123">Spoléhá se na dvě obecná rozhraní definovaná v základní knihovně .NET za účelem `IEnumerable<T>` `IEnumerator<T>`generování kódu potřebného k iterovat kolekci: a .</span><span class="sxs-lookup"><span data-stu-id="1e507-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="1e507-124">Tento mechanismus je podrobněji vysvětlen níže.</span><span class="sxs-lookup"><span data-stu-id="1e507-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="1e507-125">Obě tato rozhraní mají také neobecné `IEnumerable` protějšky: a `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="1e507-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="1e507-126">[Obecné](programming-guide/generics/index.md) verze jsou upřednostňovány pro moderní kód.</span><span class="sxs-lookup"><span data-stu-id="1e507-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="1e507-127">Zdroje výčtu pomocí metod iterátoru</span><span class="sxs-lookup"><span data-stu-id="1e507-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="1e507-128">Další skvělá funkce jazyka C# umožňuje vytvářet metody, které vytvářejí zdroj pro výčet.</span><span class="sxs-lookup"><span data-stu-id="1e507-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="1e507-129">Tyto metody se označují jako *metody iterátoru*.</span><span class="sxs-lookup"><span data-stu-id="1e507-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="1e507-130">Metoda iterátoru definuje, jak generovat objekty v pořadí na požádání.</span><span class="sxs-lookup"><span data-stu-id="1e507-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="1e507-131">Kontextová `yield return` klíčová slova slouží k definování metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1e507-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="1e507-132">Tuto metodu můžete napsat k vytvoření posloupnosti celých čísel od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="1e507-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="1e507-133">Výše uvedený kód `yield return` ukazuje odlišné příkazy zvýraznit `yield return` skutečnost, že můžete použít více diskrétní příkazy v iterátor metody.</span><span class="sxs-lookup"><span data-stu-id="1e507-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="1e507-134">Můžete (a často dělat) použít jiné jazykové konstrukce pro zjednodušení kódu metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1e507-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="1e507-135">Níže uvedená definice metody vytváří přesně stejnou posloupnost čísel:</span><span class="sxs-lookup"><span data-stu-id="1e507-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="1e507-136">Nemusíš rozhodovat o jednom nebo druhém.</span><span class="sxs-lookup"><span data-stu-id="1e507-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="1e507-137">Můžete mít tolik `yield return` příkazů, kolik je potřeba, aby vyhovovaly potřebám vaší metody:</span><span class="sxs-lookup"><span data-stu-id="1e507-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

<span data-ttu-id="1e507-138">To je základní syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1e507-138">That's the basic syntax.</span></span> <span data-ttu-id="1e507-139">Podívejme se na příklad reálného světa, kde byste napsali metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1e507-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="1e507-140">Představte si, že jste na projektu IoT a senzory zařízení generují velmi velký proud dat.</span><span class="sxs-lookup"><span data-stu-id="1e507-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="1e507-141">Chcete-li získat cit pro data, můžete napsat metodu, která vzorky každý n-tý datový prvek.</span><span class="sxs-lookup"><span data-stu-id="1e507-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="1e507-142">Tato malá metoda iterátoru dělá trik:</span><span class="sxs-lookup"><span data-stu-id="1e507-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="1e507-143">Existuje jedno důležité omezení metod iterátoru: nemůžete mít `return` jak `yield return` příkaz, tak příkaz ve stejné metodě.</span><span class="sxs-lookup"><span data-stu-id="1e507-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="1e507-144">Následující nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="1e507-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

<span data-ttu-id="1e507-145">Toto omezení obvykle není problém.</span><span class="sxs-lookup"><span data-stu-id="1e507-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="1e507-146">Máte na výběr buď `yield return` pomocí v rámci metody, nebo oddělení původní `return`metody do `yield return`více metod, některé pomocí a některé pomocí .</span><span class="sxs-lookup"><span data-stu-id="1e507-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="1e507-147">Můžete upravit poslední metodu mírně `yield return` použít všude:</span><span class="sxs-lookup"><span data-stu-id="1e507-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

<span data-ttu-id="1e507-148">Někdy je správnou odpovědí rozdělení metody iterátoru na dvě různé metody.</span><span class="sxs-lookup"><span data-stu-id="1e507-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="1e507-149">Jeden, `return`který používá , `yield return`a druhý, který používá .</span><span class="sxs-lookup"><span data-stu-id="1e507-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="1e507-150">Zvažte situaci, kdy můžete chtít vrátit prázdnou kolekci nebo prvních 5 lichých čísel na základě logického argumentu.</span><span class="sxs-lookup"><span data-stu-id="1e507-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="1e507-151">Dalo by se napsat, že jako tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="1e507-151">You could write that as these two methods:</span></span>

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
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

<span data-ttu-id="1e507-152">Podívejte se na výše uvedené metody.</span><span class="sxs-lookup"><span data-stu-id="1e507-152">Look at the methods above.</span></span> <span data-ttu-id="1e507-153">První používá standardní `return` příkaz vrátit buď prázdnou kolekci nebo iterátor vytvořený druhou metodou.</span><span class="sxs-lookup"><span data-stu-id="1e507-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="1e507-154">Druhá metoda používá `yield return` příkaz k vytvoření požadované sekvence.</span><span class="sxs-lookup"><span data-stu-id="1e507-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="1e507-155">Hlouběji ponořte se do`foreach`</span><span class="sxs-lookup"><span data-stu-id="1e507-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="1e507-156">Příkaz `foreach` rozbalí do standardní idiom, `IEnumerable<T>` `IEnumerator<T>` který používá a rozhraní iterát u všech prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="1e507-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="1e507-157">Také minimalizuje chyby, které vývojáři dělají tím, že správně nespravují prostředky.</span><span class="sxs-lookup"><span data-stu-id="1e507-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="1e507-158">Kompilátor přeloží smyčku zobrazenou `foreach` v prvním příkladu na něco podobného této konstrukci:</span><span class="sxs-lookup"><span data-stu-id="1e507-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="1e507-159">Konstrukce výše představuje kód generovaný kompilátorem Jazyka C# od verze 5 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="1e507-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="1e507-160">Před verzí 5 `item` měla proměnná jiný rozsah:</span><span class="sxs-lookup"><span data-stu-id="1e507-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="1e507-161">To bylo změněno, protože dřívější chování může vést k jemné a těžko diagnostikovat chyby zahrnující lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="1e507-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="1e507-162">Další informace o výrazech lambda naleznete v tématu [Lambda výrazy](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1e507-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="1e507-163">Přesný kód generovaný kompilátorem je poněkud složitější a zpracovává situace, kdy objekt vrácený implementuje `GetEnumerator()` `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e507-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="1e507-164">Úplné rozšíření generuje kód více takto:</span><span class="sxs-lookup"><span data-stu-id="1e507-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="1e507-165">Způsob, jakým je čítač zlikvidován, závisí `enumerator`na vlastnostech typu .</span><span class="sxs-lookup"><span data-stu-id="1e507-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="1e507-166">V obecném případě `finally` se doložka rozšiřuje na:</span><span class="sxs-lookup"><span data-stu-id="1e507-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="1e507-167">`enumerator` Pokud je však typ zapečetěného typu a neexistuje žádný `enumerator` implicitní převod z typu na `IDisposable`, `finally` klauzule se rozbalí na prázdný blok:</span><span class="sxs-lookup"><span data-stu-id="1e507-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="1e507-168">Pokud je implicitní převod z `enumerator` `IDisposable`typu `enumerator` na , a je non-null typ hodnoty, `finally` klauzule rozbalí na:</span><span class="sxs-lookup"><span data-stu-id="1e507-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="1e507-169">Naštěstí si nemusíte pamatovat všechny tyto detaily.</span><span class="sxs-lookup"><span data-stu-id="1e507-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="1e507-170">Prohlášení `foreach` zpracovává všechny tyto nuance pro vás.</span><span class="sxs-lookup"><span data-stu-id="1e507-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="1e507-171">Kompilátor vygeneruje správný kód pro všechny tyto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1e507-171">The compiler will generate the correct code for any of these constructs.</span></span>
