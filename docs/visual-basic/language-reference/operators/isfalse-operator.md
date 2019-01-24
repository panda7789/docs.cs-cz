---
title: IsFalse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: ec8d7bcd2f4ca3fb1c74f4edcf6ec8af78fd144d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740415"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="f50cb-102">IsFalse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f50cb-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="f50cb-103">Určuje, zda je výraz `False`.</span><span class="sxs-lookup"><span data-stu-id="f50cb-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="f50cb-104">Nejde volat `IsFalse` explicitně v kódu, ale jazyka Visual Basic jej kompilátor může použít ke generování kódu z `AndAlso` klauzule.</span><span class="sxs-lookup"><span data-stu-id="f50cb-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="f50cb-105">Pokud definujete třídu nebo strukturu a pak použít proměnnou daného typu v `AndAlso` klauzule, je nutné definovat `IsFalse` na této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="f50cb-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="f50cb-106">Kompilátor považuje `IsFalse` a `IsTrue` operátory jako *odpovídající dvojice*.</span><span class="sxs-lookup"><span data-stu-id="f50cb-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="f50cb-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhé.</span><span class="sxs-lookup"><span data-stu-id="f50cb-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50cb-108">`IsFalse` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="f50cb-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f50cb-109">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="f50cb-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f50cb-110">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f50cb-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50cb-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f50cb-111">Example</span></span>  
 <span data-ttu-id="f50cb-112">Následující příklad kódu definuje osnovy strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="f50cb-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f50cb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f50cb-113">See also</span></span>
- [<span data-ttu-id="f50cb-114">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="f50cb-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="f50cb-115">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="f50cb-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="f50cb-116">Operátor AndAlso</span><span class="sxs-lookup"><span data-stu-id="f50cb-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
