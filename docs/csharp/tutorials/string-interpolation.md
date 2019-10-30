---
title: Interpolace řetězce vC#
description: Naučte se, jak zahrnout formátovaný výraz do výsledného řetězce C# v rámci s interpolací řetězce.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039215"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="c2274-103">Interpolace řetězce v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="c2274-103">String interpolation in C\#</span></span>

<span data-ttu-id="c2274-104">V tomto kurzu se dozvíte, jak použít [interpolaci řetězců](../language-reference/tokens/interpolated.md) k formátování a zahrnutí výsledků výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2274-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="c2274-105">V příkladech se předpokládá, že máte zkušenosti C# se základními koncepty a formátování typu .NET.</span><span class="sxs-lookup"><span data-stu-id="c2274-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="c2274-106">Pokud začínáte s interpolací řetězců nebo formátováním typu .NET, přečtěte si nejprve [kurz o interpolaci interaktivních řetězců](exploration/interpolated-strings.yml) .</span><span class="sxs-lookup"><span data-stu-id="c2274-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="c2274-107">Další informace o typech formátování v rozhraní .NET naleznete v tématu [typy formátování v rozhraní .NET](../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="c2274-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="c2274-108">Introduction</span></span>

<span data-ttu-id="c2274-109">Funkce [interpolace řetězců](../language-reference/tokens/interpolated.md) je postavená na základě funkce [složeného formátování](../../standard/base-types/composite-formatting.md) a poskytuje čitelnější a pohodlnější syntaxi pro zahrnutí formátovaného výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2274-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="c2274-110">Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho symbolem `$`.</span><span class="sxs-lookup"><span data-stu-id="c2274-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="c2274-111">Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolované řetězcové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="c2274-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="c2274-112">V následujícím příkladu, jakmile je vyhodnocen výraz, je výsledek převeden na řetězec a zahrnutý do výsledného řetězce:</span><span class="sxs-lookup"><span data-stu-id="c2274-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="c2274-113">Jak ukazuje příklad, zahrnete výraz do interpolované řetězcové části jeho uzavřením do složených závorek:</span><span class="sxs-lookup"><span data-stu-id="c2274-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="c2274-114">Interpolované řetězce podporují všechny možnosti funkce [složeného formátování řetězce](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="c2274-115">Díky tomu jsou čitelnější alternativa k použití metody <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2274-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="c2274-116">Určení formátovacího řetězce pro výraz interpolace</span><span class="sxs-lookup"><span data-stu-id="c2274-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="c2274-117">Zadejte řetězec formátu, který je podporován typem výsledku výrazu, pomocí výrazu interpolace dvojtečkou (":") a řetězcem formátu:</span><span class="sxs-lookup"><span data-stu-id="c2274-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="c2274-118">Následující příklad ukazuje, jak zadat standardní a vlastní formátovací řetězce pro výrazy, které tvoří datum a čas nebo číselné výsledky:</span><span class="sxs-lookup"><span data-stu-id="c2274-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="c2274-119">Další informace naleznete v části [formátovací řetězec komponenty](../../standard/base-types/composite-formatting.md#format-string-component) v tématu [složené formátování](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="c2274-120">Tato část obsahuje odkazy na témata, která popisují standardní a vlastní formátovací řetězce podporované typy .NET Base.</span><span class="sxs-lookup"><span data-stu-id="c2274-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="c2274-121">Jak řídit šířku pole a zarovnání formátovaného výrazu interpolace</span><span class="sxs-lookup"><span data-stu-id="c2274-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="c2274-122">Určete minimální šířku pole a zarovnání formátovaného výrazu pomocí výrazu interpolace s čárkou (",") a výrazem konstanty:</span><span class="sxs-lookup"><span data-stu-id="c2274-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="c2274-123">Pokud je hodnota *Zarovnání* kladná, formátovaný výsledek výrazu je zarovnán vpravo; Pokud je záporná, zůstane zarovnaná doleva.</span><span class="sxs-lookup"><span data-stu-id="c2274-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="c2274-124">Pokud potřebujete zadat jak zarovnání, tak formátovací řetězec, začněte součástí zarovnání:</span><span class="sxs-lookup"><span data-stu-id="c2274-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="c2274-125">Následující příklad ukazuje, jak zadat zarovnání a použít znaky kanálu (|) k oddělení textových polí:</span><span class="sxs-lookup"><span data-stu-id="c2274-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="c2274-126">Jak ukazuje výstup, pokud délka formátovaného výsledku výrazu překročí zadanou šířku pole, hodnota *Zarovnání* se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="c2274-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="c2274-127">Další informace naleznete v části [Zarovnání komponenty](../../standard/base-types/composite-formatting.md#alignment-component) v tématu [složené formátování](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="c2274-128">Použití řídicích sekvencí v interpolované řetězci</span><span class="sxs-lookup"><span data-stu-id="c2274-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="c2274-129">Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžných řetězcových literálech.</span><span class="sxs-lookup"><span data-stu-id="c2274-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="c2274-130">Další informace naleznete v tématu [řetězcové řídicí sekvence](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="c2274-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="c2274-131">Pro interpretaci řídicích sekvencí doslova pomocí [doslovného](../language-reference/tokens/verbatim.md) řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="c2274-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="c2274-132">Interpolované doslovné řetězce začíná znakem `$` následovaným `@` znakem.</span><span class="sxs-lookup"><span data-stu-id="c2274-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="c2274-133">Počínaje C# 8,0 můžete použít tokeny`$`a`@`v libovolném pořadí: `$@"..."`i`@$"..."`jsou platné interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2274-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="c2274-134">Chcete-li ve výsledném řetězci zahrnout složené závorky "{" nebo "}", použijte dvě složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="c2274-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="c2274-135">Další informace naleznete v části [uvozovací závorky](../../standard/base-types/composite-formatting.md#escaping-braces) v tématu [složeného formátování](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="c2274-136">Následující příklad ukazuje, jak zahrnout složené závorky ve výsledném řetězci a sestavit doslovné řetězec v doslovném znění:</span><span class="sxs-lookup"><span data-stu-id="c2274-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="c2274-137">Jak použít Ternární podmíněný operátor `?:` ve výrazu interpolace</span><span class="sxs-lookup"><span data-stu-id="c2274-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="c2274-138">Jako dvojtečka (":") má zvláštní význam v položce s výrazem interpolace, aby bylo možné použít [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřít jej do závorek, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c2274-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="c2274-139">Jak vytvořit výsledný řetězec specifický pro jazykovou verzi s interpolací řetězce</span><span class="sxs-lookup"><span data-stu-id="c2274-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="c2274-140">Ve výchozím nastavení používá interpolující řetězec aktuální jazykovou verzi definovanou vlastností <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="c2274-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="c2274-141">Použijte implicitní převod interpolované řetězcové instance <xref:System.FormattableString?displayProperty=nameWithType> a voláním své <xref:System.FormattableString.ToString(System.IFormatProvider)> metody vytvořte výsledný řetězec specifický pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c2274-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="c2274-142">Následující příklad ukazuje, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="c2274-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="c2274-143">Jak ukazuje příklad, můžete použít jednu instanci <xref:System.FormattableString> pro generování více výsledných řetězců pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="c2274-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="c2274-144">Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze</span><span class="sxs-lookup"><span data-stu-id="c2274-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="c2274-145">Spolu s metodou <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> můžete použít statickou <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metodu k překladu interpolované řetězce na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="c2274-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="c2274-146">Následující příklad ukazuje, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="c2274-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="c2274-147">Závěr</span><span class="sxs-lookup"><span data-stu-id="c2274-147">Conclusion</span></span>

<span data-ttu-id="c2274-148">Tento kurz popisuje běžné scénáře použití řetězcové interpolace.</span><span class="sxs-lookup"><span data-stu-id="c2274-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="c2274-149">Další informace o interpolaci řetězců naleznete v tématu o [interpolaci řetězce](../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="c2274-150">Další informace o typech formátování v rozhraní .NET naleznete v tématech [typy formátování v rozhraní .NET a ve](../../standard/base-types/formatting-types.md) [složených formátováních](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="c2274-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2274-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2274-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="c2274-152">Řetězce</span><span class="sxs-lookup"><span data-stu-id="c2274-152">Strings</span></span>](../programming-guide/strings/index.md)
