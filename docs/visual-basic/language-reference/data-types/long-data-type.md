---
title: Long – datový typ
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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415593"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="c5bb3-102">Long – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5bb3-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="c5bb3-103">Obsahuje podepsaná 64 (8bitové) celá čísla v rozmezí hodnot od-9223372036854775808 do 9 223 372 036 854 775 807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="c5bb3-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="c5bb3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5bb3-104">Remarks</span></span>

<span data-ttu-id="c5bb3-105">Použijte `Long` datový typ obsahující celá čísla, která jsou příliš velká, aby se vešla do `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="c5bb3-106">Výchozí hodnota `Long` je 0.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="c5bb3-107">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="c5bb3-107">Literal assignments</span></span>

<span data-ttu-id="c5bb3-108">Můžete deklarovat a inicializovat `Long` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="c5bb3-109">Pokud je celočíselný literál mimo rozsah `Long` (tj. Pokud je menší <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="c5bb3-110">V následujícím příkladu jsou celá čísla rovna 4 294 967 296, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `Long` hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="c5bb3-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c5bb3-112">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c5bb3-113">Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="c5bb3-114">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c5bb3-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5bb3-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c5bb3-116">Číselné literály mohou také obsahovat `L` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , který označuje `Long` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="c5bb3-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="c5bb3-117">Programming tips</span></span>

- <span data-ttu-id="c5bb3-118">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="c5bb3-118">**Interop Considerations.**</span></span> <span data-ttu-id="c5bb3-119">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že `Long` má v jiných prostředích jinou šířku dat (32 bitů).</span><span class="sxs-lookup"><span data-stu-id="c5bb3-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="c5bb3-120">Pokud předáte 32 argument pro takovou komponentu, deklarujte ji jako `Integer` místo `Long` v novém Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="c5bb3-121">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="c5bb3-121">**Widening.**</span></span> <span data-ttu-id="c5bb3-122">`Long`Datový typ se rozšíří na `Decimal` , `Single` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="c5bb3-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="c5bb3-123">To znamená, že můžete převést `Long` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="c5bb3-124">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="c5bb3-124">**Type Characters.**</span></span> <span data-ttu-id="c5bb3-125">Připojení znaku literálového typu `L` k literálu vynutí tento `Long` datový typ.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="c5bb3-126">Připojení znaku typu identifikátoru `&` k jakémukoli identifikátoru vynutí `Long` .</span><span class="sxs-lookup"><span data-stu-id="c5bb3-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="c5bb3-127">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="c5bb3-127">**Framework Type.**</span></span> <span data-ttu-id="c5bb3-128">Odpovídající typ v .NET Framework je <xref:System.Int64?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="c5bb3-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5bb3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5bb3-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="c5bb3-130">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c5bb3-130">Data Types</span></span>](index.md)
- [<span data-ttu-id="c5bb3-131">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5bb3-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="c5bb3-132">Short – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5bb3-132">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="c5bb3-133">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="c5bb3-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="c5bb3-134">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="c5bb3-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="c5bb3-135">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="c5bb3-135">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
