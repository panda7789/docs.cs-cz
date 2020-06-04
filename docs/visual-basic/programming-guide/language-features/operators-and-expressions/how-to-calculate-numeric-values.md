---
title: 'Postupy: Výpočet numerických hodnot'
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
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403456"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="05d5c-102">Postupy: Výpočet numerických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05d5c-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="05d5c-103">Číselné hodnoty můžete vypočítat pomocí numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="05d5c-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="05d5c-104">*Číselný výraz* je výraz, který obsahuje literály, konstanty a proměnné představující číselné hodnoty a operátory, které na těchto hodnotách působí.</span><span class="sxs-lookup"><span data-stu-id="05d5c-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="05d5c-105">Výpočet číselných hodnot</span><span class="sxs-lookup"><span data-stu-id="05d5c-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="05d5c-106">Výpočet číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="05d5c-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="05d5c-107">Kombinace jednoho nebo více číselných literálů, konstant a proměnných do číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="05d5c-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="05d5c-108">Následující příklad ukazuje některé platné číselné výrazy.</span><span class="sxs-lookup"><span data-stu-id="05d5c-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="05d5c-109">První tři řádky ukazují literál, konstantu a proměnnou.</span><span class="sxs-lookup"><span data-stu-id="05d5c-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="05d5c-110">Každá z nich má platný numerický výraz sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="05d5c-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="05d5c-111">Poslední řádek ukazuje kombinaci proměnné se dvěma literály.</span><span class="sxs-lookup"><span data-stu-id="05d5c-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="05d5c-112">Všimněte si, že číselný výraz netvoří úplný příkaz Visual Basic sám sebou.</span><span class="sxs-lookup"><span data-stu-id="05d5c-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="05d5c-113">Výraz je nutné použít jako součást příkazu Complete.</span><span class="sxs-lookup"><span data-stu-id="05d5c-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="05d5c-114">Uložení číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="05d5c-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="05d5c-115">Můžete použít příkaz přiřazení pro přiřazení hodnoty reprezentované číselným výrazem proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="05d5c-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="05d5c-116">V předchozím příkladu je hodnota výrazu na pravé straně operátoru rovnosti ( `=` ) přiřazena proměnné `j` na levé straně operátoru, takže se `j` vyhodnotí jako 276.</span><span class="sxs-lookup"><span data-stu-id="05d5c-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="05d5c-117">Další informace najdete v tématu [příkazy](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="05d5c-117">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="05d5c-118">Více operátorů</span><span class="sxs-lookup"><span data-stu-id="05d5c-118">Multiple Operators</span></span>  
 <span data-ttu-id="05d5c-119">Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnocovány, je určeno pravidly priority operátoru.</span><span class="sxs-lookup"><span data-stu-id="05d5c-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="05d5c-120">Chcete-li přepsat pravidla přednosti operátorů, můžete uzavřít výrazy v závorkách, jako v předchozím příkladu. vložené výrazy jsou vyhodnoceny jako první.</span><span class="sxs-lookup"><span data-stu-id="05d5c-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="05d5c-121">Přepsání priority normálního operátoru</span><span class="sxs-lookup"><span data-stu-id="05d5c-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="05d5c-122">K uzavření operací, které chcete provést jako první, použijte kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="05d5c-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="05d5c-123">Následující příklad ukazuje dva různé výsledky se stejnými operandy a operátory.</span><span class="sxs-lookup"><span data-stu-id="05d5c-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="05d5c-124">V předchozím příkladu výpočet pro `j` provede operátor sčítání ( `+` ) nejprve, protože kulaté závorky kolem `(67 + i)` normální priority přepisují a hodnota přiřazená `j` je 276 (4 časy 69).</span><span class="sxs-lookup"><span data-stu-id="05d5c-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="05d5c-125">Výpočet pro `k` provede operátory v normální přednosti ( `*` před `+` ) a hodnota přiřazená `k` je 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="05d5c-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="05d5c-126">Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="05d5c-126">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d5c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="05d5c-127">See also</span></span>

- [<span data-ttu-id="05d5c-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="05d5c-128">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="05d5c-129">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="05d5c-129">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="05d5c-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="05d5c-130">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="05d5c-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05d5c-131">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="05d5c-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="05d5c-132">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="05d5c-133">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="05d5c-133">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
