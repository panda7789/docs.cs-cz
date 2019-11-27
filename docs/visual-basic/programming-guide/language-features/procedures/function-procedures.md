---
title: Procedury funkcí
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341090"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="60a8e-102">Procedury funkcí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60a8e-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="60a8e-103">Procedura `Function` je série Visual Basic příkazů, které jsou uzavřeny příkazy `Function` a `End Function`.</span><span class="sxs-lookup"><span data-stu-id="60a8e-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="60a8e-104">Procedura `Function` provede úlohu a vrátí řízení volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="60a8e-105">Při návratu ovládacího prvku vrátí také hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="60a8e-106">Pokaždé, když je procedura volána, její příkazy se spustí, počínaje prvním spustitelným příkazem po příkazu `Function` a končící prvním `End Function`, `Exit Function`nebo `Return`m příkazu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="60a8e-107">Můžete definovat `Function` proceduru v modulu, třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="60a8e-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="60a8e-108">Ve výchozím nastavení je `Public`, což znamená, že ho můžete volat odkudkoli v aplikaci, která má přístup k modulu, třídě nebo struktuře, ve které jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="60a8e-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="60a8e-109">`Function` procedura může přebírat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou předány volajícím kódem.</span><span class="sxs-lookup"><span data-stu-id="60a8e-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="60a8e-110">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="60a8e-110">Declaration Syntax</span></span>  
 <span data-ttu-id="60a8e-111">Syntaxe pro deklaraci `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="60a8e-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="60a8e-112">*Modifikátory* mohou určovat úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování.</span><span class="sxs-lookup"><span data-stu-id="60a8e-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="60a8e-113">Další informace naleznete v tématu [příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="60a8e-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="60a8e-114">Každý parametr deklarujete stejným způsobem jako [procedury pro sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="60a8e-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="60a8e-115">Typ dat</span><span class="sxs-lookup"><span data-stu-id="60a8e-115">Data Type</span></span>  
 <span data-ttu-id="60a8e-116">Každý `Function` procedura má datový typ stejně jako každá proměnná.</span><span class="sxs-lookup"><span data-stu-id="60a8e-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="60a8e-117">Tento typ dat je určen klauzulí `As` v příkazu `Function` a určuje datový typ hodnoty, kterou funkce vrátí na volající kód.</span><span class="sxs-lookup"><span data-stu-id="60a8e-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="60a8e-118">Tento příklad ilustruje následující ukázkové deklarace.</span><span class="sxs-lookup"><span data-stu-id="60a8e-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="60a8e-119">Další informace naleznete v části "části" v [příkazu Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="60a8e-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="60a8e-120">Vracení hodnot</span><span class="sxs-lookup"><span data-stu-id="60a8e-120">Returning Values</span></span>  
 <span data-ttu-id="60a8e-121">Hodnota `Function` procedura odesílá zpět do volajícího kódu se nazývá návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="60a8e-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="60a8e-122">Procedura vrátí tuto hodnotu jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="60a8e-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="60a8e-123">Používá příkaz `Return` k určení návratové hodnoty a vrátí řízení ihned volajícímu programu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="60a8e-124">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="60a8e-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="60a8e-125">Přiřadí hodnotu vlastnímu názvu funkce v jednom nebo více příkazech procedury.</span><span class="sxs-lookup"><span data-stu-id="60a8e-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="60a8e-126">Řízení se nevrátí do volajícího programu, dokud není proveden příkaz `Exit Function` nebo `End Function`.</span><span class="sxs-lookup"><span data-stu-id="60a8e-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="60a8e-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="60a8e-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="60a8e-128">Výhodou přiřazení návratové hodnoty k názvu funkce je, že se ovládací prvek z procedury nevrátí, dokud nenalezne příkaz `Exit Function` nebo `End Function`.</span><span class="sxs-lookup"><span data-stu-id="60a8e-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="60a8e-129">To vám umožní přiřadit předběžnou hodnotu a v případě potřeby ho upravit později.</span><span class="sxs-lookup"><span data-stu-id="60a8e-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="60a8e-130">Další informace o vrácení hodnot naleznete v tématu [příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="60a8e-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="60a8e-131">Informace o vracení polí naleznete v tématu [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="60a8e-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="60a8e-132">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="60a8e-132">Calling Syntax</span></span>  
 <span data-ttu-id="60a8e-133">Vyvoláte `Function` proceduru zahrnutím jejího názvu a argumentů buď na pravé straně příkazu přiřazení, nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="60a8e-134">Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="60a8e-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="60a8e-135">Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="60a8e-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="60a8e-136">Syntaxe pro volání `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="60a8e-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="60a8e-137">*l* -hodnota`=`*function* `[(` *ArgumentList* `)]`</span><span class="sxs-lookup"><span data-stu-id="60a8e-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="60a8e-138">`If ((` *function* `[(` *argumentlist* `)] / 3) <=`*výraz* `) Then`</span><span class="sxs-lookup"><span data-stu-id="60a8e-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="60a8e-139">Při volání `Function`ho postupu není nutné použít jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="60a8e-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="60a8e-140">Pokud to neuděláte, jsou provedeny všechny akce funkce, ale návratová hodnota je ignorována.</span><span class="sxs-lookup"><span data-stu-id="60a8e-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="60a8e-141">Tento způsob je často volán <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.</span><span class="sxs-lookup"><span data-stu-id="60a8e-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="60a8e-142">Ilustrace deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="60a8e-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="60a8e-143">Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.</span><span class="sxs-lookup"><span data-stu-id="60a8e-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="60a8e-144">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="60a8e-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="60a8e-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60a8e-145">See also</span></span>

- [<span data-ttu-id="60a8e-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="60a8e-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="60a8e-147">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="60a8e-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="60a8e-148">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="60a8e-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="60a8e-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="60a8e-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="60a8e-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="60a8e-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="60a8e-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="60a8e-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="60a8e-152">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="60a8e-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="60a8e-153">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="60a8e-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="60a8e-154">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="60a8e-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
