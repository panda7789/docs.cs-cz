---
title: 'F # – konvence kódování'
description: 'Další obecné pokyny a idioms při psaní kódu pro jazyk F #.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a><span data-ttu-id="02059-103">F # – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="02059-103">F# coding conventions</span></span>

<span data-ttu-id="02059-104">Následující konvence jsou formulovali ze zkušeností práce velké F # základy kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="02059-105">[Pět principů dobrý F # – kód](index.md#five-principles-of-good-f-code) jsou základem jednotlivá doporučení.</span><span class="sxs-lookup"><span data-stu-id="02059-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="02059-106">Se jedná o [F # součást pokynů pro návrh](component-design-guidelines.md), ale platí pro všechny F # kód, ne jenom komponenty, například knihovny.</span><span class="sxs-lookup"><span data-stu-id="02059-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="02059-107">Uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="02059-107">Organizing code</span></span>

<span data-ttu-id="02059-108">Dva primární způsoby uspořádání kód funkce F #: moduly a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="02059-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="02059-109">Ty jsou podobné, ale mají následující rozdíly:</span><span class="sxs-lookup"><span data-stu-id="02059-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="02059-110">Obory názvů zjišťují jako obory názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="02059-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="02059-111">Moduly jsou kompilovány jako statické třídy.</span><span class="sxs-lookup"><span data-stu-id="02059-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="02059-112">Obory názvů jsou vždy nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="02059-112">Namespaces are always top level.</span></span> <span data-ttu-id="02059-113">Moduly lze nejvyšší úrovně a vnořené v rámci dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="02059-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="02059-114">Obory názvů, může zahrnovat víc souborů.</span><span class="sxs-lookup"><span data-stu-id="02059-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="02059-115">Moduly nelze.</span><span class="sxs-lookup"><span data-stu-id="02059-115">Modules cannot.</span></span>
* <span data-ttu-id="02059-116">Moduly může být doplněny pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="02059-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="02059-117">Podle následujících pokynů můžete použít k uspořádání vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="02059-118">Dáváte přednost obory názvů na nejvyšší úrovni</span><span class="sxs-lookup"><span data-stu-id="02059-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="02059-119">Pro všechny veřejně použití kódu jsou obory názvů přednostní modulů na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="02059-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="02059-120">Vzhledem k tomu, že se kompilují jako obory názvů .NET, jsou použití z jazyka C# s žádný problém.</span><span class="sxs-lookup"><span data-stu-id="02059-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="02059-121">Použití modulu nejvyšší úrovně se nemůže nacházet jiný při volat pouze z F #, ale pro C# příjemci, může být sledován volající tak, že aby se dosáhlo nároku `MyClass` s `MyCode` modulu.</span><span class="sxs-lookup"><span data-stu-id="02059-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="02059-122">Pečlivě použít. `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="02059-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="02059-123">`[<AutoOpen>]` Konstrukce můžete znečištění směrovány správu rozsah co je k dispozici pro volající a kde něco pochází z odpověď je "magic".</span><span class="sxs-lookup"><span data-stu-id="02059-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="02059-124">Obecně se to dobré.</span><span class="sxs-lookup"><span data-stu-id="02059-124">This is generally not a good thing.</span></span> <span data-ttu-id="02059-125">Výjimku pro toto pravidlo je základní knihovny F #, samotné (i když tento fakt je také trochu sporná).</span><span class="sxs-lookup"><span data-stu-id="02059-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="02059-126">Je však pro vaše pohodlí Pokud máte pomocné funkce pro veřejné rozhraní API, který chcete uspořádat samostatně z této veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="02059-127">To vám umožní podrobnosti této aplikace samostatné implementace z veřejné rozhraní API funkce bez nutnosti k plnému určení pomocné rutiny pokaždé, když ji volat.</span><span class="sxs-lookup"><span data-stu-id="02059-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="02059-128">Kromě toho vystavení rozšiřující metody a tvůrci výrazů na úrovni oboru názvů se přehledně vyjadřují pomocí `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="02059-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="02059-129">Použití `[<RequireQualifiedAccess>]` kdykoli může dojít ke konfliktu názvů, nebo si myslíte, že pomáhá s čitelnost</span><span class="sxs-lookup"><span data-stu-id="02059-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="02059-130">Přidávání `[<RequireQualifiedAccess>]` atribut na modul označuje, že modul nemusí otevřít a že vyžadují explicitní odkazy na elementy modulu kvalifikovaný přístup.</span><span class="sxs-lookup"><span data-stu-id="02059-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="02059-131">Například `Microsoft.FSharp.Collections.List` modul má tento atribut.</span><span class="sxs-lookup"><span data-stu-id="02059-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="02059-132">To je užitečné, když funkce a hodnoty v modulu mají názvy, které mohou v konfliktu s názvy v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="02059-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="02059-133">Vyžadování kvalifikovaný přístup může výrazně zvýšit dlouhodobé udržovatelnosti a evolvability knihovny.</span><span class="sxs-lookup"><span data-stu-id="02059-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="02059-134">Řazení `open` příkazy topologically</span><span class="sxs-lookup"><span data-stu-id="02059-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="02059-135">V jazyce F #, záleží na pořadí deklarace, včetně s `open` příkazy.</span><span class="sxs-lookup"><span data-stu-id="02059-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="02059-136">To je rozdíl oproti C#, kde účinku `using` a `using static` je nezávislá řazení tyto příkazy v souboru.</span><span class="sxs-lookup"><span data-stu-id="02059-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="02059-137">V F # elementy otevřít do oboru stínové ostatní již existuje.</span><span class="sxs-lookup"><span data-stu-id="02059-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="02059-138">To znamená, že změna `open` příkazy může změnit význam kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="02059-139">V důsledku toho všechny libovolný řazení všech `open` příkazy (například, alfanumericky) se obecně nedoporučuje, přidejte generovat různé chování, které by se dalo očekávat.</span><span class="sxs-lookup"><span data-stu-id="02059-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="02059-140">Místo toho doporučujeme řazení je [topologically](https://en.wikipedia.org/wiki/Topological_sorting); to znamená, pořadí vaše `open` příkazy v pořadí, ve kterém _vrstvy_ jsou definovány vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="02059-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="02059-141">Provádění alfanumerické řazení v rámci různých úrovní topologické může také zvážit.</span><span class="sxs-lookup"><span data-stu-id="02059-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="02059-142">Jako příklad uvádíme topologické řazení pro F # kompilátoru veřejné rozhraní API souboru služby:</span><span class="sxs-lookup"><span data-stu-id="02059-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="02059-143">Všimněte si, že konec řádku odděluje jednotlivé úrovně řazen alfanumericky později topologické vrstvy.</span><span class="sxs-lookup"><span data-stu-id="02059-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="02059-144">To ještě jednou organizuje kód bez omylem stínový provoz hodnoty.</span><span class="sxs-lookup"><span data-stu-id="02059-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="02059-145">Pomocí třídy obsahují hodnoty, které mají vedlejší efekty</span><span class="sxs-lookup"><span data-stu-id="02059-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="02059-146">Existují tolikrát, kolikrát po inicializaci hodnotu může mít vedlejší účinky, jako je například vytvoření instance kontextu databáze nebo jiných vzdálený prostředek.</span><span class="sxs-lookup"><span data-stu-id="02059-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="02059-147">Jedná se o tempting k inicializaci takové věci v modulu a použít ho v následujících funkcí:</span><span class="sxs-lookup"><span data-stu-id="02059-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="02059-148">Toto je často vhodné z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="02059-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="02059-149">Nejprve je konfigurace aplikace vložena do základu kódu s `dep1` a `dep2`.</span><span class="sxs-lookup"><span data-stu-id="02059-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="02059-150">Toto je obtížné v, že větší základy kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="02059-151">Druhý, staticky inicializovaného data nesmí obsahovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud samotné příslušné součásti bude používat více vláken.</span><span class="sxs-lookup"><span data-stu-id="02059-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="02059-152">To jasně porušení podle `dep3`.</span><span class="sxs-lookup"><span data-stu-id="02059-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="02059-153">Nakonec inicializace modulu zkompiluje do statického konstruktoru pro celý kompilace jednotku.</span><span class="sxs-lookup"><span data-stu-id="02059-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="02059-154">V případě chyby inicializace vázané na umožňují hodnotu v tomto modulu manifesty jako `TypeInitializationException` pak mezipaměti po celou dobu života aplikace.</span><span class="sxs-lookup"><span data-stu-id="02059-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="02059-155">To může být obtížné diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="02059-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="02059-156">Obvykle je vnitřní výjimka, která můžete se pokusit o důvodu, ale pokud není, nejsou k dispozici žádné o tom, co je hlavní příčinu.</span><span class="sxs-lookup"><span data-stu-id="02059-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="02059-157">Právě použijte místo toho jednoduchá pro závislosti:</span><span class="sxs-lookup"><span data-stu-id="02059-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="02059-158">To umožňuje následující:</span><span class="sxs-lookup"><span data-stu-id="02059-158">This enables the following:</span></span>

