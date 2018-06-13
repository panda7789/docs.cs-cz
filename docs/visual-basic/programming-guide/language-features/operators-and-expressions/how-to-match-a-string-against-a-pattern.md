---
title: 'Postupy: Porovnání řetězce se vzorem (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655209"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="e6bac-102">Postupy: Porovnání řetězce se vzorem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6bac-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="e6bac-103">Pokud chcete zjistit, zda výraz, který [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md) splňuje vzor, pak můžete použít [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e6bac-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="e6bac-104">`Like` má dva operandy.</span><span class="sxs-lookup"><span data-stu-id="e6bac-104">`Like` takes two operands.</span></span> <span data-ttu-id="e6bac-105">Levý operand je řetězcového výrazu a pravý operand řetězec obsahující vzor, který se má použít k porovnání.</span><span class="sxs-lookup"><span data-stu-id="e6bac-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="e6bac-106">`Like` Vrátí `Boolean` hodnotu, která určuje, zda splňuje řetězcového výrazu vzoru.</span><span class="sxs-lookup"><span data-stu-id="e6bac-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="e6bac-107">Je možné porovnávat každý znak v řetězcového výrazu proti konkrétní znak, zástupný znak, seznamu znaků nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="e6bac-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="e6bac-108">Pozice specifikace v řetězci vzor odpovídají pozice znaků, které mají být obsažena ve řetězcového výrazu.</span><span class="sxs-lookup"><span data-stu-id="e6bac-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="e6bac-109">Tak, aby odpovídaly znak v řetězcového výrazu proti konkrétní znak</span><span class="sxs-lookup"><span data-stu-id="e6bac-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="e6bac-110">Uveďte daného znaku přímo v řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6bac-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="e6bac-111">Některé speciální znaky musí být uzavřena do hranatých závorek (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e6bac-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="e6bac-112">Další informace najdete v tématu [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e6bac-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="e6bac-113">Následující příklad testy zda `myString` se skládá právě z jednoho znaku `H`.</span><span class="sxs-lookup"><span data-stu-id="e6bac-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="e6bac-114">Tak, aby odpovídaly znak v řetězcového výrazu proti zástupný znak</span><span class="sxs-lookup"><span data-stu-id="e6bac-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="e6bac-115">Uveďte otazník (`?`) v řetězci vzor.</span><span class="sxs-lookup"><span data-stu-id="e6bac-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="e6bac-116">Libovolný platný znak v této pozici Díky úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="e6bac-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="e6bac-117">Následující příklad testy zda `myString` se skládá z jednoho znaku `W` následované přesně dva znaky žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e6bac-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="e6bac-118">Tak, aby odpovídaly znak v řetězcového výrazu podle seznamu znaků</span><span class="sxs-lookup"><span data-stu-id="e6bac-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="e6bac-119">Uveďte závorky (`[ ]`) v řetězci vzor a v závorkách put seznamu znaků.</span><span class="sxs-lookup"><span data-stu-id="e6bac-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="e6bac-120">Není jednotlivé znaky oddělte čárkami nebo jiný oddělovač.</span><span class="sxs-lookup"><span data-stu-id="e6bac-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="e6bac-121">Libovolný znak v seznamu Díky úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="e6bac-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="e6bac-122">Následující příklad testy zda `myString` se skládá z libovolný platný znak právě jeden z znaky následované `A`, `C`, nebo `E`.</span><span class="sxs-lookup"><span data-stu-id="e6bac-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     <span data-ttu-id="e6bac-123">Upozorňujeme, že toto porovnání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e6bac-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="e6bac-124">Tak, aby odpovídaly znak v řetězcového výrazu proti rozsah znaků</span><span class="sxs-lookup"><span data-stu-id="e6bac-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="e6bac-125">Uveďte závorky (`[ ]`) v řetězci vzor a v závorkách put nejnižší a nejvyšší znaky v rozsahu, oddělené pomlčkou (`–`).</span><span class="sxs-lookup"><span data-stu-id="e6bac-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="e6bac-126">Libovolný znak v rozsahu Díky úspěšné shody.</span><span class="sxs-lookup"><span data-stu-id="e6bac-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="e6bac-127">Následující příklad testy zda `myString` tvořený znaky `num` právě jeden z znaky následované `i`, `j`, `k`, `l`, `m`, nebo `n`.</span><span class="sxs-lookup"><span data-stu-id="e6bac-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     <span data-ttu-id="e6bac-128">Upozorňujeme, že toto porovnání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e6bac-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="e6bac-129">Odpovídající prázdné řetězce</span><span class="sxs-lookup"><span data-stu-id="e6bac-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="e6bac-130">`Like` zpracovává sekvenci `[]` jako řetězec nulové délky (`""`).</span><span class="sxs-lookup"><span data-stu-id="e6bac-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="e6bac-131">Můžete použít `[]` k ověření, zda je výraz celý řetězec prázdný, ale nemůžete ji použít k testování, pokud na konkrétní pozici v řetězcového výrazu je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e6bac-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="e6bac-132">Je-li prázdné pozice jednu z možností je potřeba provést testování pro můžete použít `Like` více než jednou.</span><span class="sxs-lookup"><span data-stu-id="e6bac-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="e6bac-133">Tak, aby odpovídaly znak ve výrazu řetězec seznam znaky ani žádný znak</span><span class="sxs-lookup"><span data-stu-id="e6bac-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="e6bac-134">Volání `Like` operátor dvakrát ve stejném řetězcový výraz a připojení dvě volání s buď [operátor nebo](../../../../visual-basic/language-reference/operators/or-operator.md) nebo [orelse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e6bac-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="e6bac-135">V řetězci vzor pro první `Like` klauzule, zahrnují seznamu znaků v závorkách (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e6bac-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="e6bac-136">V řetězci vzor pro druhý `Like` klauzuli nevkládejte libovolný znak na pozici nejistá.</span><span class="sxs-lookup"><span data-stu-id="e6bac-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="e6bac-137">Následující příklad testy 7 číslic telefonního čísla `phoneNum` přesně tři číslice, za nímž následuje mezery, pomlčky (`–`), tečku (`.`), nebo žádný znak vůbec, následované přesně čtyři číslice.</span><span class="sxs-lookup"><span data-stu-id="e6bac-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e6bac-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6bac-138">See Also</span></span>  
 [<span data-ttu-id="e6bac-139">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="e6bac-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="e6bac-140">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e6bac-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="e6bac-141">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="e6bac-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="e6bac-142">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="e6bac-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
