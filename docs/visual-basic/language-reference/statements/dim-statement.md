---
title: Dim – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: ac66ffdba622673ef42017d147c05b2a2733dede
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343759"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="f0c72-102">Dim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0c72-102">Dim Statement (Visual Basic)</span></span>

<span data-ttu-id="f0c72-103">Declares and allocates storage space for one or more variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0c72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0c72-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="f0c72-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f0c72-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="f0c72-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-106">Optional.</span></span> <span data-ttu-id="f0c72-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="f0c72-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-108">Optional.</span></span> <span data-ttu-id="f0c72-109">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="f0c72-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="f0c72-110">Public</span><span class="sxs-lookup"><span data-stu-id="f0c72-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="f0c72-111">Protected</span><span class="sxs-lookup"><span data-stu-id="f0c72-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="f0c72-112">Friend</span><span class="sxs-lookup"><span data-stu-id="f0c72-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="f0c72-113">Private</span><span class="sxs-lookup"><span data-stu-id="f0c72-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="f0c72-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f0c72-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="f0c72-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="f0c72-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="f0c72-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="f0c72-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-117">Optional.</span></span> <span data-ttu-id="f0c72-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="f0c72-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-119">Optional.</span></span> <span data-ttu-id="f0c72-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="f0c72-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-121">Optional.</span></span> <span data-ttu-id="f0c72-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="f0c72-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-123">Optional.</span></span> <span data-ttu-id="f0c72-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>

- `WithEvents`

<span data-ttu-id="f0c72-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-125">Optional.</span></span> <span data-ttu-id="f0c72-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span><span class="sxs-lookup"><span data-stu-id="f0c72-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="f0c72-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="f0c72-128">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f0c72-128">Required.</span></span> <span data-ttu-id="f0c72-129">List of variables being declared in this statement.</span><span class="sxs-lookup"><span data-stu-id="f0c72-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="f0c72-130">Each `variable` has the following syntax and parts:</span><span class="sxs-lookup"><span data-stu-id="f0c72-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="f0c72-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="f0c72-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="f0c72-132">Part</span><span class="sxs-lookup"><span data-stu-id="f0c72-132">Part</span></span>|<span data-ttu-id="f0c72-133">Popis</span><span class="sxs-lookup"><span data-stu-id="f0c72-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="f0c72-134">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f0c72-134">Required.</span></span> <span data-ttu-id="f0c72-135">Name of the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-135">Name of the variable.</span></span> <span data-ttu-id="f0c72-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="f0c72-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-137">Optional.</span></span> <span data-ttu-id="f0c72-138">List of bounds of each dimension of an array variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="f0c72-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-139">Optional.</span></span> <span data-ttu-id="f0c72-140">Creates a new instance of the class when the `Dim` statement runs.</span><span class="sxs-lookup"><span data-stu-id="f0c72-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="f0c72-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-141">Optional.</span></span> <span data-ttu-id="f0c72-142">Data type of the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="f0c72-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-143">Optional.</span></span> <span data-ttu-id="f0c72-144">Introduces the object initializer list.</span><span class="sxs-lookup"><span data-stu-id="f0c72-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="f0c72-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0c72-145">Optional.</span></span> <span data-ttu-id="f0c72-146">The name of a property in the class you are making an instance of.</span><span class="sxs-lookup"><span data-stu-id="f0c72-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="f0c72-147">Required after `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="f0c72-147">Required after `propertyname` =.</span></span> <span data-ttu-id="f0c72-148">The expression that is evaluated and assigned to the property name.</span><span class="sxs-lookup"><span data-stu-id="f0c72-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="f0c72-149">Optional if `New` is not specified.</span><span class="sxs-lookup"><span data-stu-id="f0c72-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="f0c72-150">Expression that is evaluated and assigned to the variable when it is created.</span><span class="sxs-lookup"><span data-stu-id="f0c72-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f0c72-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0c72-151">Remarks</span></span>

