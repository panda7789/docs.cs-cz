---
title: Referenční dokumentace symbolů a operátorů
description: 'Přečtěte si o symbolech a operátorech, které jsou používány v programovacím jazyce F #.'
ms.date: 02/11/2019
fl_keywords:
- '|>_FS'
ms.openlocfilehash: 4c3af80e8f5a686535b7c09579d29bb3da8591a3
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855386"
---
# <a name="symbol-and-operator-reference"></a>Reference k symbolům a operátorovi

Tento článek obsahuje tabulku symbolů a operátorů, které jsou používány v jazyce F #.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="table-of-symbols-and-operators"></a>Tabulka symbolů a operátorů

V následující tabulce jsou popsány symboly používané v jazyce F # a stručný popis některých použití symbolů a odkazů pro další informace. Symboly jsou seřazené podle řazení znakové sady ASCII.

|Symbol nebo operátor|Odkazy|Popis|
|------------------|-----|-----------|
|`!`|[Referenční buňky](../reference-cells.md)<br /><br />[Výpočetní výrazy](../computation-expressions.md)|<ul><li>Odkázat na odkazovou buňku.<br /></li><li>Po klíčovém slově indikuje upravenou verzi chování klíčového slova, jak je řízeno pracovním postupem.<br /></li></ul>|
|`!=`||<ul><li>Nepoužívá se v F #. Použijte `<>` pro operace nerovnosti.<br /></li></ul>|
|`"`|[Literály](../literals.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Odděluje textový řetězec.<br /></li></ul>|
|`"""`|[Řetězce](../strings.md)|Odděluje textový řetězec na doslovné hodnoty. Se liší od `@"..."` v tom, že můžete označit znak uvozovky pomocí jediné uvozovky v řetězci.|
|`#`|[Direktivy kompilátoru](../compiler-directives.md)<br /><br />[Flexibilní typy](../flexible-types.md)|<ul><li>Vytvoří předponu direktivy preprocesoru nebo kompilátoru, například `#light` .<br /></li><li>Při použití s typem, označuje *flexibilní typ*, který odkazuje na typ nebo některý z jeho odvozených typů.<br /></li></ul>|
|`$`||<ul><li>Používá se interně pro určité názvy proměnných a funkcí generovaných kompilátorem.<br /></li></ul>|
|`%`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Uvozovky kódu](../code-quotations.md)|<ul><li>Vypočítá celočíselný zbytek.<br /></li><li>Používá se pro spojování výrazů v uvozovkách psaní kódu.<br /></li></ul>|
|`%%`|[Uvozovky kódu](../code-quotations.md)|<ul><li>Používá se pro spojování výrazů do netypových nabídek kódu.<br /></li></ul>|
|`%?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá celočíselný zbytek, pokud je pravá strana typ s možnou hodnotou null.<br /></li></ul>|
|`&`|[Výrazy shody](../match-expressions.md)|<ul><li>Vypočítá adresu proměnlivé hodnoty pro použití při spolupráci s jinými jazyky.<br /></li><li>Používá se v vzorech a.<br /></li></ul>|
|`&&`|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá logickou hodnotu a operaci.<br /></li></ul>|
|`&&&`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitovou a operaci.<br /></li></ul>|
|`'`|[Literály](../literals.md)<br /><br />[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Odděluje literál s jedním znakem.<br /></li><li>Označuje parametr obecného typu.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>||<ul><li>Odděluje identifikátor, který by jinak neměl být platným identifikátorem, například klíčové slovo jazyka.<br /></li></ul>|
|`( )`|[Typ jednotky](../unit-type.md)|<ul><li>Představuje jednu hodnotu typu jednotky.<br /></li></ul>|
|`(...)`|[N-tice](../tuples.md)<br /><br />[Přetížení operátoru](../operator-overloading.md)|<ul><li>Určuje pořadí, ve kterém jsou výrazy vyhodnocovány.<br /></li><li>Naomezuje řazenou kolekci členů.<br /></li><li>Používá se v definicích operátorů.<br /></li></ul>|
|`(*...*)`||<ul><li>Odděluje komentář, který může být rozložen na více řádků.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Aktivní vzory](../active-patterns.md)|<ul><li>Odděluje aktivní vzor. Označují se také jako *klipy banánů*.<br /></li></ul>|
|`*`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[N-tice](../tuples.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Při použití jako binárního operátoru vynásobí levou a pravou stranu.<br /></li><li>V typech označuje párování v řazené kolekci členů.<br /></li><li>Používá se v jednotkách typů míry.<br /></li></ul>|
|`*?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vynásobí levou a pravou stranu, pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`**`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá operaci umocnění ( `x ** y` znamená `x` mocninu `y` ).<br /></li></ul>|
|`+`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Při použití jako binárního operátoru přidá levou a pravou stranu.<br /></li><li>Při použití jako unární operátor označuje kladné množství. (Formálně vytvoří stejnou hodnotu s znaménkem beze změny.)<br /></li></ul>|
|`+?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Přidá levou a pravou stranu, pokud je pravá strana typ s možnou hodnotou null.<br /></li></ul>|
|`,`|[N-tice](../tuples.md)|<ul><li>Odděluje prvky řazené kolekce členů nebo parametry typu.<br /></li></ul>|
|`-`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Při použití jako binárního operátoru odečte pravou stranu od levé strany.<br /></li><li>Při použití jako unární operátor provádí operaci negace.<br /></li></ul>|
|`-?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ododečte pravou stranu od levé strany, pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`->`|[Functions](../functions/index.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>V typech funkcí odděluje argumenty a návratové hodnoty.<br /></li><li>Vypočítá výraz (ve výrazech sekvence); ekvivalent `yield` klíčového slova.<br /></li><li>Používá se ve výrazech shody.<br /></li></ul>|
|`.`|[Členové](../members/index.md)<br /><br />[Primitivní typy](../basic-types.md)|<ul><li>Přistupuje ke členu a odděluje jednotlivé názvy v plně kvalifikovaném názvu.<br /></li><li>Určuje desetinnou čárku v číslech s plovoucí desetinnou čárkou.<br /></li></ul>|
|`..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah.<br /></li></ul>|
|`.. ..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah spolu s přírůstky.<br /></li></ul>|
|`.[...]`|[Pole](../arrays.md)|<ul><li>Přistupuje k elementu pole.<br /></li></ul>|
|`/`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Vydělí levou stranu (čitatel) na pravé straně (jmenovatel).<br /></li><li>Používá se v jednotkách typů míry.<br /></li></ul>|
|`/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vydělí levou stranu na pravé straně, pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`//`||<ul><li>Označuje začátek jednořádkového komentáře.<br /></li></ul>|
|`///`|[Dokumentace XML](../xml-documentation.md)|<ul><li>Označuje komentář XML.<br /></li></ul>|
|`:`|[Functions](../functions/index.md)|<ul><li>V anotaci typu odděluje parametr nebo název člena z jeho typu.<br /></li></ul>|
|`::`|[Seznamy](../lists.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>Vytvoří seznam. Element na levé straně je před seznamem na pravé straně.<br /></li><li>Používá se v porovnávání vzorů k oddělení částí seznamu.<br /></li></ul>|
|`:=`|[Referenční buňky](../reference-cells.md)|<ul><li>Přiřadí hodnotu k referenční buňce.<br /></li></ul>|
|`:>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převede typ na typ, který je v hierarchii vyšší.<br /></li></ul>|
|`:?`|[Výrazy shody](../match-expressions.md)|<ul><li>Vrátí, `true` zda hodnota odpovídá zadanému typu (včetně, pokud se jedná o podtyp); v opačném případě vrátí `false` (Type test operator).<br /></li></ul>|
|`:?>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převede typ na typ, který je níže v hierarchii.<br /></li></ul>|
|`;`|[Podrobná syntaxe](../verbose-syntax.md)<br /><br />[Seznamy](../lists.md)<br /><br />[Záznamy](../records.md)|<ul><li>Odděluje výrazy (používá se hlavně v podrobné syntaxi).<br /></li><li>Odděluje prvky seznamu.<br /></li><li>Odděluje pole záznamu.<br /></li></ul>|
|`<`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá méně než operaci.<br /></li></ul>|
|`<?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|Vypočítá méně než operaci, pokud je pravá strana typ s možnou hodnotou null.|
|`<<`|[Functions](../functions/index.md)|<ul><li>Sestaví dvě funkce v obráceném pořadí; Druhá se spustí jako první (operátor zpětného skládání).<br /></li></ul>|
|`<<<`|[Bitové operátory](bitwise-operators.md)|<ul><li>Posune bity v množství na levé straně doleva o počet bitů určených na pravé straně.<br /></li></ul>|
|`<-`|[Hodnoty](../values/index.md)|<ul><li>Přiřadí hodnotu proměnné.<br /></li></ul>|
|`<...>`|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Zamezí parametry typu.<br /></li></ul>|
|`<>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` , zda levá strana není rovna pravé straně. v opačném případě vrátí hodnotu false.<br /></li></ul>|
|`<>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci nerovnosti, pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`<=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` , zda je levá strana menší než nebo rovna pravé straně. v opačném případě vrátí hodnotu `false` .<br /></li></ul>|
|`<=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci "menší než nebo rovno", pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|<code>&lt;&#124;</code>|[Functions](../functions/index.md)|<ul><li>Předá výsledek výrazu na pravé straně k funkci na levé straně (operátor zpětného posunu).<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[Operators. &#40; &#60;&#124;&#124; &#41;&#60; t 1, t 2, "U&#62; funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá do funkce na levé straně řazené kolekce členů dvou argumentů na pravé straně.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operators. &#40; &#60;&#124;&#124;&#124; &#41;&#60; t 1, t 2, t 3, ' U&#62; funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá do funkce na levé straně řazené kolekce členů tří argumentů na pravé straně.<br /></li></ul>|
|`<@...@>`|[Uvozovky kódu](../code-quotations.md)|<ul><li>Odděluje citaci typového kódu.<br /></li></ul>|
|`<@@...@@>`|[Uvozovky kódu](../code-quotations.md)|<ul><li>Odděluje citaci netypového kódu.<br /></li></ul>|
|`=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí, `true` zda je levá strana rovna pravé straně. v opačném případě vrátí hodnotu `false` .<br /></li></ul>|
|`=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci EQUAL, pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`==`||<ul><li>Nepoužívá se v F #. Použijte `=` pro operace rovnosti.<br /></li></ul>|
|`>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí, `true` zda je levá strana větší než pravá strana. v opačném případě vrátí hodnotu `false` .<br /></li></ul>|
|`>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci "větší než", pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`>>`|[Functions](../functions/index.md)|<ul><li>Vytvoří dvě funkce (operátor předávaného skládání).<br /></li></ul>|
|`>>>`|[Bitové operátory](bitwise-operators.md)|<ul><li>Posune bity v množství na levé straně vpravo o počet míst určených na pravé straně.<br /></li></ul>|
|`>=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` , zda je levá strana větší než nebo rovna pravé straně. v opačném případě vrátí hodnotu `false` .<br /></li></ul>|
|`>=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci "větší než nebo rovno", pokud je pravá strana typem s možnou hodnotou null.<br /></li></ul>|
|`?`|[Parametry a argumenty](../parameters-and-arguments.md)|<ul><li>Určuje nepovinný argument.<br /></li><li>Slouží jako operátor pro volání dynamické metody a vlastností. Musíte zadat vlastní implementaci.<br /></li></ul>|
|`? ... <- ...`||<ul><li>Slouží jako operátor pro nastavení dynamických vlastností. Musíte zadat vlastní implementaci.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalent k odpovídajícím operátorům bez? prefix, kde je na levé straně typ s možnou hodnotou null.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalent k odpovídajícím operátorům bez? Přípona, kde je na pravé straně typ s možnou hodnotou null.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Odpovídá odpovídajícím operátorům bez okolních otazníků, kde jsou obě strany typy s možnou hodnotou null.<br /></li></ul>|
|`@`|[Seznamy](../lists.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Zřetězí dva seznamy.<br /></li><li>Při umístění před řetězcovým literálem označuje, že řetězec má být interpretován doslovné, bez interpretace řídicích znaků.<br /></li></ul>|
|`[...]`|[Seznamy](../lists.md)|<ul><li>Odděluje prvky seznamu.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Pole](../arrays.md)|<ul><li>Odděluje prvky pole.<br /></li></ul>|
|`[<...>]`|[Atributy](../attributes.md)|<ul><li>Naomezuje atribut.<br /></li></ul>|
|`\`|[Řetězce](../strings.md)|<ul><li>Řídí další znak; používá se ve znakových a řetězcových literálech.<br /></li></ul>|
|`^`|[Statisticky vyřešené parametry typu](../generics/statically-resolved-type-parameters.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Určuje parametry typu, které musí být vyřešeny v době kompilace, nikoli za běhu.<br /></li><li>Zřetězí řetězce.<br /></li></ul>|
|`^^^`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitovou exkluzivní operaci nebo.<br /></li></ul>|
|`_`|[Výrazy shody](../match-expressions.md)<br /><br />[Obecné typy](../generics/index.md)|<ul><li>Označuje vzor zástupného znaku.<br /></li><li>Určuje anonymní obecný parametr.<br /></li></ul>|
|<code>&#96;</code>|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Používá se interně k označení parametru obecného typu.<br /></li></ul>|
|`{...}`|[Sekvence](../sequences.md)<br /><br />[Záznamy](../records.md)|<ul><li>Odděluje výrazy sekvence a výpočetní výrazy.<br /></li><li>Používá se v definicích záznamů.<br /></li></ul>|
|<code>&#124;</code>|[Výrazy shody](../match-expressions.md)|<ul><li>Odděluje jednotlivé případy shody, jednotlivé rozlišené případy sjednocení a výčtové hodnoty.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá logickou hodnotu nebo operaci.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá logickou operaci nebo.<br /></li></ul>|
|<code>&#124;></code>|[Functions](../functions/index.md)|<ul><li>Předá výsledek levé strany na funkci na pravé straně (operátor přesměrování přesměrování).<br /></li></ul>|
|<code>&#124;&#124;></code>|[Operators. &#40; &#124;&#124;&#62; &#41;&#60; t 1, t 2, "U&#62; funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá do funkce na pravé straně řazené kolekce členů dvou argumentů na levé straně.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[Operators. &#40; &#124;&#124;&#124;&#62; &#41;&#60; t 1, t 2, t 3, ' U&#62; funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá do funkce na pravé straně řazenou kolekci členů tří argumentů na levé straně.<br /></li></ul>|
|`~~`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro unární operátor negace.<br /></li></ul>|
|`~~~`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitovou nefunkčnost.<br /></li></ul>|
|`~-`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro unární operátor minus.<br /></li></ul>|
|`~+`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro operátor unárního znaménka.<br /></li></ul>|

## <a name="operator-precedence"></a>Priorita operátorů

Následující tabulka ukazuje pořadí priorit operátorů a dalších klíčových slov výrazu v jazyce F # v pořadí od nejnižší priority po nejvyšší prioritu. V případě potřeby je také uveden seznam asociativita.

|Operátor|Asociativita|
|--------|-------------|
|`as`|Vpravo|
|`when`|Vpravo|
|<code>&#124;</code>příkazem|Left|
|`;`|Vpravo|
|`let`|Neasociativní|
|`function`, `fun`, `match`, `try`|Neasociativní|
|`if`|Neasociativní|
|`not`|Vpravo|
|`->`|Vpravo|
|`:=`|Vpravo|
|`,`|Neasociativní|
|`or`, <code>&#124;&#124;</code>|Left|
|`&`, `&&`|Left|
|`:>`, `:?>`|Vpravo|
|`<`*op*, `>` *op*, `=` , <code>&#124;</code> *op*, `&` *op*,`&`<br /><br />(včetně `<<<` , `>>>` , <code>&#124;&#124;&#124;</code> , `&&&` )|Left|
|`^`*evřít*<br /><br />(včetně `^^^` )|Vpravo|
|`::`|Vpravo|
|`:?`|Neasociativní|
|`-`*op*, `+` *op*|Platí pro vpony používání těchto symbolů|
|`*`*op*, `/` *op*, `%` *op*|Left|
|`**`*evřít*|Vpravo|
|`f x`(aplikace funkcí)|Left|
|<code>&#124;</code>(porovnávání vzorů)|Vpravo|
|operátory předpony ( `+` *op*, `-` *op*, `%` , `%%` , `&` , `&&` , `!` *op*, `~` *op*)|Left|
|`.`|Left|
|`f(x)`|Left|
|`f<`*druhy*`>`|Left|

Jazyk F # podporuje přetížení vlastního operátoru. To znamená, že můžete definovat vlastní operátory. V předchozí tabulce *op* může být jakákoli platná (možná prázdná) sekvence znaků operátoru, buď předdefinované, nebo definované uživatelem. Proto můžete použít tuto tabulku k určení, kterou posloupnost znaků použít pro vlastní operátor, abyste dosáhli požadované úrovně priority. Úvodní `.` znaky jsou ignorovány, pokud kompilátor určí přednost.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](../index.md)
- [Přetížení operátoru](../operator-overloading.md)
