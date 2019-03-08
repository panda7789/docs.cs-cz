---
title: Konstrukce zpětných odkazů v regulárních výrazech .NET
description: Zjistěte, jak identifikovat opakované textové prvky pomocí konstrukce zpětných odkazů v regulárním výrazu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: d478ae9e1db86718236da73917d772820707ea03
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678355"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="2d076-103">Konstrukce zpětných odkazů v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="2d076-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="2d076-104">Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaných nebo podřetězec v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="2d076-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="2d076-105">Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčí řetězec, můžete porovnat první výskyt zachytávající skupinou a pak použijte zpětný odkaz tak, aby odpovídaly další výskyty tohoto dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="2d076-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="2d076-106">Samostatná syntaxe se používá k odkazování na pojmenované a číslované zachytávající skupiny v řetězci pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="2d076-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="2d076-107">Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2d076-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="2d076-108">.NET definuje samostatné jazykové prvky k odkazování na číslem a pojmenovaných zachytávajících skupinách.</span><span class="sxs-lookup"><span data-stu-id="2d076-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="2d076-109">Další informace o zachycující skupiny, najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2d076-109">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="2d076-110">Číslované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="2d076-110">Numbered Backreferences</span></span>

<span data-ttu-id="2d076-111">Zpětný odkaz číselného používá následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="2d076-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="2d076-112">`\` *Číslo*</span><span class="sxs-lookup"><span data-stu-id="2d076-112">`\` *number*</span></span>

