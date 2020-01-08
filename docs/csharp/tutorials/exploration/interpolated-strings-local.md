---
title: Interpolace řetězců – C# kurz
description: V tomto kurzu se dozvíte, jak C# používat funkci interpolace řetězců k zahrnutí formátovaného výrazu do většího řetězce.
ms.date: 10/23/2018
ms.openlocfilehash: 593f3a77370da73dfd5f090be98112327b86b1f7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346784"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="ce153-103">Použití interpolace řetězců k vytvoření formátovaných řetězců</span><span class="sxs-lookup"><span data-stu-id="ce153-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="ce153-104">V tomto kurzu se naučíte, jak C# pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) vkládat hodnoty do jediného výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="ce153-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="ce153-105">Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="ce153-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ce153-106">Kurz obsahuje řadu lekcí, které ukazují, jak vkládat hodnoty do řetězce a naformátovat tyto hodnoty různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ce153-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="ce153-107">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="ce153-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="ce153-108">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="ce153-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ce153-109">[Interaktivní verzi](interpolated-strings.yml) tohoto kurzu můžete také dokončit v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="ce153-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="ce153-110">Vytvoření interpolovaného řetězce</span><span class="sxs-lookup"><span data-stu-id="ce153-110">Create an interpolated string</span></span>

<span data-ttu-id="ce153-111">Vytvořte adresář s názvem *interpoled*.</span><span class="sxs-lookup"><span data-stu-id="ce153-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="ce153-112">Nastavte ho na aktuální adresář a spusťte následující příkaz z okna konzoly:</span><span class="sxs-lookup"><span data-stu-id="ce153-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="ce153-113">Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ce153-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ce153-114">Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte `Console.WriteLine("Hello World!");` řádku následujícím kódem, kde nahradíte `<name>` vaším jménem:</span><span class="sxs-lookup"><span data-stu-id="ce153-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="ce153-115">Tento kód zkuste zadat `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ce153-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ce153-116">Po spuštění programu se zobrazí jeden řetězec s pozdravem, který obsahuje vaše jméno.</span><span class="sxs-lookup"><span data-stu-id="ce153-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="ce153-117">Řetězec zahrnutý v volání metody <xref:System.Console.WriteLine%2A> je *výraz interpolující řetězec*.</span><span class="sxs-lookup"><span data-stu-id="ce153-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="ce153-118">Jedná se o druh šablony, který umožňuje vytvořit jeden řetězec (označovaný jako *výsledný řetězec*) z řetězce obsahujícího vložený kód.</span><span class="sxs-lookup"><span data-stu-id="ce153-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="ce153-119">Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.</span><span class="sxs-lookup"><span data-stu-id="ce153-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="ce153-120">Tento jednoduchý příklad obsahuje oba prvky, které jsou v každém interpolovaném řetězci povinné:</span><span class="sxs-lookup"><span data-stu-id="ce153-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="ce153-121">Řetězcový literál, který začíná znakem `$` před počátečním znakem uvozovek.</span><span class="sxs-lookup"><span data-stu-id="ce153-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="ce153-122">Mezi symbolem `$` a znakem uvozovek nesmí být žádné mezery.</span><span class="sxs-lookup"><span data-stu-id="ce153-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="ce153-123">(Pokud se chcete podívat, co se stane, když jednu vložíte, vložte mezeru za `$` znak, uložte soubor a spusťte program znovu zadáním `dotnet run` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ce153-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="ce153-124">C# Kompilátor zobrazí chybovou zprávu "Error CS1056: Neočekávaný znak" $ ".)</span><span class="sxs-lookup"><span data-stu-id="ce153-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="ce153-125">Jeden nebo více *výrazů interpolace*.</span><span class="sxs-lookup"><span data-stu-id="ce153-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="ce153-126">Výraz interpolace je označen levou a pravou složenou závorkou (`{` a `}`).</span><span class="sxs-lookup"><span data-stu-id="ce153-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="ce153-127">Do složených závorek můžete vložit libovolný výraz v C#, který vrací hodnotu (včetně hodnoty `null`).</span><span class="sxs-lookup"><span data-stu-id="ce153-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="ce153-128">Pojďme vyzkoušet několik příkladů interpolace řetězců s některými jinými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="ce153-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="ce153-129">Zahrnutí různých datových typů</span><span class="sxs-lookup"><span data-stu-id="ce153-129">Include different data types</span></span>

<span data-ttu-id="ce153-130">V předchozí části jste použili interpolaci řetězců pro vložení jednoho řetězce do jiného.</span><span class="sxs-lookup"><span data-stu-id="ce153-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="ce153-131">Výsledek výrazu interpolace může být libovolný datový typ, ale.</span><span class="sxs-lookup"><span data-stu-id="ce153-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="ce153-132">Pojďme do interpolované řetězcové hodnoty zahrnout hodnoty různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="ce153-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="ce153-133">V následujícím příkladu jsme nejprve definovali datový typ [třídy](../../programming-guide/classes-and-structs/classes.md) `Vegetable`, který má [vlastnost](../../properties.md) `Name` a [metodu](../../methods.md)`ToString`, která [přepíše](../../language-reference/keywords/override.md) chování metody <xref:System.Object.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ce153-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ce153-134">[Modifikátor přístupu`public`](../../language-reference/keywords/public.md) zpřístupňuje tuto metodu libovolnému klientskému kódu a získá tak řetězcovou reprezentaci instance `Vegetable`.</span><span class="sxs-lookup"><span data-stu-id="ce153-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="ce153-135">V příkladu `Vegetable.ToString` metoda vrátí hodnotu vlastnosti `Name`, která je inicializována v [konstruktoru](../../programming-guide/classes-and-structs/constructors.md)`Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="ce153-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="ce153-136">Pak vytvoříme instanci `Vegetable` třídy s názvem `item` pomocí [operátoru`new`](../../language-reference/operators/new-operator.md) a zadáním názvu konstruktoru `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="ce153-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="ce153-137">Nakonec zahrneme `item` proměnnou do interpolované řetězce, který obsahuje také hodnotu <xref:System.DateTime>, <xref:System.Decimal> hodnotu a hodnotu [výčtu](../../language-reference/builtin-types/enum.md) `Unit`.</span><span class="sxs-lookup"><span data-stu-id="ce153-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="ce153-138">Nahraďte celý C# kód v editoru následujícím kódem a pak použijte příkaz `dotnet run` pro jeho spuštění:</span><span class="sxs-lookup"><span data-stu-id="ce153-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="ce153-139">Všimněte si, že výraz interpolace `item` v interpolované řetězci se přeloží na text "lilek" ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="ce153-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="ce153-140">To je způsobeno tím, že když typ výsledku výrazu není řetězec, výsledek je přeložen na řetězec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ce153-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="ce153-141">Pokud je výraz interpolace vyhodnocen jako `null`, je použit prázdný řetězec ("" nebo <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ce153-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="ce153-142">Pokud výraz interpolace není vyhodnocen jako `null`, je obvykle volána metoda `ToString` výsledného typu.</span><span class="sxs-lookup"><span data-stu-id="ce153-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="ce153-143">Můžete ji otestovat aktualizací implementace metody `Vegetable.ToString`.</span><span class="sxs-lookup"><span data-stu-id="ce153-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="ce153-144">Je možné, že ani nemusíte implementovat metodu `ToString`, protože každý typ má určitou implementaci této metody.</span><span class="sxs-lookup"><span data-stu-id="ce153-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="ce153-145">Pokud to chcete otestovat, zakomentujte definici metody `Vegetable.ToString` v příkladu (k tomu je potřeba vložit symbol komentáře, `//`, před ním).</span><span class="sxs-lookup"><span data-stu-id="ce153-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="ce153-146">Ve výstupu je řetězec "lilk" nahrazen plně kvalifikovaným názvem typu ("rostlinný" v tomto příkladu), což je výchozí chování metody <xref:System.Object.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ce153-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ce153-147">Výchozím chováním metody `ToString` pro hodnotu výčtu je vrácení řetězcové reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ce153-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="ce153-148">Ve výstupu z tohoto příkladu je datum příliš přesné (cena za lilek se nemění každou sekundu) a hodnota Price neindikuje jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="ce153-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="ce153-149">V další části se dozvíte, jak tyto problémy vyřešit kontrolou formátu řetězcové reprezentace výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce153-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="ce153-150">Řízení formátování výrazů interpolace</span><span class="sxs-lookup"><span data-stu-id="ce153-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="ce153-151">V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce.</span><span class="sxs-lookup"><span data-stu-id="ce153-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="ce153-152">Jedním byla hodnota data a času, ze které potřebujeme zachovat jenom datum.</span><span class="sxs-lookup"><span data-stu-id="ce153-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="ce153-153">Druhá se jednalo o cenu, která neuváděla jednotku měny.</span><span class="sxs-lookup"><span data-stu-id="ce153-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="ce153-154">Oba problémy můžeme snadno vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ce153-154">Both issues are easy to address.</span></span> <span data-ttu-id="ce153-155">Interpolace řetězců umožňuje zadat *formátovací řetězce* , které řídí formátování konkrétních typů.</span><span class="sxs-lookup"><span data-stu-id="ce153-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="ce153-156">Upravte volání `Console.WriteLine` v předchozím příkladu pro zahrnutí formátovacích řetězců pro výrazy data a ceny, jak je znázorněno na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="ce153-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="ce153-157">Řetězec formátu určíte pomocí výrazu interpolace dvojtečkou (":") a formátovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="ce153-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="ce153-158">„d“ je [standardní formátovací řetězec data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), který představuje krátký formát data.</span><span class="sxs-lookup"><span data-stu-id="ce153-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="ce153-159">„C2“ je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ce153-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="ce153-160">Řada typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="ce153-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="ce153-161">Mezi ně patří i všechny číselné typy a typy data a času.</span><span class="sxs-lookup"><span data-stu-id="ce153-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="ce153-162">Úplný seznam typů podporujících formátovací řetězce najdete v části [Formátovací řetězce a typy v knihovně tříd .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) v článku [Formátovací typy v rozhraní .NET](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ce153-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="ce153-163">Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když uděláte změnu, spusťte program znovu, abyste viděli, jak změny ovlivňují formátování data a času a číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ce153-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="ce153-164">Ve výrazu `{date:d}` změňte „d“ na „t“ (zobrazí se krátký formát času), „y“ (zobrazí se rok a měsíc) a „yyyy“ (zobrazí se rok v podobě čtyřmístného čísla).</span><span class="sxs-lookup"><span data-stu-id="ce153-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="ce153-165">Ve výrazu `{price:C2}` změňte „C2“ na „e“ (zobrazí se exponenciální tvar čísla) a „F3“ (zobrazí se číselná hodnota se třemi číslicemi za desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="ce153-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="ce153-166">Kromě řízení formátování můžete také nastavit šířku pole a zarovnání formátovaných řetězců, které jsou zahrnuty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="ce153-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="ce153-167">V další části se dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="ce153-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="ce153-168">Řízení šířky pole a zarovnání výrazů interpolace</span><span class="sxs-lookup"><span data-stu-id="ce153-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="ce153-169">V případě, že je výsledek výrazu interpolace formátován na řetězec, je tento řetězec obsažen ve výsledném řetězci bez počátečních nebo koncových mezer.</span><span class="sxs-lookup"><span data-stu-id="ce153-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="ce153-170">Zejména při práci se sadou dat, která je schopná řídit šířku pole a zarovnání textu, pomáhají vytvořit čitelnější výstup.</span><span class="sxs-lookup"><span data-stu-id="ce153-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="ce153-171">Pokud to chcete vidět, nahraďte veškerý kód v textovém editoru následujícím kódem a pak zadejte `dotnet run` pro spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="ce153-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="ce153-172">Názvy autorů jsou zarovnané vlevo a tituly, které napsaly, jsou zarovnané vpravo.</span><span class="sxs-lookup"><span data-stu-id="ce153-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="ce153-173">Zarovnání zadáte přidáním čárky (",") po výrazu interpolace a určením *minimální* šířky pole.</span><span class="sxs-lookup"><span data-stu-id="ce153-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="ce153-174">Pokud je zadaná hodnota kladné číslo, bude pole zarovnáno vpravo.</span><span class="sxs-lookup"><span data-stu-id="ce153-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="ce153-175">Pokud se jedná o záporné číslo, bude pole zarovnané vlevo.</span><span class="sxs-lookup"><span data-stu-id="ce153-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="ce153-176">Zkuste odebrat záporné znaménka z `{"Author",-25}` a `{title.Key,-25}` kódu a znovu spustit tento příklad, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ce153-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="ce153-177">Tentokrát jsou informace o autorovi zarovnány doprava.</span><span class="sxs-lookup"><span data-stu-id="ce153-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="ce153-178">Můžete zkombinovat specifikátor zarovnání a formátovací řetězec pro jedinou interpolaci výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce153-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="ce153-179">Chcete-li to provést, zadejte nejprve zarovnání následovaný dvojtečkou a řetězcem formátu.</span><span class="sxs-lookup"><span data-stu-id="ce153-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="ce153-180">Nahraďte celý kód uvnitř metody `Main` následujícím kódem, který zobrazí tři formátované řetězce s definovanými šířkami polí.</span><span class="sxs-lookup"><span data-stu-id="ce153-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="ce153-181">Pak program spusťte zadáním příkazu `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ce153-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="ce153-182">Výstup vypadá nějak takto:</span><span class="sxs-lookup"><span data-stu-id="ce153-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="ce153-183">Dokončili jste kurz o interpolaci řetězce.</span><span class="sxs-lookup"><span data-stu-id="ce153-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="ce153-184">Další informace naleznete v tématu o [interpolaci řetězců](../../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v C# ](../../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="ce153-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
