---
title: F#konvence kódování
description: Další obecné pokyny a idiomy při zápisu F# kódu.
ms.date: 05/14/2018
ms.openlocfilehash: 1ef016184180eb8d233295e8985903e07693ad26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186742"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="48ac4-103">F#konvence kódování</span><span class="sxs-lookup"><span data-stu-id="48ac4-103">F# coding conventions</span></span>

<span data-ttu-id="48ac4-104">Následující konvence jsou formulovat z prostředí pro práci s rozsáhlými F# základů kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="48ac4-105">[Pět zásadami dobrého F# kód](index.md#five-principles-of-good-f-code) jsou základem pro jednotlivá doporučení.</span><span class="sxs-lookup"><span data-stu-id="48ac4-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="48ac4-106">Se vztahují k [ F# pokyny k návrhu komponenty](component-design-guidelines.md), ale platí pro všechny F# kód, ne jenom komponent, jako jsou knihovny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="48ac4-107">Uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="48ac4-107">Organizing code</span></span>

<span data-ttu-id="48ac4-108">F#Funkce dva primární způsoby, jak organizovat kód: modulů a oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="48ac4-109">Ty jsou podobné, ale mají tyto věci:</span><span class="sxs-lookup"><span data-stu-id="48ac4-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="48ac4-110">Obory názvů jsou kompilovány jako obory názvů rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="48ac4-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="48ac4-111">Moduly jsou kompilovány jako statické třídy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="48ac4-112">Obory názvů jsou vždy nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="48ac4-112">Namespaces are always top level.</span></span> <span data-ttu-id="48ac4-113">Moduly je možné nejvyšší úrovně a vnořené v jiných modulů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="48ac4-114">Obory názvů může zahrnovat více souborů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="48ac4-115">Moduly nelze.</span><span class="sxs-lookup"><span data-stu-id="48ac4-115">Modules cannot.</span></span>
* <span data-ttu-id="48ac4-116">Moduly, může být doplněny pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="48ac4-117">Podle následujících pokynů můžete použít k uspořádání kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="48ac4-118">Dáváte přednost oborů názvů na nejvyšší úrovni</span><span class="sxs-lookup"><span data-stu-id="48ac4-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="48ac4-119">Pro všechny veřejně použitelné kódu obory názvů jsou přednostní moduly na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="48ac4-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="48ac4-120">Vzhledem k tomu, že se kompilují jako obory názvů .NET, jsou použitelné z jazyka C# s žádný problém.</span><span class="sxs-lookup"><span data-stu-id="48ac4-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="48ac4-121">Použití nejvyšší úrovně modulu nemusí vypadat jinak, když volat pouze z F#, ale pro C# spotřebitele, volající může být sledován tím, že k získání způsobilosti `MyClass` s `MyCode` modulu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="48ac4-122">Pečlivě použít. `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="48ac4-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="48ac4-123">`[<AutoOpen>]` Konstrukce můžete znečištění směrovány správu rozsah co je k dispozici pro volající a odpověď na něco ze kterého pochází je "magické".</span><span class="sxs-lookup"><span data-stu-id="48ac4-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="48ac4-124">Většinou to není dobrá věc.</span><span class="sxs-lookup"><span data-stu-id="48ac4-124">This is generally not a good thing.</span></span> <span data-ttu-id="48ac4-125">Výjimkou z tohoto pravidla je F# základní knihovny sám (i když tato skutečnost se taky o něco kontroverzním).</span><span class="sxs-lookup"><span data-stu-id="48ac4-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="48ac4-126">Je však pohodlí Pokud máte pomocnou funkci pro veřejné rozhraní API, kterou chcete uspořádat samostatně z této veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="48ac4-127">Díky tomu můžete podrobnosti implementace čistě samostatné z veřejné rozhraní API funkce bez nutnosti k plnému určení pomocné rutiny pokaždé, když ji volat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="48ac4-128">Kromě toho vystavuje metody rozšíření a Tvůrce výrazů na úrovni oboru názvů lze elegantně vyjádřit pomocí `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="48ac4-129">Použití `[<RequireQualifiedAccess>]` vždy, když mohla být v konfliktu názvů, nebo máte pocit, že pomáhá s čitelnost</span><span class="sxs-lookup"><span data-stu-id="48ac4-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="48ac4-130">Přidávání `[<RequireQualifiedAccess>]` atribut do modulu označuje, že modul nelze otevřít, a přístup, vyžaduje explicitní odkazy na elementy modulu kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="48ac4-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="48ac4-131">Například `Microsoft.FSharp.Collections.List` modul nemá tento atribut.</span><span class="sxs-lookup"><span data-stu-id="48ac4-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="48ac4-132">To je užitečné, když funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="48ac4-133">Které vyžadují přístup pro kvalifikovaný může výrazně zvýšit dlouhodobou udržovatelnost a ovlivňujících knihovny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="48ac4-134">Řazení `open` příkazy topologically</span><span class="sxs-lookup"><span data-stu-id="48ac4-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="48ac4-135">V F#, pořadí deklarace věcech, včetně `open` příkazy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="48ac4-136">To je rozdíl oproti C#, ve kterém účinek `using` a `using static` je nezávislý na pořadí těchto příkazů do souboru.</span><span class="sxs-lookup"><span data-stu-id="48ac4-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="48ac4-137">V F#, prvky otevřít do oboru můžete stínové ostatní již existuje.</span><span class="sxs-lookup"><span data-stu-id="48ac4-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="48ac4-138">To znamená, že změny pořadí `open` příkazů může změnit význam kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="48ac4-139">V důsledku toho všechny libovolného řazení všech `open` příkazy (například alfanumericky) se obecně nedoporučuje, přidejte generovat různé chování by se dalo očekávat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="48ac4-140">Namísto toho doporučujeme je seřadit [topologically](https://en.wikipedia.org/wiki/Topological_sorting); to znamená pořadí vaše `open` příkazů v pořadí, ve kterém _vrstvy_ systému jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="48ac4-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="48ac4-141">Provádění alfanumerické řazení v rámci různých topologické vrstvy mohou také zvážit.</span><span class="sxs-lookup"><span data-stu-id="48ac4-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="48ac4-142">Jako příklad uvádíme topologické řazení pro F# soubor veřejné rozhraní API služby kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="48ac4-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="48ac4-143">Všimněte si, že konec řádku odděluje topologické vrstvy s každou vrstvou seřazený alfanumericky později.</span><span class="sxs-lookup"><span data-stu-id="48ac4-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="48ac4-144">To čistě slouží k uspořádání kódu bez náhodně stínováním hodnoty.</span><span class="sxs-lookup"><span data-stu-id="48ac4-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="48ac4-145">Použití tříd obsahující hodnoty, které mají vedlejší účinky</span><span class="sxs-lookup"><span data-stu-id="48ac4-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="48ac4-146">Mnohokrát se vám při inicializaci hodnota může mít vedlejší účinky, jako je vytvoření instance kontextu do databáze nebo jiného vzdáleného prostředku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="48ac4-147">Je lákavé k inicializaci prvků v modulu a jeho použití v následující funkce:</span><span class="sxs-lookup"><span data-stu-id="48ac4-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="48ac4-148">To je často vhodné mít několik důvodů:</span><span class="sxs-lookup"><span data-stu-id="48ac4-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="48ac4-149">Nejprve konfigurace aplikace se vloží do základu kódu `dep1` a `dep2`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="48ac4-150">Toto je obtížné udržovat v větší základů kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="48ac4-151">Druhý, staticky inicializovaná data by neměl obsahovat hodnoty, které nejsou vláknově bezpečné, pokud vaše komponenta samotné používat více vláken.</span><span class="sxs-lookup"><span data-stu-id="48ac4-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="48ac4-152">To je jasně byla porušena `dep3`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="48ac4-153">Nakonec inicializace modulu kompiluje do statického konstruktoru pro celý kompilační jednotky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="48ac4-154">Pokud v inicializace hodnoty vazbou let v tomto modulu dojde k jakékoli chybě, manifesty jako `TypeInitializationException` , která se pak zapíší do mezipaměti po celou dobu života aplikace.</span><span class="sxs-lookup"><span data-stu-id="48ac4-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="48ac4-155">To může být obtížné diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="48ac4-156">Obvykle je vnitřní výjimku, která se může pokusit o důvodu, ale pokud není, nejsou k dispozici žádné o tom, co je hlavní příčinu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="48ac4-157">Stačí použijte místo toho jednoduchou třídu pro uložení závislosti:</span><span class="sxs-lookup"><span data-stu-id="48ac4-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="48ac4-158">To umožňuje následující:</span><span class="sxs-lookup"><span data-stu-id="48ac4-158">This enables the following:</span></span>

