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
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401550"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="20df0-102">Like – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20df0-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="20df0-103">Porovná řetězec se vzorem.</span><span class="sxs-lookup"><span data-stu-id="20df0-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="20df0-104">`Like`Operátor není aktuálně podporován v projektech .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="20df0-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="20df0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20df0-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="20df0-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="20df0-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="20df0-107">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20df0-107">Required.</span></span> <span data-ttu-id="20df0-108">Libovolná `Boolean` Proměnná.</span><span class="sxs-lookup"><span data-stu-id="20df0-108">Any `Boolean` variable.</span></span> <span data-ttu-id="20df0-109">Výsledkem je hodnota, `Boolean` která označuje, zda `string` vyhovuje `pattern` .</span><span class="sxs-lookup"><span data-stu-id="20df0-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="20df0-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20df0-110">Required.</span></span> <span data-ttu-id="20df0-111">Libovolný `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="20df0-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="20df0-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20df0-112">Required.</span></span> <span data-ttu-id="20df0-113">Libovolný `String` výraz, který odpovídá konvencím porovnávání vzorů popsaným v části "poznámky".</span><span class="sxs-lookup"><span data-stu-id="20df0-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20df0-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20df0-114">Remarks</span></span>  
 <span data-ttu-id="20df0-115">Pokud hodnota v `string` splňuje vzor obsažený v `pattern` , `result` je `True` .</span><span class="sxs-lookup"><span data-stu-id="20df0-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="20df0-116">Pokud řetězec nevyhovuje vzoru, `result` je `False` .</span><span class="sxs-lookup"><span data-stu-id="20df0-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="20df0-117">Pokud `string` jsou a i `pattern` prázdné řetězce, výsledek je `True` .</span><span class="sxs-lookup"><span data-stu-id="20df0-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="20df0-118">Metoda porovnání</span><span class="sxs-lookup"><span data-stu-id="20df0-118">Comparison Method</span></span>  
 <span data-ttu-id="20df0-119">Chování `Like` operátora závisí na [příkazu Option Compare](../statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="20df0-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="20df0-120">Výchozí metoda porovnání řetězců pro každý zdrojový soubor je `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="20df0-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="20df0-121">Možnosti vzorku</span><span class="sxs-lookup"><span data-stu-id="20df0-121">Pattern Options</span></span>  
 <span data-ttu-id="20df0-122">Předdefinované porovnávání vzorů poskytuje univerzální nástroj pro porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="20df0-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="20df0-123">Funkce porovnávání se vzorci vám umožní porovnat jednotlivé znaky s `string` konkrétním znakem, zástupným znakem, seznamem znaků nebo rozsahem znaků.</span><span class="sxs-lookup"><span data-stu-id="20df0-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="20df0-124">V následující tabulce jsou uvedeny znaky, které `pattern` jsou povolené v a co se shodují.</span><span class="sxs-lookup"><span data-stu-id="20df0-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="20df0-125">Znaky v`pattern`</span><span class="sxs-lookup"><span data-stu-id="20df0-125">Characters in `pattern`</span></span>|<span data-ttu-id="20df0-126">Shody v`string`</span><span class="sxs-lookup"><span data-stu-id="20df0-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="20df0-127">Libovolný jeden znak</span><span class="sxs-lookup"><span data-stu-id="20df0-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="20df0-128">Nula nebo více znaků</span><span class="sxs-lookup"><span data-stu-id="20df0-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="20df0-129">Jakákoli jedna číslice (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="20df0-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="20df0-130">Libovolný jeden znak v`charlist`</span><span class="sxs-lookup"><span data-stu-id="20df0-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="20df0-131">Libovolný jeden znak, který není v`charlist`</span><span class="sxs-lookup"><span data-stu-id="20df0-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="20df0-132">Seznamy znaků</span><span class="sxs-lookup"><span data-stu-id="20df0-132">Character Lists</span></span>  
 <span data-ttu-id="20df0-133">Skupina jednoho nebo více znaků ( `charlist` ) uzavřená v závorkách ( `[ ]` ) se dá použít k porovnávání libovolného jednotlivého znaku v `string` a může obsahovat skoro jakýkoli kód znaku, včetně číslic.</span><span class="sxs-lookup"><span data-stu-id="20df0-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="20df0-134">Vykřičník ( `!` ) na začátku `charlist` znamená, že je provedena shoda, pokud libovolný znak kromě znaků v `charlist` je nalezen v `string` .</span><span class="sxs-lookup"><span data-stu-id="20df0-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="20df0-135">Při použití mimo hranaté závorky se vykřičník shoduje.</span><span class="sxs-lookup"><span data-stu-id="20df0-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="20df0-136">Speciální znaky</span><span class="sxs-lookup"><span data-stu-id="20df0-136">Special Characters</span></span>  
 <span data-ttu-id="20df0-137">Chcete-li najít shodu se speciálními znaky, levou hranatou závorku ( `[` ), otazníkem ( `?` ), číslem znaménkem ( `#` ) a hvězdičkou ( `*` ), vložte je do závorek.</span><span class="sxs-lookup"><span data-stu-id="20df0-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="20df0-138">Pravou hranatou závorku ( `]` ) nelze použít v rámci skupiny, aby se shodovala se sebou, ale lze ji použít mimo skupinu jako jednotlivý znak.</span><span class="sxs-lookup"><span data-stu-id="20df0-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="20df0-139">Sekvence znaků `[]` je považována za řetězec s nulovou délkou ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="20df0-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="20df0-140">Nemůže však být součástí seznamu znaků uzavřený v závorkách.</span><span class="sxs-lookup"><span data-stu-id="20df0-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="20df0-141">Pokud chcete zjistit, zda pozice v umístění `string` obsahuje jednu ze skupin znaků nebo žádný znak vůbec, můžete použít `Like` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="20df0-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="20df0-142">Příklad naleznete v tématu [How to: Match String to a vzor](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="20df0-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="20df0-143">Rozsahy znaků</span><span class="sxs-lookup"><span data-stu-id="20df0-143">Character Ranges</span></span>  
 <span data-ttu-id="20df0-144">Použitím spojovníku ( `–` ) k oddělení dolních a horních mezí rozsahu `charlist` lze určit rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="20df0-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="20df0-145">Výsledkem je například `[A–Z]` shoda, pokud odpovídající pozice znaku v `string` poli obsahuje libovolný znak v rozsahu `A` – `Z` a výsledkem je shoda, `[!H–L]` Pokud odpovídající pozice znaku obsahuje libovolný znak mimo rozsah `H` – `L` .</span><span class="sxs-lookup"><span data-stu-id="20df0-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="20df0-146">Když zadáte rozsah znaků, musí být ve vzestupném pořadí řazení, tj. od nejnižší po nejvyšší.</span><span class="sxs-lookup"><span data-stu-id="20df0-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="20df0-147">Proto `[A–Z]` je platný vzor, ale není `[Z–A]` .</span><span class="sxs-lookup"><span data-stu-id="20df0-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="20df0-148">Více rozsahů znaků</span><span class="sxs-lookup"><span data-stu-id="20df0-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="20df0-149">Chcete-li zadat více rozsahů pro stejné umístění znaků, vložte je do stejné hranaté závorky bez oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="20df0-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="20df0-150">Výsledkem je například `[A–CX–Z]` shoda, pokud odpovídající pozice znaku v `string` části obsahuje libovolný znak v rámci rozsahu `A` `C` nebo rozsahu `X` – `Z` .</span><span class="sxs-lookup"><span data-stu-id="20df0-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="20df0-151">Použití pomlčky</span><span class="sxs-lookup"><span data-stu-id="20df0-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="20df0-152">Spojovník ( `–` ) se může objevit buď na začátku (za vykřičníkem, pokud existuje), nebo na konci `charlist` pro vyhledání sebe sama.</span><span class="sxs-lookup"><span data-stu-id="20df0-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="20df0-153">V jakémkoli jiném umístění pomlčka identifikuje rozsah znaků oddělených znaky na obou stranách pomlčky.</span><span class="sxs-lookup"><span data-stu-id="20df0-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="20df0-154">Sekvence řazení</span><span class="sxs-lookup"><span data-stu-id="20df0-154">Collating Sequence</span></span>  
 <span data-ttu-id="20df0-155">Význam zadaného rozsahu závisí na řazení znaků v době běhu, podle určení `Option Compare` a nastavení národního prostředí systému, na kterém je spuštěný kód.</span><span class="sxs-lookup"><span data-stu-id="20df0-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="20df0-156">S `Option Compare Binary` , rozsah `[A–E]` odpovídá,,, `A` `B` `C` `D` a `E` .</span><span class="sxs-lookup"><span data-stu-id="20df0-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="20df0-157">With `Option Compare Text` , `[A–E]` Matches,, `A` `a` `À` , `à` , `B` , `b` , `C` , `c` , `D` , `d` , a `E` `e` .</span><span class="sxs-lookup"><span data-stu-id="20df0-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="20df0-158">Rozsah neodpovídá `Ê` nebo `ê` vzhledem k tomu, že znaky zvýrazněné v pořadí řazení jsou vyrovnávány po nezvýrazněných znacích.</span><span class="sxs-lookup"><span data-stu-id="20df0-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="20df0-159">Znaky grafu</span><span class="sxs-lookup"><span data-stu-id="20df0-159">Digraph Characters</span></span>  
 <span data-ttu-id="20df0-160">V některých jazycích existují abecední znaky, které představují dva samostatné znaky.</span><span class="sxs-lookup"><span data-stu-id="20df0-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="20df0-161">Například několik jazyků používá znak `æ` k reprezentaci znaků `a` a `e` když se zobrazí společně.</span><span class="sxs-lookup"><span data-stu-id="20df0-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="20df0-162">`Like`Operátor rozpozná, že jediný znak v grafu a dva jednotlivé znaky jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="20df0-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="20df0-163">Pokud je v nastavení národního prostředí systému určen jazyk, který používá znak rozgrafu, je výskyt jednoho znaku grafu v buď `pattern` nebo `string` stejný jako ekvivalentní sekvence dvou znaků v druhém řetězci.</span><span class="sxs-lookup"><span data-stu-id="20df0-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="20df0-164">Podobně znak v grafu `pattern` uzavřený v závorkách (sám o sobě, v seznamu nebo v rozsahu) odpovídá ekvivalentní posloupnosti dvou znaků v `string` .</span><span class="sxs-lookup"><span data-stu-id="20df0-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="20df0-165">Přetížení</span><span class="sxs-lookup"><span data-stu-id="20df0-165">Overloading</span></span>  
 <span data-ttu-id="20df0-166">`Like`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="20df0-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="20df0-167">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="20df0-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="20df0-168">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="20df0-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20df0-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="20df0-169">Example</span></span>  
 <span data-ttu-id="20df0-170">Tento příklad používá `Like` operátor k porovnání řetězců s různými vzory.</span><span class="sxs-lookup"><span data-stu-id="20df0-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="20df0-171">Výsledky se přejdou do `Boolean` proměnné, která označuje, jestli každý řetězec vyhovuje vzoru.</span><span class="sxs-lookup"><span data-stu-id="20df0-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="20df0-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="20df0-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="20df0-173">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="20df0-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="20df0-174">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20df0-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="20df0-175">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="20df0-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="20df0-176">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="20df0-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="20df0-177">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="20df0-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="20df0-178">Postupy: Porovnání řetězce se vzorem</span><span class="sxs-lookup"><span data-stu-id="20df0-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
