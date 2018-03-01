---
title: "Decimal – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="2160b-102">Decimal – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2160b-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="2160b-103">Blokování podepsané 128-bit (16 bajtů) hodnoty představující 96 bitů (12 bajtů) celá čísla škálovat podle proměnné power 10.</span><span class="sxs-lookup"><span data-stu-id="2160b-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="2160b-104">Měřítko určuje počet číslic vpravo od desetinné čárky. ho rozsahu od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="2160b-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="2160b-105">S měřítkem 0 (bez desetinných míst), je největší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="2160b-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="2160b-106">S 28 desetinnými místy největší hodnota je +/-7,9228162514264337593543950335 a je nejmenší nenulovou hodnotu +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="2160b-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2160b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2160b-107">Remarks</span></span>  
 <span data-ttu-id="2160b-108">`Decimal` Datový typ pro číslo poskytuje největší počet platných číslic.</span><span class="sxs-lookup"><span data-stu-id="2160b-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="2160b-109">Podporuje až 29 platných číslic a může představovat hodnoty překračující 7.9228 × 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="2160b-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="2160b-110">Je obzvláště vhodný pro výpočty, jako například finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="2160b-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="2160b-111">Výchozí hodnota `Decimal` je 0.</span><span class="sxs-lookup"><span data-stu-id="2160b-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="2160b-112">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="2160b-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="2160b-113">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="2160b-113">**Precision.**</span></span> <span data-ttu-id="2160b-114">`Decimal`není typu data s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="2160b-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="2160b-115">`Decimal` Struktura obsahuje binární celočíselná hodnota, spolu s přihlašovací bit a celé škálování faktor, který určuje, jaká část hodnoty je zlomek decimal.</span><span class="sxs-lookup"><span data-stu-id="2160b-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="2160b-116">Z toho důvodu `Decimal` čísla mají přesnější reprezentaci v paměti, než je typy s plovoucí desetinnou čárkou (`Single` a `Double`).</span><span class="sxs-lookup"><span data-stu-id="2160b-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="2160b-117">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="2160b-117">**Performance.**</span></span> <span data-ttu-id="2160b-118">`Decimal` Datový typ je nejpomalejší pro všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="2160b-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="2160b-119">Měli byste zvážit význam přesnost proti výkonu před volbou datovým typem.</span><span class="sxs-lookup"><span data-stu-id="2160b-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="2160b-120">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="2160b-120">**Widening.**</span></span> <span data-ttu-id="2160b-121">`Decimal` Datový typ rozšiřuje na `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="2160b-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="2160b-122">To znamená, že můžete převést `Decimal` na jednu z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="2160b-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="2160b-123">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="2160b-123">**Trailing Zeros.**</span></span> <span data-ttu-id="2160b-124">Visual Basic neukládá koncové nuly v `Decimal` literálu.</span><span class="sxs-lookup"><span data-stu-id="2160b-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="2160b-125">Ale `Decimal` proměnné se zachovají všechny koncové nuly výpočetně získali.</span><span class="sxs-lookup"><span data-stu-id="2160b-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="2160b-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2160b-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="2160b-127">Výstup `MsgBox` v předchozím příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="2160b-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="2160b-128">D1 = 2.375 d2 = 1.625, d3 = 4.000 d4 = 4</span><span class="sxs-lookup"><span data-stu-id="2160b-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="2160b-129">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="2160b-129">**Type Characters.**</span></span> <span data-ttu-id="2160b-130">Připojování znak typu literálu `D` k literál vynutí, aby `Decimal` datového typu.</span><span class="sxs-lookup"><span data-stu-id="2160b-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="2160b-131">Připojování znak typu identifikátoru `@` na všechny identifikátor vynutí jeho `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2160b-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="2160b-132">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="2160b-132">**Framework Type.**</span></span> <span data-ttu-id="2160b-133">Typ odpovídající v rozhraní .NET Framework je <xref:System.Decimal?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="2160b-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="2160b-134">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2160b-134">Range</span></span>  
 <span data-ttu-id="2160b-135">Možná budete muset použít `D` znak přiřadit hodnotu velký na typu `Decimal` proměnné nebo konstantní.</span><span class="sxs-lookup"><span data-stu-id="2160b-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="2160b-136">Tento požadavek je vzhledem k tomu, že kompilátor interpretuje jako literál `Long` Pokud znak typu literálu následuje literál, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2160b-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="2160b-137">Deklarace pro `bigDec1` neobsahuje přetečení, protože hodnota, která je k němu přiřazen spadá do rozsahu pro `Long`.</span><span class="sxs-lookup"><span data-stu-id="2160b-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="2160b-138">`Long` Lze přiřadit hodnotu `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2160b-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="2160b-139">Deklarace pro `bigDec2` vygeneruje chybu přetečení, protože je příliš velká pro hodnotu, která je k němu přiřazen `Long`.</span><span class="sxs-lookup"><span data-stu-id="2160b-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="2160b-140">Protože číselný literál nelze první vyhodnocen jako `Long`, nemůže být přiřazen `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2160b-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="2160b-141">Pro `bigDec3`, znak typu literálu `D` řeší problém vynucením kompilátoru interpretovat literál jako `Decimal` místo jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="2160b-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2160b-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="2160b-142">See Also</span></span>  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2160b-143">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2160b-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2160b-144">Single – datový typ</span><span class="sxs-lookup"><span data-stu-id="2160b-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="2160b-145">Double – datový typ</span><span class="sxs-lookup"><span data-stu-id="2160b-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="2160b-146">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="2160b-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2160b-147">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="2160b-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2160b-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="2160b-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
