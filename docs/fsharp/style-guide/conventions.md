---
title: 'Převody kódování F #'
description: 'Další obecné pokyny a idiomy při psaní kódu jazyka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 21119b6d69e00f359104bfb6eab7681bdbfb8d78
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087385"
---
# <a name="f-coding-conventions"></a>Převody kódování F #

Následující konvence jsou formulovat z prostředí pro práci s velké F # základů kódu. [Pět zásady dobré kódu jazyka F #](index.md#five-principles-of-good-f-code) jsou základem pro jednotlivá doporučení. Se vztahují k [pokyny pro návrh komponentu F #](component-design-guidelines.md), ale platí pro všechny kódu jazyka F #, ne jenom komponent, jako jsou knihovny.

## <a name="organizing-code"></a>Uspořádání kódu

F # obsahuje dva primární způsoby, jak organizovat kód: modulů a oborů názvů. Ty jsou podobné, ale mají tyto věci:

* Obory názvů jsou kompilovány jako obory názvů rozhraní .NET. Moduly jsou kompilovány jako statické třídy.
* Obory názvů jsou vždy nejvyšší úrovně. Moduly je možné nejvyšší úrovně a vnořené v jiných modulů.
* Obory názvů může zahrnovat více souborů. Moduly nelze.
* Moduly, může být doplněny pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]`.

Podle následujících pokynů můžete použít k uspořádání kódu.

### <a name="prefer-namespaces-at-the-top-level"></a>Dáváte přednost oborů názvů na nejvyšší úrovni

Pro všechny veřejně použitelné kódu obory názvů jsou přednostní moduly na nejvyšší úrovni. Vzhledem k tomu, že se kompilují jako obory názvů .NET, jsou použitelné z jazyka C# s žádný problém.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Použití nejvyšší úrovně modulu nemusí vypadat jinak, při volání pouze z jazyka F #, ale pro C# spotřebitele, může být sledován volající tak, že k získání způsobilosti `MyClass` s `MyCode` modulu.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Pečlivě použít. `[<AutoOpen>]`

`[<AutoOpen>]` Konstrukce můžete znečištění směrovány správu rozsah co je k dispozici pro volající a odpověď na něco ze kterého pochází je "magické". Většinou to není dobrá věc. Výjimkou z tohoto pravidla je základní knihovny F #, samotný (i když tato skutečnost je také bit kontroverzním).

Je však pohodlí Pokud máte pomocnou funkci pro veřejné rozhraní API, kterou chcete uspořádat samostatně z této veřejné rozhraní API.

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

Díky tomu můžete podrobnosti implementace čistě samostatné z veřejné rozhraní API funkce bez nutnosti k plnému určení pomocné rutiny pokaždé, když ji volat.

Kromě toho vystavuje metody rozšíření a Tvůrce výrazů na úrovni oboru názvů lze elegantně vyjádřit pomocí `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Použití `[<RequireQualifiedAccess>]` vždy, když mohla být v konfliktu názvů, nebo máte pocit, že pomáhá s čitelnost

Přidávání `[<RequireQualifiedAccess>]` atribut do modulu označuje, že modul nelze otevřít, a přístup, vyžaduje explicitní odkazy na elementy modulu kvalifikovaný. Například `Microsoft.FSharp.Collections.List` modul nemá tento atribut.

To je užitečné, když funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v dalších modulů. Které vyžadují přístup pro kvalifikovaný může výrazně zvýšit dlouhodobou udržovatelnost a ovlivňujících knihovny.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Řazení `open` příkazy topologically

V jazyce F #, záleží na pořadí deklarace, včetně `open` příkazy. To je rozdíl oproti C#, ve kterém účinek `using` a `using static` je nezávislý na pořadí těchto příkazů do souboru.

V jazyce F # prvky otevřít do oboru stínové ostatní již existuje. To znamená, že změny pořadí `open` příkazů může změnit význam kódu. V důsledku toho všechny libovolného řazení všech `open` příkazy (například alfanumericky) se obecně nedoporučuje, přidejte generovat různé chování by se dalo očekávat.

