---
title: Referenční dokumentace klíčových slov (F#)
description: 'Odkazy na informace o všech klíčových slov jazyka F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 7d8a2bf667f5303cc19e8d4279e433efca25c294
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="keyword-reference"></a>Referenční dokumentace klíčových slov

Toto téma obsahuje odkazy na informace o všech F # klíčová slova jazyka.

## <a name="f-keyword-table"></a>Tabulka F # – klíčové slovo

Následující tabulka uvádí všechny F # klíčová slova v abecedním pořadí, společně s stručný popis a odkazy na související témata, které obsahují další informace.

|– Klíčové slovo|Odkaz|Popis|
|-------|----|-----------|
|`abstract`|[Členové](members/index.md)<br /><br />[Abstraktní třídy](abstract-classes.md)|Určuje metodu, která buď nemá žádnou implementaci v typu, ve kterém je deklarovaná, nebo se je virtuální a má výchozí implementaci.|
|`and`|[`let` Vazby](functions/let-bindings.md)<br /><br />[Členové](members/index.md)<br /><br />[Omezení](generics/constraints.md)|Použít v vzájemně rekurzivní vazby, v vlastnosti deklarací a s více omezení na obecné parametry.|
|`as`|[Třídy](classes.md)<br /><br />[Porovnávání vzorů](Pattern-Matching.md)|Umožňuje poskytnout aktuální objekt třídy názvu objektu. Rovněž pojmenujte celý vzor v rámci vzor shody.|
|`assert`|[Kontrolní výrazy](assertions.md)|Používají k ověření kódu během ladění.|
|`base`|[Třídy](classes.md)<br /><br />[Dědičnost](inheritance.md)|Použít jako název objektu základní třídy.|
|`begin`|[Podrobná syntaxe](verbose-syntax.md)|V podrobná syntaxe označuje začátek bloku kódu.|
|`class`|[Třídy](classes.md)|V podrobná syntaxe označuje začátek definici třídy.|
|`default`|[Členové](members/index.md)|Označuje implementace abstraktní metody; Chcete-li vytvořit virtuální metodu použít společně s deklarace abstraktní metody.|
|`delegate`|[Delegáti](delegates.md)|Používá k deklaraci delegáta.|
|`do`|[Vazby do](functions/do-bindings.md)<br /><br />[Smyčky: `for...to` výraz](loops-for-to-expression.md)<br /><br />[Smyčky: `for...in` výraz](loops-for-in-expression.md)<br /><br />[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Použít v opakování ve smyčce konstrukce nebo ke spouštění imperativní kódu.|
|`done`|[Podrobná syntaxe](verbose-syntax.md)|V podrobná syntaxe označuje konec bloku kódu ve výrazu opakování.|
|`downcast`|[Přetypování a převody](casting-and-conversions.md)|Umožňuje převést na typ, který je nižší úrovni v řetězu dědičnosti.|
|`downto`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|V `for` výraz, použitý při počítání pozpátku.|
|`elif`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Použít v podmíněného větvení. Zkratka pro `else if`.|
|`else`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Použít v podmíněného větvení.|
|`end`|[Struktury](structures.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Záznamy](records.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|V rozšíření a definice typů označuje konec oddíl definice člen.<br /><br />V podrobná syntaxe, slouží k zadání konec bloku kódu, který začíná `begin` – klíčové slovo.|
|`exception`|[Zpracování výjimek](exception-handling/index.md)<br /><br />[Typy výjimek](exception-handling/exception-types.md)|Používá k deklaraci typ výjimky.|
|`extern`|[Externí funkce](functions/external-functions.md)|Označuje, že element deklarované programu je definována v jiné binární soubor nebo sestavení.|
|`false`|[Primitivní typy](primitive-types.md)|Použít jako logická hodnota literál.|
|`finally`|[Výjimky: `try...finally` výraz](exception-handling/the-try-finally-expression.md)|Použít v kombinaci s `try` zavádět blok kódu, který se spustí bez ohledu na to, zda dojde k výjimce.|
|`fixed`|[Pevná](fixed.md)|Použít k "připnout" ukazatel v zásobníku na brání jeho uvolnění z paměti.|
|`for`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)<br /><br />[Smyčky: Výraz for...in](loops-for-in-expression.md)|Použít v opakování ve smyčce konstrukce.|
|`fun`|[Výrazy lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md)|Použít ve výrazech lambda, také známé jako anonymní funkce.|
|`function`|[Výrazy shody](match-expressions.md)<br /><br />[Výrazy lambda: Klíčové slovo fun](functions/lambda-expressions-the-fun-keyword.md)|Použít jako kratší alternativa k `fun` – klíčové slovo a `match` výraz ve výrazu lambda, který má na jeden argument porovnávání vzorů.|
|`global`|[Obory názvů](namespaces.md)|Slouží k odkazování nejvyšší úrovně obor názvů .NET.|
|`if`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Použít v podmíněného větvení konstrukce.|
|`in`|[Smyčky: Výraz for...in](loops-for-in-expression.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|Použít pro sekvenční výrazy a na podrobná syntaxe jednotlivé výrazy z vazby.|
|`inherit`|[Dědičnost](inheritance.md)|Slouží k zadání základní třídu nebo základní rozhraní.|
|`inline`|[Funkce](functions/index.md)<br /><br />[Vložené funkce](functions/inline-functions.md)|Slouží k určení funkci, která by měla být implementovaná přímo do kódu volajícího.|
|`interface`|[Rozhraní](interfaces.md)|Použít deklarovat a implementovat rozhraní.|
|`internal`|[Řízení přístupu](access-control.md)|Umožňuje zadat, že je člen viditelný uvnitř sestavení, ale ne mimo něj.|
|`lazy`|[Opožděné výpočty](lazy-computations.md)|Slouží k zadání výpočtu, který se má provést jenom v případě, že v důsledku toho je potřeba.|
|`let`|[`let` Vazby](functions/let-bindings.md)|Umožňuje přidružit, nebo vytvořit vazbu, název hodnoty nebo funkce.|
|`let!`|[Asynchronní pracovní postupy](asynchronous-workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Použít v asynchronní pracovní postupy pro vazbu na výsledek asynchronní výpočetní název, nebo v jiných výpočetní výrazy použitý pro vazbu název výsledku, který je typu výpočtu.|
|`match`|[Výrazy shody](match-expressions.md)|Slouží jako větve porovnáním hodnoty s konkrétním vzorem.|
|`member`|[Členové](members/index.md)|Používá k deklaraci vlastnosti nebo metody v typu objektu.|
|`module`|[Moduly](modules.md)|Umožňuje přidružit název skupiny souvisejících typů, hodnoty a funkce, logicky oddělení od jiný kód.|
|`mutable`|[Vazby let](functions/let-bindings.md)|Používá k deklaraci do proměnné, který je hodnota, která lze změnit.|
|`namespace`|[Obory názvů](namespaces.md)|Umožňuje přidružit název skupiny souvisejících typů a moduly, logicky oddělení od jiný kód.|
|`new`|[Konstruktory](members/constructors.md)<br /><br />[Omezení](generics/constraints.md)|Používá k deklaraci, definovat nebo vyvolat konstruktor, který vytvoří nebo který můžete vytvořit objekt.<br /><br />Také umožňuje v omezení obecný parametr znamená, že typ musí mít určité konstruktor.|
|`not`|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)<br /><br />[Omezení](generics/constraints.md)|Ve skutečnosti není klíčové slovo. Ale `not struct` v kombinaci se používá jako obecný parametr omezení.|
|`null`|[Hodnoty Null](values/null-values.md)<br /><br />[Omezení](generics/constraints.md)|Ukazuje na nepřítomnost objektu.<br /><br />Také použít v omezení obecný parametr.|
|`of`|[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Delegáti](delegates.md)<br /><br />[Typy výjimek](exception-handling/exception-types.md)|Používat v rozlišovaná sjednocení označující typ kategorie hodnoty a v deklaracích delegáta a výjimek.|
|`open`|[Deklarace importu: `open` – klíčové slovo](import-declarations-the-open-keyword.md)|Umožňuje zpřístupnit obsah oboru názvů nebo modul bez kvalifikace.|
|`or`|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)<br /><br />[Omezení](generics/constraints.md)|Použít s Boolean podmínky jako logická hodnota `or` operátor. Ekvivalent hodnoty '||`.<br /><br />Také použít v omezení člen.|
|`override`|[Členové](members/index.md)|Slouží k implementaci verzi metodu abstraktní nebo virtuální, která se liší od základní verze.|
|`private`|[Řízení přístupu](access-control.md)|Omezuje přístup členům kód v stejný typ nebo modul.|
|`public`|[Řízení přístupu](access-control.md)|Umožňuje přístup k člena z mimo typu.|
|`rec`|[Funkce](functions/index.md)|Slouží k určení, že funkce je rekurzivní.|
|`return`|[Asynchronní pracovní postupy](Asynchronous-Workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Slouží k určení hodnotu zajistit v důsledku výpočetní výraz.|
|`return!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Slouží k určení, výpočetní výraz, který při hodnocení, poskytuje výsledek obsahující výpočetní výraz.|
|`select`|[Výrazy dotazu](query-expressions.md)|Použít ve výrazech dotazů k určení, která pole nebo sloupce, které chcete extrahovat. Všimněte si, že se jedná o kontextové klíčové slovo, což znamená, že není ve skutečnosti o vyhrazené slovo a pouze funguje jako klíčové slovo v odpovídající kontext.|
|`static`|[Členové](members/index.md)|Slouží k určení metody nebo vlastnosti, která může být volána bez instance typu nebo členem hodnotu, která je sdílena mezi všechny instance typu.|
|`struct`|[Struktury](structures.md)<br /><br />[Omezení](generics/constraints.md)|Používá k deklaraci typ struktury.<br /><br />Také použít v omezení obecný parametr.<br /><br />Použít pro OCaml kompatibilita v definice modulu.|
|`then`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](members/constructors.md)|Použít v podmíněné výrazy.<br /><br />Také použít k provedení vedlejší účinky po vytváření objektů.|
|`to`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|Použít v `for` smyčky k označení rozsahu.|
|`true`|[Primitivní typy](primitive-types.md)|Použít jako logická hodnota literál.|
|`try`|[Výjimky: Try... with – výraz](exception-handling/the-try-with-expression.md)<br /><br />[Výjimky: Try... finally výraz](exception-handling/the-try-finally-expression.md)|Používá k zavedení blok kódu, který může generovat výjimku. Použít v kombinaci s `with` nebo `finally`.|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Třídy](classes.md)<br /><br />[Záznamy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Výčty](enumerations.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Zkratky typů](type-abbreviations.md)<br /><br />[Měrné jednotky](units-of-measure.md)|Umožňuje deklarovat třída, záznamu, struktura, rozlišovaná sjednocení, typ výčtu, měrné jednotky nebo – zkratka typu.|
|`upcast`|[Přetypování a převody](casting-and-conversions.md)|Umožňuje převést na typ, který je v řetězu dědičnosti výše.|
|`use`|[Správa prostředků: `use` – klíčové slovo](resource-management-the-use-keyword.md)|Použít místo `let` hodnot, které vyžadují `Dispose` volá se kvůli uvolnění prostředků.|
|`use!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Použít místo `let!` v asynchronní pracovní postupy a další výpočetní výrazy hodnot, které vyžadují `Dispose` volá se kvůli uvolnění prostředků.|
|`val`|[Explicitní pole: Klíčové slovo `val`](members/explicit-fields-the-val-keyword.md)<br /><br />[Signatury](signatures.md)<br /><br />[Členové](members/index.md)|Použito v podpisu pro zobrazení hodnoty, nebo v typu deklarovat člena, v situacích, omezené.|
|`void`|[Primitivní typy](primitive-types.md)|Označuje .NET `void` typu. Použít při vzájemné spolupráci s jinými jazyky rozhraní .NET.|
|`when`|[Omezení](generics/constraints.md)|Použít pro logickou podmínky (*při chrání*) na vzor odpovídá a zavádět klauzuli omezení pro parametr obecného typu.|
|`while`|[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Představuje opakování konstrukce.|
|`with`|[Výrazy shody](match-expressions.md)<br /><br />[Objektové výrazy](object-expressions.md)<br /><br />[Kopírování a aktualizace výrazů záznamů](copy-and-update-record-expressions.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Výjimky: `try...with` výraz](exception-handling/the-try-with-expression.md)|Použít v kombinaci s `match` – klíčové slovo v výrazy porovnávání vzorů. Také používají v objektové výrazy, rozšíření a záznamů kopírování výrazy zavádět člen definice a zavádět obslužné rutiny výjimek.|
|`yield`|[Sekvence](sequences.md)|Ve výrazu pořadí použít k vytvoření hodnoty pro pořadí.|
|`yield!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se v výpočetní výraz výsledku daného výpočetní výraz připojit ke kolekci obsahující výpočetní výraz výsledků.|

Následující klíčová slova jsou vyhrazená v F #, protože jsou klíčová slova v jazyce OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Pokud použijete `--mlcompatibility` – možnost kompilátoru, výše uvedené klíčová slova lze použít jako identifikátory.

Následující klíčová slova jsou vyhrazené jako klíčová slova pro budoucí rozšíření jazyka F #:

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

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)

[Možnosti kompilátoru](compiler-options.md)
