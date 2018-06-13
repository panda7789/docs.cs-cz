---
title: UShort – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 520c21d4df5c340b41a8b1e9055b3fadddfdf6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590365"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="b5ec3-102">Ushort – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5ec3-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="b5ec3-103">(Blokování nepodepsaných 16bitové 2bajtový) typ Integer v rozmezí od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5ec3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5ec3-104">Remarks</span></span>

 <span data-ttu-id="b5ec3-105">Použití `UShort` datový typ tak, aby obsahovala binární data příliš velké vzhledem k `Byte`.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="b5ec3-106">Výchozí hodnota `UShort` je 0.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="b5ec3-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="b5ec3-107">Literal assignments</span></span>

<span data-ttu-id="b5ec3-108">Můžete deklarace a inicializace `UShort` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="b5ec3-109">Pokud literálu celé číslo je mimo rozsah `UShort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="b5ec3-110">V následujícím příkladu, celá čísla rovno 65,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `UShort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="b5ec3-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b5ec3-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b5ec3-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="b5ec3-114">Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b5ec3-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b5ec3-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b5ec3-116">Číselné literály může také obsahovat `US` nebo `us` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `UShort` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="b5ec3-117">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="b5ec3-117">Programming tips</span></span>
  
-   <span data-ttu-id="b5ec3-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="b5ec3-118">**Negative Numbers.**</span></span> <span data-ttu-id="b5ec3-119">Protože `UShort` je typ bez znaménka, nelze ho představují záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="b5ec3-120">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UShort`, Visual Basic Převede výraz, který se `Integer` první.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="b5ec3-121">**Souladu se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="b5ec3-121">**CLS Compliance.**</span></span> <span data-ttu-id="b5ec3-122">`UShort` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="b5ec3-123">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="b5ec3-123">**Widening.**</span></span> <span data-ttu-id="b5ec3-124">`UShort` Datový typ rozšiřuje na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b5ec3-125">To znamená, že můžete převést `UShort` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="b5ec3-126">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="b5ec3-126">**Type Characters.**</span></span> <span data-ttu-id="b5ec3-127">Připojování znaky typu literálu `US` k literál vynutí, aby `UShort` datového typu.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="b5ec3-128">`UShort` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="b5ec3-129">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="b5ec3-129">**Framework Type.**</span></span> <span data-ttu-id="b5ec3-130">Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt16?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="b5ec3-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ec3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5ec3-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="b5ec3-132">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b5ec3-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b5ec3-133">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="b5ec3-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="b5ec3-134">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="b5ec3-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="b5ec3-135">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="b5ec3-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="b5ec3-136">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b5ec3-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