1. <span data-ttu-id="48ac4-159">Doručením (push) libovolný závislé stavu mimo samotné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="48ac4-160">Konfiguraci můžete nyní provést mimo rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="48ac4-161">Chyby při inicializaci pro závislé hodnoty nejsou pravděpodobně se projeví jako `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="48ac4-162">Rozhraní API je teď snazší testování.</span><span class="sxs-lookup"><span data-stu-id="48ac4-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="48ac4-163">Správa chyb</span><span class="sxs-lookup"><span data-stu-id="48ac4-163">Error management</span></span>

<span data-ttu-id="48ac4-164">Správa chyb v rozsáhlých systémů je složitá a odlišování zařízeními a neexistují žádné silver odrážky zajištění vašich systémů jsou odolné proti chybám a dobře se chovají.</span><span class="sxs-lookup"><span data-stu-id="48ac4-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="48ac4-165">Tyto pokyny byste měli nabízet podle pokynů uvedených v procházení tohoto obtížné prostoru.</span><span class="sxs-lookup"><span data-stu-id="48ac4-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="48ac4-166">Představují případy chyb a neplatný stav v typech, které jsou přirozené pro vaši doménu</span><span class="sxs-lookup"><span data-stu-id="48ac4-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="48ac4-167">S [Rozlišované sjednocení](../language-reference/discriminated-unions.md), F# vám dává možnost představující stav vadným programu v systému typů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="48ac4-168">Příklad:</span><span class="sxs-lookup"><span data-stu-id="48ac4-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="48ac4-169">V tomto případě existují tři způsoby známé, které zrušení peníze od bankovním účtu může selhat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="48ac4-170">Každý případ chyby je reprezentován v typu a mohou tedy řešit bezpečně v celém programu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="48ac4-171">Obecně platí, pokud různé způsoby, jak lze modelovat, že něco můžete **selhání** ve vaší doméně, pak kód pro zpracování chyb už se počítá jako něco musí čelit vedle regulární programu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="48ac4-172">Je jednoduše součástí normálního toku programu a nejsou považovány za **výjimečných**.</span><span class="sxs-lookup"><span data-stu-id="48ac4-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="48ac4-173">Existují dvě hlavní výhody tohoto:</span><span class="sxs-lookup"><span data-stu-id="48ac4-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="48ac4-174">Je snazší Údržba jako vaši doménu v průběhu času mění.</span><span class="sxs-lookup"><span data-stu-id="48ac4-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="48ac4-175">Případy chyb je snazší testování částí.</span><span class="sxs-lookup"><span data-stu-id="48ac4-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="48ac4-176">Použijte výjimky, pokud chyby nejde reprezentovat typy</span><span class="sxs-lookup"><span data-stu-id="48ac4-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="48ac4-177">Ne všechny chyby lze znázornit v doméně problému.</span><span class="sxs-lookup"><span data-stu-id="48ac4-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="48ac4-178">Tyto druhy chyb jsou *výjimečných* ze své podstaty, proto schopnost vyvolat a zaznamenat tak výjimky v F#.</span><span class="sxs-lookup"><span data-stu-id="48ac4-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="48ac4-179">Nejprve se doporučuje, abyste si přečetli [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="48ac4-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="48ac4-180">To platí také pro F#.</span><span class="sxs-lookup"><span data-stu-id="48ac4-180">These are also applicable to F#.</span></span>

<span data-ttu-id="48ac4-181">Vytvoří hlavní k dispozici v F# pro účely vyvolávání výjimek by měl být v následujícím pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="48ac4-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="48ac4-182">Funkce</span><span class="sxs-lookup"><span data-stu-id="48ac4-182">Function</span></span> | <span data-ttu-id="48ac4-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48ac4-183">Syntax</span></span> | <span data-ttu-id="48ac4-184">Účel</span><span class="sxs-lookup"><span data-stu-id="48ac4-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="48ac4-185">Vyvolá `System.ArgumentNullException` s názvem zadaného argumentu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="48ac4-186">Vyvolá `System.ArgumentException` s názvem zadaného argumentu a zprávy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="48ac4-187">Vyvolá `System.InvalidOperationException` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="48ac4-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="48ac4-188">Pro obecné účely mechanismus pro vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="48ac4-189">Vyvolá `System.Exception` se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="48ac4-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="48ac4-190">Vyvolá `System.Exception` a zobrazí se zpráva určená formátovací řetězec a jeho vstupů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="48ac4-191">Použití `nullArg`, `invalidArg` a `invalidOp` jako mechanismus pro vyvolání `ArgumentNullException`, `ArgumentException` a `InvalidOperationException` vhodných.</span><span class="sxs-lookup"><span data-stu-id="48ac4-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="48ac4-192">`failwith` a `failwithf` funkce by měla být obecně vyhnout, protože vyvolají základní `Exception` typ, ne určité výjimky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="48ac4-193">Jak je uvedeno [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md), chcete vyvolat více specifické výjimky, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="48ac4-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="48ac4-194">Pomocí syntaxe zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="48ac4-194">Using exception-handling syntax</span></span>

<span data-ttu-id="48ac4-195">F#podporuje vzory výjimky prostřednictvím `try...with` syntaxi:</span><span class="sxs-lookup"><span data-stu-id="48ac4-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="48ac4-196">Sjednocování funkci provést i v případě výjimku s porovnáváním vzorů může být trochu složité, pokud chcete zachovat čistý kód.</span><span class="sxs-lookup"><span data-stu-id="48ac4-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="48ac4-197">Jeden takový způsob, jak se o to postarají je použití [aktivní vzory](../language-reference/active-patterns.md) jako způsob, jak kolem s případem chyba s výjimkou samotné funkce skupiny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="48ac4-198">Může být například využívání rozhraní API, když dojde k výjimce, uzavře cenné informace v metadatech výjimky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="48ac4-199">Rozbalení užitečné hodnotu v těle Zachycenou výjimku uvnitř Active vzor a vrací hodnota může být užitečné v některých situacích.</span><span class="sxs-lookup"><span data-stu-id="48ac4-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="48ac4-200">Nepoužívejte monadic nahradit výjimky pro zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="48ac4-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="48ac4-201">Výjimky jsou považovány za poněkud taboo do funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="48ac4-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="48ac4-202">Ve skutečnosti výjimky porušují čistoty tak, aby byl bezpečně zvažovat je to docela není funkční.</span><span class="sxs-lookup"><span data-stu-id="48ac4-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="48ac4-203">Ale ve skutečnosti je množství kde musíte spustit kód a tohoto modulu runtime, které může dojít k chybám bude ignorovat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="48ac4-204">Obecně za předpokladu, že většinu toho, co jsou čistě ani celkový, chcete-li minimalizovat nepříjemným překvapením psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="48ac4-205">Je důležité vzít v úvahu následující základní výhody/aspekty výjimky s ohledem na jejich důležitosti a vhodnost v modulu runtime .NET a ekosystém mezi jazyky jako celku:</span><span class="sxs-lookup"><span data-stu-id="48ac4-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="48ac4-206">Obsahují podrobné diagnostické informace, které je velmi užitečné při ladění chyby.</span><span class="sxs-lookup"><span data-stu-id="48ac4-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="48ac4-207">Jsou dobře porozumí modul runtime a jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="48ac4-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="48ac4-208">Se může redukovat významné ve srovnání s kódem, který dostane mimo jeho způsob, jak *vyhnout* výjimky implementací určité dílčí sady z jejich sémantiku na základě ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="48ac4-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="48ac4-209">Tento třetí bod je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="48ac4-209">This third point is critical.</span></span> <span data-ttu-id="48ac4-210">Triviální složitých operací použití výjimky může vést k práci s struktury následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="48ac4-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="48ac4-211">Což může snadno způsobit křehké kód například porovnávání vzorů "stringly typu" chyby:</span><span class="sxs-lookup"><span data-stu-id="48ac4-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="48ac4-212">Kromě toho může být lákavé spolknout jakoukoliv výjimku v touhy "jednoduchý" funkce, která vrátí "nicer" typ:</span><span class="sxs-lookup"><span data-stu-id="48ac4-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="48ac4-213">Bohužel `tryReadAllText` může vyvolat množství výjimek, které jsou založené na řadu věcí, které může dojít v systému souborů a tento kód zahodí okamžitě žádné informace o co může ve skutečnosti být špatně ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="48ac4-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="48ac4-214">Pokud je tento kód nahradit typu výsledku, pak jste zpět "stringly typu" Chyba při analýze zprávy:</span><span class="sxs-lookup"><span data-stu-id="48ac4-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="48ac4-215">A umístění samotného objektu výjimky v `Error` konstruktor právě vynutí správně řešit typ výjimky v lokalitě volání, nikoli ve funkci.</span><span class="sxs-lookup"><span data-stu-id="48ac4-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="48ac4-216">To efektivně vytvoří výjimky kontrolovaný, kterých je známo, že unfun řešit jako volající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="48ac4-217">Dobrou alternativou výše uvedených příkladech se k zachycení *konkrétní* výjimky a vrácení smysluplné hodnoty v rámci této výjimky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="48ac4-218">Pokud změníte `tryReadAllText` následujícím způsobem funkci `None` má další význam:</span><span class="sxs-lookup"><span data-stu-id="48ac4-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="48ac4-219">Místo funguje jako pokrývající vše, tato funkce bude nyní správně zpracování případu, pokud soubor se nepovedlo najít a přiřadit tento význam pro vrácení.</span><span class="sxs-lookup"><span data-stu-id="48ac4-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="48ac4-220">Tuto hodnotu můžete namapovat na takovém Chyba při rušení žádné kontextové informace ani Vynucení volající řešit případ, který nemusí být od tohoto okamžiku v kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="48ac4-221">Typy, jako `Result<'Success, 'Error>` jsou vhodné pro základní operace, které nejsou vnořené, a F# doplňkové typy jsou ideální pro kdy představující něco může buď vrátit *něco* nebo *nic*.</span><span class="sxs-lookup"><span data-stu-id="48ac4-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="48ac4-222">Nejsou náhradou za výjimky, ale a neměl by se při pokusu o nahradit výjimky.</span><span class="sxs-lookup"><span data-stu-id="48ac4-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="48ac4-223">Místo toho se musí uplatnit uvážlivě na adresu specifických aspektů výjimky a chybové zásady správy cílové způsoby.</span><span class="sxs-lookup"><span data-stu-id="48ac4-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="48ac4-224">Částečné použití argumentů a bodu bez programování</span><span class="sxs-lookup"><span data-stu-id="48ac4-224">Partial application and point-free programming</span></span>

<span data-ttu-id="48ac4-225">F#podporuje částečné použití argumentů a proto různé způsoby, jak program ve stylu bez bodu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="48ac4-226">To může být užitečné pro opakované využívání kódu v rámci modulu nebo provádění něco, ale není obvykle něco, co je veřejně zpřístupnit.</span><span class="sxs-lookup"><span data-stu-id="48ac4-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="48ac4-227">Obecně platí bodu bez programování není důsledku v a sám sebe a můžete přidat kognitivní významnou překážkou pro uživatele, kteří nejsou ponoří ve stylu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="48ac4-228">Nepoužívejte částečné použití argumentů a curryfikace ve veřejných rozhraní API</span><span class="sxs-lookup"><span data-stu-id="48ac4-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="48ac4-229">S výjimkou malý použití částečné použití argumentů ve veřejných rozhraní API může být matoucí pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="48ac4-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="48ac4-230">Obvykle `let`-vázán hodnoty v F# kódu jsou **hodnoty**, nikoli **funkce hodnoty**.</span><span class="sxs-lookup"><span data-stu-id="48ac4-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="48ac4-231">Kombinace společně hodnoty a hodnoty funkcí může vést k uložení malý počet řádků kódu výměnou za hodně nemuseli jsme se zdržovat, zejména v případě, že v kombinaci s operátory, jako `>>` sestavit funkce.</span><span class="sxs-lookup"><span data-stu-id="48ac4-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="48ac4-232">Zvažte případné dopady nástroje bodu bez programování</span><span class="sxs-lookup"><span data-stu-id="48ac4-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="48ac4-233">Curryfikované funkce neoznačuje popiskem svých argumentů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="48ac4-234">Tato akce nemá vliv nástrojů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-234">This has tooling implications.</span></span> <span data-ttu-id="48ac4-235">Vezměte v úvahu tyto dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="48ac4-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="48ac4-236">Obě jsou platná funkce, ale `funcWithApplication` curryfikované funkce.</span><span class="sxs-lookup"><span data-stu-id="48ac4-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="48ac4-237">Když najedete myší jejich typy v editoru, uvidíte toto:</span><span class="sxs-lookup"><span data-stu-id="48ac4-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="48ac4-238">V lokalitě volání popisků v nástroje, jako je Visual Studio vám neposkytne smysluplné informace o tom, co `string` a `int` ve skutečnosti představují vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="48ac4-239">Pokud narazíte na kódu bez bodu jako `funcWithApplication` , který je veřejně použitelné, doporučuje se provést plnou expanzí η tak, aby nástrojů můžete vybrat až dále smysluplné názvy argumentů.</span><span class="sxs-lookup"><span data-stu-id="48ac4-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="48ac4-240">Kromě toho ladění kódu bez bod může být náročné, pokud není možné.</span><span class="sxs-lookup"><span data-stu-id="48ac4-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="48ac4-241">Ladicí nástroje spoléhají na hodnoty, které jsou vázány na názvy (například `let` vazby) tak, aby si mohli prohlédnout hodnoty, ležící polovině spuštění.</span><span class="sxs-lookup"><span data-stu-id="48ac4-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="48ac4-242">Pokud váš kód neobsahuje žádné hodnoty ke kontrole, není nutné nic ladění.</span><span class="sxs-lookup"><span data-stu-id="48ac4-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="48ac4-243">V budoucnu, nástroje pro ladění může vyvíjet tak, aby odpovídaly tyto hodnoty na základě dříve provedený cest, ale není vhodné zajistila vaše sázka na *potenciální* ladění funkcí.</span><span class="sxs-lookup"><span data-stu-id="48ac4-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="48ac4-244">Vezměte v úvahu částečné použití argumentů jako technika na interní redukovat</span><span class="sxs-lookup"><span data-stu-id="48ac4-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="48ac4-245">Na rozdíl od předchozího bodu částečné použití argumentů je skvělý nástroj pro snížení často používaný v rámci aplikace nebo interní podrobnější informace o rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="48ac4-246">Může být užitečné při provádění složitějších rozhraní API, kde je často používaný text často problémy řešit testování částí.</span><span class="sxs-lookup"><span data-stu-id="48ac4-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="48ac4-247">Například následující kód ukazuje, jak dosáhnout co nejvíce napodobování architektury získáte bez nutnosti přepínat externí závislost na těchto rozhraní a nemusíte se učit se souvisejícím sled prací rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48ac4-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="48ac4-248">Představte si třeba následující topografie řešení:</span><span class="sxs-lookup"><span data-stu-id="48ac4-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` <span data-ttu-id="48ac4-249">kód může zveřejnit jako například:</span><span class="sxs-lookup"><span data-stu-id="48ac4-249">might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="48ac4-250">Testování částí `Transactions.doTransaction` v `ImplementationLogic.Tests.fspoj` snadno:</span><span class="sxs-lookup"><span data-stu-id="48ac4-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="48ac4-251">Částečně použití `doTransaction` napodobování kontextu objektu umožňuje volání funkce ve všech testování částí, aniž by bylo nutné vytvořit imitaci kontextu pokaždé, když:</span><span class="sxs-lookup"><span data-stu-id="48ac4-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="48ac4-252">Tento postup neměl být všeobecně aplikován na celém základu kódu, ale je dobrým způsobem, jak redukovat pro složité interní informace a tyto interní informace o testování částí.</span><span class="sxs-lookup"><span data-stu-id="48ac4-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="48ac4-253">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="48ac4-253">Access control</span></span>

