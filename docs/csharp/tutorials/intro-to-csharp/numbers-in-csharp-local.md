---
title: Čísla v C# – Úvod do C# kurz
description: Přečtěte si C# prozkoumáním číselné typy, vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d95d5ce16abadf441158b7f8af93acc73b154e99
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661052"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="8fed3-103">Zpracování čísel s plovoucí desetinnou čárkou a integrální bod v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="8fed3-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="8fed3-104">V tomto kurzu se dozvíte, jaké typy čísel v C# interaktivně.</span><span class="sxs-lookup"><span data-stu-id="8fed3-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="8fed3-105">Budete psát malé množství kódu a pak budete kompilace a spuštění tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="8fed3-106">Tento kurz obsahuje sérii lekcí, které se zabývají čísly a matematickými operacemi v C#.</span><span class="sxs-lookup"><span data-stu-id="8fed3-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="8fed3-107">Tato lekce vás naučí základy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8fed3-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="8fed3-108">V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="8fed3-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="8fed3-109">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="8fed3-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="8fed3-110">Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="8fed3-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="8fed3-111">Prozkoumejte matematikou celých čísel</span><span class="sxs-lookup"><span data-stu-id="8fed3-111">Explore integer math</span></span>

<span data-ttu-id="8fed3-112">Vytvořte adresář **čísla quickstart**.</span><span class="sxs-lookup"><span data-stu-id="8fed3-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="8fed3-113">Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="8fed3-114">Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8fed3-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="8fed3-115">Tento kód spustit zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="8fed3-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8fed3-116">Právě jste viděli jednu ze základních matematických operací s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="8fed3-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="8fed3-117">`int` Zadejte představuje **celé číslo**, kladné nebo záporné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="8fed3-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="8fed3-118">Můžete použít `+` symbol pro přidání.</span><span class="sxs-lookup"><span data-stu-id="8fed3-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="8fed3-119">Dalším běžným matematickým operacím pro celá čísla zahrnují:</span><span class="sxs-lookup"><span data-stu-id="8fed3-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="8fed3-120">`-` pro odčítání</span><span class="sxs-lookup"><span data-stu-id="8fed3-120">`-` for subtraction</span></span>
- <span data-ttu-id="8fed3-121">`*` pro násobení</span><span class="sxs-lookup"><span data-stu-id="8fed3-121">`*` for multiplication</span></span>
- <span data-ttu-id="8fed3-122">`/` pro dělení</span><span class="sxs-lookup"><span data-stu-id="8fed3-122">`/` for division</span></span>

<span data-ttu-id="8fed3-123">Nejdřív si vyzkoušejte uvedené operace.</span><span class="sxs-lookup"><span data-stu-id="8fed3-123">Start by exploring those different operations.</span></span> <span data-ttu-id="8fed3-124">Přidejte tyto řádky po řádek, který zapíše hodnoty `c`:</span><span class="sxs-lookup"><span data-stu-id="8fed3-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="8fed3-125">Tento kód spustit zadáním `dotnet run` v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="8fed3-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8fed3-126">Můžete taky experimentovat a provést několik matematických operací na jednom řádku, pokud byste o ni.</span><span class="sxs-lookup"><span data-stu-id="8fed3-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="8fed3-127">Zkuste `c = a + b - 12 * 17;` třeba.</span><span class="sxs-lookup"><span data-stu-id="8fed3-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="8fed3-128">Kombinování proměnné a konstanty čísla je povolen.</span><span class="sxs-lookup"><span data-stu-id="8fed3-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="8fed3-129">Když se budete učit, C# (nebo libovolným programovacím jazykem), budete se při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="8fed3-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="8fed3-130">**Kompilátoru** se tyto chyby odhalí a dejte nám o nich na vás.</span><span class="sxs-lookup"><span data-stu-id="8fed3-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="8fed3-131">Pokud výstup obsahuje chybové zprávy, prohlédněte si blíže ukázkový kód a kód v okně zobrazit, co je potřeba opravit.</span><span class="sxs-lookup"><span data-stu-id="8fed3-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="8fed3-132">Toto cvičení vám pomůže seznámit se se strukturou kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8fed3-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="8fed3-133">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="8fed3-133">You've finished the first step.</span></span> <span data-ttu-id="8fed3-134">Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="8fed3-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="8fed3-135">Který usnadňuje začít pracovat s nový příklad.</span><span class="sxs-lookup"><span data-stu-id="8fed3-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="8fed3-136">Přejmenovat váš `Main` metodu `WorkingWithIntegers` a napsat nový `Main` metodu, která volá `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="8fed3-137">Jakmile budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="8fed3-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="8fed3-138">Seznámení s pořadím operací</span><span class="sxs-lookup"><span data-stu-id="8fed3-138">Explore order of operations</span></span>

