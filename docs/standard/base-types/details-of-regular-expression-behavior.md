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
ms.openlocfilehash: bb43554d53051ce02a296f225c68c74352add5ed
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567479"
---
# <a name="details-of-regular-expression-behavior"></a>Podrobnosti k chování regulárních výrazů
.NET Framework modul regulárních výrazů je zpětné navýšení shody regulárních výrazů, která zahrnuje tradiční Nedeterministický NFA modul pro nedeterministické konečné Automation (), jako je například jazyk Perl, Python, (Emacs) a TCL. Tím se odlišuje od rychlejšího, ale více omezených, čistě regulárního výrazu deterministického Automation (DFA) modulů, jako jsou ty, které se našly v AWK mají, egrep nebo Lex. Tím se také odlišuje od standardizovaného, ale pomalejšího NFAsu POSIX. V následující části jsou popsány tři typy modulů regulárních výrazů a vysvětlení, proč jsou regulární výrazy v .NET Framework implementovány pomocí tradičního modulu NFA.  
  
## <a name="benefits-of-the-nfa-engine"></a>Výhody modulu NFA  
 Pokud DFA moduly provádějí porovnávání vzorů, jejich pořadí zpracování je ovládáno vstupním řetězcem. Modul začíná na začátku vstupního řetězce a pokračuje sekvenčně a určí, zda se další znak shoduje se vzorem regulárního výrazu. Můžou zaručit, aby odpovídaly nejdelšímu možnému řetězci. Vzhledem k tomu, že nikdy netestují stejný znak dvakrát, DFA moduly nepodporují navrácení. Vzhledem k tomu, že modul DFA obsahuje pouze omezený stav, nemůže odpovídat vzoru s zpětnými odkazy a protože nevytváří explicitní rozšíření, nemůže zachytit dílčí výrazy.  
  
 Na rozdíl od DFA modulů, když tradiční moduly NFA provádějí porovnávání vzorů, jejich pořadí zpracování je založené na vzoru regulárního výrazu. Při zpracovávání konkrétního prvku jazyka používá modul hladový koshodě; To znamená, že odpovídá největšímu vstupnímu řetězci, což může být. Ale také uloží svůj stav po úspěšném porovnání dílčího výrazu. Pokud se shoda nakonec nezdařila, může se modul vrátit do uloženého stavu, aby se mohl pokusit o další shody. Tento proces opuštění úspěšné shody dílčího výrazu, aby se pozdější prvky jazyka regulárního výrazu mohly také shodovat, se označují jako *zpětné navrácení*. NFA moduly používají navrácení se změnami k otestování všech možných rozšíření regulárního výrazu v určitém pořadí a přijímají první shodu. Vzhledem k tomu, že tradiční modul NFA sestaví konkrétní rozšíření regulárního výrazu pro úspěšnou shodu, může zachytit shody dílčího výrazu a porovnat zpětná reference. Vzhledem k tomu, že tradiční NFAé zpětné navrácení, může přejít stejný stav několikrát, pokud dorazí na stav prostřednictvím různých cest. V důsledku toho může v nejhorším případě běžet exponenciálně pomalu. Vzhledem k tomu, že tradiční modul NFA akceptuje první nalezenou shodu, může také ponechávat jiné (pravděpodobně delší) shody, které se neobjevují.  
  
 NFA moduly POSIX jsou podobné tradičním NFAm modulům, s tím rozdílem, že se budou i nadále přepracovat, dokud nebudou zárukou, že by zjistili nejdelší možný rozdíl. Výsledkem je, že NFA modul POSIX je pomalejší než tradiční modul NFA a když používáte modul NFA POSIX, nemůžete upřednostnit kratší porovnání po delším pořadí, protože se mění pořadí hledání zpětného navrácení.  
  
 Tradiční moduly NFA se přidávají programátorům, protože nabízejí větší kontrolu nad řetězcovým porovnáním, než DFA nebo POSIX NFA Engines. I když v nejhorším případě může běžet pomalu, můžete je pomocí vzorů, které snižují nejednoznačnosti a omezením zpětného navrácení, nařídit, aby vyhledaly shody lineární nebo polynom. Jinými slovy, i když NFA stroje v obchodním výkonu pro výkon a flexibilitu, ve většině případů nabízí dobrý výkon, pokud je regulární výraz správně zapsaný, a zabrání tak případům, kdy zpětné navrácení snižuje výkon exponenciálně.  
  
