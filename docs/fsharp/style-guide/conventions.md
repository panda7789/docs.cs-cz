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
# <a name="f-coding-conventions"></a><span data-ttu-id="157ae-103">Zásady kódování jazyka F#</span><span class="sxs-lookup"><span data-stu-id="157ae-103">F# coding conventions</span></span>

<span data-ttu-id="157ae-104">Následující konvence jsou formulovány ze zkušeností s prací s velkými základy kódu F#.</span><span class="sxs-lookup"><span data-stu-id="157ae-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="157ae-105">[Pět zásad dobrého kódu F#](index.md#five-principles-of-good-f-code) jsou základem každého doporučení.</span><span class="sxs-lookup"><span data-stu-id="157ae-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="157ae-106">Souvisejí s pokyny pro [návrh komponent y F#](component-design-guidelines.md), ale jsou použitelné pro jakýkoli kód F#, nikoli pouze součásti, jako jsou knihovny.</span><span class="sxs-lookup"><span data-stu-id="157ae-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="157ae-107">Uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="157ae-107">Organizing code</span></span>

<span data-ttu-id="157ae-108">F# obsahuje dva primární způsoby uspořádání kódu: moduly a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="157ae-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="157ae-109">Jedná se o podobné, ale mají následující rozdíly:</span><span class="sxs-lookup"><span data-stu-id="157ae-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="157ae-110">Obory názvů jsou kompilovány jako obory názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="157ae-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="157ae-111">Moduly jsou kompilovány jako statické třídy.</span><span class="sxs-lookup"><span data-stu-id="157ae-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="157ae-112">Obory názvů jsou vždy nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="157ae-112">Namespaces are always top level.</span></span> <span data-ttu-id="157ae-113">Moduly mohou být nejvyšší úrovně a vnořené v rámci jiných modulů.</span><span class="sxs-lookup"><span data-stu-id="157ae-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="157ae-114">Obory názvů mohou přesahovat více souborů.</span><span class="sxs-lookup"><span data-stu-id="157ae-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="157ae-115">Moduly nemohou.</span><span class="sxs-lookup"><span data-stu-id="157ae-115">Modules cannot.</span></span>
* <span data-ttu-id="157ae-116">Moduly mohou být `[<RequireQualifiedAccess>]` `[<AutoOpen>]`zdobeny a .</span><span class="sxs-lookup"><span data-stu-id="157ae-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="157ae-117">Následující pokyny vám pomohou použít tyto k uspořádání kódu.</span><span class="sxs-lookup"><span data-stu-id="157ae-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="157ae-118">Preferovat obory názvů na nejvyšší úrovni</span><span class="sxs-lookup"><span data-stu-id="157ae-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="157ae-119">Pro všechny veřejně spotřební kód, obory názvů jsou přednostní moduly na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="157ae-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="157ae-120">Vzhledem k tomu, že jsou kompilovány jako obory názvů .NET, jsou spotřební z jazyka C# bez problémů.</span><span class="sxs-lookup"><span data-stu-id="157ae-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="157ae-121">Použití modulu nejvyšší úrovně nemusí vypadat jinak při volání pouze z F#, ale pro spotřebitele `MyClass` Jazyka `MyCode` C#mohou být volající překvapeni tím, že budou muset kvalifikovat modul.</span><span class="sxs-lookup"><span data-stu-id="157ae-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="157ae-122">Pečlivě aplikujte`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="157ae-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="157ae-123">Konstrukce `[<AutoOpen>]` může znečišťovat rozsah toho, co je k dispozici volajícím, a odpověď na to, odkud něco pochází, je "magie".</span><span class="sxs-lookup"><span data-stu-id="157ae-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="157ae-124">To není dobrá věc.</span><span class="sxs-lookup"><span data-stu-id="157ae-124">This is not a good thing.</span></span> <span data-ttu-id="157ae-125">Výjimkou z tohoto pravidla je F# Core knihovna sama o sobě (i když tato skutečnost je také trochu kontroverzní).</span><span class="sxs-lookup"><span data-stu-id="157ae-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="157ae-126">Je to však pohodlí, pokud máte pomocné funkce pro veřejné rozhraní API, které chcete uspořádat odděleně od tohoto veřejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="157ae-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="157ae-127">To umožňuje čistě oddělit podrobnosti implementace z veřejného rozhraní API funkce bez nutnosti plně kvalifikovat pomocníka pokaždé, když ji zavoláte.</span><span class="sxs-lookup"><span data-stu-id="157ae-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="157ae-128">Navíc vystavení metody rozšíření a tvůrce výrazů na úrovni oboru názvů lze `[<AutoOpen>]`úhledně vyjádřit pomocí .</span><span class="sxs-lookup"><span data-stu-id="157ae-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="157ae-129">Používejte `[<RequireQualifiedAccess>]` vždy, když by se jména mohla vystihovit nebo máte pocit, že to pomáhá s čitelností</span><span class="sxs-lookup"><span data-stu-id="157ae-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="157ae-130">Přidání `[<RequireQualifiedAccess>]` atributu do modulu znamená, že modul nemusí být otevřen a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup.</span><span class="sxs-lookup"><span data-stu-id="157ae-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="157ae-131">Například `Microsoft.FSharp.Collections.List` modul má tento atribut.</span><span class="sxs-lookup"><span data-stu-id="157ae-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="157ae-132">To je užitečné, pokud funkce a hodnoty v modulu mají názvy, které mohou být v konfliktu s názvy v jiných modulech.</span><span class="sxs-lookup"><span data-stu-id="157ae-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="157ae-133">Vyžadování kvalifikovaného přístupu může výrazně zvýšit dlouhodobou udržovatelnost a evolvability knihovny.</span><span class="sxs-lookup"><span data-stu-id="157ae-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="157ae-134">Tologicky seřadit `open` příkazy</span><span class="sxs-lookup"><span data-stu-id="157ae-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="157ae-135">V F#, pořadí prohlášení záležitosti, `open` včetně s příkazy.</span><span class="sxs-lookup"><span data-stu-id="157ae-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="157ae-136">To je na rozdíl od `using` Jazyka `using static` C#, kde účinek a je nezávislý na pořadí těchto příkazů v souboru.</span><span class="sxs-lookup"><span data-stu-id="157ae-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="157ae-137">V F# prvky otevřené do oboru může stín ostatní již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="157ae-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="157ae-138">To znamená, `open` že změna pořadí příkazy může změnit význam kódu.</span><span class="sxs-lookup"><span data-stu-id="157ae-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="157ae-139">V důsledku toho žádné libovolné řazení `open` všech příkazů (například alfanumericky) se nedoporučuje, jinak generovat různé chování, které můžete očekávat.</span><span class="sxs-lookup"><span data-stu-id="157ae-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="157ae-140">Místo toho doporučujeme je seřadit [topologicky](https://en.wikipedia.org/wiki/Topological_sorting); to znamená, `open` aby vaše příkazy v pořadí, ve kterém jsou _definovány vrstvy_ vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="157ae-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="157ae-141">Může být také zváženo alfanumerické třídění v různých topologických vrstvách.</span><span class="sxs-lookup"><span data-stu-id="157ae-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="157ae-142">Zde je zde topologické řazení pro soubor veřejného rozhraní API služby kompilátoru F#:</span><span class="sxs-lookup"><span data-stu-id="157ae-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="157ae-143">Všimněte si, že zalomení řádku odděluje topologické hladiny, přičemž každá vrstva je poté seřazena alfanumericky.</span><span class="sxs-lookup"><span data-stu-id="157ae-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="157ae-144">To čistě uspořádá kód bez náhodného stínování hodnoty.</span><span class="sxs-lookup"><span data-stu-id="157ae-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="157ae-145">Použití tříd k omezení hodnot, které mají vedlejší účinky</span><span class="sxs-lookup"><span data-stu-id="157ae-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="157ae-146">Existuje mnohokrát při inicializaci hodnoty může mít vedlejší účinky, jako je například vytváření instancí kontextu do databáze nebo jiného vzdáleného prostředku.</span><span class="sxs-lookup"><span data-stu-id="157ae-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="157ae-147">Je lákavé inicializovat takové věci v modulu a použít je v následujících funkcích:</span><span class="sxs-lookup"><span data-stu-id="157ae-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="157ae-148">To je často špatný nápad z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="157ae-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="157ae-149">Nejprve konfigurace aplikace je posunuta do základu kódu s `dep1` a `dep2`.</span><span class="sxs-lookup"><span data-stu-id="157ae-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="157ae-150">To je obtížné udržovat ve větších základech kódu.</span><span class="sxs-lookup"><span data-stu-id="157ae-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="157ae-151">Za druhé staticky inicializovaná data by neměla obsahovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud vaše komponenta sama použije více vláken.</span><span class="sxs-lookup"><span data-stu-id="157ae-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="157ae-152">To je jasně `dep3`porušena .</span><span class="sxs-lookup"><span data-stu-id="157ae-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="157ae-153">Nakonec se inicializace modulu zkompiluje do statického konstruktoru pro celou jednotku kompilace.</span><span class="sxs-lookup"><span data-stu-id="157ae-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="157ae-154">Pokud dojde k chybě v let-bound hodnota inicializace `TypeInitializationException` v tomto modulu, manifestuje jako, který je pak uložen do mezipaměti po celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="157ae-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="157ae-155">To může být obtížné diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="157ae-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="157ae-156">Tam je obvykle vnitřní výjimka, že se můžete pokusit důvod, ale pokud není, pak není říct, co je hlavní příčinou.</span><span class="sxs-lookup"><span data-stu-id="157ae-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="157ae-157">Místo toho stačí použít jednoduchou třídu pro uložení závislostí:</span><span class="sxs-lookup"><span data-stu-id="157ae-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="157ae-158">To umožňuje následující:</span><span class="sxs-lookup"><span data-stu-id="157ae-158">This enables the following:</span></span>

