---
title: Řetězec interpolace kurz – C# místní – elementy QuickStart
description: Tento rychlý start ukazuje, jak pomocí funkce interpolace řetězec jazyka C# lze zahrnout výsledky formátovaný výraz větší řetězce.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: 80b7a2c39094f1101e714b47f0e77f0a7c4907f2
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472760"
---
# <a name="string-interpolation"></a><span data-ttu-id="72261-103">Řetězec interpolace</span><span class="sxs-lookup"><span data-stu-id="72261-103">String interpolation</span></span>

<span data-ttu-id="72261-104">Tento rychlý start se naučíte, jak používat C# [řetězec interpolace](../language-reference/tokens/interpolated.md) vložení hodnoty do jednoho výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="72261-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="72261-105">Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="72261-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="72261-106">Rychlý Start obsahuje řadu lekce, které ukazují, jak a vložení hodnoty do řetězce formátu tyto hodnoty různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="72261-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="72261-107">Tento rychlý start očekává, že máte počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="72261-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="72261-108">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="72261-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="72261-109">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="72261-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="72261-110">Můžete také provést [interaktivní verze](interpolated-strings.yml) z tento rychlý start v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="72261-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="72261-111">Vytvoření interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="72261-111">Create an interpolated string</span></span>

<span data-ttu-id="72261-112">Vytvořte adresář s názvem **interpolované**.</span><span class="sxs-lookup"><span data-stu-id="72261-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="72261-113">Ho nastavit aktuální adresář a v okně konzoly spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="72261-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="72261-114">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="72261-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="72261-115">Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.WriteLine("Hello World!");` následujícím kódem, kde nahradíte `<name>` nahraďte názvem:</span><span class="sxs-lookup"><span data-stu-id="72261-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="72261-116">Zkuste tento kód zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="72261-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="72261-117">Když spustíte program, zobrazí jeden řetězec, který obsahuje název vaší v pozdrav.</span><span class="sxs-lookup"><span data-stu-id="72261-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="72261-118">Řetězec, které jsou součástí <xref:System.Console.WriteLine%2A> volání metody, které je *interpolované řetězce*.</span><span class="sxs-lookup"><span data-stu-id="72261-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="72261-119">Je typ šablony, která umožňuje vytvořit jeden řetězec (volat *způsobit řetězec*) z řetězce, který obsahuje integrovaný kód.</span><span class="sxs-lookup"><span data-stu-id="72261-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="72261-120">Interpolované řetězce jsou obzvláště užitečná pro vložení hodnoty do řetězec nebo řetězce zřetězení (spojení).</span><span class="sxs-lookup"><span data-stu-id="72261-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="72261-121">Tento jednoduchý příklad obsahuje dva elementy, které musí mít každý interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="72261-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="72261-122">Řetězcový literál, který začíná `$` znak před jeho otevření nabídky označit znak.</span><span class="sxs-lookup"><span data-stu-id="72261-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="72261-123">Nesmí být žádné mezery mezi `$` symbolů a znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="72261-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="72261-124">(Pokud byste chtěli vidět co se stane, když obsahují jeden, mezeru po vložení `$` znak, soubor uložte a program spusťte znovu zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="72261-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="72261-125">Jazyce C# kompilátoru zobrazí chybovou zprávu, "Chyba CS1056: Neočekávaný znak"$"".)</span><span class="sxs-lookup"><span data-stu-id="72261-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="72261-126">Jeden nebo více *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="72261-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="72261-127">Interpolované výrazu je indikován otevírací a uzavírací závorku (`{` a `}`).</span><span class="sxs-lookup"><span data-stu-id="72261-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="72261-128">Můžete vložit jakékoli C# výraz, který vrací hodnotu (včetně `null`) uvnitř složené závorky.</span><span class="sxs-lookup"><span data-stu-id="72261-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="72261-129">Nyní si vyzkoušíte několik další příklady interpolace řetězce, pomocí některé jiné datové typy.</span><span class="sxs-lookup"><span data-stu-id="72261-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="72261-130">Zahrnout různé datové typy</span><span class="sxs-lookup"><span data-stu-id="72261-130">Include different data types</span></span>

<span data-ttu-id="72261-131">V předchozí části použít řetězec interpolace vložit jeden řetězec uvnitř jiného.</span><span class="sxs-lookup"><span data-stu-id="72261-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="72261-132">Výsledek interpolované výraz může být jakékoli datového typu, ale.</span><span class="sxs-lookup"><span data-stu-id="72261-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="72261-133">Umožňuje zahrnout hodnoty různých datových typů v interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="72261-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="72261-134">V následujícím příkladu se nejdřív jsme definovali [– třída](../programming-guide/classes-and-structs/classes.md) datový typ `Vegetable` který má `Name` [vlastnost](../properties.md) a `ToString` [metoda](../methods.md), které [přepsání](../language-reference/keywords/override.md) chování <xref:System.Object.ToString?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="72261-134">In the following example, first, we define a [class](../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` [method](../methods.md), which [overrides](../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="72261-135">[ `public` – Modifikátor přístupu](../language-reference/keywords/public.md) zpřístupní dané metody žádný kód klienta získat řetězcovou reprezentaci `Vegetable` instance.</span><span class="sxs-lookup"><span data-stu-id="72261-135">The [`public` access modifier](../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="72261-136">V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnost, která je inicializován v `Vegetable` [konstruktor](../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="72261-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="72261-137">Poté vytvoříme instanci `Vegetable` pomocí [ `new` – klíčové slovo](../language-reference/keywords/new-operator.md) a poskytuje název parametr pro konstruktor `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="72261-137">Then we create an instance of the `Vegetable` class by using [`new` keyword](../language-reference/keywords/new-operator.md) and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="72261-138">Nakonec zahrnuta `item` proměnné do interpolované řetězce, který také obsahuje <xref:System.DateTime> hodnotu, <xref:System.Decimal> hodnotu a `Unit` [– výčet](../programming-guide/enumeration-types.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72261-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="72261-139">Nahraďte kód C# ve svém editoru následujícím kódem a pak použijte `dotnet run` příkaz spouštět:</span><span class="sxs-lookup"><span data-stu-id="72261-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
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

<span data-ttu-id="72261-140">Všimněte si, že interpolované výraz `item` interpolované řetězce přeloží na text "Lilek" ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="72261-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="72261-141">Důvodem je, že pokud typ výsledku výrazu není řetězec, výsledek je přeložit na řetězec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="72261-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="72261-142">Pokud je výsledkem výrazu interpolované `null`, prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>) se používá.</span><span class="sxs-lookup"><span data-stu-id="72261-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="72261-143">Pokud není vyhodnocení interpolované výraz `null`, obvykle `ToString` je volána metoda typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="72261-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="72261-144">Toto můžete otestovat aktualizací implementace `Vegetable.ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="72261-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="72261-145">Nemusí i potřebujete implementovat `ToString` metoda vzhledem k tomu, že každý typ má některé implementace této metody.</span><span class="sxs-lookup"><span data-stu-id="72261-145">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="72261-146">Abyste to mohli otestovat, komentář definice `Vegetable.ToString` metoda v příkladu (k tomu, put symbol komentáře `//`, úrovních před ním).</span><span class="sxs-lookup"><span data-stu-id="72261-146">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="72261-147">Ve výstupu řetězec "Lilek" nahrazuje plně kvalifikovaného názvu ("rostlinné" v tomto příkladu), což je výchozí chování z <xref:System.Object.ToString?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="72261-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="72261-148">Výchozí chování `ToString` metodou pro hodnotu výčtu je vrátí řetězcovou reprezentaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="72261-148">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="72261-149">Ve výstupu z tohoto příkladu datum je příliš přesné (cenu lilek nemění za sekundu) a hodnotu ceny neznamená jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="72261-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="72261-150">V další části dozvíte, jak vyřešit tyto problémy kontrolou formát řetězcové vyjádření výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="72261-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="72261-151">Ovládací prvek formátování interpolované výrazy</span><span class="sxs-lookup"><span data-stu-id="72261-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="72261-152">V předchozí části byly dva řetězce chybně formátovaný vložena do řetězce výsledek.</span><span class="sxs-lookup"><span data-stu-id="72261-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="72261-153">Jeden se hodnoty data a času, pro kterou se příslušná pouze datum.</span><span class="sxs-lookup"><span data-stu-id="72261-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="72261-154">Druhá se ceny, které nebylo signalizovat jeho jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="72261-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="72261-155">Obě tyto chyby lze snadno adresu.</span><span class="sxs-lookup"><span data-stu-id="72261-155">Both issues are easy to address.</span></span> <span data-ttu-id="72261-156">Řetězec interpolace umožňuje určit *řetězce formátu* které řídí formátování konkrétní typy.</span><span class="sxs-lookup"><span data-stu-id="72261-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="72261-157">Upravit volání `Console.WriteLine` z předchozího příkladu zahrnout řetězce formátu pro data a cena výrazy, jak je znázorněno na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="72261-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="72261-158">Zadejte řetězec, ve formátu podle interpolované výraz s dvojtečkou (":") a řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="72261-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="72261-159">"d" je [řetězec formátu standardní hodnoty data a času](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) představující formát krátkého data.</span><span class="sxs-lookup"><span data-stu-id="72261-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="72261-160">Je "C2" [standardního řetězce formátu čísel](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) představující číslo jako hodnotu měny s dvě číslice za desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="72261-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="72261-161">Počet typů v na knihovny .NET podporují předdefinovanou sadu řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="72261-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="72261-162">Mezi ně patří všechny číselnými typy a typy data a času.</span><span class="sxs-lookup"><span data-stu-id="72261-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="72261-163">Úplný seznam typů, které podporují řetězce formátu najdete v tématu [řetězce formátu a typy knihovna tříd rozhraní .NET](../../standard/base-types/formatting-types.md#stringRef) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="72261-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="72261-164">Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když provedete změny, znovu spusťte aplikaci a zjistěte, jak vliv budou změny mít formátování data a času a číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="72261-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="72261-165">Změňte "d" v `{date:d}` k "t" (zobrazíte na formát krátkého času), "y" (zobrazíte za rok a měsíc) a "rrrr" (pro zobrazení v roce jako čtyřmístné číslo).</span><span class="sxs-lookup"><span data-stu-id="72261-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="72261-166">Změňte "C2" v `{price:C2}` "e" (pro exponenciální zápis) a "F3" (pro číselná hodnota se tři číslice za desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="72261-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="72261-167">Kromě řízení, formátování, můžete také ovládat šířku pole a zarovnání formátované řetězce, které jsou zahrnuté ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="72261-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="72261-168">V další části dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="72261-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="72261-169">Řídit šířku pole a zarovnání interpolované výrazů</span><span class="sxs-lookup"><span data-stu-id="72261-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="72261-170">Normálně Pokud je výsledkem výrazu interpolované formátována na řetězec, tento řetězec je součástí výsledný řetězec bez počáteční nebo koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="72261-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="72261-171">Zejména při práci s sadu dat, bude možné řídit šířku pole a zarovnání textu pomáhá k vytváření srozumitelnější výstupu.</span><span class="sxs-lookup"><span data-stu-id="72261-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="72261-172">Toto nahraďte všechny kód v textovém editoru následujícím kódem zobrazíte zadáním `dotnet run` spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="72261-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="72261-173">Názvy autoři jsou zarovnaný doleva a názvy, které vytvořil zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="72261-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="72261-174">Zadejte zarovnání přidáním čárkou (",") po interpolované výrazu a určení *minimální* pole Šířka.</span><span class="sxs-lookup"><span data-stu-id="72261-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="72261-175">Pokud zadaná hodnota je kladné číslo, je pole zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="72261-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="72261-176">Pokud je na záporné číslo, pole je zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="72261-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="72261-177">Zkuste odebrat záporné přihlásí z `{"Author",-25}` a `{title.Key,-25}` kód a spusťte v příkladu znovu, protože následující kód:</span><span class="sxs-lookup"><span data-stu-id="72261-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="72261-178">Čas, informace o autorovi je zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="72261-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="72261-179">Můžete kombinovat specifikace zarovnání a řetězec formátu pro jeden výraz interpolované.</span><span class="sxs-lookup"><span data-stu-id="72261-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="72261-180">K tomu, zadejte zarovnání nejprve následovaný dvojtečkou a řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="72261-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="72261-181">Nahraďte kód uvnitř `Main` metoda následujícím kódem, který zobrazuje tři formátované řetězce s definované šířky polí.</span><span class="sxs-lookup"><span data-stu-id="72261-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="72261-182">Potom spusťte program zadáním `dotnet run` příkaz.</span><span class="sxs-lookup"><span data-stu-id="72261-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="72261-183">Výstup bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="72261-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="72261-184">Jste dokončili rychlé spuštění interpolace řetězec.</span><span class="sxs-lookup"><span data-stu-id="72261-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="72261-185">Můžete pokračovat [seznamu kolekce](arrays-and-collections.md) rychlé spuštění ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="72261-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="72261-186">Další informace najdete v tématu [řetězec interpolace](../language-reference/tokens/interpolated.md) tématu a [řetězec interpolace v jazyce C#](../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="72261-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
