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
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648470"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="ce4f7-102">Postupy: Definice operátora převodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce4f7-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="ce4f7-103">Pokud jste definovali třídu nebo strukturu, můžete definovat operátor převodu typu mezi typ třídu nebo strukturu a jiný datový typ (například `Integer`, `Double`, nebo `String`).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="ce4f7-104">Převod typů jako definovat [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="ce4f7-105">Musí být všechny postupy převod `Public Shared`, a každé z nich musí být buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="ce4f7-106">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce4f7-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce4f7-107">Example</span></span>  
 <span data-ttu-id="ce4f7-108">V následujícím příkladu definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="ce4f7-109">Můžete otestovat strukturu `digit` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ce4f7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce4f7-110">See Also</span></span>  
 [<span data-ttu-id="ce4f7-111">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ce4f7-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="ce4f7-112">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="ce4f7-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="ce4f7-113">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ce4f7-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="ce4f7-114">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="ce4f7-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="ce4f7-115">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="ce4f7-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="ce4f7-116">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="ce4f7-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="ce4f7-117">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="ce4f7-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="ce4f7-118">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="ce4f7-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="ce4f7-119">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="ce4f7-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
