---
title: Interpolace řetězce v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výraz formátovaný výsledek řetězec v jazyce C# s interpolace řetězec.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 447e87cd4aae49896f0efbb8ece6097181079266
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058936"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="be5dd-103">Interpolace řetězce v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be5dd-103">String interpolation in C#</span></span> #

<span data-ttu-id="be5dd-104">V tomto kurzu se dozvíte, jak používat [řetězec interpolace](../language-reference/tokens/interpolated.md) můžete naformátovat a zahrňte výsledky výraz ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="be5dd-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="be5dd-105">Příklady předpokládají, že jste obeznámeni s základní koncepty jazyka C# a rozhraní .NET typ formátování.</span><span class="sxs-lookup"><span data-stu-id="be5dd-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="be5dd-106">Pokud jste ještě interpolace řetězec nebo formátování typ rozhraní .NET, podívejte se [rychlý start interpolace interaktivní řetězec](../quick-starts/interpolated-strings.yml) první.</span><span class="sxs-lookup"><span data-stu-id="be5dd-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation quickstart](../quick-starts/interpolated-strings.yml) first.</span></span> <span data-ttu-id="be5dd-107">Další informace o typy formátování v rozhraní .NET najdete v tématu [typy formátování v .NET](../../standard/base-types/formatting-types.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="be5dd-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="be5dd-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="be5dd-108">Introduction</span></span>

