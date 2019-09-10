---
title: Větve a smyčky – Úvod k C# kurzu
description: V tomto kurzu o větvích a smyčkách napíšete C# kód pro zkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d329a871265ae42918fbf81c42be6667710e4c75
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850804"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="eb7eb-103">Další informace o podmíněné logice s příkazy větví a smyček</span><span class="sxs-lookup"><span data-stu-id="eb7eb-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="eb7eb-104">V tomto kurzu se naučíte, jak napsat kód, který kontroluje proměnné a mění cestu spuštění na základě těchto proměnných.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="eb7eb-105">Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="eb7eb-106">Kurz obsahuje řadu lekcí, které se seznámí s konstrukcemi větvení a smyček v C#.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="eb7eb-107">V těchto lekcích se naučíte základy C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="eb7eb-108">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="eb7eb-109">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="eb7eb-110">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="eb7eb-111">Rozhodnutí pomocí `if` příkazu</span><span class="sxs-lookup"><span data-stu-id="eb7eb-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="eb7eb-112">Vytvořte adresář s názvem **větve – kurz**.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="eb7eb-113">Zajistěte, aby byl aktuální `dotnet new console -n BranchesAndLoops -o .`adresář a běžel.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="eb7eb-114">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="eb7eb-115">V oblíbeném editoru otevřete **program.cs** a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="eb7eb-116">Tento kód zkuste zadat `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="eb7eb-117">Měla by se zobrazit zpráva "odpověď je větší než 10."</span><span class="sxs-lookup"><span data-stu-id="eb7eb-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="eb7eb-118">vytištěno do konzoly.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-118">printed to your console.</span></span>

