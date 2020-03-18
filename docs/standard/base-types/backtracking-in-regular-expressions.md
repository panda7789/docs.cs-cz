---
title: Navracení v regulárních výrazech rozhraní .NET
description: Přečtěte si, jak řídit navracení v porovnávání vzorů regulárních výrazů.
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
ms.openlocfilehash: 1b61cc88de4f73abfe6d8e77f8f32c2c71e70a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158061"
---
# <a name="backtracking-in-regular-expressions"></a>Zpětné navracení v regulárních výrazech
K zpětnému navracení dochází, když vzor regulárního výrazu obsahuje volitelné [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) nebo [konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)a modul regulárních výrazů se vrátí do předchozího uloženého stavu, aby pokračoval v hledání shody. Navracení má klíčový význam pro výkon regulárních výrazů, což umožňuje, aby výrazy byly výkonné a pružné a aby vyhovovaly velmi složitým vzorům. Tento výkon však zároveň něco stojí. Navracení je často jediným nejdůležitějším faktorem, který ovlivňuje výkon modulu regulárních výrazů. Vývojář má naštěstí vliv na chování modulu regulárních výrazů a způsob používání mechanismu navracení. V tomto tématu je vysvětleno fungování a ovládání mechanismu navracení.  
  
> [!NOTE]
> Obecně platí, že modul nedeterministický konečný automaton (NFA), jako je modul regulárních výrazů .NET, klade na vývojáře odpovědnost za vytváření efektivních a rychlých regulárních výrazů.  

## <a name="linear-comparison-without-backtracking"></a>Lineární porovnání bez mechanismu navracení  
 Pokud vzor regulárního výrazu nemá žádné volitelné kvantifikátory nebo konstrukce alternace, bude modul regulárních výrazů spuštěn v lineárním čase. Což znamená, že jakmile se modul regulárních výrazů shoduje s prvním prvkem jazyka ve vzorci s textem ve vstupním řetězci, pokusí se vyhledat další prvek jazyka ve vzoru s dalším znakem nebo skupinou znaků ve vstupním řetězci. Tento postup se opakuje, dokud je shoda buď úspěšná, anebo neúspěšná. V obou případech se modul regulárních výrazů posune vždy o jeden znak ve vstupním řetězci.  
  
 V následujícím příkladu je uvedena ukázka. Regulární `e{2}\w\b` výraz vyhledá dva výskyty písmene "e" následované libovolným znakem slova následovaným hranicí slova.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 I když tento regulární `{2}`výraz obsahuje kvantifikátor , je vyhodnocován lineárním způsobem. Modul regulárních výrazů `{2}` neustoupí, protože není volitelným kvantifikátorem; určuje přesné číslo a nikoli proměnný počet, kolikrát se musí předchozí dílčí výraz shodovat. V důsledku toho se modul regulárních výrazů pokusí shodovat se vzorem regulárního výrazu se vstupním řetězcem, jak je znázorněno v následující tabulce.  
  
|Operace|Pozice ve vzoru|Pozice v řetězci|Výsledek|  
|---------------|-------------------------|------------------------|------------|  
|1|e|"needing a reed" (index 0)|Žádná shoda.|  
|2|e|"eeding a reed" (index 1)|Možná shoda.|  
|3|E{2}|"eding a reed" (index 2)|Možná shoda.|  
|4|\w|"ding a reed" (index 3)|Možná shoda.|  
|5|\b|"ing a reed" (index 4)|Možná shoda se nezdaří.|  
|6|e|"eding a reed" (index 2)|Možná shoda.|  
|7|E{2}|"ding a reed" (index 3)|Možná shoda se nezdaří.|  
|8|e|"ding a reed" (index 3)|Shoda se nezdaří.|  
|9|e|"ing a reed" (index 4)|Žádná shoda.|  
|10|e|"ng a reed" (index 5)|Žádná shoda.|  
|11|e|"g a reed" (index 6)|Žádná shoda.|  
|12|e|" jazýčkové" (index 7)|Žádná shoda.|  
|13|e|"jazýčkové" (index 8)|Žádná shoda.|  
|14|e|" reed" (index 9)|Žádná shoda.|  
|15|e|"reed" (index 10)|Žádná shoda|  
|16|e|"eed" (index 11)|Možná shoda.|  
|17|E{2}|"ed" (index 12)|Možná shoda.|  
|18|\w|"d" (index 13)|Možná shoda.|  
|19|\b|"" (index 14)|Shoda.|  
  
 Pokud vzor regulárního výrazu neobsahuje žádné volitelné kvantifikátory nebo konstrukce alternace, musí maximální počet porovnání odpovídající vzoru regulárního výrazu se vstupním řetězcem být zhruba ekvivalentní počtu znaků ve vstupním řetězci. V tomto případě používá modul regulárních výrazů 19 porovnání k identifikaci možných shod v tomto řetězci o 13 znacích.  Jinými slovy to znamená, že modul regulárních výrazů je spuštěn v téměř lineárním čase, pokud neobsahuje žádné volitelné kvantifikátory nebo konstrukce alternace.

## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>Navracení pomocí volitelných kvantifikátorů nebo konstrukcí alternace  
 Pokud regulární výraz zahrnuje volitelné kvantifikátory nebo alternace konstrukce, hodnocení vstupního řetězce již není lineární. Porovnání vzorů s modulem NFA řídí prvky jazyka v regulárním výrazu, nikoli znaky, které se musí shodovat ve vstupním řetězci. Proto se modul regulárních výrazů pokouší o úplnou shodu volitelných nebo alternativních dílčích výrazů. Jakmile přejde na další prvek jazyka v dílčím výrazu a shoda není úspěšná, může modul regulárních výrazů opustit část úspěšné shody a vrátit se ke dříve uloženému stavu v zájmu shody celého regulárního výrazu ve vstupním řetězci. Tento proces návratu k předchozímu stavu pro vyhledání shody se označuje jako navracení.  
  
 Zvažte například vzor `.*(es)`regulárního výrazu , který odpovídá znakům "es" a všem znakům, které mu předchází. Jak znázorňuje následující příklad, pokud je vstupní řetězec zadán jako „Essential services are provided by regular expressions.“, shoduje se vzor s celým řetězcem a obsahuje výraz „es“ ve slově „expressions“.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 Chcete-li provést tuto akci, používá modul regulárních výrazů mechanismus navracení takto:  
  
- Odpovídá `.*` (který odpovídá nula, jeden nebo více výskytů libovolného znaku) s celý vstupní řetězec.  
  
- Pokusí se najít shodu pro písmeno „e“ ve vzoru regulárního výrazu. Vstupní řetězec však nemá žádné odpovídající zbývající znaky.  
  
- Navrátí se k poslední úspěšné shodě „Essential services are provided by regular expressions“ a pokusí se najít shodu pro písmeno „e“ s tečkou na konci věty. Tato shoda se nezdaří.  
  
- Bude pokračovat v navracení k předchozí úspěšné shodě vždy po jednom znaku, dokud nebude vyhledán nezávazně se shodující podřetězec „Essential services are provided by regular expr“. Poté porovná písmeno „e“ ve vzoru s druhým písmenem „e“ ve výrazu „expressions“ a najde shodu.  
  
- Porovná písmeno „s“ ve vzoru s písmenem „s“, které následuje za shodujícím se znakem „e“ (první výskyt písmene „s“ ve výrazu „expressions“). Tato shoda je úspěšná.  
  
 Pokud použijete mechanismus navracení, vyžaduje shoda vzoru regulárního výrazu se vstupním řetězcem, který má 55 znaků, celkem 67 operací porovnání. Obecně platí, že pokud vzor regulárních výrazů má jedinou konstrukci alternace nebo jediný volitelný kvantifikátor, je počet operací porovnání vyžadovaný pro shodu vzoru více než dvakrát větší než počet znaků ve vstupním řetězci.

## <a name="backtracking-with-nested-optional-quantifiers"></a>Mechanismus navracení s vnořenými volitelnými kvantifikátory  
 Počet operací porovnání vyžadovaný pro shodu vzoru regulárního výrazu lze zvýšit exponenciálně, pokud vzor obsahuje velký počet konstrukcí alternace, pokud obsahuje vnořené konstrukce alternace, nebo pokud obsahuje vnořené volitelné kvantifikátory, což je nejčastější případ. Například vzor regulárního výrazu `^(a+)+$` je navržen tak, aby odpovídal úplnému řetězci, který obsahuje jeden nebo více znaků "a". Příklad obsahuje dva vstupní řetězce stejné délky, ale pouze první řetězec odpovídá vzoru. Třída <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> se používá k určení, jak dlouho trvá operace shody.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Jak výstup v příkladu znázorňuje, trvalo modulu regulárních výrazů ve srovnání s délkou trvání identifikace odpovídajícího řetězce dvakrát tak dlouho, než vyhledal, že vstupní řetězec neodpovídá vzoru. Je to proto, že neúspěšná shoda vždy představuje nejhorší případ. Modul regulárních výrazů musí prohledat všechny možné cesty dat předtím, než dojde k závěru, že shoda je neúspěšná, a vnořené závorky vytvoří velký počet dodatečných cest napříč daty. Modul regulárních výrazů dojde k závěru, že druhý řetězec neodpovídá vzoru následujícím způsobem:  
  