<span data-ttu-id="f0c72-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="f0c72-153">The following example declares a variable to hold an `Integer` value.</span><span class="sxs-lookup"><span data-stu-id="f0c72-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="f0c72-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="f0c72-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="f0c72-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span><span class="sxs-lookup"><span data-stu-id="f0c72-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="f0c72-156">If you use `New`, you do not use an initializer expression.</span><span class="sxs-lookup"><span data-stu-id="f0c72-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="f0c72-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="f0c72-158">You can declare a variable in a procedure, block, class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="f0c72-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="f0c72-159">You cannot declare a variable in a source file, namespace, or interface.</span><span class="sxs-lookup"><span data-stu-id="f0c72-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="f0c72-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="f0c72-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span><span class="sxs-lookup"><span data-stu-id="f0c72-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="f0c72-162">Member variables are in scope throughout their class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="f0c72-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="f0c72-163">A variable that is declared at procedure level is a *local variable*.</span><span class="sxs-lookup"><span data-stu-id="f0c72-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="f0c72-164">Local variables are in scope only within their procedure or block.</span><span class="sxs-lookup"><span data-stu-id="f0c72-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="f0c72-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="f0c72-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="f0c72-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="f0c72-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span><span class="sxs-lookup"><span data-stu-id="f0c72-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="f0c72-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="f0c72-170">Specifying an Initial Value</span><span class="sxs-lookup"><span data-stu-id="f0c72-170">Specifying an Initial Value</span></span>

<span data-ttu-id="f0c72-171">You can assign a value to a variable when it is created.</span><span class="sxs-lookup"><span data-stu-id="f0c72-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="f0c72-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="f0c72-173">The expression must evaluate to a constant that can be calculated at compile time.</span><span class="sxs-lookup"><span data-stu-id="f0c72-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="f0c72-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span><span class="sxs-lookup"><span data-stu-id="f0c72-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="f0c72-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span><span class="sxs-lookup"><span data-stu-id="f0c72-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="f0c72-176">In the second declaration, type inference infers the type from the value 3.</span><span class="sxs-lookup"><span data-stu-id="f0c72-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="f0c72-177">Type inference applies at the procedure level.</span><span class="sxs-lookup"><span data-stu-id="f0c72-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="f0c72-178">It does not apply outside a procedure in a class, structure, module, or interface.</span><span class="sxs-lookup"><span data-stu-id="f0c72-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="f0c72-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="f0c72-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span><span class="sxs-lookup"><span data-stu-id="f0c72-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="f0c72-181">You can use an *object initializer* to declare instances of named and anonymous types.</span><span class="sxs-lookup"><span data-stu-id="f0c72-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="f0c72-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span><span class="sxs-lookup"><span data-stu-id="f0c72-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="f0c72-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="f0c72-184">Declaring Multiple Variables</span><span class="sxs-lookup"><span data-stu-id="f0c72-184">Declaring Multiple Variables</span></span>

<span data-ttu-id="f0c72-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span><span class="sxs-lookup"><span data-stu-id="f0c72-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="f0c72-186">Multiple variables are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="f0c72-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="f0c72-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="f0c72-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span><span class="sxs-lookup"><span data-stu-id="f0c72-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="f0c72-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span><span class="sxs-lookup"><span data-stu-id="f0c72-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="f0c72-190">Pole</span><span class="sxs-lookup"><span data-stu-id="f0c72-190">Arrays</span></span>

