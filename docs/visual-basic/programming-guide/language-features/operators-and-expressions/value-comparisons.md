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
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818602"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="0a5ca-102">Porovnání hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a5ca-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="0a5ca-103">Operátory porovnání lze použít k vytvoření výrazů, které porovnat hodnoty číselné proměnné.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="0a5ca-104">Vrátí tyto výrazy `Boolean` hodnotu podle toho, jestli porovnání hodnota true nebo false.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="0a5ca-105">Příklady takový výraz.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="0a5ca-106">První výraz je vyhodnocen jako `True`, protože je větší než 26 45.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="0a5ca-107">Druhý příklad je vyhodnocen jako `False`, protože není větší než 45 26.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="0a5ca-108">Můžete také porovnat numerických výrazů tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="0a5ca-109">Výrazy, které můžete porovnat mohou být samy složité výrazy, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="0a5ca-110">Předchozí složitých výraz zahrnuje literály, proměnné a volání funkce.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="0a5ca-111">Výrazy na obou stranách operátoru porovnání jsou vyhodnoceny a výsledné hodnoty jsou pak porovnány pomocí `>=` operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="0a5ca-112">Pokud je hodnota výrazu na levé straně je větší než nebo rovna hodnotě výraz na pravé straně, celý výraz vyhodnocen jako `True`; v opačném případě je vyhodnocen jako `False`.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="0a5ca-113">Výrazy, které porovnat hodnoty se běžně používají v `If...Then` konstrukce, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="0a5ca-114">`=` Podpis je operátor porovnání, stejně jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="0a5ca-115">Když se použije jako operátor porovnání, vyhodnotí, zda hodnota na levé straně je rovna hodnotě na pravé straně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="0a5ca-116">Výrazu porovnání lze také použít kdekoli `Boolean` hodnota je potřeba, například jako v `If`, `While`, `Loop`, nebo `ElseIf` příkazu, nebo když přiřadit nebo jejich předání hodnoty `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="0a5ca-117">V následujícím příkladu je přiřazená hodnota vrácená výrazu porovnání `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0a5ca-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="0a5ca-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a5ca-118">See also</span></span>

- [<span data-ttu-id="0a5ca-119">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="0a5ca-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="0a5ca-120">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="0a5ca-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="0a5ca-121">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a5ca-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="0a5ca-122">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="0a5ca-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="0a5ca-123">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a5ca-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
