---
title: Práce s kolekcí – Úvod do C# kurz
description: Přečtěte si C# prozkoumáním kolekce seznamu v tomto kurzu.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 064b01a30410b147e89b0f87180d5af9269a3a87
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634518"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="841e9-103">Naučte se spravovat pomocí typ obecný seznam kolekcí dat</span><span class="sxs-lookup"><span data-stu-id="841e9-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="841e9-104">Tento úvodní kurz obsahuje úvod do C# jazyk a základní informace o <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="841e9-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="841e9-105">V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="841e9-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="841e9-106">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="841e9-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="841e9-107">Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md), s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="841e9-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="841e9-108">Příklad základního seznamu</span><span class="sxs-lookup"><span data-stu-id="841e9-108">A basic list example</span></span>

<span data-ttu-id="841e9-109">Vytvořte adresář **list-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="841e9-109">Create a directory named **list-tutorial**.</span></span> <span data-ttu-id="841e9-110">Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="841e9-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="841e9-111">Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="841e9-111">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="841e9-112">Nahraďte `<name>` s vaším jménem.</span><span class="sxs-lookup"><span data-stu-id="841e9-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="841e9-113">Uložit **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="841e9-113">Save **Program.cs**.</span></span> <span data-ttu-id="841e9-114">Typ `dotnet run` v okně konzoly můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="841e9-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="841e9-115">Právě jste vytvořili seznam řetězců, do tohoto seznamu přidal tři názvy a vytiskne názvy všechna písmena velká.</span><span class="sxs-lookup"><span data-stu-id="841e9-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="841e9-116">Používáte koncepty, které jste se naučili v předchozích kurzech se ve smyčce prostřednictvím seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="841e9-117">Kód k zobrazení názvů využívá [interpolace](../../language-reference/tokens/interpolated.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="841e9-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="841e9-118">Když předcházet `string` s `$` znak, můžete vložit kód jazyka C# v deklaraci řetězec.</span><span class="sxs-lookup"><span data-stu-id="841e9-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="841e9-119">Aktuální řetězcovou nahradí hodnotu, kterou generuje tento kód jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="841e9-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="841e9-120">V tomto příkladu, nahradí `{name.ToUpper()}` s názvy jednotlivých převeden na velká písmena, protože jste volali <xref:System.String.ToUpper%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="841e9-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="841e9-121">Umožňuje pokračovat v prozkoumávání služby.</span><span class="sxs-lookup"><span data-stu-id="841e9-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="841e9-122">Změna seznamu obsahu</span><span class="sxs-lookup"><span data-stu-id="841e9-122">Modify list contents</span></span>

<span data-ttu-id="841e9-123">Kolekce, které jste vytvořili, používá <xref:System.Collections.Generic.List%601> typu.</span><span class="sxs-lookup"><span data-stu-id="841e9-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="841e9-124">Tento typ ukládá sekvencí prvků.</span><span class="sxs-lookup"><span data-stu-id="841e9-124">This type stores sequences of elements.</span></span> <span data-ttu-id="841e9-125">Můžete zadat typ prvků mezi ostrých závorek.</span><span class="sxs-lookup"><span data-stu-id="841e9-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="841e9-126">Jeden důležitý aspekt jazyka to <xref:System.Collections.Generic.List%601> typ je, že se může zvětšovat nebo zmenšovat, umožňuje přidat nebo odebrat prvky.</span><span class="sxs-lookup"><span data-stu-id="841e9-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="841e9-127">Přidejte tento kód před uzavírací značku `}` v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="841e9-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="841e9-128">Přidání další dva názvy do konce seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="841e9-129">Můžete rovněž jsme odstranili jeden také.</span><span class="sxs-lookup"><span data-stu-id="841e9-129">You've also removed one as well.</span></span> <span data-ttu-id="841e9-130">Uložte soubor a typ `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="841e9-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="841e9-131"><xref:System.Collections.Generic.List%601> Umožňuje odkazovat na jednotlivé položky podle **index** také.</span><span class="sxs-lookup"><span data-stu-id="841e9-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="841e9-132">Umístění indexu mezi `[` a `]` seznam název tokeny.</span><span class="sxs-lookup"><span data-stu-id="841e9-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="841e9-133">C#používá pro první index 0.</span><span class="sxs-lookup"><span data-stu-id="841e9-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="841e9-134">Přidejte tento kód přímo pod kód, který jste právě přidali a vyzkoušejte si to:</span><span class="sxs-lookup"><span data-stu-id="841e9-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="841e9-135">Index za koncem tohoto seznamu nelze přistupovat.</span><span class="sxs-lookup"><span data-stu-id="841e9-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="841e9-136">Mějte na paměti, že indexy začínají hodnotou 0, největší platný index je jeden menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="841e9-137">Můžete zkontrolovat, jak dlouho je pomocí seznamu <xref:System.Collections.Generic.List%601.Count%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="841e9-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="841e9-138">Na konci metody Main přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="841e9-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="841e9-139">Uložte soubor a typ `dotnet run` znovu, abyste viděli výsledek.</span><span class="sxs-lookup"><span data-stu-id="841e9-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="841e9-140">Vyhledávání a řazení seznamy</span><span class="sxs-lookup"><span data-stu-id="841e9-140">Search and sort lists</span></span>

<span data-ttu-id="841e9-141">Naše ukázky používat poměrně krátké seznamy, ale vaše aplikace může často vytvořit seznamy s mnoha další prvky, někdy číslování v tisících.</span><span class="sxs-lookup"><span data-stu-id="841e9-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="841e9-142">Najít prvky v těchto kolekcích větší, budete muset pro různé položky v seznamu vyhledejte.</span><span class="sxs-lookup"><span data-stu-id="841e9-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="841e9-143"><xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="841e9-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="841e9-144">Tento kód vložte do dolní části vašeho `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="841e9-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="841e9-145">Také lze seřadit položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="841e9-146"><xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v jejich normálním pořadí (podle abecedy. v případě řetězce).</span><span class="sxs-lookup"><span data-stu-id="841e9-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="841e9-147">Tento kód vložte do dolní části našich `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="841e9-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="841e9-148">Uložení souboru a typu `dotnet run` vyzkoušet tuto nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="841e9-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="841e9-149">Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="841e9-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="841e9-150">Který usnadňuje začít pracovat s nový příklad.</span><span class="sxs-lookup"><span data-stu-id="841e9-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="841e9-151">Přejmenovat váš `Main` metodu `WorkingWithStrings` a napsat nový `Main` metodu, která volá `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="841e9-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="841e9-152">Jakmile budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="841e9-152">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="841e9-153">Jiné typy seznamů</span><span class="sxs-lookup"><span data-stu-id="841e9-153">Lists of other types</span></span>

<span data-ttu-id="841e9-154">Zatím jste používali `string` typ v seznamech doposud.</span><span class="sxs-lookup"><span data-stu-id="841e9-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="841e9-155">Vytvoříme <xref:System.Collections.Generic.List%601> pomocí jiného typu.</span><span class="sxs-lookup"><span data-stu-id="841e9-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="841e9-156">Vytvořme sady čísel.</span><span class="sxs-lookup"><span data-stu-id="841e9-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="841e9-157">Přidejte následující k dolnímu okraji nové `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="841e9-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="841e9-158">Který vytvoří seznam celých čísel a nastaví prvních dvou celých čísel na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="841e9-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="841e9-159">Jde o první dvě hodnoty *Fibonacciho pořadí*, sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="841e9-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="841e9-160">Každé další číslo Fibonacciho nenajde provedením součtu předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="841e9-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="841e9-161">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="841e9-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="841e9-162">Uložení souboru a typu `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="841e9-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="841e9-163">Soustředit se na pouze této části, můžete Zakomentovat kód, který volá `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="841e9-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="841e9-164">Stačí vložit dvě `/` znaky před volání, jako jsou to: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="841e9-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="841e9-165">Výzvy</span><span class="sxs-lookup"><span data-stu-id="841e9-165">Challenge</span></span>

<span data-ttu-id="841e9-166">Zobrazit, pokud můžete umístit společně některé koncepty z tohoto a dříve lekce.</span><span class="sxs-lookup"><span data-stu-id="841e9-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="841e9-167">Rozbalte na co začlenění zatím Fibonacciho čísly.</span><span class="sxs-lookup"><span data-stu-id="841e9-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="841e9-168">Došlo k pokusu o zápis kódu pro vytvoření prvních 20 čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="841e9-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="841e9-169">(Jako pomocného parametru, je 20. prosincem Fibonacciho číslo 6765.)</span><span class="sxs-lookup"><span data-stu-id="841e9-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="841e9-170">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="841e9-170">Complete challenge</span></span>

<span data-ttu-id="841e9-171">Vidíte příklad řešení podle [prohlížení dokončení ukázkového kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="841e9-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="841e9-172">S každou iterací smyčky přenášíte posledních dvou celých čísel v seznamu je sčítání a přidáte tuto hodnotu do seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="841e9-173">Smyčka se opakuje dokud nepřidáte 20 položek do seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="841e9-174">Blahopřejeme, jste dokončili kurz seznamu.</span><span class="sxs-lookup"><span data-stu-id="841e9-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="841e9-175">Můžete pokračovat [Úvod do tříd](introduction-to-classes.md) kurz ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="841e9-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="841e9-176">Další informace o práci s `List` zadejte [Průvodce technologií .NET](../../../standard/index.md) téma na [kolekce](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="841e9-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="841e9-177">Také se dozvíte o mnoho jiných typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="841e9-177">You'll also learn about many other collection types.</span></span>
