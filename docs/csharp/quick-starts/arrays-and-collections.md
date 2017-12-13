---
title: "Rychlý Start - kolekce – Průvodce C#"
description: "Výuka C# prozkoumáním kolekce seznamu v této úvodní."
keywords: "C#, začít, kurz, kolekcí, seznamu"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 6f559c7a3290e7db2266e10ec792c283394fb904
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2017
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="331b9-104">C# rychlý start: kolekce</span><span class="sxs-lookup"><span data-stu-id="331b9-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="331b9-105">Tento úvodní poskytuje úvod do jazyka C# a základní informace o <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="331b9-105">This quick start provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="331b9-106">Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="331b9-106">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="331b9-107">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="331b9-107">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="331b9-108">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní rychlé zahájení](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="331b9-108">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="331b9-109">Příklad základního seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-109">A basic list example.</span></span>

<span data-ttu-id="331b9-110">Vytvořte adresář s názvem **seznamu – rychlý Start**.</span><span class="sxs-lookup"><span data-stu-id="331b9-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="331b9-111">Ujistěte, že aktuální adresář a spusťte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="331b9-111">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="331b9-112">Pokud jste právě dokončili [Začínáme s .NET za 10 minut](https://www.microsoft.com/net), můžete používat aplikace Moje aplikace, kterou jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="331b9-112">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>
 
<span data-ttu-id="331b9-113">Otevřete **Program.cs** v oblíbeném editoru a nahraďte existující kód následující:</span><span class="sxs-lookup"><span data-stu-id="331b9-113">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="331b9-114">Nahraďte `<name>` s vaším jménem.</span><span class="sxs-lookup"><span data-stu-id="331b9-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="331b9-115">Uložit **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="331b9-115">Save **Program.cs**.</span></span> <span data-ttu-id="331b9-116">Typ `dotnet run` v okně konzoly vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="331b9-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="331b9-117">Jste právě vytvořili seznam řetězců, přidat tři názvy do tohoto seznamu a vytisknout se názvy v velká písmena.</span><span class="sxs-lookup"><span data-stu-id="331b9-117">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="331b9-118">Koncepty, které jste se naučili v dříve rychle spustí používáte k prosmyčkování seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-118">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="331b9-119">Kód zobrazení názvů využívá **interpolované řetězce**.</span><span class="sxs-lookup"><span data-stu-id="331b9-119">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="331b9-120">Když je před `string` s `$` znak, vložením kódu C# v deklaraci řetězec.</span><span class="sxs-lookup"><span data-stu-id="331b9-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="331b9-121">Konkrétní řetězec nahradí hodnotu, kterou generuje tento kód C#.</span><span class="sxs-lookup"><span data-stu-id="331b9-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="331b9-122">V tomto příkladu se nahradí `{name.ToUpper()}` s každý název převeden na velká písmena, protože jste volali metodu <xref:System.String.ToUpper%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="331b9-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="331b9-123">Zachovat umožňuje prohlížení.</span><span class="sxs-lookup"><span data-stu-id="331b9-123">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="331b9-124">Změna seznamu obsahu</span><span class="sxs-lookup"><span data-stu-id="331b9-124">Modify list contents</span></span>

<span data-ttu-id="331b9-125">Kolekce, které jste vytvořili, používá <xref:System.Collections.Generic.List%601> typu.</span><span class="sxs-lookup"><span data-stu-id="331b9-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="331b9-126">Tento typ ukládá pořadí elementů.</span><span class="sxs-lookup"><span data-stu-id="331b9-126">This type stores sequences of elements.</span></span> <span data-ttu-id="331b9-127">Můžete zadat typ elementů mezi lomené závorky.</span><span class="sxs-lookup"><span data-stu-id="331b9-127">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="331b9-128">Jeden důležitým aspektem tohoto <xref:System.Collections.Generic.List%601> typ je ho můžete zvětšit nebo zmenšit, umožňuje přidat nebo odebrat elementy.</span><span class="sxs-lookup"><span data-stu-id="331b9-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="331b9-129">Přidejte tento kód před uzavírací `}` v `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="331b9-129">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="331b9-130">Přidali jste dva další názvy na konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="331b9-131">Můžete rovněž jsme odstranili jeden také.</span><span class="sxs-lookup"><span data-stu-id="331b9-131">You've also removed one as well.</span></span> <span data-ttu-id="331b9-132">Uložte soubor a typ `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="331b9-132">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="331b9-133"><xref:System.Collections.Generic.List%601> Umožňuje odkazovat na jednotlivé položky podle **index** také.</span><span class="sxs-lookup"><span data-stu-id="331b9-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="331b9-134">Umístěte index mezi `[` a `]` tokeny následující název seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="331b9-135">C# používá 0 pro první index.</span><span class="sxs-lookup"><span data-stu-id="331b9-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="331b9-136">Přidejte tento kód přímo pod kód, který jste právě přidali a zkuste to:</span><span class="sxs-lookup"><span data-stu-id="331b9-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="331b9-137">Nelze získat přístup k indexu přesahuje za konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-137">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="331b9-138">Mějte na paměti, že indexy, které začínají hodnotou 0, takže největší platný index představuje jedno menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="331b9-139">Můžete zkontrolovat, jak dlouho je pomocí seznamu <xref:System.Collections.Generic.List%601.Count%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="331b9-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="331b9-140">Na konci metodu Main, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="331b9-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="331b9-141">Uložte soubor a typ `dotnet run` znovu a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="331b9-141">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="331b9-142">Seznamy hledání a řazení.</span><span class="sxs-lookup"><span data-stu-id="331b9-142">Search and sort lists</span></span>
<span data-ttu-id="331b9-143">Naše ukázky použít seznamy poměrně malý, ale aplikace může často vytvořit seznamy s mnoha další prvky, které se někdy číslování v tisíců.</span><span class="sxs-lookup"><span data-stu-id="331b9-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="331b9-144">Elementy v těchto kolekcích větší najdete budete muset pro různé položky v seznamu Hledat.</span><span class="sxs-lookup"><span data-stu-id="331b9-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="331b9-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda vyhledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="331b9-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="331b9-146">Tento kód vložte do dolní části vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="331b9-146">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="331b9-147">Také lze seřadit položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-147">The items in your list can be sorted as well.</span></span> <span data-ttu-id="331b9-148"><xref:System.Collections.Generic.List%601.Sort%2A> Metoda seřadí všechny položky v seznamu v jejich normálním pořadí (podle abecedy. v případě řetězce).</span><span class="sxs-lookup"><span data-stu-id="331b9-148">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="331b9-149">Tento kód vložte do spodní části našich `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="331b9-149">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="331b9-150">Uložte soubor a typ `dotnet run` pokusit tento nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="331b9-150">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="331b9-151">Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="331b9-151">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="331b9-152">Který usnadňuje začít pracovat s novou příklad.</span><span class="sxs-lookup"><span data-stu-id="331b9-152">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="331b9-153">Přejmenujte vaše `Main` metodu `WorkingWithStrings` a zápis nový `Main` metoda, která volá `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="331b9-153">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="331b9-154">Po dokončení, váš kód by měl vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="331b9-154">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="331b9-155">Seznam dalších typů</span><span class="sxs-lookup"><span data-stu-id="331b9-155">Lists of other types</span></span>

