---
title: "Konstrukce alternace v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cea67e0309bccac7d21d7e8db659a55d34d4959a
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukce alternace v regulárních výrazech
<a name="top"></a> Konstrukce alternace upravit regulární výraz k povolení buď / nebo nebo podmíněného odpovídající. Rozhraní .NET podporuje tři konstrukce alternace:  
  
-   [Pro porovnávání s&#124;](#Either_Or)  
  
-   [Podmíněné porovnávání pomocí (? () výraz) Ano&#124;žádné)](#Conditional_Expr)  
  
-   [Podmíněné porovnávání založené na platnou zaznamenané skupinu](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Pro porovnávání s&#124;  
 Můžete použít svislá čára (`|`) znak tak, aby odpovídaly některého z řady vzory, kde `|` odděluje každý vzorek.  
  
 Třída pozitivních znaků, jako `|` znak slouží k porovnání kteréhokoli z jedné znaků. Následující příklad používá jak třídu kladné znaků a buď / nebo vzor odpovídající pomocí `|` pro nalezení výskytů slova "gray" nebo "Los" v řetězci. V takovém případě `|` znak vytváří regulární výraz, který je podrobnější.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, se interpretují jako uvedené v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`gr`|Porovná znaky "gr".|  
|<code>(a&#124;e)</code>|Porovná buď se znakem „a“, nebo s „e“.|  
|`y\b`|Porovná "y" na hranici slova.|  
  
 `|` Znak lze použít také pro porovnávání buď / nebo k vyhledání s více znaky nebo podvýrazy, které může obsahovat libovolnou kombinaci znakové literály a prvků jazyka regulárních výrazů. (Třída znaků neposkytuje tuto funkci.) Následující příklad používá `|` znaků k extrakci buď USA Číslo sociálního pojištění (SSN), což je číslo 9 číslic ve formátu *ddd*-*dd*-*dddd*, nebo US Zaměstnavatel identifikační číslo (EIN), což je číslo 9 číslic ve formátu *dd*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Porovná jednu z následujících: dva desetinných míst, za nímž následuje pomlčka následované sedm desítkových číslic; nebo tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.|  
|`\d`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Podmíněné porovnávání s výrazem  
 Tento prvek jazyka se pokusí o porovnání jedním ze dvou vzorů v závislosti na tom, zda lze porovnat počáteční vzorek. Jeho syntaxe je:  
  
 `(?(` *výraz* `)` *Ano* `|` *žádné* `)`  
  
 kde *výraz* je počáteční vzor pro shodu, *Ano* je vzor pro porovnání, pokud *výraz* je nalezena shoda, a *žádné* je nepovinný Pokud odpovídající vzor *výraz* neodpovídá. Modul regulárních výrazů zpracovává *výraz* jako assertion nulovou šířkou; to znamená, modul regulárních výrazů není zálohy v vstupního datového proudu po vyhodnocuje *výraz*. Proto tento konstruktor je ekvivalentní následující:  
  
 `(?(?=` *výraz* `)` *Ano* `|` *žádné* `)`  
  
 kde `(?=` *výraz* `)` je konstrukce nulové šířky. (Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Protože modul regulárních výrazů interpretuje *výraz* jako element anchor (assertion nulovou šířkou), *výraz* musí být buď nulovou šířkou assertion (Další informace najdete v tématu [ Kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo dílčím výrazu, která je také součástí *Ano*. Jinak *Ano* vzor nelze porovnat.  
  
> [!NOTE]
>  Pokud *výraz*je zachycené skupiny s názvem nebo číslem, alternace interpretována jako testovací zachycení; Další informace najdete v části Další [podmíněné porovnávání založené na platné zachycené skupině](#Conditional_Group). Jinými slovy modul regulárních výrazů nepokusí tak, aby odpovídaly zaznamenané dílčí řetězec, ale místo toho testů pro existenci nebo neexistenci skupiny.  
  
 V následujícím příkladu se odlišuje od příkladu, který se zobrazí v [buď / nebo vzor odpovídající pomocí &#124; ](#Either_Or) části. Chcete-li určit, jestli prvních tří znaků na hranici slova jsou dvě číslice následované pomlčka pomocí podmíněného porovnávání. Pokud ano, pokusí se porovnat americké Identifikační číslo zaměstnavatele (EIN). Pokud ne, pokusí se porovnat americké Číslo sociálního pojištění (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Regulární výraz `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?(\d{2}-)`|Určí, zda následující tři znaky se skládají ze dvou číslic, za nímž následuje pomlčka.|  
|`\d{2}-\d{7}`|Pokud předchozí vzor odpovídá, porovná dvě číslice následované pomlčkou, za nímž následuje sedm číslic.|  
|`\d{3}-\d{2}-\d{4}`|Pokud předchozí vzorek neodpovídá, odpovídat tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.|  
|`\b`|Porovná hranici slova.|  
  
 [Zpět na začátek](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Podmíněné porovnávání založené na platnou zaznamenané skupinu  
 Tento prvek jazyka se pokusí o porovnání jedním ze dvou vzorů v závislosti na tom, jestli ho odpovídá zadané zaznamenávání skupiny. Jeho syntaxe je:  
  
 `(?(` *název* `)` *Ano* `|` *žádné* `)`  
  
 or  
  
 `(?(` *číslo* `)` *Ano* `|` *žádné* `)`  
  
 kde *název* je název a *číslo* je číslo zachycené skupiny, *Ano* je výraz pro porovnání, pokud *název* nebo *číslo* má odpovídající, a *žádné* je volitelný výraz pro porovnání, pokud neexistuje.  
  
 Pokud *název* neodpovídá název zaznamenávání skupinu, která se používá v regulární výraz, alternace interpretována jako test výrazu, jak je popsáno v předchozí části. Obvykle to znamená, že *výraz* vyhodnocuje `false`. Pokud *číslo* neodpovídá číslované zaznamenávání skupině, která se používá v vzor regulárního výrazu, vyvolá modul regulární výraz <xref:System.ArgumentException>.  
  
 V následujícím příkladu se odlišuje od příkladu, který se zobrazí v [buď / nebo vzor odpovídající pomocí &#124; ](#Either_Or) části. Používá zaznamenávání skupinu s názvem `n2` který se skládá ze dvou číslic, za nímž následuje pomlčka. Konstrukce alternace testy, zda byla odpovídá této zaznamenávání skupiny ve vstupním řetězci. Pokud ano, pokusí se porovnat posledních pět číslic amerického zahraniční konstrukce alternace Identifikační číslo zaměstnavatele (EIN). Pokud ne, pokusí se porovnat zahraniční USA Číslo sociálního pojištění (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Regulární výraz `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?<n2>\d{2}-)?`|Porovná nula nebo jeden výskyt dvě číslice následované pomlčkou. Název této skupiny zaznamenávání `n2`.|  
|`(?(n2)`|Test zda `n2` , odpovídal ve vstupním řetězci.|  
|`)\d{7}`|Pokud `n2` byla obsažena, porovná sedm desetinných míst.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Pokud `n2` nebyla shodná, odpovídají tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.|  
|`\b`|Porovná hranici slova.|  
  
 Varianta tohoto příkladu, který používá skupinu číslovaných místo s názvem skupiny je znázorněno v následujícím příkladu. Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
