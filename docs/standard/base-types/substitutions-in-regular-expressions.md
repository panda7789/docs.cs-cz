---
title: Nahrazení v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
ms.openlocfilehash: 3562bd113ae4c9a3f721d8858a5d3625ef548d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160075"
---
# <a name="substitutions-in-regular-expressions"></a>Nahrazení v regulárních výrazech
Náhrady jsou prvky jazyka, které jsou rozpoznány pouze v rámci vzorů nahrazení. Pro definování celého textu nebo jeho části, která má nahradit odpovídající text ve vstupním řetězci, používají vzor regulárního výrazu. Vzor pro nahrazení se může skládat z jedné nebo několika substitucí spolu s literálními znaky. Náhradní vzory jsou k dispozici přetížení <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody, `replacement` které mají <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> parametr a metody. Metody nahradit odpovídající vzorek se vzorem, který `replacement` je definován parametrem.  
  
 Rozhraní .NET Framework definuje prvky substituce uvedené v následující tabulce.  
  
|Substituce|Popis|  
|------------------|-----------------|  
|$ *Číslo*|V náhradním řetězci zahrne poslední podřetězec odpovídající zachytávající skupině, která je označena *číslem*, kde *číslo* je desítková hodnota. Další informace naleznete [v tématu Nahrazení číslované skupiny](#substituting-a-numbered-group).|  
|${ *název* }|Zahrnuje poslední podřetězec odpovídající pojmenované skupině, která `(?<`je v náhradním řetězci označena *názvem.* `> )` Další informace naleznete [v tématu Nahrazení pojmenované skupiny](#substituting-a-named-group).|  
|$$|Zahrnuje jediný literál "$" v řetězci pro nahrazení. Další informace naleznete [v tématu Nahrazení symbolu $.](#substituting-a--character)|  
|$&|Zahrnuje kopii celé shody v řetězci pro nahrazení. Další informace naleznete [v tématu Nahrazení celé shody](#substituting-the-entire-match).|  
|$\`|Zahrnuje celý text vstupního řetězce před porovnáním v řetězci pro nahrazení. Další informace naleznete v [tématu Nahrazení textu před shodou](#substituting-the-text-before-the-match).|  
|$'|Zahrnuje celý text vstupního řetězce po porovnání v řetězci pro nahrazení. Další informace naleznete v [tématu Nahrazení textu po shodě](#substituting-the-text-after-the-match).|  
|$+|Zahrnuje poslední skupinu zachycenou v řetězci pro nahrazení. Další informace naleznete [v tématu Nahrazení poslední zachycené skupiny](#substituting-the-last-captured-group).|  
|$\_|Zahrnuje celý vstupní řetězec v řetězci pro nahrazení. Další informace naleznete [v tématu Nahrazení celého vstupního řetězce](#substituting-the-entire-input-string).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Prvky substituce a vzory pro nahrazení  
 Substituce jsou jediné speciální konstrukce, které jsou rozpoznány ve vzorech pro nahrazení. Žádný z ostatních prvků jazyka regulárních výrazů, včetně řídicích znaků a tečky (`.`), která odpovídá libovolnému znaku, není podporován. Obdobně jsou prvky jazyka pro substituci rozpoznány jen ve vzorech pro nahrazení a nejsou nikdy platné ve vzorech regulárního výrazu.  
  
 Jediný znak, který se může objevit ve vzoru regulárních výrazů nebo v nahrazení, je `$` znak, i když má v každém kontextu jiný význam. Ve vzoru regulárního výrazu je kotva, `$` která odpovídá konci řetězce. V náhradním `$` vzoru označuje začátek substituce.  
  
> [!NOTE]
> Pro funkce podobné vzoru pro nahrazení v rámci regulárního výrazu použijte zpětný odkaz. Další informace o zpětné odkazy naleznete v tématu [Backreference Constructs](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  

## <a name="substituting-a-numbered-group"></a>Nahrazování číslované skupiny  
 Prvek `$` *číselného* jazyka obsahuje poslední podřetězec odpovídající skupině zachycení *čísla* v náhradním řetězci, kde *číslo* je index zachytávající skupiny. Například náhradní vzor `$1` označuje, že odpovídající podřetězec má být nahrazen první zachycené skupiny. Další informace o číslovaných zachytávacích skupinách naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Všechny číslice, `$` které následují, jsou interpretovány jako patřící do *číselné* skupiny. Pokud to však není vaším záměrem, můžete namísto toho nahradit pojmenovanou skupinu. Náhradní řetězec `${1}1` můžete například použít `$11` místo k definování náhradního řetězce jako hodnoty první zachycené skupiny spolu s číslem "1". Další informace naleznete [v tématu Nahrazení pojmenované skupiny](#substituting-a-named-group).  
  
 Zachytávání skupin, které nejsou `(?<`explicitně přiřazeny názvy pomocí syntaxe *názvu* `>)` jsou číslovány zleva doprava počínaje na jednom. Pojmenované skupiny jsou rovněž číslovány zleva doprava. Číslování začíná číslem o jedno vyšším než index poslední nepojmenované skupiny. Například v regulárním `(\w)(?<digit>\d)`výrazu `digit` je index pojmenované skupiny 2.  
  
 Pokud *číslo* neurčuje platnou zachytávající skupinu `$`definovanou ve vzoru regulárního výrazu, *číslo* je interpretováno jako literálová znaková sekvence, která se používá k nahrazení každé shody.  
  
 Následující příklad používá `$`nahrazení *čísla* k odstranění symbolu měny z desetinné hodnoty. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Vzor regulárního výrazu `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(\s?\d+[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je první zachytávající skupina. Vzhledem k `$1`tomu, že <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> je vzor nahrazení , volání metody nahradí celý odpovídající podřetězec s touto zachycenou skupinou.|  

## <a name="substituting-a-named-group"></a>Nahrazování pojmenované skupiny  
 Element `${` *jazyka názvu* `}` nahrazuje poslední podřetězec odpovídající skupině zachycení *názvu,* kde *název* je název zachytávající skupiny definovaný elementem `(?<`jazyka *názvu.* `>)` Další informace o pojmenovaných zachytávacích skupinách naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Pokud *název* neurčuje platnou pojmenovanou zachytávající skupinu definovanou `${`ve vzoru regulárního výrazu, ale skládá se z číslic, *je název* `}` interpretován jako číslovaná skupina.  
  
 Pokud *název* neurčuje platnou pojmenovanou zachytávající skupinu ani platnou `${`číslovou zachytávající skupinu definovanou ve vzoru regulárního výrazu, *je název* `}` interpretován jako literálová znaková sekvence, která se používá k nahrazení každé shody.  
  
 Následující příklad používá `${`nahrazení *názvu* `}` k odstranění symbolu měny z desetinné hodnoty. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Vzor regulárního výrazu `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(?<amount>\s?\d[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je zachytávající skupina s názvem `amount`. Vzhledem k `${amount}`tomu, že <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> je vzor nahrazení , volání metody nahradí celý odpovídající podřetězec s touto zachycenou skupinou.|  

## <a name="substituting-a--character"></a>Nahrazování znaku "$"  
 Nahrazení `$$` vloží literál "$" znak v nahrazeném řetězci.  
  
 Následující příklad používá <xref:System.Globalization.NumberFormatInfo> objekt k určení symbolu měny aktuální jazykové verze a jeho umístění v řetězci měny. Poté dynamicky sestaví vzor regulárního výrazu a vzor pro nahrazení. Pokud je příklad spuštěn v počítači, jehož aktuální jazyková verze `\b(\d+)(\.(\d+))?` je en `$$ $1$2`US, generuje vzor regulárního výrazu a vzor nahrazení . Vzor pro nahrazení nahradí odpovídající text symbolem měny a mezerou následovanou první a druhou zachycenou skupinou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Vzor regulárního výrazu `\b(\d+)(\.(\d+))?` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Zahájí porovnání na začátku hranice slova.|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je první zachytávající skupina.|  
|`\.`|Porovná tečku (oddělovač desetinných míst).|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je třetí zachytávající skupina.|  
|`(\.(\d+))?`|Porovná žádný nebo jeden výskyt tečky následované jednou nebo několika desítkovými číslicemi. Toto je druhá zachytávající skupina.|  

## <a name="substituting-the-entire-match"></a>Nahrazování celé shody  
 Nahrazení `$&` zahrnuje celou shodu v řetězci nahrazení. Často se používá k přidání podřetězce na začátek nebo konec porovnávaného řetězce. Například `($&)` náhradní vzorek přidá závorky na začátek a konec každé shody. Pokud neexistuje žádná shoda, `$&` nahrazení nemá žádný vliv.  
  
 Následující příklad používá `$&` nahrazení k přidání uvozovek na začátek a konec názvy knih uložené v řetězcovém poli.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Vzor regulárního výrazu `^(\w+\s?)+$` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(\w+\s?)+`|Jednou nebo vícekrát porovná vzor jednoho nebo několika znaků slova následovaného žádným nebo jedním prázdným znakem.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Vzor `"$&"` nahrazení přidá literálové uvozovky na začátek a konec každé shody.  

## <a name="substituting-the-text-before-the-match"></a>Nahrazování textu před porovnáváním  
 Nahrazení ``$` `` nahradí odpovídající řetězec s celým vstupním řetězcem před shodou. To znamená, že duplikuje vstupní řetězec až po shodu a odebírá odpovídající text. Jakýkoli text, který následuje za odpovídajícím textem, zůstane ve výsledném řetězci nezměněn. Pokud existuje více shod ve vstupním řetězci, je text pro nahrazení odvozen z původního vstupního řetězce, nikoli z řetězce, ve kterém byl text nahrazen předchozími shodami. \(Příklad obsahuje ilustraci. \) Pokud neexistuje žádná shoda, ``$` `` nahrazení nemá žádný vliv.  
  
 Následující příklad používá vzor `\d+` regulárního výrazu tak, aby odpovídal posloupnosti jedné nebo více desetinných míst ve vstupním řetězci. Náhradní řetězec ``$` `` nahradí tyto číslice textem, který předchází shodě.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 V tomto příkladu `"aa1bb2cc3dd4ee5"` obsahuje vstupní řetězec pět shod. Následující tabulka ukazuje, ``$` `` jak nahrazení způsobí, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec před shodou|Výsledný řetězec|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|

## <a name="substituting-the-text-after-the-match"></a>Nahrazování textu po shodě  
 Nahrazení `$'` nahradí odpovídající řetězec s celým vstupním řetězcem po shodě. To znamená, že duplikuje vstupní řetězec po shodě a odebírá odpovídající text. Jakýkoli text, který předchází odpovídajícímu textu, zůstává ve výsledném řetězci nezměněn. Pokud neexistuje žádná shoda, `$'` nahrazení nemá žádný vliv.  
  
 Následující příklad používá vzor `\d+` regulárního výrazu tak, aby odpovídal posloupnosti jedné nebo více desetinných míst ve vstupním řetězci. Náhradní řetězec `$'` nahradí tyto číslice textem, který následuje za shodou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 V tomto příkladu `"aa1bb2cc3dd4ee5"` obsahuje vstupní řetězec pět shod. Následující tabulka ukazuje, `$'` jak nahrazení způsobí, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec po shodě|Výsledný řetězec|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  

## <a name="substituting-the-last-captured-group"></a>Nahrazování poslední zachycené skupiny  
 Nahrazení `$+` nahradí odpovídající řetězec s poslední zachycenou skupinou. Pokud neexistují žádné zachycené skupiny nebo pokud je <xref:System.String.Empty?displayProperty=nameWithType>hodnota `$+` poslední zachycené skupiny , nahrazení nemá žádný vliv.  
  
 Následující příklad identifikuje duplicitní slova v `$+` řetězci a pomocí nahrazení je nahradí jediným výskytem slova. Tato <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možnost se používá k zajištění, že slova, která se liší v případě, ale které jsou jinak identické jsou považovány za duplicitní.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Vzor regulárního výrazu `\b(\w+)\s\1\b` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`\1`|Porovná první zachycenou skupinu.|  
|`\b`|Ukončí porovnání na hranici slova.|  

## <a name="substituting-the-entire-input-string"></a>Nahrazování celého vstupního řetězce  
 Nahrazení `$_` nahradí odpovídající řetězec s celým vstupním řetězcem. To znamená, že odebere odpovídající text a nahradí jej celým řetězcem, včetně odpovídajícího textu.  
  
 Následující příklad porovnává jednu nebo několik desítkových číslic ve vstupním řetězci. Používá `$_` nahrazení nahradit je celý vstupní řetězec.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 V tomto příkladu `"ABC123DEF456"` obsahuje vstupní řetězec dvě shody. Následující tabulka ukazuje, `$_` jak nahrazení způsobí, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Shoda|Výsledný řetězec|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
