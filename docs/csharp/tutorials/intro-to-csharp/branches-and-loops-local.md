---
title: Větve a smyčky – Úvod do kurzu jazyka C#
description: V tomto kurzu o větvích a smyčkách napíšete kód v jazyce C# pro zkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d8c10a7462b7c27c5353aee6d957732a8d161015
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135942"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="d7e5f-103">Další informace o podmíněné logice s příkazy větví a smyček</span><span class="sxs-lookup"><span data-stu-id="d7e5f-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="d7e5f-104">V tomto kurzu se naučíte, jak napsat kód, který kontroluje proměnné a mění cestu spuštění na základě těchto proměnných.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="d7e5f-105">Napíšete kód v jazyce C# a zobrazíte výsledky jeho kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="d7e5f-106">Kurz obsahuje řadu lekcí, které se seznámí s konstrukcemi větvení a smyček v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="d7e5f-107">V těchto kurzech se seznámíte se základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="d7e5f-108">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="d7e5f-109">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="d7e5f-110">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="d7e5f-111">Rozhodnutí pomocí `if` příkazu</span><span class="sxs-lookup"><span data-stu-id="d7e5f-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="d7e5f-112">Vytvořte adresář s názvem *větve – kurz*.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="d7e5f-113">Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="d7e5f-114">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="d7e5f-115">V oblíbeném editoru otevřete *program.cs* a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="d7e5f-116">Tento kód zkuste zadat `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="d7e5f-117">Měla by se zobrazit zpráva "odpověď je větší než 10."</span><span class="sxs-lookup"><span data-stu-id="d7e5f-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="d7e5f-118">vytištěno do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-118">printed to your console.</span></span>

<span data-ttu-id="d7e5f-119">Upravte deklaraci `b`, aby součet byl menší než 10:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="d7e5f-120">Zadejte `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-120">Type `dotnet run` again.</span></span> <span data-ttu-id="d7e5f-121">Protože odpověď je menší než 10, nic se nevytiskne.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="d7e5f-122">Testovaná **podmínka** není splněná.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="d7e5f-123">Nemáte žádný kód, který by bylo možné provést, protože jste zatím napsali jenom jednu z možných větví příkazu `if`: větev pro splnění podmínky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="d7e5f-124">Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="d7e5f-125">Kompilátor najde a nahlásí chyby.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="d7e5f-126">Prohlédněte si úzce na výstupu chyby a kódu, který chybu generoval.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="d7e5f-127">Chyba kompilátoru může obvykle pomohly najít problém.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="d7e5f-128">Tento první příklad ukazuje sílu `if` a logické typy.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="d7e5f-129">*Logická hodnota* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="d7e5f-130">Jazyk C# definuje speciální typ `bool` pro logické proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="d7e5f-131">Příkaz `if` kontroluje hodnotu typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="d7e5f-132">Pokud je tato hodnota `true`, provede se příkaz následující za `if`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="d7e5f-133">V opačném případě se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="d7e5f-134">Tento proces kontroly podmínek a provádění příkazů na základě těchto podmínek je velmi účinný.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="d7e5f-135">Spolupráce if a else</span><span class="sxs-lookup"><span data-stu-id="d7e5f-135">Make if and else work together</span></span>

<span data-ttu-id="d7e5f-136">Chcete-li ve větvích True a False provést různý kód, vytvoříte větev `else`, která se provede, když podmínka není splněná.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="d7e5f-137">Zkuste to.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-137">Try this.</span></span> <span data-ttu-id="d7e5f-138">Přidejte poslední dva řádky v kódu níže do vaší `Main` metody (měli byste už mít první čtyři):</span><span class="sxs-lookup"><span data-stu-id="d7e5f-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="d7e5f-139">Příkaz následující za klíčovým slovem `else` se provede jen tehdy, když má testovaná podmínka hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="d7e5f-140">`if` Kombinování `else` a s logickými podmínkami poskytuje veškerou sílu, kterou potřebujete ke `true` zpracování `false` podmínky a.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7e5f-141">Důvodem odsazení pod příkazy `if` a `else` je snadnější čtení pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="d7e5f-142">Jazyk C# nezpracovává odsazení ani prázdné znaky jako významné.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="d7e5f-143">Příkaz následující za klíčovým slovem `if` nebo `else` se provede na základě podmínky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="d7e5f-144">Všechny ukázky v tomto kurzu se řídí běžným postupem odsazení řádků na základě toku řízení příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="d7e5f-145">Protože odsazení není významné, je potřeba pomocí `{` a `}` vyznačit, když chcete, aby jako součást podmíněně prováděného bloku bylo víc příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="d7e5f-146">Programátoři v C# obvykle používají tyto složené závorky pro všechny klauzule `if` a `else`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="d7e5f-147">Následující příklad je stejný jako ten, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="d7e5f-148">Upravte kód výše tak, aby odpovídal následujícímu kódu:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="d7e5f-149">Ve zbývající části tohoto kurzu obsahuje ukázka kódu všechny složené závorky, a to po přijatých postupech.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="d7e5f-150">Můžete testovat složitější podmínky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-150">You can test more complicated conditions.</span></span> <span data-ttu-id="d7e5f-151">Do své `Main` metody přidejte následující kód za dosud napsaný kód:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="d7e5f-152">Testy `==` symbolů pro *rovnost*.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="d7e5f-153">Použití `==` rozlišuje test pro rovnost z přiřazení, které jste viděli v `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="d7e5f-154">Zápis `&&` představuje „a zároveň“.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-154">The `&&` represents "and".</span></span> <span data-ttu-id="d7e5f-155">To znamená, že když se má provést větev True, musí být splněny obě podmínky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="d7e5f-156">Tyto příklady také ukazují, že můžete mít v každé podmíněné větvi víc příkazů, pokud je uzavřete mezi `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="d7e5f-157">Můžete také použít `||` k reprezentaci "nebo".</span><span class="sxs-lookup"><span data-stu-id="d7e5f-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="d7e5f-158">Po tom, co jste napsali, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="d7e5f-159">Umožňuje upravit hodnoty `a`, `b`a `c` a přepínat mezi `&&` a `||` a prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="d7e5f-160">Získáte lepší znalosti o tom, jak operátory `&&` a `||` fungují.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="d7e5f-161">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-161">You've finished the first step.</span></span> <span data-ttu-id="d7e5f-162">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="d7e5f-163">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="d7e5f-164">Přejmenujte `Main` metodu `ExploreIf` na a napište novou `Main` metodu, která `ExploreIf`volá.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="d7e5f-165">Až budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="d7e5f-166">Zakomentujte volání do `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="d7e5f-167">Výsledkem je, že při práci v této části bude výstup méně zbytečný:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="d7e5f-168">`//` Spustí **Komentář** v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="d7e5f-169">Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="d7e5f-170">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="d7e5f-171">Použití smyček k opakování operací</span><span class="sxs-lookup"><span data-stu-id="d7e5f-171">Use loops to repeat operations</span></span>