1. <span data-ttu-id="02059-159">Když zavedete všechny závislé stavu mimo rozhraní API, sám sebe.</span><span class="sxs-lookup"><span data-stu-id="02059-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="02059-160">Konfiguraci lze provést nyní mimo rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="02059-161">Chyby v inicializaci pro závislé hodnoty nejsou pravděpodobně se projeví jako `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="02059-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="02059-162">Rozhraní API je nyní snazší otestovat.</span><span class="sxs-lookup"><span data-stu-id="02059-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="02059-163">Chyba správy</span><span class="sxs-lookup"><span data-stu-id="02059-163">Error management</span></span>

<span data-ttu-id="02059-164">Správa chyby ve velkých systémů je komplexní a nuanced zařízeními a neexistují žádné silver odrážek zajištění vaše systémy jsou odolné proti chybám a chovat správně.</span><span class="sxs-lookup"><span data-stu-id="02059-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="02059-165">Následující pokyny by měl nabízí pokyny v navigace tento prostor obtížná.</span><span class="sxs-lookup"><span data-stu-id="02059-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="02059-166">Představují případech chyb a neplatný stav v typy vnitřní k vaší doméně</span><span class="sxs-lookup"><span data-stu-id="02059-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="02059-167">S [Rozlišované sjednocení](../language-reference/discriminated-unions.md), F # vám dává možnost představující stav vadný programu v systému typu.</span><span class="sxs-lookup"><span data-stu-id="02059-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="02059-168">Příklad:</span><span class="sxs-lookup"><span data-stu-id="02059-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="02059-169">V takovém případě existují tři způsoby známé, které stažení peníze z účtu bank může selhat.</span><span class="sxs-lookup"><span data-stu-id="02059-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="02059-170">Každý případ chyby představuje v typu a proto být provedeny bezpečně v rámci programu.</span><span class="sxs-lookup"><span data-stu-id="02059-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="02059-171">Obecně platí, pokud je model různé způsoby, že něco můžete **nezdaří** ve vaší doméně, pak kód pro zpracování chyb už považován za něco musí řešit kromě toku regulární programu.</span><span class="sxs-lookup"><span data-stu-id="02059-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="02059-172">Je jednoduše součástí normálního toku programu a nejsou považovány **výjimečných**.</span><span class="sxs-lookup"><span data-stu-id="02059-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="02059-173">Existují dvě hlavní výhody k tomuto:</span><span class="sxs-lookup"><span data-stu-id="02059-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="02059-174">Je také spravovat jako doménu v průběhu času mění.</span><span class="sxs-lookup"><span data-stu-id="02059-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="02059-175">Chybových případech se snadněji testování částí.</span><span class="sxs-lookup"><span data-stu-id="02059-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="02059-176">Použijte výjimky, pokud není možné vyjádřit chyby s typy</span><span class="sxs-lookup"><span data-stu-id="02059-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="02059-177">Ne všechny chyby může být reprezentován v doméně problému.</span><span class="sxs-lookup"><span data-stu-id="02059-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="02059-178">Jsou tyto druhy chyb *výjimečných* ve své podstatě, proto možnost vyvolávání a zachycení výjimek v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="02059-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="02059-179">První, doporučujeme, abyste si přečetli [pokynů pro návrh výjimka](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="02059-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="02059-180">To platí také pro F #.</span><span class="sxs-lookup"><span data-stu-id="02059-180">These are also applicable to F#.</span></span>

