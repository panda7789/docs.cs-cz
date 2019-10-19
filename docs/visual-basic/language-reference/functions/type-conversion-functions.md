---
title: Funkce pro převod typů (Visual Basic)
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 0516a579c1ad9944284d25f2f057f2f03619bbab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582992"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="e7268-102">Funkce pro převod typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7268-102">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="e7268-103">Tyto funkce jsou kompilovány vložené, což znamená, že kód převodu je součástí kódu, který vyhodnocuje výraz.</span><span class="sxs-lookup"><span data-stu-id="e7268-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="e7268-104">Někdy neexistuje žádné volání procedury k provedení převodu, což zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="e7268-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="e7268-105">Každá funkce převede výraz na konkrétní datový typ.</span><span class="sxs-lookup"><span data-stu-id="e7268-105">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7268-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7268-106">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="e7268-107">Částí</span><span class="sxs-lookup"><span data-stu-id="e7268-107">Part</span></span>

`expression`  
<span data-ttu-id="e7268-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e7268-108">Required.</span></span> <span data-ttu-id="e7268-109">Libovolný výraz zdrojového datového typu.</span><span class="sxs-lookup"><span data-stu-id="e7268-109">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="e7268-110">Datový typ vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7268-110">Return Value Data Type</span></span>

<span data-ttu-id="e7268-111">Název funkce určuje datový typ hodnoty, kterou vrátí, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e7268-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="e7268-112">Název funkce</span><span class="sxs-lookup"><span data-stu-id="e7268-112">Function name</span></span>|<span data-ttu-id="e7268-113">Návratový typ dat</span><span class="sxs-lookup"><span data-stu-id="e7268-113">Return data type</span></span>|<span data-ttu-id="e7268-114">Rozsah pro argument `expression`</span><span class="sxs-lookup"><span data-stu-id="e7268-114">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="e7268-115">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="e7268-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="e7268-116">Libovolný platný `Char` nebo `String` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="e7268-116">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="e7268-117">Datový typ Byte</span><span class="sxs-lookup"><span data-stu-id="e7268-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="e7268-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) až <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-119">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucího bodu na převod bajtů pomocí funkce `CByte`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-120">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-120">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="e7268-121">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="e7268-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="e7268-122">Libovolný platný `Char` nebo výraz `String`; je převeden pouze první znak `String`; hodnota může být 0 až 65535 (bez znaménka).</span><span class="sxs-lookup"><span data-stu-id="e7268-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="e7268-123">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="e7268-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="e7268-124">Jakákoli platná reprezentace data a času.</span><span class="sxs-lookup"><span data-stu-id="e7268-124">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="e7268-125">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="e7268-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="e7268-126">-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 pro záporné hodnoty; 4.94065645841246544 e-324 až 1.79769313486231570 E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e7268-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="e7268-127">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="e7268-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="e7268-128">+/-79,228,162,514,264,337,593,543,950,335 pro čísla s nulovou škálou, tj. čísla bez desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="e7268-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="e7268-129">Pro čísla s 28 desetinnými místy je rozsah +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="e7268-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="e7268-130">Nejmenší možné nenulové číslo je 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="e7268-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="e7268-131">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="e7268-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="e7268-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2 147 483 648) až <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="e7268-133">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na převod celého čísla pomocí funkce `CInt`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-134">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-134">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="e7268-135">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="e7268-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="e7268-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) až <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-137">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon konverze s plovoucí desetinnou čárkou na 64 celočíselnou hodnotu pomocí funkce `CLng`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-138">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-138">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="e7268-139">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="e7268-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="e7268-140">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="e7268-140">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="e7268-141">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="e7268-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="e7268-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) až <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-143">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na podepsaný bajtový převod pomocí funkce `CSByte`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-144">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-144">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="e7268-145">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="e7268-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="e7268-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) až <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-147">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na 16bitový celočíselný převod pomocí funkce `CShort`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-148">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-148">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="e7268-149">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="e7268-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="e7268-150">-3.402823 e + + 38 do-1.401298 E-45 pro záporné hodnoty; 1.401298 e-45 až 3.402823 E + 38 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e7268-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="e7268-151">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="e7268-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="e7268-152">Funkce vrátí pro `CStr` závisí na argumentu `expression`.</span><span class="sxs-lookup"><span data-stu-id="e7268-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="e7268-153">Viz [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="e7268-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="e7268-154">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="e7268-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="e7268-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-156">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na unsigned integer konverzi pomocí funkce `CUInt`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-157">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-157">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="e7268-158">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="e7268-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="e7268-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-160">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na nepodepsaný dlouhý celočíselný převod pomocí funkce `CULng`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-161">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-161">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="e7268-162">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="e7268-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="e7268-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7268-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e7268-164">Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na 16bitový celočíselný převod s funkcí `CUShort`; Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="e7268-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e7268-165">Příklad najdete v části s [Příklady CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="e7268-165">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="e7268-166"><sup>1</sup> zlomkové části mohou být předmětem zvláštního typu zaokrouhlení s názvem *zaokrouhlování bank*.</span><span class="sxs-lookup"><span data-stu-id="e7268-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="e7268-167">Další informace najdete v části "poznámky".</span><span class="sxs-lookup"><span data-stu-id="e7268-167">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7268-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7268-168">Remarks</span></span>

