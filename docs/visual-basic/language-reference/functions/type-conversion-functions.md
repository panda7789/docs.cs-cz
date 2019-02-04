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
ms.openlocfilehash: be5e1b5fff1feb8ef4cc2ff7fcbca193aafcd781
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674877"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="b8790-102">Funkce pro převod typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8790-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="b8790-103">Tyto funkce jsou zkompilovaný vloženě, což znamená, že kód převodu je součástí kódu, který se vyhodnotí výraz.</span><span class="sxs-lookup"><span data-stu-id="b8790-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b8790-104">Někdy není žádná volání procedury k provedení převodu, což zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="b8790-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="b8790-105">Každá funkce převede výraz na určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="b8790-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8790-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8790-106">Syntax</span></span>  
  
```  
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
  
## <a name="part"></a><span data-ttu-id="b8790-107">Část</span><span class="sxs-lookup"><span data-stu-id="b8790-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="b8790-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b8790-108">Required.</span></span> <span data-ttu-id="b8790-109">Libovolný výraz zdrojového datového typu.</span><span class="sxs-lookup"><span data-stu-id="b8790-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="b8790-110">Vrátí hodnotu datového typu</span><span class="sxs-lookup"><span data-stu-id="b8790-110">Return Value Data Type</span></span>  
 <span data-ttu-id="b8790-111">Název funkce určuje datový typ, který vrátí, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b8790-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b8790-112">Název funkce</span><span class="sxs-lookup"><span data-stu-id="b8790-112">Function name</span></span>|<span data-ttu-id="b8790-113">Návratový typ dat</span><span class="sxs-lookup"><span data-stu-id="b8790-113">Return data type</span></span>|<span data-ttu-id="b8790-114">Rozsah pro `expression` argument</span><span class="sxs-lookup"><span data-stu-id="b8790-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="b8790-115">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="b8790-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="b8790-116">Libovolný platný `Char` nebo `String` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="b8790-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="b8790-117">Datový typ Byte</span><span class="sxs-lookup"><span data-stu-id="b8790-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="b8790-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-119">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon s plovoucí desetinnou čárkou s převodem `CByte` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-120">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="b8790-121">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="b8790-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="b8790-122">Libovolný platný `Char` nebo `String` výrazu; pouze první znak `String` převeden; možné hodnoty jsou 0 až 65535 (unsigned).</span><span class="sxs-lookup"><span data-stu-id="b8790-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="b8790-123">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="b8790-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="b8790-124">Libovolné platné vyjádření data a času.</span><span class="sxs-lookup"><span data-stu-id="b8790-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="b8790-125">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="b8790-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="b8790-126">-1.79769313486231570E + 308 do - 4.94065645841246544E-324 pro záporné hodnoty. 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="b8790-127">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="b8790-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="b8790-128">+/-79,228,162,514,264,337,593,543,950,335 škálovaných nula čísel, tedy čísla bez desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="b8790-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="b8790-129">Pro 28 desetinná čísla jsou v rozsahu +/-7,9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="b8790-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="b8790-130">Nejmenší možný počet nenulové je 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="b8790-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="b8790-131">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="b8790-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="b8790-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) prostřednictvím <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="b8790-133">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod celého čísla s plovoucí desetinnou čárkou `CInt` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-134">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="b8790-135">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="b8790-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="b8790-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) prostřednictvím <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-137">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod 64bitové celé číslo s plovoucí desetinnou čárkou `CLng` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-138">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="b8790-139">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="b8790-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="b8790-140">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b8790-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="b8790-141">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="b8790-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="b8790-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) prostřednictvím <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-143">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod na bajty se znaménkem s plovoucí desetinnou čárkou `CSByte` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-144">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="b8790-145">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="b8790-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="b8790-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) prostřednictvím <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-147">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod 16bitové celé číslo s plovoucí desetinnou čárkou `CShort` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-148">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="b8790-149">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="b8790-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="b8790-150">-3.402823E + 38-1, 401298E-45 pro záporné hodnoty. 1, 401298E-45 prostřednictvím 3.402823E + 38 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="b8790-151">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="b8790-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="b8790-152">Vrátí `CStr` záviset `expression` argument.</span><span class="sxs-lookup"><span data-stu-id="b8790-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="b8790-153">Zobrazit [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="b8790-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="b8790-154">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="b8790-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="b8790-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-156">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod na celé číslo bez znaménka s plovoucí desetinnou čárkou `CUInt` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-157">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="b8790-158">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="b8790-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="b8790-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-160">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod dlouhé celé číslo bez znaménka s plovoucí desetinnou čárkou `CULng` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-161">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="b8790-162">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="b8790-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="b8790-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="b8790-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="b8790-164">Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod bez znaménka 16bitové celé číslo s plovoucí desetinnou čárkou `CUShort` funkce, najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8790-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="b8790-165">Zobrazit [CInt příklad](#cint-example) oddílu příklad.</span><span class="sxs-lookup"><span data-stu-id="b8790-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="b8790-166"><sup>1</sup> zlomkové části můžou podléhat zvláštní druh zaokrouhlování volané *je bankovní zaokrouhlení*.</span><span class="sxs-lookup"><span data-stu-id="b8790-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="b8790-167">Další informace viz "Poznámky".</span><span class="sxs-lookup"><span data-stu-id="b8790-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8790-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8790-168">Remarks</span></span>  
 <span data-ttu-id="b8790-169">Jako pravidlo, používejte funkce pro převod typů jazyka Visual Basic preferenci metod rozhraní .NET Framework, jako `ToString()`– buď na <xref:System.Convert> třídy nebo na individuální typu struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="b8790-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="b8790-170">Funkce jazyka Visual Basic jsou navrženy pro zajištění optimálního interakce s kódem jazyka Visual Basic a také využívají zdrojový kód kratší a snadněji čitelné.</span><span class="sxs-lookup"><span data-stu-id="b8790-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="b8790-171">Kromě toho převod metod rozhraní .NET Framework vždy nevytváří stejné výsledky jako funkce jazyka Visual Basic, například při převodu `Boolean` k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b8790-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="b8790-172">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b8790-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  


<span data-ttu-id="b8790-173">Počínaje 15.8 jazyka Visual Basic, jehož výkon byl optimalizován převodu plovoucí-desetinnou-na-celé číslo se při předávání <xref:System.Single> nebo <xref:System.Double> hodnota vrácená pomocí následujících metod do jednoho z funkce pro převod celé číslo (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="b8790-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="b8790-174">Tyto optimalizace umožňuje kód, který provádí převody celé číslo, aby běžela dvakrát tak rychle hodně.</span><span class="sxs-lookup"><span data-stu-id="b8790-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="b8790-175">Následující příklad znázorňuje tyto optimalizované převody plovoucí-desetinnou-na-celé číslo:</span><span class="sxs-lookup"><span data-stu-id="b8790-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="b8790-176">Chování</span><span class="sxs-lookup"><span data-stu-id="b8790-176">Behavior</span></span>  
  
-   <span data-ttu-id="b8790-177">**Vynucení.**</span><span class="sxs-lookup"><span data-stu-id="b8790-177">**Coercion.**</span></span> <span data-ttu-id="b8790-178">Obecně platí můžete použít funkce pro převod typů dat k vynucení výsledků na konkrétní datový typ spíše než výchozí datový typ operace.</span><span class="sxs-lookup"><span data-stu-id="b8790-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="b8790-179">Například použít `CDec` přinutit desítkové aritmetické operace v případech, kdy jednoduchou přesností, dvojitá přesnost nebo celé číslo aritmetické by vám normálně trvalo místo.</span><span class="sxs-lookup"><span data-stu-id="b8790-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="b8790-180">**Neúspěšné převody.**</span><span class="sxs-lookup"><span data-stu-id="b8790-180">**Failed Conversions.**</span></span> <span data-ttu-id="b8790-181">Pokud `expression` předaný funkci je mimo rozsah datového typu, na který se má převést <xref:System.OverflowException> vyvolá.</span><span class="sxs-lookup"><span data-stu-id="b8790-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="b8790-182">**Zlomkové části.**</span><span class="sxs-lookup"><span data-stu-id="b8790-182">**Fractional Parts.**</span></span> <span data-ttu-id="b8790-183">Při převodu nonintegral hodnotu na integrální typ, funkce pro převod celé číslo (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, a `CUShort`) odeberte desetinná část a Zaokrouhlí hodnotu na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b8790-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="b8790-184">Pokud zlomkové části je přesně 0,5, funkce pro převod celé číslo zaokrouhlit na nejbližší sudé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b8790-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="b8790-185">Například 0,5 zaokrouhlí na 0 a 1.5 a 2.5, které obě zaokrouhlit na 2.</span><span class="sxs-lookup"><span data-stu-id="b8790-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="b8790-186">To se někdy označuje jako *je bankovní zaokrouhlení*, a jejím účelem je jako kompenzaci za posun, která se můžou hromadit při přidávání mnoha těchto čísla společně.</span><span class="sxs-lookup"><span data-stu-id="b8790-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="b8790-187">`CInt` a `CLng` se liší od <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkce, které zkrátit, nikoli zaokrouhlit desetinnou část čísla.</span><span class="sxs-lookup"><span data-stu-id="b8790-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="b8790-188">Navíc `Fix` a `Int` vždy vrátí hodnotu stejného datového typu jako předáním.</span><span class="sxs-lookup"><span data-stu-id="b8790-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="b8790-189">**Datum a čas převody.**</span><span class="sxs-lookup"><span data-stu-id="b8790-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="b8790-190">Použití <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkce k určení, pokud hodnotu lze převést na datum a čas.</span><span class="sxs-lookup"><span data-stu-id="b8790-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="b8790-191">`CDate` rozpozná literály data a času literály, ale není číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="b8790-192">K převodu jazyka Visual Basic 6.0 `Date` hodnota, která se `Date` hodnoty v jazyce Visual Basic 2005 nebo novější verze, můžete použít <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b8790-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="b8790-193">**Neutrální hodnoty data a času.**</span><span class="sxs-lookup"><span data-stu-id="b8790-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="b8790-194">[Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="b8790-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="b8790-195">Pro účely převodů, Visual Basic považuje za 1/1/0001 (od 1. ledna roku 1) *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) bude neutrální hodnota pro dobu.</span><span class="sxs-lookup"><span data-stu-id="b8790-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="b8790-196">Při převodu `Date` hodnotu na řetězec, `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="b8790-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="b8790-197">Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00: 00"; informace o datu je potlačeno.</span><span class="sxs-lookup"><span data-stu-id="b8790-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="b8790-198">Informace o datu je však stále k dispozici v původní `Date` hodnotu a je možné obnovit pomocí funkcí, jako <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkce.</span><span class="sxs-lookup"><span data-stu-id="b8790-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="b8790-199">**Citlivost jazykovou verzi.**</span><span class="sxs-lookup"><span data-stu-id="b8790-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="b8790-200">Funkce pro převod typů zahrnující řetězce provádět převody na základě nastavení aktuální jazykové verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b8790-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="b8790-201">Například `CDate` rozpozná formáty kalendářního data podle nastavení národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="b8790-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="b8790-202">Je nutné zadat den, měsíc a rok ve správném pořadí pro vaše národní prostředí nebo datum nemusí být správně interpretovat.</span><span class="sxs-lookup"><span data-stu-id="b8790-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="b8790-203">Pokud obsahuje řetězec den v týdnu, jako je například "Středa" nebyl rozpoznán formát dlouhého data.</span><span class="sxs-lookup"><span data-stu-id="b8790-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="b8790-204">Pokud je potřeba převést na nebo z řetězcové reprezentace hodnoty ve formátu kromě vlákna zadaného parametrem národní prostředí, nelze používat funkce pro převod typů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b8790-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="b8790-205">Chcete-li to provést, použijte `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` metody typu tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8790-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="b8790-206">Například použít <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu na řetězec `Double`a použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.</span><span class="sxs-lookup"><span data-stu-id="b8790-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="b8790-207">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="b8790-207">CType Function</span></span>  
 <span data-ttu-id="b8790-208">[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) přijímá jako druhý argument `typename`a převede `expression` k `typename`, kde `typename` může být datového typu, struktury, třídy nebo rozhraní, ke které existuje platný převod.</span><span class="sxs-lookup"><span data-stu-id="b8790-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="b8790-209">Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b8790-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="b8790-210">CBool – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-210">CBool Example</span></span>  
 <span data-ttu-id="b8790-211">V následujícím příkladu `CBool` funkce převedete výrazy `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="b8790-212">Pokud je výraz vyhodnocen na nenulovou hodnotu, `CBool` vrátí `True`; v opačném případě vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="b8790-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="b8790-213">CByte – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-213">CByte Example</span></span>  
 <span data-ttu-id="b8790-214">V následujícím příkladu `CByte` funkce převodu výrazu `Byte`.</span><span class="sxs-lookup"><span data-stu-id="b8790-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="b8790-215">CChar – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-215">CChar Example</span></span>  
 <span data-ttu-id="b8790-216">V následujícím příkladu `CChar` funkce pro převod první znak `String` výraz, který se `Char` typu.</span><span class="sxs-lookup"><span data-stu-id="b8790-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="b8790-217">Vstupní argument `CChar` musí být datového typu `Char` nebo `String`.</span><span class="sxs-lookup"><span data-stu-id="b8790-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="b8790-218">Nemůžete použít `CChar` pro převod čísla na znak, protože `CChar` nemůže přijmout číselným datovým typem.</span><span class="sxs-lookup"><span data-stu-id="b8790-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="b8790-219">Následující příklad získá číslo představující bod kódu. (kód znaku) a převede ho na odpovídající znak.</span><span class="sxs-lookup"><span data-stu-id="b8790-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="b8790-220">Používá <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkce získat řetězec číslic, `CInt` pro převod řetězce na typ `Integer`, a `ChrW` převést číslo na typ `Char`.</span><span class="sxs-lookup"><span data-stu-id="b8790-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="b8790-221">CDate – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-221">CDate Example</span></span>  
 <span data-ttu-id="b8790-222">V následujícím příkladu `CDate` funkce pro převod řetězců na `Date` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="b8790-223">Obecně není doporučeno pevně kódováno pomocí data a času jako řetězce (jak je znázorněno v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="b8790-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="b8790-224">Použijte literály data a času literály, například #Feb 12, 1969 # a # 4:45:23 hodin #, místo toho.</span><span class="sxs-lookup"><span data-stu-id="b8790-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="b8790-225">CDbl – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="b8790-226">CDec – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-226">CDec Example</span></span>  
 <span data-ttu-id="b8790-227">V následujícím příkladu `CDec` funkce pro převod číselná hodnota, která `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b8790-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="b8790-228">Příklad CInt</span><span class="sxs-lookup"><span data-stu-id="b8790-228">CInt Example</span></span>  
 <span data-ttu-id="b8790-229">V následujícím příkladu `CInt` funkce, která se převést hodnotu na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b8790-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  

