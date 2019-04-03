---
title: Volný převod delegáta (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 57e863d9781721a997ae49e1a5c9d8f3562a1bd0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842717"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="3fe67-102">Volný převod delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fe67-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="3fe67-103">Volný převod delegáta umožňuje přiřadit typu Sub a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou identické.</span><span class="sxs-lookup"><span data-stu-id="3fe67-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="3fe67-104">Proto vazbu na delegáty stane konzistentní s vazbou již povolena pro volání metod.</span><span class="sxs-lookup"><span data-stu-id="3fe67-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="3fe67-105">Parametry a návratový typ</span><span class="sxs-lookup"><span data-stu-id="3fe67-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="3fe67-106">Místo podpis přesnou shodu volný převod vyžaduje splnění následujících podmínek při `Option Strict` je nastavena na `On`:</span><span class="sxs-lookup"><span data-stu-id="3fe67-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="3fe67-107">Rozšiřující převod musí existovat od datového typu každý parametr delegáta na datový typ odpovídající parametr přiřazené funkce nebo `Sub`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="3fe67-108">V následujícím příkladu, delegát `Del1` má jeden parametr, `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="3fe67-109">Parametr `m` v přiřazené lambda výrazy musí mít datový typ, pro kterou je rozšiřující převod z `Integer`, jako například `Long` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="3fe67-110">Zužující převody jsou povolené jenom v případě `Option Strict` je nastavena na `Off`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
-   <span data-ttu-id="3fe67-111">Rozšiřující převod musí existovat v opačném směru z návratového typu funkce přiřazené nebo `Sub` na návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3fe67-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="3fe67-112">V následujících příkladech text každého přiřazené lambda výraz se musí vyhodnotit na datový typ, který rozšiřuje na `Integer` protože návratový typ `del1` je `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="3fe67-113">Pokud `Option Strict` je nastavena na `Off`, rozšiřující omezení se už v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="3fe67-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="3fe67-114">Vynechání specifikace parametru</span><span class="sxs-lookup"><span data-stu-id="3fe67-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="3fe67-115">Uvolněné delegáty lze také kompletně vynechat specifikace parametru v metodě přiřazené:</span><span class="sxs-lookup"><span data-stu-id="3fe67-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="3fe67-116">Mějte na paměti, že nelze zadat některé parametry a ostatní vynechat.</span><span class="sxs-lookup"><span data-stu-id="3fe67-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="3fe67-117">Umožňuje vynechat je užitečné v situaci, například definování obslužné rutiny události, kde se podílejí několik složité parametry.</span><span class="sxs-lookup"><span data-stu-id="3fe67-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="3fe67-118">Nejsou použity argumenty, které mají některé obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3fe67-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="3fe67-119">Místo toho obslužnou rutinu přímý přístup k stavu ovládacího prvku, na kterém je zaregistrován události a ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="3fe67-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="3fe67-120">Uvolněné delegáty umožňují vynechejte argumenty v těchto prohlášení, pokud žádný výsledek nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="3fe67-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="3fe67-121">V následujícím příkladu, plně zadanou metodu `OnClick` může být přepsán ve formátu `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="3fe67-122">Příklady AddressOf</span><span class="sxs-lookup"><span data-stu-id="3fe67-122">AddressOf Examples</span></span>  
 <span data-ttu-id="3fe67-123">Výrazy lambda se používají v předchozích příkladech k usnadnění vztahům typů zobrazíte.</span><span class="sxs-lookup"><span data-stu-id="3fe67-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="3fe67-124">Ale stejné zmírnění jsou povolené pro přiřazení delegáta, které používají `AddressOf`, `Handles`, nebo `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="3fe67-125">V následujícím příkladu se funkce `f1`, `f2`, `f3`, a `f4` je všechny možné přiřadit k `Del1`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="3fe67-126">Následující příklad je platný jenom v případě `Option Strict` je nastavena na `Off`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="3fe67-127">Přetažení funkce vrátí</span><span class="sxs-lookup"><span data-stu-id="3fe67-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="3fe67-128">Volný převod delegáta umožňuje přiřadit funkce, která se `Sub` delegáta, efektivní systém ignoroval návratovou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe67-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="3fe67-129">Však nelze přiřadit `Sub` delegáta funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe67-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="3fe67-130">V následujícím příkladu, adresu funkce `doubler` přiřazen `Sub` delegovat `Del3`.</span><span class="sxs-lookup"><span data-stu-id="3fe67-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3fe67-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fe67-131">See also</span></span>

- [<span data-ttu-id="3fe67-132">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="3fe67-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="3fe67-133">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="3fe67-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3fe67-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="3fe67-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="3fe67-135">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fe67-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="3fe67-136">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="3fe67-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3fe67-137">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="3fe67-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
