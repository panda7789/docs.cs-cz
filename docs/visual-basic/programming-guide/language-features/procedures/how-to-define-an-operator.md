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
ms.openlocfilehash: fb150298562c1ec91f73f3c8075f4f8a4fc20b27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679523"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="45272-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45272-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="45272-103">Pokud jste definovali třídy nebo struktury, můžete definovat chování standardní – operátor (například `*`, `<>`, nebo `And`) Pokud je jeden nebo oba operandy typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="45272-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="45272-104">Standardní operátor definujte jako procedury operátora v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="45272-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="45272-105">Musí být všechny procedury operátoru `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="45272-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="45272-106">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="45272-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45272-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="45272-107">Example</span></span>  
 <span data-ttu-id="45272-108">Následující příklad definuje `+` volat operátor pro strukturu `height`.</span><span class="sxs-lookup"><span data-stu-id="45272-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="45272-109">Struktura používá měřené v stopy a palce výšky.</span><span class="sxs-lookup"><span data-stu-id="45272-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="45272-110">Jeden *palec* je 2,54 cm a jedno *zápatí* 12 palců.</span><span class="sxs-lookup"><span data-stu-id="45272-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="45272-111">Aby bylo zajištěno normalizované hodnoty (palce < 12.0), konstruktor provádí *modulo* aritmetické 12.</span><span class="sxs-lookup"><span data-stu-id="45272-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="45272-112">`+` Operátor používá konstruktor k vygenerování normalizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45272-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="45272-113">Můžete otestovat strukturu `height` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="45272-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="45272-114">Další informace a příklady najdete v tématu [přetížení operátoru v jazyce Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="45272-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45272-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45272-115">See also</span></span>
- [<span data-ttu-id="45272-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="45272-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="45272-117">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="45272-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="45272-118">Postupy: Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="45272-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="45272-119">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="45272-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="45272-120">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="45272-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="45272-121">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="45272-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="45272-122">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="45272-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="45272-123">Operátor Mod</span><span class="sxs-lookup"><span data-stu-id="45272-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
