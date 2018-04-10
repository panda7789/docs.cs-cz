---
title: Iterátory
description: Zjistěte, jak používat integrované iterátory C# a jak vytvořit vlastní vlastní iterator metody.
keywords: Rozhraní .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 403a286e9b1168b9e913b3cb2764e7fe262017d4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="iterators"></a>Iterátory

Téměř všechny programy, které můžete psát bude mít některé potřeba iterace v kolekci. Budete psát kód, který hledá každá položka v kolekci. 

Pokud vytvoříte iterator metody, které jsou metody, které vytváří iterace pro elementy této třídy. Ty lze použít pro:

+ Provedení akce na každou položku v kolekci.
+ Vytváření výčtu vlastní kolekce.
+ Rozšíření [LINQ](linq/index.md) nebo jiné knihovny.
+ Vytváření kde data proudí efektivně prostřednictvím metody iterator datovém kanálu.

Jazyk C# poskytuje funkce pro oba tyto scénáře. Tento článek obsahuje přehled těchto funkcí.

V tomto kurzu má několik kroků. Po dokončení každého kroku můžete aplikaci spustit a sledovat průběh. Můžete také [zobrazení nebo stažení je hotová ukázka](https://github.com/dotnet/samples/blob/master/csharp/iterators) pro toto téma. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterace pomocí příkazu foreach

Vytváření výčtu kolekce je jednoduchý: `foreach` – klíčové slovo zobrazí kolekci provádění embedded příkazu jednou pro každý prvek v kolekci:
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To je všechno je k němu. Iterace nad veškerý obsah do kolekce `foreach` příkaz je vše, co potřebujete. `foreach` Příkaz není magic, přestože. Přitom spoléhá na dvě obecné rozhraní definované v základní knihovny .NET, pokud chcete generovat kód nezbytné k iteraci v kolekci: `IEnumerable<T>` a `IEnumerator<T>`. Tento mechanismus je vysvětlené podrobněji níže.

Mají obě tato rozhraní taky neobecné protějšky: `IEnumerable` a `IEnumerator`. [Obecné](programming-guide/generics/index.md) verze jsou upřednostněny moderní kódu.

## <a name="enumeration-sources-with-iterator-methods"></a>Výčet zdrojů pomocí metod iterátorů

Další skvělé funkcí jazyka C# umožňuje vytvoření metody, které vytvořte zdroj pro výčet. Tyto jsou označovány jako *iterator metody*. Metodu iterator definuje, jak vygenerovat objekty v pořadí vyžádání. Můžete použít `yield return` kontextová klíčová slova k definování metodu iterator. 

Můžete napsat tuto metodu za účelem vytvoření posloupnost celých čísel od 0 do 9:

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

Výše uvedený kód ukazuje odlišné `yield return` příkazy, abyste měli na očích faktů, které můžete použít více diskrétní `yield return` příkazy v metodu iterator.
Můžete (a často udělat) pomocí jiných jazykové konstrukty můžete zjednodušit kód metody iterator. Následující metoda definice poskytne přesně stejnou sekvenci čísla:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Nemáte k rozhodování o jeden z nich. Může mít jako mnoho `yield return` příkazy podle potřeby, aby vyhovovaly vaší metody:

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

To je základní syntaxe. Pojďme se podívat v reálném světě příkladu, kde by zápis metody iterator. Představte si jste v projektu IoT a snímače zařízení generovat velmi velký datový proud. Podívat, pro data, může napíše metoda, která ukázky každých n-tou datový prvek. Tato metoda malé iterator nemá efektu:

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

Neexistuje jeden důležité omezení iterator metody: nemůže mít obě `return` příkaz a `yield return` příkaz v stejnou metodu. Kompilace nebude:

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

Toto omezení obvykle není problém. Máte možnost volby buď pomocí `yield return` v rámci metodu nebo metodu původní rozdělit do několika metod, některé pomocí `return`a některé pomocí `yield return`.

Můžete upravit jako poslední metodu mírně `yield return` everywhere:

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
 
V některých případech je pravé odpovědi metodu iterator rozdělit na dvě různé metody. Ten, který používá `return`a druhou, která používá `yield return`. Představte si situaci, kde můžete chtít vrátit prázdnou kolekci nebo prvních 5 liché čísla podle argumentem logická hodnota. Který může zapsat jako tyto dvě metody:

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
 
Podívejte se na výše uvedené metody. První způsob využívá standardní `return` příkaz, který má vrátit prázdnou kolekci, nebo iterator vytvořené druhé metody. Druhý způsob využívá `yield return` příkaz k vytvoření požadované pořadí.

## <a name="deeper-dive-into-foreach"></a>Podrobnější prohlídku do `foreach`

`foreach` Příkaz rozšíří na standardní stylu, které používá `IEnumerable<T>` a `IEnumerator<T>` rozhraní k iteraci v rámci všechny elementy z kolekce. Minimalizuje také chyb, které vývojáři, aby byly správně řízení zdrojů. 

Kompilátor převádí `foreach` smyčky uvedené v prvním příkladu do něco podobného jako tento konstrukce:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Konstrukce výše představuje kód vygenerovaný kompilátor C# od verze 5 a vyšší. Starší než verze 5 `item` proměnná měl jiný rozsah:

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

To se změnit, protože starší chování může vést k jemně a těžko diagnostikovat chyby zahrnující výrazy lambda. Projděte část o [výrazy lambda](lambda-expressions.md) Další informace. 

Přesný kód vygenerovaný kompilátor je trochu složitější a zpracovává situacích, kde se objekt vrácený `GetEnumerator()` implementuje `IDisposable` rozhraní. Plnou expanzí generuje kód další takto:

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

Způsob, ve kterém je odstraněn enumerátor závisí na vlastnosti typu `enumerator`. V případě Obecné `finally` klauzule zasahuje do:

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

Ale pokud typ `enumerator` je typu zapečetěné a neexistuje žádný implicitní převod z typu `enumerator` k `IDisposable`, `finally` klauzule zasahuje do bloku prázdný:
```csharp
finally 
{
} 
```

Pokud je implicitní převod z typu `enumerator` k `IDisposable`, a `enumerator` je typ hodnot neumožňující hodnotu Null, `finally` klauzule zasahuje do:

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

Naštěstí nemusíte pamatovat si tyto podrobnosti. `foreach` Příkaz zpracovává všechny tyto drobné odlišnosti za vás. Kompilátor vygeneruje správný kód pro některý z těchto konstrukce. 


