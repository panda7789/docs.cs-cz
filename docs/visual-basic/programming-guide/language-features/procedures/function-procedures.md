---
title: Procedury funkcí (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655532"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="f0952-102">Procedury funkcí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0952-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="f0952-103">A `Function` postup je řada příkazů jazyka Visual Basic uzavřené do `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="f0952-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="f0952-104">`Function` Postup provede úlohu a potom se vrátí ovládací prvek volání kódu.</span><span class="sxs-lookup"><span data-stu-id="f0952-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="f0952-105">Až se obnoví ovládací prvek, také vrátí hodnotu, voláním kódu.</span><span class="sxs-lookup"><span data-stu-id="f0952-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="f0952-106">Při každém volání procedury, jeho příkazy spustit, počínaje prvním příkazem spustitelný soubor po `Function` prohlášení a ukončuje se první `End Function`, `Exit Function`, nebo `Return` byl zjištěn příkaz.</span><span class="sxs-lookup"><span data-stu-id="f0952-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="f0952-107">Můžete definovat `Function` postupu v modulu, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="f0952-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="f0952-108">Je `Public` ve výchozím nastavení, což znamená, můžete ji volat z libovolného místa ve vaší aplikaci, která má přístup k modulu, třídu nebo strukturu, ve kterém jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="f0952-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="f0952-109">A `Function` postup může trvat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou k němu předaná volající kód.</span><span class="sxs-lookup"><span data-stu-id="f0952-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f0952-110">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="f0952-110">Declaration Syntax</span></span>  
 <span data-ttu-id="f0952-111">Syntaxe deklarace `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="f0952-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="f0952-112">*Modifikátory* můžete zadat úroveň přístupu a informací o přetížení, přepsání, sdílení a stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="f0952-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="f0952-113">Další informace najdete v tématu [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0952-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="f0952-114">Deklarovat každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f0952-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="f0952-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0952-115">Data Type</span></span>  
 <span data-ttu-id="f0952-116">Každý `Function` postup má datový typ, stejně jako všechny proměnné nemá.</span><span class="sxs-lookup"><span data-stu-id="f0952-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="f0952-117">Tento typ dat je zadána `As` klauzuli v `Function` příkaz a určuje datový typ hodnoty, vrátí funkce volání kódu.</span><span class="sxs-lookup"><span data-stu-id="f0952-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="f0952-118">Následující ukázka deklarace znázornění.</span><span class="sxs-lookup"><span data-stu-id="f0952-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="f0952-119">Další informace najdete v tématu "Částí" v [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0952-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="f0952-120">Návrat hodnot</span><span class="sxs-lookup"><span data-stu-id="f0952-120">Returning Values</span></span>  
 <span data-ttu-id="f0952-121">Hodnota `Function` postup odesílá zpět do volání kódu se nazývá hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0952-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="f0952-122">Postup vrací hodnotu této v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="f0952-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="f0952-123">Použije `Return` příkaz k určení návratovou hodnotu a vrátí řídit okamžitě k volací program.</span><span class="sxs-lookup"><span data-stu-id="f0952-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="f0952-124">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f0952-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="f0952-125">Přiřadí hodnotu svůj vlastní název funkce v jednom či více příkazech procedury.</span><span class="sxs-lookup"><span data-stu-id="f0952-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="f0952-126">Řízení nevrátí volací program až `Exit Function` nebo `End Function` spustit příkaz.</span><span class="sxs-lookup"><span data-stu-id="f0952-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="f0952-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f0952-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="f0952-128">Výhodou přiřazení návratovou hodnotu pro název funkce je, dokud zjistí nevrací ovládací prvek v postupu `Exit Function` nebo `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f0952-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="f0952-129">To umožňuje přiřadit hodnotu předběžná a později upravit v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="f0952-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="f0952-130">Další informace o vrácení hodnot najdete v tématu [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0952-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="f0952-131">Informace o vrácení pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0952-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="f0952-132">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="f0952-132">Calling Syntax</span></span>  
 <span data-ttu-id="f0952-133">Vyvolání `Function` postupu včetně jeho název a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="f0952-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="f0952-134">Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="f0952-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="f0952-135">Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="f0952-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="f0952-136">Syntaxe volání `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="f0952-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="f0952-137">*lvalue*`=`*%{FunctionName/* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="f0952-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="f0952-138">`If ((` *%{FunctionName/* `[(` *argumentlist* `)] / 3) <=` *výraz* `) Then`</span><span class="sxs-lookup"><span data-stu-id="f0952-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="f0952-139">Při volání `Function` postupu, není nutné použít hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0952-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="f0952-140">Pokud ho použít nechcete, všechny akce, které funkce jsou prováděny, ale vrácená hodnota je ignorována.</span><span class="sxs-lookup"><span data-stu-id="f0952-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="f0952-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> se často nazývá tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="f0952-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="f0952-142">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="f0952-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="f0952-143">Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0952-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="f0952-144">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="f0952-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f0952-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0952-145">See Also</span></span>  
 [<span data-ttu-id="f0952-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0952-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f0952-147">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="f0952-147">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="f0952-148">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f0952-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="f0952-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="f0952-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="f0952-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="f0952-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f0952-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="f0952-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="f0952-152">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="f0952-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="f0952-153">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="f0952-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="f0952-154">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="f0952-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
