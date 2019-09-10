---
title: Čísla v C# úvodu k C# kurzu
description: Naučte C# se prozkoumat číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850691"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="174ab-103">Manipulace s čísly integrálových a plovoucích bodů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="174ab-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="174ab-104">V tomto kurzu se naučíte, aby se číselné C# typy v interaktivně.</span><span class="sxs-lookup"><span data-stu-id="174ab-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="174ab-105">Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód.</span><span class="sxs-lookup"><span data-stu-id="174ab-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="174ab-106">Kurz obsahuje řadu lekcí, které prozkoumají čísla a matematické operace v C#.</span><span class="sxs-lookup"><span data-stu-id="174ab-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="174ab-107">V těchto lekcích se naučíte základy C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="174ab-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="174ab-108">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="174ab-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="174ab-109">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="174ab-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="174ab-110">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="174ab-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="174ab-111">Prozkoumat celočíselné matematické</span><span class="sxs-lookup"><span data-stu-id="174ab-111">Explore integer math</span></span>

<span data-ttu-id="174ab-112">Vytvořte adresář s názvem **Numbers – rychlý Start**.</span><span class="sxs-lookup"><span data-stu-id="174ab-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="174ab-113">Zajistěte, aby byl aktuální `dotnet new console -n NumbersInCSharp -o .`adresář a běžel.</span><span class="sxs-lookup"><span data-stu-id="174ab-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="174ab-114">V oblíbeném editoru otevřete **program.cs** a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím:</span><span class="sxs-lookup"><span data-stu-id="174ab-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="174ab-115">Spusťte tento kód zadáním `dotnet run` do příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="174ab-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="174ab-116">Právě jste viděli jednu ze základních matematických operací s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="174ab-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="174ab-117">Typ představuje celé číslo, kladné nebo záporné celé číslo. `int`</span><span class="sxs-lookup"><span data-stu-id="174ab-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="174ab-118">`+` Symbol se používá pro sčítání.</span><span class="sxs-lookup"><span data-stu-id="174ab-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="174ab-119">Mezi další běžné matematické operace pro celá čísla patří:</span><span class="sxs-lookup"><span data-stu-id="174ab-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="174ab-120">`-`pro odčítání</span><span class="sxs-lookup"><span data-stu-id="174ab-120">`-` for subtraction</span></span>
- <span data-ttu-id="174ab-121">`*`pro násobení</span><span class="sxs-lookup"><span data-stu-id="174ab-121">`*` for multiplication</span></span>
- <span data-ttu-id="174ab-122">`/`pro dělení</span><span class="sxs-lookup"><span data-stu-id="174ab-122">`/` for division</span></span>

<span data-ttu-id="174ab-123">Začněte tím, že prozkoumáte tyto různé operace.</span><span class="sxs-lookup"><span data-stu-id="174ab-123">Start by exploring those different operations.</span></span> <span data-ttu-id="174ab-124">Přidejte tyto řádky za řádek, který zapisuje hodnotu `c`:</span><span class="sxs-lookup"><span data-stu-id="174ab-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="174ab-125">Spusťte tento kód zadáním `dotnet run` do příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="174ab-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="174ab-126">Můžete také experimentovat při provádění více matematických operací na stejném řádku, pokud byste chtěli.</span><span class="sxs-lookup"><span data-stu-id="174ab-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="174ab-127">Zkuste `c = a + b - 12 * 17;` například.</span><span class="sxs-lookup"><span data-stu-id="174ab-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="174ab-128">Jsou povoleny kombinace proměnných a konstantních čísel.</span><span class="sxs-lookup"><span data-stu-id="174ab-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="174ab-129">Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby.</span><span class="sxs-lookup"><span data-stu-id="174ab-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="174ab-130">**Kompilátor** tyto chyby vyhledá a nahlásí je.</span><span class="sxs-lookup"><span data-stu-id="174ab-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="174ab-131">Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.</span><span class="sxs-lookup"><span data-stu-id="174ab-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="174ab-132">Toto cvičení vám pomůže zjistit strukturu C# kódu.</span><span class="sxs-lookup"><span data-stu-id="174ab-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="174ab-133">Dokončili jste první krok.</span><span class="sxs-lookup"><span data-stu-id="174ab-133">You've finished the first step.</span></span> <span data-ttu-id="174ab-134">Než začnete s další částí, přesuňte aktuální kód do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="174ab-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="174ab-135">Díky tomu je snazší začít pracovat s novým příkladem.</span><span class="sxs-lookup"><span data-stu-id="174ab-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="174ab-136">Přejmenujte `WorkingWithIntegers` `Main` `WorkingWithIntegers`metodu na a napište novou metodu, která volá. `Main`</span><span class="sxs-lookup"><span data-stu-id="174ab-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="174ab-137">Až budete hotovi, váš kód by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="174ab-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="174ab-138">Prozkoumat pořadí operací</span><span class="sxs-lookup"><span data-stu-id="174ab-138">Explore order of operations</span></span>

