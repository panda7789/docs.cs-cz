---
title: "Podrobnosti k chování regulárních výrazů"
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
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac5ddfb0ac7ae83537717e9bd0cd46eb629641fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="details-of-regular-expression-behavior"></a>Podrobnosti k chování regulárních výrazů
Modul regulárního výrazu rozhraní .NET Framework je navrácení regulární výraz objekt přiřazení vzorce která zahrnuje modul tradiční Nedeterministická konečné Automaton (NFA) jako je například použité Perl, Python, Emacs a Tcl. To je odlišné z rychlejší, ale omezenější, čistý regulární výraz moduly deterministický konečné Automaton (DFA) jako aplikace awk, egrep nebo lex. To je také odlišné od standardizované, ale pomalejší, k zařízení NFAs POSIX. Následující část popisuje tři typy modulů regulární výraz a vysvětluje, proč jsou regulární výrazy v rozhraní .NET Framework implementovaná pomocí modul tradiční NFA.  
  
## <a name="benefits-of-the-nfa-engine"></a>Výhody modulu NFA  
 Pokud moduly DFA provést porovnávání vzorů, jejich pořadí zpracování doprovází vstupní řetězec. Modul začne od začátku vstupní řetězec a pokračuje postupně k určení, zda další znak odpovídá regulární výraz. Se může zaručit tak, aby odpovídala nejdelší řetězec, který je možné. Vzhledem k tomu, že se nikdy otestovat ve stejném dvakrát, nepodporují DFA moduly zpětné navracení. Ale protože modul DFA obsahuje pouze konečný stav, nesmí se shodovat vzor s zpětné odkazy a protože není ji vytvořit explicitní rozšíření, nelze zachytit podvýrazy.  
  
 Na rozdíl od DFA weby když tradiční moduly NFA provést porovnávání vzorů jejich pořadí zpracování doprovází regulární výraz. Během zpracování elementu konkrétní jazyk, modul používá typu greedy odpovídající; To znamená odpovídá co nejvíc vstupní řetězec jako pravděpodobně můžete. Můžete ale také uloží stav po úspěšně odpovídající dílčím výrazu. Pokud odpovídající nakonec selže, modul, pokusí se použít další odpovídá vrátit do uloženého stavu. Zrušení úspěšné dílčím výrazu shody, aby souhlasila novější jazykové elementy v regulárním výrazu můžete také tento proces se označuje jako *zpětné navracení*. NFA moduly využívají zpětné navracení otestovat všechny možné rozšíření regulárního výrazu v určitém pořadí a přijmout na první shodu. Vzhledem k tomu, že modul tradiční NFA vytvoří konkrétní rozšíření regulárního výrazu shody úspěšné, můžete zaznamenat, odpovídá dílčím výrazu a odpovídající zpětné odkazy. Ale protože tradiční NFA provede krok zpět, je navštívit stejného stavu více než jednou. Pokud dorazí stav přes různé cesty. V důsledku toho může probíhat exponenciálnímu pomalu v nejhorším případě. Vzhledem k tomu, že modul tradiční NFA přijme první odpovídat ho najde, můžete také ponechat jiné (pravděpodobně delší) odpovídá nezjištěné.  
  
 POSIX NFA moduly jsou jako tradiční NFA moduly, s výjimkou toho, aby nadále zpětný krok, dokud se může zaručit, že jejich našli nejdelší shody možné. V důsledku toho modul POSIX NFA je nižší než tradiční modul NFA a pokud používáte modul POSIX NFA, nelze upřednostnit kratší shoda přes delší jeden změnou pořadí navrácení hledání.  
  
 Tradiční NFA moduly jsou podporuje programátory, protože nabízejí větší kontrolu nad řetězec odpovídající než DFA nebo POSIX NFA moduly. I když v nejhorším případě mohou spouštět pomalu, můžete řídit, je nalezení shody v čase lineární nebo polynomické pomocí vzorů, které snížit nejednoznačnosti a omezit zpětné navracení. Jinými slovy i když NFA moduly obchodu výkonu pro výkon a flexibilitu ve většině případů, které nabízejí pustit do přijatelný výkon, pokud regulární výraz je kvalitně a zabraňuje případy, kdy zpětné navracení snižuje výkon exponenciálně.  
  
