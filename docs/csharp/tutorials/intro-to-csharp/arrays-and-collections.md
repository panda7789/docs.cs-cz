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
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="4d67c-103">Naučte se spravovat kolekce dat pomocí obecného typu seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="4d67c-104">Tento úvodní kurz poskytuje Úvod do jazyka C# a základy <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d67c-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="4d67c-105">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="4d67c-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="4d67c-106">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="4d67c-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="4d67c-107">Rychlý přehled příkazů, které budete používat, se [seznámí s vývojářskými nástroji](local-environment.md)a odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="4d67c-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="4d67c-108">Příklad základního seznamu</span><span class="sxs-lookup"><span data-stu-id="4d67c-108">A basic list example</span></span>

<span data-ttu-id="4d67c-109">Vytvoří adresář s názvem *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="4d67c-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="4d67c-110">Zajistěte, aby byl aktuální adresář a běžel `dotnet new console` .</span><span class="sxs-lookup"><span data-stu-id="4d67c-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="4d67c-111">Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte stávající kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4d67c-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="4d67c-112">Nahraďte `<name>` vaším jménem.</span><span class="sxs-lookup"><span data-stu-id="4d67c-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="4d67c-113">Soubor *Program.cs* uložte.</span><span class="sxs-lookup"><span data-stu-id="4d67c-113">Save *Program.cs*.</span></span> <span data-ttu-id="4d67c-114">Zadejte `dotnet run` okno konzoly a zkuste to.</span><span class="sxs-lookup"><span data-stu-id="4d67c-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="4d67c-115">Vytvořili jste seznam řetězců, Přidali jste do tohoto seznamu tři názvy a vytiskli jste názvy všech velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="4d67c-115">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="4d67c-116">Pomocí konceptů, které jste se naučili v předchozích kurzech, Projděte seznam.</span><span class="sxs-lookup"><span data-stu-id="4d67c-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="4d67c-117">Kód pro zobrazení názvů využívá funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="4d67c-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="4d67c-118">Pokud předcházíte `string` `$` znak, můžete vložit kód jazyka C# do deklarace řetězce.</span><span class="sxs-lookup"><span data-stu-id="4d67c-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="4d67c-119">Skutečný řetězec nahradí kód v jazyce C# hodnotou, kterou generuje.</span><span class="sxs-lookup"><span data-stu-id="4d67c-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="4d67c-120">V tomto příkladu nahrazuje `{name.ToUpper()}` název s každým názvem převedenými na velká písmena, protože jste volali <xref:System.String.ToUpper%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="4d67c-121">Pojďme si to prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="4d67c-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="4d67c-122">Upravit obsah seznamu</span><span class="sxs-lookup"><span data-stu-id="4d67c-122">Modify list contents</span></span>

<span data-ttu-id="4d67c-123">Kolekce, kterou jste vytvořili, používá <xref:System.Collections.Generic.List%601> typ.</span><span class="sxs-lookup"><span data-stu-id="4d67c-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="4d67c-124">Tento typ ukládá sekvence prvků.</span><span class="sxs-lookup"><span data-stu-id="4d67c-124">This type stores sequences of elements.</span></span> <span data-ttu-id="4d67c-125">Zadejte typ prvků mezi lomenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="4d67c-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="4d67c-126">Jedním z důležitých aspektů tohoto <xref:System.Collections.Generic.List%601> typu je, že může být zvětšen nebo zmenšen, což umožňuje přidat nebo odebrat prvky.</span><span class="sxs-lookup"><span data-stu-id="4d67c-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="4d67c-127">Přidejte tento kód před uzavírací `}` v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d67c-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="4d67c-128">Přidali jste dva další názvy na konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="4d67c-129">Také jste odebrali i jednu z nich.</span><span class="sxs-lookup"><span data-stu-id="4d67c-129">You've also removed one as well.</span></span> <span data-ttu-id="4d67c-130">Uložte soubor a zadejte ho a `dotnet run` zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="4d67c-131"><xref:System.Collections.Generic.List%601>Umožňuje také odkazovat na jednotlivé položky podle **indexu** .</span><span class="sxs-lookup"><span data-stu-id="4d67c-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="4d67c-132">Index mezi `[` a `]` tokeny umístěte za název seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="4d67c-133">Jazyk C# používá pro první index hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="4d67c-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="4d67c-134">Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte ho:</span><span class="sxs-lookup"><span data-stu-id="4d67c-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="4d67c-135">Nemůžete získat přístup k indexu za konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-135">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="4d67c-136">Mějte na paměti, že indexy začínají na 0, takže největší platný index je jeden menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="4d67c-137">Můžete zjistit, jak dlouho seznam používá <xref:System.Collections.Generic.List%601.Count%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d67c-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="4d67c-138">Na konec metody Main přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4d67c-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="4d67c-139">Uložte soubor a zadejte znovu, `dotnet run` abyste viděli výsledky.</span><span class="sxs-lookup"><span data-stu-id="4d67c-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="4d67c-140">Hledání a řazení seznamů</span><span class="sxs-lookup"><span data-stu-id="4d67c-140">Search and sort lists</span></span>