<span data-ttu-id="2d076-113">kde *číslo* je pořadové umístění zachytávající skupinu v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="2d076-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="2d076-114">Například `\4` odpovídá obsahu čtvrtý zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="2d076-115">Pokud *číslo* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2d076-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="2d076-116">Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` je první a jediný zachytávající skupinu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2d076-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="2d076-117">Na druhé straně `\b(\w+)\s\2` není platný a vyvolá výjimku argument, protože neexistuje žádná zachytávající skupina číslované `\2`.</span><span class="sxs-lookup"><span data-stu-id="2d076-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="2d076-118">Kromě toho pokud *číslo* identifikuje zachytávající skupinu v konkrétní pořadí, ale, že zachycující skupina má přiřazenou číselnou název jiné než její pořadové umístění, takévyvoláanalyzátorregulárníchvýrazů<xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2d076-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="2d076-119">Poznámka: byla zjištěna dvojznačnost mezi osmičkovými řídícími kódy (například `\16`) a `\` *číslo* zpětných odkazech, který se používá stejná notace.</span><span class="sxs-lookup"><span data-stu-id="2d076-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="2d076-120">Tuto nejednoznačnost vyřešen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2d076-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="2d076-121">Výrazy `\1` prostřednictvím `\9` vždy interpretováno jako zpětné odkazy a ne jako osmičkové kódy.</span><span class="sxs-lookup"><span data-stu-id="2d076-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="2d076-122">Pokud první číslice vícečíslicového výrazu je 8 a 9 (například `\80` nebo `\91`), výraz, protože je interpretován jako literální.</span><span class="sxs-lookup"><span data-stu-id="2d076-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="2d076-123">Výrazy z `\10` a vyšší jsou považovány za zpětné odkazy, pokud je zpětný odkaz odpovídá na to číslo, jinak, jsou interpretovány jako osmičková kódy.</span><span class="sxs-lookup"><span data-stu-id="2d076-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="2d076-124">Obsahuje-li regulární výraz zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy, a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2d076-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="2d076-125">Pokud nejednoznačnost je nějaký problém, můžete použít `\k<` *název* `>` zápisu, která je jednoznačný a nesmí být zaměněny s osmičkovými kódy.</span><span class="sxs-lookup"><span data-stu-id="2d076-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="2d076-126">Podobně šestnáctkové kódy, jako `\xdd` jsou jednoznačný a nesmí být zaměňovány zpětné odkazy.</span><span class="sxs-lookup"><span data-stu-id="2d076-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="2d076-127">Následující příklad najde zdvojené znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2d076-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="2d076-128">Definuje regulární výraz `(\w)\1`, který se skládá z následujících elementů.</span><span class="sxs-lookup"><span data-stu-id="2d076-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="2d076-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d076-129">Element</span></span>|<span data-ttu-id="2d076-130">Popis</span><span class="sxs-lookup"><span data-stu-id="2d076-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="2d076-131">Odpovídá znaku slova a přiřaďte ho k první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="2d076-132">Porovná další znak, který je stejná jako hodnota první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="2d076-133">Pojmenované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="2d076-133">Named Backreferences</span></span>

<span data-ttu-id="2d076-134">Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="2d076-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="2d076-135">`\k<` *Jméno* `>`</span><span class="sxs-lookup"><span data-stu-id="2d076-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="2d076-136">nebo:</span><span class="sxs-lookup"><span data-stu-id="2d076-136">or:</span></span>

<span data-ttu-id="2d076-137">`\k'` *Jméno* `'`</span><span class="sxs-lookup"><span data-stu-id="2d076-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="2d076-138">kde *název* je název zachytávající skupinu definovanou ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="2d076-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="2d076-139">Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2d076-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="2d076-140">Následující příklad najde zdvojené znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2d076-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="2d076-141">Definuje regulární výraz `(?<char>\w)\k<char>`, který se skládá z následujících elementů.</span><span class="sxs-lookup"><span data-stu-id="2d076-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="2d076-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d076-142">Element</span></span>|<span data-ttu-id="2d076-143">Popis</span><span class="sxs-lookup"><span data-stu-id="2d076-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="2d076-144">Odpovídá znaku slova a přiřaďte ho ke zachytávající skupina s názvem `char`.</span><span class="sxs-lookup"><span data-stu-id="2d076-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="2d076-145">Další znak, který je stejná jako hodnota odpovídat `char` zachytávající skupinu.</span><span class="sxs-lookup"><span data-stu-id="2d076-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="2d076-146">Pojmenované číselné zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="2d076-146">Named numeric backreferences</span></span>

<span data-ttu-id="2d076-147">V pojmenovaný zpětný odkaz s `\k`, *název* může také být řetězcové vyjádření čísla.</span><span class="sxs-lookup"><span data-stu-id="2d076-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="2d076-148">Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` najít zdvojené znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2d076-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="2d076-149">V tomto případě v příkladu je definována zachytávající skupinu, která je explicitně s názvem "2" a zpětný odkaz je odpovídajícím způsobem s názvem "2".</span><span class="sxs-lookup"><span data-stu-id="2d076-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="2d076-150">Pokud *název* je řetězcové vyjádření čísla a žádná zachytávající skupina nemá název, `\k<` *název* `>` je stejné jako zpětný odkaz `\`  *číslo*, kde *číslo* je pořadové číslo pozice v zachytávání.</span><span class="sxs-lookup"><span data-stu-id="2d076-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="2d076-151">V následujícím příkladu je jeden zachytávající skupina s názvem `char`.</span><span class="sxs-lookup"><span data-stu-id="2d076-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="2d076-152">Konstrukce zpětných odkazů odkazuje na jako `\k<1>`.</span><span class="sxs-lookup"><span data-stu-id="2d076-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="2d076-153">Jak výstup z příkladu, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> proběhne úspěšně, protože `char` je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="2d076-154">Nicméně pokud *název* je řetězcové vyjádření čísla a zachytávající skupinu ve, pozice byly explicitně přiřazeny číselné název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle její pořadové umístění .</span><span class="sxs-lookup"><span data-stu-id="2d076-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="2d076-155">Místo toho se vyvolá <xref:System.ArgumentException>. Pouze zachytávající skupina v následujícím příkladu má název "2".</span><span class="sxs-lookup"><span data-stu-id="2d076-155">Instead, it throws an <xref:System.ArgumentException>.The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="2d076-156">Vzhledem k tomu, `\k` konstruktor se používá k definování zpětný odkaz s názvem "1", analyzátor regulárních výrazů se nepodařilo zjistit první zachytávající skupina a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="2d076-156">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="2d076-157">Co porovnávají</span><span class="sxs-lookup"><span data-stu-id="2d076-157">What Backreferences Match</span></span>