<span data-ttu-id="02059-181">K dispozici v F # pro účely vyvolávání výjimek hlavní konstrukce považovat za v následujícím pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="02059-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="02059-182">Funkce</span><span class="sxs-lookup"><span data-stu-id="02059-182">Function</span></span> | <span data-ttu-id="02059-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02059-183">Syntax</span></span> | <span data-ttu-id="02059-184">Účel</span><span class="sxs-lookup"><span data-stu-id="02059-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="02059-185">Vyvolá `System.ArgumentNullException` s názvem zadaného argumentu.</span><span class="sxs-lookup"><span data-stu-id="02059-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="02059-186">Vyvolá `System.ArgumentException` s názvem zadaného argumentu a zprávy.</span><span class="sxs-lookup"><span data-stu-id="02059-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="02059-187">Vyvolá `System.InvalidOperationException` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="02059-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="02059-188">Pro obecné účely mechanismus pro vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="02059-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="02059-189">Vyvolá `System.Exception` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="02059-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="02059-190">Vyvolá `System.Exception` zprávou určenému řetězec formátu a jeho vstupů.</span><span class="sxs-lookup"><span data-stu-id="02059-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="02059-191">Použití `nullArg`, `invalidArg` a `invalidOp` jako mechanizmus pro throw `ArgumentNullException`, `ArgumentException` a `InvalidOperationException` při vhodné.</span><span class="sxs-lookup"><span data-stu-id="02059-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="02059-192">`failwith` a `failwithf` funkce je nutno obecně protože vyvolají základní `Exception` typ, není určité výjimky.</span><span class="sxs-lookup"><span data-stu-id="02059-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="02059-193">Dle [pokynů pro návrh výjimka](../../standard/design-guidelines/exceptions.md), kterou chcete vygenerovat více konkrétních výjimek, pokud je možné.</span><span class="sxs-lookup"><span data-stu-id="02059-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="02059-194">Pomocí syntaxe zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="02059-194">Using exception-handling syntax</span></span>

