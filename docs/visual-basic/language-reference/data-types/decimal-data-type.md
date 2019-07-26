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
ms.openlocfilehash: bab5a0bd7e0a85d550362bc3c1166566f6dcb81b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512776"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="e8cd5-102">Decimal – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8cd5-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="e8cd5-103">Obsahuje podepsané 128 hodnoty (16 bajtů) představující 96-bit (12 bajtů) celočíselných čísel, jejichž velikost se škáluje proměnnou výkonem 10.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="e8cd5-104">Faktor škálování určuje počet číslic vpravo od desetinné čárky. Rozsah je od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="e8cd5-105">S měřítkem 0 (bez desetinných míst) je největší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="e8cd5-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="e8cd5-106">S 28 desetinnými místy je největší hodnota +/-7.9228162514264337593543950335 a nejmenší nenulová hodnota je +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="e8cd5-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="e8cd5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8cd5-107">Remarks</span></span>

<span data-ttu-id="e8cd5-108">`Decimal` Datový typ poskytuje největší počet platných číslic pro číslo.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="e8cd5-109">Podporuje až 29 platných číslic a může reprezentovat hodnoty převyšující 7,9228 × 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="e8cd5-110">Je zvláště vhodná pro výpočty, jako je finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat chyby při zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="e8cd5-111">Výchozí hodnota `Decimal` je 0.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="e8cd5-112">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="e8cd5-112">Programming Tips</span></span>

- <span data-ttu-id="e8cd5-113">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-113">**Precision.**</span></span> <span data-ttu-id="e8cd5-114">`Decimal`není datový typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="e8cd5-115">`Decimal` Struktura obsahuje binární celočíselnou hodnotu společně s bitem znaménka a koeficientem škálování celého čísla, který určuje, jaká část hodnoty je desítkový zlomek.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="e8cd5-116">Z tohoto `Decimal` důvodu čísla mají přesnější reprezentace v paměti než typy s plovoucí desetinnou čárkou`Single` ( `Double`a).</span><span class="sxs-lookup"><span data-stu-id="e8cd5-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="e8cd5-117">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-117">**Performance.**</span></span> <span data-ttu-id="e8cd5-118">`Decimal` Datový typ je nejpomalejší ze všech číselných typů.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="e8cd5-119">Před výběrem datového typu byste měli zvážit důležitost přesnosti oproti výkonu.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="e8cd5-120">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-120">**Widening.**</span></span> <span data-ttu-id="e8cd5-121">Datový typ se rozšíří na `Single` nebo `Double`. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="e8cd5-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="e8cd5-122">To znamená, že můžete `Decimal` převést na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="e8cd5-123">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-123">**Trailing Zeros.**</span></span> <span data-ttu-id="e8cd5-124">Visual Basic neukládá koncové nuly v `Decimal` literálu.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="e8cd5-125">`Decimal` Nicméně proměnná zachovává všechny koncové nuly získané výpočty.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="e8cd5-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="e8cd5-127">Výstup `MsgBox` v předchozím příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="e8cd5-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="e8cd5-128">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-128">**Type Characters.**</span></span> <span data-ttu-id="e8cd5-129">Připojení znaku `D` literálového typu k literálu vynutí `Decimal` tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="e8cd5-130">Připojení znaku `@` typu identifikátoru k jakémukoli identifikátoru vynutí `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="e8cd5-131">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="e8cd5-131">**Framework Type.**</span></span> <span data-ttu-id="e8cd5-132">Odpovídající typ v .NET Framework je <xref:System.Decimal?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="e8cd5-133">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e8cd5-133">Range</span></span>
 <span data-ttu-id="e8cd5-134">Je možné, že budete muset `D` použít znak typu pro přiřazení velké hodnoty `Decimal` proměnné nebo konstantě.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="e8cd5-135">Tento požadavek je způsoben tím, že kompilátor interpretuje literál `Long` , jako by literální znak typu literálu nenásleduje literál, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="e8cd5-136">Deklarace pro nemá `bigDec1` za následek přetečení, protože hodnota, která je přiřazena, spadá do rozsahu pro. `Long`</span><span class="sxs-lookup"><span data-stu-id="e8cd5-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="e8cd5-137">Hodnota může být přiřazena `Decimal` proměnné. `Long`</span><span class="sxs-lookup"><span data-stu-id="e8cd5-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="e8cd5-138">Deklarace pro `bigDec2` vygeneruje chybu přetečení, protože hodnota, která je přiřazena, je pro `Long`hodnotu příliš velká.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="e8cd5-139">Vzhledem k tomu, že číselný literál nemůže být nejdříve `Long`interpretován jako a, nelze jej přiřadit `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="e8cd5-140">Pro `bigDec3`je znak `D` literálového typu vyřeší problém tím, že vynutí kompilátor `Decimal` interpretovat literál jako místo jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="e8cd5-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8cd5-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8cd5-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e8cd5-142">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e8cd5-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="e8cd5-143">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="e8cd5-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="e8cd5-144">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="e8cd5-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="e8cd5-145">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="e8cd5-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e8cd5-146">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="e8cd5-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="e8cd5-147">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="e8cd5-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