<span data-ttu-id="eb7eb-119">Upravte deklaraci `b` tak, aby součet byl menší než 10:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="eb7eb-120">Zadejte `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-120">Type `dotnet run` again.</span></span> <span data-ttu-id="eb7eb-121">Vzhledem k tomu, že odpověď je menší než 10, nic se nevytiskne.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="eb7eb-122">**Podmínka** , kterou testujete, je nepravdivá.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="eb7eb-123">Nemáte žádný kód, který by bylo možné provést, protože jste zadali pouze jednu z možných větví pro `if` příkaz: jedinou větví.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="eb7eb-124">Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="eb7eb-125">Kompilátor najde a nahlásí chyby.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="eb7eb-126">Prohlédněte si úzce na výstupu chyby a kódu, který chybu generoval.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="eb7eb-127">Chyba kompilátoru může obvykle pomohly najít problém.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="eb7eb-128">Tento první příklad ukazuje sílu `if` a logické typy.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="eb7eb-129">*Logická hodnota* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="eb7eb-130">C#definuje speciální typ `bool` pro logické proměnné.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="eb7eb-131">Příkaz kontroluje hodnotu `bool`. `if`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="eb7eb-132">Pokud je `true`hodnota, příkaz `if` následující po spuštění.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="eb7eb-133">V opačném případě se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="eb7eb-134">Tento proces kontroly podmínek a provádění příkazů založených na těchto podmínkách je velmi výkonný.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="eb7eb-135">Nastavit, zda a jinak spolupracovat</span><span class="sxs-lookup"><span data-stu-id="eb7eb-135">Make if and else work together</span></span>

<span data-ttu-id="eb7eb-136">Chcete-li spustit jiný kód v větvích true i false, vytvořte `else` větev, která se spustí, když je podmínka nepravdivá.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="eb7eb-137">Zkuste to.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-137">Try this.</span></span> <span data-ttu-id="eb7eb-138">Přidejte poslední dva řádky v kódu níže do vaší `Main` metody (měli byste už mít první čtyři):</span><span class="sxs-lookup"><span data-stu-id="eb7eb-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="eb7eb-139">Příkaz následující `else` za klíčovým slovem se spustí pouze v případě, `false`že podmínka je testována.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="eb7eb-140">`if` Kombinování `else` a s logickými podmínkami poskytuje veškerou sílu, kterou `true` potřebujete ke `false` zpracování podmínky a.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb7eb-141">Odsazení pod `if` příkazy a `else` je pro lidské čtenáře.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="eb7eb-142">C# Jazyk nezpracovává odsazení ani prázdné znaky jako významné.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="eb7eb-143">Příkaz následující `if` za klíčovým `else` slovem nebo se spustí na základě podmínky.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="eb7eb-144">Všechny ukázky v tomto kurzu se řídí běžným postupem odsazení řádků na základě toku řízení příkazů.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="eb7eb-145">Vzhledem k tomu, že odsazení není důležité, je nutné `{` použít `}` a k označení, zda chcete, aby bylo více než jeden příkaz součástí bloku, který je spuštěn podmíněně.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="eb7eb-146">C#programátoři obvykle používají tyto složené závorky u `if` všech `else` klauzulí a.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="eb7eb-147">Následující příklad je stejný jako ten, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="eb7eb-148">Upravte kód výše tak, aby odpovídal následujícímu kódu:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="eb7eb-149">Ve zbývající části tohoto kurzu obsahuje ukázka kódu všechny složené závorky, a to po přijatých postupech.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="eb7eb-150">Můžete testovat složitější podmínky.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-150">You can test more complicated conditions.</span></span> <span data-ttu-id="eb7eb-151">Do své `Main` metody přidejte následující kód za dosud napsaný kód:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="eb7eb-152">Testy symbolů pro *rovnost.* `==`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="eb7eb-153">Použití `==` rozlišuje test pro rovnost z přiřazení, které jste viděli v `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="eb7eb-154">`&&` Představuje "a".</span><span class="sxs-lookup"><span data-stu-id="eb7eb-154">The `&&` represents "and".</span></span> <span data-ttu-id="eb7eb-155">To znamená, že obě podmínky musí mít hodnotu true, aby se příkaz spustil ve větvi true.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="eb7eb-156">Tyto příklady také ukazují, že můžete mít více příkazů v každé podmíněných větvích za předpokladu, `{` že `}`jsou uzavřeny v a.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="eb7eb-157">Můžete také použít `||` k reprezentaci "nebo".</span><span class="sxs-lookup"><span data-stu-id="eb7eb-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="eb7eb-158">Po tom, co jste napsali, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="eb7eb-159">Umožňuje `a`upravit hodnoty `||` , `b`a `c` a přepínat mezi `&&` a a prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="eb7eb-160">Získáte lepší znalosti o tom, jak `&&` operátory a `||` fungují.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="eb7eb-161">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-161">You've finished the first step.</span></span> <span data-ttu-id="eb7eb-162">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="eb7eb-163">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="eb7eb-164">Přejmenujte `ExploreIf` `Main` `ExploreIf`metodu na a napište novou metodu, která volá. `Main`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="eb7eb-165">Až budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="eb7eb-166">Zakomentujte volání do `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="eb7eb-167">Výsledkem je, že při práci v této části bude výstup méně zbytečný:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="eb7eb-168">Spustí komentář v C#. `//`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="eb7eb-169">Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="eb7eb-170">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="eb7eb-171">Opakování operací pomocí smyček</span><span class="sxs-lookup"><span data-stu-id="eb7eb-171">Use loops to repeat operations</span></span>

<span data-ttu-id="eb7eb-172">V této části použijete **smyčky** k opakování příkazů.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="eb7eb-173">Vyzkoušejte tento kód v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="eb7eb-174">Příkaz zkontroluje podmínku a spustí blok příkazu nebo příkazu `while`za. `while`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="eb7eb-175">Opakovaně kontroluje podmínku a spouští tyto příkazy, dokud podmínka nevrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="eb7eb-176">V tomto příkladu je druhý operátor New.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-176">There's one other new operator in this example.</span></span> <span data-ttu-id="eb7eb-177">Po proměnné je operátor **přírůstku.** `++` `counter`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="eb7eb-178">Přidá 1 k hodnotě `counter` a uloží tuto hodnotu `counter` do proměnné.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb7eb-179">Ujistěte se, že `while` se podmínka smyčky při spuštění kódu změní na false.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="eb7eb-180">V opačném případě vytvoříte **nekonečnou smyčku** , ve které program nikdy nekončí.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="eb7eb-181">To není v této ukázce znázorněno, protože je nutné vynutit ukončení programu pomocí **kombinace kláves CTRL-C** nebo jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="eb7eb-182">Smyčka testuje podmínku před spuštěním kódu `while`za. `while`</span><span class="sxs-lookup"><span data-stu-id="eb7eb-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="eb7eb-183">`do` ... `while` smyčka nejprve spustí kód a poté zkontroluje podmínku.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="eb7eb-184">Cyklus do while je zobrazen v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="eb7eb-185">Tato `do` smyčka a předchozí `while` smyčka vytvoří stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="eb7eb-186">Práce s cyklem for</span><span class="sxs-lookup"><span data-stu-id="eb7eb-186">Work with the for loop</span></span>

