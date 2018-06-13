---
title: 'F # – konvence kódování'
description: 'Další obecné pokyny a idioms při psaní kódu pro jazyk F #.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457979"
---
# <a name="f-coding-conventions"></a>F # – konvence kódování

Následující konvence jsou formulovali ze zkušeností práce velké F # základy kódu. [Pět principů dobrý F # – kód](index.md#five-principles-of-good-f-code) jsou základem jednotlivá doporučení. Se jedná o [F # součást pokynů pro návrh](component-design-guidelines.md), ale platí pro všechny F # kód, ne jenom komponenty, například knihovny.

## <a name="organizing-code"></a>Uspořádání kódu

Dva primární způsoby uspořádání kód funkce F #: moduly a obory názvů. Ty jsou podobné, ale mají následující rozdíly:

* Obory názvů zjišťují jako obory názvů .NET. Moduly jsou kompilovány jako statické třídy.
* Obory názvů jsou vždy nejvyšší úrovně. Moduly lze nejvyšší úrovně a vnořené v rámci dalších modulů.
* Obory názvů, může zahrnovat víc souborů. Moduly nelze.
* Moduly může být doplněny pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]`.

Podle následujících pokynů můžete použít k uspořádání vašeho kódu.

### <a name="prefer-namespaces-at-the-top-level"></a>Dáváte přednost obory názvů na nejvyšší úrovni

Pro všechny veřejně použití kódu jsou obory názvů přednostní modulů na nejvyšší úrovni. Vzhledem k tomu, že se kompilují jako obory názvů .NET, jsou použití z jazyka C# s žádný problém.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Použití modulu nejvyšší úrovně se nemůže nacházet jiný při volat pouze z F #, ale pro C# příjemci, může být sledován volající tak, že aby se dosáhlo nároku `MyClass` s `MyCode` modulu.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Pečlivě použít. `[<AutoOpen>]`

`[<AutoOpen>]` Konstrukce můžete znečištění směrovány správu rozsah co je k dispozici pro volající a kde něco pochází z odpověď je "magic". Obecně se to dobré. Výjimku pro toto pravidlo je základní knihovny F #, samotné (i když tento fakt je také trochu sporná).

Je však pro vaše pohodlí Pokud máte pomocné funkce pro veřejné rozhraní API, který chcete uspořádat samostatně z této veřejné rozhraní API.

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...


    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

To vám umožní podrobnosti této aplikace samostatné implementace z veřejné rozhraní API funkce bez nutnosti k plnému určení pomocné rutiny pokaždé, když ji volat.

Kromě toho vystavení rozšiřující metody a tvůrci výrazů na úrovni oboru názvů se přehledně vyjadřují pomocí `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Použití `[<RequireQualifiedAccess>]` kdykoli může dojít ke konfliktu názvů, nebo si myslíte, že pomáhá s čitelnost

Přidávání `[<RequireQualifiedAccess>]` atribut na modul označuje, že modul nemusí otevřít a že vyžadují explicitní odkazy na elementy modulu kvalifikovaný přístup. Například `Microsoft.FSharp.Collections.List` modul má tento atribut.

To je užitečné, když funkce a hodnoty v modulu mají názvy, které mohou v konfliktu s názvy v dalších modulů. Vyžadování kvalifikovaný přístup může výrazně zvýšit dlouhodobé udržovatelnosti a evolvability knihovny.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Řazení `open` příkazy topologically

V jazyce F #, záleží na pořadí deklarace, včetně s `open` příkazy. To je rozdíl oproti C#, kde účinku `using` a `using static` je nezávislá řazení tyto příkazy v souboru.

V F # elementy otevřít do oboru stínové ostatní již existuje. To znamená, že změna `open` příkazy může změnit význam kódu. V důsledku toho všechny libovolný řazení všech `open` příkazy (například, alfanumericky) se obecně nedoporučuje, přidejte generovat různé chování, které by se dalo očekávat.

