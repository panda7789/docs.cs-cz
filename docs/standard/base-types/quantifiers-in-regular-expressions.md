---
title: "Kvantifikátory v regulárních výrazech"
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
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db1c3af1bb3ad207278eed64a8fb2ef8ed6dc465
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="quantifiers-in-regular-expressions"></a>Kvantifikátory v regulárních výrazech
Kvantifikátory zadejte, kolik instancí znaku, skupiny nebo třída znak musí být ve vstupu pro shodu, která se má najít.  Následující tabulka uvádí kvantifikátory nepodporuje rozhraní .NET.  
  
|Typu greedy kvantifikátoru|Opožděné kvantifikátoru|Popis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Odpovídat počtu nula či více krát.|  
|`+`|`+?`|Odpovídat jeden či více krát.|  
|`?`|`??`|Shoda jednou nebo.|  
|`{` *n* `}`|`{` *n* `}?`|Přesně shodují  *n*  časy.|  
|`{` *n* `,}`|`{` *n* `,}?`|Odpovídají alespoň  *n*  časy.|  
|`{` *n*  `,` *m*`}`|`{` *n*  `,` *m*`}?`|Odpovídat z  *n*  k *m* časy.|  
  
 Množství `n` a `m` jsou celočíselné konstanty. Obvykle jsou kvantifikátory typu greedy; způsobí modul regulárních výrazů tak, aby odpovídaly tolik výskyty určité vzory míře. Připojení `?` znak, který má kvantifikátor umožňuje opožděné; způsobí, že modul regulárních výrazů tak, aby odpovídaly počet výskytů míře. Úplný popis rozdíl mezi typu greedy a opožděné kvantifikátory, najdete v části [Hladové a líné kvantifikátory](#Greedy) dál v tomto tématu.  
  
> [!IMPORTANT]
>  Kvantifikátory vnoření (například jako regulární výraz `(a*)*` nemá) můžete zvýšit počet porovnání, které modul regulárních výrazů se musí provádět jako exponenciální funkce se počet znaků ve vstupním řetězci. Další informace o toto chování a jeho řešení najdete v tématu [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kvantifikátory v regulárních výrazů  
 Následující části uvádějí kvantifikátory podporované regulární výrazy rozhraní .NET.  
  
> [!NOTE]
>  Pokud *, +,?, {, a} vyskytují v vzor regulárního výrazu znaky, modul regulárních výrazů je interpretuje jako kvantifikátory nebo část konstrukce kvantifikátoru jsou součástí [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Interpretovat jako literály mimo třídu znaků, musíte použít řídící tak, že před jejich zpětným lomítkem. Například řetězec `\*` v regulárním výrazu vzor interpretována jako literál hvězdičky ("\*") znaků.  
  
### <a name="match-zero-or-more-times-"></a>Odpovídat nula nebo vícekrát: *  
 `*` Kvantifikátoru porovnává předchozí prvek nula či více krát. Ta je ekvivalentní `{0,}` kvantifikátoru. `*`je typu greedy kvantifikátor, jehož opožděný ekvivalent je `*?`.  
  
 Následující příklad ilustruje tento regulární výraz. Devět číslic ve vstupním řetězci, pět odpovídají vzoru a čtyřmi (`95`, `929`, `9129`, a `9919`) nepodporují.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`91*`|Porovná "9" následované nula nebo více znaky "1".|  
|`9*`|Odpovídat počtu nula či více znaků "9".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-one-or-more-times-"></a>Odpovídat jeden či více krát: +  
 `+` Kvantifikátoru porovnává předchozí prvek jeden či více krát. Ta je ekvivalentní `{1,}`. `+`je typu greedy kvantifikátor, jehož opožděný ekvivalent je `+?`.  
  
 Například regulární výraz `\ban+\w*?\b` pokusí Hledat celá slova začínající písmenem `a` následuje jeden nebo více instancí písmeno `n`. Následující příklad ilustruje tento regulární výraz. Odpovídá regulárnímu výrazu slova `an`, `annual`, `announcement`, a `antique`a správně selže tak, aby odpovídaly `autumn` a `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an+`|Porovná znak "a" následuje jeden nebo více znaky "n".|  
|`\w*?`|Porovná znak slova nula nebo více vícekrát, ale co nejméně krát.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-zero-or-one-time-"></a>Odpovídat nula nebo jednou:?  
 `?` Kvantifikátoru odpovídá předchozí prvek nula nebo jedna jednou. Ta je ekvivalentní `{0,1}`. `?`je typu greedy kvantifikátor, jehož opožděný ekvivalent je `??`.  
  
 Například regulární výraz `\ban?\b` pokusí Hledat celá slova začínající písmenem `a` následuje žádnou nebo jednu instanci písmeno `n`. Jinými slovy, pokusí se vyhledat slova `a` a `an`. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`an?`|Porovná znak "a" následuje nula nebo jeden znak "n".|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-exactly-n-times-n"></a>Odpovídat přesně n krát: {n}  
 `{`  *n*  `}` Kvantifikátoru přesně odpovídá předchozí prvek  *n*  krát, kde  *n* je libovolné celé číslo. `{`*n*`}`je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `}?`.  
  
 Například regulární výraz `\b\d+\,\d{3}\b` pokusí porovnat hranici slova, za nímž následuje jeden nebo více desetinných číslic, za nímž následuje tři desetinných číslic, za nímž následuje hranici slova. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\,`|Porovná znak čárky.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`\b`|Skončí na hranici slova.|  
  
### <a name="match-at-least-n-times-n"></a>Odpovídají alespoň n krát: {n,}  
 `{`  *n*  `,}` Kvantifikátoru porovnává předchozí prvek alespoň  *n*  krát, kde  *n* je libovolné celé číslo. `{`*n*`,}`je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `}?`.  
  
 Například regulární výraz `\b\d{2,}\b\D+` pokusí porovnat hranici slova a alespoň dvě číslice následovaný hranici slova a nečíselným znakem. Následující příklad ilustruje tento regulární výraz. Regulární výraz selže tak, aby odpovídaly fráze `"7 days"` vzhledem k tomu, že obsahuje pouze jednu číslici desítkové soustavy, ale úspěšně porovná větu `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\d{2,}`|Odpovídat aspoň dva desetinných míst.|  
|`\b`|Porovná hranici slova.|  
|`\D+`|Odpovídat nejméně jednu číslici desetinné číslo.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Nalezena shoda mezi časy n a m: {n, m}  
 `{`  *n*  `,` *m* `}` kvantifikátoru porovnává předchozí prvek alespoň  *n*  dobu, ale ne víc než *m* krát, kde  *n*  a *m* jsou celá čísla. `{`*n*`,`*m* `}` je typu greedy kvantifikátor, jehož opožděný ekvivalent je `{`  *n*  `,` *m*`}?`.  
  
 V následujícím příkladu, regulární výraz `(00\s){2,4}` pokusí porovnat mezi dvěma a čtyřmi výskyty dvou číslic nula následované mezerou. Všimněte si, že závěrečná část vstupní řetězec obsahuje tento vzor pětkrát spíše než maximální počet čtyři. Ale pouze počáteční část tohoto podřetězce (až prostor a pátý pár nul) odpovídá regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Odpovídat nula nebo více krát (opožděné porovnávání): *?  
 `*?` Kvantifikátoru porovnává předchozí prvek nula nebo více vícekrát, ale co nejméně krát. Je opožděné protějškem typu greedy kvantifikátoru `*`.  
  
 V následujícím příkladu, regulární výraz `\b\w*?oo\w*?\b` odpovídá slova, která obsahují řetězec `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\w*?`|Porovná nula nebo více znaků slova, ale jako několika prvních znaků nejdříve.|  
|`oo`|Shoda s řetězcem "ú".|  
|`\w*?`|Porovná nula nebo více znaků slova, ale jako několika prvních znaků nejdříve.|  
|`\b`|Končí na hranici slova.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Shodovat s jednou nebo vícekrát (opožděné porovnávání): +?  
 `+?` Kvantifikátoru porovnává předchozí prvek jeden nebo více vícekrát, ale co nejméně krát. Je opožděné protějškem typu greedy kvantifikátoru `+`.  
  
 Například regulární výraz `\b\w+?\b` odpovídá jeden nebo více znaků, které jsou odděleny hranice aplikace word. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Odpovídat nula nebo jednou (opožděné porovnávání):??  
 `??` Kvantifikátoru odpovídá předchozí prvek nula nebo jedna jednou, ale nejméně krát. Je opožděné protějškem typu greedy kvantifikátoru `?`.  
  
 Například regulární výraz `^\s*(System.)??Console.Write(Line)??\(??` se pokusí o porovnání řetězce "Console.Write" nebo "Console.WriteLine". Řetězec může také obsahovat "Systém". před "Konzole" ale může následovat levé závorky. Řetězec musí být na začátku řádku, i když můžete předcházet mezer. Následující příklad ilustruje tento regulární výraz.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídat začátek vstupního datového proudu.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(System.)??`|Porovná nula nebo jeden výskyt řetězec "Systém.".|  
|`Console.Write`|Hledat řetězec "Console.Write".|  
|`(Line)??`|Porovná nula nebo jeden výskyt řetězec "Řádek".|  
|`\(??`|Porovná nula nebo jeden výskyt levé závorky.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Odpovídat přesně n krát (opožděné porovnávání): {n}?  
 `{`  *n*  `}?` Kvantifikátoru přesně odpovídá předchozí prvek `n` krát, kde  *n*  je libovolné celé číslo. Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `}+`.  
  
 V následujícím příkladu, regulární výraz `\b(\w{3,}?\.){2}?\w{3,}?\b` slouží k identifikaci adresu webu. Všimněte si, že odpovídá "www.microsoft.com" a "msdn.microsoft.com", ale neodpovídá "mywebsite" nebo "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(\w{3,}?\.)`|Porovná alespoň 3 znaky word, ale jako několika prvních znaků nejdříve, za nímž následuje tečky nebo tečka – znak. Toto je první zachytávající skupina.|  
|`(\w{3,}?\.){2}?`|Shodují se vzorem v první skupinu dvakrát, ale co nejméně krát.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Odpovídají alespoň n krát (opožděné porovnávání): {n,}?  
 `{`  *n*  `,}?` Kvantifikátoru porovnává předchozí prvek alespoň `n` krát, kde  *n*  je jakékoli číslo typu integer, ale co nejméně krát možné. Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `,}`.  
  
 Podívejte se příklad `{`  *n*  `}?` kvantifikátoru v předchozí části Obrázek. Regulární výraz v tomto příkladu používá `{`  *n*  `,}` kvantifikátoru tak, aby odpovídaly řetězec, který obsahuje alespoň tři znaky následované období.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Nalezena shoda mezi n až m krát (opožděné porovnávání): {n, m}?  
 `{`  *n*  `,` *m* `}?` kvantifikátoru porovnává předchozí prvek mezi `n` a `m` krát, kde  *n*  a *m* jsou celá čísla, ale nejméně krát. Je opožděné protějškem typu greedy kvantifikátoru `{`  *n*  `,` *m*`}`.  
  
 V následujícím příkladu, regulární výraz `\b[A-Z](\w*\s+){1,10}?[.!?]` odpovídá věty obsahující mezi slovy. jeden a 10. Odpovídá všechny věty ve vstupním řetězci s výjimkou jeden věty obsahující slova 18.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Odpovídat velké písmeno od A do Z.|  
|`(\w*\s+)`|Odpovídat nula nebo více znaků slova, za nímž následuje jeden nebo více prázdných znaků. Toto je první skupinu zachycení.|  
|`{1,10}?`|Shodovat s použitím předchozího vzoru názvů mezi 1 a 10, ale co nejméně krát.|  
|`[.!?]`|Porovná kterýkoli z interpunkční znaky ".","!", nebo "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Typu greedy a opožděné kvantifikátory  
 Počet kvantifikátory má dvě verze:  
  
-   Typu greedy verze.  
  
     Typu greedy kvantifikátor se pokusí porovnat prvek tolikrát, kolikrát je možné.  
  
-   Verze typu non-greedy (nebo opožděné).  
  
     Typu non-greedy kvantifikátor se pokusí porovnat prvek co nejméně krát. Chcete-li typu greedy kvantifikátoru na opožděné kvantifikátory jednoduše přidáním `?`.  
  
 Zvažte jednoduchý regulární výraz, který slouží k extrakci poslední čtyři číslice v řetězci čísel například číslo platební karty. Verze regulární výraz, který používá `*` je typu greedy kvantifikátoru `\b.*([0-9]{4})\b`. Ale pokud řetězec obsahuje dvě čísla, tento regulární výraz odpovídá poslední čtyři číslice druhé číslo, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Regulární výraz selže tak, aby odpovídaly první číslo, protože `*` kvantifikátoru se pokusí vyhledat předchozí element podle možný celý řetězec několikrát, a tak najde shodu na konci řetězce.  
  
 Toto není toto chování žádoucí. Místo toho můžete použít `*?`opožděné kvantifikátoru extrahovat číslic z obou čísel, jak ukazuje následující příklad.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Ve většině případů regulárních výrazů s typu greedy a opožděné kvantifikátory vracejí stejné shody. Při použití se zástupným znakem nejčastěji vracejí odlišné výsledky (`.`) metaznak, který odpovídá jakémukoliv znaku.  
  
## <a name="quantifiers-and-empty-matches"></a>Kvantifikátory a prázdné shody  
 Kvantifikátory `*`, `+`, a `{`  *n*  `,` *m* `}` a jejich opožděné protějšky nikdy opakovat po prázdná případy, kdy byl nalezen minimální počet zachycení. Toto pravidlo zabrání kvantifikátory zadat nekonečné smyčky odpovídá dílčím výrazu prázdný po neomezenou maximální počet možných skupiny zachycení nebo téměř nekonečné.  
  
 Například následující kód ukazuje výsledek volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metoda s regulární výraz `(a?)*`, který odpovídá žádnou nebo jednu "a" znak nula či více krát. Všimněte si, že jediné zachytávající skupiny zachytí každou "a" jako a taky <xref:System.String.Empty?displayProperty=nameWithType>, ta však není nalezena žádná druhá prázdný shoda, protože na první shodu prázdný způsobí, že kvantifikátor zastaví opakování.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Pokud chcete zobrazit praktické rozdíl mezi zaznamenávání skupina, která určuje minimální a maximální počet zachycení a ten, který definuje pevný počet zachycení, zvažte vzorce regulárního výrazu `(a\1|(?(1)\1)){0,2}` a `(a\1|(?(1)\1)){2}`. Obě regulární výrazy se skládá z jedné zachycené skupiny, která je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(a\1`|Buď shodu "a", spolu s hodnotou první zaznamenané skupiny...|  
|`&#124;(?(1)`|… nebo můžete otestovat, zda byla definována první zaznamenané skupinu. (Všimněte si, že `(?(1)` konstrukce nedefinuje skupinu zachycení.)|  
|`\1))`|Pokud první zaznamenané skupina existuje, odpovídají jeho hodnotu. Pokud skupina neexistuje, bude shodovat s skupině <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 První regulární výraz, který se pokusí vyhledat tento vzor mezi nula a dvě časy; druhá s názvem přesně dvakrát. Vzhledem k tomu, že první vzor dosáhne jeho minimální počet zachycení s jeho první zaznamenávání <xref:System.String.Empty?displayProperty=nameWithType>, nikdy opakuje můžete vyzkoušet tak, aby odpovídaly `a\1`; `{0,2}` kvantifikátoru umožňuje pouze prázdné shody v poslední iteraci. Naproti tomu neshoduje druhý regulární výraz "a" vzhledem k tomu, že se vyhodnotí `a\1` podruhé; minimální počet iterací, 2, vynutí se tak, aby modul opakovat po prázdné shodě.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
