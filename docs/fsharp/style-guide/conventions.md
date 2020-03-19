---
title: Zásady kódování jazyka F#
description: Při psaní kódu F# se naučte s obecnými pokyny a idiomy.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400307"
---
# <a name="f-coding-conventions"></a>Zásady kódování jazyka F#

Následující konvence jsou formulovány ze zkušeností s prací s velkými základy kódu F#. [Pět zásad dobrého kódu F#](index.md#five-principles-of-good-f-code) jsou základem každého doporučení. Souvisejí s pokyny pro [návrh komponent y F#](component-design-guidelines.md), ale jsou použitelné pro jakýkoli kód F#, nikoli pouze součásti, jako jsou knihovny.

## <a name="organizing-code"></a>Uspořádání kódu

F# obsahuje dva primární způsoby uspořádání kódu: moduly a obory názvů. Jedná se o podobné, ale mají následující rozdíly:

* Obory názvů jsou kompilovány jako obory názvů .NET. Moduly jsou kompilovány jako statické třídy.
* Obory názvů jsou vždy nejvyšší úrovně. Moduly mohou být nejvyšší úrovně a vnořené v rámci jiných modulů.
* Obory názvů mohou přesahovat více souborů. Moduly nemohou.
* Moduly mohou být `[<RequireQualifiedAccess>]` `[<AutoOpen>]`zdobeny a .

Následující pokyny vám pomohou použít tyto k uspořádání kódu.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferovat obory názvů na nejvyšší úrovni

Pro všechny veřejně spotřební kód, obory názvů jsou přednostní moduly na nejvyšší úrovni. Vzhledem k tomu, že jsou kompilovány jako obory názvů .NET, jsou spotřební z jazyka C# bez problémů.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Použití modulu nejvyšší úrovně nemusí vypadat jinak při volání pouze z F#, ale pro spotřebitele `MyClass` Jazyka `MyCode` C#mohou být volající překvapeni tím, že budou muset kvalifikovat modul.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Pečlivě aplikujte`[<AutoOpen>]`

Konstrukce `[<AutoOpen>]` může znečišťovat rozsah toho, co je k dispozici volajícím, a odpověď na to, odkud něco pochází, je "magie". To není dobrá věc. Výjimkou z tohoto pravidla je F# Core knihovna sama o sobě (i když tato skutečnost je také trochu kontroverzní).

Je to však pohodlí, pokud máte pomocné funkce pro veřejné rozhraní API, které chcete uspořádat odděleně od tohoto veřejného rozhraní API.

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

To umožňuje čistě oddělit podrobnosti implementace z veřejného rozhraní API funkce bez nutnosti plně kvalifikovat pomocníka pokaždé, když ji zavoláte.

Navíc vystavení metody rozšíření a tvůrce výrazů na úrovni oboru názvů lze `[<AutoOpen>]`úhledně vyjádřit pomocí .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Používejte `[<RequireQualifiedAccess>]` vždy, když by se jména mohla vystihovit nebo máte pocit, že to pomáhá s čitelností

Přidání `[<RequireQualifiedAccess>]` atributu do modulu znamená, že modul nemusí být otevřen a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup. Například `Microsoft.FSharp.Collections.List` modul má tento atribut.

To je užitečné, pokud funkce a hodnoty v modulu mají názvy, které mohou být v konfliktu s názvy v jiných modulech. Vyžadování kvalifikovaného přístupu může výrazně zvýšit dlouhodobou udržovatelnost a evolvability knihovny.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Tologicky seřadit `open` příkazy

V F#, pořadí prohlášení záležitosti, `open` včetně s příkazy. To je na rozdíl od `using` Jazyka `using static` C#, kde účinek a je nezávislý na pořadí těchto příkazů v souboru.

V F# prvky otevřené do oboru může stín ostatní již k dispozici. To znamená, `open` že změna pořadí příkazy může změnit význam kódu. V důsledku toho žádné libovolné řazení `open` všech příkazů (například alfanumericky) se nedoporučuje, jinak generovat různé chování, které můžete očekávat.

