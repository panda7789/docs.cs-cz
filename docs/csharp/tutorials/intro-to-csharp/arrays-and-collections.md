---
title: Práce s kolekcemi – úvod do kurzu Jazyka C#
description: Naučte se C# tak, že prozkoumáte kolekci Seznam v tomto kurzu.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 554a4601157a7d4b873c22a46ee72b6601fc36d7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635655"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Naučte se spravovat kolekce dat pomocí obecného typu seznamu

Tento úvodní kurz poskytuje úvod do jazyka C# a základy <xref:System.Collections.Generic.List%601> třídy.

Tento kurz očekává, že budete mít počítač, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS. Rychlý přehled příkazů, které budete používat, je v [seznamu Seznamte se s vývojovými nástroji](local-environment.md)s odkazy na další podrobnosti.

## <a name="a-basic-list-example"></a>Základní příklad seznamu

Vytvořte adresář s názvem *list-tutorial*. Z toho, že `dotnet new console`aktuální adresář a spustit .

Otevřete *Program.cs* v oblíbeném editoru a nahraďte existující kód následujícím:

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

Nahraďte `<name>` své jméno. Soubor *Program.cs* uložte. Zkuste `dotnet run` to zadejte do okna konzoly.

Právě jste vytvořili seznam řetězců, přidali tři názvy do tohoto seznamu a vytiskli názvy ve všech písmenech zakončení. Používáte koncepty, které jste se naučili v předchozích kurzech pro smyčku prostřednictvím seznamu.

Kód pro zobrazení názvů používá funkci [interpolace řetězců.](../../language-reference/tokens/interpolated.md)  Když předcházíte `string` `$` znak, můžete vložit kód C# do deklarace řetězce. Skutečný řetězec nahradí tento kód Jazyka C# hodnotou, kterou generuje. V tomto příkladu nahradí `{name.ToUpper()}` s každým názvem, převedeny na velká <xref:System.String.ToUpper%2A> písmena, protože jste volali metodu.

Pojďme pokračovat v průzkumu.

## <a name="modify-list-contents"></a>Změna obsahu seznamu

Kolekce, kterou jste <xref:System.Collections.Generic.List%601> vytvořili, používá typ. Tento typ ukládá sekvence prvků. Určete typ prvků mezi úhlovými závorkami.

Jedním z důležitých aspektů tohoto <xref:System.Collections.Generic.List%601> typu je, že může zvětšit nebo zmenšit, což umožňuje přidat nebo odebrat prvky. Přidejte tento kód `}` před `Main` uzávěrkou v metodě:

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

Přidali jste další dvě jména na konec seznamu. Také jste odstranili jeden stejně. Uložte soubor a `dotnet run` zadejte jej vyzkoušejte.

Umožňuje <xref:System.Collections.Generic.List%601> odkazovat na jednotlivé položky podle **indexu.** Umístíte index `[` mezi `]` a tokeny za název seznamu. C# používá 0 pro první index. Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte jej:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nelze získat přístup k indexu za konec seznamu. Mějte na paměti, že indexy začínají na 0, takže největší platný index je o jeden menší než počet položek v seznamu. Můžete zkontrolovat, jak dlouho seznam <xref:System.Collections.Generic.List%601.Count%2A> používá vlastnost. Na konec metody Main přidejte následující kód:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Uložte soubor a `dotnet run` znovu zadejte, abyste viděli výsledky.

## <a name="search-and-sort-lists"></a>Hledání a řazení v seznamech

Naše ukázky používají relativně malé seznamy, ale vaše aplikace mohou často vytvářet seznamy s mnoha dalšími prvky, někdy číslováním v tisících. Chcete-li najít prvky v těchto větších kolekcích, je třeba hledat v seznamu pro různé položky. Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> vyhledá položku a vrátí index položky. Přidejte tento kód na `Main` konec metody:

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

Položky v seznamu lze také seřadit. Metoda <xref:System.Collections.Generic.List%601.Sort%2A> seřadí všechny položky v seznamu v normálním pořadí (abecedně v případě řetězců). Přidejte tento kód na `Main` konec naší metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Chcete-li vyzkoušet tuto nejnovější verzi, uložte soubor a zadejte. `dotnet run`

Než začnete další část, přesuneme aktuální kód do samostatné metody. To usnadňuje začít pracovat s novým příkladem. Přejmenujte `Main` metodu na `WorkingWithStrings` `Main` a napište novou metodu, která volá `WorkingWithStrings`. Po dokončení by měl váš kód vypadat takto:

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

## <a name="lists-of-other-types"></a>Seznamy jiných typů

Byl jste pomocí `string` typu v seznamech tak daleko. Pojďme udělat <xref:System.Collections.Generic.List%601> použití jiného typu. Sestavíme sadu čísel.

Přidejte na konec nové `Main` metody následující:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

To vytvoří seznam celá čísla a nastaví první dvě celá čísla na hodnotu 1. Jedná se o první dvě hodnoty *Fibonacciho sekvence*, posloupnost čísel. Každé další Fibonacciho číslo se najde součtem předchozích dvou čísel. Přidejte tento kód:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Uložte soubor `dotnet run` a zadejte, abyste viděli výsledky.

> [!TIP]
> Chcete-li se soustředit pouze na tuto `WorkingWithStrings();`část, můžete zakomentovat kód, který volá . Stačí dát `/` dvě postavy v přední `// WorkingWithStrings();`části hovoru, jako je tento: .

## <a name="challenge"></a>Úloha

Uvidíme, jestli můžete dát dohromady některé pojmy z této a dřívější lekce. Rozšiřte to, co jste dosud vytvořili s Fibonacciho čísly. Pokuste se napsat kód generovat prvních 20 čísel v pořadí. (Jako náznak, 20. Fibonacciho číslo je 6765.)

## <a name="complete-challenge"></a>Dokončení výzvy

Ukázkové řešení můžete zobrazit na [hotový ukázkový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

S každou iteraci smyčky, budete mít poslední dvě celá čísla v seznamu, jejich sčítání a přidání této hodnoty do seznamu. Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.

Gratulujeme, jste dokončili seznam tutorial. Můžete pokračovat s [úvod do tříd](introduction-to-classes.md) kurzu ve vlastním vývojovém prostředí.

Další informace o práci `List` s typem naleznete v článku [s průvodcem .NET](../../../standard/index.yml) o [kolekcích](../../../standard/collections/index.md). Dozvíte se také o mnoha dalších typech kolekcí.
