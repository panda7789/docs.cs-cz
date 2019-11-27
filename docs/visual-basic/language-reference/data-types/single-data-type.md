---
title: Single – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343922"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="67f09-102">Single – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67f09-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="67f09-103">Obsahuje podepsaná čísla IEEE 32 s plovoucí desetinnou čárkou s jednoduchou přesností, která jsou v rozsahu hodnot od-3.4028235 E + 38 do-1.401298 E-45 pro záporné hodnoty a z 1.401298 E-45 až 3.4028235 E + 38 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f09-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="67f09-104">Čísla s jednoduchou přesností ukládají aproximaci reálného čísla.</span><span class="sxs-lookup"><span data-stu-id="67f09-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67f09-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67f09-105">Remarks</span></span>  

 <span data-ttu-id="67f09-106">Typ dat `Single` použijte k zahrnutí hodnot s plovoucí desetinnou čárkou, které nevyžadují plnou šířku dat `Double`.</span><span class="sxs-lookup"><span data-stu-id="67f09-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="67f09-107">V některých případech může modul CLR (Common Language Runtime) umět zabalit `Single` proměnných společně a ušetřit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="67f09-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="67f09-108">Výchozí hodnota `Single` je 0.</span><span class="sxs-lookup"><span data-stu-id="67f09-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="67f09-109">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="67f09-109">Programming Tips</span></span>  
  
- <span data-ttu-id="67f09-110">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="67f09-110">**Precision.**</span></span> <span data-ttu-id="67f09-111">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti.</span><span class="sxs-lookup"><span data-stu-id="67f09-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="67f09-112">To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a operátor `Mod`.</span><span class="sxs-lookup"><span data-stu-id="67f09-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="67f09-113">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="67f09-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="67f09-114">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="67f09-114">**Widening.**</span></span> <span data-ttu-id="67f09-115">`Single` datový typ se rozšíří na `Double`.</span><span class="sxs-lookup"><span data-stu-id="67f09-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="67f09-116">To znamená, že můžete převést `Single` na `Double` bez výskytu chyby <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67f09-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="67f09-117">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="67f09-117">**Trailing Zeros.**</span></span> <span data-ttu-id="67f09-118">Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových 0 znaků.</span><span class="sxs-lookup"><span data-stu-id="67f09-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="67f09-119">Například nerozlišuje mezi 4,2000 a 4,2.</span><span class="sxs-lookup"><span data-stu-id="67f09-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="67f09-120">V důsledku toho se po zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové 0 znaky.</span><span class="sxs-lookup"><span data-stu-id="67f09-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="67f09-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="67f09-121">**Type Characters.**</span></span> <span data-ttu-id="67f09-122">Připojení znaku typu literálu `F` k literálu vynutí typ dat `Single`.</span><span class="sxs-lookup"><span data-stu-id="67f09-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="67f09-123">Připojení znaku typu identifikátoru `!` k jakémukoli identifikátoru vynutí `Single`.</span><span class="sxs-lookup"><span data-stu-id="67f09-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="67f09-124">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="67f09-124">**Framework Type.**</span></span> <span data-ttu-id="67f09-125">Odpovídající typ v .NET Framework je struktura <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67f09-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f09-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67f09-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="67f09-127">Datové typy</span><span class="sxs-lookup"><span data-stu-id="67f09-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="67f09-128">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="67f09-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="67f09-129">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="67f09-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="67f09-130">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="67f09-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="67f09-131">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="67f09-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="67f09-132">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="67f09-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="67f09-133">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="67f09-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