Místo toho doporučujeme řazení je [topologically](https://en.wikipedia.org/wiki/Topological_sorting); to znamená, pořadí vaše `open` příkazy v pořadí, ve kterém _vrstvy_ jsou definovány vašeho systému. Provádění alfanumerické řazení v rámci různých úrovní topologické může také zvážit.

Jako příklad uvádíme topologické řazení pro F # kompilátoru veřejné rozhraní API souboru služby:

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

Všimněte si, že konec řádku odděluje jednotlivé úrovně řazen alfanumericky později topologické vrstvy. To ještě jednou organizuje kód bez omylem stínový provoz hodnoty.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Pomocí třídy obsahují hodnoty, které mají vedlejší efekty

Existují tolikrát, kolikrát po inicializaci hodnotu může mít vedlejší účinky, jako je například vytvoření instance kontextu databáze nebo jiných vzdálený prostředek. Jedná se o tempting k inicializaci takové věci v modulu a použít ho v následujících funkcí:

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

Toto je často vhodné z několika důvodů:

Nejprve je konfigurace aplikace vložena do základu kódu s `dep1` a `dep2`. Toto je obtížné v, že větší základy kódu.

Druhý, staticky inicializovaného data nesmí obsahovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud samotné příslušné součásti bude používat více vláken. To jasně porušení podle `dep3`.

Nakonec inicializace modulu zkompiluje do statického konstruktoru pro celý kompilace jednotku. V případě chyby inicializace vázané na umožňují hodnotu v tomto modulu manifesty jako `TypeInitializationException` pak mezipaměti po celou dobu života aplikace. To může být obtížné diagnostikovat. Obvykle je vnitřní výjimka, která můžete se pokusit o důvodu, ale pokud není, nejsou k dispozici žádné o tom, co je hlavní příčinu.

Právě použijte místo toho jednoduchá pro závislosti:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

To umožňuje následující:

1. Když zavedete všechny závislé stavu mimo rozhraní API, sám sebe.
2. Konfiguraci lze provést nyní mimo rozhraní API.
3. Chyby v inicializaci pro závislé hodnoty nejsou pravděpodobně se projeví jako `TypeInitializationException`.
4. Rozhraní API je nyní snazší otestovat.

## <a name="error-management"></a>Chyba správy

Správa chyby ve velkých systémů je komplexní a nuanced zařízeními a neexistují žádné silver odrážek zajištění vaše systémy jsou odolné proti chybám a chovat správně. Následující pokyny by měl nabízí pokyny v navigace tento prostor obtížná.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Představují případech chyb a neplatný stav v typy vnitřní k vaší doméně

S [Rozlišované sjednocení](../language-reference/discriminated-unions.md), F # vám dává možnost představující stav vadný programu v systému typu. Příklad:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

V takovém případě existují tři způsoby známé, které stažení peníze z účtu bank může selhat. Každý případ chyby představuje v typu a proto být provedeny bezpečně v rámci programu.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Obecně platí, pokud je model různé způsoby, že něco můžete **nezdaří** ve vaší doméně, pak kód pro zpracování chyb už považován za něco musí řešit kromě toku regulární programu. Je jednoduše součástí normálního toku programu a nejsou považovány **výjimečných**. Existují dvě hlavní výhody k tomuto:

1. Je také spravovat jako doménu v průběhu času mění.
2. Chybových případech se snadněji testování částí.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Použijte výjimky, pokud není možné vyjádřit chyby s typy

Ne všechny chyby může být reprezentován v doméně problému. Jsou tyto druhy chyb *výjimečných* ve své podstatě, proto možnost vyvolávání a zachycení výjimek v jazyce F #.

První, doporučujeme, abyste si přečetli [pokynů pro návrh výjimka](../../standard/design-guidelines/exceptions.md). To platí také pro F #.

K dispozici v F # pro účely vyvolávání výjimek hlavní konstrukce považovat za v následujícím pořadí podle priority:

| Funkce | Syntaxe | Účel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Vyvolá `System.ArgumentNullException` s názvem zadaného argumentu. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Vyvolá `System.ArgumentException` s názvem zadaného argumentu a zprávy. |
| `invalidOp` | `invalidOp "message"` | Vyvolá `System.InvalidOperationException` se zadanou zprávou. |
|`raise`| `raise (ExceptionType("message"))` | Pro obecné účely mechanismus pro vyvolávání výjimek. |
| `failwith` | `failwith "message"` | Vyvolá `System.Exception` se zadanou zprávou. |
| `failwithf` | `failwithf "format string" argForFormatString` | Vyvolá `System.Exception` zprávou určenému řetězec formátu a jeho vstupů. |

Použití `nullArg`, `invalidArg` a `invalidOp` jako mechanizmus pro throw `ArgumentNullException`, `ArgumentException` a `InvalidOperationException` při vhodné.

`failwith` a `failwithf` funkce je nutno obecně protože vyvolají základní `Exception` typ, není určité výjimky. Dle [pokynů pro návrh výjimka](../../standard/design-guidelines/exceptions.md), kterou chcete vygenerovat více konkrétních výjimek, pokud je možné.

### <a name="using-exception-handling-syntax"></a>Pomocí syntaxe zpracování výjimek

F # podporuje vzory výjimky prostřednictvím `try...with` syntaxe:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Sjednocování funkce provést při krátkodobém výjimka porovnávání vzorů může být poněkud složité, pokud chcete zachovat čistou kód. Takové to je možné použít [aktivní vzorky](../language-reference/active-patterns.md) jako prostředek k skupiny funkce, které obaluje s případem chyba s výjimkou samotné. Může být například využívají rozhraní API, která při vyhodí výjimku, obklopuje cenné informace v metadatech výjimka. Rozbalování hodnotu užitečné v těle zaznamenané výjimky uvnitř aktivní vzor a vrací hodnota může být užitečné v některých situacích.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nepoužívejte monadic nahradit výjimky pro zpracování chyb

Výjimky jsou považovány za poněkud taboo v funkční programování. Výjimky skutečně, porušení čistotu, takže je bezpečné vzít v úvahu je konce není funkční. Ale když ve skutečnosti kde kód musí být spuštěn a že runtime, který může dojít k chybám bude ignorovat. Obecně platí napište kód za předpokladu, že většina věci čistý ani celkový, chcete-li minimalizovat nepříjemným výskyt nečekaných událostí.

Je důležité vzít v úvahu následující základní síly/aspektů výjimky s ohledem na jejich relevance a vhodnost v modulu runtime rozhraní .NET a mezi jazyky ekosystém jako celek:

1. Obsahují podrobné diagnostické informace, které je velmi užitečné při ladění problém.
2. Jsou dobře porozumí modul runtime a jinými jazyky rozhraní .NET.
3. Významné standardní ve srovnání s kódem, který prochází mimo jeho způsob, jak se může snížit *vyhnout* výjimky implementací určitou podmnožinu jejich sémantiku na základě ad hoc.

Tento třetí bod je velmi důležité. Pro triviální komplexních operací selhání použít výjimky může mít za následek práci s struktury takto:

```fsharp
Result<Result<MyType, string>, string list>
```

Což může způsobit snadno křehké kódu jako porovnávání se na chyby "stringly zadány":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Kromě toho může být tempting swallow všechny výjimky v desire "jednoduchý" funkce, která vrátí hodnotu typu "nicer":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Bohužel `tryReadAllText` může vyvolat množství výjimky podle velkého počtu věcí, které může dojít v systému souborů a tento kód zahodí rychle žádné informace o co může ve skutečnosti se špatně ve vašem prostředí. Pokud jste s typem výsledku, nahraďte tento kód, pak jste zpět "stringly zadány" Chyba při analýze zpráva:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

A umístění samotného objektu výjimka v `Error` konstruktor právě vynutí správně zabývat typ výjimky v lokalitě volání místo ve funkci. To efektivně vytvoří zaškrtnuté výjimky, které jsou často unfun řešení jako volající rozhraní API.

Dobrou alternativou k uvedených příkladech je k zachycení *konkrétní* výjimky a vrátí hodnotu smysl v kontextu této výjimky. Pokud změníte `tryReadAllText` funkce následujícím způsobem `None` další význam:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Místo funguje jako catch-all, tato funkce bude nyní správně zpracování případu, když soubor nebyl nalezen a přiřadit tento význam vraťte se. Tuto hodnotu můžete mapování v takovém případě chyba, při není zahození žádné kontextové informace nebo vynucení volající řešení případu, které nemusí být důležité v tomto bodě v kódu.

Typy, jako `Result<'Success, 'Error>` jsou vhodné pro základní operace, kde budou nejsou vnořené, a volitelné typů F # jsou ideální pro udávající, kdy se něco může buď vrátit *něco* nebo *nic*. Nejsou náhradní server pro výjimky, když a nesmí být při pokusu o používá k nahrazení výjimky. Místo toho se má být použita uvážlivě na adresu konkrétních aspektů výjimku a zásady správy chybová cílové způsoby.

## <a name="partial-application-and-point-free-programming"></a>Částečné aplikace a bez bodu programování

F # podporuje částečné aplikace a proto různé způsoby, jak program ve stylu volného bodu. To může být užitečné pro opakované použití kódu v modulu nebo implementace něco, ale obecně se něco vystavit veřejně. Obecně platí bez bodu programování není důsledku v a sám sebe a můžete přidat kognitivní představují významnou překážkou pro uživatele, kteří nejsou ponořena ve stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nepoužívejte částečné aplikace a currying veřejné rozhraní API

S výjimkou malé může být matoucí pro spotřebitele použití částečné aplikace v veřejná rozhraní API. Obvykle `let`-vázané hodnoty v F # – kód **hodnoty**, nikoli **funkce hodnoty**. Kombinování společně hodnoty a hodnoty, funkce může způsobit ukládání malý počet řádků kódu za s bit režie kognitivní, obzvláště pokud se například v kombinaci s operátory `>>` k vytváření funkcí.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Zvažte dopad nástrojů pro programování bez bodu

Curryfikované funkce není popisku jejich argumentů. Tato akce nemá tooling dopad. Vezměte v úvahu následující dvě funkce:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Obě jsou platná funkce, ale `funcWithApplication` je curryfikované funkce. Po přesunutí ukazatele myši jejich typy v editoru, zobrazí toto:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

V lokalitě volání popisů tlačítek v nástrojů, jako je například Visual Studio nebude poskytují smysluplný informace o tom, co `string` a `int` ve skutečnosti představují vstupní typy.

Pokud narazíte na bodu bez kódu jako `funcWithApplication` se veřejně použití, doporučuje se provést plnou expanzí η tak, aby nástrojů můžete vybrat až dále smysluplné názvy argumenty.

Kromě toho ladění kódu bez bodu může být náročné, pokud není možné. Ladicí nástroje závisí na hodnotách, které jsou vázány na názvy (například `let` vazby) tak, aby si můžete prohlédnout v polovině pomocných hodnot prostřednictvím spuštění. Pokud váš kód neobsahuje žádné hodnoty, chcete-li prověřit, není nic k ladění. V budoucnu, nástroje pro ladění může vyvíjet syntetizovat tyto hodnoty založená na cestách ke dříve spuštění, ale není vhodné zajistila vaše dokumenty na *potenciální* ladění funkce.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Vezměte v úvahu částečné aplikace jako techniku ke snížení interní standardní

Na rozdíl od předchozího bodu částečné aplikace je skvělý nástroj pro snížení zatížení často používaný v aplikaci nebo interní podrobnější informace o rozhraní API. Může být užitečné pro testování složitější rozhraní API, kde je často používaný často problémové jak nakládat s částí. Například následující kód ukazuje, jak můžete provést co nejvíce mocking architektury získáte bez nutnosti převádět vnější závislosti na těchto rozhraní a nemusíte se učit se souvisejícím sled prací rozhraní API.

Zvažte například následující topografie řešení:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` může například vystavení kódu:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testování částí `Transactions.doTransaction` v `ImplementationLogic.Tests.fspoj` je snadné:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Částečně použití `doTransaction` s mocking kontextu objektu umožňuje volání funkce ve všech testů jednotek bez nutnosti vytvořit mocked kontextu pokaždé, když:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Tento postup by neměl všeobecně aplikuje vaší celý codebase, ale je dobrým způsobem, jak snížit často používaný pro složité internals a tyto interní informace o testování částí.

## <a name="access-control"></a>Řízení přístupu

F # má několik možností [řízení přístupu](../language-reference/access-control.md), zděděné z co je k dispozici v modulu runtime rozhraní .NET. Tyto nejsou použitelné jenom pro typy – je lze využít pro funkce, příliš.

* Dáváte přednost jinou hodnotu než`public` typů a členů mají být veřejně použití. Tím se minimalizují také jaké několika příjemci k
* Zajistit, aby všechny pomocné funkce `private`.
* Zvažte použití `[<AutoOpen>]` na privátní modul pomocných funkcí, pokud budou množství.

## <a name="type-inference-and-generics"></a>Odvození typu a obecné typy

Odvození typu můžete uložit v zadávání spoustu standardní. A Automatická Generalizace v kompilátoru F # můžete napsat kód více obecné s téměř žádné další úsilí na druhé straně. Tyto funkce však nejsou všeobecně funkční.

* Vezměte v úvahu označování názvy argumentu s explicitní typy v veřejná rozhraní API a nespoléhejte na odvození typu proměnné pro tuto.

    Důvodem je, že **jste** by měla být v ovládacím prvku tvaru rozhraní API, není kompilátoru. I když kompilátor můžete provést úlohu dobře v odvození typů pro vás, je možné, že tvar změnu rozhraní API, pokud internals, který přitom spoléhá na změnily typy. To může být to, co chcete použít, ale bude skoro určitě výsledkem narušující změně rozhraní API, který pak bude mít podřízené příjemci k řešení. Místo toho když explicitně řídíte tvaru veřejné rozhraní API, pak můžete řídit, tyto změny ukončování řádků. V podmínky DDD to může být představit jako vrstva proti poškození.

* Vezměte v úvahu smysluplný pojmenujete obecné argumenty.

    Pokud píšete skutečně obecném kódu, které nejsou specifické pro konkrétní domény, může pomoci nějaký výstižný název jinými programátory pochopení, které pracují v doméně. Například parametr typu s názvem `'Document` v kontextu interakci s dokumentem databáze je jasnější, že dokument obecné typy jsou přípustné podle funkce nebo člen pracujete s.

* Vezměte v úvahu názvy parametrů obecného typu s PascalCase.

    Toto je obecná moct provádět akce v rozhraní .NET, proto se doporučuje používat PascalCase místo snake_case nebo camelCase.

Nakonec Automatická generalizace není vždy skvělým nástrojem pro osoby, které jsou nové F # nebo velké základu kódu. Není režie kognitivní pomocí součásti, které jsou obecné. Kromě toho pokud automaticky zobecněný funkce nejsou používat s různými typy vstupu (samostatně, pokud jsou určeny k použití jako takový umožňují) a potom žádné skutečné výhody jim se obecné v tomto bodě v čase. Vždy zvažte, pokud kód, který píšete budou ve skutečnosti využívat Obecné.

## <a name="performance"></a>Výkon

F # hodnoty jsou neměnné ve výchozím nastavení, která umožňuje vyhnout určité třídy chyb (zejména těchto zahrnující souběžnosti a paralelismus). Ale v určitých případech se pro dosažení optimálního (nebo i přiměřené) efektivitu dobu provádění nebo přidělení paměti rozpětí pracovní může nejlépe implementovat pomocí místní mutace stavu. To je možné v základu přihlášení s F # s použitím `mutable` – klíčové slovo.

Ale použití `mutable` v jazyce F # může mít rozporu s funkční čistotu. To je v pořádku, pokud upravit očekávání z čistoty [referenční průhlednost](https://en.wikipedia.org/wiki/Referential_transparency). Referenční průhlednost - není čistotu - je cílem při zápisu funkce F #. To umožňuje zapisovat rozhraní je funkční přes na základě mutace implementace pro výkon kódu kritického pro.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zalomení měnitelný kódu v neměnné rozhraní

S referenční transparentnosti jako cíl je důležité napsat kód, který nevystavuje měnitelný underbelly výkonu důležitých funkcí. Například následující kód implementuje `Array.contains` funkce v základní knihovny F #:

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

Volání této funkce vícekrát pole Základní nezmění, ani nebude vyžadovat údržbu žádný měnitelný stav v jeho použití. Referentially transparentní, je to i v případě, že téměř každý jednotlivý řádek kódu v něm používá mutace.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Vezměte v úvahu zapouzdřením měnitelný datový ve třídách

Předchozí příklad používá k zapouzdření operace pomocí měnitelný datový jedné funkce. To není vždy dostatečná pro složitější datových sad. Vezměte v úvahu následující sady funkcí:

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

Tento kód je původce, ale zveřejňuje na základě mutace datová struktura, že se opravdu jedná odpovědné za údržbu. To může být uzavřen uvnitř třídu bez základní členů, které můžete změnit:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` zapouzdří podkladová struktura dat na základě mutace, a tím není vynucení volající udržovat podkladová struktura data. Třídy jsou efektivní způsob, jak zapouzdřit data a rutin, které jsou založené na mutace bez vystavení podrobnosti pro volající.

### <a name="prefer-let-mutable-to-reference-cells"></a>Dáváte přednost `let mutable` na referenční buňky

Referenční buňky představují způsob, jak představují odkaz na hodnotu než vlastní hodnota. Přestože mohou být použity pro kód kritický pro výkon, se obecně nedoporučuje. Podívejte se na následující příklad:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Použijte odkaz na buňku teď "zahltí" všechny následné kódu pomocí museli dereference a znovu referenční základní data. Místo toho zvažte `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Kromě zajištění dostatečného jediný bod mutace uprostřed výrazu lambda, všechny ostatní kód, který dotykem `acc` to lze provést tak, aby se neliší využití od normální `let`-vázaný neměnné hodnotu. To bude usnadňují časem změnit.

## <a name="object-programming"></a>Objekt programování

F # má plnou podporu pro objekty a objektově orientované koncepty (ú). I když mnohé koncepty ú jsou výkonný a užitečné, ne všechny z nich jsou ideální používat. Následující seznamy nabízí pokyny k kategorií ú funkcí na vysoké úrovni.

**Zvažte použití těchto funkcí v mnoha situacích:**

* Zápisu s tečkou (`x.Length`)
* Členy instance
* Implicitní konstruktory
* Statické členy
* Indexer zápis (`arr.[x]`)
* Pojmenované a nepovinné argumenty
* Rozhraní a implementace rozhraní

**Nemáte přístup pro tyto funkce nejprve, ale uvážlivě aplikovat když jsou vhodné k vyřešení problému:**

* Přetěžování metody
* Zapouzdřené měnitelný dat
* Operátory pro typy
* Automaticky vlastnosti
* Implementace `IDisposable` a `IEnumerable`
* Rozšíření typů
* Události
* Struktury
* Delegáty
* Výčty

**Pokud je třeba ji používat obecně předejít tyto funkce:**

* Hierarchie dědičnosti na základě typu a implementace dědičnosti
* Hodnoty Null a `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Dáváte přednost složení přes dědičnost

[Složení přes dědičnost](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhotrvající stylu, které můžete řídit kód dobrý F #. Základní princip je, že by neměl vystavit základní třídu a vynutit volající dědění z získat funkce základní třídy.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Implementace rozhraní, pokud nepotřebujete třídu pomocí objektové výrazy

[Objekt výrazy](../language-reference/object-expressions.md) umožňují implementovat rozhraní za chodu na hodnotu bez nutnosti Uděláte to tak uvnitř třídu vazby implementovaných rozhraní. Je to vhodné, zvlášť pokud je _pouze_ musí implementovat rozhraní a není nutné pro úplné třídu.

Například, zde je kód, který běží v [Ionide](http://ionide.io/) zadat akce opravy na kód, pokud je symbol, který jste přidali `open` příkaz pro:

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Protože při interakci s Visual Studio kód rozhraní API není nutné pro třídu, objektové výrazy jsou ideální nástrojem pro to. Rovněž jsou důležité pro testování, pokud chcete se zakázaným inzerováním na rozhraní s testovací rutiny ad hoc způsobem částí.

## <a name="type-abbreviations"></a>Zkratky typů

[Typ – zkratky](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit štítek jiného typu, například podpis funkce nebo více komplexního typu. Například následující alias přiřadí štítek co je potřeba k definování výpočetní s [CNTK](https://www.microsoft.com/cognitive-toolkit/), hluboká učení knihovny:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Název je pohodlný způsob, jak označují všechny funkce, která odpovídá podpisu je aliasy. Pomocí zkratky typů jako to je vhodné a umožňuje více stručného kódu.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Nepoužívejte zkratky typů představují doménu

I když zkratky typů jsou vhodné pro pojmenujete funkce podpisy, může se jednat matoucí při zkrácený zápis parametru jiné typy. Vezměte v úvahu tato zkratka:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

To může být matoucí několika způsoby:

* `BufferSize` není abstrakci; je právě jiný název pro celé číslo.
* Pokud `BufferSize` je vystaven ve veřejné rozhraní API, ho můžete snadno dojít k nesprávné interpretaci rozumí více než jen `int`. Obecně platí, typ domény mají více atributů k nim a nejsou primitivní typy, jako je `int`. Tato zkratka v rozporu se předpokládá, že.
* Malá a velká písmena z `BufferSize` (PascalCase) znamená, že tento typ obsahuje další data.
* Tento alias nenabízí vyšší přehlednost ve srovnání s poskytováním pojmenovaný argument funkci.
* Zkratka nebude manifest v kompilovaném IL; je právě celé číslo a tento alias je konstrukce kompilaci.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

V souhrnu, nebezpečí s zkratky typů je, že jsou **není** abstrakce nad typy jsou zkrácený zápis parametru. V předchozím příkladu `BufferSize` je právě `int` skrytě se žádná další data ani žádné výhody ze systému typ kromě toho, co `int` již má.
