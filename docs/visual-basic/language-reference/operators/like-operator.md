---
title: "Like – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad5729515362bfd52b0c3b401f218a49f569726e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="80f0d-102">Like – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80f0d-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="80f0d-103">Porovnání řetězce se vzorem.</span><span class="sxs-lookup"><span data-stu-id="80f0d-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80f0d-104">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="80f0d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="80f0d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="80f0d-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="80f0d-106">Required.</span></span> <span data-ttu-id="80f0d-107">Všechny `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="80f0d-107">Any `Boolean` variable.</span></span> <span data-ttu-id="80f0d-108">Výsledkem je, `Boolean` hodnotu, která určuje, jestli `string` splňuje požadavky `pattern`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="80f0d-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="80f0d-109">Required.</span></span> <span data-ttu-id="80f0d-110">Všechny `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="80f0d-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="80f0d-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="80f0d-111">Required.</span></span> <span data-ttu-id="80f0d-112">Všechny `String` výraz, který odpovídá se porovnávání názvů popsané v "Poznámky."</span><span class="sxs-lookup"><span data-stu-id="80f0d-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80f0d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80f0d-113">Remarks</span></span>  
 <span data-ttu-id="80f0d-114">Pokud je hodnota v `string` splňuje vzoru obsažené v `pattern`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="80f0d-115">Pokud řetězec nevyhovuje vzoru, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="80f0d-116">Pokud oba `string` a `pattern` jsou prázdné řetězce, výsledkem je `True`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="80f0d-117">Metoda porovnání</span><span class="sxs-lookup"><span data-stu-id="80f0d-117">Comparison Method</span></span>  
 <span data-ttu-id="80f0d-118">Chování `Like` operátor závisí na [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="80f0d-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="80f0d-119">Je výchozí metodou porovnání řetězce pro každý zdrojový soubor `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="80f0d-120">Vzor možnosti</span><span class="sxs-lookup"><span data-stu-id="80f0d-120">Pattern Options</span></span>  
 <span data-ttu-id="80f0d-121">Shoda vzoru předdefinované poskytuje univerzální nástroj pro porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="80f0d-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="80f0d-122">Funkce porovnávání umožňují odpovídat každý znak v `string` proti konkrétní znak, zástupný znak, seznamu znaků nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="80f0d-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="80f0d-123">V následující tabulce jsou uvedeny povolených znaků v `pattern` a budou odpovídat.</span><span class="sxs-lookup"><span data-stu-id="80f0d-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="80f0d-124">Znaků.`pattern`</span><span class="sxs-lookup"><span data-stu-id="80f0d-124">Characters in `pattern`</span></span>|<span data-ttu-id="80f0d-125">Odpovídá v`string`</span><span class="sxs-lookup"><span data-stu-id="80f0d-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="80f0d-126">Libovolný znak</span><span class="sxs-lookup"><span data-stu-id="80f0d-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="80f0d-127">Žádný nebo více znaků</span><span class="sxs-lookup"><span data-stu-id="80f0d-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="80f0d-128">Všechny jednu číslici (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="80f0d-128">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="80f0d-129">Libovolný znak v`charlist`</span><span class="sxs-lookup"><span data-stu-id="80f0d-129">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="80f0d-130">Libovolný znak není v`charlist`</span><span class="sxs-lookup"><span data-stu-id="80f0d-130">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="80f0d-131">Znak zobrazí</span><span class="sxs-lookup"><span data-stu-id="80f0d-131">Character Lists</span></span>  
 <span data-ttu-id="80f0d-132">Skupinu jeden nebo více znaků (`charlist`) uzavřeny do hranatých závorek (`[ ]`) lze nahradit libovolný znak v `string` a může obsahovat téměř jakoukoli znak kód, včetně číslic.</span><span class="sxs-lookup"><span data-stu-id="80f0d-132">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="80f0d-133">S vykřičníkem (`!`) na začátku `charlist` znamená, že shoda se provádí v případě, že všechny znak s výjimkou znaků v `charlist` se nachází v `string`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-133">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="80f0d-134">Při použití mimo závorky, odpovídá vykřičník sám sebe.</span><span class="sxs-lookup"><span data-stu-id="80f0d-134">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="80f0d-135">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="80f0d-135">Special Characters</span></span>  
 <span data-ttu-id="80f0d-136">Tak, aby odpovídaly speciální znaky levou hranatou závorku (`[`), otazník (`?`), počet přihlášení (`#`) a znak hvězdičky (`*`), uzavřete je do hranatých závorek.</span><span class="sxs-lookup"><span data-stu-id="80f0d-136">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="80f0d-137">Pravou hranatou závorku (`]`) nelze použít v rámci skupiny tak, aby odpovídaly samostatně, ale dá se používat mimo skupinu jako samostatný znak.</span><span class="sxs-lookup"><span data-stu-id="80f0d-137">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="80f0d-138">Posloupnost znaků `[]` se považuje za řetězec nulové délky (`""`).</span><span class="sxs-lookup"><span data-stu-id="80f0d-138">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="80f0d-139">Však nemůže být součástí seznam znak v závorkách.</span><span class="sxs-lookup"><span data-stu-id="80f0d-139">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="80f0d-140">Pokud chcete zkontrolovat, zda pozice v `string` obsahuje jednu skupinu znaky ani žádný znak na všechny, můžete použít `Like` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="80f0d-140">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="80f0d-141">Příklad, naleznete v části [postupy: porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="80f0d-141">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="80f0d-142">Rozsahy znaků</span><span class="sxs-lookup"><span data-stu-id="80f0d-142">Character Ranges</span></span>  
 <span data-ttu-id="80f0d-143">Použitím spojovníku (`–`) oddělit dolní i horní hranici rozsahu, `charlist` můžete zadat rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="80f0d-143">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="80f0d-144">Například `[A–Z]` výsledkem shody, pokud odpovídající znaku pozice v `string` obsahuje libovolný znak v rozsahu `A`–`Z`, a `[!H–L]` výsledků v shody, pokud odpovídající znaku pozice libovolný znak mimo rozsah obsahuje `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-144">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="80f0d-145">Když zadáte rozsah znaků, musí se zobrazí ve vzestupném pořadí řazení, který je od nejnižší a nejvyšší.</span><span class="sxs-lookup"><span data-stu-id="80f0d-145">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="80f0d-146">Proto `[A–Z]` je platný vzor, ale `[Z–A]` není.</span><span class="sxs-lookup"><span data-stu-id="80f0d-146">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="80f0d-147">Více rozsahům znak</span><span class="sxs-lookup"><span data-stu-id="80f0d-147">Multiple Character Ranges</span></span>  
 <span data-ttu-id="80f0d-148">Pokud chcete zadat víc rozsahů pro stejné pozice znaku, jejich umístění v rámci stejné závorky bez oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="80f0d-148">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="80f0d-149">Například `[A–CX–Z]` výsledkem shody, pokud odpovídající znaku pozice v `string` obsahuje libovolný znak buď rozsahu `A`–`C` nebo rozsahu `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-149">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="80f0d-150">Využití spojovník</span><span class="sxs-lookup"><span data-stu-id="80f0d-150">Usage of the Hyphen</span></span>  
 <span data-ttu-id="80f0d-151">Pomlčka (`–`) můžete zobrazit na začátku (po s vykřičníkem, pokud existuje) nebo na konci `charlist` tak, aby odpovídaly sám sebe.</span><span class="sxs-lookup"><span data-stu-id="80f0d-151">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="80f0d-152">V jiném umístění určuje pomlčka rozsah znaků, které jsou odděleny znaky na obou stranách spojovník.</span><span class="sxs-lookup"><span data-stu-id="80f0d-152">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="80f0d-153">Pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="80f0d-153">Collating Sequence</span></span>  
 <span data-ttu-id="80f0d-154">Význam zadaný rozsah závisí na znak řazení v době běhu určeného `Option``Compare` a nastavení národního prostředí systému kód běží na.</span><span class="sxs-lookup"><span data-stu-id="80f0d-154">The meaning of a specified range depends on the character ordering at run time, as determined by `Option``Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="80f0d-155">S `Option``Compare``Binary`, rozsahu `[A–E]` odpovídá `A`, `B`, `C`, `D`, a `E`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-155">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="80f0d-156">S `Option``Compare``Text`, `[A–E]` odpovídá `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, a `e`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-156">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="80f0d-157">Rozsah neodpovídá `Ê` nebo `ê` protože znaky s diakritikou collate po příslušných znaků v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="80f0d-157">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="80f0d-158">Spřežka znaků</span><span class="sxs-lookup"><span data-stu-id="80f0d-158">Digraph Characters</span></span>  
 <span data-ttu-id="80f0d-159">V některých jazycích jsou znaky abecedy, které představují dva samostatné znaky.</span><span class="sxs-lookup"><span data-stu-id="80f0d-159">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="80f0d-160">Například několik jazyků použít znak `æ` představují znaky `a` a `e` Jakmile se zobrazí společně.</span><span class="sxs-lookup"><span data-stu-id="80f0d-160">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="80f0d-161">`Like` Operátor rozpozná, že spřežka jeden znak a dva jednotlivé znaky jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="80f0d-161">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="80f0d-162">Když je jazyk, který používá znak spřežka zadaný v nastavení národního prostředí systému, výskytu jedné spřežka znaku buď `pattern` nebo `string` odpovídá ekvivalentní pořadí dvou znaků v další řetězec.</span><span class="sxs-lookup"><span data-stu-id="80f0d-162">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="80f0d-163">Podobně spřežka znak v `pattern` v závorkách (samy o sobě, v seznamu, nebo v rozsahu) odpovídá ekvivalentní pořadí dvou znaků v `string`.</span><span class="sxs-lookup"><span data-stu-id="80f0d-163">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="80f0d-164">Přetížení</span><span class="sxs-lookup"><span data-stu-id="80f0d-164">Overloading</span></span>  
 <span data-ttu-id="80f0d-165">`Like` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="80f0d-165">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="80f0d-166">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="80f0d-166">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="80f0d-167">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="80f0d-167">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80f0d-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="80f0d-168">Example</span></span>  
 <span data-ttu-id="80f0d-169">Tento příklad používá `Like` operátor pro porovnání řetězců do různých vzorů.</span><span class="sxs-lookup"><span data-stu-id="80f0d-169">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="80f0d-170">Výsledky přejděte do `Boolean` proměnné, která určuje, zda každý řetězec splňuje vzoru.</span><span class="sxs-lookup"><span data-stu-id="80f0d-170">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="80f0d-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="80f0d-171">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="80f0d-172">Operátory porovnávání</span><span class="sxs-lookup"><span data-stu-id="80f0d-172">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="80f0d-173">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80f0d-173">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="80f0d-174">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="80f0d-174">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="80f0d-175">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="80f0d-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="80f0d-176">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="80f0d-176">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="80f0d-177">Postupy: porovnání řetězce se vzorem</span><span class="sxs-lookup"><span data-stu-id="80f0d-177">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
