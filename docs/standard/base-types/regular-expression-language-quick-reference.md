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
ms.openlocfilehash: 8acf0886215c2d31f949e38401c4705ac9e2aef5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124309"
---
# <a name="regular-expression-language---quick-reference"></a>Jazyk regulárních výrazů – stručná referenční dokumentace

Regulární výraz je vzor, který modul regulárních výrazů porovnává se vstupním textem. Vzor sestává z jednoho nebo více znakových literálů, operátorů nebo konstrukcí. Stručný úvod naleznete v tématu [regulární výrazy .NET](regular-expressions.md).

Každý oddíl v tomto stručném přehledu obsahuje konkrétní kategorii znaků, operátorů a konstrukcí, které lze použít k definování regulárních výrazů.

Tyto informace jsme také poskytli ve dvou formátech, které si můžete stáhnout a vytisknout a získat tak snadnou referenci:

- [Stáhnout ve formátu Word (. docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Stáhnout ve formátu PDF (. PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Řídicí znaky

Znak zpětného lomítka (\\) v regulárním výrazu označuje, že následující znak je buď speciální znak (jak je uvedeno v následující tabulce), nebo by měl být interpretován doslova. Další informace naleznete v tématu [znakové řídicí znaky](character-escapes-in-regular-expressions.md).

|Řídicí znak|Popis|Vzor|Shody|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Odpovídá znaku bell \u0007.|`\a`|`"\u0007"` v `"Error!" + '\u0007'`|
|`\b`|Ve třídě znaků odpovídá znaku Backspace \u0008.|`[\b]{3,}`|`"\b\b\b\b"` v `"\b\b\b\b"`|
|`\t`|Odpovídá znaku tabulátoru \u0009.|`(\w+)\t`|`"item1\t"``"item2\t"` v `"item1\titem2\t"`|
|`\r`|Odpovídá návratovému znaku \u000D. (`\r` není ekvivalentem znaku nového řádku, `\n`.)|`\r\n(\w+)`|`"\r\nThese"` v `"\r\nThese are\ntwo lines."`|
|`\v`|Odpovídá znaku svislého tabulátoru \u000B.|`[\v]{2,}`|`"\v\v\v"` v `"\v\v\v"`|
|`\f`|Odpovídá znaku posunu strany \u000C.|`[\f]{2,}`|`"\f\f\f"` v `"\f\f\f"`|
|`\n`|Odpovídá znaku nového řádku \u000A.|`\r\n(\w+)`|`"\r\nThese"` v `"\r\nThese are\ntwo lines."`|
|`\e`|Odpovídá řídicímu znaku \u001B.|`\e`|`"\x001B"` v `"\x001B"`|
|`\` *NNN*|Používá osmičkové vyjádření k určení znaku (*NNN* se skládá ze dvou nebo tří číslic).|`\w\040\w`|`"a b"``"c d"` v `"a bc d"`|
|`\x` *NN*|Používá šestnáctkové vyjádření k určení znaku (*NN* obsahuje přesně dvě číslice).|`\w\x20\w`|`"a b"``"c d"` v `"a bc d"`|
|`\c` *X*<br /><br /> `\c` *x*|Odpovídá řídicímu znaku ASCII, který je určen *x* nebo *x*, kde *x* nebo *x* je písmeno řídicího znaku.|`\cC`|`"\x0003"` v `"\x0003"` (CTRL-C)|
|`\u` *nnnn*|Odpovídá znaku Unicode pomocí šestnáctkového vyjádření (přesně čtyři číslice reprezentované hodnotou *nnnn*).|`\w\u0020\w`|`"a b"``"c d"` v `"a bc d"`|
|`\`|V případě, že následuje znak, který není rozpoznán jako řídicí znak v této a dalších tabulkách v tomto tématu, odpovídá tomuto znaku. Například `\*` je stejná jako `\x2A`a `\.` je stejná jako `\x2E`. To umožňuje modulu regulárních výrazů rozlišit jazykové prvky (například \* nebo?) a znakové literály (reprezentované `\*` nebo `\?`).|`\d+[\+-x\*]\d+`|`"2+2"` a `"3*9"` v `"(2+2) * 3*9"`|

## <a name="character-classes"></a>Třídy znaků

Třída znaků odpovídá jakémukoli znaku z množiny znaků. Třídy znaků obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete v tématu [třídy znaků](character-classes-in-regular-expressions.md).

|Třída znaků|Popis|Vzor|Shody|
|---------------------|-----------------|-------------|-------------|
|`[` *character_group* `]`|Odpovídá jakémukoli jednomu znaku v *character_group*. Ve výchozím nastavení shoda rozlišuje velká a malá písmena.|`[ae]`|`"a"` v `"gray"`<br /><br /> `"a"``"e"` v `"lane"`|
|`[^` *character_group* `]`|Negace: odpovídá jakémukoli jednomu znaku, který není v *character_group*. Ve výchozím nastavení znaky v *character_group* rozlišují velká a malá písmena.|`[^aei]`|`"r"`, `"g"``"n"` v `"reign"`|
|`[` *první* `-` *Poslední* `]`|Rozsah znaků: odpovídá jakémukoli jednomu znaku v rozsahu od *první* po *Poslední*.|`[A-Z]`|`"A"``"B"` v `"AB123"`|
|`.`|Zástupný znak: Odpovídá jakémukoli jednomu znaku s výjimkou \n.<br /><br /> Aby odpovídala znaku tečky literálu (. nebo `\u002E`), je nutné předcházet řídicímu znaku (`\.`).|`a.e`|`"ave"` v `"nave"`<br /><br /> `"ate"` v `"water"`|
|*název* `\p{` `}`|Odpovídá jakémukoli jednomu znaku v obecné kategorii Unicode nebo pojmenovanému bloku určenému *názvem*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"``"L"` v `"City Lights"`<br /><br /> `"Д"``"Ж"` v `"ДЖem"`|
|*název* `\P{` `}`|Odpovídá jakémukoli jednomu znaku, který není v obecné kategorii Unicode nebo pojmenovaném bloku určeném *názvem*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"``"y"` v `"City"`<br /><br /> `"e"``"m"` v `"ДЖem"`|
|`\w`|Odpovídá jakémukoli znaku slova.|`\w`|`"I"`, `"D"`, `"A"``"1"``"3"``"ID A1.3"`|
|`\W`|Odpovídá jakémukoli mimoslovnímu znaku.|`\W`|`" "``"."` v `"ID A1.3"`|
|`\s`|Odpovídá jakémukoli prázdnému znaku.|`\w\s`|`"D "` v `"ID A1.3"`|
|`\S`|Odpovídá jakémukoli neprázdnému znaku.|`\s\S`|`" _"` v `"int __ctr"`|
|`\d`|Odpovídá jakékoli desítkové číslici.|`\d`|`"4"` v `"4 = IV"`|
|`\D`|Odpovídá jakémukoli znaku kromě desítkové číslice.|`\D`|`" "`, `"="`, `" "``"I"``"V"``"4 = IV"`|

## <a name="anchors"></a>Kotvy

Kotvy neboli atomické kontrolní výrazy s nulovou šířkou způsobí, že porovnávání je úspěšné nebo neúspěšné v závislosti na aktuální pozici v řetězci, ale nezpůsobí, aby nástroj postupoval dále v řetězci nebo spotřebovával znaky. Metaznaky uvedené v následující tabulce jsou kotvy. Další informace naleznete v tématu [kotvy](anchors-in-regular-expressions.md).

|Kontrolní výraz|Popis|Vzor|Shody|
|---------------|-----------------|-------------|-------------|
|`^`|Ve výchozím nastavení musí shoda začít na začátku řetězce; v víceřádkovém režimu musí začít na začátku řádku.|`^\d{3}`|`"901"` v `"901-333-"`|
|`$`|Ve výchozím nastavení se shoda musí vyskytovat na konci řetězce nebo před `\n` na konci řetězce; v víceřádkovém režimu se musí vyskytovat před koncem řádku nebo před `\n` na konci řádku.|`-\d{3}$`|`"-333"` v `"-901-333"`|
|`\A`|Ke shodě musí dojít na začátku řetězce.|`\A\d{3}`|`"901"` v `"901-333-"`|
|`\Z`|Ke shodě musí dojít na konci řetězce nebo před `\n` na konci řetězce.|`-\d{3}\Z`|`"-333"` v `"-901-333"`|
|`\z`|Ke shodě musí dojít na konci řetězce.|`-\d{3}\z`|`"-333"` v `"-901-333"`|
|`\G`|Ke shodě musí dojít v místě, kde byla ukončena předchozí shoda.|`\G\(\d\)`|`"(1)"`, `"(3)"``"(5)"` v `"(1)(3)(5)[7](9)"`|
|`\b`|Shoda se musí vyskytovat na hranici mezi `\w` (alfanumerický) a znakem `\W` (nealfanumerický).|`\b\w+\s\w+\b`|`"them theme"``"them them"` v `"them theme them them"`|
|`\B`|Shoda se nesmí vyskytovat na hranici `\b`.|`\Bend\w*\b`|`"ends"``"ender"` v `"end sends endure lender"`|

## <a name="grouping-constructs"></a>Seskupovací konstrukce

Seskupovací konstrukce vymezují dílčí výrazy regulárních výrazů a obvykle zachytávají podřetězce vstupního řetězce. Seskupovací konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete v tématu [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md).

|Seskupovací konstrukce|Popis|Vzor|Shody|
|------------------------|-----------------|-------------|-------------|
|`(` dílčí *výraz* `)`|Zachycuje porovnané dílčí výrazy a přiřazuje jim řadové číslovky od jedné.|`(\w)\1`|`"ee"` v `"deep"`|
|`(?<` *název* `>` dílčího *výrazu* `)`|Zachycuje porovnaný dílčí výraz do pojmenované skupiny.|`(?<double>\w)\k<double>`|`"ee"` v `"deep"`|
|`(?<` *název1* `-` *název2* `>` dílčí *výraz* `)`|Určuje definici vyrovnávací skupiny. Další informace naleznete v části "definice vyrovnávací skupiny" v tématu [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` v `"3+2^((1-3)*(3-1))"`|
|`(?:` dílčí *výraz* `)`|Definuje skupinu bez zachytávání.|`Write(?:Line)?`|`"WriteLine"` v `"Console.WriteLine()"`<br /><br /> `"Write"` v `"Console.Write(value)"`|
|`(?imnsx-imnsx:` dílčí *výraz* `)`|Použije nebo zakáže zadané možnosti v rámci dílčího *výrazu*. Další informace najdete v tématu [Možnosti regulárních výrazů](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"``"A12XL"` v `"A12xl A12XL a12xl"`|
|`(?=` dílčí *výraz* `)`|Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou.|`\w+(?=\.)`|`"is"`, `"ran"`a `"out"` v `"He is. The dog ran. The sun is out."`|
|`(?!` dílčí *výraz* `)`|Kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou.|`\b(?!un)\w+\b`|`"sure"``"used"` v `"unsure sure unity used"`|
|`(?<=` dílčí *výraz* `)`|Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|`(?<=19)\d{2}\b`|`"99"`, `"50"``"05"` v `"1851 1999 1950 1905 2003"`|
|`(?<!` dílčí *výraz* `)`|Kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou.|`(?<!19)\d{2}\b`|`"51"``"03"` v `"1851 1999 1950 1905 2003"`|
|`(?>` dílčí *výraz* `)`|Skupina atomie.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`a `"5AB"` v `"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Kvantifikátory

Kvantifikátor určuje, kolik instancí předchozího prvku (kterým může být znak, skupina nebo třída znaků) musí být přítomných ve vstupním řetězci, aby došlo ke shodě. Kvantifikátory zahrnují prvky jazyka uvedené v následující tabulce. Další informace najdete v tématu [kvantifikátory](quantifiers-in-regular-expressions.md).

|Kvantifikátor|Popis|Vzor|Shody|
|----------------|-----------------|-------------|-------------|
|`*`|Porovná předchozí prvek nulakrát nebo vícekrát.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Porovná předchozí prvek jednou nebo vícekrát.|`"be+"`|`"bee"` v `"been"``"be"` v `"bent"`|
|`?`|Porovná předchozí prvek nulakrát nebo jedenkrát.|`"rai?n"`|`"ran"`, `"rain"`|
|`{` *n* `}`|Porovná předchozí prvek přesně *n* krát.|`",\d{3}"`|`",043"` v `"1,043.6"`, `",876"`, `",543"`a `",210"` v `"9,876,543,210"`|
|`{` *n* `,}`|Porovná předchozí prvek nejméně *n* krát.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{` *n* `,` *m* `}`|Porovná předchozí prvek nejméně *n* krát, ale ne více než *m* krát.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` v `"193024"`|
|`*?`|Porovná předchozí prvek nulakrát nebo vícekrát, ale s co nejmenším možným počtem opakování.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Porovná předchozí prvek jednou nebo vícekrát, ale s co nejmenším možným počtem opakování.|`"be+?"`|`"be"` v `"been"``"be"` v `"bent"`|
|`??`|Porovná předchozí prvek nulakrát nebo jedenkrát, ale s co nejmenším možným počtem opakování.|`"rai??n"`|`"ran"`, `"rain"`|
|`{` *n* `}?`|Porovná předchozí prvek přesně *n* krát.|`",\d{3}?"`|`",043"` v `"1,043.6"`, `",876"`, `",543"`a `",210"` v `"9,876,543,210"`|
|`{` *n* `,}?`|Porovná předchozí prvek nejméně *n* krát, ale s co nejmenším možným počtem opakování.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{` *n* `,` *m* `}?`|Porovná předchozí prvek mezi *n* a *m* krát, ale s co nejmenším možným počtem opakování.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"``"024"` v `"193024"`|

## <a name="backreference-constructs"></a>Konstrukce zpětných odkazů

Zpětné odkazy umožňují dříve porovnaným dílčím výrazům, aby byly identifikovány následně ve stejném pořadí v daném regulárním výrazu. V následující tabulce jsou uvedeny konstrukce zpětných odkazů podporované regulárními výrazy v rozhraní .NET. Další informace naleznete v tématu [konstrukce zpětných odkazů](backreference-constructs-in-regular-expressions.md).

|Konstrukce zpětných odkazů|Popis|Vzor|Shody|
|-----------------------------|-----------------|-------------|-------------|
|`\` *číslo*|Zpětný odkaz. Odpovídá hodnotě číslovaného dílčího výrazu.|`(\w)\1`|`"ee"` v `"seek"`|
|*název* `\k<` `>`|Pojmenovaný zpětný odkaz. Odpovídá hodnotě číslovaného výrazu.|`(?<char>\w)\k<char>`|`"ee"` v `"seek"`|

## <a name="alternation-constructs"></a>Konstrukce alternace

Konstrukce alternace upravují regulární výraz, aby došlo ke shodě typu buď/anebo. Tyto konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete v tématu [konstrukce alternace](alternation-constructs-in-regular-expressions.md).

|Konstrukce alternace|Popis|Vzor|Shody|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Odpovídá jakémukoli jednomu prvku oddělenému znakem svislé čáry (<code>&#124;</code>).|<code>th(e&#124;is&#124;at)</code>|`"the"``"this"` v `"this is the day."`|
|*výraz* `(?(` `)` *yes* <code>&#124;</code> *No* `)`|Odpovídá hodnotě *Ano* , pokud se vzor regulárního výrazu určeného *výrazem* shoduje; v opačném případě se shoduje s *nevolitelnou* částí. *výraz* je interpretován jako kontrolní výraz s nulovou šířkou.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"``"910"` v `"A10 C103 910"`|
|`(?(` *název* `)` *yes* <code>&#124;</code> *No* `)`|Odpovídá hodnotě *Ano* , pokud má shoda *název*, pojmenovaná nebo číslovaná zachytávající skupina; v opačném případě se shoduje s nepovinným *číslem*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "``"\"Yiska playing.jpg\""` v `"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Náhrady

Náhrady jsou prvky jazyka regulárních výrazů, které jsou podporovány ve vzorech pro nahrazení. Další informace naleznete v tématu [nahrazování](substitutions-in-regular-expressions.md). Metaznaky uvedené v následující tabulce jsou atomické kontrolní výrazy s nulovou šířkou.

|Znak|Popis|Vzor|Vzor pro nahrazování|Vstupní řetězec|Výsledný řetězec|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$` *číslo*|Nahradí podřetězec odpovídající *číslu*skupiny.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|*název* `${` `}`|Nahradí podřetězec odpovídající pojmenované skupině *Name*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Nahradí literál "$".|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Nahradí kopii celé shody.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Nahradí celý text vstupního řetězce před shodou.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Nahradí celý text vstupního řetězce za shodou.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Nahradí poslední skupinu, která byla zachycena.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Nahradí celý vstupní řetězec.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Možnosti regulárních výrazů

Můžete zadat možnosti, které řídí způsob, jakým modul regulárních výrazů interpretuje vzor regulárního výrazu. Mnohé z těchto možností lze zadat buď jako vložené (ve vzoru regulárního výrazu), nebo jako jednu nebo více <xref:System.Text.RegularExpressions.RegexOptions> konstant. Tyto stručné referenční informace uvádí pouze vložené možnosti. Další informace o vložených a <xref:System.Text.RegularExpressions.RegexOptions>ch možnostech najdete v článku [Možnosti regulárních výrazů](regular-expression-options.md).

Vloženou možnost můžete zadat dvěma způsoby:

- Pomocí `(?imnsx-imnsx)`[různých konstrukcí](miscellaneous-constructs-in-regular-expressions.md) , kde znaménko mínus (-) před možností nebo sadou možností vypne tyto možnosti. Například `(?i-mn)` zapíná porovnávání bez rozlišení velkých a malých písmen (`i`) na, zapíná víceřádkový režim (`m`) vypnuto a vypne zachycení nepojmenované skupiny (`n`). Možnost se vztahuje na vzor regulárního výrazu od bodu, ve kterém je možnost definována, a platí buď až do konce vzoru nebo do bodu, ve kterém je možnost zrušena jiným konstruktorem.
- Pomocí`)``(?imnsx-imnsx:`dílčího *výrazu* [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md) , která definuje možnosti pouze pro zadanou skupinu.

Modul regulárních výrazů .NET podporuje následující vložené možnosti:

|Možnost|Popis|Vzor|Shody|
|------------|-----------------|-------------|-------------|
|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"``"aaaAuto"` v `"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Použije víceřádkový režim. `^` a `$` odpovídají začátku a konci řádku místo začátku a konce řetězce.|Příklad naleznete v části "víceřádkový režim" v tématu [Možnosti regulárních výrazů](regular-expression-options.md).||
|`n`|Nezachytí nepojmenované skupiny.|Příklad naleznete v části "pouze explicitní zachycení" v tématu [Možnosti regulárních výrazů](regular-expression-options.md).||
|`s`|Použije jednořádkový režim.|Příklad naleznete v části "jednořádkový režim" v tématu [Možnosti regulárních výrazů](regular-expression-options.md).||
|`x`|Ignoruje prázdný znak bez řídicího znaku ve vzoru regulárního výrazu.|`\b(?x) \d+ \s \w+`|`"1 aardvark"``"2 cats"` v `"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Různé konstrukce

Různé konstrukce buď upraví vzor regulárního výrazu, nebo o tomto vzoru poskytnou informace. V následující tabulce je uveden seznam různých konstrukcí podporovaných rozhraním .NET. Další informace naleznete v tématu [různé konstrukce](miscellaneous-constructs-in-regular-expressions.md).

|Konstrukce|Definice|Příklad|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Nastaví nebo zakáže možnosti, jako je například nerozlišování velkých a malých písmen uprostřed vzoru. Další informace najdete v tématu [Možnosti regulárních výrazů](regular-expression-options.md).|`\bA(?i)b\w+\b` odpovídá `"ABA"``"Able"` v `"ABA Able Act"`|
|`(?#` *komentář* `)`|Vložený komentář. Komentář končí první pravou závorkou.|`\bA(?#Matches words starting with A)\w+\b`|
|`#` [do konce řádku]|Komentář x-mode. Komentář začíná na neřídicím `#` a pokračuje na konci řádku.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Viz také

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Regulární výrazy](regular-expressions.md)
- [Třídy regulárních výrazů](the-regular-expression-object-model.md)
- [Příklady regulárních výrazů](regular-expression-examples.md)
- [Regulární výrazy – rychlé reference (stažení ve wordovém formátu)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Regulární výrazy – rychlé reference (stažení ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