<span data-ttu-id="e7268-169">Jako pravidlo byste měli použít funkce Visual Basic pro převod typu v předvolbách pro metody .NET Framework, jako je `ToString()`, buď na <xref:System.Convert> třídu, nebo na samostatné struktuře typu nebo třídě.</span><span class="sxs-lookup"><span data-stu-id="e7268-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="e7268-170">Funkce Visual Basic jsou navržené pro optimální interakci s kódem Visual Basic a zároveň usnadňují čtení zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e7268-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="e7268-171">Kromě toho metody převodu .NET Framework nevytváří vždy stejné výsledky jako funkce Visual Basic, například při převodu `Boolean` na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e7268-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="e7268-172">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="e7268-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="e7268-173">Počínaje Visual Basic 15,8 je výkon konverze s plovoucí desetinnou čárkou na celé číslo optimalizovaný, Pokud předáte <xref:System.Single> nebo <xref:System.Double> hodnotu vrácenou následujícími metodami do jedné z funkcí konverze celého čísla (`CByte`, `CShort`, `CInt`, @no__ t_5, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="e7268-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="e7268-174">Tato optimalizace umožňuje kódu, který provede velký počet převodů celých čísel, aby běžel dvakrát jako rychlý.</span><span class="sxs-lookup"><span data-stu-id="e7268-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="e7268-175">Následující příklad znázorňuje tyto optimalizované převody s plovoucí desetinnou čárkou na celé číslo:</span><span class="sxs-lookup"><span data-stu-id="e7268-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="e7268-176">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="e7268-176">Behavior</span></span>

- <span data-ttu-id="e7268-177">**Konverze za.**</span><span class="sxs-lookup"><span data-stu-id="e7268-177">**Coercion.**</span></span> <span data-ttu-id="e7268-178">Obecně můžete použít funkce pro převod datového typu k převedení výsledku operace na určitý datový typ, nikoli na výchozí datový typ.</span><span class="sxs-lookup"><span data-stu-id="e7268-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="e7268-179">Například můžete použít `CDec` k vynucení desítkové aritmetické operace v případech, kdy by normálně probíhat jednoduché přepřesnost, dvojitá přesnost nebo aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="e7268-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="e7268-180">**Převody se nezdařily.**</span><span class="sxs-lookup"><span data-stu-id="e7268-180">**Failed Conversions.**</span></span> <span data-ttu-id="e7268-181">Pokud `expression` předané funkci spadá mimo rozsah datového typu, na který má být převeden, dojde k <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="e7268-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="e7268-182">**Zlomkové části.**</span><span class="sxs-lookup"><span data-stu-id="e7268-182">**Fractional Parts.**</span></span> <span data-ttu-id="e7268-183">Když převedete neceločíselnou hodnotu na celočíselný typ, funkce převodu celého čísla (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` a `CUShort`) odstraní zlomkovou část a zaokrouhlí hodnotu na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e7268-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="e7268-184">Pokud je Zlomková část přesně 0,5, funkce pro převod celého čísla zaokrouhlí na nejbližší sudé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e7268-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="e7268-185">Například 0,5 se zaokrouhlí na 0 a 1,5 a 2,5 se zaokrouhlí na 2.</span><span class="sxs-lookup"><span data-stu-id="e7268-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="e7268-186">Tento postup se někdy označuje jako *zaokrouhlování bank*a jeho účelem je kompenzovat posun, který by se mohl nashromáždit při přidávání mnoha takových čísel dohromady.</span><span class="sxs-lookup"><span data-stu-id="e7268-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="e7268-187">`CInt` a `CLng` se liší od <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A>ch funkcí, které se zkrátí, spíše než zaokrouhlí na zlomkovou část čísla.</span><span class="sxs-lookup"><span data-stu-id="e7268-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="e7268-188">Také `Fix` a `Int` vždycky vracet hodnotu stejného datového typu jako při předání.</span><span class="sxs-lookup"><span data-stu-id="e7268-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="e7268-189">**Převody data a času.**</span><span class="sxs-lookup"><span data-stu-id="e7268-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="e7268-190">Pomocí funkce <xref:Microsoft.VisualBasic.Information.IsDate%2A> určíte, zda je možné hodnotu převést na datum a čas.</span><span class="sxs-lookup"><span data-stu-id="e7268-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="e7268-191">`CDate` rozpoznává literály kalendářních dat a časové literály, ale ne číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e7268-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="e7268-192">Chcete-li převést hodnotu `Date` Visual Basic 6,0 na hodnotu `Date` v Visual Basic 2005 nebo novějších verzích, můžete použít metodu <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7268-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="e7268-193">**Neutrální hodnoty data a času.**</span><span class="sxs-lookup"><span data-stu-id="e7268-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="e7268-194">[Datový typ datum](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a čase.</span><span class="sxs-lookup"><span data-stu-id="e7268-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="e7268-195">Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas.</span><span class="sxs-lookup"><span data-stu-id="e7268-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="e7268-196">Převedete-li `Date` hodnotu na řetězec, `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="e7268-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="e7268-197">Pokud například převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00 dop."; informace o datu jsou potlačeny.</span><span class="sxs-lookup"><span data-stu-id="e7268-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="e7268-198">Informace o datu jsou však stále přítomny v původní hodnotě `Date` a lze je obnovit pomocí funkcí, jako je například funkce <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7268-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="e7268-199">**Citlivostní jazyková verze.**</span><span class="sxs-lookup"><span data-stu-id="e7268-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="e7268-200">Funkce pro převod typů zahrnující řetězce provádějí převody na základě aktuálního nastavení jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7268-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="e7268-201">@No__t_0 například rozpoznává formáty data podle nastavení národního prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="e7268-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="e7268-202">Je nutné zadat den, měsíc a rok ve správném pořadí pro vaše národní prostředí nebo datum nemusí být interpretováno správně.</span><span class="sxs-lookup"><span data-stu-id="e7268-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="e7268-203">Formát dlouhého data není rozpoznán, pokud obsahuje řetězec dne v týdnu, například "Středa".</span><span class="sxs-lookup"><span data-stu-id="e7268-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="e7268-204">Pokud potřebujete převést na nebo z řetězcové reprezentace hodnoty v jiném formátu, než který je určen národním prostředím, nemůžete použít funkce pro převod typu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e7268-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="e7268-205">Chcete-li to provést, použijte metody `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e7268-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="e7268-206">Například použijte <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu řetězce na `Double` a použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.</span><span class="sxs-lookup"><span data-stu-id="e7268-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="e7268-207">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="e7268-207">CType Function</span></span>

<span data-ttu-id="e7268-208">[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) přebírá druhý argument, `typename` a převede `expression` na `typename`, kde `typename` může být libovolný datový typ, struktura, třída nebo rozhraní, na které existuje platný převod.</span><span class="sxs-lookup"><span data-stu-id="e7268-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="e7268-209">Porovnání `CType` s jinými klíčovými slovy převodu typů naleznete v tématu [operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) a [operátor TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e7268-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="e7268-210">Příklad CBool</span><span class="sxs-lookup"><span data-stu-id="e7268-210">CBool Example</span></span>

<span data-ttu-id="e7268-211">V následujícím příkladu je použita funkce `CBool` pro převod výrazů na hodnoty `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e7268-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="e7268-212">Pokud je výraz vyhodnocen jako nenulová hodnota, `CBool` vrátí `True`; v opačném případě vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="e7268-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="e7268-213">Příklad CByte</span><span class="sxs-lookup"><span data-stu-id="e7268-213">CByte Example</span></span>

<span data-ttu-id="e7268-214">V následujícím příkladu je použita funkce `CByte` pro převod výrazu na `Byte`.</span><span class="sxs-lookup"><span data-stu-id="e7268-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="e7268-215">Příklad CChar</span><span class="sxs-lookup"><span data-stu-id="e7268-215">CChar Example</span></span>

<span data-ttu-id="e7268-216">V následujícím příkladu je použita funkce `CChar` pro převedení prvního znaku `String` výrazu na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="e7268-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="e7268-217">Vstupní argument pro `CChar` musí být datového typu `Char` nebo `String`.</span><span class="sxs-lookup"><span data-stu-id="e7268-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="e7268-218">Pomocí `CChar` nelze převést číslo na znak, protože `CChar` nemůže přijmout číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="e7268-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="e7268-219">Následující příklad získá číslo představující bod kódu (kód znaku) a převede ho na odpovídající znak.</span><span class="sxs-lookup"><span data-stu-id="e7268-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="e7268-220">Používá funkci <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> pro získání řetězce číslic, `CInt` pro převod řetězce na typ `Integer` a `ChrW` k převedení čísla na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="e7268-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="e7268-221">Příklad CDate</span><span class="sxs-lookup"><span data-stu-id="e7268-221">CDate Example</span></span>

<span data-ttu-id="e7268-222">V následujícím příkladu je použita funkce `CDate` pro převod řetězců na hodnoty `Date`.</span><span class="sxs-lookup"><span data-stu-id="e7268-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="e7268-223">Obecně se nedoporučuje používat data a časy pevně zakódování jako řetězce (jak je znázorněno v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="e7268-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="e7268-224">Použijte literály data a časová literály, například #Feb 12, 1969 # a #4:45:23 PM #, místo toho.</span><span class="sxs-lookup"><span data-stu-id="e7268-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="e7268-225">Příklad CDbl</span><span class="sxs-lookup"><span data-stu-id="e7268-225">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="e7268-226">Příklad CDec</span><span class="sxs-lookup"><span data-stu-id="e7268-226">CDec Example</span></span>

<span data-ttu-id="e7268-227">Následující příklad používá funkci `CDec` k převodu číselné hodnoty na `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7268-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="e7268-228">Příklad CInt</span><span class="sxs-lookup"><span data-stu-id="e7268-228">CInt Example</span></span>

<span data-ttu-id="e7268-229">Následující příklad používá funkci `CInt` k převedení hodnoty na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e7268-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="e7268-230">Příklad CLng</span><span class="sxs-lookup"><span data-stu-id="e7268-230">CLng Example</span></span>

<span data-ttu-id="e7268-231">V následujícím příkladu je použita funkce `CLng` pro převod hodnot na `Long`.</span><span class="sxs-lookup"><span data-stu-id="e7268-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="e7268-232">Příklad CObj</span><span class="sxs-lookup"><span data-stu-id="e7268-232">CObj Example</span></span>

<span data-ttu-id="e7268-233">Následující příklad používá funkci `CObj` k převodu číselné hodnoty na `Object`.</span><span class="sxs-lookup"><span data-stu-id="e7268-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="e7268-234">Proměnná `Object` sama obsahuje pouze ukazatel se čtyřmi bajty, který odkazuje na `Double` přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e7268-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="e7268-235">Příklad CSByte</span><span class="sxs-lookup"><span data-stu-id="e7268-235">CSByte Example</span></span>

<span data-ttu-id="e7268-236">Následující příklad používá funkci `CSByte` k převodu číselné hodnoty na `SByte`.</span><span class="sxs-lookup"><span data-stu-id="e7268-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="e7268-237">Příklad CShort</span><span class="sxs-lookup"><span data-stu-id="e7268-237">CShort Example</span></span>

<span data-ttu-id="e7268-238">Následující příklad používá funkci `CShort` k převodu číselné hodnoty na `Short`.</span><span class="sxs-lookup"><span data-stu-id="e7268-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="e7268-239">Příklad CSng</span><span class="sxs-lookup"><span data-stu-id="e7268-239">CSng Example</span></span>

<span data-ttu-id="e7268-240">V následujícím příkladu je použita funkce `CSng` pro převod hodnot na `Single`.</span><span class="sxs-lookup"><span data-stu-id="e7268-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="e7268-241">Příklad CStr</span><span class="sxs-lookup"><span data-stu-id="e7268-241">CStr Example</span></span>

<span data-ttu-id="e7268-242">Následující příklad používá funkci `CStr` k převodu číselné hodnoty na `String`.</span><span class="sxs-lookup"><span data-stu-id="e7268-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="e7268-243">Následující příklad používá funkci `CStr` k převodu hodnot `Date` na hodnoty `String`.</span><span class="sxs-lookup"><span data-stu-id="e7268-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="e7268-244">`CStr` vždy vykreslí `Date` hodnotu ve standardním krátkém formátu pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="e7268-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="e7268-245">@No__t_0 však potlačí *neutrální hodnoty* 1/1/0001 pro datum a 00:00:00 pro čas.</span><span class="sxs-lookup"><span data-stu-id="e7268-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="e7268-246">Další informace o hodnotách vrácených funkcí `CStr` naleznete v tématu [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="e7268-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="e7268-247">Příklad CUInt</span><span class="sxs-lookup"><span data-stu-id="e7268-247">CUInt Example</span></span>

<span data-ttu-id="e7268-248">Následující příklad používá funkci `CUInt` k převodu číselné hodnoty na `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="e7268-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="e7268-249">Příklad CULng</span><span class="sxs-lookup"><span data-stu-id="e7268-249">CULng Example</span></span>

<span data-ttu-id="e7268-250">Následující příklad používá funkci `CULng` k převodu číselné hodnoty na `ULong`.</span><span class="sxs-lookup"><span data-stu-id="e7268-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="e7268-251">Příklad CUShort</span><span class="sxs-lookup"><span data-stu-id="e7268-251">CUShort Example</span></span>

<span data-ttu-id="e7268-252">Následující příklad používá funkci `CUShort` k převodu číselné hodnoty na `UShort`.</span><span class="sxs-lookup"><span data-stu-id="e7268-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="e7268-253">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7268-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="e7268-254">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="e7268-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="e7268-255">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7268-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