1. <span data-ttu-id="157ae-159">Odesílání všech závislých stav mimo samotné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="157ae-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="157ae-160">Konfiguraci lze nyní provést mimo rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="157ae-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="157ae-161">Chyby v inicializaci pro závislé `TypeInitializationException`hodnoty se pravděpodobně neprojeví jako .</span><span class="sxs-lookup"><span data-stu-id="157ae-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="157ae-162">Rozhraní API je nyní jednodušší testovat.</span><span class="sxs-lookup"><span data-stu-id="157ae-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="157ae-163">Správa chyb</span><span class="sxs-lookup"><span data-stu-id="157ae-163">Error management</span></span>

<span data-ttu-id="157ae-164">Správa chyb ve velkých systémech je složité a nuancí úsilí, a neexistují žádné stříbrné kulky v zajištění vašich systémů jsou poruchy-tolerantní a chovat se dobře.</span><span class="sxs-lookup"><span data-stu-id="157ae-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="157ae-165">Následující pokyny by měly nabídnout pokyny při navigaci v tomto obtížném prostoru.</span><span class="sxs-lookup"><span data-stu-id="157ae-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="157ae-166">Představují chybové případy a neplatný stav v typech, které jsou vlastní vaší doméně</span><span class="sxs-lookup"><span data-stu-id="157ae-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="157ae-167">S [discriminated sjednocení](../language-reference/discriminated-unions.md), F# umožňuje reprezentovat vadný stav programu v systému typu.</span><span class="sxs-lookup"><span data-stu-id="157ae-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="157ae-168">Například:</span><span class="sxs-lookup"><span data-stu-id="157ae-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="157ae-169">V tomto případě existují tři známé způsoby, jak výběr peněz z bankovního účtu může selhat.</span><span class="sxs-lookup"><span data-stu-id="157ae-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="157ae-170">Každý případ chyby je reprezentován v typu, a proto může být bezpečně řešena v celém programu.</span><span class="sxs-lookup"><span data-stu-id="157ae-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="157ae-171">Obecně platí, že pokud můžete modelovat různé způsoby, které něco může **selhat** ve vaší doméně, pak zpracování chyb kód již není považován za něco, co je třeba řešit kromě pravidelného toku programu.</span><span class="sxs-lookup"><span data-stu-id="157ae-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="157ae-172">Je to prostě součást normálního toku programu, a není považován za **výjimečný**.</span><span class="sxs-lookup"><span data-stu-id="157ae-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="157ae-173">Existují dvě hlavní výhody k tomuto:</span><span class="sxs-lookup"><span data-stu-id="157ae-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="157ae-174">Je snadnější udržovat, jak se vaše doména mění v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="157ae-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="157ae-175">Chybové případy jsou snadněji testování částí.</span><span class="sxs-lookup"><span data-stu-id="157ae-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="157ae-176">Výjimky používejte v případě, že chyby nelze reprezentovat typy</span><span class="sxs-lookup"><span data-stu-id="157ae-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="157ae-177">V problémové doméně nelze reprezentovat všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="157ae-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="157ae-178">Tyto druhy chyb jsou *výjimečné* povahy, proto schopnost vyvolat a zachytit výjimky v F#.</span><span class="sxs-lookup"><span data-stu-id="157ae-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="157ae-179">Nejprve doporučujeme přečíst si [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="157ae-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="157ae-180">Ty platí také pro F#.</span><span class="sxs-lookup"><span data-stu-id="157ae-180">These are also applicable to F#.</span></span>

