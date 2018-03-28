---
title: Kolekce kurz – C# místní – elementy QuickStart
description: Výuka C# prozkoumáním kolekci seznamů v tomto kurzu.
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 88471c5fc60178c058f121ba5e5703999ad61030
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="c-quickstart-collections"></a>C# rychlý start: kolekce

Tento rychlý Start obsahuje úvod do jazyka C# a základní informace o <xref:System.Collections.Generic.List%601> třídy.

Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.

## <a name="a-basic-list-example"></a>Příklad základního seznamu

Vytvořte adresář s názvem **seznamu – rychlý Start**. Ujistěte, že aktuální adresář a spusťte `dotnet new console`.

> [!NOTE]
> Pokud jste právě dokončili [Začínáme s .NET za 10 minut](https://www.microsoft.com/net), můžete používat aplikace Moje aplikace, kterou jste právě vytvořili.

Otevřete **Program.cs** v oblíbeném editoru a nahraďte existující kód následující:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

Nahraďte `<name>` s vaším jménem. Uložit **Program.cs**. Typ `dotnet run` v okně konzoly vyzkoušejte si to.

Jste právě vytvořili seznam řetězců, přidat tři názvy do tohoto seznamu a vytisknout se názvy v velká písmena. Používáte koncepty, které jste se naučili v dřívější – elementy QuickStart můžete procházet seznam.

Kód zobrazení názvů využívá [řetězec interpolace](../language-reference/tokens/interpolated.md) funkce.  Když je před `string` s `$` znak, vložením kódu C# v deklaraci řetězec. Konkrétní řetězec nahradí hodnotu, kterou generuje tento kód C#. V tomto příkladu se nahradí `{name.ToUpper()}` s každý název převeden na velká písmena, protože jste volali metodu <xref:System.String.ToUpper%2A> metoda.

Zachovat umožňuje prohlížení.

## <a name="modify-list-contents"></a>Změna seznamu obsahu

Kolekce, které jste vytvořili, používá <xref:System.Collections.Generic.List%601> typu. Tento typ ukládá pořadí elementů. Můžete zadat typ elementů mezi lomené závorky.

Jeden důležitým aspektem tohoto <xref:System.Collections.Generic.List%601> typ je ho můžete zvětšit nebo zmenšit, umožňuje přidat nebo odebrat elementy. Přidejte tento kód před uzavírací `}` v `Main` metoda:

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Přidali jste dva další názvy na konec seznamu. Můžete rovněž jsme odstranili jeden také. Uložte soubor a typ `dotnet run` vyzkoušejte si to.

<xref:System.Collections.Generic.List%601> Umožňuje odkazovat na jednotlivé položky podle **index** také. Umístěte index mezi `[` a `]` tokeny následující název seznamu. C# používá 0 pro první index. Přidejte tento kód přímo pod kód, který jste právě přidali a zkuste to:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nelze získat přístup k indexu přesahuje za konec seznamu. Mějte na paměti, že indexy, které začínají hodnotou 0, takže největší platný index představuje jedno menší než počet položek v seznamu. Můžete zkontrolovat, jak dlouho je pomocí seznamu <xref:System.Collections.Generic.List%601.Count%2A> vlastnost. Na konci metodu Main, přidejte následující kód:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Uložte soubor a typ `dotnet run` znovu a zobrazte si výsledky.

## <a name="search-and-sort-lists"></a>Seznamy hledání a řazení.

Naše ukázky použít seznamy poměrně malý, ale aplikace může často vytvořit seznamy s mnoha další prvky, které se někdy číslování v tisíců. Elementy v těchto kolekcích větší najdete budete muset pro různé položky v seznamu Hledat. <xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky. Tento kód vložte do dolní části vaší `Main` metoda:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Také lze seřadit položky v seznamu. <xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v jejich normálním pořadí (podle abecedy. v případě řetězce). Tento kód vložte do spodní části našich `Main` metoda:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Uložte soubor a typ `dotnet run` pokusit tento nejnovější verzi.

Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě. Který usnadňuje začít pracovat s novou příklad. Přejmenujte vaše `Main` metodu `WorkingWithStrings` a zápis nový `Main` metoda, která volá `WorkingWithStrings`. Po dokončení, váš kód by měl vypadat například takto:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>Seznam dalších typů

Jste dosud používali `string` typu v seznamech dosavadní práce. Provedeme <xref:System.Collections.Generic.List%601> pomocí jiného typu. Vytvořme sady čísel.

Přidejte následující k dolnímu okraji nové `Main` metoda:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Zda vytvoří seznam celých čísel a nastaví první dva celých čísel na hodnotu 1. Jedná se o první dvě hodnoty z *Fibonacciho pořadí*, pořadí čísel. Každé další číslo Fibonacciho nachází provedením součet předchozích dvou čísel. Přidejte tento kód:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Uložte soubor a typ `dotnet run` a zobrazte si výsledky.

> [!TIP]
> Soustředit se na právě v této části, můžete Zakomentovat kód, který volá `WorkingWithStrings();`. Vloží dva pouze `/` znaky před volání, jako to: `// WorkingWithStrings();`.

## <a name="challenge"></a>výzvy

Pokud můžete umístit společně najdete některé koncepty z tohoto a starší lekce. Rozbalte položku na co jste vytvořili, pokud se Fibonacciho čísla. Zkuste napsat kód pro vytvoření prvních 20 čísel v pořadí. (Jako nápovědu, je číslo 20 Fibonacciho 6765.)

## <a name="complete-challenge"></a>Dokončení výzvy

Zobrazí se příklad řešení s nástrojem [prohlížení dokončení ukázkový kód na Githubu](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)

S každou iteraci smyčky přenášíte posledních dvou celých čísel v seznamu je sčítání a přidáním této hodnoty do seznamu. Smyčky se opakuje, dokud nepřidáte 20 položky do seznamu.

Blahopřejeme, jste dokončili rychlé spuštění seznamu. Můžete pokračovat [Úvod do třídy](introduction-to-classes.md) rychlé spuštění ve vašem vývojovém prostředí.

Další informace o práci s `List` zadejte [.NET průvodce](../../standard/index.md) téma na [kolekce](../../standard/collections/index.md). Budete také informace o mnoho dalších typů kolekce.