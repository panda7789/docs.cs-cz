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
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="00dbc-103">Naučte se spravovat pomocí typ obecný seznam kolekcí dat</span><span class="sxs-lookup"><span data-stu-id="00dbc-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="00dbc-104">Tento úvodní kurz obsahuje úvod do C# jazyk a základní informace o <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="00dbc-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="00dbc-105">V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="00dbc-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="00dbc-106">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="00dbc-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="00dbc-107">Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md), s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="00dbc-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="00dbc-108">Příklad základního seznamu</span><span class="sxs-lookup"><span data-stu-id="00dbc-108">A basic list example</span></span>

<span data-ttu-id="00dbc-109">Vytvořte adresář **list-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="00dbc-109">Create a directory named **list-tutorial**.</span></span> <span data-ttu-id="00dbc-110">Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="00dbc-110">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="00dbc-111">Pokud jste právě dokončili [Začínáme s .NET během 10 minut](https://www.microsoft.com/net), můžete dál používat aplikace myApp, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="00dbc-111">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>

<span data-ttu-id="00dbc-112">Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="00dbc-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="00dbc-113">Nahraďte `<name>` s vaším jménem.</span><span class="sxs-lookup"><span data-stu-id="00dbc-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="00dbc-114">Uložit **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="00dbc-114">Save **Program.cs**.</span></span> <span data-ttu-id="00dbc-115">Typ `dotnet run` v okně konzoly můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="00dbc-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="00dbc-116">Právě jste vytvořili seznam řetězců, do tohoto seznamu přidal tři názvy a vytiskne názvy všechna písmena velká.</span><span class="sxs-lookup"><span data-stu-id="00dbc-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="00dbc-117">Používáte koncepty, které jste se naučili v předchozích kurzech se ve smyčce prostřednictvím seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-117">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="00dbc-118">Kód k zobrazení názvů využívá [interpolace](../../language-reference/tokens/interpolated.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="00dbc-118">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="00dbc-119">Když předcházet `string` s `$` znak, můžete vložit kód jazyka C# v deklaraci řetězec.</span><span class="sxs-lookup"><span data-stu-id="00dbc-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="00dbc-120">Aktuální řetězcovou nahradí hodnotu, kterou generuje tento kód jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="00dbc-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="00dbc-121">V tomto příkladu, nahradí `{name.ToUpper()}` s názvy jednotlivých převeden na velká písmena, protože jste volali <xref:System.String.ToUpper%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="00dbc-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="00dbc-122">Umožňuje pokračovat v prozkoumávání služby.</span><span class="sxs-lookup"><span data-stu-id="00dbc-122">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="00dbc-123">Změna seznamu obsahu</span><span class="sxs-lookup"><span data-stu-id="00dbc-123">Modify list contents</span></span>

<span data-ttu-id="00dbc-124">Kolekce, které jste vytvořili, používá <xref:System.Collections.Generic.List%601> typu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="00dbc-125">Tento typ ukládá sekvencí prvků.</span><span class="sxs-lookup"><span data-stu-id="00dbc-125">This type stores sequences of elements.</span></span> <span data-ttu-id="00dbc-126">Můžete zadat typ prvků mezi ostrých závorek.</span><span class="sxs-lookup"><span data-stu-id="00dbc-126">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="00dbc-127">Jeden důležitý aspekt jazyka to <xref:System.Collections.Generic.List%601> typ je, že se může zvětšovat nebo zmenšovat, umožňuje přidat nebo odebrat prvky.</span><span class="sxs-lookup"><span data-stu-id="00dbc-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="00dbc-128">Přidejte tento kód před uzavírací značku `}` v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="00dbc-128">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="00dbc-129">Přidání další dva názvy do konce seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="00dbc-130">Můžete rovněž jsme odstranili jeden také.</span><span class="sxs-lookup"><span data-stu-id="00dbc-130">You've also removed one as well.</span></span> <span data-ttu-id="00dbc-131">Uložte soubor a typ `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="00dbc-131">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="00dbc-132"><xref:System.Collections.Generic.List%601> Umožňuje odkazovat na jednotlivé položky podle **index** také.</span><span class="sxs-lookup"><span data-stu-id="00dbc-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="00dbc-133">Umístění indexu mezi `[` a `]` seznam název tokeny.</span><span class="sxs-lookup"><span data-stu-id="00dbc-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="00dbc-134">C#používá pro první index 0.</span><span class="sxs-lookup"><span data-stu-id="00dbc-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="00dbc-135">Přidejte tento kód přímo pod kód, který jste právě přidali a vyzkoušejte si to:</span><span class="sxs-lookup"><span data-stu-id="00dbc-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="00dbc-136">Index za koncem tohoto seznamu nelze přistupovat.</span><span class="sxs-lookup"><span data-stu-id="00dbc-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="00dbc-137">Mějte na paměti, že indexy začínají hodnotou 0, největší platný index je jeden menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="00dbc-138">Můžete zkontrolovat, jak dlouho je pomocí seznamu <xref:System.Collections.Generic.List%601.Count%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="00dbc-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="00dbc-139">Na konci metody Main přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="00dbc-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="00dbc-140">Uložte soubor a typ `dotnet run` znovu, abyste viděli výsledek.</span><span class="sxs-lookup"><span data-stu-id="00dbc-140">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="00dbc-141">Vyhledávání a řazení seznamy</span><span class="sxs-lookup"><span data-stu-id="00dbc-141">Search and sort lists</span></span>

<span data-ttu-id="00dbc-142">Naše ukázky používat poměrně krátké seznamy, ale vaše aplikace může často vytvořit seznamy s mnoha další prvky, někdy číslování v tisících.</span><span class="sxs-lookup"><span data-stu-id="00dbc-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="00dbc-143">Najít prvky v těchto kolekcích větší, budete muset pro různé položky v seznamu vyhledejte.</span><span class="sxs-lookup"><span data-stu-id="00dbc-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="00dbc-144"><xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="00dbc-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="00dbc-145">Tento kód vložte do dolní části vašeho `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="00dbc-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="00dbc-146">Také lze seřadit položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="00dbc-147"><xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v jejich normálním pořadí (podle abecedy. v případě řetězce).</span><span class="sxs-lookup"><span data-stu-id="00dbc-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="00dbc-148">Tento kód vložte do dolní části našich `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="00dbc-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="00dbc-149">Uložení souboru a typu `dotnet run` vyzkoušet tuto nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="00dbc-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="00dbc-150">Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="00dbc-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="00dbc-151">Který usnadňuje začít pracovat s nový příklad.</span><span class="sxs-lookup"><span data-stu-id="00dbc-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="00dbc-152">Přejmenovat váš `Main` metodu `WorkingWithStrings` a napsat nový `Main` metodu, která volá `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="00dbc-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="00dbc-153">Jakmile budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="00dbc-153">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="00dbc-154">Jiné typy seznamů</span><span class="sxs-lookup"><span data-stu-id="00dbc-154">Lists of other types</span></span>

<span data-ttu-id="00dbc-155">Zatím jste používali `string` typ v seznamech doposud.</span><span class="sxs-lookup"><span data-stu-id="00dbc-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="00dbc-156">Vytvoříme <xref:System.Collections.Generic.List%601> pomocí jiného typu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="00dbc-157">Vytvořme sady čísel.</span><span class="sxs-lookup"><span data-stu-id="00dbc-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="00dbc-158">Přidejte následující k dolnímu okraji nové `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="00dbc-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="00dbc-159">Který vytvoří seznam celých čísel a nastaví prvních dvou celých čísel na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="00dbc-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="00dbc-160">Jde o první dvě hodnoty *Fibonacciho pořadí*, sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="00dbc-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="00dbc-161">Každé další číslo Fibonacciho nenajde provedením součtu předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="00dbc-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="00dbc-162">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="00dbc-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="00dbc-163">Uložení souboru a typu `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="00dbc-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="00dbc-164">Soustředit se na pouze této části, můžete Zakomentovat kód, který volá `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="00dbc-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="00dbc-165">Stačí vložit dvě `/` znaky před volání, jako jsou to: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="00dbc-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="00dbc-166">Výzvy</span><span class="sxs-lookup"><span data-stu-id="00dbc-166">Challenge</span></span>

<span data-ttu-id="00dbc-167">Zobrazit, pokud můžete umístit společně některé koncepty z tohoto a dříve lekce.</span><span class="sxs-lookup"><span data-stu-id="00dbc-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="00dbc-168">Rozbalte na co začlenění zatím Fibonacciho čísly.</span><span class="sxs-lookup"><span data-stu-id="00dbc-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="00dbc-169">Došlo k pokusu o zápis kódu pro vytvoření prvních 20 čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="00dbc-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="00dbc-170">(Jako pomocného parametru, je 20. prosincem Fibonacciho číslo 6765.)</span><span class="sxs-lookup"><span data-stu-id="00dbc-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="00dbc-171">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="00dbc-171">Complete challenge</span></span>

<span data-ttu-id="00dbc-172">Vidíte příklad řešení podle [prohlížení dokončení ukázkového kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="00dbc-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="00dbc-173">S každou iterací smyčky přenášíte posledních dvou celých čísel v seznamu je sčítání a přidáte tuto hodnotu do seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="00dbc-174">Smyčka se opakuje dokud nepřidáte 20 položek do seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="00dbc-175">Blahopřejeme, jste dokončili kurz seznamu.</span><span class="sxs-lookup"><span data-stu-id="00dbc-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="00dbc-176">Můžete pokračovat [Úvod do tříd](introduction-to-classes.md) kurz ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="00dbc-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="00dbc-177">Další informace o práci s `List` zadejte [Průvodce technologií .NET](../../../standard/index.md) téma na [kolekce](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="00dbc-177">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="00dbc-178">Také se dozvíte o mnoho jiných typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="00dbc-178">You'll also learn about many other collection types.</span></span>