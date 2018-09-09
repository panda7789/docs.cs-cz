---
title: $ – interpolace řetězců (referenční dokumentace jazyka C#)
description: Interpolace řetězců poskytuje čitelné a pohodlné syntaxe pro formátování výstupní řetězec než tradiční řetězec složené formátování.
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
ms.openlocfilehash: 2009b3620bc4874520221a4ea847222feafca01b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251729"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="40c16-103">$ – interpolace řetězců (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="40c16-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="40c16-104">`$` Speciální znak identifikuje řetězcového literálu jako *interpolovaný řetězec*.</span><span class="sxs-lookup"><span data-stu-id="40c16-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="40c16-105">Interpolované řetězce se řetězcový literál, který může obsahovat *interpolovaných výrazů*.</span><span class="sxs-lookup"><span data-stu-id="40c16-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="40c16-106">Po vyřešení interpolovaného řetězce do výsledného řetězce položky, které interpolovaných výrazů jsou nahrazené řetězcové reprezentace výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="40c16-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="40c16-107">Tato funkce je dostupná v jazyce C# 6 a novější verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="40c16-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="40c16-108">Interpolace řetězců poskytuje čitelné a pohodlné syntaxe pro vytvoření formátovaného řetězce než [řetězec složené formátování](../../../standard/base-types/composite-formatting.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="40c16-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="40c16-109">Následující příklad používá obě funkce stejný výstup:</span><span class="sxs-lookup"><span data-stu-id="40c16-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="40c16-110">Struktura interpolovaného řetězce</span><span class="sxs-lookup"><span data-stu-id="40c16-110">Structure of an interpolated string</span></span>

<span data-ttu-id="40c16-111">K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="40c16-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="40c16-112">Nemůže obsahovat žádné prázdné znaky. mezi `$` a `"` , který spouští řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="40c16-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="40c16-113">To způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="40c16-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="40c16-114">Struktura položka s interpolovaného výrazu je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40c16-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="40c16-115">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="40c16-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="40c16-116">Následující tabulka popisuje jednotlivé prvky:</span><span class="sxs-lookup"><span data-stu-id="40c16-116">The following table describes each element:</span></span>

|<span data-ttu-id="40c16-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="40c16-117">Element</span></span>|<span data-ttu-id="40c16-118">Popis</span><span class="sxs-lookup"><span data-stu-id="40c16-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="40c16-119">Výraz, který vytváří výsledek, který má být formátováno.</span><span class="sxs-lookup"><span data-stu-id="40c16-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="40c16-120">Řetězcové vyjádření sady `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40c16-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="40c16-121">Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolovaný výraz.</span><span class="sxs-lookup"><span data-stu-id="40c16-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="40c16-122">Pokud je pozitivní, řetězcové vyjádření zarovnán doprava; záporná, je zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="40c16-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="40c16-123">Další informace najdete v tématu [součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="40c16-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="40c16-124">Formátovací řetězec, který je podporována typem výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="40c16-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="40c16-125">Další informace najdete v tématu [součást řetězec formátu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="40c16-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="40c16-126">Následující příklad používá volitelný formátování komponent popsaných výše:</span><span class="sxs-lookup"><span data-stu-id="40c16-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="40c16-127">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="40c16-127">Special characters</span></span>

<span data-ttu-id="40c16-128">Zahrnout závorek "{" nebo "}", text vytvořené metodou interpolovaného řetězce, použijte dva složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="40c16-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="40c16-129">Další informace najdete v tématu [uvozovací znaky složených závorek](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="40c16-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="40c16-130">Jako dvojtečka (":") má zvláštní význam v položce interpolovaný výraz, aby bylo možné používat [podmiňovací operátor](../operators/conditional-operator.md) v interpolovaným výrazem, použijte tento výraz v závorkách.</span><span class="sxs-lookup"><span data-stu-id="40c16-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="40c16-131">Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a jak pomocí podmíněného operátoru v interpolovaný výraz:</span><span class="sxs-lookup"><span data-stu-id="40c16-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="40c16-132">Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak.</span><span class="sxs-lookup"><span data-stu-id="40c16-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="40c16-133">Další informace o doslovném řetězci, najdete v článku [řetězec](../keywords/string.md) a [Doslovný identifikátor](verbatim.md) témata.</span><span class="sxs-lookup"><span data-stu-id="40c16-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="40c16-134">`$` Token se musí nacházet před `@` token začal v doslovném interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="40c16-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="40c16-135">Implicitní převody a určení `IFormatProvider` implementace</span><span class="sxs-lookup"><span data-stu-id="40c16-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="40c16-136">Existují tři implicitní převody z interpolovaném řetězci:</span><span class="sxs-lookup"><span data-stu-id="40c16-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="40c16-137">Převod interpolované řetězce, který se <xref:System.String> instanci, která je výsledkem řešení interpolovaný řetězec s interpolovaného výrazu položky nahrazeny správně formátovaná řetězcové reprezentace jejich výsledky.</span><span class="sxs-lookup"><span data-stu-id="40c16-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="40c16-138">Tento převod používá aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="40c16-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="40c16-139">Převod interpolované řetězce, který se <xref:System.FormattableString> instanci, která představuje složený řetězec formátu spolu s výsledky výrazu, který má být formátováno.</span><span class="sxs-lookup"><span data-stu-id="40c16-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="40c16-140">Který vám umožní vytvořit více výsledný řetězec s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance.</span><span class="sxs-lookup"><span data-stu-id="40c16-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="40c16-141">Provedete to, který volat jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="40c16-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="40c16-142">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="40c16-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="40c16-143"><xref:System.FormattableString.Invariant%2A> Metodu, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="40c16-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="40c16-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="40c16-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="40c16-145">Můžete také použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu k dispozici na uživatelem definované implementace <xref:System.IFormatProvider> rozhraní, které podporuje vlastní formátování.</span><span class="sxs-lookup"><span data-stu-id="40c16-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="40c16-146">Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="40c16-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="40c16-147">Převod interpolovaného řetězce do <xref:System.IFormattable> , jež lze také vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="40c16-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="40c16-148">Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit specifické pro jazykovou verzi výsledný řetězec:</span><span class="sxs-lookup"><span data-stu-id="40c16-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="40c16-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="40c16-149">Additional resources</span></span>

<span data-ttu-id="40c16-150">Pokud jste ještě na interpolaci řetězce, najdete v článku [interpolace v jazyce C#](../../quick-starts/interpolated-strings.yml) rychlý start.</span><span class="sxs-lookup"><span data-stu-id="40c16-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="40c16-151">Další příklady najdete v článku [interpolace v jazyce C#](../../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="40c16-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="40c16-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40c16-152">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="40c16-153">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="40c16-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="40c16-154">Řetězce</span><span class="sxs-lookup"><span data-stu-id="40c16-154">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="40c16-155">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="40c16-155">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40c16-156">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="40c16-156">C# Special Characters</span></span>](index.md)
- [<span data-ttu-id="40c16-157">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40c16-157">C# Reference</span></span>](../index.md)
