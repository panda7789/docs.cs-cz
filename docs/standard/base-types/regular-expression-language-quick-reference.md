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
ms.openlocfilehash: 09f2886173bd3a80691b78a6e3ea71b034ebe34a
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030396"
---
# <a name="regular-expression-language---quick-reference"></a>Jazyk regulárních výrazů – stručná referenční dokumentace
<a name="top"></a> Regulární výraz je vzor, který modul regulárních výrazů pokusí shodovat se vstupním textem. Vzor sestává z jednoho nebo více znakových literálů, operátorů nebo konstrukcí.  Stručný úvod naleznete zde [regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md).  
  
 Jednotlivé oddíly v tomto stručném přehledu obsahují určitou kategorii znaků, operátorů a konstrukcí, pomocí kterých lze definovat regulární výrazy:  
  
 [Řídicí sekvence znaků](#character_escapes)  
 [Třídy znaků](#character_classes)  
 [Kotvy](#anchors)  
 [Seskupovací konstrukce](#grouping_constructs)  
 [Kvantifikátory](#quantifiers)  
 [Konstrukce zpětných odkazů](#backreference_constructs)  
 [Konstrukce alternace](#alternation_constructs)  
 [Náhrady](#substitutions)  
 [Možnosti regulárních výrazů](#options)  
 [Různé konstrukce](#miscellaneous_constructs)  
  
 Tyto informace v dva formáty, které si můžete stáhnout a vytisknout poskytujeme také pro snadné odkazování:  
  
 [Stáhnout ve formátu aplikace Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Stáhnout ve formátu PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Řídicí znaky  
 Znak zpětného lomítka (\\) v regulárním výrazu označuje, že buď následující znak je speciální znak (jak je znázorněno v následující tabulce), nebo by měl být interpretován literálně. Další informace najdete v tématu [řídicí sekvence znaků](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Řídicí znak|Popis|Vzor|Shody|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Odpovídá znaku bell \u0007.|`\a`|Znak "\u0007" v části "Chyba!" + '\u0007'|  
|`\b`|Ve třídě znaků odpovídá znaku Backspace \u0008.|`[\b]{3,}`|"\b\b\b\b" ve výrazu "\b\b\b\b"|  
|`\t`|Odpovídá znaku tabulátoru \u0009.|`(\w+)\t`|"item1\t", "item2\t" ve výrazu "item1\titem2\t"|  
|`\r`|Odpovídá návratovému znaku \u000D. (`\r` není ekvivalentní znaku nového řádku `\n`.)|`\r\n(\w+)`|"\r\nToto" ve větě "\r\nToto jsou\ndva řádky."|  
|`\v`|Odpovídá znaku svislého tabulátoru \u000B.|`[\v]{2,}`|"\v\v\v" ve výrazu "\v\v\v"|  
|`\f`|Odpovídá znaku posunu strany \u000C.|`[\f]{2,}`|"\f\f\f" ve výrazu "\f\f\f"|  
|`\n`|Odpovídá znaku nového řádku \u000A.|`\r\n(\w+)`|"\r\nToto" ve větě "\r\nToto jsou\ndva řádky."|  
|`\e`|Odpovídá řídicímu znaku \u001B.|`\e`|"\x001B" ve výrazu "\x001B"|  
|`\` *nnn*|Používá osmičkové vyjádření k určení znaku (*nnn* obsahuje dvě nebo tři číslice).|`\w\040\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\x` *nn*|Používá šestnáctkové vyjádření k určení znaku (*nn* obsahuje přesně dvě číslice).|`\w\x20\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *x*|Odpovídá řídicímu znaku ASCII, která je zadána *X* nebo *x*, kde *X* nebo *x* je písmeno kontrolního znaku.|`\cC`|"\x0003" ve výrazu "\x0003" (Ctrl-C)|  
|`\u` *nnnn*|Odpovídá znaku Unicode pomocí šestnáctkového vyjádření (přesně čtyři číslice představované výrazem *nnnn*).|`\w\u0020\w`|"a b", "c d" ve výrazu<br /><br /> "a bc d"|  
|`\`|V případě, že následuje znak, který není rozpoznán jako řídicí znak v této a dalších tabulkách v tomto tématu, odpovídá tomuto znaku. Například `\*` je stejný jako `\x2A`, a `\.` je stejný jako `\x2E`. To umožňuje modulu regulárních výrazů rozpoznat prvky jazyka (například \* nebo?) a znakové literály (představované `\*` nebo `\?`).|`\d+[\+-x\*]\d+`|"2 + 2" a "3\*9" ve "(2+2) \* 3\*9"|  
  
 [Zpět na začátek](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Třídy znaků  
 Třída znaků odpovídá jakémukoli znaku z množiny znaků. Třídy znaků obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Třída znaků|Popis|Vzor|Shody|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Odpovídá jakémukoli jednomu znaku v *character_group*. Ve výchozím nastavení shoda rozlišuje velká a malá písmena.|`[ae]`|"a" ve slově "gray"<br /><br /> "a", "e" ve slově "lane"|  
|`[^` *character_group* `]`|Negace: Odpovídá jakémukoli jednomu znaku, který není součástí *character_group*. Ve výchozím nastavení, znaky v *character_group* jsou malá a velká písmena.|`[^aei]`|"r", "g", "n" ve slově "reign"|  
|`[` *první* `-` *poslední* `]`|Rozsah znaků: Odpovídá jakémukoli jednomu znaku v rozsahu od *první* k *poslední*.|`[A-Z]`|"A", "B" ve výrazu "AB123"|  
|`.`|Zástupný znak: Odpovídá jakémukoli jednomu znaku s výjimkou \n.<br /><br /> Tak, aby odpovídaly literální znak tečky (. nebo `\u002E`), je nutné před řídicí znak (`\.`).|`a.e`|"ave" ve slově "nave"<br /><br /> "ate" ve slově "water"|  
|`\p{` *Jméno* `}`|Odpovídá jakémukoli jednomu znaku v obecné kategorii Unicode nebo pojmenovanému bloku určenému pomocí *název*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"C", "L" ve výrazu "City Lights"<br /><br /> "Д", "Ж" ve slově "ДЖem"|  
|`\P{` *Jméno* `}`|Odpovídá jakémukoli jednomu znaku, který není v obecné kategorii Unicode nebo pojmenovanému bloku určenému pomocí *název*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"i", "t", "y" ve slově "City"<br /><br /> "e", "m" ve slově "ДЖem"|  
|`\w`|Odpovídá jakémukoli znaku slova.|`\w`|"I", "D", "A", "1", "3" ve výrazu "ID A1.3"|  
|`\W`|Odpovídá jakémukoli mimoslovnímu znaku.|`\W`|" ", "." ve výrazu "ID A1.3"|  
|`\s`|Odpovídá jakémukoli prázdnému znaku.|`\w\s`|"D " ve výrazu "ID A1.3"|  
|`\S`|Odpovídá jakémukoli neprázdnému znaku.|`\s\S`|"_" v "int \__ctr"|  
|`\d`|Odpovídá jakékoli desítkové číslici.|`\d`|"4" ve výrazu "4 = IV"|  
|`\D`|Odpovídá jakémukoli znaku kromě desítkové číslice.|`\D`|" ", "=", " ", "I", "V" ve výrazu "4 = IV"|  
  
 [Zpět na začátek](#top)  
  
## <a name="anchors"></a>Kotvy  
 Kotvy neboli atomické kontrolní výrazy s nulovou šířkou způsobí, že porovnávání je úspěšné nebo neúspěšné v závislosti na aktuální pozici v řetězci, ale nezpůsobí, aby nástroj postupoval dále v řetězci nebo spotřebovával znaky. Metaznaky uvedené v následující tabulce jsou kotvy. Další informace najdete v tématu [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Kontrolní výraz|Popis|Vzor|Shody|  
|---------------|-----------------|-------------|-------------|  
|`^`|Ve výchozím nastavení porovnání musí začít na začátku řetězce; v víceřádkový režim musíte spustit na začátku řádku.|`^\d{3}`|"901" ve výrazu<br /><br /> "901-333-"|  
|`$`|Ve výchozím nastavení, ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce; v víceřádkový režim, musí dojít před koncem řádku nebo před `\n` na konci řádku.|`-\d{3}$`|"-333" v<br /><br /> "-901-333"|  
|`\A`|Ke shodě musí dojít na začátku řetězce.|`\A\d{3}`|"901" ve výrazu<br /><br /> "901-333-"|  
|`\Z`|Ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce.|`-\d{3}\Z`|"-333" v<br /><br /> "-901-333"|  
|`\z`|Ke shodě musí dojít na konci řetězce.|`-\d{3}\z`|"-333" v<br /><br /> "-901-333"|  
|`\G`|Ke shodě musí dojít v místě, kde byla ukončena předchozí shoda.|`\G\(\d\)`|"(1)", "(3)", "(5)" v "(1) [3] [5] [7] (9\)"|  
|`\b`|Ke shodě musí dojít na hranici mezi `\w` (alfanumerický) a `\W` (nealfanumerický znak).|`\b\w+\s\w+\b`|"them theme", "them them" ve výrazu "them theme them them"|  
|`\B`|Ke shodě nesmí dojít na `\b` hranic.|`\Bend\w*\b`|"ends", "ender" ve výrazu "end sends endure lender"|  
  
 [Zpět na začátek](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Seskupovací konstrukce  
 Seskupovací konstrukce vymezují dílčí výrazy regulárních výrazů a obvykle zachytávají podřetězce vstupního řetězce. Seskupovací konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  
  
|Seskupovací konstrukce|Popis|Vzor|Shody|  
|------------------------|-----------------|-------------|-------------|  
|`(` *Dílčí výraz* `)`|Zachycuje porovnané dílčí výrazy a přiřazuje jim řadové číslovky od jedné.|`(\w)\1`|"ee" ve slově "deep"|  
|`(?<` *název* `>` *dílčí výraz* `)`|Zachycuje porovnaný dílčí výraz do pojmenované skupiny.|`(?<double>\w)\k<double>`|"ee" ve slově "deep"|  
|`(?<` *name1* `-` *name2* `>` *dílčí výraz* `)`|Určuje definici vyrovnávací skupiny. Další informace najdete v části "Definice vyrovnávacího seskupení" v [Grouping Constructs](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"((1-3)\*(3-1))" v "3+2^((1-3)\*(3-1))"|  
|`(?:` *Dílčí výraz* `)`|Definuje skupinu bez zachytávání.|`Write(?:Line)?`|"WriteLine" ve výrazu "Console.WriteLine()"<br /><br /> "Write" ve výrazu "Console.Write(value)"|  
|`(?imnsx-imnsx:` *Dílčí výraz* `)`|Použije nebo zakáže zadané možnosti v rámci *dílčí výraz*. Další informace najdete v tématu [Regular Expression Options](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|"A12xl", "A12XL" ve výrazu "A12xl A12XL a12xl"|  
|`(?=` *Dílčí výraz* `)`|Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou.|`\w+(?=\.)`|"is", "ran" a "out" ve výrazu "He is. The dog ran. The sun is out."|  
|`(?!` *Dílčí výraz* `)`|Kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou.|`\b(?!un)\w+\b`|"sure", "used" ve výrazu "unsure sure unity used"|  
|`(?<=` *Dílčí výraz* `)`|Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|`(?<=19)\d{2}\b`|"99", "50", "05" ve výrazu "1851 1999 1950 1905 2003"|  
|`(?<!` *Dílčí výraz* `)`|Kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou.|`(?<!19)\d{2}\b`|"51", "03" ve výrazu "1851 1999 1950 1905 2003"|  
|`(?>` *Dílčí výraz* `)`|Dílčí výraz bez mechanismu navracení (neboli dílčí výraz "greedy").|`[13579](?>A+B+)`|"1ABB", "3ABB" a "5AB" ve výrazu "1ABB 3ABBC 5AB 5AC"|  
  
 [Zpět na začátek](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Kvantifikátory  
 Kvantifikátor určuje, kolik instancí předchozího prvku (kterým může být znak, skupina nebo třída znaků) musí být přítomných ve vstupním řetězci, aby došlo ke shodě. Kvantifikátory zahrnují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [kvantifikátory](quantifiers-in-regular-expressions.md).  
  
|Kvantifikátor|Popis|Vzor|Shody|  
|----------------|-----------------|-------------|-------------|  
|`*`|Porovná předchozí prvek nulakrát nebo vícekrát.|`\d*\.\d`|".0", "19.9", "219.9"|  
|`+`|Porovná předchozí prvek jednou nebo vícekrát.|`"be+"`|"bee" ve slově "been", "be" ve slově "bent"|  
|`?`|Porovná předchozí prvek nulakrát nebo jedenkrát.|`"rai?n"`|"ran", "rain"|  
|`{` *N* `}`|Porovná předchozí prvek přesně *n* časy.|`",\d{3}"`|",043" ve výrazu "1,043.6", ",876", ",543" a ",210" ve výrazu "9,876,543,210"|  
|`{` *N* `,}`|Porovná předchozí prvek nejméně *n* časy.|`"\d{2,}"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}`|Porovná předchozí prvek nejméně *n* krát, ale ne víc než *m* časy.|`"\d{3,5}"`|"166", "17668"<br /><br /> "19302" ve výrazu "193024"|  
|`*?`|Porovná předchozí prvek nulakrát nebo vícekrát, ale s co nejmenším možným počtem opakování.|`\d*?\.\d`|".0", "19.9", "219.9"|  
|`+?`|Porovná předchozí prvek jednou nebo vícekrát, ale s co nejmenším možným počtem opakování.|`"be+?"`|"be" ve slově "been", "be" ve slově "bent"|  
|`??`|Porovná předchozí prvek nulakrát nebo jedenkrát, ale s co nejmenším možným počtem opakování.|`"rai??n"`|"ran", "rain"|  
|`{` *N* `}?`|Porovná předcházející prvek přesně *n* časy.|`",\d{3}?"`|",043" ve výrazu "1,043.6", ",876", ",543" a ",210" ve výrazu "9,876,543,210"|  
|`{` *N* `,}?`|Porovná předchozí prvek nejméně *n* krát, ale jako nejmenším možným počtem opakování.|`"\d{2,}?"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}?`|Porovná předchozí prvek mezi *n* a *m* krát, ale jako nejmenším možným počtem opakování.|`"\d{3,5}?"`|"166", "17668"<br /><br /> "193", "024" ve výrazu "193024"|  
  
 [Zpět na začátek](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Konstrukce zpětných odkazů  
 Zpětné odkazy umožňují dříve porovnaným dílčím výrazům, aby byly identifikovány následně ve stejném pořadí v daném regulárním výrazu. Následující tabulka uvádí konstrukce zpětných odkazů podporované regulárními výrazy v rozhraní .NET. Další informace najdete v tématu [konstrukce zpětných odkazů](backreference-constructs-in-regular-expressions.md).  
  
|Konstrukce zpětných odkazů|Popis|Vzor|Shody|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *Číslo*|Zpětný odkaz. Odpovídá hodnotě číslovaného dílčího výrazu.|`(\w)\1`|"ee" ve slově "seek"|  
|`\k<` *Jméno* `>`|Pojmenovaný zpětný odkaz. Odpovídá hodnotě číslovaného výrazu.|`(?<char>\w)\k<char>`|"ee" ve slově "seek"|  
  
 [Zpět na začátek](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Konstrukce alternace  
 Konstrukce alternace upravují regulární výraz, aby došlo ke shodě typu buď/anebo. Tyto konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [alternace](alternation-constructs-in-regular-expressions.md).  
  
|Konstrukce alternace|Popis|Vzor|Shody|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Odpovídá jakémukoli jednomu prvku oddělenému podle svislá čára (&#124;) znaků.|<code>th(e&#124;is&#124;at)</code>|"the", "this" ve větě "this is the day. "|  
|`(?(` *výraz* `)` *Ano* <code>&#124;</code> *žádné* `)`|Odpovídá *Ano* Pokud vzor regulárního výrazu určeném *výraz* odpovídá; jinak odpovídá nepovinnému *žádné* část. *výraz* je interpretován jako kontrolní výraz nulové šířky.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|"A10", "910" ve výrazu "A10 C103 910"|  
|`(?(` *název* `)` *Ano* <code>&#124;</code> *žádné* `)`|Odpovídá *Ano* Pokud *název*, pojmenovanou nebo číslovanou zachytávající skupinou, má odpovídající; jinak odpovídá nepovinnému *žádné*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|Dogs.jpg, "Yiska playing.jpg" ve výrazu "Dogs.jpg "Yiska playing.jpg""|  
  
 [Zpět na začátek](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Náhrady  
 Náhrady jsou prvky jazyka regulárních výrazů, které jsou podporovány ve vzorech pro nahrazení. Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md). Metaznaky uvedené v následující tabulce jsou atomické kontrolní výrazy s nulovou šířkou.  
  
|Znak|Popis|Vzor|Vzor pro nahrazování|Vstupní řetězec|Výsledný řetězec|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *Číslo*|Nahradí podřetězec odpovídající skupině *číslo*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|"one two"|"two one"|  
|`${` *Jméno* `}`|Nahradí podřetězec odpovídající pojmenované skupině *název*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|"one two"|"two one"|  
|`$$`|Nahradí literál "$".|`\b(\d+)\s?USD`|`$$$1`|"103 USD"|"$103"|  
|`$&`|Nahradí kopii celé shody.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|``$` ``|Nahradí celý text vstupního řetězce před shodou.|`B+`|``$` ``|"AABBCC"|"AAAACC"|  
|`$'`|Nahradí celý text vstupního řetězce za shodou.|`B+`|`$'`|"AABBCC"|"AACCCC"|  
|`$+`|Nahradí poslední skupinu, která byla zachycena.|`B+(C+)`|`$+`|"AABBCCDD"|"AACCDD"|  
|`$_`|Nahradí celý vstupní řetězec.|`B+`|`$_`|"AABBCC"|"AAAABBCCCC"|  
  
 [Zpět na začátek](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Možnosti regulárních výrazů  
 Můžete zadat možnosti, které řídí způsob, jakým modul regulárních výrazů interpretuje vzor regulárního výrazu. Mnohé z těchto možností může být zadán buď jako vložené (ve vzoru regulárního výrazu), nebo jako jeden nebo více <xref:System.Text.RegularExpressions.RegexOptions> konstanty. Tyto stručné referenční informace uvádí pouze vložené možnosti. Další informace o vložených a <xref:System.Text.RegularExpressions.RegexOptions> možnosti, najdete v článku [Regular Expression Options](regular-expression-options.md).  
  
 Vloženou možnost můžete zadat dvěma způsoby:  
  
-   S použitím [různých konstrukcí](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, kde znaménko mínus (-) před možností nebo sadou možností vypne tyto možnosti. Například `(?i-mn)` zapne porovnávání (`i`), vypne víceřádkový režim (`m`) a vypne zachycení nepojmenované skupiny (`n`) vypnout. Možnost se vztahuje na vzor regulárního výrazu od bodu, ve kterém je možnost definována, a platí buď až do konce vzoru nebo do bodu, ve kterém je možnost zrušena jiným konstruktorem.  
  
-   S použitím [Seskupující konstrukce](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*dílčí výraz*`)`, která definuje možnosti pouze zadané skupiny.  
  
 Modul regulárních výrazů .NET podporuje následující vložené možnosti.  
  
|Možnost|Popis|Vzor|Shody|  
|------------|-----------------|-------------|-------------|  
|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena.|`\b(?i)a(?-i)a\w+\b`|"aardvark", "aaaAuto" ve výrazu "aardvark AAAuto aaaAuto Adam breakfast"|  
|`m`|Použije víceřádkový režim. `^` a `$` odpovídají začátku a konci řádku namísto začátku a konce řetězce.|Příklad naleznete v části "Víceřádkový mód" v [Regular Expression Options](regular-expression-options.md).||  
|`n`|Nezachytí nepojmenované skupiny.|Příklad najdete v části "Pouze explicitní zachycení" v [Regular Expression Options](regular-expression-options.md).||  
|`s`|Použije jednořádkový režim.|Příklad naleznete v části "jednořádkový mód" v [Regular Expression Options](regular-expression-options.md).||  
|`x`|Ignoruje prázdný znak bez řídicího znaku ve vzoru regulárního výrazu.|`\b(?x) \d+ \s \w+`|"1 aardvark", "2 cats" ve výrazu "1 aardvark 2 cats IV centurions"|  
  
 [Zpět na začátek](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Různé konstrukce  
 Různé konstrukce buď upraví vzor regulárního výrazu, nebo o tomto vzoru poskytnou informace. Následující tabulka obsahuje seznam různých konstrukcí podporovaných rozhraním .NET. Další informace najdete v tématu [různé vytvoří](miscellaneous-constructs-in-regular-expressions.md).  
  
|Konstrukce|Definice|Příklad|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Nastaví nebo zakáže možnosti, jako je nerozlišování velikosti písmen uprostřed vzoru. Další informace najdete v tématu [Regular Expression Options](regular-expression-options.md).|`\bA(?i)b\w+\b` odpovídá "ABA", "Able" v "ABA Able Act"|  
|`(?#` *Komentář* `)`|Vložený komentář. Komentář končí první pravou závorkou.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [do konce řádku]|Komentář x-mode. Komentář začíná znakem `#` a pokračuje na konec řádku.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex>  
- [Regulární výrazy](regular-expressions.md)  
- [Třídy regulárních výrazů](the-regular-expression-object-model.md)  
- [Příklady regulárních výrazů](regular-expression-examples.md)  
- [Regulárních výrazů – Stručná referenční příručka (ke stažení ve Wordovém formátu)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Regulárních výrazů – Stručná referenční příručka (ke stažení ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
