---
title: Module – příkaz
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348019"
---
# <a name="module-statement"></a><span data-ttu-id="6bc2d-102">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="6bc2d-102">Module Statement</span></span>

<span data-ttu-id="6bc2d-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bc2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bc2d-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="6bc2d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6bc2d-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="6bc2d-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-106">Optional.</span></span> <span data-ttu-id="6bc2d-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="6bc2d-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-108">Optional.</span></span> <span data-ttu-id="6bc2d-109">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="6bc2d-109">Can be one of the following:</span></span>

- [<span data-ttu-id="6bc2d-110">Public</span><span class="sxs-lookup"><span data-stu-id="6bc2d-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="6bc2d-111">Friend</span><span class="sxs-lookup"><span data-stu-id="6bc2d-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="6bc2d-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="6bc2d-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-113">Required.</span></span> <span data-ttu-id="6bc2d-114">Name of this module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-114">Name of this module.</span></span> <span data-ttu-id="6bc2d-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="6bc2d-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-116">Optional.</span></span> <span data-ttu-id="6bc2d-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="6bc2d-118">Terminates the `Module` definition.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bc2d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bc2d-119">Remarks</span></span>

<span data-ttu-id="6bc2d-120">A `Module` statement defines a reference type available throughout its namespace.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="6bc2d-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="6bc2d-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="6bc2d-123">Modules do not support inheritance or implement interfaces.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="6bc2d-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="6bc2d-125">You can use `Module` only at namespace level.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="6bc2d-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="6bc2d-127">You cannot nest a module within another module, or within any type.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="6bc2d-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="6bc2d-129">A module has the same lifetime as your program.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="6bc2d-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="6bc2d-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="6bc2d-132">You can adjust their access levels with the access modifiers.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="6bc2d-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="6bc2d-134">All members of a module are implicitly `Shared`.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="6bc2d-135">Classes and Modules</span><span class="sxs-lookup"><span data-stu-id="6bc2d-135">Classes and Modules</span></span>

<span data-ttu-id="6bc2d-136">These elements have many similarities, but there are some important differences as well.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="6bc2d-137">**Terminology.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-137">**Terminology.**</span></span> <span data-ttu-id="6bc2d-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="6bc2d-139">The current version calls these *classes* and *modules*, respectively.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="6bc2d-140">**Shared Members.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-140">**Shared Members.**</span></span> <span data-ttu-id="6bc2d-141">You can control whether a member of a class is a shared or instance member.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="6bc2d-142">**Object Orientation.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-142">**Object Orientation.**</span></span> <span data-ttu-id="6bc2d-143">Classes are object-oriented, but modules are not.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="6bc2d-144">So only classes can be instantiated as objects.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="6bc2d-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="6bc2d-146">Rules</span><span class="sxs-lookup"><span data-stu-id="6bc2d-146">Rules</span></span>

- <span data-ttu-id="6bc2d-147">**Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-147">**Modifiers.**</span></span> <span data-ttu-id="6bc2d-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="6bc2d-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="6bc2d-150">**Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-150">**Inheritance.**</span></span> <span data-ttu-id="6bc2d-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="6bc2d-152">In particular, one module cannot inherit from another.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="6bc2d-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="6bc2d-154">**Default Property.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-154">**Default Property.**</span></span> <span data-ttu-id="6bc2d-155">You cannot define any default properties in a module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="6bc2d-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="6bc2d-157">Behavior</span><span class="sxs-lookup"><span data-stu-id="6bc2d-157">Behavior</span></span>

- <span data-ttu-id="6bc2d-158">**Access Level.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-158">**Access Level.**</span></span> <span data-ttu-id="6bc2d-159">Within a module, you can declare each member with its own access level.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="6bc2d-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="6bc2d-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="6bc2d-162">**Scope.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-162">**Scope.**</span></span> <span data-ttu-id="6bc2d-163">A module is in scope throughout its namespace.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="6bc2d-164">The scope of every module member is the entire module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="6bc2d-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="6bc2d-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="6bc2d-167">**Qualification.**</span><span class="sxs-lookup"><span data-stu-id="6bc2d-167">**Qualification.**</span></span> <span data-ttu-id="6bc2d-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="6bc2d-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span><span class="sxs-lookup"><span data-stu-id="6bc2d-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="6bc2d-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2d-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="6bc2d-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bc2d-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="6bc2d-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bc2d-172">See also</span></span>

- [<span data-ttu-id="6bc2d-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="6bc2d-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="6bc2d-174">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="6bc2d-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="6bc2d-175">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="6bc2d-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="6bc2d-176">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="6bc2d-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="6bc2d-177">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="6bc2d-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="6bc2d-178">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="6bc2d-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
