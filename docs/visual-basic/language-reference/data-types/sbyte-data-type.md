---
title: SByte – datový typ
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400790"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="66007-102">Datový typ SByte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66007-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="66007-103">Pojme podepsaná 8bitová (1bajtová) celá čísla, která se pohybují v hodnotě od -128 do 127.</span><span class="sxs-lookup"><span data-stu-id="66007-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="66007-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66007-104">Remarks</span></span>

<span data-ttu-id="66007-105">Pomocí `SByte` datového typu můžete obsahovat celočíselné hodnoty, `Integer` které nevyžadují úplnou `Short`šířku dat nebo dokonce poloviční šířku dat aplikace .</span><span class="sxs-lookup"><span data-stu-id="66007-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="66007-106">V některých případech může být běžný jazyk `SByte` runtime schopen pečlivě sbalit proměnné a ušetřit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="66007-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="66007-107">Výchozí hodnota `SByte` je 0.</span><span class="sxs-lookup"><span data-stu-id="66007-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="66007-108">Doslovná přiřazení</span><span class="sxs-lookup"><span data-stu-id="66007-108">Literal assignments</span></span>

<span data-ttu-id="66007-109">Proměnnou `SByte` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.</span><span class="sxs-lookup"><span data-stu-id="66007-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="66007-110">V následujícím příkladu jsou `SByte` hodnoty přiřazeny celá čísla rovnácí -102, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.</span><span class="sxs-lookup"><span data-stu-id="66007-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="66007-111">Tento příklad vyžaduje kompilaci `/removeintchecks` s přepínačem kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="66007-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="66007-112">Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="66007-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="66007-113">Desetinné literály nemají předponu.</span><span class="sxs-lookup"><span data-stu-id="66007-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="66007-114">Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="66007-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="66007-115">Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="66007-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="66007-116">Například:</span><span class="sxs-lookup"><span data-stu-id="66007-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="66007-117">Pokud celé číslo literál je `SByte` mimo rozsah (to znamená, <xref:System.SByte.MinValue?displayProperty=nameWithType> pokud <xref:System.SByte.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="66007-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="66007-118">Pokud celé číslo literálu nemá příponu, [integer](integer-data-type.md) je odvozen.</span><span class="sxs-lookup"><span data-stu-id="66007-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="66007-119">Pokud celé číslo literál je mimo `Integer` rozsah typu, [Long](long-data-type.md) je odvozen.</span><span class="sxs-lookup"><span data-stu-id="66007-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="66007-120">To znamená, že v předchozích příkladech `0x9A` číselné literály a `0b10011010` jsou interpretovány jako 32bitová podepsaná celá <xref:System.SByte.MaxValue?displayProperty=nameWithType>čísla s hodnotou 156, která přesahuje .</span><span class="sxs-lookup"><span data-stu-id="66007-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66007-121">Chcete-li úspěšně zkompilovat kód, jako je tento, `SByte`který přiřadí nedesítkové celé číslo k aplikaci , můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="66007-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="66007-122">Zakázat kontroly celé číslo hranice kompilací s přepínačem kompilátoru. `/removeintchecks`</span><span class="sxs-lookup"><span data-stu-id="66007-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="66007-123">Znak [typu](../../programming-guide/language-features/data-types/type-characters.md) slouží k explicitnímu definování hodnoty literálu, kterou chcete přiřadit `SByte`.</span><span class="sxs-lookup"><span data-stu-id="66007-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="66007-124">Následující příklad přiřadí zápornou hodnotu literálu `Short` . `SByte`</span><span class="sxs-lookup"><span data-stu-id="66007-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="66007-125">Všimněte si, že pro záporná čísla musí být nastaven bit vyššího řádu slova nejvyššího řádu číselného literálu.</span><span class="sxs-lookup"><span data-stu-id="66007-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="66007-126">V případě našeho příkladu se jedná o `Short` bit 15 literálové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="66007-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="66007-127">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="66007-127">Programming tips</span></span>

- <span data-ttu-id="66007-128">**Dodržování předpisů CLS.**</span><span class="sxs-lookup"><span data-stu-id="66007-128">**CLS Compliance.**</span></span> <span data-ttu-id="66007-129">Datový `SByte` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.</span><span class="sxs-lookup"><span data-stu-id="66007-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="66007-130">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="66007-130">**Widening.**</span></span> <span data-ttu-id="66007-131">Datový `SByte` typ se `Short`rozšiřuje `Integer` `Long`na `Decimal` `Single`, `Double`, , , a .</span><span class="sxs-lookup"><span data-stu-id="66007-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="66007-132">To znamená, `SByte` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="66007-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="66007-133">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="66007-133">**Type Characters.**</span></span> <span data-ttu-id="66007-134">`SByte`nemá žádný znak literálu typu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="66007-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="66007-135">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="66007-135">**Framework Type.**</span></span> <span data-ttu-id="66007-136">Odpovídající typ v rozhraní .NET <xref:System.SByte?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="66007-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="66007-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="66007-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="66007-138">Datové typy</span><span class="sxs-lookup"><span data-stu-id="66007-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="66007-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="66007-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="66007-140">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="66007-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="66007-141">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="66007-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="66007-142">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="66007-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="66007-143">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="66007-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="66007-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="66007-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
