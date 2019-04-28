---
title: Iterátory
description: Zjistěte, jak použít integrovaný C# iterátory a jak vytvořit vlastní vlastní iterátory.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: e816af698a39a4b44aefa92017efdbc9e3c8cc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672039"
---
# <a name="iterators"></a>Iterátory

Téměř každá program, který napíšete bude mít některé nutnost opakování v kolekci. Budete psát kód, který ověřuje, zda každá položka v kolekci.

Také vytvoříte metody iterátoru, které jsou metody, které vytvoří iterátor pro elementy třídy. Ty je možné použít pro:

+ Provést akci pro každou položku v kolekci.
+ Vytváření výčtu vlastní kolekce.
+ Rozšíření [LINQ](linq/index.md) nebo jiných knihoven.
+ Vytvoření datového kanálu, kde data protékají efektivně iterátory.

C# Jazyk poskytuje funkce pro oba tyto scénáře. Tento článek obsahuje přehled těchto funkcí.

V tomto kurzu má několik kroků. Po provedení každého kroku můžete spustit aplikaci a sledovat průběh. Můžete také [zobrazení nebo stažení je hotová ukázka](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterace pomocí příkazu foreach

Vytvoření výčtu kolekce je jednoduchý: `foreach` – Klíčové slovo vytvoří výčet kolekce, provádění vloženým příkazem jednou pro každý prvek v kolekci:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To je všechno je to. K iteraci přes veškerý obsah kolekce `foreach` příkaz je všechno, co potřebujete. `foreach` Příkazu není magic, i když. Spoléhá na dvě obecné rozhraní definované v knihovně .NET core k vygenerování kódu potřebného k iteraci v kolekci: `IEnumerable<T>` a `IEnumerator<T>`. Tento mechanismus je podrobněji vysvětleny níže.

Obě tato rozhraní mají také jejich obecné protějšky: `IEnumerable` a `IEnumerator`. [Obecný](programming-guide/generics/index.md) verze jsou upřednostněny moderní kód.

## <a name="enumeration-sources-with-iterator-methods"></a>Výčet zdrojů s iterátory

Další skvělou funkcí služby C# jazyka vám umožní sestavovat metody, které vytvoří zdroj pro výčet. Tyto jsou označovány jako *iterátory*. Metodu iterátoru definuje, jak generovat objekty v posloupnosti na požádání. Můžete použít `yield return` kontextová klíčová slova, chcete-li definovat metodu iterátoru.

Můžete napsat tuto metodu za účelem vytvoření sekvence celých čísel od 0 do 9:

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

Výše uvedený kód ukazuje různé `yield return` příkazy, abyste měli na očích faktů, které můžete použít více samostatných `yield return` příkazy v metodě iterátoru.
Můžete (a často tomu) pomocí jiných objektů, které jazyk můžete zjednodušit kód metodu iterátoru. Následující definici metody vytvoří přesně stejnou sekvenci čísel:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Není nutné se rozhodnout, jeden z nich. Můžete mít kolik `yield return` příkazy podle potřeby pro potřeby metodu:

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

To je základní syntaxe. Pojďme se na příklad reálného světa, kde by zapisovat metodu iterátoru. Představte si jste na IoT projektu a generovat velmi velké datový proud s daty senzorů zařízení. Chcete-li získat představu pro data, můžete například napsat metodu, která ukázky každý element n-tý data. Tato metoda malé iterátoru provede trik, jak zajistit:

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

Existuje jedna důležitá omezení iterátory: nemůže mít oba `return` příkaz a `yield return` příkaz v stejným způsobem. Nebude kompilovat následující:

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

Toto omezení se obvykle problém. Máte možnost buď pomocí `yield return` v rámci metody nebo oddělení původní metody do více metod, pomocí některé `return`a některé pomocí `yield return`.

Můžete upravit poslední metody mírně pro použití `yield return` všude:

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

V některých případech je správná odpověď metody iterátoru rozdělit na dvě různé metody. Ten, který používá `return`a druhý, který používá `yield return`. Představte si situaci, kde můžete chtít vrátit prázdnou kolekci nebo prvních 5 lichých čísel podle logický argument. Který může zapsat jako tyto dvě metody:

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

Podívejte se na metod uvedených výše. První způsob využívá standardní `return` příkaz vrátit prázdnou kolekci nebo vytvořené pomocí druhé metody iterátoru. Druhá metoda používá `yield return` příkaz pro vytvoření požadovaného pořadí.

## <a name="deeper-dive-into-foreach"></a>Prozkoumejte podrobněji `foreach`

`foreach` Příkaz rozšíří na standardní idiom, který používá `IEnumerable<T>` a `IEnumerator<T>` rozhraní k iteraci v rámci všech prvků kolekce. Také minimalizuje chyb, které vývojář podá tím, že není správně spravuje prostředky.

Kompilátor překládá `foreach` smyčky do něco podobného pro tento konstruktor je znázorněno v prvním příkladu:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Konstrukce výše představuje kód vygenerovaný C# kompilátoru od verze 5 a vyšší. Starší než verze 5 `item` proměnná měla jiného oboru:

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

To se změnit, protože starší chování může vést k nejnenápadnější a těžko Diagnostikujte chyby týkající se výrazů lambda. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Přesný kód generovaný kompilátorem je o něco složitější a zpracovává situacích, kde objekt vrácený `GetEnumerator()` implementuje `IDisposable` rozhraní. Plnou expanzí generuje kód další takto:

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

Způsob, ve kterém je enumerátor odstraněny závisí na vlastnosti typu `enumerator`. V tomto obecném případě `finally` klauzule rozšíří na:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Nicméně pokud typu `enumerator` je zapečetěný typ a neexistuje žádný implicitní převod z typu `enumerator` k `IDisposable`, `finally` klauzule rozšíří na prázdný blok:

```csharp
finally
{
}
```

Pokud je implicitní převod z typu `enumerator` k `IDisposable`, a `enumerator` je typ hodnoty Null, `finally` klauzule rozšíří na:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Naštěstí nemusíte pamatovat si tyto podrobnosti. `foreach` Příkaz zpracuje za vás tyto drobné rozdíly. Bude kompilátor generovat správný kód pro některý z těchto konstruktorů.