## <a name="clng-example"></a><span data-ttu-id="b8790-230">CLng – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-230">CLng Example</span></span>
 <span data-ttu-id="b8790-231">V následujícím příkladu `CLng` funkce pro převod hodnot `Long`.</span><span class="sxs-lookup"><span data-stu-id="b8790-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="b8790-232">Příklad CObj</span><span class="sxs-lookup"><span data-stu-id="b8790-232">CObj Example</span></span>  
 <span data-ttu-id="b8790-233">V následujícím příkladu `CObj` funkce pro převod číselná hodnota, která `Object`.</span><span class="sxs-lookup"><span data-stu-id="b8790-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="b8790-234">`Object` Sám obsahují jenom ukazatel čtyř bajtů, která odkazuje na `Double` přiřazena hodnota.</span><span class="sxs-lookup"><span data-stu-id="b8790-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="b8790-235">Csbyte – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-235">CSByte Example</span></span>  
 <span data-ttu-id="b8790-236">V následujícím příkladu `CSByte` funkce pro převod číselná hodnota, která `SByte`.</span><span class="sxs-lookup"><span data-stu-id="b8790-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="b8790-237">Příklad CShort</span><span class="sxs-lookup"><span data-stu-id="b8790-237">CShort Example</span></span>  
 <span data-ttu-id="b8790-238">V následujícím příkladu `CShort` funkce pro převod číselná hodnota, která `Short`.</span><span class="sxs-lookup"><span data-stu-id="b8790-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="b8790-239">CSng – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-239">CSng Example</span></span>  
 <span data-ttu-id="b8790-240">V následujícím příkladu `CSng` funkce pro převod hodnot `Single`.</span><span class="sxs-lookup"><span data-stu-id="b8790-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="b8790-241">Příklad CStr</span><span class="sxs-lookup"><span data-stu-id="b8790-241">CStr Example</span></span>  
 <span data-ttu-id="b8790-242">V následujícím příkladu `CStr` funkce pro převod číselná hodnota, která `String`.</span><span class="sxs-lookup"><span data-stu-id="b8790-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="b8790-243">V následujícím příkladu `CStr` funkce pro převod `Date` hodnoty `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8790-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="b8790-244">`CStr` vždy vykreslí `Date` hodnotu ve standardní krátkého formátu pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="b8790-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="b8790-245">Ale `CStr` potlačí *neutrální hodnoty* z 1/1/0001 pro datum a 00:00:00 po dobu.</span><span class="sxs-lookup"><span data-stu-id="b8790-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="b8790-246">Další podrobnosti o hodnot vrácených `CStr`, naleznete v tématu [vrátit hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="b8790-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="b8790-247">Cuint – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-247">CUInt Example</span></span>  
 <span data-ttu-id="b8790-248">V následujícím příkladu `CUInt` funkce pro převod číselná hodnota, která `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="b8790-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="b8790-249">Culng – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-249">CULng Example</span></span>  
 <span data-ttu-id="b8790-250">V následujícím příkladu `CULng` funkce pro převod číselná hodnota, která `ULong`.</span><span class="sxs-lookup"><span data-stu-id="b8790-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="b8790-251">Cushort – příklad</span><span class="sxs-lookup"><span data-stu-id="b8790-251">CUShort Example</span></span>  
 <span data-ttu-id="b8790-252">V následujícím příkladu `CUShort` funkce pro převod číselná hodnota, která `UShort`.</span><span class="sxs-lookup"><span data-stu-id="b8790-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b8790-253">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8790-253">See also</span></span>
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
- [<span data-ttu-id="b8790-254">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="b8790-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="b8790-255">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8790-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