<span data-ttu-id="48ac4-254">F#má více možností pro [řízení přístupu](../language-reference/access-control.md), zděděné z co je k dispozici v modulu .NET runtime.</span><span class="sxs-lookup"><span data-stu-id="48ac4-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="48ac4-255">Ty nejsou použitelné pouze pro typy – můžete využít pro funkce je moc.</span><span class="sxs-lookup"><span data-stu-id="48ac4-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="48ac4-256">Preferovat jinou hodnotu než`public` typy a členy, dokud nebudete potřebovat, aby to byla veřejně použitelné.</span><span class="sxs-lookup"><span data-stu-id="48ac4-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="48ac4-257">Tím se minimalizují také jaké několik příjemců do.</span><span class="sxs-lookup"><span data-stu-id="48ac4-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="48ac4-258">Přitom se snaží zachovat všechny funkce pomocné rutiny `private`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="48ac4-259">Zvažte použití `[<AutoOpen>]` v privátní modulu pomocné funkce, pokud budou mnoho.</span><span class="sxs-lookup"><span data-stu-id="48ac4-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="48ac4-260">Odvození typu proměnné a obecné typy</span><span class="sxs-lookup"><span data-stu-id="48ac4-260">Type inference and generics</span></span>

<span data-ttu-id="48ac4-261">Odvození typu proměnné můžete uložit z psát spoustu často používaný text.</span><span class="sxs-lookup"><span data-stu-id="48ac4-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="48ac4-262">Automatická Generalizace v a F# kompilátoru vám umožňují napsat obecnějším kód s téměř žádná práce navíc z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="48ac4-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="48ac4-263">Tyto funkce však nejsou univerzálně dobré.</span><span class="sxs-lookup"><span data-stu-id="48ac4-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="48ac4-264">Vezměte v úvahu názvy argumentů značení s explicitní typy ve veřejných rozhraní API a nespoléhejte na odvození typu proměnné pro tuto.</span><span class="sxs-lookup"><span data-stu-id="48ac4-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="48ac4-265">Důvodem je, že **vám** by měl být kontrolu nad tvar vaše rozhraní API, není kompilátor.</span><span class="sxs-lookup"><span data-stu-id="48ac4-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="48ac4-266">Ačkoli kompilátor může provést úlohu pořádku v odvození typů za vás, je možné mít tvar změny rozhraní API, pokud se změnily interní informace, které spoléhá na typy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="48ac4-267">To může být žádoucí, ale je téměř jistě způsobí narušující změně rozhraní API se pak bude mít podřízené příjemci.</span><span class="sxs-lookup"><span data-stu-id="48ac4-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="48ac4-268">Místo toho pokud explicitně určit tvar objektu veřejné rozhraní API, pak můžete určit tyto nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="48ac4-269">V podmínkách DDD to můžete představit jako vrstvu odolnou proti poškození.</span><span class="sxs-lookup"><span data-stu-id="48ac4-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="48ac4-270">Zvažte smysluplný název k obecným argumentům.</span><span class="sxs-lookup"><span data-stu-id="48ac4-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="48ac4-271">Pokud píšete skutečně obecný kód, který není specifická pro konkrétní domény, výstižný název může pomoci ostatním programátorům principy, které pracují v doméně.</span><span class="sxs-lookup"><span data-stu-id="48ac4-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="48ac4-272">Například parametr typu s názvem `'Document` v kontextu interakci s dokumentem databáze zvýší jeho srozumitelnost, že typy obecného dokumentu může přijmout funkce nebo člen pracujete.</span><span class="sxs-lookup"><span data-stu-id="48ac4-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="48ac4-273">Vezměte v úvahu názvy parametrů obecného typu pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="48ac4-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="48ac4-274">Toto je hlavní způsob, jak k provádění akcí v .NET, proto se doporučuje použít PascalCase spíše než formátu snake_case nebo camelCase.</span><span class="sxs-lookup"><span data-stu-id="48ac4-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="48ac4-275">A konečně, automatická generalizace není vždy skvělým nástrojem pro uživatele, kteří začínají s F# nebo velký základ kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="48ac4-276">V používání komponent, které jsou obecné, je nemuseli jsme se zdržovat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="48ac4-277">Kromě toho pokud automaticky obecné funkce nejsou použity s různými typy vstupu (umožňují samostatně, pokud jsou určeny pro použití jako takový), pak neexistuje žádné skutečné výhody je právě obecný od tohoto okamžiku v čase.</span><span class="sxs-lookup"><span data-stu-id="48ac4-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="48ac4-278">Vždy zvažte, pokud kód, který píšete se skutečně přínosné obecný.</span><span class="sxs-lookup"><span data-stu-id="48ac4-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="48ac4-279">Výkon</span><span class="sxs-lookup"><span data-stu-id="48ac4-279">Performance</span></span>

