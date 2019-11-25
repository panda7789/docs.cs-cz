---
title: 'Postupy: Definice operátora'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344864"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="599ed-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="599ed-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="599ed-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span><span class="sxs-lookup"><span data-stu-id="599ed-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="599ed-104">Define the standard operator as an operator procedure within the class or structure.</span><span class="sxs-lookup"><span data-stu-id="599ed-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="599ed-105">All operator procedures must be `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="599ed-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="599ed-106">Defining an operator on a class or structure is also called *overloading* the operator.</span><span class="sxs-lookup"><span data-stu-id="599ed-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="599ed-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="599ed-107">Example</span></span>  
 <span data-ttu-id="599ed-108">The following example defines the `+` operator for a structure called `height`.</span><span class="sxs-lookup"><span data-stu-id="599ed-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="599ed-109">The structure uses heights measured in feet and inches.</span><span class="sxs-lookup"><span data-stu-id="599ed-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="599ed-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span><span class="sxs-lookup"><span data-stu-id="599ed-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="599ed-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span><span class="sxs-lookup"><span data-stu-id="599ed-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="599ed-112">The `+` operator uses the constructor to generate normalized values.</span><span class="sxs-lookup"><span data-stu-id="599ed-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="599ed-113">You can test the structure `height` with the following code.</span><span class="sxs-lookup"><span data-stu-id="599ed-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="599ed-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="599ed-114">See also</span></span>

- [<span data-ttu-id="599ed-115">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="599ed-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="599ed-116">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="599ed-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="599ed-117">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="599ed-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="599ed-118">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="599ed-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="599ed-119">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="599ed-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="599ed-120">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="599ed-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="599ed-121">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="599ed-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="599ed-122">Operátor Mod</span><span class="sxs-lookup"><span data-stu-id="599ed-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
