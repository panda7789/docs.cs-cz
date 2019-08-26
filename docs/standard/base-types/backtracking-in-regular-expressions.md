---
title: Zpětné navrácení v regulárních výrazech .NET
description: Naučte se řídit zpětné navrácení v porovnávání vzorů regulárních výrazů.
ms.date: 11/12/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, backtracking
- alternative matching patterns
- optional matching patterns
- searching with regular expressions, backtracking
- pattern-matching with regular expressions, backtracking
- backtracking
- regular expressions [.NET Framework], backtracking
- strings [.NET Framework], regular expressions
- parsing text with regular expressions, backtracking
ms.assetid: 34df1152-0b22-4a1c-a76c-3c28c47b70d8
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 0831a22b0c1d3333cc37f86a764006c934597390
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968564"
---
# <a name="backtracking-in-regular-expressions"></a>Zpětné navracení v regulárních výrazech
<a name="top"></a>K zpětnému navrácení dojde, když vzor regulárního [](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) výrazu obsahuje volitelné kvantifikátory nebo [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)a modul regulárních výrazů se vrátí do předchozího uloženého stavu, aby bylo možné pokračovat ve vyhledávání shody. Navracení má klíčový význam pro výkon regulárních výrazů, což umožňuje, aby výrazy byly výkonné a pružné a aby vyhovovaly velmi složitým vzorům. Tento výkon však zároveň něco stojí. Navracení je často jediným nejdůležitějším faktorem, který ovlivňuje výkon modulu regulárních výrazů. Vývojář má naštěstí vliv na chování modulu regulárních výrazů a způsob používání mechanismu navracení. V tomto tématu je vysvětleno fungování a ovládání mechanismu navracení.  
  
