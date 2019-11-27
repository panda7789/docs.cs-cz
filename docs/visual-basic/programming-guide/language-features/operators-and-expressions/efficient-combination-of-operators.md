---
title: Účinná kombinace operátorů
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
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348973"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="40370-102">Účinná kombinace operátorů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40370-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="40370-103">Složité výrazy mohou obsahovat mnoho různých operátorů.</span><span class="sxs-lookup"><span data-stu-id="40370-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="40370-104">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="40370-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="40370-105">Vytváření složitých výrazů, jako je například v předchozím příkladu, vyžaduje důkladné porozumění pravidlům s prioritou operátorů.</span><span class="sxs-lookup"><span data-stu-id="40370-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="40370-106">Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="40370-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="40370-107">Výrazy kulatého závorky</span><span class="sxs-lookup"><span data-stu-id="40370-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="40370-108">Často chcete, aby operace pokračovaly v jiném pořadí, než je určeno podle priority operátora.</span><span class="sxs-lookup"><span data-stu-id="40370-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="40370-109">Vezměte v úvahu následující příklad.</span><span class="sxs-lookup"><span data-stu-id="40370-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="40370-110">Předchozí příklad vynásobí `z` hodnotou `y`a následně přidá výsledek do `4`.</span><span class="sxs-lookup"><span data-stu-id="40370-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="40370-111">Pokud ale chcete přidat `y` a `4` před vynásobením výsledku hodnotou `z`, můžete přepsat normální prioritu operátoru pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="40370-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="40370-112">Uzavřením výrazu do závorek vynutíte, aby byl tento výraz vyhodnocen jako první, bez ohledu na přednost operátoru.</span><span class="sxs-lookup"><span data-stu-id="40370-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="40370-113">Chcete-li vynutit předchozí příklad pro přidání prvního, můžete ho přepsat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="40370-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="40370-114">Předchozí příklad přidá `y` a `4`a pak vynásobí součet hodnotou `z`.</span><span class="sxs-lookup"><span data-stu-id="40370-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="40370-115">Vnořené výrazy na kulaté závorky</span><span class="sxs-lookup"><span data-stu-id="40370-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="40370-116">Můžete vnořit výrazy do několika úrovní závorek a ještě víc přepsat jejich prioritu.</span><span class="sxs-lookup"><span data-stu-id="40370-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="40370-117">Výrazy, které jsou nejvíce vnořené v závorkách, jsou vyhodnoceny jako první, následované nejbližší vnořenou, a tak dále v nejmenším hluboko vnořeném a nakonec výrazy mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="40370-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="40370-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="40370-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="40370-119">V předchozím příkladu je `z + 2` vyhodnocen jako první a pak ostatní výrazy kulatého závorky.</span><span class="sxs-lookup"><span data-stu-id="40370-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="40370-120">Umocnění, které obvykle má vyšší prioritu než sčítání nebo násobení, je vyhodnoceno jako poslední v tomto příkladu, protože ostatní výrazy jsou uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="40370-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40370-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40370-121">See also</span></span>

- [<span data-ttu-id="40370-122">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40370-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="40370-123">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40370-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="40370-124">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40370-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="40370-125">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40370-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="40370-126">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="40370-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="40370-127">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="40370-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="40370-128">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="40370-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="40370-129">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40370-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
