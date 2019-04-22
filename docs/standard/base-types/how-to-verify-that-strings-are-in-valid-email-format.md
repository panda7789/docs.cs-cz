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
ms.openlocfilehash: 78210f9f007060551130812fcb5a9cd5b4728adc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890498"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Postupy: Ověření platnosti e-mailového formátu řetězců
Následující příklad používá regulární výraz k ověření, že je řetězec ve formátu platné e-mailu.  

## <a name="example"></a>Příklad  
 V příkladu je definována `IsValidEmail` metodu, která vrací `true` Pokud řetězec obsahuje platnou e-mailovou adresu a `false` Pokud ne, ale neprovede žádnou akci.  
  
 Chcete-li ověřit, že je platný, e-mailovou adresu `IsValidEmail` volání metod <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metodu s `(@)(.+)$` vzor regulárního výrazu k oddělení názvu domény od e-mailovou adresu. Třetí parametr je <xref:System.Text.RegularExpressions.MatchEvaluator> delegáta, který představuje metodu, která zpracovává a nahradí odpovídající text. Vzor regulárního výrazu je interpretován následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(@)`|Shoda znak @. Toto je první zachytávající skupina.|  
|`(.+)`|Porovná jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|  
|`$`|Ukončit porovnávání na konci řetězce.|  
  
 Název domény spolu se znak @ je předán `DomainMapper` metodu, která používá <xref:System.Globalization.IdnMapping> třídy pro překlad znaků Unicode, které jsou mimo rozsah znaků US-ASCII na kódování Punycode. Metoda také nastaví `invalid` příznak `True` Pokud <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metoda zjistí neplatné znaky v názvu domény. Metoda vrátí název domény Punycode začínající podle symbolem @ do `IsValidEmail` metody.  
  
 `IsValidEmail` Pak zavolá metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k ověření, zda adresa odpovídá vzoru regulárního výrazu.  
  
 Všimněte si, `IsValidEmail` metoda neprovádí ověřování k ověření e-mailovou adresu. Pouze určuje, zda její formát je platný pro e-mailovou adresu. Kromě toho `IsValidEmail` metoda neověřuje, že název domény nejvyšší úrovně je platný název domény uvedený na [databázi kořenové zóny IANA](https://www.iana.org/domains/root/db), která by vyžadovala vyhledávací operace. Regulární výrazy místo toho pouze ověří, že název domény nejvyšší úrovně se skládá ze dvou až 24 znaků ASCII, první a poslední znak alfanumerický a ostatní znaky jsou buď číslice nebo alfanumerické znaky a spojovník (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 V tomto příkladu vzor regulárního výrazu ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` interpretována, jak je znázorněno v následující tabulce. Všimněte si, že regulární výraz je zkompilován pomocí <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> příznak.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`(?(")`|Určení, zda je první znak uvozovek. `(?(")` je začátek konstrukce alternace.|  
|`(?("")("".+?(?<!\\)""@)`|Pokud je první znak uvozovky, porovná počáteční uvozovky následované alespoň jedním výskyt libovolný znak, následovaný koncovými uvozovkami. Koncovými uvozovkami nesmí být předchází znak zpětného lomítka (\\). `(?<!` je začátek kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl končit zavináčem zavináč (@).|  
|<code>&#124;(([0-9a-z]</code>|Pokud prvním znakem není znak uvozovek, porovná libovolný znak abecedy od až z nebo A až Z (porovnání velká a malá písmena), nebo jakémukoli číselnému znaku od 0 do 9.|  
|`(\.(?!\.))`|Pokud další znakem je tečka, spárujte ji. Pokud není období, hledejte další znak a pokračuje v porovnávání. `(?!\.)` je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který bránil zobrazení dvou po sobě jdoucí tečky v místní části e-mailovou adresu.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>| Pokud následující znak není tečka, odpovídá jakémukoli znaku slova nebo některý z následujících znaků:-! #$% ' * +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>| Srovnejte vzor alternace (tečku následovanou bez období nebo jeden z počtu znaků) nulakrát nebo vícekrát.|  
|`@`|Shoda znak @.|  
|`(?<=[0-9a-z])`|Pokračuje v porovnávání, pokud znak, který předchází znak @ je A až Z, a až z nebo 0 až 9. `(?<=[0-9a-z])` Konstrukce definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|  
|`(?(\[)`|Zkontrolujte, zda znak, který následuje po @ je levá hranatá závorka.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Pokud je levá hranatá závorka, Porovná levou závorku následovaný IP adresou (čtyři sady jednoho až tří číslic, každá sada oddělená tečkou) a pravou hranatou závorku.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Pokud znak, který následuje @ není levá hranatá závorka, porovná jeden alfanumerický znak s hodnotou A-Z, a-z nebo 0-9, za nímž následuje nula nebo několik výskytů spojovníku, následované žádnou nebo jednu alfanumerickým znakem s hodnotou A-Z, a-z nebo 0-9 , následovaných tečkou. Tento vzor lze opakovat jednou nebo vícekrát a musí následovat název domény nejvyšší úrovně.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Název domény nejvyšší úrovně musí začínat a končit alfanumerickým znakem (a-z, A-Z a 0 – 9). Od nuly do 22 znaků ASCII, které jsou buď může také obsahovat alfanumerické znaky nebo spojovníky.|  
|`$`|Ukončit porovnávání na konci řetězce.|  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 `IsValidEmail` a `DomainMapper` metody mohou být součástí knihovny pomocných metod regulárních výrazů, nebo mohou být zahrnuty jako soukromé statické metoda nebo metody instance třídy aplikace.  
  
 Pro zahrnutí v knihovny regulárních výrazů, buď zkopírujte a vložte kód do projektu knihovny tříd Visual Studio, nebo zkopírujte a jeho vložením do textového souboru a kompilaci z příkazového řádku s příkaz podobný tomuto (za předpokladu, že název zdrojového kódu  soubor je RegexUtilities.cs nebo RegexUtilities.vb:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Můžete také použít <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> tak, aby zahrnoval tento regulární výraz v knihovny regulárních výrazů.  
  
 Pokud jsou použity v knihovny regulárních výrazů, můžete je zavolat pomocí kódu, jako jsou následující:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 Za předpokladu, že jste vytvořili knihovnu tříd s názvem RegexUtilities.dll, který obsahuje regulární výraz ověření e-mailu, můžete kompilaci tohoto příkladu v některém z následujících způsobů:  
  
-   V sadě Visual Studio, tak, že vytvoření konzolové aplikace a přidání odkazu na RegexUtilities.dll do projektu.  
  
-   Z příkazového řádku, zkopírováním a vložením kódu do textového souboru a jeho kompilace s příkaz podobný tomuto (za předpokladu, že je název souboru se zdrojovým kódem Example.cs nebo Example.vb:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazech .NET Frameworku](../../../docs/standard/base-types/regular-expressions.md)