<span data-ttu-id="157ae-181">Hlavní konstrukce, které jsou k dispozici v F# pro účely vyvolání výjimek, by měly být zváženy v následujícím pořadí podle preference:</span><span class="sxs-lookup"><span data-stu-id="157ae-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="157ae-182">Funkce</span><span class="sxs-lookup"><span data-stu-id="157ae-182">Function</span></span> | <span data-ttu-id="157ae-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="157ae-183">Syntax</span></span> | <span data-ttu-id="157ae-184">Účel</span><span class="sxs-lookup"><span data-stu-id="157ae-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="157ae-185">Vyvolá `System.ArgumentNullException` s zadaným názvem argumentu.</span><span class="sxs-lookup"><span data-stu-id="157ae-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="157ae-186">Vyvolá `System.ArgumentException` s zadaným názvem argumentu a zprávou.</span><span class="sxs-lookup"><span data-stu-id="157ae-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="157ae-187">Vyvolá `System.InvalidOperationException` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="157ae-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="157ae-188">Univerzální mechanismus pro vyvolání výjimek.</span><span class="sxs-lookup"><span data-stu-id="157ae-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="157ae-189">Vyvolá `System.Exception` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="157ae-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="157ae-190">Vyvolá `System.Exception` se zprávou určenou formátovacím řetězcem a jeho vstupy.</span><span class="sxs-lookup"><span data-stu-id="157ae-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="157ae-191">Použití `nullArg` `invalidArg` , `invalidOp` a jako `ArgumentNullException`mechanismus hodit , `ArgumentException` a `InvalidOperationException` v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="157ae-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="157ae-192">Funkce `failwith` `failwithf` a je obecně třeba se vyhnout, protože zvyšují základní `Exception` typ, nikoli konkrétní výjimku.</span><span class="sxs-lookup"><span data-stu-id="157ae-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="157ae-193">Podle [pokynů pro návrh výjimek](../../standard/design-guidelines/exceptions.md)chcete vyvolat konkrétnější výjimky, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="157ae-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="157ae-194">Použití syntaxe zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="157ae-194">Using exception-handling syntax</span></span>

<span data-ttu-id="157ae-195">F# podporuje vzory výjimek prostřednictvím `try...with` syntaxe:</span><span class="sxs-lookup"><span data-stu-id="157ae-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="157ae-196">Sladění funkce provádět tváří v tvář výjimku s porovnávání vzorů může být trochu složité, pokud chcete zachovat kód čistý.</span><span class="sxs-lookup"><span data-stu-id="157ae-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="157ae-197">Jedním z takových způsobů, jak to zpracovat, je použití [aktivních vzorů](../language-reference/active-patterns.md) jako prostředku k seskupení funkcí obklopujících chybový případ s výjimkou samotné.</span><span class="sxs-lookup"><span data-stu-id="157ae-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="157ae-198">Například může být náročné rozhraní API, které při vyvolání výjimky, uzavře cenné informace v metadatech výjimky.</span><span class="sxs-lookup"><span data-stu-id="157ae-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="157ae-199">Rozbalení užitečné hodnoty v těle zachycené výjimky uvnitř aktivní vzorek a vrácení této hodnoty může být užitečné v některých situacích.</span><span class="sxs-lookup"><span data-stu-id="157ae-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="157ae-200">Nepoužívejte monacké zpracování chyb k nahrazení výjimek</span><span class="sxs-lookup"><span data-stu-id="157ae-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="157ae-201">Výjimky jsou považovány za poněkud tabu ve funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="157ae-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="157ae-202">Ve skutečnosti výjimky porušují čistotu, takže je bezpečné považovat je za ne zcela funkční.</span><span class="sxs-lookup"><span data-stu-id="157ae-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="157ae-203">To však ignoruje realitu, kde musí být spuštěn kód a že může dojít k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="157ae-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="157ae-204">Obecně platí, že psát kód za předpokladu, že většina věcí nejsou ani čisté ani celkové, aby se minimalizovalo nepříjemné překvapení.</span><span class="sxs-lookup"><span data-stu-id="157ae-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="157ae-205">Je důležité vzít v úvahu následující hlavní silné a spekty výjimek s ohledem na jejich relevanci a vhodnost v běhu .NET a mezijazykovém ekosystému jako celku:</span><span class="sxs-lookup"><span data-stu-id="157ae-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="157ae-206">Obsahují podrobné diagnostické informace, což je velmi užitečné při ladění problému.</span><span class="sxs-lookup"><span data-stu-id="157ae-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="157ae-207">Jsou dobře pochopeny runtime a dalšími jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="157ae-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="157ae-208">Mohou snížit významné často používaný text ve srovnání s kódem, který jde z cesty, aby *se zabránilo* výjimkám implementací některé podmnožiny jejich sémantiky na základě ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="157ae-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="157ae-209">Tento třetí bod je kritický.</span><span class="sxs-lookup"><span data-stu-id="157ae-209">This third point is critical.</span></span> <span data-ttu-id="157ae-210">U netriviálních složitých operací může selhání použití výjimek vést k řešení struktur, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="157ae-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="157ae-211">Což může snadno vést k křehké kód, jako je porovnávání vzorů na "stringly-typed" chyby:</span><span class="sxs-lookup"><span data-stu-id="157ae-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="157ae-212">Navíc může být lákavé spolknout jakoukoli výjimku v touze po "jednoduché" funkci, která vrací "hezčí" typ:</span><span class="sxs-lookup"><span data-stu-id="157ae-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="157ae-213">Bohužel `tryReadAllText` může vyvolat četné výjimky založené na nesčetných věcech, které se mohou stát v systému souborů, a tento kód zahodí všechny informace o tom, co by mohlo být ve vašem prostředí skutečně špatně.</span><span class="sxs-lookup"><span data-stu-id="157ae-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="157ae-214">Pokud nahradíte tento kód typem výsledku, vrátíte se k analýzě chybové zprávy "stringly-typed":</span><span class="sxs-lookup"><span data-stu-id="157ae-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="157ae-215">A umístění samotného objektu výjimky do konstruktoru `Error` vás pouze vynutí, abyste správně řešili typ výjimky v místě volání, nikoli ve funkci.</span><span class="sxs-lookup"><span data-stu-id="157ae-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="157ae-216">Tím efektivně vytvoří zaškrtnuté výjimky, které jsou notoricky nezábavné řešit jako volající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="157ae-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="157ae-217">Dobrou alternativou k výše uvedeným příkladům je zachytit *konkrétní* výjimky a vrátit smysluplnou hodnotu v kontextu této výjimky.</span><span class="sxs-lookup"><span data-stu-id="157ae-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="157ae-218">Pokud změníte `tryReadAllText` funkci takto, `None` má větší význam:</span><span class="sxs-lookup"><span data-stu-id="157ae-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="157ae-219">Místo toho, aby fungovala jako catch-all, bude tato funkce nyní správně zpracovávat případ, kdy nebyl soubor nalezen, a přiřadí tento význam k návratu.</span><span class="sxs-lookup"><span data-stu-id="157ae-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="157ae-220">Tato vrácená hodnota může mapovat na tento případ chyby, aniž by zahodila žádné kontextové informace nebo nenutila volající, aby se zabývali případem, který nemusí být v daném okamžiku v kódu relevantní.</span><span class="sxs-lookup"><span data-stu-id="157ae-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="157ae-221">Typy, `Result<'Success, 'Error>` jako jsou vhodné pro základní operace, kde nejsou vnořené a F# volitelné typy jsou ideální pro reprezentaci, když něco může vrátit *něco* nebo *nic*.</span><span class="sxs-lookup"><span data-stu-id="157ae-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="157ae-222">Nejsou náhradou za výjimky, i když a neměly by být použity ve snaze nahradit výjimky.</span><span class="sxs-lookup"><span data-stu-id="157ae-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="157ae-223">Spíše by měly být uplatňovány uvážlivě řešit konkrétní aspekty politiky výjimky a chyb řízení cílenými způsoby.</span><span class="sxs-lookup"><span data-stu-id="157ae-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="157ae-224">Částečné programování aplikací a bodů bez bodu</span><span class="sxs-lookup"><span data-stu-id="157ae-224">Partial application and point-free programming</span></span>

