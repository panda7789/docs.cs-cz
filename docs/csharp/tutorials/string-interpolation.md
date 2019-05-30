---
title: Interpolace řetězců v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výrazu formátovaný výsledný řetězec v jazyce C# pomocí interpolace řetězců.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 2990298821fddc8a69430a4cf4bb5e3dd9df314d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251019"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="8af8a-103">Interpolace řetězců v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="8af8a-103">String interpolation in C\#</span></span>

<span data-ttu-id="8af8a-104">V tomto kurzu se dozvíte, jak používat [interpolace](../language-reference/tokens/interpolated.md) formátování a zahrňte výsledky výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="8af8a-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="8af8a-105">V příkladech se předpokládá, že máte zkušenosti s základní koncepty jazyka C# a .NET typ formátování.</span><span class="sxs-lookup"><span data-stu-id="8af8a-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="8af8a-106">Pokud jste ještě interpolace řetězců nebo formátování typu .NET, podívejte se [kurzu interpolace řetězce interaktivní](exploration/interpolated-strings.yml) první.</span><span class="sxs-lookup"><span data-stu-id="8af8a-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="8af8a-107">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8af8a-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="8af8a-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="8af8a-108">Introduction</span></span>

<span data-ttu-id="8af8a-109">[Interpolace](../language-reference/tokens/interpolated.md) funkce je založená na horní [složené formátování](../../standard/base-types/composite-formatting.md) běží na procesorech a poskytuje čitelné a pohodlné syntaxe zahrnout výsledky výrazu formátovaný výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8af8a-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="8af8a-110">K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="8af8a-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="8af8a-111">Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="8af8a-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="8af8a-112">V následujícím příkladu při vyhodnocování výrazu výsledek je převedena na řetězec a součástí výsledného řetězce:</span><span class="sxs-lookup"><span data-stu-id="8af8a-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="8af8a-113">Jak ukazuje příklad, patří uzavřením závorek výrazu v interpolovaném řetězci:</span><span class="sxs-lookup"><span data-stu-id="8af8a-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolationExpression>}
```

<span data-ttu-id="8af8a-114">Interpolované řetězce podporují všechny funkce [řetězec složené formátování](../../standard/base-types/composite-formatting.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="8af8a-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="8af8a-115">Díky tomu je lépe čitelný alternativou k použití <xref:System.String.Format%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8af8a-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="8af8a-116">Jak určit řetězec formátu pro výraz interpolace</span><span class="sxs-lookup"><span data-stu-id="8af8a-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="8af8a-117">Zadejte řetězec formátu, který je podporována typem výsledku výrazu podle interpolace výraz s čárkou (":") a nakonec formátovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="8af8a-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="8af8a-118">Následující příklad ukazuje, jak určit standardních a vlastních formátovacích řetězců pro výrazy, které produkují data a času nebo číselné výsledky:</span><span class="sxs-lookup"><span data-stu-id="8af8a-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="8af8a-119">Další informace najdete v tématu [součást řetězec formátu](../../standard/base-types/composite-formatting.md#format-string-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8af8a-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="8af8a-120">Tento oddíl poskytuje odkazy na témata, které popisují standardní a vlastní formátovací řetězce podporuje základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="8af8a-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="8af8a-121">Jak řídit šířku pole a zarovnání formátovaného interpolace výrazu</span><span class="sxs-lookup"><span data-stu-id="8af8a-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="8af8a-122">Zadejte šířku minimální pole a zarovnání formátovaného výraz výsledku pomocí interpolace výraz s čárkou (",") a konstantní výraz:</span><span class="sxs-lookup"><span data-stu-id="8af8a-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="8af8a-123">Pokud *zarovnání* hodnota je pozitivní, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="8af8a-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="8af8a-124">Pokud je třeba zadat zarovnání a řetězec formátu, začněte s komponentou zarovnání:</span><span class="sxs-lookup"><span data-stu-id="8af8a-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="8af8a-125">Následující příklad ukazuje, jak určit zarovnání a používá kanálem znaky ("|") pro vymezení textová pole:</span><span class="sxs-lookup"><span data-stu-id="8af8a-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="8af8a-126">Jako příklad ukazuje výstup, pokud výraz formátovaný výsledek délka je větší než zadaná šířka pole *zarovnání* hodnota se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="8af8a-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="8af8a-127">Další informace najdete v tématu [součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8af8a-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="8af8a-128">Použití řídicích sekvencí v interpolovaném řetězci</span><span class="sxs-lookup"><span data-stu-id="8af8a-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="8af8a-129">Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžném řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="8af8a-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="8af8a-130">Další informace najdete v tématu [řetězec řídící sekvence](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="8af8a-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="8af8a-131">Interpretace doslova řídicí sekvence, použijte [verbatim](../language-reference/tokens/verbatim.md) řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="8af8a-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="8af8a-132">Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak.</span><span class="sxs-lookup"><span data-stu-id="8af8a-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="8af8a-133">Zahrnout závorek "{" nebo "}", do výsledného řetězce, použijte dva složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="8af8a-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="8af8a-134">Další informace najdete v tématu [uvozovací znaky složených závorek](../../standard/base-types/composite-formatting.md#escaping-braces) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8af8a-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="8af8a-135">Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a sestavit verbatim interpolovaný řetězec:</span><span class="sxs-lookup"><span data-stu-id="8af8a-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="8af8a-136">Jak používat Ternární podmiňovací operátor `?:` ve výrazu interpolace</span><span class="sxs-lookup"><span data-stu-id="8af8a-136">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="8af8a-137">Jako dvojtečka (":") má zvláštní význam v položce s výrazem interpolace, aby bylo možné používat [podmiňovací operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ho do závorek, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8af8a-137">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="8af8a-138">Jak vytvořit specifické pro jazykovou verzi výsledný řetězec pomocí interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="8af8a-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="8af8a-139">Ve výchozím nastavení používá interpolovaném řetězci aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnosti pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="8af8a-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="8af8a-140">Použít implicitní převod interpolované řetězce, který se <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="8af8a-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="8af8a-141">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="8af8a-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="8af8a-142">Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instance ke generování více výsledný řetězec pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="8af8a-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="8af8a-143">Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze</span><span class="sxs-lookup"><span data-stu-id="8af8a-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="8af8a-144">Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statické <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolovaném řetězci na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="8af8a-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="8af8a-145">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="8af8a-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="8af8a-146">Závěr</span><span class="sxs-lookup"><span data-stu-id="8af8a-146">Conclusion</span></span>

<span data-ttu-id="8af8a-147">Tento kurz popisuje běžné scénáře použití interpolace řetězců.</span><span class="sxs-lookup"><span data-stu-id="8af8a-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="8af8a-148">Další informace o interpolace řetězců, najdete v článku [interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8af8a-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="8af8a-149">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.</span><span class="sxs-lookup"><span data-stu-id="8af8a-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="8af8a-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8af8a-150">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="8af8a-151">Řetězce</span><span class="sxs-lookup"><span data-stu-id="8af8a-151">Strings</span></span>](../programming-guide/strings/index.md)
