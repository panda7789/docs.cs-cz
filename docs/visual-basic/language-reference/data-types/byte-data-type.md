---
title: Byte – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400741"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="a9000-102">Datový typ bajtů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9000-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="a9000-103">Obsahuje nepodepsaná 8bitová (1bajtová) celá čísla, která se pohybují v hodnotě od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="a9000-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9000-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9000-104">Remarks</span></span>

<span data-ttu-id="a9000-105">Pomocí `Byte` datového typu můžete obsahovat binární data.</span><span class="sxs-lookup"><span data-stu-id="a9000-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="a9000-106">Výchozí hodnota `Byte` je 0.</span><span class="sxs-lookup"><span data-stu-id="a9000-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="a9000-107">Doslovná přiřazení</span><span class="sxs-lookup"><span data-stu-id="a9000-107">Literal assignments</span></span>

<span data-ttu-id="a9000-108">Proměnnou `Byte` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.</span><span class="sxs-lookup"><span data-stu-id="a9000-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a9000-109">Pokud integrální literál `Byte` je mimo rozsah (to <xref:System.Byte.MinValue?displayProperty=nameWithType> znamená, <xref:System.Byte.MaxValue?displayProperty=nameWithType>pokud je menší nebo větší než ) dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="a9000-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="a9000-110">V následujícím příkladu jsou celá čísla rovna 201, která jsou reprezentována jako desetinné, šestnáctkové a binární literály, implicitně převedeny z [Integer](integer-data-type.md) na `byte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a9000-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="a9000-111">Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="a9000-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a9000-112">Desetinné literály nemají předponu.</span><span class="sxs-lookup"><span data-stu-id="a9000-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a9000-113">Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a9000-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="a9000-114">Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="a9000-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a9000-115">Například:</span><span class="sxs-lookup"><span data-stu-id="a9000-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="a9000-116">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="a9000-116">Programming tips</span></span>

- <span data-ttu-id="a9000-117">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="a9000-117">**Negative Numbers.**</span></span> <span data-ttu-id="a9000-118">Protože `Byte` je nepodepsaný typ, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="a9000-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="a9000-119">Pokud použijete unární`-`minus ( ) operátor pro `Byte`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Short` první.</span><span class="sxs-lookup"><span data-stu-id="a9000-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="a9000-120">**Převody formátu.**</span><span class="sxs-lookup"><span data-stu-id="a9000-120">**Format Conversions.**</span></span> <span data-ttu-id="a9000-121">Při čtení nebo zápisu souborů v jazyce Visual Basic nebo při volání knihoven DLL, metod a vlastností může automaticky převést mezi formáty dat.</span><span class="sxs-lookup"><span data-stu-id="a9000-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="a9000-122">Binární data `Byte` uložená v proměnných a polích jsou zachována během těchto převodů formátu.</span><span class="sxs-lookup"><span data-stu-id="a9000-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="a9000-123">Pro binární data `String` byste neměli používat proměnnou, protože její obsah může být poškozen během převodu mezi formáty ANSI a Unicode.</span><span class="sxs-lookup"><span data-stu-id="a9000-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="a9000-124">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="a9000-124">**Widening.**</span></span> <span data-ttu-id="a9000-125">Datový `Byte` typ se `Short`rozšiřuje `UShort` `Integer`na `UInteger` `Long`, `ULong` `Decimal`, `Single`, `Double`, , , , , , nebo .</span><span class="sxs-lookup"><span data-stu-id="a9000-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="a9000-126">To znamená, `Byte` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="a9000-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="a9000-127">**Zadejte znaky.**</span><span class="sxs-lookup"><span data-stu-id="a9000-127">**Type Characters.**</span></span> <span data-ttu-id="a9000-128">`Byte`nemá žádný znak literálu typu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a9000-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="a9000-129">**Typ rámce.**</span><span class="sxs-lookup"><span data-stu-id="a9000-129">**Framework Type.**</span></span> <span data-ttu-id="a9000-130">Odpovídající typ v rozhraní .NET <xref:System.Byte?displayProperty=nameWithType> Framework je struktura.</span><span class="sxs-lookup"><span data-stu-id="a9000-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="a9000-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9000-131">Example</span></span>

 <span data-ttu-id="a9000-132">V následujícím příkladu `b` `Byte` je proměnná.</span><span class="sxs-lookup"><span data-stu-id="a9000-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="a9000-133">Příkazy ukazují rozsah proměnné a použití operátorů bitového posunu na něj.</span><span class="sxs-lookup"><span data-stu-id="a9000-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="a9000-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9000-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="a9000-135">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a9000-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a9000-136">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="a9000-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a9000-137">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="a9000-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a9000-138">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="a9000-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
