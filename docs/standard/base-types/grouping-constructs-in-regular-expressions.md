---
title: Seskupovací konstrukce v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 8bf6870e3eb3ef65b498f431cb2b8805eee7ec3c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140113"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Seskupovací konstrukce v regulárních výrazech
Seskupovací konstrukce vymezují dílčí výrazy regulárního výrazu a zachycují podřetězce vstupního řetězce. Konstrukce seskupení lze použít k následujícím akcím:  
  
- Porovnává dílčí výraz, který se opakuje ve vstupním řetězci.  
  
- Použijte kvantifikátor na dílčí výraz, který má více prvků jazyka regulárních výrazů. Další informace o kvantifikátorech naleznete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Zahrňte dílčí výraz do řetězce, který je vrácený metodami <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>.  
  
- Načte jednotlivé dílčí výrazy z vlastnosti <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> a zpracuje je odděleně od odpovídajícího textu jako celku.  
  
 V následující tabulce jsou uvedeny seskupovací konstrukce podporované modulem regulárních výrazů .NET a označuje, zda jsou zaznamenávány nebo nejsou zaznamenávány.  
  
|Seskupovací konstrukce|Zachycení nebo nezachycení|  
|------------------------|-------------------------------|  
|[Odpovídající podvýrazy](#matched_subexpression)|Zachytávání|  
|[Pojmenované odpovídající podvýrazy](#named_matched_subexpression)|Zachytávání|  
|[Vyrovnávání definic skupin](#balancing_group_definition)|Zachytávání|  
|[Skupiny bez zachycení](#noncapturing_group)|Nezachycující|  
|[Možnosti skupiny](#group_options)|Nezachycující|  
|[Pozitivní kontrolní výrazy dopředného vyhledávání s nulovou šířkou](#zerowidth_positive_lookahead_assertion)|Nezachycující|  
|[Negativní kontrolní výrazy dopředného vyhledávání s nulovou šířkou](#zerowidth_negative_lookahead_assertion)|Nezachycující|  
|[Pozitivní kontrolní výrazy zpětného vyhledávání s nulovou šířkou](#zerowidth_positive_lookbehind_assertion)|Nezachycující|  
|[Negativní kontrolní výrazy zpětného vyhledávání s nulovou šířkou](#zerowidth_negative_lookbehind_assertion)|Nezachycující|  
|[Dílčí výrazy bez mechanismu navracení](#nonbacktracking_subexpression)|Nezachycující|  
  
 Informace o skupinách a modelu objektu regulárních výrazů naleznete v tématu [seskupovací konstrukce a objekty regulárních výrazů](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Odpovídající podvýrazy  
 Následující seskupovací konstrukce zachytí odpovídající dílčí výraz:  
  
 `(` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný platný vzor regulárního výrazu. Zachycení, která používají kulaté závorky, jsou automaticky číslovány zleva doprava na základě pořadí otevíracích závorek v regulárním výrazu, počínaje od jednoho. Záznam s číslem nula je text, který odpovídá celému vzoru regulárního výrazu.  
  
> [!NOTE]
> Ve výchozím nastavení `(`dílčí *výraz*`)` prvek jazyka zachytí odpovídající dílčí výraz. Pokud ale parametr <xref:System.Text.RegularExpressions.RegexOptions> metody porovnávání vzorů regulárních výrazů obsahuje příznak <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> nebo pokud je pro tento dílčí výraz použita možnost `n` (viz [Možnosti skupiny](#group_options) dále v tomto tématu), odpovídající dílčí výraz není zachycen.  
  
 Zachycené skupiny můžete získat čtyřmi způsoby:  
  
- Pomocí konstrukce zpětných odkazů v rámci regulárního výrazu. Odpovídající dílčí výraz je odkazován ve stejném regulárním výrazu pomocí syntaxe `\`*číslo*, kde *Number* je pořadové číslo zachyceného dílčího výrazu.  
  
- Pomocí pojmenované konstrukce zpětného odkazu v rámci regulárního výrazu. Odpovídající dílčí výraz je odkazován ve stejném regulárním výrazu pomocí syntaxe `\k<`*název*`>`, kde *název* je název zachytávající skupiny nebo `\k<`*číslo*`>`, kde number je pořadové *číslo* číslo zachytávající skupiny. Zachytávající skupina má výchozí název, který je totožný s pořadovým číslem. Další informace naleznete v části [pojmenované odpovídající podvýrazy](#named_matched_subexpression) dále v tomto tématu.  
  
- Pomocí sekvence nahrazení `$`ho *čísla* ve volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>, kde *Number* je pořadové číslo zachyceného dílčího výrazu.  
  
- Programově pomocí objektu <xref:System.Text.RegularExpressions.GroupCollection> vráceného vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. Člen na pozici nula v kolekci představuje celou shodu regulárního výrazu. Každý další člen představuje odpovídající dílčí výraz. Další informace naleznete v části [seskupovací konstrukce a objekty regulárních výrazů](#Objects) .  
  
 Následující příklad ilustruje regulární výraz, který identifikuje duplicitní slova v textu. Dvě zachytávající skupiny vzoru regulárního výrazu reprezentují dvě instance duplikovaného slova. Druhá instance je zachycena pro hlášení počáteční pozice ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Vzor regulárního výrazu je následující:  
  
`(\w+)\s(\1)\W`  
  
 Následující tabulka ukazuje, jak je interpretován vzor regulárního výrazu.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\1)`|Porovnává s řetězcem v první zachycené skupině. Toto je druhá zachytávající skupina. Tento příklad přiřadí k zachycené skupině, aby bylo možné načíst počáteční pozici duplicitního slova z vlastnosti `Match.Index`.|  
|`\W`|Porovnává znak, který není slovní, včetně mezer a interpunkce. To brání vzoru regulárního výrazu v porovnání s slovem, které začíná slovem z první zachycené skupiny.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>Pojmenované odpovídající podvýrazy  
 Následující seskupovací konstrukce zachytí odpovídající dílčí výraz a umožní vám k němu přistupovat podle názvu nebo čísla:  
  
`(?<name>subexpression)`  
  
 nebo:  
  
`(?'name'subexpression)`  
  
 kde *Name* je platný název skupiny a dílčí *výraz* je libovolný platný vzor regulárního výrazu. *název* nesmí obsahovat žádné znaky interpunkce a nesmí začínat číslicí.  
  
> [!NOTE]
> Pokud parametr <xref:System.Text.RegularExpressions.RegexOptions> metody porovnávání vzorů regulárních výrazů obsahuje příznak <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nebo pokud je pro tento dílčí výraz použita možnost `n` (viz [Možnosti skupiny](#group_options) dále v tomto tématu), jediný způsob zachycení dílčího výrazu je explicitní pojmenování zachycujících skupin.  
  
 Pojmenované zachycené skupiny můžete získat následujícími způsoby:  
  
- Pomocí pojmenované konstrukce zpětného odkazu v rámci regulárního výrazu. Odpovídající dílčí výraz je odkazován ve stejném regulárním výrazu pomocí syntaxe `\k<`*název*`>`, kde *název* je název zachyceného dílčího výrazu.  
  
- Pomocí konstrukce zpětných odkazů v rámci regulárního výrazu. Odpovídající dílčí výraz je odkazován ve stejném regulárním výrazu pomocí syntaxe `\`*číslo*, kde *Number* je pořadové číslo zachyceného dílčího výrazu. Pojmenované odpovídající podvýrazy jsou po sobě řazeny po odpovídajících podvýrazech očíslovány zleva doprava.  
  
- Pomocí `${`*název*`}` sekvenci nahrazení ve volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>, kde *název* je název zachyceného dílčího výrazu.  
  
- Pomocí sekvence nahrazení `$`ho *čísla* ve volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>, kde *Number* je pořadové číslo zachyceného dílčího výrazu.  
  
- Programově pomocí objektu <xref:System.Text.RegularExpressions.GroupCollection> vráceného vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. Člen na pozici nula v kolekci představuje celou shodu regulárního výrazu. Každý další člen představuje odpovídající dílčí výraz. Pojmenované zachycené skupiny jsou uloženy v kolekci po číslovaných zachycených skupinách.  
  
- Prostřednictvím kódu programu zadáním názvu dílčího výrazu k indexeru objektu <xref:System.Text.RegularExpressions.GroupCollection> (v C#) nebo k jeho vlastnosti <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> (v Visual Basic).  
  
 Jednoduchý vzor regulárního výrazu ukazuje, jak číslované (nepojmenované) a pojmenované skupiny lze odkazovat buď programově nebo pomocí syntaxe regulárního výrazu. Regulární výraz `((?<One>abc)\d+)?(?<Two>xyz)(.*)` vytváří následující zachytávající skupiny podle čísla a podle názvu. První zachytávající skupina (číslo 0) vždy odkazuje na celý vzor.  
  
|Číslo|Name|Vzor|  
|------------|----------|-------------|  
|0,8|0 (výchozí název)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|první|1 (výchozí název)|`((?<One>abc)\d+)`|  
|odst|2 (výchozí název)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Druhá|`(?<Two>xyz)`|  
  
 Následující příklad ilustruje regulární výraz, který identifikuje duplicitní slova a slovo, které bezprostředně následuje po každém duplicitním slově. Vzor regulárního výrazu definuje dva pojmenované dílčí výrazy: `duplicateWord`, které představují duplicitní slovo; a `nextWord`, který představuje slovo, které následuje za duplikovaným slovem.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Vzor regulárního výrazu je následující:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Následující tabulka ukazuje, jak je interpretován regulární výraz.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto zachytávající skupinu `duplicateWord`.|  
|`\s`|Porovná prázdný znak.|  
|`\k<duplicateWord>`|Porovnává řetězec ze zachycené skupiny s názvem `duplicateWord`.|  
|`\W`|Porovnává znak, který není slovní, včetně mezer a interpunkce. To brání vzoru regulárního výrazu v porovnání s slovem, které začíná slovem z první zachycené skupiny.|  
|`(?<nextWord>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto zachytávající skupinu `nextWord`.|  
  
 Všimněte si, že název skupiny se může opakovat v regulárním výrazu. Například je možné pro více než jednu skupinu pojmenovat `digit`, jak ukazuje následující příklad. V případě duplicitních názvů je hodnota objektu <xref:System.Text.RegularExpressions.Group> určena posledním úspěšným zachycením ve vstupním řetězci. <xref:System.Text.RegularExpressions.CaptureCollection> se navíc naplní informacemi o každém zachycení, stejně jako by se jednalo o duplicitní název skupiny.  
  
 V následujícím příkladu regulární výraz `\D+(?<digit>\d+)\D+(?<digit>\d+)?` obsahuje dva výskyty skupiny s názvem `digit`. První `digit` pojmenovaná skupina zachycuje jeden nebo více znaků číslic. Druhá `digit` pojmenovaná skupina zachycuje buď žádný nebo jeden výskyt jednoho nebo více znaků číslic. Jak ukazuje výstup z příkladu, pokud druhá zachytávající skupina úspěšně odpovídá textu, hodnota tohoto textu definuje hodnotu objektu <xref:System.Text.RegularExpressions.Group>. Pokud druhá zachytávající skupina nemůže odpovídat vstupnímu řetězci, hodnota poslední úspěšné shody definuje hodnotu objektu <xref:System.Text.RegularExpressions.Group>.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Následující tabulka ukazuje, jak je interpretován regulární výraz.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\D+`|Porovnává jeden nebo více znaků, které nejsou desítkové číslice.|  
|`(?<digit>\d+)`|Porovnává jeden nebo více desítkových znaků. Přiřaďte shodu k `digit` pojmenované skupině.|  
|`\D+`|Porovnává jeden nebo více znaků, které nejsou desítkové číslice.|  
|`(?<digit>\d+)?`|Porovná žádný nebo jeden výskyt jednoho nebo více znaků desítkové číslice. Přiřaďte shodu k `digit` pojmenované skupině.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Vyrovnávání definic skupin  
 Vyrovnávací Seskupovací definice odstraní definici dříve definované skupiny a obchodů v aktuální skupině, interval mezi dříve definovanou skupinou a aktuální skupinou. Tato seskupovací konstrukce má následující formát:  
  
`(?<name1-name2>subexpression)`  
  
 nebo:  
  
`(?'name1-name2' subexpression)`
  
 kde *název1* je aktuální skupina (volitelné), *název2* je dříve definovaná skupina a dílčí *výraz* je libovolný platný vzor regulárního výrazu. Vyrovnávací Seskupovací definice odstraní definici *název2* a uloží interval mezi *název2* a *název1* v poli *název1*. Pokud není definována žádná skupina *název2* , porovnávání se zaznamená. Vzhledem k tomu, že odstranění poslední definice *název2* odhalí předchozí definici *název2*, Tato konstrukce vám umožní použít zásobník zachycení pro skupinu *název2* jako čítač pro udržení přehledu o vnořených konstrukcích, jako jsou závorky nebo otevírání. a uzavírací závorky.  
  
 Vyrovnávací Seskupovací definice používá *název2* jako zásobník. Počáteční znak každé vnořené konstrukce se umístí do skupiny a do kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>. Při porovnání uzavíracího znaku je jeho odpovídající znak otevření ze skupiny odebrán a kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A> poklesla o jednu. Po porovnání znaků pro otevření a ukončení všech vnořených konstrukcí je *název2* prázdné.  
  
> [!NOTE]
> Po úpravě regulárního výrazu v následujícím příkladu pro použití vhodného otevíracího a ukončovacího znaku vnořené konstrukce lze použít pro zpracování většiny vnořených konstrukcí, jako jsou matematické výrazy nebo řádky kódu programu, které zahrnují Vícenásobná volání vnořených metod  
  
 V následujícím příkladu je použita definice vyrovnávací skupiny tak, aby odpovídala levou a pravou lomenou závorku (< >) ve vstupním řetězci. V příkladu jsou definovány dvě pojmenované skupiny, `Open` a `Close`, které se používají jako zásobník pro sledování párů s odpovídajícími páry lomených závorek. Každá zachycená levá lomená závorka je vložena do kolekce zachycení skupiny `Open` a každá zachycená Pravá lomená závorka je vložena do kolekce zachycení `Close` skupiny. Definice vyrovnávací skupiny zajišťuje odpovídající pravou ostrou závorku pro každou levou lomenou závorku. Pokud není, konečný dílčí vzor `(?(Open)(?!))`, je vyhodnocen pouze v případě, že skupina `Open` není prázdná (a proto, pokud nebyly všechny vnořené konstrukce uzavřeny). Pokud je výsledný dílčí vzor vyhodnocován, shoda se nezdařila, protože dílčí vzor `(?!)` je negativním kontrolním výrazem dopředného vyhledávání s nulovou šířkou, který vždy selhává.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Vzor regulárního výrazu je:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Regulární výraz je interpretován následujícím způsobem:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začněte na začátku řetězce.|  
|`[^<>]*`|Porovná žádný nebo více znaků, které nejsou levou nebo pravou lomenou závorku.|  
|`(?'Open'<)`|Porovnává levou ostrou závorku a přiřadí ji do skupiny s názvem `Open`.|  
|`[^<>]*`|Porovná žádný nebo více znaků, které nejsou levou nebo pravou lomenou závorku.|  
|`((?'Open'<)[^<>]*)+`|Porovná jeden nebo více výskytů levé lomené závorky, za kterými následuje nula nebo více znaků, které nejsou levou nebo pravou lomenou závorku. Toto je druhá zachytávající skupina.|  
|`(?'Close-Open'>)`|Porovnává pravou ostrou závorku, přiřadí podřetězec mezi `Open` skupinu a aktuální skupinou do `Close` skupiny a odstraní definici `Open` skupiny.|  
|`[^<>]*`|Porovná žádný nebo více výskytů libovolného znaku, který není levou ani pravou ostrou závorkou.|  
|`((?'Close-Open'>)[^<>]*)+`|Porovná jeden nebo více výskytů pravé lomené závorky, za kterými následuje nula nebo více výskytů libovolného znaku, který není levou ani pravou ostrou závorkou. Při porovnání pravé lomené závorky přiřaďte podřetězec mezi `Open` skupinou a aktuální skupinou do skupiny `Close` a odstraňte definici `Open` skupiny. Toto je třetí zachytávající skupina.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Porovná žádný nebo více výskytů následujícího vzoru: jeden nebo více výskytů levé lomené závorky, za kterými následuje nula nebo více znaků bez lomené závorky následované jedním nebo více výskyty pravé lomené závorky, za kterým následuje nula nebo více výskytů. mimo lomené závorky. Při porovnání pravé lomené závorky odstraňte definici `Open` skupiny a podřetězec mezi `Open` skupinou a aktuální skupinou přiřaďte do skupiny `Close`. Toto je první zachytávající skupina.|  
|`(?(Open)(?!))`|Pokud `Open` skupina existuje, přenechání shody, pokud je možné spárovat prázdný řetězec, ale nezadávejte pozici modulu regulárních výrazů do řetězce. Toto je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou. Vzhledem k tomu, že prázdný řetězec je vždy implicitně přítomen ve vstupním řetězci, tato shoda se vždy nezdařila. Selhání této shody znamená, že lomené závorky nejsou vyrovnané.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Konečný dílčí výraz, `(?(Open)(?!))`, označuje, zda jsou vnořené konstrukce ve vstupním řetězci správně vyváženy (například zda je každá levá lomená závorka shodná s pravou ostrou závorkou). Používá podmíněné porovnání na základě platné zachycené skupiny; Další informace naleznete v tématu [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Pokud je definována skupina `Open`, modul regulárních výrazů se pokusí porovnat dílčí výraz `(?!)` ve vstupním řetězci. `Open` skupina by měla být definována pouze v případě, že vnořování konstrukcí jsou nevyvážené. Proto by vzor, který má být porovnán ve vstupním řetězci, měl být ten, který vždy způsobí selhání shody. V tomto případě je `(?!)` kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který se vždy nezdařil, protože prázdný řetězec je vždy implicitně přítomen na další pozici ve vstupním řetězci.  
  
 V tomto příkladu modul regulárních výrazů vyhodnocuje vstupní řetězec "\<ABC > < mno\<XYZ > >", jak je znázorněno v následující tabulce.  
  
|Krok|Vzor|Výsledek|  
|----------|-------------|------------|  
|první|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|odst|`[^<>]*`|Vyhledá znaky bez lomené závorky před levou lomenou závorkou; nenajde žádné shody.|  
|3|`(((?'Open'<)`|Porovná levou ostrou závorku v řetězci "\<ABC >" a přiřadí ji ke skupině `Open`.|  
|4|`[^<>]*`|Odpovídá "ABC".|  
|5|`)+`|"< ABC" je hodnota druhé zachycené skupiny.<br /><br /> Další znak ve vstupním řetězci není levá lomená závorka, takže modul regulárních výrazů nevrátí zpět do dílčího vzoru `(?'Open'<)[^<>]*)`.|  
|6|`((?'Close-Open'>)`|Porovná pravou ostrou závorku v "\<ABC >", přiřadí "ABC", což je podřetězec mezi `Open` skupinou a pravou ostrou závorkou, do skupiny `Close` a odstraní aktuální hodnotu ("<") skupiny `Open` , takže je ponechána prázdná.|  
|čl|`[^<>]*`|Vyhledá znaky bez lomené závorky za pravou ostrou závorkou; nenajde žádné shody.|  
|8|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravá lomená závorka, takže modul regulárních výrazů nevrátí zpět do dílčího vzoru `((?'Close-Open'>)[^<>]*)`.|  
|9|`)*`|Hodnota první zachycené skupiny je "\<ABC >".<br /><br /> Dalším znakem ve vstupním řetězci je levá lomená závorka, takže modul regulárních výrazů se vrátí do `(((?'Open'<)` dílčího vzoru.|  
|10pruhový|`(((?'Open'<)`|Porovná levou ostrou závorku v řetězci "\<mno" a přiřadí ji do skupiny `Open`. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce teď má jednu hodnotu "<".|  
|odst|`[^<>]*`|Odpovídá "mno".|  
|12,5|`)+`|"< mno" je hodnota druhé zachycené skupiny.<br /><br /> Dalším znakem ve vstupním řetězci je levá lomená závorka, takže modul regulárních výrazů se vrátí do `(?'Open'<)[^<>]*)` dílčího vzoru.|  
|13,5|`(((?'Open'<)`|Porovná levou ostrou závorku v "\<> xyz" a přiřadí ji ke skupině `Open`. Kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> skupiny `Open` nyní obsahuje dvě zachycení: levou lomenou závorku z "\<mno" a levou ostrou závorku z "\<XYZ >".|  
|čtrnáct|`[^<>]*`|Odpovídá "xyz".|  
|15|`)+`|"< xyz" je hodnota druhé zachycené skupiny.<br /><br /> Další znak ve vstupním řetězci není levá lomená závorka, takže modul regulárních výrazů nevrátí zpět do dílčího vzoru `(?'Open'<)[^<>]*)`.|  
|16bitovém|`((?'Close-Open'>)`|Porovná pravou ostrou závorku v\<XYZ >. "xyz" přiřadí podřetězec mezi `Open` skupinou a pravou ostrou závorkou do skupiny `Close` a odstraní aktuální hodnotu skupiny `Open`. Hodnota předchozího zachycení (levá lomená závorka v "\<mno") se stala aktuální hodnotou `Open` skupiny. Kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A> skupiny `Open` nyní obsahuje jedno zachycení, levou hranatou závorku z "\<XYZ >".|  
|sedmnáct|`[^<>]*`|Hledá znaky, které nejsou lomené závorky. nenajde žádné shody.|  
|let|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Dalším znakem ve vstupním řetězci je Pravá lomená závorka, takže modul regulárních výrazů se vrátí do `((?'Close-Open'>)[^<>]*)` dílčího vzoru.|  
|čl|`((?'Close-Open'>)`|Odpovídá konečné pravé lomené závorce v "XYZ > >" přiřadí "mno\<XYZ >" (podřetězec mezi skupinou `Open` a pravou ostrou závorkou) do skupiny `Close` a odstraní aktuální hodnotu skupiny `Open`. `Open` skupina je teď prázdná.|  
|20o|`[^<>]*`|Hledá znaky, které nejsou lomené závorky. nenajde žádné shody.|  
|20|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravá lomená závorka, takže modul regulárních výrazů nevrátí zpět do dílčího vzoru `((?'Close-Open'>)[^<>]*)`.|  
|22|`)*`|Hodnota první zachycené skupiny je "< mno\<XYZ > >".<br /><br /> Další znak ve vstupním řetězci není levá lomená závorka, takže modul regulárních výrazů nevrátí zpět do dílčího vzoru `(((?'Open'<)`.|  
|listopadu|`(?(Open)(?!))`|Skupina `Open` není definována, takže se nezkouší žádná shoda.|  
|24|`$`|Odpovídá konci vstupního řetězce.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Skupiny bez zachycení  
 Následující seskupovací konstrukce nezachycuje podřetězec, který odpovídá dílčímu výrazu:  
  
`(?:subexpression)`
  
 kde dílčí *výraz* je libovolný platný vzor regulárního výrazu. Konstrukce nezachytávající skupiny se obvykle používá při použití kvantifikátoru na skupinu, ale podřetězce zachycené skupinou nejsou žádného zájmu.  
  
> [!NOTE]
> Pokud regulární výraz obsahuje vnořené seskupovací konstrukce, vnější konstrukce nezachytávající skupinu se nevztahuje na vnitřní vnořené konstrukce skupiny.  
  
 Následující příklad znázorňuje regulární výraz, který zahrnuje nezachytávající skupiny. Všimněte si, že výstup neobsahuje žádné zachycené skupiny.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Regulární výraz `(?:\b(?:\w+)\W*)+\.` odpovídá větě, která je ukončena tečkou. Vzhledem k tomu, že regulární výraz se zaměřuje na věty a ne na jednotlivá slova, seskupovací konstrukce se používají výhradně jako kvantifikátory. Vzor regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?:\w+)`|Porovná jeden nebo více znaků slova. Nepřiřazujte odpovídající text na zachycenou skupinu.|  
|`\W*`|Porovná žádný nebo více znaků, které nejsou ve slovech.|  
|`(?:\b(?:\w+)\W*)+`|Porovná vzor jednoho nebo více slovních znaků počínaje hranicí slova, za nímž následuje nula nebo více znaků bez slova, jednou nebo vícekrát. Nepřiřazujte odpovídající text na zachycenou skupinu.|  
|`\.`|Odpovídá tečkě.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Možnosti skupiny  
 Následující seskupovací konstrukce aplikuje nebo zakáže zadané možnosti v rámci dílčího výrazu:  
  
 `(?imnsx-imnsx:` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný platný vzor regulárního výrazu. `(?i-s:)` například zapne nerozlišování velkých a malých písmen a zakáže jednořádkový režim. Další informace o vložených možnostech, které můžete zadat, najdete v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Můžete určit možnosti, které se vztahují na celý regulární výraz místo dílčího výrazu pomocí konstruktoru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy nebo statické metody. Můžete také zadat vložené možnosti, které se použijí po určitém místě regulárního výrazu pomocí konstrukce jazyka `(?imnsx-imnsx)`.  
  
 Konstrukce možností skupiny není zachytávající skupina. To znamená, že i když je část řetězce zachycená *podvýrazem* obsažena v shodě, není obsažena v zachycené skupině ani použita k naplnění objektu <xref:System.Text.RegularExpressions.GroupCollection>.  
  
 Například regulární výraz `\b(?ix: d \w+)\s` v následujícím příkladu používá vložené možnosti v seskupovací konstrukci pro povolení porovnávání bez rozlišování velkých a malých písmen v identifikaci všech slov, která začínají písmenem "d". Regulární výraz je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?ix: d \w+)`|Použití porovnávání bez rozlišení velkých a malých písmen v tomto vzoru se shoduje s písmenem "d" následovaným jedním nebo více znaky slova.|  
|`\s`|Porovná prázdný znak.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Pozitivní kontrolní výrazy dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou:  
  
 `(?=` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný vzor regulárního výrazu. Aby shoda byla úspěšná, vstupní řetězec musí odpovídat vzoru regulárního výrazu v *podvýrazu*, i když odpovídající podřetězec není zahrnutý ve výsledku shody. Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou nevrací.  
  
 Obvykle je kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou nalezen na konci vzoru regulárního výrazu. Definuje podřetězec, který musí být nalezen na konci řetězce, aby došlo ke shodě, ale který by neměl být zahrnut do shody. Je to také užitečné pro zabránění nadměrnému navrácení. Můžete použít kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou pro zajištění, že konkrétní zachycená skupina začíná textem, který odpovídá podmnožině vzoru definované pro tuto zachycenou skupinu. Například pokud zachytávající skupina odpovídá po sobě jdoucích znaků slova, můžete použít kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou pro vyžadování prvního znaku na abecedním znaku.  
  
 Následující příklad používá kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou, aby odpovídal slovu, které předchází příkazu "is" ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Regulární výraz `\b\w+(?=\sis\b)` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(?=\sis\b)`|Určí, zda jsou znaky slova následovány prázdným znakem a řetězcem "is", který končí na hranici slova. V takovém případě je shoda úspěšná.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Negativní kontrolní výrazy dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou:  
  
 `(?!` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný vzor regulárního výrazu. Aby shoda byla úspěšná, vstupní řetězec nesmí odpovídat vzoru regulárního výrazu v *podvýrazu*, i když odpovídající řetězec není zahrnutý ve výsledku shody.  
  
 Negativní kontrolní výraz dopředného vyhledávání s nulovou šířkou se obvykle používá buď na začátku nebo na konci regulárního výrazu. Na začátku regulárního výrazu může definovat konkrétní vzor, který by neměl být spárován, pokud začátek regulárního výrazu definuje podobný, ale obecnější vzor, který se má shodovat. V takovém případě se často používá k omezení zpětného navrácení. Na konci regulárního výrazu může definovat dílčí výraz, který nemůže být proveden na konci porovnávání.  
  
 Následující příklad definuje regulární výraz, který používá kontrolní výraz dopředného vyhledávání s nulovou šířkou na začátku regulárního výrazu, aby odpovídal slovům, která nezačínají na "un".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Regulární výraz `\b(?!un)\w+\b` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?!un)`|Určí, zda jsou následující dva znaky "un". Pokud nejsou, je možné, že je shoda.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Následující příklad definuje regulární výraz, který používá kontrolní výraz dopředného vyhledávání s nulovou šířkou na konci regulárního výrazu, aby odpovídal slovům, která nekončí znakem interpunkce.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Regulární výraz `\b\w+\b(?!\p{P})` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`\p{P})`|Pokud další znak není symbol interpunkce (například tečka nebo čárka), shoda se zdaří.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Pozitivní kontrolní výrazy zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<=` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný vzor regulárního výrazu. Aby byla shoda úspěšná, musí se dílčí *výraz* vyskytovat ve vstupním řetězci nalevo od aktuální pozice, i když `subexpression` není zahrnut ve výsledku shody. Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou nevrací.  
  
 Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou jsou obvykle používány na začátku regulárních výrazů. Vzor, který definuje, je podmínkou pro shodu, ačkoli se nejedná o součást výsledku shody.  
  
 Například následující příklad odpovídá poslední dvě číslice roku pro dvacátý první století (to znamená, že číslice "20" předcházejí odpovídajícím řetězcem).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Vzor regulárního výrazu `(?<=\b20)\d{2}\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\d{2}`|Porovnává dvě desítkové číslice.|  
|`(?<=\b20)`|Pokračovat v porovnávání, pokud se dvě desítkové číslice předcházejí desítkovými číslicemi "20" na hranici slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou slouží také k omezení zpětného navrácení, pokud poslední znak nebo znaky v zachycené skupině musí být podmnožinou znaků, které odpovídají vzoru regulárního výrazu dané skupiny. Například pokud skupina zachytává všechny po sobě jdoucí znaky slova, můžete použít kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou pro vyžadování, aby byl poslední znak seřazený podle abecedy.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Negativní kontrolní výrazy zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<!` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný vzor regulárního výrazu. Aby porovnávání bylo úspěšné, nesmí se dílčí *výraz* vyskytovat ve vstupním řetězci nalevo od aktuální pozice. Nicméně jakýkoli podřetězec, který neodpovídá `subexpression`, není zahrnut ve výsledku shody.  
  
 Negativní kontrolní výrazy zpětného vyhledávání s nulovou šířkou jsou obvykle používány na začátku regulárních výrazů. Vzor, který definuje, vylučuje shodu v řetězci, který následuje. Používají se také k omezení zpětného navrácení, pokud poslední znak nebo znaky v zachycené skupině nesmí být jedním nebo více znaky, které odpovídají vzoru regulárního výrazu dané skupiny. Například pokud skupina zachytává všechny po sobě jdoucí znaky slova, můžete použít kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou pro vyžadování, aby poslední znak nebyl podtržítkem (\_).  
  
 Následující příklad se shoduje s datem pro každý den v týdnu, který není víkend (tj. není to sobota ani neděle).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Vzor regulárního výrazu `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovnává jeden nebo více slovních znaků následovaných prázdným znakem.|  
|`\d{1,2},`|Porovnává buď jednu, nebo dvě desítkové číslice následovanou prázdným znakem a čárkou.|  
|`\d{4}\b`|Porovnává čtyři desítkové číslice a ukončí porovnávání na hranici slova.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Pokud shoda předchází jiné než řetězce "Sobota" nebo "neděle" následovaný mezerou, shoda je úspěšná.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Dílčí výrazy bez mechanismu navracení  
 Následující seskupovací konstrukce představuje dílčí výraz bez mechanismu navracení (označuje se také jako "hladec"):  
  
 `(?>` dílčí *výraz* `)`  
  
 kde dílčí *výraz* je libovolný vzor regulárního výrazu.  
  
 Obvykle, pokud regulární výraz obsahuje volitelný nebo alternativní odpovídající vzor a shoda není úspěšná, modul regulárních výrazů může vytvořit větve ve více směrech, aby odpovídal vstupnímu řetězci se vzorem. Pokud se shoda nenajde, když vezme první větev, modul regulárních výrazů může zálohovat nebo přesměrovat do bodu, kde trvalo první shodě, a pokusit se o shodu pomocí druhé větve. Tento proces může pokračovat, dokud nebudou všechny větve vyzkoušeny.  
  
 Konstrukce jazyka`)` `(?>`dílčího *výrazu* zakáže zpětné navrácení. Modul regulárních výrazů bude odpovídat počtu znaků ve vstupním řetězci, jak může. V případě, že žádná další shoda není možná, nebude při pokusu o alternativní porovnávání vzorů navázáno. (To znamená, že dílčí výraz odpovídá pouze řetězcům, které by odpovídaly samotnému dílčímu výrazu; nepokusí se porovnat řetězec na základě dílčího výrazu a všech dílčích výrazů, které následují.)  
  
 Tato možnost se doporučuje, pokud víte, že zpětné navrácení nebude úspěšné. Zabránění modulu regulárních výrazů v provádění zbytečných hledání zlepšuje výkon.  
  
 Následující příklad ukazuje, jak dílčí výraz bez mechanismu navracení mění výsledky porovnávání vzorů. Regulární výraz zpětného navracení úspěšně vyhledá řadu opakovaných znaků následovaných jedním dalším výskytem stejného znaku na hranici slova, ale regulární výraz bez mechanismu navrácení.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 `(?>(\w)\1+).\b` regulární výraz nemechanismu navracení je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w)`|Porovnává s jedním slovním znakem a přiřadí ho k první zachytávající skupině.|  
|`\1+`|Porovnává hodnotu prvního zaznamenaného podřetězce jednou nebo vícekrát.|  
|`.`|Odpovídá jakémukoli znaku.|  
|`\b`|Ukončí porovnávání na hranici slova.|  
|`(?>(\w)\1+)`|Porovnává jeden nebo více výskytů duplicitního znaku slova, ale nepoužívejte k tomu, aby se shodovala s posledním znakem na hranici slova.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Seskupovací konstrukce a objekty regulárních výrazů  
 Podřetězce, které jsou porovnány zachycující skupinou regulárního výrazu, jsou reprezentovány <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> objekty, které lze načíst z objektu <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType>, který je vrácen vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. Objekt <xref:System.Text.RegularExpressions.GroupCollection> se vyplní následujícím způsobem:  
  
- První objekt <xref:System.Text.RegularExpressions.Group> v kolekci (objekt na indexu nula) představuje celou shodu.  
  
- Další sada objektů <xref:System.Text.RegularExpressions.Group> představuje nepojmenované (očíslované) zachytávající skupiny. Zobrazují se v pořadí, ve kterém jsou definované v regulárním výrazu zleva doprava. Hodnoty indexu těchto skupin jsou v rozsahu od 1 do počtu nepojmenovaných zachytávajících skupin v kolekci. (Index konkrétní skupiny odpovídá jeho číslovanému zpětnému odkazu. Další informace o zpětných odkazech naleznete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- Koncová sada objektů <xref:System.Text.RegularExpressions.Group> představuje pojmenované zachytávající skupiny. Zobrazují se v pořadí, ve kterém jsou definované v regulárním výrazu zleva doprava. Hodnota indexu první pojmenované zachytávající skupiny je jedna větší než index poslední nepojmenované zachytávající skupiny. Pokud v regulárním výrazu nejsou žádné nepojmenované zachytávající skupiny, hodnota indexu první pojmenované zachytávající skupiny je jedna.  
  
 Použijete-li kvantifikátor pro zachytávající skupinu, odpovídající <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType><xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> a vlastnosti <xref:System.Text.RegularExpressions.Group> objektu odrážejí poslední podřetězec, který je zachycen zachytávající skupinou. Můžete načíst úplnou sadu podřetězců, které jsou zachyceny skupinami, které mají kvantifikátory z objektu <xref:System.Text.RegularExpressions.CaptureCollection>, který je vrácen vlastností <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.  
  
 Následující příklad vysvětluje vztah mezi objekty <xref:System.Text.RegularExpressions.Group> a <xref:System.Text.RegularExpressions.Capture>.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Vzor regulárního výrazu `(\b(\w+)\W+)+` extrahuje jednotlivá slova z řetězce. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Tyto znaky společně tvoří slovo. Toto je druhá zachytávající skupina.|  
|`\W+`|Porovnává jeden nebo více znaků, které nejsou v textu.|  
|`(\b(\w+)\W+)`|Porovnává vzor jednoho nebo více znaků slova následovaných jedním nebo více znaky, které jsou jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
 Druhá zachytávající skupina odpovídá každému slovu věty. První zachytávající skupina odpovídá jednotlivým slovům společně s interpunkčním znaménkem a prázdným znakem, který následuje za slovem. Objekt <xref:System.Text.RegularExpressions.Group>, jehož index je 2, poskytuje informace o textu, který odpovídá druhá zachytávající skupina. Kompletní sada slov zachycených zachycující skupinou je k dispozici z objektu <xref:System.Text.RegularExpressions.CaptureCollection> vráceného vlastností <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