<span data-ttu-id="eb7eb-187">Smyčka **for** se běžně používá v C#.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="eb7eb-188">Vyzkoušejte tento kód v metodě Main ():</span><span class="sxs-lookup"><span data-stu-id="eb7eb-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="eb7eb-189">To funguje stejně jako `while` smyčka `do` a smyčka, kterou jste už použili.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="eb7eb-190">`for` Příkaz má tři části, které řídí, jak to funguje.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="eb7eb-191">První část je **pro inicializátor inicializátoru**: `int index = 0;` deklaruje, že `index` je proměnná smyčky, a nastaví její počáteční hodnotu na `0`.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="eb7eb-192">Střední část je **pro podmínku**: `index < 10` deklaruje, že se tato `for` smyčka pokračuje, dokud hodnota čítače není menší než 10.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="eb7eb-193">Poslední část je **for iterátor**: `index++` určuje, jak se má změnit proměnná smyčky po provedení bloku `for` po příkazu.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="eb7eb-194">V tomto případě určuje, `index` že se má při každém spuštění bloku zvýšit o 1.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="eb7eb-195">Vyzkoušejte si je sami.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-195">Experiment with these yourself.</span></span> <span data-ttu-id="eb7eb-196">Vyzkoušejte následující:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-196">Try each of the following:</span></span>

- <span data-ttu-id="eb7eb-197">Změňte inicializátor tak, aby začínal na jiné hodnotě.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="eb7eb-198">Změňte podmínku tak, aby se zastavila s jinou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="eb7eb-199">Až to budete mít, pojďme přejít k tomu, abyste si sami napsali kód, abyste mohli používat, co jste se naučili.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="eb7eb-200">Kombinování větví a smyček</span><span class="sxs-lookup"><span data-stu-id="eb7eb-200">Combine branches and loops</span></span>

<span data-ttu-id="eb7eb-201">Teď, když jste viděli `if` příkaz a konstruktory cyklů v C# jazyce, se podívejte, jestli můžete napsat C# kód, abyste našli součet všech celých čísel od 1 do 20, která jsou dělitelná 3.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="eb7eb-202">Tady je několik tipů:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-202">Here are a few hints:</span></span>

- <span data-ttu-id="eb7eb-203">`%` Operátor poskytuje zbytek operace dělení.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="eb7eb-204">`if` Příkaz poskytuje podmínku pro zjištění, zda číslo by mělo být součástí součtu.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="eb7eb-205">`for` Smyčka vám může pomáhat zopakovat řadu kroků pro všechna čísla od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="eb7eb-206">Vyzkoušejte si to sami.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-206">Try it yourself.</span></span> <span data-ttu-id="eb7eb-207">Potom zkontrolujte, jak jste to provedli.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-207">Then check how you did.</span></span> <span data-ttu-id="eb7eb-208">Měli byste pro odpověď získat 63.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-208">You should get 63 for an answer.</span></span> <span data-ttu-id="eb7eb-209">Můžete zobrazit jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="eb7eb-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="eb7eb-210">Dokončili jste kurz "větve a smyčky".</span><span class="sxs-lookup"><span data-stu-id="eb7eb-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="eb7eb-211">Kurz pro [pole a kolekce](arrays-and-collections.md) můžete pokračovat ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="eb7eb-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="eb7eb-212">Další informace o těchto konceptech najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="eb7eb-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="eb7eb-213">IF a else – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7eb-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="eb7eb-214">While – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7eb-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="eb7eb-215">Do – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7eb-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="eb7eb-216">Příkaz for</span><span class="sxs-lookup"><span data-stu-id="eb7eb-216">For statement</span></span>](../../language-reference/keywords/for.md)
