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
ms.openlocfilehash: 14aa25de78eb357f8474d3828aa45e48e7a4f9c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863842"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="91930-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91930-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="91930-103">Pokud jste definovali třídy nebo struktury, můžete definovat chování standardní – operátor (například `*`, `<>`, nebo `And`) Pokud je jeden nebo oba operandy typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="91930-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="91930-104">Standardní operátor definujte jako procedury operátora v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="91930-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="91930-105">Musí být všechny procedury operátoru `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="91930-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="91930-106">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="91930-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91930-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="91930-107">Example</span></span>  
 <span data-ttu-id="91930-108">Následující příklad definuje `+` volat operátor pro strukturu `height`.</span><span class="sxs-lookup"><span data-stu-id="91930-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="91930-109">Struktura používá měřené v stopy a palce výšky.</span><span class="sxs-lookup"><span data-stu-id="91930-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="91930-110">Jeden *palec* je 2,54 cm a jedno *zápatí* 12 palců.</span><span class="sxs-lookup"><span data-stu-id="91930-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="91930-111">Aby bylo zajištěno normalizované hodnoty (palce < 12.0), konstruktor provádí *modulo* aritmetické 12.</span><span class="sxs-lookup"><span data-stu-id="91930-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="91930-112">`+` Operátor používá konstruktor k vygenerování normalizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="91930-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="91930-113">Můžete otestovat strukturu `height` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="91930-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="91930-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91930-114">See also</span></span>

- [<span data-ttu-id="91930-115">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="91930-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="91930-116">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="91930-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="91930-117">Postupy: Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="91930-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="91930-118">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="91930-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="91930-119">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="91930-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="91930-120">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="91930-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="91930-121">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="91930-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="91930-122">Operátor Mod</span><span class="sxs-lookup"><span data-stu-id="91930-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
