---
title: $-odinterpolace řetězců C# – referenční informace
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
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980116"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="a6407-103">$-Řetězcová interpolaceC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="a6407-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="a6407-104">`$` speciální znak identifikuje řetězcový literál jako *interpolovaná řetězec*.</span><span class="sxs-lookup"><span data-stu-id="a6407-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="a6407-105">Interpolovaná řetězcová konstanta je řetězcový literál, který může obsahovat *výrazy interpolace*.</span><span class="sxs-lookup"><span data-stu-id="a6407-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="a6407-106">Když je interpolovaná řetězcová událost přeložena na výsledný řetězec, položky s výrazy interpolace jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="a6407-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="a6407-107">Tato funkce je k dispozici C# od 6.</span><span class="sxs-lookup"><span data-stu-id="a6407-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="a6407-108">Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro vytváření formátovaných řetězců, než je funkce [složeného formátování řetězce](../../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="a6407-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="a6407-109">Následující příklad používá obě funkce k produkci stejného výstupu:</span><span class="sxs-lookup"><span data-stu-id="a6407-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="a6407-110">Struktura interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="a6407-110">Structure of an interpolated string</span></span>

<span data-ttu-id="a6407-111">Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho symbolem `$`.</span><span class="sxs-lookup"><span data-stu-id="a6407-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="a6407-112">Mezi `$` a `"`, které začínají řetězcovým literálem, nelze mít žádné prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="a6407-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="a6407-113">Struktura položky s výraz interpolace je následující:</span><span class="sxs-lookup"><span data-stu-id="a6407-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="a6407-114">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a6407-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="a6407-115">V následující tabulce jsou popsány jednotlivé prvky:</span><span class="sxs-lookup"><span data-stu-id="a6407-115">The following table describes each element:</span></span>

|<span data-ttu-id="a6407-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6407-116">Element</span></span>|<span data-ttu-id="a6407-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a6407-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="a6407-118">Výraz, který generuje výsledek, který má být formátován.</span><span class="sxs-lookup"><span data-stu-id="a6407-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="a6407-119">Řetězcová reprezentace `null` je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6407-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="a6407-120">Konstantní výraz, jehož hodnota určuje minimální počet znaků v řetězcové reprezentaci výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="a6407-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="a6407-121">Je-li kladné, Řetězcová reprezentace je zarovnána doprava; Pokud je záporná, zůstane zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="a6407-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="a6407-122">Další informace najdete v tématu [součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="a6407-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="a6407-123">Řetězec formátu, který je podporován typem výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="a6407-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="a6407-124">Další informace naleznete v tématu [formátovací řetězec – komponenta](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="a6407-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="a6407-125">Následující příklad používá volitelné formátovací komponenty popsané výše:</span><span class="sxs-lookup"><span data-stu-id="a6407-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="a6407-126">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="a6407-126">Special characters</span></span>

<span data-ttu-id="a6407-127">Chcete-li do textu vytvořeného interpolované řetězce zahrnout složené závorky "{" nebo "}", použijte dvě složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="a6407-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="a6407-128">Další informace naleznete v tématu [uvozovací závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="a6407-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="a6407-129">Jelikož dvojtečka (":") má zvláštní význam v položce výrazu interpolace, aby bylo možné použít [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolace, vložte tento výraz do závorek.</span><span class="sxs-lookup"><span data-stu-id="a6407-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="a6407-130">Následující příklad ukazuje, jak zahrnout složenou závorku ve výsledném řetězci a jak používat podmíněný operátor ve výrazu interpolace:</span><span class="sxs-lookup"><span data-stu-id="a6407-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="a6407-131">Interpolované doslovné řetězce začíná znakem `$` následovaným `@` znakem.</span><span class="sxs-lookup"><span data-stu-id="a6407-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="a6407-132">Další informace o doslovnéch řetězcích naleznete v tématech [řetězec](../builtin-types/reference-types.md) a [doslovného identifikátoru](verbatim.md) .</span><span class="sxs-lookup"><span data-stu-id="a6407-132">For more information about verbatim strings, see the [string](../builtin-types/reference-types.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="a6407-133">Počínaje C# 8,0 můžete použít tokeny `$` a `@` v libovolném pořadí: `$@"..."` i `@$"..."` jsou platné interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="a6407-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="a6407-134">V dřívějších C# verzích musí být token `$` před tokenem `@`.</span><span class="sxs-lookup"><span data-stu-id="a6407-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="a6407-135">Implicitní převody a určení `IFormatProvider` implementace</span><span class="sxs-lookup"><span data-stu-id="a6407-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="a6407-136">Existují tři implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="a6407-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="a6407-137">Převod interpolované řetězcové na <xref:System.String> instanci, která je výsledkem interpolované řetězcové překladu s položkami výrazu interpolace, které se nahrazují správně formátovanými řetězcovými reprezentacemi jejich výsledků.</span><span class="sxs-lookup"><span data-stu-id="a6407-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="a6407-138">Tento převod používá <xref:System.Globalization.CultureInfo.CurrentCulture> k formátování výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="a6407-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="a6407-139">Konverze interpolované řetězcové instance na <xref:System.FormattableString>, která představuje složený řetězec formátu společně s výsledky výrazu, který má být formátován.</span><span class="sxs-lookup"><span data-stu-id="a6407-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="a6407-140">To umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné instance <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="a6407-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="a6407-141">Chcete-li to provést, zavolejte jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="a6407-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="a6407-142"><xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="a6407-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="a6407-143">Metoda <xref:System.FormattableString.Invariant%2A>, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="a6407-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="a6407-144"><xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro určenou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a6407-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="a6407-145">Můžete také použít metodu <xref:System.FormattableString.ToString(System.IFormatProvider)> k poskytnutí uživatelsky definované implementace rozhraní <xref:System.IFormatProvider>, která podporuje vlastní formátování.</span><span class="sxs-lookup"><span data-stu-id="a6407-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="a6407-146">Další informace naleznete v části [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) oddílu [typy formátování v článku .NET](../../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="a6407-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="a6407-147">Převod interpolované řetězcové instance na <xref:System.IFormattable>, která umožňuje také vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné instance <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="a6407-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="a6407-148">Následující příklad používá implicitní převod na <xref:System.FormattableString> k vytvoření řetězců výsledků specifických pro jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="a6407-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="a6407-149">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="a6407-149">Additional resources</span></span>

<span data-ttu-id="a6407-150">Pokud s interpolací řetězce začínáte, přečtěte si téma o [interpolaci C# řetězce v](../../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu.</span><span class="sxs-lookup"><span data-stu-id="a6407-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="a6407-151">Můžete také [v C# kurzu ověřit jinou řetězcovou interpolaci](../../tutorials/string-interpolation.md) , která ukazuje, jak použít interpolované řetězce pro vytváření formátovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="a6407-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="a6407-152">Kompilace interpolovaná řetězce</span><span class="sxs-lookup"><span data-stu-id="a6407-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="a6407-153">Pokud má interpolující řetězec typ `string`, je obvykle transformovaná na volání metody <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6407-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="a6407-154">Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType>, pokud bylo analyzované chování ekvivalentní zřetězení.</span><span class="sxs-lookup"><span data-stu-id="a6407-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="a6407-155">Pokud má interpolující řetězec typ <xref:System.IFormattable> nebo <xref:System.FormattableString>, kompilátor vygeneruje volání metody <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6407-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6407-156">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6407-156">C# language specification</span></span>

<span data-ttu-id="a6407-157">Další informace naleznete v části [interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a6407-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6407-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6407-158">See also</span></span>

- [<span data-ttu-id="a6407-159">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="a6407-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a6407-160">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a6407-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="a6407-161">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a6407-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="a6407-162">Řetězce standardního číselného formátu</span><span class="sxs-lookup"><span data-stu-id="a6407-162">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="a6407-163">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="a6407-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
