---
title: Porovnání hodnot
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
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403392"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="a48eb-102">Porovnání hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a48eb-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="a48eb-103">Operátory porovnání lze použít k vytvoření výrazů, které porovnávají hodnoty číselných proměnných.</span><span class="sxs-lookup"><span data-stu-id="a48eb-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="a48eb-104">Tyto výrazy vrátí `Boolean` hodnotu na základě toho, zda je porovnání true nebo false.</span><span class="sxs-lookup"><span data-stu-id="a48eb-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="a48eb-105">Příklady takového výrazu jsou následující.</span><span class="sxs-lookup"><span data-stu-id="a48eb-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="a48eb-106">První výraz se vyhodnotí jako `True` , protože 45 je větší než 26.</span><span class="sxs-lookup"><span data-stu-id="a48eb-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="a48eb-107">Druhý příklad je vyhodnocen jako `False` , protože 26 není větší než 45.</span><span class="sxs-lookup"><span data-stu-id="a48eb-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="a48eb-108">Tímto způsobem můžete také porovnat číselné výrazy.</span><span class="sxs-lookup"><span data-stu-id="a48eb-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="a48eb-109">Výrazy, které porovnáváte, mohou být složité výrazy, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a48eb-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="a48eb-110">Předchozí složitý výraz zahrnuje literály, proměnné a volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="a48eb-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="a48eb-111">Výrazy na obou stranách operátoru porovnání jsou vyhodnoceny a výsledné hodnoty jsou pak porovnány pomocí `>=` operátoru porovnání.</span><span class="sxs-lookup"><span data-stu-id="a48eb-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="a48eb-112">Pokud je hodnota výrazu na levé straně větší než nebo rovna hodnotě výrazu na pravé straně, celý výraz se vyhodnotí jako `True` . v opačném případě se vyhodnotí jako `False` .</span><span class="sxs-lookup"><span data-stu-id="a48eb-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="a48eb-113">Výrazy, které porovnávají hodnoty, jsou nejčastěji používány v `If...Then` konstrukcích, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a48eb-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="a48eb-114">`=`Znaménkem je operátor porovnání a operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a48eb-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="a48eb-115">Při použití jako operátor porovnání vyhodnotí, zda je hodnota vlevo rovna hodnotě na pravé straně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a48eb-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="a48eb-116">Můžete také použít výraz porovnání kdekoli `Boolean` , kde je požadována hodnota, například v `If` `While` příkazu,, `Loop` nebo `ElseIf` , nebo při přiřazení hodnoty k proměnné nebo jejímu předání `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a48eb-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="a48eb-117">V následujícím příkladu je hodnota vrácená výrazem porovnání přiřazena k `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="a48eb-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="a48eb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a48eb-118">See also</span></span>

- [<span data-ttu-id="a48eb-119">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="a48eb-119">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="a48eb-120">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="a48eb-120">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="a48eb-121">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a48eb-121">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="a48eb-122">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="a48eb-122">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="a48eb-123">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a48eb-123">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
