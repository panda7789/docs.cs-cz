---
title: UInteger – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
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
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343892"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="1059e-102">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="1059e-102">UInteger data type</span></span>

<span data-ttu-id="1059e-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span><span class="sxs-lookup"><span data-stu-id="1059e-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="1059e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1059e-104">Remarks</span></span>

<span data-ttu-id="1059e-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span><span class="sxs-lookup"><span data-stu-id="1059e-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="1059e-106">The default value of `UInteger` is 0.</span><span class="sxs-lookup"><span data-stu-id="1059e-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="1059e-107">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="1059e-107">Literal assignments</span></span>

<span data-ttu-id="1059e-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="1059e-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1059e-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span><span class="sxs-lookup"><span data-stu-id="1059e-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1059e-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span><span class="sxs-lookup"><span data-stu-id="1059e-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="1059e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="1059e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1059e-112">Decimal literals have no prefix.</span><span class="sxs-lookup"><span data-stu-id="1059e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1059e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="1059e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="1059e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="1059e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1059e-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1059e-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1059e-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="1059e-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="1059e-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="1059e-117">Programming tips</span></span>

<span data-ttu-id="1059e-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span><span class="sxs-lookup"><span data-stu-id="1059e-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="1059e-119">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="1059e-119">**Negative Numbers.**</span></span> <span data-ttu-id="1059e-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span><span class="sxs-lookup"><span data-stu-id="1059e-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1059e-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span><span class="sxs-lookup"><span data-stu-id="1059e-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="1059e-122">**CLS Compliance.**</span><span class="sxs-lookup"><span data-stu-id="1059e-122">**CLS Compliance.**</span></span> <span data-ttu-id="1059e-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span><span class="sxs-lookup"><span data-stu-id="1059e-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="1059e-124">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="1059e-124">**Interop Considerations.**</span></span> <span data-ttu-id="1059e-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span><span class="sxs-lookup"><span data-stu-id="1059e-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="1059e-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="1059e-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="1059e-127">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="1059e-127">**Widening.**</span></span> <span data-ttu-id="1059e-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="1059e-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1059e-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="1059e-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="1059e-130">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="1059e-130">**Type Characters.**</span></span> <span data-ttu-id="1059e-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span><span class="sxs-lookup"><span data-stu-id="1059e-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="1059e-132">`UInteger` has no identifier type character.</span><span class="sxs-lookup"><span data-stu-id="1059e-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="1059e-133">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="1059e-133">**Framework Type.**</span></span> <span data-ttu-id="1059e-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span><span class="sxs-lookup"><span data-stu-id="1059e-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1059e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1059e-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="1059e-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="1059e-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="1059e-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="1059e-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="1059e-138">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="1059e-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="1059e-139">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="1059e-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="1059e-140">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="1059e-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