<span data-ttu-id="02059-195">F # podporuje vzory výjimky prostřednictvím `try...with` syntaxe:</span><span class="sxs-lookup"><span data-stu-id="02059-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="02059-196">Sjednocování funkce provést při krátkodobém výjimka porovnávání vzorů může být poněkud složité, pokud chcete zachovat čistou kód.</span><span class="sxs-lookup"><span data-stu-id="02059-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="02059-197">Takové to je možné použít [aktivní vzorky](../language-reference/active-patterns.md) jako prostředek k skupiny funkce, které obaluje s případem chyba s výjimkou samotné.</span><span class="sxs-lookup"><span data-stu-id="02059-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="02059-198">Může být například využívají rozhraní API, která při vyhodí výjimku, obklopuje cenné informace v metadatech výjimka.</span><span class="sxs-lookup"><span data-stu-id="02059-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="02059-199">Rozbalování hodnotu užitečné v těle zaznamenané výjimky uvnitř aktivní vzor a vrací hodnota může být užitečné v některých situacích.</span><span class="sxs-lookup"><span data-stu-id="02059-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="02059-200">Nepoužívejte monadic nahradit výjimky pro zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="02059-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="02059-201">Výjimky jsou považovány za poněkud taboo v funkční programování.</span><span class="sxs-lookup"><span data-stu-id="02059-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="02059-202">Výjimky skutečně, porušení čistotu, takže je bezpečné vzít v úvahu je konce není funkční.</span><span class="sxs-lookup"><span data-stu-id="02059-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="02059-203">Ale když ve skutečnosti kde kód musí být spuštěn a že runtime, který může dojít k chybám bude ignorovat.</span><span class="sxs-lookup"><span data-stu-id="02059-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="02059-204">Obecně platí napište kód za předpokladu, že většina věci čistý ani celkový, chcete-li minimalizovat nepříjemným výskyt nečekaných událostí.</span><span class="sxs-lookup"><span data-stu-id="02059-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="02059-205">Je důležité vzít v úvahu následující základní síly/aspektů výjimky s ohledem na jejich relevance a vhodnost v modulu runtime rozhraní .NET a mezi jazyky ekosystém jako celek:</span><span class="sxs-lookup"><span data-stu-id="02059-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="02059-206">Obsahují podrobné diagnostické informace, které je velmi užitečné při ladění problém.</span><span class="sxs-lookup"><span data-stu-id="02059-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="02059-207">Jsou dobře porozumí modul runtime a jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="02059-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="02059-208">Významné standardní ve srovnání s kódem, který prochází mimo jeho způsob, jak se může snížit *vyhnout* výjimky implementací určitou podmnožinu jejich sémantiku na základě ad hoc.</span><span class="sxs-lookup"><span data-stu-id="02059-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="02059-209">Tento třetí bod je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="02059-209">This third point is critical.</span></span> <span data-ttu-id="02059-210">Pro triviální komplexních operací selhání použít výjimky může mít za následek práci s struktury takto:</span><span class="sxs-lookup"><span data-stu-id="02059-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="02059-211">Což může způsobit snadno křehké kódu jako porovnávání se na chyby "stringly zadány":</span><span class="sxs-lookup"><span data-stu-id="02059-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="02059-212">Kromě toho může být tempting swallow všechny výjimky v desire "jednoduchý" funkce, která vrátí hodnotu typu "nicer":</span><span class="sxs-lookup"><span data-stu-id="02059-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="02059-213">Bohužel `tryReadAllText` může vyvolat množství výjimky podle velkého počtu věcí, které může dojít v systému souborů a tento kód zahodí rychle žádné informace o co může ve skutečnosti se špatně ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="02059-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="02059-214">Pokud jste s typem výsledku, nahraďte tento kód, pak jste zpět "stringly zadány" Chyba při analýze zpráva:</span><span class="sxs-lookup"><span data-stu-id="02059-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="02059-215">A umístění samotného objektu výjimka v `Error` konstruktor právě vynutí správně zabývat typ výjimky v lokalitě volání místo ve funkci.</span><span class="sxs-lookup"><span data-stu-id="02059-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="02059-216">To efektivně vytvoří zaškrtnuté výjimky, které jsou často unfun řešení jako volající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="02059-217">Dobrou alternativou k uvedených příkladech je k zachycení *konkrétní* výjimky a vrátí hodnotu smysl v kontextu této výjimky.</span><span class="sxs-lookup"><span data-stu-id="02059-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="02059-218">Pokud změníte `tryReadAllText` funkce následujícím způsobem `None` další význam:</span><span class="sxs-lookup"><span data-stu-id="02059-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="02059-219">Místo funguje jako catch-all, tato funkce bude nyní správně zpracování případu, když soubor nebyl nalezen a přiřadit tento význam vraťte se.</span><span class="sxs-lookup"><span data-stu-id="02059-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="02059-220">Tuto hodnotu můžete mapování v takovém případě chyba, při není zahození žádné kontextové informace nebo vynucení volající řešení případu, které nemusí být důležité v tomto bodě v kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="02059-221">Typy, jako `Result<'Success, 'Error>` jsou vhodné pro základní operace, kde budou nejsou vnořené, a volitelné typů F # jsou ideální pro udávající, kdy se něco může buď vrátit *něco* nebo *nic*.</span><span class="sxs-lookup"><span data-stu-id="02059-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="02059-222">Nejsou náhradní server pro výjimky, když a nesmí být při pokusu o používá k nahrazení výjimky.</span><span class="sxs-lookup"><span data-stu-id="02059-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="02059-223">Místo toho se má být použita uvážlivě na adresu konkrétních aspektů výjimku a zásady správy chybová cílové způsoby.</span><span class="sxs-lookup"><span data-stu-id="02059-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="02059-224">Částečné aplikace a bez bodu programování</span><span class="sxs-lookup"><span data-stu-id="02059-224">Partial application and point-free programming</span></span>

