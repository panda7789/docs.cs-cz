---
title: "Čísla v jazyce C# kurzu - C# místní – elementy QuickStart"
description: "Výuka C# prozkoumáním číselnými typy, jejich vlastnosti a metody."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 99c2f8e4807c4d18c0c798e3a737f4a88d6e62d6
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="numbers-in-c-quickstart"></a><span data-ttu-id="01cad-103">Čísla v jazyce C# rychlý start</span><span class="sxs-lookup"><span data-stu-id="01cad-103">Numbers in C# quickstart</span></span>

<span data-ttu-id="01cad-104">Tento rychlý start se dozvíte, jaké číslo typy v jazyku C# interaktivně.</span><span class="sxs-lookup"><span data-stu-id="01cad-104">This quickstart teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="01cad-105">Napíšete malé množství kódu a potom budete zkompilování a spuštění tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="01cad-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="01cad-106">Rychlý Start obsahuje řadu lekce, které prozkoumat matematické operace v jazyce C# a čísla.</span><span class="sxs-lookup"><span data-stu-id="01cad-106">The quickstart contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="01cad-107">Tyto poznatky získají naučit základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="01cad-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="01cad-108">Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="01cad-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="01cad-109">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="01cad-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="01cad-110">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="01cad-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="01cad-111">Prozkoumejte matematické celé číslo</span><span class="sxs-lookup"><span data-stu-id="01cad-111">Explore integer math</span></span>

