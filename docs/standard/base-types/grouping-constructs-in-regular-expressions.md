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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aa7c35ebc06fb67d9cf6216233d2bed65ae76ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789269"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Seskupovací konstrukce v regulárních výrazech
Seskupovací konstrukce vymezují dílčí výrazy regulárních výrazů a zachytávají podřetězce vstupního řetězce. Seskupovací konstrukce můžete provádět následující akce:  
  
- Porovná dílčí výraz, který se opakuje ve vstupním řetězci.  
  
- Použijte kvantifikátor na dílčí výraz, který má více prvky jazyka regulárních výrazů. Další informace o kvantifikátory, naleznete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Zahrnout podvýrazu řetězec, který je vrácený <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody.  
  
- Načíst z jednotlivých podvýrazy <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost a zpracovávat odděleně od odpovídajícího textu jako celek.  
  
 Následující tabulka uvádí seskupovací konstrukce podporuje modul regulárních výrazů rozhraní .NET a označuje, zda jsou zachytávání nebo bez zachytávání.  
  
|Seskupovací konstrukce|Zachycující nebo nezachycující|  
|------------------------|-------------------------------|  
|[Podvýrazy](#matched_subexpression)|Zachytávání|  
|[S názvem podvýrazy](#named_matched_subexpression)|Zachytávání|  
|[Definice vyrovnávací skupiny](#balancing_group_definition)|Zachytávání|  
|[Nezachycující skupiny](#noncapturing_group)|Bez zachycení|  
|[Možnosti pro skupiny](#group_options)|Bez zachycení|  
|[Kontrolní výrazy pozitivního dopředného vyhledávání s nulovou šířkou](#zerowidth_positive_lookahead_assertion)|Bez zachycení|  
|[Kontrolní výrazy negativního dopředného vyhledávání s nulovou šířkou](#zerowidth_negative_lookahead_assertion)|Bez zachycení|  
|[Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou](#zerowidth_positive_lookbehind_assertion)|Bez zachycení|  
|[Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou](#zerowidth_negative_lookbehind_assertion)|Bez zachycení|  
|[Podvýrazy bez mechanismu navracení](#nonbacktracking_subexpression)|Bez zachycení|  
  
 Informace o skupinách a model objektu regulárního výrazu, naleznete v tématu [seskupovací konstrukce a objekty regulárních výrazů](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Podvýrazy  
 Následující seskupovací konstrukce zachytí odpovídající dílčí výraz:  
  
 `(` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný platný vzor regulárního výrazu. Zaznamená, že pomocí závorek jsou automaticky číslovány zleva doprava na základě pořadí levými závorkami v regulárním výrazu, od jedné. Zachytávání číslované nula je text, odpovídající vzor celý regulární výraz.  
  
> [!NOTE]
>  Ve výchozím nastavení `(` *dílčí výraz* `)` jazyk prvek zachytí odpovídající dílčí výraz. Avšak v tom případě <xref:System.Text.RegularExpressions.RegexOptions> parametr metody porovnávání vzoru regulárního výrazu zahrnuje <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> příznak, nebo pokud `n` možnost platí pro tento dílčí výraz (naleznete v tématu [skupině možnosti](#group_options) dále v tomto tématu), odpovídající dílčí výraz se nezachytí.  
  
 Je možné otevřít zachycené skupiny čtyři způsoby:  
  
- S použitím zpětných odkazů sestavení v rámci regulárního výrazu. Odpovídající dílčí výraz se odkazuje v stejný regulární výraz pomocí syntaxe `\` *číslo*, kde *číslo* je řadová číslovka zachycený dílčí výraz.  
  
- S použitím pojmenovaný zpětný odkaz sestavení v rámci regulárního výrazu. Odpovídající dílčí výraz se odkazuje v stejný regulární výraz pomocí syntaxe `\k<` *název*`>`, kde *název* je název zachytávající skupinu, nebo `\k<` *číslo*`>`, kde *číslo* je řadová číslovka zachytávající skupina. Zachytávající skupina má výchozí název, který se shoduje s jeho ordinální číslo. Další informace najdete v tématu [pojmenované odpovídající podvýrazy](#named_matched_subexpression) dále v tomto tématu.  
  
- S použitím `$` *číslo* náhradní sekvence v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *číslo* je řadová číslovka zachycený dílčí výraz.  
  
- Programově pomocí <xref:System.Text.RegularExpressions.GroupCollection> vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. Člen na pozici nula v kolekci představuje shodu celý regulární výraz. Každý člen následné představuje odpovídající dílčí výraz. Další informace najdete v tématu [Grouping Constructs a objekty regulárních výrazů](#Objects) oddílu.  
  
 Následující příklad ukazuje regulární výraz, který identifikuje duplicitní slova v textu. Vzor regulárního výrazu dvě zachytávající skupiny představují dvě instance duplicitní slova. Druhou instanci je zachycena hlášení jeho výchozí pozice ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Vzor regulárního výrazu je následující:  
  
```  
(\w+)\s(\1)\W  
```  
  
 Následující tabulka ukazuje, jak vzorek regulárního výrazu je interpretován.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\1)`|Porovná řetězec v první zachycenou skupinou. Toto je druhá zachytávající skupina. V příkladu přiřadí ji k zachycené skupiny tak, aby počáteční pozici duplicitních slov můžete získat z `Match.Index` vlastnost.|  
|`\W`|Porovná mimoslovní znak, včetně prázdné znaky a znaky interpunkce. To brání vzor regulárního výrazu z odpovídajících slov, která začíná slovem od první zachycenou skupinou.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>S názvem podvýrazy  
 Následující seskupovací konstrukce zachytí odpovídající dílčí výraz a umožňuje přístup podle názvu nebo podle čísla:  
  
```  
(?<name>subexpression)  
```  
  
 nebo:  
  
```  
(?'name'subexpression)  
```  
  
 kde *název* je platný název skupiny, a *dílčí výraz* je libovolný platný vzor regulárního výrazu. *název* nesmí obsahovat žádné znaky interpunkce a nemůže začínat číslicí.  
  
> [!NOTE]
>  Pokud <xref:System.Text.RegularExpressions.RegexOptions> parametr metody porovnávání vzoru regulárního výrazu zahrnuje <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> příznak, nebo pokud `n` možnost platí pro tento dílčí výraz (naleznete v tématu [skupině možnosti](#group_options) dále v tomto tématu), pouze způsob, jak zachytit dílčího výrazu je explicitně název zachytávající skupiny.  
  
 Dostanete pojmenované skupiny zachycené těmito způsoby:  
  
- S použitím pojmenovaný zpětný odkaz sestavení v rámci regulárního výrazu. Odpovídající dílčí výraz se odkazuje v stejný regulární výraz pomocí syntaxe `\k<` *název*`>`, kde *název* je název zachycený dílčí výraz.  
  
- S použitím zpětných odkazů sestavení v rámci regulárního výrazu. Odpovídající dílčí výraz se odkazuje v stejný regulární výraz pomocí syntaxe `\` *číslo*, kde *číslo* je řadová číslovka zachycený dílčí výraz. Pojmenované podvýrazy jsou číslovány postupně zleva doprava po podvýrazy.  
  
- S použitím `${` *název* `}` náhradní sekvence v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *název* je název zachycený dílčí výraz.  
  
- S použitím `$` *číslo* náhradní sekvence v <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> volání metody, kde *číslo* je řadová číslovka zachycený dílčí výraz.  
  
- Programově pomocí <xref:System.Text.RegularExpressions.GroupCollection> vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. Člen na pozici nula v kolekci představuje shodu celý regulární výraz. Každý člen následné představuje odpovídající dílčí výraz. Pojmenované zachycené skupiny jsou uloženy v kolekci po číslované zachycenou skupinou.  
  
- Prostřednictvím kódu programu, tím, že poskytuje název dílčí výraz, který má <xref:System.Text.RegularExpressions.GroupCollection> indexeru objektu (v jazyce C#) nebo na jeho <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> (v jazyce Visual Basic).  
  
 Vzor regulárního výrazu jednoduché ukazuje jak číslované (nepojmenované) a pojmenované skupiny může být odkazováno prostřednictvím kódu programu nebo pomocí syntaxe jazyka regulárních výrazů. Regulární výraz `((?<One>abc)\d+)?(?<Two>xyz)(.*)` vytvoří následující zachytávání skupiny podle čísla a podle názvu. První zachytávající skupinou (číslo 0) vždy odkazuje na celý vzor.  
  
|Číslo|Název|Vzor|  
|------------|----------|-------------|  
|0|0 (výchozí název)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (výchozí název)|`((?<One>abc)\d+)`|  
|2|2 (výchozí název)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Dvě|`(?<Two>xyz)`|  
  
 Následující příklad ukazuje regulární výraz, který identifikuje duplicitních slov a slovo, které bezprostředně následuje po jednotlivých duplicitních slov. Vzor regulárního výrazu definuje dva pojmenované podvýrazy: `duplicateWord`, která představuje duplicitní slovo; a `nextWord`, která představuje slovo následující duplicitní slova.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Vzor regulárního výrazu je následujícím způsobem:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 Následující tabulka ukazuje, jak regulární výraz je interpretován.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající skupiny `duplicateWord`.|  
|`\s`|Porovná prázdný znak.|  
|`\k<duplicateWord>`|Odpovídá řetězci z zachycené skupiny s názvem `duplicateWord`.|  
|`\W`|Porovná mimoslovní znak, včetně prázdné znaky a znaky interpunkce. To brání vzor regulárního výrazu z odpovídajících slov, která začíná slovem od první zachycenou skupinou.|  
|`(?<nextWord>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající skupiny `nextWord`.|  
  
 Všimněte si, že název skupiny lze opakovat v regulárním výrazu. Například je možné pro více než jednu skupinu s názvem `digit`, jak ukazuje následující příklad. V případě duplicitní názvy, hodnoty <xref:System.Text.RegularExpressions.Group> objekt je určen při poslední úspěšné vzniku ve vstupním řetězci. Kromě toho <xref:System.Text.RegularExpressions.CaptureCollection> se načtou informace o jednotlivých zachycení stejně, jako by bylo, pokud nebyla duplicitní název skupiny.  
  
 V následujícím příkladu, regulární výraz `\D+(?<digit>\d+)\D+(?<digit>\d+)?` zahrnuje dva výskyty skupina s názvem `digit`. První `digit` pojmenovanými zachyceními skupiny jednoho nebo více znaků číslice. Druhá `digit` pojmenovanou skupinu zachycuje buď žádný nebo jeden výskyt jednoho nebo více znaků číslice. Jak výstup z příkladu, pokud se druhý zachycující skupina úspěšně shoduje s textem, hodnota textu definuje hodnoty <xref:System.Text.RegularExpressions.Group> objektu. Pokud je druhá zachytávající skupina nemůže neodpovídá vstupní řetězec, hodnota poslední úspěšná shoda definuje hodnotu <xref:System.Text.RegularExpressions.Group> objektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Následující tabulka ukazuje, jak regulární výraz je interpretován.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\D+`|Porovná jeden nebo více znaků nedesetinné číslo.|  
|`(?<digit>\d+)`|Porovná jeden nebo více znaků desítková číslice. Přiřadit shodu `digit` pojmenované skupiny.|  
|`\D+`|Porovná jeden nebo více znaků nedesetinné číslo.|  
|`(?<digit>\d+)?`|Porovná žádný nebo jeden výskyt jednoho nebo více znaků desítkových číslic. Přiřadit shodu `digit` pojmenované skupiny.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Definice vyrovnávací skupiny  
 Definici vyrovnávací skupiny odstraní definici dříve definovaného skupiny a uloží v aktuální skupině, interval mezi dříve definované skupiny a aktuální skupinou. Tato konstrukce seskupení má následující formát:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 nebo:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 kde *name1* je aktuální skupiny (nepovinné), *name2* je dříve definované skupiny, a *dílčí výraz* je libovolný platný vzor regulárního výrazu. Odstraní definici vyrovnávací skupiny definici *name2* a uloží interval mezi *name2* a *name1* v *name1*. Pokud ne *name2* skupina je definována, provided ke shodě. Protože odstranění posledního definice *name2* ukáže předchozí definici *name2*, tento konstruktor umožňuje používat zásobníku zachycení pro skupinu *name2* jako čítače pro udržování přehledu o vnořené konstrukce, jako je například závorek nebo levé a pravé závorky.  
  
 Definici vyrovnávací skupiny používá *name2* jako zásobník. Počáteční znak každé vnořené konstrukce, nachází ve skupině a v jeho <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce. Pokud je nalezena shoda s koncový znak, jeho odpovídající počáteční znak je odebrán ze skupiny a <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekce se sníží o jedna. Po počátečních a koncových znaků všechny vnořené konstrukce, *name1* je prázdný.  
  
> [!NOTE]
>  Po úpravě regulární výraz v následujícím příkladu použít odpovídající otevírání a zavírání znak vnořeném konstruktoru, slouží ke zpracování nejvíce vnořené konstruktorů, jako jsou matematické výrazy nebo řádků kódu programu, které zahrnují více volání vnořených metod.  
  
 Následující příklad používá definici vyrovnávací skupiny tak, aby odpovídaly levé a pravé ostré závorky (<>) ve vstupním řetězci. Příklad definuje dva pojmenované skupiny `Open` a `Close`, jako je zásobníku, která se používají ke sledování odpovídající páry ostrých závorek. Každý zachycené levou hranatou závorku odesílají do kolekce zachycení `Open` skupiny a každá zachycená pravé ostré závorky se vloží do kolekce sběru `Close` skupiny. Definici vyrovnávací skupiny zajišťuje, že existuje odpovídající pravé ostré závorky pro každý levou hranatou závorku. Pokud není k dispozici, konečný dílčí vzor `(?(Open)(?!))`, je vyhodnocen pouze v případě `Open` skupina není prázdný (a tedy, pokud všechny vnořené konstrukce uzavřené). Pokud se poslední dílčí vzorec se vyhodnotí, shoda se nezdaří, protože `(?!)` dílčí vzor je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který vždy selže.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Vzor regulárního výrazu je:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Regulární výraz je interpretován následujícím způsobem:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začněte na začátku řetězce.|  
|`[^<>]*`|Porovná žádný nebo více znaků, které nejsou levé nebo pravé ostré závorky.|  
|`(?'Open'<)`|Porovná levou hranatou závorku a přiřadí ji do skupiny s názvem `Open`.|  
|`[^<>]*`|Porovná žádný nebo více znaků, které nejsou levé nebo pravé ostré závorky.|  
|`((?'Open'<)[^<>]*) +`|Porovná jeden nebo více výskytů levou hranatou závorku následovanou nula nebo více znaky, které nejsou levé nebo pravé ostré závorky. Toto je druhá zachytávající skupina.|  
|`(?'Close-Open'>)`|Odpovídá pravé ostré závorky, přiřaďte podřetězec mezi `Open` skupiny a aktuální skupinou do `Close` skupině a odstranit definici `Open` skupiny.|  
|`[^<>]*`|Porovná žádný nebo více výskytů libovolného znaku, který není levé straně ani pravou ostrou závorkou.|  
|`((?'Close-Open'>)[^<>]*)+`|Porovná jeden nebo více výskytů pravé ostré závorky, následované žádnou nebo více výskytů libovolného znaku, který není levé straně ani pravé ostré závorky. Při porovnávání pravé ostré závorky, přiřaďte podřetězec mezi `Open` skupiny a aktuální skupinou do `Close` seskupovat a odstranit definici `Open` skupiny. Toto je třetí zachytávající skupina.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Porovná žádný nebo několik výskytů následujícímu vzoru: jeden nebo více výskytů levou hranatou závorku, za nímž následuje nula nebo více znaků ostré závorky, za nímž následuje jedna nebo několik výskytů pravé ostré závorky, za nímž následuje nula nebo více výskytů typů bez ostrých závorek. Při porovnávání pravé ostré závorky, odstranit definici `Open` skupiny a přiřaďte podřetězec mezi `Open` skupiny a aktuální skupinou do `Close` skupiny. Toto je první zachytávající skupina.|  
|`(?(Open)(?!))`|Pokud `Open` skupina existuje, opustit shody, pokud by se shodovala prázdný řetězec, ale nepřesouvejte vpřed pozici modul regulárních výrazů v řetězci. Toto je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou. Protože prázdný řetězec je vždy implicitně existuje ve vstupním řetězci, tento vždy nepodaří operace zjištění shody. Selhání tuto shodu znamená, že nejsou vyváženy ostrých závorek.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Poslední dílčí výraz `(?(Open)(?!))`, označuje, zda vnořené konstrukce ve vstupním řetězci vyvažují správně (například, zda každý levou hranatou závorku odpovídá ostrá závorka). Používá podmíněného přiřazování na základě platný zachycené skupiny; Další informace najdete v tématu [alternace](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Pokud `Open` skupina je definována, modul regulárních výrazů pokusí shodovat s dílčím výrazu `(?!)` ve vstupním řetězci. `Open` Skupiny by měl být definován pouze v případě, že jsou vnořené konstrukce nevyrovnané. Proto se vzor musí shodovat ve vstupním řetězci by měl být ten, který vždy způsobí selhání porovnávání. V takovém případě `(?!)` je kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou, který vždy selže, protože prázdný řetězec je vždy implicitně přítomna na další pozici ve vstupním řetězci.  
  
 V příkladu, vyhodnotí modul regulárních výrazů se vstupním řetězcem "\<abc >< mno\<xyz >>" jak je znázorněno v následující tabulce.  
  
|Krok|Vzor|Výsledek|  
|----------|-------------|------------|  
|1|`^`|Zahájí porovnávání na začátku vstupního řetězce|  
|2|`[^<>]*`|Vyhledá ostré závorky znaky před levou hranatou závorku; vyhledá žádné odpovídající položky.|  
|3|`(((?'Open'<)`|Odpovídá levé závorky v "\<abc >" a přiřadí ji k `Open` skupiny.|  
|4|`[^<>]*`|Odpovídá "abc".|  
|5|`)+`|"< abc" je hodnota druhou zachycenou skupinou.<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět do `(?'Open'<)[^<>]*)` dílčí vzorec.|  
|6|`((?'Close-Open'>)`|Odpovídá pravé ostré závorky v "\<abc >", přiřadí "abc", což je dílčí řetězec mezi `Open` skupiny a pravý úhel párování na `Close` seskupovat a vymaže aktuální hodnotu ("<") z `Open` skupiny, ponechat prázdné.|  
|7|`[^<>]*`|Vyhledá ostré závorky po pravé ostré závorky; Vyhledá žádné odpovídající položky.|  
|8|`)+`|Hodnota třetí zachycené skupině je ">".<br /><br /> Další znak ve vstupním řetězci není pravé ostré závorky, modul regulárních výrazů neskočí zpět `((?'Close-Open'>)[^<>]*)` dílčí vzorec.|  
|9|`)*`|Hodnota první zachycenou skupinu je "\<abc >".<br /><br /> Další znak ve vstupním řetězci je levou hranatou závorku, takže modul regulárních výrazů skočí zpět `(((?'Open'<)` dílčí vzorec.|  
|10|`(((?'Open'<)`|Odpovídá levé závorky v "\<mno >" a přiřadí ji k `Open` skupiny. Jeho <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce nyní obsahuje jednu hodnotu, "<".|  
|11|`[^<>]*`|Odpovídá "mno".|  
|12|`)+`|"< mno" je hodnota druhou zachycenou skupinou.<br /><br /> Další znak ve vstupním řetězci je levou hranatou závorku, takže modul regulárních výrazů skočí zpět `(?'Open'<)[^<>]*)` dílčí vzorec.|  
|13|`(((?'Open'<)`|Odpovídá levé závorky v "\<xyz >" a přiřadí ji k `Open` skupiny. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Kolekce `Open` skupiny teď obsahuje dva zachycení: levou závorku úhlu z "\<mno >" a levou závorku úhlu z "\<xyz >".|  
|14|`[^<>]*`|Odpovídá "xyz".|  
|15|`)+`|"< xyz" je hodnota druhou zachycenou skupinou.<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět do `(?'Open'<)[^<>]*)` dílčí vzorec.|  
|16|`((?'Close-Open'>)`|Pravé ostré závorky v odpovídá "\<xyz >". "xyz", přiřadí podřetězec mezi `Open` skupiny a pravý úhel závorka k `Close` skupině a odstraní aktuální hodnota `Open` skupiny. Hodnota předchozí zachycení (levém ostré závorky v "\<mno >") změní aktuální hodnotu `Open` skupiny. <xref:System.Text.RegularExpressions.Group.Captures%2A> Kolekce `Open` skupiny teď obsahuje jeden zachycení, levá závorka úhlu z "\<xyz >".|  
|17|`[^<>]*`|Vyhledá ostré závorky znaky; Vyhledá žádné odpovídající položky.|  
|18|`)+`|Hodnota třetí zachycené skupině je ">".<br /><br /> Další znak ve vstupním řetězci je pravé ostré závorky, takže modul regulárních výrazů skočí zpět `((?'Close-Open'>)[^<>]*)` dílčí vzorec.|  
|19|`((?'Close-Open'>)`|Odpovídá posledním pravé ostré závorky v "xyz >>", přiřadí "mno\<xyz >" (podřetězec mezi `Open` skupiny a pravé ostré závorky) k `Close` seskupovat a odstraní aktuální hodnota `Open` skupiny. `Open` Skupina je teď prázdný.|  
|20|`[^<>]*`|Vyhledá ostré závorky znaky; Vyhledá žádné odpovídající položky.|  
|21|`)+`|Hodnota třetí zachycené skupině je ">".<br /><br /> Další znak ve vstupním řetězci není pravé ostré závorky, modul regulárních výrazů neskočí zpět `((?'Close-Open'>)[^<>]*)` dílčí vzorec.|  
|22|`)*`|Hodnota první zachycenou skupinu je "< mno\<xyz >>".<br /><br /> Další znak ve vstupním řetězci není levou hranatou závorku, takže modul regulárních výrazů neskočí zpět do `(((?'Open'<)` dílčí vzorec.|  
|23|`(?(Open)(?!))`|`Open` Skupiny není definována, takže dojde k pokusu o nalezena žádná shoda.|  
|24|`$`|Odpovídá konci vstupního řetězce.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Nezachycující skupiny  
 Následující seskupovací konstrukce nezachytává podřetězce, který odpovídá dílčí výraz:  
  
```  
(?:subexpression)  
```  
  
 kde *dílčí výraz* je libovolný platný vzor regulárního výrazu. Seskupovací konstrukce se obvykle používá, když do skupiny je použit kvantifikátor, ale podřetězce zachycené skupině jsou nejsou podstatné.  
  
> [!NOTE]
>  Pokud regulární výraz zahrnuje vnořených seskupovací konstrukce, vnější seskupovací konstrukce se nevztahují na vnořené seskupovací konstrukce.  
  
 Následující příklad ukazuje regulární výraz, který obsahuje skupiny bez zachytávání. Všimněte si, že výstup nezahrnuje žádné zachycené skupiny.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Regulární výraz `(?:\b(?:\w+)\W*)+\.` odpovídá věty, který je ukončen tečkou. Protože regulárního výrazu, zaměřuje na věty a ne na jednotlivá slova, seskupovací konstrukce se používají výhradně jako kvantifikátorů. Vzor regulárního výrazu je interpretován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?:\w+)`|Porovná jeden nebo více znaků slova. Nepřiřazujte odpovídající text zachycené skupině.|  
|`\W*`|Porovná žádný nebo více znaků slova.|  
|`(?:\b(?:\w+)\W*)+`|Porovná vzor jednoho nebo více znaků slova začínající na hranici slova, za nímž následuje nula nebo více znaků slova, jednou nebo vícekrát. Nepřiřazujte odpovídající text zachycené skupině.|  
|`\.`|Porovná tečku.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Možnosti pro skupiny  
 Následující seskupovací konstrukce použije nebo zakáže zadané možnosti v rámci dílčího výrazu:  
  
 `(?imnsx-imnsx:` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný platný vzor regulárního výrazu. Například `(?i-s:)` zapne nerozlišování velikosti písmen a zakáže jednořádkový režim. Další informace o vložených možností můžete zadat, najdete v části [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Můžete zadat možnosti, které platí pro celý regulární výraz, ne jako dílčí výraz s využitím <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy nebo statické metody. Můžete také určit vložené možnosti, které se vztahují za konkrétní bod v regulárním výrazu s použitím `(?imnsx-imnsx)` jazykové konstrukce.  
  
 Konstrukce možnosti skupiny není zachytávající skupina. To znamená i když jakékoli její části řetězec, který je zachycen *dílčí výraz* je zahrnuta v porovnávání, není součástí zachycené skupiny ani použitých k naplnění <xref:System.Text.RegularExpressions.GroupCollection> objektu.  
  
 Například regulární výraz `\b(?ix: d \w+)\s` v následujícím příkladu používá vložené možnosti v konstrukci seskupení pro povolení porovnávání velkých a malých písmen a ignorování vzorků prázdných znaků při identifikaci všech slov začínajících na písmeno "d". Regulární výraz je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?ix: d \w+)`|Použití velkých a malých písmen a ignorování prázdné znaky v tomto vzoru, odpovídají "d" za nímž následuje jedna nebo více znaků slova.|  
|`\s`|Porovná prázdný znak.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Kontrolní výrazy pozitivního dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou:  
  
 `(?=` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný vzor regulárního výrazu. Shoda bude úspěšná, vstupní řetězec musí odpovídat vzoru regulárního výrazu v *dílčí výraz*, i když odpovídající podřetězec není zahrnut ve výsledku porovnání. Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou neprovádí zpětné navracení.  
  
 Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou se obvykle nachází na konci vzorku regulárního výrazu. Definuje řetězec, který musí být nalezen na konci řetězce pro, aby nastala shoda, ale shody, které by neměly obsahovat. Je také k zamezení nadměrného používání mechanismu navracení. K zajištění, že konkrétní zachycené skupině začíná text, který odpovídá podmnožinu vzorku definovanému pro zachycené skupiny můžete použít kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou. Například pokud zachycující skupina odpovídá po sobě jdoucích alfanumerických znaků, vám pomůže kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou vyžadují, aby první znak abecední znak velkého písmene.  
  
 Následující příklad používá kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou tak, aby odpovídaly slovo, které předchází příkaz "je" ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Regulární výraz `\b\w+(?=\sis\b)` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(?=\sis\b)`|Zjistit, jestli znaků slova následovaných prázdným znakem a řetězec "je", který končí na hranici slova. Pokud ano, tato shoda je úspěšná.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Kontrolní výrazy negativního dopředného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou:  
  
 `(?!` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný vzor regulárního výrazu. Pro úspěšné porovnání vstupního řetězce nesmí odpovídat vzoru regulárního výrazu v *dílčí výraz*, i když odpovídající řetězec není zahrnut ve výsledku porovnání.  
  
 Na začátku nebo konci regulárního výrazu, se obvykle používá kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou. Na začátek regulárního výrazu může definovat konkrétní vzor, který by neměly odpovídat, když na začátek regulárního výrazu je definován vzor podobné, ale další obecné lze porovnat. V takovém případě se často používá k omezení používání mechanismu navracení. Na konec regulárního výrazu může definovat dílčí výraz, který nemůže být na konci shoda.  
  
 Následující příklad definuje regulární výraz, který používá kontrolní výraz dopředného vyhledávání s nulovou šířkou na začátek regulárního výrazu tak, aby odpovídaly slova, která nezačínají "zrušení".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Regulární výraz `\b(?!un)\w+\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?!un)`|Určení, zda jsou další dva znaky "zrušení". Pokud nejsou, je možné shody.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Následující příklad definuje regulární výraz, který používá kontrolní výraz dopředného vyhledávání s nulovou šířkou na konec regulárního výrazu hledat slova, které nesmí končit interpunkční znaménko.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Regulární výraz `\b\w+\b(?!\p{P})` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`\p{P})`|Nejsou-li další znak interpunkčním znaménkem (třeba tečkou nebo čárkou), že porovnání se zdaří.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<=` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný vzor regulárního výrazu. Pro úspěšné, porovnání *dílčí výraz* se musí vyskytovat ve vstupním řetězci nalevo od aktuální pozice, i když `subexpression` není zahrnut ve výsledku porovnání. Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou neprovádí zpětné navracení.  
  
 Na začátku regulárních výrazů jsou obvykle používány kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou. Vzor, který definují je předpokladem pro shodu, ačkoli není součástí výsledku porovnání.  
  
 Například následující příklad porovnává posledních dvou číslic roku pro první dvacet století (to znamená, že vyžaduje, že číslice "20" předcházet odpovídající řetězec).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Vzor regulárního výrazu `(?<=\b20)\d{2}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\d{2}`|Porovná dvě desetinné číslice.|  
|`(?<=\b20)`|Pokračuje v porovnávání, pokud jsou dvě desetinné číslice předchází desítkových číslic "20" na hranici slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Omezit používání mechanismu zpětného navracení při posledním znakem nebo znaky ve zachycené skupiny musí být podmnožinou znaky, které odpovídají vzoru regulárního výrazu této skupiny se používají také kontrolní výrazy pozitivního zpětného vyhledávání s nulovou šířkou. Například pokud skupina zachycuje všechny aplikace word po sobě jdoucí znaky, vám pomůže kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou vyžadují, aby byl posledním znakem abecedy.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou  
 Následující seskupovací konstrukce definuje kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou:  
  
 `(?<!` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný vzor regulárního výrazu. Pro úspěšné, porovnání *dílčí výraz* nesmí vyskytovat ve vstupním řetězci nalevo od aktuální pozice. Nicméně některé podřetězec, který se neshoduje s `subexpression` není zahrnut ve výsledku porovnání.  
  
 Na začátku regulárních výrazů jsou obvykle používány kontrolní výrazy negativního zpětného vyhledávání s nulovou šířkou. Vzor, který definují vylučuje shodu v řetězci, který následuje. Používají se také omezit používání mechanismu zpětného navracení při posledním znakem nebo znaky ve zachycené skupiny nesmí být jeden nebo více znaků, které odpovídají vzoru regulárního výrazu této skupiny. Například pokud skupina zachycuje všechny aplikace word po sobě jdoucí znaky, vám pomůže kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou vyžadují, aby poslední znak není podtržítka (_).  
  
 Následující příklad porovnává data pro kterýkoli den v týdnu, který není víkend (to znamená, že není sobota ani neděle).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Vzor regulárního výrazu `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova, následované prázdným znakem.|  
|`\d{1,2},`|Porovná jeden nebo dva desítkové číslice následované prázdným znakem a čárku.|  
|`\d{4}\b`|Porovná čtyři desítková čísla a ukončí porovnání na hranici slova.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Pokud ke shodě předchází něco jiného než řetězce, "Sobota" nebo "Neděle" následované mezerou, porovnávání je úspěšné.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Podvýrazy bez mechanismu navracení  
 Následující seskupovací konstrukce představuje podvýraz bez mechanismu navracení (označovaný také jako "chamtivého" dílčí_výraz):  
  
 `(?>` *Dílčí výraz* `)`  
  
 kde *dílčí výraz* je libovolný vzor regulárního výrazu.  
  
 Obvykle Pokud regulární výraz zahrnuje volitelné nebo alternativní odpovídající vzoru a shoda se nezdaří, modul regulárních výrazů větvit do více pokynů, porovnávat vstupní řetězec pomocí vzoru. Pokud není nalezena shoda, při přepínání první větev, může modul regulárních výrazů zálohování nebo navrátit do místa, kde, jakou trvalo první shoda a pokoušet se shoda pomocí druhé větve. Tento proces může pokračovat, dokud všechny větve mají nebyl proveden pokus o.  
  
 `(?>` *Dílčí výraz* `)` jazyková konstrukce zakáže mechanismus navracení. Modul regulárních výrazů bude odpovídat tolik znaků ve vstupním řetězci, jak je to možné. Pokud žádné další shody je možné, nebude navracení pokus alternativní porovnávání vzorů. (To znamená, že dílčí výraz odpovídá pouze řetězce, které by měl odpovídat dílčí výraz; nepokusí se tak, aby odpovídaly řetězec založený na dílčím výrazu a všech dílčích výrazů, které na něho.)  
  
 Tato možnost se doporučuje, pokud víte, že nebude úspěšné, používání mechanismu navracení. Zabraňuje modulu regulárních výrazů provádění zbytečné hledání zvyšuje výkon.  
  
 Následující příklad ukazuje, jak podvýraz bez mechanismu navracení upraví výsledky porovnávání. Navracení regulárního výrazu odpovídá úspěšně opakované znaků, následuje další výskyt stejnému znaku na hranici slova, ale bez mechanismu navracení regulárních výrazů nemá.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Regulární výraz bez mechanismu navracení `(?>(\w)\1+).\b` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(\w)`|Odpovídá znaku jednoslovné a přiřaďte ho k první zachytávající skupina.|  
|`\1+`|Hodnoty první zachycené podřetězce shodovat s jednou nebo vícekrát.|  
|`.`|Odpovídá jakémukoli znaku.|  
|`\b`|Ukončí porovnání na hranici slova.|  
|`(?>(\w)\1+)`|Porovná jeden nebo více výskytů znaku slova duplicitní, ale nevracejte se tak, aby odpovídaly poslední znak na hranici slova.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Seskupovací konstrukce a objekty regulárních výrazů  
 Podřetězce, které jsou porovnávány pomocí regulárních výrazů zachytávající skupinou jsou reprezentovány <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> objekty, které můžete získat z <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> objekt, který je vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.GroupCollection> Objektu je naplněn takto:  
  
- První <xref:System.Text.RegularExpressions.Group> objektu v kolekci (objekt na pozici nula) představuje celkovou shodu.  
  
- Další sadu <xref:System.Text.RegularExpressions.Group> objekty představují nepojmenované (číslované) zachytávající skupiny. Zobrazí se v pořadí, ve kterém jsou definovány v regulárním výrazu zprava doleva. Index hodnoty těchto skupin rozsahu od 1 do počtu nepojmenované zachytávající skupiny v kolekci. (Index určité skupiny je ekvivalentní k jeho číslované zpětný odkaz. Další informace o zpětných odkazech naleznete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- Finální sada <xref:System.Text.RegularExpressions.Group> objekty představují pojmenovaných zachytávajících skupinách. Zobrazí se v pořadí, ve kterém jsou definovány v regulárním výrazu zprava doleva. Hodnota indexu prvního pojmenovanou zachytávající skupinu je jedno vyšším než index poslední nepojmenované zachytávající skupinu. Pokud neexistují žádné nepojmenované zachytávající skupiny v regulárním výrazu, index první zachytávající skupina s názvem hodnotu jedna.  
  
 Pokud použijete kvantifikátor zachytávající skupinu, odpovídající <xref:System.Text.RegularExpressions.Group> objektu <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, a <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> vlastnosti odrážejí poslední podřetězec, který je zachycen zachytávající skupina. Úplná sada dílčích řetězců, které jsou zachyceny na základě skupin, které mají kvantifikátory z můžete načíst <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost.  
  
 Následující příklad vysvětluje vztah mezi <xref:System.Text.RegularExpressions.Group> a <xref:System.Text.RegularExpressions.Capture> objekty.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Vzor regulárního výrazu `\b(\w+)\W+)+` extrahuje jednotlivých slov v řetězci. Je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Tyto znaky dohromady, tvoří slovo. Toto je druhá zachytávající skupina.|  
|`\W+`|Porovná jeden nebo více znaků slova.|  
|`(\w+)\W+)+`|Porovná vzor jednoho nebo více znaků slova, následovaný jednou nebo více mimoslovní znaky jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
 První zachytávající skupina odpovídá každého slova na konec věty. Druhá zachytávající skupina odpovídá každého slova spolu s interpunkce a prázdných znaků, které následují slovo. <xref:System.Text.RegularExpressions.Group> Objekt, jehož index je 2 poskytuje informace o textu odpovídající druhou zachytávající skupinu. Kompletní sadu slov zachycených zachytávající skupinou jsou k dispozici <xref:System.Text.RegularExpressions.CaptureCollection> vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
