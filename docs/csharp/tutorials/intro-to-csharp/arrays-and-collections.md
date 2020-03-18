---
title: Práce s kolekcemi – úvod do kurzu Jazyka C#
description: Naučte se C# tak, že prozkoumáte kolekci Seznam v tomto kurzu.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 25d20de2eae8ad1f544fa17553c173a6141ae464
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156686"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="f9cb1-103">Naučte se spravovat kolekce dat pomocí obecného typu seznamu</span><span class="sxs-lookup"><span data-stu-id="f9cb1-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="f9cb1-104">Tento úvodní kurz poskytuje úvod do jazyka C# a základy <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="f9cb1-105">Tento kurz očekává, že budete mít počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f9cb1-106">Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="f9cb1-107">Rychlý přehled příkazů, které budete používat, je v [seznamu Seznamte se s vývojovými nástroji](local-environment.md)s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="f9cb1-108">Základní příklad seznamu</span><span class="sxs-lookup"><span data-stu-id="f9cb1-108">A basic list example</span></span>

<span data-ttu-id="f9cb1-109">Vytvořte adresář s názvem *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="f9cb1-110">Z toho, že `dotnet new console`aktuální adresář a spustit .</span><span class="sxs-lookup"><span data-stu-id="f9cb1-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="f9cb1-111">Otevřete *Program.cs* v oblíbeném editoru a nahraďte existující kód následujícím:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="f9cb1-112">Nahraďte `<name>` své jméno.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="f9cb1-113">Soubor *Program.cs* uložte.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-113">Save *Program.cs*.</span></span> <span data-ttu-id="f9cb1-114">Zkuste `dotnet run` to zadejte do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="f9cb1-115">Právě jste vytvořili seznam řetězců, přidali tři názvy do tohoto seznamu a vytiskli názvy ve všech písmenech zakončení.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="f9cb1-116">Používáte koncepty, které jste se naučili v předchozích kurzech pro smyčku prostřednictvím seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="f9cb1-117">Kód pro zobrazení názvů používá funkci [interpolace řetězců.](../../language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="f9cb1-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="f9cb1-118">Když předcházíte `string` `$` znak, můžete vložit kód C# do deklarace řetězce.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="f9cb1-119">Skutečný řetězec nahradí tento kód Jazyka C# hodnotou, kterou generuje.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="f9cb1-120">V tomto příkladu nahradí `{name.ToUpper()}` s každým názvem, převedeny na velká <xref:System.String.ToUpper%2A> písmena, protože jste volali metodu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="f9cb1-121">Pojďme pokračovat v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="f9cb1-122">Změna obsahu seznamu</span><span class="sxs-lookup"><span data-stu-id="f9cb1-122">Modify list contents</span></span>

<span data-ttu-id="f9cb1-123">Kolekce, kterou jste <xref:System.Collections.Generic.List%601> vytvořili, používá typ.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="f9cb1-124">Tento typ ukládá sekvence prvků.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-124">This type stores sequences of elements.</span></span> <span data-ttu-id="f9cb1-125">Určete typ prvků mezi úhlovými závorkami.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="f9cb1-126">Jedním z důležitých aspektů tohoto <xref:System.Collections.Generic.List%601> typu je, že může zvětšit nebo zmenšit, což umožňuje přidat nebo odebrat prvky.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="f9cb1-127">Přidejte tento kód `}` před `Main` uzávěrkou v metodě:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="f9cb1-128">Přidali jste další dvě jména na konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="f9cb1-129">Také jste odstranili jeden stejně.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-129">You've also removed one as well.</span></span> <span data-ttu-id="f9cb1-130">Uložte soubor a `dotnet run` zadejte jej vyzkoušejte.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="f9cb1-131">Umožňuje <xref:System.Collections.Generic.List%601> odkazovat na jednotlivé položky podle **indexu.**</span><span class="sxs-lookup"><span data-stu-id="f9cb1-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="f9cb1-132">Umístíte index `[` mezi `]` a tokeny za název seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="f9cb1-133">C# používá 0 pro první index.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="f9cb1-134">Přidejte tento kód přímo pod kód, který jste právě přidali, a vyzkoušejte jej:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="f9cb1-135">Nelze získat přístup k indexu za konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="f9cb1-136">Mějte na paměti, že indexy začínají na 0, takže největší platný index je o jeden menší než počet položek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="f9cb1-137">Můžete zkontrolovat, jak dlouho seznam <xref:System.Collections.Generic.List%601.Count%2A> používá vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="f9cb1-138">Na konec metody Main přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="f9cb1-139">Uložte soubor a `dotnet run` znovu zadejte, abyste viděli výsledky.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="f9cb1-140">Hledání a řazení v seznamech</span><span class="sxs-lookup"><span data-stu-id="f9cb1-140">Search and sort lists</span></span>

<span data-ttu-id="f9cb1-141">Naše ukázky používají relativně malé seznamy, ale vaše aplikace mohou často vytvářet seznamy s mnoha dalšími prvky, někdy číslováním v tisících.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="f9cb1-142">Chcete-li najít prvky v těchto větších kolekcích, je třeba hledat v seznamu pro různé položky.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="f9cb1-143">Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> vyhledá položku a vrátí index položky.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="f9cb1-144">Přidejte tento kód na `Main` konec metody:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="f9cb1-145">Položky v seznamu lze také seřadit.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="f9cb1-146">Metoda <xref:System.Collections.Generic.List%601.Sort%2A> seřadí všechny položky v seznamu v normálním pořadí (abecedně v případě řetězců).</span><span class="sxs-lookup"><span data-stu-id="f9cb1-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="f9cb1-147">Přidejte tento kód na `Main` konec naší metody:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="f9cb1-148">Chcete-li vyzkoušet tuto nejnovější verzi, uložte soubor a zadejte. `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="f9cb1-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="f9cb1-149">Než začnete další část, přesuneme aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="f9cb1-150">To usnadňuje začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="f9cb1-151">Přejmenujte `Main` metodu na `WorkingWithStrings` `Main` a napište novou metodu, která volá `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="f9cb1-152">Po dokončení by měl váš kód vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-152">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="f9cb1-153">Seznamy jiných typů</span><span class="sxs-lookup"><span data-stu-id="f9cb1-153">Lists of other types</span></span>

<span data-ttu-id="f9cb1-154">Byl jste pomocí `string` typu v seznamech tak daleko.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="f9cb1-155">Pojďme udělat <xref:System.Collections.Generic.List%601> použití jiného typu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="f9cb1-156">Sestavíme sadu čísel.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="f9cb1-157">Přidejte na konec nové `Main` metody následující:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="f9cb1-158">To vytvoří seznam celá čísla a nastaví první dvě celá čísla na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="f9cb1-159">Jedná se o první dvě hodnoty *Fibonacciho sekvence*, posloupnost čísel.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="f9cb1-160">Každé další Fibonacciho číslo se najde součtem předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="f9cb1-161">Přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="f9cb1-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="f9cb1-162">Uložte soubor `dotnet run` a zadejte, abyste viděli výsledky.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="f9cb1-163">Chcete-li se soustředit pouze na tuto `WorkingWithStrings();`část, můžete zakomentovat kód, který volá .</span><span class="sxs-lookup"><span data-stu-id="f9cb1-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="f9cb1-164">Stačí dát `/` dvě postavy v přední `// WorkingWithStrings();`části hovoru, jako je tento: .</span><span class="sxs-lookup"><span data-stu-id="f9cb1-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="f9cb1-165">Úloha</span><span class="sxs-lookup"><span data-stu-id="f9cb1-165">Challenge</span></span>

<span data-ttu-id="f9cb1-166">Uvidíme, jestli můžete dát dohromady některé pojmy z této a dřívější lekce.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="f9cb1-167">Rozšiřte to, co jste dosud vytvořili s Fibonacciho čísly.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="f9cb1-168">Pokuste se napsat kód generovat prvních 20 čísel v pořadí.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="f9cb1-169">(Jako náznak, 20. Fibonacciho číslo je 6765.)</span><span class="sxs-lookup"><span data-stu-id="f9cb1-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="f9cb1-170">Dokončení výzvy</span><span class="sxs-lookup"><span data-stu-id="f9cb1-170">Complete challenge</span></span>

<span data-ttu-id="f9cb1-171">Ukázkové řešení můžete zobrazit na [hotový ukázkový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="f9cb1-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="f9cb1-172">S každou iteraci smyčky, budete mít poslední dvě celá čísla v seznamu, jejich sčítání a přidání této hodnoty do seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="f9cb1-173">Smyčka se opakuje, dokud do seznamu nepřidáte 20 položek.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="f9cb1-174">Gratulujeme, jste dokončili seznam tutorial.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="f9cb1-175">Můžete pokračovat s [úvod do tříd](introduction-to-classes.md) kurzu ve vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="f9cb1-176">Další informace o práci `List` s typem naleznete v tématu [průvodce .NET](../../../standard/index.md) o [kolekcích](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9cb1-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="f9cb1-177">Dozvíte se také o mnoha dalších typech kolekcí.</span><span class="sxs-lookup"><span data-stu-id="f9cb1-177">You'll also learn about many other collection types.</span></span>
