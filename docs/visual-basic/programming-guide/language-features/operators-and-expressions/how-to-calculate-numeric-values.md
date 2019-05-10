---
title: 'Postupy: Výpočet numerických hodnot (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 3e367a10a3e703241c7417d3ea17068018becb5a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649736"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="ac78d-102">Postupy: Výpočet numerických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac78d-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="ac78d-103">Můžete vypočítat číselných hodnot pomocí numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="ac78d-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="ac78d-104">A *číselného výrazu* je výraz, který obsahuje literály a konstanty a proměnné představující číselné hodnoty a operátory, které fungují u těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="ac78d-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="ac78d-105">Probíhá výpočet číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="ac78d-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="ac78d-106">Pro výpočet číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="ac78d-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="ac78d-107">Zkombinujte jeden nebo více číselné literály, konstanty a proměnné do číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac78d-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="ac78d-108">Následující příklad ukazuje některé platné numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="ac78d-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="ac78d-109">První tři řádky zobrazují literál, konstanty a proměnné.</span><span class="sxs-lookup"><span data-stu-id="ac78d-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="ac78d-110">Každé z nich tvoří platný číselný výraz samotný.</span><span class="sxs-lookup"><span data-stu-id="ac78d-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="ac78d-111">Poslední řádek ukazuje kombinaci proměnné se dva literály.</span><span class="sxs-lookup"><span data-stu-id="ac78d-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="ac78d-112">Všimněte si, že číselného výrazu netvoří úplný příkaz jazyka Visual Basic samostatně.</span><span class="sxs-lookup"><span data-stu-id="ac78d-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="ac78d-113">Výraz musí používat jako součást dokončení příkazu.</span><span class="sxs-lookup"><span data-stu-id="ac78d-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="ac78d-114">K uložení číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="ac78d-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="ac78d-115">Přiřazovací příkaz můžete použít k přiřazení hodnoty reprezentována číselné proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ac78d-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="ac78d-116">V předchozím příkladu, hodnota výrazu na pravé straně operátor je rovno (`=`) je přiřazená k proměnné `j` na levé straně operátoru, takže `j` vyhodnocen jako 276.</span><span class="sxs-lookup"><span data-stu-id="ac78d-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="ac78d-117">Další informace najdete v tématu [příkazy](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac78d-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="ac78d-118">Více operátorů</span><span class="sxs-lookup"><span data-stu-id="ac78d-118">Multiple Operators</span></span>  
 <span data-ttu-id="ac78d-119">Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnoceny je určen podle pravidel priority operátorů.</span><span class="sxs-lookup"><span data-stu-id="ac78d-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="ac78d-120">K přepsání pravidel priority operátorů, uzavřete výrazy v závorkách, stejně jako v předchozím příkladu; uzavřené výrazy jsou nejdříve vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="ac78d-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="ac78d-121">Chcete-li přepsat operátor normální priorita</span><span class="sxs-lookup"><span data-stu-id="ac78d-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="ac78d-122">Použití závorek k uzavření operace, které chcete provést jako první.</span><span class="sxs-lookup"><span data-stu-id="ac78d-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="ac78d-123">Následující příklad ukazuje dva různé výsledky se stejnými operandy a operátory.</span><span class="sxs-lookup"><span data-stu-id="ac78d-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="ac78d-124">V předchozím příkladu, pro výpočet `j` provede operátor sčítání (`+`) první protože závorky kolem `(67 + i)` přepsání normální priorita a hodnota přiřazená k `j` je 276 (4 x 69).</span><span class="sxs-lookup"><span data-stu-id="ac78d-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="ac78d-125">Výpočet pro `k` provádí operátory v jejich normální priorita (`*` před `+`) a hodnota přiřazená k `k` je 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="ac78d-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="ac78d-126">Další informace najdete v tématu [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ac78d-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac78d-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac78d-127">See also</span></span>

- [<span data-ttu-id="ac78d-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="ac78d-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="ac78d-129">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="ac78d-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="ac78d-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="ac78d-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="ac78d-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac78d-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ac78d-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="ac78d-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ac78d-133">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="ac78d-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
