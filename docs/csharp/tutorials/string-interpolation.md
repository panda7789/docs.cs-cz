---
title: Interpolace řetězců v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výrazu formátovaný výsledný řetězec v jazyce C# pomocí interpolace řetězců.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: b28890034cc0ab73f96c825b5548223e1c5cd1f4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086700"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="97c66-103">Interpolace řetězců v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="97c66-103">String interpolation in C#</span></span> #

<span data-ttu-id="97c66-104">V tomto kurzu se dozvíte, jak používat [interpolace](../language-reference/tokens/interpolated.md) formátování a zahrňte výsledky výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="97c66-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="97c66-105">V příkladech se předpokládá, že máte zkušenosti s základní koncepty jazyka C# a .NET typ formátování.</span><span class="sxs-lookup"><span data-stu-id="97c66-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="97c66-106">Pokud jste ještě interpolace řetězců nebo formátování typu .NET, podívejte se [quickstart interpolace řetězce interaktivní](../quick-starts/interpolated-strings.yml) první.</span><span class="sxs-lookup"><span data-stu-id="97c66-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation quickstart](../quick-starts/interpolated-strings.yml) first.</span></span> <span data-ttu-id="97c66-107">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="97c66-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="97c66-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="97c66-108">Introduction</span></span>

<span data-ttu-id="97c66-109">[Interpolace](../language-reference/tokens/interpolated.md) funkce je založená na horní [složené formátování](../../standard/base-types/composite-formatting.md) běží na procesorech a poskytuje čitelné a pohodlné syntaxe zahrnout výsledky výrazu formátovaný výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="97c66-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="97c66-110">K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="97c66-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="97c66-111">Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="97c66-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="97c66-112">V následujícím příkladu při vyhodnocování výrazu výsledek je převedena na řetězec a součástí výsledného řetězce:</span><span class="sxs-lookup"><span data-stu-id="97c66-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="97c66-113">Jak ukazuje příklad, patří uzavřením závorek výrazu v interpolovaném řetězci:</span><span class="sxs-lookup"><span data-stu-id="97c66-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="97c66-114">V době kompilace, interpolovaném řetězci se obvykle transformuje na <xref:System.String.Format%2A?displayProperty=nameWithType> volání metody.</span><span class="sxs-lookup"><span data-stu-id="97c66-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="97c66-115">Díky tomu se všechny funkce [řetězec složené formátování](../../standard/base-types/composite-formatting.md) funkce je k dispozici pro použití s interpolovanými řetězci najdete také.</span><span class="sxs-lookup"><span data-stu-id="97c66-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="97c66-116">Jak určit řetězec formátu pro interpolovaný výraz</span><span class="sxs-lookup"><span data-stu-id="97c66-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="97c66-117">Zadejte řetězec formátu, který je podporována typem výsledku výrazu podle interpolovaný výraz s čárkou (":") a nakonec formátovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="97c66-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="97c66-118">Následující příklad ukazuje, jak určit standardních a vlastních formátovacích řetězců pro výrazy, které produkují data a času nebo číselné výsledky:</span><span class="sxs-lookup"><span data-stu-id="97c66-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="97c66-119">Další informace najdete v tématu [součást řetězec formátu](../../standard/base-types/composite-formatting.md#format-string-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="97c66-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="97c66-120">Tento oddíl poskytuje odkazy na témata, které popisují standardní a vlastní formátovací řetězce podporuje základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="97c66-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="97c66-121">Jak řídit šířku pole a zarovnání formátovaného interpolovaný výraz</span><span class="sxs-lookup"><span data-stu-id="97c66-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="97c66-122">Zadejte šířku minimální pole a zarovnání formátovaného výraz výsledku podle interpolovaný výraz s čárkou (",") a konstantní výraz:</span><span class="sxs-lookup"><span data-stu-id="97c66-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="97c66-123">Pokud *zarovnání* hodnota je pozitivní, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="97c66-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="97c66-124">Pokud je třeba zadat zarovnání a řetězec formátu, začněte s komponentou zarovnání:</span><span class="sxs-lookup"><span data-stu-id="97c66-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="97c66-125">Následující příklad ukazuje, jak určit zarovnání a používá kanálem znaky ("|") pro vymezení textová pole:</span><span class="sxs-lookup"><span data-stu-id="97c66-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="97c66-126">Jako příklad ukazuje výstup, pokud výraz formátovaný výsledek délka je větší než zadaná šířka pole *zarovnání* hodnota se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="97c66-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="97c66-127">Další informace najdete v tématu [součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="97c66-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="97c66-128">Použití řídicích sekvencí v interpolovaném řetězci</span><span class="sxs-lookup"><span data-stu-id="97c66-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="97c66-129">Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžném řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="97c66-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="97c66-130">Další informace najdete v tématu [řetězec řídící sekvence](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="97c66-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="97c66-131">Interpretace doslova řídicí sekvence, použijte [verbatim](../language-reference/tokens/verbatim.md) řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="97c66-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="97c66-132">Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak.</span><span class="sxs-lookup"><span data-stu-id="97c66-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="97c66-133">Zahrnout závorek "{" nebo "}", do výsledného řetězce, použijte dva složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="97c66-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="97c66-134">Další informace najdete v tématu [uvozovací znaky složených závorek](../../standard/base-types/composite-formatting.md#escaping-braces) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="97c66-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="97c66-135">Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a sestavit verbatim interpolovaný řetězec:</span><span class="sxs-lookup"><span data-stu-id="97c66-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="97c66-136">Jak používat Ternární podmiňovací operátor `?:` v interpolovaným výrazem</span><span class="sxs-lookup"><span data-stu-id="97c66-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="97c66-137">Jako dvojtečka (":") má zvláštní význam v položce s interpolovaným výrazem, aby bylo možné používat [podmiňovací operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ho do závorek, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="97c66-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="97c66-138">Jak vytvořit specifické pro jazykovou verzi výsledný řetězec pomocí interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="97c66-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="97c66-139">Ve výchozím nastavení používá interpolovaném řetězci aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnosti pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="97c66-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="97c66-140">Použít implicitní převod interpolované řetězce, který se <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="97c66-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="97c66-141">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="97c66-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="97c66-142">Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instance ke generování více výsledný řetězec pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="97c66-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="97c66-143">Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze</span><span class="sxs-lookup"><span data-stu-id="97c66-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="97c66-144">Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statické <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolovaném řetězci na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="97c66-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="97c66-145">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="97c66-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="97c66-146">Závěr</span><span class="sxs-lookup"><span data-stu-id="97c66-146">Conclusion</span></span>

<span data-ttu-id="97c66-147">Tento kurz popisuje běžné scénáře použití interpolace řetězců.</span><span class="sxs-lookup"><span data-stu-id="97c66-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="97c66-148">Další informace o interpolace řetězců, najdete v článku [interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="97c66-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="97c66-149">Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.</span><span class="sxs-lookup"><span data-stu-id="97c66-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="97c66-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="97c66-150">See Also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>  
- <xref:System.FormattableString?displayProperty=nameWithType>  
- <xref:System.IFormattable?displayProperty=nameWithType>  
- [<span data-ttu-id="97c66-151">Řetězce</span><span class="sxs-lookup"><span data-stu-id="97c66-151">Strings</span></span>](../programming-guide/strings/index.md)  
