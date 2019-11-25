---
title: Set – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349557"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="29034-102">Set – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29034-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="29034-103">Declares a `Set` property procedure used to assign a value to a property.</span><span class="sxs-lookup"><span data-stu-id="29034-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29034-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29034-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="29034-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="29034-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="29034-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="29034-106">Optional.</span></span> <span data-ttu-id="29034-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="29034-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="29034-108">Optional on at most one of the `Get` and `Set` statements in this property.</span><span class="sxs-lookup"><span data-stu-id="29034-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="29034-109">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="29034-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="29034-110">Protected</span><span class="sxs-lookup"><span data-stu-id="29034-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="29034-111">Friend</span><span class="sxs-lookup"><span data-stu-id="29034-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="29034-112">Private</span><span class="sxs-lookup"><span data-stu-id="29034-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="29034-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="29034-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="29034-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="29034-114">Required.</span></span> <span data-ttu-id="29034-115">Parameter containing the new value for the property.</span><span class="sxs-lookup"><span data-stu-id="29034-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="29034-116">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="29034-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="29034-117">Data type of the `value` parameter.</span><span class="sxs-lookup"><span data-stu-id="29034-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="29034-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span><span class="sxs-lookup"><span data-stu-id="29034-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="29034-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="29034-119">Optional.</span></span> <span data-ttu-id="29034-120">One or more statements that run when the `Set` property procedure is called.</span><span class="sxs-lookup"><span data-stu-id="29034-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="29034-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="29034-121">Required.</span></span> <span data-ttu-id="29034-122">Terminates the definition of the `Set` property procedure.</span><span class="sxs-lookup"><span data-stu-id="29034-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29034-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29034-123">Remarks</span></span>  
 <span data-ttu-id="29034-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="29034-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="29034-125">The `Set` procedure is used to set the value of the property.</span><span class="sxs-lookup"><span data-stu-id="29034-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="29034-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span><span class="sxs-lookup"><span data-stu-id="29034-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="29034-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span><span class="sxs-lookup"><span data-stu-id="29034-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="29034-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span><span class="sxs-lookup"><span data-stu-id="29034-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="29034-129">The parameter holds the value to be assigned to the property.</span><span class="sxs-lookup"><span data-stu-id="29034-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="29034-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span><span class="sxs-lookup"><span data-stu-id="29034-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="29034-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span><span class="sxs-lookup"><span data-stu-id="29034-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="29034-132">It cannot store anything other than those procedures.</span><span class="sxs-lookup"><span data-stu-id="29034-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="29034-133">In particular, it cannot store the property's current value.</span><span class="sxs-lookup"><span data-stu-id="29034-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="29034-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span><span class="sxs-lookup"><span data-stu-id="29034-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="29034-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span><span class="sxs-lookup"><span data-stu-id="29034-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="29034-136">You must define a `Set` procedure inside the property to which it applies.</span><span class="sxs-lookup"><span data-stu-id="29034-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="29034-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span><span class="sxs-lookup"><span data-stu-id="29034-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="29034-138">Rules</span><span class="sxs-lookup"><span data-stu-id="29034-138">Rules</span></span>  
  
- <span data-ttu-id="29034-139">**Mixed Access Levels.**</span><span class="sxs-lookup"><span data-stu-id="29034-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="29034-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span><span class="sxs-lookup"><span data-stu-id="29034-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="29034-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span><span class="sxs-lookup"><span data-stu-id="29034-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="29034-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span><span class="sxs-lookup"><span data-stu-id="29034-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="29034-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span><span class="sxs-lookup"><span data-stu-id="29034-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="29034-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span><span class="sxs-lookup"><span data-stu-id="29034-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="29034-145">Behavior</span><span class="sxs-lookup"><span data-stu-id="29034-145">Behavior</span></span>  
  
- <span data-ttu-id="29034-146">**Returning from a Property Procedure.**</span><span class="sxs-lookup"><span data-stu-id="29034-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="29034-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span><span class="sxs-lookup"><span data-stu-id="29034-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="29034-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29034-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="29034-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span><span class="sxs-lookup"><span data-stu-id="29034-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="29034-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="29034-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29034-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="29034-151">Example</span></span>  
 <span data-ttu-id="29034-152">The following example uses the `Set` statement to set the value of a property.</span><span class="sxs-lookup"><span data-stu-id="29034-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="29034-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29034-153">See also</span></span>

- [<span data-ttu-id="29034-154">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="29034-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="29034-155">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="29034-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="29034-156">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="29034-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="29034-157">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="29034-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
