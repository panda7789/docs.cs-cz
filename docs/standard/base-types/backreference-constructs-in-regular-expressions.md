---
title: Konstrukce zpětného odkazu v regulárních výrazech rozhraní .NET
description: Zjistěte, jak identifikovat opakované textové prvky pomocí konstrukce zpětného odkazu v regulárním výrazu.
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
ms.openlocfilehash: 905578d763ebe5d5b8eb96a9056fbe11fbfab137
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711529"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="f795d-103">Konstrukce zpětných odkazů v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="f795d-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="f795d-104">Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaný znak nebo podřetězec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f795d-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="f795d-105">Pokud například vstupní řetězec obsahuje více výskytů libovolného podřetězce, můžete porovnat první výskyt se zachytávající skupinou a potom použít zpětný odkaz tak, aby odpovídal následným výskytům podřetězce.</span><span class="sxs-lookup"><span data-stu-id="f795d-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="f795d-106">Samostatná syntaxe se používá k odkazování na pojmenované a číslované zachytávající skupiny v náhradních řetězcích.</span><span class="sxs-lookup"><span data-stu-id="f795d-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="f795d-107">Další informace naleznete v [tématu Substituce](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f795d-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="f795d-108">Rozhraní .NET definuje samostatné prvky jazyka, které odkazují na číslované a pojmenované zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="f795d-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="f795d-109">Další informace o zachycení skupin naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f795d-109">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="f795d-110">Číslované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="f795d-110">Numbered Backreferences</span></span>

<span data-ttu-id="f795d-111">Číslovaný zpětný odkaz používá následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="f795d-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="f795d-112">`\`*číslo*</span><span class="sxs-lookup"><span data-stu-id="f795d-112">`\` *number*</span></span>

<span data-ttu-id="f795d-113">kde *číslo* je řadová pozice zachytávající skupiny v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="f795d-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="f795d-114">Například `\4` odpovídá obsahu čtvrté zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="f795d-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="f795d-115">Pokud *není ve* vzoru regulárního výrazu definována chyba analýzy a modul <xref:System.ArgumentException>regulárních výrazů vyvolá .</span><span class="sxs-lookup"><span data-stu-id="f795d-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="f795d-116">Například regulární `\b(\w+)\s\1` výraz je `(\w+)` platný, protože je první a jediná zachytávající skupina ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="f795d-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="f795d-117">Na druhé straně `\b(\w+)\s\2` je neplatný a vyvolá výjimku argumentu, protože `\2`neexistuje žádná zachytávající skupina očíslovaná .</span><span class="sxs-lookup"><span data-stu-id="f795d-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="f795d-118">Kromě toho pokud *číslo* identifikuje zachytávající skupinu v určité řadové pozici, ale této zachytávající skupině byl přiřazen číselný název odlišný <xref:System.ArgumentException>od své ordinální pozice, analyzátor regulárních výrazů také vyvolá .</span><span class="sxs-lookup"><span data-stu-id="f795d-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="f795d-119">Všimněte si nejednoznačnosti mezi osmičkovými řídicími kódy (například) `\16`a `\`zpětných odkazů *čísel,* které používají stejný zápis.</span><span class="sxs-lookup"><span data-stu-id="f795d-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="f795d-120">Tato nejednoznačnost je vyřešena takto:</span><span class="sxs-lookup"><span data-stu-id="f795d-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="f795d-121">Výrazy `\1` prostřednictvím `\9` jsou vždy interpretovány jako zpětné odkazy a nikoli jako osmičkové kódy.</span><span class="sxs-lookup"><span data-stu-id="f795d-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="f795d-122">Pokud je první číslice vícemístného výrazu `\80` 8 `\91`nebo 9 (například nebo ), výraz interpretován jako literál.</span><span class="sxs-lookup"><span data-stu-id="f795d-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="f795d-123">Výrazy `\10` od a větší jsou považovány za zpětné odkazy, pokud existuje zpětný odkaz odpovídající tomuto číslu; v opačném případě jsou interpretovány jako osmičkové kódy.</span><span class="sxs-lookup"><span data-stu-id="f795d-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="f795d-124">Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě <xref:System.ArgumentException>analýzy a modul regulárních výrazů vyvolá .</span><span class="sxs-lookup"><span data-stu-id="f795d-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="f795d-125">Pokud je problém nejednoznačnosti, můžete `\k<`použít *název* `>` zápisu, který je jednoznačný a nemůže být zaměňován s osmičkovými znakovými kódy.</span><span class="sxs-lookup"><span data-stu-id="f795d-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="f795d-126">Podobně šestnáctkové kódy, jako `\xdd` jsou jednoznačné a nelze je zaměnit se zpětnými odkazy.</span><span class="sxs-lookup"><span data-stu-id="f795d-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="f795d-127">Následující příklad najde v řetězci zdvojené znaky slova.</span><span class="sxs-lookup"><span data-stu-id="f795d-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="f795d-128">Definuje regulární výraz `(\w)\1`, který se skládá z následujících prvků.</span><span class="sxs-lookup"><span data-stu-id="f795d-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="f795d-129">Element</span><span class="sxs-lookup"><span data-stu-id="f795d-129">Element</span></span>|<span data-ttu-id="f795d-130">Popis</span><span class="sxs-lookup"><span data-stu-id="f795d-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="f795d-131">Porovnejte znak slova a přiřaďte jej první zachytávající skupině.</span><span class="sxs-lookup"><span data-stu-id="f795d-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="f795d-132">Porovná další znak, který je stejný jako hodnota první zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="f795d-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="f795d-133">Pojmenované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="f795d-133">Named Backreferences</span></span>

<span data-ttu-id="f795d-134">Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="f795d-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="f795d-135">`\k<`*název*`>`</span><span class="sxs-lookup"><span data-stu-id="f795d-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="f795d-136">nebo:</span><span class="sxs-lookup"><span data-stu-id="f795d-136">or:</span></span>

<span data-ttu-id="f795d-137">`\k'`*název*`'`</span><span class="sxs-lookup"><span data-stu-id="f795d-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="f795d-138">kde *název* je název zachytávající skupiny definovaný ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="f795d-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="f795d-139">Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě <xref:System.ArgumentException>analýzy a modul regulárních výrazů vyvolá .</span><span class="sxs-lookup"><span data-stu-id="f795d-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="f795d-140">Následující příklad najde v řetězci zdvojené znaky slova.</span><span class="sxs-lookup"><span data-stu-id="f795d-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="f795d-141">Definuje regulární výraz `(?<char>\w)\k<char>`, který se skládá z následujících prvků.</span><span class="sxs-lookup"><span data-stu-id="f795d-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="f795d-142">Element</span><span class="sxs-lookup"><span data-stu-id="f795d-142">Element</span></span>|<span data-ttu-id="f795d-143">Popis</span><span class="sxs-lookup"><span data-stu-id="f795d-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="f795d-144">Porovnejte znak slova a přiřaďte jej zachytávající skupině s názvem `char`.</span><span class="sxs-lookup"><span data-stu-id="f795d-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="f795d-145">Porovná další znak, který je stejný `char` jako hodnota zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="f795d-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="f795d-146">Pojmenované číselné zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="f795d-146">Named numeric backreferences</span></span>

<span data-ttu-id="f795d-147">V pojmenované zpětném `\k`odkazu s může být *název* také řetězcovou reprezentací čísla.</span><span class="sxs-lookup"><span data-stu-id="f795d-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="f795d-148">Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k nalezení zdvojené znaky slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f795d-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="f795d-149">V tomto případě příklad definuje zachytávající skupinu, která je explicitně pojmenována "2" a zpětný odkaz je odpovídajícím způsobem pojmenován "2".</span><span class="sxs-lookup"><span data-stu-id="f795d-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="f795d-150">Pokud je *název* řetězcovou reprezentací čísla a žádná `\k<`zachytávající skupina nemá tento název, *název* `>` je stejný jako číslo zpětného `\` *odkazu*, kde *číslo* je řadová pozice zachycení.</span><span class="sxs-lookup"><span data-stu-id="f795d-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="f795d-151">V následujícím příkladu je jedna zachytávající skupina s názvem `char`.</span><span class="sxs-lookup"><span data-stu-id="f795d-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="f795d-152">Konstrukce zpětného odkazu odkazuje `\k<1>`na něj jako .</span><span class="sxs-lookup"><span data-stu-id="f795d-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="f795d-153">Jak ukazuje výstup z příkladu, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> volání úspěšné, protože `char` je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="f795d-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="f795d-154">Pokud je však *název* řetězcovou reprezentací čísla a zachytávající skupině na této pozici byl explicitně přiřazen číselný název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle své ordinální pozice.</span><span class="sxs-lookup"><span data-stu-id="f795d-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="f795d-155">Místo toho hodí <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="f795d-155">Instead, it throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="f795d-156">Jediná zachytávající skupina v následujícím příkladu se nazývá "2".</span><span class="sxs-lookup"><span data-stu-id="f795d-156">The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="f795d-157">Vzhledem `\k` k tomu, že konstrukce se používá k definování zpětného odkazu s názvem "1", analyzátor regulárních výrazů není schopen identifikovat první zachytávající skupinu a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f795d-157">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="f795d-158">Co zpětné odkazy shoda</span><span class="sxs-lookup"><span data-stu-id="f795d-158">What Backreferences Match</span></span>

<span data-ttu-id="f795d-159">Zpětný odkaz odkazuje na nejnovější definici skupiny (definice nejvíce bezprostředně vlevo, při porovnávání zleva doprava).</span><span class="sxs-lookup"><span data-stu-id="f795d-159">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="f795d-160">Když skupina provede více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.</span><span class="sxs-lookup"><span data-stu-id="f795d-160">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="f795d-161">Následující příklad obsahuje vzor regulárního výrazu , `(?<1>a)(?<1>\1b)*`který předefinuje skupinu \1 s názvem.</span><span class="sxs-lookup"><span data-stu-id="f795d-161">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="f795d-162">Následující tabulka popisuje každý vzorek v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="f795d-162">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="f795d-163">Vzor</span><span class="sxs-lookup"><span data-stu-id="f795d-163">Pattern</span></span>|<span data-ttu-id="f795d-164">Popis</span><span class="sxs-lookup"><span data-stu-id="f795d-164">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="f795d-165">Porovná znak "a" a přiřadí výsledek zachytávající skupině s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="f795d-165">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="f795d-166">Porovná nula nebo více výskytů skupiny s názvem `1` spolu s "b" `1`a přiřadí výsledek zachytávající skupině s názvem .</span><span class="sxs-lookup"><span data-stu-id="f795d-166">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="f795d-167">Při porovnávání regulárního výrazu se vstupním řetězcem ("aababb") provádí modul regulárních výrazů následující operace:</span><span class="sxs-lookup"><span data-stu-id="f795d-167">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="f795d-168">Začíná na začátku řetězce a úspěšně odpovídá "a" `(?<1>a)`s výrazem .</span><span class="sxs-lookup"><span data-stu-id="f795d-168">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="f795d-169">Hodnota skupiny `1` je nyní "a".</span><span class="sxs-lookup"><span data-stu-id="f795d-169">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="f795d-170">Přejde na druhý znak a úspěšně odpovídá řetězci "ab" s výrazem `\1b`, nebo "ab".</span><span class="sxs-lookup"><span data-stu-id="f795d-170">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="f795d-171">Potom přiřadí výsledek, "ab" `\1`na .</span><span class="sxs-lookup"><span data-stu-id="f795d-171">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="f795d-172">Posouvá se na čtvrtou postavu.</span><span class="sxs-lookup"><span data-stu-id="f795d-172">It advances to the fourth character.</span></span> <span data-ttu-id="f795d-173">Výraz `(?<1>\1b)*` má odpovídat nula nebo vícekrát, takže úspěšně odpovídá řetězci "abb" s výrazem `\1b`.</span><span class="sxs-lookup"><span data-stu-id="f795d-173">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="f795d-174">Přiřadí výsledek, "abb", zpět `\1`na .</span><span class="sxs-lookup"><span data-stu-id="f795d-174">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="f795d-175">V tomto `*` příkladu je opakování kvantifikátoru -- je vyhodnocován opakovaně, dokud modul regulárních výrazů nemůže odpovídat vzoru, který definuje.</span><span class="sxs-lookup"><span data-stu-id="f795d-175">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="f795d-176">Opakování kvantifikátorů nevymaže definice skupin.</span><span class="sxs-lookup"><span data-stu-id="f795d-176">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="f795d-177">Pokud skupina nezachytila žádné podřetězce, zpětný odkaz na tuto skupinu není definován a nikdy se neshoduje.</span><span class="sxs-lookup"><span data-stu-id="f795d-177">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="f795d-178">To je znázorněno vzorem `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`regulárního výrazu , který je definován následovně:</span><span class="sxs-lookup"><span data-stu-id="f795d-178">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="f795d-179">Vzor</span><span class="sxs-lookup"><span data-stu-id="f795d-179">Pattern</span></span>|<span data-ttu-id="f795d-180">Popis</span><span class="sxs-lookup"><span data-stu-id="f795d-180">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="f795d-181">Začněte shodu na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="f795d-181">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="f795d-182">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f795d-182">Match two uppercase letters.</span></span> <span data-ttu-id="f795d-183">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="f795d-183">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="f795d-184">Porovná nulový nebo jeden výskyt dvou desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="f795d-184">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="f795d-185">Toto je druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="f795d-185">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="f795d-186">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f795d-186">Match two uppercase letters.</span></span> <span data-ttu-id="f795d-187">Toto je třetí zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="f795d-187">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="f795d-188">Ukončite shodu na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="f795d-188">End the match on a word boundary.</span></span>|

<span data-ttu-id="f795d-189">Vstupní řetězec může odpovídat tomuto regulárnímu výrazu i v případě, že dvě desetinné číslice, které jsou definovány druhou zachytávající skupinou, nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f795d-189">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="f795d-190">Následující příklad ukazuje, že i když je shoda úspěšná, je mezi dvěma úspěšnými zachytávajícími skupinami nalezena prázdná zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="f795d-190">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="f795d-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="f795d-191">See also</span></span>

- [<span data-ttu-id="f795d-192">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="f795d-192">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
