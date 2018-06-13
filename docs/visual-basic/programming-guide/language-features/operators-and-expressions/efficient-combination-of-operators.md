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
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648915"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="92855-102">Účinná kombinace operátorů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92855-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="92855-103">Složité výrazy může obsahovat mnoho různých operátory.</span><span class="sxs-lookup"><span data-stu-id="92855-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="92855-104">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="92855-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="92855-105">Vytvoření složité výrazy, jako je třeba v předchozím příkladu vyžaduje důkladné znalosti týkající se pravidla operátorů.</span><span class="sxs-lookup"><span data-stu-id="92855-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="92855-106">Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="92855-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="92855-107">Výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="92855-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="92855-108">Často se má operace pokračovat v jiném pořadí od dáno operátorů.</span><span class="sxs-lookup"><span data-stu-id="92855-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="92855-109">Podívejte se na následující příklad.</span><span class="sxs-lookup"><span data-stu-id="92855-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="92855-110">V předchozím příkladu vynásobí `z` podle `y`, pak přidá výsledek, který má `4`.</span><span class="sxs-lookup"><span data-stu-id="92855-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="92855-111">Ale pokud chcete přidat `y` a `4` před vynásobením výsledku podle `z`, normální priorita operátorů lze přepsat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="92855-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="92855-112">Uzavřením výrazu v závorkách, můžete vynutit tento výraz, který se vyhodnotí nejprve, bez ohledu na to operátorů.</span><span class="sxs-lookup"><span data-stu-id="92855-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="92855-113">Chcete-li vynutit v předchozím příkladu uděláte přidání, může být přepisování jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="92855-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="92855-114">V předchozím příkladu přidá `y` a `4`, pak vynásobí tento součet podle `z`.</span><span class="sxs-lookup"><span data-stu-id="92855-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="92855-115">Vnořené výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="92855-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="92855-116">Výrazy v závorkách přepsat přednost před i další více úrovní vnoření.</span><span class="sxs-lookup"><span data-stu-id="92855-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="92855-117">Výrazy v závorkách nejvíce hluboko vnořené se vyhodnocují jako první, za nímž následuje další nejvíce hluboko vnořené, a tak dále alespoň hluboko vložené a nakonec výrazů mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="92855-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="92855-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="92855-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="92855-119">V předchozím příkladu `z + 2` vyhodnotí první, pak je shod výrazy.</span><span class="sxs-lookup"><span data-stu-id="92855-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="92855-120">Exponenciální zápis, což obvykle má vyšší prioritu než přidání nebo násobení, je v tomto příkladu vyhodnotit poslední, protože jiné výrazy jsou uzavřené v závorkách.</span><span class="sxs-lookup"><span data-stu-id="92855-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92855-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="92855-121">See Also</span></span>  
 [<span data-ttu-id="92855-122">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92855-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="92855-123">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92855-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="92855-124">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92855-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="92855-125">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92855-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="92855-126">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="92855-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="92855-127">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="92855-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="92855-128">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="92855-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="92855-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92855-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
