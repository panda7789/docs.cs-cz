---
title: "Sub – procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e20e0dd5ff9e2b931e5792bebb3144930826f89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="50745-102">Sub – procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50745-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="50745-103">A `Sub` postup je řadu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ohraničená příkazy `Sub` a `End Sub` příkazy.</span><span class="sxs-lookup"><span data-stu-id="50745-103">A `Sub` procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="50745-104">`Sub` Postup provede úlohu a vrátí ovládací prvek pro volací kód, ale nevrací hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="50745-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="50745-105">Při každém volání procedury, jeho příkazy jsou spouštěny, počínaje prvním příkazem spustitelný soubor po `Sub` prohlášení a ukončuje se první `End Sub`, `Exit Sub`, nebo `Return` byl zjištěn příkaz.</span><span class="sxs-lookup"><span data-stu-id="50745-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="50745-106">Můžete definovat `Sub` postup v moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="50745-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="50745-107">Ve výchozím nastavení, je `Public`, což znamená, že ji volat z libovolného místa ve vaší aplikaci, která má přístup k modulu, třídu nebo strukturu, ve kterém jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="50745-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="50745-108">Termín, *metoda*, popisuje `Sub` nebo `Function` procedury, která je k němu přistupovat z mimo jeho definování modulu, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="50745-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="50745-109">Další informace najdete v tématu [postupy](./index.md).</span><span class="sxs-lookup"><span data-stu-id="50745-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="50745-110">A `Sub` postup může trvat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou k němu předaná volající kód.</span><span class="sxs-lookup"><span data-stu-id="50745-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="50745-111">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="50745-111">Declaration Syntax</span></span>  
 <span data-ttu-id="50745-112">Syntaxe deklarace `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="50745-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="50745-113">`[`*modifikátory* `] Sub` *subname* `[(` *parameterlist*  `)]`</span><span class="sxs-lookup"><span data-stu-id="50745-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="50745-114">`modifiers` Můžete zadat úroveň přístupu a informace o přetížení, přepsání, sdílení a stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="50745-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="50745-115">Další informace najdete v tématu [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="50745-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="50745-116">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="50745-116">Parameter Declaration</span></span>  
 <span data-ttu-id="50745-117">Je deklarovat každý parametr postup podobně a jak je deklarovat proměnnou, zadat název a datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="50745-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="50745-118">Můžete také určit mechanismus předávání a zda se jedná o volitelný parametr nebo pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="50745-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="50745-119">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="50745-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="50745-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *Název parametru*`As`*datový typ* </span><span class="sxs-lookup"><span data-stu-id="50745-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="50745-121">Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu v rámci jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="50745-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="50745-122">Syntaxe pro určení výchozí hodnota je následující:</span><span class="sxs-lookup"><span data-stu-id="50745-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="50745-123">`Optional [ByVal | ByRef]`  *Název parametru*`As`*datový typ*`=`*defaultvalue* </span><span class="sxs-lookup"><span data-stu-id="50745-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="50745-124">Parametry jako lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="50745-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="50745-125">Pokud ovládací prvek předává do procesu, každý parametr je považovat za místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="50745-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="50745-126">To znamená, že jeho životnost je stejný jako postup, a její obor je celý postup.</span><span class="sxs-lookup"><span data-stu-id="50745-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="50745-127">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="50745-127">Calling Syntax</span></span>  
 <span data-ttu-id="50745-128">Vyvolání `Sub` postup explicitně příkazem samostatné volání.</span><span class="sxs-lookup"><span data-stu-id="50745-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="50745-129">Ji nelze volat pomocí jeho názvu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="50745-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="50745-130">Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="50745-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="50745-131">Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="50745-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="50745-132">Použití `Call` – klíčové slovo je volitelné, ale nedoporučuje se.</span><span class="sxs-lookup"><span data-stu-id="50745-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="50745-133">Syntaxe volání `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="50745-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="50745-134">`[Call]`  *subname* `[(` *argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="50745-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="50745-135">Můžete volat `Sub` metody z mimo třídu, která ho definuje.</span><span class="sxs-lookup"><span data-stu-id="50745-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="50745-136">Nejprve budete muset použít `New` – klíčové slovo k vytvoření instance třídy nebo volání metody, které vrací instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="50745-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="50745-137">Další informace najdete v tématu [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="50745-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="50745-138">Pak použijte následující syntaxi pro volání `Sub` metoda instance objektu:</span><span class="sxs-lookup"><span data-stu-id="50745-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="50745-139">*Objekt*. *methodName*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="50745-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="50745-140">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="50745-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="50745-141">Následující `Sub` postup informuje operátor počítače úloh, které aplikace se chystáte provést a také zobrazuje časové razítko.</span><span class="sxs-lookup"><span data-stu-id="50745-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="50745-142">Místo duplikování tento kód na začátku každé úloze, aplikace právě volá `tellOperator` z různých umístění.</span><span class="sxs-lookup"><span data-stu-id="50745-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="50745-143">Každé volání předá řetězec `task` argument, který identifikuje úkol spuštění.</span><span class="sxs-lookup"><span data-stu-id="50745-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="50745-144">Následující příklad ukazuje typické volání `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="50745-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50745-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="50745-145">See Also</span></span>  
 [<span data-ttu-id="50745-146">Postupy</span><span class="sxs-lookup"><span data-stu-id="50745-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="50745-147">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="50745-147">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="50745-148">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="50745-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="50745-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="50745-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="50745-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="50745-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="50745-151">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="50745-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="50745-152">Postupy: volání procedury, která nevrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="50745-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [<span data-ttu-id="50745-153">Postupy: volání obslužné rutiny událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50745-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