Namísto toho doporučujeme je seřadit [topologically](https://en.wikipedia.org/wiki/Topological_sorting); to znamená pořadí vaše `open` příkazů v pořadí, ve kterém _vrstvy_ systému jsou definovány. Provádění alfanumerické řazení v rámci různých topologické vrstvy mohou také zvážit.

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

Všimněte si, že konec řádku odděluje topologické vrstvy s každou vrstvou seřazený alfanumericky později. To čistě slouží k uspořádání kódu bez náhodně stínováním hodnoty.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Použití tříd obsahující hodnoty, které mají vedlejší účinky

Mnohokrát se vám při inicializaci hodnota může mít vedlejší účinky, jako je vytvoření instance kontextu do databáze nebo jiného vzdáleného prostředku. Je lákavé k inicializaci prvků v modulu a jeho použití v následující funkce:

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

To je často vhodné mít několik důvodů:

Nejprve konfigurace aplikace se vloží do základu kódu `dep1` a `dep2`. Toto je obtížné udržovat v větší základů kódu.

Druhý, staticky inicializovaná data by neměl obsahovat hodnoty, které nejsou vláknově bezpečné, pokud vaše komponenta samotné používat více vláken. To je jasně byla porušena `dep3`.

Nakonec inicializace modulu kompiluje do statického konstruktoru pro celý kompilační jednotky. Pokud v inicializace hodnoty vazbou let v tomto modulu dojde k jakékoli chybě, manifesty jako `TypeInitializationException` , která se pak zapíší do mezipaměti po celou dobu života aplikace. To může být obtížné diagnostikovat. Obvykle je vnitřní výjimku, která se může pokusit o důvodu, ale pokud není, nejsou k dispozici žádné o tom, co je hlavní příčinu.

Stačí použijte místo toho jednoduchou třídu pro uložení závislosti:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

To umožňuje následující:

1. Doručením (push) libovolný závislé stavu mimo samotné rozhraní API.
2. Konfiguraci můžete nyní provést mimo rozhraní API.
3. Chyby při inicializaci pro závislé hodnoty nejsou pravděpodobně se projeví jako `TypeInitializationException`.
4. Rozhraní API je teď snazší testování.

## <a name="error-management"></a>Správa chyb

Správa chyb v rozsáhlých systémů je složitá a odlišování zařízeními a neexistují žádné silver odrážky zajištění vašich systémů jsou odolné proti chybám a dobře se chovají. Tyto pokyny byste měli nabízet podle pokynů uvedených v procházení tohoto obtížné prostoru.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Představují případy chyb a neplatný stav v typech, které jsou přirozené pro vaši doménu

S [Rozlišované sjednocení](../language-reference/discriminated-unions.md), F # vám dává možnost představující stav vadným programu v systému typů. Příklad:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

V tomto případě existují tři způsoby známé, které zrušení peníze od bankovním účtu může selhat. Každý případ chyby je reprezentován v typu a mohou tedy řešit bezpečně v celém programu.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Obecně platí, pokud různé způsoby, jak lze modelovat, že něco můžete **selhání** ve vaší doméně, pak kód pro zpracování chyb už se počítá jako něco musí čelit vedle regulární programu. Je jednoduše součástí normálního toku programu a nejsou považovány za **výjimečných**. Existují dvě hlavní výhody tohoto:

1. Je snazší Údržba jako vaši doménu v průběhu času mění.
2. Případy chyb je snazší testování částí.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Použijte výjimky, pokud chyby nejde reprezentovat typy

Ne všechny chyby lze znázornit v doméně problému. Tyto druhy chyb jsou *výjimečných* ze své podstaty, proto schopnost vyvolat a zachycení výjimek v jazyce F #.

Nejprve se doporučuje, abyste si přečetli [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md). Tyto platí také pro F #.

Hlavní konstrukce, které jsou k dispozici v jazyce F # za účelem vyvolání výjimky by měl být v následujícím pořadí podle priority:

| Funkce | Syntaxe | Účel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Vyvolá `System.ArgumentNullException` s názvem zadaného argumentu. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Vyvolá `System.ArgumentException` s názvem zadaného argumentu a zprávy. |
| `invalidOp` | `invalidOp "message"` | Vyvolá `System.InvalidOperationException` se zadanou zprávou. |
|`raise`| `raise (ExceptionType("message"))` | Pro obecné účely mechanismus pro vyvolání výjimky. |
| `failwith` | `failwith "message"` | Vyvolá `System.Exception` se zadanou zprávou. |
| `failwithf` | `failwithf "format string" argForFormatString` | Vyvolá `System.Exception` a zobrazí se zpráva určená formátovací řetězec a jeho vstupů. |

Použití `nullArg`, `invalidArg` a `invalidOp` jako mechanismus pro vyvolání `ArgumentNullException`, `ArgumentException` a `InvalidOperationException` vhodných.

`failwith` a `failwithf` funkce by měla být obecně vyhnout, protože vyvolají základní `Exception` typ, ne určité výjimky. Jak je uvedeno [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md), chcete vyvolat více specifické výjimky, pokud je to možné.

### <a name="using-exception-handling-syntax"></a>Pomocí syntaxe zpracování výjimek

Jazyk F # podporuje vzory výjimky prostřednictvím `try...with` syntaxi:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Sjednocování funkci provést i v případě výjimku s porovnáváním vzorů může být trochu složité, pokud chcete zachovat čistý kód. Jeden takový způsob, jak se o to postarají je použití [aktivní vzory](../language-reference/active-patterns.md) jako způsob, jak kolem s případem chyba s výjimkou samotné funkce skupiny. Může být například využívání rozhraní API, když dojde k výjimce, uzavře cenné informace v metadatech výjimky. Rozbalení užitečné hodnotu v těle Zachycenou výjimku uvnitř Active vzor a vrací hodnota může být užitečné v některých situacích.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nepoužívejte monadic nahradit výjimky pro zpracování chyb

Výjimky jsou považovány za poněkud taboo do funkčního programování. Ve skutečnosti výjimky porušují čistoty tak, aby byl bezpečně zvažovat je to docela není funkční. Ale ve skutečnosti je množství kde musíte spustit kód a tohoto modulu runtime, které může dojít k chybám bude ignorovat. Obecně za předpokladu, že většinu toho, co jsou čistě ani celkový, chcete-li minimalizovat nepříjemným překvapením psaní kódu.

Je důležité vzít v úvahu následující základní výhody/aspekty výjimky s ohledem na jejich důležitosti a vhodnost v modulu runtime .NET a ekosystém mezi jazyky jako celku:

1. Obsahují podrobné diagnostické informace, které je velmi užitečné při ladění chyby.
2. Jsou dobře porozumí modul runtime a jinými jazyky rozhraní .NET.
3. Se může redukovat významné ve srovnání s kódem, který dostane mimo jeho způsob, jak *vyhnout* výjimky implementací určité dílčí sady z jejich sémantiku na základě ad-hoc.

Tento třetí bod je velmi důležité. Triviální složitých operací použití výjimky může vést k práci s struktury následujícím způsobem:

```fsharp
Result<Result<MyType, string>, string list>
```

Což může snadno způsobit křehké kód například porovnávání vzorů "stringly typu" chyby:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Kromě toho může být lákavé spolknout jakoukoliv výjimku v touhy "jednoduchý" funkce, která vrátí "nicer" typ:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Bohužel `tryReadAllText` může vyvolat množství výjimek, které jsou založené na řadu věcí, které může dojít v systému souborů a tento kód zahodí okamžitě žádné informace o co může ve skutečnosti být špatně ve vašem prostředí. Pokud je tento kód nahradit typu výsledku, pak jste zpět "stringly typu" Chyba při analýze zprávy:

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

A umístění samotného objektu výjimky v `Error` konstruktor právě vynutí správně řešit typ výjimky v lokalitě volání, nikoli ve funkci. To efektivně vytvoří výjimky kontrolovaný, kterých je známo, že unfun řešit jako volající rozhraní API.

Dobrou alternativou výše uvedených příkladech se k zachycení *konkrétní* výjimky a vrácení smysluplné hodnoty v rámci této výjimky. Pokud změníte `tryReadAllText` následujícím způsobem funkci `None` má další význam:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Místo funguje jako pokrývající vše, tato funkce bude nyní správně zpracování případu, pokud soubor se nepovedlo najít a přiřadit tento význam pro vrácení. Tuto hodnotu můžete namapovat na takovém Chyba při rušení žádné kontextové informace ani Vynucení volající řešit případ, který nemusí být od tohoto okamžiku v kódu.

Typy, jako `Result<'Success, 'Error>` jsou vhodné pro základní operace, kde nejsou vnořené, a volitelné typů F # jsou ideální pro udávající, kdy se něco může buď vrátit *něco* nebo *nic*. Nejsou náhradou za výjimky, ale a neměl by se při pokusu o nahradit výjimky. Místo toho se musí uplatnit uvážlivě na adresu specifických aspektů výjimky a chybové zásady správy cílové způsoby.

## <a name="partial-application-and-point-free-programming"></a>Částečné použití argumentů a bodu bez programování

F # podporuje částečné použití argumentů a proto různé způsoby, jak program ve stylu bez bodu. To může být užitečné pro opakované využívání kódu v rámci modulu nebo provádění něco, ale není obvykle něco, co je veřejně zpřístupnit. Obecně platí bodu bez programování není důsledku v a sám sebe a můžete přidat kognitivní významnou překážkou pro uživatele, kteří nejsou ponoří ve stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nepoužívejte částečné použití argumentů a curryfikace ve veřejných rozhraní API

S výjimkou malý použití částečné použití argumentů ve veřejných rozhraní API může být matoucí pro uživatele. Obvykle `let`– hodnoty vazby v kódu F # jsou **hodnoty**, nikoli **funkce hodnoty**. Kombinace společně hodnoty a hodnoty funkcí může vést k uložení malý počet řádků kódu výměnou za hodně nemuseli jsme se zdržovat, zejména v případě, že v kombinaci s operátory, jako `>>` sestavit funkce.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Zvažte případné dopady nástroje bodu bez programování

Curryfikované funkce neoznačuje popiskem svých argumentů. Tato akce nemá vliv nástrojů. Vezměte v úvahu tyto dvě funkce:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Obě jsou platná funkce, ale `funcWithApplication` curryfikované funkce. Když najedete myší jejich typy v editoru, uvidíte toto:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

V lokalitě volání popisků v nástroje, jako je Visual Studio vám neposkytne smysluplné informace o tom, co `string` a `int` ve skutečnosti představují vstupní typy.

Pokud narazíte na kódu bez bodu jako `funcWithApplication` , který je veřejně použitelné, doporučuje se provést plnou expanzí η tak, aby nástrojů můžete vybrat až dále smysluplné názvy argumentů.

Kromě toho ladění kódu bez bod může být náročné, pokud není možné. Ladicí nástroje spoléhají na hodnoty, které jsou vázány na názvy (například `let` vazby) tak, aby si mohli prohlédnout hodnoty, ležící polovině spuštění. Pokud váš kód neobsahuje žádné hodnoty ke kontrole, není nutné nic ladění. V budoucnu, nástroje pro ladění může vyvíjet tak, aby odpovídaly tyto hodnoty na základě dříve provedený cest, ale není vhodné zajistila vaše sázka na *potenciální* ladění funkcí.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Vezměte v úvahu částečné použití argumentů jako technika na interní redukovat

Na rozdíl od předchozího bodu částečné použití argumentů je skvělý nástroj pro snížení často používaný v rámci aplikace nebo interní podrobnější informace o rozhraní API. Může být užitečné při provádění složitějších rozhraní API, kde je často používaný text často problémy řešit testování částí. Například následující kód ukazuje, jak dosáhnout co nejvíce napodobování architektury získáte bez nutnosti přepínat externí závislost na těchto rozhraní a nemusíte se učit se souvisejícím sled prací rozhraní API.

Představte si třeba následující topografie řešení:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` kód může zveřejnit jako například:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testování částí `Transactions.doTransaction` v `ImplementationLogic.Tests.fspoj` snadno:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Částečně použití `doTransaction` napodobování kontextu objektu umožňuje volání funkce ve všech testování částí, aniž by bylo nutné vytvořit imitaci kontextu pokaždé, když:

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

Tento postup neměl být všeobecně aplikován na celém základu kódu, ale je dobrým způsobem, jak redukovat pro složité interní informace a tyto interní informace o testování částí.

## <a name="access-control"></a>Řízení přístupu

F # obsahuje několik možností [řízení přístupu](../language-reference/access-control.md), zděděné z co je k dispozici v modulu .NET runtime. Ty nejsou použitelné pouze pro typy – můžete využít pro funkce je moc.

* Preferovat jinou hodnotu než`public` typy a členy, dokud nebudete potřebovat, aby to byla veřejně použitelné. Tím se minimalizují také jaké několik příjemců do.
* Přitom se snaží zachovat všechny funkce pomocné rutiny `private`.
* Zvažte použití `[<AutoOpen>]` v privátní modulu pomocné funkce, pokud budou mnoho.

## <a name="type-inference-and-generics"></a>Odvození typu proměnné a obecné typy

Odvození typu proměnné můžete uložit z psát spoustu často používaný text. A Automatická Generalizace v kompilátoru F # můžete napsat obecnějším kód s téměř žádná práce navíc z vaší strany. Tyto funkce však nejsou univerzálně dobré.

* Vezměte v úvahu názvy argumentů značení s explicitní typy ve veřejných rozhraní API a nespoléhejte na odvození typu proměnné pro tuto.

    Důvodem je, že **vám** by měl být kontrolu nad tvar vaše rozhraní API, není kompilátor. Ačkoli kompilátor může provést úlohu pořádku v odvození typů za vás, je možné mít tvar změny rozhraní API, pokud se změnily interní informace, které spoléhá na typy. To může být žádoucí, ale je téměř jistě způsobí narušující změně rozhraní API se pak bude mít podřízené příjemci. Místo toho pokud explicitně určit tvar objektu veřejné rozhraní API, pak můžete určit tyto nejnovější změny. V podmínkách DDD to můžete představit jako vrstvu odolnou proti poškození.

* Zvažte smysluplný název k obecným argumentům.

    Pokud píšete skutečně obecný kód, který není specifická pro konkrétní domény, výstižný název může pomoci ostatním programátorům principy, které pracují v doméně. Například parametr typu s názvem `'Document` v kontextu interakci s dokumentem databáze zvýší jeho srozumitelnost, že typy obecného dokumentu může přijmout funkce nebo člen pracujete.

* Vezměte v úvahu názvy parametrů obecného typu pomocí PascalCase.

    Toto je hlavní způsob, jak k provádění akcí v .NET, proto se doporučuje použít PascalCase spíše než formátu snake_case nebo camelCase.

A konečně Automatická generalizace není vždy skvělým nástrojem pro uživatele, kteří začínají s F # nebo velký základ kódu. V používání komponent, které jsou obecné, je nemuseli jsme se zdržovat. Kromě toho pokud automaticky obecné funkce nejsou použity s různými typy vstupu (umožňují samostatně, pokud jsou určeny pro použití jako takový), pak neexistuje žádné skutečné výhody je právě obecný od tohoto okamžiku v čase. Vždy zvažte, pokud kód, který píšete se skutečně přínosné obecný.

## <a name="performance"></a>Výkon

F # hodnoty jsou neměnné ve výchozím nastavení, což vám umožní vyhnout určité třídy chyb (zejména těchto zahrnující souběžnosti a paralelismu). Ale v některých případech, tak, abyste dosáhli optimálního (nebo dokonce přiměřené) účinnosti doba provádění nebo přidělení paměti, rozsah práce může nejlépe dají implementovat pomocí místní mutace stavu. To je možné v základu vyjádření souhlasu s jazykem F # s `mutable` – klíčové slovo.

Nicméně použití `mutable` v jazyce F # mohou mít pocit rozporu s funkční čistoty. To je v pořádku, pokud nastavíte očekávání z čistoty [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency). Referenční transparentnost – ne čistoty - je cílem při psaní funkcí F #. To umožňuje psaní funkční rozhraní průběhu na základě mutace implementace výkonu kritického kódu.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zabalení proměnlivé kód v neměnných rozhraní

S referenční transparentnosti jako cíl je velmi důležité napsat kód, který nemůže vystavovat proměnlivé underbelly kritickém pro výkon funkce. Například následující kód implementuje `Array.contains` funkce v základní knihovně F #:

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

Volání této funkce více než jednou podkladové pole nezmění, ani je potřeba, aby vám spravovat jakékoli proměnlivý stav v její použití. Referentially transparentní, je i v případě, téměř každý jednotlivý řádek kódu v rámci něj používá mutace.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Vezměte v úvahu zapouzdření proměnlivé datové ve třídách

Předchozí příklad použil jedné funkce k zapouzdření pomocí proměnlivé datové operace. To není vždy dostatečná pro složitější datových sad. Vezměte v úvahu následující sady funkcí:

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

Tento kód je výkonné, ale zveřejňuje na základě mutace datová struktura, že volající zodpovídají za údržbu. To může být zabaleny uvnitř třídy bez základní členů, které můžete změnit:

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

`Closure1Table` zapouzdřuje základní na základě mutace datové struktury, a tím nevynucuje volající k údržbě základní datová struktura. Třídy jsou efektivní způsob, jak zapouzdřit dat a postupy, které jsou založeny na mutace bez vystavení podrobnosti o volajícím.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferovat `let mutable` na odkazové buňky

Odkazové buňky jsou způsob, jak reprezentaci odkaz na hodnotu než samotná hodnota. I když mohou být použity pro kód kritickém pro výkon, se obecně nedoporučuje. Vezměte v úvahu v následujícím příkladu:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Použít odkazovou buňku nyní "zahltí" všechny následné kódu pomocí museli přistoupit přes ukazatel a znovu odkazují na podkladová data. Místo toho zvažte `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Kromě jediný bod mutace uprostřed výraz lambda, všechny ostatní kód, který se dotýká `acc` můžete udělat tak, aby se nijak neliší použití normální `let`-hranice neměnné hodnotu. To bude usnadňují v průběhu času měnit.

## <a name="object-programming"></a>Objekt programování

F # obsahuje plnou podporu pro objekty a objektově orientované koncepty (zálohy). I když mnohé koncepty zálohy jsou výkonné a užitečné, některé z nich jsou ideální pro použití. Následující seznamy nabízí pokyny k kategorie funkcí zálohy na vysoké úrovni.

**Zvažte použití těchto funkcí v mnoha situacích:**

* Zápisu s tečkou (`x.Length`)
* Členy instance
* Implicitní konstruktory
* Statické členy
* Notace indexeru (`arr.[x]`)
* Pojmenované a nepovinné argumenty
* Rozhraní a implementace rozhraní

**Nedostanou pro účely těchto funkcí nejprve, ale uvážlivě je použije, pokud jsou vhodné k vyřešení problému:**

* Přetěžování metody
* Zapouzdřené proměnlivé datové
* Operátory pro typy
* Automatické vlastnosti
* Implementace `IDisposable` a `IEnumerable`
* Rozšíření typů
* Události
* Struktury
* Delegáty
* Výčty

**Pokud je nutné použít obecně nepoužívejte tyto funkce:**

* Hierarchie dědičnosti na základě typu a implementaci dědičnosti
* Hodnoty Null a `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferovat složení prostřednictvím dědičnosti

[Složení prostřednictvím dědičnosti](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhotrvající idiom, která může splňovat dobré kódu jazyka F #. Základním principem je, že by neměla vystavit základní třídu a vynutit volající dědit ze základní třídy pro funkce.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Můžete implementovat rozhraní, pokud už nepotřebujete třídu objektové výrazy

[Výrazy objektu](../language-reference/object-expressions.md) vám umožňují v reálném čase, implementovat rozhraní implementované rozhraní vazby na hodnotu bez nutnosti učinit uvnitř třídy. To se může hodit, zejména v případě můžete _pouze_ musí implementovat rozhraní a nepotřebujete úplné třídy.

Například tady je kód, který běží v [Ionide](http://ionide.io/) poskytnout akce opravy kódu, pokud jste přidali symbol, který není nutné `open` příkaz pro:

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

Protože není nutné pro třídu při práci s kódem API sady Visual Studio, objektové výrazy jsou ideální nástroj pro tento. Jsou také užitečná pro testování částí, pokud chcete zástupných procedur na rozhraní s testovací rutiny ad hoc způsobem.

## <a name="type-abbreviations"></a>Zkratky typů

[Typ – zkratky](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit popisek k jinému typu, jako je například podpis funkce nebo více komplexního typu. Například následující alias přiřadí popisek co je potřeba definovat výpočet s [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), obsáhlý learning knihovny:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Jmenuje pohodlný způsob, jak označit všechny funkce, která odpovídá podpisu je aliasing. Použití zkratky typů tímto způsobem je vhodné a umožňuje stručnější kódu.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Vyhněte se použití zkratky typů k vyjádření vaší domény

I když zkratky typů jsou vhodné pro poskytnutí názvu podpisech funkcí, mohou být matoucí při zkrácený zápis parametru jiné typy. Vezměte v úvahu tato zkratka:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

To může být matoucí několika různými způsoby:

* `BufferSize` není abstrakci; je právě jiný název pro celé číslo.
* Pokud `BufferSize` je přístupný ve veřejném rozhraní API, se můžete snadno dojít k nesprávné interpretaci znamená více než jen `int`. Obecně platí, typy domén mít víc atributů k nim a nejsou primitivními typy jako `int`. Tato zkratka je v rozporu tento předpoklad.
* Použití malých a velkých `BufferSize` (PascalCase) znamená, že tento typ obsahuje další data.
* Tento alias se nebude poskytovat lepší čitelnosti ve srovnání s poskytováním pojmenovaný argument pro funkci.
* Zkratka neprojeví v kompilovaných IL; je pouze celé číslo a tento alias je konstrukce za kompilace.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Stručně řečeno, trávení s zkratky typů je, že jsou **není** abstrakce typy jsou zkrácený zápis parametru. V předchozím příkladu `BufferSize` je právě `int` skrytě se žádná další data ani žádné výhody z typu systému kromě co `int` už má.