> [!NOTE]
> Obecně platí, že nedeterministické Automation modul (NFA), jako je modul .NET regulárních výrazů, je zodpovědný za vytváření efektivních a rychlých regulárních výrazů pro vývojáře.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Lineární porovnání bez navrácení](#linear_comparison_without_backtracking)  
  
- [Navrácení se nepovinnými kvantifikátory nebo konstrukcemi alternace](#backtracking_with_optional_quantifiers_or_alternation_constructs)  
  
- [Navrácení pomocí vnořených volitelných kvantifikátorů](#backtracking_with_nested_optional_quantifiers)  
  
- [Řízení zpětného navrácení](#controlling_backtracking)  
  
<a name="linear_comparison_without_backtracking"></a>   
## <a name="linear-comparison-without-backtracking"></a>Lineární porovnání bez mechanismu navracení  
 Pokud vzor regulárního výrazu nemá žádné volitelné kvantifikátory nebo konstrukce alternace, bude modul regulárních výrazů spuštěn v lineárním čase. Což znamená, že jakmile se modul regulárních výrazů shoduje s prvním prvkem jazyka ve vzorci s textem ve vstupním řetězci, pokusí se vyhledat další prvek jazyka ve vzoru s dalším znakem nebo skupinou znaků ve vstupním řetězci. Tento postup se opakuje, dokud je shoda buď úspěšná, anebo neúspěšná. V obou případech se modul regulárních výrazů posune vždy o jeden znak ve vstupním řetězci.  
  
 V následujícím příkladu je uvedena ukázka. Regulární výraz `e{2}\w\b` hledá dva výskyty písmena "e" následovaný jakýmkoliv znakem slova následovaným hranicí slova.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 I když tento regulární výraz obsahuje kvantifikátor `{2}`, je vyhodnocen lineárním způsobem. Modul regulárních výrazů neprovádí navracení `{2}` , protože není volitelná kvantifikátor; určuje přesný počet a nikoli proměnný počet, kolikrát se musí předchozí dílčí výraz shodovat. V důsledku toho se modul regulárních výrazů pokusí shodovat se vzorem regulárního výrazu se vstupním řetězcem, jak je znázorněno v následující tabulce.  
  
|Operace|Pozice ve vzoru|Pozice v řetězci|Výsledek|  
|---------------|-------------------------|------------------------|------------|  
|1|e|"needing a reed" (index 0)|Žádná shoda.|  
|2|e|"eeding a reed" (index 1)|Možná shoda.|  
|3|e{2}|"eding a reed" (index 2)|Možná shoda.|  
|4|\w|"ding a reed" (index 3)|Možná shoda.|  
|5|\b|"ing a reed" (index 4)|Možná shoda se nezdaří.|  
|6|e|"eding a reed" (index 2)|Možná shoda.|  
|7|e{2}|"ding a reed" (index 3)|Možná shoda se nezdaří.|  
|8|e|"ding a reed" (index 3)|Shoda se nezdaří.|  
|9|e|"ing a reed" (index 4)|Žádná shoda.|  
|10|e|"ng a reed" (index 5)|Žádná shoda.|  
|11|e|"g a reed" (index 6)|Žádná shoda.|  
|12|e|"a Reed" (index 7)|Žádná shoda.|  
|13|e|"a Reed" (index 8)|Žádná shoda.|  
|14|e|"Reed" (index 9)|Žádná shoda.|  
|15|e|"Reed" (index 10)|Žádná shoda|  
|16|e|"eed" (index 11)|Možná shoda.|  
|17|e{2}|"ed" (index 12)|Možná shoda.|  
|18|\w|"d" (index 13)|Možná shoda.|  
|19|\b|"" (index 14)|Shoda.|  
  
 Pokud vzor regulárního výrazu neobsahuje žádné volitelné kvantifikátory nebo konstrukce alternace, musí maximální počet porovnání odpovídající vzoru regulárního výrazu se vstupním řetězcem být zhruba ekvivalentní počtu znaků ve vstupním řetězci. V tomto případě používá modul regulárních výrazů 19 porovnání k identifikaci možných shod v tomto řetězci o 13 znacích.  Jinými slovy to znamená, že modul regulárních výrazů je spuštěn v téměř lineárním čase, pokud neobsahuje žádné volitelné kvantifikátory nebo konstrukce alternace.  
  
 [Zpět na začátek](#top)  
  
<a name="backtracking_with_optional_quantifiers_or_alternation_constructs"></a>   
## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>Navracení pomocí volitelných kvantifikátorů nebo konstrukcí alternace  
 Pokud regulární výraz zahrnuje volitelné kvantifikátory nebo alternace konstrukce, hodnocení vstupního řetězce již není lineární. Porovnání vzorů s modulem NFA řídí prvky jazyka v regulárním výrazu, nikoli znaky, které se musí shodovat ve vstupním řetězci. Proto se modul regulárních výrazů pokouší o úplnou shodu volitelných nebo alternativních dílčích výrazů. Jakmile přejde na další prvek jazyka v dílčím výrazu a shoda není úspěšná, může modul regulárních výrazů opustit část úspěšné shody a vrátit se ke dříve uloženému stavu v zájmu shody celého regulárního výrazu ve vstupním řetězci. Tento proces návratu k předchozímu stavu pro vyhledání shody se označuje jako navracení.  
  
 Zvažte například vzor `.*(es)`regulárního výrazu, který odpovídá znakům "ES" a všem znakům, které jí předcházejí. Jak znázorňuje následující příklad, pokud je vstupní řetězec zadán jako „Essential services are provided by regular expressions.“, shoduje se vzor s celým řetězcem a obsahuje výraz „es“ ve slově „expressions“.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 Chcete-li provést tuto akci, používá modul regulárních výrazů mechanismus navracení takto:  
  
- Odpovídá `.*` typu (který odpovídá žádnému nebo více výskytům libovolného znaku) s celým vstupním řetězcem.  
  
- Pokusí se najít shodu pro písmeno „e“ ve vzoru regulárního výrazu. Vstupní řetězec však nemá žádné odpovídající zbývající znaky.  
  
- Navrátí se k poslední úspěšné shodě „Essential services are provided by regular expressions“ a pokusí se najít shodu pro písmeno „e“ s tečkou na konci věty. Tato shoda se nezdaří.  
  
- Bude pokračovat v navracení k předchozí úspěšné shodě vždy po jednom znaku, dokud nebude vyhledán nezávazně se shodující podřetězec „Essential services are provided by regular expr“. Poté porovná písmeno „e“ ve vzoru s druhým písmenem „e“ ve výrazu „expressions“ a najde shodu.  
  
- Porovná písmeno „s“ ve vzoru s písmenem „s“, které následuje za shodujícím se znakem „e“ (první výskyt písmene „s“ ve výrazu „expressions“). Tato shoda je úspěšná.  
  
 Pokud použijete mechanismus navracení, vyžaduje shoda vzoru regulárního výrazu se vstupním řetězcem, který má 55 znaků, celkem 67 operací porovnání. Obecně platí, že pokud vzor regulárních výrazů má jedinou konstrukci alternace nebo jediný volitelný kvantifikátor, je počet operací porovnání vyžadovaný pro shodu vzoru více než dvakrát větší než počet znaků ve vstupním řetězci.  
  
 [Zpět na začátek](#top)  
  
<a name="backtracking_with_nested_optional_quantifiers"></a>   
## <a name="backtracking-with-nested-optional-quantifiers"></a>Mechanismus navracení s vnořenými volitelnými kvantifikátory  
 Počet operací porovnání vyžadovaný pro shodu vzoru regulárního výrazu lze zvýšit exponenciálně, pokud vzor obsahuje velký počet konstrukcí alternace, pokud obsahuje vnořené konstrukce alternace, nebo pokud obsahuje vnořené volitelné kvantifikátory, což je nejčastější případ. Například vzor `^(a+)+$` regulárního výrazu je navržen tak, aby odpovídal kompletnímu řetězci, který obsahuje jeden nebo více znaků "a". Příklad obsahuje dva vstupní řetězce stejné délky, ale pouze první řetězec odpovídá vzoru. <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> Třída se používá k určení, jak dlouho operace porovnávání trvá.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Jak výstup v příkladu znázorňuje, trvalo modulu regulárních výrazů ve srovnání s délkou trvání identifikace odpovídajícího řetězce dvakrát tak dlouho, než vyhledal, že vstupní řetězec neodpovídá vzoru. Je to proto, že neúspěšná shoda vždy představuje nejhorší případ. Modul regulárních výrazů musí prohledat všechny možné cesty dat předtím, než dojde k závěru, že shoda je neúspěšná, a vnořené závorky vytvoří velký počet dodatečných cest napříč daty. Modul regulárních výrazů dojde k závěru, že druhý řetězec neodpovídá vzoru následujícím způsobem:  
  
- Kontroluje, zda se jednalo o začátek řetězce, a pak odpovídá prvních pěti znakům v řetězci se vzorem `a+`. Poté určí, zda řetězec neobsahuje žádné další skupiny znaků „a“. Nakonec ověří konec řetězce. Vzhledem k tomu, že v řetězci zůstává jeden další znak, shoda se nezdaří. Tato nezdařená shoda vyžaduje 9 porovnání. Modul regulárních výrazů také ukládá informace o stavu ze shody „a“ (který budeme nazývat shoda 1), „aa“ (shoda 2), „aaa“ (shoda 3) a „aaaa“ (shoda 4).  
  
- Vrátí se k předchozí uložené shodě 4. Určí, že existuje další znak „a“, který lze přiřadit dodatečné zachycené skupině. Nakonec ověří konec řetězce. Vzhledem k tomu, že v řetězci zůstává jeden další znak, shoda se nezdaří. Tato neúspěšná shoda vyžaduje 4 porovnání. Zatím bylo provedeno celkem 13 porovnání.  
  
- Vrátí se k dřív uložené shodě 3. Určí, že existují další dva znaky „a“, které lze přiřadit dodatečné zachycené skupině. Test konce řetězce se však nezdaří. Poté se vrátí ke shodě 3 a pokusí se porovnat další dva znaky „a“ v dodatečné zachycené skupině. Test konce řetězce se však ani tentokrát nezdaří. Tyto nezdařené shody vyžadují 12 porovnání. Doposud byl proveden celkem 25 porovnání.  
  
 Porovnání vstupního řetězce s regulárním výrazem pokračuje tímto způsobem, dokud se modul regulárních výrazů nepokusí vyhledat všechny možné kombinace shody, a poté dojde k závěru, že neexistuje žádná shoda. Vzhledem k vnořeným kvantifikátorům je toto porovnání typu O (2<sup>n</sup>) nebo exponenciální operace, kde *n* je počet znaků ve vstupním řetězci. To znamená, že v nejhorším případě vyžaduje vstupní znak o délce 30 znaků přibližně 1 073 741 824 porovnání a vstupní znak o délce 40 znaků vyžaduje přibližně 1 099 511 627 776 porovnání. Pokud používáte řetězce o této nebo větší délce, může dokončení metod regulárních výrazů trvat extrémně dlouhou dobu, pokud zpracovávají obsah, který se neshoduje se vzorem regulárního výrazu.  
  
 [Zpět na začátek](#top)  
  
<a name="controlling_backtracking"></a>   
## <a name="controlling-backtracking"></a>Řídicí mechanismus navracení  
 Mechanismus navracení umožňuje vytvářet výkonné a pružné regulární výrazy. Jak již však bylo znázorněno v předchozích částech, mohou tyto výhody být vázány na nepřijatelně nízký výkon. Aby nedocházelo k nadměrnému navracení, měli byste definovat interval časového limitu při vytváření instance <xref:System.Text.RegularExpressions.Regex> objektu nebo volání statické metody pro porovnání regulárního výrazu. Tento postup je popsán v následujícím oddíle. Kromě toho rozhraní .NET podporuje tři prvky regulárního výrazu, které omezují nebo potlačí zpětné navracení a které podporují složité regulární výrazy s minimální nebo žádnou pokutou výkonu: [nemechanismus](#Nonbacktracking)zpětného navracení zpět. [ kontrolní výrazy](#Lookbehind)a [kontrolní výrazy dopředného vyhledávání](#Lookahead). Další informace o jednotlivých prvcích jazyka naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
<a name="Timeout"></a>   
### <a name="defining-a-time-out-interval"></a>Definování intervalu časového limitu  
 Počínaje .NET Framework 4,5 můžete nastavit hodnotu časového limitu, která představuje nejdelší interval, který modul regulárních výrazů vyhledá jednu shodu předtím, než poruší pokus a vyvolá <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> výjimku. Interval <xref:System.TimeSpan> časového limitu určíte zadáním hodnoty <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> do konstruktoru regulárních výrazů instance. Kromě toho každá statická metoda porovnávání vzorů má přetížení s <xref:System.TimeSpan> parametrem, který umožňuje zadat hodnotu časového limitu. Ve výchozím nastavení je interval časového limitu nastaven na <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> hodnotu a modul regulárních výrazů nekončí časovým limitem.  
  
> [!IMPORTANT]
> Pokud se regulární výraz spoléhá na mechanismus navracení, doporučujeme vždy nastavit interval časového limitu.  
  
 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> Výjimka indikuje, že modul regulárních výrazů nebyl schopen nalézt shodu v rámci zadaného časového limitu, ale neindikuje, proč byla výjimka vyvolána. Důvodem může být nadměrné používání mechanismu navracení, je však také možné, že nastavený interval časového limitu byl příliš krátký vzhledem k zatížení systému v době vyvolání výjimky. Při zpracování výjimek můžete zrušit další shody se vstupním řetězcem nebo zvýšit interval časového limitu a opakovat operaci porovnání.  
  
 Například následující kód volá <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktor pro vytvoření instance <xref:System.Text.RegularExpressions.Regex> objektu s hodnotou časového limitu jedna sekunda. Vzor `(a+)+$`regulárního výrazu, který se shoduje s jednou nebo více sekvencemi jednoho nebo více znaků "a" na konci řádku, podléhá nadměrnému navrácení. <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> Pokud je vyvolána, příklad zvyšuje hodnotu časového limitu až do maximálního intervalu tři sekund. Poté zruší pokus o shodu se vzorem.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  
  
<a name="Nonbacktracking"></a>   
### <a name="nonbacktracking-subexpression"></a>Podvýraz bez mechanismu navracení  
 Prvek jazyka dílčího *výrazu* `)` potlačuje zpětné navrácení v dílčím výrazu. `(?>` Slouží k zamezení problémům s výkonem, které souvisí s neúspěšnými shodami.  
  
 Následující příklad znázorňuje, jakým způsobem potlačení mechanismu navracení zlepšuje výkon při použití vnořených kvantifikátorů. Měří čas, který modul regulárních výrazů potřebuje k určení toho, zda se vstupní řetězec neshoduje s dvěma regulárními výrazy. První regulární výraz používá mechanismus navracení k tomu, aby se pokusil porovnat řetězec, který obsahuje jeden výskyt nebo několik výskytů jedné nebo několika šestnáctkových číslic následovaných dvojtečkou, následovaných jednou nebo několika šestnáctkovými číslicemi, následovaných dvěma dvojtečkami. Druhý regulární výraz je shodný s prvním výrazem, s výjimkou toho, že zakáže mechanismus navracení. Výstup z příkladu ukazuje, že zlepšení výkonu plynoucí ze zakázání mechanismu navracení je značné.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  
  
<a name="Lookbehind"></a>   
### <a name="lookbehind-assertions"></a>Kontrolní výrazy zpětného vyhledávání  
 Rozhraní .NET obsahuje dva prvky jazyka `(?<=`, dílčí *výraz* `)` a `(?<!`dílčí *výraz*`)`, které odpovídají předchozímu znaku nebo znakům ve vstupním řetězci. Oba prvky jazyka jsou kontrolní výrazy s nulovou šířkou; To znamená, že určují, zda znak nebo znaky, které bezprostředně předcházejí aktuálnímu znaku, mohouodpovídat podvýrazu bez posunutí nebo navrácení.  
  
 `(?<=`dílčí *výraz* je kontrolní výraz pozitivního zpětného vyhledávání; to znamená, že znak nebo znaky před aktuální pozicí se musí shodovat s podvýrazem. `)` `(?<!`*dílčí výraz* `)` je kontrolní výraz negativního zpětného vyhledávání; to znamená, že znak nebo znaky před aktuální pozicí nesmíodpovídat podvýrazu. Kontrolní výrazy pozitivního i negativního zpětného vyhledávání jsou nejužitečnější, pokud je dílčí *výraz* podmnožinou předchozího dílčího výrazu.  
  
 Následující příklad používá dva ekvivalentní vzory regulárních výrazů, které ověřují uživatelské jméno v e-mailové adrese. První vzor je ovlivněn nízkým výkonem z důvodu nadměrného používání mechanismu navracení. Druhý vzor upraví první regulární výraz nahrazením vnořeného kvantifikátoru kontrolním výrazem pozitivního zpětného vyhledávání. Výstup z příkladu zobrazuje dobu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provádění metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 První vzor `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`[0-9A-Z]`|Porovná alfanumerický znak. U tohoto porovnání se nerozlišují malá a velká písmena <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> , protože metoda je volána <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> s možností.|  
|`[-.\w]*`|Porovná žádný či jeden výskyt nebo několik výskytů spojovníku, tečky nebo znaku slova.|  
|`[0-9A-Z]`|Porovná alfanumerický znak.|  
|`([-.\w]*[0-9A-Z])*`|Porovná žádný výskyt nebo několik výskytů kombinace nuly nebo několika spojovníků, teček či znaků slova, následovaných alfanumerickým znakem. Toto je první zachytávající skupina.|  
|`@`|Porovná symbol při přihlášení (\@"").|  
  
 Druhý vzor `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`regulárního výrazu, používá kontrolní výraz pozitivního zpětného vyhledávání. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`[0-9A-Z]`|Porovná alfanumerický znak. U tohoto porovnání se nerozlišují malá a velká písmena <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> , protože metoda je volána <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> s možností.|  
|`[-.\w]*`|Porovná žádný výskyt nebo několik výskytů spojovníku, tečky nebo znaku slova.|  
|`(?<=[0-9A-Z])`|Ověří poslední shodující se znak a pokračuje v porovnání, pokud se jedná o znak alfanumerický. Alfanumerické znaky jsou podmnožinou množiny, která sestává z teček, spojovníků a znaků slov.|  
|`@`|Porovná symbol při přihlášení (\@"").|  
  
<a name="Lookahead"></a>   
### <a name="lookahead-assertions"></a>Kontrolní výrazy dopředného vyhledávání  
 Rozhraní .NET obsahuje dva prvky jazyka `(?=`, dílčí *výraz* `)` a `(?!`dílčí *výraz*`)`, které odpovídají dalšímu znaku nebo znakům ve vstupním řetězci. Oba prvky jazyka jsou kontrolní výrazy s nulovou šířkou; To znamená, že určují, zda znak nebo znaky, které bezprostředně následují za aktuálním znakem,mohou odpovídat podvýrazu bez posunutí nebo navrácení.  
  
 `(?=`dílčí *výraz* je pozitivní kontrolní výraz dopředného vyhledávání; to znamená, že znak nebo znaky za aktuální pozicí se musí shodovat s podvýrazem. `)` `(?!`*dílčí výraz* `)` je negativní kontrolní výraz dopředného vyhledávání; to znamená, že znak nebo znaky za aktuální pozicí se nesmíshodovat s podvýrazem. Kladné i záporné kontrolní výrazy dopředného vyhledávání jsou nejužitečnější, pokud je dílčí *výraz* podmnožinou dalšího dílčího výrazu.  
  
 Následující příklad používá dva ekvivalentní vzory regulárních výrazů, které ověřují plně kvalifikovaný název typu. První vzor je ovlivněn nízkým výkonem z důvodu nadměrného používání mechanismu navracení. Druhý vzor upraví první regulární výraz nahrazením vnořeného kvantifikátoru kontrolním výrazem pozitivního dopředného vyhledávání. Výstup z příkladu zobrazuje dobu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provádění metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 První vzor `^(([A-Z]\w*)+\.)*[A-Z]\w*$`regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`([A-Z]\w*)+\.`|Porovná abecední znak (A-Z) následovaný žádným nebo několika znaky slova jednou nebo vícekrát, následovaných tečkou. U tohoto porovnání se nerozlišují malá a velká písmena <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> , protože metoda je volána <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> s možností.|  
|`(([A-Z]\w*)+\.)*`|Porovná předchozí vzor nulakrát nebo vícekrát.|  
|`[A-Z]\w*`|Porovná abecední znak následovaný žádným nebo několika znaky slova.|  
|`$`|Ukončí porovnávání na konci vstupního řetězce.|  
  
 Druhý vzor `^((?=[A-Z])\w+\.)*[A-Z]\w*$`regulárního výrazu, používá kontrolní výraz pozitivního dopředného vyhledávání. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`(?=[A-Z])`|Ověří první znak a pokračuje v porovnávání, pokud se jedná o abecední znak (A-Z). U tohoto porovnání se nerozlišují malá a velká písmena <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> , protože metoda je volána <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> s možností.|  
|`\w+\.`|Porovná jeden nebo více znaků slova následovaných tečkou.|  
|`((?=[A-Z])\w+\.)*`|Porovná vzor jednoho nebo několika znaků slova následovaných tečkou nulakrát nebo vícekrát. Prvním znakem slova musí být abecední znak.|  
|`[A-Z]\w*`|Porovná abecední znak následovaný žádným nebo několika znaky slova.|  
|`$`|Ukončí porovnávání na konci vstupního řetězce.|  
  
 [Zpět na začátek](#top)  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)
- [Konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)
- [Seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)
