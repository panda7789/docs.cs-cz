---
title: Sub – procedury
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352524"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="fce12-102">Sub – procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fce12-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="fce12-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span><span class="sxs-lookup"><span data-stu-id="fce12-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="fce12-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="fce12-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="fce12-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span><span class="sxs-lookup"><span data-stu-id="fce12-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="fce12-106">You can define a `Sub` procedure in modules, classes, and structures.</span><span class="sxs-lookup"><span data-stu-id="fce12-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="fce12-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span><span class="sxs-lookup"><span data-stu-id="fce12-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="fce12-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="fce12-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="fce12-109">For more information, see [Procedures](./index.md).</span><span class="sxs-lookup"><span data-stu-id="fce12-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="fce12-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span><span class="sxs-lookup"><span data-stu-id="fce12-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="fce12-111">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="fce12-111">Declaration Syntax</span></span>  
 <span data-ttu-id="fce12-112">The syntax for declaring a `Sub` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="fce12-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fce12-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="fce12-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="fce12-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span><span class="sxs-lookup"><span data-stu-id="fce12-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="fce12-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fce12-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="fce12-116">Parameter Declaration</span><span class="sxs-lookup"><span data-stu-id="fce12-116">Parameter Declaration</span></span>  
 <span data-ttu-id="fce12-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span><span class="sxs-lookup"><span data-stu-id="fce12-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="fce12-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span><span class="sxs-lookup"><span data-stu-id="fce12-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="fce12-119">The syntax for each parameter in the parameter list is as follows:</span><span class="sxs-lookup"><span data-stu-id="fce12-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="fce12-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="fce12-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="fce12-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span><span class="sxs-lookup"><span data-stu-id="fce12-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="fce12-122">The syntax for specifying a default value is as follows:</span><span class="sxs-lookup"><span data-stu-id="fce12-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="fce12-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span><span class="sxs-lookup"><span data-stu-id="fce12-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="fce12-124">Parameters as Local Variables</span><span class="sxs-lookup"><span data-stu-id="fce12-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="fce12-125">When control passes to the procedure, each parameter is treated as a local variable.</span><span class="sxs-lookup"><span data-stu-id="fce12-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="fce12-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span><span class="sxs-lookup"><span data-stu-id="fce12-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="fce12-127">Calling Syntax</span><span class="sxs-lookup"><span data-stu-id="fce12-127">Calling Syntax</span></span>  
 <span data-ttu-id="fce12-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span><span class="sxs-lookup"><span data-stu-id="fce12-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="fce12-129">You cannot call it by using its name in an expression.</span><span class="sxs-lookup"><span data-stu-id="fce12-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="fce12-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="fce12-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="fce12-131">If no arguments are supplied, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="fce12-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="fce12-132">The use of the `Call` keyword is optional but not recommended.</span><span class="sxs-lookup"><span data-stu-id="fce12-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="fce12-133">The syntax for a call to a `Sub` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="fce12-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fce12-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="fce12-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="fce12-135">You can call a `Sub` method from outside the class that defines it.</span><span class="sxs-lookup"><span data-stu-id="fce12-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="fce12-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span><span class="sxs-lookup"><span data-stu-id="fce12-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="fce12-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fce12-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="fce12-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span><span class="sxs-lookup"><span data-stu-id="fce12-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="fce12-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="fce12-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="fce12-140">Illustration of Declaration and Call</span><span class="sxs-lookup"><span data-stu-id="fce12-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="fce12-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span><span class="sxs-lookup"><span data-stu-id="fce12-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="fce12-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span><span class="sxs-lookup"><span data-stu-id="fce12-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="fce12-143">Each call passes a string in the `task` argument that identifies the task being started.</span><span class="sxs-lookup"><span data-stu-id="fce12-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="fce12-144">The following example shows a typical call to `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="fce12-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fce12-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fce12-145">See also</span></span>

- [<span data-ttu-id="fce12-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="fce12-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fce12-147">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="fce12-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="fce12-148">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fce12-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="fce12-149">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="fce12-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="fce12-150">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="fce12-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fce12-151">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="fce12-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fce12-152">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="fce12-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="fce12-153">How to: Call an Event Handler in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fce12-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
