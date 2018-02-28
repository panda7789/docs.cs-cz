---
title: "Seskupovací konstrukce v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET Framework regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b9e54d8bbc9ca7cc9172fd83bd15968b3cef8e1
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="grouping-constructs-in-regular-expressions"></a>Seskupovací konstrukce v regulárních výrazech
Seskupovací konstrukce vymezují podvýrazy regulární výraz a zachycení podřetězce vstupní řetězce. Seskupovací konstrukce můžete provést následující akce:  
  
-   Odpovídat dílčím výrazu, který se opakuje ve vstupním řetězci.  
  
-   Použití kvantifikátoru na dílčím výrazu, který má více prvků jazyka regulárních výrazů. Další informace o kvantifikátory najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Zahrnout dílčím výrazu řetězec, který je vrácený <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody.  
  
-   Načíst jednotlivé podvýrazy z <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost a zpracovat je odděleně od odpovídajícího textu jako celek.  
  
 Následující tabulka uvádí seskupovací konstrukce nepodporuje modul regulárních výrazů .NET a určuje, zda jsou zaznamenání nebo jiných zachycení.  
  
|Seskupovací konstrukce|Zaznamenávání nebo bez zachycení|  
|------------------------|-------------------------------|  
|[Podvýrazy](#matched_subexpression)|Zaznamenání|  
|[S názvem podvýrazy](#named_matched_subexpression)|Zaznamenání|  
|[Vyrovnávání definice skupin](#balancing_group_definition)|Zaznamenání|  
|[Skupiny bez zachytávání](#noncapturing_group)|Bez zachycení|  
|[Možnosti pro skupiny](#group_options)|Bez zachycení|  
|[Kontrolní výrazy s nulovou šířkou kladné dopředným vyhledáváním](#zerowidth_positive_lookahead_assertion)|Bez zachycení|  
|[Kontrolní výrazy s nulovou šířkou záporné dopředným vyhledáváním](#zerowidth_negative_lookahead_assertion)|Bez zachycení|  
|[Kontrolní výrazy kladné zpětného vyhledávání s nulovou šířkou](#zerowidth_positive_lookbehind_assertion)|Bez zachycení|  
|[Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou](#zerowidth_negative_lookbehind_assertion)|Bez zachycení|  
|[Bez mechanismu navrácení podvýrazy](#nonbacktracking_subexpression)|Bez zachycení|  
  
 Informace o skupinách a model objektu regulárního výrazu, najdete v části [seskupovací konstrukce a objekty regulární výraz](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Podvýrazy  
 Následující seskupovací konstrukce zaznamená odpovídající dílčím výrazu:  
  
 `(` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor platný regulární výraz. Zaznamená, že používají závorky jsou automaticky číslována zleva doprava na základě pořadí počáteční závorky v regulárním výrazu, od jednoho. Zachycení, které je číslem nula je text odpovídající celý regulární výraz.  
  
> [!NOTE]
>  Ve výchozím nastavení `(` *dílčím výrazu* `)` jazyk element zaznamená odpovídající dílčím výrazu. Avšak v tom případě <xref:System.Text.RegularExpressions.RegexOptions> parametr vzor regulárního výrazu odpovídající metoda obsahuje <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> příznak, nebo, pokud `n` pro tento dílčím výrazu použije možnost (najdete v části [skupiny možnosti](#group_options) dál v tomto tématu), není zaznamenaná odpovídající dílčím výrazu.  
  
 Můžete získat přístup k zaznamenané skupinám čtyři způsoby:  
  
-   Pomocí zpětných odkazů vytvořte v rámci regulární výraz. Odpovídající dílčím výrazu je odkazován ve stejném regulárního výrazu pomocí syntaxe `\` *číslo*, kde *číslo* je řadová číslovka zaznamenané dílčím výrazu.  
  
-   Pomocí pojmenovaného zpětných odkazů vytvořte v rámci regulární výraz. Odpovídající dílčím výrazu je odkazován ve stejném regulárního výrazu pomocí syntaxe `\k<` *název*`>`, kde *název* je název zachycené skupiny, nebo `\k<` *číslo*`>`, kde *číslo* je řadová číslovka zachytávající skupiny. Zaznamenávání skupina má výchozí název, který je stejný jako jeho řadová číslovka. Další informace najdete v tématu [pojmenované odpovídající podvýrazy](#named_matched_subexpression) dál v tomto tématu.  
  
-   Pomocí `$` *číslo* nahrazení pořadí v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *číslo* je řadová číslovka zaznamenané dílčím výrazu.  
  
-   Programově pomocí <xref:System.Text.RegularExpressions.GroupCollection> objekt vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. Člen na pozici nula v kolekci představuje celý regulární výraz text. Každý následující člen představuje odpovídající dílčím výrazu. Další informace najdete v tématu [vytvoří seskupení a regulární výraz objekty](#Objects) části.  
  
 Následující příklad ukazuje regulární výraz, který identifikuje duplicitní slova v textu. Vzor regulárního výrazu dvě zaznamenávání skupiny představují dvě instance duplicitní slovo. Druhou instanci se zaznamená do sestavy jeho počáteční pozice ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Regulární výraz je následující:  
  
```  
(\w+)\s(\1)\W  
```  
  
 Následující tabulka ukazuje, jak interpretovat regulární výraz.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\1)`|Porovná řetězec v první zaznamenané skupinu. Toto je druhá zachytávající skupina. Příklad přiřadí ji k zaznamenané skupiny tak, aby počáteční pozici duplicitní aplikace word se dá načíst z `Match.Index` vlastnost.|  
|`\W`|Porovná znak aplikace word, včetně mezer a interpunkce. Regulární výraz zabrání odpovídající aplikace word, který začíná slovem z první zaznamenané skupiny.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>S názvem podvýrazy  
 Následující seskupovací konstrukce zaznamená odpovídající dílčím výrazu a umožňuje přístup pomocí názvu nebo podle čísla:  
  
```  
(?<name>subexpression)  
```  
  
 nebo:  
  
```  
(?'name'subexpression)  
```  
  
 kde *název* je název skupiny platný, a *dílčím výrazu* je libovolný vzor platný regulární výraz. *název* nesmí obsahovat znaky interpunkce a nesmí začínat číslem.  
  
> [!NOTE]
>  Pokud <xref:System.Text.RegularExpressions.RegexOptions> parametr vzor regulárního výrazu odpovídající metoda zahrnuje <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> příznak, nebo pokud `n` pro tento dílčím výrazu použije možnost (najdete v části [skupiny možnosti](#group_options) dál v tomto tématu), jediný způsob, jak zachytit dílčím výrazu je explicitně název skupiny zachycení.  
  
 Pojmenované zachycené skupiny se můžete dostat následujícími způsoby:  
  
-   Pomocí pojmenovaného zpětných odkazů vytvořte v rámci regulární výraz. Odpovídající dílčím výrazu je odkazován ve stejném regulárního výrazu pomocí syntaxe `\k<` *název*`>`, kde *název* je název zaznamenané dílčím výrazu.  
  
-   Pomocí zpětných odkazů vytvořte v rámci regulární výraz. Odpovídající dílčím výrazu je odkazován ve stejném regulárního výrazu pomocí syntaxe `\` *číslo*, kde *číslo* je řadová číslovka zaznamenané dílčím výrazu. Pojmenované podvýrazy jsou číslována za sebou zleva doprava po podvýrazy.  
  
-   Pomocí `${` *název* `}` nahrazení pořadí v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *název* je název zaznamenané dílčím výrazu.  
  
-   Pomocí `$` *číslo* nahrazení pořadí v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *číslo* je řadová číslovka zaznamenané dílčím výrazu.  
  
-   Programově pomocí <xref:System.Text.RegularExpressions.GroupCollection> objekt vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. Člen na pozici nula v kolekci představuje celý regulární výraz text. Každý následující člen představuje odpovídající dílčím výrazu. Pojmenované zachycené skupiny jsou uloženy v kolekci po číslovaných zachycených skupinách.  
  
-   Prostřednictvím kódu programu, tím, že poskytuje název dílčím výrazu, který má <xref:System.Text.RegularExpressions.GroupCollection> indexeru objektu (v jazyku C#) nebo jeho <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> vlastnost (v jazyce Visual Basic).  
  
 Jednoduché regulárního výrazu ukazuje, jak číslované (bez názvu) a s názvem skupiny může být odkazováno buď programově, nebo pomocí syntaxe jazyka regulární výraz. Regulární výraz `((?<One>abc)\d+)?(?<Two>xyz)(.*)` vytváří následující zaznamenávání seskupeny podle čísla a podle názvu. První vždy zaznamenávání skupiny (číslo 0) odkazuje na celý vzor.  
  
|Číslo|Název|Vzor|  
|------------|----------|-------------|  
|0|0 (výchozí název)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (výchozí název)|`((?<One>abc)\d+)`|  
|2|2 (výchozí název)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|dvě|`(?<Two>xyz)`|  
  
 Následující příklad ukazuje regulární výraz, který identifikuje duplicitní slova a Wordu, který následuje jednotlivých slov duplicitní. Regulární výraz definuje dva pojmenované podvýrazy: `duplicateWord`, která představuje duplicitní slovo; a `nextWord`, která představuje slovo následující duplicitní slovo.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Regulární výraz je následující:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 Následující tabulka ukazuje, jak interpretovat regulární výraz.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Porovná jeden nebo více znaků slova. Název této skupiny zaznamenávání `duplicateWord`.|  
|`\s`|Porovná prázdný znak.|  
|`\k<duplicateWord>`|Shoda s řetězcem z zaznamenané skupiny, který je pojmenován `duplicateWord`.|  
|`\W`|Porovná znak aplikace word, včetně mezer a interpunkce. Regulární výraz zabrání odpovídající aplikace word, který začíná slovem z první zaznamenané skupiny.|  
|`(?<nextWord>\w+)`|Porovná jeden nebo více znaků slova. Název této skupiny zaznamenávání `nextWord`.|  
  
 Všimněte si, že název skupiny můžete opakovat v regulárním výrazu. Například je možné pro více než jednu skupinu s názvem `digit`, jak ukazuje následující příklad. V případě duplicitní názvy, hodnota <xref:System.Text.RegularExpressions.Group> objektu je dáno poslední úspěšné zachycení ve vstupním řetězci. Kromě toho <xref:System.Text.RegularExpressions.CaptureCollection> se zobrazí informace o jednotlivých zachycení v stejně, jako by bylo, pokud nebyla duplicitní název skupiny.  
  
 V následujícím příkladu, regulární výraz `\D+(?<digit>\d+)\D+(?<digit>\d+)?` obsahuje dva výskyty skupinu s názvem `digit`. První `digit` s názvem skupiny zachycení jeden nebo více znaků, číslic. Druhý `digit` pojmenovanou skupinu zaznamená buď nula nebo jeden výskyt jeden nebo více znaků, číslic. Jako výstup ukazuje příklad, pokud druhý zaznamenávání skupiny úspěšně odpovídá textu, hodnota tohoto textu definuje hodnotu <xref:System.Text.RegularExpressions.Group> objektu. Pokud nelze druhé zachytávající skupině neodpovídá vstupní řetězec, hodnota poslední úspěšné shodě definuje hodnotu <xref:System.Text.RegularExpressions.Group> objektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Následující tabulka ukazuje, jak interpretovat regulární výraz.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\D+`|Porovná jeden nebo více znaků není desítková číslice.|  
|`(?<digit>\d+)`|Porovná jeden nebo více znaků desítková číslice. Shoda pro přiřazení `digit` s názvem skupiny.|  
|\D+|Porovná jeden nebo více znaků není desítková číslice.|  
|`(?<digit>\d+)?`|Porovná nula nebo jeden výskyt jeden nebo více znaků desítková číslice. Shoda pro přiřazení `digit` s názvem skupiny.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Vyrovnávání definice skupin  
 Vyrovnávání definice skupiny odstraní definici dříve definované skupiny a úložiště v aktuální skupině, interval mezi dříve definované skupiny a aktuální skupiny. Tato seskupovací konstrukce má následující formát:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 nebo:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 kde *name1* je daná skupina (volitelné), *name2* je dříve definovaný skupina, a *dílčím výrazu* je libovolný vzor platný regulární výraz. Seskupovací definice odstraní definici *name2* a uloží interval mezi *name2* a *name1* v *name1*. Pokud žádné *name2* skupina je definována, provede krok zpět na shodu. Protože odstranění poslední definice *name2* ukáže předchozí definici *name2*, tato konstrukce umožňuje použití zásobníku zachycení pro skupinu *name2* jako Čítač pro udržování přehledu o vnořené konstruktory, jako jsou závorky nebo levé a pravé závorky.  
  
 Seskupovací definice používá *name2* jako zásobník. Počáteční znak jednotlivých vnořených konstrukcí je umístěn ve skupině a v jeho <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce. Pokud je nalezena shoda ukončovací znak, jeho odpovídající počáteční znak je odebrán ze skupiny a <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekce je snížila o jednu. Po počátečních a koncových znaků všech vnořených konstrukcí, *name1* je prázdný.  
  
> [!NOTE]
>  Po úpravě regulárnímu výrazu v následujícím příkladu k použití vhodného počátečního a koncového znaku vnořené konstrukce, můžete ji použít pro zpracování nejvíce vnořené konstrukce, jako je například matematické výrazy nebo řádky kódu programu, které obsahují více vnořených volání metod.  
  
 Následující příklad používá vyrovnávání definice skupiny tak, aby odpovídaly v levém horním a pravém úhlu závorky (<>) ve vstupním řetězci. V příkladu jsou definovány dvě skupiny s názvem `Open` a `Close`, které se používají jako zásobníky pro sledování odpovídající dvojice ostrých závorek. Každý zaznamenané levou hranatou závorku je vložena do kolekce zachycení `Open` skupiny a každý zaznamenané pravém úhlu závorka je vložena do kolekce zachycení `Close` skupiny. Seskupovací definice zajišťuje, že odpovídající práva lomená závorka pro každou levou hranatou závorku. Pokud není k dispozici, konečný dílčí vzor `(?(Open)(?!))`, vyhodnotí pouze v případě `Open` není prázdná (a tedy bylo ukončeno Pokud všechny vnořené konstrukce). Pokud vyhodnotí konečný dílčí vzor shody selže, protože `(?!)` dílčí vzor je negativního nulovou šířkou dopředného vyhledávání, který vždycky selže.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Regulární výraz je:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Regulární výraz je interpretována takto:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začít na začátku řetězce.|  
|`[^<>]*`|Odpovídat nula nebo více znaků, které nejsou doleva nebo doprava úhel závorky.|  
|`(?'Open'<)`|Odpovídající levou hranatou závorku a přiřaďte ho do skupiny s názvem `Open`.|  
|`[^<>]*`|Odpovídat nula nebo více znaků, které nejsou doleva nebo doprava úhel závorky.|  
|`((?'Open'<)[^<>]*) +`|Porovná jeden nebo více výskytů levou hranatou závorku následované nula nebo více znaků, které nejsou doleva nebo doprava úhel závorky. Toto je druhá zachytávající skupina.|  
|`(?'Close-Open'>)`|Shodují pravé ostré závorky, přiřadí podřetězec mezi `Open` skupinu a na aktuální skupinu `Close` skupiny a odstranit definici `Open` skupiny.|  
|`[^<>]*`|Porovná nula nebo více výskytů libovolný znak, který není pravé ostré závorky ani levé straně.|  
|`((?'Close-Open'>)[^<>]*)+`|Porovná jeden nebo více výskytů pravé ostré závorky, za nímž následuje nula nebo více výskytů libovolný znak, který není levou ani vpravo lomená závorka. Při porovnání pravé ostré závorky, přiřadí podřetězec mezi `Open` skupinu a na aktuální skupinu `Close` skupiny a odstranit definici `Open` skupiny. Toto je třetí zachytávající skupina.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Porovná nula nebo více výskytů následující vzor: jeden nebo více výskytů levou hranatou závorku, za nímž následuje nula nebo více znaků lomená závorka, za nímž následuje jeden nebo více výskytů pravé ostré závorky, za nímž následuje nula nebo více výskytů není lomené závorky. Při porovnání pravé ostré závorky, odstranit definici `Open` a přiřadí podřetězec mezi `Open` skupinu a na aktuální skupinu `Close` skupiny. Toto je první zachytávající skupina.|  
|`(?(Open)(?!))`|Pokud `Open` skupina existuje, zrušte shody, pokud je možné přiřadit prázdný řetězec, ale není posunutí pozice modul regulárních výrazů v řetězci. Toto je nulovou šířkou záporné dopředného vyhledávání. Protože prázdný řetězec se vždy implicitně nachází ve vstupní řetězec, toto porovnání se vždy nezdaří. Selhání této odpovídal naznačuje, že ostré závorky nejsou spárovány.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Poslední dílčím výrazu, `(?(Open)(?!))`, označuje, zda jsou vnořené konstrukce v vstupní řetězec správně rozloženy (například zda každý levou hranatou závorku má odpovídající práva ostré závorky). Pomocí podmíněného porovnávání na základě platný zaznamenané skupiny; Další informace najdete v tématu [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Pokud `Open` skupina je definována, modul regulárních výrazů se pokusí o porovnání dílčí výraz `(?!)` ve vstupním řetězci. `Open` Skupiny by měl být definován, pouze v případě, že jsou vnořené konstrukce nevyrovnané. Vzor pro porovnání ve vstupním řetězci proto musí být ten, který vždy způsobí selhání porovnávání. V takovém případě `(?!)` je nulovou šířkou záporné dopředného vyhledávání to vždy selže, protože prázdný řetězec se vždy implicitně nachází na další pozici ve vstupním řetězci.  
  
 V příkladu modul regulárních výrazů vyhodnotí vstupní řetězec "\<abc >< mno\<xyz >>" jak je znázorněno v následující tabulce.  
  
|Krok|Vzor|Výsledek|  
|----------|-------------|------------|  
|1|`^`|Spustí na shodu na začátku vstupní řetězec|  
|2|`[^<>]*`|Vyhledá lomená závorka znaků před levou hranatou závorku; vyhledá žádné odpovídající položky.|  
|3|`(((?'Open'<)`|Odpovídá levé ostré závorky v "\<abc >" a přiřadí ji k `Open` skupiny.|  
|4|`[^<>]*`|Odpovídá "abc".|  
|5|`)+`|"< abc" je hodnota druhý zaznamenané skupiny.<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět `(?'Open'<)[^<>]*)` dílčího vzoru.|  
|6|`((?'Close-Open'>)`|Odpovídá pravé ostré závorky v "\<abc >", přiřadí "abc", která je dílčí řetězec mezi `Open` skupiny a pravém úhlu závorka k `Close` skupiny a odstraní aktuální hodnotu ("<") z `Open` skupiny, ponechat prázdné.|  
|7|`[^<>]*`|Vyhledá lomená závorka znaků po pravé ostré závorky; Vyhledá žádné odpovídající položky.|  
|8|`)+`|Hodnota třetí zaznamenané skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravé ostré závorky, takže modul regulárních výrazů neskočí zpět `((?'Close-Open'>)[^<>]*)` dílčího vzoru.|  
|9|`)*`|Hodnota první zaznamenané skupinu je "\<abc >".<br /><br /> Další znak ve vstupním řetězci je levou hranatou závorku, takže modul regulárních výrazů v cyklu zpět `(((?'Open'<)` dílčího vzoru.|  
|10|`(((?'Open'<)`|Odpovídá levé ostré závorky v "\<mno >" a přiřadí ji k `Open` skupiny. Jeho <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce nyní obsahuje jednu hodnotu, "<".|  
|11|`[^<>]*`|Porovná "mno".|  
|12|`)+`|"< mno" je hodnota druhý zaznamenané skupiny.<br /><br /> Následující znak ve vstupním řetězci je levou hranatou závorku, takže modul regulárních výrazů v cyklu zpět `(?'Open'<)[^<>]*)` dílčího vzoru.|  
|13|`(((?'Open'<)`|Odpovídá levé ostré závorky v "\<xyz >" a přiřadí ji k `Open` skupiny. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Kolekce `Open` skupiny teď obsahuje dvě zachycení: levou hranatou závorku z "\<mno >" a levou hranatou závorku z "\<xyz >".|  
|14|`[^<>]*`|Porovná "xyz".|  
|15|`)+`|"< xyz" je hodnota druhý zaznamenané skupiny.<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět `(?'Open'<)[^<>]*)` dílčího vzoru.|  
|16|`((?'Close-Open'>)`|Odpovídá pravé ostré závorky v "\<xyz >". "xyz", přiřadí podřetězec mezi `Open` skupiny a pravém úhlu závorka k `Close` skupiny a odstraní aktuální hodnota `Open` skupiny. Hodnota předchozího zachycení (levé ostré závorky v "\<mno >") se změní na aktuální hodnota `Open` skupiny. <xref:System.Text.RegularExpressions.Group.Captures%2A> Kolekce `Open` skupiny nyní obsahuje jediné zachycení, levou hranatou závorku z "\<xyz >".|  
|17|`[^<>]*`|Vyhledá lomená závorka znaků; Vyhledá žádné odpovídající položky.|  
|18|`)+`|Hodnota třetí zaznamenané skupiny je ">".<br /><br /> Následující znak ve vstupním řetězci je pravé ostré závorky, takže modul regulárních výrazů v cyklu zpět `((?'Close-Open'>)[^<>]*)` dílčího vzoru.|  
|19|`((?'Close-Open'>)`|Odpovídá posledním pravé ostré závorky v "xyz >>", přiřadí "mno\<xyz >" (podřetězec mezi `Open` skupiny a pravé ostré závorky) k `Close` skupiny a odstraní aktuální hodnota `Open` skupiny. `Open` Skupina je teď prázdná.|  
|20|`[^<>]*`|Vyhledá lomená závorka znaků; Vyhledá žádné odpovídající položky.|  
|21|`)+`|Hodnota třetí zaznamenané skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravé ostré závorky, takže modul regulárních výrazů neskočí zpět `((?'Close-Open'>)[^<>]*)` dílčího vzoru.|  
|22|`)*`|Hodnotu první zaznamenané skupinu "< mno\<xyz >>".<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět `(((?'Open'<)` dílčího vzoru.|  
|23|`(?(Open)(?!))`|`Open` Skupiny není definována, takže dojde k pokusu o žádná shoda.|  
|24|`$`|Odpovídá konci vstupní řetězec.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Skupiny bez zachytávání  
 Následující seskupovací konstrukce nezachytává dílčí řetězec, který má odpovídající dílčím výrazu:  
  
```  
(?:subexpression)  
```  
  
 kde *dílčím výrazu* je libovolný vzor platný regulární výraz. Seskupovací konstrukce se obvykle používá, když kvantifikátoru do skupiny, ale jsou podřetězce zachycené skupinou nejsou důležité.  
  
> [!NOTE]
>  Obsahuje-li regulární výraz vnořené seskupovací konstrukce, vnější seskupovací konstrukce se nevztahuje na vnořené seskupovací konstrukce.  
  
 Následující příklad ukazuje regulární výraz, který obsahuje skupiny bez zachytávání. Všimněte si, že výstup neobsahuje žádné zaznamenané skupiny.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Regulární výraz `(?:\b(?:\w+)\W*)+\.` odpovídá větě, která je ukončen tečkou. Protože regulární výraz se zaměřuje na věty, nikoli na jednotlivých slov, seskupovací konstrukce jsou používány výhradně jako kvantifikátory. Regulární výraz interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?:\w+)`|Porovná jeden nebo více znaků slova. Nepřiřazujte odpovídající text do zaznamenané skupiny.|  
|`\W*`|Porovná nula nebo více znaků aplikace word.|  
|`(?:\b(?:\w+)\W*)+`|Odpovídat vzor jeden nebo více znaků slova začínající na hranici slova, za nímž následuje nula nebo více znaků aplikace word, jeden či více krát. Nepřiřazujte odpovídající text do zaznamenané skupiny.|  
|`\.`|Porovná tečku.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Možnosti pro skupiny  
 Následující seskupovací konstrukce použije nebo zakáže zadané možnosti v rámci dílčím výrazu:  
  
 `(?imnsx-imnsx:` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor platný regulární výraz. Například `(?i-s:)` zapne nerozlišování a zakáže režim jeden řádek. Další informace o vložených možností můžete určit, najdete v části [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Můžete zadat možnosti, které platí pro celý regulární výraz, nikoli dílčím výrazu pomocí <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru nebo statické metody třídy. Můžete také určit vnitřní možnosti, které platí po určitém bodě v regulárním výrazu pomocí `(?imnsx-imnsx)` konstrukce jazyka.  
  
 Konstrukce možnosti skupiny není skupinu zachycení. To znamená i když jakékoli její části řetězec, který je zachycen *dílčím výrazu* se dodává se shodují, není zahrnuta ve skupině zaznamenané ani používaných k naplnění <xref:System.Text.RegularExpressions.GroupCollection> objektu.  
  
 Například regulární výraz `\b(?ix: d \w+)\s` v následujícím příkladu používá vložených možností v seskupovací konstrukce k povolení porovnávání a Ignorovat prázdné vzor při identifikaci všech slov, která začínají znakem "d". Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?ix: d \w+)`|Pomocí velká a malá písmena a ignorování mezer v tomto vzoru, shodovat s "d" následuje jeden nebo více znaků slova.|  
|`\s`|Porovná prázdný znak.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Kontrolní výrazy s nulovou šířkou kladné dopředným vyhledáváním  
 Následující seskupovací konstrukce definuje nulovou šířkou kladné dopředného vyhledávání:  
  
 `(?=` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor regulárního výrazu. Pro úspěšné porovnání, vstupní řetězec musí odpovídat vzor regulárního výrazu v *dílčím výrazu*, i když odpovídající podřetězec není zahrnut ve výsledku porovnání. Nulovou šířkou kladné dopředného vyhledávání není zpětný krok.  
  
 Nulovou šířkou kladné dopředného vyhledávání se obvykle nachází na konci vzor regulárního výrazu. Definuje dílčí řetězec, který musí být nalezen na konci řetězce pro porovnání dojít, ale které by neměly být obsažené v shody. Je také užitečné brání nadměrné zpětné navracení. Nulovou šířkou kladné dopředného vyhledávání můžete použít k zajištění, že do určité skupiny zaznamenané začíná text, který odpovídá podmnožinu vzoru definované pro tuto skupinu zaznamenané. Například pokud skupinu zachycení odpovídá znaků po sobě jdoucí slova, můžete nulovou šířkou kladné dopředného vyhledávání vyžadují, aby první znak abecední velké písmeno.  
  
 Následující příklad používá nulovou šířkou kladné dopředného vyhledávání tak, aby odpovídaly slovo, které předchází příkaz "je" ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Regulární výraz `\b\w+(?=\sis\b)` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(?=\sis\b)`|Určete, jestli znaků slova jsou následuje prázdné znaky a řetězce "je", který končí na hranici slova. Pokud ano, je úspěšný shody.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Kontrolní výrazy s nulovou šířkou záporné dopředným vyhledáváním  
 Následující seskupovací konstrukce definuje výraz negativního dopředného vyhledávání s nulovou šířkou:  
  
 `(?!` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor regulárního výrazu. Pro úspěšné porovnání vstupní řetězec nesmí odpovídat vzor regulárního výrazu v *dílčím výrazu*, i když odpovídající řetězec není součástí výsledku porovnání.  
  
 Nulovou šířkou záporné dopředného vyhledávání se obvykle používá na začátku nebo na konci regulární výraz. Na začátku regulární výraz se může definovat konkrétní vzor, který by neměly odpovídat při začátku regulární výraz definuje podobně jako u ale obecnější vzor pro porovnání. V takovém případě se často používá k omezení zpětné navracení. Na konci regulární výraz se může definovat dílčím výrazu, který se nemůže vyskytovat na konci shody.  
  
 V následujícím příkladu definuje regulární výraz, který používá dopředného vyhledávání nulovou šířkou na začátku regulárního výrazu tak, aby odpovídaly slova, která nemají na začátku "zrušení".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Regulární výraz `\b(?!un)\w+\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?!un)`|Určení, zda jsou následující dva znaky "zrušení". Pokud tomu tak není, je možné shody.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 V následujícím příkladu definuje regulární výraz, který používá dopředného vyhledávání nulovou šířkou na konci regulární výraz k přiřazení slova, která na konci interpunkční znaménko.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Regulární výraz `\b\w+\b(?!\p{P})` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`\p{P})`|Pokud další znak není interpunkční symbol (například období nebo čárkou), bude úspěšná shody.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Kontrolní výrazy kladné zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje výraz kladné zpětného vyhledávání s nulovou šířkou:  
  
 `(?<=` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor regulárního výrazu. Pro úspěšné, porovnání *dílčím výrazu* musí objevit ve vstupním řetězci nalevo od aktuální pozice, přestože `subexpression` není zahrnut ve výsledku porovnání. Kladné zpětného vyhledávání s nulovou šířkou kontrolní mechanismus navrácení.  
  
 Kontrolní výrazy kladné zpětného vyhledávání s nulovou šířkou jsou obvykle používány na začátku regulární výrazy. Vzor, který definují je předpokladem pro shodu, i když není součástí výsledku porovnání.  
  
 Například v následujícím příkladu odpovídá poslední dvě číslice roku pro 21 dvacet (to znamená, že číslice "20" předcházet odpovídající řetězec).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Regulární výraz `(?<=\b20)\d{2}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\d{2}`|Porovná dvě desítková číslice.|  
|`{?<=\b20)`|Pokračujte shody, pokud dva desetinných míst předchází desetinných míst "20" na hranici slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Kontrolní výrazy kladné zpětného vyhledávání s nulovou šířkou se taky používají k omezení zpětné navracení při poslední znak nebo znaky ve skupině zaznamenané musí být podmnožinou znaky, které odpovídají vzor regulárního výrazu této skupiny. Například pokud skupinu zaznamená všechny aplikace word po sobě jdoucí znaky, můžete výraz kladné zpětného vyhledávání s nulovou šířkou vyžadují, aby jeho poslední znak abecední.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje výraz negativního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<!` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor regulárního výrazu. Pro úspěšné, porovnání *dílčím výrazu* nesmí vyskytovat ve vstupním řetězci nalevo od aktuální pozici. Ale jakýkoli podřetězec, který neodpovídá `subexpression` není zahrnut ve výsledku porovnání.  
  
 Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou jsou obvykle používány na začátku regulární výrazy. Vzor, který definují vylučuje porovnávání řetězce, který následuje. Používají se také omezit zpětné navracení při poslední znak nebo znaky ve skupině zaznamenané nesmí být jeden nebo více znaků, které odpovídají vzor regulárního výrazu této skupiny. Například pokud skupinu zaznamená všechny aplikace word po sobě jdoucí znaky, můžete výraz kladné zpětného vyhledávání s nulovou šířkou vyžadují, aby jeho poslední znak není podtržítko (_).  
  
 Následující příklad odpovídá datum pro všechny den v týdnu, který není víkendu (to znamená, že je sobota ani neděle).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Regulární výraz `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova, za nímž následuje prázdný znak.|  
|`\d{1,2},`|Odpovídat jedna nebo dvě desetinných míst následovaný prázdným znakem a čárkou.|  
|`\d{4}\b`|Odpovídající čtyři desetinných míst a ukončí porovnávání na hranici slova.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Pokud je shoda předchází něco jiného než řetězce "Sobota" nebo "Neděle" následované mezerou, porovnávání je úspěšné.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Bez mechanismu navrácení podvýrazy  
 Následující seskupovací konstrukce představuje podvýraz (také označované jako "chamtivého" dílčím výrazu):  
  
 `(?>` *subexpression* `)`  
  
 kde *dílčím výrazu* je libovolný vzor regulárního výrazu.  
  
 Normálně Pokud regulární výraz zahrnuje volitelný nebo alternativní odpovídající vzorek a porovnávání neproběhne úspěšně, můžete v několika směrech tak, aby odpovídaly vstupní řetězec pomocí vzoru větev modul regulárních výrazů. Pokud není nalezena shoda při přepínání první větve, můžete modul regulárních výrazů zálohovat nebo navrátit do místa, kde došlo na první shodu a pokus shody pomocí druhé větve. Tento proces může pokračovat, dokud všechny větve mají nebyl proveden pokus o.  
  
 `(?>` *Dílčím výrazu* `)` jazyková konstrukce zakáže mechanismus navrácení. Modul regulárních výrazů bude odpovídat tolik znaků ve vstupním řetězci, jak je to možné. Pokud žádné další shody je možné, nebude zpětný krok k pokusu o alternativní vzor shody. (To znamená, dílčí výraz odpovídá pouze řetězce, které by odpovídat samostatně dílčím výrazu, se nebude pokoušet o porovnání řetězce na základě dílčí výraz a všechny podvýrazy, které následují ji.)  
  
 Tato možnost se doporučuje, když víte, že zpětné navracení se nezdaří. Modul regulárních výrazů brání v provádění zbytečného hledání zvyšuje výkon.  
  
 Následující příklad ilustruje, jak podvýraz upraví výsledky vzor shody. Navrácení regulární výraz úspěšně odpovídá řadu opakovaných znaky následované více výskytů stejného znaku na hranici slova, ale nemá bez mechanismu navrácení regulární výraz.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Bez mechanismu navrácení regulární výraz `(?>(\w)\1+).\b` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w)`|Porovná znak jednoho slova a přiřaďte ho ke skupině první zaznamenávání.|  
|`\1+`|Odpovídají hodnotě první zachycený podřetězec jeden či více krát.|  
|`.`|Porovná libovolný znak.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`(?>(\w)\1+)`|Porovná jeden nebo více výskytů znak duplicitní slova, ale nevrací se tak, aby odpovídala poslední znak na hranici slova.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Seskupovací konstrukce a objekty regulární výraz  
 Podřetězce, které jsou porovnávány regulárním výrazem zaznamenávání skupiny jsou reprezentované pomocí <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> objekty, které můžete získat z <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> objekt, který je vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.GroupCollection> Objektu je naplněn takto:  
  
-   První <xref:System.Text.RegularExpressions.Group> objekt v kolekci (objekt v indexu nula) představuje celou shodu.  
  
-   Další sada <xref:System.Text.RegularExpressions.Group> objekty představuje nepojmenované (číslované) zachytávající skupiny. Zobrazí se v pořadí, ve kterém jsou definovány v regulárním výrazu zleva doprava. Index hodnoty těchto skupin rozsahu od 1 do počet nepojmenované zaznamenání skupin v kolekci. (Index určité skupiny je ekvivalentní k jeho číslem zpětných odkazů. Zpětné odkazy na další informace najdete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
-   Konečné sada <xref:System.Text.RegularExpressions.Group> objekty představuje pojmenované zachytávající skupiny. Zobrazí se v pořadí, ve kterém jsou definovány v regulárním výrazu zleva doprava. Hodnota indexu první pojmenované zachytávající skupiny je větší než index poslední nepojmenované zachytávající skupiny. Pokud neexistují žádné nepojmenované zachytávající skupiny v regulárním výrazu, je hodnota indexu první pojmenované zachytávající skupiny jeden.  
  
 Pokud použijete kvantifikátor zachycené skupiny, odpovídající <xref:System.Text.RegularExpressions.Group> objektu <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, a <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> vlastnosti vyjadřují poslední podřetězec zachycenou skupinu zachycení. Můžete načíst kompletní sadu dílčích řetězců, které jsou zachyceny skupiny, které mají kvantifikátory z <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost.  
  
 Následující příklad vysvětluje vztah mezi <xref:System.Text.RegularExpressions.Group> a <xref:System.Text.RegularExpressions.Capture> objekty.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Regulární výraz `\b(\w+)\W+)+` extrahuje jednotlivých slov v řetězci. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Tyto znaky společně tvoří slovo. Toto je druhá zachytávající skupina.|  
|`\W+`|Odpovídat jeden nebo více znaků aplikace word.|  
|`(\w+)\W+)+`|Shodují se vzorem jeden nebo více znaků slova následuje jeden nebo více mimo slovo znaků jeden či více krát. Toto je první zachytávající skupina.|  
  
 První skupinu zaznamenávání odpovídá jednotlivých slov věty. Druhá zachytávající skupina odpovídá jednotlivých slov spolu s interpunkce a prázdné znaky, které budou následovat slovo. <xref:System.Text.RegularExpressions.Group> Objekt, jehož index je 2 poskytuje informace o text odpovídající druhé zachytávající skupině. Kompletní sadu slov zachycených zachytávající skupině jsou k dispozici na <xref:System.Text.RegularExpressions.CaptureCollection> objekt vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
