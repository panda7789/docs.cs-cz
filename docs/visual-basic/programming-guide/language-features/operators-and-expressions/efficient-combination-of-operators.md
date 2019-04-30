---
title: Účinná kombinace operátorů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864649"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="dc979-102">Účinná kombinace operátorů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc979-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="dc979-103">Složité výrazy mohou obsahovat mnoho různých operátorů.</span><span class="sxs-lookup"><span data-stu-id="dc979-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="dc979-104">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="dc979-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="dc979-105">Vytváření složitých výrazů, jako je například v předchozím příkladu vyžaduje důkladné pochopení pravidel priority operátorů.</span><span class="sxs-lookup"><span data-stu-id="dc979-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="dc979-106">Další informace najdete v tématu [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="dc979-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="dc979-107">Výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="dc979-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="dc979-108">Často se má operace pokračovat v jiném pořadí od stanovené prioritou operátorů.</span><span class="sxs-lookup"><span data-stu-id="dc979-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="dc979-109">Podívejte se na následující příklad.</span><span class="sxs-lookup"><span data-stu-id="dc979-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="dc979-110">Předchozí příklad vynásobí `z` podle `y`, pak přidá výsledek, který má `4`.</span><span class="sxs-lookup"><span data-stu-id="dc979-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="dc979-111">Ale pokud chcete přidat `y` a `4` před násobením výsledků `z`, priorita operátorů normální můžete přepsat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="dc979-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="dc979-112">Uzavřením výrazu v závorkách vynutit tento výraz, který má být vyhodnocen jako první, bez ohledu na to priorita operátorů.</span><span class="sxs-lookup"><span data-stu-id="dc979-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="dc979-113">K vynucení předchozí příklad provádět přidání, může přepsat ho jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="dc979-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="dc979-114">Předchozí příklad přidá `y` a `4`, pak vynásobí tohoto součtu podle `z`.</span><span class="sxs-lookup"><span data-stu-id="dc979-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="dc979-115">Vnořené výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="dc979-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="dc979-116">Můžete vnořovat výrazy ve více úrovní závorky k přepsání priority ještě více.</span><span class="sxs-lookup"><span data-stu-id="dc979-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="dc979-117">Výrazy v závorkách k nejhlouběji vnořené jsou vyčíslen první, za nímž následuje další nejhlouběji vnořená, a tak dále nejméně hluboce vnořený a nakonec výrazů mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="dc979-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="dc979-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="dc979-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="dc979-119">V předchozím příkladu `z + 2` je Vyhodnocená první a pak kulatých závorek výrazy.</span><span class="sxs-lookup"><span data-stu-id="dc979-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="dc979-120">Umocnění, což obvykle má vyšší prioritu než sčítání a násobení, se vyhodnocují jako poslední v tomto příkladu protože dalších výrazů jsou uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="dc979-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc979-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc979-121">See also</span></span>

- [<span data-ttu-id="dc979-122">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc979-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="dc979-123">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc979-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="dc979-124">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc979-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="dc979-125">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc979-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="dc979-126">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="dc979-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="dc979-127">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="dc979-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="dc979-128">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="dc979-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="dc979-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc979-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
