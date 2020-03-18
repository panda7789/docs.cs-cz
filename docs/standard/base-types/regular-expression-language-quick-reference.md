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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124309"
---
# <a name="regular-expression-language---quick-reference"></a>Jazyk regulárních výrazů – stručná referenční dokumentace

Regulární výraz je vzor, který modul regulárních výrazů porovnává se vstupním textem. Vzor sestává z jednoho nebo více znakových literálů, operátorů nebo konstrukcí. Stručný úvod naleznete v tématu [.NET Regulární výrazy](regular-expressions.md).

V každé části tohoto stručného odkazu je uvedena určitá kategorie znaků, operátorů a konstrukcí, které můžete použít k definování regulárních výrazů.

Tyto informace jsme také poskytli ve dvou formátech, které si můžete stáhnout a vytisknout pro snadnou orientaci:

- [Stažení ve formátu Wordu (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Stažení ve formátu PDF (.pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Řídicí znaky

Znak zpětného\\lomítka ( ) v regulárním výrazu označuje, že znak, který za ním následuje, je buď speciální znak (jak je znázorněno v následující tabulce), nebo by měl být interpretován doslovně. Další informace naleznete v [tématu Znak escapes](character-escapes-in-regular-expressions.md).

|Řídicí znak|Popis|Vzor|Shody|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Odpovídá znaku bell \u0007.|`\a`|`"\u0007"` v `"Error!" + '\u0007'`|
|`\b`|Ve třídě znaků odpovídá znaku Backspace \u0008.|`[\b]{3,}`|`"\b\b\b\b"` v `"\b\b\b\b"`|
|`\t`|Odpovídá znaku tabulátoru \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` v`"item1\titem2\t"`|
|`\r`|Odpovídá návratovému znaku \u000D. (`\r` není ekvivalentní znaku nového řádku,.) `\n`|`\r\n(\w+)`|`"\r\nThese"` v `"\r\nThese are\ntwo lines."`|
|`\v`|Odpovídá znaku svislého tabulátoru \u000B.|`[\v]{2,}`|`"\v\v\v"` v `"\v\v\v"`|
|`\f`|Odpovídá znaku posunu strany \u000C.|`[\f]{2,}`|`"\f\f\f"` v `"\f\f\f"`|
|`\n`|Odpovídá znaku nového řádku \u000A.|`\r\n(\w+)`|`"\r\nThese"` v `"\r\nThese are\ntwo lines."`|
|`\e`|Odpovídá řídicímu znaku \u001B.|`\e`|`"\x001B"` v `"\x001B"`|
|`\`*nnn*|Používá osmičkovou reprezentaci k určení znaku (*nnn* se skládá ze dvou nebo tří číslic).|`\w\040\w`|`"a b"`, `"c d"` v`"a bc d"`|
|`\x`*nn*|Používá šestnáctkové reprezentace k určení znaku (*nn* se skládá přesně ze dvou číslic).|`\w\x20\w`|`"a b"`, `"c d"` v`"a bc d"`|
|`\c` *×*<br /><br /> `\c`*x*|Odpovídá řídicímu znaku ASCII určenému *písmenem X* nebo *x*, kde *X* nebo *x* je písmeno řídicího znaku.|`\cC`|`"\x0003"`v `"\x0003"` (Ctrl-C)|
|`\u`*nnnn*|Odpovídá znaku Unicode pomocí šestnáctkové reprezentace (přesně čtyři číslice, reprezentované *nnnn).*|`\w\u0020\w`|`"a b"`, `"c d"` v`"a bc d"`|
|`\`|V případě, že následuje znak, který není rozpoznán jako řídicí znak v této a dalších tabulkách v tomto tématu, odpovídá tomuto znaku. Například `\*` je stejný `\x2A`jako `\.` , a `\x2E`je stejný jako . To umožňuje modulregulárních výrazů rozptýlit jazykové \* prvky (například nebo ?) a literály znaků (reprezentované `\*` nebo `\?`).|`\d+[\+-x\*]\d+`|`"2+2"` a `"3*9"` v `"(2+2) * 3*9"`|

## <a name="character-classes"></a>Třídy znaků

Třída znaků odpovídá jakémukoli znaku z množiny znaků. Třídy znaků obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete v [tématu Třídy znaků](character-classes-in-regular-expressions.md).

|Třída znaků|Popis|Vzor|Shody|
|---------------------|-----------------|-------------|-------------|
|`[`*character_group*`]`|Odpovídá libovolnému znaku v *character_group*. Ve výchozím nastavení shoda rozlišuje velká a malá písmena.|`[ae]`|`"a"` v `"gray"`<br /><br /> `"a"`, `"e"` v`"lane"`|
|`[^`*character_group*`]`|Negace: Odpovídá libovolnému znaku, který není v *character_group*. Ve výchozím nastavení jsou znaky v *character_group* rozlišována malá a velká písmena.|`[^aei]`|`"r"`, `"g"` `"n"` , v`"reign"`|
|`[`*první* `-` *poslední*`]`|Rozsah znaků: Odpovídá libovolnému znaku v rozsahu od *prvního* do *posledního*.|`[A-Z]`|`"A"`, `"B"` v`"AB123"`|
|`.`|Zástupný znak: Odpovídá jakémukoli jednomu znaku s výjimkou \n.<br /><br /> Odpovídá znaku literálu období (. nebo `\u002E`), musíte před ním předcházet`\.`řídicíznak ( ).|`a.e`|`"ave"` v `"nave"`<br /><br /> `"ate"` v `"water"`|
|`\p{`*název*`}`|Odpovídá libovolnému znaku v obecné kategorii Unicode nebo pojmenovaném bloku určenému *názvem*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` v`"City Lights"`<br /><br /> `"Д"`, `"Ж"` v`"ДЖem"`|
|`\P{`*název*`}`|Odpovídá libovolnému znaku, který není v obecné kategorii Unicode nebo pojmenovaném bloku zadaném *názvem*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"` `"y"` , v`"City"`<br /><br /> `"e"`, `"m"` v`"ДЖem"`|
|`\w`|Odpovídá jakémukoli znaku slova.|`\w`|`"I"`, `"D"` `"A"`, `"1"` `"3"` , , v`"ID A1.3"`|
|`\W`|Odpovídá jakémukoli mimoslovnímu znaku.|`\W`|`" "`, `"."` v`"ID A1.3"`|
|`\s`|Odpovídá jakémukoli prázdnému znaku.|`\w\s`|`"D "` v `"ID A1.3"`|
|`\S`|Odpovídá jakémukoli neprázdnému znaku.|`\s\S`|`" _"` v `"int __ctr"`|
|`\d`|Odpovídá jakékoli desítkové číslici.|`\d`|`"4"` v `"4 = IV"`|
|`\D`|Odpovídá jakémukoli znaku kromě desítkové číslice.|`\D`|`" "`, `"="` `" "`, `"I"` `"V"` , , v`"4 = IV"`|

## <a name="anchors"></a>Kotvy

Kotvy neboli atomické kontrolní výrazy s nulovou šířkou způsobí, že porovnávání je úspěšné nebo neúspěšné v závislosti na aktuální pozici v řetězci, ale nezpůsobí, aby nástroj postupoval dále v řetězci nebo spotřebovával znaky. Metaznaky uvedené v následující tabulce jsou kotvy. Další informace naleznete v tématu [Kotvy](anchors-in-regular-expressions.md).

|Kontrolní výraz|Popis|Vzor|Shody|
|---------------|-----------------|-------------|-------------|
|`^`|Ve výchozím nastavení musí shoda začínat na začátku řetězce. ve víceřádkovém režimu, musí začínat na začátku řádku.|`^\d{3}`|`"901"` v `"901-333-"`|
|`$`|Ve výchozím nastavení musí dojít k shodě `\n` na konci řetězce nebo před na konci řetězce; ve víceřádkovém režimu, musí k němu `\n` dojít před koncem řádku nebo před koncem řádku.|`-\d{3}$`|`"-333"` v `"-901-333"`|
|`\A`|Ke shodě musí dojít na začátku řetězce.|`\A\d{3}`|`"901"` v `"901-333-"`|
|`\Z`|Shoda musí dojít na konci řetězce `\n` nebo před na konci řetězce.|`-\d{3}\Z`|`"-333"` v `"-901-333"`|
|`\z`|Ke shodě musí dojít na konci řetězce.|`-\d{3}\z`|`"-333"` v `"-901-333"`|
|`\G`|Ke shodě musí dojít v místě, kde byla ukončena předchozí shoda.|`\G\(\d\)`|`"(1)"`, `"(3)"` `"(5)"` , v`"(1)(3)(5)[7](9)"`|
|`\b`|Shoda musí probíhat na hranici mezi `\w` (alfanumerický) a `\W` (nealfanumerické) znak.|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` v`"them theme them them"`|
|`\B`|Shoda nesmí dojít na `\b` hranici.|`\Bend\w*\b`|`"ends"`, `"ender"` v`"end sends endure lender"`|

## <a name="grouping-constructs"></a>Seskupovací konstrukce

Seskupovací konstrukce vymezují dílčí výrazy regulárních výrazů a obvykle zachytávají podřetězce vstupního řetězce. Seskupovací konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete v [tématu Seskupování konstrukcí](grouping-constructs-in-regular-expressions.md).

|Seskupovací konstrukce|Popis|Vzor|Shody|
|------------------------|-----------------|-------------|-------------|
|`(`*dílčí výraz*`)`|Zachycuje porovnané dílčí výrazy a přiřazuje jim řadové číslovky od jedné.|`(\w)\1`|`"ee"` v `"deep"`|
|`(?<`*podvýraz* `>` *název*`)`|Zachycuje porovnaný dílčí výraz do pojmenované skupiny.|`(?<double>\w)\k<double>`|`"ee"` v `"deep"`|
|`(?<`*název1* `-` *podvýraz* *name2* `>``)`|Určuje definici vyrovnávací skupiny. Další informace naleznete v části Definice vyrovnávací skupiny v části [Seskupování konstrukcí](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` v `"3+2^((1-3)*(3-1))"`|
|`(?:`*dílčí výraz*`)`|Definuje skupinu bez zachytávání.|`Write(?:Line)?`|`"WriteLine"` v `"Console.WriteLine()"`<br /><br /> `"Write"` v `"Console.Write(value)"`|
|`(?imnsx-imnsx:`*dílčí výraz*`)`|Použije nebo zakáže zadané možnosti v rámci *dílčího výrazu*. Další informace naleznete v [tématu Možnosti regulárního výrazu](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` v`"A12xl A12XL a12xl"`|
|`(?=`*dílčí výraz*`)`|Kontrolní výraz pozitivního dopředného vyhledávání s nulovou šířkou.|`\w+(?=\.)`|`"is"`, `"ran"`a `"out"` v`"He is. The dog ran. The sun is out."`|
|`(?!`*dílčí výraz*`)`|Kontrolní výraz negativního dopředného vyhledávání s nulovou šířkou.|`\b(?!un)\w+\b`|`"sure"`, `"used"` v`"unsure sure unity used"`|
|`(?<=`*dílčí výraz*`)`|Kontrolní výraz pozitivního zpětného vyhledávání s nulovou šířkou.|`(?<=19)\d{2}\b`|`"99"`, `"50"` `"05"` , v`"1851 1999 1950 1905 2003"`|
|`(?<!`*dílčí výraz*`)`|Kontrolní výraz negativního zpětného vyhledávání s nulovou šířkou.|`(?<!19)\d{2}\b`|`"51"`, `"03"` v`"1851 1999 1950 1905 2003"`|
|`(?>`*dílčí výraz*`)`|Atomová skupina.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`a `"5AB"` v`"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Kvantifikátory

Kvantifikátor určuje, kolik instancí předchozího prvku (kterým může být znak, skupina nebo třída znaků) musí být přítomných ve vstupním řetězci, aby došlo ke shodě. Kvantifikátory zahrnují prvky jazyka uvedené v následující tabulce. Další informace naleznete [v tématu Kvantifikátory](quantifiers-in-regular-expressions.md).

|Kvantifikátor|Popis|Vzor|Shody|
|----------------|-----------------|-------------|-------------|
|`*`|Porovná předchozí prvek nulakrát nebo vícekrát.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Porovná předchozí prvek jednou nebo vícekrát.|`"be+"`|`"bee"`v `"been"` `"be"` , v`"bent"`|
|`?`|Porovná předchozí prvek nulakrát nebo jedenkrát.|`"rai?n"`|`"ran"`, `"rain"`|
|`{`*n*`}`|Odpovídá předchozímu prvku přesně *n* krát.|`",\d{3}"`|`",043"`v `"1,043.6"` `",876"`, `",543"`, `",210"` a v`"9,876,543,210"`|
|`{`*n*`,}`|Odpovídá předchozímu prvku alespoň *nkrát.*|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}`|Odpovídá předchozímu prvku alespoň *nkrát,* ale ne více než *m* krát.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` v `"193024"`|
|`*?`|Porovná předchozí prvek nulakrát nebo vícekrát, ale s co nejmenším možným počtem opakování.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Porovná předchozí prvek jednou nebo vícekrát, ale s co nejmenším možným počtem opakování.|`"be+?"`|`"be"`v `"been"` `"be"` , v`"bent"`|
|`??`|Porovná předchozí prvek nulakrát nebo jedenkrát, ale s co nejmenším možným počtem opakování.|`"rai??n"`|`"ran"`, `"rain"`|
|`{`*n*`}?`|Odpovídá předchozí prvek přesně *n* krát.|`",\d{3}?"`|`",043"`v `"1,043.6"` `",876"`, `",543"`, `",210"` a v`"9,876,543,210"`|
|`{`*n*`,}?`|Odpovídá předchozímu prvku alespoň *nkrát,* ale co nejméněkrát.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}?`|Odpovídá předchozí prvek mezi *n* a *m* krát, ale co nejméně krát, jak je to možné.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` v`"193024"`|

## <a name="backreference-constructs"></a>Konstrukce zpětných odkazů

Zpětné odkazy umožňují dříve porovnaným dílčím výrazům, aby byly identifikovány následně ve stejném pořadí v daném regulárním výrazu. V následující tabulce jsou uvedeny konstrukce zpětného odkazu podporované regulárními výrazy v rozhraní .NET. Další informace naleznete [v tématu Backreference Constructs](backreference-constructs-in-regular-expressions.md).

|Konstrukce zpětných odkazů|Popis|Vzor|Shody|
|-----------------------------|-----------------|-------------|-------------|
|`\`*číslo*|Zpětný odkaz. Odpovídá hodnotě číslovaného dílčího výrazu.|`(\w)\1`|`"ee"` v `"seek"`|
|`\k<`*název*`>`|Pojmenovaný zpětný odkaz. Odpovídá hodnotě číslovaného výrazu.|`(?<char>\w)\k<char>`|`"ee"` v `"seek"`|

## <a name="alternation-constructs"></a>Konstrukce alternace

Konstrukce alternace upravují regulární výraz, aby došlo ke shodě typu buď/anebo. Tyto konstrukce obsahují prvky jazyka uvedené v následující tabulce. Další informace naleznete [v tématu Alternation Constructs](alternation-constructs-in-regular-expressions.md).

|Konstrukce alternace|Popis|Vzor|Shody|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Odpovídá libovolnému prvku oddělenému<code>&#124;</code>znakem svislého pruhu ( ).|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` v`"this is the day."`|
|`(?(`*výraz* `)` *ano* <code>&#124;</code> *ne*`)`|Odpovídá *ano,* pokud se porovnává vzor regulárního výrazu určený *výrazem;* v opačném případě odpovídá volitelné *žádné* části. *výraz* je interpretován jako kontrolní výraz s nulovou šířkou.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` v`"A10 C103 910"`|
|`(?(`*jméno* `)` *ano* <code>&#124;</code> *ne*`)`|Odpovídá *ano,* pokud *název*, pojmenovaná nebo číslovaná zachytávající skupina, má shodu; v opačném případě odpovídá volitelnému *no*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` v`"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Náhrady

Náhrady jsou prvky jazyka regulárních výrazů, které jsou podporovány ve vzorech pro nahrazení. Další informace naleznete v [tématu Substituce](substitutions-in-regular-expressions.md). Metaznaky uvedené v následující tabulce jsou atomické kontrolní výrazy s nulovou šířkou.

|Znak|Popis|Vzor|Vzor pro nahrazování|Vstupní řetězec|Výsledný řetězec|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$`*číslo*|Nahradí podřetězec odpovídající *číslu*skupiny .|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|`${`*název*`}`|Nahradí podřetězec odpovídající názvu pojmenované *skupiny*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Nahradí literál "$".|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Nahradí kopii celé shody.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Nahradí celý text vstupního řetězce před shodou.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Nahradí celý text vstupního řetězce za shodou.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Nahradí poslední skupinu, která byla zachycena.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Nahradí celý vstupní řetězec.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Možnosti regulárních výrazů

Můžete zadat možnosti, které řídí způsob, jakým modul regulárních výrazů interpretuje vzor regulárního výrazu. Mnohé z těchto možností lze zadat buď vřadit (ve vzoru <xref:System.Text.RegularExpressions.RegexOptions> regulárního výrazu), nebo jako jednu nebo více konstant. Tyto stručné referenční informace uvádí pouze vložené možnosti. Další informace o vřádích a <xref:System.Text.RegularExpressions.RegexOptions> možnostech naleznete v článku [Možnosti regulárního výrazu](regular-expression-options.md).

Vloženou možnost můžete zadat dvěma způsoby:

- Pomocí [různé konstrukce](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, kde znaménko mínus (-) před možností nebo sadou možností tyto možnosti vypne. Například `(?i-mn)` zapne párování bez rozlišování velkých a malých písmen (`i`) , vypne víceřádkový režim (`m`) a vypne nepojmenované zachycení skupiny (`n`). Možnost se vztahuje na vzor regulárního výrazu od bodu, ve kterém je možnost definována, a platí buď až do konce vzoru nebo do bodu, ve kterém je možnost zrušena jiným konstruktorem.
- Pomocí`(?imnsx-imnsx:`*podvýrazu*`)` [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md), který definuje možnosti pouze pro zadanou skupinu.

Modul regulárních výrazů .NET podporuje následující vsazené možnosti:

|Možnost|Popis|Vzor|Shody|
|------------|-----------------|-------------|-------------|
|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` v`"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Použije víceřádkový režim. `^`a `$` porovnejte začátek a konec řádku namísto začátku a konce řetězce.|Příklad naleznete v části Víceřádkový režim v [části Možnosti regulárního výrazu](regular-expression-options.md).||
|`n`|Nezachytí nepojmenované skupiny.|Příklad naleznete v části "Pouze explicitní zachycení" v [možnostech regulárního výrazu](regular-expression-options.md).||
|`s`|Použije jednořádkový režim.|Příklad naleznete v části Jednořádkový režim v [části Možnosti regulárního výrazu](regular-expression-options.md).||
|`x`|Ignoruje prázdný znak bez řídicího znaku ve vzoru regulárního výrazu.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` v`"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Různé konstrukce

Různé konstrukce buď upraví vzor regulárního výrazu, nebo o tomto vzoru poskytnou informace. V následující tabulce jsou uvedeny různé konstrukce podporované rozhraním .NET. Další informace naleznete v tématu [Různé konstrukce](miscellaneous-constructs-in-regular-expressions.md).

|Konstrukce|Definice|Příklad|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Nastaví nebo zakáže možnosti, jako je například nerozlišování velkých a malých písmen uprostřed vzorku. Další informace naleznete v [tématu Možnosti regulárního výrazu](regular-expression-options.md).|`\bA(?i)b\w+\b``"ABA"`zápasy `"Able"` , v`"ABA Able Act"`|
|`(?#`*komentář*`)`|Vložený komentář. Komentář končí první pravou závorkou.|`\bA(?#Matches words starting with A)\w+\b`|
|`#`[do konce řádku]|Komentář x-mode. Komentář začíná na unescaped `#` a pokračuje na konec řádku.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Viz také

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Regulární výrazy](regular-expressions.md)
- [Třídy regulárních výrazů](the-regular-expression-object-model.md)
- [Příklady regulárních výrazů](regular-expression-examples.md)
- [Regulární výrazy – stručná reference (stáhnout ve formátu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Regulární výrazy - stručná reference (stáhnout ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
