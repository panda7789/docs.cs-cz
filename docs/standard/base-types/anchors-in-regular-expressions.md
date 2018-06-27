---
title: Kotvy v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET Framework regular expressions, anchors
- .NET Framework regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a579acacf41df24779252e1064e1c271310edc
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948586"
---
# <a name="anchors-in-regular-expressions"></a>Kotvy v regulárních výrazech
<a name="top"></a> Kotvy nebo atomické kontrolní výrazy s nulovou šířkou určují pozici v řetězci, kde musí dojít ke shodě. Pokud použijete na ukotvení v hledaný výraz, modul regulárních výrazů v řetězci nebo využívat znaků; Vypadá to shody na určené pozici. Například `^` Určuje, že porovnávání musí začít na začátku řádku nebo řetězec. Proto s regulárním výrazem `^http:` odpovídá "http:" pouze pokud se nachází na začátku řádku. Následující tabulka uvádí ukotvení podporované regulární výrazy v rozhraní .NET.  
  
|Ukotvení|Popis|  
|------------|-----------------|  
|`^`|Ve výchozím nastavení shoda se musí vyskytovat na začátku řetězce; v víceřádkového režimu musí dojít na začátek řádku. Další informace najdete v tématu [začátek řetězce nebo řádku](#Start).|  
|`$`|Ve výchozím nastavení, shoda se musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce; v víceřádkového režimu, musí dojít na konci řádku nebo před `\n` na konci řádku. Další informace najdete v tématu [ukončení řetězce nebo řádku](#End).|  
|`\A`|Shoda se musí vyskytovat na začátku pouze řetězec (bez víceřádkové podpory). Další informace najdete v tématu [spustit z řetězce pouze](#StartOnly).|  
|`\Z`|Shoda se musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce. Další informace najdete v tématu [ukončení řetězce nebo ukončení před novým řádkem](#EndOrNOnly).|  
|`\z`|Shoda se musí vyskytovat na konci pouze řetězce. Další informace najdete v tématu [End z řetězce pouze](#EndOnly).|  
|`\G`|Shody musí začínat na pozici, kde byl ukončen předchozí shodě. Další informace najdete v tématu [Souvislé porovnávání](#Contiguous).|  
|`\b`|Shoda se musí vyskytovat na hranici slova. Další informace najdete v tématu [hranice slova](#WordBoundary).|  
|`\B`|Ke shodě nesmí dojít na hranici slova. Další informace najdete v tématu [hranice mimo slovo](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Na začátku řetězce nebo řádku: ^  
 Ve výchozím nastavení `^` ukotvení Určuje, že následující vzor musí začínat na první pozici znaku řetězce. Pokud používáte `^` s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost (viz [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)), shoda se musí vyskytovat na začátku každého řádku.  
  
 Následující příklad používá `^` ukotvení v regulární výraz, který extrahuje informace o let, během které existovaly některé profesionální baseballové týmy. V příkladu volá dvě přetížení <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda:  
  
-   Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> přetížení vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá regulární výraz.  
  
-   Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> přetížení s `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> vyhledá všechny pět dílčích řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Regulární výraz `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začne porovnávání na začátku vstupní řetězec (nebo na začátku řádku, pokud metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost).|  
|`((\w+(\s?)){2,}`|Porovná jeden nebo více znaků slova a potom pomocí nula nebo pomocí jediného místa přesně dvakrát. Toto je první zachytávající skupina. Tento výraz také definuje skupinu zachycení druhý a třetí: druhý se skládá z zaznamenané word a třetí se skládá z zachycené mezery.|  
|`,\s`|Odpovídat středník a prázdný znak.|  
|`(\w+\s\w+)`|Porovná jeden nebo více znaků slova následované mezerou, za nímž následuje jeden nebo více znaků slova. Toto je čtvrtý zachycující skupina.|  
|`,`|Porovná čárku.|  
|`\s\d{4}`|Odpovídat mezeru a čtyři desetinných míst.|  
|<code>(-(\d{4}&#124;present))?</code>|Porovná nula nebo jeden výskyt pomlčky následovaný čtyři desítková číslice nebo řetězec "existuje". Toto je šesté zachytávající skupina. Zahrnuje také sedmý, zaznamenávání skupiny.|  
|`,?`|Porovná nula nebo jeden výskyt čárkou.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Porovná jeden nebo více výskytů následující: mezery, čtyři desetinných míst, nula nebo jeden výskyt pomlčky následovaný čtyři desítková číslice nebo řetězec "přítomen" a nula nebo jeden čárkami. Toto je pátá zachytávající skupina.|  
  
 [Zpět na začátek](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Na konci řetězce nebo řádku: $  
 `$` Ukotvení Určuje, že předchozí vzor musí dojít na konci vstupní řetězec, nebo před `\n` na konci vstupní řetězec.  
  
 Pokud používáte `$` s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost Shoda může také nastat na konci řádku. Všimněte si, že `$` odpovídá `\n` ale neodpovídá `\r\n` (kombinace znaků CR vrátit a znaky konce řádku znaky ani znaky CR/LF). Tak, aby odpovídaly kombinaci znaků CR/LF, zahrnují `\r?$` v regulární výraz.  
  
 Následující příklad přidá `$` kotvy na vzor regulárního výrazu používaný v příkladu v [začátek řetězce nebo řádku](#Start) části. Při použití s původní vstupní řetězec, který obsahuje pět řádků textu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda se nepodařilo najít shodu, protože konci prvního řádku neodpovídá `$` vzor. Pokud původní vstupní řetězec rozdělen na pole, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda úspěšně porovná každý z pěti řádků. Když <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda je volána s `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, protože regulární výraz nezahrnuje návratový prvek (\u+000D) nejsou nalezeny žádné shody. Pokud je však regulární výraz pozměněn nahrazením `$` s `\r?$`, volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda s `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znovu najde pět shod.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Zpět na začátek](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Jen za začátku řetězce: \A  
 `\A` Ukotvení Určuje, že ke shodě musí dojít na začátku vstupní řetězec. Je stejný jako `^` ukotvení, vyjma toho, že `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto může odpovídat jenom spuštění v prvním řádku Víceřádkový vstupní řetězec.  
  
 V následujícím příkladu je podobná příklady pro `^` a `$` ukotvení. Použije `\A` ukotvení v regulární výraz, který extrahuje informace o let, během které existovaly některé profesionální baseballové týmy. Vstupní řetězec obsahuje pět řádků. Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá regulární výraz. Jak ukazuje příklad <xref:System.Text.RegularExpressions.RegexOptions.Multiline> možnost nemá žádný vliv.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Zpět na začátek](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Na konci řetězce nebo před novým řádkem na konci řetězce: \Z  
 `\Z` Ukotvení Určuje, že shoda musí dojít na konci vstupní řetězec, nebo před `\n` na konci vstupní řetězec. Je stejný jako `$` ukotvení, vyjma toho, že `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto v řetězec Víceřádkový porovnávat pouze konec posledního řádku nebo před poslední řádek `\n`.  
  
 Všimněte si, že `\Z` odpovídá `\n` ale neodpovídá `\r\n` (kombinaci znaků CR/LF). Tak, aby odpovídaly CR/LF, zahrnují `\r?\Z` v regulární výraz.  
  
 Následující příklad používá `\Z` ukotvení v regulární výraz, který je podobné jako v příkladu v [začátek řetězce nebo řádku](#Start) oddíl, který extrahuje informace o let, během které některé profesionální baseballové existovaly týmy. Dílčím výrazu `\r?\Z` v regulárním výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` odpovídá konce řetězce a také shoduje s řetězcem, který končí `\n` nebo `\r\n`. V důsledku toho každý prvek v poli odpovídá regulární výraz.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Zpět na začátek](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Jen na konci řetězce: \z  
 `\z` Ukotvení Určuje, že ke shodě musí dojít na konci vstupní řetězec. Jako `$` jazyk element `\z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Na rozdíl od `\Z` prvek jazyka `\z` neodpovídá `\n` znak na konci řetězce. Proto může porovnávat pouze poslední řádek vstupní řetězec.  
  
 Následující příklad používá `\z` ukotvení v regulární výraz, který je jinak stejný jako v příkladu v předchozím oddílu, který extrahuje informace o let, během které existovaly některé profesionální baseballové týmy. V příkladu se pokusí porovnat každý z pěti prvků v poli řetězců s regulární výraz `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Dva řetězce končit znaků CR vrátit a odřádkování, jeden končí znakem, odřádkování a vrátit dvě končit ani znaků CR ani znakem odřádkování. Jak ukazuje výstup vrátit pouze řetězce bez nebo odřádkování znak shoda vzoru.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Zpět na začátek](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Souvislé porovnávání: \G  
 `\G` Ukotvení Určuje, že ke shodě musí dojít v místě, kde byl ukončen předchozí shodě. Při použití tohoto ukotvení s <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda, zajišťuje, že jsou všechny shody souvislé.  
  
 Následující příklad používá regulární výraz k extrakci názvy hlodavce z řetězce s položkami oddělenými čárkou.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Regulární výraz `\G(\w+\s?\w*),?` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začít, kde poslední porovnávání ukončeno.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\s?`|Odpovídat žádnou nebo jednu místa.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`(\w+\s?\w*)`|Porovná jeden nebo více znaků slova, za nímž následuje žádnou nebo jednu mezeru a nula nebo více znaků slova. Toto je první zachytávající skupina.|  
|`,?`|Porovná nula nebo jeden výskyt znaku čárky.|  
  
 [Zpět na začátek](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Na hranici slova: \b  
 `\b` Ukotvení Určuje, že shoda se musí vyskytovat na hranici mezi znakem slova ( `\w` prvek jazyka) a znak bez slova ( `\W` prvek jazyka). Písmena obsahovat alfanumerické znaky a podtržítka; libovolný znak, který není alfanumerické nebo podtržítkem je znak aplikace word. (Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Shody může taky dojít na hranici slova na začátku nebo na konci řetězce.  
  
 `\b` Ukotvení se často používá k zajistěte, aby odpovídal dílčím výrazu celá slova místo jen začátku nebo konci slova. Regulární výraz `\bare\w*\b` následující příklad ukazuje toto využití. Odpovídá libovolné slovo, které začíná dílčí řetězec "jsou". Výstup z příkladu také ukazuje, že `\b` odpovídá začátku a konci vstupní řetězec.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Regulární výraz interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`are`|Porovná podřetězec "jsou".|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Mimo hranice slova: \B  
 `\B` Ukotvení Určuje, že shoda nesmí objevit na hranici slova. Je opakem `\b` ukotvení.  
  
 Následující příklad používá `\B` ukotvení najít výskyty dílčí řetězec "qu" aplikace word. Regulární výraz `\Bqu\w+` odpovídá dílčí řetězec, který začíná na "qu", který není na začátku slova a který pokračuje ke konci slova.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Regulární výraz interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\B`|Není začne porovnávání na hranici slova.|  
|`qu`|Porovná podřetězec "qu".|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
