---
title: Kotvy v regulárních výrazech .NET
description: Naučte se používat kotvy ve vzorcích regulárních výrazů.
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
ms.openlocfilehash: c4853a6854f5da1a3217c976a03ddbde3b528560
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159660"
---
# <a name="anchors-in-regular-expressions"></a>Kotvy v regulárních výrazech
Kotvy nebo atomické kontrolní výrazy s nulovou šířkou určují pozici v řetězci, kde musí být shoda. Použijete-li ve výrazu hledání kotvu, modul regulárních výrazů neprojde řetězcem ani nespotřebovává znaky; vyhledá shodu pouze na zadané pozici. Například `^` určuje, že shoda musí začínat na začátku řádku nebo řetězce. Proto regulární výraz `^http:` odpovídá "http:" pouze v případě, že dojde na začátku řádku. V následující tabulce jsou uvedeny kotvy podporované regulárními výrazy v rozhraní .NET.  
  
|Ukotvení|Popis|  
|------------|-----------------|  
|`^`|Ve výchozím nastavení se shoda musí vyskytovat na začátku řetězce; v víceřádkovém režimu se musí vyskytovat na začátku řádku. Další informace naleznete v tématu [Začátek řetězce nebo řádku](#start-of-string-or-line-).|  
|`$`|Ve výchozím nastavení se shoda musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce; v víceřádkovém režimu se musí vyskytovat na konci řádku nebo před `\n` na konci řádku. Další informace najdete v tématu [konec řetězce nebo řádku](#end-of-string-or-line-).|  
|`\A`|Shoda se musí vyskytovat na začátku jenom řetězce (bez víceřádkové podpory). Další informace najdete v tématu [začátek pouze řetězce](#start-of-string-only-a).|  
|`\Z`|Ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce. Další informace najdete v tématu [konec řetězce nebo před ukončením nového řádku](#end-of-string-or-before-ending-newline-z).|  
|`\z`|Shoda se musí vyskytovat na konci řetězce. Další informace naleznete v tématu [konec řetězce](#end-of-string-only-z).|  
|`\G`|Shoda musí začínat na pozici, kde byla ukončena předchozí shoda. Další informace naleznete v tématu [souvislé shody](#contiguous-matches-g).|  
|`\b`|Shoda se musí vyskytovat na hranici slova. Další informace najdete v tématu [hranice slova](#word-boundary-b).|  
|`\B`|Shoda se nesmí vyskytovat na hranici slova. Další informace najdete v tématu [hranice jiné než slova](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Na začátku řetězce nebo řádku: ^  
 Ve výchozím nastavení kotva `^` určuje, že následující vzor musí začínat na první pozici znaku v řetězci. Použijete-li `^` s možností <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> (viz [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)), shoda se musí vyskytovat na začátku každého řádku.  
  
 Následující příklad používá kotvu `^` v regulárním výrazu, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Příklad volá dvě přetížení metody <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>:  
  
- Volání metody <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> Overload vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu.  
  
- Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> přetížení s parametrem `options` nastaveným na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> vyhledá všechny pět podřetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Vzor regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahajte shodu na začátku vstupního řetězce (nebo začátek řádku, pokud je metoda volána s možností <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>).|  
|`((\w+(\s?)){2,}`|Porovná jeden nebo více znaků slova následovaných žádným nebo jedním mezerou alespoň dvakrát. Toto je první zachytávající skupina. Tento výraz také definuje druhou a třetí zachytávající skupinu: Druhá obsahuje zachycené slovo a třetí tvoří zachycené prázdné znaky.|  
|`,\s`|Porovnává čárku následovanou prázdným znakem.|  
|`(\w+\s\w+)`|Porovnává jeden nebo více slovních znaků následovaných mezerou a následováním jednoho nebo více znaků slova. Toto je čtvrtá zachytávající skupina.|  
|`,`|Porovnává čárku.|  
|`\s\d{4}`|Porovnává mezeru následovanou čtyřmi desítkovými číslicemi.|  
|<code>(-(\d{4}&#124;present))?</code>|Porovná žádný nebo jeden výskyt spojovníku následovaný čtyřmi desítkovými číslicemi nebo řetězcem "prezentovat". Toto je šestá zachytávající skupina. Zahrnuje také sedmou zachytávající skupinu.|  
|`,?`|Porovná žádný nebo jeden výskyt čárky.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Porovná jeden nebo více výskytů následujícího: mezeru, čtyři desítkové číslice, nula nebo jeden výskyt pomlčky následovaný čtyřmi desítkovými číslicemi nebo řetězcem "prezentovat" a žádnou nebo jednou čárkou. Toto je pátá zachytávající skupina.|

## <a name="end-of-string-or-line-"></a>Na konci řetězce nebo řádku: $  
 Kotva `$` určuje, že předchozí vzor musí být na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce.  
  
 Použijete-li `$` s možností <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, může k shodě dojít také na konci řádku. Všimněte si, že `$` odpovídá `\n`, ale neodpovídá `\r\n` (kombinace návratových znaků a znaků nového řádku, nebo CR/LF). Chcete-li porovnat kombinaci znaků CR/LF, zahrňte `\r?$` do vzoru regulárního výrazu.  
  
 Následující příklad přidá kotvu `$` do vzoru regulárního výrazu, který je použit v příkladu v části [Začátek řetězce nebo řádku](#start-of-string-or-line-) . Při použití s původním vstupním řetězcem, který obsahuje pět řádků textu, metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> nemůže najít shodu, protože konec prvního řádku neodpovídá vzoru `$`. Když je původní vstupní řetězec rozdělen do pole řetězců, metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> je úspěšná v porovnání s každým pěti řádky. Pokud je metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> volána s parametrem `options` nastaveným na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nebyly nalezeny žádné shody, protože vzor regulárního výrazu není v účtu pro návratový element (\u + 000D). Pokud je však změněn vzor regulárního výrazu nahrazením `$` `\r?$`, voláním metody <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> s parametrem `options` nastaveným na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znovu najde pět shod.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Jen za začátku řetězce: \A  
 Kotva `\A` určuje, že shoda se musí vyskytovat na začátku vstupního řetězce. Je totožný s kotvou `^`, s tím rozdílem, že `\A` ignoruje možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Proto může odpovídat pouze začátku prvního řádku ve víceřádkovém vstupním řetězci.  
  
 Následující příklad je podobný příkladům pro `^` a `$` kotvy. Používá kotvu `\A` v regulárním výrazu, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Vstupní řetězec obsahuje pět řádků. Volání metody <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. Jak ukazuje příklad, možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline> nemá žádný vliv.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Na konci řetězce nebo před novým řádkem na konci řetězce: \Z  
 Kotva `\Z` určuje, že shoda se musí vyskytovat na konci vstupního řetězce, nebo před `\n` na konci vstupního řetězce. Je totožný s kotvou `$`, s tím rozdílem, že `\Z` ignoruje možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Proto může být v víceřádkovém řetězci pouze pro konec posledního řádku nebo poslední řádek před `\n`.  
  
 Všimněte si, že `\Z` odpovídá `\n`, ale neodpovídá `\r\n` (kombinace znaků CR/LF). Chcete-li porovnat znaky CR/LF, zahrňte `\r?\Z` do vzoru regulárního výrazu.  
  
 Následující příklad používá kotvu `\Z` v regulárním výrazu, který je podobný příkladu v části [Začátek řetězce nebo řádku](#start-of-string-or-line-) , který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Dílčí výraz `\r?\Z` v regulárním výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` odpovídá konci řetězce a také odpovídá řetězci, který končí `\n` nebo `\r\n`. V důsledku toho každý prvek v poli odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Jen na konci řetězce: \z  
 Kotva `\z` určuje, že shoda se musí vyskytovat na konci vstupního řetězce. Podobně jako prvek jazyka `$` `\z` ignoruje možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Na rozdíl od elementu `\Z` jazyka `\z` neodpovídá znaku `\n` na konci řetězce. Proto může odpovídat pouze poslednímu řádku vstupního řetězce.  
  
 Následující příklad používá kotvu `\z` v regulárním výrazu, který je jinak totožný s příkladem v předchozí části, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Tento příklad se pokusí porovnat každý z pěti prvků v poli řetězců se vzorem regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Dva z řetězců končí znakem pro návrat na začátek řádku a znakem kanálu čáry, jeden končí znakem kanálu čáry a dva elementy end bez znaku návratu na začátek řádku ani znakového kanálu. Jak ukazuje výstup, pouze řetězce bez návratu na začátek řádku nebo znak kanálu čáry se shodují se vzorem.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Souvislé porovnávání: \G  
 Kotva `\G` určuje, že shoda se musí vyskytovat v místě, kde byla ukončena předchozí shoda. Při použití tohoto kotvy s metodou <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> zajistíte, aby všechny shody byly souvislé.  
  
 Následující příklad používá regulární výraz k extrakci názvů druhů hlodavců z řetězce odděleného čárkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Regulární výraz `\G(\w+\s?\w*),?` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začněte, kde poslední shoda skončila.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\s?`|Porovná nula nebo jednu mezeru.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`(\w+\s?\w*)`|Porovná jeden nebo více znaků slova následovaných žádným nebo jedním znakem, za kterým následuje nula nebo více znaků slova. Toto je první zachytávající skupina.|  
|`,?`|Porovná žádný nebo jeden výskyt literálního znaku čárky.|

## <a name="word-boundary-b"></a>Na hranici slova: \b  
 Kotva `\b` určuje, že shoda se musí vyskytovat na hranici mezi znakem slova (prvek jazyka `\w`) a znakem, který není znakem slova (prvek jazyka `\W`). Znaky slova se skládají z alfanumerických znaků a podtržítek; znak jiný než Word je libovolný znak, který není alfanumerický nebo podtržítko. (Další informace naleznete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Shoda se může vyskytovat také na hranici slova na začátku nebo konci řetězce.  
  
 Kotva `\b` se často používá k zajištění, že dílčí výraz odpovídá celému slovu, a ne jenom začátku nebo konci slova. Toto použití ukazuje regulární výraz `\bare\w*\b` v následujícím příkladu. Odpovídá libovolnému slovu, které začíná podřetězcem "jsou". Výstup z příkladu také znázorňuje, že `\b` odpovídá začátku i konci vstupního řetězce.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Vzor regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`are`|Porovnává s podřetězcem "jsou".|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  

## <a name="non-word-boundary-b"></a>Mimo hranice slova: \B  
 Kotva `\B` určuje, že shoda se nesmí vyskytovat na hranici slova. Je opakem `\b` kotvy.  
  
 Následující příklad používá kotvu `\B` k vyhledání výskytů podřetězce "qu" ve slově. Vzor regulárního výrazu `\Bqu\w+` shodný s podřetězcem, který začíná "qu", který nespouští slovo a pokračuje na konci slova.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Vzor regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\B`|Nespustí porovnávání na hranici slova.|  
|`qu`|Porovnává s podřetězcem "qu".|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
