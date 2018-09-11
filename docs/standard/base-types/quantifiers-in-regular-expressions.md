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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a982082611760e4f901c427af25a0a49a4e243a1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886068"
---
# <a name="quantifiers-in-regular-expressions"></a>Kvantifikátory v regulárních výrazech
Kvantifikátory zadejte, kolik instancí znak, skupina nebo třída znaků musí být k dispozici ve vstupu pro shodu, která se má najít.  V následující tabulce jsou uvedeny kvantifikátory podporované rozhraním .NET.  
  
|Greedy kvantifikátor|Opožděným kvantifikátorem|Popis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Porovná nulakrát nebo vícekrát.|  
|`+`|`+?`|Shodovat s jednou nebo vícekrát.|  
|`?`|`??`|Porovná žádný nebo jeden čas.|  
|`{` *N* `}`|`{` *N* `}?`|Přesně odpovídat *n* časy.|  
|`{` *N* `,}`|`{` *N* `,}?`|Odpovídá alespoň *n* časy.|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|Porovná *n* k *m* časy.|  
  
 Množství `n` a `m` jsou konstanty typu integer. Obvykle jsou greedy; kvantifikátory modul regulárních výrazů odpovídá počtu výskytů určité vzory nejvíce způsobují. Přidávání `?` znak kvantifikátor díky opožděné; způsobí, že modul regulárních výrazů odpovídá co nejméně opakování nejvíce. Úplný popis rozdíl mezi metodou greedy a opožděných kvantifikátory, najdete v části [vlastnost Greedy a líné kvantifikátory](#Greedy) dále v tomto tématu.  
  
> [!IMPORTANT]
>  Kvantifikátory vnoření (například jako vzor regulárního výrazu `(a*)*` dělá) můžete zvýšit počet porovnání, která musí provést modul regulárních výrazů, jako exponenciální funkce počtu znaků ve vstupním řetězci. Další informace o tomto chování a jeho řešení najdete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kvantifikátory v regulárních výrazů  
 Kvantifikátory v regulárních výrazech .NET podporované v následujících částech.  
  
> [!NOTE]
>  Pokud *, +,?, {, a} vyskytují znaky ve vzorku regulárního výrazu, modul regulárních výrazů je interpretuje jako kvantifikátory nebo konstrukce kvantifikátoru část jsou součástí [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). K interpretaci jako literální znaky mimo třídu znaků, musíte před tím, že před zpětným lomítkem. Například řetězec `\*` v regulárním výrazu vzorek je interpretován jako literální hvězdičku ("\*") znaků.  
  
### <a name="match-zero-or-more-times-"></a>Odpovídá nule nebo víckrát: *  
 `*` Kvantifikátor Porovná předchozí prvek nulakrát nebo vícekrát. Je ekvivalentní `{0,}` kvantifikátor. `*` je greedy kvantifikátor, jehož ekvivalent opožděné je `*?`.  
  
 Následující příklad ukazuje tento regulární výraz. Devět číslic ve vstupním řetězci, pět shoduje se vzorem a čtyři (`95`, `929`, `9129`, a `9919`) nepodporují.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`91*`|Odpovídá "9" následované nula nebo více znaků "1".|  
|`9*`|Porovná žádný nebo více znaků "9".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-one-or-more-times-"></a>Shodovat s jednou nebo vícekrát: +  
 `+` Kvantifikátor Porovná předchozí prvek jednou nebo vícekrát. Je ekvivalentní `{1,}`. `+` je greedy kvantifikátor, jehož ekvivalent opožděné je `+?`.  
  
 Například regulární výraz `\ban+\w*?\b` pokusí se porovnat celá slova, která začínají písmenem `a` za nímž následuje jedna nebo víc instancí písmeno `n`. Následující příklad ukazuje tento regulární výraz. Odpovídá regulárnímu výrazu slova `an`, `annual`, `announcement`, a `antique`a vyvolá chybu správně tak, aby odpovídaly `autumn` a `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an+`|Shoda se znakem "a" následované jeden nebo více znaků "n".|  
|`\w*?`|Odpovídá znaku slova nulakrát nebo vícekrát, ale s počtem opakování nejvíce.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-zero-or-one-time-"></a>Odpovídá nule nebo jednou:?  
 `?` Kvantifikátor odpovídá předchozí element nula nebo čas. Je ekvivalentní `{0,1}`. `?` je greedy kvantifikátor, jehož ekvivalent opožděné je `??`.  
  
 Například regulární výraz `\ban?\b` pokusí se porovnat celá slova, která začínají písmenem `a` následované žádnou nebo jednou instancí písmeno `n`. Jinými slovy, pokusí se vyhledat slova `a` a `an`. Následující příklad ukazuje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an?`|Shoda se znakem "a" následované žádnou nebo jednu znak "n".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-exactly-n-times-n"></a>Odpovídá přesně n vícekrát: {n}  
 `{` *n* `}` kvantifikátor Porovná předcházející prvek přesně *n* krát, kde *n* je libovolné celé číslo. `{`*n* `}` je greedy kvantifikátor, jehož ekvivalent opožděné je `{` *n*`}?`.  
  
 Například regulární výraz `\b\d+\,\d{3}\b` pokusí se porovnat hranici slova, za nímž následuje jedna nebo více desítkových číslic následovanou třemi desítkovými číslicemi, za nímž následuje hranice slova. Následující příklad ukazuje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\,`|Porovná znak čárky.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-at-least-n-times-n"></a>Odpovídá alespoň n vícekrát: {n,}  
 `{` *n* `,}` kvantifikátor Porovná předchozí prvek nejméně *n* krát, kde *n* je libovolné celé číslo. `{`*n* `,}` je greedy kvantifikátor, jehož ekvivalent opožděné je `{` *n*`,}?`.  
  
 Například regulární výraz `\b\d{2,}\b\D+` pokusí se porovnat hranici slova a alespoň dvěma číslicemi za nímž následuje hranice slova a nečíslicovému znaku. Následující příklad ukazuje tento regulární výraz. Nezdaří regulárního výrazu tak, aby odpovídaly frázi `"7 days"` protože obsahuje pouze jednu desítkovou číslici, ale úspěšně odpovídá věty `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d{2,}`|Odpovídá alespoň dvě desetinné číslice.|  
|`\b`|Porovná hranici slova.|  
|`\D+`|Odpovídá alespoň jedné nedesetinné číslo.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Shoda mezi časy n a m: {n, m}  
 `{` *n*`,`*m* `}` kvantifikátor Porovná předchozí prvek nejméně *n* krát, ale ne víc než *m*  krát, kde *n* a *m* jsou celá čísla. `{`*n*`,`*m* `}` je greedy kvantifikátor, jehož ekvivalent opožděné je `{` *n*`,`*m* `}?`.  
  
 V následujícím příkladu, regulární výraz `(00\s){2,4}` pokusí shodovat se mezi dvěma až čtyřmi výskyty dvou nul, za nímž následuje mezera. Všimněte si, že poslední část vstupní řetězec obsahuje tento model pětkrát spíše než maximálně čtyři. Ale jenom první část tento dílčí řetězec (až místa a pátý pár nuly) odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Odpovídá nula nebo vícekrát (opožděné shoda): *?  
 `*?` Kvantifikátor odpovídá předchozí prvek nulakrát nebo vícekrát, ale s počtem opakování nejvíce. Je opožděné protějškem greedy kvantifikátor `*`.  
  
 V následujícím příkladu, regulární výraz `\b\w*?oo\w*?\b` odpovídá všem slovům, které obsahují řetězec `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\w*?`|Porovná žádný nebo více znaků slova, ale co nejméně znakům nejvíce.|  
|`oo`|Odpovídá řetězci "zálohy".|  
|`\w*?`|Porovná žádný nebo více znaků slova, ale co nejméně znakům nejvíce.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Shodovat s jednou nebo vícekrát (opožděné shoda): +?  
 `+?` Kvantifikátor Porovná předchozí prvek jednou nebo vícekrát, ale s počtem opakování nejvíce. Je opožděné protějškem greedy kvantifikátor `+`.  
  
 Například regulární výraz `\b\w+?\b` odpovídá jeden nebo více znaků, které jsou odděleny hranicích slov. Následující příklad ukazuje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Odpovídá nule nebo jednou (opožděné shoda):??  
 `??` Kvantifikátor odpovídá předchozí prvek nula nebo jednou, ale s počtem opakování nejvíce. Je opožděné protějškem greedy kvantifikátor `?`.  
  
 Například regulární výraz `^\s*(System.)??Console.Write(Line)??\(??` pokusí porovnat řetězce "Console.Write" nebo "Console.WriteLine". Řetězec může obsahovat také "Systém". předtím, než "Console" a to může být následován levou závorku. Řetězec musí být na začátku řádku, i když může být uvozen symbolem mezery. Následující příklad ukazuje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídá začátku vstupního datového proudu.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(System.)??`|Porovná žádný nebo jeden výskyt řetězce "Systém".|  
|`Console.Write`|Odpovídá řetězci "Console.Write".|  
|`(Line)??`|Porovná žádný nebo jeden výskyt řetězce "Řádek".|  
|`\(??`|Porovná žádný nebo jeden výskyt levé závorky.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Odpovídá přesně n časy (opožděné shoda): {n}?  
 `{` *n* `}?` kvantifikátor Porovná předcházející prvek přesně `n` krát, kde *n* je libovolné celé číslo. Je opožděné protějškem greedy kvantifikátor `{` *n*`}+`.  
  
 V následujícím příkladu, regulární výraz `\b(\w{3,}?\.){2}?\w{3,}?\b` slouží k identifikaci adresu webu. Všimněte si, že odpovídá "www.microsoft.com" a "msdn.microsoft.com", ale neodpovídá "mywebsite" nebo "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(\w{3,}?\.)`|Odpovídá alespoň 3 znaky slov, ale co nejméně znakům nejvíce, za nímž následuje tečky nebo znak tečky. Toto je první zachytávající skupina.|  
|`(\w{3,}?\.){2}?`|Porovná vzor v první skupině dvakrát, ale co nejmenším možným počtem opakování.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Odpovídaly alespoň n (opožděné shoda): {n,}?  
 `{` *n* `,}?` kvantifikátor Porovná předchozí prvek nejméně `n` krát, kde *n* libovolné celé číslo, je ale několik krát. Je opožděné protějškem greedy kvantifikátor `{` *n*`,}`.  
  
 Podívejte se na příklad pro `{` *n* `}?` kvantifikátor v předchozí části pro ilustraci. Regulární výraz v tomto příkladu používá `{` *n* `,}` kvantifikátor tak, aby odpovídaly řetězec, který obsahuje alespoň tři znaky, následovaných tečkou.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Nalezena shoda mezi n a m časy (opožděné shoda): {n, m}?  
 `{` *n*`,`*m* `}?` kvantifikátor Porovná předcházející prvek mezi `n` a `m` krát, kde *n* a *m* jsou celá čísla, ale s počtem opakování nejvíce. Je opožděné protějškem greedy kvantifikátor `{` *n*`,`*m*`}`.  
  
 V následujícím příkladu, regulární výraz `\b[A-Z](\w*\s+){1,10}?[.!?]` odpovídá věty obsahující mezi slovy jednu až 10. Odpovídá všem věty ve vstupním řetězci s výjimkou jedné věty obsahující slova 18.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Porovná znak velkého písmene od A až Z.|  
|`(\w*\s+)`|Porovná žádný nebo více znaků slova, za nímž následuje jedna nebo více prázdných znaků. Toto je první skupiny zachycení.|  
|`{1,10}?`|Porovná předchozí vzor mezi 1 a 10, ale co nejmenším možným počtem opakování.|  
|`[.!?]`|Odpovídat jedné z interpunkčních znaků ".","!", nebo "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Greedy a opožděných kvantifikátory  
 Počet kvantifikátory mít dvě verze:  
  
-   Greedy verze.  
  
     Greedy kvantifikátor pokusí porovnat prvek sady jako tolikrát, kolikrát to bude možné.  
  
-   Bez metody greedy (nebo opožděné) verze.  
  
     Bez metody greedy kvantifikátor pokusí porovnat prvek nejmenším počtem je to možné. Greedy kvantifikátor do opožděným kvantifikátorem můžete zapnout tak, že jednoduše přidáte `?`.  
  
 Vezměte v úvahu jednoduché regulární výraz, který se má extrahovat poslední čtyři číslice z řetězce čísel, například číslo kreditní karty. Verzi regulárního výrazu, který používá `*` je greedy kvantifikátor `\b.*([0-9]{4})\b`. Ale pokud řetězec obsahuje dvě čísla, tento regulární výraz odpovídá poslední čtyři číslice druhé číslo, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Tak, aby odpovídaly první číslo, protože se nezdaří regulárního výrazu `*` kvantifikátor pokusí shodovat se předchozí prvek tolikrát, kolikrát je možné celý řetězec, a proto najde shodu na konci řetězce.  
  
 Toto není požadované chování. Místo toho můžete použít `*?`opožděným kvantifikátorem pro extrahování číslic z obou čísel, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Ve většině případů regulárních výrazů s metodou greedy a opožděných kvantifikátory vrátí stejné shody. Nejčastěji vrátí odlišné výsledky při použití se zástupným znakem (`.`) metaznak, která odpovídá libovolnému znaku.  
  
## <a name="quantifiers-and-empty-matches"></a>Kvantifikátory a prázdné shody  
 Kvantifikátory `*`, `+`, a `{` *n*`,`*m* `}` a jejich protějšky opožděné nikdy opakovat za prázdný shodovat, kdy minimum počet zachycení nebyl nalezen. Toto pravidlo zabrání kvantifikátory zadat nekonečné smyčky, prázdná dílčí výraz odpovídá při maximální počet možných skupinové zachytávání je nekonečné nebo téměř nekonečné.  
  
 Například následující kód ukazuje výsledek volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metoda se vzorem regulárního výrazu `(a?)*`, který odpovídá žádnou nebo jednou "a" znaku nula nebo vícekrát. Všimněte si, že jediné zachytávající skupiny zachytí každou "a" jako i <xref:System.String.Empty?displayProperty=nameWithType>, ale, že není nalezena žádná druhá prázdný shoda, protože první shoda prázdný způsobí, že kvantifikátor opakující se zastaví.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Zobrazíte praktické rozdíl mezi zachytávající skupinu, která definuje minimální a maximální počet zachycení a ten, který definuje pevný počet zachycení, vezměte v úvahu vzory regulárních výrazů `(a\1|(?(1)\1)){0,2}` a `(a\1|(?(1)\1)){2}`. Obě regulárních výrazů se skládají z jednoho zachytávající skupinu, která je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(a\1`|Buď shody "a", včetně hodnoty první zachycené skupiny...|  
|<code>&#124;(?(1)</code>|… nebo můžete otestovat, jestli je definována první zachycenou skupinou. (Všimněte si, že `(?(1)` konstrukce nedefinuje zachytávající skupina.)|  
|`\1))`|Pokud existuje první zachycenou skupinou shodovat jeho hodnota. Pokud skupina neexistuje, bude odpovídat skupině <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 První regulárních výrazů pokusí shodovat se tento vzor mezi 0 a dvěma časy; druhá s názvem přesně dvakrát. Protože první vzor dosáhne jeho minimální počet zachycení s jeho prvního zachycení <xref:System.String.Empty?displayProperty=nameWithType>, nikdy opakuje pokus tak, aby odpovídaly `a\1`; `{0,2}` kvantifikátor umožňuje pouze prázdné shody v poslední iteraci. Naproti tomu druhý regulární výraz odpovídat "a" protože je vyhodnocen jako `a\1` podruhé; minimální počet iterací, 2, vynutí modulu opakovat po prázdný shoda.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
