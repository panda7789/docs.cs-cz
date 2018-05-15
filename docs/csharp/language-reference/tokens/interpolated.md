---
title: $ – řetězec interpolace (referenční dokumentace jazyka C#)
description: Řetězec interpolace poskytuje čitelnější a pohodlný syntaxe k formátování výstupu řetězec než tradiční řetězec složené formátování.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="75d42-103">$ – řetězec interpolace (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="75d42-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="75d42-104">`$` Speciální znak identifikuje řetězcový literál jako *interpolované řetězce*.</span><span class="sxs-lookup"><span data-stu-id="75d42-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="75d42-105">Interpolované řetězce je řetězcový literál, který může obsahovat *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="75d42-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="75d42-106">Po vyřešení interpolované řetězce na řetězec výsledek položky s interpolované výrazy se nahrazují řetězcové vyjádření výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="75d42-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="75d42-107">Tato funkce je k dispozici v C# 6 a novější verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="75d42-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="75d42-108">Poskytuje řetězec interpolace čitelnější a pohodlný syntaxe pro vytvoření formátované řetězce než [řetězce složené formátování](../../../standard/base-types/composite-formatting.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="75d42-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="75d42-109">Následující příklad používá k vytvoření stejný výstup obě funkce:</span><span class="sxs-lookup"><span data-stu-id="75d42-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="75d42-110">Struktura interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="75d42-110">Structure of an interpolated string</span></span>

<span data-ttu-id="75d42-111">K identifikaci řetězcový literál jako interpolované řetězce, předřazení její `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="75d42-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="75d42-112">Nemůže mít žádné mezer mezi `$` a `"` , spustí řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="75d42-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="75d42-113">To způsobí, že chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="75d42-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="75d42-114">Struktura položky s interpolované výrazu je následující:</span><span class="sxs-lookup"><span data-stu-id="75d42-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="75d42-115">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="75d42-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="75d42-116">Následující tabulka popisuje jednotlivé prvky:</span><span class="sxs-lookup"><span data-stu-id="75d42-116">The following table describes each element:</span></span>

|<span data-ttu-id="75d42-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="75d42-117">Element</span></span>|<span data-ttu-id="75d42-118">Popis</span><span class="sxs-lookup"><span data-stu-id="75d42-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="75d42-119">Výraz, který vytváří výsledek, který má být formátována.</span><span class="sxs-lookup"><span data-stu-id="75d42-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="75d42-120">Řetězec reprezentace `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75d42-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="75d42-121">Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolované výrazu.</span><span class="sxs-lookup"><span data-stu-id="75d42-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="75d42-122">Pokud kladné, je řetězcová reprezentace vpravo zarovnaný; záporná, je zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="75d42-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="75d42-123">Další informace najdete v tématu [zarovnání součást](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="75d42-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="75d42-124">Řetězec formátu, který podporuje typ výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="75d42-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="75d42-125">Další informace najdete v tématu [součást řetězce formátu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="75d42-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="75d42-126">Následující příklad používá volitelné formátování komponent popsaných výše:</span><span class="sxs-lookup"><span data-stu-id="75d42-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="75d42-127">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="75d42-127">Special characters</span></span>

<span data-ttu-id="75d42-128">Zahrnout závorek "{" nebo "}", v textu vyprodukované interpolované řetězce, použijte dva složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="75d42-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="75d42-129">Další informace najdete v tématu [uvozovací znaky složené závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="75d42-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="75d42-130">Jako dvojtečkou (":") má zvláštní význam v interpolované výraz položku, aby bylo možné používat [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolované uzavřete výrazu v závorkách.</span><span class="sxs-lookup"><span data-stu-id="75d42-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="75d42-131">Následující příklad ukazuje, jak mají být zahrnuty závorek výsledný řetězec a jak používat podmíněný operátor v interpolované výrazu:</span><span class="sxs-lookup"><span data-stu-id="75d42-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="75d42-132">Řetězec typu verbatim interpolované začíná `$` následuje znak `@` znak.</span><span class="sxs-lookup"><span data-stu-id="75d42-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="75d42-133">Další informace o typu verbatim řetězců najdete v tématu [řetězec](../keywords/string.md) a [typu verbatim identifikátor](verbatim.md) témata.</span><span class="sxs-lookup"><span data-stu-id="75d42-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="75d42-134">`$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="75d42-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="75d42-135">Implicitní převody a zadání `IFormatProvider` implementace</span><span class="sxs-lookup"><span data-stu-id="75d42-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="75d42-136">Existují tři implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="75d42-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="75d42-137">Interpolované řetězce pro převod <xref:System.String> instanci, která je výsledkem interpolované řetězce řešení pomocí výrazu interpolované položky nahrazován správně formátovaný řetězec reprezentace jejich výsledky.</span><span class="sxs-lookup"><span data-stu-id="75d42-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="75d42-138">Tento převod používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="75d42-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="75d42-139">Interpolované řetězce pro převod <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu formátování.</span><span class="sxs-lookup"><span data-stu-id="75d42-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="75d42-140">Což vám umožní vytvořit více řetězců výsledek s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance.</span><span class="sxs-lookup"><span data-stu-id="75d42-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="75d42-141">Chcete-li provést volání jednoho z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="75d42-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="75d42-142">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="75d42-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="75d42-143"><xref:System.FormattableString.Invariant%2A> Metoda, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="75d42-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="75d42-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="75d42-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="75d42-145">Můžete taky použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metody můžete zajistit na uživatelem definované implementace <xref:System.IFormatProvider> rozhraní, která podporuje vlastní formátování.</span><span class="sxs-lookup"><span data-stu-id="75d42-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="75d42-146">Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="75d42-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="75d42-147">Interpolované řetězce pro převod <xref:System.IFormattable> instanci, která umožňuje taky vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="75d42-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="75d42-148">Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit výsledek specifické pro jazykovou verzi řetězce:</span><span class="sxs-lookup"><span data-stu-id="75d42-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="75d42-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="75d42-149">Additional resources</span></span>

<span data-ttu-id="75d42-150">Pokud nový řetězec interpolace, podívejte se [řetězec interpolace v jazyce C#](../../quick-starts/interpolated-strings.yml) rychlý start.</span><span class="sxs-lookup"><span data-stu-id="75d42-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="75d42-151">Další příklady najdete v tématu [řetězec interpolace v jazyce C#](../../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="75d42-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="75d42-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="75d42-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="75d42-153">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="75d42-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="75d42-154">Řetězce</span><span class="sxs-lookup"><span data-stu-id="75d42-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="75d42-155">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="75d42-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="75d42-156">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="75d42-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="75d42-157">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75d42-157">C# Reference</span></span>](../index.md)  