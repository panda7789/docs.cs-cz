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
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Ověření platnosti e-mailového formátu řetězců

Následující příklad používá regulární výraz k ověření, zda je řetězec v platném formátu e-mailu.

## <a name="example"></a>Příklad

Příklad definuje metodu, `IsValidEmail` která `true` vrátí, pokud řetězec obsahuje `false` platnou e-mailovou adresu a pokud ne, ale neprovede žádnou jinou akci.

Chcete-li ověřit, zda je `IsValidEmail` e-mailová adresa platná, metoda volá metodu <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> se vzorem regulárního `(@)(.+)$` výrazu, která odděluje název domény od e-mailové adresy. Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegát, který představuje metodu, která zpracovává a nahrazuje odpovídající text. Vzor regulárního výrazu je interpretován následovně.

|Vzor|Popis|
|-------------|-----------------|
|`(@)`|Porovná znak @. Toto je první zachytávající skupina.|
|`(.+)`|Porovná jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|
|`$`|Ukončite shodu na konci řetězce.|

Název domény spolu se znakem @ `DomainMapper` je předán <xref:System.Globalization.IdnMapping> metodě, která používá třídu k překladu znaků Unicode, které jsou mimo rozsah znaků US-ASCII do Punycode. Metoda také nastaví `invalid` `True` příznak, <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> pokud metoda zjistí všechny neplatné znaky v názvu domény. Metoda vrátí název domény Punycode, kterému předchází symbol @ metodě. `IsValidEmail`

Metoda `IsValidEmail` pak volá <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k ověření, že adresa odpovídá vzoru regulárního výrazu.

Všimněte `IsValidEmail` si, že metoda neprovádí ověřování k ověření e-mailové adresy. Pouze určuje, zda je jeho formát platný pro e-mailovou adresu. Kromě toho `IsValidEmail` metoda neověřuje, zda je název domény nejvyšší úrovně platným názvem domény uvedeným v [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), což by vyžadovalo operaci vyhledávání. Místo toho regulární výraz pouze ověří, že název domény nejvyšší úrovně se skládá ze dvou až dvaceti čtyř znaků ASCII, přičemž alfanumerické první a poslední znaky a zbývající znaky jsou alfanumerické nebo pomlčka (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

V tomto příkladu je ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` vzor regulárního výrazu interpretován tak, jak je znázorněno v následující legendě. Regulární výraz je <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> kompilován pomocí příznaku.

Vzor `^`: Začněte shodu na začátku řetězce.

Vzorek `(?(")`: Určete, zda je prvním znakem uvozovka. `(?(")`je začátek konstrukce alternace.

Pole `(?(")(".+?(?<!\\)"@)`: Pokud je prvním znakem uvozovka, porovnejte počáteční uvozovku následovanou alespoň jedním výskytem libovolného znaku následovaným koncovou uvozovkou. Koncové uvozovky nesmí předcházet znak zpětného\\lomítka ( ). `(?<!`je začátek kontrolního výrazu negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl být zakončen znakem at (@).

Vzorek `|(([0-9a-z]`: Pokud první znak není uvozovka, porovná libovolný abecední znak od a do z nebo A do Z (porovnání je malá a velká písmena) nebo libovolný číselný znak od 0 do 9.

Vzor `(\.(?!\.))`: Pokud je dalším znakem tečka, porovnejte ji. Pokud se nejedná o tečku, podívejte se dopředu na další znak a pokračujte v zápase. `(?!\.)`je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který zabraňuje zobrazení dvou po sobě jdoucích období v místní části e-mailové adresy.

Vzorek ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: Pokud další znak není tečka, porovná libovolný znak slova nebo jeden z\*následujících znaků: -!#$%&' +/=?^\`{}|~

Vzorek ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Porovná vzor střídání (tečka následovaná netečkou nebo jedním z mnoha znaků) nula nebo vícekrát.

Vzor `@`: Shoda znaku @.

Vzorek `(?<=[0-9a-z])`: Pokračovat v shodě, pokud znak, který předchází znak @ je A až Z, až z nebo 0 až 9. Tento vzor definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.

Vzor `(?(\[)`: Zkontrolujte, zda znak, který následuje @ je otevírací závorka.

Vzor `(\[(\d{1,3}\.){3}\d{1,3}\])`: Pokud se jedná o otevírací závorku, porovnejte otevírací závorku následovanou IP adresou (čtyři sady po jedné až třech číslicích, přičemž každá sada je oddělena tečkou) a uzavírací závorkou.

Vzorek `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: Pokud znak@ není počáteční závorkou, porovnejte jeden alfanumerický znak s hodnotou A-Z, a-z nebo 0-9, následovaný nulou nebo více výskyty spojovníku, následovanýnulým nebo jedním alfanumerickým znakem s hodnotou A-Z, a-z nebo 0-9, následovanýtečkou. Tento vzor lze opakovat jednou nebo vícekrát a musí následovat název domény nejvyšší úrovně.

Vzor `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: Název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, A-Z a 0-9). Může také obsahovat od nuly do 22 znaků ASCII, které jsou alfanumerické nebo spojovníky.

Vzorek `$`: Ukončení shody na konci řetězce.

## <a name="compile-the-code"></a>Kompilace kódu

Metody `IsValidEmail` `DomainMapper` a mohou být zahrnuty do knihovny metod nástroje regulárních výrazů nebo mohou být zahrnuty jako soukromé statické metody nebo metody instance do třídy aplikace.

Metodu můžete <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> také zahrnout do knihovny regulárních výrazů.

Pokud jsou používány v knihovně regulárních výrazů, můžete je volat pomocí kódu, například následujícího:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Viz také

- [.NET Framework – regulární výrazy](../../../docs/standard/base-types/regular-expressions.md)
