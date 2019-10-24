---
title: Iterátory
description: Naučte se používat integrované C# iterátory a vytvářet vlastní metody iterátoru.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: c378ceb651eed7e7a3d8c738bd4b2b3cf7de2a0f
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773879"
---
# <a name="iterators"></a><span data-ttu-id="23b7f-103">Iterátory</span><span class="sxs-lookup"><span data-stu-id="23b7f-103">Iterators</span></span>

<span data-ttu-id="23b7f-104">Skoro každý program, který napíšete, bude nutné iterovat v kolekci.</span><span class="sxs-lookup"><span data-stu-id="23b7f-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="23b7f-105">Budete psát kód, který prověřuje každou položku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="23b7f-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="23b7f-106">Také vytvoříte iterátory, které jsou metody, které vytvoří iterátor pro prvky této třídy.</span><span class="sxs-lookup"><span data-stu-id="23b7f-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="23b7f-107">Můžete je použít pro:</span><span class="sxs-lookup"><span data-stu-id="23b7f-107">These can be used for:</span></span>

+ <span data-ttu-id="23b7f-108">Provedení akce u každé položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="23b7f-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="23b7f-109">Vytváří se výčet vlastní kolekce.</span><span class="sxs-lookup"><span data-stu-id="23b7f-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="23b7f-110">Rozšíření [LINQ](linq/index.md) nebo jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="23b7f-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="23b7f-111">Vytvoření datového kanálu, ve kterém data efektivně proudí prostřednictvím metod iterátoru.</span><span class="sxs-lookup"><span data-stu-id="23b7f-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="23b7f-112">C# Jazyk poskytuje funkce pro oba tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="23b7f-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="23b7f-113">Tento článek obsahuje přehled těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="23b7f-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="23b7f-114">V tomto kurzu se používá několik kroků.</span><span class="sxs-lookup"><span data-stu-id="23b7f-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="23b7f-115">Po každém kroku můžete spustit aplikaci a zobrazit průběh.</span><span class="sxs-lookup"><span data-stu-id="23b7f-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="23b7f-116">Můžete také [Zobrazit nebo stáhnout dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="23b7f-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="23b7f-117">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="23b7f-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="23b7f-118">Iterace pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="23b7f-118">Iterating with foreach</span></span>

<span data-ttu-id="23b7f-119">Výčet kolekce je jednoduchý: klíčové slovo `foreach` vytvoří výčet kolekce a jednou spustí vložený příkaz pro každý prvek v kolekci:</span><span class="sxs-lookup"><span data-stu-id="23b7f-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="23b7f-120">To je všechno, co je to vše.</span><span class="sxs-lookup"><span data-stu-id="23b7f-120">That's all there is to it.</span></span> <span data-ttu-id="23b7f-121">Chcete-li iterovat všechny obsahy kolekce, příkaz `foreach` je vše, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="23b7f-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="23b7f-122">Příkaz `foreach` není Magic, i když.</span><span class="sxs-lookup"><span data-stu-id="23b7f-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="23b7f-123">Spoléhá se na dvě Obecná rozhraní definovaná v knihovně .NET Core, aby bylo možné vygenerovat kód potřebný k iteraci kolekce: `IEnumerable<T>` a `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="23b7f-124">Tento mechanismus je podrobněji vysvětlen níže.</span><span class="sxs-lookup"><span data-stu-id="23b7f-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="23b7f-125">Obě tato rozhraní mají také neobecné protějšky: `IEnumerable` a `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="23b7f-126">[Obecné](programming-guide/generics/index.md) verze jsou upřednostňovány pro moderní kód.</span><span class="sxs-lookup"><span data-stu-id="23b7f-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="23b7f-127">Výčtové zdroje s metodami iterátoru</span><span class="sxs-lookup"><span data-stu-id="23b7f-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="23b7f-128">Další skvělou funkcí C# jazyka je umožňuje vytvořit metody, které vytvoří zdroj pro výčet.</span><span class="sxs-lookup"><span data-stu-id="23b7f-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="23b7f-129">Tyto metody se označují jako *iterátory*.</span><span class="sxs-lookup"><span data-stu-id="23b7f-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="23b7f-130">Metoda iterátoru definuje způsob generování objektů v pořadí podle požadavku.</span><span class="sxs-lookup"><span data-stu-id="23b7f-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="23b7f-131">K definování metody iterátoru slouží kontextové klíčové slovo `yield return`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="23b7f-132">Tuto metodu můžete zapsat pro vytvoření posloupnosti celých čísel od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="23b7f-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="23b7f-133">Výše uvedený kód ukazuje odlišné příkazy `yield return` pro zvýraznění faktu, že můžete použít více diskrétních `yield return`ch příkazů v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="23b7f-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="23b7f-134">Můžete (a často) použít jiné jazykové konstrukce pro zjednodušení kódu metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="23b7f-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="23b7f-135">Následující definice metody vytváří přesně stejnou sekvenci čísel:</span><span class="sxs-lookup"><span data-stu-id="23b7f-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="23b7f-136">Nemusíte se rozhodnout ani jedno z nich.</span><span class="sxs-lookup"><span data-stu-id="23b7f-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="23b7f-137">Pro splnění požadavků vaší metody můžete mít tolik `yield return` příkazů:</span><span class="sxs-lookup"><span data-stu-id="23b7f-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="23b7f-138">To je základní syntaxe.</span><span class="sxs-lookup"><span data-stu-id="23b7f-138">That's the basic syntax.</span></span> <span data-ttu-id="23b7f-139">Pojďme se na příklad reálného světa, kde byste napsali metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="23b7f-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="23b7f-140">Představte si, že jste v projektu IoT a senzory zařízení generují velmi velký proud dat.</span><span class="sxs-lookup"><span data-stu-id="23b7f-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="23b7f-141">Chcete-li pro data získat dojem, můžete napsat metodu, která bude odebírat každý n-tý datový prvek.</span><span class="sxs-lookup"><span data-stu-id="23b7f-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="23b7f-142">Tato metoda malého iterátoru dělá štych:</span><span class="sxs-lookup"><span data-stu-id="23b7f-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="23b7f-143">Existují jedna důležitá omezení pro metody iterátoru: ve stejné metodě nemůžete mít příkaz `return` a `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="23b7f-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="23b7f-144">Následující kroky nebudou zkompilovány:</span><span class="sxs-lookup"><span data-stu-id="23b7f-144">The following will not compile:</span></span>

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

