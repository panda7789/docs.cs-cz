---
title: "Účinná kombinace operátorů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="15fbd-102">Účinná kombinace operátorů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15fbd-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="15fbd-103">Složité výrazy může obsahovat mnoho různých operátory.</span><span class="sxs-lookup"><span data-stu-id="15fbd-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="15fbd-104">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15fbd-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="15fbd-105">Vytvoření složité výrazy, jako je třeba v předchozím příkladu vyžaduje důkladné znalosti týkající se pravidla operátorů.</span><span class="sxs-lookup"><span data-stu-id="15fbd-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="15fbd-106">Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="15fbd-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="15fbd-107">Výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="15fbd-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="15fbd-108">Často se má operace pokračovat v jiném pořadí od dáno operátorů.</span><span class="sxs-lookup"><span data-stu-id="15fbd-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="15fbd-109">Podívejte se na následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15fbd-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="15fbd-110">V předchozím příkladu vynásobí `z` podle `y`, pak přidá výsledek, který má `4`.</span><span class="sxs-lookup"><span data-stu-id="15fbd-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="15fbd-111">Ale pokud chcete přidat `y` a `4` před vynásobením výsledku podle `z`, normální priorita operátorů lze přepsat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="15fbd-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="15fbd-112">Uzavřením výrazu v závorkách, můžete vynutit tento výraz, který se vyhodnotí nejprve, bez ohledu na to operátorů.</span><span class="sxs-lookup"><span data-stu-id="15fbd-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="15fbd-113">Chcete-li vynutit v předchozím příkladu uděláte přidání, může být přepisování jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15fbd-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="15fbd-114">V předchozím příkladu přidá `y` a `4`, pak vynásobí tento součet podle `z`.</span><span class="sxs-lookup"><span data-stu-id="15fbd-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="15fbd-115">Vnořené výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="15fbd-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="15fbd-116">Výrazy v závorkách přepsat přednost před i další více úrovní vnoření.</span><span class="sxs-lookup"><span data-stu-id="15fbd-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="15fbd-117">Výrazy v závorkách nejvíce hluboko vnořené se vyhodnocují jako první, za nímž následuje další nejvíce hluboko vnořené, a tak dále alespoň hluboko vložené a nakonec výrazů mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="15fbd-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="15fbd-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15fbd-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="15fbd-119">V předchozím příkladu `z + 2` vyhodnotí první, pak je shod výrazy.</span><span class="sxs-lookup"><span data-stu-id="15fbd-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="15fbd-120">Exponenciální zápis, což obvykle má vyšší prioritu než přidání nebo násobení, je v tomto příkladu vyhodnotit poslední, protože jiné výrazy jsou uzavřené v závorkách.</span><span class="sxs-lookup"><span data-stu-id="15fbd-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15fbd-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="15fbd-121">See Also</span></span>  
 [<span data-ttu-id="15fbd-122">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15fbd-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="15fbd-123">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15fbd-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="15fbd-124">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15fbd-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="15fbd-125">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15fbd-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="15fbd-126">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="15fbd-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="15fbd-127">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="15fbd-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="15fbd-128">Postupy: výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="15fbd-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="15fbd-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15fbd-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