<span data-ttu-id="2d076-158">Zpětný odkaz odkazuje na poslední definici skupiny (definice bezprostředně nalevo, při porovnávání zleva doprava).</span><span class="sxs-lookup"><span data-stu-id="2d076-158">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="2d076-159">Pokud skupina provádí více zachycení, zpětný odkaz odkazuje na nejnovější snímek.</span><span class="sxs-lookup"><span data-stu-id="2d076-159">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="2d076-160">Následující příklad obsahuje vzor regulárního výrazu, `(?<1>a)(?<1>\1b)*`, které předefinuje \1 pojmenované skupiny.</span><span class="sxs-lookup"><span data-stu-id="2d076-160">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="2d076-161">Následující tabulka popisuje každý vzorek regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="2d076-161">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="2d076-162">Vzor</span><span class="sxs-lookup"><span data-stu-id="2d076-162">Pattern</span></span>|<span data-ttu-id="2d076-163">Popis</span><span class="sxs-lookup"><span data-stu-id="2d076-163">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="2d076-164">Porovná znak "a" a přiřadit výsledek, který má zachytávající skupina s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="2d076-164">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="2d076-165">Porovná žádný nebo několik výskytů skupina s názvem `1` spolu s "b" a přiřadit výsledek, který má zachytávající skupina s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="2d076-165">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="2d076-166">V porovnávání regulárních výrazů se vstupním řetězcem ("aababb"), modul regulárních výrazů provádí následující operace:</span><span class="sxs-lookup"><span data-stu-id="2d076-166">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="2d076-167">Začne na začátku řetězce a úspěšně odpovídá "a" s výrazem `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="2d076-167">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="2d076-168">Hodnota `1` skupina je nyní "a".</span><span class="sxs-lookup"><span data-stu-id="2d076-168">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="2d076-169">Přejde na druhém znaku a úspěšně shoduje s řetězcem "ab" s výrazem `\1b`, nebo "ab".</span><span class="sxs-lookup"><span data-stu-id="2d076-169">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="2d076-170">Poté přiřadí výsledek, "ab" k `\1`.</span><span class="sxs-lookup"><span data-stu-id="2d076-170">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="2d076-171">Přejde na čtvrté znak.</span><span class="sxs-lookup"><span data-stu-id="2d076-171">It advances to the fourth character.</span></span> <span data-ttu-id="2d076-172">Výraz `(?<1>\1b)*` je porovnán nula nebo vícekrát, takže úspěšně odpovídá řetězci "abb" s výrazem `\1b`.</span><span class="sxs-lookup"><span data-stu-id="2d076-172">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="2d076-173">Přiřadí výsledek "abb", zpět do `\1`.</span><span class="sxs-lookup"><span data-stu-id="2d076-173">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="2d076-174">V tomto příkladu `*` je kvantifikátor opakování je vyhodnocen jako opakovaně dokud modul regulárních výrazů neodpovídá vzoru definuje.</span><span class="sxs-lookup"><span data-stu-id="2d076-174">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="2d076-175">Kvantifikátory opakování nerušte zaškrtnutí políčka definice skupiny.</span><span class="sxs-lookup"><span data-stu-id="2d076-175">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="2d076-176">Pokud skupinu nezachytila žádný podřetězec, zpětný odkaz na tuto skupinu není definováno a nikdy odpovídá.</span><span class="sxs-lookup"><span data-stu-id="2d076-176">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="2d076-177">To je znázorněn ve vzoru regulárního výrazu `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, která je definovaná následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2d076-177">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="2d076-178">Vzor</span><span class="sxs-lookup"><span data-stu-id="2d076-178">Pattern</span></span>|<span data-ttu-id="2d076-179">Popis</span><span class="sxs-lookup"><span data-stu-id="2d076-179">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="2d076-180">Začne porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2d076-180">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="2d076-181">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2d076-181">Match two uppercase letters.</span></span> <span data-ttu-id="2d076-182">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-182">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="2d076-183">Porovná žádný nebo jeden výskyt dvě desetinné číslice.</span><span class="sxs-lookup"><span data-stu-id="2d076-183">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="2d076-184">Toto je druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-184">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="2d076-185">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2d076-185">Match two uppercase letters.</span></span> <span data-ttu-id="2d076-186">Toto je třetí zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-186">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="2d076-187">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2d076-187">End the match on a word boundary.</span></span>|

<span data-ttu-id="2d076-188">Vstupní řetězec může odpovídat tomuto regulárnímu výrazu i v případě, že nejsou k dispozici dvě desetinné číslice, které jsou definovány tak druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="2d076-188">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="2d076-189">Následující příklad ukazuje, že i když tato shoda je úspěšná, prázdnou zachytávající skupinou nachází mezi dvěma úspěšné zachytávajících skupinách.</span><span class="sxs-lookup"><span data-stu-id="2d076-189">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="2d076-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d076-190">See also</span></span>

- [<span data-ttu-id="2d076-191">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="2d076-191">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