<span data-ttu-id="f0c72-191">You can declare a variable to hold an *array*, which can hold multiple values.</span><span class="sxs-lookup"><span data-stu-id="f0c72-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="f0c72-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span><span class="sxs-lookup"><span data-stu-id="f0c72-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="f0c72-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="f0c72-194">You can specify the lower and upper bound of each dimension of an array.</span><span class="sxs-lookup"><span data-stu-id="f0c72-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="f0c72-195">To do this, include a `boundslist` inside the parentheses.</span><span class="sxs-lookup"><span data-stu-id="f0c72-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="f0c72-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span><span class="sxs-lookup"><span data-stu-id="f0c72-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="f0c72-197">The lower bound is always zero, whether you specify it or not.</span><span class="sxs-lookup"><span data-stu-id="f0c72-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="f0c72-198">Each index can vary from zero through its upper bound value.</span><span class="sxs-lookup"><span data-stu-id="f0c72-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="f0c72-199">The following two statements are equivalent.</span><span class="sxs-lookup"><span data-stu-id="f0c72-199">The following two statements are equivalent.</span></span> <span data-ttu-id="f0c72-200">Each statement declares an array of 21 `Integer` elements.</span><span class="sxs-lookup"><span data-stu-id="f0c72-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="f0c72-201">When you access the array, the index can vary from 0 through 20.</span><span class="sxs-lookup"><span data-stu-id="f0c72-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="f0c72-202">The following statement declares a two-dimensional array of type `Double`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="f0c72-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span><span class="sxs-lookup"><span data-stu-id="f0c72-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="f0c72-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span><span class="sxs-lookup"><span data-stu-id="f0c72-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="f0c72-205">The length of the dimension is the upper bound plus one.</span><span class="sxs-lookup"><span data-stu-id="f0c72-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="f0c72-206">An array can have from 1 to 32 dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0c72-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="f0c72-207">You can leave all the bounds blank in an array declaration.</span><span class="sxs-lookup"><span data-stu-id="f0c72-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="f0c72-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span><span class="sxs-lookup"><span data-stu-id="f0c72-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="f0c72-209">It has a value of `Nothing` until you initialize at least some of its elements.</span><span class="sxs-lookup"><span data-stu-id="f0c72-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="f0c72-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0c72-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="f0c72-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0c72-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="f0c72-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span><span class="sxs-lookup"><span data-stu-id="f0c72-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="f0c72-213">A variable that holds a zero-length array does not have the value `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="f0c72-214">Zero-length arrays are required by certain common language runtime functions.</span><span class="sxs-lookup"><span data-stu-id="f0c72-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="f0c72-215">If you try to access such an array, a runtime exception occurs.</span><span class="sxs-lookup"><span data-stu-id="f0c72-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="f0c72-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="f0c72-217">You can initialize the values of an array by using an array literal.</span><span class="sxs-lookup"><span data-stu-id="f0c72-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="f0c72-218">To do this, surround the initialization values with braces (`{}`).</span><span class="sxs-lookup"><span data-stu-id="f0c72-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="f0c72-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span><span class="sxs-lookup"><span data-stu-id="f0c72-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="f0c72-220">The elements are specified in row-major order.</span><span class="sxs-lookup"><span data-stu-id="f0c72-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="f0c72-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a> <span data-ttu-id="f0c72-222">Default Data Types and Values</span><span class="sxs-lookup"><span data-stu-id="f0c72-222">Default Data Types and Values</span></span>