<span data-ttu-id="48ac4-280">F#hodnoty jsou neměnné ve výchozím nastavení, což vám umožní vyhnout určité třídy chyb (zejména těchto zahrnující souběžnosti a paralelismu).</span><span class="sxs-lookup"><span data-stu-id="48ac4-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="48ac4-281">Ale v některých případech, tak, abyste dosáhli optimálního (nebo dokonce přiměřené) účinnosti doba provádění nebo přidělení paměti, rozsah práce může nejlépe dají implementovat pomocí místní mutace stavu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="48ac4-282">To je možné v základu vyjádření souhlasu s F# s `mutable` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="48ac4-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="48ac4-283">Nicméně použití `mutable` v F# mohou mít pocit rozporu s funkční čistoty.</span><span class="sxs-lookup"><span data-stu-id="48ac4-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="48ac4-284">To je v pořádku, pokud nastavíte očekávání z čistoty [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="48ac4-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="48ac4-285">Referenční transparentnost – ne čistoty - je cílem při zápisu F# funkce.</span><span class="sxs-lookup"><span data-stu-id="48ac4-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="48ac4-286">To umožňuje psaní funkční rozhraní průběhu na základě mutace implementace výkonu kritického kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="48ac4-287">Zabalení proměnlivé kód v neměnných rozhraní</span><span class="sxs-lookup"><span data-stu-id="48ac4-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="48ac4-288">S referenční transparentnosti jako cíl je velmi důležité napsat kód, který nemůže vystavovat proměnlivé underbelly kritickém pro výkon funkce.</span><span class="sxs-lookup"><span data-stu-id="48ac4-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="48ac4-289">Například následující kód implementuje `Array.contains` fungovat v F# základní knihovny:</span><span class="sxs-lookup"><span data-stu-id="48ac4-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="48ac4-290">Volání této funkce více než jednou podkladové pole nezmění, ani je potřeba, aby vám spravovat jakékoli proměnlivý stav v její použití.</span><span class="sxs-lookup"><span data-stu-id="48ac4-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="48ac4-291">Referentially transparentní, je i v případě, téměř každý jednotlivý řádek kódu v rámci něj používá mutace.</span><span class="sxs-lookup"><span data-stu-id="48ac4-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="48ac4-292">Vezměte v úvahu zapouzdření proměnlivé datové ve třídách</span><span class="sxs-lookup"><span data-stu-id="48ac4-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="48ac4-293">Předchozí příklad použil jedné funkce k zapouzdření pomocí proměnlivé datové operace.</span><span class="sxs-lookup"><span data-stu-id="48ac4-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="48ac4-294">To není vždy dostatečná pro složitější datových sad.</span><span class="sxs-lookup"><span data-stu-id="48ac4-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="48ac4-295">Vezměte v úvahu následující sady funkcí:</span><span class="sxs-lookup"><span data-stu-id="48ac4-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="48ac4-296">Tento kód je výkonné, ale zveřejňuje na základě mutace datová struktura, že volající zodpovídají za údržbu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="48ac4-297">To může být zabaleny uvnitř třídy bez základní členů, které můžete změnit:</span><span class="sxs-lookup"><span data-stu-id="48ac4-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

