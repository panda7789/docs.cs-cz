---
title: Referenční dokumentace klíčových slov
description: Najděte odkazy na informace o všech klíčových slovech jazyka F#.
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
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352311"
---
# <a name="keyword-reference"></a>Referenční dokumentace klíčových slov

Toto téma obsahuje odkazy na informace o všech klíčových slovech jazyka F#.

## <a name="f-keyword-table"></a>Tabulka klíčových slov F#

V následující tabulce jsou uvedena všechna klíčová slova Jazyka F# v abecedním pořadí spolu se stručným popisem a odkazy na příslušná témata, která obsahují další informace.

|Klíčové slovo|Odkaz|Popis|
|-------|----|-----------|
|`abstract`|[Členové](./members/index.md)<br /><br />[Abstraktní třídy](abstract-classes.md)|Označuje metodu, která buď nemá žádnou implementaci v typu, ve kterém je deklarována nebo která je virtuální a má výchozí implementaci.|
|`and`|[`let`Vazby](./functions/let-bindings.md)<br /><br />[Záznamy](records.md)<br /><br />[Členové](./members/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se ve vzájemně rekurzivnívazby a záznamy, v deklaracích vlastností a s více omezení na obecné parametry.|
|`as`|[Třídy](classes.md)<br /><br />[Porovnávání vzorů](Pattern-Matching.md)|Slouží k tomu, aby aktuální objekt třídy byl pojmenováním objektu. Používá se také k tomu, aby byl název celému vzoru v odpovídající vzor.|
|`assert`|[Kontrolní výrazy](assertions.md)|Slouží k ověření kódu během ladění.|
|`base`|[Třídy](classes.md)<br /><br />[Dědičnost](inheritance.md)|Používá se jako název objektu základní třídy.|
|`begin`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje začátek bloku kódu.|
|`class`|[Třídy](classes.md)|V podrobné syntaxi označuje začátek definice třídy.|
|`default`|[Členové](./members/index.md)|Označuje implementaci abstraktní metody; používá se společně s deklarací abstraktní metody k vytvoření virtuální metody.|
|`delegate`|[Delegáty](delegates.md)|Slouží k deklarování delegáta.|
|`do`|[Vazby do](./functions/do-bindings.md)<br /><br />[Smyčky: `for...to` Výraz](loops-for-to-expression.md)<br /><br />[Smyčky: `for...in` Výraz](loops-for-in-expression.md)<br /><br />[Smyčky: `while...do` Výraz](loops-while-do-expression.md)|Používá se v opakování konstrukce nebo ke spuštění imperativní kód.|
|`done`|[Podrobná syntaxe](verbose-syntax.md)|V podrobné syntaxi označuje konec bloku kódu ve zpětném vyjádření.|
|`downcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je nižší v řetězci dědičnosti.|
|`downto`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)|Ve `for` výrazu, který se používá při počítání v opačném směru.|
|`elif`|[Podmíněné výrazy:`if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněné větvení. Krátká forma `else if`.|
|`else`|[Podmíněné výrazy:`if...then...else`](conditional-expressions-if-then-else.md)|Používá se v podmíněné větvení.|
|`end`|[Struktury](structures.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Záznamy](records.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|V definicích typů a rozšíření chod typu označuje konec oddílu definice členů.<br /><br />V podrobné syntaxi, slouží k určení konce bloku kódu, který začíná klíčovým slovem. `begin`|
|`exception`|[Zpracování výjimek](./exception-handling/index.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Slouží k deklarování typu výjimky.|
|`extern`|[Externí funkce](./functions/external-functions.md)|Označuje, že deklarovaný prvek programu je definován v jiném binárním nebo sestavení.|
|`false`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`finally`|[Výjimky: `try...finally` Výraz](./exception-handling/the-try-finally-expression.md)|Používá se `try` společně s zavést blok kódu, který se spustí bez ohledu na to, zda dojde k výjimce.|
|`fixed`|[Dlouhodobého](fixed.md)|Slouží k "pin" ukazatel v zásobníku, aby se zabránilo, že jsou uvolněny.|
|`for`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)<br /><br />[Smyčky: Výraz for...in](loops-for-in-expression.md)|Používá se ve smyčkových konstrukcích.|
|`fun`|[Lambda Výrazy: `fun` Klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md)|Používá se ve výrazech lambda, označovaných také jako anonymní funkce.|
|`function`|[Výrazy shody](match-expressions.md)<br /><br />[Lambda Výrazy: Zábava klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md)|Používá se jako kratší `fun` alternativa `match` ke klíčovému slovu a výraz ve výrazu lambda, který má porovnávání vzorků na jeden argument.|
|`global`|[Jmenné prostory](namespaces.md)|Slouží k odkazování na obor názvů .NET nejvyšší úrovně.|
|`if`|[Podmíněné výrazy:`if...then...else`](conditional-expressions-if-then-else.md)|Používá se v konstrukcích podmíněného větvení.|
|`in`|[Smyčky: Výraz for...in](loops-for-in-expression.md)<br /><br />[Podrobná syntaxe](verbose-syntax.md)|Používá se pro sekvenční výrazy a v podrobné syntaxi k oddělení výrazů od vazeb.|
|`inherit`|[Dědičnost](inheritance.md)|Slouží k určení základní třídy nebo základního rozhraní.|
|`inline`|[Functions](./functions/index.md)<br /><br />[Vložené funkce](./functions/inline-functions.md)|Slouží k označení funkce, která by měla být integrována přímo do kódu volajícího.|
|`interface`|[Rozhraní](interfaces.md)|Slouží k deklarování a implementaci rozhraní.|
|`internal`|[Řízení přístupu](access-control.md)|Slouží k určení, že člen je viditelný uvnitř sestavení, ale ne mimo něj.|
|`lazy`|[Výrazy Lazy](lazy-expressions.md)|Slouží k určení výrazu, který má být proveden pouze v případě, že je potřeba výsledek.|
|`let`|[`let`Vazby](./functions/let-bindings.md)|Slouží k přidružení nebo vazbě názvu k hodnotě nebo funkci.|
|`let!`|[Asynchronní pracovní postupy](asynchronous-workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Používá se v asynchronních pracovních postupech k vytvoření svázání názvu s výsledkem asynchronního výpočtu nebo v jiných výpočetních výrazech, které se používají k vazbě názvu na výsledek, který je typu výpočtu.|
|`match`|[Výrazy shody](match-expressions.md)|Používá se k větvení porovnáním hodnoty se vzorkem.|
|`match!`|[Výpočetní výrazy](computation-expressions.md#match)|Slouží k vložení volání výpočtového výrazu a vzoru odpovídá jeho výsledku.|
|`member`|[Členové](./members/index.md)|Slouží k deklarování vlastnosti nebo metody v typu objektu.|
|`module`|[Moduly](modules.md)|Slouží k přidružení názvu ke skupině souvisejících typů, hodnot a funkcí, aby byl logicky oddělen od jiného kódu.|
|`mutable`|[let – vazby](./functions/let-bindings.md)|Slouží k deklarování proměnné, to znamená, že hodnota, která může být změněna.|
|`namespace`|[Jmenné prostory](namespaces.md)|Slouží k přidružení názvu ke skupině souvisejících typů a modulů, aby byl logicky oddělen od jiného kódu.|
|`new`|[Konstruktory](./members/constructors.md)<br /><br />[Omezení](./generics/constraints.md)|Slouží k deklarování, definování nebo vyvolání konstruktoru, který vytváří nebo může vytvořit objekt.<br /><br />Používá se také v omezení obecných parametrů k označení, že typ musí mít určitý konstruktor.|
|`not`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Ve skutečnosti to není klíčové slovo. V `not struct` kombinaci se však používá jako obecné omezení parametru.|
|`null`|[Hodnoty Null](./values/null-values.md)<br /><br />[Omezení](./generics/constraints.md)|Označuje nepřítomnost objektu.<br /><br />Používá se také v obecných omezení chodparametrů.|
|`of`|[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Delegáty](delegates.md)<br /><br />[Typy výjimek](./exception-handling/exception-types.md)|Používá se v discriminated sjednocení k označení typu kategorií hodnot a v delegáta a výjimky prohlášení.|
|`open`|[Dovozní prohlášení: `open` Klíčové slovo](import-declarations-the-open-keyword.md)|Slouží k zpřístupnění obsahu oboru názvů nebo modulu bez kvalifikace.|
|`or`|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)<br /><br />[Omezení](./generics/constraints.md)|Používá se s logickými `or` podmínkami jako logický operátor. Odpovídá `||`.<br /><br />Používá se také v omezení chanaté členy.|
|`override`|[Členové](./members/index.md)|Slouží k implementaci verze abstraktní nebo virtuální metody, která se liší od základní verze.|
|`private`|[Řízení přístupu](access-control.md)|Omezuje přístup k členu na kód ve stejném typu nebo modulu.|
|`public`|[Řízení přístupu](access-control.md)|Umožňuje přístup k členu mimo typ.|
|`rec`|[Functions](./functions/index.md)|Slouží k označení, že funkce je rekurzivní.|
|`return`|[Asynchronní pracovní postupy](Asynchronous-Workflows.md)<br /><br />[Výpočetní výrazy](computation-expressions.md)|Slouží k označení hodnoty, která má být poskytnuta jako výsledek výpočtového výrazu.|
|`return!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se k označení výpočetního výrazu, který při vyhodnocení poskytuje výsledek obsahujícího výpočetního výrazu.|
|`select`|[Výrazy dotazu](query-expressions.md)|Používá se ve výrazech dotazu k určení polí nebo sloupců, které mají být extrahovány. Všimněte si, že se jedná o kontextové klíčové slovo, což znamená, že ve skutečnosti není vyhrazené slovo a funguje pouze jako klíčové slovo v příslušném kontextu.|
|`static`|[Členové](./members/index.md)|Používá se k označení metody nebo vlastnosti, která může být volána bez instance typu nebo člena hodnoty, který je sdílen mezi všemi instancemi typu.|
|`struct`|[Struktury](structures.md)<br /><br /> [N-tice](tuples.md)<br/><br/>[Omezení](./generics/constraints.md)|Slouží k deklarování typu struktury.<br /><br/>Slouží k určení strukturní řazené kolekce členů.<br/><br />Používá se také v obecných omezení chodparametrů.<br /><br />Používá se pro kompatibilitu OCaml v definicích modulů.|
|`then`|[Podmíněné výrazy:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](./members/constructors.md)|Používá se v podmíněných výrazech.<br /><br />Používá se také k provádění vedlejších účinků po konstrukci objektu.|
|`to`|[Smyčky: `for...to` Výraz](loops-for-to-expression.md)|Používá `for` se ve smyčkách k označení rozsahu.|
|`true`|[Primitivní typy](basic-types.md)|Používá se jako logický literál.|
|`try`|[Výjimky: Výraz try...with](./exception-handling/the-try-with-expression.md)<br /><br />[Výjimky: Výraz try...finally](./exception-handling/the-try-finally-expression.md)|Slouží k zavedení bloku kódu, který může generovat výjimku. Používá se `with` `finally`společně s nebo .|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Třídy](classes.md)<br /><br />[Záznamy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Výčty](enumerations.md)<br /><br />[Rozlišovaná sjednocení](discriminated-unions.md)<br /><br />[Zkratky typů](type-abbreviations.md)<br /><br />[Měrné jednotky](units-of-measure.md)|Slouží k deklarování třídy, záznamu, struktury, discriminated sjednocení, typu výčtu, měrné jednotky nebo zkratky typu.|
|`upcast`|[Přetypování a převody](casting-and-conversions.md)|Slouží k převodu na typ, který je vyšší v řetězci dědičnosti.|
|`use`|[Správa zdrojů: `use` Klíčové slovo](resource-management-the-use-keyword.md)|Používá se `let` místo pro `Dispose` hodnoty, které vyžadují volání k uvolnění prostředků.|
|`use!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se `let!` místo v asynchronních pracovních postupech a dalších výpočetních výrazech pro hodnoty, které vyžadují `Dispose` volání volných prostředků.|
|`val`|[Explicitní pole: Klíčové slovo `val`](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatury](signature-files.md)<br /><br />[Členové](./members/index.md)|Používá se v podpisu k označení hodnoty nebo typu deklarovat člena v omezených situacích.|
|`void`|[Primitivní typy](basic-types.md)|Označuje typ `void` .NET. Používá se při spolupráci s jinými jazyky .NET.|
|`when`|[Omezení](./generics/constraints.md)|Používá se pro logické podmínky *(když chrání)* na pole odpovídá a zavést klauzuli omezení pro parametr obecného typu.|
|`while`|[Smyčky: `while...do` Výraz](loops-while-do-expression.md)|Zavádí smyčkové konstrukce.|
|`with`|[Výrazy shody](match-expressions.md)<br /><br />[Objektové výrazy](object-expressions.md)<br /><br />[Kopírování a aktualizace výrazů záznamů](copy-and-update-record-expressions.md)<br /><br />[Rozšíření typů](type-extensions.md)<br /><br />[Výjimky: `try...with` Výraz](./exception-handling/the-try-with-expression.md)|Používá se `match` společně s klíčovým slovem ve vzorodpovídající výrazy. Používá se také ve výrazech objektu, výrazech pro kopírování záznamů a rozšířeních typů k zavedení definic členů a k zavedení obslužných rutin výjimek.|
|`yield`|[Seznamy](lists.md), [Pole](arrays.md), [Sekvence](sequences.md)|Používá se ve výrazu seznamu, matice nebo sekvence k vytvoření hodnoty pro sekvenci. Obvykle lze vynechat, protože je implicitní ve většině situací.|
|`yield!`|[Výpočetní výrazy](computation-expressions.md)<br /><br />[Asynchronní pracovní postupy](asynchronous-workflows.md)|Používá se ve výrazu výpočtu připojit výsledek daného výpočtu výrazu do kolekce výsledků pro obsahující výpočetní výraz.|

Následující tokeny jsou vyhrazeny v Jazyce F#, protože jsou klíčová slova v jazyce OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Pokud použijete `--mlcompatibility` možnost kompilátoru, výše uvedená klíčová slova jsou k dispozici pro použití jako identifikátory.

Následující tokeny jsou vyhrazeny jako klíčová slova pro budoucí rozšíření jazyka F#:

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

- [Referenční příručka jazyka F#](index.md)
- [Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)
- [Možnosti kompilátoru](compiler-options.md)