<span data-ttu-id="157ae-225">F# podporuje částečné aplikace, a proto různé způsoby, jak programovat ve stylu bez bodu.</span><span class="sxs-lookup"><span data-stu-id="157ae-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="157ae-226">To může být prospěšné pro opětovné použití kódu v rámci modulu nebo implementace něco, ale není něco vystavit veřejně.</span><span class="sxs-lookup"><span data-stu-id="157ae-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="157ae-227">Obecně platí, že point-free programování není ctnost sama o sobě, a může přidat významnou kognitivní bariéru pro lidi, kteří nejsou ponořeni do stylu.</span><span class="sxs-lookup"><span data-stu-id="157ae-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="157ae-228">Nepoužívejte částečnou aplikaci a currying ve veřejných API</span><span class="sxs-lookup"><span data-stu-id="157ae-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="157ae-229">S malou výjimkou použití částečné aplikace ve veřejných api může být matoucí pro spotřebitele.</span><span class="sxs-lookup"><span data-stu-id="157ae-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="157ae-230">Hodnoty `let`-bound v kódu F# jsou obvykle **hodnoty**, nikoli **hodnoty funkcí**.</span><span class="sxs-lookup"><span data-stu-id="157ae-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="157ae-231">Smíchání min. hodnot a hodnot funkcí může vést k uložení malého počtu řádků kódu výměnou za `>>` poměrně dost kognitivní režie, zejména v kombinaci s operátory, jako je například skládání funkcí.</span><span class="sxs-lookup"><span data-stu-id="157ae-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="157ae-232">Zvažte důsledky nástrojů pro programování bez bodů</span><span class="sxs-lookup"><span data-stu-id="157ae-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="157ae-233">Curried funkce neoznačují jejich argumenty.</span><span class="sxs-lookup"><span data-stu-id="157ae-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="157ae-234">To má dopad y nástrojů.</span><span class="sxs-lookup"><span data-stu-id="157ae-234">This has tooling implications.</span></span> <span data-ttu-id="157ae-235">Zvažte následující dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="157ae-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="157ae-236">Obě jsou platné `funcWithApplication` funkce, ale je curried funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="157ae-237">Když najevíte nad jejich typy v editoru, zobrazí se toto:</span><span class="sxs-lookup"><span data-stu-id="157ae-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="157ae-238">Na webu volání popisky v nástrojích, jako je například Visual `string` Studio `int` nebude vám smysluplné informace o tom, co a vstupní typy skutečně představují.</span><span class="sxs-lookup"><span data-stu-id="157ae-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="157ae-239">Pokud narazíte na kód `funcWithApplication` bez bodu, jako je to veřejně spotřební, je doporučeno provést úplné η-expansion tak, aby nástroje mohou vyzvednout na smysluplné názvy pro argumenty.</span><span class="sxs-lookup"><span data-stu-id="157ae-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="157ae-240">Kromě toho ladění kódu bez bodů může být náročné, ne-li nemožné.</span><span class="sxs-lookup"><span data-stu-id="157ae-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="157ae-241">Ladicí nástroje spoléhají na hodnoty vázané na `let` názvy (například vazby), takže můžete zkontrolovat mezilehlé hodnoty uprostřed provádění.</span><span class="sxs-lookup"><span data-stu-id="157ae-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="157ae-242">Pokud váš kód nemá žádné hodnoty ke kontrole, není nic ladit.</span><span class="sxs-lookup"><span data-stu-id="157ae-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="157ae-243">V budoucnu se mohou vyvíjet ladicí nástroje, které syntetizují tyto hodnoty na základě dříve provedených cest, ale není vhodné zajistit vaše sázky na *potenciální* funkci ladění.</span><span class="sxs-lookup"><span data-stu-id="157ae-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="157ae-244">Zvažte částečnou aplikaci jako techniku ke snížení vnitřního standardního</span><span class="sxs-lookup"><span data-stu-id="157ae-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="157ae-245">Na rozdíl od předchozího bodu je částečná aplikace skvělým nástrojem pro snížení standardního nastavení uvnitř aplikace nebo hlubších vnitřních částí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="157ae-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="157ae-246">To může být užitečné pro testování částí implementace složitějších API, kde často je bolest řešit.</span><span class="sxs-lookup"><span data-stu-id="157ae-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="157ae-247">Například následující kód ukazuje, jak můžete dosáhnout toho, co většina zoslňující architektury vám bez přijetí externí závislost na takové rozhraní a museli naučit související rozhraní API na míru.</span><span class="sxs-lookup"><span data-stu-id="157ae-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="157ae-248">Zvažte například následující topografii řešení:</span><span class="sxs-lookup"><span data-stu-id="157ae-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="157ae-249">`ImplementationLogic.fsproj`může vystavit kód, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="157ae-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="157ae-250">Testování `Transactions.doTransaction` částí `ImplementationLogic.Tests.fsproj` je snadné:</span><span class="sxs-lookup"><span data-stu-id="157ae-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="157ae-251">Částečné `doTransaction` použití s objektem kontextu zesměšňuje umožňuje volat funkci ve všech testech částí bez nutnosti vytvářet zesměšňovaný kontext pokaždé:</span><span class="sxs-lookup"><span data-stu-id="157ae-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="157ae-252">Tato technika by neměla být univerzálně použita na celý základ kódu, ale je to dobrý způsob, jak snížit standardní text pro složité vnitřní a testování částí těchto vnitřních.</span><span class="sxs-lookup"><span data-stu-id="157ae-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="157ae-253">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="157ae-253">Access control</span></span>

