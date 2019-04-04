---
title: Větve a smyčky – Úvod do C# kurz
description: V tomto kurzu o větvích a smyčkách napíšete C# kódu syntaxi jazyka, který podporuje podmíněné větvení a smyček opakovaně spouštět příkazy.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: ad5891c11c516a7c5e3d46bea9c17c85b4a8536e
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920945"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="1de99-103">Další podmíněnou logiku s příkazy větve a smyčky</span><span class="sxs-lookup"><span data-stu-id="1de99-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="1de99-104">V tomto kurzu se naučíte, jak napsat kód, který vyhodnocuje proměnné a mění cestu provedení na základě těchto proměnných.</span><span class="sxs-lookup"><span data-stu-id="1de99-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="1de99-105">Napíšete kód v C# a zobrazovat výsledky kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="1de99-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="1de99-106">Tento kurz obsahuje sérii lekcí, které probírají konstrukty v větvení a smyček C#.</span><span class="sxs-lookup"><span data-stu-id="1de99-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="1de99-107">Tato lekce vás naučí základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1de99-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="1de99-108">V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="1de99-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="1de99-109">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="1de99-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="1de99-110">Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="1de99-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="1de99-111">Rozhodování pomocí `if` – příkaz</span><span class="sxs-lookup"><span data-stu-id="1de99-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="1de99-112">Vytvořte adresář **kurz větve**.</span><span class="sxs-lookup"><span data-stu-id="1de99-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="1de99-113">Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="1de99-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="1de99-114">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="1de99-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="1de99-115">Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1de99-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="1de99-116">Vyzkoušejte tento kód tak, že zadáte `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="1de99-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="1de99-117">Zobrazí se zpráva "odpověď je větší než 10."</span><span class="sxs-lookup"><span data-stu-id="1de99-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="1de99-118">vytiskne na konzolu.</span><span class="sxs-lookup"><span data-stu-id="1de99-118">printed to your console.</span></span>

<span data-ttu-id="1de99-119">Upravte deklaraci `b` tak, aby součet je menší než 10:</span><span class="sxs-lookup"><span data-stu-id="1de99-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="1de99-120">Typ `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="1de99-120">Type `dotnet run` again.</span></span> <span data-ttu-id="1de99-121">Protože odpověď je menší než 10, nic se nevytiskne.</span><span class="sxs-lookup"><span data-stu-id="1de99-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="1de99-122">**Podmínku** jste testování má hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="1de99-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="1de99-123">Nemáte žádný kód spustit, protože jste zatím napsali jenom jednu z možných větví `if` – příkaz: větev pro splnění podmínky.</span><span class="sxs-lookup"><span data-stu-id="1de99-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="1de99-124">Když se budete učit, C# (nebo libovolným programovacím jazykem), budete se při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="1de99-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="1de99-125">Kompilátor vyhledá a ohlásit chyby.</span><span class="sxs-lookup"><span data-stu-id="1de99-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="1de99-126">Prohlédněte si blíže chybový výstup a kód, který vytvořil chybu.</span><span class="sxs-lookup"><span data-stu-id="1de99-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="1de99-127">Chyba kompilátoru obvykle můžete nalezení příčiny problému.</span><span class="sxs-lookup"><span data-stu-id="1de99-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="1de99-128">Tento první příklad ukazuje sílu příkazu `if` a logických typů.</span><span class="sxs-lookup"><span data-stu-id="1de99-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="1de99-129">A *logická* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="1de99-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="1de99-130">C#definuje speciální typ `bool` pro proměnné typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="1de99-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="1de99-131">`if` Příkaz zkontroluje hodnotu vlastnosti `bool`.</span><span class="sxs-lookup"><span data-stu-id="1de99-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="1de99-132">Pokud je hodnotou `true`, příkazu za příkazem `if` spustí.</span><span class="sxs-lookup"><span data-stu-id="1de99-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="1de99-133">V opačném případě se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="1de99-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="1de99-134">Tento proces kontroly podmínek a provádění příkazů na základě těchto podmínek je velmi výkonné.</span><span class="sxs-lookup"><span data-stu-id="1de99-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="1de99-135">If a else spolupracují</span><span class="sxs-lookup"><span data-stu-id="1de99-135">Make if and else work together</span></span>

