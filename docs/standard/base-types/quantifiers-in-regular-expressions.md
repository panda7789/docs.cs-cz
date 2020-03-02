---
title: Kvantifikátory v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
ms.openlocfilehash: f1627248cbed0f03c6fb76ce660f9b2bf7764781
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160011"
---
# <a name="quantifiers-in-regular-expressions"></a>Kvantifikátory v regulárních výrazech
Kvantifikátory určují, kolik instancí znaku, skupiny nebo třídy znaků musí být přítomné ve vstupu pro nalezení shody.  V následující tabulce jsou uvedeny kvantifikátory podporované rozhraním .NET.  
  
|Hladový kvantifikátor|Opožděný kvantifikátor|Popis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Porovná nula nebo vícekrát.|  
|`+`|`+?`|Porovnává jednou nebo vícekrát.|  
|`?`|`??`|Porovná žádný nebo jeden čas.|  
|`{` *n* `}`|`{` *n* `}?`|Porovná přesně *n* krát.|  
|`{` *n* `,}`|`{` *n* `,}?`|Porovnává alespoň *n* krát.|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|Porovnává od *n* do *m* krát.|  
  
 Množství `n` a `m` jsou konstanty typu Integer. Obvykle jsou kvantifikátory hladce; způsobují, že modul regulárních výrazů porovnává tolik výskytů určitých vzorů, jak je to možné. Připojení `?`ho znaku k kvantifikátoru je opožděné; způsobí, že se modul regulárních výrazů porovnává s počtem výskytů, jak je to možné. Úplný popis rozdílu mezi hladce a opožděnými kvantifikátory naleznete v části [hladce a opožděné kvantifikátory](#Greedy) dále v tomto tématu.  
  
> [!IMPORTANT]
> Vnořování kvantifikátorů (například jako vzor regulárního výrazu `(a*)*`) může zvýšit počet porovnání, které musí modul regulárních výrazů provádět, jako exponenciální funkci počtu znaků ve vstupním řetězci. Další informace o tomto chování a jejich řešeních najdete v tématu [zpětné navrácení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kvantifikátory regulárního výrazu  
 V následujících částech jsou uvedeny kvantifikátory podporované regulárními výrazy .NET.  
  
> [!NOTE]
> Pokud jsou ve vzoru regulárního výrazu zjištěny znaky *, +,?, {a}, modul regulárních výrazů je interpretuje jako kvantifikátory nebo část konstrukcí kvantifikátoru, pokud nejsou zahrnuty ve [třídě znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Chcete-li je interpretovat jako literální znaky vně třídy znaků, je nutné je před pomocí zpětného lomítka řídicím znakem. Například řetězec `\*` ve vzoru regulárního výrazu je interpretován jako literální znak hvězdičky ("\*").  
  
### <a name="match-zero-or-more-times-"></a>Porovná nula nebo více časů: *  
 Kvantifikátor `*` odpovídá předchozímu prvku nula nebo vícekrát. Je ekvivalentní s kvantifikátorem `{0,}`. `*` je hladový kvantifikátor, jehož opožděný ekvivalent je `*?`.  
  
 Následující příklad ilustruje tento regulární výraz. Z devíti číslic ve vstupním řetězci, pět odpovídá vzoru a čtyři (`95`, `929`, `9219`a `9919`).  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`91*`|Porovná řetězec "9" následovaný žádným nebo více znaky "1".|  
|`9*`|Porovná nula nebo více znaků "9".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-one-or-more-times-"></a>Porovnává jednou nebo víckrát: +  
 Kvantifikátor `+` Porovná předchozí prvek jednou nebo vícekrát. Je ekvivalentní `{1,}`. `+` je hladový kvantifikátor, jehož opožděný ekvivalent je `+?`.  
  
 Například regulární výraz `\ban+\w*?\b` se snaží vyhledat celá slova, která začínají písmenem `a` následovaný jednou nebo více instancemi písmena `n`. Následující příklad ilustruje tento regulární výraz. Regulární výraz odpovídá slovům `an`, `annual`, `announcement`a `antique`a správně nevyhovuje `autumn` a `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an+`|Porovnává se znakem "a" následovaným jedním nebo více znaky "n".|  
|`\w*?`|Porovná znak slova nula nebo vícekrát, ale s co nejmenším možným počtem opakování.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-zero-or-one-time-"></a>Odpovídá žádnému nebo jednomu času:?  
 Kvantifikátor `?` odpovídá předchozímu prvku nula nebo jednou. Je ekvivalentní `{0,1}`. `?` je hladový kvantifikátor, jehož opožděný ekvivalent je `??`.  
  
 Například regulární výraz `\ban?\b` se snaží vyhledat celá slova, která začínají písmenem `a` následovaný nulou nebo jednou instancí `n`ho písmene. Jinými slovy se pokusí vyhledat slova `a` a `an`. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an?`|Porovná znak "a" následovaný žádným nebo jedním znakem "n".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-exactly-n-times-n"></a>Porovná přesně n krát: {n}  
 Kvantifikátor`}` `{`*n* odpovídá předchozímu prvku přesně *n* krát, kde *n* je libovolné celé číslo. `{`*n*`}` je hladový kvantifikátor, jehož opožděný ekvivalent je `{`*n*`}?`.  
  
 Například regulární výraz `\b\d+\,\d{3}\b` se snaží porovnat hranici slova následovaný jednou nebo více desítkovými číslicemi následovanými třemi desítkovými číslicemi, za kterými následuje hranice slova. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\,`|Porovnává se znakem čárky.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-at-least-n-times-n"></a>Porovnává alespoň n krát: {n,}  
 Kvantifikátor`,}` `{`*n* odpovídá předchozímu prvku nejméně *n* krát, kde *n* je libovolné celé číslo. `{`*n*`,}` je hladový kvantifikátor, jehož opožděný ekvivalent je `{`*n*`,}?`.  
  
 Například regulární výraz `\b\d{2,}\b\D+` se snaží porovnat hranici slova následovaný alespoň dvěma číslicemi následovanými hranicí slova a znakem, který není číslice. Následující příklad ilustruje tento regulární výraz. Regulárnímu výrazu se nepodaří najít frázi `"7 days"`, protože obsahuje jenom jednu desítkovou číslici, ale úspěšně odpovídá frázím `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d{2,}`|Porovnává alespoň dvě desítkové číslice.|  
|`\b`|Porovná hranici slova.|  
|`\D+`|Porovnává alespoň jednu jinou než desítkovou číslici.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Shoda mezi n a m časy: {n, m}  
 Kvantifikátor `{`*n*`,`*m*`}` Porovná předchozí prvek nejméně *n* krát, ale ne více než *m* krát, kde *n* a *m* jsou celá čísla. `{`*n*`,`*m*`}` je hladový kvantifikátor, jehož opožděný ekvivalent je `{`*n*`,`*m*`}?`.  
  
 V následujícím příkladu regulární výraz `(00\s){2,4}` se pokusí porovnat dva a čtyři výskyty dvou číslic s nulovým počtem následovaným mezerou. Všimněte si, že poslední část vstupního řetězce obsahuje tento vzor pětkrát, ne jako maximum čtyři. Pouze počáteční část tohoto podřetězce (až do prostoru a páté dvojice nul) však odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Porovná nula nebo více časů (opožděné porovnávání): *?  
 Kvantifikátor `*?` odpovídá předchozímu prvku nula nebo vícekrát, ale s co nejmenším možným počtem opakování. Je opožděným protějškem hladového kvantifikátoru `*`.  
  
 V následujícím příkladu regulární výraz `\b\w*?oo\w*?\b` odpovídá všem slovům, která obsahují řetězec `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\w*?`|Porovná žádný nebo více znaků slova, ale co nejvíce znaků.|  
|`oo`|Porovnává s řetězcem "ó".|  
|`\w*?`|Porovná žádný nebo více znaků slova, ale co nejvíce znaků.|  
|`\b`|Ukončí hranici slova.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Odpovídá jednomu nebo více výskytům (opožděné porovnávání): +?  
 Kvantifikátor `+?` Porovná předchozí prvek jednou nebo vícekrát, ale s co nejmenším možným počtem opakování. Je opožděným protějškem hladového kvantifikátoru `+`.  
  
 Například regulární výraz `\b\w+?\b` odpovídá jednomu nebo více znakům odděleným ohraničením slova. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Odpovídá žádnému nebo jednomu času (opožděné porovnávání):??  
 Kvantifikátor `??` odpovídá předchozímu prvku nula nebo jednou, ale s co nejmenším možným počtem opakování. Je opožděným protějškem hladového kvantifikátoru `?`.  
  
 Například regulární výraz `^\s*(System.)??Console.Write(Line)??\(??` se pokusí porovnat řetězce "Console. Write" nebo "Console. WriteLine". Řetězec může obsahovat také "System." před "Console" a za ní může následovat levá závorka. Řetězec musí být na začátku řádku, i když může předcházet prázdné znaky. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídá začátku vstupního datového proudu.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(System.)??`|Porovná žádný nebo jeden výskyt řetězce "System.".|  
|`Console.Write`|Porovnává s řetězcem "Console. Write".|  
|`(Line)??`|Porovná žádný nebo jeden výskyt řetězce "line".|  
|`\(??`|Porovná žádný nebo jeden výskyt levé závorky.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Porovná přesně n krát (opožděná shoda): {n}?  
 Kvantifikátor`}?` `{`*n* odpovídá předchozímu prvku přesně `n` časy, kde *n* je libovolné celé číslo. Je opožděným protějškem hladového kvantifikátoru `{`*n*`}`.  
  
 V následujícím příkladu regulární výraz `\b(\w{3,}?\.){2}?\w{3,}?\b` slouží k identifikaci adresy webu. Všimněte si, že odpovídá "www.microsoft.com" a "msdn.microsoft.com", ale neodpovídá "mywebsite" nebo "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(\w{3,}?\.)`|Porovnává alespoň 3 znaky slova, ale co nejvíce znaků a znak tečky nebo tečky. Toto je první zachytávající skupina.|  
|`(\w{3,}?\.){2}?`|Porovnává vzor v první skupině dvakrát, ale s co nejmenším možným počtem opakování.|  
|`\b`|Ukončí porovnávání na hranici slova.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Porovnává alespoň n krát (opožděná shoda): {n,}?  
 Kvantifikátor`,}?` `{`*n* odpovídá předchozímu prvku alespoň `n` časy, kde *n* je libovolné celé číslo, ale co nejmenším možným způsobem. Je opožděným protějškem hladového kvantifikátoru `{`*n*`,}`.  
  
 Obrázek najdete v příkladu pro kvantifikátor `{`*n*`}?` v předchozí části. Regulární výraz v tomto příkladu používá kvantifikátor `{`*n*`,}`, aby se shodoval s řetězcem, který má alespoň tři znaky následovaný tečkou.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Rozlišovat mezi n a m krátkou (opožděné porovnávání): {n, m}?  
 `{`*n*`,`*m*`}?` kvantifikátor se shoduje s předchozím prvkem mezi `n` a `m`mi časy, kde *n* a *m* jsou celá čísla, ale s co nejmenším možným počtem opakování. Je opožděným protějškem hladového kvantifikátoru `{`*n*`,`*m*`}`.  
  
 V následujícím příkladu regulární výraz `\b[A-Z](\w*?\s*?){1,10}[.!?]` odpovídá vět, které obsahují mezi jedním a deseti slovy. Odpovídá všem větuem ve vstupním řetězci s výjimkou jedné věty, která obsahuje 18 slov.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Porovnává velké písmeno od A do Z.|  
|`(\w*?\s*?)`|Porovná žádný nebo více slovních znaků následovaných jedním nebo více prázdnými znaky, ale co nejmenším možným počtem opakování. Toto je první skupina zachycení.|  
|`{1,10}`|Porovnává s předchozím vzorem mezi 1 a 10krát.|  
|`[.!?]`|Porovnává s libovolným znakem interpunkce ".", "!" nebo "?".|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a>Hladce a opožděné kvantifikátory  
 Počet kvantifikátorů má dvě verze:  
  
- Hladec – verze  
  
     Hladový kvantifikátor se snaží porovnat prvek tolikrát, kolikrát je to možné.  
  
- Nehladec (nebo opožděná) verze.  
  
     Nehladý kvantifikátor se snaží porovnat element co nejmenším možným počtem opakování. Hladový kvantifikátor můžete převést na opožděný kvantifikátor pouhým přidáním `?`.  
  
 Vezměte v úvahu jednoduchý regulární výraz, který je určen k extrakci posledních čtyř číslic z řetězce čísel, jako je číslo platební karty. Verze regulárního výrazu, který používá `*` hladový kvantifikátor, je `\b.*([0-9]{4})\b`. Nicméně pokud řetězec obsahuje dvě čísla, tento regulární výraz odpovídá posledním čtyřm číslicím druhé číslo, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Regulárnímu výrazu se neshoduje s prvním číslem, protože kvantifikátor `*` se snaží vyhledat předchozí prvek tolikrát, kolikrát je to možné v celém řetězci, a tak najde shodu na konci řetězce.  
  
 Nejedná se o požadované chování. Místo toho můžete použít `*?`opožděný kvantifikátor pro extrakci číslic z obou čísel, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Ve většině případů regulární výrazy s hladkou a opožděným kvantifikátorem vracejí stejné shody. Nejčastěji vracejí různé výsledky při použití se metaznakem zástupného znaku (`.`), který odpovídá jakémukoli znaku.  
  
## <a name="quantifiers-and-empty-matches"></a>Kvantifikátory a prázdné shody  
 Kvantifikátory `*`, `+`a `{`*n*`,`*m*`}` a jejich opožděné protějšky se nikdy neopakují po prázdné shodě, pokud byl nalezen minimální počet zachycení. Toto pravidlo brání kvantifikátorům v zadávání nekonečných smyček u prázdných dílčích výrazů, pokud je maximální počet možných zachycení skupin nekonečný nebo je blízko nekonečné.  
  
 Například následující kód ukazuje výsledek volání metody <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> se vzorem regulárního výrazu `(a?)*`, který odpovídá žádnému nebo jednomu znaku "a" nula nebo vícekrát. Všimněte si, že jedna zachytávající skupina zachycuje každou "a", ale také <xref:System.String.Empty?displayProperty=nameWithType>, ale neexistuje žádná druhá prázdná shoda, protože první prázdná shoda způsobí, že kvantifikátor přestane opakovat.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Chcete-li zobrazit praktický rozdíl mezi zachytávající skupinou definující minimální a maximální počet zachycení a jednu, která definuje pevný počet zachycení, zvažte vzory regulárních výrazů `(a\1|(?(1)\1)){0,2}` a `(a\1|(?(1)\1)){2}`. Oba regulární výrazy se skládají z jedné zachytávající skupiny, která je definována tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(a\1`|Buď porovnává "a" spolu s hodnotou první zachycené skupiny...|  
|<code>&#124;(?(1)</code>|… nebo testujte, zda byla definována první zachycená skupina. (Všimněte si, že `(?(1)` konstrukce nedefinuje zachytávající skupinu.)|  
|`\1))`|Pokud existuje první zachycená skupina, odpovídá její hodnotě. Pokud skupina neexistuje, bude skupina odpovídat <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 První regulární výraz se pokusí porovnat tento vzor mezi nulou a dvakrát. druhý, přesně dvakrát. Vzhledem k tomu, že první model dosáhne svého minimálního počtu zachycení s prvním zachycením <xref:System.String.Empty?displayProperty=nameWithType>, nikdy se neopakuje, aby se pokusila porovnat `a\1`; kvantifikátor `{0,2}` povoluje v poslední iteraci pouze prázdné shody. Naopak druhý regulární výraz odpovídá "a", protože vyhodnocuje `a\1` podruhé. minimální počet iterací, 2, vynutí, aby se modul opakoval po prázdné shodě.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
