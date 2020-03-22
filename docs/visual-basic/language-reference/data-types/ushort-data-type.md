---
title: UShort – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400692"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="74391-102">UKrátký datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74391-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="74391-103">Obsahuje nepodepsaná 16bitová (2bajtová) celá čísla v hodnotě od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="74391-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74391-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74391-104">Remarks</span></span>

 <span data-ttu-id="74391-105">`UShort` Datový typ slouží k tomu, `Byte`aby obsahoval binární data příliš velká pro .</span><span class="sxs-lookup"><span data-stu-id="74391-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="74391-106">Výchozí hodnota `UShort` je 0.</span><span class="sxs-lookup"><span data-stu-id="74391-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="74391-107">Doslovná přiřazení</span><span class="sxs-lookup"><span data-stu-id="74391-107">Literal assignments</span></span>

<span data-ttu-id="74391-108">Proměnnou `UShort` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.</span><span class="sxs-lookup"><span data-stu-id="74391-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="74391-109">Pokud celé číslo literál je `UShort` mimo rozsah (to znamená, <xref:System.UInt16.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt16.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="74391-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="74391-110">V následujícím příkladu jsou `UShort` hodnoty přiřazeny celá čísla rovnající se 65 034, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.</span><span class="sxs-lookup"><span data-stu-id="74391-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="74391-111">Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="74391-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="74391-112">Desetinné literály nemají předponu.</span><span class="sxs-lookup"><span data-stu-id="74391-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="74391-113">Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="74391-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="74391-114">Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="74391-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="74391-115">Například:</span><span class="sxs-lookup"><span data-stu-id="74391-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="74391-116">Číselné literály mohou `US` `us` také obsahovat znak `UShort` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="74391-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="74391-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="74391-117">Programming tips</span></span>
  
- <span data-ttu-id="74391-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="74391-118">**Negative Numbers.**</span></span> <span data-ttu-id="74391-119">Protože `UShort` je nepodepsaný typ, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="74391-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="74391-120">Pokud použijete unární`-`minus ( ) operátor pro `UShort`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Integer` první.</span><span class="sxs-lookup"><span data-stu-id="74391-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="74391-121">**Dodržování předpisů CLS.**</span><span class="sxs-lookup"><span data-stu-id="74391-121">**CLS Compliance.**</span></span> <span data-ttu-id="74391-122">Datový `UShort` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.</span><span class="sxs-lookup"><span data-stu-id="74391-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="74391-123">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="74391-123">**Widening.**</span></span> <span data-ttu-id="74391-124">Datový `UShort` typ se `Integer`rozšiřuje `UInteger` `Long`na `ULong` `Decimal`, `Single`, `Double`, , a .</span><span class="sxs-lookup"><span data-stu-id="74391-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="74391-125">To znamená, `UShort` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="74391-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="74391-126">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="74391-126">**Type Characters.**</span></span> <span data-ttu-id="74391-127">Připojení znaků `US` literálu typu k literálu `UShort` vynutí na datový typ.</span><span class="sxs-lookup"><span data-stu-id="74391-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="74391-128">`UShort`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="74391-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="74391-129">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="74391-129">**Framework Type.**</span></span> <span data-ttu-id="74391-130">Odpovídající typ v rozhraní .NET <xref:System.UInt16?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="74391-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74391-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="74391-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="74391-132">Datové typy</span><span class="sxs-lookup"><span data-stu-id="74391-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="74391-133">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="74391-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="74391-134">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="74391-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="74391-135">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="74391-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="74391-136">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="74391-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
