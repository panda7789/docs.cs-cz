---
title: Long – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687c235be76ef522758658fd1c5fe0cb1dbeb414
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591363"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="0103c-102">Long – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0103c-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="0103c-103">Blokování podepsaná celá čísla 64-bit (8 bajtů) v rozmezí od-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807 (9.2 … E + 18).</span><span class="sxs-lookup"><span data-stu-id="0103c-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0103c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0103c-104">Remarks</span></span>

 <span data-ttu-id="0103c-105">Použití `Long` datový typ tak, aby obsahovala celá čísla, která je příliš velký, aby se vešla do `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="0103c-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="0103c-106">Výchozí hodnota `Long` je 0.</span><span class="sxs-lookup"><span data-stu-id="0103c-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="0103c-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="0103c-107">Literal assignments</span></span> 

<span data-ttu-id="0103c-108">Můžete deklarace a inicializace `Long` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="0103c-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0103c-109">Pokud literálu celé číslo je mimo rozsah `Long` (tj. Pokud je menší než <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="0103c-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0103c-110">V následujícím příkladu, celá čísla rovno 4 294 967 296 jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `Long` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0103c-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="0103c-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="0103c-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0103c-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="0103c-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0103c-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="0103c-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="0103c-114">Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice.</span><span class="sxs-lookup"><span data-stu-id="0103c-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0103c-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0103c-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0103c-116">Číselné literály může také obsahovat `L` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `Long` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0103c-116">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="0103c-117">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="0103c-117">Programming tips</span></span>

-   <span data-ttu-id="0103c-118">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="0103c-118">**Interop Considerations.**</span></span> <span data-ttu-id="0103c-119">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, nezapomeňte, že `Long` má odlišné datové šířku (32bitová verze) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="0103c-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="0103c-120">32-bit argument předáte pro tyto součásti, deklarujte ji jako `Integer` místo `Long` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0103c-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="0103c-121">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="0103c-121">**Widening.**</span></span> <span data-ttu-id="0103c-122">`Long` Datový typ rozšiřuje na `Decimal`, `Single`, nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="0103c-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0103c-123">To znamená, že můžete převést `Long` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="0103c-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="0103c-124">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="0103c-124">**Type Characters.**</span></span> <span data-ttu-id="0103c-125">Připojování znak typu literálu `L` k literál vynutí, aby `Long` datového typu.</span><span class="sxs-lookup"><span data-stu-id="0103c-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="0103c-126">Připojování znak typu identifikátoru `&` na všechny identifikátor vynutí jeho `Long`.</span><span class="sxs-lookup"><span data-stu-id="0103c-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="0103c-127">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="0103c-127">**Framework Type.**</span></span> <span data-ttu-id="0103c-128">Typ odpovídající v rozhraní .NET Framework je <xref:System.Int64?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="0103c-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0103c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0103c-129">See also</span></span>

<span data-ttu-id="0103c-130"><xref:System.Int64>
[Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="0103c-130"><xref:System.Int64>
[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="0103c-131">[Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0103c-131">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="0103c-132">[Short – datový typ](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0103c-132">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="0103c-133">[Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="0103c-133">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="0103c-134">[Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="0103c-134">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="0103c-135">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="0103c-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
