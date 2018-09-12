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
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705177"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="36a88-102">Single – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36a88-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="36a88-103">Blokování podepsané IEEE 32bitová (4bajtová) jednoduchou přesnost s plovoucí desetinnou čárkou čísla v rozmezí od - 3.4028235E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty a z 1, 401298E-45 prostřednictvím 3.4028235E + 38 pro kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36a88-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="36a88-104">Čísla s jednoduchou přesností ukládání aproximaci reálné číslo.</span><span class="sxs-lookup"><span data-stu-id="36a88-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36a88-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36a88-105">Remarks</span></span>  
 <span data-ttu-id="36a88-106">Použití `Single` datový typ tak, aby obsahovala s plovoucí desetinnou čárkou hodnoty, které nevyžadují šířku úplná `Double`.</span><span class="sxs-lookup"><span data-stu-id="36a88-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="36a88-107">V některých případech může být schopni pack modul common language runtime vaše `Single` proměnné úzce spolupracují a uložit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="36a88-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="36a88-108">Výchozí hodnota `Single` je 0.</span><span class="sxs-lookup"><span data-stu-id="36a88-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="36a88-109">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="36a88-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="36a88-110">**Přesnost.**</span><span class="sxs-lookup"><span data-stu-id="36a88-110">**Precision.**</span></span> <span data-ttu-id="36a88-111">Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti.</span><span class="sxs-lookup"><span data-stu-id="36a88-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="36a88-112">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="36a88-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="36a88-113">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="36a88-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="36a88-114">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="36a88-114">**Widening.**</span></span> <span data-ttu-id="36a88-115">`Single` Datový typ rozšiřuje na `Double`.</span><span class="sxs-lookup"><span data-stu-id="36a88-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="36a88-116">To znamená, že můžete převést `Single` k `Double` aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="36a88-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="36a88-117">**Koncové nuly.**</span><span class="sxs-lookup"><span data-stu-id="36a88-117">**Trailing Zeros.**</span></span> <span data-ttu-id="36a88-118">S plovoucí desetinnou čárkou datové typy, které nemají žádné vnitřní reprezentaci koncové znaky 0.</span><span class="sxs-lookup"><span data-stu-id="36a88-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="36a88-119">Například že nerozlišuje mezi 4.2000 a 4.2.</span><span class="sxs-lookup"><span data-stu-id="36a88-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="36a88-120">V důsledku toho koncové znaky 0 se nezobrazují při zobrazení nebo tisk hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="36a88-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="36a88-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="36a88-121">**Type Characters.**</span></span> <span data-ttu-id="36a88-122">Přidávání znak typu literálu `F` k literálu se z něj stane `Single` datového typu.</span><span class="sxs-lookup"><span data-stu-id="36a88-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="36a88-123">Přidávání znak typu identifikátoru `!` k libovolnému identifikátoru se z něj stane `Single`.</span><span class="sxs-lookup"><span data-stu-id="36a88-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="36a88-124">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="36a88-124">**Framework Type.**</span></span> <span data-ttu-id="36a88-125">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Single?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="36a88-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a88-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="36a88-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="36a88-127">Datové typy</span><span class="sxs-lookup"><span data-stu-id="36a88-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="36a88-128">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="36a88-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="36a88-129">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="36a88-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="36a88-130">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="36a88-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="36a88-131">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="36a88-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="36a88-132">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="36a88-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="36a88-133">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="36a88-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
