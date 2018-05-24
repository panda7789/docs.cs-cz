---
title: Kurz větve a smyčky – C# místní – elementy QuickStart
description: V tento rychlý start o větve a smyčky můžete napsat kód C# a prozkoumejte syntaxi jazyka, která podporuje podmíněného větvení a smyčky provést příkazy opakovaně.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: a25ea7f266405a017f6f4576659195b2ac1afbf4
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="branches-and-loops"></a><span data-ttu-id="beeff-103">Větve a smyčky</span><span class="sxs-lookup"><span data-stu-id="beeff-103">Branches and loops</span></span>

<span data-ttu-id="beeff-104">Tento rychlý start se naučíte, jak napsat kód, který hledá proměnné a změní cesta spuštění na základě těchto proměnných.</span><span class="sxs-lookup"><span data-stu-id="beeff-104">This quickstart teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="beeff-105">Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="beeff-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="beeff-106">Rychlý Start obsahuje řadu lekce, které prozkoumat větvení a opakování ve smyčce konstrukce v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="beeff-106">The quickstart contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="beeff-107">Tyto poznatky získají naučit základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="beeff-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="beeff-108">Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="beeff-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="beeff-109">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="beeff-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="beeff-110">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="beeff-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="beeff-111">Rozhodnutí, pomocí `if` – příkaz</span><span class="sxs-lookup"><span data-stu-id="beeff-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="beeff-112">Vytvořte adresář s názvem **větví – rychlý Start**.</span><span class="sxs-lookup"><span data-stu-id="beeff-112">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="beeff-113">Ujistěte, že aktuální adresář a spusťte `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="beeff-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="beeff-114">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="beeff-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="beeff-115">Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.Writeline("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="beeff-115">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="beeff-116">Zkuste tento kód zadáním `dotnet run` v vaše okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="beeff-116">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="beeff-117">Zobrazí se zpráva "odpověď je větší než 10."</span><span class="sxs-lookup"><span data-stu-id="beeff-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="beeff-118">vytištěny konzole.</span><span class="sxs-lookup"><span data-stu-id="beeff-118">printed to your console.</span></span>

<span data-ttu-id="beeff-119">Upravit deklaraci `b` tak, aby součet menší než 10:</span><span class="sxs-lookup"><span data-stu-id="beeff-119">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="beeff-120">Typ `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="beeff-120">Type `dotnet run` again.</span></span> <span data-ttu-id="beeff-121">Protože odpověď je menší než 10, nic vytisknout.</span><span class="sxs-lookup"><span data-stu-id="beeff-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="beeff-122">**Podmínku** jste testování je false.</span><span class="sxs-lookup"><span data-stu-id="beeff-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="beeff-123">Nemáte žádný kód provést, protože jste zapsat pouze jedním z možných větve pro `if` příkaz: true větev.</span><span class="sxs-lookup"><span data-stu-id="beeff-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="beeff-124">Jak můžete prozkoumat jazyka C# (nebo žádný programovací jazyk), uděláte budete chyby při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="beeff-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="beeff-125">Kompilátor vyhledá a ohlásit chyby.</span><span class="sxs-lookup"><span data-stu-id="beeff-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="beeff-126">Prohlédněte si blíže výstup chyba a kód, který vytvořil chybu.</span><span class="sxs-lookup"><span data-stu-id="beeff-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="beeff-127">Chyba kompilátoru obvykle vám může pomoci najít problém.</span><span class="sxs-lookup"><span data-stu-id="beeff-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="beeff-128">Tento první příklad ukazuje možnosti `if` a Boolean typy.</span><span class="sxs-lookup"><span data-stu-id="beeff-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="beeff-129">A *Boolean* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="beeff-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="beeff-130">C# definuje speciální typ `bool` pro logická hodnota proměnné.</span><span class="sxs-lookup"><span data-stu-id="beeff-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="beeff-131">`if` Příkaz kontroluje hodnotu `bool`.</span><span class="sxs-lookup"><span data-stu-id="beeff-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="beeff-132">Pokud je hodnota `true`, následující příkaz `if` provede.</span><span class="sxs-lookup"><span data-stu-id="beeff-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="beeff-133">Jinak se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="beeff-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="beeff-134">Tento proces probíhá kontrola podmínky a provádění příkazů na základě těchto podmínek je velice mocný nástroj.</span><span class="sxs-lookup"><span data-stu-id="beeff-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="beeff-135">Ujistěte se, pokud a jinak spolupracují</span><span class="sxs-lookup"><span data-stu-id="beeff-135">Make if and else work together</span></span>