<span data-ttu-id="331b9-156">Jste dosud používali `string` typu v seznamech dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="331b9-156">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="331b9-157">Provedeme <xref:System.Collections.Generic.List%601> pomocí jiného typu.</span><span class="sxs-lookup"><span data-stu-id="331b9-157">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="331b9-158">Vytvořme sady čísel.</span><span class="sxs-lookup"><span data-stu-id="331b9-158">Let's build a set of numbers.</span></span> 

<span data-ttu-id="331b9-159">Přidejte následující k dolnímu okraji nové `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="331b9-159">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="331b9-160">Zda vytvoří seznam celých čísel a nastaví první dva celých čísel na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="331b9-160">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="331b9-161">Jedná se o první dvě hodnoty z *Fibonacciho pořadí*, pořadí čísel.</span><span class="sxs-lookup"><span data-stu-id="331b9-161">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="331b9-162">Každé další číslo Fibonacciho nachází provedením součet předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="331b9-162">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="331b9-163">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="331b9-163">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="331b9-164">Uložte soubor a typ `dotnet run` a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="331b9-164">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="331b9-165">Soustředit se na právě v této části, můžete Zakomentovat kód, který volá `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="331b9-165">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="331b9-166">Vloží dva pouze `/` znaky před volání, jako to: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="331b9-166">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="331b9-167">výzvy</span><span class="sxs-lookup"><span data-stu-id="331b9-167">Challenge</span></span>
<span data-ttu-id="331b9-168">Pokud můžete umístit společně najdete některé koncepty z tohoto a starší lekce.</span><span class="sxs-lookup"><span data-stu-id="331b9-168">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="331b9-169">Rozbalte položku na co jste vytvořili, pokud se Fibonacciho čísla.</span><span class="sxs-lookup"><span data-stu-id="331b9-169">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="331b9-170">Zkuste napsat kód pro vytvoření prvních 20 čísel v pořadí.</span><span class="sxs-lookup"><span data-stu-id="331b9-170">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="331b9-171">(Jako nápovědu, je číslo 20 Fibonacciho 6765.)</span><span class="sxs-lookup"><span data-stu-id="331b9-171">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="331b9-172">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="331b9-172">Complete challenge</span></span>

<span data-ttu-id="331b9-173">Zobrazí se příklad řešení s nástrojem [prohlížení dokončení ukázkový kód na Githubu](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="331b9-173">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="331b9-174">S každou iteraci smyčky přenášíte posledních dvou celých čísel v seznamu je sčítání a přidáním této hodnoty do seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-174">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="331b9-175">Smyčky se opakuje, dokud nepřidáte 20 položky do seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-175">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="331b9-176">Blahopřejeme, jste dokončili rychlé spuštění seznamu.</span><span class="sxs-lookup"><span data-stu-id="331b9-176">Congratulations, you've completed the list quick start.</span></span> <span data-ttu-id="331b9-177">Můžete pokračovat [Úvod do třídy](introduction-to-classes.md) úvodní ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="331b9-177">You can continue with the [Introduction to classes](introduction-to-classes.md) quick start in your own development environment.</span></span>

<span data-ttu-id="331b9-178">Další informace o práci s `List` zadejte [.NET průvodce](../../standard/index.md) téma na [kolekce](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="331b9-178">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="331b9-179">Budete také informace o mnoho dalších typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="331b9-179">You'll also learn about many other collection types.</span></span>
