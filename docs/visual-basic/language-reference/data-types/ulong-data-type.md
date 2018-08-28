---
title: ULong – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214243f6a8a87f4e4cc15f31be23275fff00d07d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998927"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="202fb-102">Ulong – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="202fb-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="202fb-103">Obsahuje bez znaménka 64bitová (8 bajtů) celá čísla v rozmezí od 0 do 18,446,744,073,709,551,615 (více než 1.84 časy 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="202fb-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="202fb-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="202fb-104">Remarks</span></span>

<span data-ttu-id="202fb-105">Použití `ULong` datový typ obsahující binární data jsou příliš velká pro `UInteger`, nebo unsigned nejvyšší možné celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="202fb-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="202fb-106">Výchozí hodnota `ULong` je 0.</span><span class="sxs-lookup"><span data-stu-id="202fb-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="202fb-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="202fb-107">Literal assignments</span></span>

<span data-ttu-id="202fb-108">Můžete deklarovat a inicializovat `ULong` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="202fb-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="202fb-109">Pokud celočíselný literál je mimo rozsah `ULong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="202fb-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="202fb-110">V následujícím příkladu celých čísel je rovno 7,934,076,125, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `ULong` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="202fb-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="202fb-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální.</span><span class="sxs-lookup"><span data-stu-id="202fb-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="202fb-112">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="202fb-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="202fb-113">Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="202fb-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="202fb-114">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="202fb-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="202fb-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="202fb-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="202fb-116">Číselné literály může také zahrnovat `UL` nebo `ul` [znak](../../programming-guide\language-features\data-types/type-characters.md) k označení `ULong` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="202fb-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="202fb-117">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="202fb-117">Programming tips</span></span>
  
-   <span data-ttu-id="202fb-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="202fb-118">**Negative Numbers.**</span></span> <span data-ttu-id="202fb-119">Protože `ULong` typ bez znaménka, je ho nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="202fb-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="202fb-120">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `ULong`, Visual Basic Převede výraz, který má `Decimal` první.</span><span class="sxs-lookup"><span data-stu-id="202fb-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="202fb-121">**Dodržování specifikace CLS.**</span><span class="sxs-lookup"><span data-stu-id="202fb-121">**CLS Compliance.**</span></span> <span data-ttu-id="202fb-122">`ULong` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="202fb-122">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="202fb-123">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="202fb-123">**Interop Considerations.**</span></span> <span data-ttu-id="202fb-124">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy, jako `ulong` může mít v jiných prostředích odlišnou datovou šířku (32bitová verze).</span><span class="sxs-lookup"><span data-stu-id="202fb-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="202fb-125">Pokud takové součásti předáváte 32-bit argument, deklarujte ho jako `UInteger` místo `ULong` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="202fb-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="202fb-126">Kromě toho automatizace nepodporuje 64bitová celá čísla na Windows 95, Windows 98, Windows ME nebo Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="202fb-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="202fb-127">V jazyce Visual Basic nelze předat `ULong` argument pro komponentu služby Automation na těchto platformách.</span><span class="sxs-lookup"><span data-stu-id="202fb-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="202fb-128">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="202fb-128">**Widening.**</span></span> <span data-ttu-id="202fb-129">`ULong` Datový typ rozšiřuje na `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="202fb-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="202fb-130">To znamená, že můžete převést `ULong` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="202fb-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="202fb-131">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="202fb-131">**Type Characters.**</span></span> <span data-ttu-id="202fb-132">Přidávání znaky literálového typu `UL` k literálu se z něj stane `ULong` datového typu.</span><span class="sxs-lookup"><span data-stu-id="202fb-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="202fb-133">`ULong` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="202fb-133">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="202fb-134">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="202fb-134">**Framework Type.**</span></span> <span data-ttu-id="202fb-135">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.UInt64?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="202fb-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202fb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="202fb-136">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="202fb-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="202fb-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="202fb-138">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="202fb-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="202fb-139">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="202fb-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="202fb-140">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="202fb-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="202fb-141">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="202fb-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
