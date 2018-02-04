---
title: "Interpolované řetězce kurz – C# místní – elementy QuickStart"
description: "V tento rychlý start o interpolované řetězce zapisovat do incude výsledek výrazu v řetězci větší kód C#."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 3cd9fc23dba104f92255b031eef32f80cca915b0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="37a24-103">Interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="37a24-103">Interpolated strings</span></span>

<span data-ttu-id="37a24-104">Tento rychlý start se naučíte, jak používat interpolované řetězce v jazyce C# k vložení hodnoty do řetězec jeden výstup.</span><span class="sxs-lookup"><span data-stu-id="37a24-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="37a24-105">Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="37a24-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="37a24-106">Rychlý Start obsahuje řadu lekce, které vložení hodnoty do řetězce a formátování tyto hodnoty různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="37a24-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="37a24-107">Tento rychlý start očekává, že máte počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="37a24-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="37a24-108">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="37a24-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="37a24-109">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="37a24-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="37a24-110">Vytvoření interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="37a24-110">Create an interpolated string</span></span>

<span data-ttu-id="37a24-111">Vytvořte adresář s názvem **interpolované rychlý Start**.</span><span class="sxs-lookup"><span data-stu-id="37a24-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="37a24-112">Ho nastavit aktuální adresář a v okně konzoly spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="37a24-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="37a24-113">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="37a24-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="37a24-114">Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.WriteLine("Hello World!");` následujícím kódem, kde nahradíte `<name>` nahraďte názvem:</span><span class="sxs-lookup"><span data-stu-id="37a24-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="37a24-115">Zkuste tento kód zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="37a24-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="37a24-116">Když spustíte program, zobrazí jeden řetězec, který obsahuje název vaší v pozdrav.</span><span class="sxs-lookup"><span data-stu-id="37a24-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="37a24-117">Řetězec, které jsou součástí <xref:System.Console.WriteLine%2A> volání metody, které je *interpolované řetězce*.</span><span class="sxs-lookup"><span data-stu-id="37a24-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="37a24-118">Je typ šablony, která umožňuje vytvořit jeden řetězec (volat *způsobit řetězec*) z řetězce, který obsahuje integrovaný kód.</span><span class="sxs-lookup"><span data-stu-id="37a24-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="37a24-119">Interpolované řetězce jsou obzvláště užitečná pro vložení hodnoty do řetězec nebo řetězce zřetězení (spojení).</span><span class="sxs-lookup"><span data-stu-id="37a24-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="37a24-120">Tento jednoduchý příklad obsahuje dva elementy, které musí mít každý interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="37a24-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="37a24-121">Řetězcový literál, který začíná `$` znak před jeho otevření nabídky označit znak.</span><span class="sxs-lookup"><span data-stu-id="37a24-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="37a24-122">Nesmí být žádné mezery mezi `$` symbolů a znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="37a24-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="37a24-123">(Pokud byste chtěli vidět co se stane, když obsahují jeden, mezeru po vložení `$` znak, soubor uložte a program spusťte znovu zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="37a24-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="37a24-124">Jazyce C# kompilátoru zobrazí chybovou zprávu, "Chyba CS1056: Neočekávaný znak"$"".)</span><span class="sxs-lookup"><span data-stu-id="37a24-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="37a24-125">Jeden nebo více *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="37a24-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="37a24-126">Interpolované výrazu je indikován otevírací a uzavírací závorku (`{` a `}`).</span><span class="sxs-lookup"><span data-stu-id="37a24-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="37a24-127">Můžete vložit jakékoli C# výraz, který vrací hodnotu (včetně `null`) uvnitř složené závorky.</span><span class="sxs-lookup"><span data-stu-id="37a24-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="37a24-128">Nyní si vyzkoušíte několik příkladů více interpolované řetězce s jiné datové typy.</span><span class="sxs-lookup"><span data-stu-id="37a24-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="37a24-129">Zahrnout různé datové typy</span><span class="sxs-lookup"><span data-stu-id="37a24-129">Include different data types</span></span>

<span data-ttu-id="37a24-130">V předchozí části použít interpolované řetězce k vložení jednoho řetězce v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="37a24-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="37a24-131">Výraz interpolované řetězce mohou být jakéhokoli typu dat, ale.</span><span class="sxs-lookup"><span data-stu-id="37a24-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="37a24-132">Nyní si vyzkoušíte interpolované řetězec, který obsahuje hodnoty více datových typů.</span><span class="sxs-lookup"><span data-stu-id="37a24-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="37a24-133">Následující příklad obsahuje interpolované výrazy s `Vegetable` objektu, členem `Unit` výčtu <xref:System.DateTime> hodnotu a <xref:System.Decimal> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="37a24-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="37a24-134">Nahraďte kód C# ve svém editoru následujícím kódem a pak použijte `console run` příkaz spouštět:</span><span class="sxs-lookup"><span data-stu-id="37a24-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```
    
<span data-ttu-id="37a24-135">Všimněte si, že druhá interpolované výraz obsahuje `item` objektu ve výsledném řetězci, který se zobrazí konzole a v takovém případě je řetězec "Lilek" vložena do řetězce výsledek.</span><span class="sxs-lookup"><span data-stu-id="37a24-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="37a24-136">Důvodem je, že pokud není typ výrazu interpolované řetězce, kompilátor jazyka C# provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="37a24-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="37a24-137">Pokud je interpolované výraz `null`, interpolované výraz vrátí prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="37a24-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="37a24-138">Pokud není interpolované výraz `null`, `ToString` je volána metoda typu interpolované výrazu.</span><span class="sxs-lookup"><span data-stu-id="37a24-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="37a24-139">Toto můžete otestovat pomocí komentářů se definice `Vegetable.ToString` metoda v příkladu umístěním symbol komentáře (`//`) úrovních před ním.</span><span class="sxs-lookup"><span data-stu-id="37a24-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="37a24-140">Ve výstupu řetězec "Lilek" nahrazuje typ název, "Zeleniny", což je výchozí chování <xref:System.Object.ToString?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="37a24-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="37a24-141">Ve výstupu z tohoto příkladu datum je příliš přesné (cenu lilek nebude měnit druhou) a hodnotu ceny neznamená jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="37a24-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="37a24-142">V další části dozvíte, jak tyto problémy vyřešit kontrolou formát řetězce vrácené interpolované výrazy.</span><span class="sxs-lookup"><span data-stu-id="37a24-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="37a24-143">Ovládací prvek formátování interpolované výrazy</span><span class="sxs-lookup"><span data-stu-id="37a24-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="37a24-144">V předchozí části byly dva řetězce chybně formátovaný vložena do řetězce výsledek.</span><span class="sxs-lookup"><span data-stu-id="37a24-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="37a24-145">Jeden se hodnoty data a času, pro kterou se příslušná pouze datum.</span><span class="sxs-lookup"><span data-stu-id="37a24-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="37a24-146">Druhý byl ceníku, který neobsahoval pokyn jeho jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="37a24-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="37a24-147">Obě tyto chyby lze snadno adresu.</span><span class="sxs-lookup"><span data-stu-id="37a24-147">Both issues are easy to address.</span></span> <span data-ttu-id="37a24-148">Interpolované výrazy může zahrnovat *řetězce formátu* které řídí formátování konkrétní typy.</span><span class="sxs-lookup"><span data-stu-id="37a24-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="37a24-149">Upravit volání `Console.WriteLine` z předchozího příkladu zahrnout specifikace formátu pro pole data a ceny, jak je znázorněno na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="37a24-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="37a24-150">Pomocí následujících interpolované výraz s dvojtečkou a řetězec formátu zadáte řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="37a24-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="37a24-151">"d" je [řetězec formátu standardní hodnoty data a času](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) představující formát krátkého data.</span><span class="sxs-lookup"><span data-stu-id="37a24-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="37a24-152">Je "C2" [standardního řetězce formátu čísel](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) představující číslo jako hodnotu měny s dvě číslice za desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="37a24-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="37a24-153">Počet typů v rozhraní .NET standardní knihovny podporují předdefinovanou sadu řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="37a24-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="37a24-154">Mezi ně patří všechny číselnými typy a typy data a času.</span><span class="sxs-lookup"><span data-stu-id="37a24-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="37a24-155">Úplný seznam typů, které podporují řetězce formátu najdete v tématu [řetězce formátu a typy knihovna tříd rozhraní .NET](../../standard/base-types/formatting-types.md#stringRef) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="37a24-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="37a24-156">Žádný typ, může podporovat sadu řetězce formátu, a také lze vytvářet vlastní rozšíření formátování, které poskytují vlastní formátování pro existující typy.</span><span class="sxs-lookup"><span data-stu-id="37a24-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="37a24-157">Informace o vlastní formátování tím, že poskytuje <xref:System.ICustomFormatter> implementaci, najdete v části [vlastní formátování pomocí ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="37a24-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="37a24-158">Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když provedete změny, znovu spusťte aplikaci a zjistěte, jak vliv budou změny mít formátování data a času a číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="37a24-158">Try modifying the the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="37a24-159">Změňte "d" v `{date:d}` k "t" (zobrazíte na formát krátkého času), "y" (zobrazíte za rok a měsíc) a "rrrr" (pro zobrazení v roce jako čtyřmístné číslo).</span><span class="sxs-lookup"><span data-stu-id="37a24-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="37a24-160">Změňte "C2" v `{price:C2}` "e" (pro exponenciální zápis) a "F3" (pro číselná hodnota se tři číslice za desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="37a24-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="37a24-161">Kromě řízení, formátování, můžete také ovládat šířku pole a zarovnání vrácený výraz interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="37a24-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="37a24-162">V další části dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="37a24-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="37a24-163">Řídit šířku pole a zarovnání interpolované výrazů</span><span class="sxs-lookup"><span data-stu-id="37a24-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="37a24-164">Obvykle po řetězec vrácený interpolované výrazu je zahrnutý ve výsledném řetězci, nemá žádné počáteční a koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="37a24-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="37a24-165">Platí to hlavně o instancích, ve kterých pracujete s sadu dat, interpolované výrazy umožňují určit šířku pole a jeho zarovnání.</span><span class="sxs-lookup"><span data-stu-id="37a24-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="37a24-166">Toto nahraďte všechny kód v textovém editoru následujícím kódem zobrazíte zadáním `console run` spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="37a24-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
<span data-ttu-id="37a24-167">Názvy autoři jsou zarovnaný doleva a názvy, které vytvořil zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="37a24-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="37a24-168">Zadejte zarovnání přidáním čárkou (",") po ve výrazu a určení šířku pole.</span><span class="sxs-lookup"><span data-stu-id="37a24-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="37a24-169">Pokud je šířka pole kladné číslo, pole je zarovnaný doprava:</span><span class="sxs-lookup"><span data-stu-id="37a24-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="37a24-170">Pokud je šířka pole na záporné číslo, pole je zarovnaný doleva:</span><span class="sxs-lookup"><span data-stu-id="37a24-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="37a24-171">Zkuste odebrat záporné přihlásí z `{"Author",-25}` a `{title.Key,-25}` interpolované výrazy a spusťte v příkladu znovu, protože následující kód:</span><span class="sxs-lookup"><span data-stu-id="37a24-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

<span data-ttu-id="37a24-172">Čas, informace o autorovi je zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="37a24-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="37a24-173">Šířka pole a řetězec formátu v jediném interpolované výrazu můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="37a24-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="37a24-174">Šířka pole je nejdříve následovaný dvojtečkou a řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="37a24-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="37a24-175">Nahraďte kód uvnitř `Main` metoda následujícím kódem, který zobrazuje tři formátované řetězce s definované šířky polí.</span><span class="sxs-lookup"><span data-stu-id="37a24-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="37a24-176">Potom spusťte program zadáním `dotnet run` příkaz.</span><span class="sxs-lookup"><span data-stu-id="37a24-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="37a24-177">Výstup bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="37a24-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="37a24-178">Jste dokončili rychlé spuštění interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="37a24-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="37a24-179">Můžete pokračovat [pole a kolekce](arrays-and-collections.md) rychlé spuštění ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="37a24-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="37a24-180">Další informace o práci s interpolované řetězce v [interpolované řetězce](../language-reference/keywords/interpolated-strings.md) téma v referenční dokumentace jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="37a24-180">You can learn more about working with interpolated strings in the [Interpolated Strings](../language-reference/keywords/interpolated-strings.md) topic in the C# Reference.</span></span>

