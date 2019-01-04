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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51e22407bd20cc6aa17b242948a83d698167590e
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030151"
---
# <a name="substitutions-in-regular-expressions"></a>Nahrazení v regulárních výrazech
<a name="Top"></a> Substituce jsou prvky jazyka, které jsou rozpoznány pouze v rámci vzory pro nahrazení. Pro definování celého textu nebo jeho části, která má nahradit odpovídající text ve vstupním řetězci, používají vzor regulárního výrazu. Vzor pro nahrazení se může skládat z jedné nebo několika substitucí spolu s literálními znaky. Vzory pro nahrazení jsou poskytovány pro přetížení <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu, která mají `replacement` parametr a <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda. Metody nahradí odpovídající vzor vzorem, který je definován `replacement` parametru.  
  
 Rozhraní .NET Framework definuje prvky substituce uvedené v následující tabulce.  
  
|Substituce|Popis|  
|------------------|-----------------|  
|`$` *Číslo*|Zahrnuje poslední podřetězec porovnaný zachytávající skupinou, která je identifikovaná *číslo*, kde *číslo* je desítková hodnota v řetězci pro nahrazení. Další informace najdete v tématu [Nahrazování číslované skupiny](#Numbered).|  
|`${` *Jméno* `}`|Zahrnuje poslední podřetězec odpovídající pojmenované skupině, která je stanovena podle prvku `(?<` *název* `> )` v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování pojmenované skupiny](#Named).|  
|`$$`|Zahrnuje jediný literál "$" v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování symbolu "$"](#DollarSign).|  
|`$&`|Zahrnuje kopii celé shody v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování celé shody](#EntireMatch).|  
|``$` ``|Zahrnuje celý text vstupního řetězce před porovnáním v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování textu před porovnáním](#BeforeMatch).|  
|`$'`|Zahrnuje celý text vstupního řetězce po porovnání v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování textu po shodě](#AfterMatch).|  
|`$+`|Zahrnuje poslední skupinu zachycenou v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování poslední zachycené skupiny](#LastGroup).|  
|`$_`|Zahrnuje celý vstupní řetězec v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování celého vstupního řetězce](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Prvky substituce a vzory pro nahrazení  
 Substituce jsou jediné speciální konstrukce, které jsou rozpoznány ve vzorech pro nahrazení. Žádná z ostatní prvky jazyka regulárních výrazů, včetně řídicích znaků a období (`.`), který odpovídá libovolnému znaku, jsou podporovány. Obdobně jsou prvky jazyka pro substituci rozpoznány jen ve vzorech pro nahrazení a nejsou nikdy platné ve vzorech regulárního výrazu.  
  
 Jediný znak, který může zobrazit ve vzoru regulárního výrazu i v substituci je `$` znak, ačkoli má v jednotlivých kontextech odlišný význam. Ve vzoru regulárního výrazu `$` kotva, která odpovídá konci řetězce. Ve vzorech pro nahrazení `$` označuje začátek substituce.  
  
> [!NOTE]
>  Pro funkce podobné vzoru pro nahrazení v rámci regulárního výrazu použijte zpětný odkaz. Další informace o zpětných odkazech naleznete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Nahrazování číslované skupiny  
 `$` *Číslo* prvek jazyka zahrnuje poslední podřetězec porovnaný *číslo* zachytávající skupinou v řetězci pro nahrazení, kde *číslo* je index zachytávající skupina. Například vzor pro nahrazení `$1` označuje, že odpovídající podřetězec bude nahrazen první zachycenou skupinou. Další informace o číslovaných zachytávajících skupinách naleznete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Všechny číslice za znakem `$` se interpretují jako součást *číslo* skupiny. Pokud to však není vaším záměrem, můžete namísto toho nahradit pojmenovanou skupinu. Například můžete použít řetězci pro nahrazení `${1}1` místo `$11` k definování řetězci pro nahrazení jako hodnoty první zachycené skupiny spolu s číslem "1". Další informace najdete v tématu [nahrazování pojmenované skupiny](#Named).  
  
 Zachycující skupiny, které nejsou explicitně přiřazeny názvy pomocí `(?<` *název* `>)` syntaxe jsou číslovány zleva doprava od čísla 1. Pojmenované skupiny jsou rovněž číslovány zleva doprava. Číslování začíná číslem o jedno vyšším než index poslední nepojmenované skupiny. Například v regulárním výrazu `(\w)(?<digit>\d)`, index `digit` pojmenovanou skupinu se 2.  
  
 Pokud *číslo* neurčuje platnou zachytávající skupinu definovanou ve vzoru regulárního výrazu `$` *číslo* je interpretován jako sekvence literálních znaků, který se používá k nahrazení jednotlivých shod.  
  
 V následujícím příkladu `$` *číslo* nahrazení pro oříznutí symbolu měny z desítkové hodnoty čísla. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Vzor regulárního výrazu `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(\s?\d+[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je první zachytávající skupina. Protože je vzor pro nahrazení `$1`, volání <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda nahradí celý odpovídající podřetězec této zachycené skupiny.|  
  
 [Zpět na začátek](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Nahrazování pojmenované skupiny  
 `${` *Název* `}` prvek jazyka nahradí poslední podřetězec porovnaný *název* zachytávající skupinou, kde *název* je název zachycující skupiny definovány `(?<` *název* `>)` elementu jazyka. Další informace o pojmenovaných zachytávajících skupinách naleznete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Pokud *název* neurčuje platnou pojmenovanou zachytávající skupinu definovanou ve vzoru regulárního výrazu, ale sestává z číslic, `${` *název* `}` je interpretován jako očíslovaná skupina.  
  
 Pokud *název* Určuje platnou pojmenovanou zachytávající skupinu ani platnou očíslovanou zachytávající skupinu definovanou ve vzoru regulárního výrazu, `${` *název* `}` je interpretován jako sekvence literálních znaků, který se používá k nahrazení jednotlivých shod.  
  
 V následujícím příkladu `${` *název* `}` nahrazení pro oříznutí symbolu měny z desítkové hodnoty čísla. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Vzor regulárního výrazu `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(?<amount>\s?\d[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je zachytávající skupina s názvem `amount`. Protože je vzor pro nahrazení `${amount}`, volání <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda nahradí celý odpovídající podřetězec této zachycené skupiny.|  
  
 [Zpět na začátek](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Nahrazování znaku "$"  
 `$$` Nahrazení vloží literální znak "$" do nahrazeného řetězce.  
  
 V následujícím příkladu <xref:System.Globalization.NumberFormatInfo> objektem pro určení symbolu měny aktuální jazykové verze a jeho umístění v řetězci měny. Poté dynamicky sestaví vzor regulárního výrazu a vzor pro nahrazení. Pokud je příklad spuštěn na počítači, jehož aktuální jazyková verze je en US, vygeneruje vzor regulárního výrazu `\b(\d+)(\.(\d+))?` a vzor pro nahrazení `$$ $1$2`. Vzor pro nahrazení nahradí odpovídající text symbolem měny a mezerou následovanou první a druhou zachycenou skupinou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Vzor regulárního výrazu `\b(\d+)(\.(\d+))?` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Zahájí porovnání na začátku hranice slova.|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je první zachytávající skupina.|  
|`\.`|Porovná tečku (oddělovač desetinných míst).|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je třetí zachytávající skupina.|  
|`(\.(\d+))?`|Porovná žádný nebo jeden výskyt tečky následované jednou nebo několika desítkovými číslicemi. Toto je druhá zachytávající skupina.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Nahrazování celé shody  
 `$&` Nahrazení zahrnuje celou shodu v řetězci pro nahrazení. Často se používá k přidání podřetězce na začátek nebo konec porovnávaného řetězce. Například `($&)` vzor pro nahrazení se přidají závorky na začátek a konec jednotlivých shod. Pokud není nalezena žádná shoda, `$&` nahrazení nemá žádný vliv.  
  
 V následujícím příkladu `$&` nahrazení pro přidání uvozovek na začátek a konec názvů knih uložených v poli řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Vzor regulárního výrazu `^(\w+\s?)+$` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(\w+\s?)+`|Jednou nebo vícekrát porovná vzor jednoho nebo několika znaků slova následovaného žádným nebo jedním prázdným znakem.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 `"$&"` Vzor pro nahrazení přidá literální znak uvozovek na začátek a konec jednotlivých shod.  
  
 [Zpět na začátek](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Nahrazování textu před porovnáváním  
 ``$` `` Nahrazení nahradí odpovídající řetězec celým vstupním řetězcem před shodou. To znamená, že duplikuje vstupní řetězec až po shodu a odebírá odpovídající text. Jakýkoli text, který následuje za odpovídajícím textem, zůstane ve výsledném řetězci nezměněn. Pokud existuje více shod ve vstupním řetězci, je text pro nahrazení odvozen z původního vstupního řetězce, nikoli z řetězce, ve kterém byl text nahrazen předchozími shodami. \(V příkladu je uvedena ukázka.\) Pokud není nalezena žádná shoda, ``$` `` nahrazení nemá žádný vliv.  
  
 Následující příklad používá vzor regulárního výrazu `\d+` pro porovnání sekvence jedné nebo více desítkových číslic ve vstupním řetězci. Řetězci pro nahrazení ``$` `` nahradí tyto číslice textem, který předchází shodě.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shod. Následující tabulka ukazuje, jak ``$` `` nahrazení způsobí, že modul regulárních výrazů nahradí jednotlivé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec před shodou|Výsledný řetězec|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Zpět na začátek](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Nahrazování textu po shodě  
 `$'` Nahrazení nahradí porovnávaný řetězec celým vstupním řetězcem po shodě. To znamená, že duplikuje vstupní řetězec po shodě a odebírá odpovídající text. Jakýkoli text, který předchází odpovídajícímu textu, zůstává ve výsledném řetězci nezměněn. Pokud není nalezena žádná shoda, `$'` nahrazení nemá žádný vliv.  
  
 Následující příklad používá vzor regulárního výrazu `\d+` pro porovnání sekvence jedné nebo více desítkových číslic ve vstupním řetězci. Řetězci pro nahrazení `$'` nahradí tyto číslice textem, který následuje po shodě.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shod. Následující tabulka ukazuje, jak `$'` nahrazení způsobí, že modul regulárních výrazů nahradí jednotlivé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec po shodě|Výsledný řetězec|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Zpět na začátek](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Nahrazování poslední zachycené skupiny  
 `$+` Nahrazení nahradí odpovídající řetězec poslední zachycenou skupinou. Pokud nebyly nalezeny žádné zachycené skupiny nebo pokud je hodnota poslední zachycenou skupinou <xref:System.String.Empty?displayProperty=nameWithType>, `$+` nahrazení nemá žádný vliv.  
  
 Následující příklad vyhledává duplicitní slova v řetězci a používá `$+` nahrazení pro jejich nahrazení jedním výskytem slova. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Možnost se používá k zajištění, že slova, která se liší velikostí písmen, ale které jsou jinak identická považována za duplicitní.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Vzor regulárního výrazu `\b(\w+)\s\1\b` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`\1`|Porovná první zachycenou skupinu.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#Top)  
  
<a name="EntireString"></a>   
## <a name="substituting-the-entire-input-string"></a>Nahrazování celého vstupního řetězce  
 `$_` Nahrazení nahradí porovnávaný řetězec celým vstupním řetězcem. To znamená, že odebere odpovídající text a nahradí jej celým řetězcem, včetně odpovídajícího textu.  
  
 Následující příklad porovnává jednu nebo několik desítkových číslic ve vstupním řetězci. Používá `$_` nahrazení pro jejich nahrazení celým vstupním řetězcem.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 V tomto příkladu vstupní řetězec `"ABC123DEF456"` obsahuje dvě shody. Následující tabulka ukazuje, jak `$_` nahrazení způsobí, že modul regulárních výrazů nahradí jednotlivé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Shoda|Výsledný řetězec|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