<span data-ttu-id="02059-225">F # podporuje částečné aplikace a proto různé způsoby, jak program ve stylu volného bodu.</span><span class="sxs-lookup"><span data-stu-id="02059-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="02059-226">To může být užitečné pro opakované použití kódu v modulu nebo implementace něco, ale obecně se něco vystavit veřejně.</span><span class="sxs-lookup"><span data-stu-id="02059-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="02059-227">Obecně platí bez bodu programování není důsledku v a sám sebe a můžete přidat kognitivní představují významnou překážkou pro uživatele, kteří nejsou ponořena ve stylu.</span><span class="sxs-lookup"><span data-stu-id="02059-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="02059-228">Nepoužívejte částečné aplikace a currying veřejné rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02059-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="02059-229">S výjimkou malé může být matoucí pro spotřebitele použití částečné aplikace v veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="02059-230">Obvykle `let`-vázané hodnoty v F # – kód **hodnoty**, nikoli **funkce hodnoty**.</span><span class="sxs-lookup"><span data-stu-id="02059-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="02059-231">Kombinování společně hodnoty a hodnoty, funkce může způsobit ukládání malý počet řádků kódu za s bit režie kognitivní, obzvláště pokud se například v kombinaci s operátory `>>` k vytváření funkcí.</span><span class="sxs-lookup"><span data-stu-id="02059-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="02059-232">Zvažte dopad nástrojů pro programování bez bodu</span><span class="sxs-lookup"><span data-stu-id="02059-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="02059-233">Curryfikované funkce není popisku jejich argumentů.</span><span class="sxs-lookup"><span data-stu-id="02059-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="02059-234">Tato akce nemá tooling dopad.</span><span class="sxs-lookup"><span data-stu-id="02059-234">This has tooling implications.</span></span> <span data-ttu-id="02059-235">Vezměte v úvahu následující dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="02059-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="02059-236">Obě jsou platná funkce, ale `funcWithApplication` je curryfikované funkce.</span><span class="sxs-lookup"><span data-stu-id="02059-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="02059-237">Po přesunutí ukazatele myši jejich typy v editoru, zobrazí toto:</span><span class="sxs-lookup"><span data-stu-id="02059-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="02059-238">V lokalitě volání popisů tlačítek v nástrojů, jako je například Visual Studio nebude poskytují smysluplný informace o tom, co `string` a `int` ve skutečnosti představují vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="02059-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="02059-239">Pokud narazíte na bodu bez kódu jako `funcWithApplication` se veřejně použití, doporučuje se provést plnou expanzí η tak, aby nástrojů můžete vybrat až dále smysluplné názvy argumenty.</span><span class="sxs-lookup"><span data-stu-id="02059-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="02059-240">Kromě toho ladění kódu bez bodu může být náročné, pokud není možné.</span><span class="sxs-lookup"><span data-stu-id="02059-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="02059-241">Ladicí nástroje závisí na hodnotách, které jsou vázány na názvy (například `let` vazby) tak, aby si můžete prohlédnout v polovině pomocných hodnot prostřednictvím spuštění.</span><span class="sxs-lookup"><span data-stu-id="02059-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="02059-242">Pokud váš kód neobsahuje žádné hodnoty, chcete-li prověřit, není nic k ladění.</span><span class="sxs-lookup"><span data-stu-id="02059-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="02059-243">V budoucnu, nástroje pro ladění může vyvíjet syntetizovat tyto hodnoty založená na cestách ke dříve spuštění, ale není vhodné zajistila vaše dokumenty na *potenciální* ladění funkce.</span><span class="sxs-lookup"><span data-stu-id="02059-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="02059-244">Vezměte v úvahu částečné aplikace jako techniku ke snížení interní standardní</span><span class="sxs-lookup"><span data-stu-id="02059-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="02059-245">Na rozdíl od předchozího bodu částečné aplikace je skvělý nástroj pro snížení zatížení často používaný v aplikaci nebo interní podrobnější informace o rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="02059-246">Může být užitečné pro testování složitější rozhraní API, kde je často používaný často problémové jak nakládat s částí.</span><span class="sxs-lookup"><span data-stu-id="02059-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="02059-247">Například následující kód ukazuje, jak můžete provést co nejvíce mocking architektury získáte bez nutnosti převádět vnější závislosti na těchto rozhraní a nemusíte se učit se souvisejícím sled prací rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02059-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="02059-248">Zvažte například následující topografie řešení:</span><span class="sxs-lookup"><span data-stu-id="02059-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="02059-249">`ImplementationLogic.fsproj` může například vystavení kódu:</span><span class="sxs-lookup"><span data-stu-id="02059-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="02059-250">Testování částí `Transactions.doTransaction` v `ImplementationLogic.Tests.fspoj` je snadné:</span><span class="sxs-lookup"><span data-stu-id="02059-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="02059-251">Částečně použití `doTransaction` s mocking kontextu objektu umožňuje volání funkce ve všech testů jednotek bez nutnosti vytvořit mocked kontextu pokaždé, když:</span><span class="sxs-lookup"><span data-stu-id="02059-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="02059-252">Tento postup by neměl všeobecně aplikuje vaší celý codebase, ale je dobrým způsobem, jak snížit často používaný pro složité internals a tyto interní informace o testování částí.</span><span class="sxs-lookup"><span data-stu-id="02059-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="02059-253">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="02059-253">Access control</span></span>

<span data-ttu-id="02059-254">F # má několik možností [řízení přístupu](../language-reference/access-control.md), zděděné z co je k dispozici v modulu runtime rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="02059-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="02059-255">Tyto nejsou použitelné jenom pro typy – je lze využít pro funkce, příliš.</span><span class="sxs-lookup"><span data-stu-id="02059-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="02059-256">Dáváte přednost jinou hodnotu než`public` typů a členů mají být veřejně použití.</span><span class="sxs-lookup"><span data-stu-id="02059-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="02059-257">Tím se minimalizují také jaké několika příjemci k</span><span class="sxs-lookup"><span data-stu-id="02059-257">This also minimizes what consumers couple to</span></span>
* <span data-ttu-id="02059-258">Zajistit, aby všechny pomocné funkce `private`.</span><span class="sxs-lookup"><span data-stu-id="02059-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="02059-259">Zvažte použití `[<AutoOpen>]` na privátní modul pomocných funkcí, pokud budou množství.</span><span class="sxs-lookup"><span data-stu-id="02059-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="02059-260">Odvození typu a obecné typy</span><span class="sxs-lookup"><span data-stu-id="02059-260">Type inference and generics</span></span>

