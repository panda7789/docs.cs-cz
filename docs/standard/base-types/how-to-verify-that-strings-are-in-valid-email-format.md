---
title: Ověření platnosti e-mailového formátu řetězců
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: c02fc215fa66951ae3333175191ab96a226a2afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73197579"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="b9527-102">Ověření platnosti e-mailového formátu řetězců</span><span class="sxs-lookup"><span data-stu-id="b9527-102">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="b9527-103">Následující příklad používá regulární výraz k ověření, zda je řetězec v platném formátu e-mailu.</span><span class="sxs-lookup"><span data-stu-id="b9527-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

## <a name="example"></a><span data-ttu-id="b9527-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9527-104">Example</span></span>

<span data-ttu-id="b9527-105">Příklad definuje metodu, `IsValidEmail` která `true` vrátí, pokud řetězec obsahuje `false` platnou e-mailovou adresu a pokud ne, ale neprovede žádnou jinou akci.</span><span class="sxs-lookup"><span data-stu-id="b9527-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>

<span data-ttu-id="b9527-106">Chcete-li ověřit, zda je `IsValidEmail` e-mailová adresa platná, metoda volá metodu <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> se vzorem regulárního `(@)(.+)$` výrazu, která odděluje název domény od e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="b9527-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="b9527-107">Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegát, který představuje metodu, která zpracovává a nahrazuje odpovídající text.</span><span class="sxs-lookup"><span data-stu-id="b9527-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="b9527-108">Vzor regulárního výrazu je interpretován následovně.</span><span class="sxs-lookup"><span data-stu-id="b9527-108">The regular expression pattern is interpreted as follows.</span></span>

|<span data-ttu-id="b9527-109">Vzor</span><span class="sxs-lookup"><span data-stu-id="b9527-109">Pattern</span></span>|<span data-ttu-id="b9527-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b9527-110">Description</span></span>|
|-------------|-----------------|
|`(@)`|<span data-ttu-id="b9527-111">Porovná znak @.</span><span class="sxs-lookup"><span data-stu-id="b9527-111">Match the @ character.</span></span> <span data-ttu-id="b9527-112">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="b9527-112">This is the first capturing group.</span></span>|
|`(.+)`|<span data-ttu-id="b9527-113">Porovná jeden nebo více výskytů libovolného znaku.</span><span class="sxs-lookup"><span data-stu-id="b9527-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="b9527-114">Toto je druhá zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="b9527-114">This is the second capturing group.</span></span>|
|`$`|<span data-ttu-id="b9527-115">Ukončite shodu na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="b9527-115">End the match at the end of the string.</span></span>|

<span data-ttu-id="b9527-116">Název domény spolu se znakem @ `DomainMapper` je předán <xref:System.Globalization.IdnMapping> metodě, která používá třídu k překladu znaků Unicode, které jsou mimo rozsah znaků US-ASCII do Punycode.</span><span class="sxs-lookup"><span data-stu-id="b9527-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="b9527-117">Metoda také nastaví `invalid` `True` příznak, <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> pokud metoda zjistí všechny neplatné znaky v názvu domény.</span><span class="sxs-lookup"><span data-stu-id="b9527-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="b9527-118">Metoda vrátí název domény Punycode, kterému předchází symbol @ metodě. `IsValidEmail`</span><span class="sxs-lookup"><span data-stu-id="b9527-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

<span data-ttu-id="b9527-119">Metoda `IsValidEmail` pak volá <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k ověření, že adresa odpovídá vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="b9527-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="b9527-120">Všimněte `IsValidEmail` si, že metoda neprovádí ověřování k ověření e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="b9527-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="b9527-121">Pouze určuje, zda je jeho formát platný pro e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="b9527-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="b9527-122">Kromě toho `IsValidEmail` metoda neověřuje, zda je název domény nejvyšší úrovně platným názvem domény uvedeným v [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), což by vyžadovalo operaci vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="b9527-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="b9527-123">Místo toho regulární výraz pouze ověří, že název domény nejvyšší úrovně se skládá ze dvou až dvaceti čtyř znaků ASCII, přičemž alfanumerické první a poslední znaky a zbývající znaky jsou alfanumerické nebo pomlčka (-).</span><span class="sxs-lookup"><span data-stu-id="b9527-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

