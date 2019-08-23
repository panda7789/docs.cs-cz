---
title: Konstrukce alternace v regulárních výrazech .NET
description: Naučte se používat konstrukce alternace pro podmíněné porovnání v regulárních výrazech.
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 560597770d667cf8c7668bf2338ac4bac3eb192f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968577"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukce alternace v regulárních výrazech
<a name="top"></a>Konstrukce alternace upravují regulární výraz pro povolení nebo podmíněné porovnání. Rozhraní .NET podporuje tři konstrukce alternace:  
  
- [Porovnávání vzorů s&#124;](#Either_Or)  
  
- [Podmíněné porovnání s (? ( výraz) Ano&#124;ne)](#Conditional_Expr)  
  
- [Podmíněné porovnání na základě platné zachycené skupiny](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Porovnávání vzorů s&#124;  
 Znak svislé čáry (`|`) můžete použít k vyhledání jedné z řady vzorů, `|` kde znak odděluje každý vzorek.  
  
 Podobně jako třída pozitivního znaku, `|` lze znak použít k vyhledání jednoho z několika jednoduchých znaků. V následujícím příkladu je použita třída pozitivního znaku a buď porovnávání vzorů, nebo porovnávání `|` se znakem pro hledání výskytů slov "Gray" nebo "šedá" v řetězci. V tomto případě `|` znak vytvoří regulární výraz, který je podrobněji podrobnější.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`gr`|Porovnává se se znaky "GR".|  
|<code>(a&#124;e)</code>|Porovná buď se znakem „a“, nebo s „e“.|  
|`y\b`|Porovnává s "y" na hranici slova.|  
  
 `|` Znak lze také použít k provedení shody s více znaky nebo podvýrazy, které mohou obsahovat libovolnou kombinaci znakových literálů a prvků jazyka regulárních výrazů. (Třída znaků tuto funkci neposkytuje.) Následující příklad používá `|` znak k extrakci typu USA. Číslo sociálního pojištění (SSN), což je číslo 9 číslic ve formátu *DDD*-*DD*-*dddd*nebo USA Identifikační číslo zaměstnavatele (EIN), což je číslo 9 číslic ve formátu *DD*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Porovnává jednu z následujících hodnot: dvě desítkové číslice následované spojovníkem a sedmi desítkových číslic; nebo tři desítkové číslice, pomlčky, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.|  
|`\d`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Podmíněné porovnání s výrazem  
 Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se může shodovat s počátečním vzorem. Jeho syntaxe je:  
  
 `(?(`*výraz* `)` Ano –`|` *ne*`)`  
  
 *výraz* WHERE je počáteční vzorek, který se má shodovat, *Ano* je vzor, který se má shodovat, pokud se *výraz* shoduje, a *ne* je volitelný vzor, který by odpovídal, pokud se *výraz* neshoduje. Modul regulárních výrazů považuje *výraz* za kontrolní výraz s nulovou šířkou; To znamená, že modul regulárních výrazů není ve vstupním datovém proudu před vyhodnocením *výrazu*. Proto je tato konstrukce ekvivalentní následujícímu:  
  
 `(?(?=`*výraz* `)` Ano –`|` *ne*`)`  
  
 výraz `(?=`Where`)` je konstrukce kontrolního výrazu s nulovou šířkou. (Další informace naleznete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Vzhledem k tomu, že modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz s nulovou šířkou), musí být *výraz* buď kontrolní výraz s nulovou šířkou (Další informace naleznete v tématu [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo dílčí výraz, který je také obsažen v *Ano*. V opačném případě nelze porovnat vzor *Ano* .  
  
> [!NOTE]
> Pokud je *výraz*pojmenovanou nebo číslovanou zachytávající skupinou, konstrukce alternace je interpretována jako test Capture; Další informace najdete v další části s podmíněným [porovnáním na základě platné skupiny zachycení](#Conditional_Group). Jinými slovy, modul regulárních výrazů se nepokusí porovnat zachycený dílčí řetězec, ale místo toho testuje přítomnost nebo nepřítomnost skupiny.  
  
 V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním](#Either_Or) nebo vzorem. Pomocí podmíněného porovnání Určuje, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem. Pokud jsou, pokusí se porovnat USA Identifikační číslo zaměstnavatele (EIN). Pokud tomu tak není, pokusí se porovnat americký Rodné číslo (sociální zabezpečení).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Vzor `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?(\d{2}-)`|Určí, zda následující tři znaky sestávají ze dvou číslic následovaných spojovníkem.|  
|`\d{2}-\d{7}`|Pokud předchozí vzor souhlasí, porovná dvě číslice následované spojovníkem následovaným sedmi číslicemi.|  
|`\d{3}-\d{2}-\d{4}`|Pokud předchozí vzor neodpovídá, porovnává tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.|  
|`\b`|Porovná hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Podmíněné porovnání na základě platné zachycené skupiny  
 Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se shodoval se zadanou zachytávající skupinou. Jeho syntaxe je:  
  
 `(?(`*název* `)` Ano –`|` *ne*`)`  
  
 or  
  
 `(?(`*číslo* `)` Ano –`|` *ne*`)`  
  
 kde *Name* je název a *číslo* je číslo zachytávající skupiny, *Ano* je výraz, který se má shodovat, pokud má *název* nebo *číslo* shodu a *ne* není volitelný výraz, který by odpovídal, pokud není.  
  
 Pokud *název* neodpovídá názvu zachytávající skupiny, která je použita ve vzoru regulárního výrazu, konstrukce alternace je interpretována jako test výrazu, jak je vysvětleno v předchozí části. Obvykle to znamená, že je *výraz* vyhodnocen `false`jako. Pokud *číslo* neodpovídá očíslované zachytávající skupině, která je použita ve vzoru regulárního výrazu, modul regulárních výrazů vyvolá <xref:System.ArgumentException>.  
  
 V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním](#Either_Or) nebo vzorem. Používá zachytávající skupinu s názvem `n2` , která se skládá ze dvou číslic následovaných spojovníkem. Konstrukce alternace testuje, zda byla tato zachytávající skupina spárována ve vstupním řetězci. Pokud má, konstrukce alternace se pokusí porovnat posledních sedm číslic v devíti číslicích. Identifikační číslo zaměstnavatele (EIN). Pokud tomu tak není, pokusí se porovnat s devíti číslicemi USA. Rodné číslo (sociální zabezpečení).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Vzor `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?<n2>\d{2}-)?`|Porovná žádný nebo jeden výskyt dvou číslic následovaný spojovníkem. Pojmenujte tuto `n2`zachytávající skupinu.|  
|`(?(n2)`|Otestuje `n2` , zda byla shodná se vstupním řetězcem.|  
|`\d{7}`|Pokud `n2` se shodoval, porovná sedm desítkových číslic.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Pokud `n2` se neshodoval, porovná tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.|  
|`\b`|Porovná hranici slova.|  
  
 V následujícím příkladu je uvedena variace tohoto příkladu, který používá očíslovanou skupinu namísto pojmenované skupiny. Jeho vzor regulárního výrazu `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`je.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