<span data-ttu-id="02059-261">Odvození typu můžete uložit v zadávání spoustu standardní.</span><span class="sxs-lookup"><span data-stu-id="02059-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="02059-262">A Automatická Generalizace v kompilátoru F # můžete napsat kód více obecné s téměř žádné další úsilí na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="02059-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="02059-263">Tyto funkce však nejsou všeobecně funkční.</span><span class="sxs-lookup"><span data-stu-id="02059-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="02059-264">Vezměte v úvahu označování názvy argumentu s explicitní typy v veřejná rozhraní API a nespoléhejte na odvození typu proměnné pro tuto.</span><span class="sxs-lookup"><span data-stu-id="02059-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="02059-265">Důvodem je, že **jste** by měla být v ovládacím prvku tvaru rozhraní API, není kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02059-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="02059-266">I když kompilátor můžete provést úlohu dobře v odvození typů pro vás, je možné, že tvar změnu rozhraní API, pokud internals, který přitom spoléhá na změnily typy.</span><span class="sxs-lookup"><span data-stu-id="02059-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="02059-267">To může být to, co chcete použít, ale bude skoro určitě výsledkem narušující změně rozhraní API, který pak bude mít podřízené příjemci k řešení.</span><span class="sxs-lookup"><span data-stu-id="02059-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="02059-268">Místo toho když explicitně řídíte tvaru veřejné rozhraní API, pak můžete řídit, tyto změny ukončování řádků.</span><span class="sxs-lookup"><span data-stu-id="02059-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="02059-269">V podmínky DDD to může být představit jako vrstva proti poškození.</span><span class="sxs-lookup"><span data-stu-id="02059-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="02059-270">Vezměte v úvahu smysluplný pojmenujete obecné argumenty.</span><span class="sxs-lookup"><span data-stu-id="02059-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="02059-271">Pokud píšete skutečně obecném kódu, které nejsou specifické pro konkrétní domény, může pomoci nějaký výstižný název jinými programátory pochopení, které pracují v doméně.</span><span class="sxs-lookup"><span data-stu-id="02059-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="02059-272">Například parametr typu s názvem `'Document` v kontextu interakci s dokumentem databáze je jasnější, že dokument obecné typy jsou přípustné podle funkce nebo člen pracujete s.</span><span class="sxs-lookup"><span data-stu-id="02059-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="02059-273">Vezměte v úvahu názvy parametrů obecného typu s PascalCase.</span><span class="sxs-lookup"><span data-stu-id="02059-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="02059-274">Toto je obecná moct provádět akce v rozhraní .NET, proto se doporučuje používat PascalCase místo snake_case nebo camelCase.</span><span class="sxs-lookup"><span data-stu-id="02059-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="02059-275">Nakonec Automatická generalizace není vždy skvělým nástrojem pro osoby, které jsou nové F # nebo velké základu kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="02059-276">Není režie kognitivní pomocí součásti, které jsou obecné.</span><span class="sxs-lookup"><span data-stu-id="02059-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="02059-277">Kromě toho pokud automaticky zobecněný funkce nejsou používat s různými typy vstupu (samostatně, pokud jsou určeny k použití jako takový umožňují) a potom žádné skutečné výhody jim se obecné v tomto bodě v čase.</span><span class="sxs-lookup"><span data-stu-id="02059-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="02059-278">Vždy zvažte, pokud kód, který píšete budou ve skutečnosti využívat Obecné.</span><span class="sxs-lookup"><span data-stu-id="02059-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="02059-279">Výkon</span><span class="sxs-lookup"><span data-stu-id="02059-279">Performance</span></span>

