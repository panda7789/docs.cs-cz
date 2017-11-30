---
title: "ULong – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ulong
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc52bfd16541feed599d5445adad7aba04f8e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="32fdf-102">Ulong – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32fdf-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="32fdf-103">Ukládání nepodepsané celých čísel 64-bit (8 bajtů), v rozmezí od 0 prostřednictvím 18,446,744,073,709,551,615 (více než 1.84 výskyty 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="32fdf-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32fdf-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32fdf-104">Remarks</span></span>

<span data-ttu-id="32fdf-105">Použití `ULong` datový typ tak, aby obsahovala binární data příliš velké vzhledem k `UInteger`, nebo největší možné nepodepsané celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32fdf-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="32fdf-106">Výchozí hodnota `ULong` je 0.</span><span class="sxs-lookup"><span data-stu-id="32fdf-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="32fdf-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="32fdf-107">Literal assignments</span></span>

<span data-ttu-id="32fdf-108">Můžete deklarace a inicializace `ULong` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="32fdf-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="32fdf-109">Pokud literálu celé číslo je mimo rozsah `ULong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="32fdf-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="32fdf-110">V následujícím příkladu, celá čísla rovno 7,934,076,125, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `ULong` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32fdf-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="32fdf-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="32fdf-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="32fdf-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="32fdf-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="32fdf-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="32fdf-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="32fdf-114">Číselné literály může také obsahovat `UL` nebo `ul` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `ULong` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="32fdf-114">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="32fdf-115">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="32fdf-115">Programming tips</span></span>
  
-   <span data-ttu-id="32fdf-116">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-116">**Negative Numbers.**</span></span> <span data-ttu-id="32fdf-117">Protože `ULong` je typ bez znaménka, nelze ho představují záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="32fdf-117">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="32fdf-118">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `ULong`, Visual Basic Převede výraz, který se `Decimal` první.</span><span class="sxs-lookup"><span data-stu-id="32fdf-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="32fdf-119">**Souladu se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-119">**CLS Compliance.**</span></span> <span data-ttu-id="32fdf-120">`ULong` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.</span><span class="sxs-lookup"><span data-stu-id="32fdf-120">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="32fdf-121">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-121">**Interop Considerations.**</span></span> <span data-ttu-id="32fdf-122">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, které typy, jako `ulong` může mít různé datové šířka (32bitová verze) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="32fdf-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="32fdf-123">32-bit argument předáte pro tyto součásti, deklarujte ji jako `UInteger` místo `ULong` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32fdf-123">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="32fdf-124">Kromě toho automatizace nepodporuje 64bitových celých čísel na systém Windows 95, Windows 98, Windows ME nebo Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="32fdf-124">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="32fdf-125">Nelze předat jazyka Visual Basic `ULong` argument pro komponentu automatizace na těchto platformách.</span><span class="sxs-lookup"><span data-stu-id="32fdf-125">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="32fdf-126">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-126">**Widening.**</span></span> <span data-ttu-id="32fdf-127">`ULong` Datový typ rozšiřuje na `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="32fdf-127">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="32fdf-128">To znamená, že můžete převést `ULong` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="32fdf-128">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="32fdf-129">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-129">**Type Characters.**</span></span> <span data-ttu-id="32fdf-130">Připojování znaky typu literálu `UL` k literál vynutí, aby `ULong` datového typu.</span><span class="sxs-lookup"><span data-stu-id="32fdf-130">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="32fdf-131">`ULong`nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="32fdf-131">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="32fdf-132">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="32fdf-132">**Framework Type.**</span></span> <span data-ttu-id="32fdf-133">Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt64?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="32fdf-133">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fdf-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="32fdf-134">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="32fdf-135">Datové typy</span><span class="sxs-lookup"><span data-stu-id="32fdf-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="32fdf-136">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="32fdf-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="32fdf-137">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="32fdf-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="32fdf-138">Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="32fdf-138">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="32fdf-139">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="32fdf-139">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
