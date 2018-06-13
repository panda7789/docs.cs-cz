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
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604832"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="e8476-102">Set – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8476-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="e8476-103">Deklaruje `Set` procedura property sloužící k přidělování hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8476-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8476-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="e8476-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e8476-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="e8476-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e8476-106">Optional.</span></span> <span data-ttu-id="e8476-107">V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="e8476-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="e8476-108">Volitelné na maximálně jedno z `Get` a `Set` příkazy v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="e8476-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="e8476-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="e8476-110">Protected</span><span class="sxs-lookup"><span data-stu-id="e8476-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="e8476-111">Friend</span><span class="sxs-lookup"><span data-stu-id="e8476-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="e8476-112">Private</span><span class="sxs-lookup"><span data-stu-id="e8476-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="e8476-113">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e8476-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="e8476-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8476-114">Required.</span></span> <span data-ttu-id="e8476-115">Parametr, který obsahuje novou hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8476-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="e8476-116">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="e8476-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="e8476-117">Datový typ `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8476-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="e8476-118">Datový typ zadaný musí být stejný jako datový typ vlastnosti kde to `Set` příkaz je deklarován.</span><span class="sxs-lookup"><span data-stu-id="e8476-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="e8476-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e8476-119">Optional.</span></span> <span data-ttu-id="e8476-120">Jeden nebo více příkazů, které při spuštění `Set` vlastnost procedura je volána.</span><span class="sxs-lookup"><span data-stu-id="e8476-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="e8476-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8476-121">Required.</span></span> <span data-ttu-id="e8476-122">Ukončí definice `Set` procedura property.</span><span class="sxs-lookup"><span data-stu-id="e8476-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8476-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8476-123">Remarks</span></span>  
 <span data-ttu-id="e8476-124">Všech vlastností, musí mít `Set` procedura property Pokud je vlastnost označena `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="e8476-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="e8476-125">`Set` Postup slouží k nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="e8476-126">Visual Basic automaticky volá vlastnost `Set` procedury při příkazu přiřazení obsahuje hodnotu k uložení vlastností.</span><span class="sxs-lookup"><span data-stu-id="e8476-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="e8476-127">Parametr, který se předá jazyka Visual Basic `Set` postup při přiřazení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="e8476-128">Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="e8476-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="e8476-129">Parametr obsahuje hodnota, která má být přiřazeno k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="e8476-130">Obvykle uložte tuto hodnotu v privátní místní proměnné a obnoví v něm vždy, když `Get` procedura je volána.</span><span class="sxs-lookup"><span data-stu-id="e8476-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="e8476-131">Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8476-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="e8476-132">Nelze uložit jakoukoli jinou hodnotu než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="e8476-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="e8476-133">Konkrétně ho Nejde uložit aktuální hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="e8476-134">Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládá uvnitř buď procedury vlastností, jiné procedury vlastnosti nelze k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="e8476-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="e8476-135">Obvyklé přístup je pro uložení hodnotu v [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarována na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8476-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="e8476-136">Je nutné definovat `Set` postupu uvnitř vlastnosti, na který se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="e8476-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="e8476-137">`Set` Postup výchozí úroveň přístupu jeho obsahující vlastnosti, pokud nechcete použít `accessmodifier` v `Set` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8476-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e8476-138">Pravidla</span><span class="sxs-lookup"><span data-stu-id="e8476-138">Rules</span></span>  
  
-   <span data-ttu-id="e8476-139">**Smíšenými úrovněmi přístupu.**</span><span class="sxs-lookup"><span data-stu-id="e8476-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="e8476-140">Pokud definujete vlastnost pro čtení a zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="e8476-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="e8476-141">Pokud to uděláte, musí být úroveň přístupu postup více omezující než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="e8476-142">Například, pokud je deklarovaná vlastnost `Friend`, můžou deklarovat `Set` postup `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="e8476-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="e8476-143">Pokud definujete `WriteOnly` vlastnost, `Set` představuje vlastnost celý postup.</span><span class="sxs-lookup"><span data-stu-id="e8476-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="e8476-144">Pro přístup k jiné nelze deklarovat úrovně pro `Set`, vzhledem k tomu, který se nastavuje dvě úrovně přístupu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8476-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="e8476-145">Chování</span><span class="sxs-lookup"><span data-stu-id="e8476-145">Behavior</span></span>  
  
-   <span data-ttu-id="e8476-146">**Vrácení z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="e8476-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="e8476-147">Když `Set` postup vrátí kód volání, provádění pokračuje následující příkaz, který poskytuje hodnota, která má být uložen.</span><span class="sxs-lookup"><span data-stu-id="e8476-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="e8476-148">`Set` procedury vlastností může vrátit buď pomocí [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo [ukončovací příkaz](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8476-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="e8476-149">`Exit Property` a `Return` příkazy způsobí okamžité ukončení z procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="e8476-150">Libovolný počet `Exit Property` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e8476-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8476-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8476-151">Example</span></span>  
 <span data-ttu-id="e8476-152">Následující příklad používá `Set` příkaz nastavit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e8476-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e8476-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8476-153">See Also</span></span>  
 [<span data-ttu-id="e8476-154">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="e8476-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="e8476-155">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="e8476-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="e8476-156">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="e8476-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e8476-157">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e8476-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
