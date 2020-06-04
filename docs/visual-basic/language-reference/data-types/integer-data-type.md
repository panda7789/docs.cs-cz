---
title: Integer – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: aa7b64162308d6af2763b29034c5a7276c973876
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415606"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="4c249-102">Celočíselný datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c249-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="4c249-103">Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="4c249-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c249-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c249-104">Remarks</span></span>

 <span data-ttu-id="4c249-105">`Integer`Datový typ poskytuje optimální výkon v 32 procesorech.</span><span class="sxs-lookup"><span data-stu-id="4c249-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="4c249-106">Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.</span><span class="sxs-lookup"><span data-stu-id="4c249-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="4c249-107">Výchozí hodnota `Integer` je 0.</span><span class="sxs-lookup"><span data-stu-id="4c249-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="4c249-108">Přiřazení literálů</span><span class="sxs-lookup"><span data-stu-id="4c249-108">Literal assignments</span></span>

<span data-ttu-id="4c249-109">Můžete deklarovat a inicializovat `Integer` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu.</span><span class="sxs-lookup"><span data-stu-id="4c249-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4c249-110">Pokud je celočíselný literál mimo rozsah `Integer` (tj. Pokud je menší <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="4c249-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4c249-111">V následujícím příkladu jsou celá čísla rovna 90 946, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `Integer` hodnotám.</span><span class="sxs-lookup"><span data-stu-id="4c249-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="4c249-112">Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu.</span><span class="sxs-lookup"><span data-stu-id="4c249-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4c249-113">Desítkové literály nemají žádnou předponu.</span><span class="sxs-lookup"><span data-stu-id="4c249-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4c249-114">Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4c249-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="4c249-115">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="4c249-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4c249-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4c249-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4c249-117">Číselné literály mohou také obsahovat `I` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , který označuje `Integer` datový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4c249-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="4c249-118">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="4c249-118">Programming tips</span></span>

- <span data-ttu-id="4c249-119">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="4c249-119">**Interop Considerations.**</span></span> <span data-ttu-id="4c249-120">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, jako je například automatizace nebo objekty COM, pamatujte, že `Integer` má v jiných prostředích jinou šířku dat (16 bitů).</span><span class="sxs-lookup"><span data-stu-id="4c249-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="4c249-121">Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `Short` místo `Integer` v novém kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4c249-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="4c249-122">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="4c249-122">**Widening.**</span></span> <span data-ttu-id="4c249-123">`Integer`Datový typ se rozšíří na `Long` , `Decimal` , `Single` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="4c249-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="4c249-124">To znamená, že můžete převést `Integer` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="4c249-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="4c249-125">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="4c249-125">**Type Characters.**</span></span> <span data-ttu-id="4c249-126">Připojení znaku literálového typu `I` k literálu vynutí tento `Integer` datový typ.</span><span class="sxs-lookup"><span data-stu-id="4c249-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="4c249-127">Připojení znaku typu identifikátoru `%` k jakémukoli identifikátoru vynutí `Integer` .</span><span class="sxs-lookup"><span data-stu-id="4c249-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="4c249-128">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="4c249-128">**Framework Type.**</span></span> <span data-ttu-id="4c249-129">Odpovídající typ v .NET Framework je <xref:System.Int32?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="4c249-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="4c249-130">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4c249-130">Range</span></span>

<span data-ttu-id="4c249-131">Pokud se pokusíte nastavit proměnnou celočíselného typu na číslo, které není v rozsahu tohoto typu, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="4c249-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="4c249-132">Pokud se ji pokusíte nastavit na zlomek, bude číslo zaokrouhleno nahoru nebo dolů na nejbližší celočíselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4c249-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="4c249-133">Pokud je číslo stejně vzdáleno od dvou celočíselných hodnot, je hodnota zaokrouhlena nejbližší sudé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4c249-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="4c249-134">Toto chování minimalizuje zaokrouhlovací chyby, které vznikají při konzistentním zaokrouhlování střední hodnoty v jednom směru.</span><span class="sxs-lookup"><span data-stu-id="4c249-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="4c249-135">Následující kód znázorňuje příklady zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="4c249-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="4c249-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c249-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="4c249-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4c249-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="4c249-138">Long – datový typ</span><span class="sxs-lookup"><span data-stu-id="4c249-138">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="4c249-139">Short – datový typ</span><span class="sxs-lookup"><span data-stu-id="4c249-139">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="4c249-140">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="4c249-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="4c249-141">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="4c249-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="4c249-142">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="4c249-142">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
