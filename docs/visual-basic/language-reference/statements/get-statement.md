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
# <a name="get-statement"></a><span data-ttu-id="98c14-102">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="98c14-102">Get Statement</span></span>
<span data-ttu-id="98c14-103">Deklaruje proceduru vlastnosti `Get`, která slouží k načtení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98c14-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="98c14-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="98c14-105">Parts</span></span>  
  
|<span data-ttu-id="98c14-106">Termín</span><span class="sxs-lookup"><span data-stu-id="98c14-106">Term</span></span>|<span data-ttu-id="98c14-107">Definice</span><span class="sxs-lookup"><span data-stu-id="98c14-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="98c14-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="98c14-108">Optional.</span></span> <span data-ttu-id="98c14-109">Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="98c14-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="98c14-110">Volitelné na maximálně jeden z příkazů `Get` a `Set` v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="98c14-111">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="98c14-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="98c14-112">-   [chráněno](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="98c14-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="98c14-113">-   [přítel](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="98c14-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="98c14-114">-   [privátní](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="98c14-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="98c14-115">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="98c14-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="98c14-116">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="98c14-116">Optional.</span></span> <span data-ttu-id="98c14-117">Jeden nebo více příkazů, které se spouštějí při volání procedury vlastnosti `Get`.</span><span class="sxs-lookup"><span data-stu-id="98c14-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="98c14-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="98c14-118">Required.</span></span> <span data-ttu-id="98c14-119">Ukončí definici procedury vlastnosti `Get`.</span><span class="sxs-lookup"><span data-stu-id="98c14-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98c14-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98c14-120">Remarks</span></span>  
 <span data-ttu-id="98c14-121">Každá vlastnost musí mít proceduru `Get` vlastnost, pokud vlastnost není označena `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="98c14-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="98c14-122">Procedura `Get` slouží k vrácení aktuální hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="98c14-123">Visual Basic automaticky volá `Get` proceduru vlastnosti, když výraz požaduje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="98c14-124">Tělo deklarace vlastnosti může obsahovat pouze `Get` vlastnosti a procedury `Set` mezi [příkazem Property](../../../visual-basic/language-reference/statements/property-statement.md) a příkazem `End Property`.</span><span class="sxs-lookup"><span data-stu-id="98c14-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="98c14-125">Nemůže uložit cokoli jiného než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="98c14-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="98c14-126">Konkrétně nemůže uložit aktuální hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="98c14-127">Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup.</span><span class="sxs-lookup"><span data-stu-id="98c14-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="98c14-128">Obvyklým přístupem je uložení hodnoty do [soukromé](../../../visual-basic/language-reference/modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98c14-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="98c14-129">Musíte definovat `Get` proceduru uvnitř vlastnosti, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="98c14-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="98c14-130">Pokud nepoužijete `accessmodifier` v příkazu `Get`, bude výchozí hodnota `Get` nastavena na úroveň přístupu jeho obsahující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="98c14-131">Pravidla</span><span class="sxs-lookup"><span data-stu-id="98c14-131">Rules</span></span>  
  
- <span data-ttu-id="98c14-132">**Smíšené úrovně přístupu.**</span><span class="sxs-lookup"><span data-stu-id="98c14-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="98c14-133">Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="98c14-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="98c14-134">Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="98c14-135">Například pokud je vlastnost deklarována `Friend`, můžete deklarovat `Get` proceduru `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="98c14-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="98c14-136">Pokud definujete vlastnost `ReadOnly`, bude procedura `Get` představovat celou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98c14-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="98c14-137">Pro `Get`nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="98c14-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="98c14-138">**Návratový typ**</span><span class="sxs-lookup"><span data-stu-id="98c14-138">**Return Type.**</span></span> <span data-ttu-id="98c14-139">[Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md) může deklarovat datový typ hodnoty, kterou vrátí.</span><span class="sxs-lookup"><span data-stu-id="98c14-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="98c14-140">`Get` procedura tento datový typ automaticky vrátí.</span><span class="sxs-lookup"><span data-stu-id="98c14-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="98c14-141">Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98c14-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="98c14-142">Pokud příkaz `Property` neurčí `returntype`, procedura vrátí `Object`.</span><span class="sxs-lookup"><span data-stu-id="98c14-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="98c14-143">Chování</span><span class="sxs-lookup"><span data-stu-id="98c14-143">Behavior</span></span>  
  
- <span data-ttu-id="98c14-144">**Návrat z procedury.**</span><span class="sxs-lookup"><span data-stu-id="98c14-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="98c14-145">Když se `Get` procedura vrátí k volajícímu kódu, provádění pokračuje v rámci příkazu, který požadoval hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="98c14-146">procedury vlastnosti `Get` mohou vracet hodnotu buď pomocí [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md) , nebo přiřazením návratové hodnoty názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="98c14-147">Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="98c14-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="98c14-148">Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="98c14-149">Libovolný počet `Exit Property` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="98c14-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="98c14-150">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="98c14-150">**Return Value.**</span></span> <span data-ttu-id="98c14-151">Chcete-li vrátit hodnotu z `Get` postup, můžete buď přiřadit hodnotu k názvu vlastnosti nebo ji zahrnout do [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="98c14-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="98c14-152">Příkaz `Return` současně přiřadí návratovou hodnotu procedury `Get` a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="98c14-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="98c14-153">Použijete-li `Exit Property` bez přiřazení hodnoty k názvu vlastnosti, procedura `Get` vrátí výchozí hodnotu pro datový typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="98c14-154">Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="98c14-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="98c14-155">Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vracet hodnotu uloženou v soukromé proměnné `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="98c14-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="98c14-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="98c14-156">Example</span></span>  
 <span data-ttu-id="98c14-157">Následující příklad používá příkaz `Get` pro návrat hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98c14-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="98c14-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98c14-158">See also</span></span>

- [<span data-ttu-id="98c14-159">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="98c14-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="98c14-160">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="98c14-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="98c14-161">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="98c14-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="98c14-162">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="98c14-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="98c14-163">Návod: Definování tříd</span><span class="sxs-lookup"><span data-stu-id="98c14-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