<span data-ttu-id="beeff-136">Ke spouštění různých kódu v true a false větve, vytvoříte `else` firemní pobočky, který provede, když je podmínka vyhodnocena jako false.</span><span class="sxs-lookup"><span data-stu-id="beeff-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="beeff-137">Zkuste to.</span><span class="sxs-lookup"><span data-stu-id="beeff-137">Try this.</span></span> <span data-ttu-id="beeff-138">Přidejte poslední dva řádky v kódu níže na vaše `Main` – metoda (byste již měli mít první čtyři):</span><span class="sxs-lookup"><span data-stu-id="beeff-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="beeff-139">Následující příkaz `else` – klíčové slovo provede pouze, pokud je podmínka testuje `false`.</span><span class="sxs-lookup"><span data-stu-id="beeff-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="beeff-140">Kombinování `if` a `else` s logickou hodnotu podmínky poskytuje všechny možnosti je nutné zpracovat oba `true` a `false` podmínku.</span><span class="sxs-lookup"><span data-stu-id="beeff-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="beeff-141">Odsazení pod `if` a `else` příkazy je pro lidské čtečky.</span><span class="sxs-lookup"><span data-stu-id="beeff-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="beeff-142">Jazyk C# nepodporuje považovat za odsazení nebo mezer významné.</span><span class="sxs-lookup"><span data-stu-id="beeff-142">The C# language doesn't treat indentation or white space as significant.</span></span> <span data-ttu-id="beeff-143">Následující příkaz `if` nebo `else` – klíčové slovo bude proveden podle stavu.</span><span class="sxs-lookup"><span data-stu-id="beeff-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="beeff-144">Všechny ukázky tento rychlý start podle běžnou praxí odsazovat řádky založené na toku řízení příkazů.</span><span class="sxs-lookup"><span data-stu-id="beeff-144">All the samples in this quickstart follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="beeff-145">Protože odsazení není důležité, budete muset použít `{` a `}` označte, když má více než jeden příkaz, který má být součástí blok, který provede podmíněně.</span><span class="sxs-lookup"><span data-stu-id="beeff-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="beeff-146">Programátory v jazyce C# obvykle používají tyto složené závorky na všech `if` a `else` klauzule.</span><span class="sxs-lookup"><span data-stu-id="beeff-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="beeff-147">Následující příklad je stejný jako ten, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="beeff-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="beeff-148">Upravte kód výše tak, aby odpovídala následující kód:</span><span class="sxs-lookup"><span data-stu-id="beeff-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="beeff-149">Procházení zbytku tento rychlý start, ukázky kódu, všechny zahrnují složené závorky, následující přijata postupy.</span><span class="sxs-lookup"><span data-stu-id="beeff-149">Through the rest of this quickstart, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="beeff-150">Složitější podmínky můžete otestovat.</span><span class="sxs-lookup"><span data-stu-id="beeff-150">You can test more complicated conditions.</span></span> <span data-ttu-id="beeff-151">Přidejte následující kód ve vaší `Main` po napsání dosavadní kódu:</span><span class="sxs-lookup"><span data-stu-id="beeff-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="beeff-152">`&&` Představuje "a".</span><span class="sxs-lookup"><span data-stu-id="beeff-152">The `&&` represents "and".</span></span> <span data-ttu-id="beeff-153">Znamená to, že musí být splněny příkaz nelze provést ve větvi true obě podmínky.</span><span class="sxs-lookup"><span data-stu-id="beeff-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="beeff-154">Tyto příklady také ukazují, že můžete mít více příkazů v každé větve podmíněného zadaný uzavřete je v `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="beeff-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="beeff-155">Můžete také použít `||` představují "nebo".</span><span class="sxs-lookup"><span data-stu-id="beeff-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="beeff-156">Přidejte následující kód po co jste vytvořili, pokud:</span><span class="sxs-lookup"><span data-stu-id="beeff-156">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="beeff-157">Prvním krokem dokončíte.</span><span class="sxs-lookup"><span data-stu-id="beeff-157">You've finished the first step.</span></span> <span data-ttu-id="beeff-158">Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="beeff-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="beeff-159">Který usnadňuje začít pracovat s novou příklad.</span><span class="sxs-lookup"><span data-stu-id="beeff-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="beeff-160">Přejmenujte vaše `Main` metodu `ExploreIf` a zápis nový `Main` metoda, která volá `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="beeff-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="beeff-161">Po dokončení, váš kód by měl vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="beeff-161">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="beeff-162">Komentář volání `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="beeff-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="beeff-163">To bude dávat výstup, který menší zaplněny, při práci v této části:</span><span class="sxs-lookup"><span data-stu-id="beeff-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="beeff-164">`//` Spustí **komentář** v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="beeff-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="beeff-165">Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nemůžou provést jako kód.</span><span class="sxs-lookup"><span data-stu-id="beeff-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="beeff-166">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="beeff-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="beeff-167">Používat smyčky opakování operace</span><span class="sxs-lookup"><span data-stu-id="beeff-167">Use loops to repeat operations</span></span>

