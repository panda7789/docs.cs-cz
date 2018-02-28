---
title: "Kvantifikátory v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad4e8ab527ca59c21bf4771ca9d386866d9919f7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="quantifiers-in-regular-expressions"></a><span data-ttu-id="eec65-102">Kvantifikátory v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="eec65-102">Quantifiers in Regular Expressions</span></span>
<span data-ttu-id="eec65-103">Kvantifikátory zadejte, kolik instancí znaku, skupiny nebo třída znak musí být ve vstupu pro shodu, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="eec65-103">Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.</span></span>  <span data-ttu-id="eec65-104">Následující tabulka uvádí kvantifikátory nepodporuje rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="eec65-104">The following table lists the quantifiers supported by .NET.</span></span>  
  
|<span data-ttu-id="eec65-105">Typu greedy kvantifikátoru</span><span class="sxs-lookup"><span data-stu-id="eec65-105">Greedy quantifier</span></span>|<span data-ttu-id="eec65-106">Opožděné kvantifikátoru</span><span class="sxs-lookup"><span data-stu-id="eec65-106">Lazy quantifier</span></span>|<span data-ttu-id="eec65-107">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-107">Description</span></span>|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|<span data-ttu-id="eec65-108">Odpovídat počtu nula či více krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-108">Match zero or more times.</span></span>|  
|`+`|`+?`|<span data-ttu-id="eec65-109">Odpovídat jeden či více krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-109">Match one or more times.</span></span>|  
|`?`|`??`|<span data-ttu-id="eec65-110">Shoda jednou nebo.</span><span class="sxs-lookup"><span data-stu-id="eec65-110">Match zero or one time.</span></span>|  
|<span data-ttu-id="eec65-111">`{` *n* `}`</span><span class="sxs-lookup"><span data-stu-id="eec65-111">`{` *n* `}`</span></span>|<span data-ttu-id="eec65-112">`{` *n* `}?`</span><span class="sxs-lookup"><span data-stu-id="eec65-112">`{` *n* `}?`</span></span>|<span data-ttu-id="eec65-113">Přesně shodují  *n*  časy.</span><span class="sxs-lookup"><span data-stu-id="eec65-113">Match exactly *n* times.</span></span>|  
|<span data-ttu-id="eec65-114">`{` *n* `,}`</span><span class="sxs-lookup"><span data-stu-id="eec65-114">`{` *n* `,}`</span></span>|<span data-ttu-id="eec65-115">`{` *n* `,}?`</span><span class="sxs-lookup"><span data-stu-id="eec65-115">`{` *n* `,}?`</span></span>|<span data-ttu-id="eec65-116">Odpovídají alespoň  *n*  časy.</span><span class="sxs-lookup"><span data-stu-id="eec65-116">Match at least *n* times.</span></span>|  
|<span data-ttu-id="eec65-117">`{` *n* `,` *m* `}`</span><span class="sxs-lookup"><span data-stu-id="eec65-117">`{` *n* `,` *m* `}`</span></span>|<span data-ttu-id="eec65-118">`{` *n* `,` *m* `}?`</span><span class="sxs-lookup"><span data-stu-id="eec65-118">`{` *n* `,` *m* `}?`</span></span>|<span data-ttu-id="eec65-119">Odpovídat z  *n*  k *m* časy.</span><span class="sxs-lookup"><span data-stu-id="eec65-119">Match from *n* to *m* times.</span></span>|  
  
 <span data-ttu-id="eec65-120">Množství `n` a `m` jsou celočíselné konstanty.</span><span class="sxs-lookup"><span data-stu-id="eec65-120">The quantities `n` and `m` are integer constants.</span></span> <span data-ttu-id="eec65-121">Obvykle jsou kvantifikátory typu greedy; způsobí modul regulárních výrazů tak, aby odpovídaly tolik výskyty určité vzory míře.</span><span class="sxs-lookup"><span data-stu-id="eec65-121">Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible.</span></span> <span data-ttu-id="eec65-122">Připojení `?` znak, který má kvantifikátor umožňuje opožděné; způsobí, že modul regulárních výrazů tak, aby odpovídaly počet výskytů míře.</span><span class="sxs-lookup"><span data-stu-id="eec65-122">Appending the `?` character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.</span></span> <span data-ttu-id="eec65-123">Úplný popis rozdíl mezi typu greedy a opožděné kvantifikátory, najdete v části [Hladové a líné kvantifikátory](#Greedy) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="eec65-123">For a complete description of the difference between greedy and lazy quantifiers, see the section [Greedy and Lazy Quantifiers](#Greedy) later in this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eec65-124">Kvantifikátory vnoření (například jako regulární výraz `(a*)*` nemá) můžete zvýšit počet porovnání, které modul regulárních výrazů se musí provádět jako exponenciální funkce se počet znaků ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="eec65-124">Nesting quantifiers (for example, as the regular expression pattern `(a*)*` does) can increase the number of comparisons that the regular expression engine must perform, as an exponential function of the number of characters in the input string.</span></span> <span data-ttu-id="eec65-125">Další informace o toto chování a jeho řešení najdete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eec65-125">For more information about this behavior and its workarounds, see [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).</span></span>  
  
## <a name="regular-expression-quantifiers"></a><span data-ttu-id="eec65-126">Kvantifikátory v regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="eec65-126">Regular Expression Quantifiers</span></span>  
 <span data-ttu-id="eec65-127">Následující části uvádějí kvantifikátory podporované regulární výrazy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="eec65-127">The following sections list the quantifiers supported by .NET regular expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eec65-128">Pokud \*, +,?, {, a} vyskytují v vzor regulárního výrazu znaky, modul regulárních výrazů je interpretuje jako kvantifikátory nebo část konstrukce kvantifikátoru jsou součástí [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eec65-128">If the \*, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a [character class](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="eec65-129">Interpretovat jako literály mimo třídu znaků, musíte použít řídící tak, že před jejich zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="eec65-129">To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash.</span></span> <span data-ttu-id="eec65-130">Například řetězec `\*` v regulárním výrazu vzor interpretována jako literál hvězdičky ("\*") znaků.</span><span class="sxs-lookup"><span data-stu-id="eec65-130">For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk ("\*") character.</span></span>  
  
### <a name="match-zero-or-more-times-"></a><span data-ttu-id="eec65-131">Odpovídat nula nebo vícekrát: \*</span><span class="sxs-lookup"><span data-stu-id="eec65-131">Match Zero or More Times: \*</span></span>  
 <span data-ttu-id="eec65-132">`*` Kvantifikátoru porovnává předchozí prvek nula či více krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-132">The `*` quantifier matches the preceding element zero or more times.</span></span> <span data-ttu-id="eec65-133">Ta je ekvivalentní `{0,}` kvantifikátoru.</span><span class="sxs-lookup"><span data-stu-id="eec65-133">It is equivalent to the `{0,}` quantifier.</span></span> <span data-ttu-id="eec65-134">`*` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `*?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-134">`*` is a greedy quantifier whose lazy equivalent is `*?`.</span></span>  
  
 <span data-ttu-id="eec65-135">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-135">The following example illustrates this regular expression.</span></span> <span data-ttu-id="eec65-136">Devět číslic ve vstupním řetězci, pět odpovídají vzoru a čtyřmi (`95`, `929`, `9129`, a `9919`) nepodporují.</span><span class="sxs-lookup"><span data-stu-id="eec65-136">Of the nine digits in the input string, five match the pattern and four (`95`, `929`, `9129`, and `9919`) do not.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 <span data-ttu-id="eec65-137">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-137">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-138">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-138">Pattern</span></span>|<span data-ttu-id="eec65-139">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-139">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-140">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-140">Start at a word boundary.</span></span>|  
|`91*`|<span data-ttu-id="eec65-141">Porovná "9" následované nula nebo více znaky "1".</span><span class="sxs-lookup"><span data-stu-id="eec65-141">Match a "9" followed by zero or more "1" characters.</span></span>|  
|`9*`|<span data-ttu-id="eec65-142">Odpovídat počtu nula či více znaků "9".</span><span class="sxs-lookup"><span data-stu-id="eec65-142">Match zero or more "9" characters.</span></span>|  
|`\b`|<span data-ttu-id="eec65-143">Skončí na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-143">End at a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-"></a><span data-ttu-id="eec65-144">Odpovídat jeden či více krát: +</span><span class="sxs-lookup"><span data-stu-id="eec65-144">Match One or More Times: +</span></span>  
 <span data-ttu-id="eec65-145">`+` Kvantifikátoru porovnává předchozí prvek jeden či více krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-145">The `+` quantifier matches the preceding element one or more times.</span></span> <span data-ttu-id="eec65-146">Ta je ekvivalentní `{1,}`.</span><span class="sxs-lookup"><span data-stu-id="eec65-146">It is equivalent to `{1,}`.</span></span> <span data-ttu-id="eec65-147">`+` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `+?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-147">`+` is a greedy quantifier whose lazy equivalent is `+?`.</span></span>  
  
 <span data-ttu-id="eec65-148">Například regulární výraz `\ban+\w*?\b` pokusí Hledat celá slova začínající písmenem `a` následuje jeden nebo více instancí písmeno `n`.</span><span class="sxs-lookup"><span data-stu-id="eec65-148">For example, the regular expression `\ban+\w*?\b` tries to match entire words that begin with the letter `a` followed by one or more instances of the letter `n`.</span></span> <span data-ttu-id="eec65-149">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-149">The following example illustrates this regular expression.</span></span> <span data-ttu-id="eec65-150">Odpovídá regulárnímu výrazu slova `an`, `annual`, `announcement`, a `antique`a správně selže tak, aby odpovídaly `autumn` a `all`.</span><span class="sxs-lookup"><span data-stu-id="eec65-150">The regular expression matches the words `an`, `annual`, `announcement`, and `antique`, and correctly fails to match `autumn` and `all`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 <span data-ttu-id="eec65-151">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-151">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-152">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-152">Pattern</span></span>|<span data-ttu-id="eec65-153">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-153">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-154">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-154">Start at a word boundary.</span></span>|  
|`an+`|<span data-ttu-id="eec65-155">Porovná znak "a" následuje jeden nebo více znaky "n".</span><span class="sxs-lookup"><span data-stu-id="eec65-155">Match an "a" followed by one or more "n" characters.</span></span>|  
|`\w*?`|<span data-ttu-id="eec65-156">Porovná znak slova nula nebo více vícekrát, ale co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-156">Match a word character zero or more times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="eec65-157">Skončí na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-157">End at a word boundary.</span></span>|  
  
### <a name="match-zero-or-one-time-"></a><span data-ttu-id="eec65-158">Odpovídat nula nebo jednou:?</span><span class="sxs-lookup"><span data-stu-id="eec65-158">Match Zero or One Time: ?</span></span>  
 <span data-ttu-id="eec65-159">`?` Kvantifikátoru odpovídá předchozí prvek nula nebo jedna jednou.</span><span class="sxs-lookup"><span data-stu-id="eec65-159">The `?` quantifier matches the preceding element zero or one time.</span></span> <span data-ttu-id="eec65-160">Ta je ekvivalentní `{0,1}`.</span><span class="sxs-lookup"><span data-stu-id="eec65-160">It is equivalent to `{0,1}`.</span></span> <span data-ttu-id="eec65-161">`?` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `??`.</span><span class="sxs-lookup"><span data-stu-id="eec65-161">`?` is a greedy quantifier whose lazy equivalent is `??`.</span></span>  
  
 <span data-ttu-id="eec65-162">Například regulární výraz `\ban?\b` pokusí Hledat celá slova začínající písmenem `a` následuje žádnou nebo jednu instanci písmeno `n`.</span><span class="sxs-lookup"><span data-stu-id="eec65-162">For example, the regular expression `\ban?\b` tries to match entire words that begin with the letter `a` followed by zero or one instances of the letter `n`.</span></span> <span data-ttu-id="eec65-163">Jinými slovy, pokusí se vyhledat slova `a` a `an`.</span><span class="sxs-lookup"><span data-stu-id="eec65-163">In other words, it tries to match the words `a` and `an`.</span></span> <span data-ttu-id="eec65-164">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-164">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 <span data-ttu-id="eec65-165">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-165">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-166">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-166">Pattern</span></span>|<span data-ttu-id="eec65-167">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-167">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-168">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-168">Start at a word boundary.</span></span>|  
|`an?`|<span data-ttu-id="eec65-169">Porovná znak "a" následuje nula nebo jeden znak "n".</span><span class="sxs-lookup"><span data-stu-id="eec65-169">Match an "a" followed by zero or one "n" character.</span></span>|  
|`\b`|<span data-ttu-id="eec65-170">Skončí na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-170">End at a word boundary.</span></span>|  
  
### <a name="match-exactly-n-times-n"></a><span data-ttu-id="eec65-171">Odpovídat přesně n krát: {n}</span><span class="sxs-lookup"><span data-stu-id="eec65-171">Match Exactly n Times: {n}</span></span>  
 <span data-ttu-id="eec65-172">`{`  *n*  `}` Kvantifikátoru přesně odpovídá předchozí prvek  *n*  krát, kde  *n* je libovolné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="eec65-172">The `{`*n*`}` quantifier matches the preceding element exactly *n* times, where *n* is any integer.</span></span> <span data-ttu-id="eec65-173">`{`*n*`}` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `}?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-173">`{`*n*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="eec65-174">Například regulární výraz `\b\d+\,\d{3}\b` pokusí porovnat hranici slova, za nímž následuje jeden nebo více desetinných číslic, za nímž následuje tři desetinných číslic, za nímž následuje hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-174">For example, the regular expression `\b\d+\,\d{3}\b` tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary.</span></span> <span data-ttu-id="eec65-175">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-175">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 <span data-ttu-id="eec65-176">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-176">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-177">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-177">Pattern</span></span>|<span data-ttu-id="eec65-178">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-178">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-179">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-179">Start at a word boundary.</span></span>|  
|`\d+`|<span data-ttu-id="eec65-180">Porovná jednu nebo více desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="eec65-180">Match one or more decimal digits.</span></span>|  
|`\,`|<span data-ttu-id="eec65-181">Porovná znak čárky.</span><span class="sxs-lookup"><span data-stu-id="eec65-181">Match a comma character.</span></span>|  
|`\d{3}`|<span data-ttu-id="eec65-182">Porovná tři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="eec65-182">Match three decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="eec65-183">Skončí na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-183">End at a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-n"></a><span data-ttu-id="eec65-184">Odpovídají alespoň n krát: {n,}</span><span class="sxs-lookup"><span data-stu-id="eec65-184">Match at Least n Times: {n,}</span></span>  
 <span data-ttu-id="eec65-185">`{`  *n*  `,}` Kvantifikátoru porovnává předchozí prvek alespoň  *n*  krát, kde  *n* je libovolné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="eec65-185">The `{`*n*`,}` quantifier matches the preceding element at least *n* times, where *n* is any integer.</span></span> <span data-ttu-id="eec65-186">`{`*n*`,}` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `}?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-186">`{`*n*`,}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="eec65-187">Například regulární výraz `\b\d{2,}\b\D+` pokusí porovnat hranici slova a alespoň dvě číslice následovaný hranici slova a nečíselným znakem.</span><span class="sxs-lookup"><span data-stu-id="eec65-187">For example, the regular expression `\b\d{2,}\b\D+` tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character.</span></span> <span data-ttu-id="eec65-188">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-188">The following example illustrates this regular expression.</span></span> <span data-ttu-id="eec65-189">Regulární výraz selže tak, aby odpovídaly fráze `"7 days"` vzhledem k tomu, že obsahuje pouze jednu číslici desítkové soustavy, ale úspěšně porovná větu `"10 weeks and 300 years"`.</span><span class="sxs-lookup"><span data-stu-id="eec65-189">The regular expression fails to match the phrase `"7 days"` because it contains just one decimal digit, but it successfully matches the phrases `"10 weeks and 300 years"`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 <span data-ttu-id="eec65-190">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-190">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-191">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-191">Pattern</span></span>|<span data-ttu-id="eec65-192">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-192">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-193">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-193">Start at a word boundary.</span></span>|  
|`\d{2,}`|<span data-ttu-id="eec65-194">Odpovídat aspoň dva desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="eec65-194">Match at least two decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="eec65-195">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-195">Match a word boundary.</span></span>|  
|`\D+`|<span data-ttu-id="eec65-196">Odpovídat nejméně jednu číslici desetinné číslo.</span><span class="sxs-lookup"><span data-stu-id="eec65-196">Match at least one non-decimal digit.</span></span>|  
  
### <a name="match-between-n-and-m-times-nm"></a><span data-ttu-id="eec65-197">Nalezena shoda mezi časy n a m: {n, m}</span><span class="sxs-lookup"><span data-stu-id="eec65-197">Match Between n and m Times: {n,m}</span></span>  
 <span data-ttu-id="eec65-198">`{`  *n*  `,` *m* `}` kvantifikátoru porovnává předchozí prvek alespoň  *n*  dobu, ale ne víc než *m* krát, kde  *n*  a *m* jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="eec65-198">The `{`*n*`,`*m*`}` quantifier matches the preceding element at least *n* times, but no more than *m* times, where *n* and *m* are integers.</span></span> <span data-ttu-id="eec65-199">`{`*n*`,`*m* `}` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `,` *m*`}?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-199">`{`*n*`,`*m*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`,`*m*`}?`.</span></span>  
  
 <span data-ttu-id="eec65-200">V následujícím příkladu, regulární výraz `(00\s){2,4}` pokusí porovnat mezi dvěma a čtyřmi výskyty dvou číslic nula následované mezerou.</span><span class="sxs-lookup"><span data-stu-id="eec65-200">In the following example, the regular expression `(00\s){2,4}` tries to match between two and four occurrences of two zero digits followed by a space.</span></span> <span data-ttu-id="eec65-201">Všimněte si, že závěrečná část vstupní řetězec obsahuje tento vzor pětkrát spíše než maximální počet čtyři.</span><span class="sxs-lookup"><span data-stu-id="eec65-201">Note that the final portion of the input string includes this pattern five times rather than the maximum of four.</span></span> <span data-ttu-id="eec65-202">Ale pouze počáteční část tohoto podřetězce (až prostor a pátý pár nul) odpovídá regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-202">However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a><span data-ttu-id="eec65-203">Odpovídat nula nebo více krát (opožděné porovnávání): \*?</span><span class="sxs-lookup"><span data-stu-id="eec65-203">Match Zero or More Times (Lazy Match): \*?</span></span>  
 <span data-ttu-id="eec65-204">`*?` Kvantifikátoru porovnává předchozí prvek nula nebo více vícekrát, ale co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-204">The `*?` quantifier matches the preceding element zero or more times, but as few times as possible.</span></span> <span data-ttu-id="eec65-205">Je opožděné protějškem typu greedy kvantifikátoru `*`.</span><span class="sxs-lookup"><span data-stu-id="eec65-205">It is the lazy counterpart of the greedy quantifier `*`.</span></span>  
  
 <span data-ttu-id="eec65-206">V následujícím příkladu, regulární výraz `\b\w*?oo\w*?\b` odpovídá slova, která obsahují řetězec `oo`.</span><span class="sxs-lookup"><span data-stu-id="eec65-206">In the following example, the regular expression `\b\w*?oo\w*?\b` matches all words that contain the string `oo`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 <span data-ttu-id="eec65-207">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-207">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-208">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-208">Pattern</span></span>|<span data-ttu-id="eec65-209">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-209">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-210">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-210">Start at a word boundary.</span></span>|  
|`\w*?`|<span data-ttu-id="eec65-211">Porovná nula nebo více znaků slova, ale jako několika prvních znaků nejdříve.</span><span class="sxs-lookup"><span data-stu-id="eec65-211">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`oo`|<span data-ttu-id="eec65-212">Shoda s řetězcem "ú".</span><span class="sxs-lookup"><span data-stu-id="eec65-212">Match the string "oo".</span></span>|  
|`\w*?`|<span data-ttu-id="eec65-213">Porovná nula nebo více znaků slova, ale jako několika prvních znaků nejdříve.</span><span class="sxs-lookup"><span data-stu-id="eec65-213">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`\b`|<span data-ttu-id="eec65-214">Končí na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-214">End on a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-lazy-match-"></a><span data-ttu-id="eec65-215">Shodovat s jednou nebo vícekrát (opožděné porovnávání): +?</span><span class="sxs-lookup"><span data-stu-id="eec65-215">Match One or More Times (Lazy Match): +?</span></span>  
 <span data-ttu-id="eec65-216">`+?` Kvantifikátoru porovnává předchozí prvek jeden nebo více vícekrát, ale co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-216">The `+?` quantifier matches the preceding element one or more times, but as few times as possible.</span></span> <span data-ttu-id="eec65-217">Je opožděné protějškem typu greedy kvantifikátoru `+`.</span><span class="sxs-lookup"><span data-stu-id="eec65-217">It is the lazy counterpart of the greedy quantifier `+`.</span></span>  
  
 <span data-ttu-id="eec65-218">Například regulární výraz `\b\w+?\b` odpovídá jeden nebo více znaků, které jsou odděleny hranice aplikace word.</span><span class="sxs-lookup"><span data-stu-id="eec65-218">For example, the regular expression `\b\w+?\b` matches one or more characters separated by word boundaries.</span></span> <span data-ttu-id="eec65-219">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-219">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a><span data-ttu-id="eec65-220">Odpovídat nula nebo jednou (opožděné porovnávání):??</span><span class="sxs-lookup"><span data-stu-id="eec65-220">Match Zero or One Time (Lazy Match): ??</span></span>  
 <span data-ttu-id="eec65-221">`??` Kvantifikátoru odpovídá předchozí prvek nula nebo jedna jednou, ale nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-221">The `??` quantifier matches the preceding element zero or one time, but as few times as possible.</span></span> <span data-ttu-id="eec65-222">Je opožděné protějškem typu greedy kvantifikátoru `?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-222">It is the lazy counterpart of the greedy quantifier `?`.</span></span>  
  
 <span data-ttu-id="eec65-223">Například regulární výraz `^\s*(System.)??Console.Write(Line)??\(??` se pokusí o porovnání řetězce "Console.Write" nebo "Console.WriteLine".</span><span class="sxs-lookup"><span data-stu-id="eec65-223">For example, the regular expression `^\s*(System.)??Console.Write(Line)??\(??` attempts to match the strings "Console.Write" or "Console.WriteLine".</span></span> <span data-ttu-id="eec65-224">Řetězec může také obsahovat "Systém".</span><span class="sxs-lookup"><span data-stu-id="eec65-224">The string can also include "System."</span></span> <span data-ttu-id="eec65-225">před "Konzole" ale může následovat levé závorky.</span><span class="sxs-lookup"><span data-stu-id="eec65-225">before "Console", and it can be followed by an opening parenthesis.</span></span> <span data-ttu-id="eec65-226">Řetězec musí být na začátku řádku, i když můžete předcházet mezer.</span><span class="sxs-lookup"><span data-stu-id="eec65-226">The string must be at the beginning of a line, although it can be preceded by white space.</span></span> <span data-ttu-id="eec65-227">Následující příklad ilustruje tento regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="eec65-227">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 <span data-ttu-id="eec65-228">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-228">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-229">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-229">Pattern</span></span>|<span data-ttu-id="eec65-230">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-230">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="eec65-231">Odpovídat začátek vstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="eec65-231">Match the start of the input stream.</span></span>|  
|`\s*`|<span data-ttu-id="eec65-232">Porovná žádný nebo více prázdných znaků.</span><span class="sxs-lookup"><span data-stu-id="eec65-232">Match zero or more white-space characters.</span></span>|  
|`(System.)??`|<span data-ttu-id="eec65-233">Porovná nula nebo jeden výskyt řetězec "Systém.".</span><span class="sxs-lookup"><span data-stu-id="eec65-233">Match zero or one occurrence of the string "System.".</span></span>|  
|`Console.Write`|<span data-ttu-id="eec65-234">Hledat řetězec "Console.Write".</span><span class="sxs-lookup"><span data-stu-id="eec65-234">Match the string "Console.Write".</span></span>|  
|`(Line)??`|<span data-ttu-id="eec65-235">Porovná nula nebo jeden výskyt řetězec "Řádek".</span><span class="sxs-lookup"><span data-stu-id="eec65-235">Match zero or one occurrence of the string "Line".</span></span>|  
|`\(??`|<span data-ttu-id="eec65-236">Porovná nula nebo jeden výskyt levé závorky.</span><span class="sxs-lookup"><span data-stu-id="eec65-236">Match zero or one occurrence of the opening parenthesis.</span></span>|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a><span data-ttu-id="eec65-237">Odpovídat přesně n krát (opožděné porovnávání): {n}?</span><span class="sxs-lookup"><span data-stu-id="eec65-237">Match Exactly n Times (Lazy Match): {n}?</span></span>  
 <span data-ttu-id="eec65-238">`{`  *n*  `}?` Kvantifikátoru přesně odpovídá předchozí prvek `n` krát, kde  *n*  je libovolné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="eec65-238">The `{`*n*`}?` quantifier matches the preceding element exactly `n` times, where *n* is any integer.</span></span> <span data-ttu-id="eec65-239">Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `}+`.</span><span class="sxs-lookup"><span data-stu-id="eec65-239">It is the lazy counterpart of the greedy quantifier `{`*n*`}+`.</span></span>  
  
 <span data-ttu-id="eec65-240">V následujícím příkladu, regulární výraz `\b(\w{3,}?\.){2}?\w{3,}?\b` slouží k identifikaci adresu webu.</span><span class="sxs-lookup"><span data-stu-id="eec65-240">In the following example, the regular expression `\b(\w{3,}?\.){2}?\w{3,}?\b` is used to identify a Web site address.</span></span> <span data-ttu-id="eec65-241">Všimněte si, že odpovídá "www.microsoft.com" a "msdn.microsoft.com", ale neodpovídá "mywebsite" nebo "mycompany.com".</span><span class="sxs-lookup"><span data-stu-id="eec65-241">Note that it matches "www.microsoft.com" and "msdn.microsoft.com", but does not match "mywebsite" or "mycompany.com".</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 <span data-ttu-id="eec65-242">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-242">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-243">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-243">Pattern</span></span>|<span data-ttu-id="eec65-244">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-244">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-245">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-245">Start at a word boundary.</span></span>|  
|`(\w{3,}?\.)`|<span data-ttu-id="eec65-246">Porovná alespoň 3 znaky word, ale jako několika prvních znaků nejdříve, za nímž následuje tečky nebo tečka – znak.</span><span class="sxs-lookup"><span data-stu-id="eec65-246">Match at least 3 word characters, but as few characters as possible, followed by a dot or period character.</span></span> <span data-ttu-id="eec65-247">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="eec65-247">This is the first capturing group.</span></span>|  
|`(\w{3,}?\.){2}?`|<span data-ttu-id="eec65-248">Shodují se vzorem v první skupinu dvakrát, ale co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-248">Match the pattern in the first group two times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="eec65-249">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-249">End the match on a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a><span data-ttu-id="eec65-250">Odpovídají alespoň n krát (opožděné porovnávání): {n,}?</span><span class="sxs-lookup"><span data-stu-id="eec65-250">Match at Least n Times (Lazy Match): {n,}?</span></span>  
 <span data-ttu-id="eec65-251">`{`  *n*  `,}?` Kvantifikátoru porovnává předchozí prvek alespoň `n` krát, kde  *n*  je jakékoli číslo typu integer, ale co nejméně krát možné.</span><span class="sxs-lookup"><span data-stu-id="eec65-251">The `{`*n*`,}?` quantifier matches the preceding element at least `n` times, where *n* is any integer, but as few times as possible.</span></span> <span data-ttu-id="eec65-252">Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `,}`.</span><span class="sxs-lookup"><span data-stu-id="eec65-252">It is the lazy counterpart of the greedy quantifier `{`*n*`,}`.</span></span>  
  
 <span data-ttu-id="eec65-253">Podívejte se příklad `{`  *n*  `}?` kvantifikátoru v předchozí části Obrázek.</span><span class="sxs-lookup"><span data-stu-id="eec65-253">See the example for the `{`*n*`}?` quantifier in the previous section for an illustration.</span></span> <span data-ttu-id="eec65-254">Regulární výraz v tomto příkladu používá `{`  *n*  `,}` kvantifikátoru tak, aby odpovídaly řetězec, který obsahuje alespoň tři znaky následované období.</span><span class="sxs-lookup"><span data-stu-id="eec65-254">The regular expression in that example uses the `{`*n*`,}` quantifier to match a string that has at least three characters followed by a period.</span></span>  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a><span data-ttu-id="eec65-255">Nalezena shoda mezi n až m krát (opožděné porovnávání): {n, m}?</span><span class="sxs-lookup"><span data-stu-id="eec65-255">Match Between n and m Times (Lazy Match): {n,m}?</span></span>  
 <span data-ttu-id="eec65-256">`{`  *n*  `,` *m* `}?` kvantifikátoru porovnává předchozí prvek mezi `n` a `m` krát, kde  *n*  a *m* jsou celá čísla, ale nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-256">The `{`*n*`,`*m*`}?` quantifier matches the preceding element between `n` and `m` times, where *n* and *m* are integers, but as few times as possible.</span></span> <span data-ttu-id="eec65-257">Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `,` *m*`}`.</span><span class="sxs-lookup"><span data-stu-id="eec65-257">It is the lazy counterpart of the greedy quantifier `{`*n*`,`*m*`}`.</span></span>  
  
 <span data-ttu-id="eec65-258">V následujícím příkladu, regulární výraz `\b[A-Z](\w*\s+){1,10}?[.!?]` odpovídá věty obsahující mezi slovy. jeden a 10.</span><span class="sxs-lookup"><span data-stu-id="eec65-258">In the following example, the regular expression `\b[A-Z](\w*\s+){1,10}?[.!?]` matches sentences that contain between one and ten words.</span></span> <span data-ttu-id="eec65-259">Odpovídá všechny věty ve vstupním řetězci s výjimkou jeden věty obsahující slova 18.</span><span class="sxs-lookup"><span data-stu-id="eec65-259">It matches all the sentences in the input string except for one sentence that contains 18 words.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 <span data-ttu-id="eec65-260">Regulární výraz je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-260">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-261">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-261">Pattern</span></span>|<span data-ttu-id="eec65-262">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-262">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eec65-263">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="eec65-263">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="eec65-264">Odpovídat velké písmeno od A do Z.</span><span class="sxs-lookup"><span data-stu-id="eec65-264">Match an uppercase character from A to Z.</span></span>|  
|`(\w*\s+)`|<span data-ttu-id="eec65-265">Odpovídat nula nebo více znaků slova, za nímž následuje jeden nebo více prázdných znaků.</span><span class="sxs-lookup"><span data-stu-id="eec65-265">Match zero or more word characters, followed by one or more white-space characters.</span></span> <span data-ttu-id="eec65-266">Toto je první skupinu zachycení.</span><span class="sxs-lookup"><span data-stu-id="eec65-266">This is the first capture group.</span></span>|  
|`{1,10}?`|<span data-ttu-id="eec65-267">Shodovat s použitím předchozího vzoru názvů mezi 1 a 10, ale co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-267">Match the previous pattern between 1 and 10 times, but as few times as possible.</span></span>|  
|`[.!?]`|<span data-ttu-id="eec65-268">Porovná kterýkoli z interpunkční znaky ".","!", nebo "?".</span><span class="sxs-lookup"><span data-stu-id="eec65-268">Match any one of the punctuation characters ".", "!", or "?".</span></span>|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a><span data-ttu-id="eec65-269">Typu greedy a opožděné kvantifikátory</span><span class="sxs-lookup"><span data-stu-id="eec65-269">Greedy and Lazy Quantifiers</span></span>  
 <span data-ttu-id="eec65-270">Počet kvantifikátory má dvě verze:</span><span class="sxs-lookup"><span data-stu-id="eec65-270">A number of the quantifiers have two versions:</span></span>  
  
-   <span data-ttu-id="eec65-271">Typu greedy verze.</span><span class="sxs-lookup"><span data-stu-id="eec65-271">A greedy version.</span></span>  
  
     <span data-ttu-id="eec65-272">Typu greedy kvantifikátor se pokusí porovnat prvek tolikrát, kolikrát je možné.</span><span class="sxs-lookup"><span data-stu-id="eec65-272">A greedy quantifier tries to match an element as many times as possible.</span></span>  
  
-   <span data-ttu-id="eec65-273">Verze typu non-greedy (nebo opožděné).</span><span class="sxs-lookup"><span data-stu-id="eec65-273">A non-greedy (or lazy) version.</span></span>  
  
     <span data-ttu-id="eec65-274">Typu non-greedy kvantifikátor se pokusí porovnat prvek co nejméně krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-274">A non-greedy quantifier tries to match an element as few times as possible.</span></span> <span data-ttu-id="eec65-275">Chcete-li typu greedy kvantifikátoru na opožděné kvantifikátory jednoduše přidáním `?`.</span><span class="sxs-lookup"><span data-stu-id="eec65-275">You can turn a greedy quantifier into a lazy quantifier by simply adding a `?`.</span></span>  
  
 <span data-ttu-id="eec65-276">Zvažte jednoduchý regulární výraz, který slouží k extrakci poslední čtyři číslice v řetězci čísel například číslo platební karty.</span><span class="sxs-lookup"><span data-stu-id="eec65-276">Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number.</span></span> <span data-ttu-id="eec65-277">Verze regulární výraz, který používá `*` je typu greedy kvantifikátoru `\b.*([0-9]{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="eec65-277">The version of the regular expression that uses the `*` greedy quantifier is `\b.*([0-9]{4})\b`.</span></span> <span data-ttu-id="eec65-278">Ale pokud řetězec obsahuje dvě čísla, tento regulární výraz odpovídá poslední čtyři číslice druhé číslo, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="eec65-278">However, if a string contains two numbers, this regular expression matches the last four digits of the second number only, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 <span data-ttu-id="eec65-279">Regulární výraz selže tak, aby odpovídaly první číslo, protože `*` kvantifikátoru se pokusí vyhledat předchozí element podle možný celý řetězec několikrát, a tak najde shodu na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="eec65-279">The regular expression fails to match the first number because the `*` quantifier tries to match the previous element as many times as possible in the entire string, and so it finds its match at the end of the string.</span></span>  
  
 <span data-ttu-id="eec65-280">Toto není toto chování žádoucí.</span><span class="sxs-lookup"><span data-stu-id="eec65-280">This is not the desired behavior.</span></span> <span data-ttu-id="eec65-281">Místo toho můžete použít `*?`opožděné kvantifikátoru extrahovat číslic z obou čísel, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="eec65-281">Instead, you can use the `*?`lazy quantifier to extract digits from both numbers, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 <span data-ttu-id="eec65-282">Ve většině případů regulárních výrazů s typu greedy a opožděné kvantifikátory vracejí stejné shody.</span><span class="sxs-lookup"><span data-stu-id="eec65-282">In most cases, regular expressions with greedy and lazy quantifiers return the same matches.</span></span> <span data-ttu-id="eec65-283">Při použití se zástupným znakem nejčastěji vracejí odlišné výsledky (`.`) metaznak, který odpovídá jakémukoliv znaku.</span><span class="sxs-lookup"><span data-stu-id="eec65-283">They most commonly return different results when they are used with the wildcard (`.`) metacharacter, which matches any character.</span></span>  
  
## <a name="quantifiers-and-empty-matches"></a><span data-ttu-id="eec65-284">Kvantifikátory a prázdné shody</span><span class="sxs-lookup"><span data-stu-id="eec65-284">Quantifiers and Empty Matches</span></span>  
 <span data-ttu-id="eec65-285">Kvantifikátory `*`, `+`, a `{`  *n*  `,` *m* `}` a jejich opožděné protějšky nikdy opakovat po prázdná případy, kdy byl nalezen minimální počet zachycení.</span><span class="sxs-lookup"><span data-stu-id="eec65-285">The quantifiers `*`, `+`, and `{`*n*`,`*m*`}` and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found.</span></span> <span data-ttu-id="eec65-286">Toto pravidlo zabrání kvantifikátory zadat nekonečné smyčky odpovídá dílčím výrazu prázdný po neomezenou maximální počet možných skupiny zachycení nebo téměř nekonečné.</span><span class="sxs-lookup"><span data-stu-id="eec65-286">This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.</span></span>  
  
 <span data-ttu-id="eec65-287">Například následující kód ukazuje výsledek volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metoda s regulární výraz `(a?)*`, který odpovídá žádnou nebo jednu "a" znak nula či více krát.</span><span class="sxs-lookup"><span data-stu-id="eec65-287">For example, the following code shows the result of a call to the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> method with the regular expression pattern `(a?)*`, which matches zero or one "a" character zero or more times.</span></span> <span data-ttu-id="eec65-288">Všimněte si, že jediné zachytávající skupiny zachytí každou "a" jako a taky <xref:System.String.Empty?displayProperty=nameWithType>, ta však není nalezena žádná druhá prázdný shoda, protože na první shodu prázdný způsobí, že kvantifikátor zastaví opakování.</span><span class="sxs-lookup"><span data-stu-id="eec65-288">Note that the single capturing group captures each "a" as well as <xref:System.String.Empty?displayProperty=nameWithType>, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 <span data-ttu-id="eec65-289">Pokud chcete zobrazit praktické rozdíl mezi zaznamenávání skupina, která určuje minimální a maximální počet zachycení a ten, který definuje pevný počet zachycení, zvažte vzorce regulárního výrazu `(a\1|(?(1)\1)){0,2}` a `(a\1|(?(1)\1)){2}`.</span><span class="sxs-lookup"><span data-stu-id="eec65-289">To see the practical difference between a capturing group that defines a minimum and a maximum number of captures and one that defines a fixed number of captures, consider the regular expression patterns `(a\1|(?(1)\1)){0,2}` and `(a\1|(?(1)\1)){2}`.</span></span> <span data-ttu-id="eec65-290">Obě regulární výrazy se skládá z jedné zachycené skupiny, která je definována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eec65-290">Both regular expressions consist of a single capturing group, which is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="eec65-291">Vzor</span><span class="sxs-lookup"><span data-stu-id="eec65-291">Pattern</span></span>|<span data-ttu-id="eec65-292">Popis</span><span class="sxs-lookup"><span data-stu-id="eec65-292">Description</span></span>|  
|-------------|-----------------|  
|`(a\1`|<span data-ttu-id="eec65-293">Buď shodu "a", spolu s hodnotou první zaznamenané skupiny...</span><span class="sxs-lookup"><span data-stu-id="eec65-293">Either match "a" along with the value of the first captured group …</span></span>|  
|<code>&#124;(?(1)</code>|<span data-ttu-id="eec65-294">…</span><span class="sxs-lookup"><span data-stu-id="eec65-294">…</span></span> <span data-ttu-id="eec65-295">nebo můžete otestovat, zda byla definována první zaznamenané skupinu.</span><span class="sxs-lookup"><span data-stu-id="eec65-295">or test whether the first captured group has been defined.</span></span> <span data-ttu-id="eec65-296">(Všimněte si, že `(?(1)` konstrukce nedefinuje skupinu zachycení.)</span><span class="sxs-lookup"><span data-stu-id="eec65-296">(Note that the `(?(1)` construct does not define a capturing group.)</span></span>|  
|`\1))`|<span data-ttu-id="eec65-297">Pokud první zaznamenané skupina existuje, odpovídají jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eec65-297">If the first captured group exists, match its value.</span></span> <span data-ttu-id="eec65-298">Pokud skupina neexistuje, bude shodovat s skupině <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eec65-298">If the group does not exist, the group will match <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|  
  
 <span data-ttu-id="eec65-299">První regulární výraz, který se pokusí vyhledat tento vzor mezi nula a dvě časy; druhá s názvem přesně dvakrát.</span><span class="sxs-lookup"><span data-stu-id="eec65-299">The first regular expression tries to match this pattern between zero and two times; the second, exactly two times.</span></span> <span data-ttu-id="eec65-300">Vzhledem k tomu, že první vzor dosáhne jeho minimální počet zachycení s jeho první zaznamenávání <xref:System.String.Empty?displayProperty=nameWithType>, nikdy opakuje můžete vyzkoušet tak, aby odpovídaly `a\1`; `{0,2}` kvantifikátoru umožňuje pouze prázdné shody v poslední iteraci.</span><span class="sxs-lookup"><span data-stu-id="eec65-300">Because the first pattern reaches its minimum number of captures with its first capture of <xref:System.String.Empty?displayProperty=nameWithType>, it never repeats to try to match `a\1`; the `{0,2}` quantifier allows only empty matches in the last iteration.</span></span> <span data-ttu-id="eec65-301">Naproti tomu neshoduje druhý regulární výraz "a" vzhledem k tomu, že se vyhodnotí `a\1` podruhé; minimální počet iterací, 2, vynutí se tak, aby modul opakovat po prázdné shodě.</span><span class="sxs-lookup"><span data-stu-id="eec65-301">In contrast, the second regular expression does match "a" because it evaluates `a\1` a second time; the minimum number of iterations, 2, forces the engine to repeat after an empty match.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eec65-302">Viz také</span><span class="sxs-lookup"><span data-stu-id="eec65-302">See Also</span></span>  
 [<span data-ttu-id="eec65-303">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="eec65-303">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [<span data-ttu-id="eec65-304">Zpětné navracení</span><span class="sxs-lookup"><span data-stu-id="eec65-304">Backtracking</span></span>](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