<span data-ttu-id="174ab-139">Zakomentujte volání do `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="174ab-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="174ab-140">Výsledkem je, že při práci v této části bude výstup méně zbytečný:</span><span class="sxs-lookup"><span data-stu-id="174ab-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="174ab-141">Spustí komentář v C#. `//`</span><span class="sxs-lookup"><span data-stu-id="174ab-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="174ab-142">Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód.</span><span class="sxs-lookup"><span data-stu-id="174ab-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="174ab-143">Kompilátor negeneruje žádný spustitelný kód z komentářů.</span><span class="sxs-lookup"><span data-stu-id="174ab-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="174ab-144">C# Jazyk definuje prioritu různých matematických operací s pravidly, která jsou v souladu s pravidly, která jste se naučili v matematice.</span><span class="sxs-lookup"><span data-stu-id="174ab-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="174ab-145">Násobení a dělení mají přednost před sčítáním a odčítáním.</span><span class="sxs-lookup"><span data-stu-id="174ab-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="174ab-146">Prozkoumejte to přidáním následujícího kódu do `Main` metody a provedením příkazu: `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="174ab-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="174ab-147">Výstup ukazuje, že násobení je provedeno před sčítáním.</span><span class="sxs-lookup"><span data-stu-id="174ab-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="174ab-148">Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operací, které chcete provést jako první.</span><span class="sxs-lookup"><span data-stu-id="174ab-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="174ab-149">Přidejte následující řádky a spusťte znovu:</span><span class="sxs-lookup"><span data-stu-id="174ab-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="174ab-150">Kombinování různých operací vám umožní prozkoumat víc.</span><span class="sxs-lookup"><span data-stu-id="174ab-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="174ab-151">V dolní `Main` části metody přidejte něco podobného jako následující řádky.</span><span class="sxs-lookup"><span data-stu-id="174ab-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="174ab-152">Zkuste `dotnet run` to znovu.</span><span class="sxs-lookup"><span data-stu-id="174ab-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="174ab-153">Možná jste si všimli zajímavého chování pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="174ab-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="174ab-154">Celočíselné dělení vždy vytváří celočíselný výsledek, i když byste očekávali, že by výsledek zahrnoval desítkovou nebo zlomkovou část.</span><span class="sxs-lookup"><span data-stu-id="174ab-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="174ab-155">Pokud jste toto chování neviděli, vyzkoušejte následující kód na konci vaší `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="174ab-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="174ab-156">Pro `dotnet run` zobrazení výsledků zadejte znovu.</span><span class="sxs-lookup"><span data-stu-id="174ab-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="174ab-157">Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="174ab-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="174ab-158">Zavolejte tuto novou metodu `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="174ab-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="174ab-159">Měli byste skončit přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="174ab-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="174ab-160">Prozkoumat celočíselnou přesnost a omezení</span><span class="sxs-lookup"><span data-stu-id="174ab-160">Explore integer precision and limits</span></span>

