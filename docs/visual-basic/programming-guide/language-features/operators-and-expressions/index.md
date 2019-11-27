---
title: Operátory a výrazy
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343613"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="d0059-102">Operátory a výrazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0059-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="d0059-103">*Operátor* je prvek kódu, který provádí operaci na jednom nebo více prvcích kódu, které uchovávají hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0059-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="d0059-104">Prvky hodnoty zahrnují proměnné, konstanty, literály, vlastnosti, návrat z `Function` a `Operator` a výrazy.</span><span class="sxs-lookup"><span data-stu-id="d0059-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="d0059-105">*Výraz* je řada prvků hodnot, které jsou kombinovány s operátory, což má za důsledek novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d0059-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="d0059-106">Operátory působí na prvky hodnoty provedením výpočtů, porovnávání nebo jiných operací.</span><span class="sxs-lookup"><span data-stu-id="d0059-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="d0059-107">Typy operátorů</span><span class="sxs-lookup"><span data-stu-id="d0059-107">Types of Operators</span></span>  
 <span data-ttu-id="d0059-108">Visual Basic poskytuje následující typy operátorů:</span><span class="sxs-lookup"><span data-stu-id="d0059-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="d0059-109">[Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) provádějí známé výpočty číselných hodnot, včetně posunování jejich bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="d0059-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="d0059-110">[Relační operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnávají dva výrazy a vracejí hodnotu `Boolean` reprezentující výsledek porovnání.</span><span class="sxs-lookup"><span data-stu-id="d0059-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="d0059-111">[Operátory zřetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) spojí více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="d0059-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="d0059-112">[Logické a bitové operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vracet výsledek stejného datového typu jako hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0059-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="d0059-113">Prvky hodnoty, které jsou kombinovány s operátorem, se nazývají *operandy* daného operátoru.</span><span class="sxs-lookup"><span data-stu-id="d0059-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="d0059-114">Operátory kombinované s prvky hodnoty formuláře s výjimkou operátoru přiřazení, který tvoří *příkaz*.</span><span class="sxs-lookup"><span data-stu-id="d0059-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="d0059-115">Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="d0059-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="d0059-116">Vyhodnocení výrazů</span><span class="sxs-lookup"><span data-stu-id="d0059-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="d0059-117">Konečný výsledek výrazu představuje hodnotu, což je obvykle známý datový typ, například `Boolean`, `String`nebo číselný typ.</span><span class="sxs-lookup"><span data-stu-id="d0059-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="d0059-118">Následují příklady výrazů.</span><span class="sxs-lookup"><span data-stu-id="d0059-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="d0059-119">Několik operátorů může provádět akce v jednom výrazu nebo příkazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d0059-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="d0059-120">V předchozím příkladu Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`) a následně přiřadí výslednou hodnotu k proměnné `x` vlevo.</span><span class="sxs-lookup"><span data-stu-id="d0059-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="d0059-121">Neexistuje žádné praktické omezení počtu operátorů, které je možné zkombinovat do výrazu, ale porozumění [prioritě operátorů v Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nezbytné k zajištění toho, abyste dosáhli očekávaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="d0059-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d0059-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0059-122">See also</span></span>

- [<span data-ttu-id="d0059-123">Operátory</span><span class="sxs-lookup"><span data-stu-id="d0059-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="d0059-124">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="d0059-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="d0059-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d0059-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