<span data-ttu-id="01cad-112">Vytvořte adresář s názvem **čísla – rychlý Start**.</span><span class="sxs-lookup"><span data-stu-id="01cad-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="01cad-113">Ujistěte, že aktuální adresář a spusťte `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="01cad-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="01cad-114">Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.Writeline("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="01cad-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="01cad-115">Spuštění tohoto kódu zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="01cad-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="01cad-116">Seznámili jste se právě jeden z základní matematické operace s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="01cad-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="01cad-117">`int` Zadejte představuje **celé číslo**, kladné a záporné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="01cad-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="01cad-118">Můžete použít `+` symbol pro přidání.</span><span class="sxs-lookup"><span data-stu-id="01cad-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="01cad-119">Další běžné matematické operace pro celá čísla zahrnují:</span><span class="sxs-lookup"><span data-stu-id="01cad-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="01cad-120">`-` pro odčítání</span><span class="sxs-lookup"><span data-stu-id="01cad-120">`-` for subtraction</span></span>
- <span data-ttu-id="01cad-121">`*` pro násobení</span><span class="sxs-lookup"><span data-stu-id="01cad-121">`*` for multiplication</span></span>
- <span data-ttu-id="01cad-122">`/` pro dělení</span><span class="sxs-lookup"><span data-stu-id="01cad-122">`/` for division</span></span>

<span data-ttu-id="01cad-123">Začít seznamovat se tyto jiné operace.</span><span class="sxs-lookup"><span data-stu-id="01cad-123">Start by exploring those different operations.</span></span> <span data-ttu-id="01cad-124">Přidejte tyto řádky po řádek, který zapíše hodnota `c`:</span><span class="sxs-lookup"><span data-stu-id="01cad-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="01cad-125">Spuštění tohoto kódu zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="01cad-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="01cad-126">Můžete vyzkoušet tak, že provedete více operací Matematika na stejném řádku, pokud vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="01cad-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="01cad-127">Zkuste `c = a + b - 12 * 17;` třeba.</span><span class="sxs-lookup"><span data-stu-id="01cad-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="01cad-128">Kombinování proměnné a čísla konstantní je povolen.</span><span class="sxs-lookup"><span data-stu-id="01cad-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="01cad-129">Jak můžete prozkoumat jazyka C# (nebo žádný programovací jazyk), uděláte budete chyby při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="01cad-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="01cad-130">**Kompilátoru** vyhledá tyto chyby a sestav je pro vás.</span><span class="sxs-lookup"><span data-stu-id="01cad-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="01cad-131">Když výstup obsahuje chybové zprávy, podívejte se úzce na ukázkový kód a kód v okně zobrazíte co opravit.</span><span class="sxs-lookup"><span data-stu-id="01cad-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="01cad-132">Tento úkol vám pomohou naučit struktury kódu C#.</span><span class="sxs-lookup"><span data-stu-id="01cad-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="01cad-133">Prvním krokem dokončíte.</span><span class="sxs-lookup"><span data-stu-id="01cad-133">You've finished the first step.</span></span> <span data-ttu-id="01cad-134">Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="01cad-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="01cad-135">Který usnadňuje začít pracovat s novou příklad.</span><span class="sxs-lookup"><span data-stu-id="01cad-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="01cad-136">Přejmenujte vaše `Main` metodu `WorkingWithIntegers` a zápis nový `Main` metoda, která volá `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="01cad-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="01cad-137">Po dokončení, váš kód by měl vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="01cad-137">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="01cad-138">Prozkoumejte pořadí operací</span><span class="sxs-lookup"><span data-stu-id="01cad-138">Explore order of operations</span></span>

<span data-ttu-id="01cad-139">Komentář volání `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="01cad-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="01cad-140">To bude dávat výstup, který menší zaplněny, při práci v této části:</span><span class="sxs-lookup"><span data-stu-id="01cad-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="01cad-141">`//` Spustí **komentář** v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="01cad-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="01cad-142">Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nemůžou provést jako kód.</span><span class="sxs-lookup"><span data-stu-id="01cad-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="01cad-143">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="01cad-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="01cad-144">Jazyk C# definuje prioritu různých Matematika operací s pravidly konzistentní s pravidly, že jste se naučili v Matematika.</span><span class="sxs-lookup"><span data-stu-id="01cad-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="01cad-145">Násobení a dělení mají přednost před sčítání a odečítání.</span><span class="sxs-lookup"><span data-stu-id="01cad-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="01cad-146">Prozkoumejte, přidáním následující kód do vaší `Main` metoda a execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="01cad-146">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="01cad-147">Výstup ukazuje, že násobení se provádí před přidání.</span><span class="sxs-lookup"><span data-stu-id="01cad-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="01cad-148">Můžete vynutit jiném pořadí operace přidáním v závorkách operaci nebo operace, které chcete provést první.</span><span class="sxs-lookup"><span data-stu-id="01cad-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="01cad-149">Přidejte následující řádky a znovu spusťte:</span><span class="sxs-lookup"><span data-stu-id="01cad-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="01cad-150">Prozkoumejte více kombinací mnoha různých operací.</span><span class="sxs-lookup"><span data-stu-id="01cad-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="01cad-151">Přidat něco jako následující řádky na konci vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="01cad-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="01cad-152">Zkuste `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="01cad-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="01cad-153">Možná jste si všimli zajímavé chování celých čísel.</span><span class="sxs-lookup"><span data-stu-id="01cad-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="01cad-154">Celočíselné dělení vždy vytvoří celé číslo, i v případě, že by uživatel očekával výsledek, který má zahrnout desetinné nebo zlomkové části.</span><span class="sxs-lookup"><span data-stu-id="01cad-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="01cad-155">Pokud toto chování ještě neviděli, zkuste následující kód na konci vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="01cad-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="01cad-156">Typ `dotnet run` znovu a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="01cad-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="01cad-157">Než budete pokračovat, podívejme všechny kód jsme vytvořené v této části a umístí jej do nové metody.</span><span class="sxs-lookup"><span data-stu-id="01cad-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="01cad-158">Volání této nové metody `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="01cad-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="01cad-159">Měli skončili s přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="01cad-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="01cad-160">Prozkoumejte přesnost celé číslo a omezení</span><span class="sxs-lookup"><span data-stu-id="01cad-160">Explore integer precision and limits</span></span>
<span data-ttu-id="01cad-161">Tento posledního vzorku vám ukázal, že celočíselné dělení zkrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="01cad-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="01cad-162">Můžete získat **zbývající** pomocí **modulo** operátor, `%` znak.</span><span class="sxs-lookup"><span data-stu-id="01cad-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="01cad-163">Zkuste následující kód ve vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="01cad-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="01cad-164">Typ integer jazyka C# se liší od matematickém celých čísel jeden jiným způsobem: `int` typ má minimální a maximální meze.</span><span class="sxs-lookup"><span data-stu-id="01cad-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="01cad-165">Přidejte tento kód, aby vaše `Main` metoda zobrazíte tato omezení:</span><span class="sxs-lookup"><span data-stu-id="01cad-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="01cad-166">Pokud výpočtu slouží k vytvoření hodnoty, které tato omezení překročí, máte **podtečení** nebo **přetečení** podmínku.</span><span class="sxs-lookup"><span data-stu-id="01cad-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="01cad-167">Zdá se, že odpověď zabalení z limitu jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="01cad-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="01cad-168">Přidejte tyto dva řádky do vaší `Main` metoda zobrazíte příklad:</span><span class="sxs-lookup"><span data-stu-id="01cad-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="01cad-169">Všimněte si, že odpověď je velmi brzy bude dosaženo minimální (záporné) celé číslo.</span><span class="sxs-lookup"><span data-stu-id="01cad-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="01cad-170">Je stejný jako `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="01cad-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="01cad-171">Operace přidání **došlo k přetečení** povolené hodnoty pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="01cad-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="01cad-172">Odpověď je velmi velké záporné číslo, protože přetečení "obtéká" z největší možné celočíselnou hodnotu po nejmenší.</span><span class="sxs-lookup"><span data-stu-id="01cad-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="01cad-173">Existují další číselnými typy s jinou omezení a přesnost, že by se použijte, když `int` typ nevyhovuje vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="01cad-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="01cad-174">Podíváme se na tyto další.</span><span class="sxs-lookup"><span data-stu-id="01cad-174">Let's explore those next.</span></span>

<span data-ttu-id="01cad-175">Přejděme znovu, kód, který jste napsali v této části do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="01cad-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="01cad-176">Pojmenujte ji `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="01cad-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="01cad-177">Práce s typ double</span><span class="sxs-lookup"><span data-stu-id="01cad-177">Work with the double type</span></span>

<span data-ttu-id="01cad-178">`double` Číselného typu představuje číslo s plovoucí desetinnou dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="01cad-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="01cad-179">Tyto podmínky může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="01cad-179">Those terms may be new to you.</span></span> <span data-ttu-id="01cad-180">A **plovoucí desetinnou čárkou** číslo je užitečné k reprezentaci bez integrální čísla, která může být velmi velké nebo malé řádově.</span><span class="sxs-lookup"><span data-stu-id="01cad-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="01cad-181">**Dvojitá přesnost** znamená, že tato čísla ukládat pomocí přesností větší než **jednoduchou přesností**.</span><span class="sxs-lookup"><span data-stu-id="01cad-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="01cad-182">Na počítačích moderní je dnes běžné používat Dvojitá přesnost než čísla s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="01cad-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="01cad-183">Podíváme se na.</span><span class="sxs-lookup"><span data-stu-id="01cad-183">Let's explore.</span></span> <span data-ttu-id="01cad-184">Přidejte následující kód a zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="01cad-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="01cad-185">Všimněte si, že odpověď obsahuje desetinná část podílu.</span><span class="sxs-lookup"><span data-stu-id="01cad-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="01cad-186">Zkuste něco víc složitý výraz s hodnoty Double:</span><span class="sxs-lookup"><span data-stu-id="01cad-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="01cad-187">Rozsah hodnota typu double je mnohem větší než celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01cad-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="01cad-188">Zkuste následující kód níže, co jste vytvořili, pokud:</span><span class="sxs-lookup"><span data-stu-id="01cad-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="01cad-189">Tyto hodnoty jsou vytiskne v exponenciální notace.</span><span class="sxs-lookup"><span data-stu-id="01cad-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="01cad-190">Číslo směrem doleva od `E` je mantisy.</span><span class="sxs-lookup"><span data-stu-id="01cad-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="01cad-191">Číslo, které má právo je exponent, jako druhou mocninou 10.</span><span class="sxs-lookup"><span data-stu-id="01cad-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="01cad-192">Stejně jako desetinná čísla v matematické může mít hodnoty Double v jazyce C# zaokrouhlení chyby.</span><span class="sxs-lookup"><span data-stu-id="01cad-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="01cad-193">Zkuste tento kód:</span><span class="sxs-lookup"><span data-stu-id="01cad-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="01cad-194">Víte, že `0.3` opakující se právě není stejný jako `1/3`.</span><span class="sxs-lookup"><span data-stu-id="01cad-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="01cad-195">***výzvy***</span><span class="sxs-lookup"><span data-stu-id="01cad-195">***Challenge***</span></span>

<span data-ttu-id="01cad-196">Zkuste jiné výpočty s velká čísla, malá čísla, násobení a dělení pomocí `double` typu.</span><span class="sxs-lookup"><span data-stu-id="01cad-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="01cad-197">Zkuste složitější výpočty.</span><span class="sxs-lookup"><span data-stu-id="01cad-197">Try more complicated calculations.</span></span>

<span data-ttu-id="01cad-198">Jakmile jste stráví chvíli s otázkou, trvat kód jsme zapsané a jeho následné uložení do nové metody.</span><span class="sxs-lookup"><span data-stu-id="01cad-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="01cad-199">Název této nové metody `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="01cad-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="01cad-200">Práce s pevnou bodu typy</span><span class="sxs-lookup"><span data-stu-id="01cad-200">Work with fixed point types</span></span>

<span data-ttu-id="01cad-201">Seznámili jste se základní číselnými typy v jazyku C#: celá čísla a hodnoty Double.</span><span class="sxs-lookup"><span data-stu-id="01cad-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="01cad-202">Neexistuje jeden další typ. Další: `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="01cad-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="01cad-203">`decimal` Typ má menší oblast ale přesností větší než `double`.</span><span class="sxs-lookup"><span data-stu-id="01cad-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="01cad-204">Termín **pevné bodu** znamená, že se nepřesune desetinné čárky (nebo binární bodu).</span><span class="sxs-lookup"><span data-stu-id="01cad-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="01cad-205">Podívejme se:</span><span class="sxs-lookup"><span data-stu-id="01cad-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="01cad-206">Všimněte si, že rozsah je menší, než `double` typu.</span><span class="sxs-lookup"><span data-stu-id="01cad-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="01cad-207">Větší přesnost s typ decimal, můžete zjistit tak, že zkusíte následující kód:</span><span class="sxs-lookup"><span data-stu-id="01cad-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="01cad-208">`M` Příponu na čísla, která je, jak můžete označit, že by měl použít konstanta `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="01cad-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="01cad-209">Všimněte si, že výpočty pomocí typu decimal obsahuje více číslic vpravo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="01cad-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="01cad-210">***výzvy***</span><span class="sxs-lookup"><span data-stu-id="01cad-210">***Challenge***</span></span>

<span data-ttu-id="01cad-211">Teď, když jste se seznámili s různými typy číselné, napište kód, který vypočítá oblasti kruh jejichž radius je 2.50 cm.</span><span class="sxs-lookup"><span data-stu-id="01cad-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="01cad-212">Mějte na paměti, že oblast kruhu je radius spolehlivosti násobí hodnotou platformy.</span><span class="sxs-lookup"><span data-stu-id="01cad-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="01cad-213">Jeden pomocný parametr: .NET obsahuje konstanty pro platformy, <xref:System.Math.PI?displayProperty=nameWithType> , můžete použít pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01cad-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="01cad-214">Měli byste obdržet odpověď až 19, 20.</span><span class="sxs-lookup"><span data-stu-id="01cad-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="01cad-215">Můžete zkontrolovat vaše odpověď podle [prohlížení dokončení ukázkový kód na Githubu](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="01cad-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="01cad-216">Pokud chcete, zkuste některé jiné vzorce.</span><span class="sxs-lookup"><span data-stu-id="01cad-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="01cad-217">Jste dokončili rychlé spuštění "čísla v C#".</span><span class="sxs-lookup"><span data-stu-id="01cad-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="01cad-218">Můžete pokračovat [větve a smyčky](branches-and-loops-local.md) rychlé spuštění ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="01cad-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="01cad-219">Další informace o čísla v jazyce C# v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="01cad-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="01cad-220">[Tabulka celočíselných typů](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="01cad-220">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="01cad-221">[Tabulka typů s plovoucí desetinnou čárkou](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="01cad-221">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="01cad-222">[Tabulka předdefinovaných typů](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="01cad-222">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="01cad-223">[Tabulka implicitních číselných převodů](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="01cad-223">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="01cad-224">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="01cad-224">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