<span data-ttu-id="174ab-161">Poslední ukázka ukázala, že dělení celého čísla zkráte výsledek.</span><span class="sxs-lookup"><span data-stu-id="174ab-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="174ab-162">**Zbytek** můžete získat pomocí `%` operátoru **modulo** , znaku.</span><span class="sxs-lookup"><span data-stu-id="174ab-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="174ab-163">Vyzkoušejte následující kód v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="174ab-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="174ab-164">C# Celočíselný typ se liší od matematických celých čísel jiným způsobem: `int` typ má minimální a maximální limity.</span><span class="sxs-lookup"><span data-stu-id="174ab-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="174ab-165">Přidejte tento kód do `Main` metody, abyste viděli tato omezení:</span><span class="sxs-lookup"><span data-stu-id="174ab-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="174ab-166">Pokud výpočet vytvoří hodnotu, která překračuje tato omezení, **dojde k podtečení nebo** **podtečení** .</span><span class="sxs-lookup"><span data-stu-id="174ab-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="174ab-167">Odpověď se zobrazí jako zabalení od jednoho limitu k druhému.</span><span class="sxs-lookup"><span data-stu-id="174ab-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="174ab-168">Přidejte tyto dva řádky do `Main` metody, abyste viděli příklad:</span><span class="sxs-lookup"><span data-stu-id="174ab-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="174ab-169">Všimněte si, že odpověď se velmi blíží minimálnímu (zápornému) celému číslu.</span><span class="sxs-lookup"><span data-stu-id="174ab-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="174ab-170">Je stejný jako `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="174ab-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="174ab-171">Operace sčítání **přetéká** povolené hodnoty pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="174ab-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="174ab-172">Odpověď je velmi velké záporné číslo, protože přetečení se zalomí od největší možné celočíselné hodnoty k nejmenší.</span><span class="sxs-lookup"><span data-stu-id="174ab-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="174ab-173">Existují i jiné číselné typy s různými limity a přesností, které byste použili, `int` když typ nevyhovuje vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="174ab-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="174ab-174">Pojďme se podívat na další.</span><span class="sxs-lookup"><span data-stu-id="174ab-174">Let's explore those next.</span></span>

<span data-ttu-id="174ab-175">Později můžete kód, který jste napsali v této části, přesunout do samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="174ab-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="174ab-176">Pojmenujte ji `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="174ab-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="174ab-177">Práce s typem Double</span><span class="sxs-lookup"><span data-stu-id="174ab-177">Work with the double type</span></span>

<span data-ttu-id="174ab-178">`double` Číselný typ představuje číslo s dvojitou přesností a plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="174ab-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="174ab-179">Tyto výrazy můžou být pro vás nové.</span><span class="sxs-lookup"><span data-stu-id="174ab-179">Those terms may be new to you.</span></span> <span data-ttu-id="174ab-180">Číslo s **plovoucí desetinnou** čárkou je užitečné k vyjádření neintegrálních čísel, která mohou být velmi velká nebo malá.</span><span class="sxs-lookup"><span data-stu-id="174ab-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="174ab-181">**Dvojitá přesnost** znamená, že se tato čísla ukládají s větší přesností než s **jednoduchou přesností**.</span><span class="sxs-lookup"><span data-stu-id="174ab-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="174ab-182">Na moderních počítačích je častější používat dvojitou přesnost než čísla s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="174ab-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="174ab-183">Pojďme prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="174ab-183">Let's explore.</span></span> <span data-ttu-id="174ab-184">Přidejte následující kód a podívejte se na výsledek:</span><span class="sxs-lookup"><span data-stu-id="174ab-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="174ab-185">Všimněte si, že odpověď obsahuje desetinnou část podílu.</span><span class="sxs-lookup"><span data-stu-id="174ab-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="174ab-186">Vyzkoušejte trochu složitější výraz s dvojitou přesností:</span><span class="sxs-lookup"><span data-stu-id="174ab-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="174ab-187">Rozsah hodnoty Double je mnohem větší než celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="174ab-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="174ab-188">Vyzkoušejte následující kód, který jste doposud napsali:</span><span class="sxs-lookup"><span data-stu-id="174ab-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="174ab-189">Tyto hodnoty se tisknou v matematickém zápisu.</span><span class="sxs-lookup"><span data-stu-id="174ab-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="174ab-190">Číslo nalevo od `E` je mantisa.</span><span class="sxs-lookup"><span data-stu-id="174ab-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="174ab-191">Číslo vpravo je exponent, jako mocnina 10.</span><span class="sxs-lookup"><span data-stu-id="174ab-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="174ab-192">Stejně jako desítková čísla v matematických případech můžou C# být v uvozovkách chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="174ab-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="174ab-193">Vyzkoušejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="174ab-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="174ab-194">Víte, že `0.3` opakování není přesně stejné jako. `1/3`</span><span class="sxs-lookup"><span data-stu-id="174ab-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="174ab-195">***Výzev***</span><span class="sxs-lookup"><span data-stu-id="174ab-195">***Challenge***</span></span>

