---
title: "Postupy: Definice operátora převodu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="0a64d-102">Postupy: Definice operátora převodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a64d-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="0a64d-103">Pokud jste definovali třídu nebo strukturu, můžete definovat operátor převodu typu mezi typ třídu nebo strukturu a jiný datový typ (například `Integer`, `Double`, nebo `String`).</span><span class="sxs-lookup"><span data-stu-id="0a64d-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="0a64d-104">Převod typů jako definovat [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="0a64d-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="0a64d-105">Musí být všechny postupy převod `Public Shared`, a každé z nich musí být buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="0a64d-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="0a64d-106">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="0a64d-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a64d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a64d-107">Example</span></span>  
 <span data-ttu-id="0a64d-108">V následujícím příkladu definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.</span><span class="sxs-lookup"><span data-stu-id="0a64d-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="0a64d-109">Můžete otestovat strukturu `digit` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="0a64d-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0a64d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a64d-110">See Also</span></span>  
 [<span data-ttu-id="0a64d-111">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="0a64d-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="0a64d-112">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="0a64d-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="0a64d-113">Postupy: volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="0a64d-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="0a64d-114">Postupy: použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="0a64d-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="0a64d-115">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="0a64d-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="0a64d-116">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="0a64d-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="0a64d-117">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="0a64d-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="0a64d-118">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="0a64d-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="0a64d-119">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="0a64d-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
