---
title: Referenční dokumentace klíčových slov
description: Vyhledá odkazy na informace o všech klíčových F# slovech jazyka.
ms.date: 11/04/2019
ms.openlocfilehash: 64bb680a0861f4b8287f887ea67edb6fcf4f88a6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976623"
---
# <a name="keyword-reference"></a>Referenční dokumentace klíčových slov

Toto téma obsahuje odkazy na informace o všech F# klíčových slovech jazyka.

## <a name="f-keyword-table"></a>F#Tabulka klíčových slov

V následující tabulce jsou uvedena F# všechna klíčová slova v abecedním pořadí spolu s krátkými popisy a odkazy na související témata, která obsahují další informace.

|Klíčové slovo|Propojit|Popis|
|-------|----|-----------|
|`abstract`|[Členové](./members/index.md)<br /><br />[Abstraktní třídy](abstract-classes.md)|Označuje metodu, která buď nemá implementaci v typu, ve kterém je deklarovaná, nebo která je virtuální a má výchozí implementaci.|
|`and`|[`let` vazby](./functions/let-bindings.md)<br /><br />[Záznamy](records.md)<br /><br />[Členové](./members/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se ve vzájemně rekurzivních vazbách a záznamech, v deklaracích vlastností a s několika omezeními u obecných parametrů.|
|`as`|[Třídy](classes.md)<br /><br />[Porovnávání vzorů](Pattern-Matching.md)|Slouží k udělení názvu objektu aktuální třídě. Používá se také k předání názvu celému vzoru v rámci porovnávání vzorů.|
|`assert`|[Kontrolní výrazy](assertions.md)|Slouží k ověření kódu během ladění.|
|`base`|[Třídy](classes.md)<br /><br />[Dědičnost](inheritance.md)|Používá se jako název objektu základní třídy.|
|`begin`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje začátek bloku kódu.|
|`class`|[Třídy](classes.md)|V podrobné syntaxi označuje začátek definice třídy.|
|`default`|[Členové](./members/index.md)|Označuje implementaci abstraktní metody; používá se společně s deklarací abstraktní metody k vytvoření virtuální metody.|
|`delegate`|[Delegáty](delegates.md)|Slouží k deklaraci delegáta.|
|`do`|[Vazby do](./functions/do-bindings.md)<br /><br />[Smyčky: výraz `for...to`](loops-for-to-expression.md)<br /><br />[Smyčky: výraz `for...in`](loops-for-in-expression.md)<br /><br />[Smyčky: výraz `while...do`](loops-while-do-expression.md)|Používá se v konstrukcích cyklů nebo k provádění imperativního kódu.|
|`done`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje konec bloku kódu ve výrazu smyčky.|
|`downcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je níže v řetězu dědičnosti.|
|`downto`|[Smyčky: výraz `for...to`](loops-for-to-expression.md)|Ve výrazu `for`, který se používá při počítání v obráceném pořadí.|
|`elif`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení. Krátká forma `else if`.|
|`else`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení.|
|`end`|[Struktury](structures.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Záznamy](records.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|V definicích typů a příponách typů označuje konec oddílu definic členů.<br /><br />V podrobné syntaxi, která se používá k určení konce bloku kódu, který začíná klíčovým slovem `begin`.|
|`exception`|[Zpracování výjimek](./exception-handling/index.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Slouží k deklaraci typu výjimky.|
|`extern`|[Externí funkce](./functions/external-functions.md)|Označuje, že deklarovaný element programu je definovaný v jiném binárním souboru nebo sestavení.|
|`false`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`finally`|[Výjimky: výraz `try...finally`](./exception-handling/the-try-finally-expression.md)|Používá se společně s `try` k zavedení bloku kódu, který se provede bez ohledu na to, jestli dojde k výjimce.|
|`fixed`|[Určí](fixed.md)|Používá se k "připnutí" ukazatele v zásobníku, aby se zabránilo uvolňování paměti.|
|`for`|[Smyčky: výraz `for...to`](loops-for-to-expression.md)<br /><br />[Smyčky: Výraz for...in](loops-for-in-expression.md)|Používá se v konstruktorech cyklů.|
|`fun`|[Výrazy lambda: klíčové slovo `fun`](./functions/lambda-expressions-the-fun-keyword.md)|Používá se ve výrazech lambda, označovaných také jako anonymní funkce.|
|`function`|[Výrazy shody](match-expressions.md)<br /><br />[Výrazy lambda: klíčové slovo fun](./functions/lambda-expressions-the-fun-keyword.md)|Používá se jako kratší alternativa klíčového slova `fun` a výrazu `match` ve výrazu lambda, který má porovnávání vzorů u jednoho argumentu.|
|`global`|[Obory názvů](namespaces.md)|Slouží k odkazování na obor názvů .NET nejvyšší úrovně.|
|`if`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v konstruktorech podmíněného větvení.|
|`in`|[Smyčky: Výraz for...in](loops-for-in-expression.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|Používá se pro výrazy sekvence a v podrobné syntaxi k oddělení výrazů od vazeb.|
|`inherit`|[Dědičnost](inheritance.md)|Slouží k určení základní třídy nebo základního rozhraní.|
|`inline`|[Funkce](./functions/index.md)<br /><br />[Vložené funkce](./functions/inline-functions.md)|Slouží k označení funkce, která by měla být integrována přímo do kódu volajícího.|
|`interface`|[Rozhraní](interfaces.md)|Slouží k deklaraci a implementaci rozhraní.|
|`internal`|[Řízení přístupu](access-control.md)|Slouží k určení, že je člen viditelný uvnitř sestavení, ale mimo něj.|
|`lazy`|[Výrazy Lazy](lazy-expressions.md)|Slouží k zadání výrazu, který má být proveden pouze v případě, že je požadován výsledek.|
|`let`|[`let` vazby](./functions/let-bindings.md)|Slouží k přidružení (nebo k) názvu k hodnotě nebo funkci.|
|`let!`|[Asynchronní pracovní postupy](asynchronous-workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Používá se v asynchronních pracovních postupech k navázání názvu na výsledek asynchronního výpočtu nebo v jiných výrazech výpočtu, který se používá k vytvoření vazby názvu k výsledku, který je typu výpočtu.|
|`match`|[Výrazy shody](match-expressions.md)|Používá se k větvení porovnáním hodnoty se vzorem.|
|`match!`|[Výpočetní výrazy](computation-expressions.md#match)|Slouží k vložení volání do výpočetního výrazu a porovnávání vzorů na jeho výsledku.|
|`member`|[Členové](./members/index.md)|Slouží k deklaraci vlastnosti nebo metody v typu objektu.|
|`module`|[Moduly](modules.md)|Slouží k přidružení názvu ke skupině souvisejících typů, hodnot a funkcí k logickému oddělení od jiného kódu.|
|`mutable`|[Vazby let](./functions/let-bindings.md)|Slouží k deklaraci proměnné, tedy hodnoty, kterou lze změnit.|
|`namespace`|[Obory názvů](namespaces.md)|Slouží k přidružení názvu ke skupině souvisejících typů a modulů k logickému oddělení od jiného kódu.|
|`new`|[Konstruktory](./members/constructors.md)<br /><br />[Omezení](./generics/constraints.md)|Slouží k deklaraci, definování nebo vyvolání konstruktoru, který vytváří nebo který může vytvořit objekt.<br /><br />Používá se také v omezeních obecných parametrů k označení toho, že typ musí mít určitý konstruktor.|
|`not`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Ve skutečnosti není klíčové slovo. `not struct` v kombinaci se však používá jako omezení obecného parametru.|
|`null`|[Hodnoty Null](./values/null-values.md)<br /><br />[Omezení](./generics/constraints.md)|Označuje absenci objektu.<br /><br />Používá se také v omezeních obecných parametrů.|
|`of`|[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Delegáty](delegates.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Používá se v rozlišených sjednoceních k označení typu kategorií hodnot a v deklaracích delegování a výjimek.|
|`open`|[Deklarace importu: klíčové slovo `open`](import-declarations-the-open-keyword.md)|Slouží k zpřístupnění obsahu oboru názvů nebo modulu bez kvalifikace.|
|`or`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se s logickými podmínkami jako logický operátor `or`. Ekvivalent `||`.<br /><br />Používá se také v omezeních členů.|
|`override`|[Členové](./members/index.md)|Slouží k implementaci verze abstraktní nebo virtuální metody, která se liší od základní verze.|
|`private`|[Řízení přístupu](access-control.md)|Omezí přístup ke členovi na kód ve stejném typu nebo modulu.|
|`public`|[Řízení přístupu](access-control.md)|Umožňuje přístup ke členu mimo typ.|
|`rec`|[Funkce](./functions/index.md)|Slouží k označení toho, že funkce je rekurzivní.|
|`return`|[Asynchronní pracovní postupy](Asynchronous-Workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Slouží k označení hodnoty, která se má poskytnout jako výsledek výpočetního výrazu.|
|`return!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Slouží k označení výrazu výpočtu, který při vyhodnocování poskytuje výsledek obsahujícího výrazu výpočtu.|
|`select`|[Výrazy dotazu](query-expressions.md)|Používá se ve výrazech dotazů k určení toho, která pole nebo sloupce se mají extrahovat. Všimněte si, že se jedná o kontextové klíčové slovo, což znamená, že se ve skutečnosti nejedná o rezervované slovo a funguje pouze jako klíčové slovo v příslušném kontextu.|
|`static`|[Členové](./members/index.md)|Slouží k označení metody nebo vlastnosti, kterou lze volat bez instance typu, nebo člena hodnoty, který je sdílen mezi všemi instancemi typu.|
|`struct`|[Struktury](structures.md)<br /><br /> [Řazené kolekce členů](tuples.md)<br/><br/>[Omezení](./generics/constraints.md)|Slouží k deklaraci typu struktury.<br /><br/>Slouží k zadání řazené kolekce členů struktury.<br/><br />Používá se také v omezeních obecných parametrů.<br /><br />Používá se pro kompatibilitu OCaml v definicích modulů.|
|`then`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](./members/constructors.md)|Používá se v podmíněných výrazech.<br /><br />Slouží také k provádění vedlejších účinků po konstrukci objektu.|
|`to`|[Smyčky: výraz `for...to`](loops-for-to-expression.md)|Používá se ve smyčce `for` k označení rozsahu.|
|`true`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`try`|[Výjimky: try... Výraz with](./exception-handling/the-try-with-expression.md)<br /><br />[Výjimky: try... Výraz finally](./exception-handling/the-try-finally-expression.md)|Slouží k zavedení bloku kódu, který může generovat výjimku. Používá se společně s `with` nebo `finally`.|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Třídy](classes.md)<br /><br />[Záznamy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Výčty](enumerations.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Zkratky typů](type-abbreviations.md)<br /><br />[Měrné jednotky](units-of-measure.md)|Slouží k deklaraci třídy, záznamu, struktury, rozlišeného sjednocení, výčtového typu, měrné jednotky nebo zkratky typu.|
|`upcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je vyšší v řetězu dědičnosti.|
|`use`|[Správa prostředků: klíčové slovo `use`](resource-management-the-use-keyword.md)|Používá se místo `let` pro hodnoty, které vyžadují, aby se `Dispose` zavolaly k bezplatným prostředkům.|
|`use!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se místo `let!` v asynchronních pracovních postupech a dalších výrazech výpočtu pro hodnoty, které vyžadují, aby se `Dispose` zavolaly k bezplatným prostředkům.|
|`val`|[Explicitní pole: Klíčové slovo `val`](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatury](signature-files.md)<br /><br />[Členové](./members/index.md)|Používá se v signatuře k označení hodnoty nebo v typu k deklarování člena v omezeném situacích.|
|`void`|[Primitivní typy](basic-types.md)|Určuje typ `void` .NET. Používá se při spolupráci s dalšími jazyky .NET.|
|`when`|[Omezení](./generics/constraints.md)|Používá se pro logické podmínky (v*případě Guard*) u porovnávání vzorů a pro zavedení klauzule omezení pro parametr obecného typu.|
|`while`|[Smyčky: výraz `while...do`](loops-while-do-expression.md)|Zavádí konstrukci smyček.|
|`with`|[Výrazy shody](match-expressions.md)<br /><br />[Objektové výrazy](object-expressions.md)<br /><br />[Kopírování a aktualizace výrazů záznamů](copy-and-update-record-expressions.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Výjimky: výraz `try...with`](./exception-handling/the-try-with-expression.md)|Používá se společně s klíčovým slovem `match` ve výrazech porovnávání vzorů. Používá se také ve výrazech objektů, kopírování výrazů a příponách typů k zavedení definic členů a k zavedení obslužných rutin výjimek.|
|`yield`|[Seznamy](lists.md), [pole](arrays.md), [posloupnosti](sequences.md)|Používá se ve výrazu list, Array nebo Sequence k vytvoření hodnoty pro sekvenci. Obvykle se dá vynechat, protože je ve většině případů implicitní.|
|`yield!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se ve výrazu výpočtu k připojení výsledku daného výpočetního výrazu ke kolekci výsledků obsahujícího výrazu výpočtu.|

Následující tokeny jsou vyhrazené v F# , protože jsou klíčovými slovy v jazyce OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Použijete-li možnost kompilátoru `--mlcompatibility`, jsou výše uvedená klíčová slova k dispozici pro použití jako identifikátory.

Následující tokeny jsou vyhrazené jako klíčová slova pro budoucí rozšiřování F# jazyka:

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)
- [Možnosti kompilátoru](compiler-options.md)
