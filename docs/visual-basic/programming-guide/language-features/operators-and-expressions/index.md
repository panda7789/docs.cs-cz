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
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403431"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="7b815-102">Operátory a výrazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b815-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="7b815-103">*Operátor* je prvek kódu, který provádí operaci na jednom nebo více prvcích kódu, které uchovávají hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7b815-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="7b815-104">Mezi prvky hodnoty patří proměnné, konstanty, literály, vlastnosti, návratové `Function` `Operator` procedury a a výrazy.</span><span class="sxs-lookup"><span data-stu-id="7b815-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="7b815-105">*Výraz* je řada prvků hodnot, které jsou kombinovány s operátory, což má za důsledek novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7b815-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="7b815-106">Operátory působí na prvky hodnoty provedením výpočtů, porovnávání nebo jiných operací.</span><span class="sxs-lookup"><span data-stu-id="7b815-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="7b815-107">Typy operátorů</span><span class="sxs-lookup"><span data-stu-id="7b815-107">Types of Operators</span></span>  
 <span data-ttu-id="7b815-108">Visual Basic poskytuje následující typy operátorů:</span><span class="sxs-lookup"><span data-stu-id="7b815-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="7b815-109">[Aritmetické operátory](arithmetic-operators.md) provádějí známé výpočty číselných hodnot, včetně posunování jejich bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="7b815-109">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="7b815-110">[Relační operátory](comparison-operators.md) porovnávají dva výrazy a vrátí `Boolean` hodnotu představující výsledek porovnání.</span><span class="sxs-lookup"><span data-stu-id="7b815-110">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="7b815-111">[Operátory zřetězení](concatenation-operators.md) spojí více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="7b815-111">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="7b815-112">[Logické a bitové operátory v Visual Basic](logical-and-bitwise-operators.md) slučují `Boolean` nebo číslují hodnoty a vracejí výsledek stejného datového typu jako hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7b815-112">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="7b815-113">Prvky hodnoty, které jsou kombinovány s operátorem, se nazývají *operandy* daného operátoru.</span><span class="sxs-lookup"><span data-stu-id="7b815-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="7b815-114">Operátory kombinované s prvky hodnoty formuláře s výjimkou operátoru přiřazení, který tvoří *příkaz*.</span><span class="sxs-lookup"><span data-stu-id="7b815-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="7b815-115">Další informace najdete v tématu [příkazy](../statements.md).</span><span class="sxs-lookup"><span data-stu-id="7b815-115">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="7b815-116">Vyhodnocení výrazů</span><span class="sxs-lookup"><span data-stu-id="7b815-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="7b815-117">Konečný výsledek výrazu představuje hodnotu, což je obvykle známý datový typ `Boolean` , například, `String` nebo číselný typ.</span><span class="sxs-lookup"><span data-stu-id="7b815-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="7b815-118">Následují příklady výrazů.</span><span class="sxs-lookup"><span data-stu-id="7b815-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="7b815-119">Několik operátorů může provádět akce v jednom výrazu nebo příkazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7b815-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="7b815-120">V předchozím příkladu Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení ( `=` ) a potom přiřadí výslednou hodnotu k proměnné `x` na levé straně.</span><span class="sxs-lookup"><span data-stu-id="7b815-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="7b815-121">Neexistuje žádné praktické omezení počtu operátorů, které je možné zkombinovat do výrazu, ale porozumění [prioritě operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md) je nezbytné k zajištění toho, abyste dosáhli očekávaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="7b815-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7b815-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b815-122">See also</span></span>

- [<span data-ttu-id="7b815-123">Operátory</span><span class="sxs-lookup"><span data-stu-id="7b815-123">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="7b815-124">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="7b815-124">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="7b815-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="7b815-125">Statements</span></span>](../../../language-reference/statements/index.md)
