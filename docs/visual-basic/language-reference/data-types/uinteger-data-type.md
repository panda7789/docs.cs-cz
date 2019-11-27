---
title: UInteger – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343892"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="fbd65-102">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="fbd65-102">UInteger data type</span></span>

<span data-ttu-id="fbd65-103">Obsahuje nepodepsaná 32 (4 bajt) celá čísla v rozsahu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="fbd65-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="fbd65-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbd65-104">Remarks</span></span>

<span data-ttu-id="fbd65-105">`UInteger` datový typ poskytuje největší hodnotu bez znaménka v nejúčinnější šířce dat.</span><span class="sxs-lookup"><span data-stu-id="fbd65-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="fbd65-106">Výchozí hodnota `UInteger` je 0.</span><span class="sxs-lookup"><span data-stu-id="fbd65-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="fbd65-107">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="fbd65-107">Literal assignments</span></span>

<span data-ttu-id="fbd65-108">Můžete deklarovat a inicializovat `UInteger` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="fbd65-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="fbd65-109">Pokud je celočíselný literál mimo rozsah `UInteger` (to znamená, pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="fbd65-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="fbd65-110">V následujícím příkladu jsou celá čísla rovna 3 000 000 000, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `UInteger` hodnot.</span><span class="sxs-lookup"><span data-stu-id="fbd65-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="fbd65-111">Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="fbd65-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fbd65-112">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="fbd65-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fbd65-113">Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fbd65-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="fbd65-114">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="fbd65-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="fbd65-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fbd65-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="fbd65-116">Číselné literály mohou také zahrnovat `UI` nebo `ui` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení `UInteger` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fbd65-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="fbd65-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="fbd65-117">Programming tips</span></span>

<span data-ttu-id="fbd65-118">Datové typy `UInteger` a `Integer` poskytují optimální výkon na 32 procesor, protože menší celočíselné typy (`UShort`, `Short`, `Byte`a `SByte`), i když používají méně bitů, vybírají více času načítání, ukládání a načítání.</span><span class="sxs-lookup"><span data-stu-id="fbd65-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="fbd65-119">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-119">**Negative Numbers.**</span></span> <span data-ttu-id="fbd65-120">Vzhledem k tomu, že `UInteger` je typ bez znaménka, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="fbd65-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="fbd65-121">Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `UInteger`, Visual Basic výraz převede na `Long` jako první.</span><span class="sxs-lookup"><span data-stu-id="fbd65-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="fbd65-122">**Kompatibilita se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-122">**CLS Compliance.**</span></span> <span data-ttu-id="fbd65-123">`UInteger` datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="fbd65-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="fbd65-124">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-124">**Interop Considerations.**</span></span> <span data-ttu-id="fbd65-125">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy jako `uint` mohou mít v jiných prostředích jinou šířku dat (16 bitů).</span><span class="sxs-lookup"><span data-stu-id="fbd65-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="fbd65-126">Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `UShort` místo `UInteger` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fbd65-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="fbd65-127">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-127">**Widening.**</span></span> <span data-ttu-id="fbd65-128">`UInteger` datový typ se rozšíří na `Long`, `ULong`, `Decimal`, `Single`a `Double`.</span><span class="sxs-lookup"><span data-stu-id="fbd65-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="fbd65-129">To znamená, že můžete převést `UInteger` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fbd65-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="fbd65-130">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-130">**Type Characters.**</span></span> <span data-ttu-id="fbd65-131">Připojení znaků literálového typu `UI` k literálu vynutí tento datový typ `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="fbd65-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="fbd65-132">`UInteger` nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="fbd65-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="fbd65-133">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="fbd65-133">**Framework Type.**</span></span> <span data-ttu-id="fbd65-134">Odpovídající typ v .NET Framework je struktura <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fbd65-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd65-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbd65-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="fbd65-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="fbd65-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="fbd65-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="fbd65-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="fbd65-138">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="fbd65-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="fbd65-139">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="fbd65-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="fbd65-140">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="fbd65-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
