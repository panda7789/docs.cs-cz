---
title: 'Interpolace řetězců v C #'
description: Zjistěte, jak zahrnout formátovaný výraz výsledky ve výsledku řetězce v C# s řetězci interpolace.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039215"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="b7f29-103">Interpolace řetězců v C\#</span><span class="sxs-lookup"><span data-stu-id="b7f29-103">String interpolation in C\#</span></span>

<span data-ttu-id="b7f29-104">Tento kurz ukazuje, jak používat [interpolaci řetězce](../language-reference/tokens/interpolated.md) k formátování a zahrnutí výsledků výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="b7f29-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="b7f29-105">Příklady předpokládají, že jste obeznámeni se základními koncepty jazyka C# a formátováním typu .NET.</span><span class="sxs-lookup"><span data-stu-id="b7f29-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="b7f29-106">Pokud s interpolací řetězců nebo formátováním typu .NET teprve začínáte, podívejte se nejprve na [kurz interaktivní interpolace řetězců.](exploration/interpolated-strings.yml)</span><span class="sxs-lookup"><span data-stu-id="b7f29-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="b7f29-107">Další informace o formátování typů v rozhraní .NET naleznete v tématu [Typy formátování v rozhraní .NET.](../../standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="b7f29-108">Úvod</span><span class="sxs-lookup"><span data-stu-id="b7f29-108">Introduction</span></span>