<span data-ttu-id="beeff-168">V této části můžete použít **smyčky** opakování příkazy.</span><span class="sxs-lookup"><span data-stu-id="beeff-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="beeff-169">Zkuste tento kód ve vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="beeff-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="beeff-170">`while` Příkaz kontroluje podmínku a spustí příkaz nebo blok příkazu následující `while`.</span><span class="sxs-lookup"><span data-stu-id="beeff-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="beeff-171">Opakovaně kontroluje podmínku a provádění tyto příkazy, dokud je podmínka vyhodnocena jako false.</span><span class="sxs-lookup"><span data-stu-id="beeff-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="beeff-172">V tomto příkladu je jeden další nové operátor.</span><span class="sxs-lookup"><span data-stu-id="beeff-172">There's one other new operator in this example.</span></span> <span data-ttu-id="beeff-173">`++` Po `counter` proměnná **přírůstek** operátor.</span><span class="sxs-lookup"><span data-stu-id="beeff-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="beeff-174">Přidá 1 na hodnotu `counter` a uloží tuto hodnotu v `counter` proměnné.</span><span class="sxs-lookup"><span data-stu-id="beeff-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="beeff-175">Ujistěte se, že `while` cykly změny stavu na hodnotu false, při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="beeff-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="beeff-176">Jinak, vytvoříte **nekonečná smyčka** které nikdy končí vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="beeff-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="beeff-177">Který není ukázáno v této ukázce, protože budete muset vynutit ukončení pomocí vašeho programu **CTRL-C** nebo jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="beeff-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="beeff-178">`while` Smyčky testuje podmínku před provedením následující kód `while`.</span><span class="sxs-lookup"><span data-stu-id="beeff-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="beeff-179">`do` ... `while` smyček nejprve spustí kód a pak kontroluje podmínku.</span><span class="sxs-lookup"><span data-stu-id="beeff-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="beeff-180">Proveďte při smyčky je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="beeff-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="beeff-181">To `do` smyčky a dříve `while` smyčky poskytnou stejný výsledek.</span><span class="sxs-lookup"><span data-stu-id="beeff-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="beeff-182">Pracovat smyčky for</span><span class="sxs-lookup"><span data-stu-id="beeff-182">Work with the for loop</span></span>

<span data-ttu-id="beeff-183">**Pro** smyčky se často používá v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="beeff-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="beeff-184">Zkuste tento kód ve své metodě Main():</span><span class="sxs-lookup"><span data-stu-id="beeff-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="beeff-185">Funguje jako `while` smyčky a `do` smyčky jste už použili.</span><span class="sxs-lookup"><span data-stu-id="beeff-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="beeff-186">`for` Příkaz má tři části, které řídí, jak to funguje.</span><span class="sxs-lookup"><span data-stu-id="beeff-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="beeff-187">První část je **pro inicializátoru**: `for index = 0;` uvádí, že `index` je proměnná smyčky a nastaví počáteční hodnoty `0`.</span><span class="sxs-lookup"><span data-stu-id="beeff-187">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="beeff-188">Střední část je **pro podmínku**: `index < 10` deklaruje, že tato `for` smyčce bude pokračovat v provádění, dokud hodnota čítače je menší než 10.</span><span class="sxs-lookup"><span data-stu-id="beeff-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="beeff-189">Poslední část je **pro iterator**: `index++` Určuje, jak upravit proměnnou smyčky po provedení těchto bloku `for` příkaz.</span><span class="sxs-lookup"><span data-stu-id="beeff-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="beeff-190">Zde, určuje, že `index` by se zvýší o 1 pokaždé, když provádí bloku.</span><span class="sxs-lookup"><span data-stu-id="beeff-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="beeff-191">Experimentujte s sami.</span><span class="sxs-lookup"><span data-stu-id="beeff-191">Experiment with these yourself.</span></span> <span data-ttu-id="beeff-192">Zkuste každou z následujících:</span><span class="sxs-lookup"><span data-stu-id="beeff-192">Try each of the following:</span></span>