- Zkontroluje, zda byl na začátku řetězce, a pak odpovídá prvních pěti `a+`znakům v řetězci se vzorem . Poté určí, zda řetězec neobsahuje žádné další skupiny znaků „a“. Nakonec ověří konec řetězce. Vzhledem k tomu, že v řetězci zůstává jeden další znak, shoda se nezdaří. Tato nezdařená shoda vyžaduje 9 porovnání. Modul regulárních výrazů také ukládá informace o stavu ze shody „a“ (který budeme nazývat shoda 1), „aa“ (shoda 2), „aaa“ (shoda 3) a „aaaa“ (shoda 4).  
  
- Vrátí se k předchozí uložené shodě 4. Určí, že existuje další znak „a“, který lze přiřadit dodatečné zachycené skupině. Nakonec ověří konec řetězce. Vzhledem k tomu, že v řetězci zůstává jeden další znak, shoda se nezdaří. Tato neúspěšná shoda vyžaduje 4 porovnání. Zatím bylo provedeno celkem 13 porovnání.  
  
- Vrátí se k dříve uložené shodě 3. Určí, že existují další dva znaky „a“, které lze přiřadit dodatečné zachycené skupině. Test konce řetězce se však nezdaří. Poté se vrátí ke shodě 3 a pokusí se porovnat další dva znaky „a“ v dodatečné zachycené skupině. Test konce řetězce se však ani tentokrát nezdaří. Tyto nezdařené shody vyžadují 12 porovnání. Dosud bylo provedeno celkem 25 srovnání.  
  
 Porovnání vstupního řetězce s regulárním výrazem pokračuje tímto způsobem, dokud se modul regulárních výrazů nepokusí vyhledat všechny možné kombinace shody, a poté dojde k závěru, že neexistuje žádná shoda. Z důvodu vnořené kvantifikátory toto porovnání je O(2<sup>n</sup>) nebo exponenciální operace, kde *n* je počet znaků ve vstupním řetězci. To znamená, že v nejhorším případě vyžaduje vstupní znak o délce 30 znaků přibližně 1 073 741 824 porovnání a vstupní znak o délce 40 znaků vyžaduje přibližně 1 099 511 627 776 porovnání. Pokud používáte řetězce o této nebo větší délce, může dokončení metod regulárních výrazů trvat extrémně dlouhou dobu, pokud zpracovávají obsah, který se neshoduje se vzorem regulárního výrazu.

