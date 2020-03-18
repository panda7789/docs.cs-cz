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
# <a name="iterators"></a>Iterátory

Téměř každý program, který napíšete, bude mít nějakou potřebu iterate přes sbírku. Napíšete kód, který zkoumá každou položku v kolekci.

Budete také vytvořit iterátor metody, které jsou metody, které vytváří iterátor pro prvky této třídy. Ty mohou být použity pro:

+ Provedení akce pro každou položku v kolekci.
+ Výčet vlastní kolekce.
+ Rozšíření [LINQ](linq/index.md) nebo jiných knihoven.
+ Vytvoření datového kanálu, kde data efektivně proudí prostřednictvím metod iterátoru.

Jazyk C# poskytuje funkce pro oba tyto scénáře. Tento článek obsahuje přehled těchto funkcí.

Tento kurz má několik kroků. Po každém kroku můžete spustit aplikaci a zobrazit průběh. Můžete také [zobrazit nebo stáhnout dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterace s foreach

Výčet kolekce je jednoduchý: `foreach` Klíčové slovo vyjmenovává kolekci a jednou provede vložený příkaz pro každý prvek v kolekci:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

A to je vše. Chcete-li iterate přes veškerý obsah `foreach` kolekce, prohlášení je vše, co potřebujete. To `foreach` prohlášení ale není kouzelné. Spoléhá se na dvě obecná rozhraní definovaná v základní knihovně .NET za účelem `IEnumerable<T>` `IEnumerator<T>`generování kódu potřebného k iterovat kolekci: a . Tento mechanismus je podrobněji vysvětlen níže.

Obě tato rozhraní mají také neobecné `IEnumerable` protějšky: a `IEnumerator`. [Obecné](programming-guide/generics/index.md) verze jsou upřednostňovány pro moderní kód.

## <a name="enumeration-sources-with-iterator-methods"></a>Zdroje výčtu pomocí metod iterátoru

Další skvělá funkce jazyka C# umožňuje vytvářet metody, které vytvářejí zdroj pro výčet. Tyto metody se označují jako *metody iterátoru*. Metoda iterátoru definuje, jak generovat objekty v pořadí na požádání. Kontextová `yield return` klíčová slova slouží k definování metody iterátoru.

Tuto metodu můžete napsat k vytvoření posloupnosti celých čísel od 0 do 9:

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

Výše uvedený kód `yield return` ukazuje odlišné příkazy zvýraznit `yield return` skutečnost, že můžete použít více diskrétní příkazy v iterátor metody.
Můžete (a často dělat) použít jiné jazykové konstrukce pro zjednodušení kódu metody iterátoru. Níže uvedená definice metody vytváří přesně stejnou posloupnost čísel:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Nemusíš rozhodovat o jednom nebo druhém. Můžete mít tolik `yield return` příkazů, kolik je potřeba, aby vyhovovaly potřebám vaší metody:

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

To je základní syntaxe. Podívejme se na příklad reálného světa, kde byste napsali metodu iterátoru. Představte si, že jste na projektu IoT a senzory zařízení generují velmi velký proud dat. Chcete-li získat cit pro data, můžete napsat metodu, která vzorky každý n-tý datový prvek. Tato malá metoda iterátoru dělá trik:

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

Existuje jedno důležité omezení metod iterátoru: nemůžete mít `return` jak `yield return` příkaz, tak příkaz ve stejné metodě. Následující nebude kompilovat:

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

Toto omezení obvykle není problém. Máte na výběr buď `yield return` pomocí v rámci metody, nebo oddělení původní `return`metody do `yield return`více metod, některé pomocí a některé pomocí .

Můžete upravit poslední metodu mírně `yield return` použít všude:

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

Někdy je správnou odpovědí rozdělení metody iterátoru na dvě různé metody. Jeden, `return`který používá , `yield return`a druhý, který používá . Zvažte situaci, kdy můžete chtít vrátit prázdnou kolekci nebo prvních 5 lichých čísel na základě logického argumentu. Dalo by se napsat, že jako tyto dvě metody:

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

Podívejte se na výše uvedené metody. První používá standardní `return` příkaz vrátit buď prázdnou kolekci nebo iterátor vytvořený druhou metodou. Druhá metoda používá `yield return` příkaz k vytvoření požadované sekvence.

## <a name="deeper-dive-into-foreach"></a>Hlouběji ponořte se do`foreach`

Příkaz `foreach` rozbalí do standardní idiom, `IEnumerable<T>` `IEnumerator<T>` který používá a rozhraní iterát u všech prvků kolekce. Také minimalizuje chyby, které vývojáři dělají tím, že správně nespravují prostředky.

Kompilátor přeloží smyčku zobrazenou `foreach` v prvním příkladu na něco podobného této konstrukci:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Konstrukce výše představuje kód generovaný kompilátorem Jazyka C# od verze 5 a vyšší. Před verzí 5 `item` měla proměnná jiný rozsah:

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

To bylo změněno, protože dřívější chování může vést k jemné a těžko diagnostikovat chyby zahrnující lambda výrazy. Další informace o výrazech lambda naleznete v tématu [Lambda výrazy](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Přesný kód generovaný kompilátorem je poněkud složitější a zpracovává situace, kdy objekt vrácený implementuje `GetEnumerator()` `IDisposable` rozhraní. Úplné rozšíření generuje kód více takto:

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

Způsob, jakým je čítač zlikvidován, závisí `enumerator`na vlastnostech typu . V obecném případě `finally` se doložka rozšiřuje na:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

`enumerator` Pokud je však typ zapečetěného typu a neexistuje žádný `enumerator` implicitní převod z typu na `IDisposable`, `finally` klauzule se rozbalí na prázdný blok:

```csharp
finally
{
}
```

Pokud je implicitní převod z `enumerator` `IDisposable`typu `enumerator` na , a je non-null typ hodnoty, `finally` klauzule rozbalí na:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Naštěstí si nemusíte pamatovat všechny tyto detaily. Prohlášení `foreach` zpracovává všechny tyto nuance pro vás. Kompilátor vygeneruje správný kód pro všechny tyto konstrukce.
