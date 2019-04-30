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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783874"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="131a0-102">Set – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="131a0-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="131a0-103">Deklaruje `Set` procedury vlastnosti použít pro přiřazení hodnoty k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="131a0-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="131a0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="131a0-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="131a0-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="131a0-106">Optional.</span></span> <span data-ttu-id="131a0-107">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="131a0-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="131a0-108">Volitelné na nanejvýš jeden z `Get` a `Set` příkazy v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="131a0-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="131a0-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="131a0-110">Protected</span><span class="sxs-lookup"><span data-stu-id="131a0-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="131a0-111">Friend</span><span class="sxs-lookup"><span data-stu-id="131a0-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="131a0-112">Private</span><span class="sxs-lookup"><span data-stu-id="131a0-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="131a0-113">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="131a0-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="131a0-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="131a0-114">Required.</span></span> <span data-ttu-id="131a0-115">Parametr, který obsahuje novou hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="131a0-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="131a0-116">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="131a0-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="131a0-117">Datový typ `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="131a0-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="131a0-118">Zadaný datový typ musí být stejné jako datový typ vlastnosti kde to `Set` příkaz je deklarována.</span><span class="sxs-lookup"><span data-stu-id="131a0-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="131a0-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="131a0-119">Optional.</span></span> <span data-ttu-id="131a0-120">Jeden nebo více příkazů, které při spuštění `Set` volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="131a0-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="131a0-121">Required.</span></span> <span data-ttu-id="131a0-122">Ukončí definici `Set` procedura property.</span><span class="sxs-lookup"><span data-stu-id="131a0-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="131a0-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="131a0-123">Remarks</span></span>  
 <span data-ttu-id="131a0-124">Každou vlastnost musí mít `Set` procedura property Pokud je vlastnost označena `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="131a0-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="131a0-125">`Set` Postup slouží k nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="131a0-126">Visual Basic automaticky volá vlastnosti `Set` postup po příkazu přiřazení poskytuje hodnotu uložená ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="131a0-127">Visual Basic předá parametr `Set` postupu během přiřazení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="131a0-128">Pokud nezadáte parametr `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="131a0-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="131a0-129">Parametr obsahuje hodnotu pro přiřazení k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="131a0-130">Obvykle tuto hodnotu v privátní místní proměnné a vrácení pokaždé, když `Get` volání procedury.</span><span class="sxs-lookup"><span data-stu-id="131a0-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="131a0-131">Text deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="131a0-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="131a0-132">Nejde uložit nic jiného než tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="131a0-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="131a0-133">Konkrétně to nejde uložit aktuální hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="131a0-134">Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládat v některé z vlastností, jiné procedury vlastnosti nejde získat přístup.</span><span class="sxs-lookup"><span data-stu-id="131a0-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="131a0-135">Obvyklým přístupem je uložení hodnoty [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarovaná na stejné úrovni jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="131a0-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="131a0-136">Je nutné definovat `Set` postupu uvnitř vlastnosti, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="131a0-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="131a0-137">`Set` Postup výchozí úroveň přístupu její nadřazenou vlastnost, pokud nechcete použít `accessmodifier` v `Set` příkazu.</span><span class="sxs-lookup"><span data-stu-id="131a0-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="131a0-138">pravidla</span><span class="sxs-lookup"><span data-stu-id="131a0-138">Rules</span></span>  
  
- <span data-ttu-id="131a0-139">**Smíšenými úrovněmi přístupu.**</span><span class="sxs-lookup"><span data-stu-id="131a0-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="131a0-140">Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="131a0-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="131a0-141">Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="131a0-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="131a0-142">Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Set` postup `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="131a0-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="131a0-143">Pokud definujete `WriteOnly` vlastnost, `Set` postup představuje celou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="131a0-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="131a0-144">Nelze deklarovat různý přístup úroveň `Set`, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.</span><span class="sxs-lookup"><span data-stu-id="131a0-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="131a0-145">Chování</span><span class="sxs-lookup"><span data-stu-id="131a0-145">Behavior</span></span>  
  
- <span data-ttu-id="131a0-146">**Návrat z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="131a0-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="131a0-147">Když `Set` postup vrátí volajícímu kódu, provádění pokračuje po příkazu, který poskytuje hodnota, která má být uložena.</span><span class="sxs-lookup"><span data-stu-id="131a0-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="131a0-148">`Set` procedury vlastnosti může vrátit buď pomocí [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo [příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="131a0-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="131a0-149">`Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="131a0-150">Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="131a0-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="131a0-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="131a0-151">Example</span></span>  
 <span data-ttu-id="131a0-152">V následujícím příkladu `Set` příkaz k nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="131a0-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="131a0-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="131a0-153">See also</span></span>

- [<span data-ttu-id="131a0-154">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="131a0-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="131a0-155">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="131a0-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="131a0-156">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="131a0-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="131a0-157">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="131a0-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
