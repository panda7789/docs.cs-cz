---
title: $-odinterpolace řetězců C# – referenční informace
ms.custom: seodec18
description: Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro formátování výstupu řetězce než tradiční složené formátování řetězce.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 53a8938a373136df65e23c162b94c4d8dc1f30b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253866"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="db04d-103">$-Řetězcová interpolaceC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="db04d-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="db04d-104">Speciální znak identifikuje řetězcový literál jako *interpolovaná řetězec.* `$`</span><span class="sxs-lookup"><span data-stu-id="db04d-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="db04d-105">Interpolovaná řetězcová konstanta je řetězcový literál, který může obsahovat *výrazy interpolace*.</span><span class="sxs-lookup"><span data-stu-id="db04d-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="db04d-106">Když je interpolovaná řetězcová událost přeložena na výsledný řetězec, položky s výrazy interpolace jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="db04d-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="db04d-107">Tato funkce je k dispozici C# od 6.</span><span class="sxs-lookup"><span data-stu-id="db04d-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="db04d-108">Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro vytváření formátovaných řetězců, než je funkce [složeného formátování řetězce](../../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="db04d-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="db04d-109">Následující příklad používá obě funkce k produkci stejného výstupu:</span><span class="sxs-lookup"><span data-stu-id="db04d-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="db04d-110">Struktura interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="db04d-110">Structure of an interpolated string</span></span>

<span data-ttu-id="db04d-111">Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho `$` symbolem.</span><span class="sxs-lookup"><span data-stu-id="db04d-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="db04d-112">Mezi `$` znakem `"` a, který začíná řetězcovým literálem, nelze zadat prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="db04d-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="db04d-113">Struktura položky s výraz interpolace je následující:</span><span class="sxs-lookup"><span data-stu-id="db04d-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="db04d-114">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="db04d-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="db04d-115">V následující tabulce jsou popsány jednotlivé prvky:</span><span class="sxs-lookup"><span data-stu-id="db04d-115">The following table describes each element:</span></span>

|<span data-ttu-id="db04d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="db04d-116">Element</span></span>|<span data-ttu-id="db04d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="db04d-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="db04d-118">Výraz, který generuje výsledek, který má být formátován.</span><span class="sxs-lookup"><span data-stu-id="db04d-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="db04d-119">Řetězcová reprezentace `null` je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db04d-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="db04d-120">Konstantní výraz, jehož hodnota určuje minimální počet znaků v řetězcové reprezentaci výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="db04d-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="db04d-121">Je-li kladné, Řetězcová reprezentace je zarovnána doprava; Pokud je záporná, zůstane zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="db04d-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="db04d-122">Další informace najdete v tématu [součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="db04d-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="db04d-123">Řetězec formátu, který je podporován typem výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="db04d-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="db04d-124">Další informace naleznete v tématu [formátovací řetězec – komponenta](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="db04d-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="db04d-125">Následující příklad používá volitelné formátovací komponenty popsané výše:</span><span class="sxs-lookup"><span data-stu-id="db04d-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="db04d-126">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="db04d-126">Special characters</span></span>

<span data-ttu-id="db04d-127">Chcete-li do textu vytvořeného interpolované řetězce zahrnout složené závorky "{" nebo "}", použijte dvě složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="db04d-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="db04d-128">Další informace naleznete v tématu [uvozovací závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="db04d-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="db04d-129">Jelikož dvojtečka (":") má zvláštní význam v položce výrazu interpolace, aby bylo možné použít [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolace, vložte tento výraz do závorek.</span><span class="sxs-lookup"><span data-stu-id="db04d-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="db04d-130">Následující příklad ukazuje, jak zahrnout složenou závorku ve výsledném řetězci a jak používat podmíněný operátor ve výrazu interpolace:</span><span class="sxs-lookup"><span data-stu-id="db04d-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="db04d-131">Interpolované doslovné řetězce začíná `$` znakem následovaným `@` znakem.</span><span class="sxs-lookup"><span data-stu-id="db04d-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="db04d-132">Další informace o doslovnéch řetězcích naleznete v tématech [řetězec](../keywords/string.md) a [doslovného identifikátoru](verbatim.md) .</span><span class="sxs-lookup"><span data-stu-id="db04d-132">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="db04d-133">Počínaje C# 8,0 můžete použít `$` tokeny a `@` v libovolném pořadí: `$@"..."` a `@$"..."` jsou platné interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="db04d-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="db04d-134">V dřívějších C# verzích `$` se token `@` musí vyskytovat před tokenem.</span><span class="sxs-lookup"><span data-stu-id="db04d-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="db04d-135">Implicitní převody a určení `IFormatProvider` implementace</span><span class="sxs-lookup"><span data-stu-id="db04d-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="db04d-136">Existují tři implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="db04d-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="db04d-137">Převod interpolované řetězcové na <xref:System.String> instanci, která je výsledkem interpolované řetězcové překladu s položkami výrazu interpolace, které se nahrazují správně formátovanými řetězcovými reprezentacemi jejich výsledků.</span><span class="sxs-lookup"><span data-stu-id="db04d-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="db04d-138">Tento převod používá <xref:System.Globalization.CultureInfo.CurrentCulture> k formátování výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="db04d-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="db04d-139">Převod interpolované řetězcové na <xref:System.FormattableString> instanci, která představuje složený řetězec formátu společně s výsledky výrazu, který má být formátován.</span><span class="sxs-lookup"><span data-stu-id="db04d-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="db04d-140">To umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z <xref:System.FormattableString> jedné instance.</span><span class="sxs-lookup"><span data-stu-id="db04d-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="db04d-141">Chcete-li to provést, zavolejte jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="db04d-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="db04d-142">Přetížení, které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro. <xref:System.FormattableString.ToString></span><span class="sxs-lookup"><span data-stu-id="db04d-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="db04d-143">Metoda, která vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro. <xref:System.FormattableString.Invariant%2A></span><span class="sxs-lookup"><span data-stu-id="db04d-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="db04d-144"><xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="db04d-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="db04d-145">Můžete také použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu k poskytnutí uživatelsky definované implementace <xref:System.IFormatProvider> rozhraní, které podporuje vlastní formátování.</span><span class="sxs-lookup"><span data-stu-id="db04d-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="db04d-146">Další informace naleznete v části [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) oddílu [typy formátování v článku .NET](../../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="db04d-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="db04d-147">Převod interpolované řetězce na <xref:System.IFormattable> instanci, která také umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="db04d-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="db04d-148">Následující příklad používá implicitní převod na <xref:System.FormattableString> k vytvoření řetězců výsledků specifických pro jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="db04d-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="db04d-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="db04d-149">Additional resources</span></span>

<span data-ttu-id="db04d-150">Pokud s interpolací řetězce začínáte, přečtěte si téma o [interpolaci C# řetězce v](../../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu.</span><span class="sxs-lookup"><span data-stu-id="db04d-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="db04d-151">Můžete také [v C# kurzu ověřit jinou řetězcovou interpolaci](../../tutorials/string-interpolation.md) , která ukazuje, jak použít interpolované řetězce pro vytváření formátovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="db04d-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="db04d-152">Kompilace interpolovaná řetězce</span><span class="sxs-lookup"><span data-stu-id="db04d-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="db04d-153">Pokud má interpolující řetězec typ `string`, je obvykle transformovaná <xref:System.String.Format%2A?displayProperty=nameWithType> na volání metody.</span><span class="sxs-lookup"><span data-stu-id="db04d-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="db04d-154">Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> , <xref:System.String.Concat%2A?displayProperty=nameWithType> Pokud bylo analyzované chování ekvivalentní zřetězení.</span><span class="sxs-lookup"><span data-stu-id="db04d-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="db04d-155">Pokud má interpolující řetězec typ <xref:System.IFormattable> nebo <xref:System.FormattableString>, kompilátor <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> vygeneruje volání metody.</span><span class="sxs-lookup"><span data-stu-id="db04d-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db04d-156">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="db04d-156">C# language specification</span></span>

<span data-ttu-id="db04d-157">Další informace naleznete v části [interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="db04d-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db04d-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db04d-158">See also</span></span>

- [<span data-ttu-id="db04d-159">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="db04d-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db04d-160">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="db04d-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="db04d-161">Řetězce</span><span class="sxs-lookup"><span data-stu-id="db04d-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="db04d-162">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="db04d-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="db04d-163">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="db04d-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
