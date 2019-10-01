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
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700867"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="75d91-102">Decimal – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75d91-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="75d91-103">Obsahuje podepsané 128 hodnoty (16 bajtů) představující 96-bit (12 bajtů) celočíselných čísel, jejichž velikost se škáluje proměnnou výkonem 10.</span><span class="sxs-lookup"><span data-stu-id="75d91-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="75d91-104">Faktor škálování určuje počet číslic vpravo od desetinné čárky. Rozsah je od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="75d91-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="75d91-105">S měřítkem 0 (bez desetinných míst) je největší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="75d91-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="75d91-106">S 28 desetinnými místy je největší hodnota +/-7.9228162514264337593543950335 a nejmenší nenulová hodnota je +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="75d91-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="75d91-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75d91-107">Remarks</span></span>

<span data-ttu-id="75d91-108">Datový typ `Decimal` poskytuje největší počet platných číslic pro číslo.</span><span class="sxs-lookup"><span data-stu-id="75d91-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="75d91-109">Podporuje až 29 platných číslic a může reprezentovat hodnoty převyšující 7,9228 × 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="75d91-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="75d91-110">Je zvláště vhodná pro výpočty, jako je finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat chyby při zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="75d91-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="75d91-111">Výchozí hodnota `Decimal` je 0.</span><span class="sxs-lookup"><span data-stu-id="75d91-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="75d91-112">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="75d91-112">Programming Tips</span></span>

- <span data-ttu-id="75d91-113">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="75d91-113">**Precision.**</span></span> <span data-ttu-id="75d91-114">`Decimal` není datový typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="75d91-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="75d91-115">Struktura `Decimal` obsahuje binární celočíselnou hodnotu společně s bitem znaménka a koeficientem škálování celého čísla, který určuje, jaká část hodnoty je desítková frakce.</span><span class="sxs-lookup"><span data-stu-id="75d91-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="75d91-116">Z tohoto důvodu jsou hodnoty `Decimal` přesnější reprezentace v paměti než typy s plovoucí desetinnou čárkou (`Single` a `Double`).</span><span class="sxs-lookup"><span data-stu-id="75d91-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="75d91-117">**Předepsané.**</span><span class="sxs-lookup"><span data-stu-id="75d91-117">**Performance.**</span></span> <span data-ttu-id="75d91-118">Datový typ `Decimal` je nejpomalejší ze všech číselných typů.</span><span class="sxs-lookup"><span data-stu-id="75d91-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="75d91-119">Před výběrem datového typu byste měli zvážit důležitost přesnosti oproti výkonu.</span><span class="sxs-lookup"><span data-stu-id="75d91-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="75d91-120">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="75d91-120">**Widening.**</span></span> <span data-ttu-id="75d91-121">Datový typ `Decimal` se rozšíří na `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="75d91-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="75d91-122">To znamená, že můžete převést `Decimal` na některý z těchto typů bez výskytu chyby <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75d91-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="75d91-123">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="75d91-123">**Trailing Zeros.**</span></span> <span data-ttu-id="75d91-124">Visual Basic neukládá koncové nuly v literálu `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="75d91-125">Proměnná `Decimal` však zachovává všechny koncové nuly získané výpočtem.</span><span class="sxs-lookup"><span data-stu-id="75d91-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="75d91-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="75d91-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="75d91-127">Výstup `MsgBox` v předchozím příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="75d91-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="75d91-128">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="75d91-128">**Type Characters.**</span></span> <span data-ttu-id="75d91-129">Připojení znaku typu literálu `D` do literálu vynutí jej datový typ `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="75d91-130">Připojení znaku typu identifikátoru `@` k jakémukoli identifikátoru vynutí `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="75d91-131">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="75d91-131">**Framework Type.**</span></span> <span data-ttu-id="75d91-132">Odpovídající typ v .NET Framework je struktura <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75d91-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="75d91-133">Rozsah</span><span class="sxs-lookup"><span data-stu-id="75d91-133">Range</span></span>
 <span data-ttu-id="75d91-134">Je možné, že budete muset použít znak `D`, abyste přiřadili velkou hodnotu proměnné nebo konstantě `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="75d91-135">Tento požadavek je způsoben tím, že kompilátor interpretuje literál jako `Long`, pokud literální znak typu se neřídí literálem, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="75d91-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="75d91-136">Deklarace `bigDec1` nevyprodukuje přetečení, protože hodnota, která je přiřazena, spadá do rozsahu pro `Long`.</span><span class="sxs-lookup"><span data-stu-id="75d91-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="75d91-137">Hodnotu `Long` lze přiřadit proměnné `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="75d91-138">Deklarace `bigDec2` generuje chybu přetečení, protože hodnota, která je přiřazena, je pro `Long` příliš velká.</span><span class="sxs-lookup"><span data-stu-id="75d91-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="75d91-139">Vzhledem k tomu, že číselný literál nemůže být nejdříve interpretován jako `Long`, nelze jej přiřadit proměnné `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75d91-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="75d91-140">U `bigDec3` znak typu literálu `D` vyřeší problém tím, že kompilátor vynutí interpretaci literálu jako `Decimal` namísto jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="75d91-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="75d91-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75d91-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="75d91-142">Datové typy</span><span class="sxs-lookup"><span data-stu-id="75d91-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="75d91-143">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="75d91-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="75d91-144">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="75d91-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="75d91-145">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="75d91-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="75d91-146">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="75d91-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="75d91-147">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="75d91-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
