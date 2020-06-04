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
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415631"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="2e28d-102">Double – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e28d-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="2e28d-103">Obsahuje 64 podepsaná čísla s plovoucí desetinnou čárkou (v bajtech) s dvojitou přesností, která jsou v rozsahu od-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 pro záporné hodnoty a od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e28d-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="2e28d-104">Čísla s dvojitou přesností ukládají přibližnou hodnotu reálného čísla.</span><span class="sxs-lookup"><span data-stu-id="2e28d-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e28d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e28d-105">Remarks</span></span>

<span data-ttu-id="2e28d-106">`Double`Datový typ poskytuje největší a nejmenší možnou velikost čísla.</span><span class="sxs-lookup"><span data-stu-id="2e28d-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="2e28d-107">Výchozí hodnota `Double` je 0.</span><span class="sxs-lookup"><span data-stu-id="2e28d-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="2e28d-108">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="2e28d-108">Programming Tips</span></span>

- <span data-ttu-id="2e28d-109">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="2e28d-109">**Precision.**</span></span> <span data-ttu-id="2e28d-110">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti vždy nejsou přesné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="2e28d-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="2e28d-111">To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="2e28d-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="2e28d-112">Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="2e28d-112">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="2e28d-113">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="2e28d-113">**Trailing Zeros.**</span></span> <span data-ttu-id="2e28d-114">Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových nulových znaků.</span><span class="sxs-lookup"><span data-stu-id="2e28d-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="2e28d-115">Například nerozlišuje mezi 4,2000 a 4,2.</span><span class="sxs-lookup"><span data-stu-id="2e28d-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="2e28d-116">V důsledku toho se při zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové nula znaků.</span><span class="sxs-lookup"><span data-stu-id="2e28d-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="2e28d-117">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="2e28d-117">**Type Characters.**</span></span> <span data-ttu-id="2e28d-118">Připojení znaku literálového typu `R` k literálu vynutí tento `Double` datový typ.</span><span class="sxs-lookup"><span data-stu-id="2e28d-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="2e28d-119">Například pokud je celočíselná hodnota následována `R` , hodnota se změní na `Double` .</span><span class="sxs-lookup"><span data-stu-id="2e28d-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="2e28d-120">Připojení znaku typu identifikátoru `#` k jakémukoli identifikátoru vynutí `Double` .</span><span class="sxs-lookup"><span data-stu-id="2e28d-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="2e28d-121">V následujícím příkladu `num` je proměnná zadána jako `Double` :</span><span class="sxs-lookup"><span data-stu-id="2e28d-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="2e28d-122">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="2e28d-122">**Framework Type.**</span></span> <span data-ttu-id="2e28d-123">Odpovídající typ v .NET Framework je <xref:System.Double?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="2e28d-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e28d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e28d-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="2e28d-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2e28d-125">Data Types</span></span>](index.md)
- [<span data-ttu-id="2e28d-126">Decimal – datový typ</span><span class="sxs-lookup"><span data-stu-id="2e28d-126">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="2e28d-127">Single – datový typ</span><span class="sxs-lookup"><span data-stu-id="2e28d-127">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="2e28d-128">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="2e28d-128">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="2e28d-129">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="2e28d-129">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="2e28d-130">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="2e28d-130">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="2e28d-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="2e28d-131">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="2e28d-132">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="2e28d-132">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
