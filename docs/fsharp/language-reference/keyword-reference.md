---
title: Referenční dokumentace klíčových slov
description: 'Najdete zde odkazy na informace o všech klíčových slovech jazyka F #.'
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
- const_FS
dev_langs:
- FSharp
ms.date: 08/15/2020
ms.openlocfilehash: 15505c123dd0d6497fbc80c8fc9f0910018911ea
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558098"
---
# <a name="keyword-reference"></a>Referenční dokumentace klíčových slov

Toto téma obsahuje odkazy na informace o všech klíčových slovech jazyka F #.

## <a name="f-keyword-table"></a>Tabulka klíčových slov F #

V následující tabulce jsou uvedena všechna klíčová slova F # v abecedním pořadí spolu s krátkými popisy a odkazy na související témata, která obsahují další informace.

|Klíčové slovo|Odkaz|Popis|
|-------|----|-----------|
|`abstract`|[Členové](./members/index.md)<br /><br />[Abstraktní třídy](abstract-classes.md)|Označuje metodu, která buď nemá implementaci v typu, ve kterém je deklarovaná, nebo která je virtuální a má výchozí implementaci.|
|`and`|[`let` Vazeb](./functions/let-bindings.md)<br /><br />[Záznamy](records.md)<br /><br />[Členové](./members/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se ve vzájemně rekurzivních vazbách a záznamech, v deklaracích vlastností a s několika omezeními u obecných parametrů.|
|`as`|[Třídy](classes.md)<br /><br />[Porovnávání vzorů](Pattern-Matching.md)|Slouží k udělení názvu objektu aktuální třídě. Používá se také k předání názvu celému vzoru v rámci porovnávání vzorů.|
|`assert`|[Kontrolní výrazy](assertions.md)|Slouží k ověření kódu během ladění.|
|`base`|[Třídy](classes.md)<br /><br />[Dědičnost](inheritance.md)|Používá se jako název objektu základní třídy.|
|`begin`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje začátek bloku kódu.|
|`class`|[Třídy](classes.md)|V podrobné syntaxi označuje začátek definice třídy.|
|`default`|[Členové](./members/index.md)|Označuje implementaci abstraktní metody; používá se společně s deklarací abstraktní metody k vytvoření virtuální metody.|
|`delegate`|[Delegáti](delegates.md)|Slouží k deklaraci delegáta.|
|`do`|[do – vazby](./functions/do-bindings.md)<br /><br />[Smyčky: `for...to` výraz](loops-for-to-expression.md)<br /><br />[Smyčky: `for...in` výraz](loops-for-in-expression.md)<br /><br />[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Používá se v konstrukcích cyklů nebo k provádění imperativního kódu.|
|`done`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje konec bloku kódu ve výrazu smyčky.|
|`downcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je níže v řetězu dědičnosti.|
|`downto`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|Ve `for` výrazu, který se používá při započítání v opačném pořadí.|
|`elif`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení. Krátká forma `else if` .|
|`else`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněném větvení.|
|`end`|[Struktury](structures.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Záznamy](records.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|V definicích typů a příponách typů označuje konec oddílu definic členů.<br /><br />V podrobné syntaxi, která se používá k určení konce bloku kódu, který začíná `begin` klíčovým slovem.|
|`exception`|[Zpracování výjimek](./exception-handling/index.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Slouží k deklaraci typu výjimky.|
|`extern`|[Externí funkce](./functions/external-functions.md)|Označuje, že deklarovaný element programu je definovaný v jiném binárním souboru nebo sestavení.|
|`false`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`finally`|[Výjimky: `try...finally` výraz](./exception-handling/the-try-finally-expression.md)|Používá se společně s nástrojem `try` k zavedení bloku kódu, který se provede bez ohledu na to, jestli dojde k výjimce.|
|`fixed`|[Určí](fixed.md)|Používá se k "připnutí" ukazatele v zásobníku, aby se zabránilo uvolňování paměti.|
|`for`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)<br /><br />[Smyčky: Výraz for...in](loops-for-in-expression.md)|Používá se v konstruktorech cyklů.|
|`fun`|[Výrazy lambda: `fun` klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md)|Používá se ve výrazech lambda, označovaných také jako anonymní funkce.|
|`function`|[Výrazy shody](match-expressions.md)<br /><br />[Výrazy lambda: klíčové slovo fun](./functions/lambda-expressions-the-fun-keyword.md)|Používá se jako kratší alternativa `fun` klíčového slova a `match` výrazu ve výrazu lambda, který má porovnávání vzorů u jednoho argumentu.|
|`global`|[Obory názvů](namespaces.md)|Slouží k odkazování na obor názvů .NET nejvyšší úrovně.|
|`if`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Používá se v konstruktorech podmíněného větvení.|
|`in`|[Smyčky: Výraz for...in](loops-for-in-expression.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|Používá se pro výrazy sekvence a v podrobné syntaxi k oddělení výrazů od vazeb.|
|`inherit`|[Dědičnost](inheritance.md)|Slouží k určení základní třídy nebo základního rozhraní.|
|`inline`|[Functions](./functions/index.md)<br /><br />[Vložené funkce](./functions/inline-functions.md)|Slouží k označení funkce, která by měla být integrována přímo do kódu volajícího.|
|`interface`|[Rozhraní](interfaces.md)|Slouží k deklaraci a implementaci rozhraní.|
|`internal`|[Access Control](access-control.md)|Slouží k určení, že je člen viditelný uvnitř sestavení, ale mimo něj.|
|`lazy`|[Výrazy Lazy](lazy-expressions.md)|Slouží k zadání výrazu, který má být proveden pouze v případě, že je požadován výsledek.|
|`let`|[`let` Vazeb](./functions/let-bindings.md)|Slouží k přidružení (nebo k) názvu k hodnotě nebo funkci.|
|`let!`|[Asynchronní pracovní postupy](asynchronous-workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Používá se v asynchronních pracovních postupech k navázání názvu na výsledek asynchronního výpočtu nebo v jiných výrazech výpočtu, který se používá k vytvoření vazby názvu k výsledku, který je typu výpočtu.|
|`match`|[Výrazy shody](match-expressions.md)|Používá se k větvení porovnáním hodnoty se vzorem.|
|`match!`|[Výpočetní výrazy](computation-expressions.md#match)|Slouží k vložení volání do výpočetního výrazu a porovnávání vzorů na jeho výsledku.|
|`member`|[Členové](./members/index.md)|Slouží k deklaraci vlastnosti nebo metody v typu objektu.|
|`module`|[Moduly](modules.md)|Slouží k přidružení názvu ke skupině souvisejících typů, hodnot a funkcí k logickému oddělení od jiného kódu.|
|`mutable`|[let – vazby](./functions/let-bindings.md)|Slouží k deklaraci proměnné, tedy hodnoty, kterou lze změnit.|
|`namespace`|[Obory názvů](namespaces.md)|Slouží k přidružení názvu ke skupině souvisejících typů a modulů k logickému oddělení od jiného kódu.|
|`new`|[Konstruktory](./members/constructors.md)<br /><br />[Omezení](./generics/constraints.md)|Slouží k deklaraci, definování nebo vyvolání konstruktoru, který vytváří nebo který může vytvořit objekt.<br /><br />Používá se také v omezeních obecných parametrů k označení toho, že typ musí mít určitý konstruktor.|
|`not`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Ve skutečnosti není klíčové slovo. `not struct`V kombinaci se však používá jako omezení obecného parametru.|
|`null`|[Hodnoty null](./values/null-values.md)<br /><br />[Omezení](./generics/constraints.md)|Označuje absenci objektu.<br /><br />Používá se také v omezeních obecných parametrů.|
|`of`|[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Delegáti](delegates.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Používá se v rozlišených sjednoceních k označení typu kategorií hodnot a v deklaracích delegování a výjimek.|
|`open`|[Deklarace importu: `open` klíčové slovo](import-declarations-the-open-keyword.md)|Slouží k zpřístupnění obsahu oboru názvů nebo modulu bez kvalifikace.|
|`or`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se s logickými podmínkami jako logický `or` operátor. Ekvivalent `||` .<br /><br />Používá se také v omezeních členů.|
|`override`|[Členové](./members/index.md)|Slouží k implementaci verze abstraktní nebo virtuální metody, která se liší od základní verze.|
|`private`|[Access Control](access-control.md)|Omezí přístup ke členovi na kód ve stejném typu nebo modulu.|
|`public`|[Access Control](access-control.md)|Umožňuje přístup ke členu mimo typ.|
|`rec`|[Functions](./functions/index.md)|Slouží k označení toho, že funkce je rekurzivní.|
|`return`|[Asynchronní pracovní postupy](Asynchronous-Workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Slouží k označení hodnoty, která se má poskytnout jako výsledek výpočetního výrazu.|
|`return!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Slouží k označení výrazu výpočtu, který při vyhodnocování poskytuje výsledek obsahujícího výrazu výpočtu.|
|`select`|[Výrazy dotazu](query-expressions.md)|Používá se ve výrazech dotazů k určení toho, která pole nebo sloupce se mají extrahovat. Všimněte si, že se jedná o kontextové klíčové slovo, což znamená, že se ve skutečnosti nejedná o rezervované slovo a funguje pouze jako klíčové slovo v příslušném kontextu.|
|`static`|[Členové](./members/index.md)|Slouží k označení metody nebo vlastnosti, kterou lze volat bez instance typu, nebo člena hodnoty, který je sdílen mezi všemi instancemi typu.|
|`struct`|[Struktury](structures.md)<br /><br /> [N-tice](tuples.md)<br/><br/>[Omezení](./generics/constraints.md)|Slouží k deklaraci typu struktury.<br /><br/>Slouží k zadání řazené kolekce členů struktury.<br/><br />Používá se také v omezeních obecných parametrů.<br /><br />Používá se pro kompatibilitu OCaml v definicích modulů.|
|`then`|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](./members/constructors.md)|Používá se v podmíněných výrazech.<br /><br />Slouží také k provádění vedlejších účinků po konstrukci objektu.|
|`to`|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|Používá se ve `for` smyčce k označení rozsahu.|
|`true`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`try`|[Výjimky: Výraz try...with](./exception-handling/the-try-with-expression.md)<br /><br />[Výjimky: Výraz try...finally](./exception-handling/the-try-finally-expression.md)|Slouží k zavedení bloku kódu, který může generovat výjimku. Používá se společně s `with` nebo `finally` .|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Třídy](classes.md)<br /><br />[Záznamy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Výčty](enumerations.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Zkratky typů](type-abbreviations.md)<br /><br />[Měrné jednotky](units-of-measure.md)|Slouží k deklaraci třídy, záznamu, struktury, rozlišeného sjednocení, výčtového typu, měrné jednotky nebo zkratky typu.|
|`upcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je vyšší v řetězu dědičnosti.|
|`use`|[Správa prostředků: `use` klíčové slovo](resource-management-the-use-keyword.md)|Používá se místo `let` pro hodnoty, které vyžadují `Dispose` volání k uvolnění prostředků.|
|`use!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se místo `let!` v asynchronních pracovních postupech a dalších výrazech výpočtu pro hodnoty, které vyžadují, aby se `Dispose` prostředky vyvolaly pro uvolnění prostředků.|
|`val`|[Explicitní pole: `val` klíčové slovo](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatury](signature-files.md)<br /><br />[Členové](./members/index.md)|Používá se v signatuře k označení hodnoty nebo v typu k deklarování člena v omezeném situacích.|
|`void`|[Primitivní typy](basic-types.md)|Označuje typ .NET `void` . Používá se při spolupráci s dalšími jazyky .NET.|
|`when`|[Omezení](./generics/constraints.md)|Používá se pro logické podmínky (v*případě Guard*) u porovnávání vzorů a pro zavedení klauzule omezení pro parametr obecného typu.|
|`while`|[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Zavádí konstrukci smyček.|
|`with`|[Výrazy shody](match-expressions.md)<br /><br />[Objektové výrazy](object-expressions.md)<br /><br />[Kopírování a aktualizace výrazů záznamů](copy-and-update-record-expressions.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Výjimky: `try...with` výraz](./exception-handling/the-try-with-expression.md)|Používá se společně s `match` klíčovým slovem ve výrazech porovnávání vzorů. Používá se také ve výrazech objektů, kopírování výrazů a příponách typů k zavedení definic členů a k zavedení obslužných rutin výjimek.|
|`yield`|[Seznamy](lists.md), [pole](arrays.md), [posloupnosti](sequences.md)|Používá se ve výrazu list, Array nebo Sequence k vytvoření hodnoty pro sekvenci. Obvykle se dá vynechat, protože je ve většině případů implicitní.|
|`yield!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se ve výrazu výpočtu k připojení výsledku daného výpočetního výrazu ke kolekci výsledků obsahujícího výrazu výpočtu.|
|`const`|[Zprostředkovatelé typů](../tutorials/type-providers/index.md)| Zprostředkovatelé typů umožňují použití `const` jako klíčového slova k určení konstantního literálu jako argumentu parametru typu.|

Následující tokeny jsou vyhrazené v F #, protože se jedná o klíčová slova v jazyce OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Použijete-li `--mlcompatibility` možnost kompilátoru, jsou výše uvedená klíčová slova k dispozici pro použití jako identifikátory.

Následující tokeny jsou vyhrazené jako klíčová slova pro budoucí rozšiřování jazyka F #:

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

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)
- [Možnosti kompilátoru](compiler-options.md)