<span data-ttu-id="157ae-254">F# má více možností pro [řízení přístupu](../language-reference/access-control.md), zděděné z toho, co je k dispozici v běhu .NET.</span><span class="sxs-lookup"><span data-stu-id="157ae-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="157ae-255">Ty nejsou použitelné jen pro typy - můžete je použít i pro funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="157ae-256">Upřednostňujte netypy`public` a členy, dokud je nebudete potřebovat k veřejnému spotřebnímu materiálu.</span><span class="sxs-lookup"><span data-stu-id="157ae-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="157ae-257">To také minimalizuje to, co spotřebitelé pár.</span><span class="sxs-lookup"><span data-stu-id="157ae-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="157ae-258">Snažte se zachovat všechny `private`pomocné funkce .</span><span class="sxs-lookup"><span data-stu-id="157ae-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="157ae-259">Zvažte použití `[<AutoOpen>]` na soukromém modulu pomocných funkcí, pokud se stanou četnými.</span><span class="sxs-lookup"><span data-stu-id="157ae-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="157ae-260">Odvození typu a obecné typy</span><span class="sxs-lookup"><span data-stu-id="157ae-260">Type inference and generics</span></span>

<span data-ttu-id="157ae-261">Odvození typu vám může ušetřit psaní velkého množství často používaných textových destiček.</span><span class="sxs-lookup"><span data-stu-id="157ae-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="157ae-262">A automatické generalizace v kompilátoru F# vám může pomoci napsat obecnější kód s téměř žádné další úsilí z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="157ae-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="157ae-263">Tyto funkce však nejsou univerzálně dobré.</span><span class="sxs-lookup"><span data-stu-id="157ae-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="157ae-264">Zvažte označení názvy argumentů s explicitní typy ve veřejných api a nespoléhejte na odvození typu pro toto.</span><span class="sxs-lookup"><span data-stu-id="157ae-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="157ae-265">Důvodem je, že **byste** měli mít kontrolu nad tvarem rozhraní API, nikoli kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="157ae-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="157ae-266">Přestože kompilátor může provést dobrou práci při odvození typů pro vás, je možné mít tvar rozhraní API změnit, pokud vnitřní části, na kterých spoléhá, změnily typy.</span><span class="sxs-lookup"><span data-stu-id="157ae-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="157ae-267">To může být to, co chcete, ale to bude téměř jistě mít za následek porušení změny rozhraní API, že příjem spotřebitelů pak bude muset vypořádat s.</span><span class="sxs-lookup"><span data-stu-id="157ae-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="157ae-268">Místo toho pokud explicitně řídíte tvar veřejného rozhraní API, můžete tyto narušující změny řídit.</span><span class="sxs-lookup"><span data-stu-id="157ae-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="157ae-269">Z hlediska DDD si to lze myslet jako antikorupční vrstvu.</span><span class="sxs-lookup"><span data-stu-id="157ae-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="157ae-270">Zvažte poskytnutí smysluplného názvu obecným argumentům.</span><span class="sxs-lookup"><span data-stu-id="157ae-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="157ae-271">Pokud nepíšete skutečně obecný kód, který není specifický pro určitou doménu, může smysluplný název pomoci ostatním programátorům pochopit doménu, ve které pracují.</span><span class="sxs-lookup"><span data-stu-id="157ae-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="157ae-272">Například parametr typu `'Document` pojmenovaný v kontextu interakce s databází dokumentů umožňuje jasnější, že obecné typy dokumentů mohou být přijaty funkcí nebo členem, se kterým pracujete.</span><span class="sxs-lookup"><span data-stu-id="157ae-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="157ae-273">Zvažte pojmenování parametrů obecného typu pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="157ae-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="157ae-274">Toto je obecný způsob, jak dělat věci v rozhraní .NET, takže je doporučeno používat PascalCase spíše než snake_case nebo camelCase.</span><span class="sxs-lookup"><span data-stu-id="157ae-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="157ae-275">Nakonec automatické generalizace není vždy přínosem pro lidi, kteří jsou nové F# nebo velký základ kódu.</span><span class="sxs-lookup"><span data-stu-id="157ae-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="157ae-276">Existuje kognitivní režie v použití komponent, které jsou obecné.</span><span class="sxs-lookup"><span data-stu-id="157ae-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="157ae-277">Kromě toho pokud automaticky generalizované funkce nejsou používány s různými typy vstupů (natož pokud jsou určeny k použití jako takové), pak neexistuje žádný skutečný přínos pro ně jsou obecné v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="157ae-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="157ae-278">Vždy zvažte, zda kód, který píšete bude skutečně těžit z obecné.</span><span class="sxs-lookup"><span data-stu-id="157ae-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="157ae-279">Výkon</span><span class="sxs-lookup"><span data-stu-id="157ae-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="157ae-280">Preferujte struktury pro malé datové typy</span><span class="sxs-lookup"><span data-stu-id="157ae-280">Prefer structs for small data types</span></span>

