---
title: "Double – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="24963-102">Double – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24963-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="24963-103">Blokování podepsané IEEE 64-bit (8 bajtů) dvojitou přesností s plovoucí desetinnou čárkou čísla, která rozsah v hodnotě od - 1.79769313486231570E + 308 prostřednictvím - 4.94065645841246544E-324 pro záporné hodnoty a z 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="24963-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="24963-104">Dvojitá přesnost – čísla ukládat sblížení reálné číslo.</span><span class="sxs-lookup"><span data-stu-id="24963-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24963-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24963-105">Remarks</span></span>  
 <span data-ttu-id="24963-106">`Double` Datový typ poskytuje by velikosti největší a nejmenší možný počet.</span><span class="sxs-lookup"><span data-stu-id="24963-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="24963-107">Výchozí hodnota `Double` je 0.</span><span class="sxs-lookup"><span data-stu-id="24963-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="24963-108">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="24963-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="24963-109">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="24963-109">**Precision.**</span></span> <span data-ttu-id="24963-110">Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti.</span><span class="sxs-lookup"><span data-stu-id="24963-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="24963-111">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="24963-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="24963-112">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="24963-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="24963-113">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="24963-113">**Trailing Zeros.**</span></span> <span data-ttu-id="24963-114">Typy s plovoucí desetinnou čárkou dat nemají žádné interní reprezentace koncové nulové znaky.</span><span class="sxs-lookup"><span data-stu-id="24963-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="24963-115">Například se nerozlišují mezi 4.2000 a 4.2.</span><span class="sxs-lookup"><span data-stu-id="24963-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="24963-116">V důsledku toho koncové nulové znaky se nezobrazí při zobrazení nebo tisku hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="24963-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="24963-117">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="24963-117">**Type Characters.**</span></span> <span data-ttu-id="24963-118">Připojování znak typu literálu `R` k literál vynutí, aby `Double` datového typu.</span><span class="sxs-lookup"><span data-stu-id="24963-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="24963-119">Například, pokud je následován celočíselnou hodnotu `R`, je hodnota změněna na `Double`.</span><span class="sxs-lookup"><span data-stu-id="24963-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="24963-120">Připojování znak typu identifikátoru `#` na všechny identifikátor vynutí jeho `Double`.</span><span class="sxs-lookup"><span data-stu-id="24963-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="24963-121">V následujícím příkladu, proměnná `num` je zadán jako `Double`:</span><span class="sxs-lookup"><span data-stu-id="24963-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="24963-122">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="24963-122">**Framework Type.**</span></span> <span data-ttu-id="24963-123">Typ odpovídající v rozhraní .NET Framework je <xref:System.Double?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="24963-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24963-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="24963-124">See Also</span></span>  
 <xref:System.Double?displayProperty=nameWithType>  
 [<span data-ttu-id="24963-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="24963-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="24963-126">Decimal – datový typ</span><span class="sxs-lookup"><span data-stu-id="24963-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="24963-127">Single – datový typ</span><span class="sxs-lookup"><span data-stu-id="24963-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="24963-128">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="24963-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="24963-129">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="24963-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="24963-130">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="24963-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="24963-131">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="24963-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="24963-132">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="24963-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
