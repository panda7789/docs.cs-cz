---
title: "Volný převod delegáta (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cca3d09b538905714f627c9fa006187b8927383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="8ea9f-102">Volný převod delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea9f-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="8ea9f-103">Volný převod delegáta umožňuje přiřadit předplatných a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou identické.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="8ea9f-104">Vazba na delegáty tedy stane konzistentní s vazbou již povolena pro volání metod.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="8ea9f-105">Parametry a návratový typ</span><span class="sxs-lookup"><span data-stu-id="8ea9f-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="8ea9f-106">Místo podpis přesnou shodu, volný převod vyžaduje splnění následujících podmínek při `Option Strict` je nastaven na `On`:</span><span class="sxs-lookup"><span data-stu-id="8ea9f-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="8ea9f-107">Rozšiřující převod musí existovat od datového typu parametru každý delegáta na datový typ parametru odpovídající funkce přiřazené nebo `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="8ea9f-108">V následujícím příkladu, delegát `Del1` má jeden parametr `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="8ea9f-109">Parametr `m` v přiřazené lambda výrazy musí mít datový typ, pro kterou je rozšiřující převod z `Integer`, jako například `Long` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="8ea9f-110">Zužující převody jsou povoleny pouze tehdy, když `Option Strict` je nastaven na `Off`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="8ea9f-111">Rozšiřující převod musí existovat v opačném směru z návratový typ funkce přiřazené nebo `Sub` návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="8ea9f-112">V následujících příkladech se musí text každého výrazu lambda přiřazené vyhodnotit datový typ, který rozšiřuje na `Integer` protože návratový typ `del1` je `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="8ea9f-113">Pokud `Option Strict` je nastaven na `Off`, v obou směrech rozšiřující omezení je odebrána.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="8ea9f-114">Vynechání parametru specifikace</span><span class="sxs-lookup"><span data-stu-id="8ea9f-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="8ea9f-115">Volný delegáti taky umožňují zcela vynechejte parametr specifikace v metodě přiřazené:</span><span class="sxs-lookup"><span data-stu-id="8ea9f-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="8ea9f-116">Všimněte si, nelze zadat některé parametry a ostatní vynechejte.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="8ea9f-117">Umožňuje vynechat parametry je užitečné v situaci, jako je například definování obslužné rutiny události, které se podílejí několika komplexní parametry.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="8ea9f-118">Argumenty, které mají některé obslužné rutiny událostí se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="8ea9f-119">Místo toho obslužná rutina přímý přístup k stavu ovládacího prvku, na kterém je zaregistrován události a ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="8ea9f-120">Volný Delegáti umožňují vynechejte argumentů taková deklarace, pokud žádný výsledek nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="8ea9f-121">V následujícím příkladu plně zadanou metodu `OnClick` může být přepsán jako `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="8ea9f-122">AddressOf příklady</span><span class="sxs-lookup"><span data-stu-id="8ea9f-122">AddressOf Examples</span></span>  
 <span data-ttu-id="8ea9f-123">Lambda – výrazy se používají v předchozích příkladech snadno zjistit, aby typ relace.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="8ea9f-124">Však stejné zmírnění jsou povoleny pro přiřazení delegáta, které používají `AddressOf`, `Handles`, nebo `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="8ea9f-125">V následujícím příkladu funkce `f1`, `f2`, `f3`, a `f4` lze všechny přiřadit k `Del1`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="8ea9f-126">Následující příklad je platný jenom v případě `Option Strict` je nastaven na `Off`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="8ea9f-127">Vrátí vyřazování – funkce</span><span class="sxs-lookup"><span data-stu-id="8ea9f-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="8ea9f-128">Volný převod delegáta umožňuje přiřadit funkce, která se `Sub` delegáta, efektivně ignoruje návratovou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="8ea9f-129">Však nelze přiřadit `Sub` k delegáta funkce.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="8ea9f-130">V následujícím příkladu, adresy funkce `doubler` je přiřazena k `Sub` delegovat `Del3`.</span><span class="sxs-lookup"><span data-stu-id="8ea9f-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8ea9f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ea9f-131">See Also</span></span>  
 [<span data-ttu-id="8ea9f-132">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="8ea9f-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="8ea9f-133">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="8ea9f-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="8ea9f-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="8ea9f-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="8ea9f-135">Postupy: předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ea9f-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="8ea9f-136">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="8ea9f-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="8ea9f-137">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="8ea9f-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
