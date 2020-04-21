---
title: Kurz interpolace řetězců – c#
description: Tento kurz ukazuje, jak pomocí funkce interpolace řetězce Jazyka C# zahrnout formátovaný výraz výsledky ve větším řetězci.
ms.date: 10/23/2018
ms.openlocfilehash: 22637895f241585bac4909479f225bf3cb581614
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738286"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="3722d-103">Použití interpolace řetězců k vytvoření formátovaných řetězců</span><span class="sxs-lookup"><span data-stu-id="3722d-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="3722d-104">Tento kurz vás naučí, jak pomocí [interpolace řetězce](../../language-reference/tokens/interpolated.md) Jazyka C# vložit hodnoty do jednoho výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="3722d-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="3722d-105">Napíšete kód Jazyka C# a zobrazí výsledky kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="3722d-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="3722d-106">Kurz obsahuje řadu lekcí, které vám ukáží, jak vložit hodnoty do řetězce a formátovat tyto hodnoty různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="3722d-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="3722d-107">Tento kurz očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="3722d-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="3722d-108">Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="3722d-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="3722d-109">Můžete také dokončit [interaktivní verzi](interpolated-strings.yml) tohoto kurzu ve vašem prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="3722d-109">You can also complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="3722d-110">Vytvoření interpolovaného řetězce</span><span class="sxs-lookup"><span data-stu-id="3722d-110">Create an interpolated string</span></span>

<span data-ttu-id="3722d-111">Vytvořte adresář s názvem *Interpolované*.</span><span class="sxs-lookup"><span data-stu-id="3722d-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="3722d-112">Zmizte z něj aktuální adresář a spusťte z okna konzoly následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3722d-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="3722d-113">Tento příkaz vytvoří novou aplikaci konzoly .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="3722d-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="3722d-114">Otevřete *Program.cs* v oblíbeném editoru a nahraďte `Console.WriteLine("Hello World!");` `<name>` řádek následujícím kódem, kde nahradíte svým jménem:</span><span class="sxs-lookup"><span data-stu-id="3722d-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="3722d-115">Zkuste tento kód `dotnet run` zadáním do okna konzole.</span><span class="sxs-lookup"><span data-stu-id="3722d-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="3722d-116">Po spuštění programu se zobrazí jeden řetězec s pozdravem, který obsahuje vaše jméno.</span><span class="sxs-lookup"><span data-stu-id="3722d-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="3722d-117">Řetězec obsažený ve <xref:System.Console.WriteLine%2A> volání metody je *interpolovaný řetězcový výraz*.</span><span class="sxs-lookup"><span data-stu-id="3722d-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="3722d-118">Jedná se o druh šablony, který umožňuje vytvořit jeden řetězec (označovaný jako *výsledný řetězec*) z řetězce obsahujícího vložený kód.</span><span class="sxs-lookup"><span data-stu-id="3722d-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="3722d-119">Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.</span><span class="sxs-lookup"><span data-stu-id="3722d-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="3722d-120">Tento jednoduchý příklad obsahuje oba prvky, které jsou v každém interpolovaném řetězci povinné:</span><span class="sxs-lookup"><span data-stu-id="3722d-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="3722d-121">Řetězcový literál, který začíná znakem `$` před počátečním znakem uvozovek.</span><span class="sxs-lookup"><span data-stu-id="3722d-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="3722d-122">Mezi symbolem `$` a znakem uvozovek nesmí být žádné mezery.</span><span class="sxs-lookup"><span data-stu-id="3722d-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="3722d-123">(Pokud chcete zjistit, co se stane, pokud jej zahrnete, vložte za `$` znak mezeru, uložte soubor a znovu spusťte program zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3722d-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="3722d-124">Kompilátor Jazyka C# zobrazí chybovou zprávu "error CS1056: Unexpected character '$'".)</span><span class="sxs-lookup"><span data-stu-id="3722d-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="3722d-125">Jeden nebo více *interpolačních výrazů*.</span><span class="sxs-lookup"><span data-stu-id="3722d-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="3722d-126">Interpolační výraz je označen otevírací a uzavírací složenou závorkou (`{` a `}`).</span><span class="sxs-lookup"><span data-stu-id="3722d-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="3722d-127">Do složených závorek můžete vložit libovolný výraz v C#, který vrací hodnotu (včetně hodnoty `null`).</span><span class="sxs-lookup"><span data-stu-id="3722d-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="3722d-128">Zkusme několik dalších příkladů interpolace řetězce s některými jinými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="3722d-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="3722d-129">Zahrnutí různých datových typů</span><span class="sxs-lookup"><span data-stu-id="3722d-129">Include different data types</span></span>

