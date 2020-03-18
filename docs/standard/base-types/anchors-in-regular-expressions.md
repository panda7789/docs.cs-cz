---
title: Kotvy v regulárních výrazech rozhraní .NET
description: Přečtěte si, jak používat kotvy ve vzorcích regulárních výrazů.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159660"
---
# <a name="anchors-in-regular-expressions"></a>Kotvy v regulárních výrazech
Kotvy nebo atomické kontrolní výrazy s nulovou šířkou určují pozici v řetězci, kde musí dojít ke shodě. Při použití kotvy ve vyhledávacím výrazu modul regulárních výrazů nepostupuje řetězcem ani nespotřebovává znaky; vyhledá shodu pouze v zadané pozici. Například `^` určuje, že shoda musí začínat na začátku řádku nebo řetězce. Regulární výraz `^http:` proto odpovídá "http:" pouze v případě, že k němu dojde na začátku řádku. V následující tabulce jsou uvedeny kotvy podporované regulárními výrazy v rozhraní .NET.  
  
|Ukotvení|Popis|  
|------------|-----------------|  
|`^`|Ve výchozím nastavení musí dojít k shodě na začátku řetězce; ve víceřádkovém režimu, musí se objevit na začátku řádku. Další informace naleznete [v tématu Začátek řetězce nebo řádku](#start-of-string-or-line-).|  
|`$`|Ve výchozím nastavení musí dojít k shodě `\n` na konci řetězce nebo před na konci řetězce; ve víceřádkovém režimu, musí se objevit `\n` na konci řádku nebo před koncem řádku. Další informace naleznete [v tématu Konec řetězce nebo řádek](#end-of-string-or-line-).|  
|`\A`|Shoda musí dojít pouze na začátku řetězce (bez podpory více řádků). Další informace naleznete [v tématu Začátek pouze řetězce](#start-of-string-only-a).|  
|`\Z`|Shoda musí dojít na konci řetězce nebo `\n` před na konci řetězce. Další informace naleznete [v tématu Konec řetězce nebo Před ukončením nového řádku](#end-of-string-or-before-ending-newline-z).|  
|`\z`|Shoda musí dojít pouze na konci řetězce. Další informace naleznete [v tématu End of String Only](#end-of-string-only-z).|  
|`\G`|Shoda musí začínat na pozici, kde skončila předchozí shoda. Další informace naleznete [v tématu Sousedící shody](#contiguous-matches-g).|  
|`\b`|Shoda musí dojít na hranici slova. Další informace naleznete v tématu [Hranice aplikace Word](#word-boundary-b).|  
|`\B`|Shoda nesmí dojít na hranici slova. Další informace naleznete [v tématu Non-Word Boundary](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Na začátku řetězce nebo řádku: ^  
 Ve výchozím `^` nastavení kotva určuje, že následující vzorek musí začínat na pozici prvního znaku řetězce. Pokud použijete `^` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> s možností (viz [Možnosti regulárního výrazu](../../../docs/standard/base-types/regular-expression-options.md)), musí dojít ke shodě na začátku každého řádku.  
  
 Následující příklad používá `^` kotvu v regulárním výrazu, který extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Příklad volá dvě přetížení <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
- Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> přetížení najde pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu.  
  
- Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> přetížení s parametrem `options` nastaveným na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> vyhledá všech pět podřetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Vzor regulárního výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začněte shodu na začátku vstupního řetězce (nebo začátku <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> řádku, pokud je metoda volána s možností).|  
|`((\w+(\s?)){2,}`|Porovná jeden nebo více znaků slova následovaných nulou nebo jednou mezerou alespoň dvakrát. Toto je první zachytávající skupina. Tento výraz také definuje druhou a třetí zachytávající skupinu: Druhý se skládá ze zachyceného slova a třetí se skládá ze zachyceného prázdného místa.|  
|`,\s`|Porovná čárku následovanou znakem prázdného místa.|  
|`(\w+\s\w+)`|Porovná jeden nebo více znaků slova následovaných mezerou následovanou jedním nebo více znaky slova. Toto je čtvrtá zachytávající skupina.|  
|`,`|Porovnejte čárku.|  
|`\s\d{4}`|Porovná mezeru následovanou čtyřmi desetinnými místy.|  
|<code>(-(\d{4}&#124;present))?</code>|Porovná nulový nebo jeden výskyt pomlčky následovaný čtyřmi desetinnými číslicemi nebo řetězcem "present". Toto je šestá zachytávající skupina. Obsahuje také sedmou zachytávající skupinu.|  
|`,?`|Porovná nula nebo jeden výskyt čárky.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Porovná jeden nebo více výskytů následujících událostí: mezeru, čtyři desetinná místa, nulu nebo jeden výskyt pomlčky následovaný čtyřmi desetinnými místy nebo řetězcem "prezentovat" a nulou nebo jednou čárkou. Toto je pátá zachytávající skupina.|

## <a name="end-of-string-or-line-"></a>Na konci řetězce nebo řádku: $  
 Kotva `$` určuje, že předchozí vzorek musí dojít na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce.  
  
 Pokud použijete `$` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> s možností, shoda může dojít také na konci řádku. Všimněte `$` `\n` si, že `\r\n` odpovídá, ale neodpovídá (kombinace návratu vozíku a znaků nového řádku nebo CR/LF). Chcete-li shodovat kombinaci znaků CR/LF, zahrňte do `\r?$` vzoru regulárního výrazu.  
  
 Následující příklad přidá `$` kotvu do vzoru regulárního výrazu použitého v příkladu v části [Začátek řetězce nebo čáry.](#start-of-string-or-line-) Při použití s původním vstupním řetězcem, který <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> obsahuje pět řádků textu, metoda nemůže najít shodu, protože konec prvního řádku neodpovídá `$` vzoru. Pokud je původní vstupní řetězec rozdělen na <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> pole řetězců, metoda se podaří porovnat každý z pěti řádků. Pokud <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> je metoda volána s parametrem `options` nastaveným na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nejsou nalezeny žádné shody, protože vzor regulárního výrazu nezohledňuje prvek return u přepravy (\u+000D). Však při změně vzoru regulárního `\r?$`výrazu <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> nahrazením `options` `$` , <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> volání metody s parametrem nastavena znovu najde pět shody.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Jen za začátku řetězce: \A  
 Kotva `\A` určuje, že shoda musí dojít na začátku vstupního řetězce. Je totožný s `^` kotvou, <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> s tím rozdílem, že `\A` ignoruje možnost. Proto může odpovídat pouze začátek prvního řádku ve víceřádkovém vstupním řetězci.  
  
 Následující příklad je podobný příklady `^` pro `$` a kotvy. Používá kotvu `\A` v regulárním výrazu, který extrahuje informace o letech, během nichž existovaly některé profesionální baseballové týmy. Vstupní řetězec obsahuje pět řádků. Volání <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody vyhledá pouze první podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. Jak ukazuje příklad, <xref:System.Text.RegularExpressions.RegexOptions.Multiline> možnost nemá žádný vliv.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Na konci řetězce nebo před novým řádkem na konci řetězce: \Z  
 Kotva `\Z` určuje, že shoda musí dojít na konci vstupního řetězce nebo před `\n` na konci vstupního řetězce. Je totožný s `$` kotvou, <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> s tím rozdílem, že `\Z` ignoruje možnost. Proto ve víceřádkovém řetězci může odpovídat pouze konci posledního `\n`řádku nebo posledního řádku před .  
  
 Všimněte `\Z` `\n` si, že `\r\n` odpovídá, ale neodpovídá (kombinace znaků CR/LF). Chcete-li shodovat cr/LF, zahrňte `\r?\Z` do vzoru regulárního výrazu.  
  
 Následující příklad používá `\Z` kotvu v regulárním výrazu, který je podobný příkladu v části [Začátek řetězce nebo čáry,](#start-of-string-or-line-) která extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Dílčí výraz `\r?\Z` v regulárním výrazu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` odpovídá konci řetězce a `\n` také `\r\n`odpovídá řetězci, který končí řetězcem nebo . Výsledkem je, že každý prvek v poli odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Jen na konci řetězce: \z  
 Kotva `\z` určuje, že shoda musí dojít na konci vstupního řetězce. Stejně `$` jako `\z` prvek jazyka, ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost. Na `\Z` rozdíl od `\z` elementu `\n` jazyka neodpovídá znaku na konci řetězce. Proto může odpovídat pouze poslední řádek vstupní řetězec.  
  
 Následující příklad používá `\z` kotvu v regulárním výrazu, který je jinak totožný s příkladem v předchozí části, která extrahuje informace o letech, během kterých existovaly některé profesionální baseballové týmy. Příklad se pokusí porovnat každý z pěti prvků v `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`řetězcovém poli se vzorem regulárního výrazu . Dva řetězce končí znaky return carriage a line feed, jeden končí znakem posuvu řádku a dva končí ani návratem vozíku, ani znakem posuvu řádků. Jak ukazuje výstup, pouze řetězce bez konce řádku nebo znak uvozovek řádku odpovídají vzoru.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Souvislé porovnávání: \G  
 Kotva `\G` určuje, že shoda musí dojít v místě, kde skončila předchozí shoda. Při použití této <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> kotvy <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> s metodou nebo zajišťuje, že všechny shody jsou souvislé.  
  
 Následující příklad používá regulární výraz k extrahování názvů hlodavců z řetězce odděleného čárkou.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Regulární `\G(\w+\s?\w*),?` výraz je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začněte tam, kde skončila poslední shoda.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\s?`|Porovná nulu nebo jednu mezeru.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`(\w+\s?\w*)`|Porovná jeden nebo více znaků slova následovaných nulou nebo jednou mezerou následovanou nulou nebo více znaky slova. Toto je první zachytávající skupina.|  
|`,?`|Porovná nula nebo jeden výskyt znaku literálu čárky.|

## <a name="word-boundary-b"></a>Na hranici slova: \b  
 Kotva `\b` určuje, že shoda musí dojít na hranici `\w` mezi znakslova (prvek jazyka) `\W` a non-word znak (prvek jazyka). Znaky aplikace Word se skládají z alfanumerických znaků a podtržítek; znak bez slova je libovolný znak, který není alfanumerický nebo podtržítkem. (Další informace naleznete v [tématu Třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Shoda může dojít také na hranici slova na začátku nebo na konci řetězce.  
  
 Kotva se `\b` často používá k zajištění, že podvýraz odpovídá celé slovo namísto jen začátek nebo konec slova. Regulární `\bare\w*\b` výraz v následujícím příkladu ilustruje toto použití. Odpovídá jakékoli slovo, které začíná podřetězec "jsou". Výstup z příkladu také `\b` ukazuje, že odpovídá začátku i konci vstupního řetězce.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Vzor regulárního výrazu je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`are`|Porovná podřetězec "jsou".|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  

## <a name="non-word-boundary-b"></a>Mimo hranice slova: \B  
 Kotva `\B` určuje, že shoda nesmí dojít na hranici slova. Je to opak `\b` kotvy.  
  
 Následující příklad používá `\B` kotvu k vyhledání výskytů podřetězce "qu" ve slově. Vzor `\Bqu\w+` regulárního výrazu odpovídá podřetězci, který začíná řetězcem "qu", který nezakládá slovo a který pokračuje až do konce slova.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Vzor regulárního výrazu je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\B`|Nezačínejte shodu na hranici slova.|  
|`qu`|Porovná podřetězec "qu".|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
