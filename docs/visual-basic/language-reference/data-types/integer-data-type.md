---
title: "Integer – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="183e0-102">Integer – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="183e0-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="183e0-103">Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="183e0-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="183e0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="183e0-104">Remarks</span></span>
 <span data-ttu-id="183e0-105">`Integer` Datový typ poskytuje optimální výkon procesoru 32-bit.</span><span class="sxs-lookup"><span data-stu-id="183e0-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="183e0-106">Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.</span><span class="sxs-lookup"><span data-stu-id="183e0-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="183e0-107">Výchozí hodnota `Integer` je 0.</span><span class="sxs-lookup"><span data-stu-id="183e0-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="183e0-108">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="183e0-108">Literal assignments</span></span>

<span data-ttu-id="183e0-109">Můžete deklarace a inicializace `Integer` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="183e0-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="183e0-110">Pokud literálu celé číslo je mimo rozsah `Integer` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="183e0-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="183e0-111">V následujícím příkladu, celá čísla rovno 16,342, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `Integer` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="183e0-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="183e0-112">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="183e0-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="183e0-113">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="183e0-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="183e0-114">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="183e0-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="183e0-115">Číselné literály může také obsahovat `I` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `Integer` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="183e0-115">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a><span data-ttu-id="183e0-116">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="183e0-116">Programming tips</span></span>

-   <span data-ttu-id="183e0-117">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="183e0-117">**Interop Considerations.**</span></span> <span data-ttu-id="183e0-118">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework, jako je například objekty automatizace nebo COM, nezapomeňte, že `Integer` má odlišné datové šířku (16 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="183e0-118">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="183e0-119">Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `Short` místo `Integer` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="183e0-119">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="183e0-120">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="183e0-120">**Widening.**</span></span> <span data-ttu-id="183e0-121">`Integer` Datový typ rozšiřuje na `Long`, `Decimal`, `Single`, nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="183e0-121">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="183e0-122">To znamená, že můžete převést `Integer` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="183e0-122">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="183e0-123">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="183e0-123">**Type Characters.**</span></span> <span data-ttu-id="183e0-124">Připojování znak typu literálu `I` k literál vynutí, aby `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="183e0-124">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="183e0-125">Připojování znak typu identifikátoru `%` na všechny identifikátor vynutí jeho `Integer`.</span><span class="sxs-lookup"><span data-stu-id="183e0-125">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="183e0-126">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="183e0-126">**Framework Type.**</span></span> <span data-ttu-id="183e0-127">Typ odpovídající v rozhraní .NET Framework je <xref:System.Int32?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="183e0-127">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="183e0-128">Rozsah</span><span class="sxs-lookup"><span data-stu-id="183e0-128">Range</span></span>

<span data-ttu-id="183e0-129">Pokud se pokusíte nastavit proměnnou celočíselného typu na číslo, které není v rozsahu tohoto typu, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="183e0-129">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="183e0-130">Pokud se ji pokusíte nastavit na zlomek, bude číslo zaokrouhleno nahoru nebo dolů na nejbližší celočíselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="183e0-130">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="183e0-131">Pokud je číslo stejně vzdáleno od dvou celočíselných hodnot, je hodnota zaokrouhlena nejbližší sudé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="183e0-131">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="183e0-132">Toto chování minimalizuje zaokrouhlovací chyby, které vznikají při konzistentním zaokrouhlování střední hodnoty v jednom směru.</span><span class="sxs-lookup"><span data-stu-id="183e0-132">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="183e0-133">Následující kód znázorňuje příklady zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="183e0-133">The following code shows examples of rounding.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="183e0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="183e0-134">See also</span></span>

<span data-ttu-id="183e0-135"><xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="183e0-135"><xref:System.Int32?displayProperty=nameWithType></span></span>   
 [<span data-ttu-id="183e0-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="183e0-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="183e0-137">Long – datový typ</span><span class="sxs-lookup"><span data-stu-id="183e0-137">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="183e0-138">Short – datový typ</span><span class="sxs-lookup"><span data-stu-id="183e0-138">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="183e0-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="183e0-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="183e0-140">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="183e0-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="183e0-141">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="183e0-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
