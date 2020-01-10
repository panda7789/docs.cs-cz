---
title: Čísla v C# úvodu k C# kurzu
description: Naučte C# se prozkoumat číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7537bb597665461021946a792e342149f29c0e95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694657"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="5796b-103">Manipulace s čísly integrálních a plovoucích bodů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="5796b-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="5796b-104">V tomto kurzu se naučíte, aby se číselné C# typy v interaktivně.</span><span class="sxs-lookup"><span data-stu-id="5796b-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="5796b-105">Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód.</span><span class="sxs-lookup"><span data-stu-id="5796b-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="5796b-106">Kurz obsahuje řadu lekcí, které prozkoumají čísla a matematické operace v C#.</span><span class="sxs-lookup"><span data-stu-id="5796b-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="5796b-107">V těchto kurzech se seznámíte se základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5796b-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="5796b-108">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="5796b-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="5796b-109">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="5796b-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="5796b-110">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="5796b-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="5796b-111">Seznámení s matematikou celých čísel</span><span class="sxs-lookup"><span data-stu-id="5796b-111">Explore integer math</span></span>

<span data-ttu-id="5796b-112">Vytvořte adresář s názvem *Numbers – rychlý Start*.</span><span class="sxs-lookup"><span data-stu-id="5796b-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="5796b-113">Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5796b-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="5796b-114">Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte `Console.WriteLine("Hello World!");` řádku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5796b-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="5796b-115">Spusťte tento kód zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="5796b-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="5796b-116">Právě jste viděli jednu ze základních matematických operací s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="5796b-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="5796b-117">Typ `int` představuje **celé**číslo, nula, kladné nebo záporné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="5796b-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="5796b-118">Pro sčítání se používá symbol `+`.</span><span class="sxs-lookup"><span data-stu-id="5796b-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="5796b-119">K dalším běžným matematickým operacím s celými čísly patří tyto:</span><span class="sxs-lookup"><span data-stu-id="5796b-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="5796b-120">`-` pro odčítání</span><span class="sxs-lookup"><span data-stu-id="5796b-120">`-` for subtraction</span></span>
- <span data-ttu-id="5796b-121">`*` pro násobení</span><span class="sxs-lookup"><span data-stu-id="5796b-121">`*` for multiplication</span></span>
- <span data-ttu-id="5796b-122">`/` pro dělení</span><span class="sxs-lookup"><span data-stu-id="5796b-122">`/` for division</span></span>

<span data-ttu-id="5796b-123">Nejdřív si vyzkoušejte uvedené operace.</span><span class="sxs-lookup"><span data-stu-id="5796b-123">Start by exploring those different operations.</span></span> <span data-ttu-id="5796b-124">Přidejte tyto řádky za řádek, který zapíše hodnotu `c`:</span><span class="sxs-lookup"><span data-stu-id="5796b-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="5796b-125">Spusťte tento kód zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="5796b-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="5796b-126">Pokud chcete, můžete taky experimentovat a provést několik matematických operací na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="5796b-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="5796b-127">Zkuste například `c = a + b - 12 * 17;`.</span><span class="sxs-lookup"><span data-stu-id="5796b-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="5796b-128">Jsou povoleny kombinace proměnných a konstantních čísel.</span><span class="sxs-lookup"><span data-stu-id="5796b-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="5796b-129">Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="5796b-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="5796b-130">**Kompilátor** tyto chyby odhalí a upozorní vás na ně.</span><span class="sxs-lookup"><span data-stu-id="5796b-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="5796b-131">Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.</span><span class="sxs-lookup"><span data-stu-id="5796b-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="5796b-132">Toto cvičení vám pomůže seznámit se se strukturou kódu v C#.</span><span class="sxs-lookup"><span data-stu-id="5796b-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="5796b-133">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="5796b-133">You've finished the first step.</span></span> <span data-ttu-id="5796b-134">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="5796b-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="5796b-135">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="5796b-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="5796b-136">Přejmenujte metodu `Main` na `WorkingWithIntegers` a zapište novou `Main` metodu, která volá `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="5796b-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="5796b-137">Až skončíte, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="5796b-137">When you finish, your code should look like this:</span></span>

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
            
            // addition
            int c = a + b;
            Console.WriteLine(c);
            
            // subtraction
            c = a - b;
            Console.WriteLine(c);
            
            // multiplication
            c = a * b;
            Console.WriteLine(c);
            
            // division
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