<span data-ttu-id="23b7f-145">Toto omezení se obvykle nejedná o problém.</span><span class="sxs-lookup"><span data-stu-id="23b7f-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="23b7f-146">Máte možnost volby buď pomocí `yield return` v rámci této metody, nebo oddělením původní metody do více metod, některých pomocí `return` a některých pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="23b7f-147">Poslední metodu můžete upravit mírně a použít `yield return` všude:</span><span class="sxs-lookup"><span data-stu-id="23b7f-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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

<span data-ttu-id="23b7f-148">V některých případech je správná odpověď rozdělením metody iterátoru do dvou různých metod.</span><span class="sxs-lookup"><span data-stu-id="23b7f-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="23b7f-149">Ten používá `return` a druhý, který používá `yield return`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="23b7f-150">Vezměte v úvahu situaci, kdy byste mohli chtít vrátit prázdnou kolekci, nebo prvních 5 lichých čísel na základě argumentu Boolean.</span><span class="sxs-lookup"><span data-stu-id="23b7f-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="23b7f-151">Můžete napsat tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="23b7f-151">You could write that as these two methods:</span></span>

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

<span data-ttu-id="23b7f-152">Podívejte se na výše uvedené metody.</span><span class="sxs-lookup"><span data-stu-id="23b7f-152">Look at the methods above.</span></span> <span data-ttu-id="23b7f-153">První používá příkaz standardní `return` pro vrácení prázdné kolekce nebo iterátoru vytvořeného druhou metodou.</span><span class="sxs-lookup"><span data-stu-id="23b7f-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="23b7f-154">Druhá metoda používá příkaz `yield return` k vytvoření požadované sekvence.</span><span class="sxs-lookup"><span data-stu-id="23b7f-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="23b7f-155">Hlubší podrobně do `foreach`</span><span class="sxs-lookup"><span data-stu-id="23b7f-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="23b7f-156">Příkaz `foreach` se rozšíří na standardní idiom, který používá rozhraní `IEnumerable<T>` a `IEnumerator<T>` k iterování napříč všemi prvky kolekce.</span><span class="sxs-lookup"><span data-stu-id="23b7f-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="23b7f-157">Také minimalizuje chyby, které vývojáři vytvářejí při nesprávné správě prostředků.</span><span class="sxs-lookup"><span data-stu-id="23b7f-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="23b7f-158">Kompilátor transformuje `foreach` cyklus zobrazený v prvním příkladu na něco podobného této konstrukci:</span><span class="sxs-lookup"><span data-stu-id="23b7f-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="23b7f-159">Výše uvedená konstrukce představuje kód generovaný C# kompilátorem ve verzi 5 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="23b7f-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="23b7f-160">Před verzí 5 měla proměnná `item` jiný obor:</span><span class="sxs-lookup"><span data-stu-id="23b7f-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="23b7f-161">Tato změna byla změněna, protože předchozí chování může vést k nejemnému a obtížnému Diagnostikování chyb týkajících se výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="23b7f-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="23b7f-162">Další informace o výrazech lambda naleznete v tématu [lambda Expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="23b7f-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="23b7f-163">Přesný kód generovaný kompilátorem je poněkud složitější a zpracovává situace, kde objekt vrácený `GetEnumerator()` implementuje rozhraní `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="23b7f-164">Úplné rozšíření generuje podobný kód jako tento:</span><span class="sxs-lookup"><span data-stu-id="23b7f-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="23b7f-165">Způsob, jakým je uvolněn enumerátor, závisí na charakteristikách typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="23b7f-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="23b7f-166">V obecném případě je klauzule `finally` rozšířena na:</span><span class="sxs-lookup"><span data-stu-id="23b7f-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="23b7f-167">Pokud je však typ `enumerator` zapečetěný typ a neexistuje žádný implicitní převod z typu `enumerator` na `IDisposable`, klauzule `finally` se rozšíří do prázdného bloku:</span><span class="sxs-lookup"><span data-stu-id="23b7f-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="23b7f-168">Pokud existuje implicitní převod z typu `enumerator` na `IDisposable` a `enumerator` je typ hodnoty, která není null, klauzule `finally` se rozšíří na:</span><span class="sxs-lookup"><span data-stu-id="23b7f-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="23b7f-169">Naštěstí, nemusíte si pamatovat všechny tyto podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="23b7f-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="23b7f-170">Příkaz `foreach` zpracuje všechny tyto drobné odlišnosti za vás.</span><span class="sxs-lookup"><span data-stu-id="23b7f-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="23b7f-171">Kompilátor vygeneruje správný kód pro některý z těchto konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="23b7f-171">The compiler will generate the correct code for any of these constructs.</span></span>
