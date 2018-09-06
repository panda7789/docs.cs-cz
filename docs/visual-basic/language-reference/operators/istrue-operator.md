---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bf81384b0cecfd1ee3d438e4463949381279a181
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785189"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="3642d-102">IsTrue – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3642d-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="3642d-103">Určuje, zda je výraz `True`.</span><span class="sxs-lookup"><span data-stu-id="3642d-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="3642d-104">Nejde volat `IsTrue` explicitně v kódu, ale jazyka Visual Basic jej kompilátor může použít ke generování kódu z `OrElse` klauzule.</span><span class="sxs-lookup"><span data-stu-id="3642d-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="3642d-105">Pokud definujete třídu nebo strukturu a pak použít proměnnou daného typu v `OrElse` klauzule, je nutné definovat `IsTrue` na této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3642d-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="3642d-106">Kompilátor považuje `IsTrue` a `IsFalse` operátory jako *odpovídající dvojice*.</span><span class="sxs-lookup"><span data-stu-id="3642d-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="3642d-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhé.</span><span class="sxs-lookup"><span data-stu-id="3642d-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="3642d-108">Použití kompilátoru IsTrue</span><span class="sxs-lookup"><span data-stu-id="3642d-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="3642d-109">Po definování třídy nebo struktury, můžete použít proměnnou daného typu v `For`, `If`, `Else If`, nebo `While` příkazu, nebo `When` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3642d-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="3642d-110">Pokud to uděláte, kompilátor, vyžaduje operátor převede typ do `Boolean` hodnoty, aby ho mohli otestovat podmínku.</span><span class="sxs-lookup"><span data-stu-id="3642d-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="3642d-111">Vyhledá vhodný operátor v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="3642d-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="3642d-112">Rozšiřující operátor převodu z třídy nebo struktury `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3642d-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="3642d-113">Rozšiřující operátor převodu z třídy nebo struktury `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="3642d-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="3642d-114">`IsTrue` Operátor v třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3642d-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="3642d-115">Zužující převody na `Boolean?` , který nevyžaduje převod z `Boolean` k `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="3642d-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="3642d-116">Zužující operátor převodu z třídy nebo struktury `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3642d-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="3642d-117">Pokud jste nedefinovali jakýkoli převod na `Boolean` nebo `IsTrue` operátor signály kompilátor chybu.</span><span class="sxs-lookup"><span data-stu-id="3642d-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3642d-118">`IsTrue` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3642d-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="3642d-119">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="3642d-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3642d-120">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3642d-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3642d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="3642d-121">Example</span></span>  
 <span data-ttu-id="3642d-122">Následující příklad kódu definuje osnovy strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="3642d-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3642d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="3642d-123">See Also</span></span>  
 [<span data-ttu-id="3642d-124">Operátor IsFalse</span><span class="sxs-lookup"><span data-stu-id="3642d-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="3642d-125">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="3642d-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="3642d-126">Operátor OrElse</span><span class="sxs-lookup"><span data-stu-id="3642d-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
