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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160011"
---
# <a name="quantifiers-in-regular-expressions"></a>Kvantifikátory v regulárních výrazech
Kvantifikátory určují, kolik instancí znaku, skupiny nebo třídy znaků musí být přítomno ve vstupu pro nalezenou shodu.  V následující tabulce jsou uvedeny kvantifikátory podporované rozhraním .NET.  
  
|Chamtivý kvantifikátor|Líný kvantifikátor|Popis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Zápas nula nebo vícekrát.|  
|`+`|`+?`|Zápas jednou nebo vícekrát.|  
|`?`|`??`|Zápas nula nebo jednou.|  
|`{`*n*`}`|`{`*n*`}?`|Zápas přesně *n* krát.|  
|`{`*n*`,}`|`{`*n*`,}?`|Zápas alespoň *n* krát.|  
|`{`*n* `,` *m*`}`|`{`*n* `,` *m*`}?`|Shoda od *n* do *m* krát.|  
  
 Množství `n` a `m` jsou celé konstanty. Obvykle jsou kvantifikátory chamtivé; způsobí, že modul regulárních výrazů odpovídá co největšímu počtu výskytů určitých vzorů. Připojení znaku `?` k vkusovateli způsobí, že je líný; způsobí, že modul regulárních výrazů odpovídá co nejmenšímu výskytu. Úplný popis rozdílu mezi chamtivými a opožděnými kvantifikátory naleznete v části [Greedy a Lazy Quantifiers](#Greedy) dále v tomto tématu.  
  
> [!IMPORTANT]
> Vnoření kvantifikátorů (například `(a*)*` jako vzor regulárního výrazu) může zvýšit počet porovnání, které musí modul regulárních výrazů provést, jako exponenciální funkce počtu znaků ve vstupním řetězci. Další informace o tomto chování a jeho řešení naleznete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kvantifikátory regulárního výrazu  
 V následujících částech jsou uvedeny kvantifikátory podporované regulárními výrazy .NET.  
  
> [!NOTE]
> Pokud jsou ve vzorku regulárních výrazů zjištěny znaky *, +, ?, {a } , modul regulárních výrazů je interpretuje jako kvantifikátory nebo část kvantifikátorů, pokud nejsou zahrnuty do [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Chcete-li interpretovat tyto jako literál znaky mimo třídu znaků, je nutné uniknout jim před nimi s zpětné lomítko. Například řetězec `\*` ve vzoru regulárního výrazu je interpretován jako\*literál hvězdička (" ") znak.  
  
### <a name="match-zero-or-more-times-"></a>Shoda nula nebo vícekrát: *  
 Kvantifikátor `*` odpovídá předchozí prvek nula nebo vícekrát. Je ekvivalentní kvantifikátoru. `{0,}` `*`je nenasytný kvantifikátor, jehož opožděný ekvivalent je `*?`.  
  
 Následující příklad ilustruje tento regulární výraz. Z devíti číslic ve vstupním řetězci pět odpovídá`95` `929`vzoru `9219`a `9919`čtyři ( , , , a ) ne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`91*`|Porovná "9" následované nulou nebo více znaky "1".|  
|`9*`|Porovná nula nebo více znaků "9".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-one-or-more-times-"></a>Shoda jednou nebo vícekrát: +  
 Kvantifikátor `+` odpovídá předchozí prvek jednou nebo vícekrát. Je ekvivalentní `{1,}`. `+`je nenasytný kvantifikátor, jehož opožděný ekvivalent je `+?`.  
  
 Regulární výraz `\ban+\w*?\b` se například pokusí porovnat celá `a` slova začínající písmenem následovaným `n`jednou nebo více instancemi písmene . Následující příklad ilustruje tento regulární výraz. Regulární výraz `an`odpovídá `annual` `announcement`slovům `antique`, , a `autumn` `all`, a správně se neshoduje a .  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an+`|Porovná "a" následované jedním nebo více znaky "n".|  
|`\w*?`|Porovná znak slova nula nebo vícekrát, ale co nejméněkrát.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-zero-or-one-time-"></a>Zápas nula nebo jeden čas: ?  
 Kvantifikátor `?` odpovídá předchozímu prvku nula nebo jednou. Je ekvivalentní `{0,1}`. `?`je nenasytný kvantifikátor, jehož opožděný ekvivalent je `??`.  
  
 Regulární výraz `\ban?\b` se například pokusí porovnat celá `a` slova začínající písmenem následovaným `n`nulou nebo jednou instancí písmene . Jinými slovy, snaží se `a` odpovídat slova a `an`. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an?`|Porovná "a" následované nulou nebo jedním znakem "n".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-exactly-n-times-n"></a>Přesně n Časy: {n}  
 N `{`kvantifikátor *n* `}` odpovídá předchozí prvek přesně *n* krát, kde *n* je libovolné celé číslo. `{`*n* `}` je chamtivý kvantifikátor, jehož opožděný ekvivalent je `{` *n*`}?`.  
  
 Regulární výraz `\b\d+\,\d{3}\b` se například pokusí porovnat hranici slova následovanou jednou nebo více desetinnými číslicemi následovanými třemi desetinnými číslicemi následovanými hranicí slova. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\,`|Porovná znak čárky.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-at-least-n-times-n"></a>Shoda alespoň n krát: {n,}  
 N `{`kvantifikátor *n* `,}` odpovídá předchozí prvek alespoň *n* krát, kde *n* je libovolné celé číslo. `{`*n* `,}` je chamtivý kvantifikátor, jehož opožděný ekvivalent je `{` *n*`,}?`.  
  
 Regulární výraz `\b\d{2,}\b\D+` se například pokusí porovnat hranici slova následovanou alespoň dvěma číslicemi následovanými hranicí slova a nečíslicovým znakem. Následující příklad ilustruje tento regulární výraz. Regulární výraz neodpovídá `"7 days"` frázi, protože obsahuje pouze jednu desetinnou `"10 weeks and 300 years"`číslici, ale úspěšně odpovídá frázím .  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d{2,}`|Porovná alespoň dvě desetinná místa.|  
|`\b`|Porovná hranici slova.|  
|`\D+`|Porovná alespoň jednu nedesítkovou číslici.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Shoda mezi n a m Časy: {n,m}  
 `{` *n*N`,`*m* `}` m kvantifikátor odpovídá předchozí prvek alespoň *n* krát, ale ne více než *m* krát, kde *n* a *m* jsou celá čísla. `{`*n*`,`*m* `}` je chamtivý kvantifikátor, jehož opožděný ekvivalent `{`je *n*`,`*m*`}?`.  
  
 V následujícím příkladu se `(00\s){2,4}` regulární výraz pokusí porovnat dva až čtyři výskyty dvou nulových číslic následovaných mezerou. Všimněte si, že konečná část vstupní řetězec obsahuje tento vzor pětkrát, nikoli maximálně čtyři. Pouze počáteční část tohoto podřetězce (až do mezery a pátý pár nul) však odpovídá vzoru regulárního výrazu.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Shoda nula nebo více krát (Lazy Match): *?  
 Kvantifikátor `*?` odpovídá předchozí prvek nula nebo vícekrát, ale co nejméně krát, jak je to možné. Je to líný protějšek chamtivý kvantifikátor `*`.  
  
 V následujícím příkladu regulární výraz `\b\w*?oo\w*?\b` odpovídá `oo`všem slovům, která obsahují řetězec .  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\w*?`|Porovná nulové nebo více znaků slova, ale co nejméně znaků.|  
|`oo`|Porovnejte řetězec "oo".|  
|`\w*?`|Porovná nulové nebo více znaků slova, ale co nejméně znaků.|  
|`\b`|Konec na hranici slova.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Shoda jeden nebo více krát (Lazy Match): +?  
 Kvantifikátor `+?` odpovídá předchozí prvek jednou nebo vícekrát, ale co nejméně krát. Je to líný protějšek chamtivý kvantifikátor `+`.  
  
 Regulární výraz `\b\w+?\b` například odpovídá jednomu nebo více znakům odděleným hranicemi slov. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Zápas Nula nebo jeden čas (Lazy Match): ??  
 Kvantifikátor `??` odpovídá předchozí prvek nula nebo jednou, ale co nejméně krát, jak je to možné. Je to líný protějšek chamtivý kvantifikátor `?`.  
  
 Například regulární `^\s*(System.)??Console.Write(Line)??\(??` výraz se pokusí odpovídat řetězce "Console.Write" nebo "Console.WriteLine". Řetězec může také obsahovat "Systém". před "Console", a to může následovat otevření závorky. Řetězec musí být na začátku řádku, i když mu může předcházet prázdné místo. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Porovná začátek vstupního datového proudu.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(System.)??`|Porovná nula nebo jeden výskyt řetězce "Systém".|  
|`Console.Write`|Porovná řetězec "Console.Write".|  
|`(Line)??`|Porovná nula nebo jeden výskyt řetězce "Line".|  
|`\(??`|Porovná nulový nebo jeden výskyt počáteční závorky.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Přesně n Časy (Opožděná shoda): {n}?  
 N `{`kvantifikátor *n* `}?` odpovídá `n` předchozí prvek přesně časy, kde *n* je libovolné celé číslo. Je to líný protějšek chamtivý kvantifikátor `{` *n*`}`.  
  
 V následujícím příkladu se `\b(\w{3,}?\.){2}?\w{3,}?\b` regulární výraz používá k identifikaci adresy webu. Všimněte si, že odpovídá "www.microsoft.com" a "msdn.microsoft.com", ale neodpovídá "mywebsite" nebo "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(\w{3,}?\.)`|Porovná alespoň 3 znaky slova, ale co nejméně znaků, následované tečkou nebo tečkou. Toto je první zachytávající skupina.|  
|`(\w{3,}?\.){2}?`|Porovná vzor v první skupině dvakrát, ale co nejméněkrát.|  
|`\b`|Ukončite shodu na hranici slova.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Shoda alespoň n krát (Opožděná shoda): {n,}?  
 N `{`kvantifikátor *n* `,}?` odpovídá předchozí `n` prvek alespoň časy, kde *n* je libovolné celé číslo, ale co nejméně krát. Je to líný protějšek chamtivý kvantifikátor `{` *n*`,}`.  
  
 Viz příklad `{` *pro n* `}?` kvantifikátor v předchozí části pro ilustraci. Regulární výraz v `{`tomto příkladu používá *n* `,}` kvantifikátor tak, aby odpovídal řetězci, který má alespoň tři znaky následované tečkou.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Shoda mezi n a m časy (opožděná shoda): {n,m}?  
 `{` *N*`}?` `n` `m` *m* *n* *m* m kvantifikátor odpovídá předchozí prvek mezi a časy, kde n a m jsou celá čísla, ale co nejméně krát.`,` Je to líný `{`protějšek chamtivý kvantifikátor *n*`,`*m*`}`.  
  
 V následujícím příkladu regulární výraz `\b[A-Z](\w*?\s*?){1,10}[.!?]` odpovídá větám, které obsahují jedno až deset slov. Odpovídá všem větám ve vstupním řetězci s výjimkou jedné věty, která obsahuje 18 slov.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Porovná velký znak od A do Z.|  
|`(\w*?\s*?)`|Porovná nulové nebo více znaků slova následovaných jedním nebo více znaky prázdného místa, ale co nejméně krát. Toto je první skupina zachycení.|  
|`{1,10}`|Porovná předchozí vzorek mezi 1 a 10 krát.|  
|`[.!?]`|Porovná některý z interpunkčních znaků ".", "!"nebo "?".|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a>Chamtivý a Líný Kvantifikátory  
 Počet kvantifikátorů má dvě verze:  
  
- Chamtivá verze.  
  
     Chamtivý kvantifikátor se pokusí porovnat prvek tolikrát, kolikrát je to možné.  
  
- Nehladová (nebo líná) verze.  
  
     Nechamantigrátka se pokusí porovnat prvek co nejméně krát. Můžete proměnit chamtivý kvantifikátor do `?`líný kvantifikátor pouhým přidáním .  
  
 Zvažte jednoduchý regulární výraz, který je určen k extrahování posledních čtyř číslic z řetězce čísel, jako je číslo platební karty. Verze regulárního výrazu, která používá `*` kvantifikátor hladový je `\b.*([0-9]{4})\b`. Pokud však řetězec obsahuje dvě čísla, bude tento regulární výraz shodovat pouze s posledními čtyřmi číslicemi druhého čísla, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Regulární výraz se neshoduje `*` s prvním číslem, protože kvantifikátor se pokusí porovnat předchozí prvek co nejvíce v celém řetězci, a proto najde jeho shodu na konci řetězce.  
  
 Toto není požadované chování. Místo toho můžete `*?`použít opožděný kvantifikátor extrahovat číslice z obou čísel, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Ve většině případů regulární výrazy s nenasytný a opožděné kvantifikátory vrátit stejné shody. Nejčastěji vracejí různé výsledky při použití s metaznakem se zástupným znakem ,`.`který odpovídá libovolnému znaku.  
  
## <a name="quantifiers-and-empty-matches"></a>Kvantifikátory a prázdné shody  
 `*`Kvantifikátory `+`, `{`a *n*`,`*m* `}` a jejich líné protějšky se nikdy neopakují po prázdné shodě, když byl nalezen minimální počet zachycení. Toto pravidlo zabraňuje kvantifikátory od zadání nekonečné smyčky na prázdné shody dílčívýraz, pokud maximální počet možných skupin zachycení je nekonečný nebo blízko nekonečné.  
  
 Například následující kód zobrazuje výsledek volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody se vzorem `(a?)*`regulárního výrazu , který odpovídá nule nebo jednomu znaku "a" nula nebo vícekrát. Všimněte si, že jedna zachytávající skupina <xref:System.String.Empty?displayProperty=nameWithType>zachycuje každý "a" stejně jako , ale že neexistuje žádná druhá prázdná shoda, protože první prázdná shoda způsobí, že kvantifikátor přestane opakovat.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Chcete-li zobrazit praktický rozdíl mezi zachytávající skupinou, která definuje minimální a maximální počet zachycení, a skupinou, která definuje pevný počet zachycení, zvažte vzory regulárních výrazů `(a\1|(?(1)\1)){0,2}` a `(a\1|(?(1)\1)){2}`. Oba regulární výrazy se skládají z jedné zachytávající skupiny, která je definována tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(a\1`|Buď zápas "a" spolu s hodnotou první zachycené skupiny ...|  
|<code>&#124;(?(1)</code>|… nebo otestujte, zda byla definována první zachycená skupina. (Všimněte `(?(1)` si, že konstrukce nedefinuje zachytávající skupinu.)|  
|`\1))`|Pokud existuje první zachycená skupina, shodovat její hodnotu. Pokud skupina neexistuje, bude se <xref:System.String.Empty?displayProperty=nameWithType>skupina shodovat .|  
  
 První regulární výraz se pokusí porovnat tento vzor mezi nulou a dvakrát; druhý, přesně dvakrát. Vzhledem k tomu, že první vzor dosáhne svého <xref:System.String.Empty?displayProperty=nameWithType>minimálního počtu zachycení s `a\1`jeho první zachycení , nikdy se opakuje, aby se pokusili zápas ; kvantifikátor `{0,2}` umožňuje pouze prázdné shody v poslední iteraci. Naproti tomu druhý regulární výraz odpovídá "a", protože vyhodnocuje `a\1` podruhé; minimální počet iterací, 2, vynutí, aby se motor opakoval po prázdné shodě.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
