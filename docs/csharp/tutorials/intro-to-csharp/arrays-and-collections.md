---
title: Práce s kolekcí – Úvod do C# kurz
description: Přečtěte si C# prozkoumáním kolekce seznamu v tomto kurzu.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: eaf921be2bd50b6e346f57f42e17f151ff336821
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205279"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Naučte se spravovat pomocí typ obecný seznam kolekcí dat

Tento úvodní kurz obsahuje úvod do C# jazyk a základní informace o <xref:System.Collections.Generic.List%601> třídy.

V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj. Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux. Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md), s odkazy na další podrobnosti.

## <a name="a-basic-list-example"></a>Příklad základního seznamu

Vytvořte adresář **list-tutorial**. Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console`.

> [!NOTE]
> Pokud jste právě dokončili [Začínáme s .NET během 10 minut](https://www.microsoft.com/net), můžete dál používat aplikace myApp, který jste právě vytvořili.

Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte existující kód následujícím kódem:

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

Nahraďte `<name>` s vaším jménem. Uložit **Program.cs**. Typ `dotnet run` v okně konzoly můžete vyzkoušet.

Právě jste vytvořili seznam řetězců, do tohoto seznamu přidal tři názvy a vytiskne názvy všechna písmena velká. Používáte koncepty, které jste se naučili v předchozích kurzech se ve smyčce prostřednictvím seznamu.

Kód k zobrazení názvů využívá [interpolace](../../language-reference/tokens/interpolated.md) funkce.  Když předcházet `string` s `$` znak, můžete vložit kód jazyka C# v deklaraci řetězec. Aktuální řetězcovou nahradí hodnotu, kterou generuje tento kód jazyka C#. V tomto příkladu, nahradí `{name.ToUpper()}` s názvy jednotlivých převeden na velká písmena, protože jste volali <xref:System.String.ToUpper%2A> metody.

Umožňuje pokračovat v prozkoumávání služby.

## <a name="modify-list-contents"></a>Změna seznamu obsahu

Kolekce, které jste vytvořili, používá <xref:System.Collections.Generic.List%601> typu. Tento typ ukládá sekvencí prvků. Můžete zadat typ prvků mezi ostrých závorek.

Jeden důležitý aspekt jazyka to <xref:System.Collections.Generic.List%601> typ je, že se může zvětšovat nebo zmenšovat, umožňuje přidat nebo odebrat prvky. Přidejte tento kód před uzavírací značku `}` v `Main` metody:

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

Přidání další dva názvy do konce seznamu. Můžete rovněž jsme odstranili jeden také. Uložte soubor a typ `dotnet run` vyzkoušejte si to.

<xref:System.Collections.Generic.List%601> Umožňuje odkazovat na jednotlivé položky podle **index** také. Umístění indexu mezi `[` a `]` seznam název tokeny. C#používá pro první index 0. Přidejte tento kód přímo pod kód, který jste právě přidali a vyzkoušejte si to:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Index za koncem tohoto seznamu nelze přistupovat. Mějte na paměti, že indexy začínají hodnotou 0, největší platný index je jeden menší než počet položek v seznamu. Můžete zkontrolovat, jak dlouho je pomocí seznamu <xref:System.Collections.Generic.List%601.Count%2A> vlastnost. Na konci metody Main přidejte následující kód:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Uložte soubor a typ `dotnet run` znovu, abyste viděli výsledek.

## <a name="search-and-sort-lists"></a>Vyhledávání a řazení seznamy

Naše ukázky používat poměrně krátké seznamy, ale vaše aplikace může často vytvořit seznamy s mnoha další prvky, někdy číslování v tisících. Najít prvky v těchto kolekcích větší, budete muset pro různé položky v seznamu vyhledejte. <xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky. Tento kód vložte do dolní části vašeho `Main` metody:

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

Také lze seřadit položky v seznamu. <xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v jejich normálním pořadí (podle abecedy. v případě řetězce). Tento kód vložte do dolní části našich `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Uložení souboru a typu `dotnet run` vyzkoušet tuto nejnovější verzi.

Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě. Který usnadňuje začít pracovat s nový příklad. Přejmenovat váš `Main` metodu `WorkingWithStrings` a napsat nový `Main` metodu, která volá `WorkingWithStrings`. Jakmile budete hotovi, váš kód by měl vypadat takto:

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

## <a name="lists-of-other-types"></a>Jiné typy seznamů

Zatím jste používali `string` typ v seznamech doposud. Vytvoříme <xref:System.Collections.Generic.List%601> pomocí jiného typu. Vytvořme sady čísel.

Přidejte následující k dolnímu okraji nové `Main` metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Který vytvoří seznam celých čísel a nastaví prvních dvou celých čísel na hodnotu 1. Jde o první dvě hodnoty *Fibonacciho pořadí*, sekvenci čísel. Každé další číslo Fibonacciho nenajde provedením součtu předchozích dvou čísel. Přidejte tento kód:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Uložení souboru a typu `dotnet run` zobrazíte výsledky.

> [!TIP]
> Soustředit se na pouze této části, můžete Zakomentovat kód, který volá `WorkingWithStrings();`. Stačí vložit dvě `/` znaky před volání, jako jsou to: `// WorkingWithStrings();`.

## <a name="challenge"></a>Výzvy

Zobrazit, pokud můžete umístit společně některé koncepty z tohoto a dříve lekce. Rozbalte na co začlenění zatím Fibonacciho čísly. Došlo k pokusu o zápis kódu pro vytvoření prvních 20 čísel v sekvenci. (Jako pomocného parametru, je 20. prosincem Fibonacciho číslo 6765.)

## <a name="complete-challenge"></a>Dokončení výzvy

Vidíte příklad řešení podle [prohlížení dokončení ukázkového kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)

S každou iterací smyčky přenášíte posledních dvou celých čísel v seznamu je sčítání a přidáte tuto hodnotu do seznamu. Smyčka se opakuje dokud nepřidáte 20 položek do seznamu.

Blahopřejeme, jste dokončili kurz seznamu. Můžete pokračovat [Úvod do tříd](introduction-to-classes.md) kurz ve svém vlastním vývojovém prostředí.

Další informace o práci s `List` zadejte [Průvodce technologií .NET](../../../standard/index.md) téma na [kolekce](../../../standard/collections/index.md). Také se dozvíte o mnoho jiných typů kolekce.