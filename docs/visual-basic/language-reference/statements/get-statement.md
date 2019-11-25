---
title: Get – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 9560faf90d531c32f104dbd053a7c1f5584cfb1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351176"
---
# <a name="get-statement"></a><span data-ttu-id="3a220-102">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="3a220-102">Get Statement</span></span>
<span data-ttu-id="3a220-103">Declares a `Get` property procedure used to retrieve the value of a property.</span><span class="sxs-lookup"><span data-stu-id="3a220-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a220-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="3a220-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3a220-105">Parts</span></span>  
  
|<span data-ttu-id="3a220-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3a220-106">Term</span></span>|<span data-ttu-id="3a220-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3a220-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="3a220-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3a220-108">Optional.</span></span> <span data-ttu-id="3a220-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3a220-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="3a220-110">Optional on at most one of the `Get` and `Set` statements in this property.</span><span class="sxs-lookup"><span data-stu-id="3a220-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="3a220-111">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="3a220-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="3a220-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="3a220-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="3a220-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="3a220-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="3a220-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="3a220-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="3a220-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3a220-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="3a220-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3a220-116">Optional.</span></span> <span data-ttu-id="3a220-117">One or more statements that run when the `Get` property procedure is called.</span><span class="sxs-lookup"><span data-stu-id="3a220-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="3a220-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3a220-118">Required.</span></span> <span data-ttu-id="3a220-119">Terminates the definition of the `Get` property procedure.</span><span class="sxs-lookup"><span data-stu-id="3a220-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a220-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a220-120">Remarks</span></span>  
 <span data-ttu-id="3a220-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="3a220-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3a220-122">The `Get` procedure is used to return the current value of the property.</span><span class="sxs-lookup"><span data-stu-id="3a220-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="3a220-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span><span class="sxs-lookup"><span data-stu-id="3a220-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="3a220-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span><span class="sxs-lookup"><span data-stu-id="3a220-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="3a220-125">It cannot store anything other than those procedures.</span><span class="sxs-lookup"><span data-stu-id="3a220-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="3a220-126">In particular, it cannot store the property's current value.</span><span class="sxs-lookup"><span data-stu-id="3a220-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="3a220-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span><span class="sxs-lookup"><span data-stu-id="3a220-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="3a220-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span><span class="sxs-lookup"><span data-stu-id="3a220-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="3a220-129">You must define a `Get` procedure inside the property to which it applies.</span><span class="sxs-lookup"><span data-stu-id="3a220-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="3a220-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span><span class="sxs-lookup"><span data-stu-id="3a220-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a220-131">Rules</span><span class="sxs-lookup"><span data-stu-id="3a220-131">Rules</span></span>  
  
- <span data-ttu-id="3a220-132">**Mixed Access Levels.**</span><span class="sxs-lookup"><span data-stu-id="3a220-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="3a220-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span><span class="sxs-lookup"><span data-stu-id="3a220-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3a220-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span><span class="sxs-lookup"><span data-stu-id="3a220-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3a220-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span><span class="sxs-lookup"><span data-stu-id="3a220-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3a220-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span><span class="sxs-lookup"><span data-stu-id="3a220-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="3a220-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span><span class="sxs-lookup"><span data-stu-id="3a220-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="3a220-138">**Return Type.**</span><span class="sxs-lookup"><span data-stu-id="3a220-138">**Return Type.**</span></span> <span data-ttu-id="3a220-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span><span class="sxs-lookup"><span data-stu-id="3a220-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="3a220-140">The `Get` procedure automatically returns that data type.</span><span class="sxs-lookup"><span data-stu-id="3a220-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="3a220-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="3a220-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="3a220-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span><span class="sxs-lookup"><span data-stu-id="3a220-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3a220-143">Behavior</span><span class="sxs-lookup"><span data-stu-id="3a220-143">Behavior</span></span>  
  
- <span data-ttu-id="3a220-144">**Returning from a Procedure.**</span><span class="sxs-lookup"><span data-stu-id="3a220-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="3a220-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span><span class="sxs-lookup"><span data-stu-id="3a220-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="3a220-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span><span class="sxs-lookup"><span data-stu-id="3a220-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="3a220-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3a220-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="3a220-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span><span class="sxs-lookup"><span data-stu-id="3a220-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3a220-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="3a220-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="3a220-150">**Return Value.**</span><span class="sxs-lookup"><span data-stu-id="3a220-150">**Return Value.**</span></span> <span data-ttu-id="3a220-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3a220-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="3a220-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span><span class="sxs-lookup"><span data-stu-id="3a220-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="3a220-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span><span class="sxs-lookup"><span data-stu-id="3a220-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="3a220-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3a220-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="3a220-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="3a220-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="3a220-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a220-156">Example</span></span>  
 <span data-ttu-id="3a220-157">The following example uses the `Get` statement to return the value of a property.</span><span class="sxs-lookup"><span data-stu-id="3a220-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="3a220-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a220-158">See also</span></span>

- [<span data-ttu-id="3a220-159">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="3a220-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="3a220-160">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="3a220-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3a220-161">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="3a220-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="3a220-162">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="3a220-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3a220-163">Návod: Definování tříd</span><span class="sxs-lookup"><span data-stu-id="3a220-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
