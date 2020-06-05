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
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388034"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="bfb5b-102">Postupy: Definice operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfb5b-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="bfb5b-103">Pokud jste definovali třídu nebo strukturu, můžete definovat chování operátoru standardního (například `*` , `<>` nebo `And` ), pokud jeden nebo oba operandy jsou typu vaší třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="bfb5b-104">V rámci třídy nebo struktury definujte operátor standardní jako proceduru operátoru.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="bfb5b-105">Všechny procedury operátoru musí být `Public` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="bfb5b-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="bfb5b-106">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfb5b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfb5b-107">Example</span></span>  
 <span data-ttu-id="bfb5b-108">Následující příklad definuje `+` operátor pro strukturu s názvem `height` .</span><span class="sxs-lookup"><span data-stu-id="bfb5b-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="bfb5b-109">Struktura využívá výšky měřenou v nohou a palcích.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="bfb5b-110">Jedna *palec* je 2,54 centimetrů a jedno *chodidlo* je 12 palců.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="bfb5b-111">Chcete-li zajistit normalizované hodnoty (palce < 12,0), konstruktor provede *modulo* 12 aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="bfb5b-112">`+`Operátor používá konstruktor ke generování normalizovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="bfb5b-113">Strukturu můžete otestovat `height` pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="bfb5b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfb5b-114">See also</span></span>

- [<span data-ttu-id="bfb5b-115">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="bfb5b-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="bfb5b-116">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="bfb5b-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="bfb5b-117">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="bfb5b-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="bfb5b-118">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="bfb5b-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="bfb5b-119">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="bfb5b-119">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="bfb5b-120">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="bfb5b-120">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="bfb5b-121">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="bfb5b-121">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="bfb5b-122">Mod – operátor</span><span class="sxs-lookup"><span data-stu-id="bfb5b-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
