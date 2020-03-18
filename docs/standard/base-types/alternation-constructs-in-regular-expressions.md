---
title: Konstrukce alternace v regulárních výrazech rozhraní .NET
description: Přečtěte si, jak používat konstrukce alternace pro podmíněné párování v regulárních výrazech.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159686"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukce alternace v regulárních výrazech

Konstrukce alternace upravují regulární výraz tak, aby umožňoval nebo nebo podmíněné porovnávání. .NET podporuje tři konstrukce alternace:

- [Porovnávání vzorů s &#124;](#Either_Or)
- [Podmíněné shody s (?( výraz)ano&#124;ne)](#Conditional_Expr)
- [Podmíněné párování založené na platné zachycené skupině](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>Porovnávání vzorů s &#124;

Můžete použít svislý pruh (`|`) znak, aby odpovídaly `|` některý z řady vzorků, kde znak odděluje každý vzorek.

Stejně jako třída `|` kladných znaků lze znak použít tak, aby odpovídal libovolnému z několika jednotlivých znaků. Následující příklad používá kladné třídy znaků a buď/nebo vzor odpovídající `|` znak u hledání výskytů slov "šedá" nebo "šedá" v řetězci. V tomto případě `|` znak vytvoří regulární výraz, který je podrobnější.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

Regulární výraz, `|` který `\bgr(a|e)y\b`používá znak , je interpretován tak, jak je znázorněno v následující tabulce:

|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`gr`|Zápas znaky "gr".|  
|<code>(a&#124;e)</code>|Porovná buď se znakem „a“, nebo s „e“.|  
|`y\b`|Porovná "y" na hranici slova.|  

Znak `|` lze také použít k provedení buď nebo zápas s více znaky nebo podvýrazy, které mohou zahrnovat libovolnou kombinaci literálů znaků a prvků jazyka regulárních výrazů. (Třída znaků tuto funkci neposkytuje.) Následující příklad používá `|` znak k extrahování čísla sociálního zabezpečení USA (SSN), což je 9místné číslo s formátem *ddd*-*dd*-*dddd*, nebo identifikační číslo zaměstnavatele USA (EIN), což je 9místné číslo s formátem *dd*-*ddddddd*.

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

Regulární `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` výraz je interpretován tak, jak je znázorněno v následující tabulce:
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Shoda jedné z následujících hodnot: dvě desetinná místa následovaná pomlčkou následovanou sedmi desetinnými místy; nebo tři desetinné číslice, pomlčku, dvě desetinné číslice, jiný spojovník a čtyři desetinné číslice.|  
|`\d`|Ukončí porovnání na hranici slova.|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a>Podmíněné shody s výrazem

Tento element jazyka se pokusí porovnat jeden ze dvou vzorů v závislosti na tom, zda může odpovídat počáteční vzorek. Jeho syntaxe je:  

`(?(`*výraz* `)` *ano* `|` *ne*`)`

kde *výraz* je počáteční vzor, který se má shodovat, *ano* je vzorek, který odpovídá, pokud je *výraz* spárován, a *ne* je volitelný vzor, který odpovídá, pokud *výraz* není spárován. Modul regulárních výrazů považuje *výraz* za výraz s nulovou šířkou; to znamená, že modul regulárních výrazů nepostoupí ve vstupním datovém proudu po vyhodnocení *výrazu*. Proto tato konstrukce je ekvivalentní následující:

`(?(?=`*výraz* `)` *ano* `|` *ne*`)`

kde `(?=` *výraz* `)` je konstrukce výrazu s nulovou šířkou. (Další informace naleznete v [tématu Seskupování konstrukcí](grouping-constructs-in-regular-expressions.md).) Vzhledem k tomu, že modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz s nulovou šířkou), musí být *výraz* emitrovaný s nulovou šířkou (další informace viz [Kotvy)](anchors-in-regular-expressions.md)nebo dílčí výraz, který je také obsažen v *ano*. V opačném případě nelze spárovat vzor *yes.*  
  
> [!NOTE]
> Pokud je *výraz* pojmenovaná nebo číslovaná zachytávající skupina, konstrukce alternace je interpretována jako test sběru; Další informace naleznete v další části [Podmíněné shody založené na platné skupině zachycení](#Conditional_Group). Jinými slovy modul regulárních výrazů se nepokouší odpovídat zachycenépodřetězec, ale místo toho testuje přítomnost nebo nepřítomnost skupiny.  
  
Následující příklad je varianta příkladu, který se zobrazí v [buď/nebo porovnávání vzorků s &#124;](#Either_Or) části. Používá podmíněné porovnávání k určení, zda první tři znaky za hranice slova jsou dvě číslice následované pomlčkou. Pokud ano, pokusí se porovnat identifikační číslo amerického zaměstnavatele (EIN). Pokud ne, pokusí se porovnat číslo sociálního zabezpečení USA (SSN).

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:

|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?(\d{2}-)`|Určete, zda se následující tři znaky skládají ze dvou číslic následovaných pomlčkou.|  
|`\d{2}-\d{7}`|Pokud se předchozí vzorek shoduje, shodovat se dvěma číslicemi následovanými pomlčkou následovanou sedmi číslicemi.|  
|`\d{3}-\d{2}-\d{4}`|Pokud předchozí vzorek neodpovídá, shodovat se třemi desetinnými místy, pomlčkou, dvěma desetinnými místy, jinou pomlčkou a čtyřmi desetinnými místy.|  
|`\b`|Porovná hranici slova.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Podmíněné párování založené na platné zachycené skupině

Tento element jazyka se pokusí porovnat jeden ze dvou vzorů v závislosti na tom, zda odpovídá zadané zachytávající skupině. Jeho syntaxe je:

`(?(`*jméno* `)` *ano* `|` *ne*`)`

– nebo –

`(?(`*číslo* `)` *ano* `|` *ne*`)`

kde *název* je název a *číslo* je číslo zachytávající skupiny, *ano* je výraz, který se má shodovat, pokud *název* nebo *číslo* má shodu, a *ne* je volitelný výraz, který se má shodovat, pokud tomu tak není.

Pokud *název* neodpovídá názvu zachytávající skupiny, která se používá ve vzoru regulárního výrazu, konstrukce alternace je interpretována jako test výrazů, jak je vysvětleno v předchozí části. Obvykle to znamená, *expression* že výraz `false`vyhodnotí . Pokud *number* neodpovídá číslované zachytávající skupině, která se používá ve vzoru <xref:System.ArgumentException>regulárních výrazů, modul regulárních výrazů vyvolá .

Následující příklad je varianta příkladu, který se zobrazí v [buď/nebo porovnávání vzorků s &#124;](#Either_Or) části. Používá zachytávající `n2` skupinu s názvem, která se skládá ze dvou číslic následovaných pomlčkou. Konstrukce alternace testuje, zda tato zachytávající skupina byla spárována ve vstupním řetězci. Pokud ano, konstrukce alternace se pokusí porovnat posledních sedm číslic devítimístného identifikačního čísla zaměstnavatele USA (EIN). Pokud tomu tak není, pokusí se porovnat devítimístné číslo sociálního zabezpečení USA (SSN).

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:

|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?<n2>\d{2}-)?`|Porovná nulový nebo jeden výskyt dvou číslic následovaný pomlčkou. Pojmenujte tuto `n2`zachytávající skupinu .|  
|`(?(n2)`|Otestujte, zda `n2` byl spárován ve vstupním řetězci.|  
|`\d{7}`|Pokud `n2` byla spárována, porovná sedm desetinných míst.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Pokud `n2` nebyla spárována, porovná tři desetinná místa, pomlčku, dvě desetinné číslice, jiný spojovník a čtyři desetinné číslice.|  
|`\b`|Porovná hranici slova.|  

Varianta tohoto příkladu, který používá číslovou skupinu namísto pojmenované skupiny, je uvedena v následujícím příkladu. Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](regular-expression-language-quick-reference.md)
