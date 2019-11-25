---
title: Zásady kódování jazyka F#
description: Seznamte se s obecnými pokyny F# a idiomy při psaní kódu.
ms.date: 11/04/2019
ms.openlocfilehash: 60eff6392d71caa54eeb438f2f6ba9db910f1bc1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978227"
---
# <a name="f-coding-conventions"></a>Zásady kódování jazyka F#

Následující konvence jsou formulované z prostředí práce s velkými F# základy kódu. [Pět principů F# dobrého kódu](index.md#five-principles-of-good-f-code) je základem každého doporučení. Vztahují se k [ F# pokynům pro návrh komponent](component-design-guidelines.md), ale platí pro jakýkoliv F# kód, nikoli jenom na komponenty, jako jsou knihovny.

## <a name="organizing-code"></a>Uspořádání kódu

F#nabízí dva hlavní způsoby uspořádání kódu: moduly a obory názvů. Jsou podobné, ale mají následující rozdíly:

* Obory názvů jsou kompilovány jako obory názvů .NET. Moduly jsou kompilovány jako statické třídy.
* Obory názvů jsou vždycky nejvyšší úrovně. Moduly můžou být na nejvyšší úrovni a vnořené v jiných modulech.
* Obory názvů můžou zahrnovat víc souborů. Moduly se nedají.
* Moduly lze dekorovat pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]`.

Následující pokyny vám pomohou s jejich použitím k uspořádání kódu.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferovat obory názvů na nejvyšší úrovni

Pro veškerý veřejně spotřební kód jsou obory názvů pro moduly na nejvyšší úrovni. Protože jsou kompilovány jako obory názvů .NET, jsou spotřební C# bez problémů.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Použití modulu nejvyšší úrovně se nemusí zobrazovat jinak, když se volá jenom z F#, ale u C# spotřebitelů můžou být volající, protože musí kvalifikovat`MyClass`s modulem`MyCode`.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Pečlivě použít `[<AutoOpen>]`

Konstrukce `[<AutoOpen>]` může znehodnotit rozsah toho, co je k dispozici volajícím, a odpověď na místo, kde je něco z nich "Magic". Většinou to není dobré. Výjimkou z tohoto pravidla je F# základní knihovna samotná (i když je to také bit kontroverzním).

Je to ale pohodlí, pokud máte pomocnou funkci pro veřejné rozhraní API, které chcete uspořádat odděleně od tohoto veřejného rozhraní API.

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

To umožňuje čistě oddělit podrobnosti implementace z veřejného rozhraní API funkce bez nutnosti úplného vyřazení pomocné rutiny pokaždé, když ji zavoláte.

Kromě toho může být vystavení metod rozšíření a tvůrců výrazů na úrovni oboru názvů bez jakýchkoli hodnot vyjádřeno `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Používejte `[<RequireQualifiedAccess>]` vždy, když by mohlo dojít ke konfliktu názvů, nebo pokud se vám podaří s čitelností.

Přidání atributu `[<RequireQualifiedAccess>]` do modulu znamená, že modul nelze otevřít a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup. Například modul `Microsoft.FSharp.Collections.List` má tento atribut.

To je užitečné v případě, že funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v jiných modulech. Vyžadování kvalifikovaného přístupu může značně prodloužit dlouhodobou udržovatelnost a možnost využití knihovny.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Topologické řazení příkazů `open`

V F#nástroji se jedná o pořadí deklarací, včetně příkazů `open`. To je na rozdíl C#od, kde účinek`using`a`using static`je nezávislý na řazení těchto příkazů v souboru.

V F#nástroji můžou prvky otevřené do oboru stínové kopie, které už jsou přítomné, jiné. To znamená, že změna pořadí `open`ch příkazů by mohla změnit význam kódu. V důsledku toho se obecně nedoporučuje žádné libovolné řazení všech příkazů `open` (například alfanumerické), lest vygenerujete různé chování, které byste mohli očekávat.

