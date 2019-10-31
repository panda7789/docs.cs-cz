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
ms.openlocfilehash: 5934a342f653f294c07e00d38d51dae6b159dab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122484"
---
# <a name="substitutions-in-regular-expressions"></a>Nahrazení v regulárních výrazech
<a name="Top"></a>Náhrady jsou prvky jazyka, které jsou rozpoznávány pouze v rámci vzorů pro nahrazování. Pro definování celého textu nebo jeho části, která má nahradit odpovídající text ve vstupním řetězci, používají vzor regulárního výrazu. Vzor pro nahrazení se může skládat z jedné nebo několika substitucí spolu s literálními znaky. Vzory nahrazení jsou k dispozici pro přetížení metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>, které mají `replacement` parametr a metodu <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>. Metody nahradí odpovídající vzor vzorem, který je definován parametrem `replacement`.  
  
 Rozhraní .NET Framework definuje prvky substituce uvedené v následující tabulce.  
  
|Substituce|Popis|  
|------------------|-----------------|  
|$ *číslo*|Zahrnuje poslední podřetězec odpovídající zachytávající skupině, která je identifikována *číslem*, kde *Number* je desítková hodnota v řetězci pro nahrazení. Další informace najdete v tématu [Nahrazování číslované skupiny](#Numbered).|  
|$ { *Name* }|Zahrnuje poslední podřetězec odpovídající pojmenované skupině, která je určena názvem `(?<`*název*`> )` v řetězci pro nahrazení. Další informace naleznete v tématu [nahrazování pojmenované skupiny](#Named).|  
|$$|Zahrnuje jediný literál "$" v řetězci pro nahrazení. Další informace naleznete v tématu [nahrazování symbolu "$"](#DollarSign).|  
|$&|Zahrnuje kopii celé shody v řetězci pro nahrazení. Další informace naleznete v tématu [Nahrazování celé shody](#EntireMatch).|  
|$\`|Zahrnuje celý text vstupního řetězce před porovnáním v řetězci pro nahrazení. Další informace naleznete v tématu [nahrazování textu před porovnáváním](#BeforeMatch).|  
|$'|Zahrnuje celý text vstupního řetězce po porovnání v řetězci pro nahrazení. Další informace naleznete v tématu [nahrazování textu po porovnávání](#AfterMatch).|  
|$+|Zahrnuje poslední skupinu zachycenou v řetězci pro nahrazení. Další informace najdete v tématu [Nahrazování poslední zachycené skupiny](#LastGroup).|  
|$_|Zahrnuje celý vstupní řetězec v řetězci pro nahrazení. Další informace naleznete v tématu [Nahrazování celého vstupního řetězce](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Prvky substituce a vzory pro nahrazení  
 Substituce jsou jediné speciální konstrukce, které jsou rozpoznány ve vzorech pro nahrazení. Nejsou podporovány žádné jiné prvky jazyka regulárních výrazů, včetně řídicích znaků a tečky (`.`), která odpovídá jakémukoli znaku. Obdobně jsou prvky jazyka pro substituci rozpoznány jen ve vzorech pro nahrazení a nejsou nikdy platné ve vzorech regulárního výrazu.  
  
 Jediný znak, který se může objevit ve vzoru regulárního výrazu nebo v substituci, je `$` znak, i když má v každém kontextu jiný význam. Ve vzorku regulárního výrazu je `$` ukotvení, které odpovídá konci řetězce. V rámci vzoru pro nahrazování `$` označuje začátek substituce.  
  
> [!NOTE]
> Pro funkce podobné vzoru pro nahrazení v rámci regulárního výrazu použijte zpětný odkaz. Další informace o zpětných odkazech naleznete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Nahrazování číslované skupiny  
 Prvek jazyka `$`*číslo* zahrnuje poslední podřetězec, který odpovídá skupině zachycení *Number* v řetězci pro nahrazení, kde *Number* je index zachytávající skupiny. Například vzor pro nahrazení `$1` označuje, že odpovídající podřetězec má být nahrazen první zachycenou skupinou. Další informace o číslovaných zachytávajících skupinách naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Všechny číslice, které následují `$` jsou interpretovány jako patřící do skupiny *Number* . Pokud to však není vaším záměrem, můžete namísto toho nahradit pojmenovanou skupinu. Například můžete použít náhradní řetězec `${1}1` namísto `$11` definovat řetězec pro nahrazení jako hodnotu první zachycené skupiny spolu s číslem "1". Další informace naleznete v tématu [nahrazování pojmenované skupiny](#Named).  
  
 Zachytávající skupiny, kterým nejsou explicitně přiřazeny názvy pomocí `(?<`*název*`>)` syntaxe, jsou číslovány zleva doprava od čísla 1. Pojmenované skupiny jsou rovněž číslovány zleva doprava. Číslování začíná číslem o jedno vyšším než index poslední nepojmenované skupiny. Například v regulárním výrazu `(\w)(?<digit>\d)`index `digit` pojmenované skupiny je 2.  
  
 Pokud *číslo* neurčuje platnou zachytávající skupinu definovanou ve vzoru regulárního výrazu, `$`*číslo* je interpretováno jako literální znak sekvence, která se používá k nahrazení jednotlivých shod.  
  
 Následující příklad používá substituci `$`ho *čísla* k obložení symbolu měny z desítkové hodnoty. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Vzor regulárního výrazu `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(\s?\d+[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je první zachytávající skupina. Vzhledem k tomu, že je vzor pro nahrazení `$1`, volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nahradí celý odpovídající podřetězec touto zachycenou skupinou.|  
  
 [Zpět na začátek](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Nahrazování pojmenované skupiny  
 *Název* `${``}` prvek jazyka nahradí poslední podřetězec shodný se skupinou zachycení *názvu* , kde *název* je název zachytávající skupiny definované `(?<`*název*`>)` element Language. Další informace o pojmenovaných zachycujících skupinách naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Pokud *název* neurčuje platnou pojmenovanou zachytávající skupinu definovanou ve vzoru regulárního výrazu, ale skládá se z číslic, `${`*název*`}` interpretován jako číslovaná skupina.  
  
 Pokud *název* neurčuje platnou pojmenovanou zachytávající skupinu ani platnou očíslovanou zachytávající skupinu definovanou ve vzoru regulárního výrazu, `${`*název*`}` interpretován jako sekvence literálních znaků, která se používá k nahrazení jednotlivých shod.  
  
 Následující příklad používá `${`*název*`}` substituce k odstranění symbolu měny z desítkové hodnoty. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Vzor regulárního výrazu `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(?<amount>\s?\d[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je zachytávající skupina s názvem `amount`. Vzhledem k tomu, že je vzor pro nahrazení `${amount}`, volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nahradí celý odpovídající podřetězec touto zachycenou skupinou.|  
  
 [Zpět na začátek](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Nahrazování znaku "$"  
 Nahrazení `$$` vloží literál "$" do nahrazeného řetězce.  
  
 Následující příklad používá objekt <xref:System.Globalization.NumberFormatInfo> k určení symbolu měny aktuální jazykové verze a jeho umístění v řetězci měny. Poté dynamicky sestaví vzor regulárního výrazu a vzor pro nahrazení. Pokud je příklad spuštěn v počítači, jehož aktuální jazyková verze je en-US, vygeneruje vzor regulárního výrazu `\b(\d+)(\.(\d+))?` a `$$ $1$2`vzor pro nahrazení. Vzor pro nahrazení nahradí odpovídající text symbolem měny a mezerou následovanou první a druhou zachycenou skupinou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Vzor regulárního výrazu `\b(\d+)(\.(\d+))?` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Zahájí porovnání na začátku hranice slova.|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je první zachytávající skupina.|  
|`\.`|Porovná tečku (oddělovač desetinných míst).|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je třetí zachytávající skupina.|  
|`(\.(\d+))?`|Porovná žádný nebo jeden výskyt tečky následované jednou nebo několika desítkovými číslicemi. Toto je druhá zachytávající skupina.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Nahrazování celé shody  
 Nahrazení `$&` zahrnuje celou shodu v řetězci pro nahrazení. Často se používá k přidání podřetězce na začátek nebo konec porovnávaného řetězce. Například vzor pro nahrazení `($&)` přidá závorky na začátek a konec každé shody. Pokud se neshoduje, náhrada `$&` nemá žádný vliv.  
  
 Následující příklad používá `$&` substituce k přidávání uvozovek na začátku a na konci názvů knih uložených v poli řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Vzor regulárního výrazu `^(\w+\s?)+$` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(\w+\s?)+`|Jednou nebo vícekrát porovná vzor jednoho nebo několika znaků slova následovaného žádným nebo jedním prázdným znakem.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 Vzor pro nahrazení `"$&"` přidá literální znak citace na začátek a konec každé shody.  
  
 [Zpět na začátek](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Nahrazování textu před porovnáváním  
 Nahrazení ``$` `` nahradí porovnávaný řetězec celým vstupním řetězcem před shodou. To znamená, že duplikuje vstupní řetězec až po shodu a odebírá odpovídající text. Jakýkoli text, který následuje za odpovídajícím textem, zůstane ve výsledném řetězci nezměněn. Pokud existuje více shod ve vstupním řetězci, je text pro nahrazení odvozen z původního vstupního řetězce, nikoli z řetězce, ve kterém byl text nahrazen předchozími shodami. \(příklad poskytuje ilustraci. Pokud se neshoduje,\) nahrazení ``$` `` nijak neovlivní.  
  
 Následující příklad používá vzor regulárního výrazu `\d+`, aby odpovídal sekvenci jedné nebo více desítkových číslic ve vstupním řetězci. Nahrazující řetězec ``$` `` nahradí tyto číslice textem, který předchází shodě.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shod. Následující tabulka ukazuje, jak ``$` `` nahrazování způsobuje, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec před shodou|Výsledný řetězec|  
|-----------|--------------|-------------------------|-------------------|  
|první|odst|aa|AA**AA AA**bb2cc3dd4ee5|  
|odst|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|odst|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|čtrnáct|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Zpět na začátek](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Nahrazování textu po shodě  
 Nahrazení `$'` nahradí odpovídající řetězec celým vstupním řetězcem po shodě. To znamená, že duplikuje vstupní řetězec po shodě a odebírá odpovídající text. Jakýkoli text, který předchází odpovídajícímu textu, zůstává ve výsledném řetězci nezměněn. Pokud se neshoduje, náhrada `$'` nemá žádný vliv.  
  
 Následující příklad používá vzor regulárního výrazu `\d+`, aby odpovídal sekvenci jedné nebo více desítkových číslic ve vstupním řetězci. Nahrazující řetězec `$'` nahradí tyto číslice textem, který následuje za shodou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shod. Následující tabulka ukazuje, jak `$'` nahrazování způsobuje, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Řetězec po shodě|Výsledný řetězec|  
|-----------|--------------|------------------------|-------------------|  
|první|odst|bb2cc3dd4ee5|AA**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|odst|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|odst|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|čtrnáct|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Zpět na začátek](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Nahrazování poslední zachycené skupiny  
 Nahrazení `$+` nahradí porovnávaný řetězec poslední zachycenou skupinou. Pokud nejsou k dispozici žádné zachycené skupiny nebo pokud je hodnota poslední zachycené skupiny <xref:System.String.Empty?displayProperty=nameWithType>, náhrada `$+` nemá žádný vliv.  
  
 Následující příklad identifikuje duplicitní slova v řetězci a používá substituci `$+` k jejich nahrazení jediným výskytem slova. Možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> slouží k zajištění, že slova, která se liší v případě, která jsou jinak totožná, jsou považována za duplicitní.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Vzor regulárního výrazu `\b(\w+)\s\1\b` je definován tak, jak je uvedeno v následující tabulce.  
  
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
 Nahrazení `$_` nahradí porovnávaný řetězec celým vstupním řetězcem. To znamená, že odebere odpovídající text a nahradí jej celým řetězcem, včetně odpovídajícího textu.  
  
 Následující příklad porovnává jednu nebo několik desítkových číslic ve vstupním řetězci. Používá substituci `$_` k jejich nahrazení celým vstupním řetězcem.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 V tomto příkladu vstupní řetězec `"ABC123DEF456"` obsahuje dvě shody. Následující tabulka ukazuje, jak `$_` nahrazování způsobuje, že modul regulárních výrazů nahradí každou shodu ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Shoda|Výsledný řetězec|  
|-----------|--------------|-----------|-------------------|  
|první|3|123|ABC**ABC123DEF456**DEF456|  
|odst|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
