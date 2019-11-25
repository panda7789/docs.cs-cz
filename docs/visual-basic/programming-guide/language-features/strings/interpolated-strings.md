---
title: Interpolované řetězce
ms.date: 10/31/2017
ms.openlocfilehash: d1220f3804d571f6da229dc5dfa099a22ab1478d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344326"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="2f2ce-102">Interpolated Strings (Visual Basic Reference)</span><span class="sxs-lookup"><span data-stu-id="2f2ce-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="2f2ce-103">Used to construct strings.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-103">Used to construct strings.</span></span>  <span data-ttu-id="2f2ce-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="2f2ce-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="2f2ce-106">This feature is available in Visual Basic 14 and later versions.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="2f2ce-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="2f2ce-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="2f2ce-108">For example, the interpolated string</span><span class="sxs-lookup"><span data-stu-id="2f2ce-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="2f2ce-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="2f2ce-110">The equivalent composite format string is:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="2f2ce-111">The structure of an interpolated string is:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="2f2ce-112">kde:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-112">where:</span></span>

- <span data-ttu-id="2f2ce-113">*field-width* is a signed integer that indicates the number of characters in the field.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="2f2ce-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="2f2ce-115">*format-string* is a format string appropriate for the type of object being formatted.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="2f2ce-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span><span class="sxs-lookup"><span data-stu-id="2f2ce-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f2ce-117">You cannot have any white space between the `$` and the `"` that starts the string.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="2f2ce-118">Doing so causes a compiler error.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="2f2ce-119">You can use an interpolated string anywhere you can use a string literal.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="2f2ce-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="2f2ce-121">This allows you to separate the definition and evaluation of an interpolated string.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="2f2ce-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span><span class="sxs-lookup"><span data-stu-id="2f2ce-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="2f2ce-123">See the Implicit Conversions section for more details.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="2f2ce-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="2f2ce-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="2f2ce-126">Implicit Conversions</span><span class="sxs-lookup"><span data-stu-id="2f2ce-126">Implicit Conversions</span></span>

<span data-ttu-id="2f2ce-127">There are three implicit type conversions from an interpolated string:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="2f2ce-128">Conversion of an interpolated string to a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="2f2ce-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="2f2ce-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="2f2ce-131">This is the final result of a string interpretation.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="2f2ce-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="2f2ce-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="2f2ce-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="2f2ce-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="2f2ce-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="2f2ce-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="2f2ce-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="2f2ce-139">Note that the interpolated string can be inspected only by using reflection.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="2f2ce-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="2f2ce-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="2f2ce-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="2f2ce-143">A <xref:System.FormattableString> also includes:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="2f2ce-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="2f2ce-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="2f2ce-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="2f2ce-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="2f2ce-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span><span class="sxs-lookup"><span data-stu-id="2f2ce-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="2f2ce-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f2ce-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="2f2ce-150">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f2ce-150">Visual Basic Language Reference</span></span>](index.md)
