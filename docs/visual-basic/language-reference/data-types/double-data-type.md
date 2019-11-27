---
title: Double – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344017"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="f3307-102">Double – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3307-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="f3307-103">Obsahuje 64 podepsaná čísla s plovoucí desetinnou čárkou (v bajtech) s dvojitou přesností, která jsou v rozsahu od-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 pro záporné hodnoty a od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3307-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="f3307-104">Čísla s dvojitou přesností ukládají přibližnou hodnotu reálného čísla.</span><span class="sxs-lookup"><span data-stu-id="f3307-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3307-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3307-105">Remarks</span></span>

<span data-ttu-id="f3307-106">`Double` datový typ poskytuje nejvyšší a nejmenší možné množství pro číslo.</span><span class="sxs-lookup"><span data-stu-id="f3307-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="f3307-107">Výchozí hodnota `Double` je 0.</span><span class="sxs-lookup"><span data-stu-id="f3307-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="f3307-108">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="f3307-108">Programming Tips</span></span>

- <span data-ttu-id="f3307-109">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="f3307-109">**Precision.**</span></span> <span data-ttu-id="f3307-110">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti vždy nejsou přesné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="f3307-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="f3307-111">To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a operátor `Mod`.</span><span class="sxs-lookup"><span data-stu-id="f3307-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="f3307-112">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f3307-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="f3307-113">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="f3307-113">**Trailing Zeros.**</span></span> <span data-ttu-id="f3307-114">Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových nulových znaků.</span><span class="sxs-lookup"><span data-stu-id="f3307-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="f3307-115">Například nerozlišuje mezi 4,2000 a 4,2.</span><span class="sxs-lookup"><span data-stu-id="f3307-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="f3307-116">V důsledku toho se při zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové nula znaků.</span><span class="sxs-lookup"><span data-stu-id="f3307-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="f3307-117">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="f3307-117">**Type Characters.**</span></span> <span data-ttu-id="f3307-118">Připojení znaku typu literálu `R` k literálu vynutí typ dat `Double`.</span><span class="sxs-lookup"><span data-stu-id="f3307-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="f3307-119">Například pokud je celočíselná hodnota následována `R`, hodnota se změní na `Double`.</span><span class="sxs-lookup"><span data-stu-id="f3307-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="f3307-120">Připojení znaku typu identifikátoru `#` k jakémukoli identifikátoru vynutí `Double`.</span><span class="sxs-lookup"><span data-stu-id="f3307-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="f3307-121">V následujícím příkladu je proměnná `num` zadána jako `Double`:</span><span class="sxs-lookup"><span data-stu-id="f3307-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="f3307-122">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="f3307-122">**Framework Type.**</span></span> <span data-ttu-id="f3307-123">Odpovídající typ v .NET Framework je struktura <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3307-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3307-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3307-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="f3307-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f3307-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f3307-126">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="f3307-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="f3307-127">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="f3307-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="f3307-128">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="f3307-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f3307-129">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="f3307-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f3307-130">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="f3307-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="f3307-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="f3307-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f3307-132">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="f3307-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