> [!NOTE]
>  Informace o penalizaci výkonu způsobené nadměrným navrácením a způsoby, jak vymezit regulární výrazy, najdete v tématu [navrácení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>Možnosti modulu .NET Framework  
 Aby bylo možné využít výhody tradičního stroje NFA, modul regulárních výrazů .NET Framework obsahuje kompletní sadu konstrukcí, která programátorům umožní řídit modul pro navrácení. Tyto konstrukce lze použít k vyhledání shody rychleji nebo k upřednostnění konkrétního rozšíření přes jiné.  
  
 Mezi další funkce modulu .NET Framework regulárních výrazů patří následující:  
  
- Opožděné kvantifikátory `??`: `*?`, `+?`, `{`, *n*`,`*m*.`}?` Tyto konstrukce instruují modul zpětného navrácení, aby nejdříve hledali minimální počet opakování. Oproti tomu běžné hladové kvantifikátory se snaží vyhledat maximální počet opakování jako první. Následující příklad znázorňuje rozdíl mezi těmito dvěma. Regulární výraz odpovídá větě, která končí číslem, a zachytávající skupina je určena k extrakci daného čísla. Regulární výraz `.+(\d+)\.` zahrnuje hladový `.+`kvantifikátor, který způsobí, že modul regulárních výrazů zachytí pouze poslední číslici čísla. Naopak regulární výraz `.+?(\d+)\.` obsahuje opožděný `.+?`kvantifikátor, který způsobí, že modul regulárních výrazů zachytí celé číslo.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Hladce a opožděné verze tohoto regulárního výrazu jsou definovány tak, jak je uvedeno v následující tabulce:
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`.+`(hladový kvantifikátor)|Porovnává alespoň jeden výskyt libovolného znaku. To způsobí, že modul regulárních výrazů bude odpovídat celému řetězci a následně k převrácení podle potřeby, aby odpovídal zbývajícímu vzoru.|  
    |`.+?`(opožděný kvantifikátor)|Porovnává alespoň jeden výskyt libovolného znaku, ale porovnává co nejvíce.|  
    |`(\d+)`|Porovnává alespoň jeden číselný znak a přiřadí ho první zachytávající skupině.|  
    |`\.`|Odpovídá tečkě.|  
  
     Další informace o opožděných kvantifikátorech naleznete v [](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)tématu Kvantifikátory.  
  
- Pozitivní dopředného `(?=`vyhledávání: dílčí *výraz*`)`. Tato funkce umožňuje, aby se modul zpětného navracení vrátil na stejné místo v textu po porovnání dílčího výrazu. Je užitečné Hledat v celém textu tím, že ověřuje více vzorů, které začínají na stejné pozici. Umožňuje modulu také ověřit, zda podřetězec existuje na konci porovnávání bez zahrnutí podřetězce do odpovídajícího textu. Následující příklad používá pozitivní dopředného vyhledávání k extrakci slov ve větě, která nejsou následována symboly interpunkce.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Regulární výraz `\b[A-Z]+\b(?=\P{P})` je definován tak, jak je uvedeno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`[A-Z]+`|Porovnává libovolný abecední znak jednou nebo vícekrát. Vzhledem k tomu, že je <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> metodavolánasmožností,porovnávánírozlišujevelkáamalápísmena.<xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>|  
    |`\b`|Ukončí porovnání na hranici slova.|  
    |`(?=\P{P})`|Před zjištěním, zda je další znak symbol interpunkce, se podívejte dopředu. Pokud tomu tak není, bude shoda úspěšná.|  
  
     Další informace o kladném kontrolním výrazu dopředného [](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)vyhledávání naleznete v tématu Grouping konstrukcís.  
  
- Negativní dopředného `(?!`vyhledávání: dílčí *výraz*`)`. Tato funkce přidá schopnost vyhledat výraz pouze v případě, že se dílčí výraz neshoduje. To je obzvláště výkonné pro vyřazení hledání, protože je často jednodušší poskytnout výraz pro případ, který by se měl vyloučit než výraz pro případy, které musí být zahrnuté. Například je obtížné napsat výraz pro slova, která nezačínají na "non". Následující příklad používá negativní dopředné vyhledávání k vyloučení.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Vzor `\b(?!non)\w+\b` regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`\b`|Začne porovnání na hranici slova.|  
    |`(?!non)`|Prohlédněte si, abyste zajistili, že aktuální řetězec nezačíná na "non". Pokud k tomu dojde, shoda se nezdařila.|  
    |`(\w+)`|Porovná jeden nebo více znaků slova.|  
    |`\b`|Ukončí porovnání na hranici slova.|  
  
     Další informace o záporné kontrolní výrazy dopředného vyhledávání naleznete [](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)v tématu Grouping konstrukcís.  
  
- Podmíněné vyhodnocení: `(?(` *výraz*`)`*Ano*ne a názevAno`)``)` `|` `(?(``|``)`, kde *výraz* je dílčí výraz, který se má shodovat, *název* je název zachytávající skupiny, *Ano* je řetězec, který se má shodovat, pokud je *výraz* shodný nebo je *název* platnou neprázdnou zachycenou skupinou a *ne* je dílčí výraz, který se má shodovat, pokud se *výraz* neshoduje nebo *název* není platná zachycená skupina, která není prázdná. Tato funkce umožňuje modulu vyhledávat pomocí více než jednoho alternativního vzoru, v závislosti na výsledku předchozího dílčího výrazu nebo výsledku kontrolního výrazu s nulovou šířkou. To umožňuje výkonnější formu zpětného odkazování, které umožňuje například porovnání dílčího výrazu na základě toho, zda byl předchozí dílčí výraz spárován. Regulární výraz v následujícím příkladu odpovídá odstavcům, které jsou určeny pro veřejné i interní použití. Odstavce určené pouze pro interní použití začínají `<PRIVATE>` značkou. Vzor `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` regulárního výrazu používá podmíněné vyhodnocení k přiřazení obsahu odstavců, které jsou určené pro veřejné a pro interní použití k oddělení zachycujících skupin. Tyto odstavce pak můžete zpracovat odlišně.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Zahájí porovnávání na začátku řádku.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Porovná žádný nebo jeden výskyt řetězce `<PRIVATE>` následovaný prázdným znakem. Přiřaďte shodu k zachycené skupině `Pvt`s názvem.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|`Pvt` Pokud zachytávající skupina existuje, porovná jeden nebo více výskytů jednoho nebo více znaků slova následovaných žádným nebo jedním oddělovačem interpunkce následovaným prázdným znakem. Přiřaďte dílčí řetězec k první zachytávající skupině.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|`Pvt` Pokud zachytávající skupina neexistuje, porovná jeden nebo více výskytů jednoho nebo více znaků slova následovaných žádným nebo jedním oddělovačem interpunkce následovaným prázdným znakem. Přiřaďte podřetězec třetí zachytávající skupině.|  
    |`\r?$`|Odpovídá konci řádku nebo konci řetězce.|  
  
     Další informace o podmíněném vyhodnocení naleznete v tématu [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
- Definice vyrovnávání `(?<`skupin: dílčí`>` *výraz*`-` název1`)`název2. Tato funkce umožňuje modulu regulárních výrazů sledovat vnořené konstrukce, jako jsou závorky nebo levou a pravou hranaté závorky. Příklad naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Dílčí výrazy bez mechanismu navracení (označují se také jako hladové podvýrazy `(?>`): dílčí *výraz*`)`. Tato funkce umožňuje modulu zpětného navrácení, aby se zaručilo, že dílčí výraz odpovídá pouze první shodě nalezené pro tento dílčí výraz, jako kdyby byl výraz spuštěn nezávisle na jeho obsahujícím výrazu. Pokud nepoužijete tuto konstrukci, hledání zpětného navrácení z většího výrazu může změnit chování dílčího výrazu. Například regulární výraz `(a+)\w` odpovídá jednomu nebo více znakům "a" společně se znakem slova, který následuje za sekvencí "a" a přiřadí sekvenci "a" do první zachytávající skupiny, ale pokud konečný znak vstupní řetězec je také "a", `\w` odpovídá prvku jazyka a není zahrnutý v zachycené skupině.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Regulární výraz `((?>a+))\w` zabrání tomuto chování. Vzhledem k tomu, že všechny po sobě jdoucí "a" znaky se shodují bez navrácení, první zachytávající skupina zahrnuje všechny po sobě jdoucí znaky "a". Pokud za znaky "a" nenásleduje aspoň jeden další znak jiný než "a", shoda se nezdařila.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Další informace o podvýrazech převracení naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Shoda zprava doleva, která je určena <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> zadáním možnosti konstruktoru <xref:System.Text.RegularExpressions.Regex> třídy nebo metody pro porovnání statických instancí. Tato funkce je užitečná při hledání zprava doleva, nikoli zleva doprava, nebo v případech, kdy je efektivnější zahájit shodu v pravé části vzoru namísto levého. Jak ukazuje následující příklad, použití spárování zprava doleva může změnit chování hladových kvantifikátorů. V tomto příkladu se provádí dvě hledání věty, která končí číslem. Hledání zleva doprava, které používá hladce `+` , odpovídá jedné ze šesti číslic ve větě, zatímco hledání zprava doleva se shoduje se všemi šesti číslicemi. Popis vzoru regulárního výrazu naleznete v příkladu, který ukazuje opožděné kvantifikátory dříve v této části.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Další informace o porovnání zprava doleva naleznete v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
- Pozitivní a negativní zpětné vyhledávání `(?<=`: dílčí *výraz* `)` pro pozitivní zpětné vyhledávání `(?<!`a dílčí *výraz* `)` pro negativní zpětné vyhledávání. Tato funkce se podobá dopřednému vyhledávání, který je popsaný výše v tomto tématu. Vzhledem k tomu, že modul regulárních výrazů umožňuje úplné porovnání zprava doleva, regulární výrazy povolují neomezený lookbehinds. Kladné a záporné zpětné vyhledávání lze také použít k zamezení vnořování kvantifikátorů, je-li vnořený dílčí výraz nadmnožinou vnějšího výrazu. Regulární výrazy s takovými vnořenými kvantifikátory často nabízejí nízký výkon. Například následující příklad ověřuje, že řetězec začíná a končí alfanumerickým znakem a že jakýkoli jiný znak v řetězci je jedna z větší podmnožiny. Tvoří část regulárního výrazu, který slouží k ověření e-mailových adres. Další informace naleznete v tématu [How to: Ověřte, že jsou řetězce v platném](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)formátu e-mailu.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Regulární výraz ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` je definován tak, jak je uvedeno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |`^`|Zahajte shodu na začátku řetězce.|  
    |`[A-Z0-9]`|Odpovídá jakémukoli číselnému nebo alfanumerickému znaku. (Porovnání nerozlišuje malá a velká písmena.)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Porovná žádný nebo více výskytů libovolného znaku slova nebo jakýkoli z následujících znaků:-,!, #, $,%, &, ',., \*, +,/, =,?, ^, \`, {,}, &#124;nebo ~.|  
    |`(?<=[A-Z0-9])`|Prohlédněte si předchozí znak, který musí být numerický nebo alfanumerický. (Porovnání nerozlišuje malá a velká písmena.)|  
    |`$`|Ukončí porovnávání na konci řetězce.|  
  
     Další informace o pozitivním a negativním zpětném vyhledávání najdete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Poskytuje informace o tom, jak se ve výrazech zpětného navrácení větví regulárních výrazů hledají alternativní shody.|  
|[Kompilace a opětovné používání](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Poskytuje informace o kompilaci a opětovném použití regulárních výrazů ke zvýšení výkonu.|  
|[Bezpečnost vlákna](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Poskytuje informace o bezpečnosti vláken regulárních výrazů a vysvětluje, kdy byste měli synchronizovat přístup k objektům regulárních výrazů.|  
|[.NET Framework regulární výrazy](../../../docs/standard/base-types/regular-expressions.md)|Poskytuje přehled aspektů regulárních výrazů programovacího jazyka.|  
|[Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Poskytuje informace a příklady kódu ilustrující použití tříd regulárních výrazů.|  
|[Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md)|Obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžných aplikacích.|  
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Poskytuje informace o sadě znaků, operátorech a konstrukcích, které lze použít k definování regulárních výrazů.|  
  
## <a name="reference"></a>Reference  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
