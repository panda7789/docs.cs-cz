---
title: Procedury operátoru
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: b395f5fcf1b89bb49e55e207c4910e95f2aae69d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346000"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="fd691-102">Procedury operátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd691-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="fd691-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span><span class="sxs-lookup"><span data-stu-id="fd691-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="fd691-104">This is also called *operator overloading*.</span><span class="sxs-lookup"><span data-stu-id="fd691-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="fd691-105">When to Define Operator Procedures</span><span class="sxs-lookup"><span data-stu-id="fd691-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="fd691-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="fd691-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span><span class="sxs-lookup"><span data-stu-id="fd691-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="fd691-108">To do this, it must be an operand of an operator.</span><span class="sxs-lookup"><span data-stu-id="fd691-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="fd691-109">Visual Basic defines operators only on its fundamental data types.</span><span class="sxs-lookup"><span data-stu-id="fd691-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="fd691-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="fd691-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd691-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="fd691-112">Types of Operator Procedure</span><span class="sxs-lookup"><span data-stu-id="fd691-112">Types of Operator Procedure</span></span>

<span data-ttu-id="fd691-113">An operator procedure can be one of the following types:</span><span class="sxs-lookup"><span data-stu-id="fd691-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="fd691-114">A definition of a unary operator where the argument is of the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="fd691-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="fd691-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="fd691-117">A definition of a conversion operator that returns the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="fd691-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span><span class="sxs-lookup"><span data-stu-id="fd691-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="fd691-119">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="fd691-119">Declaration Syntax</span></span>

<span data-ttu-id="fd691-120">The syntax for declaring an operator procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="fd691-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="fd691-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span><span class="sxs-lookup"><span data-stu-id="fd691-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="fd691-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span><span class="sxs-lookup"><span data-stu-id="fd691-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="fd691-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span><span class="sxs-lookup"><span data-stu-id="fd691-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="fd691-124">All operands must be declared `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="fd691-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="fd691-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fd691-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="fd691-126">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fd691-126">Data Type</span></span>

<span data-ttu-id="fd691-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="fd691-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span><span class="sxs-lookup"><span data-stu-id="fd691-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="fd691-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd691-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="fd691-130">Calling Syntax</span><span class="sxs-lookup"><span data-stu-id="fd691-130">Calling Syntax</span></span>

<span data-ttu-id="fd691-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span><span class="sxs-lookup"><span data-stu-id="fd691-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="fd691-132">You supply the operands the same way you do for predefined operators.</span><span class="sxs-lookup"><span data-stu-id="fd691-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="fd691-133">The syntax for an implicit call to an operator procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="fd691-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="fd691-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="fd691-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="fd691-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span><span class="sxs-lookup"><span data-stu-id="fd691-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="fd691-136">Illustration of Declaration and Call</span><span class="sxs-lookup"><span data-stu-id="fd691-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="fd691-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span><span class="sxs-lookup"><span data-stu-id="fd691-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="fd691-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span><span class="sxs-lookup"><span data-stu-id="fd691-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="fd691-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="fd691-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="fd691-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd691-140">See also</span></span>

- [<span data-ttu-id="fd691-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="fd691-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fd691-142">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="fd691-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="fd691-143">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="fd691-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="fd691-144">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fd691-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="fd691-145">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="fd691-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fd691-146">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="fd691-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="fd691-147">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="fd691-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="fd691-148">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="fd691-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fd691-149">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="fd691-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="fd691-150">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="fd691-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
