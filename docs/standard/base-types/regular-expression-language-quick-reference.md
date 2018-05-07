---
title: Jazyk regulárních výrazů – stručná referenční dokumentace
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b41161d1511f7dce975ac5ad916750734972fa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="regular-expression-language---quick-reference"></a>Jazyk regulárních výrazů – stručná referenční dokumentace
<a name="top"></a> Regulární výraz je vzor, který modul regulárních výrazů se pokusí o porovnání v vstupního textu. Vzor sestává z jednoho nebo více znakových literálů, operátorů nebo konstrukcí.  Stručný úvod najdete v části [regulárních výrazech .NET](../../../docs/standard/base-types/regular-expressions.md).  
  
 Jednotlivé oddíly v tomto stručném přehledu obsahují určitou kategorii znaků, operátorů a konstrukcí, pomocí kterých lze definovat regulární výrazy:  
  
 [Řídicí sekvence znaků](#character_escapes)  
 [Třídy znaků](#character_classes)  
 [Kotvy](#atomic_zerowidth_assertions)  
 [Seskupovací konstrukce](#grouping_constructs)  
 [Kvantifikátory](#quantifiers)  
 [Konstrukce zpětných odkazů](#backreference_constructs)  
 [Konstrukce alternace](#alternation_constructs)  
 [Náhrady](#substitutions)  
 [Možnosti regulárních výrazů](#options)  
 [Různé konstrukce](#miscellaneous_constructs)  
  
 Tyto informace v dva formáty, které si můžete stáhnout a vytisknout nabízíme také referenční:  
  
 [Stáhnout ve formátu aplikace Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Stáhnout ve formátu PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Řídicí znaky  
 Znak zpětného lomítka (\\) v regulárním výrazu označuje, že je znak, který následuje buď speciální znak (jak je znázorněno v následující tabulce), nebo by měla být interpretována oznámena. Další informace najdete v tématu [řídicí sekvence znaků](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Řídicí znak|Popis|Vzor|Shody|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Odpovídá znaku bell \u0007.|`\a`|Znak "\u0007" v části "Chyba!" + '\u0007'|  
|`\b`|Ve třídě znaků odpovídá znaku Backspace \u0008.|`[\b]{3,}`|"\b\b\b\b" ve výrazu "\b\b\b\b"|  
|`\t`|Odpovídá znaku tabulátoru \u0009.|`(\w+)\t`|"item1\t", "item2\t" ve výrazu "item1\titem2\t"|  
|`\r`|Odpovídá návratovému znaku \u000D. (`\r` není ekvivalentní znak nového řádku `\n`.)|`\r\n(\w+)`|"\r\nToto" ve větě "\r\nToto jsou\ndva řádky."|  
|`\v`|Odpovídá znaku svislého tabulátoru \u000B.|`[\v]{2,}`|"\v\v\v" ve výrazu "\v\v\v"|  
|`\f`|Odpovídá znaku posunu strany \u000C.|`[\f]{2,}`|"\f\f\f" ve výrazu "\f\f\f"|  
|`\n`|Odpovídá znaku nového řádku \u000A.|`\r\n(\w+)`|"\r\nToto" ve větě "\r\nToto jsou\ndva řádky."|  
|`\e`|Odpovídá řídicímu znaku \u001B.|`\e`|"\x001B" ve výrazu "\x001B"|  
|`\` *nnn*|Používá osmičkové vyjádření k určení znaku (*nnn* obsahuje dvě nebo tři číslice).|`\w\040\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\x` *nn*|Používá k určení znaku hexadecimální reprezentace (*nn* obsahuje přesně dvě číslice).|`\w\x20\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *X*|Odpovídá řízení znaků ASCII, která je zadána *X* nebo *x*, kde *X* nebo *x* je písmeno řídicí znak.|`\cC`|"\x0003" ve výrazu "\x0003" (Ctrl-C)|  
|`\u` *nnnn*|Odpovídá znak Unicode s použitím šestnáctkového vyjádření (přesně čtyři číslice, reprezentovaná *nnnn*).|`\w\u0020\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\`|V případě, že následuje znak, který není rozpoznán jako řídicí znak v této a dalších tabulkách v tomto tématu, odpovídá tomuto znaku. Například `\*` je stejný jako `\x2A`, a `\.` je stejný jako `\x2E`. To umožňuje modul regulárních výrazů k rozlišení prvků jazyka (například \* nebo?) a znakové literály (reprezentována `\*` nebo `\?`).|`\d+[\+-x\*]\d+`|"2 + 2" a "3\*9" "(2+2) \* 3\*9"|  
  
 [Zpět na začátek](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Třídy znaků  
 Třída znaků odpovídá jakémukoli znaku z množiny znaků. Třídy znaků obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Třída znaků|Popis|Vzor|Shody|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Odpovídá jakémukoliv jedinému znaku v *character_group*. Ve výchozím nastavení shoda rozlišuje velká a malá písmena.|`[ae]`|"a" ve slově "gray"<br /><br /> "a", "e" ve slově "lane"|  
|`[^` *character_group* `]`|Negace: Odpovídá jakémukoliv jedinému znaku, který není součástí *character_group*. Ve výchozím nastavení, znaky v *character_group* malých a velkých písmen.|`[^aei]`|"r", "g", "n" ve slově "reign"|  
|`[` *první* `-` *poslední* `]`|Znak rozsah: odpovídá jakémukoliv jedinému znaku v rozsahu od *první* k *poslední*.|`[A-Z]`|"A", "B" ve výrazu "AB123"|  
|`.`|Zástupný znak: Odpovídá jakémukoli jednomu znaku s výjimkou \n.<br /><br /> Tak, aby odpovídaly literálu tečka (. nebo `\u002E`), je nutné před s řídicí znak (`\.`).|`a.e`|"ave" ve slově "nave"<br /><br /> "ate" ve slově "water"|  
|`\p{` *Jméno* `}`|Odpovídá jakémukoliv jedinému znaku v obecné kategorie Unicode nebo pojmenované bloku určeného *název*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"C", "L" ve výrazu "City Lights"<br /><br /> "Д", "Ж" ve slově "ДЖem"|  
|`\P{` *Jméno* `}`|Odpovídá jakémukoliv jedinému znaku, který není v obecné kategorii Unicode nebo pojmenované bloku určeného *název*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"i", "t", "y" ve slově "City"<br /><br /> "e", "m" ve slově "ДЖem"|  
|`\w`|Odpovídá jakémukoli znaku slova.|`\w`|"I", "D", "A", "1", "3" ve výrazu "ID A1.3"|  
|`\W`|Odpovídá jakémukoli mimoslovnímu znaku.|`\W`|" ", "." ve výrazu "ID A1.3"|  
|`\s`|Odpovídá jakémukoli prázdnému znaku.|`\w\s`|"D " ve výrazu "ID A1.3"|  
|`\S`|Odpovídá jakémukoli neprázdnému znaku.|`\s\S`|"_" v "int \__ctr"|  
|`\d`|Odpovídá jakékoli desítkové číslici.|`\d`|"4" ve výrazu "4 = IV"|  
|`\D`|Odpovídá jakémukoli znaku kromě desítkové číslice.|`\D`|" ", "=", " ", "I", "V" ve výrazu "4 = IV"|  
  
 [Zpět na začátek](#top)  
  
<a name="atomic_zerowidth_assertions"></a>   
## <a name="anchors"></a>Kotvy  
 Kotvy neboli atomické kontrolní výrazy s nulovou šířkou způsobí, že porovnávání je úspěšné nebo neúspěšné v závislosti na aktuální pozici v řetězci, ale nezpůsobí, aby nástroj postupoval dále v řetězci nebo spotřebovával znaky. Metaznaky uvedené v následující tabulce jsou kotvy. Další informace najdete v tématu [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Kontrolní výraz|Popis|Vzor|Shody|  
|---------------|-----------------|-------------|-------------|  
|`^`|Porovnání musí začít na začátku řetězce nebo řádku.|`^\d{3}`|"901" ve výrazu<br /><br /> "901-333-"|  
|`$`|Shoda se musí vyskytovat na konci řetězce nebo před `\n` na konci řádku nebo řetězec.|`-\d{3}$`|"-333" v<br /><br /> "-901-333"|  
|`\A`|Ke shodě musí dojít na začátku řetězce.|`\A\d{3}`|"901" ve výrazu<br /><br /> "901-333-"|  
|`\Z`|Shoda se musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce.|`-\d{3}\Z`|"-333" v<br /><br /> "-901-333"|  
|`\z`|Ke shodě musí dojít na konci řetězce.|`-\d{3}\z`|"-333" v<br /><br /> "-901-333"|  
|`\G`|Ke shodě musí dojít v místě, kde byla ukončena předchozí shoda.|`\G\(\d\)`|"(1)", "(3)", "(5)" v "(1) [3] [5] [7] (9\)"|  
|`\b`|Shoda se musí vyskytovat na hranici mezi `\w` (alfanumerických) a `\W` (nealfanumerické) znak.|`\b\w+\s\w+\b`|"them theme", "them them" ve výrazu "them theme them them"|  
|`\B`|Shoda se nesmí objevit na `\b` hranic.|`\Bend\w*\b`|"ends", "ender" ve výrazu "end sends endure lender"|  
  
 [Zpět na začátek](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Seskupovací konstrukce  
 Seskupovací konstrukce vymezují dílčí výrazy regulárních výrazů a obvykle zachytávají podřetězce vstupního řetězce. Seskupovací konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [seskupení vytvoří](grouping-constructs-in-regular-expressions.md).  
  
|Seskupovací konstrukce|Popis|Vzor|Shody|  
|------------------------|-----------------|-------------|-------------|  
|`(` *dílčím výrazu* `)`|Zachycuje porovnané dílčí výrazy a přiřazuje jim řadové číslovky od jedné.|`(\w)\1`|"ee" ve slově "deep"|  
|`(?<` *název* `>` *dílčím výrazu* `)`|Zachycuje porovnaný dílčí výraz do pojmenované skupiny.|`(?<double>\w)\k<double>`|"ee" ve slově "deep"|  
|`(?<` *name1* `-` *name2* `>` *dílčím výrazu* `)`|Určuje definici vyrovnávací skupiny. Další informace najdete v části "Vyrovnávání definice skupiny" v [seskupení vytvoří](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"((1-3)\*(3-1))" v "3+2^((1-3)\*(3-1))"|  
|`(?:` *dílčím výrazu* `)`|Definuje skupinu bez zachytávání.|`Write(?:Line)?`|"WriteLine" ve výrazu "Console.WriteLine()"<br /><br /> "Write" ve výrazu "Console.Write(value)"|  
|`(?imnsx-imnsx:` *dílčím výrazu* `)`|Použije nebo zakáže zadané možnosti v rámci *dílčím výrazu*. Další informace najdete v tématu [možnosti regulárních výrazů](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|"A12xl", "A12XL" ve výrazu "A12xl A12XL a12xl"|  
|`(?=` *dílčím výrazu* `)`|Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou.|`\w+(?=\.)`|"is", "ran" a "out" ve výrazu "He is. The dog ran. The sun is out."|  
|`(?!` *dílčím výrazu* `)`|Kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou.|`\b(?!un)\w+\b`|"sure", "used" ve výrazu "unsure sure unity used"|  
|`(?<=` *dílčím výrazu* `)`|Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|`(?<=19)\d{2}\b`|"99", "50", "05" ve výrazu "1851 1999 1950 1905 2003"|  
|`(?<!` *dílčím výrazu* `)`|Kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou.|`(?<!19)\d{2}\b`|"51", "03" ve výrazu "1851 1999 1950 1905 2003"|  
|`(?>` *dílčím výrazu* `)`|Dílčí výraz bez mechanismu navracení (neboli dílčí výraz "greedy").|`[13579](?>A+B+)`|"1ABB", "3ABB" a "5AB" ve výrazu "1ABB 3ABBC 5AB 5AC"|  
  
 [Zpět na začátek](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Kvantifikátory  
 Kvantifikátor určuje, kolik instancí předchozího prvku (kterým může být znak, skupina nebo třída znaků) musí být přítomných ve vstupním řetězci, aby došlo ke shodě. Kvantifikátory zahrnují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [kvantifikátory](quantifiers-in-regular-expressions.md).  
  
|Kvantifikátor|Popis|Vzor|Shody|  
|----------------|-----------------|-------------|-------------|  
|`*`|Porovná předchozí prvek nulakrát nebo vícekrát.|`\d*\.\d`|".0", "19.9", "219.9"|  
|`+`|Porovná předchozí prvek jednou nebo vícekrát.|`"be+"`|"bee" ve slově "been", "be" ve slově "bent"|  
|`?`|Porovná předchozí prvek nulakrát nebo jedenkrát.|`"rai?n"`|"ran", "rain"|  
|`{` *N* `}`|Odpovídá předchozí prvek přesně *n* časy.|`",\d{3}"`|",043" ve výrazu "1,043.6", ",876", ",543" a ",210" ve výrazu "9,876,543,210"|  
|`{` *N* `,}`|Odpovídá předchozí prvek alespoň *n* časy.|`"\d{2,}"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}`|Odpovídá předchozí prvek alespoň *n* časy, ale ne víc než *m* časy.|`"\d{3,5}"`|"166", "17668"<br /><br /> "19302" ve výrazu "193024"|  
|`*?`|Porovná předchozí prvek nulakrát nebo vícekrát, ale s co nejmenším možným počtem opakování.|`\d*?\.\d`|".0", "19.9", "219.9"|  
|`+?`|Porovná předchozí prvek jednou nebo vícekrát, ale s co nejmenším možným počtem opakování.|`"be+?"`|"be" ve slově "been", "be" ve slově "bent"|  
|`??`|Porovná předchozí prvek nulakrát nebo jedenkrát, ale s co nejmenším možným počtem opakování.|`"rai??n"`|"ran", "rain"|  
|`{` *N* `}?`|Odpovídá předchozí prvek přesně *n* časy.|`",\d{3}?"`|",043" ve výrazu "1,043.6", ",876", ",543" a ",210" ve výrazu "9,876,543,210"|  
|`{` *N* `,}?`|Odpovídá předchozí prvek alespoň *n* dobu, ale co nejméně krát.|`"\d{2,}?"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}?`|Odpovídá předchozí element mezi *n* a *m* dobu, ale co nejméně krát.|`"\d{3,5}?"`|"166", "17668"<br /><br /> "193", "024" ve výrazu "193024"|  
  
 [Zpět na začátek](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Konstrukce zpětných odkazů  
 Zpětné odkazy umožňují dříve porovnaným dílčím výrazům, aby byly identifikovány následně ve stejném pořadí v daném regulárním výrazu. Následující tabulka uvádí konstrukce zpětných odkazů podporované regulární výrazy v rozhraní .NET. Další informace najdete v tématu [konstrukce zpětných odkazů](backreference-constructs-in-regular-expressions.md).  
  
|Konstrukce zpětných odkazů|Popis|Vzor|Shody|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *Číslo*|Zpětný odkaz. Odpovídá hodnotě číslovaného dílčího výrazu.|`(\w)\1`|"ee" ve slově "seek"|  
|`\k<` *Jméno* `>`|Pojmenovaný zpětný odkaz. Odpovídá hodnotě číslovaného výrazu.|`(?<char>\w)\k<char>`|"ee" ve slově "seek"|  
  
 [Zpět na začátek](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Konstrukce alternace  
 Konstrukce alternace upravují regulární výraz, aby došlo ke shodě typu buď/anebo. Tyto konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [konstrukce alternace](alternation-constructs-in-regular-expressions.md).  
  
|Konstrukce alternace|Popis|Vzor|Shody|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Odpovídá jakémukoli jednomu prvku oddělených svislá čára (&#124;) znaků.|<code>th(e&#124;is&#124;at)</code>|"the", "this" ve větě "this is the day. "|  
|`(?(` *výraz* `)` *Ano* <code>&#124;</code> *žádné* `)`|Odpovídá *Ano* Pokud regulární výraz určený hodnotou *výraz* odpovídá; jinak, odpovídá nepovinný *žádné* část. *výraz* interpretována jako assertion nulovou šířkou.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|"A10", "910" ve výrazu "A10 C103 910"|  
|`(?(` *název* `)` *Ano* <code>&#124;</code> *žádné* `)`|Odpovídá *Ano* Pokud *název*, s názvem nebo číslem zaznamenávání skupiny, má odpovídající; jinak hodnota odpovídá nepovinný *žádné*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|Dogs.jpg, "Yiska playing.jpg" ve výrazu "Dogs.jpg "Yiska playing.jpg""|  
  
 [Zpět na začátek](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Náhrady  
 Náhrady jsou prvky jazyka regulárních výrazů, které jsou podporovány ve vzorech pro nahrazení. Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md). Metaznaky uvedené v následující tabulce jsou atomické kontrolní výrazy s nulovou šířkou.  
  
|Znak|Popis|Vzor|Vzor pro nahrazování|Vstupní řetězec|Výsledný řetězec|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *Číslo*|Nahradí podřetězec skupiny *číslo*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|"one two"|"two one"|  
|`${` *Jméno* `}`|Nahradí podřetězec pojmenovanou skupinu *název*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|"one two"|"two one"|  
|`$$`|Nahradí literál "$".|`\b(\d+)\s?USD`|`$$$1`|"103 USD"|"$103"|  
|`$&`|Nahradí kopii celé shody.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|<code>$`</code>|Nahradí celý text vstupního řetězce před shodou.|`B+`|<code>$`</code>|"AABBCC"|"AAAACC"|  
|`$'`|Nahradí celý text vstupního řetězce za shodou.|`B+`|`$'`|"AABBCC"|"AACCCC"|  
|`$+`|Nahradí poslední skupinu, která byla zachycena.|`B+(C+)`|`$+`|"AABBCCDD"|AACCDD|  
|`$_`|Nahradí celý vstupní řetězec.|`B+`|`$_`|"AABBCC"|"AAAABBCCCC"|  
  
 [Zpět na začátek](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Možnosti regulárních výrazů  
 Můžete zadat možnosti, které řídí způsob, jakým modul regulárních výrazů interpretuje vzor regulárního výrazu. Mnoho z těchto možností může být zadán buď vložený (v vzor regulárního výrazu) nebo jako jeden nebo více <xref:System.Text.RegularExpressions.RegexOptions> konstanty. Tyto stručné referenční informace uvádí pouze vložené možnosti. Další informace o vložených a <xref:System.Text.RegularExpressions.RegexOptions> možnosti, najdete v článku [možnosti regulárních výrazů](regular-expression-options.md).  
  
 Vloženou možnost můžete zadat dvěma způsoby:  
  
-   Pomocí [různé konstrukce](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, kdy se znaménkem minus (-) před možností nebo sadu voleb pro tyto možnosti vypne. Například `(?i-mn)` změní porovnávání (`i`), změní víceřádkového režimu (`m`) vypnutí a znovu nepojmenované skupiny zachycení (`n`) vypnout. Možnost se vztahuje na vzor regulárního výrazu od bodu, ve kterém je možnost definována, a platí buď až do konce vzoru nebo do bodu, ve kterém je možnost zrušena jiným konstruktorem.  
  
-   Pomocí [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*dílčím výrazu*`)`, která definuje možnosti pro zadanou skupinu pouze.  
  
 Modul regulárních výrazů .NET podporuje následující možnosti vložené.  
  
|Možnost|Popis|Vzor|Shody|  
|------------|-----------------|-------------|-------------|  
|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena.|`\b(?i)a(?-i)a\w+\b`|"aardvark", "aaaAuto" ve výrazu "aardvark AAAuto aaaAuto Adam breakfast"|  
|`m`|Použije víceřádkový režim. `^` a `$` odpovídají začátku a konci řádku, místo začátku a konce řetězce.|Příklad, najdete v části "Víceřádkových režim" v [možnosti regulárních výrazů](regular-expression-options.md).||  
|`n`|Nezachytí nepojmenované skupiny.|Příklad najdete v části "Pouze explicitní zachycení" v [možnosti regulárních výrazů](regular-expression-options.md).||  
|`s`|Použije jednořádkový režim.|Příklad, najdete v části "režim jeden řádek" v [možnosti regulárních výrazů](regular-expression-options.md).||  
|`x`|Ignoruje prázdný znak bez řídicího znaku ve vzoru regulárního výrazu.|`\b(?x) \d+ \s \w+`|"1 aardvark", "2 cats" ve výrazu "1 aardvark 2 cats IV centurions"|  
  
 [Zpět na začátek](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Různé konstrukce  
 Různé konstrukce buď upraví vzor regulárního výrazu, nebo o tomto vzoru poskytnou informace. Následující tabulka uvádí různé konstrukce nepodporuje rozhraní .NET. Další informace najdete v tématu [různé vytvoří](miscellaneous-constructs-in-regular-expressions.md).  
  
|Konstrukce|Definice|Příklad|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Nastaví nebo zakáže možnosti, například nerozlišování uprostřed vzor. Další informace najdete v tématu [možnosti regulárních výrazů](regular-expression-options.md).|`\bA(?i)b\w+\b` odpovídá "ABA", "Možnost" v "ABA možné Act"|  
|`(?#` *Komentář* `)`|Vložený komentář. Komentář končí první pravou závorkou.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [na konci řádku]|Komentář x-mode. Komentář začíná neuvozené `#` a pokračuje na konec řádku.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex>  
 [Regulární výrazy](regular-expressions.md)  
 [Třídy regulárních výrazů](the-regular-expression-object-model.md)  
 [Příklady regulárních výrazů](regular-expression-examples.md)  
 [Regulárních výrazů – Stručná referenční dokumentace (ke stažení ve Wordovém formátu)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Regulárních výrazů – Stručná referenční dokumentace (ke stažení ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
