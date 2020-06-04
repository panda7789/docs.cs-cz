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
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415528"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="090e7-102">Single – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="090e7-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="090e7-103">Obsahuje podepsaná čísla IEEE 32 s plovoucí desetinnou čárkou s jednoduchou přesností, která jsou v rozsahu hodnot od-3.4028235 E + 38 do-1.401298 E-45 pro záporné hodnoty a z 1.401298 E-45 až 3.4028235 E + 38 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="090e7-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="090e7-104">Čísla s jednoduchou přesností ukládají aproximaci reálného čísla.</span><span class="sxs-lookup"><span data-stu-id="090e7-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="090e7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="090e7-105">Remarks</span></span>  

 <span data-ttu-id="090e7-106">`Single`Datový typ použijte k zahrnutí hodnot s plovoucí desetinnou čárkou, které nevyžadují plnou šířku dat `Double` .</span><span class="sxs-lookup"><span data-stu-id="090e7-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="090e7-107">V některých případech může modul CLR (Common Language Runtime) umožňovat rozbalení `Single` proměnných společně a ušetřit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="090e7-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="090e7-108">Výchozí hodnota `Single` je 0.</span><span class="sxs-lookup"><span data-stu-id="090e7-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="090e7-109">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="090e7-109">Programming Tips</span></span>  
  
- <span data-ttu-id="090e7-110">**Číslic.**</span><span class="sxs-lookup"><span data-stu-id="090e7-110">**Precision.**</span></span> <span data-ttu-id="090e7-111">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti.</span><span class="sxs-lookup"><span data-stu-id="090e7-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="090e7-112">To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="090e7-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="090e7-113">Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="090e7-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="090e7-114">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="090e7-114">**Widening.**</span></span> <span data-ttu-id="090e7-115">`Single`Datový typ se rozšíří na `Double` .</span><span class="sxs-lookup"><span data-stu-id="090e7-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="090e7-116">To znamená, že můžete převést `Single` na `Double` bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="090e7-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="090e7-117">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="090e7-117">**Trailing Zeros.**</span></span> <span data-ttu-id="090e7-118">Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových 0 znaků.</span><span class="sxs-lookup"><span data-stu-id="090e7-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="090e7-119">Například nerozlišuje mezi 4,2000 a 4,2.</span><span class="sxs-lookup"><span data-stu-id="090e7-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="090e7-120">V důsledku toho se po zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové 0 znaky.</span><span class="sxs-lookup"><span data-stu-id="090e7-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="090e7-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="090e7-121">**Type Characters.**</span></span> <span data-ttu-id="090e7-122">Připojení znaku literálového typu `F` k literálu vynutí tento `Single` datový typ.</span><span class="sxs-lookup"><span data-stu-id="090e7-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="090e7-123">Připojení znaku typu identifikátoru `!` k jakémukoli identifikátoru vynutí `Single` .</span><span class="sxs-lookup"><span data-stu-id="090e7-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="090e7-124">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="090e7-124">**Framework Type.**</span></span> <span data-ttu-id="090e7-125">Odpovídající typ v .NET Framework je <xref:System.Single?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="090e7-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090e7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="090e7-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="090e7-127">Datové typy</span><span class="sxs-lookup"><span data-stu-id="090e7-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="090e7-128">Decimal – datový typ</span><span class="sxs-lookup"><span data-stu-id="090e7-128">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="090e7-129">Double – datový typ</span><span class="sxs-lookup"><span data-stu-id="090e7-129">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="090e7-130">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="090e7-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="090e7-131">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="090e7-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="090e7-132">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="090e7-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="090e7-133">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="090e7-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
