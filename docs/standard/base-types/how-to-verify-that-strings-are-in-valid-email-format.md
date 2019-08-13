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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6381747bc998f73b374442fcb15e025ca15795d
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "65589522"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Postupy: Ověření platnosti e-mailového formátu řetězců
Následující příklad používá regulární výraz pro ověření, zda je řetězec v platném formátu e-mailu.  

## <a name="example"></a>Příklad  
 Příklad definuje `IsValidEmail` metodu, která vrátí `true` , pokud řetězec obsahuje platnou e-mailovou adresu, `false` a pokud ne, ale neprovede žádnou jinou akci.  
  
 Chcete-li ověřit, zda je e-mailová adresa platná <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> , `IsValidEmail` metoda volá `(@)(.+)$` metodu se vzorem regulárního výrazu, který odděluje název domény od e-mailové adresy. Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegát, který představuje metodu, která zpracovává a nahrazuje odpovídající text. Vzor regulárního výrazu je interpretován následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(@)`|Porovnává znak @. Toto je první zachytávající skupina.|  
|`(.+)`|Porovnává jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|  
|`$`|Ukončí porovnávání na konci řetězce.|  
  
 Název domény společně s znakem @ je předán `DomainMapper` metodě, která <xref:System.Globalization.IdnMapping> používá třídu k překladu znaků Unicode, které jsou mimo rozsah znaků US-ASCII na Punycode. Metoda také nastaví `invalid` příznak na, `True` Pokud <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> Metoda zjistí v názvu domény neplatné znaky. Metoda vrátí název domény Punycode předchází symbolu @ do `IsValidEmail` metody.  
  
 `IsValidEmail` Metoda pak <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> zavolá metodu pro ověření, že adresa odpovídá vzoru regulárního výrazu.  
  
 Všimněte si, `IsValidEmail` že metoda neprovádí ověřování pro ověření e-mailové adresy. Pouze určuje, zda je formát platný pro e-mailovou adresu. Kromě toho `IsValidEmail` metoda neověřuje, jestli je název domény nejvyšší úrovně platný název domény uvedený v [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), což by vyžadovalo vyhledávací operaci. Místo toho regulární výraz pouze ověří, zda se název domény nejvyšší úrovně skládá ze dvou a dvaceti čtyř znaků ASCII, s alfanumerickým prvním a posledním znakem a zbývajícími znaky buď alfanumerických, nebo spojovníkem (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 V tomto příkladu je vzor ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` regulárního výrazu interpretován tak, jak je znázorněno v následující tabulce. Všimněte si, že regulární výraz je kompilován pomocí <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> příznaku.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahajte shodu na začátku řetězce.|  
|`(?(")`|Určí, zda je první znak uvozovka. `(?(")`je začátek konstrukce alternace.|  
|`(?("")("".+?(?<!\\)""@)`|Pokud je prvním znakem uvozovka, porovnává počáteční uvozovku následovanou alespoň jedním výskytem libovolného znaku následovaný koncovou uvozovkou. Koncovému uvozovku nesmí předcházet znak zpětného lomítka (\\). `(?<!`je začátek kontrolního výrazu negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl být uzavřen znakem @.|  
|<code>&#124;(([0-9a-z]</code>|Pokud první znak není znak uvozovek, porovná libovolný abecední znak od a do z nebo A až Z (porovnání rozlišuje malá a velká písmena) nebo libovolný číselný znak od 0 do 9.|  
|`(\.(?!\.))`|Je-li dalším znakem tečka, bude odpovídat. Pokud se nejedná o tečku, hledejte dopředu na další znak a pokračujte v porovnávání. `(?!\.)`je negativní kontrolní výraz dopředného vyhledávání s nulovou šířkou, který brání v zobrazení dvou po sobě jdoucích teček v místní části e-mailové adresy.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>|Pokud další znak není tečka, odpovídá libovolnému znaku slova nebo jednomu z následujících znaků:-! # $% ' * + =? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>|Odpovídá vzoru alternace (tečka následovaný netečkou nebo jedním z několika znaků) nula nebo vícekrát.|  
|`@`|Porovnává znak @.|  
|`(?<=[0-9a-z])`|Pokračuje v porovnávání, pokud znak, který předchází znaku @, je A až Z, a až z nebo 0 až 9. `(?<=[0-9a-z])` Konstrukce definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|  
|`(?(\[)`|Ověřte, zda je znak, který následuje po znaku @, levou hranatou závorkou.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Pokud se jedná o levou hranatou závorku, porovnává levou hranatou závorku následovanou IP adresou (čtyři sady jedna až tři číslice, každá sada oddělená tečkou) a pravou hranatou závorku.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Pokud znak, který následuje za @, není levou závorku, porovná jeden alfanumerický znak s hodnotou A-Z, a-z nebo 0-9, za kterým následuje nula nebo více výskytů spojovníku, následovaný žádným nebo jedním alfanumerickým znakem a hodnotou A-Z, a-z nebo 0-9 následovaný tečkou. Tento model se může opakovat jednou nebo víckrát a musí následovat název domény nejvyšší úrovně.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, A-Z a 0-9). Může také obsahovat nula až 22 znaků ASCII, které jsou buď alfanumerické, nebo spojovníky.|  
|`$`|Ukončí porovnávání na konci řetězce.|  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Metody `IsValidEmail` a`DomainMapper` mohou být zahrnuty v knihovně nástrojů regulárních výrazů, nebo mohou být zahrnuty jako privátní statické nebo metody instance třídy aplikace.  
  
 Můžete také použít <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodu k zahrnutí tohoto regulárního výrazu do knihovny regulárních výrazů.  
  
 Pokud jsou použity v knihovně regulárních výrazů, můžete je volat pomocí kódu, jako je následující:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [.NET Framework regulární výrazy](../../../docs/standard/base-types/regular-expressions.md)
