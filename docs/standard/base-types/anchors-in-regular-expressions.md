---
title: Kotvy v regulárních výrazech .NET
description: Další informace o použití kotvy ve vzorech regulárního výrazu.
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
ms.custom: seodec18
ms.openlocfilehash: d5d07dd290a857a0c6dbfcd9074d8d16ff47e6cd
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155035"
---
# <a name="anchors-in-regular-expressions"></a>Kotvy v regulárních výrazech
<a name="top"></a> Kotvy vztahů nebo atomické kontrolní výrazy s nulovou šířkou, určit pozici v řetězci, kde ke shodě musí dojít. Při použití ukotvení v hledaný výraz, modul regulárních výrazů v řetězci nebo spotřebovával znaky; Vyhledá shodu pouze na určené pozici. Například `^` Určuje, že porovnání musí začít na začátku řetězce nebo řádku. Proto regulárního výrazu `^http:` odpovídá "http:" pouze pokud se nachází na začátku řádku. V následující tabulce jsou uvedeny kotvy podporované regulárními výrazy v rozhraní .NET.  
  
|Ukotvení|Popis|  
|------------|-----------------|  
|`^`|Ve výchozím nastavení ke shodě musí dojít na začátku řetězce; v víceřádkový režim musí dojít na začátku řádku. Další informace najdete v tématu [začátek řetězce nebo řádku](#Start).|  
|`$`|Ve výchozím nastavení, ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce; v víceřádkový režim, musí dojít na konci čáry nebo před `\n` na konci řádku. Další informace najdete v tématu [ukončení řetězce nebo řádku](#End).|  
|`\A`|Ke shodě musí dojít na začátku řetězce pouze (bez podpory multiline). Další informace najdete v tématu [spustit z řetězce pouze](#StartOnly).|  
|`\Z`|Ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce. Další informace najdete v tématu [ukončení řetězce nebo před koncovou znaku nového řádku](#EndOrNOnly).|  
|`\z`|Ke shodě musí dojít na konci řetězce pouze. Další informace najdete v tématu [End z řetězce pouze](#EndOnly).|  
|`\G`|Porovnání musí začít na pozici, kde nskončila předchozí shoda. Další informace najdete v tématu [Souvislé porovnávání](#Contiguous).|  
|`\b`|Ke shodě musí dojít na hranici slova. Další informace najdete v tématu [hranice slova](#WordBoundary).|  
|`\B`|Ke shodě nesmí dojít na hranici slova. Další informace najdete v tématu [mimoslovní hranice](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Na začátku řetězce nebo řádku: ^  
 Ve výchozím nastavení `^` ukotvení Určuje, že následující vzor musí začínat na první pozici znaku řetězce. Pokud používáte `^` s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost (viz [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md)), ke shodě musí dojít na začátku každého řádku.  
  
 V následujícím příkladu `^` ukotvení v regulárním výrazu, který extrahuje informace o let, během které existovaly některé baseballu profesionální týmy. Příklad volá dvě přetížení <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
-   Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> přetížení vyhledá pouze prvního podřetězce ve vstupním řetězci, který odpovídá vzoru regulárního výrazu.  
  
-   Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> přetížení s `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> vyhledá všech pět podřetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Vzor regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce (nebo na začátku řádku, pokud je metoda volána s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost).|  
|`((\w+(\s?)){2,}`|Porovná jeden nebo více znaků slova, následovaný nulou nebo o jednu mezeru přesně dvakrát. Toto je první zachytávající skupina. Tento výraz definuje také druhý a třetí zachytávající skupina: Druhý se skládá ze zachyceného slova a třetí se skládá z zachycené mezery.|  
|`,\s`|Porovná čárkou následovanou prázdným znakem.|  
|`(\w+\s\w+)`|Porovná jeden nebo více znaků slova, za nímž následuje mezera, za nímž následuje jedna nebo více znaků slova. Toto je čtvrtý zachytávající skupina.|  
|`,`|Porovná čárku.|  
|`\s\d{4}`|Porovná mezerou následovanou čtyři desítková čísla.|  
|<code>(-(\d{4}&#124;present))?</code>|Porovná žádný nebo jeden výskyt spojovník následovaný písmenem čtyři desítková čísla nebo řetězce "k dispozici". Toto je šestého zachytávající skupina. Zahrnuje také sedmý zachytávající skupinu.|  
|`,?`|Porovná žádný nebo jeden výskyt čárku.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Porovná jeden nebo více výskytů následující: mezera, čtyři desítková čísla, žádný nebo jeden výskyt spojovník následovaný písmenem čtyři desítková čísla nebo řetězce "obsahuje" a žádnou či jednou čárkou. Toto je pátý zachytávající skupina.|  
  
 [Zpět na začátek](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Na konci řetězce nebo řádku: $  
 `$` Ukotvení Určuje, že předchozí vzor se musí vyskytovat na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce.  
  
 Pokud používáte `$` s <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možností shody může také dojít na konci řádku. Všimněte si, že `$` odpovídá `\n` ale neodpovídá `\r\n` (kombinace znaků návrat na začátek řádku vrátit a znakem nového řádku nebo CR/LF). Tak, aby odpovídaly kombinaci znaků CR/LF, zahrnují `\r?$` ve vzoru regulárního výrazu.  
  
 Následující příklad přidá `$` kotvy na vzor regulárního výrazu použitý v příkladu v [začátek řetězce nebo řádku](#Start) oddílu. Při použití s původního vstupního řetězce, který obsahuje pět řádků textu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda nepovedlo se najít shodu, protože konci prvního řádku se neshoduje s `$` vzor. Když je rozdělit původního vstupního řetězce na pole řetězců, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda bude úspěšná ve všech pěti řádcích odpovídající. Když <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda je volána `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nejsou nalezeny žádné shody, protože vzor regulárního výrazu nezahrnuje návratový prvek (\u+000D). Ale kdy vzor regulárního výrazu upraven tak, že nahradíte `$` s `\r?$`, volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metodu `options` parametr nastaven na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znovu najde pět shod.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Zpět na začátek](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Jen za začátku řetězce: \A  
 `\A` Ukotvení Určuje, že ke shodě musí dojít na začátku vstupního řetězce. Je stejný jako `^` ukotvení, s výjimkou, že `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto lze porovnávat pouze spuštění prvního řádku v Víceřádkový vstupní řetězec.  
  
 Následující příklad je podobné příklady `^` a `$` ukotvení. Používá `\A` ukotvení v regulárním výrazu, který extrahuje informace o let, během které existovaly některé baseballu profesionální týmy. Vstupní řetězec obsahuje pět řádků. Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda vyhledá pouze prvního podřetězce ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. Jak ukazuje příklad <xref:System.Text.RegularExpressions.RegexOptions.Multiline> možnost nemá žádný vliv.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Zpět na začátek](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Na konci řetězce nebo před novým řádkem na konci řetězce: \Z  
 `\Z` Ukotvení Určuje, že ke shodě musí dojít na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce. Je stejný jako `$` ukotvení, s výjimkou, že `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Proto v Víceřádkový řetězec ho odpovídá pouze konci poslední řádek nebo poslední řádek před `\n`.  
  
 Všimněte si, že `\Z` odpovídá `\n` ale neodpovídá `\r\n` (kombinaci znaků CR/LF). Tak, aby odpovídaly znaků CR/LF, zahrnují `\r?\Z` ve vzoru regulárního výrazu.  
  
 V následujícím příkladu `\Z` ukotvení v regulárním výrazu, který je podobně jako v příkladu v [začátek řetězce nebo řádku](#Start) oddíl, který extrahuje informace o let, během které některé profesionální baseballu existovaly týmy. Dílčí výraz `\r?\Z` v regulárním výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` odpovídá konci řetězce a také odpovídající řetězec, který končí `\n` nebo `\r\n`. V důsledku toho každý prvek v poli odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Zpět na začátek](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Jen na konci řetězce: \z  
 `\z` Ukotvení Určuje, že ke shodě musí dojít na konci vstupního řetězce. Podobně jako `$` prvek jazyka `\z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Na rozdíl od `\Z` prvek jazyka `\z` se neshoduje `\n` znak na konci řetězce. Proto lze porovnávat pouze poslední řádek vstupního řetězce.  
  
 V následujícím příkladu `\z` ukotvení v regulárním výrazu, který jinak je stejný jako v příkladu v předchozí části, který extrahuje informace o let, během které existovaly některé baseballu profesionální týmy. Příklad se pokusí porovnat každý z pěti prvků v poli řetězců se vzorem regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Dva konce řetězce s návrat na začátek řádku vrátit a LF znaků, jeden končí znakem, odřádkování a dva koncové s ani zalomení řádku vrátit ani znak LF. Jak ukazuje výstup, vrátí pouze řetězce bez nebo LF znaků shoda vzoru.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Zpět na začátek](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Souvislé porovnávání: \G  
 `\G` Ukotvení Určuje, že ke shodě musí dojít v místě, kde nskončila předchozí shoda. Při použití tohoto ukotvení s <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda, je zaručeno, že všechny shody jsou souvislé.  
  
 Následující příklad používá regulární výraz k extrahování názvů hlodavce z řetězce oddělených čárkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Regulární výraz `\G(\w+\s?\w*),?` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Proces, kde skončila poslední shody.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\s?`|Porovná žádnou nebo jednu mezeru.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`(\w+\s?\w*)`|Porovná jeden nebo více znaků slova, za nímž následuje žádný nebo jeden znak, následovaný nula nebo více znaků slova. Toto je první zachytávající skupina.|  
|`,?`|Porovná žádný nebo jeden výskyt znak čárky.|  
  
 [Zpět na začátek](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Na hranici slova: \b  
 `\b` Ukotvení Určuje, že shoda se musí vyskytovat na hranici mezi znakem slova ( `\w` prvek jazyka) a mimoslovní znak ( `\W` prvek jazyka). Znaků slova skládat z alfanumerické znaky nebo podtržítka; Mimoslovní znak je jakýkoli znak, který není alfanumerické znaky nebo podtržítka. (Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Ke shodě může také dojít na hranici slova na začátku nebo konci řetězce.  
  
 `\b` Ukotvení se často používá k zajištění, že dílčí výraz odpovídá celé slovo namísto pouze začátku nebo konci slova. Regulární výraz `\bare\w*\b` v následujícím příkladu ukazuje toto využití. Odpovídá libovolné slovo, který začíná pod řetězcem "je". Výstup z příkladu také ukazuje, že `\b` odpovídá začátku a konci vstupního řetězce.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Vzor regulárního výrazu je interpretován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`are`|Porovná podřetězec "je".|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Mimo hranice slova: \B  
 `\B` Ukotvení Určuje, že ke shodě nesmí dojít na hranici slova. Je opakem `\b` ukotvení.  
  
 V následujícím příkladu `\B` ukotvení vyhledáte výskyty podřetězce "časový" ve slově. Vzor regulárního výrazu `\Bqu\w+` odpovídá dílčí řetězec, který začíná "časový", nespustí slovo a, která dál konci slovo.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Vzor regulárního výrazu je interpretován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\B`|Začne porovnání na hranici slova.|  
|`qu`|Porovná podřetězec "časový".|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
- [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
