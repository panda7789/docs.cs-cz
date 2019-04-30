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
ms.openlocfilehash: c14aa35ce15549ad9eccabe2330a7c43b6795140
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864699"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="133d7-102">Postupy: Porovnání řetězce se vzorem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="133d7-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="133d7-103">Pokud chcete zjistit, zda výraz [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md) vyhovuje vzoru, můžete použít [operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="133d7-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="133d7-104">`Like` má dva operandy.</span><span class="sxs-lookup"><span data-stu-id="133d7-104">`Like` takes two operands.</span></span> <span data-ttu-id="133d7-105">Levý operand je výraz řetězce a pravý operand je řetězec obsahující vzor se použije k porovnání.</span><span class="sxs-lookup"><span data-stu-id="133d7-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="133d7-106">`Like` Vrátí `Boolean` hodnotu, která udává, zda splňuje řetězcového výrazu vzoru.</span><span class="sxs-lookup"><span data-stu-id="133d7-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="133d7-107">Odpovídá každému znaku v řetězci výraz proti konkrétní znak, zástupných znaků, seznam znak nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="133d7-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="133d7-108">Pozice specifikace v řetězci vzoru odpovídají pozic znaků, které mají být obsažena ve řetězcového výrazu.</span><span class="sxs-lookup"><span data-stu-id="133d7-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="133d7-109">Odpovídá znaku v řetězcový výraz proti konkrétní znak</span><span class="sxs-lookup"><span data-stu-id="133d7-109">To match a character in the string expression against a specific character</span></span>  
  
- <span data-ttu-id="133d7-110">Umístěte na konkrétní znak přímo řetězec vzoru.</span><span class="sxs-lookup"><span data-stu-id="133d7-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="133d7-111">Některé speciální znaky musí být uzavřen v závorkách (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="133d7-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="133d7-112">Další informace najdete v tématu [operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="133d7-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="133d7-113">Následující příklad testuje, jestli `myString` obsahuje přesně jeden znak `H`.</span><span class="sxs-lookup"><span data-stu-id="133d7-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="133d7-114">Odpovídá znaku v řetězci výraz proti zástupný znak</span><span class="sxs-lookup"><span data-stu-id="133d7-114">To match a character in the string expression against a wildcard character</span></span>  
  
- <span data-ttu-id="133d7-115">Vložit otazník (`?`) v řetězci vzor.</span><span class="sxs-lookup"><span data-stu-id="133d7-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="133d7-116">Jakýkoli platný znak na této pozici díky úspěšná shoda.</span><span class="sxs-lookup"><span data-stu-id="133d7-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="133d7-117">Následující příklad testuje, jestli `myString` se skládá z jednoho znaku `W` následovaný přesně dva znaky žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="133d7-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="133d7-118">Odpovídá znaku v řetězcového výrazu seznam znaků</span><span class="sxs-lookup"><span data-stu-id="133d7-118">To match a character in the string expression against a list of characters</span></span>  
  
- <span data-ttu-id="133d7-119">Umístit závorky (`[ ]`) v řetězci vzor a v závorkách vložit seznam znaků.</span><span class="sxs-lookup"><span data-stu-id="133d7-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="133d7-120">Pomocí čárky nebo jakéhokoliv jiného oddělovače neoddělujte znaky.</span><span class="sxs-lookup"><span data-stu-id="133d7-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="133d7-121">Libovolný znak v seznamu je úspěšná shoda.</span><span class="sxs-lookup"><span data-stu-id="133d7-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="133d7-122">Následující příklad testuje, jestli `myString` jakýkoli platný znak následovaný přesně jedním ze znaků se skládá ze `A`, `C`, nebo `E`.</span><span class="sxs-lookup"><span data-stu-id="133d7-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     <span data-ttu-id="133d7-123">Všimněte si, že tuto shodu je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="133d7-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="133d7-124">Odpovídá znaku v řetězci výraz proti rozsahu znaků</span><span class="sxs-lookup"><span data-stu-id="133d7-124">To match a character in the string expression against a range of characters</span></span>  
  
- <span data-ttu-id="133d7-125">Umístit závorky (`[ ]`) v řetězci vzor a v závorkách do rozsahu znaků nejnižší a nejvyšší oddělené pomlčkou (`–`).</span><span class="sxs-lookup"><span data-stu-id="133d7-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="133d7-126">Jakémukoli jednomu znaku v rozsahu díky úspěšná shoda.</span><span class="sxs-lookup"><span data-stu-id="133d7-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="133d7-127">Následující příklad testuje, jestli `myString` se skládá ze znaků `num` za nímž následuje přesně jedním ze znaků `i`, `j`, `k`, `l`, `m`, nebo `n`.</span><span class="sxs-lookup"><span data-stu-id="133d7-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     <span data-ttu-id="133d7-128">Všimněte si, že tuto shodu je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="133d7-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="133d7-129">Odpovídající prázdné řetězce</span><span class="sxs-lookup"><span data-stu-id="133d7-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="133d7-130">`Like` zpracovává sekvence `[]` jako řetězec nulové délky (`""`).</span><span class="sxs-lookup"><span data-stu-id="133d7-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="133d7-131">Můžete použít `[]` k ověření, zda výraz celý řetězec je prázdný, ale nemůžete je použít k testování, pokud na konkrétní umístění v řetězcového výrazu je prázdný.</span><span class="sxs-lookup"><span data-stu-id="133d7-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="133d7-132">Je-li prázdná pozice jednu z možností je potřeba testovat pro, můžete použít `Like` více než jednou.</span><span class="sxs-lookup"><span data-stu-id="133d7-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="133d7-133">Odpovídá znaku v řetězci výrazu seznam se znaky ani žádný znak</span><span class="sxs-lookup"><span data-stu-id="133d7-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1. <span data-ttu-id="133d7-134">Volání `Like` operátor dvakrát na stejném řetězcový výraz a dvě volání s buď [nebo operátor](../../../../visual-basic/language-reference/operators/or-operator.md) nebo [OrElse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="133d7-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2. <span data-ttu-id="133d7-135">V řetězci vzor pro první `Like` klauzule, zahrnují seznamu znak uzavřen v závorkách (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="133d7-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3. <span data-ttu-id="133d7-136">V řetězci vzor pro druhý `Like` klauzule neumisťujte libovolný znak na pozici nejistá.</span><span class="sxs-lookup"><span data-stu-id="133d7-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="133d7-137">Následující příklad testuje sedmičíselné telefonní číslo `phoneNum` přesně tři číslice, za nímž následuje mezeru, pomlčku (`–`), tečku (`.`), nebo žádný znak, následovaný přesně čtyři číslice.</span><span class="sxs-lookup"><span data-stu-id="133d7-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="133d7-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="133d7-138">See also</span></span>

- [<span data-ttu-id="133d7-139">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="133d7-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="133d7-140">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="133d7-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="133d7-141">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="133d7-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="133d7-142">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="133d7-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