Místo toho doporučujeme, abyste je seřadili [Topologicky](https://en.wikipedia.org/wiki/Topological_sorting). To znamená, že příkazy `open` v pořadí, ve kterém jsou definovány _vrstvy_ systému. Je také možné zvážit alfanumerické řazení v různých topologických vrstvách.

Tady je příklad topologické řazení pro veřejný soubor rozhraní API F# služby kompilátoru:

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

Všimněte si, že zalomení řádku odděluje topologické vrstvy s každou vrstvou, která je následně tříděna. Tím se čistě organizují kód bez náhodných hodnot stínování.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Použití tříd k zahrnutí hodnot, které mají vedlejší účinky

Při inicializaci hodnoty může mít vedlejší účinky, jako je například vytvoření instance kontextu databáze nebo jiného vzdáleného prostředku, existuje mnoho času. Nachází se na inicializaci takových věcí v modulu a jejich použití v následujících funkcích:

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

Nejprve se konfigurace aplikace vloží do základu kódu pomocí `dep1` a `dep2`. To je obtížné udržovat ve větších základech kódu.

Druhá, staticky inicializovaná data by neměla zahrnovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud vaše komponenta sám použije více vláken. To je jasně narušeno `dep3`.

Nakonec se inicializace modulu zkompiluje do statického konstruktoru pro celou jednotku kompilace. Pokud dojde k nějaké chybě v inicializaci hodnoty s vazbou v tomto modulu, manifestuje se jako `TypeInitializationException`, která je poté ukládána do mezipaměti pro celou dobu životnosti aplikace. To může být obtížné diagnostikovat. Obvykle se jedná o vnitřní výjimku, kterou se můžete pokusit o důvod, ale pokud tam není, neoznamuje to, co je hlavní příčina.

Místo toho stačí použít jednoduchou třídu pro uchování závislostí:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

To umožňuje následující:

1. Vložení libovolného závislého stavu mimo samotné rozhraní API.
2. Konfigurace se teď dá udělat mimo rozhraní API.
3. Chyby při inicializaci závislých hodnot nejsou nejspíš manifestovat jako `TypeInitializationException`.
4. Rozhraní API je teď snadněji vyzkoušené.

## <a name="error-management"></a>Správa chyb

Správa chyb ve velkých systémech je složitá a odlišitá Endeavor a neexistují žádné stříbrné odrážky v tom, že vaše systémy jsou odolné proti chybám a chovají se dobře. Následující pokyny by měly nabízet pokyny k tomu, aby se tento obtížný prostor přecházeníly.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Reprezentuje chybové případy a neplatný stav ve vnitřních typech pro vaši doménu.

Díky [rozlišeným sjednocením](../language-reference/discriminated-unions.md) F# poskytuje možnost vyjádřit v systému typů chybný stav programu. Příklad:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

V tomto případě existují tři známé způsoby, jak se odeberou peníze z bankovního účtu, může selhat. Jednotlivé chybové případy jsou reprezentovány v typu a lze je proto v rámci programu bezpečně zařídit.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Obecně platí, že pokud můžete modelovat různé způsoby, které může něco v doméně **selhat** , pak se kód pro zpracování chyb už nepovažuje za něco, co je potřeba řešit Kromě pravidelného toku programu. Je jenom součástí normálního toku programu a nepovažuje se za **výjimečné**. Existují dvě hlavní výhody:

1. Údržba se v průběhu času mění v rámci domény.
2. Chybové případy jsou snazší pro testování částí.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Použít výjimky v případě, že chyby nemohou být reprezentovány s typy

Ne všechny chyby mohou být reprezentovány v doméně problému. Tyto druhy chyb jsou *výjimečné* povahy, takže schopnost vyvolat a zachytit výjimky v F#.

Nejprve doporučujeme, abyste si přečetli [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md). Tyto podmínky platí i pro F#.

Hlavní konstrukce, které jsou k F# dispozici v pro účely vyvolání výjimek, by měly být zváženy v následujícím pořadí:

| Funkce | Syntaxe | Účel |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Vyvolá `System.ArgumentNullException` se zadaným názvem argumentu. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Vyvolá `System.ArgumentException` se zadaným názvem a zprávou argumentu. |
| `invalidOp` | `invalidOp "message"` | Vyvolá `System.InvalidOperationException` se zadanou zprávou. |
|`raise`| `raise (ExceptionType("message"))` | Mechanismus pro obecné účely pro vyvolávání výjimek. |
| `failwith` | `failwith "message"` | Vyvolá `System.Exception` se zadanou zprávou. |
| `failwithf` | `failwithf "format string" argForFormatString` | Vyvolá `System.Exception` se zprávou určenou formátovacím řetězcem a jeho vstupy. |

Použijte `nullArg`, `invalidArg` a `invalidOp` jako mechanismus pro vyvolání `ArgumentNullException`, `ArgumentException` a `InvalidOperationException`, pokud je to vhodné.

Funkce `failwith` a `failwithf` by se měly obecně vyhnout, protože vyvolávají základní `Exception` typ, ne konkrétní výjimku. Podle pokynů pro [Návrh výjimek](../../standard/design-guidelines/exceptions.md)chcete vyvolat konkrétnější výjimky, když můžete.

### <a name="using-exception-handling-syntax"></a>Použití syntaxe pro zpracování výjimek

F#podporuje vzory výjimek pomocí syntaxe`try...with`:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Sladění funkcionality, která se má provést na tváři výjimky s porovnáváním vzorů, může být bit obtížné, pokud chcete zachovat vyčištění kódu. Jedním z těchto způsobů, jak to zpracovat, je použít [aktivní vzory](../language-reference/active-patterns.md) jako způsob seskupení funkcí v případě chyby s jedinou výjimkou. Například můžete využívat rozhraní API, které při vyvolání výjimky vloží cenné informace do metadat výjimky. Rozbalení užitečné hodnoty v těle zachycené výjimky uvnitř aktivního vzoru a vrácení této hodnoty může být v některých situacích užitečné.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Nepoužívejte zpracování chyb monadic k nahrazení výjimek.

Výjimky se zobrazují jako poněkud Taboo v funkčním programování. Výjimky jsou ve skutečnosti porušení čistoty, takže je bezpečné je považovat za nepoměrně funkční. Nicméně to bude ignorovat skutečnost, kde musí být kód spuštěn, a může dojít k chybám za běhu. Obecně platí, že při zapisování kódu na předpokladu, že většina věcí není ani čistá ani celkově, se minimalizuje nepříjemný překvapením.

Je důležité vzít v úvahu následující základní síly/aspekty výjimek s ohledem na jejich relevanci a vhodnost v prostředí .NET runtime a ekosystém mezi jazyky jako celek:

1. Obsahují podrobné diagnostické informace, které jsou velmi užitečné při ladění problému.
2. Jsou dobře pochopitelné modulem runtime a dalšími jazyky .NET.
3. Můžou snížit významný často používaný kód v porovnání s kódem, který se dokončí způsobem, aby *nedocházelo* k výjimkám tím, že implementuje určitou podmnožinu jejich sémantiky na základě ad hoc.

Tento třetí bod je kritický. U netriviální složitých operací může selhání při použití výjimek vést ke strukturám, jako jsou tyto:

```fsharp
Result<Result<MyType, string>, string list>
```

Což může snadno vést k křehkému kódu, jako je porovnávání vzorů při chybách typu "String-Type":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Kromě toho je možné zvážit, že se bude považovat za požití jakékoli výjimky v možnosti "jednoduchá" funkce, která vrací typ "Nicer":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

`tryReadAllText` například může vyvolat mnoho výjimek na základě nesčetných věcí, které se mohou vyskytnout v systému souborů, a tento kód zahodí všechny informace o tom, co se ve vašem prostředí skutečně stane špatným. Pokud nahradíte tento kód výsledným typem, budete zpět k analýze chybové zprávy typu "String-Type":

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

A umístění samotného objektu Exception do konstruktoru `Error` pouze vynutí, abyste správně zapracovali s typem výjimky na webu volání, nikoli ve funkci. Díky tomu efektivně vznikne zaškrtnuté výjimky, které jsou obvykle odlaďuje unfun, které se zabývat jako volající rozhraní API.

Dobrou alternativou k výše uvedeným příkladům je zachycení *specifických* výjimek a vrácení smysluplné hodnoty v kontextu této výjimky. Pokud funkci `tryReadAllText` upravíte následujícím způsobem, `None` má větší význam:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Místo toho, aby tato funkce fungovala jako zachycení, tato funkce nyní správně zpracuje případ, kdy nebyl nalezen soubor a přiřadí tento význam k návratu. Tato návratová hodnota může být namapována na daný chybový případ, přičemž nedojde k zahození jakýchkoli kontextových informací nebo k vynucení volajících, aby se zabývat případem, který v tomto okamžiku v kódu nemusí být relevantní.

Typy, jako je například `Result<'Success, 'Error>`, jsou vhodné pro základní operace, kde nejsou F# vnořené, a volitelné typy jsou ideální pro reprezentaci, kdy může něco vrátit *něco* nebo *nic*. Nejsou náhradou za výjimky, ale a neměly by se používat v pokusu o nahrazení výjimek. Místo toho by se měly použít uvážlivě k vyřešení konkrétních aspektů zásad výjimky a správy chyb, a to cílené způsobem.

## <a name="partial-application-and-point-free-programming"></a>Částečné a bezplatné programování aplikací a koncových bodů

F#podporuje částečnou aplikaci, a proto různé způsoby programování ve stylu bez bodu. To může být užitečné pro opětovné použití kódu v rámci modulu nebo implementace nějakého, ale obecně není něco k veřejně vystavení. Obecně platí, že programování bez koncových bodů není v a samo samé a může přidat významnou bariéru rozpoznávání pro lidi, kteří nejsou ve stylu ponořeni.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Nepoužívejte částečné aplikace a procesu curryfikace ve veřejných rozhraních API.

S malou výjimkou může být použití částečné aplikace ve veřejných rozhraních API pro uživatele matoucí. Hodnoty, které jsou v F# kódu obvykle `let`, jsou obvykle **hodnoty**, nikoli **hodnoty funkcí**. Kombinování hodnot a hodnot funkcí může mít za následek uložení malého počtu řádků kódu v Exchangi pro poměrně bitovou zátěž, zejména v případě kombinace s operátory, jako je `>>` k vytváření funkcí.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Vezměte v úvahu dopady nástrojů pro programování bez jakéhokoli bodu.

Funkce curryfikované nepopisují své argumenty. To má vliv na nástroje. Vezměte v úvahu tyto dvě funkce:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Obě jsou platné funkce, ale `funcWithApplication` je funkce curryfikované. Když najedete myší na své typy v editoru, uvidíte toto:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

V lokalitě volání popisy v nástrojích, jako je například Visual Studio, neposkytnou smysluplné informace o tom, co `string` a `int` vstupní typy skutečně reprezentují.

Pokud narazíte na kód bezplatného bodu, jako je `funcWithApplication`, který je veřejně vhodný, doporučuje se provést úplné rozšíření η, aby nástroj mohl na základě argumentů vybrat smysluplné názvy.

Kromě toho může být kód bez bodu ladění náročný, pokud není možný. Nástroje pro ladění spoléhají na hodnoty vázané na názvy (například `let` vazby), abyste mohli kontrolovat mezilehlé hodnoty pomocí provádění. Pokud váš kód nemá žádné hodnoty ke kontrole, není k dispozici žádný k ladění. V budoucnu se ladicí nástroje můžou vyvíjet k syntetizaci těchto hodnot na základě dříve provedených cest, ale není dobré zakládat své tipy na *možné* funkce ladění.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Zvažte částečnou aplikaci jako metodu pro snížení interního často používaného textu.

Na rozdíl od předchozího bodu je částečná aplikace vynikajícím nástrojem pro omezení často používaného textu v rámci aplikace nebo hlubších vnitřních funkcí rozhraní API. To může být užitečné při testování jednotek implementace složitějších rozhraní API, kde často je často jednodušší se vypořádat s. Například následující kód ukazuje, jak můžete dosáhnout toho, co nejpodobující architektury poskytují, aniž byste museli přebírat externí závislost na takové architektuře a musí se naučit související rozhraní Bespoke API.

Zvažte například následující topografii řešení:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` může vystavovat kód jako:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Testování částí `Transactions.doTransaction` v `ImplementationLogic.Tests.fsproj` je snadné:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Částečně aplikování `doTransaction` s objektem s napodobnou kontextovou funkcí umožňuje zavolat funkci ve všech testech jednotek bez nutnosti sestavit napodobný kontext pokaždé, když:

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

Tato technika by se nedala univerzálně aplikovat na celý základ kódu, ale je dobrým způsobem, jak omezit často používané složité interní prvky a testování jednotek těchto interních.

## <a name="access-control"></a>Řízení přístupu

F#má více možností pro [řízení přístupu](../language-reference/access-control.md)zděděné od toho, co je k dispozici v modulu .NET Runtime. Nedají se použít jen pro typy – můžete je používat i pro funkce.

* Dáváte přednost ne`public`m typům a členům, dokud je nebudete potřebovat k veřejnému spotřebnímu přířazení. Tím se taky minimalizuje to, k čemu se spotřebitelé pojí.
* Snažte se zachovat všechny funkce pomocníka `private`.
* Zvažte použití `[<AutoOpen>]` u privátního modulu pomocných funkcí, pokud se stanou řadou.

## <a name="type-inference-and-generics"></a>Odvození typu a obecné typy

Odvození typu vám může ušetřit od zadání spousty často používaného textu. A Automatická generalizace v F# kompilátoru vám může přispět při psaní obecnější kódu s skoro bez dalšího úsilí na vaši část. Tyto funkce nejsou ale všeobecně dobré.

* Zvažte označení názvů argumentů explicitními typy ve veřejných rozhraních API a nespoléhejte se na odvození typu.

    Důvodem **je, že byste měli** mít kontrolu nad tvarem rozhraní API, nikoli kompilátorem. I když může kompilátor provést podrobnější úlohu při odvozování typů za vás, je možné mít tvar svého rozhraní API změněn, pokud interní funkce, na kterých závisí, mají změněné typy. To může být to, co potřebujete, ale téměř jistě by to mělo za následek přerušující změnu rozhraní API, o kterou budou moct vzdálení uživatelé řešit. Místo toho, pokud explicitně ovládáte tvar veřejného rozhraní API, můžete tyto zásadní změny řídit. V DDD výrazy to lze představit jako vrstvu odolnou proti poškození.

* Zvažte poskytnutí smysluplného názvu obecným argumentům.

    Pokud nezapisujete skutečně obecný kód, který není specifický pro konkrétní doménu, smysluplný název může pomáhat ostatním programátorům pochopit doménu, ve které pracují. Například parametr typu s názvem `'Document` v kontextu interakce s databází dokumentu umožňuje vymazat, že obecné typy dokumentů mohou být přijaty funkcí nebo členem, se kterými pracujete.

* Zvažte pojmenování obecných parametrů typu pomocí PascalCase.

    Toto je obecný způsob, jak provádět akce v .NET, takže se místo snake_case nebo camelCase doporučuje používat PascalCase.

Kromě toho automatické generalizace není vždy Boon pro uživatele, kteří jsou novými F# nebo velký základ kódu. Při používání komponent, které jsou obecné, se vyvnímání zátěže. Kromě toho, pokud jsou automaticky zobecněné funkce použity s různými vstupními typy (ať už jsou určeny pro použití jako takové), neexistují žádné výhody, které jsou v daném časovém okamžiku v tomto okamžiku obecně k dispozici. Vždy zvažte, jestli kód, který píšete, bude mít ve skutečnosti obecný přínos.

## <a name="performance"></a>Výkon

F#hodnoty jsou ve výchozím nastavení neměnné, což umožňuje vyhnout se určitým třídám chyb (zejména ty, které se týkají souběžnosti a paralelismu). Nicméně v některých případech, aby bylo dosaženo optimální (nebo ještě rozumně) efektivity času spuštění nebo přidělení paměti, je možné, že je možné využít rozsah práce pomocí místní mutace stavu. To je možné na základě výslovného souhlasu s F# klíčovým slovem`mutable`.

Použití `mutable` v F# se však může cítit na lichá s funkcí čistoty. To je v pořádku, pokud upravíte očekávání z čistoty na [referenční transparentnost](https://en.wikipedia.org/wiki/Referential_transparency). Referenční transparentnost – nečistota – je koncovým cílem při F# psaní funkcí. To vám umožní napsat funkční rozhraní přes implementaci na základě mutací pro kód kritický pro výkon.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Zalamování měnitelného kódu v neměnných rozhraních

V případě referenční transparentnosti jako cíle je velmi důležité napsat kód, který nezveřejňuje proměnlivou podšpičku funkcí kritických pro výkon. Například následující kód implementuje funkci `Array.contains` v F# základní knihovně:

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

Vícenásobné volání této funkce nemění podkladové pole, ani nevyžaduje, abyste zachovali proměnlivý stav, který je v tom, že ho budete spotřebovávat. Je tak transparentní, i když skoro každý řádek kódu v něm používá mutace.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Zvažte zapouzdření proměnlivých dat ve třídách

Předchozí příklad používal jednu funkci k zapouzdření operací pomocí proměnlivých dat. To není vždy dostačující pro složitější sady dat. Vezměte v úvahu následující sady funkcí:

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

Tento kód je proveden, ale zveřejňuje datovou strukturu založenou na mutacích, kterou volající zodpovídá za údržbu. To lze zabalit do třídy bez základních členů, které mohou změnit:

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

`Closure1Table` zapouzdřuje základní datovou strukturu založenou na mutacích, a proto nenutí volajícím udržovat podkladovou strukturu dat. Třídy představují účinný způsob, jak zapouzdřit data a rutiny, které jsou založené na mutacích bez odhalení podrobností volajícím.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferovat `let mutable` k odkazování na buňky

Odkazové buňky představují způsob, jak znázornit odkaz na hodnotu namísto samotné hodnoty. I když je lze použít pro kód kritický pro výkon, obecně se nedoporučuje. Vezměte v úvahu následující příklad:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Použití referenční buňky teď "znečišťující" všechny následné kódy, které se musí přesměrovat a znovu odkazovat na podkladová data. Místo toho zvažte `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Kromě jediného bodu mutace uprostřed výrazu lambda může veškerý další kód, který se dotýká `acc`, tak způsobem, který se neliší od použití normálního neměnného typu `let`vázaného na sebe. To usnadňuje změnu v průběhu času.

## <a name="object-programming"></a>Programování objektů

F#má plnou podporu pro objekty a koncepty orientované na objekt (ó). I když je mnoho konceptů ú náročných a užitečných, ne všechny z nich jsou ideální pro použití. V následujících seznamech jsou uvedeny doprovodné materiály k kategoriím funkcí ó na vysoké úrovni.

**Zvažte použití těchto funkcí v mnoha situacích:**

* Tečkový zápis (`x.Length`)
* Členy instance
* Implicitní konstruktory
* Statické členy
* Notace indexeru (`arr.[x]`)
* Pojmenované a nepovinné argumenty
* Implementace rozhraní a rozhraní

**Tyto funkce nejdřív nemusíte používat, ale v případě, že jsou praktické k vyřešení problému, je třeba je použít uvážlivě:**

* Přetížení metody
* Zapouzdřená proměnlivá data
* Operátory na typech
* Automatické vlastnosti
* Implementace `IDisposable` a `IEnumerable`
* Rozšíření typů
* Události
* Struktury
* Delegáty
* Výčty

**Obecně se vyhnete těmto funkcím, pokud je nemusíte používat:**

* Hierarchie typů založené na dědičnosti a dědičnost implementace
* Hodnoty null a `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferovat kompozici před děděním

[Kompozice proti dědičnosti](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhodobá idiom, na F# kterou může vyhovovat dobrý kód. Základní princip je, že byste neměli vystavovat základní třídu a vynutit, aby volající dědili z této základní třídy, aby získala funkčnost.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Použití výrazů objektů k implementaci rozhraní, pokud nepotřebujete třídu

[Výrazy objektů](../language-reference/object-expressions.md) umožňují implementovat rozhraní za chodu, vázání implementovaného rozhraní na hodnotu, aniž by bylo nutné tak učinit uvnitř třídy. To je užitečné, zejména _Pokud potřebujete implementovat_ rozhraní a nemusíte mít úplnou třídu.

Například zde je kód, který je spuštěn v [Ionide](http://ionide.io/) a poskytuje akci opravy kódu, pokud jste přidali symbol, který nemáte příkaz `open` pro:

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

Vzhledem k tomu, že při interakci s rozhraním API Visual Studio Code není potřeba žádná třída, jsou výrazy objektu ideálním nástrojem. Jsou také cenné pro testování částí, pokud chcete odhlásit rozhraní s testovacími rutinami v ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Zvažte zkratky typu pro zkrácení signatur.

[Zkratky typů](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit popisek jinému typu, jako je například signatura funkce nebo složitější typ. Například následující alias přiřadí popisek k tomu, co je potřeba k definování výpočtu pomocí [CNTK](https://docs.microsoft.com/cognitive-toolkit/), knihovny hloubkového učení:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Název `Computation` je pohodlný způsob, jak si poznamenat jakoukoliv funkci, která odpovídá signatuře. Použití zkratek typů, jako je to pohodlné a umožňuje výstižnější kód.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Nepoužívejte zkratky typů k vyjádření vaší domény.

I když zkratky typu jsou vhodné pro poskytnutí názvu podpisům funkcí, mohou být matoucí při abbreviating jiných typů. Zvažte tuto zkratku:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

To může být matoucí v několika ohledech:

* `BufferSize` není abstrakce; je to pouze jiný název pro celé číslo.
* Pokud je `BufferSize` zveřejněné ve veřejném rozhraní API, může být snadno neinterpretované na více než jenom `int`. Obecně platí, že doménové typy mají více atributů a nejsou primitivní typy jako `int`. Tato zkratka je v rozporu s tímto předpokladem.
* Malá a velká písmena `BufferSize` (PascalCase) znamená, že tento typ obsahuje více dat.
* Tento alias nenabízí větší přehlednost v porovnání s poskytnutím pojmenovaného argumentu funkce.
* Zkratka nebude manifest v kompilovaném IL; je to jenom celé číslo a tento alias je konstrukce, která je v čase kompilace.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

V souhrnu Pitfall s zkratkami typu je, že nejsou abstrakce prostřednictvím typů, **které jsou abbreviating** . V předchozím příkladu je `BufferSize` pouze `int` v rámci pokrývání bez dalších dat, ani žádné výhody ze systému typů kromě těch, které `int` již mají.

Alternativním přístupem k použití zkratek typů k vyjádření domény je použití sjednocených sjednocení. Předchozí vzorek lze modelovat následujícím způsobem:

```fsharp
type BufferSize = BufferSize of int
```

Pokud píšete kód, který funguje v rámci `BufferSize` a jeho podkladové hodnoty, je nutné sestavit místo toho, aby předával libovolné libovolné celé číslo:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Tím se sníží pravděpodobnost neúspěšného předání libovolného celého čísla do funkce `send`, protože volající musí vytvořit `BufferSize` typ pro zabalení hodnoty před voláním funkce.
