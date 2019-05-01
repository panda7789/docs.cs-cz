---
title: Podrobnosti k chování regulárních výrazů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4d8fdc39153f227e8344ea1da52a0dba2688d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955956"
---
# <a name="details-of-regular-expression-behavior"></a>Podrobnosti k chování regulárních výrazů
Modul regulárních výrazů rozhraní .NET Framework je navracení předávaný regulární výraz, který zahrnuje modul tradiční Nedeterministická Finite Automaton (NFA) jako, který používá Perl, Python, (emacs) a Tcl je. To která ho odlišuje od rychleji, ale moduly Deterministické omezené Automaton (DFA) omezenější, čistý regulární výraz například výstrahám nacházejícím se v awk, egrep nebo lex. To také která ho odlišuje od standardizované, ale pomalejší, k zařízení NFAs POSIX. Následující část popisuje tři typy strojů regulárních výrazů a vysvětluje, proč jsou regulární výrazy v rozhraní .NET Framework implementovat pomocí tradičních modulem NFA.  
  
## <a name="benefits-of-the-nfa-engine"></a>Výhody modulem NFA  
 Když DFA moduly provádění porovnávání vzorů, jejich pořadí zpracování stanovených ve vstupním řetězci. Modul začne na začátku vstupního řetězce a postupně pokračuje k určení, zda další znak odpovídá vzoru regulárního výrazu. Se může zaručit tak, aby odpovídaly nejdelší řetězec je to možné. Vzhledem k tomu, že nikdy otestovat ve stejném dvakrát, DFA moduly nepodporuje používání mechanismu navracení. Ale protože DFA modul obsahuje pouze omezené stavu, nelze porovnání vzoru se zpětnými odkazy a protože ji nelze vytvořit explicitní rozšíření, nelze zachytit dílčích výrazů.  
  
 Na rozdíl od DFA modulů když tradiční NFA moduly provádění porovnávání vzorů, jejich pořadí zpracování doprovází vzor regulárního výrazu. Při zpracování elementu konkrétní jazyk, používá modul odpovídajícím metodou greedy; To znamená odpovídá co nejvíce vstupní řetězec jako to pravděpodobně možné. Můžete ale také ukládá svůj stav po úspěšně odpovídající dílčí výraz. Pokud odpovídající nakonec dojde k chybě, modul vrátit k uloženému stavu proto ji můžete vyzkoušet další shody. Tento proces zrušení shodu úspěšně dílčí výraz tak, aby novější prvky jazyka v regulárním výrazu můžete také hledat shody se označuje jako *používání mechanismu zpětného navracení*. NFA modulů pomocí mechanismu zpětného navracení k testování všech možných rozšíření regulárního výrazu v určitém pořadí a přijímat první shoda. Protože tradiční modulem NFA vytvoří konkrétní rozšíření regulární výraz pro porovnání, můžete zachytit, dílčí výraz odpovídá a odpovídající zpětnými odkazy. Ale protože tradiční NFA provided, ji můžou navštívit stejného stavu více než jednou Pokud dorazí stav prostřednictvím různých cest. V důsledku toho může probíhat exponenciálně pomalu v nejhorším případě. Protože tradiční modulem NFA přijímá první odpovídat ho najde, můžete také ponechat další (možná delší) odpovídá nezjištěné.  
  
 POSIX NFA moduly jsou podobné tradiční NFA modulů, s tím rozdílem, že nadále navracení, dokud se může zaručit, že se našel nejdelší shoda je to možné. V důsledku toho je pomalejší než tradiční modulem NFA modulem POSIX NFA a při použití modulem POSIX NFA kratší shoda nelze upřednostnil před delší jeden změnou pořadí hledání navracení.  
  
 Tradiční NFA moduly jsou podporuje programátory, protože nabízí větší kontrolu nad shody než DFA nebo POSIX NFA motorů řetězců. I když v nejhorším případě, že lze spustit pomalu, můžete řídit, je pro vyhledání shody v čase lineární nebo polynomické pomocí vzorce, které snížit nejednoznačnosti a omezit používání mechanismu navracení. Jinými slovy i když NFA moduly obchodu výkonu pro výkon, flexibilitu a ve většině případů, které nabízejí dobrý přijatelný výkon, pokud je kvalitně napsané regulárního výrazu a přitom vylučuje případy, kdy používání mechanismu zpětného navracení snižuje výkon exponenciálně zvyšuje.  
  
