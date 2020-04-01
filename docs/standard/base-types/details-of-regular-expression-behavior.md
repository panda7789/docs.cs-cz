---
title: Chování regulárního výrazu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
ms.openlocfilehash: 288bf4256670d34c600e23618b62ad81866daadf
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523841"
---
# <a name="details-of-regular-expression-behavior"></a>Podrobnosti o chování regulárních výrazů

Modul regulárních výrazů rozhraní .NET Framework je backtrackingový matcher regulárních výrazů, který obsahuje tradiční modul NFA (Nondeterministic Finite Automaton), například modul používaný perlem, pythonem, emacsem a tcl. Tím se odlišuje od rychlejší, ale omezenější, čistě regulární výraz Deterministický konečný automaton (DFA) motory, jako jsou ty, které se nacházejí v awk, egrep, nebo lex. To také odlišuje od standardizované, ale pomalejší, POSIX NFAs. Následující část popisuje tři typy modulů regulárních výrazů a vysvětluje, proč jsou regulární výrazy v rozhraní .NET Framework implementovány pomocí tradičního modulu NFA.

## <a name="benefits-of-the-nfa-engine"></a>Výhody motoru NFA

 Když moduly DFA provádět porovnávání vzorů, jejich pořadí zpracování je řízeno vstupní řetězec. Modul začíná na začátku vstupního řetězce a pokračuje postupně k určení, zda další znak odpovídá vzoru regulárního výrazu. Mohou zaručit, že budou odpovídat nejdelšímu možnému řetězci. Protože nikdy testovat stejný znak dvakrát, DFA motory nepodporují navracení. Však vzhledem k tomu, že modul DFA obsahuje pouze konečný stav, nemůže odpovídat vzorek s backreferences a protože nevytváří explicitní rozšíření, nemůže zachytit podvýrazy.

 Na rozdíl od modulů DFA, když tradiční moduly NFA provádějí porovnávání vzorů, jejich pořadí zpracování je řízeno vzorem regulárního výrazu. Při zpracování určitého prvku jazyka používá modul chamtivé párování; to znamená, že odpovídá co nejvíce vstupního řetězce, jak je to možné. Ale také uloží jeho stav po úspěšném porovnání dílčího výrazu. Pokud se shoda nakonec nezdaří, modul se může vrátit do uloženého stavu, aby mohl vyzkoušet další shody. Tento proces opuštění úspěšné shody podvýrazu tak, aby pozdější prvky jazyka v regulárním výrazu se také mohly shodovat, se označuje jako *backtracking*. Moduly NFA používají backtracking k testování všech možných rozšíření regulárního výrazu v určitém pořadí a přijmout první shodu. Vzhledem k tomu, že tradiční modul NFA vytvoří konkrétní rozšíření regulárního výrazu pro úspěšnou shodu, může zachytit shody podvýrazu a odpovídající zpětné odkazy. Však protože tradiční NFA backtracks, může navštívit stejný stav vícekrát, pokud dorazí do stavu přes různé cesty. V důsledku toho může běžet exponenciálně pomalu v nejhorším případě. Vzhledem k tomu, že tradiční modul NFA přijímá první shodu, kterou najde, může také ponechat jiné (případně delší) shody neobjevené.

 POSIX NFA motory jsou jako tradiční NFA motory, kromě toho, že i nadále ustoupit, dokud mohou zaručit, že našli nejdelší možnou shodu. V důsledku toho posix NFA motor je pomalejší než tradiční modul NFA a při použití modulu POSIX NFA, nelze upřednostnit kratší shoda přes delší změnou pořadí backtracking vyhledávání.

 Tradiční moduly NFA jsou upřednostňovány programátory, protože nabízejí větší kontrolu nad porovnáváním řetězců než motory DFA nebo POSIX NFA. I když v nejhorším případě mohou běžet pomalu, můžete je nasměrovat k nalezení shody v lineárním nebo polynomickém čase pomocí vzorů, které snižují nejasnosti a omezují backtracking. Jinými slovy, i když nfa motory obchodu výkon pro výkon a flexibilitu, ve většině případů nabízejí dobré přijatelné výkon, pokud regulární výraz je dobře napsaný a vyhýbá se případy, ve kterých backtracking snižuje výkon exponenciálně.

