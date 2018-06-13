---
title: Porovnání hodnot (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649604"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="1474e-102">Porovnání hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1474e-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="1474e-103">Operátory porovnání lze použít k vytvoření výrazy, které porovnávají hodnoty proměnných číselná.</span><span class="sxs-lookup"><span data-stu-id="1474e-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="1474e-104">Tyto výrazy vrátit `Boolean` hodnota založená na tom, zda je výsledkem porovnávání PRAVDA nebo NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="1474e-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="1474e-105">Příklady takových výraz.</span><span class="sxs-lookup"><span data-stu-id="1474e-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="1474e-106">První vyhodnocen jako `True`, protože je větší než 26 45.</span><span class="sxs-lookup"><span data-stu-id="1474e-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="1474e-107">V druhém příkladu se vyhodnocuje `False`, protože 26 není větší než 45.</span><span class="sxs-lookup"><span data-stu-id="1474e-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="1474e-108">Numerické výrazy tímto způsobem, můžete porovnat.</span><span class="sxs-lookup"><span data-stu-id="1474e-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="1474e-109">Sami výrazy, které můžete porovnat může být složité výrazy, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1474e-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="1474e-110">Předchozí složitý výraz obsahuje literály, proměnné a volání funkce.</span><span class="sxs-lookup"><span data-stu-id="1474e-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="1474e-111">Výrazy na obou stranách operátoru porovnání vyhodnocují a výsledné hodnoty jsou potom porovná pomocí `>=` operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="1474e-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="1474e-112">Pokud hodnota výraz na levé straně je větší než nebo rovna hodnotě výrazu na pravé straně, celý výraz vyhodnocen jako `True`, jinak se vyhodnotí jako `False`.</span><span class="sxs-lookup"><span data-stu-id="1474e-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="1474e-113">Výrazy, které porovnat hodnoty se obvykle používají v `If...Then` konstrukce, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1474e-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="1474e-114">`=` Přihlášení je operátor porovnání a také operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1474e-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="1474e-115">Když se použije jako operátor porovnání, vyhodnotí, zda hodnota na levé straně je stejná jako hodnota na pravé straně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1474e-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="1474e-116">Můžete také použít výraz porovnání kdekoli `Boolean` hodnota je potřebné, například jako v `If`, `While`, `Loop`, nebo `ElseIf` prohlášení, nebo při přiřazování nebo předáním hodnoty do `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="1474e-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="1474e-117">V následujícím příkladu je přiřazená hodnoty vrácené výraz pro porovnání `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="1474e-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1474e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1474e-118">See Also</span></span>  
 [<span data-ttu-id="1474e-119">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="1474e-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="1474e-120">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="1474e-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="1474e-121">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1474e-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="1474e-122">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="1474e-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="1474e-123">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1474e-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