## <a name="controlling-backtracking"></a>Řídicí mechanismus navracení  
 Mechanismus navracení umožňuje vytvářet výkonné a pružné regulární výrazy. Jak již však bylo znázorněno v předchozích částech, mohou tyto výhody být vázány na nepřijatelně nízký výkon. Chcete-li zabránit nadměrnému navracení, měli byste definovat časový <xref:System.Text.RegularExpressions.Regex> interval při vytváření instancí objektu nebo volání statické metody porovnávání regulárních výrazů. Tento postup je popsán v následujícím oddíle. Kromě toho rozhraní .NET podporuje tři prvky jazyka regulárních výrazů, které omezují nebo potlačují backtracking a podporují složité regulární výrazy s malou nebo žádnou sankcí výkonu: [atomické skupiny](#atomic-groups), [kontrolní výrazy zpětného získání](#lookbehind-assertions)a [kontrolní výrazy dopředného vyhledávání](#lookahead-assertions). Další informace o jednotlivých elementech jazyka naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  

### <a name="defining-a-time-out-interval"></a>Definování intervalu časového limitu  
 Počínaje rozhraním .NET Framework 4.5 můžete nastavit hodnotu časového času, která představuje nejdelší interval, kdy modul regulárních <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> výrazů vyhledá jednu shodu před tím, než opustí pokus a vyvolá výjimku. Časový interval zadáte zadáním <xref:System.TimeSpan> hodnoty konstruktoru, <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> například regulárních výrazů. Kromě toho každá metoda statické hořce <xref:System.TimeSpan> vzor má přetížení s parametrem, který umožňuje zadat hodnotu časového rozlišení. Ve výchozím nastavení je časový limit <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> nastaven na a modul regulárních výrazů není časový limit.  
  
> [!IMPORTANT]
> Pokud se regulární výraz spoléhá na mechanismus navracení, doporučujeme vždy nastavit interval časového limitu.  
  
 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> Výjimka označuje, že modul regulárních výrazů nemohl najít shodu v zadaném časovém intervalu, ale neoznačuje, proč byla výjimka vyvolána. Důvodem může být nadměrné používání mechanismu navracení, je však také možné, že nastavený interval časového limitu byl příliš krátký vzhledem k zatížení systému v době vyvolání výjimky. Při zpracování výjimek můžete zrušit další shody se vstupním řetězcem nebo zvýšit interval časového limitu a opakovat operaci porovnání.  
  
 Například následující kód volá <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Text.RegularExpressions.Regex> instance objektu s hodnotou časového času jedné sekundy. Vzor regulárního výrazu `(a+)+$`, který odpovídá jedné nebo více sekvencí jednoho nebo více znaků "a" na konci řádku, podléhá nadměrnému navracení. Pokud <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> je vyvolána, příklad zvyšuje hodnotu časového limitu až na maximální interval tři sekundy. Poté zruší pokus o shodu se vzorem.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  

### <a name="atomic-groups"></a>Atomové skupiny
 Prvek `(?>` jazyka *podvýrazpotlačí* `)` backtracking do dílčího výrazu. Jakmile bude úspěšně spárována, nevzdá se žádné části své shody s následným navracením. Například ve vzoru `(?>\w*\d*)1`, `1` pokud nelze spárovat, `\d*` se nevzdává žádné hospodařících, `1` i když to znamená, že by umožnil úspěšně srovnat. Atomické skupiny mohou pomoci zabránit problémům s výkonem spojeným s neúspěšnými shodami.
  
 Následující příklad znázorňuje, jakým způsobem potlačení mechanismu navracení zlepšuje výkon při použití vnořených kvantifikátorů. Měří čas, který modul regulárních výrazů potřebuje k určení toho, zda se vstupní řetězec neshoduje s dvěma regulárními výrazy. První regulární výraz používá mechanismus navracení k tomu, aby se pokusil porovnat řetězec, který obsahuje jeden výskyt nebo několik výskytů jedné nebo několika šestnáctkových číslic následovaných dvojtečkou, následovaných jednou nebo několika šestnáctkovými číslicemi, následovaných dvěma dvojtečkami. Druhý regulární výraz je shodný s prvním výrazem, s výjimkou toho, že zakáže mechanismus navracení. Výstup z příkladu ukazuje, že zlepšení výkonu plynoucí ze zakázání mechanismu navracení je značné.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  

### <a name="lookbehind-assertions"></a>Kontrolní výrazy zpětného vyhledávání  
 Síť .NET obsahuje `(?<=`dva elementy jazyka, *dílčí výraz* `)` a `(?<!` *podvýraz*`)`, které odpovídají předchozímu znaku nebo znakům ve vstupním řetězci. Oba elementy jazyka jsou kontrolní výrazy s nulovou šířkou; to znamená, že určují, zda znak nebo znaky, které bezprostředně předcházejí aktuální znak může být uzavřeno *podvýraz*, bez postupující nebo backtracking.  
  
 `(?<=`*podvýraz* `)` je kontrolní výraz pozitivního zpětného vyhledávání; to znamená, že znak nebo znaky před aktuální pozicí musí odpovídat *podvýrazu*. `(?<!`*podvýraz* `)` je kontrolní výraz negativního zpětného vyhledávání; to znamená, že znak nebo znaky před aktuální pozicí se nesmí shodovat s *podvýrazem*. Kontrolní výrazy pozitivního i negativního zpětného vyhledávání jsou nejužitečnější, pokud je *dílčí výraz* podmnožinou předchozího dílčího výrazu.  
  
 Následující příklad používá dva ekvivalentní vzory regulárních výrazů, které ověřují uživatelské jméno v e-mailové adrese. První vzor je ovlivněn nízkým výkonem z důvodu nadměrného používání mechanismu navracení. Druhý vzor upraví první regulární výraz nahrazením vnořeného kvantifikátoru kontrolním výrazem pozitivního zpětného vyhledávání. Výstup z příkladu zobrazuje čas <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> spuštění metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 První vzor regulárního výrazu , je definován tak, `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`[0-9A-Z]`|Porovná alfanumerický znak. Toto porovnání je malá a <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> velká písmena, protože metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možností.|  
|`[-.\w]*`|Porovná žádný či jeden výskyt nebo několik výskytů spojovníku, tečky nebo znaku slova.|  
|`[0-9A-Z]`|Porovná alfanumerický znak.|  
|`([-.\w]*[0-9A-Z])*`|Porovná žádný výskyt nebo několik výskytů kombinace nuly nebo několika spojovníků, teček či znaků slova, následovaných alfanumerickým znakem. Toto je první zachytávající skupina.|  
|`@`|Porovná znak at\@(" ").|  
  
 Druhý vzor regulárního výrazu , `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`používá kontrolní výraz pozitivního zpětného vyhledávání. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`[0-9A-Z]`|Porovná alfanumerický znak. Toto porovnání je malá a <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> velká písmena, protože metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možností.|  
|`[-.\w]*`|Porovná žádný výskyt nebo několik výskytů spojovníku, tečky nebo znaku slova.|  
|`(?<=[0-9A-Z])`|Ověří poslední shodující se znak a pokračuje v porovnání, pokud se jedná o znak alfanumerický. Alfanumerické znaky jsou podmnožinou množiny, která sestává z teček, spojovníků a znaků slov.|  
|`@`|Porovná znak at\@(" ").|  

### <a name="lookahead-assertions"></a>Kontrolní výrazy dopředného vyhledávání  
 Síť .NET obsahuje `(?=`dva elementy jazyka, *dílčí výraz* `)` a `(?!` *podvýraz*`)`, které odpovídají dalšímu znaku nebo znakům ve vstupním řetězci. Oba elementy jazyka jsou kontrolní výrazy s nulovou šířkou; to znamená, že určují, zda znak nebo znaky, které bezprostředně následují za aktuálním znakem, mohou být spárovány *podvýrazem*, bez posunu nebo navracení.  
  
 `(?=`*podvýraz* `)` je kontrolní výraz pozitivního dopředného vyhledávání; to znamená, že znak nebo znaky za aktuální pozicí musí odpovídat *podvýrazu*. `(?!`*podvýraz* `)` je kontrolní výraz negativního dopředného vyhledávání; to znamená, že znak nebo znaky za aktuální pozicí se nesmí shodovat s *podvýrazem*. Pozitivní i negativní dopředné výrazy jsou nejužitečnější, pokud je *dílčí výraz* podmnožinou dalšího dílčího výrazu.  
  
 Následující příklad používá dva ekvivalentní vzory regulárních výrazů, které ověřují plně kvalifikovaný název typu. První vzor je ovlivněn nízkým výkonem z důvodu nadměrného používání mechanismu navracení. Druhý vzor upraví první regulární výraz nahrazením vnořeného kvantifikátoru kontrolním výrazem pozitivního dopředného vyhledávání. Výstup z příkladu zobrazuje čas <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> spuštění metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 První vzor regulárního výrazu , je definován tak, `^(([A-Z]\w*)+\.)*[A-Z]\w*$`jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`([A-Z]\w*)+\.`|Porovná abecední znak (A-Z) následovaný žádným nebo několika znaky slova jednou nebo vícekrát, následovaných tečkou. Toto porovnání je malá a <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> velká písmena, protože metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možností.|  
|`(([A-Z]\w*)+\.)*`|Porovná předchozí vzor nulakrát nebo vícekrát.|  
|`[A-Z]\w*`|Porovná abecední znak následovaný žádným nebo několika znaky slova.|  
|`$`|Ukončí porovnávání na konci vstupního řetězce.|  
  
 Druhý vzor regulárního výrazu , `^((?=[A-Z])\w+\.)*[A-Z]\w*$`používá kontrolní výraz pozitivního dopředného vyhledávání. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`(?=[A-Z])`|Ověří první znak a pokračuje v porovnávání, pokud se jedná o abecední znak (A-Z). Toto porovnání je malá a <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> velká písmena, protože metoda je volána s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možností.|  
|`\w+\.`|Porovná jeden nebo více znaků slova následovaných tečkou.|  
|`((?=[A-Z])\w+\.)*`|Porovná vzor jednoho nebo několika znaků slova následovaných tečkou nulakrát nebo vícekrát. Prvním znakem slova musí být abecední znak.|  
|`[A-Z]\w*`|Porovná abecední znak následovaný žádným nebo několika znaky slova.|  
|`$`|Ukončí porovnávání na konci vstupního řetězce.|  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)
- [Konstrukce alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)
- [Seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)
