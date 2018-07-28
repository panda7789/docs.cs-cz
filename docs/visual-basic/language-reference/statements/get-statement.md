---
title: Get – příkaz (Visual Basic)
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
ms.openlocfilehash: 32b89caf56c010f9e6ed7b78309ef30b56b682ea
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332893"
---
# <a name="get-statement"></a><span data-ttu-id="4fc28-102">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="4fc28-102">Get Statement</span></span>
<span data-ttu-id="4fc28-103">Deklaruje `Get` vlastnost postup použitý k načtení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fc28-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="4fc28-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4fc28-105">Parts</span></span>  
  
|<span data-ttu-id="4fc28-106">Termín</span><span class="sxs-lookup"><span data-stu-id="4fc28-106">Term</span></span>|<span data-ttu-id="4fc28-107">Definice</span><span class="sxs-lookup"><span data-stu-id="4fc28-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="4fc28-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fc28-108">Optional.</span></span> <span data-ttu-id="4fc28-109">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4fc28-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="4fc28-110">Volitelné na nanejvýš jeden z `Get` a `Set` příkazy v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="4fc28-111">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4fc28-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="4fc28-112">-   [chráněný](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="4fc28-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="4fc28-113">-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="4fc28-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="4fc28-114">-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="4fc28-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="4fc28-115">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4fc28-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="4fc28-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fc28-116">Optional.</span></span> <span data-ttu-id="4fc28-117">Jeden nebo více příkazů, které při spuštění `Get` volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="4fc28-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4fc28-118">Required.</span></span> <span data-ttu-id="4fc28-119">Ukončí definici `Get` procedura property.</span><span class="sxs-lookup"><span data-stu-id="4fc28-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fc28-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fc28-120">Remarks</span></span>  
 <span data-ttu-id="4fc28-121">Každou vlastnost musí mít `Get` procedura property Pokud je vlastnost označena `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="4fc28-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="4fc28-122">`Get` Postup se používá k vrácení aktuální hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="4fc28-123">Visual Basic automaticky volá vlastnosti `Get` postup, pokud výraz vyžaduje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="4fc28-124">Text deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4fc28-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="4fc28-125">Nejde uložit nic jiného než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="4fc28-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="4fc28-126">Konkrétně to nejde uložit aktuální hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="4fc28-127">Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládat v některé z vlastností, jiné procedury vlastnosti nejde získat přístup.</span><span class="sxs-lookup"><span data-stu-id="4fc28-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="4fc28-128">Obvyklým přístupem je uložení hodnoty [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarovaná na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4fc28-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="4fc28-129">Je nutné definovat `Get` postupu uvnitř vlastnosti, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="4fc28-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="4fc28-130">`Get` Postup výchozí úroveň přístupu její nadřazenou vlastnost, pokud nechcete použít `accessmodifier` v `Get` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4fc28-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4fc28-131">pravidla</span><span class="sxs-lookup"><span data-stu-id="4fc28-131">Rules</span></span>  
  
-   <span data-ttu-id="4fc28-132">**Smíšenými úrovněmi přístupu.**</span><span class="sxs-lookup"><span data-stu-id="4fc28-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="4fc28-133">Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="4fc28-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="4fc28-134">Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="4fc28-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="4fc28-135">Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Get` postup `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="4fc28-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="4fc28-136">Pokud definujete `ReadOnly` vlastnost, `Get` postup představuje celou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4fc28-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="4fc28-137">Nelze deklarovat různý přístup úroveň `Get`, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.</span><span class="sxs-lookup"><span data-stu-id="4fc28-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="4fc28-138">**Návratový typ.**</span><span class="sxs-lookup"><span data-stu-id="4fc28-138">**Return Type.**</span></span> <span data-ttu-id="4fc28-139">[Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) můžete deklarovat datový typ hodnoty vrácením.</span><span class="sxs-lookup"><span data-stu-id="4fc28-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="4fc28-140">`Get` Procedura automaticky vrací, datového typu.</span><span class="sxs-lookup"><span data-stu-id="4fc28-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="4fc28-141">Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4fc28-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="4fc28-142">Pokud `Property` příkaz neurčuje `returntype`, vrátí postup `Object`.</span><span class="sxs-lookup"><span data-stu-id="4fc28-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4fc28-143">Chování</span><span class="sxs-lookup"><span data-stu-id="4fc28-143">Behavior</span></span>  
  
-   <span data-ttu-id="4fc28-144">**Vrácení z procedury.**</span><span class="sxs-lookup"><span data-stu-id="4fc28-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="4fc28-145">Když `Get` postup vrátí volajícímu kódu, provádění pokračuje v rámci příkazu, který požadovaná hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="4fc28-146">`Get` procedury vlastnosti může vrátit hodnotu pomocí buď [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo přiřazením návratovou hodnotu pro název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="4fc28-147">Další informace najdete v tématu "Vrátit hodnotu" v [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc28-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="4fc28-148">`Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="4fc28-149">Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="4fc28-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="4fc28-150">**Vrátí hodnotu.**</span><span class="sxs-lookup"><span data-stu-id="4fc28-150">**Return Value.**</span></span> <span data-ttu-id="4fc28-151">Pro navrácení hodnoty z `Get` postup, můžete přiřadit hodnoty pro název vlastnosti, nebo ho v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc28-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="4fc28-152">`Return` Příkaz současně přiřadí `Get` procedura vracet hodnotu a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="4fc28-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="4fc28-153">Pokud používáte `Exit Property` bez přiřazení hodnoty pro název vlastnosti `Get` procedura vrací výchozí hodnota pro typ dat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="4fc28-154">Další informace najdete v tématu "Vrátit hodnotu" v [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc28-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="4fc28-155">Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vrátit hodnotu obsaženou referenčním v soukromé proměnné `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="4fc28-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="4fc28-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fc28-156">Example</span></span>  
 <span data-ttu-id="4fc28-157">V následujícím příkladu `Get` příkazu vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fc28-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4fc28-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fc28-158">See Also</span></span>  
 [<span data-ttu-id="4fc28-159">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="4fc28-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="4fc28-160">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="4fc28-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="4fc28-161">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="4fc28-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="4fc28-162">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4fc28-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="4fc28-163">Návod: Definování tříd</span><span class="sxs-lookup"><span data-stu-id="4fc28-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
