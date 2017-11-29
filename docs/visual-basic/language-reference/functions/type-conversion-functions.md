---
title: "Funkce pro převod typů (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 117cd4ce038a533715bbc86558545f0f223dd149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="9bfcf-102">Funkce pro převod typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bfcf-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="9bfcf-103">Tyto funkce jsou kompilované vložené, což znamená, že kód převod je součástí kód, který se vyhodnotí výraz.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="9bfcf-104">Někdy je žádná volání procedury k provádění převodu, což zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="9bfcf-105">Jednotlivé funkce převede výraz na určitého datového typu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfcf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bfcf-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="9bfcf-107">Část</span><span class="sxs-lookup"><span data-stu-id="9bfcf-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="9bfcf-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-108">Required.</span></span> <span data-ttu-id="9bfcf-109">Jakýkoli výraz zdrojového datového typu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="9bfcf-110">Vrátí hodnotu datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-110">Return Value Data Type</span></span>  
 <span data-ttu-id="9bfcf-111">Název funkce určuje datový typ hodnoty, které se vrátí, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="9bfcf-112">Název funkce</span><span class="sxs-lookup"><span data-stu-id="9bfcf-112">Function name</span></span>|<span data-ttu-id="9bfcf-113">Návratový datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-113">Return data type</span></span>|<span data-ttu-id="9bfcf-114">Rozsah pro `expression` argument</span><span class="sxs-lookup"><span data-stu-id="9bfcf-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="9bfcf-115">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="9bfcf-116">Libovolný platný `Char` nebo `String` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="9bfcf-117">Byte – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="9bfcf-118">0 do 255 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="9bfcf-119">Char – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="9bfcf-120">Libovolný platný `Char` nebo `String` výraz; pouze první znak `String` je převést; hodnota může být 0 až 65535 (bez znaménka).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="9bfcf-121">Date – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="9bfcf-122">Platný reprezentace data a času.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="9bfcf-123">Double – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="9bfcf-124">-1.79769313486231570E + 308 prostřednictvím - 4.94065645841246544E-324 pro záporné hodnoty; 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="9bfcf-125">Decimal – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="9bfcf-126">+/-79,228,162,514,264,337,593,543,950,335 pro škálovat nula čísla, který je čísla bez desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="9bfcf-127">Pro 28 desetinná čísla je rozsah +/-7,9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="9bfcf-128">Nejmenší možný počet nenulové je 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="9bfcf-129">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="9bfcf-130">-2,147,483,648 prostřednictvím 2 147 483 647; jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="9bfcf-131">Long – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="9bfcf-132">-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807; jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="9bfcf-133">Object – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="9bfcf-134">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="9bfcf-135">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="9bfcf-136">-128 až 127; jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="9bfcf-137">Short – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="9bfcf-138">-32 768 do 32 767; jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="9bfcf-139">Single – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="9bfcf-140">-3.402823E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty; 1, 401298E-45 prostřednictvím 3.402823E + 38 kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="9bfcf-141">String – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="9bfcf-142">Vrátí pro `CStr` závisí na `expression` argument.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="9bfcf-143">V tématu [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="9bfcf-144">Uinteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="9bfcf-145">0 až 4 294 967 295 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="9bfcf-146">Ulong – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="9bfcf-147">0 až 18,446,744,073,709,551,615 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="9bfcf-148">Ushort – datový typ</span><span class="sxs-lookup"><span data-stu-id="9bfcf-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="9bfcf-149">0 až 65 535 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9bfcf-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="9bfcf-150"><sup>1</sup> zlomkové části mohou podléhat zvláštním typem zaokrouhlení volané *banker je zaokrouhlení*.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="9bfcf-151">Další informace najdete v části "Poznámky".</span><span class="sxs-lookup"><span data-stu-id="9bfcf-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bfcf-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bfcf-152">Remarks</span></span>  
 <span data-ttu-id="9bfcf-153">Platí, měli byste použít funkce pro převod typů jazyka Visual Basic přednostně metod rozhraní .NET Framework, jako `ToString()`, buď na <xref:System.Convert> třídy nebo na strukturou jednotlivých typů nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="9bfcf-154">Funkce jazyka Visual Basic jsou navrženy pro optimální interakci s kód jazyka Visual Basic a také provádění zdrojového kódu kratší a snadněji číst.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="9bfcf-155">Kromě toho převod metod rozhraní .NET Framework vždy nevedou stejné výsledky jako funkce jazyka Visual Basic, například při převádění `Boolean` k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="9bfcf-156">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9bfcf-157">Chování</span><span class="sxs-lookup"><span data-stu-id="9bfcf-157">Behavior</span></span>  
  
-   <span data-ttu-id="9bfcf-158">**Převod.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-158">**Coercion.**</span></span> <span data-ttu-id="9bfcf-159">Obecně platí můžete funkce pro převod typů dat coerce výsledek operace datový typ. spíše než výchozí typ data.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="9bfcf-160">Například použít `CDec` vynutit decimal aritmetické v případech, kde jednoduchou přesností, dvojitá přesnost nebo celé číslo aritmetické by za normálních okolností probíhat.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="9bfcf-161">**Převody se nezdařilo.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-161">**Failed Conversions.**</span></span> <span data-ttu-id="9bfcf-162">Pokud `expression` předaný funkci je mimo rozsah datového typu, na která se má být převeden, <xref:System.OverflowException> dojde.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="9bfcf-163">**Zlomkové části.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-163">**Fractional Parts.**</span></span> <span data-ttu-id="9bfcf-164">Při převodu nonintegral hodnotu na integrální typ, funkce pro převod celé číslo (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, a `CUShort`) odebrat zlomkové součástí a zaokrouhlit hodnotu na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="9bfcf-165">Pokud zlomkové části přesně 0,5, funkce pro převod celé číslo zaokrouhlit, aby nejbližší sudé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="9bfcf-166">Například 0,5 zaokrouhlí na 0 a 1.5 a 2.5, které obě zaokrouhlit na 2.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="9bfcf-167">To se někdy nazývá *banker je zaokrouhlení*, a jejím účelem je kompenzovat odchylka, které můžou hromadit při přidávání mnoho taková čísla společně.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="9bfcf-168">`CInt`a `CLng` se liší od <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkce, které zkrátit, nikoli zaokrouhlit zlomkové části čísla.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="9bfcf-169">Navíc `Fix` a `Int` vždy vrátí hodnotu stejný datový typ. jako předáte v.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="9bfcf-170">**Datum a čas převody.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="9bfcf-171">Použití <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkce k určení, pokud hodnotu lze převést datum a čas.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="9bfcf-172">`CDate`rozpozná literály data a času literály, ale není číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="9bfcf-173">Převést Visual Basic 6.0 `Date` hodnotu `Date` hodnotu v jazyce Visual Basic 2005 nebo novější verze, můžete použít <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="9bfcf-174">**Neutrální hodnoty data a času.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="9bfcf-175">[Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="9bfcf-176">Pro účely převod typů, Visual Basic považuje za 1/1/0001 (1. ledna roku 1) *neutrální hodnota* pro datum a 00:00:00 (půlnoc) se má nastavit neutrální hodnota pro dobu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="9bfcf-177">Pokud převedete `Date` hodnotu na řetězec `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="9bfcf-178">Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00: 00"; potlačeno informace o datu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="9bfcf-179">Informace o datu je však stále nachází na původní `Date` hodnotu a je možné obnovit s funkcemi, jako například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkce.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="9bfcf-180">**Jazyková verze velkých a malých písmen.**</span><span class="sxs-lookup"><span data-stu-id="9bfcf-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="9bfcf-181">Funkce pro převod typů zahrnující řetězce provést převody na základě aktuální nastavení jazykové verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="9bfcf-182">Například `CDate` rozpoznává formáty data podle nastavení národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="9bfcf-183">Je nutné zadat den, měsíc a rok ve správném pořadí pro národní prostředí nebo datum nemusí být správně interpretovat.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="9bfcf-184">Pokud obsahuje řetězec den v týdnu, jako je například "Středa" nebyl rozpoznán formát dlouhého data.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="9bfcf-185">Pokud musíte převést do nebo z řetězcovou reprezentaci hodnoty ve formátu, než jaké byla určená elementem národní prostředí, nebudete moct používat funkce pro převod typů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="9bfcf-186">Chcete-li to provést, použijte `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` metody typu tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="9bfcf-187">Například použít <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu řetězce `Double`a použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="9bfcf-188">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="9bfcf-188">CType Function</span></span>  
 <span data-ttu-id="9bfcf-189">[CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md) použije druhý argument, `typename`a převede `expression` k `typename`, kde `typename` můžou být datový typ, struktura, třída nebo rozhraní, na kterou existuje platná převod.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="9bfcf-190">Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="9bfcf-191">CBool – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-191">CBool Example</span></span>  
 <span data-ttu-id="9bfcf-192">Následující příklad používá `CBool` funkce pro převod výrazy a `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="9bfcf-193">Pokud je výsledkem výrazu nenulovou hodnotu, `CBool` vrátí `True`, jinak vrátí hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="9bfcf-194">CByte – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-194">CByte Example</span></span>  
 <span data-ttu-id="9bfcf-195">Následující příklad používá `CByte` funkce pro převod výraz, který se `Byte`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="9bfcf-196">CChar – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-196">CChar Example</span></span>  
 <span data-ttu-id="9bfcf-197">Následující příklad používá `CChar` funkce pro převod první znak `String` výraz, který se `Char` typu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="9bfcf-198">Vstupní argument `CChar` musí být datového typu `Char` nebo `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="9bfcf-199">Nemůžete použít `CChar` k převodu číslo znak, protože `CChar` nemůže přijímat číselným datovým typem.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="9bfcf-200">Následující příklad získá číslo představující bod kódu (kód znaku) a převede jej na odpovídající znak.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="9bfcf-201">Použije <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkce získat řetězec číslic, `CInt` se převést řetězec na typ `Integer`, a `ChrW` převést na typ číslo `Char`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="9bfcf-202">CDate – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-202">CDate Example</span></span>  
 <span data-ttu-id="9bfcf-203">Následující příklad používá `CDate` funkce pro převod řetězců na `Date` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="9bfcf-204">Obecně se nedoporučuje pevně kódováno data a časy jako řetězce (jak je uvedeno v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="9bfcf-205">Použijte literály datum a čas literály, jako je například #Feb 12, &#1969; a # 4:45:23 PM #, místo toho.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="9bfcf-206">CDbl – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="9bfcf-207">CDec – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-207">CDec Example</span></span>  
 <span data-ttu-id="9bfcf-208">Následující příklad používá `CDec` funkce pro převod číselná hodnota, která `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="9bfcf-209">CInt – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-209">CInt Example</span></span>  
 <span data-ttu-id="9bfcf-210">Následující příklad používá `CInt` funkce, která se převést hodnotu na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="9bfcf-211">CLng – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-211">CLng Example</span></span>  
 <span data-ttu-id="9bfcf-212">Následující příklad používá `CLng` funkce pro převod hodnoty na `Long`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="9bfcf-213">Příklad CObj</span><span class="sxs-lookup"><span data-stu-id="9bfcf-213">CObj Example</span></span>  
 <span data-ttu-id="9bfcf-214">Následující příklad používá `CObj` funkce pro převod číselná hodnota, která `Object`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="9bfcf-215">`Object` Proměnnou obsahují jenom ukazatel čtyř bajtů, který odkazuje na `Double` hodnotu přiřazenou k němu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="9bfcf-216">Csbyte – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-216">CSByte Example</span></span>  
 <span data-ttu-id="9bfcf-217">Následující příklad používá `CSByte` funkce pro převod číselná hodnota, která `SByte`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="9bfcf-218">Příklad CShort</span><span class="sxs-lookup"><span data-stu-id="9bfcf-218">CShort Example</span></span>  
 <span data-ttu-id="9bfcf-219">Následující příklad používá `CShort` funkce pro převod číselná hodnota, která `Short`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="9bfcf-220">CSng – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-220">CSng Example</span></span>  
 <span data-ttu-id="9bfcf-221">Následující příklad používá `CSng` funkce pro převod hodnoty na `Single`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="9bfcf-222">Příklad CStr</span><span class="sxs-lookup"><span data-stu-id="9bfcf-222">CStr Example</span></span>  
 <span data-ttu-id="9bfcf-223">Následující příklad používá `CStr` funkce pro převod číselná hodnota, která `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="9bfcf-224">Následující příklad používá `CStr` funkce pro převod `Date` hodnoty k `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="9bfcf-225">`CStr`vždy vykreslí `Date` hodnotu ve formátu standard krátké pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="9bfcf-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="9bfcf-226">Ale `CStr` potlačí *neutrální hodnoty* z 1/1/0001 pro datum a 00:00:00 po dobu.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="9bfcf-227">Další podrobnosti o hodnot vrácených `CStr`, najdete v části [vrátit hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="9bfcf-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="9bfcf-228">Cuint – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-228">CUInt Example</span></span>  
 <span data-ttu-id="9bfcf-229">Následující příklad používá `CUInt` funkce pro převod číselná hodnota, která `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="9bfcf-230">Culng – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-230">CULng Example</span></span>  
 <span data-ttu-id="9bfcf-231">Následující příklad používá `CULng` funkce pro převod číselná hodnota, která `ULong`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="9bfcf-232">Cushort – příklad</span><span class="sxs-lookup"><span data-stu-id="9bfcf-232">CUShort Example</span></span>  
 <span data-ttu-id="9bfcf-233">Následující příklad používá `CUShort` funkce pro převod číselná hodnota, která `UShort`.</span><span class="sxs-lookup"><span data-stu-id="9bfcf-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9bfcf-234">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bfcf-234">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="9bfcf-235">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="9bfcf-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="9bfcf-236">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bfcf-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
