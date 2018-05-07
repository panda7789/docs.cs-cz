---
title: Referenční dokumentace symbolů a operátorů (F#)
description: 'Další informace o operátory, které se používají v programovací jazyk F # a symboly.'
ms.date: 04/04/2018
ms.openlocfilehash: 79518b990f3a5c794f7658490bdadc2d5b985504
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="symbol-and-operator-reference"></a>Referenční dokumentace symbolů a operátorů

> [!NOTE]
Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Toto téma obsahuje tabulku symboly a operátory, které se používají v jazyce F #.

## <a name="table-of-symbols-and-operators"></a>Tabulka symbolů a operátorů
Následující tabulka popisuje symboly použité v jazyce F #, obsahuje odkazy na témata, které poskytují další informace a obsahuje stručný popis některých používá symbolu. Symboly jsou seřazené podle řazení sadu znaků ASCII.

|Symbol or – operátor|Odkazy|Popis|
|------------------|-----|-----------|
|`!`|[Referenční buňky](../reference-cells.md)<br /><br />[Výpočetní výrazy](../computation-expressions.md)|<ul><li>Dereferences odkaz na buňku.<br /></li><li>Po klíčové slovo označuje upravenou verzi – klíčové slovo chování řízený pracovního postupu.<br /></li><ul/>|
|`!=`|Nelze použít.|<ul><li>Nepoužívá se v jazyce F #. Použití `<>` pro nerovnosti operace.<br /></li><ul/>|
|`"`|[Literály](../literals.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Vymezuje textového řetězce.<br /></li><ul/>|
|`"""`|[Řetězce](../strings.md)|Vymezuje typu verbatim textového řetězce. Se liší od `@"..."` , můžete určit znak dvojité uvozovky, pomocí v jednoduchých uvozovkách v řetězci.|
|`#`|[Direktivy kompilátoru](../compiler-directives.md)<br /><br />[Flexibilní typy](../flexible-types.md)|<ul><li>Například předpony direktivu preprocesor nebo kompilátoru `#light`.<br /></li><li>Při použití s typem, označuje *flexibilní typu*, které odkazuje na určitý typ nebo jeden z jeho odvozených typů.<br /></li><ul/>|
|`$`|Není k dispozici žádné další informace.|<ul><li>Interně používá k určité generované kompilátorem proměnná názvy a funkcí.<br /></li><ul/>|
|`%`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Citace kódu](../code-quotations.md)|<ul><li>Vypočítá zbytek celé číslo.<br /></li><li>Použít pro splétání výrazy do uvozovky typové kódu.<br /></li><ul/>|
|`%%`|[Citace kódu](../code-quotations.md)|<ul><li>Použít pro splétání výrazy do netypový kód uvozovky.<br /></li><ul/>|
|`%?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá zbytek celé číslo, když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`&`|[Výrazy shody](../match-expressions.md)|<ul><li>Vypočítá adresu měnitelný hodnoty pro použití při vzájemné spolupráci s jinými jazyky.<br /></li><li>Použít v a vzory.<br /></li><ul/>|
|`&&`|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá Boolean a operace.<br /></li><ul/>|
|`&&&`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitové operace AND.<br /></li><ul/>|
|`'`|[Literály](../literals.md)<br /><br />[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Vymezuje literál délce jednoho znaku.<br /></li><li>Označuje parametr obecného typu.<br /></li><ul/>|
|<code>&#96;&#96;...&#96;&#96;</code>|Není k dispozici žádné další informace.|<ul><li>Vymezuje identifikátor, který by jinak právní identifikátor, jako je například klíčové slovo jazyka.<br /></li><ul/>|
|`( )`|[Typ jednotky](../unit-type.md)|<ul><li>Představuje jednu hodnotu typu jednotky.<br /></li><ul/>|
|`(...)`|[Řazené kolekce členů](../tuples.md)<br /><br />[Přetížení operátoru](../operator-overloading.md)|<ul><li>Určuje pořadí, ve kterém se vyhodnotí výrazy.<br /></li><li>Vymezuje řazené kolekce členů.<br /></li><li>Použít v definicích operátor.<br /></li><ul/>|
|`(*...*)`||<ul><li>Vymezuje komentář, který může zahrnovat více řádků.<br /></li><ul/>|
|<code>(&#124;...&#124;)</code>|[Aktivní vzory](../active-patterns.md)|<ul><li>Vymezuje aktivní vzor. Označuje taky jako *banánů klipů*.<br /></li><ul/>|
|`*`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Řazené kolekce členů](../tuples.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Pokud se použije jako binární operátor, vynásobí levé a pravé straně.<br /></li><li>Typy označuje párování v řazené kolekce členů.<br /></li><li>Použít v jednotkách míry.<br /></li><ul/>|
|`*?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vynásobí levé a pravé straně, když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`**`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá operaci exponenciální zápis (`x ** y` znamená `x` exponentem `y`).<br /></li><ul/>|
|`+`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Pokud se použije jako binární operátor, přidá levé a pravé straně.<br /></li><li>Když se použije jako unární operátor, označuje kladné množství. (Dříve, vyvolá se stejnou hodnotou znakem beze změny.)<br /></li><ul/>|
|`+?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Přidá levé a pravé straně, když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`,`|[Řazené kolekce členů](../tuples.md)|<ul><li>Oddělí prvky řazené kolekce členů, nebo parametry typu.<br /></li><ul/>|
|`-`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Pokud se použije jako binární operátor, odečítá od pravé straně z levé strany.<br /></li><li>Když se použije jako unární operátor, provede operaci negace.<br /></li><ul/>|
|`-`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Odečítá od pravé straně z levé strany, když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`->`|[Funkce](../functions/index.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>Ve funkci typy, vymezuje argumenty a návratové hodnoty.<br /></li><li>Vypočítá výraz (v pořadí výrazy); ekvivalentní `yield` – klíčové slovo.<br /></li><li>Použít ve výrazech porovnání<br /></li><ul/>|
|`.`|[Členové](../members/index.md)<br /><br />[Primitivní typy](../primitive-types.md)|<ul><li>Přístupy člena a odděluje jednotlivé názvy ve plně kvalifikovaný název.<br /></li><li>Čísla s plovoucí desetinnou určuje desetinné čárky.<br /></li><ul/>|
|`..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah.<br /></li><ul/>|
|`.. ..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah společně s vyšší.<br /></li><ul/>|
|`.[...]`|[Pole](../arrays.md)|<ul><li>Umožňuje přístup k elementu pole.<br /></li><ul/>|
|`/`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Rozdělí na levé straně (dělenec) podle pravé straně (jmenovatel).<br /></li><li>Použít v jednotkách míry.<br /></li><ul/>|
|`/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vydělí na levé straně podle pravé straně, když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`//`||<ul><li>Označuje začátek komentáře jeden řádek.<br /></li><ul/>|
|`///`|[Dokumentace XML](../xml-documentation.md)|<ul><li>Označuje komentáře jazyka XML.<br /></li><ul/>|
|`:`|[Funkce](../functions/index.md)|<ul><li>V anotaci typu odděluje názvu parametru nebo člena z jeho typu.<br /></li><ul/>|
|`::`|[Seznamy](../lists.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>Vytvoří seznam. Před elementu na levé straně se zobrazí v seznamu na pravé straně.<br /></li><li>Používá se v porovnávání vzorů jednotlivé části seznamu.<br /></li><ul/>|
|`:=`|[Referenční buňky](../reference-cells.md)|<ul><li>Odkaz na buňku přiřazuje hodnotu.<br /></li><ul/>|
|`:>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převádí typu pro typ, který je v hierarchii.<br /></li><ul/>|
|`:?`|[Výrazy shody](../match-expressions.md)|<ul><li>Vrátí `true` Pokud hodnota odpovídá zadaný typ; jinak vrátí `false` (operátor typu test).<br /></li><ul/>|
|`:?>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převede typu typ, který je nižší úrovni v hierarchii.<br /></li><ul/>|
|`;`|[Podrobná syntaxe](../verbose-syntax.md)<br /><br />[Seznamy](../lists.md)<br /><br />[Záznamy](../records.md)|<ul><li>Odděluje výrazy (používá nejčastěji v podrobná syntaxe).<br /></li><li>Odděluje prvků seznamu.<br /></li><li>Odděluje polí záznamu.<br /></li><ul/>|
|`<`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá je menší – než operaci.<br /></li><ul/>|
|`<?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|Vypočítá je menší než operaci, když na pravé straně je typ s možnou hodnotou Null.|
|`<<`|[Funkce](../functions/index.md)|<ul><li>Vytvoří dvě funkce v obráceném pořadí; Druhá je provést první (operátor zpětné složení).<br /></li><ul/>|
|`<<<`|[Bitové operátory](bitwise-operators.md)|<ul><li>Posune bitů množství na levé straně na levé straně podle počtu bitů zadaný na pravé straně.<br /></li><ul/>|
|`<-`|[Hodnoty](../values/index.md)|<ul><li>Přiřazuje hodnotu proměnné.<br /></li><ul/>|
|`<...>`|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Vymezuje parametry typu.<br /></li><ul/>|
|`<>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně rovná není pravé straně; jinak vrátí hodnotu false.<br /></li><ul/>|
|`<>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "není rovno" operaci po pravé straně typu s povolenou hodnotou Null.<br /></li><ul/>|
|`<=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud na levé straně je menší než nebo rovna pravé straně; jinak vrátí `false`.<br /></li><ul/>|
|`<=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci "menší než nebo rovno", když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|<code>&lt;&#124;</code>|[Funkce](../functions/index.md)|<ul><li>Funkce na levé straně (operátor zpětné kanálu) předá výsledek výrazu na pravé straně.<br /></li><ul/>|
|<code>&lt;&#124;&#124;</code>|[Operátory. &#40; &#60; &#124; &#124; &#41; &#60;' T1, T2, U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá řazené kolekce členů z dva argumenty funkce na levé straně na pravé straně.<br /></li><ul/>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operátory. &#40; &#60; &#124; &#124; &#124; &#41; &#60;'T1, "T2," T3,' U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Předá řazenou kolekci členů ze tří argumentů funkce na levé straně na pravé straně.<br /></li><ul/>|
|`<@...@>`|[Citace kódu](../code-quotations.md)|<ul><li>Vymezuje typové kód uvozovek.<br /></li><ul/>|
|`<@@...@@>`|[Citace kódu](../code-quotations.md)|<ul><li>Vymezuje netypový kód uvozovek.<br /></li><ul/>|
|`=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud pravé straně; rovná na levé straně, jinak vrátí `false`.<br /></li><ul/>|
|`=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "stejné" operaci po pravé straně typu s povolenou hodnotou Null.<br /></li><ul/>|
|`==`|Nelze použít.|<ul><li>Nepoužívá se v jazyce F #. Použití `=` pro operace rovnosti.<br /></li><ul/>|
|`>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně je větší než pravé straně jinak, vrátí `false`.<br /></li><ul/>|
|`>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operaci "větší než", když na pravé straně je typ s možnou hodnotou Null.<br /></li><ul/>|
|`>>`|[Funkce](../functions/index.md)|<ul><li>Vytvoří dvě funkce (operátor dopředného složení).<br /></li><ul/>|
|`>>>`|[Bitové operátory](bitwise-operators.md)|<ul><li>Množství na levé straně vpravo podle počtu bitů posuny umístí zadaný na pravé straně.<br /></li><ul/>|
|`>=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně je větší než nebo rovno pravé straně; jinak vrátí `false`.<br /></li><ul/>|
|`>=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "větší než nebo rovno" operaci po pravé straně typu s povolenou hodnotou Null.<br /></li><ul/>|
|`?`|[Parametry a argumenty](../parameters-and-arguments.md)|<ul><li>Určuje za volitelným argumentem.<br /></li><li>Použít jako operátor pro dynamické volání metod a vlastností. Je nutné zadat vlastní implementaci.<br /></li><ul/>|
|`? ... <- ...`|Není k dispozici žádné další informace.|<ul><li>Použít jako operátor pro nastavení dynamických vlastností. Je nutné zadat vlastní implementaci.<br /></li><ul/>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalentní odpovídající operátorů bez? Předpona, kde je typ s možnou hodnotou Null na levé straně.<br /></li><ul/>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalentní odpovídající operátorů bez? přípona, kde je typ s možnou hodnotou Null na pravé straně.<br /></li><ul/>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalent odpovídající operátory bez okolního otazníky, kde jsou na obou stranách typy s možnou hodnotou Null.<br /></li><ul/>|
|`@`|[Seznamy](../lists.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Zřetězí dva seznamy.<br /></li><li>Pokud je ponecháno před řetězcový literál, označuje, že řetězec je budou interpretovat doslovné, s žádné výklad řídicí znaky.<br /></li><ul/>|
|`[...]`|[Seznamy](../lists.md)|<ul><li>Vymezuje prvků seznamu.<br /></li><ul/>|
|<code>[&#124;...&#124;]</code>|[Pole](../arrays.md)|<ul><li>Vymezuje prvků pole.<br /></li><ul/>|
|`[<...>]`|[Atributy](../attributes.md)|<ul><li>Vymezuje atribut.<br /></li><ul/>|
|`\`|[Řetězce](../strings.md)|<ul><li>Řídicí sekvence další znak; použít v řetězec a znakové literály.<br /></li><ul/>|
|`^`|[Statisticky vyřešené parametry typu](../generics/statically-resolved-type-parameters.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Určuje typ parametry, které je třeba vyřešit, v době kompilace, není za běhu.<br /></li><li>Zřetězí řetězec.<br /></li><ul/>|
|`^^^`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitový exkluzivní OR operaci.<br /></li><ul/>|
|`_`|[Výrazy shody](../match-expressions.md)<br /><br />[Obecné typy](../generics/index.md)|<ul><li>Určuje vzor zástupný znak.<br /></li><li>Určuje anonymní obecný parametr.<br /></li><ul/>|
|<code>&#96;</code>|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Interně používá k označení parametr obecného typu.<br /></li><ul/>|
|`{...}`|[Sekvence](../sequences.md)<br /><br />[Záznamy](../records.md)|<ul><li>Vymezuje sekvenční výrazy a výpočetní výrazy.<br /></li><li>Použít v definicích záznamu.<br /></li><ul/>|
|<code>&#124;</code>|[Výrazy shody](../match-expressions.md)|<ul><li>Vymezuje shody jednotlivých případech jednotlivých případech rozlišovaná sjednocení a hodnoty výčtu.<br /></li><ul/>|
|<code>&#124;&#124;</code>|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá logická hodnota nebo operaci.<br /></li><ul/>|
|<code>&#124;&#124;&#124;</code>|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitové operace OR.<br /></li><ul/>|
|<code>&#124;></code>|[Funkce](../functions/index.md)|<ul><li>Předá výsledek na levé straně funkce na pravé straně (operátor kanálu předat dál).<br /></li><ul/>|
|<code>&#124;&#124;></code>|[Operátory. &#40; &#124; &#124; &#62; &#41; &#60;' T1, T2, U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Na levé straně předá řazené kolekce členů z dva argumenty funkce na pravé straně.<br /></li><ul/>|
|<code>&#124;&#124;&#124;></code>|[Operátory. &#40; &#124; &#124; &#124; &#62; &#41; &#60;'T1, "T2," T3,' U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Na levé straně předá řazenou kolekci členů ze tří argumentů funkce na pravé straně.<br /></li><ul/>|
|`~~`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Používá k deklaraci přetížení pro operátor unární negace.<br /></li><ul/>|
|`~~~`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitové hodnotě není operace.<br /></li><ul/>|
|`~-`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Používá k deklaraci přetížení pro unární mínus – operátor.<br /></li><ul/>|
|`~+`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Používá k deklaraci přetížení pro Unární plus operátor.<br /></li><ul/>|

## <a name="operator-precedence"></a>Priorita operátorů
Následující tabulka uvádí pořadí priority operátory a žádná jiná klíčová slova výrazu v F # jazyk, v pořadí od nejnižší prioritu nejvyšší prioritu. Najdete ho taky je asociativnost, pokud je k dispozici.

|Operátor|Asociativita|
|--------|-------------|
|`as`|Vpravo|
|`when`|Vpravo|
|<code>&#124;</code> (kanálu)|Vlevo|
|`;`|Vpravo|
|`let`|Neasociativní|
|`function`, `fun`, `match`, `try`|Neasociativní|
|`if`|Neasociativní|
|`->`|Vpravo|
|`:=`|Vpravo|
|`,`|Neasociativní|
|`or`, <code>&#124;&#124;</code>|Vlevo|
|`&`, `&&`|Vlevo|
|`:>`, `:?>`|Vpravo|
|`!=`*op*, `<` *op*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op* , `&`<br /><br />(včetně `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Vlevo|
|`^`*OP*<br /><br />(včetně `^^^`)|Vpravo|
|`::`|Vpravo|
|`:?`|Není asociativní|
|`-`*op*, `+` *op*|Platí pro infix používá tyto symboly|
|`*`*op*, `/` *op*, `%` *op*|Vlevo|
|`**`*OP*|Vpravo|
|`f x` (funkce aplikace)|Vlevo|
|<code>&#124;</code> (Porovnávací)|Vpravo|
|operátory předpony (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|Vlevo|
|`.`|Vlevo|
|`f(x)`|Vlevo|
|`f<`*Typy*`>`|Vlevo|
F # podporuje vlastní přetížení operátoru. To znamená, že můžete definovat vlastní operátory. V předchozí tabulce *op* může být jakékoli platné (pravděpodobně prázdná) posloupnosti znaků operátor, předdefinované nebo definované uživatelem. Proto můžete tuto tabulku určit, jakou posloupnost znaků se má použít pro vlastní operátor k dosažení požadované úrovně priorit. Úvodní `.` znaky jsou ignorovány, když kompilátor určuje prioritu.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](../index.md)

[Přetížení operátoru](../operator-overloading.md)
