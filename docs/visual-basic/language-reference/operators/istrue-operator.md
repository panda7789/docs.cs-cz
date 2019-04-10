---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 6c5ec6d953d174b525dee7ad3034d2d01ae4950f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344946"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="b58e7-102">IsTrue – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b58e7-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="b58e7-103">Určuje, zda je výraz `True`.</span><span class="sxs-lookup"><span data-stu-id="b58e7-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="b58e7-104">Nejde volat `IsTrue` explicitně v kódu, ale jazyka Visual Basic jej kompilátor může použít ke generování kódu z `OrElse` klauzule.</span><span class="sxs-lookup"><span data-stu-id="b58e7-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="b58e7-105">Pokud definujete třídu nebo strukturu a pak použít proměnnou daného typu v `OrElse` klauzule, je nutné definovat `IsTrue` na této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b58e7-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="b58e7-106">Kompilátor považuje `IsTrue` a `IsFalse` operátory jako *odpovídající dvojice*.</span><span class="sxs-lookup"><span data-stu-id="b58e7-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="b58e7-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhé.</span><span class="sxs-lookup"><span data-stu-id="b58e7-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="b58e7-108">Použití kompilátoru IsTrue</span><span class="sxs-lookup"><span data-stu-id="b58e7-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="b58e7-109">Po definování třídy nebo struktury, můžete použít proměnnou daného typu v `For`, `If`, `Else If`, nebo `While` příkazu, nebo `When` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b58e7-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="b58e7-110">Pokud to uděláte, kompilátor, vyžaduje operátor převede typ do `Boolean` hodnoty, aby ho mohli otestovat podmínku.</span><span class="sxs-lookup"><span data-stu-id="b58e7-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="b58e7-111">Vyhledá vhodný operátor v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="b58e7-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="b58e7-112">Rozšiřující operátor převodu z třídy nebo struktury `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b58e7-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="b58e7-113">Rozšiřující operátor převodu z třídy nebo struktury `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="b58e7-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="b58e7-114">`IsTrue` Operátor v třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b58e7-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="b58e7-115">Zužující převody na `Boolean?` , který nevyžaduje převod z `Boolean` k `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="b58e7-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="b58e7-116">Zužující operátor převodu z třídy nebo struktury `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b58e7-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="b58e7-117">Pokud jste nedefinovali jakýkoli převod na `Boolean` nebo `IsTrue` operátor signály kompilátor chybu.</span><span class="sxs-lookup"><span data-stu-id="b58e7-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b58e7-118">`IsTrue` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b58e7-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="b58e7-119">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="b58e7-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b58e7-120">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b58e7-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b58e7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="b58e7-121">Example</span></span>  
 <span data-ttu-id="b58e7-122">Následující příklad kódu definuje osnovy strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="b58e7-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="b58e7-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b58e7-123">See also</span></span>

- [<span data-ttu-id="b58e7-124">IsFalse – operátor</span><span class="sxs-lookup"><span data-stu-id="b58e7-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="b58e7-125">Postupy: Definování operátoru</span><span class="sxs-lookup"><span data-stu-id="b58e7-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="b58e7-126">OrElse – operátor</span><span class="sxs-lookup"><span data-stu-id="b58e7-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
