---
title: 'Postupy: Definice operátora (Visual Basic)'
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
ms.openlocfilehash: 1f5a020a710cecdfd8722a9fca0a8b329697eced
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805396"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="32432-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32432-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="32432-103">Pokud jste definovali třídu nebo strukturu, můžete definovat chování standardní operátor (například `*`, `<>`, nebo `And`) Pokud je jedna nebo obě sady operandy typu třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="32432-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="32432-104">Definujte standardní operátor jako procedury operátora v rámci třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="32432-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="32432-105">Musí být všechny postupy operátor `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="32432-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="32432-106">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="32432-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32432-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="32432-107">Example</span></span>  
 <span data-ttu-id="32432-108">V následujícím příkladu je definován `+` názvem operátor pro strukturu `height`.</span><span class="sxs-lookup"><span data-stu-id="32432-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="32432-109">Struktura používá výšky měřená v stopy a palce.</span><span class="sxs-lookup"><span data-stu-id="32432-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="32432-110">Jeden *palec* je 2,54 cm a jeden */zápatí* je 12 palců.</span><span class="sxs-lookup"><span data-stu-id="32432-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="32432-111">Aby normalizovaný hodnoty (palce < 12.0), provede konstruktoru *modulo* aritmetické 12.</span><span class="sxs-lookup"><span data-stu-id="32432-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="32432-112">`+` Operátor používá ke generování hodnot normalizovaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="32432-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="32432-113">Můžete otestovat strukturu `height` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="32432-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="32432-114">Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="32432-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32432-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="32432-115">See Also</span></span>  
 [<span data-ttu-id="32432-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="32432-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="32432-117">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="32432-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="32432-118">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="32432-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="32432-119">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="32432-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="32432-120">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="32432-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="32432-121">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="32432-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="32432-122">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="32432-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="32432-123">Operátor Mod</span><span class="sxs-lookup"><span data-stu-id="32432-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
