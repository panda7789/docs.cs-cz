---
title: "Nahrazení v regulárních výrazech"
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
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f93584b9dff721c8521d8cb58aaf5eab2c1fc931
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="substitutions-in-regular-expressions"></a>Nahrazení v regulárních výrazech
<a name="Top"></a>Náhrady jsou prvky jazyka, které jsou rozpoznány jenom v rámci vzory pro nahrazování. Pro definování celého textu nebo jeho části, která má nahradit odpovídající text ve vstupním řetězci, používají vzor regulárního výrazu. Vzor pro nahrazení se může skládat z jedné nebo několika substitucí spolu s literálními znaky. Vzory pro nahrazování jsou poskytovány přetížení <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda, která mají `replacement` parametru a <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda. Metody nahradí odpovídající vzor vzor, který je definován `replacement` parametr.  
  
 Rozhraní .NET Framework definuje prvky substituce uvedené v následující tabulce.  
  
|Substituce|Popis|  
|------------------|-----------------|  
|`$`*číslo*|Obsahuje poslední podřetězec zachytávající skupině, která je identifikovaná *číslo*, kde *číslo* je desítková hodnota v řetězci nahrazení. Další informace najdete v tématu [Nahrazování číslované skupiny](#Numbered).|  
|`${`*název*`}`|Obsahuje poslední podřetězec s názvem skupiny, který je určen podle `(?<` *název* `> )` v řetězci nahrazení. Další informace najdete v tématu [nahrazování pojmenované skupiny](#Named).|  
|`$$`|Zahrnuje jediný literál "$" v řetězci pro nahrazení. Další informace najdete v tématu [nahraďte Symbol "$"](#DollarSign).|  
|`$&`|Zahrnuje kopii celé shody v řetězci pro nahrazení. Další informace najdete v tématu [nahrazení celé shody](#EntireMatch).|  
|<code>$\`</code>|Zahrnuje celý text vstupního řetězce před porovnáním v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování textu před shody](#BeforeMatch).|  
|`$'`|Zahrnuje celý text vstupního řetězce po porovnání v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování textu po porovnávání](#AfterMatch).|  
|`$+`|Zahrnuje poslední skupinu zachycenou v řetězci pro nahrazení. Další informace najdete v tématu [nahrazování poslední zachycené skupiny](#LastGroup).|  
|`$_`|Zahrnuje celý vstupní řetězec v řetězci pro nahrazení. Další informace najdete v tématu [nahraďte celý vstupní řetězec](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Prvky substituce a vzory pro nahrazení  
 Substituce jsou jediné speciální konstrukce, které jsou rozpoznány ve vzorech pro nahrazení. Žádné jiné regulární výraz jazyka prvky, včetně znak řídicí sekvence a období (`.`), který odpovídá libovolný znak, jsou podporovány. Obdobně jsou prvky jazyka pro substituci rozpoznány jen ve vzorech pro nahrazení a nejsou nikdy platné ve vzorech regulárního výrazu.  
  
 Jediným znakem, která se může zobrazit v vzor regulárního výrazu nebo v nahrazování, je `$` znak, i když má jiný význam v každém kontextu. V vzor regulárního výrazu `$` je element anchor, který odpovídá konci řetězce. Ve vzoru nahrazení `$` označuje začátek nahrazení.  
  
> [!NOTE]
>  Pro funkce podobné vzoru pro nahrazení v rámci regulárního výrazu použijte zpětný odkaz. Zpětné odkazy na další informace najdete v tématu [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Nahrazování číslované skupiny  
 `$` *Číslo* element jazyk obsahuje poslední podřetězec odpovídající *číslo* zaznamenávání skupiny v řetězci nahrazení, kde *číslo* je index zachycující skupiny. Například vzorek pro nahrazení `$1` označuje, že odpovídající podřetězec je nahradit za první zaznamenané skupinu. Další informace o číslované zachytávající skupiny najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Všechny číslic, které následují `$` se interpretují jako náležící do *číslo* skupiny. Pokud to však není vaším záměrem, můžete namísto toho nahradit pojmenovanou skupinu. Například můžete použít náhradní řetězec `${1}1` místo `$11` k definování náhradní řetězec jako hodnotu první skupinu zaznamenané společně s číslo "1". Další informace najdete v tématu [nahrazování pojmenované skupiny](#Named).  
  
 Zachycující skupiny, které nejsou explicitně přiřazeny názvy pomocí `(?<` *název* `>)` syntaxe jsou číslována zleva doprava a začínají na jedné. Pojmenované skupiny jsou rovněž číslovány zleva doprava. Číslování začíná číslem o jedno vyšším než index poslední nepojmenované skupiny. Například v regulárním výrazu `(\w)(?<digit>\d)`, index `digit` pojmenovanou skupinu je 2.  
  
 Pokud *číslo* neurčuje platnou zachytávající skupiny definované v vzor regulárního výrazu `$` *číslo* interpretována jako posloupnost literálu znak, který se používá k nahrazení každé shody.  
  
 Následující příklad používá `$` *číslo* nahrazení oddělit symbolu měny z desítkovou hodnotu. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Regulární výraz `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(\s?\d+[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je první zachytávající skupina. Protože je vzor nahrazení `$1`, volání <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda nahradí celý odpovídající podřetězec této zaznamenané skupiny.|  
  
 [Zpět na začátek](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Nahrazování pojmenované skupiny  
 `${` *Název* `}` jazyk element nahradí poslední podřetězec odpovídající pomocí *název* zaznamenávání skupiny, kde *název* je název zaznamenání skupiny definované `(?<` *název* `>)` element jazyka. Další informace o pojmenované zachytávající skupiny najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Pokud *název* neurčuje platnou s názvem zachytávající skupiny definované v regulární výraz, ale obsahuje číslice, `${` *název* `}` interpretována jako číslované skupině.  
  
 Pokud *název* určuje platná skupina s názvem zaznamenávání ani platný číslované zachytávající skupiny definované v vzor regulárního výrazu `${` *název* `}` interpretována jako posloupnost literálu znaků, který se používá k nahrazení každé shody.  
  
 Následující příklad používá `${` *název* `}` nahrazení oddělit symbolu měny z desítkovou hodnotu. Odebere symboly měny nalezené na začátku nebo konci peněžní hodnoty a rozpozná dva nejběžnější oddělovače desetinných míst "." a ",".  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Regulární výraz `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}*`|Porovná žádný nebo více znaků symbolu měny.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`[.,]?`|Porovná žádnou nebo jednu tečku či čárku.|  
|`\d*`|Porovná žádnou nebo několik desítkových číslic.|  
|`(?<amount>\s?\d[.,]?\d*)`|Porovná prázdný znak, následovaný jednou nebo několika desítkovými číslicemi, následovanými žádnou nebo jednou tečkou nebo čárkou, následovanou žádnou nebo několika desítkovými číslicemi. Toto je zachytávající skupina s názvem `amount`. Protože je vzor nahrazení `${amount}`, volání <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda nahradí celý odpovídající podřetězec této zaznamenané skupiny.|  
  
 [Zpět na začátek](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Nahrazování znaku "$"  
 `$$` Nahrazení vloží znak "$" literálu nahrazeného řetězce.  
  
 Následující příklad používá <xref:System.Globalization.NumberFormatInfo> objektem pro určení symbolu měny aktuální jazykovou verzi a její umístění v řetězci měny. Poté dynamicky sestaví vzor regulárního výrazu a vzor pro nahrazení. Pokud v příkladu běží na počítači, jejichž aktuální jazykové verze je en US, generuje regulární výraz `\b(\d+)(\.(\d+))?` a vzorek pro nahrazení `$$ $1$2`. Vzor pro nahrazení nahradí odpovídající text symbolem měny a mezerou následovanou první a druhou zachycenou skupinou.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Regulární výraz `\b(\d+)(\.(\d+))?` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Zahájí porovnání na začátku hranice slova.|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je první zachytávající skupina.|  
|`\.`|Porovná tečku (oddělovač desetinných míst).|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je třetí zachytávající skupina.|  
|`(\.(\d+))?`|Porovná žádný nebo jeden výskyt tečky následované jednou nebo několika desítkovými číslicemi. Toto je druhá zachytávající skupina.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Nahrazování celé shody  
 `$&` Nahrazení zahrnuje celou shodu v řetězci nahrazení. Často se používá k přidání podřetězce na začátek nebo konec porovnávaného řetězce. Například `($&)` nahrazení vzor přidá na začátek a konec každé shoda závorky. Pokud není nalezena žádná shoda `$&` nahrazení nemá žádný vliv.  
  
 Následující příklad používá `$&` nahrazení pro přidání uvozovek na začátek a konec názvů knih uložených v poli řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Regulární výraz `^(\w+\s?)+$` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(\w+\s?)+`|Jednou nebo vícekrát porovná vzor jednoho nebo několika znaků slova následovaného žádným nebo jedním prázdným znakem.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 `"$&"` Nahrazení vzor přidá na začátek a konec každé shoda literálu uvozovky.  
  
 [Zpět na začátek](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Nahrazování textu před porovnáváním  
 <code>$\`</code> Nahrazení nahradí celý vstupní řetězec před shody odpovídající řetězec. To znamená, že duplikuje vstupní řetězec až po shodu a odebírá odpovídající text. Jakýkoli text, který následuje za odpovídajícím textem, zůstane ve výsledném řetězci nezměněn. Pokud existuje více shod ve vstupním řetězci, je text pro nahrazení odvozen z původního vstupního řetězce, nikoli z řetězce, ve kterém byl text nahrazen předchozími shodami. \(Příklad uvádí ukázku.\) Pokud není nalezena žádná shoda <code>$\`</code> nahrazení nemá žádný vliv.  
  
 Následující příklad používá regulární výraz `\d+` tak, aby odpovídala pořadí jeden nebo více desítkových číslic ve vstupním řetězci. Náhradní řetězec <code>$`</code> nahradí tyto číslic text, který předchází shody.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shody. Následující tabulka popisuje, jak <code>$`</code> nahrazení způsobí, že modul regulárních výrazů k nahrazení každé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
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
 `$'` Nahrazování nahradí odpovídající řetězec celý vstupní řetězec po shody. To znamená, že duplikuje vstupní řetězec po shodě a odebírá odpovídající text. Jakýkoli text, který předchází odpovídajícímu textu, zůstává ve výsledném řetězci nezměněn. Pokud není nalezena žádná shoda `$'` nahrazení nemá žádný vliv.  
  
 Následující příklad používá regulární výraz `\d+` tak, aby odpovídala pořadí jeden nebo více desítkových číslic ve vstupním řetězci. Náhradní řetězec `$'` nahradí tyto číslic text, který následuje shody.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 V tomto příkladu vstupní řetězec `"aa1bb2cc3dd4ee5"` obsahuje pět shody. Následující tabulka popisuje, jak `$'` nahrazení způsobí, že modul regulárních výrazů k nahrazení každé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
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
 `$+` Nahrazování nahradí odpovídající řetězec poslední zachycené skupiny. Pokud neexistují žádné zachycené skupiny nebo pokud je hodnota poslední zachycené skupiny <xref:System.String.Empty?displayProperty=nameWithType>, `$+` nahrazení nemá žádný vliv.  
  
 Následující příklad určuje duplicitní slova v řetězci a používá `$+` nahrazování pro nahrazení je jediný výskyt aplikace word. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Možnost se používá k zajištění, že jsou slova, která se liší v případě, ale které jsou jinak identická považována za duplicitní.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Regulární výraz `\b(\w+)\s\1\b` je definovaný jak je znázorněno v následující tabulce.  
  
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
 `$_` Nahrazení nahradí celý vstupní řetězec odpovídající řetězec. To znamená, že odebere odpovídající text a nahradí jej celým řetězcem, včetně odpovídajícího textu.  
  
 Následující příklad porovnává jednu nebo několik desítkových číslic ve vstupním řetězci. Použije `$_` nahrazování pro nahrazení celý vstupní řetězec.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 V tomto příkladu vstupní řetězec `"ABC123DEF456"` obsahuje dvě shody. Následující tabulka popisuje, jak `$_` nahrazení způsobí, že modul regulárních výrazů k nahrazení každé shody ve vstupním řetězci. Vložený text je zobrazen tučně ve sloupci výsledků.  
  
|Shoda|Pozice|Shoda|Výsledný řetězec|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