<span data-ttu-id="b7f29-109">Funkce [interpolace řetězců](../language-reference/tokens/interpolated.md) je postavena na funkci [složeného formátování](../../standard/base-types/composite-formatting.md) a poskytuje čitelnější a pohodlnější syntaxi pro zahrnutí formátovaného výrazu do výsledného řetězce.</span><span class="sxs-lookup"><span data-stu-id="b7f29-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="b7f29-110">Chcete-li identifikovat literál řetězce jako interpolovaný řetězec, předřávejte jej symbolem. `$`</span><span class="sxs-lookup"><span data-stu-id="b7f29-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="b7f29-111">Můžete vložit libovolný platný výraz Jazyka C#, který vrátí hodnotu v interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="b7f29-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="b7f29-112">V následujícím příkladu, jakmile je výraz vyhodnocen, jeho výsledek je převeden na řetězec a zahrnuty do výsledkového řetězce:</span><span class="sxs-lookup"><span data-stu-id="b7f29-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="b7f29-113">Jak ukazuje příklad, zahrnete výraz do interpolovaného řetězce tím, že jej ohraničujete závorkami:</span><span class="sxs-lookup"><span data-stu-id="b7f29-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="b7f29-114">Interpolované řetězce podporují všechny možnosti funkce [složeného formátování řetězce.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="b7f29-115">To z nich dělá čitelnější alternativu <xref:System.String.Format%2A?displayProperty=nameWithType> k použití metody.</span><span class="sxs-lookup"><span data-stu-id="b7f29-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="b7f29-116">Jak zadat formátovací řetězec pro výraz interpolace</span><span class="sxs-lookup"><span data-stu-id="b7f29-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="b7f29-117">Formátovací řetězec, který je podporován typem výsledku výrazu, určíte podle výrazu interpolace s dvojtečkou (":") a formátovacím řetězcem:</span><span class="sxs-lookup"><span data-stu-id="b7f29-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="b7f29-118">Následující příklad ukazuje, jak zadat standardní a vlastní formátovací řetězce pro výrazy, které vytvářejí datum a čas nebo číselné výsledky:</span><span class="sxs-lookup"><span data-stu-id="b7f29-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="b7f29-119">Další informace naleznete v části [Komponenta formátovacího řetězce](../../standard/base-types/composite-formatting.md#format-string-component) v tématu [Složené formátování.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="b7f29-120">Tato část obsahuje odkazy na témata, která popisují standardní a vlastní formátovací řetězce podporované základními typy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b7f29-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="b7f29-121">Jak řídit šířku pole a zarovnání formátovaného interpolačního výrazu</span><span class="sxs-lookup"><span data-stu-id="b7f29-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="b7f29-122">Minimální šířku pole a zarovnání výsledku formátovaného výrazu určíte tak, že se budete řídit interpolačním výrazem s čárkou (",") a konstantním výrazem:</span><span class="sxs-lookup"><span data-stu-id="b7f29-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="b7f29-123">Pokud je hodnota *zarovnání* kladná, výsledek formátovaného výrazu je zarovnán doprava; Pokud je záporná, je zarovnána doleva.</span><span class="sxs-lookup"><span data-stu-id="b7f29-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="b7f29-124">Pokud potřebujete zadat zarovnání i formátovací řetězec, začněte komponentou zarovnání:</span><span class="sxs-lookup"><span data-stu-id="b7f29-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="b7f29-125">Následující příklad ukazuje, jak určit zarovnání a používá znaky kanálu ("|") k vymezení textových polí:</span><span class="sxs-lookup"><span data-stu-id="b7f29-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="b7f29-126">Jak ukazuje ukázkový výstup, pokud délka výsledku formátovaného výrazu překročí zadanou šířku pole, hodnota *zarovnání* bude ignorována.</span><span class="sxs-lookup"><span data-stu-id="b7f29-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="b7f29-127">Další informace naleznete v části [Součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) v tématu [Složené formátování.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="b7f29-128">Použití řídicích sekvencí v interpolovaném řetězci</span><span class="sxs-lookup"><span data-stu-id="b7f29-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="b7f29-129">Interpolované řetězce podporují všechny sekvence escape, které lze použít v běžných řetězcových literálech.</span><span class="sxs-lookup"><span data-stu-id="b7f29-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="b7f29-130">Další informace naleznete v [tématu String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="b7f29-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="b7f29-131">Chcete-li interpretovat escape sekvence doslova, použijte [doslovný](../language-reference/tokens/verbatim.md) řetězec literál.</span><span class="sxs-lookup"><span data-stu-id="b7f29-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="b7f29-132">Interpolovaný doslovný řetězec začíná `$` znakem následovaným znakem. `@`</span><span class="sxs-lookup"><span data-stu-id="b7f29-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="b7f29-133">Počínaje C# 8.0, můžete `$` použít `@` a tokeny v `$@"..."` `@$"..."` libovolném pořadí: oba a jsou platné interpolované doslovné řetězce.</span><span class="sxs-lookup"><span data-stu-id="b7f29-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="b7f29-134">Chcete-li zahrnout závorku {" nebo "}", použijte do výsledného řetězce dvě závorky{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="b7f29-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="b7f29-135">Další informace naleznete v části [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) v tématu [složené formátování.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="b7f29-136">Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a vytvořit doslovný interpolovaný řetězec:</span><span class="sxs-lookup"><span data-stu-id="b7f29-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="b7f29-137">Použití ternárního podmíněného `?:` operátoru ve výrazu interpolace</span><span class="sxs-lookup"><span data-stu-id="b7f29-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="b7f29-138">Jako dvojtečka (":") má zvláštní význam v položce s výrazem interpolace, aby bylo možné použít [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete jej do závorek, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b7f29-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="b7f29-139">Jak vytvořit výsledný řetězec specifický pro jazykovou verzi s interpolací řetězců</span><span class="sxs-lookup"><span data-stu-id="b7f29-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="b7f29-140">Ve výchozím nastavení používá interpolovaný řetězec aktuální <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> jazykovou verzi definovanou vlastností pro všechny operace formátování.</span><span class="sxs-lookup"><span data-stu-id="b7f29-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="b7f29-141">Použijte implicitní převod interpolovaného <xref:System.FormattableString?displayProperty=nameWithType> řetězce na <xref:System.FormattableString.ToString(System.IFormatProvider)> instanci a zavolejte její metodu k vytvoření výsledného řetězce specifického pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b7f29-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="b7f29-142">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="b7f29-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="b7f29-143">Jak ukazuje příklad, můžete <xref:System.FormattableString> použít jednu instanci ke generování více řetězců výsledků pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="b7f29-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="b7f29-144">Jak vytvořit výsledný řetězec pomocí invariantní jazykové verze</span><span class="sxs-lookup"><span data-stu-id="b7f29-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="b7f29-145">Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodou můžete použít <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> statickou metodu k vyřešení interpolovaného <xref:System.Globalization.CultureInfo.InvariantCulture>řetězce na výsledný řetězec pro .</span><span class="sxs-lookup"><span data-stu-id="b7f29-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="b7f29-146">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="b7f29-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="b7f29-147">Závěr</span><span class="sxs-lookup"><span data-stu-id="b7f29-147">Conclusion</span></span>

<span data-ttu-id="b7f29-148">Tento kurz popisuje běžné scénáře použití interpolace řetězce.</span><span class="sxs-lookup"><span data-stu-id="b7f29-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="b7f29-149">Další informace o interpolaci řetězců naleznete v tématu [Interpolace řetězce.](../language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="b7f29-150">Další informace o typech formátování v rozhraní .NET naleznete v tématech Typy formátování v tématech [rozhraní .NET](../../standard/base-types/formatting-types.md) a [Složené formátování.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b7f29-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7f29-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7f29-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="b7f29-152">Řetězce</span><span class="sxs-lookup"><span data-stu-id="b7f29-152">Strings</span></span>](../programming-guide/strings/index.md)