<span data-ttu-id="8fed3-139">Odkomentujte volání `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="8fed3-140">Bude výstup, který zaplněný při práci v této části:</span><span class="sxs-lookup"><span data-stu-id="8fed3-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="8fed3-141">`//` Spustí **komentář** v C#.</span><span class="sxs-lookup"><span data-stu-id="8fed3-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="8fed3-142">Komentáře jsou jakýkoli text, který chcete ponechat ve zdrojovém kódu, ale nemůžou provést jako kód.</span><span class="sxs-lookup"><span data-stu-id="8fed3-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="8fed3-143">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="8fed3-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="8fed3-144">Jazyk C# definuje prioritu různých matematických operací pravidla souladu se stejnými pravidly, že jste se naučili v matematice.</span><span class="sxs-lookup"><span data-stu-id="8fed3-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="8fed3-145">Úlohy násobení a dělení přednost před sčítáním a odčítáním.</span><span class="sxs-lookup"><span data-stu-id="8fed3-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="8fed3-146">Vyzkoušejte si to tak, že přidáte následující kód do vašeho `Main` metoda a provádění `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="8fed3-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="8fed3-147">Z výstupu vyplývá, operace násobení se provede dřív než operace sčítání.</span><span class="sxs-lookup"><span data-stu-id="8fed3-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="8fed3-148">Jiné pořadí operací můžete vynutit závorek uzavřením operace nebo operací, které chcete provést jako první.</span><span class="sxs-lookup"><span data-stu-id="8fed3-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="8fed3-149">Přidejte následující řádky a znovu spusťte:</span><span class="sxs-lookup"><span data-stu-id="8fed3-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="8fed3-150">Teď prozkoumáme i další kombinací několika různých operací.</span><span class="sxs-lookup"><span data-stu-id="8fed3-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="8fed3-151">Přidat něco podobného následující řádky na konci vaší `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8fed3-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="8fed3-152">Zkuste `dotnet run` znovu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="8fed3-153">Mohli jste si všimnout zvláštního chování pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="8fed3-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="8fed3-154">Dělení celého čísla vždy vytváří celé číslo výsledku, i když byste očekávali bude výsledek obsahovat desetinné nebo zlomkové části.</span><span class="sxs-lookup"><span data-stu-id="8fed3-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="8fed3-155">Pokud toto chování nezaznamenali, zkuste následující kód na konci vaší `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8fed3-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8fed3-156">Typ `dotnet run` znovu, abyste viděli výsledek.</span><span class="sxs-lookup"><span data-stu-id="8fed3-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="8fed3-157">Než budete pokračovat, Pojďme se na veškerý kód jsme napsané v této části a vložit ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="8fed3-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="8fed3-158">Volání této nové metody `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="8fed3-159">By měla skončit s vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="8fed3-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="8fed3-160">Prozkoumat celé číslo přesnosti a omezení</span><span class="sxs-lookup"><span data-stu-id="8fed3-160">Explore integer precision and limits</span></span>

