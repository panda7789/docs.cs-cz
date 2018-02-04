---
title: "SByte – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d391d7eea27ec7696dbb4c28da8916c744712f32
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="b8ddf-102">SByte – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8ddf-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="b8ddf-103">Blokování podepsaná celá čísla 8bitové (1bajtů), které pohybovat v rozmezí -128 do 127.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8ddf-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8ddf-104">Remarks</span></span>

<span data-ttu-id="b8ddf-105">Použití `SByte` datový typ tak, aby obsahovala celé číslo hodnoty, které nevyžadují šířku úplná data `Integer` nebo dokonce šířku poloviční data `Short`.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="b8ddf-106">V některých případech může být modul common language runtime moct pack vaší `SByte` proměnné úzce spolupracují a uložte využití paměti.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="b8ddf-107">Výchozí hodnota `SByte` je 0.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="b8ddf-108">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="b8ddf-108">Literal assignments</span></span>
  
<span data-ttu-id="b8ddf-109">Můžete deklarace a inicializace `SByte` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="b8ddf-110">V následujícím příkladu, celá čísla rovno-102, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `SByte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="b8ddf-111">Tento příklad vyžaduje, aby kompilujete s `/removeintchecks` přepínače kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="b8ddf-112">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b8ddf-113">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b8ddf-114">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="b8ddf-115">Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b8ddf-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b8ddf-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b8ddf-117">Pokud literálu celé číslo je mimo rozsah `SByte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="b8ddf-118">Když celé literál bez přípony, [celé číslo](integer-data-type.md) je odvodit.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="b8ddf-119">Pokud literálu celé číslo je mimo rozsah `Integer` typ, [dlouho](long-data-type.md) je odvodit.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="b8ddf-120">To znamená, že v předchozích příkladech číselné literály `0x9A` a `0b10011010` se interpretují jako 32bitová podepsaná celá čísla s hodnotou 156, který přesahuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8ddf-121">Úspěšně zkompilovat kód jako to, který přiřazuje celé číslo bez desetinných k `SByte`, můžete provést jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b8ddf-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="b8ddf-122">Kompilování pomocí zakázat kontroly rozsah celých čísel `/removeintchecks` přepínače kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="b8ddf-123">Použití [znak typu](../../programming-guide\language-features\data-types/type-characters.md) explicitně definujte literálovou hodnotou, kterou chcete přiřadit `SByte`.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-123">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="b8ddf-124">Následující příklad přiřadí záporné literál `Short` hodnotu `SByte`.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="b8ddf-125">Všimněte si, že pro záporná čísla, musíte nastavit vysokou bitem aplikace word horní z číselný literál.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="b8ddf-126">V případě našem příkladu to je bit 15 literálové `Short` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="b8ddf-127">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="b8ddf-127">Programming tips</span></span>
  
-   <span data-ttu-id="b8ddf-128">**Souladu se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="b8ddf-128">**CLS Compliance.**</span></span> <span data-ttu-id="b8ddf-129">`SByte` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-129">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="b8ddf-130">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="b8ddf-130">**Widening.**</span></span> <span data-ttu-id="b8ddf-131">`SByte` Datový typ rozšiřuje na `Short`, `Integer`, `Long`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b8ddf-132">To znamená, že můžete převést `SByte` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="b8ddf-133">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="b8ddf-133">**Type Characters.**</span></span> <span data-ttu-id="b8ddf-134">`SByte`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-134">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="b8ddf-135">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="b8ddf-135">**Framework Type.**</span></span> <span data-ttu-id="b8ddf-136">Typ odpovídající v rozhraní .NET Framework je <xref:System.SByte?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="b8ddf-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b8ddf-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8ddf-137">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="b8ddf-138">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b8ddf-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b8ddf-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="b8ddf-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="b8ddf-140">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="b8ddf-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="b8ddf-141">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="b8ddf-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="b8ddf-142">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="b8ddf-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="b8ddf-143">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="b8ddf-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="b8ddf-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b8ddf-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
