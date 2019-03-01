---
title: Operátory a výrazy v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
  - 'operators [Visual Basic], operands'
  - 'operators [Visual Basic]'
  - 'operands [Visual Basic], definition'
  - 'Visual Basic code, operators'
  - 'Visual Basic code, expressions'
  - operands
  - 'expressions [Visual Basic]'
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="d2f7a-102">Operátory a výrazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2f7a-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="d2f7a-103">*Operátor* je prvek kódu, který provádí operace na jeden nebo více prvků kódu, které obsahují hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="d2f7a-104">Například prvky hodnotu proměnné, konstanty, literály, vlastnosti, vrátí z `Function` a `Operator` postupy a výrazy.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="d2f7a-105">*Výraz* je řady hodnota prvků v kombinaci s operátory, které vrací novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="d2f7a-106">Operátory elementů hodnotu zabývat tím, že provádí výpočty, porovnání nebo jiné operace.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="d2f7a-107">Typy operátorů</span><span class="sxs-lookup"><span data-stu-id="d2f7a-107">Types of Operators</span></span>  
 <span data-ttu-id="d2f7a-108">Visual Basic poskytuje následující typy operátorů:</span><span class="sxs-lookup"><span data-stu-id="d2f7a-108">Visual Basic provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="d2f7a-109">[Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) známých výpočtů na číselných hodnot, včetně jejich bitové vzory posunutí.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="d2f7a-110">[Operátory porovnání](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnat dva výrazy a vrátí `Boolean` hodnotu představující výsledek porovnání.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="d2f7a-111">[Operátory řetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) připojit k více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="d2f7a-112">[Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vrátí výsledek stejný datový typ jako hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="d2f7a-113">Hodnota prvků, které jsou spojené s operátorem se nazývají *operandy* tohoto operátoru.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="d2f7a-114">Operátory v kombinaci s výrazy formuláře prvky hodnot, s výjimkou operátoru přiřazení, které formuláře *příkaz*.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="d2f7a-115">Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f7a-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="d2f7a-116">Vyhodnocování výrazů</span><span class="sxs-lookup"><span data-stu-id="d2f7a-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="d2f7a-117">Představuje hodnotu, která je obvykle známých datový typ jako konečný výsledek výrazu `Boolean`, `String`, nebo číselného typu.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="d2f7a-118">Následují příklady výrazů.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="d2f7a-119">Několik operátorů můžete provádět akce v jednom výrazu nebo příkazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="d2f7a-120">V předchozím příkladu, Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`), pak přiřadí výslednou hodnotu proměnné `x` na levé straně.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="d2f7a-121">Praktické neomezený počet operátorů, které je možné kombinovat do výrazu, ale znalost [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nutné zajistit, že dostanete nezískáte očekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="d2f7a-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="d2f7a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2f7a-122">See also</span></span>
- [<span data-ttu-id="d2f7a-123">Operátory</span><span class="sxs-lookup"><span data-stu-id="d2f7a-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="d2f7a-124">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="d2f7a-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="d2f7a-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d2f7a-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