<span data-ttu-id="8fed3-161">Z poslední ukázky vám ukázal, že dělení celého čísla zkrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="8fed3-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="8fed3-162">Můžete získat **zbývající** pomocí **modulo** operátoru `%` znak.</span><span class="sxs-lookup"><span data-stu-id="8fed3-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="8fed3-163">Následující kód ve vašich `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8fed3-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="8fed3-164">Typ integer jazyka C# se liší od matematické celých čísel v jednom ohledu: `int` typ má minimální a maximální mezí.</span><span class="sxs-lookup"><span data-stu-id="8fed3-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="8fed3-165">Přidejte tento kód, aby vaše `Main` metoda tyto limity zjistíte:</span><span class="sxs-lookup"><span data-stu-id="8fed3-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="8fed3-166">Pokud výsledkem určitého výpočtu hodnota, která tyto limity překračuje, máte **podtečení** nebo **přetečení** podmínku.</span><span class="sxs-lookup"><span data-stu-id="8fed3-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="8fed3-167">Zobrazí se odpověď cyklicky přechází od jednoho limitu k druhému.</span><span class="sxs-lookup"><span data-stu-id="8fed3-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="8fed3-168">Přidejte následující dva řádky do vaší `Main` metoda k prohlédnutí příkladu:</span><span class="sxs-lookup"><span data-stu-id="8fed3-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="8fed3-169">Všimněte si, že odpověď těsně blíží minimální (zápornému) celému číslu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="8fed3-170">Je stejný jako `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="8fed3-171">Operace sčítání **došlo k přetečení** povolené hodnoty celých čísel.</span><span class="sxs-lookup"><span data-stu-id="8fed3-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="8fed3-172">Odpověď je velmi velké záporné číslo, protože přetečení "cyklickému přechodu" od nejvyšší možné celočíselné hodnoty k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="8fed3-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="8fed3-173">Existují další číselné typy s různými limity a přesností, můžete použít, pokud `int` typu nevyhovuje vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="8fed3-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="8fed3-174">Podíváme se na ně podívat.</span><span class="sxs-lookup"><span data-stu-id="8fed3-174">Let's explore those next.</span></span>

<span data-ttu-id="8fed3-175">Ještě jednou přejdeme kód, který jste napsali v této části do samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="8fed3-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="8fed3-176">Pojmenujte ji `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="8fed3-177">Práce s typem double</span><span class="sxs-lookup"><span data-stu-id="8fed3-177">Work with the double type</span></span>

<span data-ttu-id="8fed3-178">`double` Číselného typu představuje číslo s plovoucí desetinnou dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="8fed3-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="8fed3-179">Tyto výrazy možná pro vás nová.</span><span class="sxs-lookup"><span data-stu-id="8fed3-179">Those terms may be new to you.</span></span> <span data-ttu-id="8fed3-180">A **s plovoucí desetinnou čárkou** číslo slouží k reprezentaci jiných než celých čísel, která může být velmi velké nebo velmi vysoká.</span><span class="sxs-lookup"><span data-stu-id="8fed3-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="8fed3-181">**Dvojité přesnosti** znamená, že tato čísla ukládají s větší přesností než **jednoduchou přesností**.</span><span class="sxs-lookup"><span data-stu-id="8fed3-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="8fed3-182">V moderních počítačích se častěji používají s dvojitou přesností než čísla a jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="8fed3-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="8fed3-183">Zkusíme zjistit.</span><span class="sxs-lookup"><span data-stu-id="8fed3-183">Let's explore.</span></span> <span data-ttu-id="8fed3-184">Přidejte následující kód a zobrazit výsledek:</span><span class="sxs-lookup"><span data-stu-id="8fed3-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="8fed3-185">Všimněte si, že odpověď obsahuje desetinnou část podílu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="8fed3-186">Try – o něco složitější výraz s čísly typu Double:</span><span class="sxs-lookup"><span data-stu-id="8fed3-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8fed3-187">Rozsah hodnoty double je mnohem větší než u hodnot typu integer.</span><span class="sxs-lookup"><span data-stu-id="8fed3-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="8fed3-188">Vyzkoušejte následující co jste napsali zatím následující kód:</span><span class="sxs-lookup"><span data-stu-id="8fed3-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="8fed3-189">Tyto hodnoty jsou vytiskne zapsaný exponenciální notací.</span><span class="sxs-lookup"><span data-stu-id="8fed3-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="8fed3-190">Číslo vlevo od `E` se říká mantisa.</span><span class="sxs-lookup"><span data-stu-id="8fed3-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="8fed3-191">Exponent, je číslo vpravo jako mocninu 10.</span><span class="sxs-lookup"><span data-stu-id="8fed3-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="8fed3-192">Stejně jako desetinná čísla v matematice můžou mít typu Double v C# chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="8fed3-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="8fed3-193">Vyzkoušejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="8fed3-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="8fed3-194">Víte, že `0.3` periodických přesně neodpovídá stejný jako `1/3`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="8fed3-195">***Výzvy***</span><span class="sxs-lookup"><span data-stu-id="8fed3-195">***Challenge***</span></span>

