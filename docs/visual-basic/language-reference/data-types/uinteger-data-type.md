---
title: "UInteger – datový typ"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3852bd56d11c19e327e6c2f3e23cfb082a54e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="uinteger-data-type"></a><span data-ttu-id="03a44-102">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="03a44-102">UInteger data type</span></span>

<span data-ttu-id="03a44-103">(Blokování nepodepsaných 32-bit 4bajtový) typ Integer v rozmezí od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="03a44-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03a44-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03a44-104">Remarks</span></span>

 <span data-ttu-id="03a44-105">`UInteger` Datový typ poskytuje největší hodnotu bez znaménka nejúčinnější šířku data.</span><span class="sxs-lookup"><span data-stu-id="03a44-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="03a44-106">Výchozí hodnota `UInteger` je 0.</span><span class="sxs-lookup"><span data-stu-id="03a44-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="03a44-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="03a44-107">Literal assignments</span></span>

<span data-ttu-id="03a44-108">Můžete deklarace a inicializace `UInteger` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="03a44-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="03a44-109">Pokud literálu celé číslo je mimo rozsah `UInteger` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="03a44-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="03a44-110">V následujícím příkladu, celá čísla rovno 3,000,000,000, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `UInteger` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="03a44-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="03a44-111">Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál.</span><span class="sxs-lookup"><span data-stu-id="03a44-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="03a44-112">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="03a44-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="03a44-113">Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="03a44-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="03a44-114">Číselné literály může také obsahovat `UI` nebo `ui` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `UInteger` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="03a44-114">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="03a44-115">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="03a44-115">Programming tips</span></span>

 <span data-ttu-id="03a44-116">`UInteger` a `Integer` datové typy poskytnout optimální výkon procesoru 32-bit, protože menší typy celého čísla (`UShort`, `Short`, `Byte`, a `SByte`), i když používají méně bits trvat déle načtení, uložení a načtení.</span><span class="sxs-lookup"><span data-stu-id="03a44-116">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="03a44-117">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="03a44-117">**Negative Numbers.**</span></span> <span data-ttu-id="03a44-118">Protože `UInteger` je typ bez znaménka, nelze ho představují záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="03a44-118">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="03a44-119">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UInteger`, Visual Basic Převede výraz, který se `Long` první.</span><span class="sxs-lookup"><span data-stu-id="03a44-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="03a44-120">**Souladu se specifikací CLS.**</span><span class="sxs-lookup"><span data-stu-id="03a44-120">**CLS Compliance.**</span></span> <span data-ttu-id="03a44-121">`UInteger` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.</span><span class="sxs-lookup"><span data-stu-id="03a44-121">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="03a44-122">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="03a44-122">**Interop Considerations.**</span></span> <span data-ttu-id="03a44-123">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, které typy, jako `uint` může mít různé datové šířka (16 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="03a44-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="03a44-124">Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03a44-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="03a44-125">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="03a44-125">**Widening.**</span></span> <span data-ttu-id="03a44-126">`UInteger` Datový typ rozšiřuje na `Long`, `ULong`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="03a44-126">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="03a44-127">To znamená, že můžete převést `UInteger` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="03a44-127">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="03a44-128">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="03a44-128">**Type Characters.**</span></span> <span data-ttu-id="03a44-129">Připojování znaky typu literálu `UI` k literál vynutí, aby `UInteger` datového typu.</span><span class="sxs-lookup"><span data-stu-id="03a44-129">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="03a44-130">`UInteger`nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="03a44-130">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="03a44-131">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="03a44-131">**Framework Type.**</span></span> <span data-ttu-id="03a44-132">Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt32?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="03a44-132">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a44-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a44-133">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="03a44-134">Datové typy</span><span class="sxs-lookup"><span data-stu-id="03a44-134">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="03a44-135">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="03a44-135">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="03a44-136">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="03a44-136">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="03a44-137">Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="03a44-137">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="03a44-138">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="03a44-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
