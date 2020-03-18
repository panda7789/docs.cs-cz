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
ms.openlocfilehash: 5b2ea110837d9d5b905f97ab706af52a594f1c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159218"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Seskupovací konstrukce v regulárních výrazech
Seskupení konstrukce vymezit podvýrazy regulárního výrazu a zachytit podřetězce vstupního řetězce. Pomocí seskupovacích konstrukcí můžete provést následující akce:  
  
- Porovná dílčí výraz, který se opakuje ve vstupním řetězci.  
  
- Použijte kvantifikátor pro podvýraz, který má více prvků jazyka regulárních výrazů. Další informace o kvantifikátorech naleznete [v tématu Kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Zahrnout podvýraz do řetězce, který <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> je <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> vrácen a metody.  
  
- Načíst jednotlivé dílčí <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> výrazy z vlastnosti a zpracovat je odděleně od odpovídající ho textu jako celku.  
  
 V následující tabulce jsou uvedeny konstrukce seskupení podporované modulem regulárních výrazů .NET a označuje, zda zachycují nebo nezachycují.  
  
|Seskupovací konstrukce|Zachycení nebo nezachycení|  
|------------------------|-------------------------------|  
|[Odpovídající podvýrazy](#matched_subexpression)|Zachycení|  
|[Pojmenované odpovídající podvýrazy](#named_matched_subexpression)|Zachycení|  
|[Definice vyvažování skupin](#balancing_group_definition)|Zachycení|  
|[Skupiny bez zachycení](#noncapturing_group)|Nezachytávání|  
|[Možnosti skupiny](#group_options)|Nezachytávání|  
|[Kontrolní výrazy pozitivního dopředného vyhledávání s nulovou šířkou](#zerowidth_positive_lookahead_assertion)|Nezachytávání|  
|[Kontrolní výrazy negativního dopředného vyhledávání s nulovou šířkou](#zerowidth_negative_lookahead_assertion)|Nezachytávání|  
|[Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou](#zerowidth_positive_lookbehind_assertion)|Nezachytávání|  
|[Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou](#zerowidth_negative_lookbehind_assertion)|Nezachytávání|  
|[Atomové skupiny](#atomic_groups)|Nezachytávání|  
  
 Informace o skupinách a objektovém modelu regulárních výrazů naleznete v [tématu Seskupování konstrukcí a objektů regulárních výrazů](#Objects).  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Odpovídající podvýrazy  
 Následující seskupovací konstrukce zachycuje odpovídající dílčí výraz:  
  
 `(`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný platný vzor regulárního výrazu. Zachycení, která používají závorky, jsou číslována automaticky zleva doprava na základě pořadí počátečních závorek v regulárním výrazu, počínaje jedním. Zachycení, které je číslono nula je text, který odpovídá celému vzoru regulárního výrazu.  
  
> [!NOTE]
> Ve výchozím `(`nastavení prvek jazyka *podvýrazu* `)` zachycuje odpovídající podvýraz. Ale pokud <xref:System.Text.RegularExpressions.RegexOptions> parametr metody porovnávání vzorů <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> regulárních `n` výrazů obsahuje příznak nebo pokud je pro tento podvýraz použita možnost (viz [Možnosti skupiny](#group_options) dále v tomto tématu), odpovídající podvýraz není zachycen.  
  
 K zachycené skupinám můžete přistupovat čtyřmi způsoby:  
  
- Pomocí konstrukce zpětného odkazu v rámci regulárního výrazu. Odpovídající podvýraz je odkazován ve stejném regulárním výrazu pomocí `\` *čísla*syntaxe , kde *číslo* je číslo číslo zachyceného dílčího výrazu.  
  
- Pomocí pojmenované backreference konstrukce v rámci regulárního výrazu. Odpovídající podvýraz je odkazován ve stejném `\k<`regulárním výrazu pomocí *názvu*`>`syntaxe , `\k<`kde je *název* název zachytávající skupiny nebo *číslo*`>`, kde *číslo* je číslo číslo zachytávající skupiny. Zachytávající skupina má výchozí název, který je shodný s jejím řadovéčíslo. Další informace naleznete [v tématu Pojmenované odpovídající podvýrazy](#named_matched_subexpression) dále v tomto tématu.  
  
- `$`Pomocí pořadí nahrazení *čísla* <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> v <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody nebo, kde *číslo* je pořadové číslo zachyceného dílčího výrazu.  
  
- Programově pomocí objektu <xref:System.Text.RegularExpressions.GroupCollection> vrácené <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností. Člen na pozici nula v kolekci představuje celou shodu regulárního výrazu. Každý následující člen představuje odpovídající podvýraz. Další informace naleznete v části [Seskupování konstrukcí a objektů regulárních výrazů.](#Objects)  
  
 Následující příklad ilustruje regulární výraz, který identifikuje duplicitní slova v textu. Dvě zachytávající skupiny regulárního výrazu představují dvě instance duplikovaného slova. Druhá instance je zachycena, aby hlásila svou počáteční pozici ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Vzor regulárního výrazu je následující:  
  
`(\w+)\s(\1)\W`  
  
 Následující tabulka ukazuje, jak je interpretován vzor regulárního výrazu.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\1)`|Porovná řetězec v první zachycené skupině. Toto je druhá zachytávající skupina. Příklad jej přiřadí zachycené skupině, aby bylo možné z vlastnosti `Match.Index` načíst počáteční pozici duplicitního slova.|  
|`\W`|Porovná neslovaný znak, včetně prázdného místa a interpunkce. Tím zabráníte vzoru regulárního výrazu v porovnání slova, které začíná slovem z první zachycené skupiny.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>Pojmenované odpovídající podvýrazy  
 Následující konstrukce seskupení zachycuje odpovídající podvýraz a umožňuje přístup k němu podle názvu nebo čísla:  
  
`(?<name>subexpression)`  
  
 nebo:  
  
`(?'name'subexpression)`  
  
 kde *název* je platný název skupiny a *podvýraz* je libovolný platný vzor regulárního výrazu. *název* nesmí obsahovat žádné interpunkční znaky a nesmí začínat číslem.  
  
> [!NOTE]
> Pokud <xref:System.Text.RegularExpressions.RegexOptions> parametr metody porovnávání vzorů regulárních výrazů obsahuje <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> příznak nebo pokud je `n` pro tento podvýraz použita možnost (viz [Možnosti skupiny](#group_options) dále v tomto tématu), je jediným způsobem, jak zachytit podvýraz, explicitně pojmenovat zachytávající skupiny.  
  
 K pojmenovaným zachycených skupinám můžete přistupovat následujícími způsoby:  
  
- Pomocí pojmenované backreference konstrukce v rámci regulárního výrazu. Odpovídající podvýraz je odkazován ve stejném regulárním výrazu pomocí `\k<` *názvu*`>`syntaxe , kde *název* je název zachyceného dílčího výrazu.  
  
- Pomocí konstrukce zpětného odkazu v rámci regulárního výrazu. Odpovídající podvýraz je odkazován ve stejném regulárním výrazu pomocí `\` *čísla*syntaxe , kde *číslo* je číslo číslo zachyceného dílčího výrazu. Pojmenované odpovídající podvýrazy jsou číslovány postupně zleva doprava po odpovídajících podvýrazech.  
  
- `${`Pomocí pořadí nahrazení *názvu* `}` <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> v <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody nebo, kde *název* je název zachyceného dílčího výrazu.  
  
- `$`Pomocí pořadí nahrazení *čísla* <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> v <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody nebo, kde *číslo* je pořadové číslo zachyceného dílčího výrazu.  
  
- Programově pomocí objektu <xref:System.Text.RegularExpressions.GroupCollection> vrácené <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností. Člen na pozici nula v kolekci představuje celou shodu regulárního výrazu. Každý následující člen představuje odpovídající podvýraz. Pojmenované zachycené skupiny jsou uloženy v kolekci po číslované zachycené skupiny.  
  
- Programově tím, že podvýraz název <xref:System.Text.RegularExpressions.GroupCollection> indexeru objektu (v jazyce <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> C#) nebo jeho vlastnost (v jazyce Visual Basic).  
  
 Jednoduchý vzor regulárního výrazu ilustruje, jak lze číslované (nepojmenované) a pojmenované skupiny odkazovat programově nebo pomocí syntaxe jazyka regulárních výrazů. Regulární `((?<One>abc)\d+)?(?<Two>xyz)(.*)` výraz vytváří následující zachytávající skupiny podle čísla a názvu. První zachytávající skupina (číslo 0) vždy odkazuje na celý vzor.  
  
|Číslo|Name (Název)|Vzor|  
|------------|----------|-------------|  
|0|0 (výchozí název)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (výchozí název)|`((?<One>abc)\d+)`|  
|2|2 (výchozí název)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Dva|`(?<Two>xyz)`|  
  
 Následující příklad ilustruje regulární výraz, který identifikuje duplicitní slova a slovo, které bezprostředně následuje za každým duplicitním slovem. Vzor regulárního výrazu definuje `duplicateWord`dva pojmenované podvýrazy: , který představuje duplicitní slovo; a `nextWord`, který představuje slovo, které následuje za duplicitní slovo.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Vzor regulárního výrazu je následující:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Následující tabulka ukazuje, jak je regulární výraz interpretován.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto `duplicateWord`zachytávající skupinu .|  
|`\s`|Porovná prázdný znak.|  
|`\k<duplicateWord>`|Porovná řetězec ze zachycené skupiny `duplicateWord`s názvem .|  
|`\W`|Porovná neslovaný znak, včetně prázdného místa a interpunkce. Tím zabráníte vzoru regulárního výrazu v porovnání slova, které začíná slovem z první zachycené skupiny.|  
|`(?<nextWord>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto `nextWord`zachytávající skupinu .|  
  
 Všimněte si, že název skupiny lze opakovat v regulárním výrazu. Například je možné pro více než jednu skupinu, která má být pojmenována `digit`, jak ukazuje následující příklad. V případě duplicitních názvů je <xref:System.Text.RegularExpressions.Group> hodnota objektu určena posledním úspěšným zachycením ve vstupním řetězci. Kromě toho <xref:System.Text.RegularExpressions.CaptureCollection> je naplněn informace mi informace o každém zachycení stejně jako by to bylo, pokud název skupiny nebyl duplikován.  
  
 V následujícím příkladu regulární výraz `\D+(?<digit>\d+)\D+(?<digit>\d+)?` obsahuje dva `digit`výskyty skupiny s názvem . První `digit` pojmenovaná skupina zachytí jeden nebo více znaků číslic. Druhá `digit` pojmenovaná skupina zachytí nulu nebo jeden výskyt jednoho nebo více číslicových znaků. Jak ukazuje výstup z příkladu, pokud druhá zachytávající skupina úspěšně odpovídá textu, <xref:System.Text.RegularExpressions.Group> hodnota tohoto textu definuje hodnotu objektu. Pokud druhá zachytávající skupina nemůže odpovídat vstupnímu řetězci, hodnota poslední <xref:System.Text.RegularExpressions.Group> úspěšné shody definuje hodnotu objektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Následující tabulka ukazuje, jak je regulární výraz interpretován.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\D+`|Porovná jeden nebo více nedesetinných desetinných znaků.|  
|`(?<digit>\d+)`|Porovná jeden nebo více desetinných míst. Přiřaďte `digit` shodu pojmenované skupině.|  
|`\D+`|Porovná jeden nebo více nedesetinných desetinných znaků.|  
|`(?<digit>\d+)?`|Porovná nulový nebo jeden výskyt jednoho nebo více desetinných míst. Přiřaďte `digit` shodu pojmenované skupině.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Definice vyvažování skupin  
 Definice vyrovnávací skupiny odstraní definici dříve definované skupiny a uloží v aktuální skupině interval mezi dříve definovanou skupinou a aktuální skupinou. Tato seskatovská konstrukce má následující formát:  
  
`(?<name1-name2>subexpression)`  
  
 nebo:  
  
`(?'name1-name2' subexpression)`
  
 kde *name1* je aktuální skupina (nepovinné), *name2* je dříve definovaná skupina a *podvýraz* je libovolný platný vzor regulárního výrazu. Definice vyrovnávací skupiny odstraní definici *name2* a uloží interval mezi *name2* a *name1* v *name1*. Pokud není definována žádná skupina *name2,* shoda se vrátí zpět. Vzhledem k tomu, že odstranění poslední definice *name2* odhaluje předchozí definici *name2*, tato konstrukce umožňuje použít zásobník zachycení pro název skupiny2 jako čítač pro sledování vnořené konstrukce, jako jsou závorky nebo otevírací a uzavírací závorky. *name2*  
  
 Definice vyvažovací skupiny používá *name2* jako zásobník. Počáteční znak každé vnořené konstrukce je umístěn <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> ve skupině a v její kolekci. Při spárovat uzávěrkový znak, jeho odpovídající počáteční znak <xref:System.Text.RegularExpressions.Group.Captures%2A> je odebrán ze skupiny a kolekce je snížena o jeden. Po otevření a zavření znaky všech vnořených konstrukcí byly spárovány, *name2* je prázdný.  
  
> [!NOTE]
> Po úpravě regulárního výrazu v následujícím příkladu tak, aby používal příslušný otevírací a uzavírací znak vnořené konstrukce, jej můžete použít ke zpracování většiny vnořených konstrukcí, jako jsou matematické výrazy nebo řádky kódu programu, které obsahují více vnořených volání metod.  
  
 Následující příklad používá definici vyvažovací skupiny tak, aby odpovídala levému a pravému úhlu (<>) ve vstupním řetězci. Příklad definuje dvě pojmenované `Open` skupiny a `Close`, které se používají jako zásobník ke sledování odpovídajících párů úhlových závorek. Každá zachycená levá úhlová závorka je zasunuta do kolekce zachycení `Open` skupiny `Close` a každá zachycená pravá úhlová závorka je zasunuta do kolekce zachycení skupiny. Definice vyvažovací skupiny zajišťuje, že pro každou levou úhlovou závorku je odpovídající pravá úhlová závorka. Pokud není, konečné dílčí vzor `(?(Open)(?!))`, je vyhodnocena pouze v případě, že `Open` skupina není prázdná (a proto, pokud všechny vnořené konstrukce nebyly uzavřeny). Pokud je vyhodnocen konečný dílčí vzor, `(?!)` shoda se nezdaří, protože dílčí vzor je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který se vždy nezdaří.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Vzor regulárního výrazu je:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Regulární výraz je interpretován takto:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začněte na začátku řetězce.|  
|`[^<>]*`|Porovná nulové nebo více znaků, které nejsou levé nebo pravé úhlové závorky.|  
|`(?'Open'<)`|Porovná levou úhlovou závorku `Open`a přiřadí ji skupině s názvem .|  
|`[^<>]*`|Porovná nulové nebo více znaků, které nejsou levé nebo pravé úhlové závorky.|  
|`((?'Open'<)[^<>]*)+`|Porovná jeden nebo více výskytů levé houštiny následované nulovými nebo více znaky, které nejsou levými nebo pravými úhlovými závorkami. Toto je druhá zachytávající skupina.|  
|`(?'Close-Open'>)`|Porovná pravou úhlovou závorku, `Open` přiřadí skupině podřetězec mezi skupinou a aktuální skupinou `Close` a odstraní definici `Open` skupiny.|  
|`[^<>]*`|Porovná nula nebo více výskytů libovolného znaku, který není levým ani pravým úhlovým závorkou.|  
|`((?'Close-Open'>)[^<>]*)+`|Porovná jeden nebo více výskytů pravého úhlového závorky následovaného nulou nebo více výskyty libovolného znaku, který není ani levým, ani pravým úhlovým závorkou. Při porovnávání pravé houštiny `Open` přiřaďte skupině `Close` podřetězec mezi skupinou `Open` a aktuální skupinou a odstraňte definici skupiny. Toto je třetí zachytávající skupina.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Porovná nula nebo více výskytů následujícího vzoru: jeden nebo více výskytů levé úhlové závorky následované nulovými nebo více neúhlovými znaky závorky následované jedním nebo více výskyty pravé úhlové závorky následované nulovými nebo více výskyty neúhlové držáky. Při porovnávání pravé houštinové závorky odstraňte definici `Open` skupiny a přiřaďte skupině podřetězec mezi skupinou `Open` a aktuální skupinou. `Close` Toto je první zachytávající skupina.|  
|`(?(Open)(?!))`|Pokud `Open` skupina existuje, opusťte shodu, pokud lze spárovat prázdný řetězec, ale neposuňte pozici modulu regulárních výrazů v řetězci. Toto je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou. Vzhledem k tomu, že prázdný řetězec je vždy implicitně přítomen ve vstupním řetězci, tato shoda se vždy nezdaří. Selhání této shody znamená, že úhlové závorky nejsou vyvážené.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Konečný dílčí výraz `(?(Open)(?!))`, označuje, zda jsou vnořené konstrukce ve vstupním řetězci správně vyváženy (například zda je každá levá úhlová závorka spárována s pravou úhlovou závorkou). Používá podmíněné porovnávání na základě platné zachycené skupiny; Další informace naleznete v tématu [Alternation Constructs](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Pokud `Open` je skupina definována, modul regulárních `(?!)` výrazů se pokusí porovnat dílčí výraz ve vstupním řetězci. Skupina `Open` by měla být definována pouze v případě, že vnoření konstrukce jsou nevyvážené. Proto vzor, který má být spárován ve vstupním řetězci by měl být ten, který vždy způsobí selhání shody. V tomto `(?!)` případě je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který vždy selže, protože prázdný řetězec je vždy implicitně přítomen na další pozici ve vstupním řetězci.  
  
 V příkladu modul regulárních výrazů\<vyhodnotí\<vstupní řetězec abc><mno xyz>>", jak je znázorněno v následující tabulce.  
  
|Krok|Vzor|Výsledek|  
|----------|-------------|------------|  
|1|`^`|Spustí shodu na začátku vstupního řetězce.|  
|2|`[^<>]*`|Vyhledá znaky neúhelníku před levou úhlovou závorkou;|  
|3|`(((?'Open'<)`|Porovná levou úhlovou\<závorku v "abc `Open`>" a přiřadí ji skupině.|  
|4|`[^<>]*`|Odpovídá "abc".|  
|5|`)+`|"<abc" je hodnota druhé zachycené skupiny.<br /><br /> Další znak ve vstupním řetězci není levý mýše, takže modul `(?'Open'<)[^<>]*)` regulárních výrazů se nevrátí zpět do dílčího vzoru.|  
|6|`((?'Close-Open'>)`|Odpovídá pravé úhlové\<závorce v "abc>", přiřadí `Open` "abc", což je `Close` podřetězec mezi skupinou a pravou úhlovou `Open` závorkou, skupině a odstraní aktuální hodnotu ("<") skupiny a ponechá ji prázdnou.|  
|7|`[^<>]*`|Hledá znaky neúhlové závorky za pravou úhlovou závorkou; nenajde žádné shody.|  
|8|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravý úhel držáku, takže modul `((?'Close-Open'>)[^<>]*)` regulárních výrazů není smyčka zpět do dílčího vzoru.|  
|9|`)*`|Hodnota první zachycené skupiny\<je "abc>".<br /><br /> Dalším znakem ve vstupním řetězci je levý úhel, takže modul `(((?'Open'<)` regulárních výrazů se vrátí zpět do dílčího vzoru.|  
|10|`(((?'Open'<)`|Porovná levou úhlovou\<závorku v "mno" a přiřadí ji skupině. `Open` Jeho <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce má nyní jedinou hodnotu, "<".|  
|11|`[^<>]*`|Odpovídá "mno".|  
|12|`)+`|"<mno" je hodnota druhé zachycené skupiny.<br /><br /> Dalším znakem ve vstupním řetězci je levý úhel, takže modul `(?'Open'<)[^<>]*)` regulárních výrazů se vrátí zpět do dílčího vzoru.|  
|13|`(((?'Open'<)`|Porovná levou úhlovou\<závorku v "xyz `Open`>" a přiřadí ji skupině. Kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> `Open` skupiny nyní obsahuje dvě zachycení: levý úhel\<držáku z " mno\<" a levý úhel držák u " xyz> ".|  
|14|`[^<>]*`|Odpovídá "xyz".|  
|15|`)+`|"<xyz" je hodnota druhé zachycené skupiny.<br /><br /> Další znak ve vstupním řetězci není levý mýše, takže modul `(?'Open'<)[^<>]*)` regulárních výrazů se nevrátí zpět do dílčího vzoru.|  
|16|`((?'Close-Open'>)`|Odpovídá pravému úhlu\<v "xyz>". "xyz", přiřadí skupině podřetězec mezi skupinou `Open` a `Close` pravou úhlovou závorkou `Open` a odstraní aktuální hodnotu skupiny. Hodnota předchozího zachycení (levý úhel držáku v "\<mno") `Open` se stane aktuální hodnotou skupiny. Kolekce <xref:System.Text.RegularExpressions.Group.Captures%2A> skupiny `Open` nyní obsahuje jeden zachycení, levý úhel\<držák u " xyz> ".|  
|17|`[^<>]*`|Vyhledá znaky neúhlové závorky; nenajde žádné shody.|  
|18|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Další znak ve vstupním řetězci je pravý úhel držáku, takže `((?'Close-Open'>)[^<>]*)` modul regulárních výrazů smyčky zpět do dílčího vzoru.|  
|19|`((?'Close-Open'>)`|Odpovídá poslední pravé úhlové závorce v "xyz>>",\<přiřadí `Open` `Close` skupině "mno xyz>" (podřetězec mezi skupinou `Open` a pravou úhlovou závorkou) a odstraní aktuální hodnotu skupiny. Skupina `Open` je nyní prázdná.|  
|20|`[^<>]*`|Vyhledá znaky neúhlové závorky; nenajde žádné shody.|  
|21|`)+`|Hodnota třetí zachycené skupiny je ">".<br /><br /> Další znak ve vstupním řetězci není pravý úhel držáku, takže modul `((?'Close-Open'>)[^<>]*)` regulárních výrazů není smyčka zpět do dílčího vzoru.|  
|22|`)*`|Hodnota první zachycené skupiny je "<mno\<xyz>>".<br /><br /> Další znak ve vstupním řetězci není levý mýše, takže modul `(((?'Open'<)` regulárních výrazů se nevrátí zpět do dílčího vzoru.|  
|23|`(?(Open)(?!))`|Skupina `Open` není definována, takže se nepokouší žádná shoda.|  
|24|`$`|Odpovídá konci vstupního řetězce.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Skupiny bez zachycení  
 Následující konstrukce seskupení nezachycuje podřetězec, který je spárován podvýrazem:  
  
`(?:subexpression)`
  
 kde *podvýraz* je libovolný platný vzor regulárního výrazu. Konstrukce skupiny bez zachycení se obvykle používá, když je na skupinu aplikován kvantifikátor, ale podřetězce zachycené skupinou nejsou zajímavé.  
  
> [!NOTE]
> Pokud regulární výraz obsahuje vnořené konstrukce seskupení, vnější konstrukce skupiny bez zachycení se nevztahuje na vnitřní vnořené skupiny konstrukce.  
  
 Následující příklad ilustruje regulární výraz, který zahrnuje skupiny bez zachycení. Všimněte si, že výstup neobsahuje žádné zachycené skupiny.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Regulární `(?:\b(?:\w+)\W*)+\.` výraz odpovídá větě, která je ukončena tečkou. Vzhledem k tomu, že regulární výraz se zaměřuje na věty a nikoli na jednotlivá slova, seskupování konstrukce se používají výhradně jako kvantifikátory. Vzor regulárního výrazu je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?:\w+)`|Porovná jeden nebo více znaků slova. Nepřiřazujte odpovídající text zachycené skupině.|  
|`\W*`|Porovná nulové nebo více neslovních znaků.|  
|`(?:\b(?:\w+)\W*)+`|Porovná vzorek jednoho nebo více znaků slova začínajících na hranici slova, následovanýnulým nebo více neslovními znaky, jednou nebo vícekrát. Nepřiřazujte odpovídající text zachycené skupině.|  
|`\.`|Porovná tečku.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Možnosti skupiny  
 Následující konstrukce seskupení použije nebo zakáže zadané možnosti v rámci dílčího výrazu:  
  
 `(?imnsx-imnsx:`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný platný vzor regulárního výrazu. Například `(?i-s:)` zapne nerozlišování malých a velkých písmen a zakáže režim jednoho řádku. Další informace o možnostech vsazení, které můžete zadat, naleznete v [tématu Možnosti regulárního výrazu](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Pomocí konstruktoru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy nebo statické metody můžete určit možnosti, které platí pro celý regulární výraz, nikoli pro dílčí výraz. Můžete také určit vložkové možnosti, které platí za `(?imnsx-imnsx)` určitým bodem v regulárním výrazu pomocí konstrukce jazyka.  
  
 Konstrukce možností skupiny není zachytávající skupinou. To znamená, že i když jakákoli část řetězce, který je zachycen *podvýraz* je součástí shody, není <xref:System.Text.RegularExpressions.GroupCollection> zahrnuta do zachycené skupiny ani slouží k naplnění objektu.  
  
 Například regulární `\b(?ix: d \w+)\s` výraz v následujícím příkladu používá včleněné možnosti v konstrukci seskupení k povolení porovnávání bez rozlišování velkých a malých písmen a ignorování prázdného místa ve vzorku při identifikaci všech slov začínajících písmenem "d". Regulární výraz je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?ix: d \w+)`|Pomocí porovnávání bez rozlišování velkých a malých písmen v tomto vzoru odpovídá písmenu "d" následovanému jedním nebo více znaky slova.|  
|`\s`|Porovná prázdný znak.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Kontrolní výrazy pozitivního dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou:  
  
 `(?=`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný vzor regulárního výrazu. Aby byla shoda úspěšná, musí vstupní řetězec odpovídat vzoru regulárního výrazu v *dílčím výrazu*, i když odpovídající podřetězec není zahrnut ve výsledku shody. Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou se nevrací zpět.  
  
 Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou se obvykle nachází na konci vzoru regulárního výrazu. Definuje podřetězec, který musí být nalezen na konci řetězce pro shodu dojít, ale které by neměly být zahrnuty do shody. Je také užitečné pro prevenci nadměrné hodování. Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou můžete použít k zajištění, že konkrétní zachycená skupina začíná textem, který odpovídá podmnožině vzoru definovaného pro tuto zachycenou skupinu. Pokud například zachytávající skupina odpovídá po sobě jdoucím znakům slova, můžete použít kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou, který vyžaduje, aby první znak byl abecední znak s velkými písmeny.  
  
 Následující příklad používá kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou, který odpovídá slovu, které předchází slovesu "is" ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Regulární `\b\w+(?=\sis\b)` výraz je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(?=\sis\b)`|Určete, zda jsou znaky slova následovány znakem prázdného místa a řetězcem "is", který končí na hranici slova. Pokud ano, shoda je úspěšná.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Kontrolní výrazy negativního dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou:  
  
 `(?!`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný vzor regulárního výrazu. Aby byla shoda úspěšná, nesmí vstupní řetězec odpovídat vzoru regulárního výrazu v *dílčím výrazu*, i když odpovídající řetězec není zahrnut ve výsledku shody.  
  
 Kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou se obvykle používá na začátku nebo na konci regulárního výrazu. Na začátku regulárního výrazu může definovat konkrétní vzor, který by neměl odpovídat, když začátek regulárního výrazu definuje podobný, ale obecnější vzor, který má být spárován. V tomto případě se často používá k omezení navracení. Na konci regulárního výrazu může definovat podvýraz, který nemůže nastat na konci shody.  
  
 Následující příklad definuje regulární výraz, který používá výraz dopředného vyhledávání s nulovou šířkou na začátku regulárního výrazu tak, aby odpovídal slovům, která nezačínají na "un".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Regulární `\b(?!un)\w+\b` výraz je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?!un)`|Určete, zda jsou další dva znaky "un". Pokud tomu tak není, shoda je možná.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Následující příklad definuje regulární výraz, který používá kontrolní výraz dopředného vyhledávání s nulovou šířkou na konci regulárního výrazu tak, aby odpovídal slovům, která nekončí interpunkčním znakem.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Regulární `\b\w+\b(?!\p{P})` výraz je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`\p{P})`|Pokud následující znak není interpunkční symbol (například tečka nebo čárka), shoda je úspěšná.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<=`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný vzor regulárního výrazu. Aby byla shoda úspěšná, musí dojít *ke vstupnímu řetězci* nalevo od aktuální pozice, i když `subexpression` není zahrnut o výsledek shody. Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou neustoupí.  
  
 Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou se obvykle používají na začátku regulárních výrazů. Vzor, který definují, je předpokladem pro shodu, i když není součástí výsledku shody.  
  
 Například následující příklad odpovídá poslední dvě číslice roku pro dvacáté první století (to znamená, že vyžaduje, aby číslice "20" předcházet odpovídající řetězec).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Vzor regulárního výrazu `(?<=\b20)\d{2}\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\d{2}`|Porovná dvě desetinná místa.|  
|`(?<=\b20)`|Pokračujte v shodě, pokud dvě desetinné číslice předchází desetinné číslice "20" na hranici slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou se také používají k omezení zpětného navracení, když poslední znak nebo znaky v zachycené skupině musí být podmnožinou znaků, které odpovídají vzoru regulárního výrazu této skupiny. Pokud například skupina zachytí všechny po sobě jdoucí znaky slova, můžete použít kontrolní výraz s nulovou šířkou pozitivního zpětného vyhledávání, který vyžaduje, aby poslední znak byl abecední.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<!`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný vzor regulárního výrazu. Aby byla shoda úspěšná, nesmí se *dílčí výraz* vyskytovat ve vstupním řetězci nalevo od aktuální pozice. Však žádné podřetězec, `subexpression` který se neshoduje není zahrnuta ve výsledku shody.  
  
 Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou se obvykle používají na začátku regulárních výrazů. Vzor, který definují vylučuje shodu v řetězci, který následuje. Používají se také k omezení zpětného navracení, když poslední znak nebo znaky v zachycené skupině nesmí být jedním nebo více znaky, které odpovídají vzoru regulárního výrazu této skupiny. Pokud například skupina zachytí všechny po sobě jdoucí znaky slova, můžete použít kontrolní výraz s nulovou\_šířkou pro pozitivní zpětné vyhledávání, který vyžaduje, aby poslední znak nebyl podtržítkem ( ).  
  
 Následující příklad odpovídá datu pro libovolný den v týdnu, který není víkend (to znamená, že není ani sobota ani neděle).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Vzor regulárního výrazu `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova následovaných nebílým znakem.|  
|`\d{1,2},`|Porovná jednu nebo dvě desetinná číslice následovaná znakem prázdného místa a čárkou.|  
|`\d{4}\b`|Porovná čtyři desetinné číslice a ukončí shodu na hranici slova.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Pokud shodě předchází něco jiného než řetězce "Sobota" nebo "Neděle" následovaný mezerou, shoda je úspěšná.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Atomové skupiny  
 Následující konstrukce seskupení představuje atomickou skupinu (známou v některých jiných modulech regulárních výrazů jako podvýraz bez zpětného navracení, atomický dílčí výraz nebo podvýraz pouze jednou):
  
 `(?>`*dílčí výraz*`)`  
  
 kde *podvýraz* je libovolný vzor regulárního výrazu.  
  
 Obvykle pokud regulární výraz obsahuje volitelný nebo alternativní odpovídající vzorek a shoda neproběhne úspěšně, modul regulárních výrazů může větvit ve více směrech tak, aby odpovídalvstupnímu řetězci se vzorkem. Pokud shoda není nalezena, když trvá první větev, modul regulárních výrazů může zálohovat nebo zpětně do bodu, kde vzal první shodu a pokusit se o shodu pomocí druhé větve. Tento proces může pokračovat, dokud nebyly vyzkoušeny všechny větve.  
  
 Konstrukce `(?>`jazyka *podvýrazu* `)` zakáže backtracking. Modul regulárních výrazů bude odpovídat co nejvíce znaků ve vstupním řetězci, jak je to možné. Pokud není možné žádné další shody, nebude ustoupit k pokusu o alternativní vzor shody. (To znamená, že podvýraz odpovídá pouze řetězcům, které by odpovídaly pouze dílčímu výrazu; nepokouší se odpovídat řetězci založenému na dílčím výrazu a všech podvýrazech, které za ním následují.)  
  
 Tato možnost je doporučena, pokud víte, že navracení nebude úspěšné. Zabránění modulu regulárních výrazů v provádění zbytečného vyhledávání zlepšuje výkon.  
  
 Následující příklad ukazuje, jak atomická skupina upravuje výsledky shody vzoru. Regulární výraz backtracking úspěšně odpovídá řadě opakovaných znaků následovaných dalším výskytem stejného znaku na hranici slova, ale regulární výraz bez zpětného sledování nikoli.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Regulární výraz `(?>(\w)\1+).\b` bez zpětného navracení je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w)`|Porovnejte jeden znak slova a přiřaďte jej první zachytávající skupině.|  
|`\1+`|Porovná hodnotu prvního zachyceného podřetězce jednou nebo vícekrát.|  
|`.`|Porovná libovolný znak.|  
|`\b`|Ukončite shodu na hranici slova.|  
|`(?>(\w)\1+)`|Porovná jeden nebo více výskytů duplicitního znaku slova, ale neustupujte tak, aby odpovídal poslednímu znaku na hranici slova.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Seskupování konstrukčních konstrukcí a objektů regulárních výrazů  
 Podřetězce, které jsou porovnány se skupinou zachytávání regulárních výrazů, jsou reprezentovány objekty, <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> které lze načíst z objektu, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> který je vrácen vlastností. Objekt <xref:System.Text.RegularExpressions.GroupCollection> je naplněn následujícím způsobem:  
  
- První <xref:System.Text.RegularExpressions.Group> objekt v kolekci (objekt na indexu nula) představuje celou shodu.  
  
- Další sada <xref:System.Text.RegularExpressions.Group> objektů představuje nepojmenované (číslované) zachytávající skupiny. Zobrazují se v pořadí, ve kterém jsou definovány v regulárním výrazu, zleva doprava. Indexové hodnoty těchto skupin jsou v rozsahu od 1 do počtu nepojmenovaných zachytávacích skupin v kolekci. (Index určité skupiny je ekvivalentní jeho číslované zpětné hodu. Další informace o zpětné odkazy naleznete v tématu [Backreference Constructs](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- Konečná sada <xref:System.Text.RegularExpressions.Group> objektů představuje pojmenované zachytávající skupiny. Zobrazují se v pořadí, ve kterém jsou definovány v regulárním výrazu, zleva doprava. Hodnota indexu první pojmenované zachytávající skupiny je o jednu větší než index poslední nepojmenované zachytávající skupiny. Pokud v regulárním výrazu nejsou žádné nepojmenované zachytávající skupiny, je hodnota indexu první pojmenované zachytávající skupiny jedna.  
  
 Pokud aplikujete kvantifikátor na <xref:System.Text.RegularExpressions.Group> zachytávající skupinu, odpovídající objekt <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>a <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> vlastnosti odrážejí poslední podřetězec, který je zachycen zachytávající skupinou. Můžete načíst úplnou sadu podřetězců, které jsou zachyceny skupinami, <xref:System.Text.RegularExpressions.CaptureCollection> které mají kvantifikátory z objektu, <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> který je vrácen vlastností.  
  
 Následující příklad objasňuje vztah <xref:System.Text.RegularExpressions.Group> <xref:System.Text.RegularExpressions.Capture> mezi a objekty.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Vzor `(\b(\w+)\W+)+` regulárního výrazu extrahuje jednotlivá slova z řetězce. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Společně tyto znaky tvoří slovo. Toto je druhá zachytávající skupina.|  
|`\W+`|Porovná jeden nebo více znaků, které nejsou slovem.|  
|`(\b(\w+)\W+)`|Porovná vzorek jednoho nebo více znaků slova následovaný jedním nebo více znaky, které nejsou slovem, jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
 Druhá zachytávající skupina odpovídá každému slovu věty. První zachytávající skupina odpovídá každému slovu spolu s interpunkcí a prázdné místo, které následují za slovem. Objekt, <xref:System.Text.RegularExpressions.Group> jehož index je 2 poskytuje informace o textu odpovídající druhé zachytávání skupiny. Kompletní sada slov zachycených zachytávající skupinou <xref:System.Text.RegularExpressions.CaptureCollection> je k <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> dispozici z objektu vráceného vlastností.  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