<span data-ttu-id="d7e5f-172">V této části použijete **smyčky** k opakování příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="d7e5f-173">Vyzkoušejte tento kód v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="d7e5f-174">`while` Příkaz zkontroluje podmínku a spustí blok příkazu nebo příkazu za `while`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="d7e5f-175">Opakovaně kontroluje podmínku a spouští tyto příkazy, dokud podmínka nevrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="d7e5f-176">V tomto příkladu je ještě jeden nový operátor.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-176">There's one other new operator in this example.</span></span> <span data-ttu-id="d7e5f-177">Zápis `++` za proměnnou `counter` je operátor **inkrementace**.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="d7e5f-178">Přidá 1 k hodnotě `counter` a uloží tuto hodnotu do `counter` proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7e5f-179">Ujistěte se, že `while` se podmínka smyčky při spuštění kódu změní na false.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="d7e5f-180">Jinak vytvoříte **nekonečnou smyčku**, ve které program nikdy neskončí.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="d7e5f-181">To není v této ukázce znázorněno, protože je nutné vynutit ukončení programu pomocí **kombinace kláves CTRL-C** nebo jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="d7e5f-182">Smyčka `while` otestuje podmínku před spuštěním kódu, který následuje za `while`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="d7e5f-183">Smyčka `do` ... `while` nejdřív spustí kód a potom zkontrolujte tuto podmínku.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="d7e5f-184">Cyklus do while je zobrazen v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="d7e5f-185">Tato `do` smyčka a předchozí `while` smyčka vytvoří stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="d7e5f-186">Práce se smyčkou for</span><span class="sxs-lookup"><span data-stu-id="d7e5f-186">Work with the for loop</span></span>