<span data-ttu-id="f0c72-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="f0c72-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="f0c72-224">Data type specified?</span><span class="sxs-lookup"><span data-stu-id="f0c72-224">Data type specified?</span></span>|<span data-ttu-id="f0c72-225">Initializer specified?</span><span class="sxs-lookup"><span data-stu-id="f0c72-225">Initializer specified?</span></span>|<span data-ttu-id="f0c72-226">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0c72-226">Example</span></span>|<span data-ttu-id="f0c72-227">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f0c72-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="f0c72-228">Ne</span><span class="sxs-lookup"><span data-stu-id="f0c72-228">No</span></span>|<span data-ttu-id="f0c72-229">Ne</span><span class="sxs-lookup"><span data-stu-id="f0c72-229">No</span></span>|`Dim qty`|<span data-ttu-id="f0c72-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="f0c72-231">If `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="f0c72-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="f0c72-232">Ne</span><span class="sxs-lookup"><span data-stu-id="f0c72-232">No</span></span>|<span data-ttu-id="f0c72-233">Ano</span><span class="sxs-lookup"><span data-stu-id="f0c72-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="f0c72-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span><span class="sxs-lookup"><span data-stu-id="f0c72-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="f0c72-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="f0c72-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="f0c72-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="f0c72-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="f0c72-238">Ano</span><span class="sxs-lookup"><span data-stu-id="f0c72-238">Yes</span></span>|<span data-ttu-id="f0c72-239">Ne</span><span class="sxs-lookup"><span data-stu-id="f0c72-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="f0c72-240">The variable is initialized to the default value for the data type.</span><span class="sxs-lookup"><span data-stu-id="f0c72-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="f0c72-241">See the table later in this section.</span><span class="sxs-lookup"><span data-stu-id="f0c72-241">See the table later in this section.</span></span>|
|<span data-ttu-id="f0c72-242">Ano</span><span class="sxs-lookup"><span data-stu-id="f0c72-242">Yes</span></span>|<span data-ttu-id="f0c72-243">Ano</span><span class="sxs-lookup"><span data-stu-id="f0c72-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="f0c72-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="f0c72-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="f0c72-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span><span class="sxs-lookup"><span data-stu-id="f0c72-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="f0c72-246">The following table shows the default initialization values.</span><span class="sxs-lookup"><span data-stu-id="f0c72-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="f0c72-247">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0c72-247">Data type</span></span>|<span data-ttu-id="f0c72-248">Default value</span><span class="sxs-lookup"><span data-stu-id="f0c72-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="f0c72-249">All numeric types (including `Byte` and `SByte`)</span><span class="sxs-lookup"><span data-stu-id="f0c72-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="f0c72-250">0</span><span class="sxs-lookup"><span data-stu-id="f0c72-250">0</span></span>|
|`Char`|<span data-ttu-id="f0c72-251">Binary 0</span><span class="sxs-lookup"><span data-stu-id="f0c72-251">Binary 0</span></span>|
|<span data-ttu-id="f0c72-252">All reference types (including `Object`, `String`, and all arrays)</span><span class="sxs-lookup"><span data-stu-id="f0c72-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="f0c72-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="f0c72-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="f0c72-254">Each element of a structure is initialized as if it were a separate variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="f0c72-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="f0c72-256">Static Local Variable Lifetime</span><span class="sxs-lookup"><span data-stu-id="f0c72-256">Static Local Variable Lifetime</span></span>

<span data-ttu-id="f0c72-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span><span class="sxs-lookup"><span data-stu-id="f0c72-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="f0c72-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="f0c72-259">Procedure declaration</span><span class="sxs-lookup"><span data-stu-id="f0c72-259">Procedure declaration</span></span>|<span data-ttu-id="f0c72-260">Variable initialized</span><span class="sxs-lookup"><span data-stu-id="f0c72-260">Variable initialized</span></span>|<span data-ttu-id="f0c72-261">Variable stops existing</span><span class="sxs-lookup"><span data-stu-id="f0c72-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="f0c72-262">In a module</span><span class="sxs-lookup"><span data-stu-id="f0c72-262">In a module</span></span>|<span data-ttu-id="f0c72-263">The first time the procedure is called</span><span class="sxs-lookup"><span data-stu-id="f0c72-263">The first time the procedure is called</span></span>|<span data-ttu-id="f0c72-264">When your program stops execution</span><span class="sxs-lookup"><span data-stu-id="f0c72-264">When your program stops execution</span></span>|
|<span data-ttu-id="f0c72-265">In a class or structure, procedure is `Shared`</span><span class="sxs-lookup"><span data-stu-id="f0c72-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="f0c72-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span><span class="sxs-lookup"><span data-stu-id="f0c72-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="f0c72-267">When your program stops execution</span><span class="sxs-lookup"><span data-stu-id="f0c72-267">When your program stops execution</span></span>|
|<span data-ttu-id="f0c72-268">In a class or structure, procedure isn't `Shared`</span><span class="sxs-lookup"><span data-stu-id="f0c72-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="f0c72-269">The first time the procedure is called on a specific instance</span><span class="sxs-lookup"><span data-stu-id="f0c72-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="f0c72-270">When the instance is released for garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="f0c72-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="f0c72-271">Attributes and Modifiers</span><span class="sxs-lookup"><span data-stu-id="f0c72-271">Attributes and Modifiers</span></span>

<span data-ttu-id="f0c72-272">You can apply attributes only to member variables, not to local variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="f0c72-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="f0c72-274">At module level, you cannot use the `Static` modifier to declare member variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="f0c72-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span><span class="sxs-lookup"><span data-stu-id="f0c72-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="f0c72-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="f0c72-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span><span class="sxs-lookup"><span data-stu-id="f0c72-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="f0c72-278">You can adjust their access levels with the access modifiers.</span><span class="sxs-lookup"><span data-stu-id="f0c72-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="f0c72-279">You cannot use access modifiers on local variables (inside a procedure).</span><span class="sxs-lookup"><span data-stu-id="f0c72-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="f0c72-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span><span class="sxs-lookup"><span data-stu-id="f0c72-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="f0c72-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="f0c72-282">You cannot declare an array with `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="f0c72-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="f0c72-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f0c72-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="f0c72-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="f0c72-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span><span class="sxs-lookup"><span data-stu-id="f0c72-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="f0c72-286">Releasing Managed Resources</span><span class="sxs-lookup"><span data-stu-id="f0c72-286">Releasing Managed Resources</span></span>

