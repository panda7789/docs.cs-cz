---
title: Volný převod delegáta
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410667"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="7ffed-102">Volný převod delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ffed-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="7ffed-103">Odlehčený převod delegáta umožňuje přiřadit vlastníky a funkce delegátům nebo obslužným rutinám, i když jejich signatury nejsou identické.</span><span class="sxs-lookup"><span data-stu-id="7ffed-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="7ffed-104">Proto vazba na delegáty se bude shodovat s vazbou, která je již povolena pro vyvolání metod.</span><span class="sxs-lookup"><span data-stu-id="7ffed-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="7ffed-105">Parametry a návratový typ</span><span class="sxs-lookup"><span data-stu-id="7ffed-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="7ffed-106">Místo přesné shody signatury vyžaduje odlehčený převod, aby byly splněny následující podmínky, pokud `Option Strict` je nastavena na `On` :</span><span class="sxs-lookup"><span data-stu-id="7ffed-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="7ffed-107">Rozšiřující převod musí existovat z datového typu každého parametru delegáta na datový typ odpovídajícího parametru přiřazené funkce nebo `Sub` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="7ffed-108">V následujícím příkladu `Del1` má delegát jeden parametr, a `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="7ffed-109">Parametr `m` v přiřazených výrazech lambda musí mít datový typ, pro který existuje rozšiřující převod z `Integer` , například `Long` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="7ffed-110">Zužující převody jsou povoleny pouze v případě `Option Strict` , že je nastavena na `Off` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="7ffed-111">Rozšiřující převod musí existovat v opačném směru od návratového typu přiřazené funkce nebo `Sub` na návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="7ffed-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="7ffed-112">V následujících příkladech se tělo každého přiřazeného výrazu lambda musí vyhodnotit na datový typ, který se rozšíří, `Integer` protože návratový typ `del1` je `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="7ffed-113">Pokud `Option Strict` je nastavená na `Off` , rozšiřující omezení se odebere v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="7ffed-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="7ffed-114">Vynechávání specifikací parametrů</span><span class="sxs-lookup"><span data-stu-id="7ffed-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="7ffed-115">Odlehčení Delegáti vám také umožní zcela vynechat specifikace parametrů v přiřazené metodě:</span><span class="sxs-lookup"><span data-stu-id="7ffed-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="7ffed-116">Všimněte si, že nemůžete zadat některé parametry a vynechat jiné.</span><span class="sxs-lookup"><span data-stu-id="7ffed-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="7ffed-117">Možnost vynechat parametry je užitečná v situaci, jako je například definování obslužné rutiny události, kde je zapojeno několik složitých parametrů.</span><span class="sxs-lookup"><span data-stu-id="7ffed-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="7ffed-118">Argumenty pro některé obslužné rutiny událostí se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="7ffed-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="7ffed-119">Místo toho obslužná rutina přímo přistupuje ke stavu ovládacího prvku, na kterém je událost zaregistrována, a ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="7ffed-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="7ffed-120">Odlehčení Delegáti umožňují vynechat argumenty v těchto prohlášeních, pokud výsledek nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="7ffed-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="7ffed-121">V následujícím příkladu lze úplnou zadanou metodu `OnClick` přepsat jako `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="7ffed-122">AddressOf – příklady</span><span class="sxs-lookup"><span data-stu-id="7ffed-122">AddressOf Examples</span></span>  
 <span data-ttu-id="7ffed-123">Výrazy lambda se používají v předchozích příkladech k usnadnění zobrazení vztahů typů.</span><span class="sxs-lookup"><span data-stu-id="7ffed-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="7ffed-124">U přiřazení delegátů, které používají, nebo jsou však povolena stejná `AddressOf` zmírnění `Handles` `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="7ffed-125">V následujícím příkladu funkce,, `f1` `f2` `f3` a `f4` mohou být přiřazeny k `Del1` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="7ffed-126">Následující příklad je platný pouze v případě `Option Strict` , že je nastavena na `Off` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="7ffed-127">Vyhození funkcí vrátí</span><span class="sxs-lookup"><span data-stu-id="7ffed-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="7ffed-128">Odlehčený převod delegáta umožňuje přiřadit funkci `Sub` delegátovi a efektivně tak ignorovat vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="7ffed-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="7ffed-129">Nemůžete však přiřadit `Sub` delegáta funkce.</span><span class="sxs-lookup"><span data-stu-id="7ffed-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="7ffed-130">V následujícím příkladu je adresa funkce `doubler` přiřazena `Sub` delegátovi `Del3` .</span><span class="sxs-lookup"><span data-stu-id="7ffed-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7ffed-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ffed-131">See also</span></span>

- [<span data-ttu-id="7ffed-132">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="7ffed-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="7ffed-133">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="7ffed-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="7ffed-134">Delegáti</span><span class="sxs-lookup"><span data-stu-id="7ffed-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="7ffed-135">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ffed-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="7ffed-136">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="7ffed-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="7ffed-137">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="7ffed-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
