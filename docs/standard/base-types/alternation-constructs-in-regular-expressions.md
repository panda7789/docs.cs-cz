---
title: Konstrukce alternace v regulárních výrazech
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
ms.openlocfilehash: 6b653972fad71ce3a89c35598513b94f71fb4bf0
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743372"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukce alternace v regulárních výrazech
<a name="top"></a> Konstrukce alternace upravují regulární výraz, aby buď / nebo podmíněného přiřazování nebo. .NET podporuje tři konstrukcí alternace:  
  
-   [Porovnávání vzorů s&#124;](#Either_Or)  
  
-   [Podmíněné porovnávání s (? () výraz) Ano&#124;žádné)](#Conditional_Expr)  
  
-   [Podmíněného přiřazování na základě platný zachycené skupiny](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Porovnávání vzorů s&#124;  
 Můžete použít svislá čára (`|`) znaků tak, aby odpovídaly některou z řady vzory, kde `|` odděluje každý vzorek.  
  
 Třída kladné znaků, jako jsou `|` znak můžete použít tak, aby odpovídaly některou z jednoho znaků. Následující příklad používá třídu kladné znaků a buď / nebo porovnávání vzorů s `|` znak vyhledáte výskyty slova "gray" nebo "šedou" v řetězci. V takovém případě `|` znak vytváří regulární výraz, který je podrobnější.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`gr`|Porovná znaky "gr".|  
|<code>(a&#124;e)</code>|Porovná buď se znakem „a“, nebo s „e“.|  
|`y\b`|Odpovídá "y", na hranici slova.|  
  
 `|` Znak je také možné provést buď / nebo shodu s více znaky nebo dílčích výrazů, které může obsahovat libovolnou kombinaci znakové literály a prvky jazyka regulárních výrazů. (Znak třídy tuto funkci neposkytuje.) V následujícím příkladu `|` znaků k extrakci buď USA Sociálního pojištění USA (SSN), což je číslo 9 číslic s formátem *ddd*-*dd*-*dddd*, nebo číslu Zaměstnavatel identifikační číslo (EIN), což je číslo 9 číslic s formátem *dd*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Porovná jednu z následujících akcí: dvě desetinné číslice, za nímž následuje spojovník následovaný písmenem sedm desítkových číslic; nebo tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.|  
|`\d`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Podmíněné porovnávání s výrazem  
 Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, zda lze porovnat počáteční vzorek. Syntaxe je:  
  
 `(?(` *výraz* `)` *Ano* `|` *žádné* `)`  
  
 kde *výraz* je počáteční vzor pro shodu, *Ano* je vzor splněno, pokud *výraz* je nalezena shoda, a *žádné* je volitelný Pokud odpovídající vzor *výraz* se neshoduje. Modul regulárních výrazů zachází *výraz* jako kontrolní výraz nulové šířky; to znamená, že modul regulárních výrazů nepřesouvejte vpřed v vstupního datového proudu po je vyhodnocen jako *výraz*. Proto tento konstruktor je ekvivalentní následujícímu zápisu:  
  
 `(?(?=` *výraz* `)` *Ano* `|` *žádné* `)`  
  
 kde `(?=` *výraz* `)` je konstrukce kontrolní výraz nulové šířky. (Další informace najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Protože modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz nulové šířky), *výraz* musí být buď kontrolní výraz nulové šířky (Další informace najdete v tématu [ Kotvy vztahů](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo jako dílčí výraz, který je také součástí *Ano*. V opačném případě *Ano* vzor neshoduje.  
  
> [!NOTE]
>  Pokud *výraz*pojmenovanou nebo číslovanou zachytávající skupinu, je konstrukce alternace, je interpretován jako zachycení testu; Další informace naleznete v další části [podmíněné odpovídající založené na platné zachycené skupině](#Conditional_Group). Jinými slovy modul regulárních výrazů nepokusí tak, aby odpovídaly zachycené podřetězce, ale místo toho testy pro přítomnosti nebo nepřítomnosti skupiny.  
  
 Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu. Používá podmíněného přiřazování k určení, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem. Pokud ano, pokusí se porovnat USA Zaměstnavatel identifikační číslo (EIN). Pokud ne, pokusí se porovnat americké Číslo sociálního pojištění (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?(\d{2}-)`|Určení, zda následující tři znaky jsou dvě číslice následované spojovníkem.|  
|`\d{2}-\d{7}`|Pokud předchozí vzor odpovídá, porovná dvě číslice následované spojovníkem a 7 číslicemi.|  
|`\d{3}-\d{2}-\d{4}`|Pokud předchozí vzorek neodpovídá, porovná tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.|  
|`\b`|Porovná hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Podmíněného přiřazování na základě platný zachycené skupiny  
 Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, jestli má odpovídá zadané zachytávající skupiny. Syntaxe je:  
  
 `(?(` *název* `)` *Ano* `|` *žádné* `)`  
  
 or  
  
 `(?(` *číslo* `)` *Ano* `|` *žádné* `)`  
  
 kde *název* je název a *číslo* je počet zachytávající skupinu, *Ano* je výraz, který se shodují, pokud *název* nebo *číslo* shoduje, a *žádné* je volitelný výraz, který splněno, pokud tomu tak není.  
  
 Pokud *název* neodpovídá názvu zachytávající skupinu, která se používá ve vzoru regulárního výrazu, alternace je interpretován jako test výrazu, jak je popsáno v předchozí části. Obvykle to znamená, že *výraz* vyhodnotí jako `false`. Pokud *číslo* neodpovídá očíslovanou zachytávající skupinu, která se používá ve vzoru regulárního výrazu, vyvolá modul regulárních výrazů <xref:System.ArgumentException>.  
  
 Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu. Používá zachytávající skupina s názvem `n2` , která obsahuje dvě číslice následované spojovníkem. Konstrukce alternace testuje, jestli tato zachytávající skupina pravá složená závorka ve vstupním řetězci. Pokud ano, bude se Alternující konstrukce pokusí se porovnat posledních 7 číslic devět číslic USA Zaměstnavatel identifikační číslo (EIN). Pokud ne, pokusí se porovnat devět číslic USA Číslo sociálního pojištění (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?<n2>\d{2}-)?`|Porovná žádný nebo jeden výskyt dvě číslice následované spojovníkem. Název této zachytávající skupiny `n2`.|  
|`(?(n2)`|Test, zda `n2` odpovídal ve vstupním řetězci.|  
|`)\d{7}`|Pokud `n2` byla shoda, porovná sedm desítkových číslic.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Pokud `n2` neodpovídá, odpovídá tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.|  
|`\b`|Porovná hranici slova.|  
  
 Variace tohoto příkladu, který používá číslované skupiny místo pojmenovanou skupinu se zobrazí v následujícím příkladu. Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
