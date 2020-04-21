---
title: $ - interpolace řetězce - c# odkaz
description: Interpolace řetězců poskytuje čitelnější a pohodlnější syntaxi pro formátování výstupu řetězce než tradiční složené formátování řetězců.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 2b95fa5fe5cecd4825e8c17a33f7795c6c9480c6
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738372"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="887a7-103">$ - interpolace řetězce (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="887a7-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="887a7-104">Speciální `$` znak identifikuje literál řetězce jako *interpolovaný řetězec*.</span><span class="sxs-lookup"><span data-stu-id="887a7-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="887a7-105">Interpolovaný řetězec je řetězcový literál, který může obsahovat *interpolační výrazy*.</span><span class="sxs-lookup"><span data-stu-id="887a7-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="887a7-106">Když je interpolovaný řetězec přeložen na výsledný řetězec, položky s interpolačními výrazy jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="887a7-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="887a7-107">Tato funkce je k dispozici počínaje C# 6.</span><span class="sxs-lookup"><span data-stu-id="887a7-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="887a7-108">Interpolace řetězců poskytuje čitelnější a pohodlnější syntaxi pro vytvoření formátovaných řetězců než funkce [složeného formátování řetězce.](../../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="887a7-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="887a7-109">Následující příklad používá oba prvky k vytvoření stejného výstupu:</span><span class="sxs-lookup"><span data-stu-id="887a7-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="887a7-110">Struktura interpolovaného řetězce</span><span class="sxs-lookup"><span data-stu-id="887a7-110">Structure of an interpolated string</span></span>

<span data-ttu-id="887a7-111">Chcete-li identifikovat literál řetězce jako interpolovaný řetězec, předřávejte jej symbolem. `$`</span><span class="sxs-lookup"><span data-stu-id="887a7-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="887a7-112">Mezi `$` a, `"` která spustí literál řetězce, nelze mít žádné prázdné místo.</span><span class="sxs-lookup"><span data-stu-id="887a7-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="887a7-113">Struktura položky s interpolačním výrazem je následující:</span><span class="sxs-lookup"><span data-stu-id="887a7-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="887a7-114">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="887a7-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="887a7-115">Následující tabulka popisuje každý prvek:</span><span class="sxs-lookup"><span data-stu-id="887a7-115">The following table describes each element:</span></span>

|<span data-ttu-id="887a7-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="887a7-116">Element</span></span>|<span data-ttu-id="887a7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="887a7-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="887a7-118">Výraz, který vytváří výsledek, který má být formátován.</span><span class="sxs-lookup"><span data-stu-id="887a7-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="887a7-119">Řetězcová `null` reprezentace is <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="887a7-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="887a7-120">Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcové reprezentaci výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="887a7-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="887a7-121">Pokud je kladná, reprezentace řetězce je zarovnána doprava; Pokud je záporná, je zarovnána doleva.</span><span class="sxs-lookup"><span data-stu-id="887a7-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="887a7-122">Další informace naleznete v [tématu Součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="887a7-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="887a7-123">Formátovací řetězec podporovaný typem výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="887a7-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="887a7-124">Další informace naleznete v [tématu Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="887a7-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="887a7-125">Následující příklad používá volitelné formátovací součásti popsané výše:</span><span class="sxs-lookup"><span data-stu-id="887a7-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="887a7-126">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="887a7-126">Special characters</span></span>

<span data-ttu-id="887a7-127">Chcete-li zahrnout závorku "{" nebo "}", do textu vytvořeného interpolovaným řetězcem použijte dvě závorky,{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="887a7-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="887a7-128">Další informace naleznete v [tématu Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="887a7-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="887a7-129">Jako dvojtečka (":") má zvláštní význam v položce výrazu interpolace, aby bylo možné použít [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolace, uzavřete tento výraz do závorek.</span><span class="sxs-lookup"><span data-stu-id="887a7-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="887a7-130">Následující příklad ukazuje, jak zahrnout složenou závorku do výsledného řetězce a jak použít podmíněný operátor ve výrazu interpolace:</span><span class="sxs-lookup"><span data-stu-id="887a7-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="887a7-131">Interpolovaný doslovný řetězec začíná `$` znakem následovaným znakem. `@`</span><span class="sxs-lookup"><span data-stu-id="887a7-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="887a7-132">Další informace o doslovných řetězcích naleznete v tématech [řetězce](../builtin-types/reference-types.md) a [doslovného identifikátoru.](verbatim.md)</span><span class="sxs-lookup"><span data-stu-id="887a7-132">For more information about verbatim strings, see the [string](../builtin-types/reference-types.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="887a7-133">Počínaje C# 8.0, můžete `$` použít `@` a tokeny v `$@"..."` `@$"..."` libovolném pořadí: oba a jsou platné interpolované doslovné řetězce.</span><span class="sxs-lookup"><span data-stu-id="887a7-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="887a7-134">V dřívějších verzích `$` jazyka C# `@` token musí zobrazit před token.</span><span class="sxs-lookup"><span data-stu-id="887a7-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="887a7-135">Implicitní převody a `IFormatProvider` jak určit implementaci</span><span class="sxs-lookup"><span data-stu-id="887a7-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="887a7-136">Existují tři implicitní převody z interpolovaného řetězce:</span><span class="sxs-lookup"><span data-stu-id="887a7-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="887a7-137">Převod interpolovaného řetězce na <xref:System.String> instanci, která je výsledkem interpolovaného rozlišení řetězce s položkami exprese interpolace, které jsou nahrazeny správně formátovanými řetězcovými reprezentacemi jejich výsledků.</span><span class="sxs-lookup"><span data-stu-id="887a7-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="887a7-138">Tento převod <xref:System.Globalization.CultureInfo.CurrentCulture> používá k formátování výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="887a7-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="887a7-139">Převod interpolovaného řetězce na <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu, které mají být formátovány.</span><span class="sxs-lookup"><span data-stu-id="887a7-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="887a7-140">To umožňuje vytvořit více řetězců výsledků s obsahem <xref:System.FormattableString> specifickým pro jazykovou verzi z jedné instance.</span><span class="sxs-lookup"><span data-stu-id="887a7-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="887a7-141">Chcete-li to provést, zavolejte jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="887a7-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="887a7-142">Přetížení, <xref:System.FormattableString.ToString> které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro .</span><span class="sxs-lookup"><span data-stu-id="887a7-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="887a7-143">Metoda, <xref:System.FormattableString.Invariant%2A> která vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro .</span><span class="sxs-lookup"><span data-stu-id="887a7-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="887a7-144">Metoda, <xref:System.FormattableString.ToString(System.IFormatProvider)> která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="887a7-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="887a7-145">Tuto metodu <xref:System.FormattableString.ToString(System.IFormatProvider)> můžete také použít k poskytnutí <xref:System.IFormatProvider> uživatelem definované implementace rozhraní, které podporuje vlastní formátování.</span><span class="sxs-lookup"><span data-stu-id="887a7-145">You can also use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="887a7-146">Další informace naleznete v části [Vlastní formátování s iCustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) v části Typy formátování v článku [rozhraní .NET.](../../../standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="887a7-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="887a7-147">Převod interpolovaného řetězce na <xref:System.IFormattable> instanci, která také umožňuje vytvořit více řetězců výsledků <xref:System.IFormattable> s obsahem specifickým pro jazykovou verzi z jedné instance.</span><span class="sxs-lookup"><span data-stu-id="887a7-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="887a7-148">Následující příklad používá implicitní převod k <xref:System.FormattableString> vytvoření řetězců výsledků specifických pro jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="887a7-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="887a7-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="887a7-149">Additional resources</span></span>

<span data-ttu-id="887a7-150">Pokud jste novým řetězce interpolace, naleznete [řetězec interpolace v C#](../../tutorials/exploration/interpolated-strings.yml) interaktivní kurz.</span><span class="sxs-lookup"><span data-stu-id="887a7-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="887a7-151">Můžete také zkontrolovat jiný [řetězec interpolace v kurzu Jazyka C#,](../../tutorials/string-interpolation.md) který ukazuje, jak používat interpolované řetězce k výrobě formátovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="887a7-151">You can also check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="887a7-152">Kompilace interpolovaných řetězců</span><span class="sxs-lookup"><span data-stu-id="887a7-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="887a7-153">Pokud interpolovaný řetězec má `string`typ , je obvykle transformována do volání <xref:System.String.Format%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="887a7-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="887a7-154">Kompilátor může <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> nahradit, pokud by analyzované chování bylo ekvivalentní zřetězení.</span><span class="sxs-lookup"><span data-stu-id="887a7-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="887a7-155">Pokud interpolovaný řetězec má <xref:System.IFormattable> typ <xref:System.FormattableString>nebo , kompilátor generuje <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> volání metody.</span><span class="sxs-lookup"><span data-stu-id="887a7-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="887a7-156">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="887a7-156">C# language specification</span></span>

<span data-ttu-id="887a7-157">Další informace naleznete v části [Interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="887a7-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="887a7-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="887a7-158">See also</span></span>

- [<span data-ttu-id="887a7-159">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="887a7-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="887a7-160">Speciální znaky jazyka C#</span><span class="sxs-lookup"><span data-stu-id="887a7-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="887a7-161">Řetězce</span><span class="sxs-lookup"><span data-stu-id="887a7-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="887a7-162">Standardní řetězce formátu čísla</span><span class="sxs-lookup"><span data-stu-id="887a7-162">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="887a7-163">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="887a7-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
