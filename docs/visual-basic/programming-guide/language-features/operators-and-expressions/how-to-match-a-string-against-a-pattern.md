---
title: 'Postupy: Porovnání řetězce se vzorem'
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
ms.openlocfilehash: d8a3c363d1a443db4a0b7633e380562af1913aca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403443"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="bfbc6-102">Postupy: Porovnání řetězce se vzorem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfbc6-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="bfbc6-103">Pokud chcete zjistit, zda výraz [řetězcového datového typu](../../../language-reference/data-types/string-data-type.md) splňuje vzor, lze použít [operátor LIKE](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-103">If you want to find out if an expression of the [String Data Type](../../../language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="bfbc6-104">`Like`přebírá dva operandy.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-104">`Like` takes two operands.</span></span> <span data-ttu-id="bfbc6-105">Levý operand je řetězcový výraz a pravý operand je řetězec obsahující vzor, který se má použít pro porovnávání.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="bfbc6-106">`Like`Vrátí `Boolean` hodnotu, která označuje, zda řetězcový výraz vyhovuje vzoru.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="bfbc6-107">Každý znak v řetězcovém výrazu můžete porovnat s konkrétním znakem, zástupným znakem, seznamem znaků nebo rozsahem znaků.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="bfbc6-108">Pozice specifikací v řetězci vzoru odpovídají polohám znaků, které mají být ve výrazu řetězce spárovány.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="bfbc6-109">Chcete-li porovnat znak v řetězcovém výrazu proti určitému znaku</span><span class="sxs-lookup"><span data-stu-id="bfbc6-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="bfbc6-110">Konkrétní znak umístěte přímo do řetězce vzoru.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="bfbc6-111">Některé speciální znaky musí být uzavřeny do závorek ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="bfbc6-112">Další informace naleznete v tématu [operátor LIKE](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-112">For more information, see [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="bfbc6-113">Následující příklad testuje, zda `myString` je tvořen přesně jedním znakem `H` .</span><span class="sxs-lookup"><span data-stu-id="bfbc6-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="bfbc6-114">Chcete-li porovnat znak ve výrazu řetězce se zástupným znakem</span><span class="sxs-lookup"><span data-stu-id="bfbc6-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="bfbc6-115">Vložte otazník ( `?` ) do řetězce vzoru.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="bfbc6-116">Libovolný platný znak v této pozici provede úspěšnou shodu.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="bfbc6-117">Následující příklad testuje, zda `myString` se skládá z jednoho znaku `W` následovanýho přesně dvěma znaky libovolné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="bfbc6-118">Chcete-li porovnat znak ve výrazu řetězce se seznamem znaků</span><span class="sxs-lookup"><span data-stu-id="bfbc6-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="bfbc6-119">Vložte hranaté závorky ( `[ ]` ) do řetězce vzorů a uvnitř závorek vložte seznam znaků.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="bfbc6-120">Znaky nedělte čárkami ani žádné jiné oddělovače.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="bfbc6-121">Libovolný jeden znak v seznamu provede úspěšnou shodu.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="bfbc6-122">Následující příklad testuje, zda `myString` obsahuje libovolný platný znak následovaný přesně jedním ze znaků `A` , `C` nebo `E` .</span><span class="sxs-lookup"><span data-stu-id="bfbc6-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="bfbc6-123">Všimněte si, že tato shoda rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="bfbc6-124">Chcete-li porovnat znak ve výrazu řetězce s rozsahem znaků</span><span class="sxs-lookup"><span data-stu-id="bfbc6-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="bfbc6-125">Vložte hranaté závorky ( `[ ]` ) do řetězce vzorů a uvnitř závorek vložte nejnižší a nejvyšší znaky v rozsahu oddělené spojovníkem ( `–` ).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="bfbc6-126">Libovolný jednotlivý znak v rozsahu provede úspěšnou shodu.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="bfbc6-127">Následující příklad testuje, zda `myString` se skládá ze znaků `num` následovaných právě jedním ze znaků `i` ,,,, `j` `k` `l` `m` nebo `n` .</span><span class="sxs-lookup"><span data-stu-id="bfbc6-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="bfbc6-128">Všimněte si, že tato shoda rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="bfbc6-129">Porovnání prázdných řetězců</span><span class="sxs-lookup"><span data-stu-id="bfbc6-129">Matching Empty Strings</span></span>

<span data-ttu-id="bfbc6-130">`Like`zpracuje sekvenci `[]` jako řetězec s nulovou délkou ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="bfbc6-131">Můžete použít `[]` k otestování, zda je celý řetězcový výraz prázdný, ale nelze jej použít k otestování, pokud je určitá pozice ve výrazu řetězce prázdná.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="bfbc6-132">Pokud je prázdná pozice jednou z možností, které je třeba otestovat, můžete použít `Like` více než jednou.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="bfbc6-133">Chcete-li porovnat znak ve výrazu řetězce se seznamem znaků nebo žádným znakem</span><span class="sxs-lookup"><span data-stu-id="bfbc6-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="bfbc6-134">Zavolejte `Like` operátor dvakrát u stejného řetězcového výrazu a připojte dvě volání pomocí [operátoru OR](../../../language-reference/operators/or-operator.md) nebo [operátoru OrElse](../../../language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../language-reference/operators/or-operator.md) or the [OrElse Operator](../../../language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="bfbc6-135">V řetězci vzoru pro první `Like` klauzuli uveďte seznam znaků uzavřený do závorek ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="bfbc6-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="bfbc6-136">V řetězci vzoru pro druhou `Like` klauzuli neumísťujte žádný znak na pozici v daném umístění.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="bfbc6-137">Následující příklad testuje sedm číslic telefonního čísla `phoneNum` pro přesně tři číselné číslice, za kterými následuje mezera, spojovník ( `–` ), tečka ( `.` ) nebo žádný znak, následovaný přesně čtyřmi číselnými číslicemi.</span><span class="sxs-lookup"><span data-stu-id="bfbc6-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="bfbc6-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfbc6-138">See also</span></span>

- [<span data-ttu-id="bfbc6-139">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="bfbc6-139">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="bfbc6-140">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="bfbc6-140">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="bfbc6-141">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="bfbc6-141">Like Operator</span></span>](../../../language-reference/operators/like-operator.md)
- [<span data-ttu-id="bfbc6-142">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="bfbc6-142">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
