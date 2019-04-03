---
title: Double – datový typ (Visual Basic)
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
ms.openlocfilehash: 701d10a334757a96ffd634204c1e1d5eb5418ce6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824660"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="a6fd0-102">Double – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6fd0-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="a6fd0-103">Blokování podepsané IEEE – 64bitová (8 bajtů) dvojité přesnosti s plovoucí desetinnou čárkou čísla v rozsahu od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 pro záporné hodnoty a z 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="a6fd0-104">Dvojitá přesnost – čísla ukládání aproximaci reálné číslo.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6fd0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6fd0-105">Remarks</span></span>  
 <span data-ttu-id="a6fd0-106">`Double` Datový typ poskytuje řádově největší a co nejmenší možné číslo.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="a6fd0-107">Výchozí hodnota `Double` je 0.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="a6fd0-108">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="a6fd0-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="a6fd0-109">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="a6fd0-109">**Precision.**</span></span> <span data-ttu-id="a6fd0-110">Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="a6fd0-111">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="a6fd0-112">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a6fd0-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="a6fd0-113">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="a6fd0-113">**Trailing Zeros.**</span></span> <span data-ttu-id="a6fd0-114">S plovoucí desetinnou čárkou datové typy, které nemají žádné vnitřní reprezentaci koncové nulové znaky.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="a6fd0-115">Například že nerozlišuje mezi 4.2000 a 4.2.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="a6fd0-116">V důsledku toho koncové nulové znaky se nezobrazují při zobrazení nebo tisk hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="a6fd0-117">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="a6fd0-117">**Type Characters.**</span></span> <span data-ttu-id="a6fd0-118">Přidávání znak typu literálu `R` k literálu se z něj stane `Double` datového typu.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="a6fd0-119">Například, pokud je následována celočíselnou hodnotu `R`, hodnota se změní na `Double`.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="a6fd0-120">Přidávání znak typu identifikátoru `#` k libovolnému identifikátoru se z něj stane `Double`.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="a6fd0-121">V následujícím příkladu je proměnná `num` je zadán jako `Double`:</span><span class="sxs-lookup"><span data-stu-id="a6fd0-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="a6fd0-122">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="a6fd0-122">**Framework Type.**</span></span> <span data-ttu-id="a6fd0-123">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Double?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="a6fd0-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fd0-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6fd0-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="a6fd0-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a6fd0-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a6fd0-126">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="a6fd0-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="a6fd0-127">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="a6fd0-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="a6fd0-128">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="a6fd0-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a6fd0-129">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="a6fd0-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a6fd0-130">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="a6fd0-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="a6fd0-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="a6fd0-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="a6fd0-132">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="a6fd0-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
