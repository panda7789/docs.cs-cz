---
title: Operátory a výrazy v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7c32ce34dc7d6cb662ebdb42a3d3431f8107687f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="d8ed9-102">Operátory a výrazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8ed9-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="d8ed9-103">*Operátor* je element kódu, který provede operaci na jeden nebo více elementy kódu, které mají hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="d8ed9-104">Například prvky hodnotu proměnné, konstanty, literály, vlastnosti, vrátí z `Function` a `Operator` procedury a výrazy.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="d8ed9-105">*Výraz* je řada hodnota elementy v kombinaci s operátory, která dává novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="d8ed9-106">Operátory fungují na elementy hodnota provedením výpočtů, porovnání nebo jiné operace.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="d8ed9-107">Typy operátorů</span><span class="sxs-lookup"><span data-stu-id="d8ed9-107">Types of Operators</span></span>  
 <span data-ttu-id="d8ed9-108">Visual Basic poskytuje následující typy operátory:</span><span class="sxs-lookup"><span data-stu-id="d8ed9-108">Visual Basic provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="d8ed9-109">[Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) provádět výpočty obeznámeni s číselných hodnot, včetně jejich bit vzory s posunem.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="d8ed9-110">[Operátory porovnání](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnání dvou výrazů a vrátí `Boolean` hodnotu představující výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="d8ed9-111">[Operátory zřetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) připojení více řetězce do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="d8ed9-112">[Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vrátit výsledek stejný datový typ jako hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="d8ed9-113">Hodnota elementy, které jsou spojené s operátor se nazývají *operandy* tohoto operátoru.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="d8ed9-114">Operátory v kombinaci s výrazy formuláře prvky hodnot, s výjimkou operátoru přiřazení, které formuláře *příkaz*.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="d8ed9-115">Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ed9-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="d8ed9-116">Vyhodnocení výrazu</span><span class="sxs-lookup"><span data-stu-id="d8ed9-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="d8ed9-117">Konečný výsledek výrazu představuje hodnotu, která je obvykle známé datového typu, jako `Boolean`, `String`, nebo číselného typu.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="d8ed9-118">Následují příklady výrazů.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="d8ed9-119">Několik operátorů můžete provádět akce v jeden výraz nebo příkaz, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 <span data-ttu-id="d8ed9-120">V předchozím příkladu, Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`), potom přiřadí výsledná hodnota proměnné `x` na levé straně.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="d8ed9-121">Neexistuje žádné praktické omezení počtu operátory, které lze spojit do výrazu, ale k pochopení [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nutné zajistit, že dostanete očekáváte, že výsledky.</span><span class="sxs-lookup"><span data-stu-id="d8ed9-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
 <span data-ttu-id="d8ed9-122">Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="d8ed9-122">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ed9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8ed9-123">See Also</span></span>  
 [<span data-ttu-id="d8ed9-124">Operátory</span><span class="sxs-lookup"><span data-stu-id="d8ed9-124">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="d8ed9-125">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="d8ed9-125">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="d8ed9-126">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d8ed9-126">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
