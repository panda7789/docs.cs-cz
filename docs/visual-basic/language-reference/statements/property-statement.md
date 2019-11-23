---
title: Property – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346759"
---
# <a name="property-statement"></a><span data-ttu-id="2b854-102">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2b854-102">Property Statement</span></span>

<span data-ttu-id="2b854-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b854-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="2b854-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2b854-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="2b854-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-106">Optional.</span></span> <span data-ttu-id="2b854-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="2b854-108">See [Attribute List](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="2b854-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-109">Optional.</span></span> <span data-ttu-id="2b854-110">Specifies that this property is the default property for the class or structure on which it is defined.</span><span class="sxs-lookup"><span data-stu-id="2b854-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="2b854-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span><span class="sxs-lookup"><span data-stu-id="2b854-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="2b854-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span><span class="sxs-lookup"><span data-stu-id="2b854-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="2b854-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span><span class="sxs-lookup"><span data-stu-id="2b854-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="2b854-114">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="2b854-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="2b854-115">Public</span><span class="sxs-lookup"><span data-stu-id="2b854-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="2b854-116">Protected</span><span class="sxs-lookup"><span data-stu-id="2b854-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="2b854-117">Friend</span><span class="sxs-lookup"><span data-stu-id="2b854-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="2b854-118">Private</span><span class="sxs-lookup"><span data-stu-id="2b854-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="2b854-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2b854-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="2b854-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="2b854-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="2b854-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="2b854-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-122">Optional.</span></span> <span data-ttu-id="2b854-123">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="2b854-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="2b854-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="2b854-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="2b854-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="2b854-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="2b854-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="2b854-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="2b854-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="2b854-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="2b854-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="2b854-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="2b854-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-129">Optional.</span></span> <span data-ttu-id="2b854-130">See [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="2b854-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-131">Optional.</span></span> <span data-ttu-id="2b854-132">See [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="2b854-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-133">Optional.</span></span> <span data-ttu-id="2b854-134">See [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="2b854-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-135">Optional.</span></span> <span data-ttu-id="2b854-136">See [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="2b854-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-137">Optional.</span></span> <span data-ttu-id="2b854-138">See [Iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="2b854-139">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2b854-139">Required.</span></span> <span data-ttu-id="2b854-140">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2b854-140">Name of the property.</span></span> <span data-ttu-id="2b854-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="2b854-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-142">Optional.</span></span> <span data-ttu-id="2b854-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="2b854-144">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="2b854-145">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="2b854-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="2b854-146">Data type of the value returned by this property.</span><span class="sxs-lookup"><span data-stu-id="2b854-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="2b854-147">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-147">Optional.</span></span> <span data-ttu-id="2b854-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="2b854-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="2b854-149">See [Implements Statement](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="2b854-150">Required if `Implements` is supplied.</span><span class="sxs-lookup"><span data-stu-id="2b854-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="2b854-151">List of properties being implemented.</span><span class="sxs-lookup"><span data-stu-id="2b854-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="2b854-152">Each `implementedproperty` has the following syntax and parts:</span><span class="sxs-lookup"><span data-stu-id="2b854-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="2b854-153">Part</span><span class="sxs-lookup"><span data-stu-id="2b854-153">Part</span></span>|<span data-ttu-id="2b854-154">Popis</span><span class="sxs-lookup"><span data-stu-id="2b854-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="2b854-155">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2b854-155">Required.</span></span> <span data-ttu-id="2b854-156">Name of an interface implemented by this property's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="2b854-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="2b854-157">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2b854-157">Required.</span></span> <span data-ttu-id="2b854-158">Name by which the property is defined in `interface`.</span><span class="sxs-lookup"><span data-stu-id="2b854-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="2b854-159">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-159">Optional.</span></span> <span data-ttu-id="2b854-160">Required if the property is marked `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="2b854-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="2b854-161">Starts a `Get` property procedure that is used to return the value of the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="2b854-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="2b854-163">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-163">Optional.</span></span> <span data-ttu-id="2b854-164">Block of statements to run within the `Get` or `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="2b854-165">Terminates the `Get` property procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="2b854-166">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b854-166">Optional.</span></span> <span data-ttu-id="2b854-167">Required if the property is marked `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="2b854-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="2b854-168">Starts a `Set` property procedure that is used to store the value of the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="2b854-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="2b854-170">Terminates the `Set` property procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="2b854-171">Terminates the definition of this property.</span><span class="sxs-lookup"><span data-stu-id="2b854-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b854-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b854-172">Remarks</span></span>

<span data-ttu-id="2b854-173">The `Property` statement introduces the declaration of a property.</span><span class="sxs-lookup"><span data-stu-id="2b854-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="2b854-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span><span class="sxs-lookup"><span data-stu-id="2b854-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="2b854-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span><span class="sxs-lookup"><span data-stu-id="2b854-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="2b854-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="2b854-177">You can use `Property` only at class level.</span><span class="sxs-lookup"><span data-stu-id="2b854-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="2b854-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="2b854-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="2b854-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2b854-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="2b854-180">By default, properties use public access.</span><span class="sxs-lookup"><span data-stu-id="2b854-180">By default, properties use public access.</span></span> <span data-ttu-id="2b854-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span><span class="sxs-lookup"><span data-stu-id="2b854-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="2b854-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span><span class="sxs-lookup"><span data-stu-id="2b854-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="2b854-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span><span class="sxs-lookup"><span data-stu-id="2b854-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="2b854-184">This parameter holds the value to be assigned to the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="2b854-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span><span class="sxs-lookup"><span data-stu-id="2b854-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="2b854-186">Rules</span><span class="sxs-lookup"><span data-stu-id="2b854-186">Rules</span></span>

- <span data-ttu-id="2b854-187">**Mixed Access Levels.**</span><span class="sxs-lookup"><span data-stu-id="2b854-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="2b854-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span><span class="sxs-lookup"><span data-stu-id="2b854-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="2b854-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span><span class="sxs-lookup"><span data-stu-id="2b854-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="2b854-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span><span class="sxs-lookup"><span data-stu-id="2b854-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="2b854-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="2b854-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span><span class="sxs-lookup"><span data-stu-id="2b854-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="2b854-193">**Return Type.**</span><span class="sxs-lookup"><span data-stu-id="2b854-193">**Return Type.**</span></span> <span data-ttu-id="2b854-194">The `Property` statement can declare the data type of the value it returns.</span><span class="sxs-lookup"><span data-stu-id="2b854-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="2b854-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="2b854-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="2b854-196">If you do not specify `returntype`, the property returns `Object`.</span><span class="sxs-lookup"><span data-stu-id="2b854-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="2b854-197">**Implementation.**</span><span class="sxs-lookup"><span data-stu-id="2b854-197">**Implementation.**</span></span> <span data-ttu-id="2b854-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="2b854-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="2b854-199">The `Implements` statement must include each interface specified in `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="2b854-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="2b854-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span><span class="sxs-lookup"><span data-stu-id="2b854-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="2b854-201">Behavior</span><span class="sxs-lookup"><span data-stu-id="2b854-201">Behavior</span></span>

- <span data-ttu-id="2b854-202">**Returning from a Property Procedure.**</span><span class="sxs-lookup"><span data-stu-id="2b854-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="2b854-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span><span class="sxs-lookup"><span data-stu-id="2b854-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="2b854-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="2b854-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="2b854-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="2b854-206">**Return Value.**</span><span class="sxs-lookup"><span data-stu-id="2b854-206">**Return Value.**</span></span> <span data-ttu-id="2b854-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="2b854-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="2b854-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span><span class="sxs-lookup"><span data-stu-id="2b854-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="2b854-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span><span class="sxs-lookup"><span data-stu-id="2b854-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="2b854-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span><span class="sxs-lookup"><span data-stu-id="2b854-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="2b854-211">The following example shows this.</span><span class="sxs-lookup"><span data-stu-id="2b854-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="2b854-212">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b854-212">Example</span></span>

<span data-ttu-id="2b854-213">The following example declares a property in a class.</span><span class="sxs-lookup"><span data-stu-id="2b854-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="2b854-214">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b854-214">See also</span></span>

- [<span data-ttu-id="2b854-215">Automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2b854-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="2b854-216">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2b854-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="2b854-217">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="2b854-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="2b854-218">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="2b854-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="2b854-219">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="2b854-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="2b854-220">Default</span><span class="sxs-lookup"><span data-stu-id="2b854-220">Default</span></span>](../modifiers/default.md)
