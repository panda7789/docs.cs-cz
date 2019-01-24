---
title: Sub – procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: f558c61d2e81471e167e97816ff47bc4465c5f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638116"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="10378-102">Sub – procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10378-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="10378-103">A `Sub` postup je řadu příkazů jazyka Visual Basic ohraničená `Sub` a `End Sub` příkazy.</span><span class="sxs-lookup"><span data-stu-id="10378-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="10378-104">`Sub` Postupu provede úlohu a potom vrátí řízení volajícímu kódu, ale nevrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="10378-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="10378-105">Pokaždé, když volání procedury, jeho příkazy jsou spouštěny, počínaje první spustitelný příkaz po `Sub` příkazu a končí prvním `End Sub`, `Exit Sub`, nebo `Return` byl zjištěn příkaz.</span><span class="sxs-lookup"><span data-stu-id="10378-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="10378-106">Můžete definovat `Sub` postupu na portále moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="10378-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="10378-107">Ve výchozím nastavení je to `Public`, což znamená, že ji volat z libovolného místa v aplikaci, která má přístup k modulu, třídy nebo struktury, ve kterém jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="10378-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="10378-108">Termín, *metoda*, popisuje `Sub` nebo `Function` proceduru, která přistupuje z mimo jeho definování modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="10378-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="10378-109">Další informace najdete v tématu [postupy](./index.md).</span><span class="sxs-lookup"><span data-stu-id="10378-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="10378-110">A `Sub` postupu můžete převzít argumenty, jako jsou konstanty, proměnné a výrazy, které jsou předávány do ní volající kód.</span><span class="sxs-lookup"><span data-stu-id="10378-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="10378-111">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="10378-111">Declaration Syntax</span></span>  
 <span data-ttu-id="10378-112">Syntaxe pro deklarování `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="10378-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="10378-113">`[` *Modifikátory* `] Sub` *subname* `[(` *seznam_parametrů*  `)]`</span><span class="sxs-lookup"><span data-stu-id="10378-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="10378-114">`modifiers` Můžete určit úroveň přístupu a informací o přetížení, přepsání, sdílení a stínování.</span><span class="sxs-lookup"><span data-stu-id="10378-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="10378-115">Další informace najdete v tématu [příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10378-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="10378-116">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="10378-116">Parameter Declaration</span></span>  
 <span data-ttu-id="10378-117">Deklarujete každý parametr procedury podobně a jak můžete deklarovat proměnnou, zadáte název a datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="10378-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="10378-118">Můžete také určit mechanismu předávání a určuje, zda se jedná o volitelný parametr, nebo pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="10378-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="10378-119">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="10378-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="10378-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *Název parametru*`As`*datový typ* </span><span class="sxs-lookup"><span data-stu-id="10378-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="10378-121">Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="10378-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="10378-122">Syntaxe pro určení výchozí hodnota je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="10378-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="10378-123">`Optional [ByVal | ByRef]`  *Název parametru*`As`*datový typ*`=`*defaultvalue* </span><span class="sxs-lookup"><span data-stu-id="10378-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="10378-124">Parametry jako lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="10378-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="10378-125">Při řízení se předá podle postupu, každý parametr je zpracováván jako místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="10378-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="10378-126">To znamená, že jeho životnost je stejný jako postup a jeho rozsah je celý postup.</span><span class="sxs-lookup"><span data-stu-id="10378-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="10378-127">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="10378-127">Calling Syntax</span></span>  
 <span data-ttu-id="10378-128">Vyvolání `Sub` postup explicitně pomocí samostatné volání příkazu.</span><span class="sxs-lookup"><span data-stu-id="10378-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="10378-129">Ji nelze volat pomocí jeho názvu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="10378-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="10378-130">Je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="10378-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="10378-131">Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="10378-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="10378-132">Použití `Call` – klíčové slovo je volitelné, ale nedoporučuje se.</span><span class="sxs-lookup"><span data-stu-id="10378-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="10378-133">Syntaxe pro volání `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="10378-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="10378-134">`[Call]`  *subname* `[(` *seznam_argumentů* `)]`</span><span class="sxs-lookup"><span data-stu-id="10378-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="10378-135">Můžete volat `Sub` metodu z vně třídy, který ji definuje.</span><span class="sxs-lookup"><span data-stu-id="10378-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="10378-136">Nejprve je nutné použít `New` – klíčové slovo k vytvoření instance třídy, nebo volat metodu, která vrací instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="10378-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="10378-137">Další informace najdete v tématu [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="10378-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="10378-138">Potom použijte následující syntaxi pro volání `Sub` metodu na instanci objektu:</span><span class="sxs-lookup"><span data-stu-id="10378-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="10378-139">*Objekt*. *methodName*`[(`*seznam_argumentů*`)]`</span><span class="sxs-lookup"><span data-stu-id="10378-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="10378-140">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="10378-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="10378-141">Následující `Sub` postup říká operátor počítače úloh, které aplikace se chystáte provést a také zobrazuje časové razítko.</span><span class="sxs-lookup"><span data-stu-id="10378-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="10378-142">Namísto duplikování tento kód na začátku každé úlohy, aplikace jen volá `tellOperator` z různých umístění.</span><span class="sxs-lookup"><span data-stu-id="10378-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="10378-143">Každé volání předává řetězcový v `task` argument, který identifikuje úlohy se spouští.</span><span class="sxs-lookup"><span data-stu-id="10378-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="10378-144">Následující příklad ukazuje typické volání `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="10378-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="10378-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10378-145">See also</span></span>
- [<span data-ttu-id="10378-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="10378-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="10378-147">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="10378-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="10378-148">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="10378-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="10378-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="10378-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="10378-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="10378-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="10378-151">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="10378-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="10378-152">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="10378-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="10378-153">Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10378-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