> [!NOTE]
>  Informace o snížení výkonu kvůli nadměrné zpětné navracení a způsoby, jak vytvořit regulární výraz je obejít najdete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>Možnosti modulu .NET framework  
 Abyste mohli využívat výhod modul tradiční NFA, zahrnuje modul regulárního výrazu rozhraní .NET Framework kompletní sadu konstrukty, které umožňují řídit modul navrácení programátory v jazyce. Tyto konstrukce lze použít k vyhledání shody rychlejší nebo upřednostnit konkrétní rozšíření přes jiné.  
  
 Další funkce modulu regulárního výrazu rozhraní .NET Framework zahrnují následující:  
  
-   Líné kvantifikátory: `??`, `*?`, `+?`, `{`  *n*  `,` *m*`}?`. Tyto konstrukce řekněte modul navrácení nejprve hledání minimální počet opakování. Naproti tomu obyčejnou typu greedy kvantifikátory pokusit nejprve porovnat maximální počet opakování. Následující příklad ukazuje rozdíl mezi nimi. Regulární výraz odpovídá věty, které končí číslem a zaznamenávání skupiny slouží k extrakci toto číslo. Regulární výraz `.+(\d+)\.` zahrnuje typu greedy kvantifikátoru `.+`, což způsobí, že modul regulárních výrazů k zachycení pouze poslední číslice čísla. Naproti tomu regulární výraz `.+?(\d+)\.` zahrnuje opožděné kvantifikátoru `.+?`, což způsobí, že modul regulárních výrazů k zachycení celé číslo.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Verze typu greedy a opožděné tento regulární výraz jsou definovány, jak je znázorněno v následující tabulce. "  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`.+`(typu greedy kvantifikátoru)|Porovná alespoň jeden výskyt libovolného znaku. To způsobí, že modul regulárních výrazů tak, aby odpovídaly celý řetězec a pak zpětný krok jako potřeby tak, aby odpovídaly zbytek vzoru.|  
    |`.+?`(opožděné kvantifikátoru)|Porovná alespoň jeden výskyt libovolný znak, ale odpovídat co nejméně.|  
    |`(\d+)`|Odpovídají alespoň jeden znak číselné a přiřaďte ho ke skupině první zaznamenávání.|  
    |`\.`|Porovná tečku.|  
  
     Další informace o líné kvantifikátory najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Kladné s dopředným vyhledáváním: `(?=` *dílčím výrazu*`)`. Tato funkce umožňuje modul navrácení se vraťte do stejné pozici v textu po porovnávání dílčím výrazu. Je užitečné pro vyhledávání v celém textu kontrolou více vzorů, které začínají stejnou pozici. Také umožňuje, aby modul ověřte, zda je dílčí řetězec nachází na konci shody bez zahrnutí dílčí řetězec v odpovídající text. Následující příklad používá kladné s dopředným vyhledáváním pro extrahování slova ve větě, která nejsou následuje interpunkčních znamének.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Regulární výraz `\b[A-Z]+\b(?=\P{P})` je definovaný jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`[A-Z]+`|Porovná libovolný znak abecedy jeden či více krát. Protože <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možnost, porovnání nerozlišuje.|  
    |`\b`|Ukončí porovnání na hranici slova.|  
    |`(?=\P{P})`|Hledat k určení, zda další znak je symbol interpunkce. Pokud není, bude úspěšná shody.|  
  
     Další informace o kontrolní výrazy s dopředným vyhledáváním kladné najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Záporné s dopředným vyhledáváním: `(?!` *dílčím výrazu*`)`. Tato funkce přidává možnost tak, aby odpovídaly výrazu, pouze pokud selže dílčím výrazu tak, aby odpovídaly. To je zvláště efektivní pro vyřazování hledání, protože je často jednodušší zajistit výrazu pro případ, který by měly být odstraněny než výrazu v případech, kdy musí být zahrnut. Například je obtížné zápisu výrazu pro slova, která nemají na začátku "jiné". Následující příklad používá záporné s dopředným vyhledáváním z nich vyloučit.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Regulární výraz `\b(?!non)\w+\b` je definovaný jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`(?!non)`|Hledat zajistit, aby aktuálního řetězce nezačíná "jiné". Pokud ano, porovnání se nezdaří.|  
    |`(\w+)`|Porovná jeden nebo více znaků slova.|  
    |`\b`|Ukončí porovnání na hranici slova.|  
  
     Další informace o kontrolní výrazy s dopředným vyhledáváním záporné najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Podmíněné vyhodnocení: `(?(` *výraz*`)`*Ano*`|`*žádné* `)` a `(?(` *název*`)`*Ano*`|`*žádné*`)`, kde *výraz* je dílčím výrazu tak, aby odpovídaly, *název* je název zachycené skupiny, *Ano* je řetězec, který má splněno, pokud *výraz* je nalezena shoda nebo *název* je platný, neprázdný zaznamenané skupiny, a *žádné* dílčím výrazu pro porovnání, pokud je *výraz* neodpovídá nebo *název* není platné, prázdný zaznamenané skupiny. Tato funkce umožňuje modul pro vyhledávání pomocí více než jeden alternativní vzorek, v závislosti na výsledek předchozí shodě dílčím výrazu nebo výsledek assertion nulovou šířkou. To umožňuje výkonnější formu zpětných odkazů, která umožňuje například odpovídající dílčím výrazu založené na tom, jestli byl shodná předchozí dílčím výrazu. Odpovídá regulárnímu výrazu v následujícím příkladu odstavců, které jsou určeny pro veřejný i interní použití. Začínat odstavců určena pouze pro interní použití `<PRIVATE>` značky. Regulární výraz `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` používá podmíněného vyhodnocení přiřadit obsah odstavců určený pro veřejné a pro interní použití jednotlivé skupiny zachycení. Tyto odstavců můžete poté zpracovány jinak.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Začne porovnávání na začátku řádku.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Porovná nula nebo jeden výskyt řetězec `<PRIVATE>` následuje prázdný znak. Přiřadit shody zachycující skupiny s názvem `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Pokud `Pvt` zaznamenávání skupina existuje, porovná jeden nebo více výskytů jeden nebo více znaků slova následuje žádnou nebo jednu oddělovače interpunkce následuje prázdný znak. Dílčí řetězec přiřadíte ke skupině první zaznamenávání.|  
    |`&#124;((\w+\p{P}?\s)+))`|Pokud `Pvt` zachycující skupina neexistuje, shodovat s jedním nebo více výskytů jeden nebo více znaků slova následuje žádnou nebo jednu oddělovače interpunkce následuje prázdný znak. Dílčí řetězec přiřadíte ke skupině třetí zaznamenávání.|  
    |`\r?$`|Odpovídat konci řádku nebo konci řetězce.|  
  
     Další informace o vyhodnocení podmíněného najdete v tématu [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
-   Definice skupin vyrovnávání: `(?<` *name1*`-`*name2* `>` *dílčím výrazu*`)`. Tato funkce umožňuje modul regulárních výrazů ke sledování vnořené konstruktory, jako jsou závorky nebo levé a pravé závorky. Příklad, naleznete v části [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Bez mechanismu navrácení podvýrazy (také označované jako typu greedy podvýrazy): `(?>` *dílčím výrazu*`)`. Tato funkce umožňuje, aby navrácení modul zaručit, že dílčím výrazu odpovídá pouze na první shodu nalezeno pro tento dílčím výrazu, jako by byla spuštěna nezávislé jejího výrazu obsahujícího výraz. Pokud nepoužijete tento konstrukce, navrácení vyhledávání z větší výrazu můžete změnit chování dílčím výrazu. Například regulární výraz `(a+)\w` odpovídá jeden nebo více znaků "a, společně s word znak, který odpovídá pořadí znaků"a"a přiřadí posloupnost znaků"a"první zachycující skupiny, ale" pokud posledním znakem vstupní řetězec je také "a", it má odpovídající `\w` element jazyk, který není zahrnut ve skupině zaznamenané.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Regulární výraz `((?>a+))\w` brání toto chování. Protože všechny po sobě jdoucích znaků "a" se splní bez zpětné navracení, první zaznamenávání skupina zahrnuje všechny po sobě jdoucích znaků "a". Pokud znaků "a" nejsou následuje nejméně jeden znak více než "a", shody se nezdaří.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Další informace o bez mechanismu navrácení podvýrazy najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Doleva párování, který je určený zadáním <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> možnost k <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické odpovídající metodu instance. Tato funkce je užitečná při hledání zprava doleva místo zleva doprava nebo v případech, kdy je efektivnější zahájíte porovnávání na pravou část vzoru místo doleva. Jak ukazuje následující příklad, porovnáváním zprava doleva můžete změnit chování typu greedy kvantifikátory. V příkladu provede dvě vyhledá věty, které končí číslem. Vyhledávání zleva doprava, který používá typu greedy kvantifikátoru `+` odpovídá jednomu z šesti číslic ve větě, zatímco hledání zprava doleva odpovídá všech šest číslic. Popis regulární výraz podívejte se na příklad, který znázorňuje líné kvantifikátory dříve v této části.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Další informace o hledání shody zprava doleva najdete v tématu [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
-   Kladné a záporné zpětného vyhledávání: `(?<=` *dílčím výrazu* `)` pro pozitivní zpětného vyhledávání, a `(?<!` *dílčím výrazu* `)` pro negativního zpětného vyhledávání. Tato funkce je podobná dopředného vyhledávání, která je popsána dříve v tomto tématu. Vzhledem k tomu, že modul regulárních výrazů umožňuje dokončení odpovídající zprava doleva, regulární výrazy Povolit neomezené konstrukce lookbehind. Abyste se vyhnuli vnoření kvantifikátory při vnořené dílčím výrazu je nadmnožinou vnější výrazu se lze také kladné a záporné zpětného vyhledávání. Regulární výrazy se takový vnořené kvantifikátory často nabízejí snížený výkon. Například v následujícím příkladu ověřuje, že řetězec zahájení a ukončení alfanumerickým znakem a že další znak v řetězci je jednou z podmnožinu větší. Tvoří část regulární výraz používaný k ověření e-mailové adresy; Další informace najdete v tématu [postup: Ověřte, zda jsou řetězce v platném formátu e-mailu](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Regulární výraz `^[A-Z0-9]([-!#$%&'.*+/=?^`{} | ~ \w])* (? < = [A-Z0-9]) $"je definován, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Začne porovnávání na začátku řetězce.|  
    |`[A-Z0-9]`|Porovná libovolný znak číselné nebo alfanumerické znaky. (Porovnání se velká a malá písmena.)|  
    |`([-!#$%&'.*+/=?^`{} &#124; ~\w]) *.|Porovná nula nebo více výskytů libovolný znak, nebo libovolná z následujících znaků:-,!, #, $, % &,:,., *, +, /, =,?, ^, ', {,}, &#124; nebo ~.|  
    |`(?<=[A-Z0-9])`|Vyhledejte za předchozí znak, který musí být číselné nebo alfanumerické znaky. (Porovnání se velká a malá písmena.)|  
    |`$`|Ukončí porovnávání na konci řetězce.|  
  
     Další informace o kladné a záporné zpětného vyhledávání najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Poskytuje informace o tom, jak regulární výraz zpětné navracení větví najít alternativní shody.|  
|[Kompilace a opětovné používání](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Poskytuje informace o kompilace a opětovné použití regulárních výrazů pro zvýšení výkonu.|  
|[Bezpečnost vlákna](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Poskytuje informace o zabezpečení vlákna regulární výraz a vysvětluje, kdy bude třeba synchronizovat přístup k objektům regulární výraz.|  
|[Regulární výrazy rozhraní .NET framework](../../../docs/standard/base-types/regular-expressions.md)|Poskytuje přehled programovací jazyk aspektů regulární výrazy.|  
|[Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Poskytuje informace a příklady kódu znázorňující způsob použití třídy regulárních výrazů.|  
|[Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md)|Obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžné aplikace.|  
|[Jazyk regulárních výrazů – Stručná referenční příručka](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Poskytuje informace o sadě znaků, operátory a konstrukce, které můžete použít k definování regulární výrazy.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