- <span data-ttu-id="beeff-193">Změňte inicializátoru spustit na jinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="beeff-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="beeff-194">Změňte stav kdykoli zastavit jinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="beeff-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="beeff-195">Když jste hotovi, můžeme přesunout k zápisu některé sami používat co když jste se naučili kódu.</span><span class="sxs-lookup"><span data-stu-id="beeff-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="beeff-196">Kombinace větví a smyčky</span><span class="sxs-lookup"><span data-stu-id="beeff-196">Combine branches and loops</span></span>

<span data-ttu-id="beeff-197">Teď, když jste viděli `if` prohlášení a opakování konstrukce v jazyce C#, najdete v části Pokud můžete napsat kód C# k vyhledání součet všech celá čísla 1 až 20, které jsou dělitelná 3.</span><span class="sxs-lookup"><span data-stu-id="beeff-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="beeff-198">Tady je několik pomocných parametrů:</span><span class="sxs-lookup"><span data-stu-id="beeff-198">Here are a few hints:</span></span>

- <span data-ttu-id="beeff-199">`%` Operátor vám dává zbytek operace dělení.</span><span class="sxs-lookup"><span data-stu-id="beeff-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="beeff-200">`if` Příkaz vám dává stav chcete zobrazit, pokud číslo musí být součástí součet.</span><span class="sxs-lookup"><span data-stu-id="beeff-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="beeff-201">`for` Smyčky vám může pomoct opakujte sérii kroků pro všechna čísla 1 až 20.</span><span class="sxs-lookup"><span data-stu-id="beeff-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="beeff-202">Vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="beeff-202">Try it yourself.</span></span> <span data-ttu-id="beeff-203">Potom zkontrolujte, jak jste to udělali.</span><span class="sxs-lookup"><span data-stu-id="beeff-203">Then check how you did.</span></span> <span data-ttu-id="beeff-204">Měli byste obdržet 63 pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="beeff-204">You should get 63 for an answer.</span></span> <span data-ttu-id="beeff-205">Zobrazí jednu možnou odpověď podle [zobrazení Dokončený kód v Githubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="beeff-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="beeff-206">Jste dokončili rychlé spuštění "větve a smyčky".</span><span class="sxs-lookup"><span data-stu-id="beeff-206">You've completed the "branches and loops" quickstart.</span></span>

<span data-ttu-id="beeff-207">Můžete pokračovat [řetězec interpolace](interpolated-strings-local.md) rychlé spuštění ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="beeff-207">You can continue with the [String interpolation](interpolated-strings-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="beeff-208">Další informace o těchto konceptech v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="beeff-208">You can learn more about these concepts in these topics:</span></span>

[<span data-ttu-id="beeff-209">Pokud a else – příkaz</span><span class="sxs-lookup"><span data-stu-id="beeff-209">If and else statement</span></span>](../language-reference/keywords/if-else.md)  
[<span data-ttu-id="beeff-210">While – příkaz</span><span class="sxs-lookup"><span data-stu-id="beeff-210">While statement</span></span>](../language-reference/keywords/while.md)  
[<span data-ttu-id="beeff-211">Do – příkaz</span><span class="sxs-lookup"><span data-stu-id="beeff-211">Do statement</span></span>](../language-reference/keywords/do.md)  
[<span data-ttu-id="beeff-212">For – příkaz</span><span class="sxs-lookup"><span data-stu-id="beeff-212">For statement</span></span>](../language-reference/keywords/for.md)  
