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
# <a name="iterators"></a>Iterátory

Skoro každý program, který napíšete, bude nutné iterovat v kolekci. Budete psát kód, který prověřuje každou položku v kolekci.

Také vytvoříte iterátory, které jsou metody, které vytvoří iterátor pro prvky této třídy. Můžete je použít pro:

+ Provedení akce u každé položky v kolekci.
+ Vytváří se výčet vlastní kolekce.
+ Rozšíření [LINQ](linq/index.md) nebo jiné knihovny.
+ Vytvoření datového kanálu, ve kterém data efektivně proudí prostřednictvím metod iterátoru.

C# Jazyk poskytuje funkce pro oba tyto scénáře. Tento článek obsahuje přehled těchto funkcí.

V tomto kurzu se používá několik kroků. Po každém kroku můžete spustit aplikaci a zobrazit průběh. Můžete také [Zobrazit nebo stáhnout dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterace pomocí příkazu foreach

Výčet kolekce je jednoduchý: klíčové slovo `foreach` vytvoří výčet kolekce a jednou spustí vložený příkaz pro každý prvek v kolekci:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To je všechno, co je to vše. Chcete-li iterovat všechny obsahy kolekce, příkaz `foreach` je vše, co potřebujete. Příkaz `foreach` není Magic, i když. Spoléhá se na dvě Obecná rozhraní definovaná v knihovně .NET Core, aby bylo možné vygenerovat kód potřebný k iteraci kolekce: `IEnumerable<T>` a `IEnumerator<T>`. Tento mechanismus je podrobněji vysvětlen níže.

Obě tato rozhraní mají také neobecné protějšky: `IEnumerable` a `IEnumerator`. [Obecné](programming-guide/generics/index.md) verze jsou upřednostňovány pro moderní kód.

## <a name="enumeration-sources-with-iterator-methods"></a>Výčtové zdroje s metodami iterátoru

Další skvělou funkcí C# jazyka je umožňuje vytvořit metody, které vytvoří zdroj pro výčet. Tyto metody se označují jako *iterátory*. Metoda iterátoru definuje způsob generování objektů v pořadí podle požadavku. K definování metody iterátoru slouží kontextové klíčové slovo `yield return`.

Tuto metodu můžete zapsat pro vytvoření posloupnosti celých čísel od 0 do 9:

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

Výše uvedený kód ukazuje odlišné příkazy `yield return` pro zvýraznění faktu, že můžete použít více diskrétních `yield return`ch příkazů v metodě iterátoru.
Můžete (a často) použít jiné jazykové konstrukce pro zjednodušení kódu metody iterátoru. Následující definice metody vytváří přesně stejnou sekvenci čísel:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Nemusíte se rozhodnout ani jedno z nich. Pro splnění požadavků vaší metody můžete mít tolik `yield return` příkazů:

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

To je základní syntaxe. Pojďme se na příklad reálného světa, kde byste napsali metodu iterátoru. Představte si, že jste v projektu IoT a senzory zařízení generují velmi velký proud dat. Chcete-li pro data získat dojem, můžete napsat metodu, která bude odebírat každý n-tý datový prvek. Tato metoda malého iterátoru dělá štych:

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

Existují jedna důležitá omezení pro metody iterátoru: ve stejné metodě nemůžete mít příkaz `return` a `yield return` příkaz. Následující kroky nebudou zkompilovány:

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

Toto omezení se obvykle nejedná o problém. Máte možnost volby buď pomocí `yield return` v rámci této metody, nebo oddělením původní metody do více metod, některých pomocí `return` a některých pomocí `yield return`.

Poslední metodu můžete upravit mírně a použít `yield return` všude:

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

V některých případech je správná odpověď rozdělením metody iterátoru do dvou různých metod. Ten používá `return` a druhý, který používá `yield return`. Vezměte v úvahu situaci, kdy byste mohli chtít vrátit prázdnou kolekci, nebo prvních 5 lichých čísel na základě argumentu Boolean. Můžete napsat tyto dvě metody:

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

Podívejte se na výše uvedené metody. První používá příkaz standardní `return` pro vrácení prázdné kolekce nebo iterátoru vytvořeného druhou metodou. Druhá metoda používá příkaz `yield return` k vytvoření požadované sekvence.

## <a name="deeper-dive-into-foreach"></a>Hlubší podrobně do `foreach`

Příkaz `foreach` se rozšíří na standardní idiom, který používá rozhraní `IEnumerable<T>` a `IEnumerator<T>` k iterování napříč všemi prvky kolekce. Také minimalizuje chyby, které vývojáři vytvářejí při nesprávné správě prostředků.

Kompilátor transformuje `foreach` cyklus zobrazený v prvním příkladu na něco podobného této konstrukci:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Výše uvedená konstrukce představuje kód generovaný C# kompilátorem ve verzi 5 a vyšší. Před verzí 5 měla proměnná `item` jiný obor:

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

Tato změna byla změněna, protože předchozí chování může vést k nejemnému a obtížnému Diagnostikování chyb týkajících se výrazů lambda. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Přesný kód generovaný kompilátorem je poněkud složitější a zpracovává situace, kde objekt vrácený `GetEnumerator()` implementuje rozhraní `IDisposable`. Úplné rozšíření generuje podobný kód jako tento:

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

Způsob, jakým je uvolněn enumerátor, závisí na charakteristikách typu `enumerator`. V obecném případě je klauzule `finally` rozšířena na:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Pokud je však typ `enumerator` zapečetěný typ a neexistuje žádný implicitní převod z typu `enumerator` na `IDisposable`, klauzule `finally` se rozšíří do prázdného bloku:

```csharp
finally
{
}
```

Pokud existuje implicitní převod z typu `enumerator` na `IDisposable` a `enumerator` je typ hodnoty, která není null, klauzule `finally` se rozšíří na:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Naštěstí, nemusíte si pamatovat všechny tyto podrobnosti. Příkaz `foreach` zpracuje všechny tyto drobné odlišnosti za vás. Kompilátor vygeneruje správný kód pro některý z těchto konstrukcí.