<span data-ttu-id="b9527-124">V tomto příkladu je ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` vzor regulárního výrazu interpretován tak, jak je znázorněno v následující legendě.</span><span class="sxs-lookup"><span data-stu-id="b9527-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following legend.</span></span> <span data-ttu-id="b9527-125">Regulární výraz je <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> kompilován pomocí příznaku.</span><span class="sxs-lookup"><span data-stu-id="b9527-125">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

<span data-ttu-id="b9527-126">Vzor `^`: Začněte shodu na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="b9527-126">Pattern `^`: Begin the match at the start of the string.</span></span>

<span data-ttu-id="b9527-127">Vzorek `(?(")`: Určete, zda je prvním znakem uvozovka.</span><span class="sxs-lookup"><span data-stu-id="b9527-127">Pattern `(?(")`: Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="b9527-128">`(?(")`je začátek konstrukce alternace.</span><span class="sxs-lookup"><span data-stu-id="b9527-128">`(?(")` is the beginning of an alternation construct.</span></span>

<span data-ttu-id="b9527-129">Pole `(?(")(".+?(?<!\\)"@)`: Pokud je prvním znakem uvozovka, porovnejte počáteční uvozovku následovanou alespoň jedním výskytem libovolného znaku následovaným koncovou uvozovkou.</span><span class="sxs-lookup"><span data-stu-id="b9527-129">Pattern `(?(")(".+?(?<!\\)"@)`: If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="b9527-130">Koncové uvozovky nesmí předcházet znak zpětného\\lomítka ( ).</span><span class="sxs-lookup"><span data-stu-id="b9527-130">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="b9527-131">`(?<!`je začátek kontrolního výrazu negativního zpětného vyhledávání s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="b9527-131">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="b9527-132">Řetězec by měl být zakončen znakem at (@).</span><span class="sxs-lookup"><span data-stu-id="b9527-132">The string should conclude with an at sign (@).</span></span>

<span data-ttu-id="b9527-133">Vzorek `|(([0-9a-z]`: Pokud první znak není uvozovka, porovná libovolný abecední znak od a do z nebo A do Z (porovnání je malá a velká písmena) nebo libovolný číselný znak od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="b9527-133">Pattern `|(([0-9a-z]`: If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>

<span data-ttu-id="b9527-134">Vzor `(\.(?!\.))`: Pokud je dalším znakem tečka, porovnejte ji.</span><span class="sxs-lookup"><span data-stu-id="b9527-134">Pattern `(\.(?!\.))`: If the next character is a period, match it.</span></span> <span data-ttu-id="b9527-135">Pokud se nejedná o tečku, podívejte se dopředu na další znak a pokračujte v zápase.</span><span class="sxs-lookup"><span data-stu-id="b9527-135">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="b9527-136">`(?!\.)`je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který zabraňuje zobrazení dvou po sobě jdoucích období v místní části e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="b9527-136">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>

<span data-ttu-id="b9527-137">Vzorek ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: Pokud další znak není tečka, porovná libovolný znak slova nebo jeden z\*následujících znaků: -!#$%&' +/=?^\`{}|~</span><span class="sxs-lookup"><span data-stu-id="b9527-137">Pattern ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: If the next character is not a period, match any word character or one of the following characters: -!#$%&'\*+/=?^\`{}|~</span></span>

<span data-ttu-id="b9527-138">Vzorek ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Porovná vzor střídání (tečka následovaná netečkou nebo jedním z mnoha znaků) nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="b9527-138">Pattern ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>

<span data-ttu-id="b9527-139">Vzor `@`: Shoda znaku @.</span><span class="sxs-lookup"><span data-stu-id="b9527-139">Pattern `@`: Match the @ character.</span></span>

<span data-ttu-id="b9527-140">Vzorek `(?<=[0-9a-z])`: Pokračovat v shodě, pokud znak, který předchází znak @ je A až Z, až z nebo 0 až 9.</span><span class="sxs-lookup"><span data-stu-id="b9527-140">Pattern `(?<=[0-9a-z])`: Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="b9527-141">Tento vzor definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="b9527-141">This pattern defines a zero-width positive lookbehind assertion.</span></span>

<span data-ttu-id="b9527-142">Vzor `(?(\[)`: Zkontrolujte, zda znak, který následuje @ je otevírací závorka.</span><span class="sxs-lookup"><span data-stu-id="b9527-142">Pattern `(?(\[)`: Check whether the character that follows @ is an opening bracket.</span></span>

<span data-ttu-id="b9527-143">Vzor `(\[(\d{1,3}\.){3}\d{1,3}\])`: Pokud se jedná o otevírací závorku, porovnejte otevírací závorku následovanou IP adresou (čtyři sady po jedné až třech číslicích, přičemž každá sada je oddělena tečkou) a uzavírací závorkou.</span><span class="sxs-lookup"><span data-stu-id="b9527-143">Pattern `(\[(\d{1,3}\.){3}\d{1,3}\])`: If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>

<span data-ttu-id="b9527-144">Vzorek `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: Pokud znak@ není počáteční závorkou, porovnejte jeden alfanumerický znak s hodnotou A-Z, a-z nebo 0-9, následovaný nulou nebo více výskyty spojovníku, následovanýnulým nebo jedním alfanumerickým znakem s hodnotou A-Z, a-z nebo 0-9, následovanýtečkou.</span><span class="sxs-lookup"><span data-stu-id="b9527-144">Pattern `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="b9527-145">Tento vzor lze opakovat jednou nebo vícekrát a musí následovat název domény nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="b9527-145">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>

<span data-ttu-id="b9527-146">Vzor `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: Název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, A-Z a 0-9).</span><span class="sxs-lookup"><span data-stu-id="b9527-146">Pattern `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="b9527-147">Může také obsahovat od nuly do 22 znaků ASCII, které jsou alfanumerické nebo spojovníky.</span><span class="sxs-lookup"><span data-stu-id="b9527-147">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>

<span data-ttu-id="b9527-148">Vzorek `$`: Ukončení shody na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="b9527-148">Pattern `$`: End the match at the end of the string.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="b9527-149">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b9527-149">Compile the code</span></span>

<span data-ttu-id="b9527-150">Metody `IsValidEmail` `DomainMapper` a mohou být zahrnuty do knihovny metod nástroje regulárních výrazů nebo mohou být zahrnuty jako soukromé statické metody nebo metody instance do třídy aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9527-150">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>

<span data-ttu-id="b9527-151">Metodu můžete <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> také zahrnout do knihovny regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="b9527-151">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>

<span data-ttu-id="b9527-152">Pokud jsou používány v knihovně regulárních výrazů, můžete je volat pomocí kódu, například následujícího:</span><span class="sxs-lookup"><span data-stu-id="b9527-152">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a><span data-ttu-id="b9527-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9527-153">See also</span></span>

- [<span data-ttu-id="b9527-154">.NET Framework – regulární výrazy</span><span class="sxs-lookup"><span data-stu-id="b9527-154">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
