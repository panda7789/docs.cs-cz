---
title: Kurz práce s kolekcemi – Úvod do jazyka C#
description: Naučte se v jazyce C# prozkoumat shromažďování seznamů v tomto kurzu.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: c99f5582702120db238de1206de42d964837cdbd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396897"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Naučte se spravovat kolekce dat pomocí obecného typu seznamu.

Tento úvodní kurz poskytuje Úvod do jazyka C# a základy <xref:System.Collections.Generic.List%601> třídy.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, se [seznámí s vývojářskými nástroji](local-environment.md)a odkazy na další podrobnosti.

## <a name="a-basic-list-example"></a>Příklad základního seznamu

Vytvoří adresář s názvem *list-tutorial*. Zajistěte, aby byl aktuální adresář a běžel `dotnet new console` .

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte stávající kód následujícím kódem:

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

Nahraďte `<name>` vaším jménem. Soubor *Program.cs* uložte. Zadejte `dotnet run` okno konzoly a zkuste to.

Vytvořili jste seznam řetězců, Přidali jste do tohoto seznamu tři názvy a vytiskli jste názvy všech velkých písmen. Pomocí konceptů, které jste se naučili v předchozích kurzech, Projděte seznam.

Kód pro zobrazení názvů využívá funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) .  Pokud předcházíte `string` `$` znak, můžete vložit kód jazyka C# do deklarace řetězce. Skutečný řetězec nahradí kód v jazyce C# hodnotou, kterou generuje. V tomto příkladu nahrazuje `{name.ToUpper()}` název s každým názvem převedenými na velká písmena, protože jste volali <xref:System.String.ToUpper%2A> metodu.

Pojďme si to prozkoumat.

## <a name="modify-list-contents"></a>Upravit obsah seznamu

Kolekce, kterou jste vytvořili, používá <xref:System.Collections.Generic.List%601> typ. Tento typ ukládá sekvence prvků. Zadejte typ prvků mezi lomenými závorkami.

Jedním z důležitých aspektů tohoto <xref:System.Collections.Generic.List%601> typu je, že může být zvětšen nebo zmenšen, což umožňuje přidat nebo odebrat prvky. Přidejte tento kód před uzavírací `}` v `Main` metodě:

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

Přidali jste dva další názvy na konec seznamu. Také jste odebrali i jednu z nich. Uložte soubor a zadejte ho a `dotnet run` zkuste to znovu.

<xref:System.Collections.Generic.List%601>Umožňuje také odkazovat na jednotlivé položky podle **indexu** . Index mezi `[` a `]` tokeny umístěte za název seznamu. Jazyk C# používá pro první index hodnotu 0. Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte ho:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nemůžete získat přístup k indexu za konec seznamu. Mějte na paměti, že indexy začínají na 0, takže největší platný index je jeden menší než počet položek v seznamu. Můžete zjistit, jak dlouho seznam používá <xref:System.Collections.Generic.List%601.Count%2A> vlastnost. Na konec metody Main přidejte následující kód:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Uložte soubor a zadejte znovu, `dotnet run` abyste viděli výsledky.

## <a name="search-and-sort-lists"></a>Hledání a řazení seznamů

Naše ukázky používají relativně malé seznamy, ale vaše aplikace často můžou vytvářet seznamy s mnoha více prvky, někdy se číslování v tisících. Chcete-li najít prvky v těchto větších kolekcích, je nutné hledat v seznamu různé položky. <xref:System.Collections.Generic.List%601.IndexOf%2A>Metoda vyhledá položku a vrátí index položky. Pokud položka není v seznamu, `IndexOf` vrátí `-1` . Přidejte tento kód do dolní části vaší `Main` metody:

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

Položky v seznamu lze seřadit také. <xref:System.Collections.Generic.List%601.Sort%2A>Metoda seřadí všechny položky v seznamu v normálním pořadí (abecedně pro řetězce). Přidejte tento kód do dolní části naší `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Uložte soubor a zadejte, `dotnet run` abyste si vyzkoušeli tuto nejnovější verzi.

Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `Main` metodu na `WorkingWithStrings` a napište novou `Main` metodu, která volá `WorkingWithStrings` . Až budete hotovi, váš kód by měl vypadat takto:

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

        static void WorkingWithStrings()
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

`string`V seznamu zatím jste používali typ v seznamech. Pojďme <xref:System.Collections.Generic.List%601> použít jiný typ. Pojďme sestavit sadu čísel.

Do dolní části nové metody přidejte následující `Main` :

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

Uložte soubor a zadejte, `dotnet run` aby se zobrazily výsledky.

> [!TIP]
> Chcete-li se soustředit jenom na tuto část, můžete komentovat kód, který volá `WorkingWithStrings();` . Stačí umístit dva `/` znaky před volání jako toto: `// WorkingWithStrings();` .

## <a name="challenge"></a>Úloha

Podívejte se, jestli můžete některé z konceptů spojit z tohoto a předchozích lekcí. Rozhlaste se podle toho, co jste zatím vytvořili s Fibonacci čísly. Zkuste napsat kód, který vygeneruje prvních 20 čísel v sekvenci. (Jako pomocný parametr se jedná o 20 Fibonacci číslo 6765.)

## <a name="complete-challenge"></a>Dokončení výzvy

Ukázkové řešení si můžete prohlédnout po zobrazení [dokončeného ukázkového kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

V každé iteraci smyčky přebíráte poslední dvě celá čísla v seznamu, sečtete je a přidáte tuto hodnotu do seznamu. Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.

Blahopřejeme, dokončili jste kurz k seznamům. V kurzu [Úvod ke třídám](introduction-to-classes.md) můžete pokračovat ve svém vlastním vývojovém prostředí.

Další informace o práci s `List` typem najdete v článku [příručka .NET](../../../standard/index.yml) o [kolekcích](../../../standard/collections/index.md). Naučíte se také mnoho dalších typů kolekcí.
