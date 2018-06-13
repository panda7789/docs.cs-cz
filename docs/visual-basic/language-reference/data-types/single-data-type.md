---
title: Single – datový typ (Visual Basic)
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
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590768"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="cc40c-102">Single – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc40c-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="cc40c-103">Blokování podepsané IEEE 32-bit (4bajtový) s plovoucí desetinnou čárkou čísla s jednoduchou přesností v rozmezí od - 3.4028235E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty a z 1, 401298E-45 prostřednictvím 3.4028235E + 38 kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cc40c-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="cc40c-104">Čísla s jednoduchou přesností ukládat sblížení reálné číslo.</span><span class="sxs-lookup"><span data-stu-id="cc40c-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc40c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc40c-105">Remarks</span></span>  
 <span data-ttu-id="cc40c-106">Použití `Single` datový typ tak, aby obsahovala s plovoucí desetinnou čárkou hodnoty, které nevyžadují šířku úplná data `Double`.</span><span class="sxs-lookup"><span data-stu-id="cc40c-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="cc40c-107">V některých případech může být modul common language runtime moct pack vaší `Single` proměnné úzce spolupracují a uložte využití paměti.</span><span class="sxs-lookup"><span data-stu-id="cc40c-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="cc40c-108">Výchozí hodnota `Single` je 0.</span><span class="sxs-lookup"><span data-stu-id="cc40c-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="cc40c-109">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="cc40c-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="cc40c-110">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="cc40c-110">**Precision.**</span></span> <span data-ttu-id="cc40c-111">Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti.</span><span class="sxs-lookup"><span data-stu-id="cc40c-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="cc40c-112">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="cc40c-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="cc40c-113">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc40c-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="cc40c-114">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="cc40c-114">**Widening.**</span></span> <span data-ttu-id="cc40c-115">`Single` Datový typ rozšiřuje na `Double`.</span><span class="sxs-lookup"><span data-stu-id="cc40c-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="cc40c-116">To znamená, že můžete převést `Single` k `Double` bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="cc40c-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="cc40c-117">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="cc40c-117">**Trailing Zeros.**</span></span> <span data-ttu-id="cc40c-118">Typy s plovoucí desetinnou čárkou dat nemají žádné interního vyjádření koncové znaky 0.</span><span class="sxs-lookup"><span data-stu-id="cc40c-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="cc40c-119">Například se nerozlišují mezi 4.2000 a 4.2.</span><span class="sxs-lookup"><span data-stu-id="cc40c-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="cc40c-120">Při zobrazení nebo tisku hodnoty s plovoucí desetinnou čárkou v důsledku toho nejsou zobrazeny koncové znaky 0.</span><span class="sxs-lookup"><span data-stu-id="cc40c-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="cc40c-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="cc40c-121">**Type Characters.**</span></span> <span data-ttu-id="cc40c-122">Připojování znak typu literálu `F` k literál vynutí, aby `Single` datového typu.</span><span class="sxs-lookup"><span data-stu-id="cc40c-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="cc40c-123">Připojování znak typu identifikátoru `!` na všechny identifikátor vynutí jeho `Single`.</span><span class="sxs-lookup"><span data-stu-id="cc40c-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="cc40c-124">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="cc40c-124">**Framework Type.**</span></span> <span data-ttu-id="cc40c-125">Typ odpovídající v rozhraní .NET Framework je <xref:System.Single?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="cc40c-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc40c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc40c-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="cc40c-127">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cc40c-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="cc40c-128">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="cc40c-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="cc40c-129">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="cc40c-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="cc40c-130">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="cc40c-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="cc40c-131">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="cc40c-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="cc40c-132">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="cc40c-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="cc40c-133">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="cc40c-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