> [!NOTE]
>  Informace o snížení výkonu způsobené nadměrného používání mechanismu navracení a způsoby, jak si poradit regulární výraz je obejít, najdete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>Možnosti modulu rozhraní .NET framework  
 Abyste mohli využívat výhody tradičního modulem NFA, modul regulárních výrazů rozhraní .NET Framework zahrnuje kompletní sadu konstrukty, které umožňují programátorům řídit modul navracení. Tato konstrukce je možné, abyste rychleji odhalili shody nebo konkrétní rozšíření upřednostnil před ostatními.  
  
 Další funkce modulu regulárních výrazů rozhraní .NET Framework patří:  
  
- Líné kvantifikátory: `??`, `*?`, `+?`, `{` *n*`,`*m*`}?`. Tyto konstrukce řekněte modul navracení k vyhledání nejprve minimální počet opakování. Běžnou metodou greedy kvantifikátory naproti tomu pokusí nejprve srovnat maximální počet opakování. Následující příklad ukazuje rozdíl mezi nimi. Regulární výraz odpovídá věty, které končí na číslo a zachytávající skupina slouží k extrakci tohoto čísla. Regulární výraz `.+(\d+)\.` zahrnuje kvantifikátor greedy `.+`, což způsobí, že modul regulárních výrazů k zachycení pouze poslední číslice čísla. Naproti tomu regulárního výrazu `.+?(\d+)\.` zahrnuje opožděným kvantifikátorem `.+?`, což způsobí, že modul regulárních výrazů k zachycení celé číslo.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Jsou definovány greedy a opožděné verze tohoto regulárního výrazu, jak je znázorněno v následující tabulce. "  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`.+` (greedy kvantifikátor)|Porovná jeden výskyt libovolného znaku. To způsobí, že modul regulárních výrazů tak, aby odpovídaly celý řetězec a pak navracení jako potřeby tak, aby odpovídala zůstatek vzor.|  
    |`.+?` (opožděným kvantifikátorem)|Odpovídá alespoň jeden výskyt jakéhokoliv znaku, ale odpovídá co nejméně.|  
    |`(\d+)`|Odpovídá alespoň jednu číslici a přiřaďte ho k první zachytávající skupina.|  
    |`\.`|Porovná tečku.|  
  
     Další informace o líné kvantifikátory, naleznete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Pozitivního dopředného vyhledávání: `(?=` *dílčí výraz*`)`. Tato funkce umožňuje vrátit na stejné místo v textu po odpovídající dílčí výraz modulu navracení. To je užitečné pro vyhledávání v rámci text tak, že ověříte více vzorům, které začínají na stejné pozici. Umožňuje také modulu ověřte, zda je dílčí řetězec existuje na konci porovnávání bez zahrnutí podřetězec v odpovídající text. Následující příklad používá k extrakci slova ve větě, která nejsou následovány interpunkčních znamének pozitivního dopředného vyhledávání.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Regulární výraz `\b[A-Z]+\b(?=\P{P})` je definován, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`[A-Z]+`|Porovná libovolný znak abecedy jednou nebo vícekrát. Protože <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možnost, při porovnávání se velká a malá písmena.|  
    |`\b`|Ukončí porovnání na hranici slova.|  
    |`(?=\P{P})`|Dívejte se k určení, zda je další znak interpunkčním znaménkem. Pokud není, bude úspěšná shoda.|  
  
     Další informace o kontrolní výrazy pozitivního dopředného vyhledávání najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Negativního dopředného vyhledávání s: `(?!` *dílčí výraz*`)`. Tato funkce přidává možnost tak, aby odpovídaly výraz pouze v případě, že dílčí výraz selže při porovnávání. To je zvláště efektivní při vyřazování vyhledávání, protože často je jednodušší zajistit výrazu pro případ, který by měly být odstraněny než výrazu pro případy, které musí být zahrnut. Například je obtížné je napsat výraz slova, která nezačínají "jiné". Následující příklad používá negativního dopředného vyhledávání s vyloučit.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Vzor regulárního výrazu `\b(?!non)\w+\b` je definován, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`(?!non)`|Dívejte se a zkontrolujte, že aktuální řetězec nezačíná řetězcem "jiné". Pokud tomu tak, shoda se nezdaří.|  
    |`(\w+)`|Porovná jeden nebo více znaků slova.|  
    |`\b`|Ukončí porovnání na hranici slova.|  
  
     Další informace o kontrolní výrazy dopředného vyhledávání záporný, naleznete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Vyhodnocení podmíněného: `(?(` *výraz*`)`*Ano*`|`*žádné* `)` a `(?(` *název*`)`*Ano*`|`*žádné*`)`, kde *výraz* je dílčí výraz tak, aby odpovídaly, *název* je název zachytávající skupiny *Ano* je řetězec, který se shodují, pokud *výraz* je nalezena shoda nebo *název* je platný, zachycené skupiny není prázdná, a *žádné* je dílčí výraz pro porovnání, pokud *výraz* neodpovídá nebo *název* není platné, prázdný zachycené skupině. Tato funkce umožňuje modulu pro vyhledávání s použitím více než jeden alternativní vzorek, v závislosti na výsledek předchozí dílčí výraz porovnání nebo výsledek kontrolní výraz nulové šířky. Díky tomu zvyšují efektivitu formu zpětný odkaz, který umožňuje například odpovídající dílčí výraz na základě na, jestli byl předchozí dílčí výraz odpovídá. Regulární výraz v následujícím příkladu odpovídá odstavců, které jsou určeny k použití veřejné a vnitřní. Začínat odstavců určené pouze pro interní použití `<PRIVATE>` značky. Vzor regulárního výrazu `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` používá vyhodnocení podmíněného přiřadit obsah odstavců určených pro veřejnost a pro interní použití k oddělení zachytávajících skupinách. Těchto odstavcích můžete pak zpracovány jinak.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Zahájí porovnávání na začátku řádku.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Porovná žádný nebo jeden výskyt řetězce `<PRIVATE>` následované prázdným znakem. Přiřadit ke shodě zachytávající skupina s názvem `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Pokud `Pvt` zachycující skupina existuje, porovná jeden nebo více výskytů jednoho nebo více znaků slova, následované žádnou nebo jednu oddělovač interpunkční znaménka, následované prázdným znakem. Přiřadíte podřetězec první zachytávající skupina.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|Pokud `Pvt` zachycující skupina neexistuje, odpovídat jedné nebo více výskytů jednoho nebo více znaků slova, následované žádnou nebo jednu oddělovač interpunkční znaménka, následované prázdným znakem. Podřetězec přiřadíte třetí zachytávající skupina.|  
    |`\r?$`|Porovná konec řádku nebo konec řetězce.|  
  
     Další informace o vyhodnocení podmíněného najdete v tématu [alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
- Definice skupiny vyrovnávání: `(?<` *name1*`-`*name2* `>` *dílčí výraz*`)`. Tato funkce umožňuje modulu regulárních výrazů ke sledování vnořené konstrukce, jako je například závorky nebo levé a pravé hranaté závorky. Příklad najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Podvýrazy bez mechanismu navracení (označovaný také jako greedy podvýrazy): `(?>` *dílčí výraz*`)`. Tato funkce umožňuje zajistit, že dílčí výraz odpovídá pouze první shoda pro tento dílčí výraz se nenašly jako kdyby byly spuštěné výraz nezávisle na jeho obsahujícího výrazu modulu navracení. Pokud nepoužijete tento konstruktor, navracení vyhledávání z rozsáhlejšího výrazu můžete změnit chování podvýrazu. Například regulární výraz `(a+)\w` odpovídá jedné nebo více znaků "a, spolu s znaku slova, která odpovídá sekvenci znaků"a"a přiřadí pořadí znaků"a"první zachytávající skupina, ale" pokud poslední znak vstupní řetězec je také "a", it, který odpovídá `\w` prvek jazyka a není součástí zachycenou skupinou.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Regulární výraz `((?>a+))\w` brání toto chování. Protože všechny po sobě jdoucích znaků "a" jsou porovnány bez mechanismu navracení, první zachytávající skupina obsahuje všechny po sobě jdoucích znaků "a". Pokud se alespoň jeden další znak jiný než "a" nejsou následovány znaky "a", shoda se nezdaří.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Další informace o podvýrazy bez mechanismu navracení najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Doleva porovnávání, který je zadán zadáním <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> umožňuje <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické odpovídající metodu instance. Tato funkce je užitečná při vyhledávání zprava doleva namísto zleva doprava, nebo v případech, kdy je efektivnější zahájit porovnávání na pravou část vzoru místo vlevo. Jak ukazuje následující příklad pomocí odpovídající zprava doleva můžete změnit chování greedy kvantifikátory. Příklad provádí dvě vyhledá věty, které končí na číslo. Hledání zleva doprava, který používá greedy kvantifikátor `+` shoduje s jedním z šesti číslic ve větě, že hledání zprava doleva odpovídá všech šesti číslic. Popis vzor regulárního výrazu prohlédněte si příklad znázorňuje líné kvantifikátory uvedené v této části.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Další informace o odpovídajících zprava doleva, naleznete v tématu [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
- Kladné a záporné zpětného vyhledávání: `(?<=` *dílčí výraz* `)` pro pozitivního zpětného vyhledávání, a `(?<!` *dílčí výraz* `)` pro negativního zpětného vyhledávání. Tato funkce je podobný s dopředným vyhledáváním, která je popsána výše v tomto tématu. Protože modul regulárních výrazů umožňuje kompletní odpovídající zprava doleva, regulární výrazy umožňují kontrolu neomezený dozadu. Kladné a záporné zpětného vyhledávání také umožňuje vyhnout se vnoření kvantifikátory při vnořené dílčí výraz je nadstavbou jazyka vnější výraz. Regulární výrazy pouze za těchto vnořených kvantifikátorů často nabízejí nízký výkon. Například následující příklad ověří, že řetězec začíná a končí u alfanumerickým znakem a že jakýkoli jiný znak v řetězci je jedním z větších dílčí. Tvoří část regulární výraz používaný k ověření e-mailové adresy; Další informace najdete v tématu [jak: Ověřte, zda jsou řetězce ve formátu platné e-mailové](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Regulární výraz `^[A-Z0-9]([-!#$%&'.*+/=?^` {}| ~ \w])* (? < = [A-Z0-9]) $' je definován, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Zahájí porovnávání na začátku řetězce.|  
    |`[A-Z0-9]`|Odpovídá jakémukoli znaku číselné nebo alfanumerické znaky. (Při porovnávání se velká a malá písmena.)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])*<code>|Match zero or more occurrences of any word character, or any of the following characters:  -, !, #, $, %, &, ', ., *, +, /, =, ?, ^, \`, {, }, &#124;, or ~.|  
    |`(?<=[A-Z0-9])`|Podívá se za předchozí znak, který musí být číselné nebo alfanumerické znaky. (Při porovnávání se velká a malá písmena.)|  
    |`$`|Ukončit porovnávání na konci řetězce.|  
  
     Další informace o kladné a záporné zpětného vyhledávání najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Poskytuje informace o způsobu regulárních výrazů mechanismus navracení větví můžete najít alternativní shody.|  
|[Kompilace a opětovné používání](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Poskytuje informace o kompilaci a opětovné použití regulárních výrazů ke zvýšení výkonu.|  
|[Bezpečnost vlákna](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Poskytuje informace o zabezpečení vlákna regulárního výrazu a vysvětluje, kdy bude třeba synchronizovat přístup k objektům regulární výraz.|  
|[Regulárních výrazech .NET Frameworku](../../../docs/standard/base-types/regular-expressions.md)|Poskytuje přehled o programovací jazyk aspekt regulární výrazy.|  
|[Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Poskytuje informace a příklady kódu znázorňující způsob používání tříd regulárních výrazů.|  
|[Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md)|Obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžných aplikací.|  
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Poskytuje informace o sadě znaků, operátorů a konstrukcí, které můžete použít pro definování regulárních výrazů.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
