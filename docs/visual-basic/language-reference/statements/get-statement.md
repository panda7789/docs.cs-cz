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
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404599"
---
# <a name="get-statement"></a><span data-ttu-id="78394-102">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="78394-102">Get Statement</span></span>
<span data-ttu-id="78394-103">Deklaruje `Get` proceduru vlastnosti použitou k načtení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78394-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78394-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="78394-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="78394-105">Parts</span></span>  
  
|<span data-ttu-id="78394-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="78394-106">Term</span></span>|<span data-ttu-id="78394-107">Definice</span><span class="sxs-lookup"><span data-stu-id="78394-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="78394-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="78394-108">Optional.</span></span> <span data-ttu-id="78394-109">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="78394-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="78394-110">Volitelné na maximálně jeden z `Get` `Set` příkazů a v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="78394-111">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="78394-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="78394-112">-   [Proti](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="78394-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="78394-113">-   [Friend](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="78394-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="78394-114">-   [Hlášen](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="78394-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="78394-115">Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="78394-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="78394-116">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="78394-116">Optional.</span></span> <span data-ttu-id="78394-117">Jeden nebo více příkazů, které se spouštějí při `Get` volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="78394-118">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="78394-118">Required.</span></span> <span data-ttu-id="78394-119">Ukončí definici `Get` procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78394-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78394-120">Remarks</span></span>  
 <span data-ttu-id="78394-121">Každá vlastnost musí mít `Get` proceduru vlastnosti, pokud není označena vlastnost `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="78394-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="78394-122">`Get`Procedura slouží k vrácení aktuální hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="78394-123">Visual Basic automaticky volá `Get` proceduru vlastnosti, když výraz vyžádá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="78394-124">Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` procedury mezi [příkazem Property](property-statement.md) a `End Property` příkazem.</span><span class="sxs-lookup"><span data-stu-id="78394-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="78394-125">Nemůže uložit cokoli jiného než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="78394-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="78394-126">Konkrétně nemůže uložit aktuální hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="78394-127">Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup.</span><span class="sxs-lookup"><span data-stu-id="78394-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="78394-128">Obvyklým přístupem je uložení hodnoty do [soukromé](../modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78394-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="78394-129">Musíte definovat `Get` proceduru uvnitř vlastnosti, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="78394-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="78394-130">`Get`Pokud použijete `accessmodifier` příkaz v příkazu, použije se výchozí hodnota úrovně přístupu jeho obsahující vlastnosti `Get` .</span><span class="sxs-lookup"><span data-stu-id="78394-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="78394-131">Pravidla</span><span class="sxs-lookup"><span data-stu-id="78394-131">Rules</span></span>  
  
- <span data-ttu-id="78394-132">**Smíšené úrovně přístupu.**</span><span class="sxs-lookup"><span data-stu-id="78394-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="78394-133">Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` `Set` proceduru nebo, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="78394-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="78394-134">Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="78394-135">Například pokud je vlastnost deklarována `Friend` , můžete deklarovat `Get` proceduru `Private` , ale ne `Public` .</span><span class="sxs-lookup"><span data-stu-id="78394-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="78394-136">Pokud definujete `ReadOnly` vlastnost, `Get` procedura představuje celou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78394-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="78394-137">Nemůžete deklarovat jinou úroveň přístupu pro `Get` , protože by se pro vlastnost nastavily dvě úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="78394-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="78394-138">**Návratový typ**</span><span class="sxs-lookup"><span data-stu-id="78394-138">**Return Type.**</span></span> <span data-ttu-id="78394-139">[Příkaz Property](property-statement.md) může deklarovat datový typ hodnoty, kterou vrátí.</span><span class="sxs-lookup"><span data-stu-id="78394-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="78394-140">`Get`Procedura automaticky vrátí tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="78394-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="78394-141">Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78394-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="78394-142">Pokud `Property` příkaz neurčí `returntype` , procedura vrátí `Object` .</span><span class="sxs-lookup"><span data-stu-id="78394-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="78394-143">Chování</span><span class="sxs-lookup"><span data-stu-id="78394-143">Behavior</span></span>  
  
- <span data-ttu-id="78394-144">**Návrat z procedury.**</span><span class="sxs-lookup"><span data-stu-id="78394-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="78394-145">Když se `Get` procedura vrátí na volající kód, provádění pokračuje v rámci příkazu, který požadoval hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="78394-146">`Get`procedury vlastnosti mohou vracet hodnotu buď pomocí [příkazu return](return-statement.md) , nebo přiřazením návratové hodnoty názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="78394-147">Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="78394-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="78394-148">`Exit Property`Příkazy a `Return` způsobují bezprostřední ukončení procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="78394-149">Libovolný počet `Exit Property` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="78394-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="78394-150">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="78394-150">**Return Value.**</span></span> <span data-ttu-id="78394-151">Chcete-li vrátit hodnotu z `Get` procedury, můžete buď přiřadit hodnotu k názvu vlastnosti nebo ji zahrnout do [příkazu return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="78394-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="78394-152">`Return`Příkaz současně přiřadí `Get` návratovou hodnotu procedury a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="78394-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="78394-153">Pokud použijete `Exit Property` bez přiřazení hodnoty k názvu vlastnosti, `Get` procedura vrátí výchozí hodnotu pro datový typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="78394-154">Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="78394-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="78394-155">Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vracet hodnotu drženou v soukromé proměnné `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="78394-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="78394-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="78394-156">Example</span></span>  
 <span data-ttu-id="78394-157">Následující příklad používá `Get` příkaz k vrácení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78394-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="78394-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="78394-158">See also</span></span>

- [<span data-ttu-id="78394-159">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="78394-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="78394-160">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="78394-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="78394-161">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="78394-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="78394-162">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="78394-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="78394-163">Návod: Definování tříd</span><span class="sxs-lookup"><span data-stu-id="78394-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