<span data-ttu-id="f0c72-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span><span class="sxs-lookup"><span data-stu-id="f0c72-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="f0c72-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f0c72-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="f0c72-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span><span class="sxs-lookup"><span data-stu-id="f0c72-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="f0c72-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f0c72-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="f0c72-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span><span class="sxs-lookup"><span data-stu-id="f0c72-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="f0c72-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span><span class="sxs-lookup"><span data-stu-id="f0c72-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="f0c72-293">However, the resource must implement the <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="f0c72-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="f0c72-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0c72-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="f0c72-295">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0c72-295">Example</span></span>

<span data-ttu-id="f0c72-296">The following example declares variables by using the `Dim` statement with various options.</span><span class="sxs-lookup"><span data-stu-id="f0c72-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="f0c72-297">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0c72-297">Example</span></span>

<span data-ttu-id="f0c72-298">The following example lists the prime numbers between 1 and 30.</span><span class="sxs-lookup"><span data-stu-id="f0c72-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="f0c72-299">The scope of local variables is described in code comments.</span><span class="sxs-lookup"><span data-stu-id="f0c72-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="f0c72-300">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0c72-300">Example</span></span>

<span data-ttu-id="f0c72-301">In the following example, the `speedValue` variable is declared at the class level.</span><span class="sxs-lookup"><span data-stu-id="f0c72-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="f0c72-302">The `Private` keyword is used to declare the variable.</span><span class="sxs-lookup"><span data-stu-id="f0c72-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="f0c72-303">The variable can be accessed by any procedure in the `Car` class.</span><span class="sxs-lookup"><span data-stu-id="f0c72-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="f0c72-304">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0c72-304">See also</span></span>

- [<span data-ttu-id="f0c72-305">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="f0c72-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="f0c72-306">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="f0c72-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="f0c72-307">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="f0c72-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="f0c72-308">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="f0c72-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="f0c72-309">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="f0c72-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f0c72-310">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0c72-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="f0c72-311">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="f0c72-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="f0c72-312">Pole</span><span class="sxs-lookup"><span data-stu-id="f0c72-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f0c72-313">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f0c72-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f0c72-314">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f0c72-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f0c72-315">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f0c72-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f0c72-316">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="f0c72-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="f0c72-317">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f0c72-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
