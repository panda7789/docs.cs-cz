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
ms.openlocfilehash: 4fd24369380e5f8ccf8de939c36ba72a12dc872e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649619"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="3afe8-102">Procedury funkcí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3afe8-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="3afe8-103">A `Function` postup je řadu příkazů jazyka Visual Basic ohraničená `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3afe8-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="3afe8-104">`Function` Postupu provede úlohu a potom vrátí řízení volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="3afe8-105">Když vrátí řízení, také vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="3afe8-106">Pokaždé, když volání procedury, jeho příkazy, počínaje první spustitelný příkaz po `Function` příkazu a končí prvním `End Function`, `Exit Function`, nebo `Return` byl zjištěn příkaz.</span><span class="sxs-lookup"><span data-stu-id="3afe8-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="3afe8-107">Můžete definovat `Function` postupu v modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3afe8-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="3afe8-108">Je `Public` ve výchozím nastavení, což znamená, že ho můžete volat z libovolného místa v aplikaci, která má přístup k modulu, třídy nebo struktury, ve kterém jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="3afe8-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="3afe8-109">A `Function` postupu můžete převzít argumenty, jako jsou konstanty, proměnné a výrazy, které jsou předávány do ní volající kód.</span><span class="sxs-lookup"><span data-stu-id="3afe8-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="3afe8-110">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="3afe8-110">Declaration Syntax</span></span>  
 <span data-ttu-id="3afe8-111">Syntaxe pro deklarování `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="3afe8-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="3afe8-112">*Modifikátory* můžete určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování.</span><span class="sxs-lookup"><span data-stu-id="3afe8-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="3afe8-113">Další informace najdete v tématu [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3afe8-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="3afe8-114">Deklarujete každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3afe8-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="3afe8-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3afe8-115">Data Type</span></span>  
 <span data-ttu-id="3afe8-116">Každý `Function` postupu má datový typ, stejně jako každá proměnná nemá.</span><span class="sxs-lookup"><span data-stu-id="3afe8-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="3afe8-117">Tento typ dat je určená `As` klauzule `Function` příkaz který určuje datový typ hodnoty, vrátí funkce hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="3afe8-118">Následující ukázka deklarace ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="3afe8-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="3afe8-119">Další informace najdete v tématu "Části" [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3afe8-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="3afe8-120">Vrací hodnoty</span><span class="sxs-lookup"><span data-stu-id="3afe8-120">Returning Values</span></span>  
 <span data-ttu-id="3afe8-121">Hodnota `Function` postup odešle zpět volajícímu kódu nazývá jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="3afe8-122">Postup vrátí tuto hodnotu v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="3afe8-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="3afe8-123">Používá `Return` příkaz a zadejte návratovou hodnotu a vrátí řízení okamžitě na volající program.</span><span class="sxs-lookup"><span data-stu-id="3afe8-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="3afe8-124">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3afe8-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="3afe8-125">Přiřadí hodnotu svůj vlastní název funkce v jeden nebo více příkazů procedury.</span><span class="sxs-lookup"><span data-stu-id="3afe8-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="3afe8-126">Ovládací prvek nevrací do volajícího programu do `Exit Function` nebo `End Function` je proveden příkaz.</span><span class="sxs-lookup"><span data-stu-id="3afe8-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="3afe8-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3afe8-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="3afe8-128">Výhodou přiřazení návratovou hodnotu pro název funkce je, dokud nenarazí nevrátí řízení z procedury `Exit Function` nebo `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="3afe8-129">To umožňuje přiřadit hodnotu předběžné a upravte ho později, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="3afe8-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="3afe8-130">Další informace o vrácení hodnot najdete v tématu [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3afe8-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="3afe8-131">Informace o vrácení pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3afe8-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="3afe8-132">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="3afe8-132">Calling Syntax</span></span>  
 <span data-ttu-id="3afe8-133">Vyvolání `Function` proceduru včetně jejího názvu a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="3afe8-134">Je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="3afe8-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="3afe8-135">Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="3afe8-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="3afe8-136">Syntaxe pro volání `Function` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="3afe8-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="3afe8-137">*l-hodnoty*`=`*functionname* `[(` *seznam_argumentů* `)]`</span><span class="sxs-lookup"><span data-stu-id="3afe8-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="3afe8-138">`If ((` *FunctionName* `[(` *seznam_argumentů* `)] / 3) <=` *výraz* `) Then`</span><span class="sxs-lookup"><span data-stu-id="3afe8-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="3afe8-139">Při volání `Function` procedury, není nutné používat jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3afe8-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="3afe8-140">Pokud ho nevidíte, jsou provedeny všechny akce funkce, ale je návratová hodnota ignorována.</span><span class="sxs-lookup"><span data-stu-id="3afe8-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="3afe8-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> se často nazývá tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3afe8-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="3afe8-142">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="3afe8-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="3afe8-143">Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3afe8-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3afe8-144">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="3afe8-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3afe8-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3afe8-145">See also</span></span>

- [<span data-ttu-id="3afe8-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="3afe8-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3afe8-147">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="3afe8-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="3afe8-148">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3afe8-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3afe8-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3afe8-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="3afe8-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="3afe8-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3afe8-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="3afe8-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3afe8-152">Postupy: Vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="3afe8-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="3afe8-153">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="3afe8-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="3afe8-154">Postupy: Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="3afe8-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