<span data-ttu-id="1de99-136">Chcete-li ve větvích true a false provést různý kód, vytvoříte `else` větev, která se provede, když podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="1de99-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="1de99-137">Vyzkoušejte to.</span><span class="sxs-lookup"><span data-stu-id="1de99-137">Try this.</span></span> <span data-ttu-id="1de99-138">Přidejte poslední dva řádky ve níže uvedeného kódu vaší `Main` – metoda (byste už měli mít první čtyři):</span><span class="sxs-lookup"><span data-stu-id="1de99-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="1de99-139">Následující příkaz `else` – klíčové slovo provede pouze, pokud je testovaná podmínka `false`.</span><span class="sxs-lookup"><span data-stu-id="1de99-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="1de99-140">Kombinování `if` a `else` s logickými podmínkami poskytuje veškerou sílu, bude potřeba zpracovat oba `true` a `false` podmínku.</span><span class="sxs-lookup"><span data-stu-id="1de99-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1de99-141">Důvodem odsazení pod `if` a `else` příkazy je snadnější čtení pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="1de99-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="1de99-142">Jazyk C# nepovažuje odsazení a mezery za významné.</span><span class="sxs-lookup"><span data-stu-id="1de99-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="1de99-143">Následující příkaz `if` nebo `else` – klíčové slovo se spustí na základě podmínky.</span><span class="sxs-lookup"><span data-stu-id="1de99-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="1de99-144">Všechny ukázky v tomto kurzu dodržují běžnou praxi odsazování řádků podle toku řízení příkazů.</span><span class="sxs-lookup"><span data-stu-id="1de99-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="1de99-145">Protože odsazení není významné, je třeba použít `{` a `}` označte, když má více než jeden výraz jako součást podmíněně prováděného bloku.</span><span class="sxs-lookup"><span data-stu-id="1de99-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="1de99-146">Programátoři v C# obvykle používají tyto složené závorky ve všech `if` a `else` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1de99-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="1de99-147">Následující příklad je stejný jako ten, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="1de99-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="1de99-148">Upravte kód tak, aby odpovídala následující kód výše:</span><span class="sxs-lookup"><span data-stu-id="1de99-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="1de99-149">Postupujte podle zbývajících kroků v tomto kurzu, patří ukázky složené závorky podle přijaté praxe.</span><span class="sxs-lookup"><span data-stu-id="1de99-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="1de99-150">Můžete testovat složitější podmínky.</span><span class="sxs-lookup"><span data-stu-id="1de99-150">You can test more complicated conditions.</span></span> <span data-ttu-id="1de99-151">Přidejte následující kód do vašeho `Main` za jste zatím napsali kód:</span><span class="sxs-lookup"><span data-stu-id="1de99-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

<span data-ttu-id="1de99-152">`&&` Představuje "a".</span><span class="sxs-lookup"><span data-stu-id="1de99-152">The `&&` represents "and".</span></span> <span data-ttu-id="1de99-153">Znamená to, že obě podmínky musí mít hodnotu true, má provést větev true.</span><span class="sxs-lookup"><span data-stu-id="1de99-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="1de99-154">Tyto příklady také ukazují, že můžete mít více příkazů v každé podmíněné větvi, je v uzavřete `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="1de99-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="1de99-155">Můžete také použít `||` představující "nebo".</span><span class="sxs-lookup"><span data-stu-id="1de99-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="1de99-156">Přidejte následující kód za co jste napsali zatím:</span><span class="sxs-lookup"><span data-stu-id="1de99-156">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

