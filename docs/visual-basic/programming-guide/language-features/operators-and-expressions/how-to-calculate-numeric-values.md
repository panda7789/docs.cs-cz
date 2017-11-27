---
title: "Postupy: Výpočet numerických hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="32f1b-102">Postupy: Výpočet numerických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32f1b-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="32f1b-103">Můžete vypočítat číselné hodnoty prostřednictvím numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="32f1b-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="32f1b-104">A *číselného výrazu* je výraz, který obsahuje literály, konstanty a proměnné představující číselné hodnoty a operátory, které fungují v těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="32f1b-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="32f1b-105">Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="32f1b-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="32f1b-106">Chcete-li vypočítat číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="32f1b-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="32f1b-107">Jeden nebo více číselné literály, konstanty a proměnné Kombinujte do číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="32f1b-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="32f1b-108">Následující příklad ukazuje některé platné numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="32f1b-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="32f1b-109">První tři řádky zobrazit literál, konstanty a proměnné.</span><span class="sxs-lookup"><span data-stu-id="32f1b-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="32f1b-110">Každé z nich tvoří platný číselného výrazu samostatně.</span><span class="sxs-lookup"><span data-stu-id="32f1b-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="32f1b-111">Poslední řádek zobrazuje kombinaci proměnná s dvěma literály.</span><span class="sxs-lookup"><span data-stu-id="32f1b-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="32f1b-112">Všimněte si, že číselného výrazu netvoří úplná [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="32f1b-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statement by itself.</span></span> <span data-ttu-id="32f1b-113">Výraz musí používat jako součást dokončení příkazu.</span><span class="sxs-lookup"><span data-stu-id="32f1b-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="32f1b-114">K uložení číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="32f1b-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="32f1b-115">Příkazu přiřazení můžete přiřadit hodnotu reprezentována číselného výrazu proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="32f1b-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="32f1b-116">V předchozím příkladu, hodnota výrazu na pravé straně operátor je rovno (`=`) je přiřazen k proměnné `j` na levé straně operátoru, takže `j` se vyhodnocuje 276.</span><span class="sxs-lookup"><span data-stu-id="32f1b-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="32f1b-117">Další informace najdete v tématu [příkazy](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="32f1b-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="32f1b-118">Několik operátorů</span><span class="sxs-lookup"><span data-stu-id="32f1b-118">Multiple Operators</span></span>  
 <span data-ttu-id="32f1b-119">Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnocovány je určen podle pravidel objektů operátorů.</span><span class="sxs-lookup"><span data-stu-id="32f1b-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="32f1b-120">Chcete-li přepsat pravidla operátorů, uzavřete výrazy v závorkách, jako v předchozím příkladu; výrazy závorkách se vyhodnocují jako první.</span><span class="sxs-lookup"><span data-stu-id="32f1b-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="32f1b-121">Chcete-li přepsat normální priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="32f1b-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="32f1b-122">Závorky lze použijte k uzavřete operace, které chcete provést první.</span><span class="sxs-lookup"><span data-stu-id="32f1b-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="32f1b-123">Následující příklad ukazuje dva odlišné výsledky se stejným operandy a operátory.</span><span class="sxs-lookup"><span data-stu-id="32f1b-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="32f1b-124">V předchozím příkladu, výpočtu pro `j` provede operátor sčítání (`+`) první protože závorky `(67 + i)` přepsání normální prioritu a hodnotu přiřazenou `j` je 276 (4 časy 69).</span><span class="sxs-lookup"><span data-stu-id="32f1b-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="32f1b-125">Výpočet pro `k` provede operátory v jejich normálním prioritu (`*` před `+`) a hodnotu přiřazenou `k` je 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="32f1b-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="32f1b-126">Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="32f1b-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f1b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="32f1b-127">See Also</span></span>  
 [<span data-ttu-id="32f1b-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="32f1b-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="32f1b-129">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="32f1b-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="32f1b-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="32f1b-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="32f1b-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32f1b-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="32f1b-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="32f1b-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="32f1b-133">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="32f1b-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
