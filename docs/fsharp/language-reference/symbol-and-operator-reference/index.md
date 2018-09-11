---
title: Referenční dokumentace symbolů a operátorů (F#)
description: 'Další informace o symbolů a operátorů, které se používají v programovacím jazyce F #.'
ms.date: 04/04/2018
ms.openlocfilehash: 0e36f6cfc75b7d2e79bcf7acb89d260fd4e9b1ad
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44338685"
---
# <a name="symbol-and-operator-reference"></a>Referenční dokumentace symbolů a operátorů

> [!NOTE]
Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Toto téma obsahuje tabulky symbolů a operátorů, které se používají v jazyce F #.

## <a name="table-of-symbols-and-operators"></a>Tabulka symbolů a operátorů

Následující tabulka popisuje symboly použité v jazyce F #, obsahuje odkazy na témata, která poskytují další informace a obsahuje stručný popis některých používá symbolu. Symboly jsou řazeny podle sadu pořadí znaků ASCII.

|Symbol nebo – operátor|Odkazy|Popis|
|------------------|-----|-----------|
|`!`|[Referenční buňky](../reference-cells.md)<br /><br />[Výpočetní výrazy](../computation-expressions.md)|<ul><li>Přístupů přes ukazatel odkazovou buňku.<br /></li><li>Za klíčovým slovem označuje upravenou verzi chování klíčového slova jako řídí pracovního postupu.<br /></li></ul>|
|`!=`|Nelze použít.|<ul><li>V jazyce F # nepoužívá. Použití `<>` pro operace nerovnost.<br /></li></ul>|
|`"`|[Literály](../literals.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Odděluje citaci textový řetězec.<br /></li></ul>|
|`"""`|[Řetězce](../strings.md)|Odděluje citaci doslovný řetězec. Se liší od `@"..."` , můžete určit znak uvozovky pomocí jednoduchá uvozovka v řetězci.|
|`#`|[Direktivy kompilátoru](../compiler-directives.md)<br /><br />[Flexibilní typy](../flexible-types.md)|<ul><li>Předpony adres direktiva preprocesoru nebo kompilátor, jako například `#light`.<br /></li><li>Při použití s typem, znamená to *flexibilní typ*, který odkazuje na typ nebo v jednom z jeho odvozených typů.<br /></li></ul>|
|`$`|Není k dispozici žádné další informace.|<ul><li>Interně používá k určité vygenerovaný kompilátorem proměnné a funkce názvy.<br /></li></ul>|
|`%`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Citace kódu](../code-quotations.md)|<ul><li>Vypočítá zbytek celé číslo.<br /></li><li>Používá se pro spojení výrazů do nabídky kódu.<br /></li></ul>|
|`%%`|[Citace kódu](../code-quotations.md)|<ul><li>Používá se pro spojení výrazů do nabídky netypového kódu.<br /></li></ul>|
|`%?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá zbytek celého čísla po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`&`|[Výrazy shody](../match-expressions.md)|<ul><li>Vypočítá adresu proměnlivé hodnoty pro použití při vzájemné spolupráci s jinými jazyky.<br /></li><li>Použít ve vzorcích a.<br /></li></ul>|
|`&&`|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá Boolean a operace.<br /></li></ul>|
|`&&&`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitové operace AND.<br /></li></ul>|
|`'`|[Literály](../literals.md)<br /><br />[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Odděluje citaci literálu s jedním znakem.<br /></li><li>Určuje obecný parametr typu.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>|Není k dispozici žádné další informace.|<ul><li>Odděluje citaci identifikátor, který by jinak platný identifikátor, jako je klíčové slovo jazyka.<br /></li></ul>|
|`( )`|[Typ jednotky](../unit-type.md)|<ul><li>Představuje jednu hodnotu typu jednotky.<br /></li></ul>|
|`(...)`|[Řazené kolekce členů](../tuples.md)<br /><br />[Přetížení operátoru](../operator-overloading.md)|<ul><li>Určuje pořadí, ve kterém jsou výrazy vyhodnocovány.<br /></li><li>Odděluje citaci řazené kolekce členů.<br /></li><li>Použití také v definicích operátor.<br /></li></ul>|
|`(*...*)`||<ul><li>Odděluje citaci komentář, který může zahrnovat více řádků.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Aktivní vzory](../active-patterns.md)|<ul><li>Odděluje citaci active vzor. Zkratka *banánů klipy*.<br /></li></ul>|
|`*`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Řazené kolekce členů](../tuples.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Pokud se použije jako binární operátor vynásobí levé a pravé straně.<br /></li><li>V typech označuje párování v řazené kolekce členů.<br /></li><li>Použít v jednotkách, které typy měr.<br /></li></ul>|
|`*?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vynásobí levé a pravé straně, když pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`**`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá operace umocnění (`x ** y` znamená, že `x` exponentem `y`).<br /></li></ul>|
|`+`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Když se použije jako binárního operátoru, přidá levé a pravé straně.<br /></li><li>Při použití jako unární operátor, znamená pozitivní množství. (Formálně, vytvoří stejnou hodnotu se znaménkem beze změny.)<br /></li></ul>|
|`+?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Přidá levé a pravé straně, když pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`,`|[Řazené kolekce členů](../tuples.md)|<ul><li>Odděluje prvky řazené kolekce členů, nebo parametr typu.<br /></li></ul>|
|`-`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Pokud se použije jako binární operátor odečte od levého okraje pravé straně.<br /></li><li>Pokud se použije jako unární operátor provádí operaci negace.<br /></li></ul>|
|`-`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Odečte od levého okraje pravé straně po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`->`|[Funkce](../functions/index.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>Ve funkci typy, vymezuje argumenty a návratové hodnoty.<br /></li><li>Výsledkem výrazu (ve výrazech pořadí); ekvivalentní `yield` – klíčové slovo.<br /></li><li>Použít ve výrazech porovnání<br /></li></ul>|
|`.`|[Členové](../members/index.md)<br /><br />[Primitivní typy](../primitive-types.md)|<ul><li>Zpřístupňuje člen a odděluje jednotlivé názvy v plně kvalifikovaném názvu.<br /></li><li>Určuje desetinné čárky v plovoucí desetinnou čárkou.<br /></li></ul>|
|`..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah.<br /></li></ul>|
|`.. ..`|[Smyčky: `for...in` výraz](../loops-for-in-expression.md)|<ul><li>Určuje rozsah spolu s přírůstek.<br /></li></ul>|
|`.[...]`|[Pole](../arrays.md)|<ul><li>Přistupuje k prvku pole.<br /></li></ul>|
|`/`|[Aritmetické operátory](arithmetic-operators.md)<br /><br />[Měrné jednotky](../units-of-measure.md)|<ul><li>Vydělí na levé straně (Čítač) pravé straně (jmenovatel).<br /></li><li>Použít v jednotkách, které typy měr.<br /></li></ul>|
|`/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vydělí na levé straně pravé straně po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`//`||<ul><li>Označuje začátek jednořádkový komentář.<br /></li></ul>|
|`///`|[Dokumentace XML](../xml-documentation.md)|<ul><li>Označuje komentáře XML.<br /></li></ul>|
|`:`|[Funkce](../functions/index.md)|<ul><li>V anotaci typu odděluje název parametru nebo člena z jeho typu.<br /></li></ul>|
|`::`|[Seznamy](../lists.md)<br /><br />[Výrazy shody](../match-expressions.md)|<ul><li>Vytvoří seznam. Před element na levé straně se zobrazí v seznamu na pravé straně.<br /></li><li>K oddělení částí seznamu se používá v porovnávání vzorů.<br /></li></ul>|
|`:=`|[Referenční buňky](../reference-cells.md)|<ul><li>Přiřadí hodnotu odkazovou buňku.<br /></li></ul>|
|`:>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převede daný typ na typ, který je výše v hierarchii.<br /></li></ul>|
|`:?`|[Výrazy shody](../match-expressions.md)|<ul><li>Vrátí `true` Pokud hodnota neodpovídá zadanému typu; v opačném případě vrátí `false` (operátor testu typu).<br /></li></ul>|
|`:?>`|[Přetypování a převody](../casting-and-conversions.md)|<ul><li>Převede daný typ na typ, který je níže v hierarchii.<br /></li></ul>|
|`;`|[Podrobná syntaxe](../verbose-syntax.md)<br /><br />[Seznamy](../lists.md)<br /><br />[Záznamy](../records.md)|<ul><li>Odděluje výrazy (většinou v podrobné syntaxi).<br /></li><li>Odděluje prvky seznamu.<br /></li><li>Odděluje polí záznamu.<br /></li></ul>|
|`<`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vypočítá větší-než operace.<br /></li></ul>|
|`<?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|Vypočítá je menší než operace, když pravé straně je typ připouštějící hodnotu Null.|
|`<<`|[Funkce](../functions/index.md)|<ul><li>Vytvoří dvě funkce v obráceném pořadí; druhý probíhá první (operátor zpětně složení).<br /></li></ul>|
|`<<<`|[Bitové operátory](bitwise-operators.md)|<ul><li>Posune bitů v množství na levé straně vlevo o počet bitů určený na pravé straně.<br /></li></ul>|
|`<-`|[Hodnoty](../values/index.md)|<ul><li>Přiřadí hodnotu k proměnné.<br /></li></ul>|
|`<...>`|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Odděluje citaci parametry typu.<br /></li></ul>|
|`<>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně se nerovná na pravou stranu; v opačném případě vrátí hodnotu false.<br /></li></ul>|
|`<>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "není rovno" operaci po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`<=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně je menší nebo rovna na pravou stranu; v opačném případě vrátí `false`.<br /></li></ul>|
|`<=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operace "menší než nebo rovno" po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|<code>&lt;&#124;</code>|[Funkce](../functions/index.md)|<ul><li>Výsledek výrazu na pravé straně předává do funkce na levé straně (operátor zpětně kanálu).<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[Operátory. &#40; &#60; &#124; &#124; &#41; &#60;"T1, T2, U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Řazená kolekce členů dva argumenty na pravé straně předává do funkce na levé straně.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operátory. &#40; &#60; &#124; &#124; &#124; &#41; &#60;"T1,"T2,"T3," U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>N-tice tří argumentů na pravé straně předává do funkce na levé straně.<br /></li></ul>|
|`<@...@>`|[Citace kódu](../code-quotations.md)|<ul><li>Odděluje citaci typového kódu.<br /></li></ul>|
|`<@@...@@>`|[Citace kódu](../code-quotations.md)|<ul><li>Odděluje citaci nabídky netypového kódu.<br /></li></ul>|
|`=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud rovná na levé straně na pravou stranu; v opačném případě vrátí `false`.<br /></li></ul>|
|`=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "rovno" operaci po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`==`|Nelze použít.|<ul><li>V jazyce F # nepoužívá. Použití `=` pro operace rovnosti.<br /></li></ul>|
|`>`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně je větší než pravé straně; jinak vrátí hodnotu, vrátí `false`.<br /></li></ul>|
|`>?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá "větší než" operaci po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`>>`|[Funkce](../functions/index.md)|<ul><li>Vytvoří dvě funkce (operátor přesměrování sestavení).<br /></li></ul>|
|`>>>`|[Bitové operátory](bitwise-operators.md)|<ul><li>Posuny bitů v množství na levé straně doprava o počet umístí zadané na pravé straně.<br /></li></ul>|
|`>=`|[Aritmetické operátory](arithmetic-operators.md)|<ul><li>Vrátí `true` Pokud levé straně je větší než nebo rovna hodnotě na pravé straně; v opačném případě vrátí `false`.<br /></li></ul>|
|`>=?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Vypočítá operace "větší než nebo rovno" po pravé straně je typ připouštějící hodnotu Null.<br /></li></ul>|
|`?`|[Parametry a argumenty](../parameters-and-arguments.md)|<ul><li>Určuje volitelný argument.<br /></li><li>Použít jako operátor pro dynamické volání metod a vlastností. Je nutné zadat vlastní implementaci.<br /></li></ul>|
|`? ... <- ...`|Není k dispozici žádné další informace.|<ul><li>Použít jako operátor pro nastavení dynamických vlastností. Je nutné zadat vlastní implementaci.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalentní operátory odpovídající bez? Předpona, kde je typ připouštějící hodnotu Null na levé straně.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalentní operátory odpovídající bez? přípona, kde je typ připouštějící hodnotu Null na pravé straně.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Operátory s povolenou hodnotou Null](nullable-operators.md)|<ul><li>Ekvivalentní operátory odpovídající bez okolních otazníky, ve kterém jsou obě strany typy připouštějící hodnotu Null.<br /></li></ul>|
|`@`|[Seznamy](../lists.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Zřetězí dva seznamy.<br /></li><li>Při umístění před řetězcový literál, označuje, že řetězec má být interpretován verbatim, s žádná interpretace řídicí znaky.<br /></li></ul>|
|`[...]`|[Seznamy](../lists.md)|<ul><li>Odděluje citaci prvky seznamu.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Pole](../arrays.md)|<ul><li>Odděluje citaci prvků pole.<br /></li></ul>|
|`[<...>]`|[Atributy](../attributes.md)|<ul><li>Odděluje citaci atribut.<br /></li></ul>|
|`\`|[Řetězce](../strings.md)|<ul><li>Řídicí sekvence na další znak; použít v znakové a řetězcové literály.<br /></li></ul>|
|`^`|[Statisticky vyřešené parametry typu](../generics/statically-resolved-type-parameters.md)<br /><br />[Řetězce](../strings.md)|<ul><li>Určuje parametry typu, které je třeba vyřešit v době kompilace, ne za běhu.<br /></li><li>Zřetězí řetězce.<br /></li></ul>|
|`^^^`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitový exkluzivní OR operace.<br /></li></ul>|
|`_`|[Výrazy shody](../match-expressions.md)<br /><br />[Obecné typy](../generics/index.md)|<ul><li>Určuje vzorec zástupných znaků.<br /></li><li>Určuje anonymní obecný parametr.<br /></li></ul>|
|<code>&#96;</code>|[Automatická generalizace](../generics/automatic-generalization.md)|<ul><li>Interně používá k označení parametru obecného typu.<br /></li></ul>|
|`{...}`|[Sekvence](../sequences.md)<br /><br />[Záznamy](../records.md)|<ul><li>Odděluje citaci výrazech pořadí a výpočtu výrazů.<br /></li><li>Použití také v definicích záznamu.<br /></li></ul>|
|<code>&#124;</code>|[Výrazy shody](../match-expressions.md)|<ul><li>Odděluje citaci jednotlivé shody případy, jednotlivé rozlišené případy typu union a hodnotami výčtu.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Logické operátory](boolean-operators.md)|<ul><li>Vypočítá logická nebo operace.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitová operace OR.<br /></li></ul>|
|<code>&#124;></code>|[Funkce](../functions/index.md)|<ul><li>Na pravé straně (operátor svislou) předá funkci výsledek na levé straně.<br /></li></ul>|
|<code>&#124;&#124;></code>|[Operátory. &#40; &#124; &#124; &#62; &#41; &#60;"T1, T2, U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Řazená kolekce členů dva argumenty na levé straně předává do funkce na pravé straně.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[Operátory. &#40; &#124; &#124; &#124; &#62; &#41; &#60;"T1,"T2,"T3," U&#62; – funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>N-tice tří argumentů na levé straně předává do funkce na pravé straně.<br /></li></ul>|
|`~~`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro operátor unární negace.<br /></li></ul>|
|`~~~`|[Bitové operátory](bitwise-operators.md)|<ul><li>Vypočítá bitový není operace.<br /></li></ul>|
|`~-`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro unární operátor minus.<br /></li></ul>|
|`~+`|[Přetížení operátoru](../operator-overloading.md)|<ul><li>Slouží k deklaraci přetížení pro unárního operátoru plus.<br /></li></ul>|

## <a name="operator-precedence"></a>Priorita operátorů

V následující tabulce jsou uvedeny pořadí podle priority operátorů a dalších klíčových slovech výrazu v jazyce F #, v pořadí od nejnižší, nejvyšší priority. Také je asociativita operátorů, pokud je k dispozici.

|Operátor|Asociativita|
|--------|-------------|
|`as`|doprava|
|`when`|doprava|
|<code>&#124;</code> (kanál)|doleva|
|`;`|doprava|
|`let`|Neasociativní|
|`function`, `fun`, `match`, `try`|Neasociativní|
|`if`|Neasociativní|
|`->`|doprava|
|`:=`|doprava|
|`,`|Neasociativní|
|`or`, <code>&#124;&#124;</code>|doleva|
|`&`, `&&`|doleva|
|`:>`, `:?>`|doprava|
|`!=`*op*, `<` *op*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op* , `&`<br /><br />(včetně `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|doleva|
|`^`*OP*<br /><br />(včetně `^^^`)|doprava|
|`::`|doprava|
|`:?`|Není asociativní|
|`-`*op*, `+` *op*|Platí pro infix používá tyto symboly|
|`*`*op*, `/` *op*, `%` *op*|doleva|
|`**`*OP*|doprava|
|`f x` (použití funkce)|doleva|
|<code>&#124;</code> (Porovnávací)|doprava|
|operátory předpony (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|doleva|
|`.`|doleva|
|`f(x)`|doleva|
|`f<`*Typy*`>`|doleva|
Jazyk F # podporuje vlastní přetížení operátoru. To znamená, že můžete definovat vlastní operátory. V předchozí tabulce *op* může být libovolná platná (pravděpodobně prázdná) sekvence znaků operátoru, předdefinovaných nebo uživatelem definovaný. Proto můžete tuto tabulku určit, jaké posloupnost znaků, které mají použít pro vlastní operátor k dosažení požadované úrovně priority. Úvodní `.` znaky jsou ignorovány, pokud kompilátor určuje prioritu.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](../index.md)
- [Přetížení operátoru](../operator-overloading.md)
