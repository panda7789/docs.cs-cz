---
title: Byte – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28189ab4ab1a9be9265d1cca020039b5302fb5d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590531"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="7bee5-102">Byte – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bee5-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="7bee5-103">Ukládání nepodepsané celých čísel 8bitové (1bajtů), které rozsah v hodnotě od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="7bee5-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bee5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bee5-104">Remarks</span></span>

<span data-ttu-id="7bee5-105">Použití `Byte` datový typ tak, aby obsahovala binární data.</span><span class="sxs-lookup"><span data-stu-id="7bee5-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="7bee5-106">Výchozí hodnota `Byte` je 0.</span><span class="sxs-lookup"><span data-stu-id="7bee5-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="7bee5-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="7bee5-107">Literal assignments</span></span>

<span data-ttu-id="7bee5-108">Můžete deklarace a inicializace `Byte` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="7bee5-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7bee5-109">Pokud celočíselný literál je mimo rozsah `Byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="7bee5-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="7bee5-110">V následujícím příkladu, celá čísla rovno 201, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [celé číslo](integer-data-type.md) k `byte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7bee5-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="7bee5-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="7bee5-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7bee5-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="7bee5-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7bee5-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="7bee5-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="7bee5-114">Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice.</span><span class="sxs-lookup"><span data-stu-id="7bee5-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7bee5-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7bee5-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="7bee5-116">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="7bee5-116">Programming tips</span></span>

-   <span data-ttu-id="7bee5-117">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="7bee5-117">**Negative Numbers.**</span></span> <span data-ttu-id="7bee5-118">Protože `Byte` je typ bez znaménka, nelze ho představují záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="7bee5-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="7bee5-119">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `Byte`, Visual Basic Převede výraz, který se `Short` první.</span><span class="sxs-lookup"><span data-stu-id="7bee5-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
-   <span data-ttu-id="7bee5-120">**Převody formátu.**</span><span class="sxs-lookup"><span data-stu-id="7bee5-120">**Format Conversions.**</span></span> <span data-ttu-id="7bee5-121">Když Visual Basic čte a zapisuje soubory nebo při volání knihovny DLL, metod a vlastností, může automaticky převádět mezi formáty dat.</span><span class="sxs-lookup"><span data-stu-id="7bee5-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="7bee5-122">Binární data uložená v `Byte` proměnných a polí je během takový formát převody zachována.</span><span class="sxs-lookup"><span data-stu-id="7bee5-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="7bee5-123">Neměli byste používat `String` proměnná pro binární data, protože její obsah může dojít k porušení během převodu mezi formáty ANSI a Unicode.</span><span class="sxs-lookup"><span data-stu-id="7bee5-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

-   <span data-ttu-id="7bee5-124">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="7bee5-124">**Widening.**</span></span> <span data-ttu-id="7bee5-125">`Byte` Datový typ rozšiřuje na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="7bee5-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="7bee5-126">To znamená, že můžete převést `Byte` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="7bee5-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="7bee5-127">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="7bee5-127">**Type Characters.**</span></span> <span data-ttu-id="7bee5-128">`Byte` nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="7bee5-128">`Byte` has no literal type character or identifier type character.</span></span>

-   <span data-ttu-id="7bee5-129">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="7bee5-129">**Framework Type.**</span></span> <span data-ttu-id="7bee5-130">Typ odpovídající v rozhraní .NET Framework je <xref:System.Byte?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="7bee5-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="7bee5-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bee5-131">Example</span></span>

 <span data-ttu-id="7bee5-132">V následujícím příkladu `b` je `Byte` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7bee5-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="7bee5-133">Příkazy ukazují rozsahu proměnné a do něj aplikaci bitové posunutí – operátory.</span><span class="sxs-lookup"><span data-stu-id="7bee5-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a><span data-ttu-id="7bee5-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bee5-134">See Also</span></span>

 <xref:System.Byte?displayProperty=nameWithType>  
 [<span data-ttu-id="7bee5-135">Datové typy</span><span class="sxs-lookup"><span data-stu-id="7bee5-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="7bee5-136">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="7bee5-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7bee5-137">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="7bee5-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="7bee5-138">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="7bee5-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