<span data-ttu-id="be5dd-109">[Řetězec interpolace](../language-reference/tokens/interpolated.md) funkce je postavený na [složené formátování](../../standard/base-types/composite-formatting.md) funkci a poskytuje čitelnější a pohodlný syntaxe zahrnout výsledky výraz formátovaný výsledek řetězce.</span><span class="sxs-lookup"><span data-stu-id="be5dd-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="be5dd-110">K identifikaci řetězcový literál jako interpolované řetězce, předřazení její `$` symbol.</span><span class="sxs-lookup"><span data-stu-id="be5dd-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="be5dd-111">Můžete vložit libovolný platný C# výraz, který vrátí hodnotu ve formátu interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="be5dd-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="be5dd-112">V následujícím příkladu při vyhodnocení výrazu svůj výsledek je převést na řetězec a součástí výsledný řetězec:</span><span class="sxs-lookup"><span data-stu-id="be5dd-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="be5dd-113">Jak ukazuje příklad patří uzavřením s složené závorky výrazu ve formátu interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="be5dd-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="be5dd-114">Při kompilaci, interpolované řetězce obvykle převede na <xref:System.String.Format%2A?displayProperty=nameWithType> volání metody.</span><span class="sxs-lookup"><span data-stu-id="be5dd-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="be5dd-115">Který zpřístupňuje všechny možnosti [řetězce složené formátování](../../standard/base-types/composite-formatting.md) funkce, které jsou k dispozici pro použití s také interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="be5dd-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="be5dd-116">Jak určit řetězec formátu pro interpolované výrazu</span><span class="sxs-lookup"><span data-stu-id="be5dd-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="be5dd-117">Zadejte řetězec formátu, který je podporován typ výsledku výrazu podle interpolované výraz s dvojtečkou (":") a řetězec formátu:</span><span class="sxs-lookup"><span data-stu-id="be5dd-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="be5dd-118">Následující příklad ukazuje, jak zadat standardní a vlastní formát řetězce pro výrazy, které produkují data a času nebo číselných výsledků:</span><span class="sxs-lookup"><span data-stu-id="be5dd-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="be5dd-119">Další informace najdete v tématu [součást řetězce formátu](../../standard/base-types/composite-formatting.md#format-string-component) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="be5dd-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="be5dd-120">Tento oddíl obsahuje odkazy na témata, která popisují řetězce formátu Standardní a vlastní podporuje základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="be5dd-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="be5dd-121">Tom, jak řídit šířku pole a zarovnání formátovaný interpolované výrazu</span><span class="sxs-lookup"><span data-stu-id="be5dd-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="be5dd-122">Zadejte šířku minimální pole a zarovnání výraz formátovaný výsledek podle interpolované výraz s použitím čárky (",") a konstantní výraz:</span><span class="sxs-lookup"><span data-stu-id="be5dd-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="be5dd-123">Pokud *zarovnání* hodnota je kladné, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="be5dd-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="be5dd-124">Pokud potřebujete k určení zarovnání a řetězec formátu, začněte s komponentou zarovnání:</span><span class="sxs-lookup"><span data-stu-id="be5dd-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="be5dd-125">Následující příklad ukazuje, jak k určení zarovnání a používá zřetězit znaky ("|") a tím vymezit textová pole:</span><span class="sxs-lookup"><span data-stu-id="be5dd-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="be5dd-126">Jako příklad výstupu zobrazí, pokud délka výsledku formátovaný výrazu překračuje zadaný šířku pole, *zarovnání* hodnota je ignorována.</span><span class="sxs-lookup"><span data-stu-id="be5dd-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="be5dd-127">Další informace najdete v tématu [zarovnání součást](../../standard/base-types/composite-formatting.md#alignment-component) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="be5dd-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="be5dd-128">Použití řídicích sekvencí v interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="be5dd-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="be5dd-129">Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v obyčejnou textové literály.</span><span class="sxs-lookup"><span data-stu-id="be5dd-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="be5dd-130">Další informace najdete v tématu [řetězec řídicí sekvence](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="be5dd-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="be5dd-131">Řídicí sekvence interpretovat oznámena, používat [typu verbatim](../language-reference/tokens/verbatim.md) řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="be5dd-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="be5dd-132">Řetězec typu verbatim interpolované začíná `$` následuje znak `@` znak.</span><span class="sxs-lookup"><span data-stu-id="be5dd-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="be5dd-133">Zahrnout závorek "{" nebo "}", ve výsledném řetězci, použijte dva složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="be5dd-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="be5dd-134">Další informace najdete v tématu [uvozovací znaky složené závorky](../../standard/base-types/composite-formatting.md#escaping-braces) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="be5dd-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="be5dd-135">Následující příklad ukazuje, jak chcete zahrnout do výsledku řetězec složené závorky a vytvořit typu verbatim interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="be5dd-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="be5dd-136">Jak používat Ternární podmíněný operátor `?:` ve výrazu interpolované</span><span class="sxs-lookup"><span data-stu-id="be5dd-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="be5dd-137">Jako dvojtečkou (":") má zvláštní význam v položku se interpolované výrazu, aby bylo možné používat [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ji v závorkách, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="be5dd-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="be5dd-138">Postup vytvoření specifické pro jazykovou verzi výsledném řetězci s řetězec interpolace</span><span class="sxs-lookup"><span data-stu-id="be5dd-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="be5dd-139">Ve výchozím nastavení používá interpolované řetězce aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnost pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="be5dd-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="be5dd-140">Implicitní převod interpolované řetězce pro použití <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="be5dd-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="be5dd-141">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="be5dd-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="be5dd-142">Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instanci pro generování vícenásobných řetězců výsledek pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="be5dd-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="be5dd-143">Postup vytvoření výsledný řetězec pomocí neutrální jazykovou verzi</span><span class="sxs-lookup"><span data-stu-id="be5dd-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="be5dd-144">Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statickou <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolované řetězce na řetězec výsledek pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="be5dd-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="be5dd-145">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="be5dd-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="be5dd-146">Závěr</span><span class="sxs-lookup"><span data-stu-id="be5dd-146">Conclusion</span></span>

<span data-ttu-id="be5dd-147">Tento kurz popisuje běžné scénáře řetězec interpolace využití.</span><span class="sxs-lookup"><span data-stu-id="be5dd-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="be5dd-148">Další informace o řetězce interpolace najdete v tématu [řetězec interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="be5dd-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="be5dd-149">Další informace o typy formátování v rozhraní .NET najdete v tématu [typy formátování v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.</span><span class="sxs-lookup"><span data-stu-id="be5dd-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="be5dd-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="be5dd-150">See also</span></span>

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[<span data-ttu-id="be5dd-151">Řetězce</span><span class="sxs-lookup"><span data-stu-id="be5dd-151">Strings</span></span>](../programming-guide/strings/index.md)  
