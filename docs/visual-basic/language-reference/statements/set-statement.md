---
title: Set – příkaz (Visual Basic)
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
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583235"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="aea63-102">Set – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aea63-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="aea63-103">Deklaruje proceduru vlastnosti `Set`, která slouží k přiřazení hodnoty k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aea63-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="aea63-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="aea63-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="aea63-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="aea63-106">Optional.</span></span> <span data-ttu-id="aea63-107">Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="aea63-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="aea63-108">Volitelné na maximálně jeden z příkazů `Get` a `Set` v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="aea63-109">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="aea63-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="aea63-110">Protected</span><span class="sxs-lookup"><span data-stu-id="aea63-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="aea63-111">Friend</span><span class="sxs-lookup"><span data-stu-id="aea63-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="aea63-112">Private</span><span class="sxs-lookup"><span data-stu-id="aea63-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="aea63-113">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="aea63-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="aea63-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aea63-114">Required.</span></span> <span data-ttu-id="aea63-115">Parametr, který obsahuje novou hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aea63-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="aea63-116">Vyžaduje se, pokud je `Option Strict` `On`.</span><span class="sxs-lookup"><span data-stu-id="aea63-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="aea63-117">Datový typ parametru `value`.</span><span class="sxs-lookup"><span data-stu-id="aea63-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="aea63-118">Zadaný datový typ musí být stejný jako datový typ vlastnosti, kde je tento příkaz `Set` deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="aea63-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="aea63-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="aea63-119">Optional.</span></span> <span data-ttu-id="aea63-120">Jeden nebo více příkazů, které se spouštějí při volání procedury vlastnosti `Set`.</span><span class="sxs-lookup"><span data-stu-id="aea63-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="aea63-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aea63-121">Required.</span></span> <span data-ttu-id="aea63-122">Ukončí definici procedury vlastnosti `Set`.</span><span class="sxs-lookup"><span data-stu-id="aea63-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aea63-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aea63-123">Remarks</span></span>  
 <span data-ttu-id="aea63-124">Každá vlastnost musí mít proceduru `Set` vlastnost, pokud vlastnost není označena `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="aea63-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="aea63-125">Procedura `Set` slouží k nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="aea63-126">Visual Basic automaticky volá proceduru `Set`, pokud příkaz přiřazení poskytuje hodnotu, která má být uložena ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="aea63-127">Visual Basic předá do přiřazení vlastností parametr `Set` proceduře.</span><span class="sxs-lookup"><span data-stu-id="aea63-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="aea63-128">Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="aea63-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="aea63-129">Parametr obsahuje hodnotu, která má být přiřazena vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="aea63-130">Tuto hodnotu obvykle ukládáte do privátní místní proměnné a vrátíte ji pokaždé, když je volána procedura `Get`.</span><span class="sxs-lookup"><span data-stu-id="aea63-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="aea63-131">Tělo deklarace vlastnosti může obsahovat pouze `Get` vlastnosti a procedury `Set` mezi [příkazem Property](../../../visual-basic/language-reference/statements/property-statement.md) a příkazem `End Property`.</span><span class="sxs-lookup"><span data-stu-id="aea63-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="aea63-132">Nemůže uložit cokoli jiného než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="aea63-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="aea63-133">Konkrétně nemůže uložit aktuální hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="aea63-134">Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup.</span><span class="sxs-lookup"><span data-stu-id="aea63-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="aea63-135">Obvyklým přístupem je uložení hodnoty do [soukromé](../../../visual-basic/language-reference/modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aea63-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="aea63-136">Musíte definovat `Set` proceduru uvnitř vlastnosti, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="aea63-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="aea63-137">Pokud nepoužijete `accessmodifier` v příkazu `Set`, bude výchozí hodnota `Set` nastavena na úroveň přístupu jeho obsahující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="aea63-138">Pravidly</span><span class="sxs-lookup"><span data-stu-id="aea63-138">Rules</span></span>  
  
- <span data-ttu-id="aea63-139">**Smíšené úrovně přístupu.**</span><span class="sxs-lookup"><span data-stu-id="aea63-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="aea63-140">Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="aea63-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="aea63-141">Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="aea63-142">Například pokud je vlastnost deklarována `Friend`, můžete deklarovat `Set` proceduru `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="aea63-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="aea63-143">Pokud definujete vlastnost `WriteOnly`, bude procedura `Set` představovat celou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aea63-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="aea63-144">Pro `Set` nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="aea63-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="aea63-145">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="aea63-145">Behavior</span></span>  
  
- <span data-ttu-id="aea63-146">**Návrat z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="aea63-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="aea63-147">Když se `Set` procedura vrátí k volajícímu kódu, provádění pokračuje po příkazu, který poskytl hodnotu, která má být uložena.</span><span class="sxs-lookup"><span data-stu-id="aea63-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="aea63-148">procedury vlastnosti `Set` mohou vracet buď pomocí [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md) , nebo [příkazu exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aea63-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="aea63-149">Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="aea63-150">Libovolný počet `Exit Property` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="aea63-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea63-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="aea63-151">Example</span></span>  
 <span data-ttu-id="aea63-152">Následující příklad používá příkaz `Set` k nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aea63-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="aea63-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aea63-153">See also</span></span>

- [<span data-ttu-id="aea63-154">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="aea63-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="aea63-155">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="aea63-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="aea63-156">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="aea63-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="aea63-157">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aea63-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
