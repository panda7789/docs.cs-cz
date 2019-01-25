---
title: 'Postupy: Definice operátora převodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 76d0769456e30766b830023c1f27381ceca59cbb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521527"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="a70d1-102">Postupy: Definice operátora převodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a70d1-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="a70d1-103">Pokud jste definovali třídy nebo struktury, můžete definovat operátor převodu typu mezi typem třídy nebo struktury a jiný typ dat (například `Integer`, `Double`, nebo `String`).</span><span class="sxs-lookup"><span data-stu-id="a70d1-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="a70d1-104">Definovat převod typu jako [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="a70d1-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="a70d1-105">Všechny postupy převod musí být `Public Shared`, a každý z nich musí určovat buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="a70d1-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="a70d1-106">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="a70d1-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70d1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a70d1-107">Example</span></span>  
 <span data-ttu-id="a70d1-108">Následující příklad definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="a70d1-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="a70d1-109">Můžete otestovat strukturu `digit` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a70d1-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a70d1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a70d1-110">See also</span></span>
- [<span data-ttu-id="a70d1-111">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a70d1-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a70d1-112">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="a70d1-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="a70d1-113">Postupy: Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="a70d1-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a70d1-114">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="a70d1-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a70d1-115">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="a70d1-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a70d1-116">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a70d1-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a70d1-117">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="a70d1-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a70d1-118">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="a70d1-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a70d1-119">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="a70d1-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
