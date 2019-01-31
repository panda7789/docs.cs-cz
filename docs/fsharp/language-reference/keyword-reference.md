---
title: Referenční dokumentace klíčových slov
description: Odkazy na informace o všech F# klíčová slova jazyka.
ms.date: 05/16/2016
ms.openlocfilehash: 5a94a30ca0f73538cc22e76fa75bd76741b70d99
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "54857902"
---
# <a name="keyword-reference"></a>Referenční dokumentace klíčových slov

Toto téma obsahuje odkazy na informace o všech F# klíčová slova jazyka.

## <a name="f-keyword-table"></a>F#Tabulky – klíčové slovo

V následující tabulce jsou uvedeny všechny F# klíčová slova v abecedním pořadí, společně s stručný popis a odkazy na související témata, které obsahují další informace.

|Klíčové slovo|Odkaz|Popis|
|-------|----|-----------|
|`abstract`|[Členové](members/index.md)<br /><br />[Abstraktní třídy](abstract-classes.md)|Určuje metodu, která buď nemá implementaci v typu, ve kterém je deklarovaná, nebo že je virtuální a má výchozí implementaci.|
|`and`|[`let` Vazby](functions/let-bindings.md)<br /><br />[Záznamy](records.md)<br /><br />[Členové](members/index.md)<br /><br />[Omezení](generics/constraints.md)|Použít ve vzájemně rekurzivních vazbách a záznamy, v deklaracích vlastností a s několika omezeními u generických parametrů.|
|`as`|[Třídy](classes.md)<br /><br />[Porovnávání vzorů](Pattern-Matching.md)|Umožňuje poskytnout název objektu objektu aktuální třídy. Také použít k pojmenování celého vzoru v rámci porovnávání.|
|`assert`|[Kontrolní výrazy](assertions.md)|Slouží k ověření kódu během ladění.|
|`base`|[Třídy](classes.md)<br /><br />[Dědičnost](inheritance.md)|Použít jako název objektu základní třídy.|
|`begin`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje začátek bloku kódu.|
|`class`|[Třídy](classes.md)|V podrobné syntaxi označuje začátek definice třídy.|
|`default`|[Členové](members/index.md)|Označuje implementaci abstraktní metody; použít společně s deklarací abstraktní metody k vytvoření virtuální metody.|
|`delegate`|[Delegáti](delegates.md)|Slouží k deklaraci delegáta.|
|`do`|[Vazby do](functions/do-bindings.md)<br /><br />[Smyčky: `for...to` Výraz](loops-for-to-expression.md)<br /><br />[Smyčky: `for...in` Výraz](loops-for-in-expression.md)<br /><br />[Smyčky: `while...do` Výraz](loops-while-do-expression.md)|Používá se v konstruktorech cyklů nebo k provádění imperativního kódu.|
|`done`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje konec bloku kódu ve výrazu cyklu.|
|`downcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je nižší pozici v řetězu dědičnosti.|
|`downto`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)|V `for` výrazu, slouží k počítání pozpátku.|
|`elif`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení. Krátká forma výrazu `else if`.|
|`else`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení.|
|`end`|[Struktury](structures.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Záznamy](records.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|V definicích typů a rozšíření typu označuje konec sekce definic členů.<br /><br />V podrobné syntaxi se používá k určení konce bloku kódu, který začíná `begin` – klíčové slovo.|
|`exception`|[Zpracování výjimek](exception-handling/index.md)<br /><br />[Typy výjimek](exception-handling/exception-types.md)|Slouží k deklaraci typu výjimky.|
|`extern`|[Externí funkce](functions/external-functions.md)|Označuje, že deklarovaný element programu je definovaný v jiném binárním souboru nebo sestavení.|
|`false`|[Primitivní typy](primitive-types.md)|Použít jako logický literál.|
|`finally`|[Výjimky: `try...finally` Výraz](exception-handling/the-try-finally-expression.md)|Použít v kombinaci s `try` k uvození bloku kódu, který se spustí bez ohledu na to, zda dojde k výjimce.|
|`fixed`|[Oprava](fixed.md)|Použít "připnout" ukazatel zásobníku tak, aby se uvolněna z paměti.|
|`for`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)<br /><br />[Smyčky: Výraz for...in](loops-for-in-expression.md)|Používá se v konstruktorech cyklů.|
|`fun`|[Výrazy lambda: Klíčové slovo `fun`](functions/lambda-expressions-the-fun-keyword.md)|Použít ve výrazech lambda, označovaný také jako anonymní funkce.|
|`function`|[Výrazy shody](match-expressions.md)<br /><br />[Výrazy lambda: Klíčové slovo fun](functions/lambda-expressions-the-fun-keyword.md)|Používá se jako kratší alternativa `fun` – klíčové slovo a `match` výraz ve výrazu lambda, který má porovnávání vzorů u jednoho argumentu.|
|`global`|[Obory názvů](namespaces.md)|Slouží k odkazování nejvyšší úrovni obor názvů .NET.|
|`if`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v konstruktorech podmíněného větvení.|
|`in`|[Smyčky: Výraz for...in](loops-for-in-expression.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|Použít ve výrazech pořadí a v podrobné syntaxi k oddělení výrazů od vazeb.|
|`inherit`|[Dědičnost](inheritance.md)|Slouží k určení základní třídy nebo základních rozhraní.|
|`inline`|[Funkce](functions/index.md)<br /><br />[Vložené funkce](functions/inline-functions.md)|Slouží k označení funkce, která se má integrovat přímo do kódu volajícího.|
|`interface`|[Rozhraní](interfaces.md)|Slouží k deklaraci a implementaci rozhraní.|
|`internal`|[Řízení přístupu](access-control.md)|Používá se k určení, že je člen viditelný uvnitř sestavení, ale ne mimo něj.|
|`lazy`|[Opožděné výpočty](lazy-computations.md)|Slouží k určení výpočtu, který se má provést jenom v případě potřeby výsledek.|
|`let`|[`let` Vazby](functions/let-bindings.md)|Použít k přidružení (neboli svázání) názvu k hodnotě nebo funkci.|
|`let!`|[Asynchronní pracovní postupy](asynchronous-workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Použít v asynchronních pracovních postupech k vytvoření vazby názvu s výsledkem asynchronního výpočtu, nebo v jiných výrazech výpočtu se používá k vytvoření vazby názvu s výsledkem, který je výpočetního typu.|
|`match`|[Výrazy shody](match-expressions.md)|Používá se k větvení porovnáním hodnoty s vzoru.|
|`match!`|[Výpočetní výrazy](computation-expressions.md#match)|Použít pro vložení volání do výpočtu výrazu a vzor shody na jeho výsledek.|
|`member`|[Členové](members/index.md)|Slouží k deklaraci vlastnosti nebo metody v objektovém typu.|
|`module`|[Moduly](modules.md)|Použito k přidružení názvu ke skupině souvisejících typů, hodnot a funkce a jeho logickému oddělení od jiného kódu.|
|`mutable`|[Vazby let](functions/let-bindings.md)|Slouží k deklaraci proměnné, to znamená, hodnotu, která lze změnit.|
|`namespace`|[Obory názvů](namespaces.md)|Použít k přidružení názvu ke skupině souvisejících typů a modulů a jeho logickému oddělení od jiného kódu.|
|`new`|[Konstruktory](members/constructors.md)<br /><br />[Omezení](generics/constraints.md)|Slouží k deklaraci, definici nebo vyvolání konstruktoru, který vytvoří nebo dokáže vytvořit objekt.<br /><br />Také v omezeních obecných parametrů označuje, že typ musí mít určitý konstruktor.|
|`not`|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)<br /><br />[Omezení](generics/constraints.md)|Ve skutečnosti klíčové slovo. Ale `not struct` v kombinaci se používá jako omezení obecného parametru.|
|`null`|[Hodnoty Null](values/null-values.md)<br /><br />[Omezení](generics/constraints.md)|Označuje absenci objektu.<br /><br />Používá se také v omezeních obecných parametrů.|
|`of`|[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Delegáti](delegates.md)<br /><br />[Typy výjimek](exception-handling/exception-types.md)|Použít v rozlišovaných sjednoceních k označení typu kategorií hodnot a v deklaracích delegování a výjimek.|
|`open`|[Deklarace importu: Klíčové slovo `open`](import-declarations-the-open-keyword.md)|Umožňuje zpřístupnění obsahu oboru názvů nebo modulu bez kvalifikace.|
|`or`|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)<br /><br />[Omezení](generics/constraints.md)|Používá se v logických podmínkách jako logická hodnota `or` operátor. Ekvivalentní `||`.<br /><br />Používá se také v omezeních členů.|
|`override`|[Členové](members/index.md)|Používaný k implementaci verze abstraktní nebo virtuální metody, která se liší od základní verze.|
|`private`|[Řízení přístupu](access-control.md)|Omezení přístupu k členovi na kód ve stejném typu nebo modulu.|
|`public`|[Řízení přístupu](access-control.md)|Umožňuje přístup ke členovi zvnějška typu.|
|`rec`|[Funkce](functions/index.md)|Slouží k označení, že funkce je rekurzivní.|
|`return`|[Asynchronní pracovní postupy](Asynchronous-Workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Slouží k označení hodnotu, která vznikne jako výsledek výrazu výpočtu.|
|`return!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Slouží k označení výrazu výpočtu, který po vyhodnocení poskytne výsledek obsahujícího výrazu výpočtu.|
|`select`|[Výrazy dotazu](query-expressions.md)|Použít ve výrazech dotazu k určení, která pole nebo sloupce, které chcete extrahovat. Všimněte si, že se kontextové klíčové slovo, což znamená, že není ve skutečnosti o vyhrazené slovo a funguje jen jako klíčové slovo v příslušném kontextu.|
|`static`|[Členové](members/index.md)|Slouží k označení metody nebo vlastnosti, kterou lze volat bez instance typu nebo člena hodnoty, který se sdílí mezi všemi instancemi typu.|
|`struct`|[Struktury](structures.md)<br /><br /> [Řazené kolekce členů](tuples.md)<br/><br/>[Omezení](generics/constraints.md)|Slouží k deklaraci typu struktury.<br /><br/>Slouží k určení řazené kolekce členů struktury.<br/><br />Používá se také v omezeních obecných parametrů.<br /><br />Používá kvůli kompatibilitě s OCaml v definicích modulů.|
|`then`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](members/constructors.md)|Používat v podmíněných výrazech.<br /><br />Také použít k provedení vedlejších efektů po konstrukci objektu.|
|`to`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)|Použít v `for` smyček k označení rozsahu.|
|`true`|[Primitivní typy](primitive-types.md)|Použít jako logický literál.|
|`try`|[Výjimky: Try... with – výraz](exception-handling/the-try-with-expression.md)<br /><br />[Výjimky: Try... finally výraz](exception-handling/the-try-finally-expression.md)|Používá k uvození bloku kódu, který může vygenerovat výjimku. Použít v kombinaci s `with` nebo `finally`.|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Třídy](classes.md)<br /><br />[Záznamy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Výčty](enumerations.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Zkratky typů](type-abbreviations.md)<br /><br />[Měrné jednotky](units-of-measure.md)|Používá k deklaraci třídy, záznamu, struktury, diskriminované sjednocení, výčtového typu, měrné jednotky nebo zkratky typu.|
|`upcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je vyšší pozici v řetězu dědičnosti.|
|`use`|[Správa prostředků: Klíčové slovo `use`](resource-management-the-use-keyword.md)|Použít namísto `let` pro hodnoty, které vyžadují `Dispose` říkalo k uvolnění prostředků.|
|`use!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Použít namísto `let!` v asynchronních pracovních postupech a jiných výrazech výpočtu pro hodnoty, které vyžadují `Dispose` říkalo k uvolnění prostředků.|
|`val`|[Explicitní pole: Klíčové slovo `val`](members/explicit-fields-the-val-keyword.md)<br /><br />[Signatury](signatures.md)<br /><br />[Členové](members/index.md)|Použít v podpisu k označení hodnoty, nebo v typu k deklarování člena v situacích, omezené.|
|`void`|[Primitivní typy](primitive-types.md)|Označuje .NET `void` typu. Používány při spolupráci s jinými jazyky rozhraní .NET.|
|`when`|[Omezení](generics/constraints.md)|Používá se pro logické podmínky (*při chrání*) u porovnávání vzorů a k uvození klauzule omezení parametru obecného typu.|
|`while`|[Smyčky: `while...do` Výraz](loops-while-do-expression.md)|Zavádí uvozuje konstruktor cyklu.|
|`with`|[Výrazy shody](match-expressions.md)<br /><br />[Objektové výrazy](object-expressions.md)<br /><br />[Kopírování a aktualizace výrazů záznamů](copy-and-update-record-expressions.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Výjimky: `try...with` Výraz](exception-handling/the-try-with-expression.md)|Použít v kombinaci s `match` – klíčové slovo ve vzorech porovnávání výrazů. Používá i v objektové výrazy, výrazy záznamu zkopírování a typ rozšíření představují definice členů a zavést obslužných rutin výjimek.|
|`yield`|[Sekvence](sequences.md)|Použít ve výrazu pořadí k vytvoření hodnoty pořadí.|
|`yield!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Použít ve výrazu výpočtu k připojení výsledku daného výpočetního výrazu ke kolekci výsledků obsahujícího výrazu výpočtu.|

Následující klíčová slova jsou vyhrazená v F# vzhledem k tomu, že jsou klíčová slova v jazyce OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Pokud používáte `--mlcompatibility` – možnost kompilátoru, výše klíčová slova jsou k dispozici pro použití jako identifikátory.

Následující klíčová slova jsou vyhrazená jako klíčová slova pro budoucí rozšíření F# jazyka:

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)
- [Možnosti kompilátoru](compiler-options.md)
