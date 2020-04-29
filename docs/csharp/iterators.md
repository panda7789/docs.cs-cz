---
title: Iterátory
description: Naučte se používat integrované iterátory C# a vytvářet vlastní metody iterátoru.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: efa755c2243c18fb51b653abccb2bfc702bbc055
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507374"
---
# <a name="iterators"></a>Iterátory

Skoro každý program, který napíšete, bude nutné iterovat v kolekci. Budete psát kód, který prověřuje každou položku v kolekci.

Také vytvoříte iterátor metody, které jsou metody, které vytvoří iterátor (což je objekt, který projde kontejner, zejména seznamy) pro prvky této třídy. Můžete je použít pro:

+ Provedení akce u každé položky v kolekci.
+ Vytváří se výčet vlastní kolekce.
+ Rozšíření [LINQ](linq/index.md) nebo jiné knihovny.
+ Vytvoření datového kanálu, ve kterém data efektivně proudí prostřednictvím metod iterátoru.

Jazyk C# poskytuje funkce pro oba tyto scénáře. Tento článek obsahuje přehled těchto funkcí.

V tomto kurzu se používá několik kroků. Po každém kroku můžete spustit aplikaci a zobrazit průběh. Můžete také [Zobrazit nebo stáhnout dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterace pomocí příkazu foreach

Vytváření výčtu kolekce je jednoduché: `foreach` klíčové slovo vypíše kolekci a provede vložený příkaz jednou pro každý prvek v kolekci:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

A to je vše. Chcete-li iterovat všechny obsahy kolekce, je `foreach` příkaz vše, co potřebujete. `foreach` Příkaz není Magic, i když. Spoléhá se na dvě Obecná rozhraní definovaná v knihovně .NET Core, aby bylo možné vygenerovat kód potřebný k iteraci kolekce: `IEnumerable<T>` a `IEnumerator<T>`. Tento mechanismus je podrobněji vysvětlen níže.

Obě tato rozhraní mají také neobecné protějšky: `IEnumerable` a. `IEnumerator` [Obecné](programming-guide/generics/index.md) verze jsou upřednostňovány pro moderní kód.

## <a name="enumeration-sources-with-iterator-methods"></a>Výčtové zdroje s metodami iterátoru

Další skvělé funkce jazyka C# vám umožní vytvořit metody, které vytvoří zdroj pro výčet. Tyto metody se označují jako *iterátory*. Metoda iterátoru definuje způsob generování objektů v pořadí podle požadavku. Použijte `yield return` kontextová klíčová slova k definování metody iterátoru.

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

Výše uvedený kód ukazuje různé `yield return` příkazy k zdůraznění faktu, že můžete použít více `yield return` diskrétních příkazů v metodě iterátoru.
Můžete (a často) použít jiné jazykové konstrukce pro zjednodušení kódu metody iterátoru. Následující definice metody vytváří přesně stejnou sekvenci čísel:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Nemusíte se rozhodnout ani jedno z nich. K splnění potřeb vaší metody `yield return` můžete mít tolik příkazů, kolik je potřeba:

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

Existují jedna důležitá omezení pro metody iterátoru: ve stejné metodě nemůžete mít `return` příkaz `yield return` a příkaz. Následující kroky nebudou zkompilovány:

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

Toto omezení se obvykle nejedná o problém. Můžete zvolit buď pomocí `yield return` celé metody, nebo oddělit původní metodu do více metod, některé pomocí `return`a některé z nich. `yield return`

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

V některých případech je správná odpověď rozdělením metody iterátoru do dvou různých metod. Ten, který `return`používá, a druhý, který `yield return`používá. Vezměte v úvahu situaci, kdy byste mohli chtít vrátit prázdnou kolekci, nebo prvních 5 lichých čísel na základě argumentu Boolean. Můžete napsat tyto dvě metody:

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

Podívejte se na výše uvedené metody. První používá příkaz standardní `return` k vrácení prázdné kolekce nebo iterátoru vytvořeného druhou metodou. Druhá metoda používá `yield return` příkaz k vytvoření požadované sekvence.

## <a name="deeper-dive-into-foreach"></a>Hlubší podrobně`foreach`

Příkaz `foreach` se rozšíří na standardní idiom, který používá rozhraní `IEnumerable<T>` a `IEnumerator<T>` k iteraci napříč všemi prvky kolekce. Také minimalizuje chyby, které vývojáři vytvářejí při nesprávné správě prostředků.

Kompilátor transformuje `foreach` smyčku zobrazenou v prvním příkladu na něco podobného této konstrukci:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Výše uvedená konstrukce představuje kód generovaný kompilátorem jazyka C# od verze 5 a vyšší. Před verzí 5 byla proměnná v `item` jiném oboru:

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

Přesný kód generovaný kompilátorem je poněkud složitější a zpracovává situace, kde objekt vrácený `GetEnumerator()` implementací `IDisposable` rozhraní. Úplné rozšíření generuje podobný kód jako tento:

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

Způsob, jakým je uvolněn enumerátor, závisí na charakteristikách typu `enumerator`. V obecném případě je `finally` klauzule rozšířena na:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Nicméně `enumerator` Pokud typ je zapečetěný typ a neexistuje žádný implicitní převod z `enumerator` typu na `IDisposable`, `finally` klauzule se rozšíří do prázdného bloku:

```csharp
finally
{
}
```

Pokud existuje implicitní převod z `enumerator` typu na `IDisposable`, a `enumerator` je typ hodnoty, která není null, `finally` klauzule se rozšíří na:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Naštěstí, nemusíte si pamatovat všechny tyto podrobnosti. `foreach` Příkaz zpracuje všechny tyto drobné odlišnosti za vás. Kompilátor vygeneruje správný kód pro některý z těchto konstrukcí.
