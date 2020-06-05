---
title: Byte – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374314"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="82dc1-102">Byte – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82dc1-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="82dc1-103">Obsahuje nepodepsaná 8bitové (1 bajt) celá čísla, která mají rozsah hodnot od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="82dc1-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="82dc1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82dc1-104">Remarks</span></span>

<span data-ttu-id="82dc1-105">`Byte`Datový typ použijte k zahrnutí binárních dat.</span><span class="sxs-lookup"><span data-stu-id="82dc1-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="82dc1-106">Výchozí hodnota `Byte` je 0.</span><span class="sxs-lookup"><span data-stu-id="82dc1-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="82dc1-107">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="82dc1-107">Literal assignments</span></span>

<span data-ttu-id="82dc1-108">Můžete deklarovat a inicializovat `Byte` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="82dc1-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="82dc1-109">Pokud je celočíselný literál mimo rozsah a `Byte` (tj. Pokud je menší <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="82dc1-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="82dc1-110">V následujícím příkladu jsou celá čísla rovnající se 201, která jsou reprezentována jako Desítková, šestnáctková a binární literála, implicitně převedena z [celého čísla](integer-data-type.md) na `byte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="82dc1-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="82dc1-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="82dc1-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="82dc1-112">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="82dc1-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="82dc1-113">Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="82dc1-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="82dc1-114">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="82dc1-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="82dc1-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="82dc1-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="82dc1-116">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="82dc1-116">Programming tips</span></span>

- <span data-ttu-id="82dc1-117">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="82dc1-117">**Negative Numbers.**</span></span> <span data-ttu-id="82dc1-118">Protože `Byte` je typ bez znaménka, nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="82dc1-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="82dc1-119">Použijete-li unární operátor mínus ( `-` ) u výrazu, který je vyhodnocen jako typ `Byte` , Visual Basic výraz převede na `Short` první.</span><span class="sxs-lookup"><span data-stu-id="82dc1-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="82dc1-120">**Převody formátu.**</span><span class="sxs-lookup"><span data-stu-id="82dc1-120">**Format Conversions.**</span></span> <span data-ttu-id="82dc1-121">Když Visual Basic čte nebo zapisuje soubory nebo když volá knihovny DLL, metody a vlastnosti, může automaticky převádět mezi formáty dat.</span><span class="sxs-lookup"><span data-stu-id="82dc1-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="82dc1-122">Binární data uložená v `Byte` proměnných a polích jsou během těchto převodů formátu zachovaná.</span><span class="sxs-lookup"><span data-stu-id="82dc1-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="82dc1-123">`String`Pro binární data byste neměli používat proměnnou, protože její obsah může být během konverze mezi formáty ANSI a Unicode poškozen.</span><span class="sxs-lookup"><span data-stu-id="82dc1-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="82dc1-124">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="82dc1-124">**Widening.**</span></span> <span data-ttu-id="82dc1-125">`Byte`Datový typ se rozšíří na `Short` ,, `UShort` , `Integer` `UInteger` , `Long` , `ULong` , `Decimal` , `Single` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="82dc1-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="82dc1-126">To znamená, že můžete převést `Byte` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="82dc1-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="82dc1-127">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="82dc1-127">**Type Characters.**</span></span> <span data-ttu-id="82dc1-128">`Byte`nemá žádný znak typu literálu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="82dc1-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="82dc1-129">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="82dc1-129">**Framework Type.**</span></span> <span data-ttu-id="82dc1-130">Odpovídající typ v .NET Framework je <xref:System.Byte?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="82dc1-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="82dc1-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="82dc1-131">Example</span></span>

 <span data-ttu-id="82dc1-132">V následujícím příkladu `b` je `Byte` Proměnná.</span><span class="sxs-lookup"><span data-stu-id="82dc1-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="82dc1-133">Příkazy ukazují rozsah proměnné a aplikaci operátorů bitových posunutí na ni.</span><span class="sxs-lookup"><span data-stu-id="82dc1-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="82dc1-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="82dc1-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="82dc1-135">Datové typy</span><span class="sxs-lookup"><span data-stu-id="82dc1-135">Data Types</span></span>](index.md)
- [<span data-ttu-id="82dc1-136">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="82dc1-136">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="82dc1-137">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="82dc1-137">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="82dc1-138">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="82dc1-138">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