<span data-ttu-id="02059-280">F # hodnoty jsou neměnné ve výchozím nastavení, která umožňuje vyhnout určité třídy chyb (zejména těchto zahrnující souběžnosti a paralelismus).</span><span class="sxs-lookup"><span data-stu-id="02059-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="02059-281">Ale v určitých případech se pro dosažení optimálního (nebo i přiměřené) efektivitu dobu provádění nebo přidělení paměti rozpětí pracovní může nejlépe implementovat pomocí místní mutace stavu.</span><span class="sxs-lookup"><span data-stu-id="02059-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="02059-282">To je možné v základu přihlášení s F # s použitím `mutable` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="02059-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="02059-283">Ale použití `mutable` v jazyce F # může mít rozporu s funkční čistotu.</span><span class="sxs-lookup"><span data-stu-id="02059-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="02059-284">To je v pořádku, pokud upravit očekávání z čistoty [referenční průhlednost](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="02059-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="02059-285">Referenční průhlednost - není čistotu - je cílem při zápisu funkce F #.</span><span class="sxs-lookup"><span data-stu-id="02059-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="02059-286">To umožňuje zapisovat rozhraní je funkční přes na základě mutace implementace pro výkon kódu kritického pro.</span><span class="sxs-lookup"><span data-stu-id="02059-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="02059-287">Zalomení měnitelný kódu v neměnné rozhraní</span><span class="sxs-lookup"><span data-stu-id="02059-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="02059-288">S referenční transparentnosti jako cíl je důležité napsat kód, který nevystavuje měnitelný underbelly výkonu důležitých funkcí.</span><span class="sxs-lookup"><span data-stu-id="02059-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="02059-289">Například následující kód implementuje `Array.contains` funkce v základní knihovny F #:</span><span class="sxs-lookup"><span data-stu-id="02059-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="02059-290">Volání této funkce vícekrát pole Základní nezmění, ani nebude vyžadovat údržbu žádný měnitelný stav v jeho použití.</span><span class="sxs-lookup"><span data-stu-id="02059-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="02059-291">Referentially transparentní, je to i v případě, že téměř každý jednotlivý řádek kódu v něm používá mutace.</span><span class="sxs-lookup"><span data-stu-id="02059-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="02059-292">Vezměte v úvahu zapouzdřením měnitelný datový ve třídách</span><span class="sxs-lookup"><span data-stu-id="02059-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="02059-293">Předchozí příklad používá k zapouzdření operace pomocí měnitelný datový jedné funkce.</span><span class="sxs-lookup"><span data-stu-id="02059-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="02059-294">To není vždy dostatečná pro složitější datových sad.</span><span class="sxs-lookup"><span data-stu-id="02059-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="02059-295">Vezměte v úvahu následující sady funkcí:</span><span class="sxs-lookup"><span data-stu-id="02059-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="02059-296">Tento kód je původce, ale zveřejňuje na základě mutace datová struktura, že se opravdu jedná odpovědné za údržbu.</span><span class="sxs-lookup"><span data-stu-id="02059-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="02059-297">To může být uzavřen uvnitř třídu bez základní členů, které můžete změnit:</span><span class="sxs-lookup"><span data-stu-id="02059-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="02059-298">`Closure1Table` zapouzdří podkladová struktura dat na základě mutace, a tím není vynucení volající udržovat podkladová struktura data.</span><span class="sxs-lookup"><span data-stu-id="02059-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="02059-299">Třídy jsou efektivní způsob, jak zapouzdřit data a rutin, které jsou založené na mutace bez vystavení podrobnosti pro volající.</span><span class="sxs-lookup"><span data-stu-id="02059-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="02059-300">Dáváte přednost `let mutable` na referenční buňky</span><span class="sxs-lookup"><span data-stu-id="02059-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="02059-301">Referenční buňky představují způsob, jak představují odkaz na hodnotu než vlastní hodnota.</span><span class="sxs-lookup"><span data-stu-id="02059-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="02059-302">Přestože mohou být použity pro kód kritický pro výkon, se obecně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="02059-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="02059-303">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02059-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="02059-304">Použijte odkaz na buňku teď "zahltí" všechny následné kódu pomocí museli dereference a znovu referenční základní data.</span><span class="sxs-lookup"><span data-stu-id="02059-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="02059-305">Místo toho zvažte `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="02059-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="02059-306">Kromě zajištění dostatečného jediný bod mutace uprostřed výrazu lambda, všechny ostatní kód, který dotykem `acc` to lze provést tak, aby se neliší využití od normální `let`-vázaný neměnné hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02059-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="02059-307">To bude usnadňují časem změnit.</span><span class="sxs-lookup"><span data-stu-id="02059-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="02059-308">Objekt programování</span><span class="sxs-lookup"><span data-stu-id="02059-308">Object programming</span></span>

