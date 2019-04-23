---
title: 'Postupy: Změna hodnoty argumentu procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316619"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="89144-102">Postupy: Změna hodnoty argumentu procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89144-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="89144-103">Při volání procedury, každý argument, který zadáte odpovídá jednomu z parametrů definovaných v postupu.</span><span class="sxs-lookup"><span data-stu-id="89144-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="89144-104">V některých případech můžete změnit kód procedury hodnotu základní argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="89144-105">V ostatních případech procedura může změnit pouze místní kopie argumentu.</span><span class="sxs-lookup"><span data-stu-id="89144-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="89144-106">Při volání postupu Visual Basic vytvoří místní kopii každý argument, který je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="89144-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="89144-107">Každý argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic poskytuje kód procedury přímý odkaz na programovací prvek základní argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="89144-108">Pokud základní prvek ve volajícím kódu je upravitelná prvek a argument je předán `ByRef`, kód procedury můžete použít přímý odkaz ke změně hodnoty prvku ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="89144-109">Změna zdrojové hodnoty</span><span class="sxs-lookup"><span data-stu-id="89144-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="89144-110">Chcete-li změnit nadřazenou hodnotu argumentu ve volajícím kódu procedury</span><span class="sxs-lookup"><span data-stu-id="89144-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="89144-111">V deklaraci procedury zadejte [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametru odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="89144-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="89144-112">Ve volajícím kódu předáte jako argument upravitelná programovací element.</span><span class="sxs-lookup"><span data-stu-id="89144-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="89144-113">Ve volajícím kódu neuvádějte argument v závorkách v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="89144-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="89144-114">V kódu procedury používejte název parametru pro přiřazení hodnoty na základní element ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="89144-115">Podívejte se na příklad dále dolů ukázku.</span><span class="sxs-lookup"><span data-stu-id="89144-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="89144-116">Změna místní kopie</span><span class="sxs-lookup"><span data-stu-id="89144-116">Changing Local Copies</span></span>  
 <span data-ttu-id="89144-117">Pokud základní prvek ve volajícím kódu je neupravitelnými prvek, nebo pokud je argument předaný `ByVal`, postup nelze změnit jeho hodnotu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="89144-118">Postup však můžete změnit jeho místní kopii těchto argument.</span><span class="sxs-lookup"><span data-stu-id="89144-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="89144-119">Chcete-li změnit kopie argumentu procedury v kódu procedury</span><span class="sxs-lookup"><span data-stu-id="89144-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="89144-120">V deklaraci procedury zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) parametru odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="89144-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="89144-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="89144-121">-or-</span></span>  
  
     <span data-ttu-id="89144-122">Ve volajícím kódu uzavřete jej do v závorkách v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="89144-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="89144-123">To vynutí jazyka Visual Basic k předání argumentu podle hodnoty, i v případě, že odpovídající parametr určuje `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="89144-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="89144-124">V kódu procedury používejte název parametru pro přiřazení hodnoty k místní kopie argumentu.</span><span class="sxs-lookup"><span data-stu-id="89144-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="89144-125">Základní hodnota ve volajícím kódu se nezmění.</span><span class="sxs-lookup"><span data-stu-id="89144-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89144-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="89144-126">Example</span></span>  
 <span data-ttu-id="89144-127">Následující příklad ukazuje dva postupy, které trvat proměnnou pole a provozují na jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="89144-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="89144-128">`increase` Procedura přidá pouze jednu na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="89144-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="89144-129">`replace` Postup přiřadí nové pole parametru `a()` a pak přidá jednu na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="89144-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="89144-130">První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="89144-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="89144-131">Protože pole `n` je typem odkazu `replace` lze měnit její členy, i když je mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="89144-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="89144-132">Druhá `MsgBox` volání zobrazí "po replace(n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="89144-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="89144-133">Protože `n` je předán `ByRef`, `replace` můžete upravit proměnnou `n` v volající kód a přiřaďte nové pole do něj.</span><span class="sxs-lookup"><span data-stu-id="89144-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="89144-134">Protože `n` je typem odkazu `replace` můžete také změnit jeho členů.</span><span class="sxs-lookup"><span data-stu-id="89144-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="89144-135">Postup lze zabránit ve změně samotného proměnné ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="89144-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="89144-136">Zobrazit [jak: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="89144-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89144-137">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89144-137">Compiling the Code</span></span>  
 <span data-ttu-id="89144-138">Při předání proměnné podle odkazu, je nutné použít `ByRef` – klíčové slovo k určení tento mechanismus.</span><span class="sxs-lookup"><span data-stu-id="89144-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="89144-139">Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="89144-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="89144-140">Ale při programování je dobrým zvykem zahrnout buď [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="89144-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="89144-141">Díky tomu váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="89144-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="89144-142">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89144-142">.NET Framework Security</span></span>  
 <span data-ttu-id="89144-143">Je vždycky představuje potenciální riziko postup, chcete-li změnit hodnotu argumentu ve volajícím kódu základní, kterému je povoleno.</span><span class="sxs-lookup"><span data-stu-id="89144-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="89144-144">Ujistěte se, že očekáváte, že tuto hodnotu změnit a připravit tak zkontrolovat, že platnost před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="89144-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89144-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89144-145">See also</span></span>

- [<span data-ttu-id="89144-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="89144-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="89144-147">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="89144-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="89144-148">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="89144-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="89144-149">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="89144-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="89144-150">Rozdíly mezi upravitelnými a neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="89144-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="89144-151">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="89144-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="89144-152">Postupy: Ochrana argumentu procedury proti změnám hodnoty</span><span class="sxs-lookup"><span data-stu-id="89144-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="89144-153">Postupy: Vynucení argumentu být předána podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="89144-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="89144-154">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="89144-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="89144-155">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="89144-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
