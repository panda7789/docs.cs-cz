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
ms.openlocfilehash: 360ed985575358dd9603a55fc2d5d6c297621ec8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290419"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Ověření platnosti e-mailového formátu řetězců

Následující příklad používá regulární výraz pro ověření, zda je řetězec v platném formátu e-mailu.

## <a name="example"></a>Příklad

Příklad definuje `IsValidEmail` metodu, která vrátí, `true` Pokud řetězec obsahuje platnou e-mailovou adresu `false` , a pokud ne, ale neprovede žádnou jinou akci.

Chcete-li ověřit, zda je e-mailová adresa platná, `IsValidEmail` metoda volá <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metodu se `(@)(.+)$` vzorem regulárního výrazu, který odděluje název domény od e-mailové adresy. Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegát, který představuje metodu, která zpracovává a nahrazuje odpovídající text. Vzor regulárního výrazu je interpretován následujícím způsobem.

|Vzor|Popis|
|-------------|-----------------|
|`(@)`|Porovnává znak @. Toto je první zachytávající skupina.|
|`(.+)`|Porovnává jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|
|`$`|Ukončí porovnávání na konci řetězce.|

Název domény společně s znakem @ je předán `DomainMapper` metodě, která používá <xref:System.Globalization.IdnMapping> třídu k překladu znaků Unicode, které jsou mimo rozsah znaků US-ASCII na Punycode. Metoda také nastaví `invalid` příznak na, `True` Pokud <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> Metoda zjistí v názvu domény neplatné znaky. Metoda vrátí název domény Punycode předchází symbolu @ do `IsValidEmail` metody.

`IsValidEmail`Metoda pak zavolá <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu pro ověření, že adresa odpovídá vzoru regulárního výrazu.

Všimněte si, že `IsValidEmail` Metoda neprovádí ověřování pro ověření e-mailové adresy. Pouze určuje, zda je formát platný pro e-mailovou adresu. Kromě toho `IsValidEmail` metoda neověřuje, jestli je název domény nejvyšší úrovně platný název domény uvedený v [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), což by vyžadovalo vyhledávací operaci. Místo toho regulární výraz pouze ověří, zda se název domény nejvyšší úrovně skládá ze dvou a dvaceti čtyř znaků ASCII, s alfanumerickým prvním a posledním znakem a zbývajícími znaky buď alfanumerických, nebo spojovníkem (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

V tomto příkladu je vzor regulárního výrazu ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` interpretován tak, jak je znázorněno v následující legendě. Regulární výraz je kompilován pomocí <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> příznaku.

Vzor `^` : začátek porovnávání na začátku řetězce.

Vzor `(?(")` : Určete, zda je první znak uvozovka. `(?(")`je začátek konstrukce alternace.

Vzor `(?(")(".+?(?<!\\)"@)` : Pokud je první znak uvozovky, porovnává počáteční uvozovku následovanou alespoň jedním výskytem libovolného znaku následovaný koncovou uvozovkou. Koncovému uvozovku nesmí předcházet znak zpětného lomítka ( \\ ). `(?<!`je začátek kontrolního výrazu negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl být uzavřen znakem @.

Vzor `|(([0-9a-z]` : Pokud první znak není uvozovka, odpovídá jakémukoli abecednímu znaku z a až z nebo a až z (porovnání rozlišuje malá a velká písmena) nebo libovolný číselný znak od 0 do 9.

Vzor `(\.(?!\.))` : Pokud je další znak tečky, porovnejte ho. Pokud se nejedná o tečku, hledejte dopředu na další znak a pokračujte v porovnávání. `(?!\.)`je negativní kontrolní výraz dopředného vyhledávání s nulovou šířkou, který brání v zobrazení dvou po sobě jdoucích teček v místní části e-mailové adresy.

Vzor ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]`` : Pokud následující znak není tečka, odpovídá libovolnému znaku slova nebo jednomu z následujících znaků:-! # $% & ' \* +/=? ^ \` {} | ~

Vzor ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*`` : vyrovnává vzor alternace (perioda následovaná netečkou nebo jedním z několika znaků) nula nebo vícekrát.

Vzor `@` : porovnává znak @.

Vzor `(?<=[0-9a-z])` : pokračuje v porovnávání, pokud znak, který předchází znaku @, je a až z, a až z nebo 0 až 9. Tento model definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.

Vzor `(?(\[)` : Ověřte, zda je znak, který následuje po znaku @, levou hranatou závorkou.

Vzor `(\[(\d{1,3}\.){3}\d{1,3}\])` : Pokud se jedná o levou hranatou závorku, porovnává levou hranatou závorku následovanou IP adresou (čtyři sady jedna až tři číslice, každá sada oddělená tečkou) a pravou hranatou závorku.

Vzor `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+` : Pokud znak, který následuje za @, není levou hranatou závorkou, porovná jeden alfanumerický znak s hodnotou a-z, a-z nebo 0-9, následovaný žádným nebo více výskyty pomlčky, následovaný žádným nebo jedním alfanumerickým znakem a hodnotou a-z, a-z nebo 0-9 následovaný tečkou. Tento model se může opakovat jednou nebo víckrát a musí následovat název domény nejvyšší úrovně.

Vzor `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` : název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, a-z a 0-9). Může také obsahovat nula až 22 znaků ASCII, které jsou buď alfanumerické, nebo spojovníky.

Vzor `$` : ukončí porovnávání na konci řetězce.

## <a name="compile-the-code"></a>Kompilovat kód

`IsValidEmail`Metody a `DomainMapper` mohou být zahrnuty v knihovně nástrojů regulárních výrazů, nebo mohou být zahrnuty jako privátní statické nebo metody instance třídy aplikace.

Můžete také použít <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodu k zahrnutí tohoto regulárního výrazu do knihovny regulárních výrazů.

Pokud jsou použity v knihovně regulárních výrazů, můžete je volat pomocí kódu, jako je následující:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Viz také

- [.NET Framework – regulární výrazy](regular-expressions.md)
