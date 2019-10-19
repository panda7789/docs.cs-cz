---
title: ULong – datový typ (Visual Basic)
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
ms.openlocfilehash: 19a75f056436b858a22588d7ac5f37df5dd326f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583116"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="b1807-102">ULong – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1807-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="b1807-103">Obsahuje nepodepsaná 64 (8 bajtů) celých čísel v rozsahu od 0 do 18446744073709551615 (více než 1,84 krát 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="b1807-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="b1807-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1807-104">Remarks</span></span>

<span data-ttu-id="b1807-105">Datový typ `ULong` použijte k zahrnutí binárních dat, která jsou pro `UInteger` příliš velká, nebo největší možné hodnoty unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="b1807-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="b1807-106">Výchozí hodnota `ULong` je 0.</span><span class="sxs-lookup"><span data-stu-id="b1807-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="b1807-107">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="b1807-107">Literal assignments</span></span>

<span data-ttu-id="b1807-108">Můžete deklarovat a inicializovat `ULong` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="b1807-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="b1807-109">Pokud je celočíselný literál mimo rozsah `ULong` (to znamená, pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="b1807-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="b1807-110">V následujícím příkladu jsou celá čísla rovna 7 934 076 125, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `ULong` hodnot.</span><span class="sxs-lookup"><span data-stu-id="b1807-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="b1807-111">Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="b1807-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b1807-112">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="b1807-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b1807-113">Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_` jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b1807-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="b1807-114">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="b1807-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b1807-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1807-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b1807-116">Číselné literály mohou také zahrnovat `UL` nebo `ul` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení `ULong` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b1807-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="b1807-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="b1807-117">Programming tips</span></span>

- <span data-ttu-id="b1807-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="b1807-118">**Negative Numbers.**</span></span> <span data-ttu-id="b1807-119">Vzhledem k tomu, že `ULong` je typ bez znaménka, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="b1807-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="b1807-120">Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `ULong`, Visual Basic výraz převede na `Decimal` jako první.</span><span class="sxs-lookup"><span data-stu-id="b1807-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="b1807-121">**Kompatibilita se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="b1807-121">**CLS Compliance.**</span></span> <span data-ttu-id="b1807-122">@No__t_0 datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="b1807-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="b1807-123">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="b1807-123">**Interop Considerations.**</span></span> <span data-ttu-id="b1807-124">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy jako `ulong` mohou mít v jiných prostředích jinou šířku dat (32 bitů).</span><span class="sxs-lookup"><span data-stu-id="b1807-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="b1807-125">Pokud předáváte 32 argument pro takovou komponentu, deklarujte ji jako `UInteger` místo `ULong` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b1807-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="b1807-126">Kromě toho Automation nepodporuje 64 celých čísel v systémech Windows 95, Windows 98, Windows MILLENNIUM nebo Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="b1807-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="b1807-127">Do komponenty automatizace na těchto platformách nelze předat Visual Basic `ULong` argument.</span><span class="sxs-lookup"><span data-stu-id="b1807-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="b1807-128">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="b1807-128">**Widening.**</span></span> <span data-ttu-id="b1807-129">@No__t_0 datový typ se rozšíří na `Decimal`, `Single` a `Double`.</span><span class="sxs-lookup"><span data-stu-id="b1807-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b1807-130">To znamená, že můžete převést `ULong` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1807-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="b1807-131">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="b1807-131">**Type Characters.**</span></span> <span data-ttu-id="b1807-132">Připojení znaků literálového typu `UL` k literálu vynutí tento datový typ `ULong`.</span><span class="sxs-lookup"><span data-stu-id="b1807-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="b1807-133">`ULong` nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b1807-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="b1807-134">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="b1807-134">**Framework Type.**</span></span> <span data-ttu-id="b1807-135">Odpovídající typ v .NET Framework je struktura <xref:System.UInt64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1807-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1807-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1807-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="b1807-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b1807-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b1807-138">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="b1807-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b1807-139">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="b1807-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b1807-140">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="b1807-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="b1807-141">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b1807-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