<span data-ttu-id="02059-309">F # má plnou podporu pro objekty a objektově orientované koncepty (ú).</span><span class="sxs-lookup"><span data-stu-id="02059-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="02059-310">I když mnohé koncepty ú jsou výkonný a užitečné, ne všechny z nich jsou ideální používat.</span><span class="sxs-lookup"><span data-stu-id="02059-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="02059-311">Následující seznamy nabízí pokyny k kategorií ú funkcí na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="02059-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="02059-312">**Zvažte použití těchto funkcí v mnoha situacích:**</span><span class="sxs-lookup"><span data-stu-id="02059-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="02059-313">Zápisu s tečkou (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="02059-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="02059-314">Členy instance</span><span class="sxs-lookup"><span data-stu-id="02059-314">Instance members</span></span>
* <span data-ttu-id="02059-315">Implicitní konstruktory</span><span class="sxs-lookup"><span data-stu-id="02059-315">Implicit constructors</span></span>
* <span data-ttu-id="02059-316">Statické členy</span><span class="sxs-lookup"><span data-stu-id="02059-316">Static members</span></span>
* <span data-ttu-id="02059-317">Indexer zápis (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="02059-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="02059-318">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="02059-318">Named and Optional arguments</span></span>
* <span data-ttu-id="02059-319">Rozhraní a implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="02059-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="02059-320">**Nemáte přístup pro tyto funkce nejprve, ale uvážlivě aplikovat když jsou vhodné k vyřešení problému:**</span><span class="sxs-lookup"><span data-stu-id="02059-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="02059-321">Přetěžování metody</span><span class="sxs-lookup"><span data-stu-id="02059-321">Method overloading</span></span>
* <span data-ttu-id="02059-322">Zapouzdřené měnitelný dat</span><span class="sxs-lookup"><span data-stu-id="02059-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="02059-323">Operátory pro typy</span><span class="sxs-lookup"><span data-stu-id="02059-323">Operators on types</span></span>
* <span data-ttu-id="02059-324">Automaticky vlastnosti</span><span class="sxs-lookup"><span data-stu-id="02059-324">Auto properties</span></span>
* <span data-ttu-id="02059-325">Implementace `IDisposable` a `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="02059-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="02059-326">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="02059-326">Type extensions</span></span>
* <span data-ttu-id="02059-327">Události</span><span class="sxs-lookup"><span data-stu-id="02059-327">Events</span></span>
* <span data-ttu-id="02059-328">Struktury</span><span class="sxs-lookup"><span data-stu-id="02059-328">Structs</span></span>
* <span data-ttu-id="02059-329">Delegáty</span><span class="sxs-lookup"><span data-stu-id="02059-329">Delegates</span></span>
* <span data-ttu-id="02059-330">Výčty</span><span class="sxs-lookup"><span data-stu-id="02059-330">Enums</span></span>

<span data-ttu-id="02059-331">**Pokud je třeba ji používat obecně předejít tyto funkce:**</span><span class="sxs-lookup"><span data-stu-id="02059-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="02059-332">Hierarchie dědičnosti na základě typu a implementace dědičnosti</span><span class="sxs-lookup"><span data-stu-id="02059-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="02059-333">Hodnoty Null a `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="02059-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="02059-334">Dáváte přednost složení přes dědičnost</span><span class="sxs-lookup"><span data-stu-id="02059-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="02059-335">[Složení přes dědičnost](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhotrvající stylu, které můžete řídit kód dobrý F #.</span><span class="sxs-lookup"><span data-stu-id="02059-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="02059-336">Základní princip je, že by neměl vystavit základní třídu a vynutit volající dědění z získat funkce základní třídy.</span><span class="sxs-lookup"><span data-stu-id="02059-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="02059-337">Implementace rozhraní, pokud nepotřebujete třídu pomocí objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="02059-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="02059-338">[Objekt výrazy](../language-reference/object-expressions.md) umožňují implementovat rozhraní za chodu na hodnotu bez nutnosti Uděláte to tak uvnitř třídu vazby implementovaných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02059-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="02059-339">Je to vhodné, zvlášť pokud je _pouze_ musí implementovat rozhraní a není nutné pro úplné třídu.</span><span class="sxs-lookup"><span data-stu-id="02059-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="02059-340">Například, zde je kód, který běží v [Ionide](http://ionide.io/) zadat akce opravy na kód, pokud je symbol, který jste přidali `open` příkaz pro:</span><span class="sxs-lookup"><span data-stu-id="02059-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="02059-341">Protože při interakci s Visual Studio kód rozhraní API není nutné pro třídu, objektové výrazy jsou ideální nástrojem pro to.</span><span class="sxs-lookup"><span data-stu-id="02059-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="02059-342">Rovněž jsou důležité pro testování, pokud chcete se zakázaným inzerováním na rozhraní s testovací rutiny ad hoc způsobem částí.</span><span class="sxs-lookup"><span data-stu-id="02059-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="02059-343">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="02059-343">Type Abbreviations</span></span>

<span data-ttu-id="02059-344">[Typ – zkratky](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit štítek jiného typu, například podpis funkce nebo více komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="02059-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="02059-345">Například následující alias přiřadí štítek co je potřeba k definování výpočetní s [CNTK](https://www.microsoft.com/cognitive-toolkit/), hluboká učení knihovny:</span><span class="sxs-lookup"><span data-stu-id="02059-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="02059-346">`Computation` Název je pohodlný způsob, jak označují všechny funkce, která odpovídá podpisu je aliasy.</span><span class="sxs-lookup"><span data-stu-id="02059-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="02059-347">Pomocí zkratky typů jako to je vhodné a umožňuje více stručného kódu.</span><span class="sxs-lookup"><span data-stu-id="02059-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="02059-348">Nepoužívejte zkratky typů představují doménu</span><span class="sxs-lookup"><span data-stu-id="02059-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="02059-349">I když zkratky typů jsou vhodné pro pojmenujete funkce podpisy, může se jednat matoucí při zkrácený zápis parametru jiné typy.</span><span class="sxs-lookup"><span data-stu-id="02059-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="02059-350">Vezměte v úvahu tato zkratka:</span><span class="sxs-lookup"><span data-stu-id="02059-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="02059-351">To může být matoucí několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="02059-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="02059-352">`BufferSize` není abstrakci; je právě jiný název pro celé číslo.</span><span class="sxs-lookup"><span data-stu-id="02059-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="02059-353">Pokud `BufferSize` je vystaven ve veřejné rozhraní API, ho můžete snadno dojít k nesprávné interpretaci rozumí více než jen `int`.</span><span class="sxs-lookup"><span data-stu-id="02059-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="02059-354">Obecně platí, typ domény mají více atributů k nim a nejsou primitivní typy, jako je `int`.</span><span class="sxs-lookup"><span data-stu-id="02059-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="02059-355">Tato zkratka v rozporu se předpokládá, že.</span><span class="sxs-lookup"><span data-stu-id="02059-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="02059-356">Malá a velká písmena z `BufferSize` (PascalCase) znamená, že tento typ obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="02059-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="02059-357">Tento alias nenabízí vyšší přehlednost ve srovnání s poskytováním pojmenovaný argument funkci.</span><span class="sxs-lookup"><span data-stu-id="02059-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="02059-358">Zkratka nebude manifest v kompilovaném IL; je právě celé číslo a tento alias je konstrukce kompilaci.</span><span class="sxs-lookup"><span data-stu-id="02059-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="02059-359">V souhrnu, nebezpečí s zkratky typů je, že jsou **není** abstrakce nad typy jsou zkrácený zápis parametru.</span><span class="sxs-lookup"><span data-stu-id="02059-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="02059-360">V předchozím příkladu `BufferSize` je právě `int` skrytě se žádná další data ani žádné výhody ze systému typ kromě toho, co `int` již má.</span><span class="sxs-lookup"><span data-stu-id="02059-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
