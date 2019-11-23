---
title: CType – funkce
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 18b2d5a28cd6ef885ba8d237da6764dbbd108b59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348098"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="8633e-102">CType – funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8633e-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="8633e-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="8633e-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="8633e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8633e-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="8633e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8633e-105">Parts</span></span>

<span data-ttu-id="8633e-106">`expression` Any valid expression.</span><span class="sxs-lookup"><span data-stu-id="8633e-106">`expression` Any valid expression.</span></span> <span data-ttu-id="8633e-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span><span class="sxs-lookup"><span data-stu-id="8633e-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="8633e-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="8633e-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="8633e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8633e-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="8633e-110">You can also use the following functions to perform a type conversion:</span><span class="sxs-lookup"><span data-stu-id="8633e-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="8633e-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span><span class="sxs-lookup"><span data-stu-id="8633e-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="8633e-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="8633e-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="8633e-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8633e-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="8633e-114">These operators require that one type inherit from or implement the other type.</span><span class="sxs-lookup"><span data-stu-id="8633e-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="8633e-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span><span class="sxs-lookup"><span data-stu-id="8633e-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="8633e-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span><span class="sxs-lookup"><span data-stu-id="8633e-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="8633e-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span><span class="sxs-lookup"><span data-stu-id="8633e-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="8633e-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span><span class="sxs-lookup"><span data-stu-id="8633e-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="8633e-119">If a conversion fails at run time, the appropriate exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="8633e-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="8633e-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span><span class="sxs-lookup"><span data-stu-id="8633e-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="8633e-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span><span class="sxs-lookup"><span data-stu-id="8633e-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="8633e-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span><span class="sxs-lookup"><span data-stu-id="8633e-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="8633e-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span><span class="sxs-lookup"><span data-stu-id="8633e-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="8633e-124">This makes `CType` act as an *overloaded operator*.</span><span class="sxs-lookup"><span data-stu-id="8633e-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="8633e-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span><span class="sxs-lookup"><span data-stu-id="8633e-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="8633e-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="8633e-126">Overloading</span></span>

<span data-ttu-id="8633e-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span><span class="sxs-lookup"><span data-stu-id="8633e-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="8633e-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span><span class="sxs-lookup"><span data-stu-id="8633e-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="8633e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8633e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="8633e-130">Converting Dynamic Objects</span><span class="sxs-lookup"><span data-stu-id="8633e-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="8633e-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span><span class="sxs-lookup"><span data-stu-id="8633e-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="8633e-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span><span class="sxs-lookup"><span data-stu-id="8633e-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="8633e-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="8633e-133">Example</span></span>

<span data-ttu-id="8633e-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span><span class="sxs-lookup"><span data-stu-id="8633e-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="8633e-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8633e-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8633e-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8633e-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="8633e-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="8633e-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8633e-138">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="8633e-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="8633e-139">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="8633e-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="8633e-140">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="8633e-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="8633e-141">Type Conversion in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8633e-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