<span data-ttu-id="157ae-281">Použití struktury (také volal Typy hodnot) může často vést k vyšší výkon pro některé kód, protože obvykle zabraňuje přidělování objektů.</span><span class="sxs-lookup"><span data-stu-id="157ae-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="157ae-282">Struktury však nejsou vždy tlačítko "jít rychleji": pokud velikost dat ve struktuře překročí 16 bajtů, kopírování dat může často vést k více času procesoru než použití typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="157ae-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="157ae-283">Chcete-li zjistit, zda byste měli použít strukturu, zvažte následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="157ae-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="157ae-284">Pokud je velikost dat 16 bajtů nebo menší.</span><span class="sxs-lookup"><span data-stu-id="157ae-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="157ae-285">Pokud je pravděpodobné, že mnoho z těchto datových typů rezidentní v paměti v běžícím programu.</span><span class="sxs-lookup"><span data-stu-id="157ae-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="157ae-286">Pokud platí první podmínka, měli byste obecně použít strukturu.</span><span class="sxs-lookup"><span data-stu-id="157ae-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="157ae-287">Pokud se obě platí, měli byste téměř vždy použít strukturu.</span><span class="sxs-lookup"><span data-stu-id="157ae-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="157ae-288">Mohou existovat některé případy, kdy platí předchozí podmínky, ale použití struktury není lepší nebo horší než použití referenčního typu, ale je pravděpodobné, že budou vzácné.</span><span class="sxs-lookup"><span data-stu-id="157ae-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="157ae-289">Je důležité vždy měřit při provádění změn, jako je tento, i když, a ne pracovat na předpokladu nebo intuice.</span><span class="sxs-lookup"><span data-stu-id="157ae-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="157ae-290">Preferovat strukturní řazené kolekce členů při seskupování malých typů hodnot</span><span class="sxs-lookup"><span data-stu-id="157ae-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="157ae-291">Zvažte následující dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="157ae-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="157ae-292">Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako je `runWithStructTuple` [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že funkce, která používá strukturní řazené řazené kolekce členů, běží o 40% rychleji a nepřiděluje žádnou paměť.</span><span class="sxs-lookup"><span data-stu-id="157ae-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="157ae-293">Tyto výsledky však nebude vždy případ ve vašem vlastním kódu.</span><span class="sxs-lookup"><span data-stu-id="157ae-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="157ae-294">Pokud označíte `inline`funkci jako , kód, který používá referenční řazené kolekce členů, může získat některé další optimalizace nebo kód, který by přidělit by jednoduše optimalizovat pryč.</span><span class="sxs-lookup"><span data-stu-id="157ae-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="157ae-295">Výsledky byste měli vždy měřit vždy, když se jedná o výkon, a nikdy nepracovat na základě předpokladu nebo intuice.</span><span class="sxs-lookup"><span data-stu-id="157ae-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="157ae-296">Preferovat záznamy struktury, pokud je datový typ malý</span><span class="sxs-lookup"><span data-stu-id="157ae-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="157ae-297">Pravidlo popsané výše platí také pro [typy záznamů F#](../language-reference/records.md).</span><span class="sxs-lookup"><span data-stu-id="157ae-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="157ae-298">Zvažte následující datové typy a funkce, které je zpracovávají:</span><span class="sxs-lookup"><span data-stu-id="157ae-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="157ae-299">To je podobné předchozí n-tice kód, ale tentokrát v příkladu používá záznamy a vložené vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="157ae-300">Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako `processStructPoint` je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že běží téměř o 60% rychleji a nepřiděluje nic na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="157ae-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="157ae-301">Preferovat strukturní discriminated sjednocení, pokud je datový typ malý</span><span class="sxs-lookup"><span data-stu-id="157ae-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="157ae-302">Předchozí pozorování o výkonu s nit řazené kolekce členů a záznamy platí také pro [F# discriminated sjednocení](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="157ae-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="157ae-303">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="157ae-303">Consider the following code:</span></span>

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

<span data-ttu-id="157ae-304">Je běžné definovat jednopřípadové discriminated sjednocení, jako je tento pro modelování domény.</span><span class="sxs-lookup"><span data-stu-id="157ae-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="157ae-305">Když porovnáte tyto funkce pomocí statistického srovnávacího nástroje, jako `structReverseName` je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že běží asi o 25% rychleji než `reverseName` u malých řetězců.</span><span class="sxs-lookup"><span data-stu-id="157ae-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="157ae-306">U velkých řetězců oba provádět přibližně stejné.</span><span class="sxs-lookup"><span data-stu-id="157ae-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="157ae-307">Takže v tomto případě je vždy vhodnější použít strukturu.</span><span class="sxs-lookup"><span data-stu-id="157ae-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="157ae-308">Jak již bylo zmíněno, vždy měřit a nepracují na předpokladech nebo intuici.</span><span class="sxs-lookup"><span data-stu-id="157ae-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="157ae-309">Přestože předchozí příklad ukázal, že struktura discriminated Unie přinesla lepší výkon, je běžné mít větší discriminated sjednocení při modelování domény.</span><span class="sxs-lookup"><span data-stu-id="157ae-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="157ae-310">Větší datové typy, jako že nemusí provádět stejně, pokud jsou struktury v závislosti na operacích na nich, protože další kopírování může být zapojen.</span><span class="sxs-lookup"><span data-stu-id="157ae-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="157ae-311">Funkční programování a mutace</span><span class="sxs-lookup"><span data-stu-id="157ae-311">Functional programming and mutation</span></span>

<span data-ttu-id="157ae-312">Hodnoty Jazyka F# jsou ve výchozím nastavení neměnné, což umožňuje vyhnout se určitým třídám chyb (zejména těch, které zahrnují souběžnost a paralelismus).</span><span class="sxs-lookup"><span data-stu-id="157ae-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="157ae-313">V některých případech však za účelem dosažení optimální (nebo dokonce přiměřené) účinnosti doby provádění nebo přidělení paměti může být nejlepší využití rozsahu práce pomocí mutace stavu na místě.</span><span class="sxs-lookup"><span data-stu-id="157ae-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="157ae-314">To je možné v opt-in základě `mutable` s F# s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="157ae-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="157ae-315">Použití `mutable` v F# může cítit v rozporu s funkční čistoty.</span><span class="sxs-lookup"><span data-stu-id="157ae-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="157ae-316">To je pochopitelné, ale funkční čistota všude může být v rozporu s výkonnostními cíli.</span><span class="sxs-lookup"><span data-stu-id="157ae-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="157ae-317">Kompromis emituje mutace tak, že volající nemusí starat o to, co se stane, když volají funkci.</span><span class="sxs-lookup"><span data-stu-id="157ae-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="157ae-318">To umožňuje psát funkční rozhraní přes implementaci založenou na mutaci pro kód kritický pro výkon.</span><span class="sxs-lookup"><span data-stu-id="157ae-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="157ae-319">Zalamování proměnlivého kódu v neměnných rozhraních</span><span class="sxs-lookup"><span data-stu-id="157ae-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="157ae-320">S referenční transparentnost jako cíl, je důležité napsat kód, který nezveřejňuje proměnlivé podbřišek funkce kritické pro výkon.</span><span class="sxs-lookup"><span data-stu-id="157ae-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="157ae-321">Například následující kód implementuje `Array.contains` funkci v základní knihovně F#:</span><span class="sxs-lookup"><span data-stu-id="157ae-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="157ae-322">Volání této funkce vícekrát nezmění základní pole, ani nevyžaduje udržovat proměnlivý stav při jeho využívání.</span><span class="sxs-lookup"><span data-stu-id="157ae-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="157ae-323">Je to referenční transparentní, i když téměř každý řádek kódu v něm používá mutaci.</span><span class="sxs-lookup"><span data-stu-id="157ae-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="157ae-324">Zvažte zapouzdření proměnlivých dat do tříd</span><span class="sxs-lookup"><span data-stu-id="157ae-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="157ae-325">Předchozí příklad používá jednu funkci zapouzdřit operace pomocí proměnlivá data.</span><span class="sxs-lookup"><span data-stu-id="157ae-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="157ae-326">To není vždy dostačující pro složitější sady dat.</span><span class="sxs-lookup"><span data-stu-id="157ae-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="157ae-327">Zvažte následující sady funkcí:</span><span class="sxs-lookup"><span data-stu-id="157ae-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="157ae-328">Tento kód je performant, ale zveřejňuje strukturu dat na základě mutace, že volající jsou zodpovědní za údržbu.</span><span class="sxs-lookup"><span data-stu-id="157ae-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="157ae-329">To může být zabaleno uvnitř třídy bez podkladových členů, které se mohou změnit:</span><span class="sxs-lookup"><span data-stu-id="157ae-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="157ae-330">`Closure1Table`zapouzdřuje základní strukturu dat založenou na mutacích, čímž volající nenutí udržovat základní datovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="157ae-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="157ae-331">Třídy jsou účinný způsob, jak zapouzdřit data a rutiny, které jsou založeny na mutaci bez vystavení podrobnosti volajícím.</span><span class="sxs-lookup"><span data-stu-id="157ae-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="157ae-332">Preferujte `let mutable` referenční buňky</span><span class="sxs-lookup"><span data-stu-id="157ae-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="157ae-333">Referenční buňky představují odkaz na hodnotu, nikoli na samotnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="157ae-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="157ae-334">Přestože je lze použít pro kód kritický pro výkon, nejsou doporučeny.</span><span class="sxs-lookup"><span data-stu-id="157ae-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="157ae-335">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="157ae-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="157ae-336">Použití referenční buňky nyní "znečišťuje" všechny následné kódy s nutností odkazovat a znovu odkazovat na podkladová data.</span><span class="sxs-lookup"><span data-stu-id="157ae-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="157ae-337">Místo toho `let mutable`zvažte:</span><span class="sxs-lookup"><span data-stu-id="157ae-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="157ae-338">Kromě jediného bodu mutace uprostřed výrazu lambda, všechny `acc` ostatní kód, který se dotýká může tak učinit `let`způsobem, který se neliší od použití normální vázané neměnné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="157ae-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="157ae-339">To usnadní změnu v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="157ae-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="157ae-340">Programování objektů</span><span class="sxs-lookup"><span data-stu-id="157ae-340">Object programming</span></span>

<span data-ttu-id="157ae-341">F# má plnou podporu pro objekty a objektově orientované (OO) koncepty.</span><span class="sxs-lookup"><span data-stu-id="157ae-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="157ae-342">Ačkoli mnoho Konceptů OO je výkonných a užitečných, ne všechny jsou ideální pro použití.</span><span class="sxs-lookup"><span data-stu-id="157ae-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="157ae-343">Následující seznamy obsahují pokyny pro kategorie funkcí OO na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="157ae-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="157ae-344">**Zvažte použití těchto funkcí v mnoha situacích:**</span><span class="sxs-lookup"><span data-stu-id="157ae-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="157ae-345">Dot notace (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="157ae-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="157ae-346">Členové instance</span><span class="sxs-lookup"><span data-stu-id="157ae-346">Instance members</span></span>
* <span data-ttu-id="157ae-347">Implicitní konstruktory</span><span class="sxs-lookup"><span data-stu-id="157ae-347">Implicit constructors</span></span>
* <span data-ttu-id="157ae-348">Statické členy</span><span class="sxs-lookup"><span data-stu-id="157ae-348">Static members</span></span>
* <span data-ttu-id="157ae-349">Zápis indexeru`arr.[x]`( )</span><span class="sxs-lookup"><span data-stu-id="157ae-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="157ae-350">Pojmenované a volitelné argumenty</span><span class="sxs-lookup"><span data-stu-id="157ae-350">Named and Optional arguments</span></span>
* <span data-ttu-id="157ae-351">Rozhraní a implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="157ae-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="157ae-352">**Nesahujte po těchto funkcích jako první, ale uvážlivě je aplikujte, když jsou vhodné k vyřešení problému:**</span><span class="sxs-lookup"><span data-stu-id="157ae-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="157ae-353">Přetížení metody</span><span class="sxs-lookup"><span data-stu-id="157ae-353">Method overloading</span></span>
* <span data-ttu-id="157ae-354">Zapouzdřená proměnlivá data</span><span class="sxs-lookup"><span data-stu-id="157ae-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="157ae-355">Operátory na typech</span><span class="sxs-lookup"><span data-stu-id="157ae-355">Operators on types</span></span>
* <span data-ttu-id="157ae-356">Automatické vlastnosti</span><span class="sxs-lookup"><span data-stu-id="157ae-356">Auto properties</span></span>
* <span data-ttu-id="157ae-357">Provádění `IDisposable` a provádění`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="157ae-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="157ae-358">Rozšíření typu</span><span class="sxs-lookup"><span data-stu-id="157ae-358">Type extensions</span></span>
* <span data-ttu-id="157ae-359">Akce</span><span class="sxs-lookup"><span data-stu-id="157ae-359">Events</span></span>
* <span data-ttu-id="157ae-360">Struktury</span><span class="sxs-lookup"><span data-stu-id="157ae-360">Structs</span></span>
* <span data-ttu-id="157ae-361">Delegáty</span><span class="sxs-lookup"><span data-stu-id="157ae-361">Delegates</span></span>
* <span data-ttu-id="157ae-362">Výčty</span><span class="sxs-lookup"><span data-stu-id="157ae-362">Enums</span></span>

<span data-ttu-id="157ae-363">**Obecně se těmto funkcím vyhněte, pokud je nepotřebujete použít:**</span><span class="sxs-lookup"><span data-stu-id="157ae-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="157ae-364">Hierarchie typu založené na dědičnosti a dědičnost implementace</span><span class="sxs-lookup"><span data-stu-id="157ae-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="157ae-365">Nulla a`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="157ae-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="157ae-366">Upřednostnit složení před dědičností</span><span class="sxs-lookup"><span data-stu-id="157ae-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="157ae-367">[Složení nad dědičnost](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhotrvající idiom, že dobrý kód F#může dodržovat.</span><span class="sxs-lookup"><span data-stu-id="157ae-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="157ae-368">Základním principem je, že byste neměli vystavit základní třídy a vynutit volající dědit z této základní třídy získat funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="157ae-369">Použití výrazů objektu k implementaci rozhraní, pokud nepotřebujete třídu</span><span class="sxs-lookup"><span data-stu-id="157ae-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="157ae-370">[Objektové výrazy](../language-reference/object-expressions.md) umožňují implementovat rozhraní za běhu, vazby implementované rozhraní na hodnotu bez nutnosti tak učinit uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="157ae-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="157ae-371">To je výhodné, zejména pokud potřebujete _pouze_ implementovat rozhraní a nemáte potřebu celé třídy.</span><span class="sxs-lookup"><span data-stu-id="157ae-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="157ae-372">Například zde je kód, který je spuštěn v [Ionide](http://ionide.io/) poskytnout opravu kódu akce, pokud jste `open` přidali symbol, který nemáte příkaz pro:</span><span class="sxs-lookup"><span data-stu-id="157ae-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="157ae-373">Vzhledem k tomu, že není potřeba pro třídu při interakci s rozhraním API kódu visual studio, objektové výrazy jsou ideálním nástrojem pro tento.</span><span class="sxs-lookup"><span data-stu-id="157ae-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="157ae-374">Jsou také cenné pro testování částí, pokud chcete získat výtržek z rozhraní s testovací rutiny způsobem ad hoc.</span><span class="sxs-lookup"><span data-stu-id="157ae-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="157ae-375">Zvažte zkratky typu pro zkrácení podpisů</span><span class="sxs-lookup"><span data-stu-id="157ae-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="157ae-376">[Zkratky typu](../language-reference/type-abbreviations.md) jsou pohodlným způsobem přiřazení popisku jinému typu, například podpisu funkce nebo složitějšímu typu.</span><span class="sxs-lookup"><span data-stu-id="157ae-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="157ae-377">Například následující alias přiřadí popisek k tomu, co je potřeba k definování výpočtu s [CNTK](https://docs.microsoft.com/cognitive-toolkit/), knihovnou hlubokého učení:</span><span class="sxs-lookup"><span data-stu-id="157ae-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="157ae-378">Název `Computation` je pohodlný způsob, jak oznamovat všechny funkce, které odpovídají podpisu, který aliasuje.</span><span class="sxs-lookup"><span data-stu-id="157ae-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="157ae-379">Použití typových zkratek, jako je tento, je pohodlné a umožňuje stručnější kód.</span><span class="sxs-lookup"><span data-stu-id="157ae-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="157ae-380">Vyhněte se použití zkratky typu reprezentovat svou doménu</span><span class="sxs-lookup"><span data-stu-id="157ae-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="157ae-381">Přestože zkratky typu jsou vhodné pro zadání názvu pro funkce podpisy, mohou být matoucí při zkrácení jiných typů.</span><span class="sxs-lookup"><span data-stu-id="157ae-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="157ae-382">Vezměme si tuto zkratku:</span><span class="sxs-lookup"><span data-stu-id="157ae-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="157ae-383">To může být matoucí několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="157ae-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="157ae-384">`BufferSize`není abstrakcí; je to jen jiný název pro celé číslo.</span><span class="sxs-lookup"><span data-stu-id="157ae-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="157ae-385">Pokud `BufferSize` je vystavena ve veřejném rozhraní API, může být snadno `int`nesprávně interpretována znamenat více než jen .</span><span class="sxs-lookup"><span data-stu-id="157ae-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="157ae-386">Obecně platí, že typy domén mají více atributů k nim a nejsou primitivní typy jako `int`.</span><span class="sxs-lookup"><span data-stu-id="157ae-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="157ae-387">Tato zkratka tento předpoklad porušuje.</span><span class="sxs-lookup"><span data-stu-id="157ae-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="157ae-388">Caseing `BufferSize` (PascalCase) znamená, že tento typ obsahuje více dat.</span><span class="sxs-lookup"><span data-stu-id="157ae-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="157ae-389">Tento alias nenabízí větší srozumitelnost ve srovnání s poskytováním pojmenované argument funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="157ae-390">Zkratka se neprojeví v kompilovaném IL; je pouze celé číslo a tento alias je konstrukce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="157ae-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="157ae-391">Stručně řečeno, úskalí s typem zkratky je, že **nejsou** abstrakce nad typy, které jsou zkrácení.</span><span class="sxs-lookup"><span data-stu-id="157ae-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="157ae-392">V předchozím příkladu, `int` je jen pod kryty, bez dalších údajů, `int` ani žádné výhody z typového systému kromě toho, `BufferSize` co již má.</span><span class="sxs-lookup"><span data-stu-id="157ae-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="157ae-393">Alternativní přístup k použití zkratky typu představují doménu je použití jednomístné diskriminované sjednocení.</span><span class="sxs-lookup"><span data-stu-id="157ae-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="157ae-394">Předchozí vzorek lze modelovat takto:</span><span class="sxs-lookup"><span data-stu-id="157ae-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="157ae-395">Pokud píšete kód, který `BufferSize` pracuje z hlediska a jeho základní hodnotu, je třeba vytvořit jeden spíše než předat v libovolné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="157ae-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="157ae-396">To snižuje pravděpodobnost chybně předání libovolné celé číslo `send` do funkce, protože `BufferSize` volající musí vytvořit typ zabalit hodnotu před voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="157ae-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
