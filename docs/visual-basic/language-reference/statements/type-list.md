---
title: Seznam typů
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 3f2aaa65293ed2bcc6c8eeb4bd77e49907d93425
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352778"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="70996-102">Seznam typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70996-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="70996-103">Specifies the *type parameters* for a *generic* programming element.</span><span class="sxs-lookup"><span data-stu-id="70996-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="70996-104">Multiple parameters are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="70996-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="70996-105">Following is the syntax for one type parameter.</span><span class="sxs-lookup"><span data-stu-id="70996-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="70996-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70996-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="70996-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="70996-107">Parts</span></span>

|<span data-ttu-id="70996-108">Termín</span><span class="sxs-lookup"><span data-stu-id="70996-108">Term</span></span>|<span data-ttu-id="70996-109">Definice</span><span class="sxs-lookup"><span data-stu-id="70996-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="70996-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="70996-110">Optional.</span></span> <span data-ttu-id="70996-111">Can be used only in generic interfaces and delegates.</span><span class="sxs-lookup"><span data-stu-id="70996-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="70996-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="70996-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="70996-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="70996-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="70996-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="70996-114">Required.</span></span> <span data-ttu-id="70996-115">Name of the type parameter.</span><span class="sxs-lookup"><span data-stu-id="70996-115">Name of the type parameter.</span></span> <span data-ttu-id="70996-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span><span class="sxs-lookup"><span data-stu-id="70996-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="70996-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="70996-117">Optional.</span></span> <span data-ttu-id="70996-118">List of requirements that constrain the data type that can be supplied for `typename`.</span><span class="sxs-lookup"><span data-stu-id="70996-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="70996-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span><span class="sxs-lookup"><span data-stu-id="70996-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="70996-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="70996-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="70996-121">You use `As` only once, at the beginning of the list.</span><span class="sxs-lookup"><span data-stu-id="70996-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70996-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70996-122">Remarks</span></span>

<span data-ttu-id="70996-123">Every generic programming element must take at least one type parameter.</span><span class="sxs-lookup"><span data-stu-id="70996-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="70996-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span><span class="sxs-lookup"><span data-stu-id="70996-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="70996-125">You can define a generic class, structure, interface, procedure, or delegate.</span><span class="sxs-lookup"><span data-stu-id="70996-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="70996-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="70996-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="70996-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="70996-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="70996-128">Rules</span><span class="sxs-lookup"><span data-stu-id="70996-128">Rules</span></span>

- <span data-ttu-id="70996-129">**Parentheses.**</span><span class="sxs-lookup"><span data-stu-id="70996-129">**Parentheses.**</span></span> <span data-ttu-id="70996-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="70996-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="70996-131">You use `Of` only once, at the beginning of the list.</span><span class="sxs-lookup"><span data-stu-id="70996-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="70996-132">**Constraints.**</span><span class="sxs-lookup"><span data-stu-id="70996-132">**Constraints.**</span></span> <span data-ttu-id="70996-133">A list of *constraints* on a type parameter can include the following items in any combination:</span><span class="sxs-lookup"><span data-stu-id="70996-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="70996-134">Any number of interfaces.</span><span class="sxs-lookup"><span data-stu-id="70996-134">Any number of interfaces.</span></span> <span data-ttu-id="70996-135">The supplied type must implement every interface in this list.</span><span class="sxs-lookup"><span data-stu-id="70996-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="70996-136">At most one class.</span><span class="sxs-lookup"><span data-stu-id="70996-136">At most one class.</span></span> <span data-ttu-id="70996-137">The supplied type must inherit from that class.</span><span class="sxs-lookup"><span data-stu-id="70996-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="70996-138">The `New` keyword.</span><span class="sxs-lookup"><span data-stu-id="70996-138">The `New` keyword.</span></span> <span data-ttu-id="70996-139">The supplied type must expose a parameterless constructor that your generic type can access.</span><span class="sxs-lookup"><span data-stu-id="70996-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="70996-140">This is useful if you constrain a type parameter by one or more interfaces.</span><span class="sxs-lookup"><span data-stu-id="70996-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="70996-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span><span class="sxs-lookup"><span data-stu-id="70996-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="70996-142">Either the `Class` keyword or the `Structure` keyword.</span><span class="sxs-lookup"><span data-stu-id="70996-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="70996-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span><span class="sxs-lookup"><span data-stu-id="70996-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="70996-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span><span class="sxs-lookup"><span data-stu-id="70996-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="70996-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="70996-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="70996-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="70996-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="70996-147">Constraints on each type parameter are independent of constraints on other type parameters.</span><span class="sxs-lookup"><span data-stu-id="70996-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="70996-148">Behavior</span><span class="sxs-lookup"><span data-stu-id="70996-148">Behavior</span></span>

- <span data-ttu-id="70996-149">**Compile-Time Substitution.**</span><span class="sxs-lookup"><span data-stu-id="70996-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="70996-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span><span class="sxs-lookup"><span data-stu-id="70996-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="70996-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span><span class="sxs-lookup"><span data-stu-id="70996-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="70996-152">**Absence of Constraints.**</span><span class="sxs-lookup"><span data-stu-id="70996-152">**Absence of Constraints.**</span></span> <span data-ttu-id="70996-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span><span class="sxs-lookup"><span data-stu-id="70996-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="70996-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="70996-154">Example</span></span>

<span data-ttu-id="70996-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span><span class="sxs-lookup"><span data-stu-id="70996-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="70996-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="70996-156">Example</span></span>

<span data-ttu-id="70996-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span><span class="sxs-lookup"><span data-stu-id="70996-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="70996-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span><span class="sxs-lookup"><span data-stu-id="70996-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="70996-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="70996-159">Example</span></span>

<span data-ttu-id="70996-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span><span class="sxs-lookup"><span data-stu-id="70996-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="70996-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70996-161">See also</span></span>

- [<span data-ttu-id="70996-162">Of</span><span class="sxs-lookup"><span data-stu-id="70996-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="70996-163">Operátor New</span><span class="sxs-lookup"><span data-stu-id="70996-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="70996-164">Access levels in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70996-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="70996-165">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="70996-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="70996-166">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="70996-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="70996-167">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="70996-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="70996-168">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="70996-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="70996-169">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="70996-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="70996-170">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="70996-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="70996-171">In</span><span class="sxs-lookup"><span data-stu-id="70996-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="70996-172">Out</span><span class="sxs-lookup"><span data-stu-id="70996-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
