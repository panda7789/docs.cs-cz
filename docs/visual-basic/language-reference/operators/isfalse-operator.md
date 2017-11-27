---
title: "IsFalse – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="54ce2-102">IsFalse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54ce2-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="54ce2-103">Určuje, zda je výraz `False`.</span><span class="sxs-lookup"><span data-stu-id="54ce2-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="54ce2-104">Nelze volat `IsFalse` explicitně v kódu, ale Visual Basicu kompilátoru můžete ji použít k generování kódu z `AndAlso` klauzule.</span><span class="sxs-lookup"><span data-stu-id="54ce2-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="54ce2-105">Pokud můžete definovat třídu nebo strukturu a potom pomocí proměnné daného typu v `AndAlso` klauzule, je nutné definovat `IsFalse` na tuto třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="54ce2-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="54ce2-106">Kompilátor zvažuje `IsFalse` a `IsTrue` operátory jako *odpovídá páru*.</span><span class="sxs-lookup"><span data-stu-id="54ce2-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="54ce2-107">To znamená, že pokud jeden z nich definujete, je nutné také definovat jiného.</span><span class="sxs-lookup"><span data-stu-id="54ce2-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54ce2-108">`IsFalse` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="54ce2-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="54ce2-109">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="54ce2-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="54ce2-110">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="54ce2-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54ce2-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="54ce2-111">Example</span></span>  
 <span data-ttu-id="54ce2-112">Následující příklad kódu definuje obrys strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="54ce2-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="54ce2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="54ce2-113">See Also</span></span>  
 [<span data-ttu-id="54ce2-114">IsTrue – operátor</span><span class="sxs-lookup"><span data-stu-id="54ce2-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="54ce2-115">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="54ce2-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="54ce2-116">AndAlso – operátor</span><span class="sxs-lookup"><span data-stu-id="54ce2-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
