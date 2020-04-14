---
title: Decimal – datový typ
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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243320"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="0b5db-102">Decimal – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b5db-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="0b5db-103">Pojmy podepsané 128bitové (16bajtové) hodnoty představující 96bitová (12bajtová) celá čísla se změnami o proměnlivou sílu 10.</span><span class="sxs-lookup"><span data-stu-id="0b5db-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="0b5db-104">Faktor měřítka určuje počet číslic vpravo od desetinné čárky; pohybuje se od 0 do 28.</span><span class="sxs-lookup"><span data-stu-id="0b5db-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="0b5db-105">S stupnicí 0 (bez desetinných míst) je nejvyšší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7.922816251426437593543950335E+28).</span><span class="sxs-lookup"><span data-stu-id="0b5db-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="0b5db-106">S 28 desetinnými místy je největší hodnota +/-7.9228162514264337593543950335 a nejmenší nenulová hodnota je +/-0.00000000000000000000000000000000000000000000000000000000000000000000000000000228.</span><span class="sxs-lookup"><span data-stu-id="0b5db-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="0b5db-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b5db-107">Remarks</span></span>

<span data-ttu-id="0b5db-108">Datový `Decimal` typ poskytuje největší počet platných číslic pro číslo.</span><span class="sxs-lookup"><span data-stu-id="0b5db-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="0b5db-109">Podporuje až 29 platných číslic a může představovat hodnoty přesahující 7,9228 x 10^28.</span><span class="sxs-lookup"><span data-stu-id="0b5db-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="0b5db-110">Je vhodný zejména pro výpočty, jako jsou finanční, které vyžadují velký počet číslic, ale nemohou tolerovat chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="0b5db-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="0b5db-111">Výchozí hodnota `Decimal` je 0.</span><span class="sxs-lookup"><span data-stu-id="0b5db-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="0b5db-112">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="0b5db-112">Programming Tips</span></span>

- <span data-ttu-id="0b5db-113">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-113">**Precision.**</span></span> <span data-ttu-id="0b5db-114">`Decimal`není datový typ s plovoucí desetinnou desetinnou tázkou.</span><span class="sxs-lookup"><span data-stu-id="0b5db-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="0b5db-115">Struktura `Decimal` obsahuje binární integer hodnotu, spolu s znaménkový bit a faktor měřítka celé číslo, který určuje, která část hodnoty je desetinný zlomek.</span><span class="sxs-lookup"><span data-stu-id="0b5db-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="0b5db-116">Z tohoto `Decimal` důvodu čísla mají přesnější reprezentaci v`Single` paměti `Double`než typy s plovoucí desetinnou desetinnou tálicí ( a ).</span><span class="sxs-lookup"><span data-stu-id="0b5db-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="0b5db-117">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-117">**Performance.**</span></span> <span data-ttu-id="0b5db-118">Datový `Decimal` typ je nejpomalejší ze všech číselných typů.</span><span class="sxs-lookup"><span data-stu-id="0b5db-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="0b5db-119">Před výběrem datového typu byste měli zvážit důležitost přesnosti oproti výkonu.</span><span class="sxs-lookup"><span data-stu-id="0b5db-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="0b5db-120">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-120">**Widening.**</span></span> <span data-ttu-id="0b5db-121">Datový `Decimal` typ se `Single` rozšiřuje `Double`na nebo .</span><span class="sxs-lookup"><span data-stu-id="0b5db-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="0b5db-122">To znamená, `Decimal` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="0b5db-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="0b5db-123">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-123">**Trailing Zeros.**</span></span> <span data-ttu-id="0b5db-124">Visual Basic neukládá koncové nuly `Decimal` v literálu.</span><span class="sxs-lookup"><span data-stu-id="0b5db-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="0b5db-125">Proměnná `Decimal` však zachová všechny koncové nuly získané výpočetně.</span><span class="sxs-lookup"><span data-stu-id="0b5db-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="0b5db-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0b5db-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="0b5db-127">Výstup `MsgBox` v předchozím příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="0b5db-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="0b5db-128">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-128">**Type Characters.**</span></span> <span data-ttu-id="0b5db-129">Připojení znaku `D` typu literálu k literálu jej vynutí na `Decimal` datový typ.</span><span class="sxs-lookup"><span data-stu-id="0b5db-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="0b5db-130">Připojení znaku `@` typu identifikátoru k `Decimal`libovolnému identifikátoru jej vynutí .</span><span class="sxs-lookup"><span data-stu-id="0b5db-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="0b5db-131">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="0b5db-131">**Framework Type.**</span></span> <span data-ttu-id="0b5db-132">Odpovídající typ v rozhraní .NET <xref:System.Decimal?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="0b5db-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="0b5db-133">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0b5db-133">Range</span></span>

 <span data-ttu-id="0b5db-134">Může být nutné `D` použít znak typu k přiřazení `Decimal` velké hodnoty proměnné nebo konstanty.</span><span class="sxs-lookup"><span data-stu-id="0b5db-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="0b5db-135">Tento požadavek je, protože kompilátor `Long` interpretuje literál jako pokud literál typ znak následuje literál, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0b5db-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="0b5db-136">Deklarace `bigDec1` pro nevytváří přetečení, protože hodnota, která je přiřazena `Long`k němu spadá do rozsahu pro .</span><span class="sxs-lookup"><span data-stu-id="0b5db-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="0b5db-137">Hodnotu `Long` lze přiřadit `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0b5db-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="0b5db-138">Deklarace `bigDec2` pro generuje chybu přetečení, protože hodnota, která je `Long`přiřazena k němu je příliš velký pro .</span><span class="sxs-lookup"><span data-stu-id="0b5db-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="0b5db-139">Vzhledem k tomu, že číselný literál nelze nejprve interpretovat jako `Long`a , nelze jej přiřadit k `Decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0b5db-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="0b5db-140">Pro `bigDec3`znak typu literálu `D` řeší problém vynucením kompilátoru interpretovat literál jako `Decimal` místo jako . `Long`</span><span class="sxs-lookup"><span data-stu-id="0b5db-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b5db-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b5db-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0b5db-142">Typy dat</span><span class="sxs-lookup"><span data-stu-id="0b5db-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0b5db-143">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="0b5db-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="0b5db-144">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="0b5db-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="0b5db-145">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="0b5db-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0b5db-146">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="0b5db-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0b5db-147">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="0b5db-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
