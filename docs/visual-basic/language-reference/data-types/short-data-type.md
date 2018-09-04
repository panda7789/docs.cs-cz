---
title: Short – datový typ (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: eb218a9b72208b13700ebd18dbf588066839203d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537991"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="2b88e-102">Short – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b88e-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="2b88e-103">Blokování podepsané 16bitová celá čísla (2bajtových), které v rozsahu od-32 768 až 32 767.</span><span class="sxs-lookup"><span data-stu-id="2b88e-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b88e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b88e-104">Remarks</span></span>  
 <span data-ttu-id="2b88e-105">Použití `Short` datový typ tak, aby obsahovala celočíselných hodnot, které nevyžadují šířku úplná `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2b88e-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="2b88e-106">V některých případech můžete sbalit modul common language runtime vaše `Short` proměnné úzce spolupracují a uložit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="2b88e-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="2b88e-107">Výchozí hodnota `Short` je 0.</span><span class="sxs-lookup"><span data-stu-id="2b88e-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="2b88e-108">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="2b88e-108">Literal assignments</span></span>

<span data-ttu-id="2b88e-109">Můžete deklarovat a inicializovat `Short` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="2b88e-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="2b88e-110">Pokud celočíselný literál je mimo rozsah `Short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="2b88e-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="2b88e-111">V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [celé číslo](integer-data-type.md) k `Short` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2b88e-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="2b88e-112">Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální.</span><span class="sxs-lookup"><span data-stu-id="2b88e-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2b88e-113">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="2b88e-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2b88e-114">Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="2b88e-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="2b88e-115">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="2b88e-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2b88e-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2b88e-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2b88e-117">Číselné literály může také zahrnovat `S` [znak](../../programming-guide\language-features\data-types/type-characters.md) k označení `Short` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2b88e-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="2b88e-118">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="2b88e-118">Programming tips</span></span>

-   <span data-ttu-id="2b88e-119">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="2b88e-119">**Widening.**</span></span> <span data-ttu-id="2b88e-120">`Short` Datový typ rozšiřuje na `Integer`, `Long`, `Decimal`, `Single`, nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="2b88e-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="2b88e-121">To znamená, že můžete převést `Short` na některý z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="2b88e-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="2b88e-122">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="2b88e-122">**Type Characters.**</span></span> <span data-ttu-id="2b88e-123">Přidávání znak typu literálu `S` k literálu se z něj stane `Short` datového typu.</span><span class="sxs-lookup"><span data-stu-id="2b88e-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="2b88e-124">`Short` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="2b88e-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="2b88e-125">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="2b88e-125">**Framework Type.**</span></span> <span data-ttu-id="2b88e-126">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Int16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="2b88e-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b88e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b88e-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="2b88e-128">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2b88e-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="2b88e-129">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="2b88e-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2b88e-130">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="2b88e-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2b88e-131">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="2b88e-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="2b88e-132">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="2b88e-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="2b88e-133">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="2b88e-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
