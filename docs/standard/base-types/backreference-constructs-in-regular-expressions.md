---
title: "Konstrukce zpětných odkazů v regulárních výrazech"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ec92933bdf123412a3d489fc493d76c4a0dc0d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="00d8b-102">Konstrukce zpětných odkazů v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="00d8b-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="00d8b-103">Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaných znaku nebo podřetězce v řetězci.</span><span class="sxs-lookup"><span data-stu-id="00d8b-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="00d8b-104">Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčího řetězce, můžete porovnat první výskyt se skupinou zaznamenávání a pak použít zpětný odkaz pro porovnání dalších výskytů dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="00d8b-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00d8b-105">Samostatná syntaxe slouží k odkazování na pojmenované a číslované zachytávající skupiny v náhradní řetězce.</span><span class="sxs-lookup"><span data-stu-id="00d8b-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="00d8b-106">Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="00d8b-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="00d8b-107">Rozhraní .NET definuje samostatné jazykové elementy označují číslem a pojmenované zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="00d8b-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="00d8b-108">Další informace o zaznamenání skupin najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="00d8b-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="00d8b-109">Číslované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="00d8b-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="00d8b-110">Číslovaný zpětný odkaz používá následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="00d8b-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="00d8b-111">`\`*číslo*</span><span class="sxs-lookup"><span data-stu-id="00d8b-111">`\` *number*</span></span>  
  
 <span data-ttu-id="00d8b-112">kde *číslo* je pořadové číslo pozice zachytávající skupiny v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="00d8b-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="00d8b-113">Například `\4` odpovídá obsah čtvrtý zachycující skupiny.</span><span class="sxs-lookup"><span data-stu-id="00d8b-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="00d8b-114">Pokud *číslo* není definovaná v regulární výraz, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="00d8b-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="00d8b-115">Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` je první a pouze zaznamenávání skupiny ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="00d8b-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="00d8b-116">Na druhé straně `\b(\w+)\s\2` je neplatný a vyvolá výjimku argument, protože neexistuje žádná zachytávající skupina s číslem `\2`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="00d8b-117">Všimněte si nejednoznačnosti mezi osmičková řídicí kódy (například `\16`) a `\` *číslo* používajících stejnou zápis.</span><span class="sxs-lookup"><span data-stu-id="00d8b-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="00d8b-118">Tato nejednoznačnost je přeložit takto:</span><span class="sxs-lookup"><span data-stu-id="00d8b-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="00d8b-119">Výrazy `\1` prostřednictvím `\9` jsou vždy interpretovány jako zpětné odkazy a ne jako osmičková kódy.</span><span class="sxs-lookup"><span data-stu-id="00d8b-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="00d8b-120">Pokud je první číslice vícečíslicového výrazu 8 nebo 9 (například `\80` nebo `\91`), jak interpretovat jako literál výrazu.</span><span class="sxs-lookup"><span data-stu-id="00d8b-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="00d8b-121">Výrazy z `\10` a větší jsou považovány za zpětné odkazy, pokud je zpětný odkaz odpovídající, na který číslo; jinak hodnota, se interpretují jako osmičkové kódy.</span><span class="sxs-lookup"><span data-stu-id="00d8b-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="00d8b-122">Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="00d8b-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="00d8b-123">Pokud je nejednoznačnost problém, můžete použít `\k<` *název* `>` zápis, což je jednoznačné a nelze zaměňovat s kódy osmičková znaků.</span><span class="sxs-lookup"><span data-stu-id="00d8b-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="00d8b-124">Podobně, jako například šestnáctková kódy `\xdd` jsou jednoznačné a nelze zaměňovat s zpětné odkazy.</span><span class="sxs-lookup"><span data-stu-id="00d8b-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="00d8b-125">Následující příklad vyhledá zdvojené znaky slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="00d8b-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="00d8b-126">Definuje regulární výraz, `(\w)\1`, která zahrnuje následující prvky.</span><span class="sxs-lookup"><span data-stu-id="00d8b-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="00d8b-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="00d8b-127">Element</span></span>|<span data-ttu-id="00d8b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8b-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="00d8b-129">Porovná znak slova a přiřaďte ho ke skupině první zaznamenávání.</span><span class="sxs-lookup"><span data-stu-id="00d8b-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="00d8b-130">Porovná další znak, který je stejná jako hodnota první zachycující skupiny.</span><span class="sxs-lookup"><span data-stu-id="00d8b-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="00d8b-131">Pojmenované zpětné odkazy</span><span class="sxs-lookup"><span data-stu-id="00d8b-131">Named Backreferences</span></span>  
 <span data-ttu-id="00d8b-132">Pojmenované zpětných odkazů se definuje pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="00d8b-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="00d8b-133">`\k<`*název*`>`</span><span class="sxs-lookup"><span data-stu-id="00d8b-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="00d8b-134">nebo:</span><span class="sxs-lookup"><span data-stu-id="00d8b-134">or:</span></span>  
  
 <span data-ttu-id="00d8b-135">`\k'`*název*`'`</span><span class="sxs-lookup"><span data-stu-id="00d8b-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="00d8b-136">kde *název* je název zachytávající skupiny definované v regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="00d8b-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="00d8b-137">Pokud *název* není definovaná v regulární výraz, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="00d8b-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="00d8b-138">Následující příklad vyhledá zdvojené znaky slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="00d8b-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="00d8b-139">Definuje regulární výraz, `(?<char>\w)\k<char>`, která zahrnuje následující prvky.</span><span class="sxs-lookup"><span data-stu-id="00d8b-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="00d8b-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="00d8b-140">Element</span></span>|<span data-ttu-id="00d8b-141">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8b-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="00d8b-142">Porovná znak slova a přiřaďte ho k zaznamenávání skupina s názvem `char`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="00d8b-143">Porovná další znak, který je stejná jako hodnota `char` zaznamenávání skupiny.</span><span class="sxs-lookup"><span data-stu-id="00d8b-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="00d8b-144">Všimněte si, že *název* může být také řetězcovou reprezentaci číslo.</span><span class="sxs-lookup"><span data-stu-id="00d8b-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="00d8b-145">Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k nalezení zdvojených znaků slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="00d8b-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="00d8b-146">Co porovnávají</span><span class="sxs-lookup"><span data-stu-id="00d8b-146">What Backreferences Match</span></span>  
 <span data-ttu-id="00d8b-147">Zpětný odkaz odkazuje na nejnovější definice skupiny (definici nejvíce okamžitě na levé straně při kontrole shody zleva doprava).</span><span class="sxs-lookup"><span data-stu-id="00d8b-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="00d8b-148">Pokud skupina provádí více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.</span><span class="sxs-lookup"><span data-stu-id="00d8b-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="00d8b-149">Následující příklad obsahuje vzor regulárního výrazu `(?<1>a)(?<1>\1b)*`, který definuje nové \1 s názvem skupiny.</span><span class="sxs-lookup"><span data-stu-id="00d8b-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="00d8b-150">Následující tabulka popisuje každý vzor v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="00d8b-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="00d8b-151">Vzor</span><span class="sxs-lookup"><span data-stu-id="00d8b-151">Pattern</span></span>|<span data-ttu-id="00d8b-152">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8b-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="00d8b-153">Porovná znak "a" a přiřadit výsledek, který má zaznamenávání skupiny s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="00d8b-154">Shoda 0 nebo 1 výskyt skupiny s názvem `1` spolu s "b" a přiřaďte výsledek zachycující skupiny s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="00d8b-155">Modul regulárních výrazů v porovnání s regulárním výrazem se vstupní řetězec ("aababb"), provede následující operace:</span><span class="sxs-lookup"><span data-stu-id="00d8b-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="00d8b-156">Začne od začátku řetězce a úspěšně odpovídá "a" názvem výraz `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="00d8b-157">Hodnota `1` skupiny je nyní "a".</span><span class="sxs-lookup"><span data-stu-id="00d8b-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="00d8b-158">Přejde na druhý znak a úspěšně shoduje s řetězcem "ab" s výraz `\1b`, nebo "ab".</span><span class="sxs-lookup"><span data-stu-id="00d8b-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="00d8b-159">Poté přiřadí výsledek, "ab" k `\1`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="00d8b-160">Přejde na čtvrtý znak.</span><span class="sxs-lookup"><span data-stu-id="00d8b-160">It advances to the fourth character.</span></span> <span data-ttu-id="00d8b-161">Výraz `(?<1>\1b)` je porovnán nula nebo vícekrát, takže úspěšně shoduje s řetězcem "abb" s výraz `\1b`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="00d8b-162">Přiřadí výsledek "abb" zpět na `\1`.</span><span class="sxs-lookup"><span data-stu-id="00d8b-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="00d8b-163">V tomto příkladu `*` je kvantifikátor opakování je vyhodnocen jako opakovaně dokud modul regulární výraz nelze shodují se vzorem definuje.</span><span class="sxs-lookup"><span data-stu-id="00d8b-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="00d8b-164">Kvantifikátory opakování nerušte zaškrtnutí definice skupin.</span><span class="sxs-lookup"><span data-stu-id="00d8b-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="00d8b-165">Pokud skupina nezachytila žádný podřetězec, zpětných odkazů na tuto skupinu není definováno a nikdy odpovídá.</span><span class="sxs-lookup"><span data-stu-id="00d8b-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="00d8b-166">Tento koncept je znázorněn podle regulární výraz `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, který je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="00d8b-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="00d8b-167">Vzor</span><span class="sxs-lookup"><span data-stu-id="00d8b-167">Pattern</span></span>|<span data-ttu-id="00d8b-168">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8b-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="00d8b-169">Začne porovnávání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="00d8b-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="00d8b-170">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="00d8b-170">Match two uppercase letters.</span></span> <span data-ttu-id="00d8b-171">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="00d8b-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="00d8b-172">Porovná nula nebo jeden výskyt dvou desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="00d8b-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="00d8b-173">Toto je druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="00d8b-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="00d8b-174">Porovná dvě velká písmena.</span><span class="sxs-lookup"><span data-stu-id="00d8b-174">Match two uppercase letters.</span></span> <span data-ttu-id="00d8b-175">Toto je třetí zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="00d8b-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="00d8b-176">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="00d8b-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="00d8b-177">Vstupní řetězec můžete tento regulárním výrazům neodpovídá, i když nejsou k dispozici dva desetinných číslic, které jsou definované za druhé zachytávající skupině.</span><span class="sxs-lookup"><span data-stu-id="00d8b-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="00d8b-178">Následující příklad ukazuje, že přestože shody je úspěšné, prázdné skupiny zaznamenávání nalézt mezi dvěma skupinami zaznamenávání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="00d8b-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="00d8b-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d8b-179">See Also</span></span>  
 [<span data-ttu-id="00d8b-180">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="00d8b-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
