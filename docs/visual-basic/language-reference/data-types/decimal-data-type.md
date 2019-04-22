---
title: Decimal – datový typ (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834098"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="8b92b-102">Decimal – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b92b-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="8b92b-103">Blokování podepsané 128-bit (16 bajtů) hodnoty představující celé číslo (12 bajtů) verze 96 čísla měřítkem řídit proměnné násobky 10.</span><span class="sxs-lookup"><span data-stu-id="8b92b-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="8b92b-104">Koeficient změny měřítka určuje počet číslic vpravo od desetinné čárky rozsah od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="8b92b-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="8b92b-105">S měřítkem 0 (bez desetinných míst), je možná největší hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="8b92b-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="8b92b-106">28 desetinných míst největší hodnota, je +/-7,9228162514264337593543950335 a +/-0,0000000000000000000000000001 (+/-1E-28) je nejmenší nenulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8b92b-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b92b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b92b-107">Remarks</span></span>  
 <span data-ttu-id="8b92b-108">`Decimal` Datový typ poskytuje největší počet platných číslic pro číslo.</span><span class="sxs-lookup"><span data-stu-id="8b92b-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="8b92b-109">Podporuje až 29 významných číslic a může představovat hodnoty překračující 7.9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="8b92b-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="8b92b-110">Je obzvláště vhodný pro výpočty, například finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="8b92b-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="8b92b-111">Výchozí hodnota `Decimal` je 0.</span><span class="sxs-lookup"><span data-stu-id="8b92b-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="8b92b-112">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="8b92b-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="8b92b-113">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-113">**Precision.**</span></span> <span data-ttu-id="8b92b-114">`Decimal` není typ s plovoucí desetinnou čárkou data.</span><span class="sxs-lookup"><span data-stu-id="8b92b-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="8b92b-115">`Decimal` Struktura obsahuje binární celočíselnou hodnotu, společně s bit znaménka a měřítko, která určuje, jaká část hodnoty je desetinný zlomek celého čísla.</span><span class="sxs-lookup"><span data-stu-id="8b92b-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="8b92b-116">Z tohoto důvodu `Decimal` čísla mají přesnější reprezentací v paměti než u typů s plovoucí desetinnou čárkou (`Single` a `Double`).</span><span class="sxs-lookup"><span data-stu-id="8b92b-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="8b92b-117">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-117">**Performance.**</span></span> <span data-ttu-id="8b92b-118">`Decimal` Datový typ se načítají nejpomaleji. všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="8b92b-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="8b92b-119">Měli byste zvážit důležitost přesnost proti výkonu před výběrem datového typu.</span><span class="sxs-lookup"><span data-stu-id="8b92b-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="8b92b-120">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-120">**Widening.**</span></span> <span data-ttu-id="8b92b-121">`Decimal` Datový typ rozšiřuje na `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="8b92b-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="8b92b-122">To znamená, že můžete převést `Decimal` některou z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="8b92b-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="8b92b-123">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-123">**Trailing Zeros.**</span></span> <span data-ttu-id="8b92b-124">Koncové nuly v jazyce Visual Basic nejsou uložené `Decimal` literálu.</span><span class="sxs-lookup"><span data-stu-id="8b92b-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="8b92b-125">Ale `Decimal` proměnná zachová všechny koncové nuly výpočetně získali.</span><span class="sxs-lookup"><span data-stu-id="8b92b-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="8b92b-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8b92b-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="8b92b-127">Výstup `MsgBox` v předchozím příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8b92b-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="8b92b-128">D1 = 2.375 d2 = 1.625 d3 = 4.000 d4 = 4</span><span class="sxs-lookup"><span data-stu-id="8b92b-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="8b92b-129">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-129">**Type Characters.**</span></span> <span data-ttu-id="8b92b-130">Přidávání znak typu literálu `D` k literálu se z něj stane `Decimal` datového typu.</span><span class="sxs-lookup"><span data-stu-id="8b92b-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="8b92b-131">Přidávání znak typu identifikátoru `@` k libovolnému identifikátoru se z něj stane `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8b92b-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="8b92b-132">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-132">**Framework Type.**</span></span> <span data-ttu-id="8b92b-133">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Decimal?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="8b92b-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="8b92b-134">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8b92b-134">Range</span></span>  
 <span data-ttu-id="8b92b-135">Možná budete muset použít `D` přiřadit hodnotu velké znak `Decimal` proměnné nebo konstantní.</span><span class="sxs-lookup"><span data-stu-id="8b92b-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="8b92b-136">Tento požadavek je, protože kompilátor interpretuje jako literál `Long` Pokud následuje znak typu literálu literálu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8b92b-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="8b92b-137">Deklarace `bigDec1` nevytvoří přetečení, protože hodnota, která je k němu přiřazen spadá do rozsahu pro `Long`.</span><span class="sxs-lookup"><span data-stu-id="8b92b-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="8b92b-138">`Long` Lze přiřadit hodnotu `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b92b-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="8b92b-139">Deklarace `bigDec2` vygeneruje chybu přetečení, protože je příliš velká pro hodnotu, která je k němu přiřazen `Long`.</span><span class="sxs-lookup"><span data-stu-id="8b92b-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="8b92b-140">Protože číselný literál nemůže být nejprve interpretován jako `Long`, nelze přiřadit k `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b92b-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="8b92b-141">Pro `bigDec3`, znak typu literálu `D` řeší problém vynucením kompilátor k interpretaci jako literál `Decimal` místo jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="8b92b-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b92b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b92b-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b92b-143">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8b92b-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8b92b-144">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="8b92b-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="8b92b-145">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="8b92b-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="8b92b-146">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="8b92b-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8b92b-147">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="8b92b-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="8b92b-148">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="8b92b-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
