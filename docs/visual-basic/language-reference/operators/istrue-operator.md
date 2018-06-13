---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605144"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="84a2d-102">IsTrue – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84a2d-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="84a2d-103">Určuje, zda je výraz `True`.</span><span class="sxs-lookup"><span data-stu-id="84a2d-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="84a2d-104">Nelze volat `IsTrue` explicitně v kódu, ale Visual Basicu kompilátoru můžete ji použít k generování kódu z `OrElse` klauzule.</span><span class="sxs-lookup"><span data-stu-id="84a2d-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="84a2d-105">Pokud můžete definovat třídu nebo strukturu a potom pomocí proměnné daného typu v `OrElse` klauzule, je nutné definovat `IsTrue` na tuto třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="84a2d-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="84a2d-106">Kompilátor zvažuje `IsTrue` a `IsFalse` operátory jako *odpovídá páru*.</span><span class="sxs-lookup"><span data-stu-id="84a2d-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="84a2d-107">To znamená, že pokud jeden z nich definujete, je nutné také definovat jiného.</span><span class="sxs-lookup"><span data-stu-id="84a2d-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="84a2d-108">IsTrue – použití kompilátoru</span><span class="sxs-lookup"><span data-stu-id="84a2d-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="84a2d-109">Pokud jste definovali třídu nebo strukturu, můžete použít proměnné daného typu v `For`, `If`, `Else``If`, nebo `While` prohlášení, nebo v `When` klauzule.</span><span class="sxs-lookup"><span data-stu-id="84a2d-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="84a2d-110">Pokud to uděláte, vyžaduje kompilátor operátor, který převede do vašeho typu `Boolean` hodnotu, takže ho můžete otestovat podmínku.</span><span class="sxs-lookup"><span data-stu-id="84a2d-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="84a2d-111">Vyhledá vhodný operátor v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="84a2d-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="84a2d-112">Rozšiřující operátora převodu z třídy nebo k strukturu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="84a2d-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="84a2d-113">Rozšiřující operátora převodu z třídy nebo k strukturu `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="84a2d-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="84a2d-114">`IsTrue` Operátor na třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="84a2d-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="84a2d-115">Zužující převody na `Boolean?` nezahrnuje převod z `Boolean` k `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="84a2d-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="84a2d-116">Narrowing operátora převodu z třídy nebo k strukturu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="84a2d-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="84a2d-117">Pokud nebyly definovány žádné převod na `Boolean` nebo `IsTrue` operátor, kompilátor nevydá signál k chybě.</span><span class="sxs-lookup"><span data-stu-id="84a2d-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84a2d-118">`IsTrue` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="84a2d-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="84a2d-119">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="84a2d-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="84a2d-120">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="84a2d-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a2d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="84a2d-121">Example</span></span>  
 <span data-ttu-id="84a2d-122">Následující příklad kódu definuje obrys strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="84a2d-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="84a2d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="84a2d-123">See Also</span></span>  
 [<span data-ttu-id="84a2d-124">Operátor IsFalse</span><span class="sxs-lookup"><span data-stu-id="84a2d-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="84a2d-125">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="84a2d-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="84a2d-126">Operátor OrElse</span><span class="sxs-lookup"><span data-stu-id="84a2d-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
