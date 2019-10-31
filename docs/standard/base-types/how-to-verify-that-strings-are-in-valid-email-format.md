---
title: 'Postupy: Ověření platnosti e-mailového formátu řetězců'
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
ms.openlocfilehash: 1812235da6e6d02a97fe994568c5c26a3c7cde33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126403"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Postupy: ověření, zda jsou řetězce v platném formátu e-mailu

Následující příklad používá regulární výraz pro ověření, zda je řetězec v platném formátu e-mailu.

## <a name="example"></a>Příklad

Příklad definuje metodu `IsValidEmail`, která vrátí `true`, pokud řetězec obsahuje platnou e-mailovou adresu a `false` Pokud není, ale neprovede žádnou jinou akci.

Chcete-li ověřit, zda je e-mailová adresa platná, metoda `IsValidEmail` volá metodu <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> se vzorem regulárního výrazu `(@)(.+)$` pro oddělení názvu domény z e-mailové adresy. Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegát, který představuje metodu, která zpracovává a nahrazuje odpovídající text. Vzor regulárního výrazu je interpretován následujícím způsobem.

|Vzor|Popis|
|-------------|-----------------|
|`(@)`|Porovnává znak @. Toto je první zachytávající skupina.|
|`(.+)`|Porovnává jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|
|`$`|Ukončí porovnávání na konci řetězce.|

Název domény společně s znakem @ je předán metodě `DomainMapper`, která používá třídu <xref:System.Globalization.IdnMapping> k překladu znaků Unicode, které jsou mimo rozsah znaků US-ASCII na Punycode. Metoda také nastaví příznak `invalid`, aby `True`, pokud metoda <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> zjistí v názvu domény neplatné znaky. Metoda vrátí název domény Punycode předchází symbolem @ do metody `IsValidEmail`.

Metoda `IsValidEmail` pak zavolá metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> a ověří tak, že adresa odpovídá vzoru regulárního výrazu.

Všimněte si, že metoda `IsValidEmail` neprovádí ověřování pro ověření e-mailové adresy. Pouze určuje, zda je formát platný pro e-mailovou adresu. Kromě toho metoda `IsValidEmail` neověřuje, jestli je název domény nejvyšší úrovně platný název domény uvedený v [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), která by vyžadovala vyhledávací operaci. Místo toho regulární výraz pouze ověří, zda se název domény nejvyšší úrovně skládá ze dvou a dvaceti čtyř znaků ASCII, s alfanumerickým prvním a posledním znakem a zbývajícími znaky buď alfanumerických, nebo spojovníkem (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

V tomto příkladu je vzor regulárního výrazu ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` interpretován tak, jak je znázorněno v následující legendě. Regulární výraz je kompilován pomocí příznaku <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.

`^`vzoru: začátek porovnávání na začátku řetězce.

Vzor `(?(")`: Určete, zda je první znak uvozovka. `(?(")` je začátek konstrukce alternace.

Vzor `(?(")(".+?(?<!\\)"@)`: Pokud je první znak uvozovky, porovnává počáteční uvozovku následovanou alespoň jedním výskytem libovolného znaku následovaný koncovou uvozovkou. Koncovému znaku uvozovky nesmí předcházet znak zpětného lomítka (\\). `(?<!` je začátek kontrolního výrazu negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl být uzavřen znakem @.

Vzor `|(([0-9a-z]`: Pokud první znak není znak uvozovek, odpovídá jakémukoli abecednímu znaku z a až z nebo A až Z (porovnání rozlišuje malá a velká písmena) nebo libovolný číselný znak od 0 do 9.

Vzor `(\.(?!\.))`: Pokud je dalším znakem tečka, porovnává se s ním. Pokud se nejedná o tečku, hledejte dopředu na další znak a pokračujte v porovnávání. `(?!\.)` je negativní kontrolní výraz dopředného vyhledávání s nulovou šířkou, který brání v zobrazení dvou po sobě jdoucích teček v místní části e-mailové adresy.

Vzor ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: Pokud následující znak není tečka, odpovídá libovolnému znaku slova nebo jednomu z následujících znaků:-! # $% & ' * +/=? ^ '{}| ~

Vzor ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: odpovídá vzoru alternace (tečka následovaná netečkou nebo jedním z několika znaků) nula nebo vícekrát.

Pattern `@`: odpovídá znaku @.

Pattern `(?<=[0-9a-z])`: pokračuje v porovnávání, pokud znak, který předchází znaku @, je A až Z, a až z nebo 0 až 9. Tento model definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.

Vzor `(?(\[)`: Ověřte, zda je znak, který následuje po znaku @, levou hranatou závorkou.

Vzor `(\[(\d{1,3}\.){3}\d{1,3}\])`: Pokud se jedná o levou hranatou závorku, porovnává levou závorku následovanou IP adresou (čtyři sady jedna až tři číslice, každá sada oddělená tečkou) a pravou hranatou závorku.

Vzor `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: Pokud znak, který následuje za @, není levou hranatou závorkou, odpovídá jednomu alfanumerickému znaku s hodnotou A-Z, a-z nebo 0-9, následuje nula nebo více výskytů spojovníku, následovaný žádným nebo jedním alfanumerickým znakem a hodnotou A-Z , a-z nebo 0-9, následované tečkou. Tento model se může opakovat jednou nebo víckrát a musí následovat název domény nejvyšší úrovně.

Vzor `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, A-Z a 0-9). Může také obsahovat nula až 22 znaků ASCII, které jsou buď alfanumerické, nebo spojovníky.

Pattern `$`: ukončí porovnávání na konci řetězce.

## <a name="compile-the-code"></a>Kompilovat kód

Metody `IsValidEmail` a `DomainMapper` lze zahrnout do knihovny nástrojů regulárních výrazů, nebo mohou být zahrnuty jako soukromé statické nebo instanční metody třídy aplikace.

Můžete také použít metodu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> k zahrnutí tohoto regulárního výrazu do knihovny regulárních výrazů.

Pokud jsou použity v knihovně regulárních výrazů, můžete je volat pomocí kódu, jako je následující:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Viz také:

- [.NET Framework regulární výrazy](../../../docs/standard/base-types/regular-expressions.md)