## <a name="explore-order-of-operations"></a><span data-ttu-id="5796b-138">Seznámení s pořadím operací</span><span class="sxs-lookup"><span data-stu-id="5796b-138">Explore order of operations</span></span>

<span data-ttu-id="5796b-139">Odkomentujte volání `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="5796b-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="5796b-140">Výsledkem je, že při práci v této části bude výstup méně zbytečný:</span><span class="sxs-lookup"><span data-stu-id="5796b-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="5796b-141">`//` spustí **Komentář** v C#.</span><span class="sxs-lookup"><span data-stu-id="5796b-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="5796b-142">Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód.</span><span class="sxs-lookup"><span data-stu-id="5796b-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="5796b-143">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="5796b-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="5796b-144">Jazyk C# definuje prioritu různých matematických operací v souladu se stejnými pravidly, jaká jste se naučili při hodinách matematiky.</span><span class="sxs-lookup"><span data-stu-id="5796b-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="5796b-145">Násobení a dělení mají přednost před sčítáním a odčítáním.</span><span class="sxs-lookup"><span data-stu-id="5796b-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="5796b-146">Prozkoumejte to přidáním následujícího kódu do metody `Main` a spuštěním `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="5796b-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="5796b-147">Z výstupu vyplývá, že operace násobení se provede dřív než operace sčítání.</span><span class="sxs-lookup"><span data-stu-id="5796b-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="5796b-148">Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operací, které chcete provést jako první.</span><span class="sxs-lookup"><span data-stu-id="5796b-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="5796b-149">Přidejte následující řádky a spusťte znovu:</span><span class="sxs-lookup"><span data-stu-id="5796b-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="5796b-150">Teď prozkoumáme i další možnosti s kombinací několika různých operací.</span><span class="sxs-lookup"><span data-stu-id="5796b-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="5796b-151">V dolní části metody `Main` přidejte něco jako na následující řádky.</span><span class="sxs-lookup"><span data-stu-id="5796b-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="5796b-152">Znovu zkuste příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="5796b-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="5796b-153">Můžete si u celých čísel všimnout zvláštního chování.</span><span class="sxs-lookup"><span data-stu-id="5796b-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="5796b-154">Výsledkem dělení celých čísel je vždycky celé číslo, i když byste očekávali, že bude výsledek obsahovat číslo s desetinnou čárkou nebo zlomek.</span><span class="sxs-lookup"><span data-stu-id="5796b-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="5796b-155">Pokud jste toto chování neviděli, vyzkoušejte následující kód na konci vaší `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5796b-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="5796b-156">Opětovným zadáním `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="5796b-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="5796b-157">Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="5796b-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="5796b-158">Zavolejte novou metodu `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="5796b-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="5796b-159">Měli byste skončit přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="5796b-159">You should end up with something like this:</span></span>

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
            
            // addition
            int c = a + b;
            Console.WriteLine(c);
            
            // subtraction
            c = a - b;
            Console.WriteLine(c);
            
            // multiplication
            c = a * b;
            Console.WriteLine(c);
            
            // division
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

            d = (a + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="5796b-160">Seznámení s přesností a limity celých čísel</span><span class="sxs-lookup"><span data-stu-id="5796b-160">Explore integer precision and limits</span></span>

<span data-ttu-id="5796b-161">Z poslední ukázky jste se dozvěděli, že při dělení celých čísel dochází ke zkrácení výsledku.</span><span class="sxs-lookup"><span data-stu-id="5796b-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="5796b-162">**Zbytek** můžete získat pomocí operátoru **modulo** , `%`ho znaku.</span><span class="sxs-lookup"><span data-stu-id="5796b-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="5796b-163">Vyzkoušejte následující kód v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="5796b-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="5796b-164">Od celých čísel v matematice se typ integer v jazyce C# se liší v jednom ohledu: typ `int` má minimální a maximální limit.</span><span class="sxs-lookup"><span data-stu-id="5796b-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="5796b-165">Přidejte tento kód do metody `Main`, abyste viděli tato omezení:</span><span class="sxs-lookup"><span data-stu-id="5796b-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="5796b-166">Pokud je výsledkem určitého výpočtu hodnota, která tyto limity překračuje, nastane stav **podtečení** nebo **přetečení**.</span><span class="sxs-lookup"><span data-stu-id="5796b-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="5796b-167">Odpověď cyklicky přechází od jednoho limitu k druhému.</span><span class="sxs-lookup"><span data-stu-id="5796b-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="5796b-168">Přidejte tyto dva řádky do metody `Main`, abyste viděli příklad:</span><span class="sxs-lookup"><span data-stu-id="5796b-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="5796b-169">Všimněte si, že se odpověď těsně blíží minimálnímu (zápornému) celému číslu.</span><span class="sxs-lookup"><span data-stu-id="5796b-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="5796b-170">Je stejná jako při operaci `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="5796b-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="5796b-171">Operace sčítání **přetekla** povolené hodnoty celých čísel.</span><span class="sxs-lookup"><span data-stu-id="5796b-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="5796b-172">Výsledkem je velmi velké záporné číslo, protože při přetečení došlo k „cyklickému přechodu“ od nejvyšší možné celočíselné hodnoty k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="5796b-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="5796b-173">Existují i další číselné typy s různými limity a přesností, které můžete použít, pokud typ `int` nevyhovuje vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="5796b-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="5796b-174">Pojďme se teď na ně podívat.</span><span class="sxs-lookup"><span data-stu-id="5796b-174">Let's explore those next.</span></span>

<span data-ttu-id="5796b-175">Později můžete kód, který jste napsali v této části, přesunout do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="5796b-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="5796b-176">Pojmenujte ji `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="5796b-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="5796b-177">Práce s typem double</span><span class="sxs-lookup"><span data-stu-id="5796b-177">Work with the double type</span></span>

<span data-ttu-id="5796b-178">Číselný typ `double` představuje číslo s plovoucí desetinnou čárkou a dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="5796b-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="5796b-179">Tyto výrazy možná ještě neznáte.</span><span class="sxs-lookup"><span data-stu-id="5796b-179">Those terms may be new to you.</span></span> <span data-ttu-id="5796b-180">Číslo s **plovoucí desetinnou čárkou** slouží k reprezentaci jiných než celých čísel, která mohou být buď velmi nízká, nebo velmi vysoká.</span><span class="sxs-lookup"><span data-stu-id="5796b-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="5796b-181">**Dvojitá přesnost** znamená, že se tato čísla ukládají s větší přesností než s **jednoduchou přesností**.</span><span class="sxs-lookup"><span data-stu-id="5796b-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="5796b-182">V moderních počítačích se častěji používají čísla s dvojitou přesností než s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="5796b-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="5796b-183">Pojďme se na to podívat blíž.</span><span class="sxs-lookup"><span data-stu-id="5796b-183">Let's explore.</span></span> <span data-ttu-id="5796b-184">Přidejte následující kód a podívejte se na výsledek:</span><span class="sxs-lookup"><span data-stu-id="5796b-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="5796b-185">Všimněte si, že odpověď obsahuje desetinnou část podílu.</span><span class="sxs-lookup"><span data-stu-id="5796b-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="5796b-186">Teď zkusíme zadat o něco složitější výraz s čísly typu double:</span><span class="sxs-lookup"><span data-stu-id="5796b-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="5796b-187">Rozsah hodnoty double je mnohem větší než u hodnot typu integer.</span><span class="sxs-lookup"><span data-stu-id="5796b-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="5796b-188">Vyzkoušejte následující kód, který jste doposud napsali:</span><span class="sxs-lookup"><span data-stu-id="5796b-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="5796b-189">Hodnoty jsou uvedené za použití vědeckého zápisu čísel.</span><span class="sxs-lookup"><span data-stu-id="5796b-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="5796b-190">Číslu vlevo od písmene `E` se říká mantisa.</span><span class="sxs-lookup"><span data-stu-id="5796b-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="5796b-191">Číslo vpravo se označuje jako exponent a značí násobky 10.</span><span class="sxs-lookup"><span data-stu-id="5796b-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="5796b-192">Stejně jako desetinná čísla v matematice můžou mít i hodnoty typu double v C# chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="5796b-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="5796b-193">Vyzkoušejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="5796b-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="5796b-194">Víte, že hodnota `0.3` periodických přesně neodpovídá hodnotě `1/3`.</span><span class="sxs-lookup"><span data-stu-id="5796b-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="5796b-195">***Výzva***</span><span class="sxs-lookup"><span data-stu-id="5796b-195">***Challenge***</span></span>

<span data-ttu-id="5796b-196">Vyzkoušejte si různé výpočty s vysokými čísly, nízkými čísly, násobením a dělením za použití typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5796b-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="5796b-197">Zkuste zadat i složitější výpočty.</span><span class="sxs-lookup"><span data-stu-id="5796b-197">Try more complicated calculations.</span></span>

<span data-ttu-id="5796b-198">Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="5796b-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="5796b-199">Pojmenujte novou metodu `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="5796b-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="5796b-200">Práce s typy s pevnou desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="5796b-200">Work with fixed point types</span></span>

<span data-ttu-id="5796b-201">Seznámili jste se se základními typy čísel v jazyce C#: celými čísly a čísly s dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="5796b-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="5796b-202">Zbývá už jenom jeden další typ, `decimal`.</span><span class="sxs-lookup"><span data-stu-id="5796b-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="5796b-203">Typ `decimal` má menší rozsah, ale zato větší přesnost než typ `double`.</span><span class="sxs-lookup"><span data-stu-id="5796b-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="5796b-204">Výraz **pevná desetinná čárka** znamená, že se desetinná (neboli řádová) čárka nepohybuje.</span><span class="sxs-lookup"><span data-stu-id="5796b-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="5796b-205">Podívejme se na to:</span><span class="sxs-lookup"><span data-stu-id="5796b-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="5796b-206">Všimněte si, že je rozsah menší než u typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5796b-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="5796b-207">Větší přesnost typu decimal si můžete ověřit zadáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5796b-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="5796b-208">Přípona `M` za čísly představuje způsob, jak naznačit, že má konstanta používat typ `decimal`.</span><span class="sxs-lookup"><span data-stu-id="5796b-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="5796b-209">Všimněte si, že výsledek s typem decimal má napravo od desetinné čárky víc číslic.</span><span class="sxs-lookup"><span data-stu-id="5796b-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="5796b-210">***Výzva***</span><span class="sxs-lookup"><span data-stu-id="5796b-210">***Challenge***</span></span>

<span data-ttu-id="5796b-211">Seznámili jste se s různými typy čísel a teď můžete napsat kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru.</span><span class="sxs-lookup"><span data-stu-id="5796b-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="5796b-212">Obsah kruhu se vypočítá jako poloměr na druhou krát číslo pí.</span><span class="sxs-lookup"><span data-stu-id="5796b-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="5796b-213">Nápověda: Prostředí .NET obsahuje pro číslo pí konstantu <xref:System.Math.PI?displayProperty=nameWithType>, kterou můžete pro tuto hodnotu použít.</span><span class="sxs-lookup"><span data-stu-id="5796b-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="5796b-214">Měl by vám vyjít výsledek mezi 19 a 20.</span><span class="sxs-lookup"><span data-stu-id="5796b-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="5796b-215">Odpověď si můžete [prohlédnout na stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span><span class="sxs-lookup"><span data-stu-id="5796b-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="5796b-216">Jestli chcete, můžete si vyzkoušet i další vzorce.</span><span class="sxs-lookup"><span data-stu-id="5796b-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="5796b-217">Dokončili jste rychlý Start s čísly C#.</span><span class="sxs-lookup"><span data-stu-id="5796b-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="5796b-218">Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="5796b-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="5796b-219">Další informace o číslech v jazyce C# se dozvíte v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="5796b-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="5796b-220">Celočíselné číselné typy</span><span class="sxs-lookup"><span data-stu-id="5796b-220">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="5796b-221">Číselné typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="5796b-221">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="5796b-222">Předdefinované číselné převody</span><span class="sxs-lookup"><span data-stu-id="5796b-222">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
