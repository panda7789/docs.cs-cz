---
title: Práce s kolekcemi – Úvod C# do kurzu
description: Seznamte se s C# tím, že v tomto kurzu prozkoumáte kolekci seznamů.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: b80225cf1614a7c25ac9011acd39e74032465ca3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834150"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="ef825-103">Naučte se spravovat kolekce dat pomocí obecného typu seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="ef825-104">Tento úvodní kurz poskytuje Úvod k C# jazyku a základům třídy <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ef825-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="ef825-105">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="ef825-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="ef825-106">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="ef825-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ef825-107">Rychlý přehled příkazů, které budete používat, se [seznámí s vývojářskými nástroji](local-environment.md)a odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="ef825-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="ef825-108">Příklad základního seznamu</span><span class="sxs-lookup"><span data-stu-id="ef825-108">A basic list example</span></span>

<span data-ttu-id="ef825-109">Vytvoří adresář s názvem *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="ef825-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="ef825-110">Zajistěte, aby byl aktuální adresář a běžel `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="ef825-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="ef825-111">Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte stávající kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ef825-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="ef825-112">Nahraďte `<name>` vaším jménem.</span><span class="sxs-lookup"><span data-stu-id="ef825-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="ef825-113">Uložte *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef825-113">Save *Program.cs*.</span></span> <span data-ttu-id="ef825-114">V okně konzoly zadejte `dotnet run` a zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="ef825-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="ef825-115">Právě jste vytvořili seznam řetězců, Přidali jste do tohoto seznamu tři názvy a vytiskli názvy všech velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="ef825-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="ef825-116">Pomocí konceptů, které jste se naučili v předchozích kurzech, Projděte seznam.</span><span class="sxs-lookup"><span data-stu-id="ef825-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="ef825-117">Kód pro zobrazení názvů využívá funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="ef825-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="ef825-118">Pokud předcházíte `string` s znakem `$`, můžete vložit C# kód do deklarace řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef825-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="ef825-119">Skutečný řetězec nahradí tento C# kód hodnotou, kterou generuje.</span><span class="sxs-lookup"><span data-stu-id="ef825-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="ef825-120">V tomto příkladu nahrazuje `{name.ToUpper()}` s každým názvem převedenými na velká písmena, protože jste volali metodu <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef825-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="ef825-121">Pojďme si to prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="ef825-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="ef825-122">Upravit obsah seznamu</span><span class="sxs-lookup"><span data-stu-id="ef825-122">Modify list contents</span></span>

<span data-ttu-id="ef825-123">Kolekce, kterou jste vytvořili, používá typ <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ef825-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="ef825-124">Tento typ ukládá sekvence prvků.</span><span class="sxs-lookup"><span data-stu-id="ef825-124">This type stores sequences of elements.</span></span> <span data-ttu-id="ef825-125">Zadejte typ prvků mezi lomenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="ef825-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="ef825-126">Jedním z důležitých aspektů tohoto typu <xref:System.Collections.Generic.List%601> je to, že se může zvětšovat nebo zmenšovat, což umožňuje přidat nebo odebrat prvky.</span><span class="sxs-lookup"><span data-stu-id="ef825-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="ef825-127">Přidejte tento kód před uzavírací `}` v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="ef825-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="ef825-128">Přidali jste dva další názvy na konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="ef825-129">Také jste odebrali i jednu z nich.</span><span class="sxs-lookup"><span data-stu-id="ef825-129">You've also removed one as well.</span></span> <span data-ttu-id="ef825-130">Uložte soubor a zadejte `dotnet run` a zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="ef825-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="ef825-131">@No__t-0 umožňuje odkazovat také na jednotlivé položky podle **indexu** .</span><span class="sxs-lookup"><span data-stu-id="ef825-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="ef825-132">Index můžete umístit mezi `[` a tokeny `]` za názvem seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="ef825-133">C#pro první index používá hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="ef825-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="ef825-134">Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte ho:</span><span class="sxs-lookup"><span data-stu-id="ef825-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="ef825-135">Nemůžete získat přístup k indexu za konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="ef825-136">Mějte na paměti, že indexy začínají na 0, takže největší platný index je jeden menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="ef825-137">Můžete zjistit, jak dlouho seznam používá vlastnost <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef825-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="ef825-138">Na konec metody Main přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ef825-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="ef825-139">Uložte soubor a zadejte `dotnet run`, aby se zobrazily výsledky.</span><span class="sxs-lookup"><span data-stu-id="ef825-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="ef825-140">Hledání a řazení seznamů</span><span class="sxs-lookup"><span data-stu-id="ef825-140">Search and sort lists</span></span>

