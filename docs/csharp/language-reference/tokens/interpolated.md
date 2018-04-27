---
title: $ – řetězec interpolace (referenční dokumentace jazyka C#)
description: Řetězec interpolace poskytuje čitelnější a pohodlný syntaxe k formátování výstupu řetězec než tradiční řetězec složené formátování.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="b6b40-103">$ – řetězec interpolace (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b6b40-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="b6b40-104">`$` Speciální znak identifikuje řetězcový literál jako *interpolované řetězce*.</span><span class="sxs-lookup"><span data-stu-id="b6b40-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="b6b40-105">Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="b6b40-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="b6b40-106">Po vyřešení interpolované řetězce na řetězec výsledek položky s interpolované výrazy se nahrazují řetězcové vyjádření výsledků výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6b40-106">When the interpolated string is resolved to the result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="b6b40-107">Tato funkce je k dispozici v C# 6 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="b6b40-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="b6b40-108">Poskytuje řetězec interpolace čitelnější a pohodlný syntaxe pro vytvoření formátované řetězce než [řetězce složené formátování](../../../standard/base-types/composite-formatting.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b6b40-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="b6b40-109">Následující příklad používá k vytvoření stejný výstup obě funkce:</span><span class="sxs-lookup"><span data-stu-id="b6b40-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="b6b40-110">Nemůže mít žádné mezer mezi `$` a `"` , začíná řetězec.</span><span class="sxs-lookup"><span data-stu-id="b6b40-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="b6b40-111">To způsobí, že chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="b6b40-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="b6b40-112">Struktura položky s interpolované výrazu je následující:</span><span class="sxs-lookup"><span data-stu-id="b6b40-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="b6b40-113">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="b6b40-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="b6b40-114">Následující tabulka popisuje jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="b6b40-114">The following table describes each element.</span></span>

|<span data-ttu-id="b6b40-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6b40-115">Element</span></span>|<span data-ttu-id="b6b40-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b6b40-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="b6b40-117">Výraz k vyhodnocení k získání výsledku, který má být formátována.</span><span class="sxs-lookup"><span data-stu-id="b6b40-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="b6b40-118">Řetězec reprezentace `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6b40-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="b6b40-119">Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolované výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6b40-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="b6b40-120">Pokud kladné, je řetězcová reprezentace vpravo zarovnaný; záporná, je zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="b6b40-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="b6b40-121">Další informace najdete v tématu [zarovnání součást](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="b6b40-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="b6b40-122">Řetězec standardní nebo vlastní formát, který podporuje typ výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6b40-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="b6b40-123">Další informace najdete v tématu [součást řetězce formátu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="b6b40-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="b6b40-124">Následující příklad používá volitelné formátování komponent popsaných výše:</span><span class="sxs-lookup"><span data-stu-id="b6b40-124">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="b6b40-125">Zahrnout složená závorka ("{" nebo "}") v textu vyprodukované interpolované řetězce, použijte dva složené závorky "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="b6b40-125">To include a brace ("{" or "}") in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="b6b40-126">Další informace najdete v tématu [uvozovací znaky složené závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="b6b40-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="b6b40-127">Dvojtečkou (:) má zvláštní význam interpolované výraz položku, aby bylo možné používat [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolované uzavřete výrazu v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b6b40-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="b6b40-128">Následující příklad ukazuje, jak se zahrnuje do řetězce výsledek složená závorka a jak používat podmíněný operátor v interpolované výrazu:</span><span class="sxs-lookup"><span data-stu-id="b6b40-128">The following example shows how to include a brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="b6b40-129">Doslovné interpolované řetězce použití `$` následuje znak `@` znak.</span><span class="sxs-lookup"><span data-stu-id="b6b40-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="b6b40-130">Další informace o typu verbatim řetězců najdete v tématu [řetězec](../keywords/string.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b6b40-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="b6b40-131">`$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="b6b40-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

<span data-ttu-id="b6b40-132">Existují tři implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="b6b40-132">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="b6b40-133">Interpolované řetězce pro převod <xref:System.String> instanci, která je výsledkem interpolované řetězce řešení pomocí výrazu interpolované položky nahrazován správně formátovaný řetězec reprezentace jejich výsledky.</span><span class="sxs-lookup"><span data-stu-id="b6b40-133">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="b6b40-134">Tento převod používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b6b40-134">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="b6b40-135">Interpolované řetězce pro převod <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu formátování.</span><span class="sxs-lookup"><span data-stu-id="b6b40-135">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="b6b40-136">Což vám umožní vytvořit více řetězců výsledek s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance.</span><span class="sxs-lookup"><span data-stu-id="b6b40-136">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="b6b40-137">Chcete-li provést volání jednoho z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="b6b40-137">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="b6b40-138">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="b6b40-138">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="b6b40-139">A <xref:System.FormattableString.Invariant%2A> metoda, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="b6b40-139">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="b6b40-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b6b40-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="b6b40-141">Interpolované řetězce pro převod <xref:System.IFormattable> instanci, která umožňuje taky vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="b6b40-141">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="b6b40-142">Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit výsledek specifické pro jazykovou verzi řetězce:</span><span class="sxs-lookup"><span data-stu-id="b6b40-142">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

<span data-ttu-id="b6b40-143">Pokud začínáte interpolace řetězec, podívejte se [řetězec interpolace v jazyce C#](../../quick-starts/interpolated-strings.yml) rychlý start.</span><span class="sxs-lookup"><span data-stu-id="b6b40-143">If you are new to the string interpolation, check the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="b6b40-144">Další příklady najdete v tématu [řetězec interpolace kurzu](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="b6b40-144">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6b40-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6b40-145">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="b6b40-146">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="b6b40-146">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="b6b40-147">Řetězce</span><span class="sxs-lookup"><span data-stu-id="b6b40-147">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="b6b40-148">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b6b40-148">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="b6b40-149">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b6b40-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b6b40-150">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b6b40-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  