<span data-ttu-id="d7e5f-187">Smyčka **for** se běžně používá v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="d7e5f-188">Vyzkoušejte tento kód v metodě Main ():</span><span class="sxs-lookup"><span data-stu-id="d7e5f-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="d7e5f-189">Dělá to samé jako smyčky `while` a `do`, které jste už použili.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="d7e5f-190">Příkaz `for` má tři části, které řídí jeho fungování.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="d7e5f-191">První část je **pro inicializátor inicializátoru**: `int index = 0;` deklaruje, že `index` je proměnná smyčky, a nastaví její počáteční hodnotu na `0`.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="d7e5f-192">Střední část je **pro podmínku**: `index < 10` deklaruje, že se tato `for` smyčka pokračuje, dokud hodnota čítače není menší než 10.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="d7e5f-193">Poslední část je **for iterátor**: `index++` určuje, jak se má změnit proměnná smyčky po provedení bloku po `for` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="d7e5f-194">V tomto případě určuje, že `index` se má po každém provedení bloku zvýšit o 1.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="d7e5f-195">Zkuste si s touto ukázkou zaexperimentovat.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-195">Experiment with these yourself.</span></span> <span data-ttu-id="d7e5f-196">Vyzkoušejte všechny následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-196">Try each of the following:</span></span>

- <span data-ttu-id="d7e5f-197">Změňte inicializační výraz, aby začínal jinou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="d7e5f-198">Změňte podmínku tak, aby se zastavila při jiné hodnotě.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="d7e5f-199">Až skončíte, přejdeme k tomu, abyste si vyzkoušeli, co jste se naučili, a napsali kus kódu sami.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="d7e5f-200">Vytvořené vnořené smyčky</span><span class="sxs-lookup"><span data-stu-id="d7e5f-200">Created nested loops</span></span>

<span data-ttu-id="d7e5f-201">Smyčka `do` or `for` může být vnořena uvnitř jiné smyčky `while`, aby bylo možné vytvořit matici pomocí kombinace každé položky ve vnějším cyklu s každou položkou uvnitř vnitřní smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-201">A `while`, `do` or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="d7e5f-202">Pojďme to udělat pro sestavení sady alfanumerických párů reprezentujících řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-202">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="d7e5f-203">Jedna `for` smyčka může vygenerovat řádky:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-203">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="d7e5f-204">Další smyčka může vygenerovat sloupce:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-204">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="d7e5f-205">Můžete vnořit jednu smyčku dovnitř do dvojice formulářů:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-205">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="d7e5f-206">Můžete vidět, že vnější smyčka se jednou zvýší pro každé úplné spuštění vnitřní smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-206">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="d7e5f-207">Zaměnit vnořování řádků a sloupců a Prohlédněte si změny sami.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-207">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="d7e5f-208">Kombinace větví a smyček</span><span class="sxs-lookup"><span data-stu-id="d7e5f-208">Combine branches and loops</span></span>

<span data-ttu-id="d7e5f-209">Teď když jste viděli příkaz `if` a konstruktory cyklů v jazyce C#, zkuste, jestli dokážete v jazyce C# napsat kód, který zjistí součet všech celých čísel od 1 do 20, která jsou dělitelná 3.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-209">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="d7e5f-210">Tady je několik tipů:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-210">Here are a few hints:</span></span>

- <span data-ttu-id="d7e5f-211">Operátor `%` vrací zbytek po operaci dělení.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-211">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="d7e5f-212">Příkaz `if` poskytuje podmínku pro zjištění, jestli konkrétní číslo má být součástí tohoto součtu.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-212">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="d7e5f-213">Smyčka `for` pomůže zopakovat sérii kroků pro všechna čísla od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-213">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="d7e5f-214">Vyzkoušejte si to sami.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-214">Try it yourself.</span></span> <span data-ttu-id="d7e5f-215">A potom se podívejte, jak jste si vedli.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-215">Then check how you did.</span></span> <span data-ttu-id="d7e5f-216">Měli byste pro odpověď získat 63.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-216">You should get 63 for an answer.</span></span> <span data-ttu-id="d7e5f-217">Můžete zobrazit jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="d7e5f-217">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="d7e5f-218">Dokončili jste kurz "větve a smyčky".</span><span class="sxs-lookup"><span data-stu-id="d7e5f-218">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="d7e5f-219">Kurz pro [pole a kolekce](arrays-and-collections.md) můžete pokračovat ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-219">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="d7e5f-220">Více se o těchto konceptech dozvíte v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="d7e5f-220">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="d7e5f-221">Příkaz If a else</span><span class="sxs-lookup"><span data-stu-id="d7e5f-221">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="d7e5f-222">While – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7e5f-222">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="d7e5f-223">Příkaz Do</span><span class="sxs-lookup"><span data-stu-id="d7e5f-223">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="d7e5f-224">Příkaz for</span><span class="sxs-lookup"><span data-stu-id="d7e5f-224">For statement</span></span>](../../language-reference/keywords/for.md)
