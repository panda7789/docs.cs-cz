---
title: IsFalse – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349520"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="fa189-102">IsFalse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa189-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="fa189-103">Určuje, zda je výraz `False`.</span><span class="sxs-lookup"><span data-stu-id="fa189-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="fa189-104">Ve svém kódu nemůžete volat `IsFalse` explicitně, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `AndAlso` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="fa189-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="fa189-105">Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v klauzuli `AndAlso`, je nutné definovat `IsFalse` v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="fa189-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="fa189-106">Kompilátor považuje operátory `IsFalse` a `IsTrue` za *spárovaný pár*.</span><span class="sxs-lookup"><span data-stu-id="fa189-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="fa189-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.</span><span class="sxs-lookup"><span data-stu-id="fa189-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa189-108">Operátor `IsFalse` může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má jeho operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="fa189-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="fa189-109">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="fa189-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fa189-110">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fa189-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa189-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa189-111">Example</span></span>  
 <span data-ttu-id="fa189-112">Následující příklad kódu definuje obrys struktury, která obsahuje definice pro operátory `IsFalse` a `IsTrue`.</span><span class="sxs-lookup"><span data-stu-id="fa189-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="fa189-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa189-113">See also</span></span>

- [<span data-ttu-id="fa189-114">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="fa189-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="fa189-115">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="fa189-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="fa189-116">Operátor AndAlso</span><span class="sxs-lookup"><span data-stu-id="fa189-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