<span data-ttu-id="1de99-157">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="1de99-157">You've finished the first step.</span></span> <span data-ttu-id="1de99-158">Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="1de99-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="1de99-159">Který usnadňuje začít pracovat s nový příklad.</span><span class="sxs-lookup"><span data-stu-id="1de99-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="1de99-160">Přejmenovat váš `Main` metodu `ExploreIf` a napsat nový `Main` metodu, která volá `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="1de99-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="1de99-161">Jakmile budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1de99-161">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="1de99-162">Odkomentujte volání `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="1de99-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="1de99-163">Bude výstup, který zaplněný při práci v této části:</span><span class="sxs-lookup"><span data-stu-id="1de99-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="1de99-164">`//` Spustí **komentář** v C#.</span><span class="sxs-lookup"><span data-stu-id="1de99-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="1de99-165">Komentáře jsou jakýkoli text, který chcete ponechat ve zdrojovém kódu, ale nemůžou provést jako kód.</span><span class="sxs-lookup"><span data-stu-id="1de99-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="1de99-166">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="1de99-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="1de99-167">Použití smyček k opakování operací</span><span class="sxs-lookup"><span data-stu-id="1de99-167">Use loops to repeat operations</span></span>

<span data-ttu-id="1de99-168">V této části použijete **smyčky** k opakování příkazů.</span><span class="sxs-lookup"><span data-stu-id="1de99-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="1de99-169">Vyzkoušejte tento kód ve vašich `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1de99-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="1de99-170">`while` Příkaz zkontroluje podmínku a provede příkaz nebo blok příkazů následující `while`.</span><span class="sxs-lookup"><span data-stu-id="1de99-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="1de99-171">Opakovaně zkontroluje podmínku a provádět příkaz, dokud podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="1de99-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="1de99-172">V tomto příkladu je jeden nový operátor.</span><span class="sxs-lookup"><span data-stu-id="1de99-172">There's one other new operator in this example.</span></span> <span data-ttu-id="1de99-173">`++` Po `counter` proměnná je **přírůstek** operátor.</span><span class="sxs-lookup"><span data-stu-id="1de99-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="1de99-174">Přičte 1 k hodnotě z `counter` a uloží hodnotu v `counter` proměnné.</span><span class="sxs-lookup"><span data-stu-id="1de99-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1de99-175">Ujistěte se, že `while` smyčky změny stavu na hodnotu false, při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="1de99-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="1de99-176">V opačném případě můžete vytvořit **nekonečná smyčka** kde program nikdy neskončí.</span><span class="sxs-lookup"><span data-stu-id="1de99-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="1de99-177">Který není ukázáno v této ukázce, protože budete muset vynutit ukončení pomocí vašeho programu **CTRL-C** nebo jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1de99-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="1de99-178">`while` Smyčky otestuje podmínku před spuštěním kódu, který následuje `while`.</span><span class="sxs-lookup"><span data-stu-id="1de99-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="1de99-179">`do` ... `while` smyčky nejdřív spustí kód a potom zkontrolujte tuto podmínku.</span><span class="sxs-lookup"><span data-stu-id="1de99-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="1de99-180">Úkol, zatímco smyčky je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1de99-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="1de99-181">To `do` smyčky a dřívější `while` smyčky generovat stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="1de99-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="1de99-182">Práce s smyčka for</span><span class="sxs-lookup"><span data-stu-id="1de99-182">Work with the for loop</span></span>

