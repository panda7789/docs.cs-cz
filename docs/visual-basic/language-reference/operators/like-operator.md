---
title: Like – operátor
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350936"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="cd397-102">Like – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd397-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="cd397-103">Compares a string against a pattern.</span><span class="sxs-lookup"><span data-stu-id="cd397-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="cd397-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span><span class="sxs-lookup"><span data-stu-id="cd397-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd397-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd397-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="cd397-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="cd397-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="cd397-107">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cd397-107">Required.</span></span> <span data-ttu-id="cd397-108">Any `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="cd397-108">Any `Boolean` variable.</span></span> <span data-ttu-id="cd397-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span><span class="sxs-lookup"><span data-stu-id="cd397-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="cd397-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cd397-110">Required.</span></span> <span data-ttu-id="cd397-111">Any `String` expression.</span><span class="sxs-lookup"><span data-stu-id="cd397-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="cd397-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cd397-112">Required.</span></span> <span data-ttu-id="cd397-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span><span class="sxs-lookup"><span data-stu-id="cd397-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd397-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd397-114">Remarks</span></span>  
 <span data-ttu-id="cd397-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="cd397-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="cd397-116">If the string does not satisfy the pattern, `result` is `False`.</span><span class="sxs-lookup"><span data-stu-id="cd397-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="cd397-117">If both `string` and `pattern` are empty strings, the result is `True`.</span><span class="sxs-lookup"><span data-stu-id="cd397-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="cd397-118">Comparison Method</span><span class="sxs-lookup"><span data-stu-id="cd397-118">Comparison Method</span></span>  
 <span data-ttu-id="cd397-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd397-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="cd397-120">The default string comparison method for each source file is `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="cd397-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="cd397-121">Pattern Options</span><span class="sxs-lookup"><span data-stu-id="cd397-121">Pattern Options</span></span>  
 <span data-ttu-id="cd397-122">Built-in pattern matching provides a versatile tool for string comparisons.</span><span class="sxs-lookup"><span data-stu-id="cd397-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="cd397-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span><span class="sxs-lookup"><span data-stu-id="cd397-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="cd397-124">The following table shows the characters allowed in `pattern` and what they match.</span><span class="sxs-lookup"><span data-stu-id="cd397-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="cd397-125">Characters in `pattern`</span><span class="sxs-lookup"><span data-stu-id="cd397-125">Characters in `pattern`</span></span>|<span data-ttu-id="cd397-126">Matches in `string`</span><span class="sxs-lookup"><span data-stu-id="cd397-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="cd397-127">Any single character</span><span class="sxs-lookup"><span data-stu-id="cd397-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="cd397-128">Zero or more characters</span><span class="sxs-lookup"><span data-stu-id="cd397-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="cd397-129">Any single digit (0–9)</span><span class="sxs-lookup"><span data-stu-id="cd397-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="cd397-130">Any single character in `charlist`</span><span class="sxs-lookup"><span data-stu-id="cd397-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="cd397-131">Any single character not in `charlist`</span><span class="sxs-lookup"><span data-stu-id="cd397-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="cd397-132">Character Lists</span><span class="sxs-lookup"><span data-stu-id="cd397-132">Character Lists</span></span>  
 <span data-ttu-id="cd397-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span><span class="sxs-lookup"><span data-stu-id="cd397-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="cd397-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span><span class="sxs-lookup"><span data-stu-id="cd397-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="cd397-135">When used outside brackets, the exclamation point matches itself.</span><span class="sxs-lookup"><span data-stu-id="cd397-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="cd397-136">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="cd397-136">Special Characters</span></span>  
 <span data-ttu-id="cd397-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span><span class="sxs-lookup"><span data-stu-id="cd397-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="cd397-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span><span class="sxs-lookup"><span data-stu-id="cd397-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="cd397-139">The character sequence `[]` is considered a zero-length string (`""`).</span><span class="sxs-lookup"><span data-stu-id="cd397-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="cd397-140">However, it cannot be part of a character list enclosed in brackets.</span><span class="sxs-lookup"><span data-stu-id="cd397-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="cd397-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span><span class="sxs-lookup"><span data-stu-id="cd397-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="cd397-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="cd397-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="cd397-143">Character Ranges</span><span class="sxs-lookup"><span data-stu-id="cd397-143">Character Ranges</span></span>  
 <span data-ttu-id="cd397-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span><span class="sxs-lookup"><span data-stu-id="cd397-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="cd397-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="cd397-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="cd397-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span><span class="sxs-lookup"><span data-stu-id="cd397-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="cd397-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span><span class="sxs-lookup"><span data-stu-id="cd397-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="cd397-148">Multiple Character Ranges</span><span class="sxs-lookup"><span data-stu-id="cd397-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="cd397-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span><span class="sxs-lookup"><span data-stu-id="cd397-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="cd397-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="cd397-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="cd397-151">Usage of the Hyphen</span><span class="sxs-lookup"><span data-stu-id="cd397-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="cd397-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span><span class="sxs-lookup"><span data-stu-id="cd397-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="cd397-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span><span class="sxs-lookup"><span data-stu-id="cd397-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="cd397-154">Collating Sequence</span><span class="sxs-lookup"><span data-stu-id="cd397-154">Collating Sequence</span></span>  
 <span data-ttu-id="cd397-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span><span class="sxs-lookup"><span data-stu-id="cd397-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="cd397-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span><span class="sxs-lookup"><span data-stu-id="cd397-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="cd397-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span><span class="sxs-lookup"><span data-stu-id="cd397-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="cd397-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span><span class="sxs-lookup"><span data-stu-id="cd397-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="cd397-159">Digraph Characters</span><span class="sxs-lookup"><span data-stu-id="cd397-159">Digraph Characters</span></span>  
 <span data-ttu-id="cd397-160">In some languages, there are alphabetic characters that represent two separate characters.</span><span class="sxs-lookup"><span data-stu-id="cd397-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="cd397-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span><span class="sxs-lookup"><span data-stu-id="cd397-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="cd397-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span><span class="sxs-lookup"><span data-stu-id="cd397-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="cd397-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span><span class="sxs-lookup"><span data-stu-id="cd397-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="cd397-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span><span class="sxs-lookup"><span data-stu-id="cd397-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cd397-165">Přetížení</span><span class="sxs-lookup"><span data-stu-id="cd397-165">Overloading</span></span>  
 <span data-ttu-id="cd397-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="cd397-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cd397-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="cd397-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cd397-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cd397-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd397-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd397-169">Example</span></span>  
 <span data-ttu-id="cd397-170">This example uses the `Like` operator to compare strings to various patterns.</span><span class="sxs-lookup"><span data-stu-id="cd397-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="cd397-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span><span class="sxs-lookup"><span data-stu-id="cd397-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="cd397-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd397-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="cd397-173">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="cd397-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="cd397-174">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd397-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cd397-175">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="cd397-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cd397-176">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="cd397-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="cd397-177">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="cd397-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="cd397-178">Postupy: Porovnání řetězce se vzorem</span><span class="sxs-lookup"><span data-stu-id="cd397-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