> [!NOTE]
> Informace o snížení výkonu způsobené nadměrným navracením a způsoby vytvoření regulárního výrazu k jejich obejít, naleznete v [tématu Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).

## <a name="net-framework-engine-capabilities"></a>Možnosti modulu rozhraní .NET Framework

 Chcete-li využít výhod tradiční modul NFA, modul regulárních výrazů rozhraní .NET Framework obsahuje úplnou sadu konstrukcí, které umožňují programátorům řídit modul backtracking. Tyto konstrukce lze použít k nalezení shody rychleji nebo upřednostnit konkrétní rozšíření nad ostatními.

 Mezi další funkce modulu regulárních výrazů rozhraní .NET Framework patří následující:

- `??`Opožděné kvantifikátory: , `*?`, `+?`, `{` *n*`,`*m*`}?`. Tyto konstrukce sdělit backtracking motoru hledat minimální počet opakování jako první. Naproti tomu obyčejné chamtivé kvantifikátory se nejprve snaží vyrovnat maximálnímu počtu opakování. Následující příklad ilustruje rozdíl mezi těmito dvěma. Regulární výraz odpovídá větě, která končí číslem, a zachytávající skupina je určena k extrahování tohoto čísla. Regulární `.+(\d+)\.` výraz obsahuje nenasytný kvantifikátor `.+`, který způsobí, že modul regulárních výrazů zachytí pouze poslední číslici čísla. Naproti tomu regulární výraz `.+?(\d+)\.` obsahuje `.+?`opožděný kvantifikátor , který způsobí, že modul regulárních výrazů zachytí celé číslo.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Chamtivé a opožděné verze tohoto regulárního výrazu jsou definovány tak, jak je znázorněno v následující tabulce:

    |Vzor|Popis|
    |-------------|-----------------|
    |`.+`(nenasytný kvantifikátor)|Porovná alespoň jeden výskyt libovolného znaku. To způsobí, že modul regulárních výrazů tak, aby odpovídaly celý řetězec a potom ustoupit podle potřeby tak, aby odpovídaly zbytek vzoru.|
    |`.+?`(líný kvantifikátor)|Porovná alespoň jeden výskyt libovolného znaku, ale shoduje se co nejméně.|
    |`(\d+)`|Porovná alespoň jeden číselný znak a přiřadí ho první zachytávající skupině.|
    |`\.`|Porovná tečku.|

     Další informace o opožděných kvantifikárech naleznete [v tématu Kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).

