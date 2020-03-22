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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400783"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="c58ac-102">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="c58ac-102">UInteger data type</span></span>

<span data-ttu-id="c58ac-103">Obsahuje nepodepsaná 32bitová (4bajtová) celá čísla v hodnotě od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="c58ac-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="c58ac-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c58ac-104">Remarks</span></span>

<span data-ttu-id="c58ac-105">Datový `UInteger` typ poskytuje největší nepodepsanou hodnotu v nejefektivnější šířce dat.</span><span class="sxs-lookup"><span data-stu-id="c58ac-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="c58ac-106">Výchozí hodnota `UInteger` je 0.</span><span class="sxs-lookup"><span data-stu-id="c58ac-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="c58ac-107">Doslovná přiřazení</span><span class="sxs-lookup"><span data-stu-id="c58ac-107">Literal assignments</span></span>

<span data-ttu-id="c58ac-108">Proměnnou `UInteger` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.</span><span class="sxs-lookup"><span data-stu-id="c58ac-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="c58ac-109">Pokud celé číslo literál je `UInteger` mimo rozsah (to znamená, <xref:System.UInt32.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt32.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="c58ac-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="c58ac-110">V následujícím příkladu jsou `UInteger` hodnoty přiřazeny celá čísla rovnající se 3 000 000 000, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.</span><span class="sxs-lookup"><span data-stu-id="c58ac-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="c58ac-111">Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="c58ac-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c58ac-112">Desetinné literály nemají předponu.</span><span class="sxs-lookup"><span data-stu-id="c58ac-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c58ac-113">Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c58ac-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="c58ac-114">Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="c58ac-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c58ac-115">Například:</span><span class="sxs-lookup"><span data-stu-id="c58ac-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c58ac-116">Číselné literály mohou `UI` `ui` také obsahovat znak `UInteger` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c58ac-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="c58ac-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="c58ac-117">Programming tips</span></span>

<span data-ttu-id="c58ac-118">Datové `UInteger` `Integer` typy a poskytují optimální výkon na 32bitovém procesoru,`UShort` `Short`protože `Byte`menší `SByte`celočíselné typy ( , , , a ), i když používají méně bitů, zabere více času na načtení, uložení a načtení.</span><span class="sxs-lookup"><span data-stu-id="c58ac-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="c58ac-119">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-119">**Negative Numbers.**</span></span> <span data-ttu-id="c58ac-120">Protože `UInteger` je nepodepsaný typ, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="c58ac-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="c58ac-121">Pokud použijete unární`-`minus ( ) operátor pro `UInteger`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Long` první.</span><span class="sxs-lookup"><span data-stu-id="c58ac-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="c58ac-122">**Dodržování předpisů CLS.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-122">**CLS Compliance.**</span></span> <span data-ttu-id="c58ac-123">Datový `UInteger` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.</span><span class="sxs-lookup"><span data-stu-id="c58ac-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="c58ac-124">**Interop úvahy.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-124">**Interop Considerations.**</span></span> <span data-ttu-id="c58ac-125">Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní .NET Framework, například Automation nebo COM objekty, mějte na paměti, že typy, jako `uint` je například může mít jinou šířku dat (16 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="c58ac-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="c58ac-126">Pokud předáváte 16bitový argument takové součásti, `UShort` deklarujte jej jako místo ve spravovaném `UInteger` kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c58ac-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="c58ac-127">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-127">**Widening.**</span></span> <span data-ttu-id="c58ac-128">Datový `UInteger` typ se `Long`rozšiřuje `ULong` `Decimal`na `Single`, `Double`, , a .</span><span class="sxs-lookup"><span data-stu-id="c58ac-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="c58ac-129">To znamená, `UInteger` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="c58ac-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="c58ac-130">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-130">**Type Characters.**</span></span> <span data-ttu-id="c58ac-131">Připojení znaků `UI` literálu typu k literálu `UInteger` vynutí na datový typ.</span><span class="sxs-lookup"><span data-stu-id="c58ac-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="c58ac-132">`UInteger`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="c58ac-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="c58ac-133">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="c58ac-133">**Framework Type.**</span></span> <span data-ttu-id="c58ac-134">Odpovídající typ v rozhraní .NET <xref:System.UInt32?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="c58ac-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c58ac-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c58ac-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="c58ac-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c58ac-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c58ac-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="c58ac-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c58ac-138">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="c58ac-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="c58ac-139">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="c58ac-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="c58ac-140">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="c58ac-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
