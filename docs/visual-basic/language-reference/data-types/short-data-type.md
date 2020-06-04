---
title: Short – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415554"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="b5c1c-102">Short – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c1c-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="b5c1c-103">Obsahuje 16bitová celá čísla se znaménkem (2 bajty), která mají rozsah hodnot od-32 768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5c1c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5c1c-104">Remarks</span></span>  

 <span data-ttu-id="b5c1c-105">`Short`Datový typ použijte k omezení celočíselných hodnot, které nevyžadují plnou šířku dat `Integer` .</span><span class="sxs-lookup"><span data-stu-id="b5c1c-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="b5c1c-106">V některých případech může modul CLR (Common Language Runtime) sbalit `Short` proměnné společně a ušetřit spotřebu paměti.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="b5c1c-107">Výchozí hodnota `Short` je 0.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="b5c1c-108">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="b5c1c-108">Literal assignments</span></span>

<span data-ttu-id="b5c1c-109">Můžete deklarovat a inicializovat `Short` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="b5c1c-110">Pokud je celočíselný literál mimo rozsah `Short` (tj. Pokud je menší <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="b5c1c-111">V následujícím příkladu jsou celá čísla rovnající se 1 034, která jsou reprezentována jako Desítková, šestnáctková a binární literála, implicitně převedena z [celého čísla](integer-data-type.md) na `Short` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="b5c1c-112">Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b5c1c-113">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b5c1c-114">Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="b5c1c-115">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b5c1c-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b5c1c-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b5c1c-117">Číselné literály mohou také obsahovat `S` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , který označuje `Short` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="b5c1c-118">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="b5c1c-118">Programming tips</span></span>

- <span data-ttu-id="b5c1c-119">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="b5c1c-119">**Widening.**</span></span> <span data-ttu-id="b5c1c-120">`Short`Datový typ se rozšíří na `Integer` ,, `Long` , `Decimal` `Single` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="b5c1c-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="b5c1c-121">To znamená, že můžete převést `Short` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="b5c1c-122">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="b5c1c-122">**Type Characters.**</span></span> <span data-ttu-id="b5c1c-123">Připojení znaku literálového typu `S` k literálu vynutí tento `Short` datový typ.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="b5c1c-124">`Short`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="b5c1c-125">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="b5c1c-125">**Framework Type.**</span></span> <span data-ttu-id="b5c1c-126">Odpovídající typ v .NET Framework je <xref:System.Int16?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="b5c1c-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c1c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5c1c-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="b5c1c-128">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b5c1c-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="b5c1c-129">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="b5c1c-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="b5c1c-130">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="b5c1c-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="b5c1c-131">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="b5c1c-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="b5c1c-132">Long – datový typ</span><span class="sxs-lookup"><span data-stu-id="b5c1c-132">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="b5c1c-133">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b5c1c-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
