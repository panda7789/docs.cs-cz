---
title: "UShort – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="ba954-102">Ushort – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba954-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="ba954-103">(Blokování nepodepsaných 16bitové 2bajtový) typ Integer v rozmezí od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="ba954-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba954-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba954-104">Remarks</span></span>

 <span data-ttu-id="ba954-105">Použití `UShort` datový typ tak, aby obsahovala binární data příliš velké vzhledem k `Byte`.</span><span class="sxs-lookup"><span data-stu-id="ba954-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="ba954-106">Výchozí hodnota `UShort` je 0.</span><span class="sxs-lookup"><span data-stu-id="ba954-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="ba954-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="ba954-107">Literal assignments</span></span>

<span data-ttu-id="ba954-108">Můžete deklarace a inicializace `UShort` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="ba954-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ba954-109">Pokud literálu celé číslo je mimo rozsah `UShort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="ba954-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ba954-110">V následujícím příkladu, celá čísla rovno 65,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `UShort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ba954-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="ba954-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="ba954-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ba954-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="ba954-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ba954-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="ba954-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="ba954-114">Číselné literály může také obsahovat `US` nebo `us` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `UShort` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ba954-114">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a><span data-ttu-id="ba954-115">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="ba954-115">Programming tips</span></span>
  
-   <span data-ttu-id="ba954-116">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="ba954-116">**Negative Numbers.**</span></span> <span data-ttu-id="ba954-117">Protože `UShort` je typ bez znaménka, nelze ho představují záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="ba954-117">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ba954-118">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UShort`, Visual Basic Převede výraz, který se `Integer` první.</span><span class="sxs-lookup"><span data-stu-id="ba954-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="ba954-119">**Souladu se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="ba954-119">**CLS Compliance.**</span></span> <span data-ttu-id="ba954-120">`UShort` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.</span><span class="sxs-lookup"><span data-stu-id="ba954-120">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="ba954-121">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="ba954-121">**Widening.**</span></span> <span data-ttu-id="ba954-122">`UShort` Datový typ rozšiřuje na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="ba954-122">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ba954-123">To znamená, že můžete převést `UShort` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="ba954-123">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="ba954-124">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="ba954-124">**Type Characters.**</span></span> <span data-ttu-id="ba954-125">Připojování znaky typu literálu `US` k literál vynutí, aby `UShort` datového typu.</span><span class="sxs-lookup"><span data-stu-id="ba954-125">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="ba954-126">`UShort`nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ba954-126">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="ba954-127">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="ba954-127">**Framework Type.**</span></span> <span data-ttu-id="ba954-128">Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt16?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="ba954-128">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba954-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba954-129">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="ba954-130">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ba954-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="ba954-131">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ba954-131">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ba954-132">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="ba954-132">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="ba954-133">Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="ba954-133">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="ba954-134">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="ba954-134">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
