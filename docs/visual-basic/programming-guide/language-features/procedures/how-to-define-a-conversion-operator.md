---
title: 'Postupy: Definice operátora převodu'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 53b0211c6304625edd7ac24fa52ff0c051d8f0a0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388086"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="f9f44-102">Postupy: Definice operátora převodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9f44-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="f9f44-103">Pokud jste definovali třídu nebo strukturu, můžete definovat operátor konverze typu mezi typem vaší třídy nebo struktury a jiným datovým typem (například `Integer` , `Double` nebo `String` ).</span><span class="sxs-lookup"><span data-stu-id="f9f44-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="f9f44-104">Definujte převod typu jako proceduru [funkce CType](../../../language-reference/functions/ctype-function.md) v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="f9f44-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="f9f44-105">Všechny postupy převodu musí být `Public Shared` a každá z nich musí určovat buď [rozšiřování](../../../language-reference/modifiers/widening.md) , nebo [zúžení](../../../language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="f9f44-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="f9f44-106">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="f9f44-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f44-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f44-107">Example</span></span>  
 <span data-ttu-id="f9f44-108">Následující příklad definuje operátory převodu mezi strukturou nazvanou `digit` a `Byte` .</span><span class="sxs-lookup"><span data-stu-id="f9f44-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="f9f44-109">Strukturu můžete otestovat `digit` pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="f9f44-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="f9f44-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9f44-110">See also</span></span>

- [<span data-ttu-id="f9f44-111">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="f9f44-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f9f44-112">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="f9f44-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="f9f44-113">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="f9f44-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="f9f44-114">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="f9f44-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="f9f44-115">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="f9f44-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="f9f44-116">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="f9f44-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="f9f44-117">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="f9f44-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="f9f44-118">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="f9f44-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="f9f44-119">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="f9f44-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
