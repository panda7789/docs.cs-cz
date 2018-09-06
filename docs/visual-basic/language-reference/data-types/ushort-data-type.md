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
ms.openlocfilehash: 038aad2c41f655d0699dab33df276132a70e3ede
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036009"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="a27ed-102">Ushort – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a27ed-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="a27ed-103">Blokování 16 bitů (2bajtových) celá čísla bez znaménka v rozmezí od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="a27ed-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27ed-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a27ed-104">Remarks</span></span>

 <span data-ttu-id="a27ed-105">Použití `UShort` datový typ obsahující binární data jsou příliš velká pro `Byte`.</span><span class="sxs-lookup"><span data-stu-id="a27ed-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="a27ed-106">Výchozí hodnota `UShort` je 0.</span><span class="sxs-lookup"><span data-stu-id="a27ed-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="a27ed-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="a27ed-107">Literal assignments</span></span>

<span data-ttu-id="a27ed-108">Můžete deklarovat a inicializovat `UShort` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="a27ed-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a27ed-109">Pokud celočíselný literál je mimo rozsah `UShort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="a27ed-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="a27ed-110">V následujícím příkladu celých čísel je rovno 65,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `UShort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a27ed-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="a27ed-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální.</span><span class="sxs-lookup"><span data-stu-id="a27ed-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a27ed-112">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="a27ed-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a27ed-113">Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="a27ed-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="a27ed-114">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="a27ed-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a27ed-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a27ed-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="a27ed-116">Číselné literály může také zahrnovat `US` nebo `us` [znak](../../programming-guide\language-features\data-types/type-characters.md) k označení `UShort` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a27ed-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="a27ed-117">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="a27ed-117">Programming tips</span></span>
  
-   <span data-ttu-id="a27ed-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="a27ed-118">**Negative Numbers.**</span></span> <span data-ttu-id="a27ed-119">Protože `UShort` typ bez znaménka, je ho nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="a27ed-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="a27ed-120">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UShort`, Visual Basic Převede výraz, který má `Integer` první.</span><span class="sxs-lookup"><span data-stu-id="a27ed-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="a27ed-121">**Dodržování specifikace CLS.**</span><span class="sxs-lookup"><span data-stu-id="a27ed-121">**CLS Compliance.**</span></span> <span data-ttu-id="a27ed-122">`UShort` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="a27ed-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="a27ed-123">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="a27ed-123">**Widening.**</span></span> <span data-ttu-id="a27ed-124">`UShort` Datový typ rozšiřuje na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="a27ed-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="a27ed-125">To znamená, že můžete převést `UShort` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="a27ed-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="a27ed-126">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="a27ed-126">**Type Characters.**</span></span> <span data-ttu-id="a27ed-127">Přidávání znaky literálového typu `US` k literálu se z něj stane `UShort` datového typu.</span><span class="sxs-lookup"><span data-stu-id="a27ed-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="a27ed-128">`UShort` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a27ed-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="a27ed-129">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="a27ed-129">**Framework Type.**</span></span> <span data-ttu-id="a27ed-130">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.UInt16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="a27ed-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27ed-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a27ed-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="a27ed-132">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a27ed-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="a27ed-133">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="a27ed-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="a27ed-134">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="a27ed-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="a27ed-135">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="a27ed-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="a27ed-136">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="a27ed-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