<span data-ttu-id="4d67c-141">Naše ukázky používají relativně malé seznamy, ale vaše aplikace často můžou vytvářet seznamy s mnoha více prvky, někdy se číslování v tisících.</span><span class="sxs-lookup"><span data-stu-id="4d67c-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="4d67c-142">Chcete-li najít prvky v těchto větších kolekcích, je nutné hledat v seznamu různé položky.</span><span class="sxs-lookup"><span data-stu-id="4d67c-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="4d67c-143"><xref:System.Collections.Generic.List%601.IndexOf%2A>Metoda vyhledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="4d67c-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="4d67c-144">Pokud položka není v seznamu, `IndexOf` vrátí `-1` .</span><span class="sxs-lookup"><span data-stu-id="4d67c-144">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="4d67c-145">Přidejte tento kód do dolní části vaší `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="4d67c-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="4d67c-146">Položky v seznamu lze seřadit také.</span><span class="sxs-lookup"><span data-stu-id="4d67c-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="4d67c-147"><xref:System.Collections.Generic.List%601.Sort%2A>Metoda seřadí všechny položky v seznamu v normálním pořadí (abecedně pro řetězce).</span><span class="sxs-lookup"><span data-stu-id="4d67c-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="4d67c-148">Přidejte tento kód do dolní části naší `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="4d67c-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="4d67c-149">Uložte soubor a zadejte, `dotnet run` abyste si vyzkoušeli tuto nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="4d67c-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="4d67c-150">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="4d67c-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="4d67c-151">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="4d67c-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="4d67c-152">Přejmenujte `Main` metodu na `WorkingWithStrings` a napište novou `Main` metodu, která volá `WorkingWithStrings` .</span><span class="sxs-lookup"><span data-stu-id="4d67c-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="4d67c-153">Až budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="4d67c-153">When you've finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="4d67c-154">Seznamy dalších typů</span><span class="sxs-lookup"><span data-stu-id="4d67c-154">Lists of other types</span></span>

<span data-ttu-id="4d67c-155">`string`V seznamu zatím jste používali typ v seznamech.</span><span class="sxs-lookup"><span data-stu-id="4d67c-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="4d67c-156">Pojďme <xref:System.Collections.Generic.List%601> použít jiný typ.</span><span class="sxs-lookup"><span data-stu-id="4d67c-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="4d67c-157">Pojďme sestavit sadu čísel.</span><span class="sxs-lookup"><span data-stu-id="4d67c-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="4d67c-158">Do dolní části nové metody přidejte následující `Main` :</span><span class="sxs-lookup"><span data-stu-id="4d67c-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="4d67c-159">Vytvoří seznam celých čísel a nastaví první dvě celá čísla na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="4d67c-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="4d67c-160">Jedná se o první dvě hodnoty *Fibonacci sekvence*, sekvence čísel.</span><span class="sxs-lookup"><span data-stu-id="4d67c-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="4d67c-161">Každé další Fibonacci číslo se zjistí tak, že se vybere součet předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="4d67c-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="4d67c-162">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="4d67c-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="4d67c-163">Uložte soubor a zadejte, `dotnet run` aby se zobrazily výsledky.</span><span class="sxs-lookup"><span data-stu-id="4d67c-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="4d67c-164">Chcete-li se soustředit jenom na tuto část, můžete komentovat kód, který volá `WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="4d67c-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="4d67c-165">Stačí umístit dva `/` znaky před volání jako toto: `// WorkingWithStrings();` .</span><span class="sxs-lookup"><span data-stu-id="4d67c-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="4d67c-166">Úloha</span><span class="sxs-lookup"><span data-stu-id="4d67c-166">Challenge</span></span>

<span data-ttu-id="4d67c-167">Podívejte se, jestli můžete některé z konceptů spojit z tohoto a předchozích lekcí.</span><span class="sxs-lookup"><span data-stu-id="4d67c-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="4d67c-168">Rozhlaste se podle toho, co jste zatím vytvořili s Fibonacci čísly.</span><span class="sxs-lookup"><span data-stu-id="4d67c-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="4d67c-169">Zkuste napsat kód, který vygeneruje prvních 20 čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4d67c-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="4d67c-170">(Jako pomocný parametr se jedná o 20 Fibonacci číslo 6765.)</span><span class="sxs-lookup"><span data-stu-id="4d67c-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="4d67c-171">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="4d67c-171">Complete challenge</span></span>

<span data-ttu-id="4d67c-172">Ukázkové řešení si můžete prohlédnout po zobrazení [dokončeného ukázkového kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="4d67c-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="4d67c-173">V každé iteraci smyčky přebíráte poslední dvě celá čísla v seznamu, sečtete je a přidáte tuto hodnotu do seznamu.</span><span class="sxs-lookup"><span data-stu-id="4d67c-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="4d67c-174">Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.</span><span class="sxs-lookup"><span data-stu-id="4d67c-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="4d67c-175">Blahopřejeme, dokončili jste kurz k seznamům.</span><span class="sxs-lookup"><span data-stu-id="4d67c-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="4d67c-176">V kurzu [Úvod ke třídám](introduction-to-classes.md) můžete pokračovat ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="4d67c-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="4d67c-177">Další informace o práci s `List` typem najdete v článku [příručka .NET](../../../standard/index.yml) o [kolekcích](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d67c-177">You can learn more about working with the `List` type in the [.NET guide](../../../standard/index.yml) article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="4d67c-178">Naučíte se také mnoho dalších typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="4d67c-178">You'll also learn about many other collection types.</span></span>
