---
title: Práce s kolekcemi – Úvod C# do kurzu
description: Seznamte se s C# tím, že v tomto kurzu prozkoumáte kolekci seznamů.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 160e34ddb529a8515a08d6aab838ba107936c616
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587252"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Naučte se spravovat kolekce dat pomocí obecného typu seznamu.

Tento úvodní kurz poskytuje Úvod k C# jazyku a základům <xref:System.Collections.Generic.List%601> třídy.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Téma rozhraní .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux. Rychlý přehled příkazů, které budete používat, se [seznámí s vývojářskými nástroji](local-environment.md)a odkazy na další podrobnosti.

## <a name="a-basic-list-example"></a>Příklad základního seznamu

Vytvoří adresář s názvem **list-tutorial**. Zajistěte, aby byl aktuální `dotnet new console`adresář a běžel.

Ve svém oblíbeném editoru otevřete **program.cs** a nahraďte stávající kód následujícím kódem:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

Nahraďte `<name>` vaším jménem. Uložte **program.cs**. Zadejte `dotnet run` okno konzoly a zkuste to.

Právě jste vytvořili seznam řetězců, Přidali jste do tohoto seznamu tři názvy a vytiskli názvy všech velkých písmen. Pomocí konceptů, které jste se naučili v předchozích kurzech, Projděte seznam.

Kód pro zobrazení názvů využívá funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) .  Pokud předcházíte `string` `$` znak, můžete vložit C# kód do deklarace řetězce. Skutečný řetězec nahradí tento C# kód hodnotou, kterou generuje. V tomto příkladu nahrazuje `{name.ToUpper()}` název s každým názvem převedenými na velká písmena, protože jste <xref:System.String.ToUpper%2A> volali metodu.

Pojďme si to prozkoumat.

## <a name="modify-list-contents"></a>Upravit obsah seznamu

Kolekce, kterou jste vytvořili, <xref:System.Collections.Generic.List%601> používá typ. Tento typ ukládá sekvence prvků. Zadejte typ prvků mezi lomenými závorkami.

Jedním z důležitých aspektů <xref:System.Collections.Generic.List%601> tohoto typu je, že může být zvětšen nebo zmenšen, což umožňuje přidat nebo odebrat prvky. Přidejte tento kód před uzavírací `}` `Main` v metodě:

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

Přidali jste dva další názvy na konec seznamu. Také jste odebrali i jednu z nich. Uložte soubor a zadejte `dotnet run` ho a zkuste to znovu.

Umožňuje také odkazovat na jednotlivé položky podle **indexu.** <xref:System.Collections.Generic.List%601> Index mezi `[` a `]` tokeny umístěte za název seznamu. C#pro první index používá hodnotu 0. Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte ho:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nemůžete získat přístup k indexu za konec seznamu. Mějte na paměti, že indexy začínají na 0, takže největší platný index je jeden menší než počet položek v seznamu. Můžete zjistit, jak dlouho seznam používá <xref:System.Collections.Generic.List%601.Count%2A> vlastnost. Na konec metody Main přidejte následující kód:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Uložte soubor a zadejte `dotnet run` znovu, abyste viděli výsledky.

## <a name="search-and-sort-lists"></a>Hledání a řazení seznamů

Naše ukázky používají relativně malé seznamy, ale vaše aplikace často můžou vytvářet seznamy s mnoha více prvky, někdy se číslování v tisících. Chcete-li najít prvky v těchto větších kolekcích, je nutné hledat v seznamu různé položky. <xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky. Přidejte tento kód do dolní části vaší `Main` metody:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Položky v seznamu lze seřadit také. <xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v normálním pořadí (abecedně v případě řetězců). Přidejte tento kód do dolní části naší `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Uložte soubor a zadejte `dotnet run` , abyste si vyzkoušeli tuto nejnovější verzi.

Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `WorkingWithStrings` `Main` `WorkingWithStrings`metodu na a napište novou metodu, která volá. `Main` Až budete hotovi, váš kód by měl vypadat takto:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

## <a name="lists-of-other-types"></a>Seznamy dalších typů

V seznamu zatím jste používali `string` typ v seznamech. <xref:System.Collections.Generic.List%601> Pojďme použít jiný typ. Pojďme sestavit sadu čísel.

Do dolní části nové `Main` metody přidejte následující:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Vytvoří seznam celých čísel a nastaví první dvě celá čísla na hodnotu 1. Jedná se o první dvě hodnoty *Fibonacci sekvence*, sekvence čísel. Každé další Fibonacci číslo se zjistí tak, že se vybere součet předchozích dvou čísel. Přidejte tento kód:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Uložte soubor a zadejte `dotnet run` , aby se zobrazily výsledky.

> [!TIP]
> Chcete-li se soustředit jenom na tuto část, můžete komentovat kód, který volá `WorkingWithStrings();`. Stačí umístit dva `/` znaky před volání jako toto:. `// WorkingWithStrings();`

## <a name="challenge"></a>Výzev

Podívejte se, jestli můžete některé z konceptů spojit z tohoto a předchozích lekcí. Rozhlaste se podle toho, co jste zatím vytvořili s Fibonacci čísly. Zkuste napsat kód, který vygeneruje prvních 20 čísel v sekvenci. (Jako pomocný parametr se jedná o 20 Fibonacci číslo 6765.)

## <a name="complete-challenge"></a>Dokončení výzvy

Ukázkové řešení si můžete prohlédnout po zobrazení [dokončeného ukázkového kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

V každé iteraci smyčky přebíráte poslední dvě celá čísla v seznamu, sečtete je a přidáte tuto hodnotu do seznamu. Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.

Blahopřejeme, dokončili jste kurz k seznamům. V kurzu [Úvod ke třídám](introduction-to-classes.md) můžete pokračovat ve svém vlastním vývojovém prostředí.

Další informace o práci s `List` typem najdete v tématu [příručka .NET](../../../standard/index.md) o [kolekcích](../../../standard/collections/index.md). Naučíte se také mnoho dalších typů kolekcí.