<span data-ttu-id="1de99-183">**Pro** smyčky se běžně používá v C#.</span><span class="sxs-lookup"><span data-stu-id="1de99-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="1de99-184">Vyzkoušejte tento kód v metodě Main():</span><span class="sxs-lookup"><span data-stu-id="1de99-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="1de99-185">Funguje jako `while` smyčky a `do` smyčky, které jste už použili.</span><span class="sxs-lookup"><span data-stu-id="1de99-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="1de99-186">`for` Příkaz má tři části, které řídí, jak to funguje.</span><span class="sxs-lookup"><span data-stu-id="1de99-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="1de99-187">První část je **pro inicializátor**: `int index = 0;` deklaruje, že `index` je proměnná smyčky a nastavuje její počáteční hodnotu `0`.</span><span class="sxs-lookup"><span data-stu-id="1de99-187">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="1de99-188">Prostřední část je **pro podmínku**: `index < 10` deklaruje, že tento `for` smyčky pokračuje v provádění za předpokladu, hodnota čítače je menší než 10.</span><span class="sxs-lookup"><span data-stu-id="1de99-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="1de99-189">Poslední část je **iterátoru**: `index++` Určuje, jak upravit proměnnou smyčky po provedení bloku následujícího `for` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1de99-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="1de99-190">V tomto poli, určuje, že `index` měli zvyšuje o 1 při každém provedení bloku.</span><span class="sxs-lookup"><span data-stu-id="1de99-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="1de99-191">Vyzkoušet sami.</span><span class="sxs-lookup"><span data-stu-id="1de99-191">Experiment with these yourself.</span></span> <span data-ttu-id="1de99-192">Vyzkoušejte všechny z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="1de99-192">Try each of the following:</span></span>

- <span data-ttu-id="1de99-193">Změňte inicializační začínal jinou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="1de99-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="1de99-194">Změňte podmínku, která má zastavit na jinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1de99-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="1de99-195">Až skončíte, přejdeme napsali kus kódu sami používat, co jste se naučili.</span><span class="sxs-lookup"><span data-stu-id="1de99-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="1de99-196">Kombinace větví a smyček</span><span class="sxs-lookup"><span data-stu-id="1de99-196">Combine branches and loops</span></span>

<span data-ttu-id="1de99-197">Teď, když už víte, `if` příkazu a konstruktory cyklů v jazyce C# najdete v části Pokud můžete napsat kód jazyka C# pro zjistí součet všech celých čísel od 1 do 20, která jsou dělitelná 3.</span><span class="sxs-lookup"><span data-stu-id="1de99-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="1de99-198">Tady je několik tipů:</span><span class="sxs-lookup"><span data-stu-id="1de99-198">Here are a few hints:</span></span>

- <span data-ttu-id="1de99-199">`%` Operátor poskytuje zbytek operace dělení.</span><span class="sxs-lookup"><span data-stu-id="1de99-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="1de99-200">`if` Příkaz poskytuje podmínku pro zjištění, pokud se číslo by mělo být součástí tohoto součtu.</span><span class="sxs-lookup"><span data-stu-id="1de99-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="1de99-201">`for` Smyčky pomůže zopakovat sérii kroků pro všechna čísla od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="1de99-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="1de99-202">Vyzkoušejte si to sami.</span><span class="sxs-lookup"><span data-stu-id="1de99-202">Try it yourself.</span></span> <span data-ttu-id="1de99-203">Zkontrolujte, jak jste to udělali.</span><span class="sxs-lookup"><span data-stu-id="1de99-203">Then check how you did.</span></span> <span data-ttu-id="1de99-204">Měli byste obdržet 63 pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="1de99-204">You should get 63 for an answer.</span></span> <span data-ttu-id="1de99-205">Zobrazí jednu možnou odpověď podle [zobrazení dokončené kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="1de99-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="1de99-206">Dokončili jste kurz "větve a smyčky".</span><span class="sxs-lookup"><span data-stu-id="1de99-206">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="1de99-207">Můžete pokračovat [pole a kolekce](arrays-and-collections.md) kurz ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="1de99-207">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="1de99-208">Další informace o těchto konceptech v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="1de99-208">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="1de99-209">Pokud a else – příkaz</span><span class="sxs-lookup"><span data-stu-id="1de99-209">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="1de99-210">While – příkaz</span><span class="sxs-lookup"><span data-stu-id="1de99-210">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="1de99-211">Do – příkaz</span><span class="sxs-lookup"><span data-stu-id="1de99-211">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="1de99-212">For – příkaz</span><span class="sxs-lookup"><span data-stu-id="1de99-212">For statement</span></span>](../../language-reference/keywords/for.md)
