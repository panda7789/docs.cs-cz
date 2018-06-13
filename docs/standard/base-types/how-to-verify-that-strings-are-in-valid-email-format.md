---
title: 'Postupy: Ověření platnosti e-mailového formátu řetězců'
ms.date: 03/30/2017
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
ms.openlocfilehash: 02c942dea3314581ce8f758bb9ed3ce88c2fe150
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172325"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Postupy: Ověření platnosti e-mailového formátu řetězců
Následující příklad používá regulární výraz k ověření, že je řetězec ve formátu platné e-mailu.  

> [!NOTE]
>  Doporučujeme používat <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> třídy Kontrola, zda je řetězec ve formátu platnou e-mailovou adresu. Kvůli tomu předat e-mailovou adresu řetězec, který má <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktoru třídy, která vyvolává <xref:System.FormatException> Pokud řetězec obsahuje nerozpoznaný formát.  
  
## <a name="example"></a>Příklad  
 V příkladu je definován `IsValidEmail` metoda, která vrátí `true` Pokud řetězec obsahuje platnou e-mailovou adresu a `false` Pokud ne, ale žádné další akce.  
  
 Chcete-li ověřit, že e-mailová adresa je platná, `IsValidEmail` volání metod <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metoda s `(@)(.+)$` vzor regulárního výrazu nezávislá na název domény e-mailovou adresu. Třetí parametr není <xref:System.Text.RegularExpressions.MatchEvaluator> delegáta, který představuje metodu, která zpracovává a nahradí odpovídající text. Regulární výraz interpretována následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(@)`|Shoda znak @. Toto je první zachytávající skupina.|  
|`(.+)`|Porovná jeden nebo více výskytů libovolného znaku. Toto je druhá zachytávající skupina.|  
|`$`|Ukončí porovnávání na konci řetězce.|  
  
 Název domény spolu s znak @ je předán `DomainMapper` metoda, která používá <xref:System.Globalization.IdnMapping> třída přeložit znaky znakové sady Unicode, které jsou mimo rozsah znaků US-ASCII na kódování Punycode. Metoda také nastaví `invalid` příznak, který `True` Pokud <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metoda zjistí žádné neplatné znaky v názvu domény. Metoda vrátí název domény Punycode předchází @ symbol, který má `IsValidEmail` metoda.  
  
 `IsValidEmail` Metoda pak zavolá <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k ověření, že adresa odpovídá regulárnímu výrazu.  
  
 Všimněte si, že `IsValidEmail` metoda neprovádí ověřování k ověření e-mailovou adresu. Jenom Určuje, zda je formát platný pro e-mailovou adresu. Kromě toho `IsValidEmail` metoda neověřuje, zda je název domény nejvyšší úrovně platný název domény uvedený na [IANA kořenová zóna databáze](https://www.iana.org/domains/root/db), které by vyžadovaly operace hledání. Regulární výraz místo toho jenom ověřuje, že název domény nejvyšší úrovně se skládá z mezi dvěma a 24 znaky ASCII s alfanumerické znaky první a poslední a ostatní znaky, alfanumerické znaky nebo a pomlčku (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 V tomto příkladu regulární výraz ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` interpretována, jak je znázorněno v následující tabulce. Všimněte si, že regulární výraz zkompilován pomocí <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> příznak.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začne porovnávání na začátku řetězce.|  
|`(?(")`|Určete, zda je první znak uvozovky. `(?(")` je začátku alternace.|  
|`(?("")("".+?(?<!\\)""@)`|Je-li první znak je znak uvozovek, odpovídat začátku uvozovky následuje alespoň jeden výskyt libovolný znak, za nímž následuje koncové uvozovky. Koncové uvozovky nesmí předcházet zpětné lomítko (\\). `(?<!` je začátku kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou. Řetězec by měl uzavřít s znaku zavináče (@).|  
|<code>&#124;(([0-9a-z]</code>|Je-li první znak není uvozovky, odpovídat libovolný znak abecedy z do z nebo A až Z (porovnání se malá a velká písmena), nebo jakékoli číselné znak od 0 do 9.|  
|`(\.(?!\.))`|Pokud další znak je dobou, shodovat se. Pokud není po dobu, Hledat na další znak a pokračovat na shodu. `(?!\.)` je negativního nulovou šířkou dopředného vyhledávání, která zabraňuje zobrazování v místní část e-mailovou adresu dvě po sobě jdoucí tečky.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}\&#124;~\w]</code>|Pokud další znak není dobou, odpovídají libovolný znak nebo jeden z následujících znaků:-! #$% ' * +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}\&#124;~\w])*</code>|Shodují se vzorem alternace (období, za nímž následuje jiný období nebo jeden z a počet znaků) nula či více krát.|  
|`@`|Shoda znak @.|  
|`(?<=[0-9a-z])`|Pokračovat shody, pokud znak, který předchází @ – znak je A až Z, a až z nebo 0 až 9. `(?<=[0-9a-z])` Konstrukce definuje výraz kladné zpětného vyhledávání s nulovou šířkou.|  
|`(?(\[)`|Zkontrolujte, zda je znak, který následuje @ levou hranatou závorku.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Pokud je levou hranatou závorku, odpovídat levá hranatá závorka následovaný IP adresu (čtyři sady číslic jednu až tři, každý sadou odděleny tečkou) a pravá závorka.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Pokud je znak, který následuje @ není levou hranatou závorku, jeden alfanumerický znak shodu s hodnotou A-Z, a-z nebo 0-9, za nímž následuje nula nebo více výskytů pomlčka, za nímž následuje žádnou nebo jednu alfanumerický znak s hodnotou A-Z, a-z nebo 0-9 , za nímž následuje období. Tento vzor lze opakovat, jeden či více krát a musí následovat název domény nejvyšší úrovně.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Název domény nejvyšší úrovně musí začít a končit alfanumerickým znakem (a-z, A-Z a 0 – 9). Může být také dostupný od nuly do 22 znaků ASCII, které jsou buď alfanumerické nebo pomlčky.|  
|`$`|Ukončí porovnávání na konci řetězce.|  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 `IsValidEmail` a `DomainMapper` metody mohou být součástí knihovny metod nástroj regulární výraz nebo může být zahrnuta jako privátní statickou nebo instanci metody třídy aplikace.  
  
 Pro zahrnutí do knihovny regulárních výrazů, buď zkopírujte a vložte kód do projektu knihovny tříd Visual Studio, nebo zkopírujte a vložte ho do textového souboru a kompilaci z příkazového řádku pomocí příkazu takto (za předpokladu, že název zdrojového kódu  soubor je RegexUtilities.cs nebo RegexUtilities.vb:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Můžete také <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> tak, aby zahrnoval regulárnímu výrazu v knihovně regulární výraz.  
  
 Pokud se používají v knihovně regulárního výrazu, můžete je volat pomocí kódu, například následující:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 Za předpokladu, že jste vytvořili knihovny tříd s názvem RegexUtilities.dll, která obsahuje vaše e-mailu ověření regulárního výrazu, můžete zkompilovat tento příklad v některém z následujících způsobů:  
  
-   V sadě Visual Studio, vytvoření konzolové aplikace a přidáním odkaz na RegexUtilities.dll do projektu.  
  
-   Z příkazového řádku, kopírování a vkládání zdrojový kód do textového souboru a kompilování pomocí příkazu takto (za předpokladu, že je název souboru se zdrojovým kódem Example.cs nebo Example.vb:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET framework](../../../docs/standard/base-types/regular-expressions.md)
