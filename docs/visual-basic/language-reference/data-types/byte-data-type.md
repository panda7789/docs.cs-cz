---
title: Byte – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: e1725b709c03b0d77cf7e28761396236b5ef1a00
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622433"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="0445d-102">Byte – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0445d-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="0445d-103">Obsahuje 8 bitů (1bajtový) celá čísla bez znaménka, které v rozsahu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="0445d-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="0445d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0445d-104">Remarks</span></span>

<span data-ttu-id="0445d-105">Použití `Byte` datový typ binární data obsahovat.</span><span class="sxs-lookup"><span data-stu-id="0445d-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="0445d-106">Výchozí hodnota `Byte` je 0.</span><span class="sxs-lookup"><span data-stu-id="0445d-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="0445d-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="0445d-107">Literal assignments</span></span>

<span data-ttu-id="0445d-108">Můžete deklarovat a inicializovat `Byte` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="0445d-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0445d-109">Pokud celočíselný literál je mimo rozsah `Byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="0445d-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="0445d-110">V následujícím příkladu celých čísel je rovno 201, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [celé číslo](integer-data-type.md) k `byte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0445d-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="0445d-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální.</span><span class="sxs-lookup"><span data-stu-id="0445d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0445d-112">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="0445d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0445d-113">Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="0445d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="0445d-114">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="0445d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0445d-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0445d-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="0445d-116">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="0445d-116">Programming tips</span></span>

- <span data-ttu-id="0445d-117">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="0445d-117">**Negative Numbers.**</span></span> <span data-ttu-id="0445d-118">Protože `Byte` typ bez znaménka, je ho nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="0445d-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="0445d-119">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `Byte`, Visual Basic Převede výraz, který má `Short` první.</span><span class="sxs-lookup"><span data-stu-id="0445d-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="0445d-120">**Převody formátů.**</span><span class="sxs-lookup"><span data-stu-id="0445d-120">**Format Conversions.**</span></span> <span data-ttu-id="0445d-121">Když jazyka Visual Basic čte nebo zapisuje soubory nebo při volání knihovny DLL, metody a vlastnosti, můžete automaticky převádět mezi datových formátů.</span><span class="sxs-lookup"><span data-stu-id="0445d-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="0445d-122">Binární data uložená v `Byte` proměnných a polí se zachovají během tyto převody formátů.</span><span class="sxs-lookup"><span data-stu-id="0445d-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="0445d-123">Neměli byste používat `String` proměnné pro binární data, protože jeho obsah může být poškozen při převodu mezi formáty ANSI a Unicode.</span><span class="sxs-lookup"><span data-stu-id="0445d-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="0445d-124">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="0445d-124">**Widening.**</span></span> <span data-ttu-id="0445d-125">`Byte` Datový typ rozšiřuje na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="0445d-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0445d-126">To znamená, že můžete převést `Byte` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="0445d-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="0445d-127">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="0445d-127">**Type Characters.**</span></span> <span data-ttu-id="0445d-128">`Byte` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="0445d-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="0445d-129">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="0445d-129">**Framework Type.**</span></span> <span data-ttu-id="0445d-130">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Byte?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="0445d-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="0445d-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="0445d-131">Example</span></span>

 <span data-ttu-id="0445d-132">V následujícím příkladu `b` je `Byte` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0445d-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="0445d-133">Příkazy ukazují rozsah proměnné a do něj aplikaci bitové posunutí – operátory.</span><span class="sxs-lookup"><span data-stu-id="0445d-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="0445d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0445d-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="0445d-135">Datové typy</span><span class="sxs-lookup"><span data-stu-id="0445d-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0445d-136">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="0445d-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0445d-137">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="0445d-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0445d-138">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="0445d-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