- Pozitivní dopředné vyhledávání: `(?=` *podvýraz*`)`. Tato funkce umožňuje backtracking motoru vrátit na stejné místo v textu po odpovídající podvýraz. Je užitečné pro vyhledávání v celém textu ověřením více vzorků, které začínají ze stejné pozice. Také umožňuje modulu ověřit, že podřetězec existuje na konci shody bez zahrnutí podřetězce do odpovídajícího textu. Následující příklad používá pozitivní dopředné vyhledávání extrahovat slova ve větě, které nejsou následovány interpunkční symboly.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     Regulární `\b[A-Z]+\b(?=\P{P})` výraz je definován tak, jak je znázorněno v následující tabulce.

    |Vzor|Popis|
    |-------------|-----------------|
    |`\b`|Začne porovnání na hranici slova.|
    |`[A-Z]+`|Porovná libovolný abecední znak jednou nebo vícekrát. Vzhledem <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> k tomu, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> že metoda je volána s možností, porovnání je malá a velká písmena.|
    |`\b`|Ukončí porovnání na hranici slova.|
    |`(?=\P{P})`|Podívejte se dopředu a zjistěte, zda je dalším znakem symbol interpunkce. Pokud tomu tak není, shoda proběhne úspěšně.|

     Další informace o kontrolních výrazech pozitivního dopředného vyhledávání naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Negativní dopředné vyhledávání: `(?!` *podvýraz*`)`. Tato funkce přidává možnost odpovídat výrazu pouze v případě, že dílčí výraz neodpovídá. To je obzvláště silný pro prořezávání hledání, protože je často jednodušší poskytnout výraz pro případ, který by měl být odstraněn, než výraz pro případy, které musí být zahrnuty. Například je obtížné napsat výraz pro slova, která nezačínají na "non". Následující příklad používá negativní dopředné vyhledávání k jejich vyloučení.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     Vzor regulárního výrazu `\b(?!non)\w+\b` je definován tak, jak je znázorněno v následující tabulce.

    |Vzor|Popis|
    |-------------|-----------------|
    |`\b`|Začne porovnání na hranici slova.|
    |`(?!non)`|Podívejte se dopředu, abyste zajistili, že aktuální řetězec nezačíná na "non". Pokud ano, shoda se nezdaří.|
    |`(\w+)`|Porovná jeden nebo více znaků slova.|
    |`\b`|Ukončí porovnání na hranici slova.|

     Další informace o kontrolních výrazech negativního dopředného vyhledávání naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Podmíněné `(?(`vyhodnocení: *výraz*`)`*ano*`|`*ne* `)` a `(?(` *název*`)`*ano ne*`|`*no*`)`, kde *výraz* je podvýraz, který se má shodovat, *název* je název zachytávající skupiny, *ano* je řetězec, který odpovídá, pokud je *výraz* spárován nebo *název* je platná, neprázdná zachycená skupina a *ne* je dílčívýraz, který odpovídá, pokud *výraz* není spárován nebo *název* není platná, neprázdná zachycená skupina. Tato funkce umožňuje motoru prohledávat pomocí více než jeden alternativní vzorek, v závislosti na výsledku předchozí shody dílčího výrazu nebo výsledek kontrolnívýraz s nulovou šířkou. To umožňuje výkonnější formu zpětného odkazu, který umožňuje například odpovídající podvýraz na základě toho, zda byl spárován předchozí dílčí výraz. Regulární výraz v následujícím příkladu odpovídá odstavcům, které jsou určeny pro veřejné i interní použití. Odstavce určené pouze pro vnitřní `<PRIVATE>` použití začínají tagem. Vzor regulárního výrazu `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` používá podmíněné vyhodnocení k přiřazení obsahu odstavců určených pro veřejné a interní použití k oddělení zachytávacích skupin. Tyto odstavce pak mohou být zpracovány odlišně.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.

    |Vzor|Popis|
    |-------------|-----------------|
    |`^`|Začněte zápas na začátku řádku.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Porovná nula nebo jeden `<PRIVATE>` výskyt řetězce následovaný znakem prázdnémezery. Přiřaďte shodu `Pvt`zachytávající skupině s názvem .|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Pokud `Pvt` zachytávající skupina existuje, porovnejte jeden nebo více výskytů jednoho nebo více znaků slova následovaných nulou nebo jedním oddělovačem interpunkce následovaným bílým znakem. Přiřaďte podřetězec k první zachytávající skupině.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|Pokud `Pvt` zachytávající skupina neexistuje, porovnejte jeden nebo více výskytů jednoho nebo více znaků slova následovaných nulou nebo jedním oddělovačem interpunkce následovaným znakem prázdného místa. Přiřaďte podřetězec třetí zachytávající skupině.|
    |`\r?$`|Porovná konec řádku nebo konec řetězce.|

     Další informace o podmíněném vyhodnocení naleznete v [tématu Alternation Constructs](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).

