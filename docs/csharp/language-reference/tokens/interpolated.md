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
ms.openlocfilehash: b6873c3b419323fa9f5523143ad607289b6fd6e2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="df511-103">$ – řetězec interpolace (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="df511-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="df511-104">`$` Speciální znak identifikuje řetězcový literál jako *interpolované řetězce*.</span><span class="sxs-lookup"><span data-stu-id="df511-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="df511-105">Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="df511-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="df511-106">Při vyřešení interpolované řetězce, například v příkazu přiřazení nebo volání metody interpolované výrazy se nahrazují řetězcové vyjádření jejich výsledků k vytvoření výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="df511-106">When the interpolated string is resolved, for example in an assignment statement or a method call, interpolated expressions are replaced by the string representations of their results to produce the result string.</span></span> <span data-ttu-id="df511-107">Tato funkce je k dispozici v C# 6 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="df511-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="df511-108">Řetězec interpolace je čitelnější a pohodlný způsob, jak vytvořit formátované řetězce než [řetězce složené formátování](../../../standard/base-types/composite-formatting.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="df511-108">String interpolation is a more readable and convenient way to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="df511-109">Následující příklad používá k vytvoření stejný výstup obě funkce:</span><span class="sxs-lookup"><span data-stu-id="df511-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="df511-110">Nemůže mít žádné mezer mezi `$` a `"` , začíná řetězec.</span><span class="sxs-lookup"><span data-stu-id="df511-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="df511-111">To způsobí, že chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="df511-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="df511-112">Struktura položky s interpolované výrazu je následující:</span><span class="sxs-lookup"><span data-stu-id="df511-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="df511-113">Prvky v hranatých závorkách jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="df511-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="df511-114">Následující tabulka popisuje jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="df511-114">The following table describes each element.</span></span>

|<span data-ttu-id="df511-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="df511-115">Element</span></span>|<span data-ttu-id="df511-116">Popis</span><span class="sxs-lookup"><span data-stu-id="df511-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="df511-117">Výraz k vyhodnocení k získání výsledku, který má být formátována.</span><span class="sxs-lookup"><span data-stu-id="df511-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="df511-118">Řetězec reprezentace `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df511-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="df511-119">Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolované výrazu.</span><span class="sxs-lookup"><span data-stu-id="df511-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="df511-120">Pokud kladné, je řetězcová reprezentace vpravo zarovnaný; záporná, je zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="df511-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="df511-121">Další informace najdete v tématu [zarovnání součást](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="df511-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="df511-122">Řetězec standardní nebo vlastní formát, který podporuje typ výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="df511-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="df511-123">Další informace najdete v tématu [součást řetězce formátu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="df511-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="df511-124">Následující příklad používá volitelné formátování komponent popsaných v předchozí tabulce:</span><span class="sxs-lookup"><span data-stu-id="df511-124">The following example uses optional formatting components described in the table above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="df511-125">Zahrnout složené závorky ("{" nebo "}") v textu vyprodukované interpolované řetězce, použijte dva složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="df511-125">To include a curly brace ("{" or "}") in the text produced by an interpolated string, use two curly braces, "{{" or "}}".</span></span> <span data-ttu-id="df511-126">Další informace najdete v tématu [uvozovací znaky složené závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="df511-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="df511-127">Dvojtečkou (:) má zvláštní význam interpolované výraz položku, aby bylo možné používat [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolované uzavřete výrazu v závorkách.</span><span class="sxs-lookup"><span data-stu-id="df511-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="df511-128">Následující příklad ukazuje, jak se zahrnuje do řetězce výsledek složené závorky a jak používat podmíněný operátor v interpolované výrazu:</span><span class="sxs-lookup"><span data-stu-id="df511-128">The following example shows how to include a curly brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="df511-129">Doslovné interpolované řetězce použití `$` následuje znak `@` znak.</span><span class="sxs-lookup"><span data-stu-id="df511-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="df511-130">Další informace o typu verbatim řetězců najdete v tématu [řetězec](../keywords/string.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="df511-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="df511-131">`$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="df511-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions"></a><span data-ttu-id="df511-132">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="df511-132">Implicit conversions</span></span>

<span data-ttu-id="df511-133">Existují tři typu implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="df511-133">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="df511-134">Interpolované řetězce pro převod <xref:System.String> instanci, která je výsledkem interpolované řetězce řešení pomocí výrazu interpolované položky nahrazován správně formátovaný řetězec reprezentace jejich výsledky.</span><span class="sxs-lookup"><span data-stu-id="df511-134">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="df511-135">Tento převod používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="df511-135">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="df511-136">Interpolované řetězce pro převod <xref:System.FormattableString> proměnné, která představuje složený formátovací řetězec spolu s výsledky výraz, který má být formátována.</span><span class="sxs-lookup"><span data-stu-id="df511-136">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="df511-137">Což vám umožní vytvořit více řetězců výsledek s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance.</span><span class="sxs-lookup"><span data-stu-id="df511-137">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="df511-138">Chcete-li provést volání jednoho z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="df511-138">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="df511-139">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="df511-139">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="df511-140">A <xref:System.FormattableString.Invariant%2A> metoda, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="df511-140">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="df511-141">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="df511-141">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="df511-142">Interpolované řetězce pro převod <xref:System.IFormattable> proměnné, která umožňuje taky vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="df511-142">Conversion of an interpolated string to an <xref:System.IFormattable> variable that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="df511-143">Následující příklad používá implicitní převod na <xref:System.FormattableString> pro vytváření řetězců výsledek specifické pro jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="df511-143">The following example uses implicit conversion to <xref:System.FormattableString> for creating culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-reading"></a><span data-ttu-id="df511-144">Další čtení</span><span class="sxs-lookup"><span data-stu-id="df511-144">Additional reading</span></span>

<span data-ttu-id="df511-145">Pokud začínáte interpolace řetězec, podívejte se [interpolované řetězce rychlý Start](../../quick-starts//interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="df511-145">If you are new to the string interpolation, check the [interpolated strings quickstart](../../quick-starts//interpolated-strings.yml).</span></span> <span data-ttu-id="df511-146">Další příklady najdete v tématu [řetězec interpolace kurzu](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="df511-146">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df511-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="df511-147">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="df511-148">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="df511-148">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="df511-149">Řetězce</span><span class="sxs-lookup"><span data-stu-id="df511-149">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="df511-150">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="df511-150">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="df511-151">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="df511-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="df511-152">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df511-152">C# Reference</span></span>](../../../csharp/language-reference/index.md)  