`Closure1Table` <span data-ttu-id="48ac4-298">zapouzdřuje základní na základě mutace datové struktury, a tím nevynucuje volající k údržbě základní datová struktura.</span><span class="sxs-lookup"><span data-stu-id="48ac4-298">encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="48ac4-299">Třídy jsou efektivní způsob, jak zapouzdřit dat a postupy, které jsou založeny na mutace bez vystavení podrobnosti o volajícím.</span><span class="sxs-lookup"><span data-stu-id="48ac4-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="48ac4-300">Preferovat `let mutable` na odkazové buňky</span><span class="sxs-lookup"><span data-stu-id="48ac4-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="48ac4-301">Odkazové buňky jsou způsob, jak reprezentaci odkaz na hodnotu než samotná hodnota.</span><span class="sxs-lookup"><span data-stu-id="48ac4-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="48ac4-302">I když mohou být použity pro kód kritickém pro výkon, se obecně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="48ac4-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="48ac4-303">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="48ac4-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="48ac4-304">Použít odkazovou buňku nyní "zahltí" všechny následné kódu pomocí museli přistoupit přes ukazatel a znovu odkazují na podkladová data.</span><span class="sxs-lookup"><span data-stu-id="48ac4-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="48ac4-305">Místo toho zvažte `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="48ac4-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="48ac4-306">Kromě jediný bod mutace uprostřed výraz lambda, všechny ostatní kód, který se dotýká `acc` můžete udělat tak, aby se nijak neliší použití normální `let`-hranice neměnné hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="48ac4-307">To bude usnadňují v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="48ac4-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="48ac4-308">Objekt programování</span><span class="sxs-lookup"><span data-stu-id="48ac4-308">Object programming</span></span>

<span data-ttu-id="48ac4-309">F#obsahuje plnou podporu pro objekty a objektově orientované koncepty (zálohy).</span><span class="sxs-lookup"><span data-stu-id="48ac4-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="48ac4-310">I když mnohé koncepty zálohy jsou výkonné a užitečné, některé z nich jsou ideální pro použití.</span><span class="sxs-lookup"><span data-stu-id="48ac4-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="48ac4-311">Následující seznamy nabízí pokyny k kategorie funkcí zálohy na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="48ac4-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

**<span data-ttu-id="48ac4-312">Zvažte použití těchto funkcí v mnoha situacích:</span><span class="sxs-lookup"><span data-stu-id="48ac4-312">Consider using these features in many situations:</span></span>**

* <span data-ttu-id="48ac4-313">Zápisu s tečkou (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="48ac4-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="48ac4-314">Členy instance</span><span class="sxs-lookup"><span data-stu-id="48ac4-314">Instance members</span></span>
* <span data-ttu-id="48ac4-315">Implicitní konstruktory</span><span class="sxs-lookup"><span data-stu-id="48ac4-315">Implicit constructors</span></span>
* <span data-ttu-id="48ac4-316">Statické členy</span><span class="sxs-lookup"><span data-stu-id="48ac4-316">Static members</span></span>
* <span data-ttu-id="48ac4-317">Notace indexeru (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="48ac4-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="48ac4-318">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="48ac4-318">Named and Optional arguments</span></span>
* <span data-ttu-id="48ac4-319">Rozhraní a implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="48ac4-319">Interfaces and interface implementations</span></span>

**<span data-ttu-id="48ac4-320">Nedostanou pro účely těchto funkcí nejprve, ale uvážlivě je použije, pokud jsou vhodné k vyřešení problému:</span><span class="sxs-lookup"><span data-stu-id="48ac4-320">Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:</span></span>**

* <span data-ttu-id="48ac4-321">Přetěžování metody</span><span class="sxs-lookup"><span data-stu-id="48ac4-321">Method overloading</span></span>
* <span data-ttu-id="48ac4-322">Zapouzdřené proměnlivé datové</span><span class="sxs-lookup"><span data-stu-id="48ac4-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="48ac4-323">Operátory pro typy</span><span class="sxs-lookup"><span data-stu-id="48ac4-323">Operators on types</span></span>
* <span data-ttu-id="48ac4-324">Automatické vlastnosti</span><span class="sxs-lookup"><span data-stu-id="48ac4-324">Auto properties</span></span>
* <span data-ttu-id="48ac4-325">Implementace `IDisposable` a</span><span class="sxs-lookup"><span data-stu-id="48ac4-325">Implementing `IDisposable` and</span></span> `IEnumerable`
* <span data-ttu-id="48ac4-326">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="48ac4-326">Type extensions</span></span>
* <span data-ttu-id="48ac4-327">Události</span><span class="sxs-lookup"><span data-stu-id="48ac4-327">Events</span></span>
* <span data-ttu-id="48ac4-328">Struktury</span><span class="sxs-lookup"><span data-stu-id="48ac4-328">Structs</span></span>
* <span data-ttu-id="48ac4-329">Delegáty</span><span class="sxs-lookup"><span data-stu-id="48ac4-329">Delegates</span></span>
* <span data-ttu-id="48ac4-330">Výčty</span><span class="sxs-lookup"><span data-stu-id="48ac4-330">Enums</span></span>

**<span data-ttu-id="48ac4-331">Pokud je nutné použít obecně nepoužívejte tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="48ac4-331">Generally avoid these features unless you must use them:</span></span>**

* <span data-ttu-id="48ac4-332">Hierarchie dědičnosti na základě typu a implementaci dědičnosti</span><span class="sxs-lookup"><span data-stu-id="48ac4-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="48ac4-333">Hodnoty Null a</span><span class="sxs-lookup"><span data-stu-id="48ac4-333">Nulls and</span></span> `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="48ac4-334">Preferovat složení prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="48ac4-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="48ac4-335">[Složení prostřednictvím dědičnosti](https://en.wikipedia.org/wiki/Composition_over_inheritance) je to dobrá dlouhotrvající idiom F# kódu můžete dodržovat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="48ac4-336">Základním principem je, že by neměla vystavit základní třídu a vynutit volající dědit ze základní třídy pro funkce.</span><span class="sxs-lookup"><span data-stu-id="48ac4-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="48ac4-337">Můžete implementovat rozhraní, pokud už nepotřebujete třídu objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="48ac4-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="48ac4-338">[Výrazy objektu](../language-reference/object-expressions.md) vám umožňují v reálném čase, implementovat rozhraní implementované rozhraní vazby na hodnotu bez nutnosti učinit uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="48ac4-339">To se může hodit, zejména v případě můžete _pouze_ musí implementovat rozhraní a nepotřebujete úplné třídy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="48ac4-340">Například tady je kód, který běží v [Ionide](http://ionide.io/) poskytnout akce opravy kódu, pokud jste přidali symbol, který není nutné `open` příkaz pro:</span><span class="sxs-lookup"><span data-stu-id="48ac4-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="48ac4-341">Protože není nutné pro třídu při práci s kódem API sady Visual Studio, objektové výrazy jsou ideální nástroj pro tento.</span><span class="sxs-lookup"><span data-stu-id="48ac4-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="48ac4-342">Jsou také užitečná pro testování částí, pokud chcete zástupných procedur na rozhraní s testovací rutiny ad hoc způsobem.</span><span class="sxs-lookup"><span data-stu-id="48ac4-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="48ac4-343">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="48ac4-343">Type Abbreviations</span></span>

