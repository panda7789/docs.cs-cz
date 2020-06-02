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
ms.openlocfilehash: e86bae8a687e89acba9a0b713630b43809f081d1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290626"
---
# <a name="anchors-in-regular-expressions"></a>Kotvy v regulárních výrazech
Kotvy nebo atomické kontrolní výrazy s nulovou šířkou určují pozici v řetězci, kde musí být shoda. Použijete-li ve výrazu hledání kotvu, modul regulárních výrazů neprojde řetězcem ani nespotřebovává znaky; vyhledá shodu pouze na zadané pozici. Například `^` Určuje, že shoda musí začínat na začátku řádku nebo řetězce. Proto regulární výraz `^http:` odpovídá "http:" pouze v případě, že dojde na začátku řádku. V následující tabulce jsou uvedeny kotvy podporované regulárními výrazy v rozhraní .NET.  
  
|Ukotvení|Popis|  
|------------|-----------------|  
|`^`|Ve výchozím nastavení se shoda musí vyskytovat na začátku řetězce; v víceřádkovém režimu se musí vyskytovat na začátku řádku. Další informace naleznete v tématu [Začátek řetězce nebo řádku](#start-of-string-or-line-).|  
|`$`|Ve výchozím nastavení se shoda musí vyskytovat na konci řetězce nebo před `\n` koncem řetězce; ve víceřádkovém režimu se musí vyskytovat na konci řádku nebo před `\n` koncem řádku. Další informace najdete v tématu [konec řetězce nebo řádku](#end-of-string-or-line-).|  
|`\A`|Shoda se musí vyskytovat na začátku jenom řetězce (bez víceřádkové podpory). Další informace najdete v tématu [začátek pouze řetězce](#start-of-string-only-a).|  
|`\Z`|Shoda se musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce. Další informace najdete v tématu [konec řetězce nebo před ukončením nového řádku](#end-of-string-or-before-ending-newline-z).|  
|`\z`|Shoda se musí vyskytovat na konci řetězce. Další informace naleznete v tématu [konec řetězce](#end-of-string-only-z).|  
|`\G`|Shoda musí začínat na pozici, kde byla ukončena předchozí shoda. Další informace naleznete v tématu [souvislé shody](#contiguous-matches-g).|  
|`\b`|Shoda se musí vyskytovat na hranici slova. Další informace najdete v tématu [hranice slova](#word-boundary-b).|  
|`\B`|Shoda se nesmí vyskytovat na hranici slova. Další informace najdete v tématu [hranice jiné než slova](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Na začátku řetězce nebo řádku: ^  
 Ve výchozím nastavení `^` kotva určuje, že následující vzor musí začínat na první pozici znaku v řetězci. Pokud použijete `^` s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možností (viz [Možnosti regulárních výrazů](regular-expression-options.md)), shoda se musí vyskytovat na začátku každého řádku.  
  
 Následující příklad používá `^` kotvu v regulárním výrazu, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Příklad volá dvě přetížení <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
- Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> přetížení vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu.  
  
- Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> přetížení s `options` parametrem nastaveným k <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> vyhledá všechny pět podřetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Vzor regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahajte porovnávání na začátku vstupního řetězce (nebo začátek řádku, pokud je metoda volána s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možností).|  
|`((\w+(\s?)){2,}`|Porovná jeden nebo více znaků slova následovaných žádným nebo jedním mezerou alespoň dvakrát. Toto je první zachytávající skupina. Tento výraz také definuje druhou a třetí zachytávající skupinu: Druhá obsahuje zachycené slovo a třetí tvoří zachycené prázdné znaky.|  
|`,\s`|Porovnává čárku následovanou prázdným znakem.|  
|`(\w+\s\w+)`|Porovnává jeden nebo více slovních znaků následovaných mezerou a následováním jednoho nebo více znaků slova. Toto je čtvrtá zachytávající skupina.|  
|`,`|Porovnává čárku.|  
|`\s\d{4}`|Porovnává mezeru následovanou čtyřmi desítkovými číslicemi.|  
|<code>(-(\d{4}&#124;present))?</code>|Porovná žádný nebo jeden výskyt spojovníku následovaný čtyřmi desítkovými číslicemi nebo řetězcem "prezentovat". Toto je šestá zachytávající skupina. Zahrnuje také sedmou zachytávající skupinu.|  
|`,?`|Porovná žádný nebo jeden výskyt čárky.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Porovná jeden nebo více výskytů následujícího: mezeru, čtyři desítkové číslice, nula nebo jeden výskyt pomlčky následovaný čtyřmi desítkovými číslicemi nebo řetězcem "prezentovat" a žádnou nebo jednou čárkou. Toto je pátá zachytávající skupina.|

## <a name="end-of-string-or-line-"></a>Na konci řetězce nebo řádku: $  
 `$`Kotva určuje, že předchozí vzorek musí být na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce.  
  
 Použijete `$` -li s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možností, může k shodě dojít také na konci řádku. Všimněte si, že se `$` `\n` shodují, ale neshodují `\r\n` se (kombinace návratových znaků a znaků nového řádku, nebo CR/LF). Chcete-li porovnat kombinaci znaků CR/LF, zahrňte `\r?$` do vzoru regulárního výrazu.  
  
 Následující příklad přidá `$` kotvu do vzoru regulárního výrazu, který je použit v příkladu v části [Začátek řetězce nebo řádku](#start-of-string-or-line-) . Při použití s původním vstupním řetězcem, který obsahuje pět řádků textu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> Metoda nemůže najít shodu, protože konec prvního řádku neodpovídá `$` vzoru. Když je původní vstupní řetězec rozdělen do pole řetězce, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> Metoda bude úspěšná v porovnání s každým pěti řádky. Pokud <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> je metoda volána s `options` parametrem nastaveným na hodnotu <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> , nebyly nalezeny žádné shody, protože vzor regulárního výrazu není v účtu pro návratový element (\u + 000D). Nicméně, když je vzor regulárního výrazu upraven nahrazením `$` pomocí `\r?$` , volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody s `options` parametrem nastaveným pro <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opětovné vyhledá pět shod.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Jen za začátku řetězce: \A  
 `\A`Kotva určuje, že shoda se musí vyskytovat na začátku vstupního řetězce. Je totožný s `^` ukotvením, s tím rozdílem, že `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto může odpovídat pouze začátku prvního řádku ve víceřádkovém vstupním řetězci.  
  
 Následující příklad je podobný příkladům pro `^` `$` kotvy a. Používá `\A` kotvu v regulárním výrazu, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Vstupní řetězec obsahuje pět řádků. Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. Jak ukazuje příklad, <xref:System.Text.RegularExpressions.RegexOptions.Multiline> možnost nemá žádný vliv.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Na konci řetězce nebo před novým řádkem na konci řetězce: \Z  
 `\Z`Kotva určuje, že shoda se musí vyskytovat na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce. Je totožný s `$` ukotvením, s tím rozdílem, že `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto může být v víceřádkovém řetězci jen na konci posledního řádku nebo posledního řádku `\n` .  
  
 Všimněte si, že se `\Z` `\n` shodují, ale neshodují `\r\n` se (kombinace znaků CR/LF). Chcete-li porovnat znaky CR/LF, zahrňte `\r?\Z` do vzoru regulárního výrazu.  
  
 V následujícím příkladu je použita `\Z` kotva regulárního výrazu, který je podobný příkladu v části [Začátek řetězce nebo řádku](#start-of-string-or-line-) , který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Dílčí výraz `\r?\Z` regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` odpovídá konci řetězce a také odpovídá řetězci, který končí `\n` nebo `\r\n` . V důsledku toho každý prvek v poli odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Jen na konci řetězce: \z  
 `\z`Kotva určuje, že shoda se musí vyskytovat na konci vstupního řetězce. Podobně jako `$` prvek jazyka, `\z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Na rozdíl od `\Z` elementu jazyka, neodpovídá `\z` `\n` znaku na konci řetězce. Proto může odpovídat pouze poslednímu řádku vstupního řetězce.  
  
 V následujícím příkladu je použita `\z` kotva regulárního výrazu, který je jinak totožný s příkladem v předchozí části, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Tento příklad se pokusí porovnat každý z pěti prvků v poli řetězců se vzorem regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z` . Dva z řetězců končí znakem pro návrat na začátek řádku a znakem kanálu čáry, jeden končí znakem kanálu čáry a dva elementy end bez znaku návratu na začátek řádku ani znakového kanálu. Jak ukazuje výstup, pouze řetězce bez návratu na začátek řádku nebo znak kanálu čáry se shodují se vzorem.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Souvislé porovnávání: \G  
 `\G`Kotva určuje, že shoda se musí vyskytovat v místě, kde byla ukončena předchozí shoda. Použijete-li tento kotvu <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> s <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodou nebo, zajistíte, aby všechny shody byly souvislé.  
  
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
 `\b`Kotva určuje, že shoda se musí vyskytovat na hranici mezi znakem slova ( `\w` element jazyka) a znakem, který není ( `\W` element jazyka). Znaky slova se skládají z alfanumerických znaků a podtržítek; znak jiný než Word je libovolný znak, který není alfanumerický nebo podtržítko. (Další informace naleznete v tématu [třídy znaků](character-classes-in-regular-expressions.md).) Shoda se může vyskytovat také na hranici slova na začátku nebo konci řetězce.  
  
 `\b`Kotva se často používá k zajištění, že dílčí výraz odpovídá celému slovu, a ne jenom začátku nebo konci slova. Regulární výraz `\bare\w*\b` v následujícím příkladě znázorňuje toto použití. Odpovídá libovolnému slovu, které začíná podřetězcem "jsou". Výstup z příkladu také znázorňuje, že `\b` odpovídá začátku i konci vstupního řetězce.  
  
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
 `\B`Kotva určuje, že shoda se nesmí vyskytovat na hranici slova. Je opakem `\b` kotvy.  
  
 Následující příklad používá `\B` kotvu k vyhledání výskytů podřetězce "qu" ve slově. Vzor regulárního výrazu se `\Bqu\w+` shoduje s podřetězcem, který začíná "qu", který nespouští slovo a pokračuje na konci slova.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Vzor regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\B`|Nespustí porovnávání na hranici slova.|  
|`qu`|Porovnává s podřetězcem "qu".|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](regular-expression-language-quick-reference.md)
- [Možnosti regulárních výrazů](regular-expression-options.md)