<span data-ttu-id="3722d-130">V předchozí části jste použili interpolaci řetězce k vložení jednoho řetězce do jiného.</span><span class="sxs-lookup"><span data-stu-id="3722d-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="3722d-131">Výsledkem interpolačního výrazu však může být libovolný datový typ.</span><span class="sxs-lookup"><span data-stu-id="3722d-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="3722d-132">Zahrňme hodnoty různých datových typů do interpolovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="3722d-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="3722d-133">V následujícím příkladu nejprve definujeme `Vegetable` datový `Name` typ [třídy,](../../programming-guide/classes-and-structs/classes.md) který má [vlastnost](../../properties.md) <xref:System.Object.ToString?displayProperty=nameWithType> a `ToString` [metodu](../../methods.md), která [přepíše](../../language-reference/keywords/override.md) chování metody.</span><span class="sxs-lookup"><span data-stu-id="3722d-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3722d-134">[ `public` Modifikátor přístupu](../../language-reference/keywords/public.md) zpřístupňuje tuto metodu pro `Vegetable` libovolný kód klienta, aby získal řetězcovou reprezentaci instance.</span><span class="sxs-lookup"><span data-stu-id="3722d-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="3722d-135">V příkladu `Vegetable.ToString` metoda vrátí hodnotu vlastnosti, `Name` která `Vegetable` je inicializována na [konstruktoru](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="3722d-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="3722d-136">Potom vytvoříme instanci `Vegetable` `item` třídy pojmenované pomocí [ `new` operátoru](../../language-reference/operators/new-operator.md) a `Vegetable`zadáním názvu pro konstruktor :</span><span class="sxs-lookup"><span data-stu-id="3722d-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="3722d-137">Nakonec zahrneme `item` proměnnou do interpolovaného <xref:System.DateTime> řetězce, <xref:System.Decimal> který také `Unit` obsahuje hodnotu, hodnotu a hodnotu [výčtu.](../../language-reference/builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="3722d-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="3722d-138">Nahraďte veškerý kód Jazyka C# v editoru následujícím `dotnet run` kódem a potom jej spusťte pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="3722d-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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
   public enum Unit { item, kilogram, gram, dozen };

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

<span data-ttu-id="3722d-139">Všimněte si, `item` že interpolační výraz v interpolovaném řetězci se překládá na text "lilek" ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="3722d-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="3722d-140">Je to proto, že když typ výsledku výrazu není řetězec, výsledek je vyřešen na řetězec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3722d-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="3722d-141">Pokud se výraz interpolace vyhodnotí na , použije se `null`prázdný řetězec (""nebo) <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3722d-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="3722d-142">Pokud se výraz interpolace `null`nevyhodnocuje na , obvykle se nazývá `ToString` metoda typu výsledek.</span><span class="sxs-lookup"><span data-stu-id="3722d-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="3722d-143">Můžete otestovat aktualizací implementace `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="3722d-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="3722d-144">Pravděpodobně ani není nutné `ToString` implementovat metodu, protože každý typ má některé implementace této metody.</span><span class="sxs-lookup"><span data-stu-id="3722d-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="3722d-145">Chcete-li to otestovat, `Vegetable.ToString` zakomentujte definici metody v příkladu `//`(k tomu, že, dát symbol komentáře, , před ním).</span><span class="sxs-lookup"><span data-stu-id="3722d-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="3722d-146">Ve výstupu je řetězec "lilek" nahrazen plně kvalifikovaným názvem typu ("Zelenina" v tomto <xref:System.Object.ToString?displayProperty=nameWithType> příkladu), což je výchozí chování metody.</span><span class="sxs-lookup"><span data-stu-id="3722d-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3722d-147">Výchozí chování `ToString` metody pro hodnotu výčtu je vrátit řetězcové reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3722d-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="3722d-148">Ve výstupu z tohoto příkladu je datum příliš přesné (cena lilku se nemění každou sekundu) a hodnota ceny neoznačuje měnovou jednotku.</span><span class="sxs-lookup"><span data-stu-id="3722d-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="3722d-149">V další části se dozvíte, jak tyto problémy vyřešit řízením formátu řetězcových reprezentací výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="3722d-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="3722d-150">Řízení formátování interpolačních výrazů</span><span class="sxs-lookup"><span data-stu-id="3722d-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="3722d-151">V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce.</span><span class="sxs-lookup"><span data-stu-id="3722d-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="3722d-152">Jedním byla hodnota data a času, ze které potřebujeme zachovat jenom datum.</span><span class="sxs-lookup"><span data-stu-id="3722d-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="3722d-153">Druhá byla cena, která neuváděla její měnovou jednotku.</span><span class="sxs-lookup"><span data-stu-id="3722d-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="3722d-154">Oba problémy můžeme snadno vyřešit.</span><span class="sxs-lookup"><span data-stu-id="3722d-154">Both issues are easy to address.</span></span> <span data-ttu-id="3722d-155">Interpolace řetězců umožňuje určit *formátovací řetězce,* které řídí formátování určitých typů.</span><span class="sxs-lookup"><span data-stu-id="3722d-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="3722d-156">Upravte volání `Console.WriteLine` z předchozího příkladu tak, aby zahrnovalo formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="3722d-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="3722d-157">Formátovací řetězec určíte tak, že se budete řídit interpolačním výrazem s dvojtečkou (":") a formátovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="3722d-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="3722d-158">„d“ je [standardní formátovací řetězec data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), který představuje krátký formát data.</span><span class="sxs-lookup"><span data-stu-id="3722d-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="3722d-159">„C2“ je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="3722d-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="3722d-160">Počet typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="3722d-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="3722d-161">Mezi ně patří i všechny číselné typy a typy data a času.</span><span class="sxs-lookup"><span data-stu-id="3722d-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="3722d-162">Úplný seznam typů podporujících formátovací řetězce najdete v části [Formátovací řetězce a typy v knihovně tříd .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) v článku [Formátovací typy v rozhraní .NET](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="3722d-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="3722d-163">Zkuste upravit formátovací řetězce v textovém editoru a pokaždé, když provedete změnu, znovu spusťte program, abyste zjistili, jak změny ovlivňují formátování data a času a číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3722d-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="3722d-164">Ve výrazu `{date:d}` změňte „d“ na „t“ (zobrazí se krátký formát času), „y“ (zobrazí se rok a měsíc) a „yyyy“ (zobrazí se rok v podobě čtyřmístného čísla).</span><span class="sxs-lookup"><span data-stu-id="3722d-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="3722d-165">Ve výrazu `{price:C2}` změňte „C2“ na „e“ (zobrazí se exponenciální tvar čísla) a „F3“ (zobrazí se číselná hodnota se třemi číslicemi za desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="3722d-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="3722d-166">Kromě řízení formátování můžete také řídit šířku pole a zarovnání formátovaných řetězců, které jsou zahrnuty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="3722d-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="3722d-167">V další části se dozvíte, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="3722d-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="3722d-168">Řízení šířky pole a zarovnání interpolačních výrazů</span><span class="sxs-lookup"><span data-stu-id="3722d-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="3722d-169">Obvykle při výsledek interpolační výraz je formátován na řetězec, tento řetězec je součástí výsledkového řetězce bez úvodní nebo koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="3722d-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="3722d-170">Zejména při práci se sadou dat pomáhá ovládat šířku pole a zarovnání textu čitelnější výstup.</span><span class="sxs-lookup"><span data-stu-id="3722d-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="3722d-171">Chcete-li to vidět, nahraďte veškerý kód v `dotnet run` textovém editoru následujícím kódem a zadejte pro spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="3722d-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="3722d-172">Jména autorů jsou zarovnána doleva a názvy, které napsali, jsou zarovnány doprava.</span><span class="sxs-lookup"><span data-stu-id="3722d-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="3722d-173">Trasu určíte přidáním čárky (",") za interpolační výraz a určením *minimální* šířky pole.</span><span class="sxs-lookup"><span data-stu-id="3722d-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="3722d-174">Pokud je zadanou hodnotou kladné číslo, je pole zarovnáno doprava.</span><span class="sxs-lookup"><span data-stu-id="3722d-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="3722d-175">Pokud se jedná o záporné číslo, je pole zarovnáno doleva.</span><span class="sxs-lookup"><span data-stu-id="3722d-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="3722d-176">Zkuste odebrat negativní `{"Author",-25}` znaménky z kódu a `{title.Key,-25}` spusťte příklad znovu, jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="3722d-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="3722d-177">Tentokrát jsou informace o autorovi zarovnány doprava.</span><span class="sxs-lookup"><span data-stu-id="3722d-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="3722d-178">Můžete kombinovat specifikátor zarovnání a formátovací řetězec pro jeden interpolační výraz.</span><span class="sxs-lookup"><span data-stu-id="3722d-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="3722d-179">Chcete-li to provést, nejprve zadejte zarovnání následované dvojtečkou a formátovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="3722d-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="3722d-180">Nahraďte celý kód `Main` uvnitř metody následujícím kódem, který zobrazuje tři formátované řetězce s definovanými šířkami polí.</span><span class="sxs-lookup"><span data-stu-id="3722d-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="3722d-181">Poté spusťte program `dotnet run` zadáním příkazu.</span><span class="sxs-lookup"><span data-stu-id="3722d-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="3722d-182">Výstup vypadá podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="3722d-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="3722d-183">Dokončili jste kurz interpolace řetězce.</span><span class="sxs-lookup"><span data-stu-id="3722d-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="3722d-184">Další informace naleznete v tématu [Interpolace řetězce](../../language-reference/tokens/interpolated.md) a [string interpolace v c#](../../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="3722d-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
