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
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="a6d9f-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6d9f-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="a6d9f-103">Pokud jste definovali třídu nebo strukturu, můžete definovat chování operátoru standardního (například `*`, `<>`nebo `And`), pokud jeden nebo oba operandy jsou typu vaší třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a6d9f-104">V rámci třídy nebo struktury definujte operátor standardní jako proceduru operátoru.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="a6d9f-105">Všechny procedury operátoru musí být `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="a6d9f-106">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6d9f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6d9f-107">Example</span></span>  
 <span data-ttu-id="a6d9f-108">Následující příklad definuje operátor `+` pro strukturu s názvem `height`.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="a6d9f-109">Struktura využívá výšky měřenou v nohou a palcích.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="a6d9f-110">Jedna *palec* je 2,54 centimetrů a jedno *chodidlo* je 12 palců.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="a6d9f-111">Chcete-li zajistit normalizované hodnoty (palce < 12,0), konstruktor provede *modulo* 12 aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="a6d9f-112">Operátor `+` používá konstruktor ke generování normalizovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="a6d9f-113">Strukturu `height` lze otestovat pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="a6d9f-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="a6d9f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6d9f-114">See also</span></span>

- [<span data-ttu-id="a6d9f-115">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a6d9f-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a6d9f-116">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="a6d9f-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a6d9f-117">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a6d9f-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a6d9f-118">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="a6d9f-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a6d9f-119">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="a6d9f-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a6d9f-120">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a6d9f-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a6d9f-121">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="a6d9f-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a6d9f-122">Operátor Mod</span><span class="sxs-lookup"><span data-stu-id="a6d9f-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