Místo toho doporučujeme je seřadit [topologicky](https://en.wikipedia.org/wiki/Topological_sorting); to znamená, `open` aby vaše příkazy v pořadí, ve kterém jsou _definovány vrstvy_ vašeho systému. Může být také zváženo alfanumerické třídění v různých topologických vrstvách.

Zde je zde topologické řazení pro soubor veřejného rozhraní API služby kompilátoru F#:

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

Všimněte si, že zalomení řádku odděluje topologické hladiny, přičemž každá vrstva je poté seřazena alfanumericky. To čistě uspořádá kód bez náhodného stínování hodnoty.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Použití tříd k omezení hodnot, které mají vedlejší účinky

Existuje mnohokrát při inicializaci hodnoty může mít vedlejší účinky, jako je například vytváření instancí kontextu do databáze nebo jiného vzdáleného prostředku. Je lákavé inicializovat takové věci v modulu a použít je v následujících funkcích:

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

To je často špatný nápad z několika důvodů:

Nejprve konfigurace aplikace je posunuta do základu kódu s `dep1` a `dep2`. To je obtížné udržovat ve větších základech kódu.

Za druhé staticky inicializovaná data by neměla obsahovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud vaše komponenta sama použije více vláken. To je jasně `dep3`porušena .

Nakonec se inicializace modulu zkompiluje do statického konstruktoru pro celou jednotku kompilace. Pokud dojde k chybě v let-bound hodnota inicializace `TypeInitializationException` v tomto modulu, manifestuje jako, který je pak uložen do mezipaměti po celou dobu životnosti aplikace. To může být obtížné diagnostikovat. Tam je obvykle vnitřní výjimka, že se můžete pokusit důvod, ale pokud není, pak není říct, co je hlavní příčinou.

Místo toho stačí použít jednoduchou třídu pro uložení závislostí:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

To umožňuje následující:

1. Odesílání všech závislých stav mimo samotné rozhraní API.
2. Konfiguraci lze nyní provést mimo rozhraní API.
3. Chyby v inicializaci pro závislé `TypeInitializationException`hodnoty se pravděpodobně neprojeví jako .
4. Rozhraní API je nyní jednodušší testovat.

## <a name="error-management"></a>Správa chyb

Správa chyb ve velkých systémech je složité a nuancí úsilí, a neexistují žádné stříbrné kulky v zajištění vašich systémů jsou poruchy-tolerantní a chovat se dobře. Následující pokyny by měly nabídnout pokyny při navigaci v tomto obtížném prostoru.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Představují chybové případy a neplatný stav v typech, které jsou vlastní vaší doméně

S [discriminated sjednocení](../language-reference/discriminated-unions.md), F# umožňuje reprezentovat vadný stav programu v systému typu. Například:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

V tomto případě existují tři známé způsoby, jak výběr peněz z bankovního účtu může selhat. Každý případ chyby je reprezentován v typu, a proto může být bezpečně řešena v celém programu.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Obecně platí, že pokud můžete modelovat různé způsoby, které něco může **selhat** ve vaší doméně, pak zpracování chyb kód již není považován za něco, co je třeba řešit kromě pravidelného toku programu. Je to prostě součást normálního toku programu, a není považován za **výjimečný**. Existují dvě hlavní výhody k tomuto:

1. Je snadnější udržovat, jak se vaše doména mění v průběhu času.
2. Chybové případy jsou snadněji testování částí.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Výjimky používejte v případě, že chyby nelze reprezentovat typy

V problémové doméně nelze reprezentovat všechny chyby. Tyto druhy chyb jsou *výjimečné* povahy, proto schopnost vyvolat a zachytit výjimky v F#.

Nejprve doporučujeme přečíst si [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md). Ty platí také pro F#.

Hlavní konstrukce, které jsou k dispozici v F# pro účely vyvolání výjimek, by měly být zváženy v následujícím pořadí podle preference:

| Funkce | Syntaxe | Účel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Vyvolá `System.ArgumentNullException` s zadaným názvem argumentu. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Vyvolá `System.ArgumentException` s zadaným názvem argumentu a zprávou. |
| `invalidOp` | `invalidOp "message"` | Vyvolá `System.InvalidOperationException` se zadanou zprávou. |
|`raise`| `raise (ExceptionType("message"))` | Univerzální mechanismus pro vyvolání výjimek. |
| `failwith` | `failwith "message"` | Vyvolá `System.Exception` se zadanou zprávou. |
| `failwithf` | `failwithf "format string" argForFormatString` | Vyvolá `System.Exception` se zprávou určenou formátovacím řetězcem a jeho vstupy. |

Použití `nullArg` `invalidArg` , `invalidOp` a jako `ArgumentNullException`mechanismus hodit , `ArgumentException` a `InvalidOperationException` v případě potřeby.

Funkce `failwith` `failwithf` a je obecně třeba se vyhnout, protože zvyšují základní `Exception` typ, nikoli konkrétní výjimku. Podle [pokynů pro návrh výjimek](../../standard/design-guidelines/exceptions.md)chcete vyvolat konkrétnější výjimky, pokud je to možné.

### <a name="using-exception-handling-syntax"></a>Použití syntaxe zpracování výjimek

F# podporuje vzory výjimek prostřednictvím `try...with` syntaxe:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Sladění funkce provádět tváří v tvář výjimku s porovnávání vzorů může být trochu složité, pokud chcete zachovat kód čistý. Jedním z takových způsobů, jak to zpracovat, je použití [aktivních vzorů](../language-reference/active-patterns.md) jako prostředku k seskupení funkcí obklopujících chybový případ s výjimkou samotné. Například může být náročné rozhraní API, které při vyvolání výjimky, uzavře cenné informace v metadatech výjimky. Rozbalení užitečné hodnoty v těle zachycené výjimky uvnitř aktivní vzorek a vrácení této hodnoty může být užitečné v některých situacích.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nepoužívejte monacké zpracování chyb k nahrazení výjimek

Výjimky jsou považovány za poněkud tabu ve funkčním programování. Ve skutečnosti výjimky porušují čistotu, takže je bezpečné považovat je za ne zcela funkční. To však ignoruje realitu, kde musí být spuštěn kód a že může dojít k chybám za běhu. Obecně platí, že psát kód za předpokladu, že většina věcí nejsou ani čisté ani celkové, aby se minimalizovalo nepříjemné překvapení.

Je důležité vzít v úvahu následující hlavní silné a spekty výjimek s ohledem na jejich relevanci a vhodnost v běhu .NET a mezijazykovém ekosystému jako celku:

1. Obsahují podrobné diagnostické informace, což je velmi užitečné při ladění problému.
2. Jsou dobře pochopeny runtime a dalšími jazyky .NET.
3. Mohou snížit významné často používaný text ve srovnání s kódem, který jde z cesty, aby *se zabránilo* výjimkám implementací některé podmnožiny jejich sémantiky na základě ad-hoc.

Tento třetí bod je kritický. U netriviálních složitých operací může selhání použití výjimek vést k řešení struktur, jako je tento:

```fsharp
Result<Result<MyType, string>, string list>
```

Což může snadno vést k křehké kód, jako je porovnávání vzorů na "stringly-typed" chyby:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Navíc může být lákavé spolknout jakoukoli výjimku v touze po "jednoduché" funkci, která vrací "hezčí" typ:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Bohužel `tryReadAllText` může vyvolat četné výjimky založené na nesčetných věcech, které se mohou stát v systému souborů, a tento kód zahodí všechny informace o tom, co by mohlo být ve vašem prostředí skutečně špatně. Pokud nahradíte tento kód typem výsledku, vrátíte se k analýzě chybové zprávy "stringly-typed":

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

A umístění samotného objektu výjimky do konstruktoru `Error` vás pouze vynutí, abyste správně řešili typ výjimky v místě volání, nikoli ve funkci. Tím efektivně vytvoří zaškrtnuté výjimky, které jsou notoricky nezábavné řešit jako volající rozhraní API.

Dobrou alternativou k výše uvedeným příkladům je zachytit *konkrétní* výjimky a vrátit smysluplnou hodnotu v kontextu této výjimky. Pokud změníte `tryReadAllText` funkci takto, `None` má větší význam:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Místo toho, aby fungovala jako catch-all, bude tato funkce nyní správně zpracovávat případ, kdy nebyl soubor nalezen, a přiřadí tento význam k návratu. Tato vrácená hodnota může mapovat na tento případ chyby, aniž by zahodila žádné kontextové informace nebo nenutila volající, aby se zabývali případem, který nemusí být v daném okamžiku v kódu relevantní.

Typy, `Result<'Success, 'Error>` jako jsou vhodné pro základní operace, kde nejsou vnořené a F# volitelné typy jsou ideální pro reprezentaci, když něco může vrátit *něco* nebo *nic*. Nejsou náhradou za výjimky, i když a neměly by být použity ve snaze nahradit výjimky. Spíše by měly být uplatňovány uvážlivě řešit konkrétní aspekty politiky výjimky a chyb řízení cílenými způsoby.

## <a name="partial-application-and-point-free-programming"></a>Částečné programování aplikací a bodů bez bodu

F# podporuje částečné aplikace, a proto různé způsoby, jak programovat ve stylu bez bodu. To může být prospěšné pro opětovné použití kódu v rámci modulu nebo implementace něco, ale není něco vystavit veřejně. Obecně platí, že point-free programování není ctnost sama o sobě, a může přidat významnou kognitivní bariéru pro lidi, kteří nejsou ponořeni do stylu.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nepoužívejte částečnou aplikaci a currying ve veřejných API

S malou výjimkou použití částečné aplikace ve veřejných api může být matoucí pro spotřebitele. Hodnoty `let`-bound v kódu F# jsou obvykle **hodnoty**, nikoli **hodnoty funkcí**. Smíchání min. hodnot a hodnot funkcí může vést k uložení malého počtu řádků kódu výměnou za `>>` poměrně dost kognitivní režie, zejména v kombinaci s operátory, jako je například skládání funkcí.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Zvažte důsledky nástrojů pro programování bez bodů

Curried funkce neoznačují jejich argumenty. To má dopad y nástrojů. Zvažte následující dvě funkce:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Obě jsou platné `funcWithApplication` funkce, ale je curried funkce. Když najevíte nad jejich typy v editoru, zobrazí se toto:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Na webu volání popisky v nástrojích, jako je například Visual `string` Studio `int` nebude vám smysluplné informace o tom, co a vstupní typy skutečně představují.

Pokud narazíte na kód `funcWithApplication` bez bodu, jako je to veřejně spotřební, je doporučeno provést úplné η-expansion tak, aby nástroje mohou vyzvednout na smysluplné názvy pro argumenty.

Kromě toho ladění kódu bez bodů může být náročné, ne-li nemožné. Ladicí nástroje spoléhají na hodnoty vázané na `let` názvy (například vazby), takže můžete zkontrolovat mezilehlé hodnoty uprostřed provádění. Pokud váš kód nemá žádné hodnoty ke kontrole, není nic ladit. V budoucnu se mohou vyvíjet ladicí nástroje, které syntetizují tyto hodnoty na základě dříve provedených cest, ale není vhodné zajistit vaše sázky na *potenciální* funkci ladění.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Zvažte částečnou aplikaci jako techniku ke snížení vnitřního standardního

Na rozdíl od předchozího bodu je částečná aplikace skvělým nástrojem pro snížení standardního nastavení uvnitř aplikace nebo hlubších vnitřních částí rozhraní API. To může být užitečné pro testování částí implementace složitějších API, kde často je bolest řešit. Například následující kód ukazuje, jak můžete dosáhnout toho, co většina zoslňující architektury vám bez přijetí externí závislost na takové rozhraní a museli naučit související rozhraní API na míru.

Zvažte například následující topografii řešení:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`může vystavit kód, jako jsou:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testování `Transactions.doTransaction` částí `ImplementationLogic.Tests.fsproj` je snadné:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Částečné `doTransaction` použití s objektem kontextu zesměšňuje umožňuje volat funkci ve všech testech částí bez nutnosti vytvářet zesměšňovaný kontext pokaždé:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Tato technika by neměla být univerzálně použita na celý základ kódu, ale je to dobrý způsob, jak snížit standardní text pro složité vnitřní a testování částí těchto vnitřních.

## <a name="access-control"></a>Řízení přístupu

F# má více možností pro [řízení přístupu](../language-reference/access-control.md), zděděné z toho, co je k dispozici v běhu .NET. Ty nejsou použitelné jen pro typy - můžete je použít i pro funkce.

* Upřednostňujte netypy`public` a členy, dokud je nebudete potřebovat k veřejnému spotřebnímu materiálu. To také minimalizuje to, co spotřebitelé pár.
* Snažte se zachovat všechny `private`pomocné funkce .
* Zvažte použití `[<AutoOpen>]` na soukromém modulu pomocných funkcí, pokud se stanou četnými.

## <a name="type-inference-and-generics"></a>Odvození typu a obecné typy

Odvození typu vám může ušetřit psaní velkého množství často používaných textových destiček. A automatické generalizace v kompilátoru F# vám může pomoci napsat obecnější kód s téměř žádné další úsilí z vaší strany. Tyto funkce však nejsou univerzálně dobré.

* Zvažte označení názvy argumentů s explicitní typy ve veřejných api a nespoléhejte na odvození typu pro toto.

    Důvodem je, že **byste** měli mít kontrolu nad tvarem rozhraní API, nikoli kompilátoru. Přestože kompilátor může provést dobrou práci při odvození typů pro vás, je možné mít tvar rozhraní API změnit, pokud vnitřní části, na kterých spoléhá, změnily typy. To může být to, co chcete, ale to bude téměř jistě mít za následek porušení změny rozhraní API, že příjem spotřebitelů pak bude muset vypořádat s. Místo toho pokud explicitně řídíte tvar veřejného rozhraní API, můžete tyto narušující změny řídit. Z hlediska DDD si to lze myslet jako antikorupční vrstvu.

* Zvažte poskytnutí smysluplného názvu obecným argumentům.

    Pokud nepíšete skutečně obecný kód, který není specifický pro určitou doménu, může smysluplný název pomoci ostatním programátorům pochopit doménu, ve které pracují. Například parametr typu `'Document` pojmenovaný v kontextu interakce s databází dokumentů umožňuje jasnější, že obecné typy dokumentů mohou být přijaty funkcí nebo členem, se kterým pracujete.

* Zvažte pojmenování parametrů obecného typu pomocí PascalCase.

    Toto je obecný způsob, jak dělat věci v rozhraní .NET, takže je doporučeno používat PascalCase spíše než snake_case nebo camelCase.

Nakonec automatické generalizace není vždy přínosem pro lidi, kteří jsou nové F# nebo velký základ kódu. Existuje kognitivní režie v použití komponent, které jsou obecné. Kromě toho pokud automaticky generalizované funkce nejsou používány s různými typy vstupů (natož pokud jsou určeny k použití jako takové), pak neexistuje žádný skutečný přínos pro ně jsou obecné v tomto okamžiku. Vždy zvažte, zda kód, který píšete bude skutečně těžit z obecné.

## <a name="performance"></a>Výkon

### <a name="prefer-structs-for-small-data-types"></a>Preferujte struktury pro malé datové typy

Použití struktury (také volal Typy hodnot) může často vést k vyšší výkon pro některé kód, protože obvykle zabraňuje přidělování objektů. Struktury však nejsou vždy tlačítko "jít rychleji": pokud velikost dat ve struktuře překročí 16 bajtů, kopírování dat může často vést k více času procesoru než použití typu odkazu.

Chcete-li zjistit, zda byste měli použít strukturu, zvažte následující podmínky:

- Pokud je velikost dat 16 bajtů nebo menší.
- Pokud je pravděpodobné, že mnoho z těchto datových typů rezidentní v paměti v běžícím programu.

Pokud platí první podmínka, měli byste obecně použít strukturu. Pokud se obě platí, měli byste téměř vždy použít strukturu. Mohou existovat některé případy, kdy platí předchozí podmínky, ale použití struktury není lepší nebo horší než použití referenčního typu, ale je pravděpodobné, že budou vzácné. Je důležité vždy měřit při provádění změn, jako je tento, i když, a ne pracovat na předpokladu nebo intuice.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Preferovat strukturní řazené kolekce členů při seskupování malých typů hodnot

Zvažte následující dvě funkce:

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako je `runWithStructTuple` [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že funkce, která používá strukturní řazené řazené kolekce členů, běží o 40% rychleji a nepřiděluje žádnou paměť.

Tyto výsledky však nebude vždy případ ve vašem vlastním kódu. Pokud označíte `inline`funkci jako , kód, který používá referenční řazené kolekce členů, může získat některé další optimalizace nebo kód, který by přidělit by jednoduše optimalizovat pryč. Výsledky byste měli vždy měřit vždy, když se jedná o výkon, a nikdy nepracovat na základě předpokladu nebo intuice.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Preferovat záznamy struktury, pokud je datový typ malý

Pravidlo popsané výše platí také pro [typy záznamů F#](../language-reference/records.md). Zvažte následující datové typy a funkce, které je zpracovávají:

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

To je podobné předchozí n-tice kód, ale tentokrát v příkladu používá záznamy a vložené vnitřní funkce.

Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako `processStructPoint` je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že běží téměř o 60% rychleji a nepřiděluje nic na spravované haldě.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Preferovat strukturní discriminated sjednocení, pokud je datový typ malý

Předchozí pozorování o výkonu s nit řazené kolekce členů a záznamy platí také pro [F# discriminated sjednocení](../language-reference/discriminated-unions.md). Uvažujte následující kód:

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

Je běžné definovat jednopřípadové discriminated sjednocení, jako je tento pro modelování domény. Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako `structReverseName` je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že běží asi o 25% rychleji než `reverseName` u malých řetězců. U velkých řetězců oba provádět přibližně stejné. Takže v tomto případě je vždy vhodnější použít strukturu. Jak již bylo zmíněno, vždy měřit a nepracují na předpokladech nebo intuici.

Přestože předchozí příklad ukázal, že struktura discriminated Unie přinesla lepší výkon, je běžné mít větší discriminated sjednocení při modelování domény. Větší datové typy, jako že nemusí provádět stejně, pokud jsou struktury v závislosti na operacích na nich, protože další kopírování může být zapojen.

### <a name="functional-programming-and-mutation"></a>Funkční programování a mutace

Hodnoty Jazyka F# jsou ve výchozím nastavení neměnné, což umožňuje vyhnout se určitým třídám chyb (zejména těch, které zahrnují souběžnost a paralelismus). V některých případech však za účelem dosažení optimální (nebo dokonce přiměřené) účinnosti doby provádění nebo přidělení paměti může být nejlepší využití rozsahu práce pomocí mutace stavu na místě. To je možné v opt-in základě `mutable` s F# s klíčovým slovem.

Použití `mutable` v F# může cítit v rozporu s funkční čistoty. To je pochopitelné, ale funkční čistota všude může být v rozporu s výkonnostními cíli. Kompromis emituje mutace tak, že volající nemusí starat o to, co se stane, když volají funkci. To umožňuje psát funkční rozhraní přes implementaci založenou na mutaci pro kód kritický pro výkon.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zalamování proměnlivého kódu v neměnných rozhraních

S referenční transparentnost jako cíl, je důležité napsat kód, který nezveřejňuje proměnlivé podbřišek funkce kritické pro výkon. Například následující kód implementuje `Array.contains` funkci v základní knihovně F#:

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

Volání této funkce vícekrát nezmění základní pole, ani nevyžaduje udržovat proměnlivý stav při jeho využívání. Je to referenční transparentní, i když téměř každý řádek kódu v něm používá mutaci.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Zvažte zapouzdření proměnlivých dat do tříd

Předchozí příklad používá jednu funkci zapouzdřit operace pomocí proměnlivá data. To není vždy dostačující pro složitější sady dat. Zvažte následující sady funkcí:

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

Tento kód je performant, ale zveřejňuje strukturu dat na základě mutace, že volající jsou zodpovědní za údržbu. To může být zabaleno uvnitř třídy bez podkladových členů, které se mohou změnit:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`zapouzdřuje základní strukturu dat založenou na mutacích, čímž volající nenutí udržovat základní datovou strukturu. Třídy jsou účinný způsob, jak zapouzdřit data a rutiny, které jsou založeny na mutaci bez vystavení podrobnosti volajícím.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Preferujte `let mutable` referenční buňky

Referenční buňky představují odkaz na hodnotu, nikoli na samotnou hodnotu. Přestože je lze použít pro kód kritický pro výkon, nejsou doporučeny. Uvažujte následující příklad:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Použití referenční buňky nyní "znečišťuje" všechny následné kódy s nutností odkazovat a znovu odkazovat na podkladová data. Místo toho `let mutable`zvažte:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Kromě jediného bodu mutace uprostřed výrazu lambda, všechny `acc` ostatní kód, který se dotýká může tak učinit `let`způsobem, který se neliší od použití normální vázané neměnné hodnoty. To usnadní změnu v průběhu času.

## <a name="object-programming"></a>Programování objektů

F# má plnou podporu pro objekty a objektově orientované (OO) koncepty. Ačkoli mnoho Konceptů OO je výkonných a užitečných, ne všechny jsou ideální pro použití. Následující seznamy obsahují pokyny pro kategorie funkcí OO na vysoké úrovni.

**Zvažte použití těchto funkcí v mnoha situacích:**

* Dot notace (`x.Length`)
* Členové instance
* Implicitní konstruktory
* Statické členy
* Zápis indexeru`arr.[x]`( )
* Pojmenované a volitelné argumenty
* Rozhraní a implementace rozhraní

**Nesahujte po těchto funkcích jako první, ale uvážlivě je aplikujte, když jsou vhodné k vyřešení problému:**

* Přetížení metody
* Zapouzdřená proměnlivá data
* Operátory na typech
* Automatické vlastnosti
* Provádění `IDisposable` a provádění`IEnumerable`
* Rozšíření typu
* Akce
* Struktury
* Delegáty
* Výčty

**Obecně se těmto funkcím vyhněte, pokud je nepotřebujete použít:**

* Hierarchie typu založené na dědičnosti a dědičnost implementace
* Nulla a`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Upřednostnit složení před dědičností

[Složení nad dědičnost](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhotrvající idiom, že dobrý kód F#může dodržovat. Základním principem je, že byste neměli vystavit základní třídy a vynutit volající dědit z této základní třídy získat funkce.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Použití výrazů objektu k implementaci rozhraní, pokud nepotřebujete třídu

[Objektové výrazy](../language-reference/object-expressions.md) umožňují implementovat rozhraní za běhu, vazby implementované rozhraní na hodnotu bez nutnosti tak učinit uvnitř třídy. To je výhodné, zejména pokud potřebujete _pouze_ implementovat rozhraní a nemáte potřebu celé třídy.

Například zde je kód, který je spuštěn v [Ionide](http://ionide.io/) poskytnout opravu kódu akce, pokud jste `open` přidali symbol, který nemáte příkaz pro:

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

Vzhledem k tomu, že není potřeba pro třídu při interakci s rozhraním API kódu visual studio, objektové výrazy jsou ideálním nástrojem pro tento. Jsou také cenné pro testování částí, pokud chcete získat výtržek z rozhraní s testovací rutiny způsobem ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Zvažte zkratky typu pro zkrácení podpisů

[Zkratky typu](../language-reference/type-abbreviations.md) jsou pohodlným způsobem přiřazení popisku jinému typu, například podpisu funkce nebo složitějšímu typu. Například následující alias přiřadí popisek k tomu, co je potřeba k definování výpočtu s [CNTK](https://docs.microsoft.com/cognitive-toolkit/), knihovnou hlubokého učení:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Název `Computation` je pohodlný způsob, jak oznamovat všechny funkce, které odpovídají podpisu, který aliasuje. Použití typových zkratek, jako je tento, je pohodlné a umožňuje stručnější kód.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Vyhněte se použití zkratky typu reprezentovat svou doménu

Přestože zkratky typu jsou vhodné pro zadání názvu pro funkce podpisy, mohou být matoucí při zkrácení jiných typů. Vezměme si tuto zkratku:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

To může být matoucí několika způsoby:

* `BufferSize`není abstrakcí; je to jen jiný název pro celé číslo.
* Pokud `BufferSize` je vystavena ve veřejném rozhraní API, může být snadno `int`nesprávně interpretována znamenat více než jen . Obecně platí, že typy domén mají více atributů k nim a nejsou primitivní typy jako `int`. Tato zkratka tento předpoklad porušuje.
* Caseing `BufferSize` (PascalCase) znamená, že tento typ obsahuje více dat.
* Tento alias nenabízí větší srozumitelnost ve srovnání s poskytováním pojmenované argument funkce.
* Zkratka se neprojeví v kompilovaném IL; je pouze celé číslo a tento alias je konstrukce v době kompilace.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Stručně řečeno, úskalí s typem zkratky je, že **nejsou** abstrakce nad typy, které jsou zkrácení. V předchozím příkladu, `int` je jen pod kryty, bez dalších údajů, `int` ani žádné výhody z typového systému kromě toho, `BufferSize` co již má.

Alternativní přístup k použití zkratky typu představují doménu je použití jednomístné diskriminované sjednocení. Předchozí vzorek lze modelovat takto:

```fsharp
type BufferSize = BufferSize of int
```

Pokud píšete kód, který `BufferSize` pracuje z hlediska a jeho základní hodnotu, je třeba vytvořit jeden spíše než předat v libovolné celé číslo:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

To snižuje pravděpodobnost chybně předání libovolné celé číslo `send` do funkce, protože `BufferSize` volající musí vytvořit typ zabalit hodnotu před voláním funkce.
