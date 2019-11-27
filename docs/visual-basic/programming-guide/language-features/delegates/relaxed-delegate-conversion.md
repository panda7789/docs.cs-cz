---
title: Volný převod delegáta
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345220"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="250ab-102">Volný převod delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="250ab-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="250ab-103">Odlehčený převod delegáta umožňuje přiřadit vlastníky a funkce delegátům nebo obslužným rutinám, i když jejich signatury nejsou identické.</span><span class="sxs-lookup"><span data-stu-id="250ab-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="250ab-104">Proto vazba na delegáty se bude shodovat s vazbou, která je již povolena pro vyvolání metod.</span><span class="sxs-lookup"><span data-stu-id="250ab-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="250ab-105">Parametry a návratový typ</span><span class="sxs-lookup"><span data-stu-id="250ab-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="250ab-106">V případě shody přes přesný podpis vyžaduje odlehčený převod, aby při `Option Strict` nastavené na `On`byly splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="250ab-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="250ab-107">Rozšiřující převod musí existovat z datového typu každého parametru delegáta na datový typ odpovídajícího parametru přiřazené funkce nebo `Sub`.</span><span class="sxs-lookup"><span data-stu-id="250ab-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="250ab-108">V následujícím příkladu má delegát `Del1` jeden parametr, `Integer`.</span><span class="sxs-lookup"><span data-stu-id="250ab-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="250ab-109">Parametr `m` v přiřazených výrazech lambda musí mít datový typ, pro který existuje rozšiřující převod z `Integer`, jako je například `Long` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="250ab-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="250ab-110">Zužující převody jsou povoleny pouze v případě, že je `Option Strict` nastaveno na hodnotu `Off`.</span><span class="sxs-lookup"><span data-stu-id="250ab-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="250ab-111">Rozšiřující převod musí existovat v opačném směru od návratového typu přiřazené funkce nebo `Sub` k návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="250ab-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="250ab-112">V následujících příkladech se tělo každého přiřazeného výrazu lambda musí vyhodnotit na datový typ, který se rozšíří na `Integer`, protože návratový typ `del1` je `Integer`.</span><span class="sxs-lookup"><span data-stu-id="250ab-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="250ab-113">Pokud je `Option Strict` nastavené na `Off`, rozšiřující omezení se odebere v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="250ab-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="250ab-114">Vynechávání specifikací parametrů</span><span class="sxs-lookup"><span data-stu-id="250ab-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="250ab-115">Odlehčení Delegáti vám také umožní zcela vynechat specifikace parametrů v přiřazené metodě:</span><span class="sxs-lookup"><span data-stu-id="250ab-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="250ab-116">Všimněte si, že nemůžete zadat některé parametry a vynechat jiné.</span><span class="sxs-lookup"><span data-stu-id="250ab-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="250ab-117">Možnost vynechat parametry je užitečná v situaci, jako je například definování obslužné rutiny události, kde je zapojeno několik složitých parametrů.</span><span class="sxs-lookup"><span data-stu-id="250ab-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="250ab-118">Argumenty pro některé obslužné rutiny událostí se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="250ab-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="250ab-119">Místo toho obslužná rutina přímo přistupuje ke stavu ovládacího prvku, na kterém je událost zaregistrována, a ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="250ab-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="250ab-120">Odlehčení Delegáti umožňují vynechat argumenty v těchto prohlášeních, pokud výsledek nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="250ab-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="250ab-121">V následujícím příkladu lze jako `RelaxedOnClick`přepsat úplnou zadanou metodu `OnClick`.</span><span class="sxs-lookup"><span data-stu-id="250ab-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="250ab-122">AddressOf – příklady</span><span class="sxs-lookup"><span data-stu-id="250ab-122">AddressOf Examples</span></span>  
 <span data-ttu-id="250ab-123">Výrazy lambda se používají v předchozích příkladech k usnadnění zobrazení vztahů typů.</span><span class="sxs-lookup"><span data-stu-id="250ab-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="250ab-124">U přiřazení delegátů, které používají `AddressOf`, `Handles`nebo `AddHandler`je však povoleno stejné zmírnit.</span><span class="sxs-lookup"><span data-stu-id="250ab-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="250ab-125">V následujícím příkladu funkce `f1`, `f2`, `f3`a `f4`, mohou být přiřazeny `Del1`.</span><span class="sxs-lookup"><span data-stu-id="250ab-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="250ab-126">Následující příklad je platný, pouze pokud je `Option Strict` nastaveno na `Off`.</span><span class="sxs-lookup"><span data-stu-id="250ab-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="250ab-127">Vyhození funkcí vrátí</span><span class="sxs-lookup"><span data-stu-id="250ab-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="250ab-128">Odlehčený převod delegáta umožňuje přiřadit funkci delegátovi `Sub` a efektivně tak ignorovat vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="250ab-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="250ab-129">Nemůžete však přiřadit `Sub` delegátovi funkce.</span><span class="sxs-lookup"><span data-stu-id="250ab-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="250ab-130">V následujícím příkladu je adresa funkce `doubler` přiřazená `Sub` delegátům `Del3`.</span><span class="sxs-lookup"><span data-stu-id="250ab-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="250ab-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="250ab-131">See also</span></span>

- [<span data-ttu-id="250ab-132">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="250ab-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="250ab-133">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="250ab-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="250ab-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="250ab-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="250ab-135">Postupy: Předání procedur jinému postupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="250ab-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="250ab-136">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="250ab-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="250ab-137">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="250ab-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