- Definice vyrovnávacích `(?<`skupin: *podvýraz*`)` *name1*`-`*name2* `>` . Tato funkce umožňuje modulu regulárních výrazů sledovat vnořené konstrukce, jako jsou závorky nebo otevírací a uzavírací závorky. Příklad naleznete v [tématu Seskupení konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Atomové `(?>`skupiny: *podvýraz*`)`. Tato funkce umožňuje backtracking motoru zaručit, že podvýraz odpovídá pouze první shodě nalezené pro tento dílčí výraz, jako kdyby výraz byl spuštěn nezávisle na jeho obsahující výraz. Pokud tuto konstrukci nepoužijete, může zpětné navracení hledání z většího výrazu změnit chování dílčího výrazu. Například regulární `(a+)\w` výraz odpovídá jednomu nebo více znakům "a" spolu se znakem slova, který následuje za posloupností znaků "a" a přiřazuje posloupnost znaků "a" první zachytávající skupině. Pokud je však konečný znak vstupního řetězce také "a", `\w` je porovnán s elementem jazyka a není zahrnut do zachycené skupiny.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     Regulární `((?>a+))\w` výraz zabraňuje tomuto chování. Vzhledem k tomu, že všechny po sobě jdoucí znaky "a" jsou spárovány bez zpětného navracení, první zachytávající skupina obsahuje všechny po sobě jdoucí znaky "a". Pokud znaky "a" nejsou následovány alespoň jeden další znak než "a", shoda se nezdaří.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Další informace o atomických skupinách naleznete [v tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Párování zprava doleva, které je <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> určeno <xref:System.Text.RegularExpressions.Regex> zadáním možnosti konstruktoru třídy nebo statické metody párování instancí. Tato funkce je užitečná při hledání zprava doleva namísto zleva doprava nebo v případech, kdy je efektivnější začít shodu v pravé části vzoru namísto vlevo. Jak ukazuje následující příklad, použití porovnávání zprava doleva může změnit chování nenasytných kvantifikátorů. Příklad provádí dvě hledání věty, která končí číslem. Hledání zleva doprava, které používá nenasytný kvantifikátor, `+` odpovídá jedné ze šesti číslic ve větě, zatímco hledání zprava doleva odpovídá všem šesti číslicím. Popis vzoru regulárního výrazu naleznete v příkladu, který ilustruje opožděné kvantifikátory dříve v této části.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Další informace o porovnávání zprava doleva naleznete v [tématu Možnosti regulárního výrazu](../../../docs/standard/base-types/regular-expression-options.md).

- Pozitivní a negativní `(?<=`zpětné vyhledávání: *dílčí* `)` výraz `(?<!`pro pozitivní zpětné vyhledávání a *dílčí výraz* `)` pro negativní zpětné vyhledávání. Tato funkce je podobná dopředné vyhledávání, která je popsána dříve v tomto tématu. Vzhledem k tomu, že modul regulárních výrazů umožňuje kompletní párování zprava doleva, umožňují regulární výrazy neomezená vyhledávání. Pozitivní a negativní zpětné vyhledávání lze také použít k zabránění vnoření kvantifikátory, když vnořený podvýraz je nadmnožinou vnějšího výrazu. Regulární výrazy s takovými vnořenými kvantifikátory často nabízejí nízký výkon. Například následující příklad ověří, zda řetězec začíná a končí alfanumerickým znakem a že jakýkoli jiný znak v řetězci je jedním z větší podmnožiny. Tvoří část regulárního výrazu používaného k ověření e-mailových adres; Další informace naleznete v [tématu Postup: Ověření, zda jsou řetězce v platném formátu e-mailu](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     Regulární ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` výraz je definován tak, jak je znázorněno v následující tabulce.

    |Vzor|Popis|
    |-------------|-----------------|
    |`^`|Začněte zápas na začátku řetězce.|
    |`[A-Z0-9]`|Porovná libovolný číselný nebo alfanumerický znak. (Porovnání nerozlišuje malá a velká písmena.)|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Shodovat nula nebo více výskytů libovolného znaku slova nebo některého z následujících znaků: -, !, #, $, %, &, ', ., \*, +, /, =, ^, &#96;, {, }, &#124; nebo ~.|
    |`(?<=[A-Z0-9])`|Podívejte se za předchozí znak, který musí být číselný nebo alfanumerický. (Porovnání nerozlišuje malá a velká písmena.)|
    |`$`|Ukončite shodu na konci řetězce.|

     Další informace o pozitivní matné a záporné zpětné vyhledávání naleznete v [tématu seskupení konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="related-articles"></a>Související články

|Nadpis|Popis|
|-----------|-----------------|
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Obsahuje informace o tom, jak regulární výraz backtracking větve najít alternativní shody.|
|[Kompilace a opětovné používání](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Obsahuje informace o kompilaci a opakovaném použití regulárních výrazů pro zvýšení výkonu.|
|[Bezpečnost vlákna](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Obsahuje informace o bezpečnosti podprocesu regulárních výrazů a vysvětluje, kdy byste měli synchronizovat přístup k objektům regulárních výrazů.|
|[.NET Framework – regulární výrazy](../../../docs/standard/base-types/regular-expressions.md)|Poskytuje přehled aspektu programovacího jazyka regulárních výrazů.|
|[Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Obsahuje informace a příklady kódu znázorňující, jak používat třídy regulárních výrazů.|
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Obsahuje informace o sadě znaků, operátorů a konstrukcí, které lze použít k definování regulárních výrazů.|

## <a name="reference"></a>Odkaz

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
