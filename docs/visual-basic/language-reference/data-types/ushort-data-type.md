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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343857"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="3e487-102">UShort – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e487-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="3e487-103">Obsahuje nepodepsaná 16bitová (2-bajt) celá čísla v rozsahu od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="3e487-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e487-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e487-104">Remarks</span></span>

 <span data-ttu-id="3e487-105">Datový typ `UShort` použijte k zahrnutí binárních dat, která jsou pro `Byte`příliš velká.</span><span class="sxs-lookup"><span data-stu-id="3e487-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="3e487-106">Výchozí hodnota `UShort` je 0.</span><span class="sxs-lookup"><span data-stu-id="3e487-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="3e487-107">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="3e487-107">Literal assignments</span></span>

<span data-ttu-id="3e487-108">Můžete deklarovat a inicializovat `UShort` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="3e487-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="3e487-109">Pokud je celočíselný literál mimo rozsah `UShort` (to znamená, pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="3e487-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="3e487-110">V následujícím příkladu jsou celá čísla rovna 65 034, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `UShort` hodnot.</span><span class="sxs-lookup"><span data-stu-id="3e487-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="3e487-111">Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="3e487-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="3e487-112">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="3e487-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3e487-113">Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3e487-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="3e487-114">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="3e487-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="3e487-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3e487-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="3e487-116">Číselné literály mohou také zahrnovat `US` nebo `us` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení `UShort` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3e487-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="3e487-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="3e487-117">Programming tips</span></span>
  
- <span data-ttu-id="3e487-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="3e487-118">**Negative Numbers.**</span></span> <span data-ttu-id="3e487-119">Vzhledem k tomu, že `UShort` je typ bez znaménka, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="3e487-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="3e487-120">Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `UShort`, Visual Basic výraz převede na `Integer` jako první.</span><span class="sxs-lookup"><span data-stu-id="3e487-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="3e487-121">**Kompatibilita se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="3e487-121">**CLS Compliance.**</span></span> <span data-ttu-id="3e487-122">`UShort` datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="3e487-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="3e487-123">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="3e487-123">**Widening.**</span></span> <span data-ttu-id="3e487-124">`UShort` datový typ rozšiřuje na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`a `Double`.</span><span class="sxs-lookup"><span data-stu-id="3e487-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="3e487-125">To znamená, že můžete převést `UShort` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e487-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="3e487-126">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="3e487-126">**Type Characters.**</span></span> <span data-ttu-id="3e487-127">Připojení znaků literálového typu `US` k literálu vynutí tento datový typ `UShort`.</span><span class="sxs-lookup"><span data-stu-id="3e487-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="3e487-128">`UShort` nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="3e487-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="3e487-129">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="3e487-129">**Framework Type.**</span></span> <span data-ttu-id="3e487-130">Odpovídající typ v .NET Framework je struktura <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e487-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e487-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e487-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="3e487-132">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3e487-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="3e487-133">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="3e487-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="3e487-134">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="3e487-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="3e487-135">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="3e487-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="3e487-136">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="3e487-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