<span data-ttu-id="8fed3-196">Vyzkoušejte si různé výpočty s velkým, malé čísly, násobením a dělením za použití `double` typu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="8fed3-197">Zkuste složitější výpočty.</span><span class="sxs-lookup"><span data-stu-id="8fed3-197">Try more complicated calculations.</span></span>

<span data-ttu-id="8fed3-198">Jakmile strávili jste už nějakou dobu s výzvou, trvat, než kód napsali a umístěte ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="8fed3-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="8fed3-199">Název této nové metody `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="8fed3-200">Práce s typy s pevnou desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="8fed3-200">Work with fixed point types</span></span>

<span data-ttu-id="8fed3-201">Seznámili jste se základními typy čísel v jazyce C#: celými čísly a čísly typu Double.</span><span class="sxs-lookup"><span data-stu-id="8fed3-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="8fed3-202">Existuje jeden další typ: `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="8fed3-203">`decimal` Má menší rozsah, ale zato větší přesnost než typ `double`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="8fed3-204">Termín **Pevná desetinná** znamená, že desetinné čárky (nebo řádová) čárka nepohybuje.</span><span class="sxs-lookup"><span data-stu-id="8fed3-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="8fed3-205">Podívejme se na to:</span><span class="sxs-lookup"><span data-stu-id="8fed3-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="8fed3-206">Všimněte si, že je rozsah menší, než `double` typu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="8fed3-207">Větší přesnost typu decimal můžete zobrazit pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8fed3-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="8fed3-208">`M` Přípona u čísel je způsob, jak naznačit, že má konstanta používat `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="8fed3-209">Všimněte si, že výsledek s typem decimal má napravo od desetinné čárky víc číslic.</span><span class="sxs-lookup"><span data-stu-id="8fed3-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="8fed3-210">***Výzvy***</span><span class="sxs-lookup"><span data-stu-id="8fed3-210">***Challenge***</span></span>

<span data-ttu-id="8fed3-211">Teď, když jste se seznámili s různými typy čísel, psát kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru.</span><span class="sxs-lookup"><span data-stu-id="8fed3-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="8fed3-212">Mějte na paměti, že obsah kruhu je jako poloměr na druhou krát číslo PÍ.</span><span class="sxs-lookup"><span data-stu-id="8fed3-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="8fed3-213">Jeden pomocný parametr: .NET obsahuje pro číslo PÍ konstantu <xref:System.Math.PI?displayProperty=nameWithType> , můžete použít pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8fed3-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="8fed3-214">By vám vyjít výsledek mezi 19 a 20.</span><span class="sxs-lookup"><span data-stu-id="8fed3-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="8fed3-215">Můžete zkontrolovat odpověď podle [prohlížení dokončení ukázkového kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="8fed3-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="8fed3-216">Pokud chcete, vyzkoušejte i další vzorce.</span><span class="sxs-lookup"><span data-stu-id="8fed3-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="8fed3-217">Dokončili jste "čísla v C#" rychlý start.</span><span class="sxs-lookup"><span data-stu-id="8fed3-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="8fed3-218">Můžete pokračovat [větve a smyčky](branches-and-loops-local.md) rychlý start ve svém vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="8fed3-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="8fed3-219">Další informace o číslech v jazyce C# v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="8fed3-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="8fed3-220">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="8fed3-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="8fed3-221">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="8fed3-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="8fed3-222">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="8fed3-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="8fed3-223">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="8fed3-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="8fed3-224">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="8fed3-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