<span data-ttu-id="174ab-196">Zkuste další výpočty s velkými čísly, malými čísly, násobení a `double` dělení pomocí typu.</span><span class="sxs-lookup"><span data-stu-id="174ab-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="174ab-197">Vyzkoušejte složitější výpočty.</span><span class="sxs-lookup"><span data-stu-id="174ab-197">Try more complicated calculations.</span></span>

<span data-ttu-id="174ab-198">Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody.</span><span class="sxs-lookup"><span data-stu-id="174ab-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="174ab-199">Pojmenujte tuto `WorkWithDoubles`novou metodu.</span><span class="sxs-lookup"><span data-stu-id="174ab-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="174ab-200">Práce s pevnými typy bodů</span><span class="sxs-lookup"><span data-stu-id="174ab-200">Work with fixed point types</span></span>

<span data-ttu-id="174ab-201">Viděli jste základní číselné typy v C#: celá čísla a Dvojitá přesnost.</span><span class="sxs-lookup"><span data-stu-id="174ab-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="174ab-202">Existuje jeden další typ, který se naučí: `decimal` typ.</span><span class="sxs-lookup"><span data-stu-id="174ab-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="174ab-203">Typ má menší rozsah, ale větší přesnost než `double`. `decimal`</span><span class="sxs-lookup"><span data-stu-id="174ab-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="174ab-204">**Pevný** bod znamená, že desetinná čárka (nebo binární bod) nepřesouvá.</span><span class="sxs-lookup"><span data-stu-id="174ab-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="174ab-205">Podívejme se na to:</span><span class="sxs-lookup"><span data-stu-id="174ab-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="174ab-206">Všimněte si, že rozsah je menší než `double` typ.</span><span class="sxs-lookup"><span data-stu-id="174ab-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="174ab-207">Větší přesnost s typem Decimal můžete zobrazit tak, že zkusíte následující kód:</span><span class="sxs-lookup"><span data-stu-id="174ab-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="174ab-208">Přípona čísel představuje způsob, jakým by měl být `decimal` typ konstanty použit. `M`</span><span class="sxs-lookup"><span data-stu-id="174ab-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="174ab-209">Všimněte si, že matematický použití typu Decimal má na pravé straně desetinné čárky více číslic.</span><span class="sxs-lookup"><span data-stu-id="174ab-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="174ab-210">***Výzev***</span><span class="sxs-lookup"><span data-stu-id="174ab-210">***Challenge***</span></span>

<span data-ttu-id="174ab-211">Teď, když jste viděli různé číselné typy, napište kód, který vypočítá oblast kruhu, jehož poloměr je 2,50 centimetrů.</span><span class="sxs-lookup"><span data-stu-id="174ab-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="174ab-212">Pamatujte, že oblast kruhu je poloměr čtvercového vynásobený hodnotou pí.</span><span class="sxs-lookup"><span data-stu-id="174ab-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="174ab-213">Jedna Nápověda: .NET obsahuje konstantu pro PI, <xref:System.Math.PI?displayProperty=nameWithType> kterou můžete použít pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="174ab-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="174ab-214">Měli byste získat odpověď mezi 19 a 20.</span><span class="sxs-lookup"><span data-stu-id="174ab-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="174ab-215">Svou odpověď si můžete prohlédnout na [stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) .</span><span class="sxs-lookup"><span data-stu-id="174ab-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="174ab-216">Pokud chcete, zkuste použít jiné vzorce.</span><span class="sxs-lookup"><span data-stu-id="174ab-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="174ab-217">Dokončili jste rychlý Start s čísly C#.</span><span class="sxs-lookup"><span data-stu-id="174ab-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="174ab-218">Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="174ab-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="174ab-219">Další informace o číslech v C# najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="174ab-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="174ab-220">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="174ab-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="174ab-221">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="174ab-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="174ab-222">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="174ab-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="174ab-223">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="174ab-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="174ab-224">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="174ab-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