<span data-ttu-id="48ac4-344">[Typ – zkratky](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit popisek k jinému typu, jako je například podpis funkce nebo více komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="48ac4-345">Například následující alias přiřadí popisek co je potřeba definovat výpočet s [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), obsáhlý learning knihovny:</span><span class="sxs-lookup"><span data-stu-id="48ac4-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="48ac4-346">`Computation` Jmenuje pohodlný způsob, jak označit všechny funkce, která odpovídá podpisu je aliasing.</span><span class="sxs-lookup"><span data-stu-id="48ac4-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="48ac4-347">Použití zkratky typů tímto způsobem je vhodné a umožňuje stručnější kódu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="48ac4-348">Vyhněte se použití zkratky typů k vyjádření vaší domény</span><span class="sxs-lookup"><span data-stu-id="48ac4-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="48ac4-349">I když zkratky typů jsou vhodné pro poskytnutí názvu podpisech funkcí, mohou být matoucí při zkrácený zápis parametru jiné typy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="48ac4-350">Vezměte v úvahu tato zkratka:</span><span class="sxs-lookup"><span data-stu-id="48ac4-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="48ac4-351">To může být matoucí několika různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="48ac4-351">This can be confusing in multiple ways:</span></span>

* `BufferSize` <span data-ttu-id="48ac4-352">není abstrakci; je právě jiný název pro celé číslo.</span><span class="sxs-lookup"><span data-stu-id="48ac4-352">is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="48ac4-353">Pokud `BufferSize` je přístupný ve veřejném rozhraní API, se můžete snadno dojít k nesprávné interpretaci znamená více než jen `int`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="48ac4-354">Obecně platí, typy domén mít víc atributů k nim a nejsou primitivními typy jako `int`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="48ac4-355">Tato zkratka je v rozporu tento předpoklad.</span><span class="sxs-lookup"><span data-stu-id="48ac4-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="48ac4-356">Použití malých a velkých `BufferSize` (PascalCase) znamená, že tento typ obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="48ac4-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="48ac4-357">Tento alias se nebude poskytovat lepší čitelnosti ve srovnání s poskytováním pojmenovaný argument pro funkci.</span><span class="sxs-lookup"><span data-stu-id="48ac4-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="48ac4-358">Zkratka neprojeví v kompilovaných IL; je pouze celé číslo a tento alias je konstrukce za kompilace.</span><span class="sxs-lookup"><span data-stu-id="48ac4-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="48ac4-359">Stručně řečeno, trávení s zkratky typů je, že jsou **není** abstrakce typy jsou zkrácený zápis parametru.</span><span class="sxs-lookup"><span data-stu-id="48ac4-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="48ac4-360">V předchozím příkladu `BufferSize` je právě `int` skrytě se žádná další data ani žádné výhody z typu systému kromě co `int` už má.</span><span class="sxs-lookup"><span data-stu-id="48ac4-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