<span data-ttu-id="ef825-141">Naše ukázky používají relativně malé seznamy, ale vaše aplikace často můžou vytvářet seznamy s mnoha více prvky, někdy se číslování v tisících.</span><span class="sxs-lookup"><span data-stu-id="ef825-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="ef825-142">Chcete-li najít prvky v těchto větších kolekcích, je nutné hledat v seznamu různé položky.</span><span class="sxs-lookup"><span data-stu-id="ef825-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="ef825-143">Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> hledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="ef825-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="ef825-144">Přidejte tento kód do dolní části vaší metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="ef825-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="ef825-145">Položky v seznamu lze seřadit také.</span><span class="sxs-lookup"><span data-stu-id="ef825-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="ef825-146">Metoda <xref:System.Collections.Generic.List%601.Sort%2A> seřadí všechny položky v seznamu v normálním pořadí (abecedně v případě řetězců).</span><span class="sxs-lookup"><span data-stu-id="ef825-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="ef825-147">Přidejte tento kód do dolní části našeho `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ef825-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="ef825-148">Uložte soubor a zadejte `dotnet run` a vyzkoušejte si tuto nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="ef825-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="ef825-149">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="ef825-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="ef825-150">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="ef825-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="ef825-151">Přejmenujte metodu `Main` na `WorkingWithStrings` a zapište novou metodu `Main`, která volá `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="ef825-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="ef825-152">Až budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ef825-152">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="ef825-153">Seznamy dalších typů</span><span class="sxs-lookup"><span data-stu-id="ef825-153">Lists of other types</span></span>

<span data-ttu-id="ef825-154">V seznamu zatím jste používali typ `string`.</span><span class="sxs-lookup"><span data-stu-id="ef825-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="ef825-155">Pojďme udělat <xref:System.Collections.Generic.List%601> s použitím jiného typu.</span><span class="sxs-lookup"><span data-stu-id="ef825-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="ef825-156">Pojďme sestavit sadu čísel.</span><span class="sxs-lookup"><span data-stu-id="ef825-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="ef825-157">Do dolní části nové metody @no__t 0 přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="ef825-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="ef825-158">Vytvoří seznam celých čísel a nastaví první dvě celá čísla na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="ef825-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="ef825-159">Jedná se o první dvě hodnoty *Fibonacci sekvence*, sekvence čísel.</span><span class="sxs-lookup"><span data-stu-id="ef825-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="ef825-160">Každé další Fibonacci číslo se zjistí tak, že se vybere součet předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="ef825-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="ef825-161">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="ef825-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="ef825-162">Uložte soubor a zadejte `dotnet run`, aby se zobrazily výsledky.</span><span class="sxs-lookup"><span data-stu-id="ef825-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="ef825-163">Pokud se chcete soustředit jenom na tuto část, můžete komentovat kód, který volá `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="ef825-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="ef825-164">Stačí vložit dva znaky `/` před volání jako toto: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="ef825-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="ef825-165">Výzev</span><span class="sxs-lookup"><span data-stu-id="ef825-165">Challenge</span></span>

<span data-ttu-id="ef825-166">Podívejte se, jestli můžete některé z konceptů spojit z tohoto a předchozích lekcí.</span><span class="sxs-lookup"><span data-stu-id="ef825-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="ef825-167">Rozhlaste se podle toho, co jste zatím vytvořili s Fibonacci čísly.</span><span class="sxs-lookup"><span data-stu-id="ef825-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="ef825-168">Zkuste napsat kód, který vygeneruje prvních 20 čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ef825-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="ef825-169">(Jako pomocný parametr se jedná o 20 Fibonacci číslo 6765.)</span><span class="sxs-lookup"><span data-stu-id="ef825-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="ef825-170">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="ef825-170">Complete challenge</span></span>

<span data-ttu-id="ef825-171">Ukázkové řešení si můžete prohlédnout po zobrazení [dokončeného ukázkového kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="ef825-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="ef825-172">V každé iteraci smyčky přebíráte poslední dvě celá čísla v seznamu, sečtete je a přidáte tuto hodnotu do seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef825-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="ef825-173">Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.</span><span class="sxs-lookup"><span data-stu-id="ef825-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="ef825-174">Blahopřejeme, dokončili jste kurz k seznamům.</span><span class="sxs-lookup"><span data-stu-id="ef825-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="ef825-175">V kurzu [Úvod ke třídám](introduction-to-classes.md) můžete pokračovat ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef825-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="ef825-176">Další informace o práci s typem `List` najdete v tématu [Průvodce .NET](../../../standard/index.md) pro [kolekce](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef825-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="ef825-177">Naučíte se také mnoho dalších typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="ef825-177">You'll also learn about many other collection types.</span></span>
