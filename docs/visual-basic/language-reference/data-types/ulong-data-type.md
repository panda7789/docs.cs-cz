---
title: ULong – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400699"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="6a21e-102">Datový typ ULong (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a21e-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="6a21e-103">Obsahuje nepodepsaná 64bitová (8bajtová) celá čísla v hodnotě od 0 do 18 446 744 073 709 551 615 (více než 1,84krát 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="6a21e-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="6a21e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a21e-104">Remarks</span></span>

<span data-ttu-id="6a21e-105">`ULong` Datový typ slouží k tomu, `UInteger`aby obsahoval binární data příliš velká pro nebo největší možné hodnoty nepodepsaných celého čísla.</span><span class="sxs-lookup"><span data-stu-id="6a21e-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="6a21e-106">Výchozí hodnota `ULong` je 0.</span><span class="sxs-lookup"><span data-stu-id="6a21e-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="6a21e-107">Doslovná přiřazení</span><span class="sxs-lookup"><span data-stu-id="6a21e-107">Literal assignments</span></span>

<span data-ttu-id="6a21e-108">Proměnnou `ULong` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.</span><span class="sxs-lookup"><span data-stu-id="6a21e-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6a21e-109">Pokud celé číslo literál je `ULong` mimo rozsah (to znamená, <xref:System.UInt64.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt64.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="6a21e-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6a21e-110">V následujícím příkladu jsou `ULong` hodnoty přiřazeny celá čísla rovnající se 7 934 076 125, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.</span><span class="sxs-lookup"><span data-stu-id="6a21e-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="6a21e-111">Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="6a21e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6a21e-112">Desetinné literály nemají předponu.</span><span class="sxs-lookup"><span data-stu-id="6a21e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6a21e-113">Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6a21e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="6a21e-114">Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="6a21e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6a21e-115">Například:</span><span class="sxs-lookup"><span data-stu-id="6a21e-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6a21e-116">Číselné literály mohou `UL` `ul` také obsahovat znak `ULong` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6a21e-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="6a21e-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="6a21e-117">Programming tips</span></span>

- <span data-ttu-id="6a21e-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-118">**Negative Numbers.**</span></span> <span data-ttu-id="6a21e-119">Protože `ULong` je nepodepsaný typ, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="6a21e-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="6a21e-120">Pokud použijete unární`-`minus ( ) operátor pro `ULong`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Decimal` první.</span><span class="sxs-lookup"><span data-stu-id="6a21e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="6a21e-121">**Dodržování předpisů CLS.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-121">**CLS Compliance.**</span></span> <span data-ttu-id="6a21e-122">Datový `ULong` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.</span><span class="sxs-lookup"><span data-stu-id="6a21e-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="6a21e-123">**Interop úvahy.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-123">**Interop Considerations.**</span></span> <span data-ttu-id="6a21e-124">Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní .NET Framework, například Automation nebo COM objekty, mějte na paměti, že typy, jako `ulong` je například může mít jinou šířku dat (32 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6a21e-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="6a21e-125">Pokud předáváte 32bitový argument takové součásti, `UInteger` deklarujte jej jako místo ve spravovaném `ULong` kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6a21e-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="6a21e-126">Automatizace navíc nepodporuje 64bitová celá čísla v systémech Windows 95, Windows 98, Windows ME nebo Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="6a21e-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="6a21e-127">Argument jazyka Visual `ULong` Basic nelze předat součásti Automation na těchto platformách.</span><span class="sxs-lookup"><span data-stu-id="6a21e-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="6a21e-128">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-128">**Widening.**</span></span> <span data-ttu-id="6a21e-129">Datový `ULong` typ se `Decimal`rozšiřuje `Single`na `Double`, a .</span><span class="sxs-lookup"><span data-stu-id="6a21e-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="6a21e-130">To znamená, `ULong` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="6a21e-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="6a21e-131">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-131">**Type Characters.**</span></span> <span data-ttu-id="6a21e-132">Připojení znaků `UL` literálu typu k literálu `ULong` vynutí na datový typ.</span><span class="sxs-lookup"><span data-stu-id="6a21e-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="6a21e-133">`ULong`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="6a21e-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="6a21e-134">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="6a21e-134">**Framework Type.**</span></span> <span data-ttu-id="6a21e-135">Odpovídající typ v rozhraní .NET <xref:System.UInt64?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="6a21e-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a21e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a21e-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="6a21e-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="6a21e-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6a21e-138">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="6a21e-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6a21e-139">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="6a21e-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="6a21e-140">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="6a21e-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="6a21e-141">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="6a21e-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
