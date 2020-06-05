---
title: IsFalse – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 7c5ad5fa0b72370eeb19fbaced88807570467552
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370671"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="8a87b-102">IsFalse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a87b-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="8a87b-103">Určuje, zda je výraz `False` .</span><span class="sxs-lookup"><span data-stu-id="8a87b-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="8a87b-104">Nemůžete volat `IsFalse` explicitně v kódu, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `AndAlso` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="8a87b-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="8a87b-105">Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v `AndAlso` klauzuli, je nutné definovat `IsFalse` v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="8a87b-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="8a87b-106">Kompilátor považuje `IsFalse` operátory a `IsTrue` za *spárované páry*.</span><span class="sxs-lookup"><span data-stu-id="8a87b-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="8a87b-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.</span><span class="sxs-lookup"><span data-stu-id="8a87b-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a87b-108">`IsFalse`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8a87b-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="8a87b-109">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="8a87b-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8a87b-110">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8a87b-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a87b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a87b-111">Example</span></span>  
 <span data-ttu-id="8a87b-112">Následující příklad kódu definuje obrys struktury, která obsahuje definice pro `IsFalse` `IsTrue` operátory a.</span><span class="sxs-lookup"><span data-stu-id="8a87b-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="8a87b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a87b-113">See also</span></span>

- [<span data-ttu-id="8a87b-114">IsTrue – operátor</span><span class="sxs-lookup"><span data-stu-id="8a87b-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="8a87b-115">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="8a87b-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8a87b-116">AndAlso – operátor</span><span class="sxs-lookup"><span data-stu-id="8a87b-116">AndAlso Operator</span></span>](andalso-operator.md)
