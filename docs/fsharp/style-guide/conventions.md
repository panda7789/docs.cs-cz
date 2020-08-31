---
title: Zásady kódování jazyka F#
description: 'Seznamte se s obecnými pokyny a idiomy při psaní kódu F #.'
ms.date: 01/15/2020
ms.openlocfilehash: 748a9c26794f46dcc67fdcfcf21f41847a462a19
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053008"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="89e46-103">Zásady kódování jazyka F#</span><span class="sxs-lookup"><span data-stu-id="89e46-103">F# coding conventions</span></span>

<span data-ttu-id="89e46-104">Následující konvence jsou formulované z prostředí, které pracuje s velkými základem kódu jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="89e46-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="89e46-105">[Pět principů dobrého kódu F #](index.md#five-principles-of-good-f-code) je základem každého doporučení.</span><span class="sxs-lookup"><span data-stu-id="89e46-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="89e46-106">Vztahují se k [pokynům pro návrh součástí f #](component-design-guidelines.md), ale platí pro jakýkoliv kód f #, nikoli jenom na komponenty, jako jsou knihovny.</span><span class="sxs-lookup"><span data-stu-id="89e46-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="89e46-107">Uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="89e46-107">Organizing code</span></span>

<span data-ttu-id="89e46-108">F # nabízí dva hlavní způsoby uspořádání kódu: moduly a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="89e46-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="89e46-109">Jsou podobné, ale mají následující rozdíly:</span><span class="sxs-lookup"><span data-stu-id="89e46-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="89e46-110">Obory názvů jsou kompilovány jako obory názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="89e46-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="89e46-111">Moduly jsou kompilovány jako statické třídy.</span><span class="sxs-lookup"><span data-stu-id="89e46-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="89e46-112">Obory názvů jsou vždycky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="89e46-112">Namespaces are always top level.</span></span> <span data-ttu-id="89e46-113">Moduly můžou být na nejvyšší úrovni a vnořené v jiných modulech.</span><span class="sxs-lookup"><span data-stu-id="89e46-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="89e46-114">Obory názvů můžou zahrnovat víc souborů.</span><span class="sxs-lookup"><span data-stu-id="89e46-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="89e46-115">Moduly se nedají.</span><span class="sxs-lookup"><span data-stu-id="89e46-115">Modules cannot.</span></span>
* <span data-ttu-id="89e46-116">Moduly lze dekorovat pomocí `[<RequireQualifiedAccess>]` a `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="89e46-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="89e46-117">Následující pokyny vám pomohou s jejich použitím k uspořádání kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="89e46-118">Preferovat obory názvů na nejvyšší úrovni</span><span class="sxs-lookup"><span data-stu-id="89e46-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="89e46-119">Pro veškerý veřejně spotřební kód jsou obory názvů pro moduly na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="89e46-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="89e46-120">Protože jsou kompilovány jako obory názvů .NET, jsou spotřební z jazyka C# bez problémů.</span><span class="sxs-lookup"><span data-stu-id="89e46-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="89e46-121">Použití modulu nejvyšší úrovně se nemusí zobrazovat jinak, když se volá jenom z F #, ale pro příjemce v jazyce C# můžou být volajícím schopni kvalifikovat `MyClass` `MyCode` modulem.</span><span class="sxs-lookup"><span data-stu-id="89e46-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="89e46-122">Pečlivě použít `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="89e46-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="89e46-123">`[<AutoOpen>]`Konstrukce může znehodnotit rozsah toho, co je k dispozici volajícím a odpověď na místo, kde je něco z něj "Magic".</span><span class="sxs-lookup"><span data-stu-id="89e46-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="89e46-124">Nejedná se o dobrou věc.</span><span class="sxs-lookup"><span data-stu-id="89e46-124">This is not a good thing.</span></span> <span data-ttu-id="89e46-125">Výjimkou z tohoto pravidla je samotné základní knihovna F # (i když je tento fakt také bitová kontroverzním).</span><span class="sxs-lookup"><span data-stu-id="89e46-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="89e46-126">Je to ale pohodlí, pokud máte pomocnou funkci pro veřejné rozhraní API, které chcete uspořádat odděleně od tohoto veřejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="89e46-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="89e46-127">To umožňuje čistě oddělit podrobnosti implementace z veřejného rozhraní API funkce bez nutnosti úplného vyřazení pomocné rutiny pokaždé, když ji zavoláte.</span><span class="sxs-lookup"><span data-stu-id="89e46-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="89e46-128">Kromě toho může být vystavení rozšiřujících metod a tvůrců výrazů na úrovni oboru názvů začínat pomocí `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="89e46-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="89e46-129">Použijte `[<RequireQualifiedAccess>]` vždy, když by mohlo dojít ke konfliktu názvů, nebo pokud se vám podaří s čitelností.</span><span class="sxs-lookup"><span data-stu-id="89e46-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="89e46-130">Přidání `[<RequireQualifiedAccess>]` atributu do modulu znamená, že modul nemůže být otevřen a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup.</span><span class="sxs-lookup"><span data-stu-id="89e46-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="89e46-131">`Microsoft.FSharp.Collections.List`Modul má například tento atribut.</span><span class="sxs-lookup"><span data-stu-id="89e46-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="89e46-132">To je užitečné v případě, že funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v jiných modulech.</span><span class="sxs-lookup"><span data-stu-id="89e46-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="89e46-133">Vyžadování kvalifikovaného přístupu může značně prodloužit dlouhodobou udržovatelnost a možnost využití knihovny.</span><span class="sxs-lookup"><span data-stu-id="89e46-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="89e46-134">`open`Topologické řazení příkazů</span><span class="sxs-lookup"><span data-stu-id="89e46-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="89e46-135">V jazyce F # se jedná o pořadí deklarací, včetně `open` příkazů.</span><span class="sxs-lookup"><span data-stu-id="89e46-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="89e46-136">To je na rozdíl od jazyka C#, kde účinek `using` a `using static` je nezávislé na řazení těchto příkazů v souboru.</span><span class="sxs-lookup"><span data-stu-id="89e46-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="89e46-137">V F # prvky otevřené do oboru mohou stíny, které jsou již přítomny, jiné.</span><span class="sxs-lookup"><span data-stu-id="89e46-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="89e46-138">To znamená, že `open` příkazy změny pořadí mohou změnit význam kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="89e46-139">V důsledku toho se nedoporučuje jakékoli třídění všech `open` příkazů (například alfanumerické), lest vygenerujete různé chování, které byste mohli očekávat.</span><span class="sxs-lookup"><span data-stu-id="89e46-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="89e46-140">Místo toho doporučujeme, abyste je seřadili [Topologicky](https://en.wikipedia.org/wiki/Topological_sorting). To znamená, že příkazy budou seřazeny `open` v pořadí, ve kterém jsou definovány _vrstvy_ systému.</span><span class="sxs-lookup"><span data-stu-id="89e46-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="89e46-141">Je také možné zvážit alfanumerické řazení v různých topologických vrstvách.</span><span class="sxs-lookup"><span data-stu-id="89e46-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="89e46-142">Tady je příklad topologické řazení pro veřejný soubor rozhraní API služby kompilátoru F #:</span><span class="sxs-lookup"><span data-stu-id="89e46-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open FSharp.Compiler
open FSharp.Compiler.AbstractIL
open FSharp.Compiler.AbstractIL.Diagnostics
open FSharp.Compiler.AbstractIL.IL
open FSharp.Compiler.AbstractIL.ILBinaryReader
open FSharp.Compiler.AbstractIL.Internal
open FSharp.Compiler.AbstractIL.Internal.Library

open FSharp.Compiler.AccessibilityLogic
open FSharp.Compiler.Ast
open FSharp.Compiler.CompileOps
open FSharp.Compiler.CompileOptions
open FSharp.Compiler.Driver

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="89e46-143">Všimněte si, že zalomení řádku odděluje topologické vrstvy s každou vrstvou, která je následně tříděna.</span><span class="sxs-lookup"><span data-stu-id="89e46-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="89e46-144">Tím se čistě organizují kód bez náhodných hodnot stínování.</span><span class="sxs-lookup"><span data-stu-id="89e46-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="89e46-145">Použití tříd k zahrnutí hodnot, které mají vedlejší účinky</span><span class="sxs-lookup"><span data-stu-id="89e46-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="89e46-146">Při inicializaci hodnoty může mít vedlejší účinky, jako je například vytvoření instance kontextu databáze nebo jiného vzdáleného prostředku, existuje mnoho času.</span><span class="sxs-lookup"><span data-stu-id="89e46-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="89e46-147">Nachází se na inicializaci takových věcí v modulu a jejich použití v následujících funkcích:</span><span class="sxs-lookup"><span data-stu-id="89e46-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="89e46-148">To je často špatný nápad z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="89e46-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="89e46-149">Nejprve je konfigurace aplikace vložena do základu kódu pomocí `dep1` a `dep2` .</span><span class="sxs-lookup"><span data-stu-id="89e46-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="89e46-150">To je obtížné udržovat ve větších základech kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="89e46-151">Druhá, staticky inicializovaná data by neměla zahrnovat hodnoty, které nejsou bezpečné pro přístup z více vláken, pokud vaše komponenta sám použije více vláken.</span><span class="sxs-lookup"><span data-stu-id="89e46-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="89e46-152">To je jasně narušeno `dep3` .</span><span class="sxs-lookup"><span data-stu-id="89e46-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="89e46-153">Nakonec se inicializace modulu zkompiluje do statického konstruktoru pro celou jednotku kompilace.</span><span class="sxs-lookup"><span data-stu-id="89e46-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="89e46-154">Pokud dojde k nějaké chybě v inicializaci hodnoty s vazbou v tomto modulu, manifestuje se jako `TypeInitializationException` , který je poté ukládán do mezipaměti pro celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e46-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="89e46-155">To může být obtížné diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="89e46-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="89e46-156">Obvykle se jedná o vnitřní výjimku, kterou se můžete pokusit o důvod, ale pokud tam není, neoznamuje to, co je hlavní příčina.</span><span class="sxs-lookup"><span data-stu-id="89e46-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="89e46-157">Místo toho stačí použít jednoduchou třídu pro uchování závislostí:</span><span class="sxs-lookup"><span data-stu-id="89e46-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="89e46-158">To umožňuje následující:</span><span class="sxs-lookup"><span data-stu-id="89e46-158">This enables the following:</span></span>

1. <span data-ttu-id="89e46-159">Vložení libovolného závislého stavu mimo samotné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="89e46-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="89e46-160">Konfigurace se teď dá udělat mimo rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="89e46-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="89e46-161">Chyby při inicializaci závislých hodnot se nejspíš nemanifestují jako `TypeInitializationException` .</span><span class="sxs-lookup"><span data-stu-id="89e46-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="89e46-162">Rozhraní API je teď snadněji vyzkoušené.</span><span class="sxs-lookup"><span data-stu-id="89e46-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="89e46-163">Správa chyb</span><span class="sxs-lookup"><span data-stu-id="89e46-163">Error management</span></span>

<span data-ttu-id="89e46-164">Správa chyb ve velkých systémech je složitá a odlišitá Endeavor a neexistují žádné stříbrné odrážky v tom, že vaše systémy jsou odolné proti chybám a chovají se dobře.</span><span class="sxs-lookup"><span data-stu-id="89e46-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="89e46-165">Následující pokyny by měly nabízet pokyny k tomu, aby se tento obtížný prostor přecházeníly.</span><span class="sxs-lookup"><span data-stu-id="89e46-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="89e46-166">Reprezentuje chybové případy a neplatný stav ve vnitřních typech pro vaši doménu.</span><span class="sxs-lookup"><span data-stu-id="89e46-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="89e46-167">Díky [rozlišeným sjednocením](../language-reference/discriminated-unions.md)vám jazyk F # umožní znázornit chybný stav programu v systému typů.</span><span class="sxs-lookup"><span data-stu-id="89e46-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="89e46-168">Příklad:</span><span class="sxs-lookup"><span data-stu-id="89e46-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="89e46-169">V tomto případě existují tři známé způsoby, jak se odeberou peníze z bankovního účtu, může selhat.</span><span class="sxs-lookup"><span data-stu-id="89e46-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="89e46-170">Jednotlivé chybové případy jsou reprezentovány v typu a lze je proto v rámci programu bezpečně zařídit.</span><span class="sxs-lookup"><span data-stu-id="89e46-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="89e46-171">Obecně platí, že pokud můžete modelovat různé způsoby, které může něco v doméně **selhat** , pak se kód pro zpracování chyb už nepovažuje za něco, co je potřeba řešit Kromě pravidelného toku programu.</span><span class="sxs-lookup"><span data-stu-id="89e46-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="89e46-172">Je jenom součástí normálního toku programu a nepovažuje se za **výjimečné**.</span><span class="sxs-lookup"><span data-stu-id="89e46-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="89e46-173">Existují dvě hlavní výhody:</span><span class="sxs-lookup"><span data-stu-id="89e46-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="89e46-174">Údržba se v průběhu času mění v rámci domény.</span><span class="sxs-lookup"><span data-stu-id="89e46-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="89e46-175">Chybové případy jsou snazší pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="89e46-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="89e46-176">Použít výjimky v případě, že chyby nemohou být reprezentovány s typy</span><span class="sxs-lookup"><span data-stu-id="89e46-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="89e46-177">Ne všechny chyby mohou být reprezentovány v doméně problému.</span><span class="sxs-lookup"><span data-stu-id="89e46-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="89e46-178">Tyto druhy chyb jsou *výjimečné* povahy, takže schopnost vyvolat a zachytit výjimky v F #.</span><span class="sxs-lookup"><span data-stu-id="89e46-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="89e46-179">Nejprve doporučujeme, abyste si přečetli [pokyny pro návrh výjimek](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="89e46-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="89e46-180">Tyto podmínky se vztahují také na F #.</span><span class="sxs-lookup"><span data-stu-id="89e46-180">These are also applicable to F#.</span></span>

<span data-ttu-id="89e46-181">Hlavní konstrukce dostupné v F # pro účely vyvolání výjimek by měly být považovány za následující pořadí:</span><span class="sxs-lookup"><span data-stu-id="89e46-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="89e46-182">Funkce</span><span class="sxs-lookup"><span data-stu-id="89e46-182">Function</span></span> | <span data-ttu-id="89e46-183">Syntax</span><span class="sxs-lookup"><span data-stu-id="89e46-183">Syntax</span></span> | <span data-ttu-id="89e46-184">Účel</span><span class="sxs-lookup"><span data-stu-id="89e46-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="89e46-185">Vyvolává `System.ArgumentNullException` se zadaným názvem argumentu.</span><span class="sxs-lookup"><span data-stu-id="89e46-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="89e46-186">Vyvolá a `System.ArgumentException` se zadaným názvem a zprávou argumentu.</span><span class="sxs-lookup"><span data-stu-id="89e46-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="89e46-187">Vyvolá `System.InvalidOperationException` zprávu se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="89e46-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="89e46-188">Mechanismus pro obecné účely pro vyvolávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="89e46-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="89e46-189">Vyvolá `System.Exception` zprávu se zadanou zprávou.</span><span class="sxs-lookup"><span data-stu-id="89e46-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="89e46-190">Vyvolá `System.Exception` zprávu se zprávou určenou formátovacím řetězcem a jeho vstupy.</span><span class="sxs-lookup"><span data-stu-id="89e46-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="89e46-191">Použijte `nullArg` `invalidArg` a `invalidOp` jako mechanismus, který chcete vyvolat `ArgumentNullException` , `ArgumentException` a v `InvalidOperationException` případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="89e46-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="89e46-192">`failwith`Funkce a `failwithf` by měly být obecně zabráněno, protože vyvolávají základní `Exception` typ, nikoli specifickou výjimku.</span><span class="sxs-lookup"><span data-stu-id="89e46-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="89e46-193">Podle pokynů pro [Návrh výjimek](../../standard/design-guidelines/exceptions.md)chcete vyvolat konkrétnější výjimky, když můžete.</span><span class="sxs-lookup"><span data-stu-id="89e46-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="use-exception-handling-syntax"></a><span data-ttu-id="89e46-194">Použití syntaxe pro zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="89e46-194">Use exception-handling syntax</span></span>

<span data-ttu-id="89e46-195">Jazyk F # podporuje vzory výjimek prostřednictvím `try...with` syntaxe:</span><span class="sxs-lookup"><span data-stu-id="89e46-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="89e46-196">Sladění funkcionality, která se má provést na tváři výjimky s porovnáváním vzorů, může být bit obtížné, pokud chcete zachovat vyčištění kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="89e46-197">Jedním z těchto způsobů, jak to zpracovat, je použít [aktivní vzory](../language-reference/active-patterns.md) jako způsob seskupení funkcí v případě chyby s jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="89e46-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="89e46-198">Například můžete využívat rozhraní API, které při vyvolání výjimky vloží cenné informace do metadat výjimky.</span><span class="sxs-lookup"><span data-stu-id="89e46-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="89e46-199">Rozbalení užitečné hodnoty v těle zachycené výjimky uvnitř aktivního vzoru a vrácení této hodnoty může být v některých situacích užitečné.</span><span class="sxs-lookup"><span data-stu-id="89e46-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="89e46-200">Nepoužívejte zpracování chyb monadic k nahrazení výjimek.</span><span class="sxs-lookup"><span data-stu-id="89e46-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="89e46-201">Výjimky se zobrazují jako poněkud Taboo v funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="89e46-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="89e46-202">Výjimky jsou ve skutečnosti porušení čistoty, takže je bezpečné je považovat za nepoměrně funkční.</span><span class="sxs-lookup"><span data-stu-id="89e46-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="89e46-203">Nicméně to bude ignorovat skutečnost, kde musí být kód spuštěn, a může dojít k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="89e46-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="89e46-204">Obecně platí, že při zapisování kódu na předpokladu, že většina věcí není ani čistá ani celkově, se minimalizuje nepříjemný překvapením.</span><span class="sxs-lookup"><span data-stu-id="89e46-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="89e46-205">Je důležité vzít v úvahu následující základní síly/aspekty výjimek s ohledem na jejich relevanci a vhodnost v prostředí .NET runtime a ekosystém mezi jazyky jako celek:</span><span class="sxs-lookup"><span data-stu-id="89e46-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="89e46-206">Obsahují podrobné diagnostické informace, které jsou velmi užitečné při ladění problému.</span><span class="sxs-lookup"><span data-stu-id="89e46-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="89e46-207">Jsou dobře pochopitelné modulem runtime a dalšími jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="89e46-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="89e46-208">Můžou snížit významný často používaný kód v porovnání s kódem, který se dokončí způsobem, aby *nedocházelo* k výjimkám tím, že implementuje určitou podmnožinu jejich sémantiky na základě ad hoc.</span><span class="sxs-lookup"><span data-stu-id="89e46-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="89e46-209">Tento třetí bod je kritický.</span><span class="sxs-lookup"><span data-stu-id="89e46-209">This third point is critical.</span></span> <span data-ttu-id="89e46-210">U netriviální složitých operací může selhání při použití výjimek vést ke strukturám, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="89e46-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="89e46-211">Což může snadno vést k křehkému kódu, jako je porovnávání vzorů při chybách typu "String-Type":</span><span class="sxs-lookup"><span data-stu-id="89e46-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="89e46-212">Kromě toho je možné zvážit, že se bude považovat za požití jakékoli výjimky v možnosti "jednoduchá" funkce, která vrací typ "Nicer":</span><span class="sxs-lookup"><span data-stu-id="89e46-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="89e46-213">Bohužel `tryReadAllText` může vyvolat mnoho výjimek na základě nesčetných věcí, ke kterým může dojít v systému souborů, a tento kód zahodí všechny informace o tom, co se ve vašem prostředí skutečně stane špatným.</span><span class="sxs-lookup"><span data-stu-id="89e46-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="89e46-214">Pokud nahradíte tento kód výsledným typem, budete zpět k analýze chybové zprávy typu "String-Type":</span><span class="sxs-lookup"><span data-stu-id="89e46-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="89e46-215">A umístění samotného objektu Exception do `Error` konstruktoru pouze vynutí, abyste správně zapracovali s typem výjimky na webu volání, nikoli ve funkci.</span><span class="sxs-lookup"><span data-stu-id="89e46-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="89e46-216">Díky tomu efektivně vznikne zaškrtnuté výjimky, které jsou obvykle odlaďuje unfun, které se zabývat jako volající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="89e46-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="89e46-217">Dobrou alternativou k výše uvedeným příkladům je zachycení *specifických* výjimek a vrácení smysluplné hodnoty v kontextu této výjimky.</span><span class="sxs-lookup"><span data-stu-id="89e46-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="89e46-218">Pokud tuto funkci upravíte takto `tryReadAllText` , `None` má více význam:</span><span class="sxs-lookup"><span data-stu-id="89e46-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="89e46-219">Místo toho, aby tato funkce fungovala jako zachycení, tato funkce nyní správně zpracuje případ, kdy nebyl nalezen soubor a přiřadí tento význam k návratu.</span><span class="sxs-lookup"><span data-stu-id="89e46-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="89e46-220">Tato návratová hodnota může být namapována na daný chybový případ, přičemž nedojde k zahození jakýchkoli kontextových informací nebo k vynucení volajících, aby se zabývat případem, který v tomto okamžiku v kódu nemusí být relevantní.</span><span class="sxs-lookup"><span data-stu-id="89e46-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="89e46-221">Typy, jako `Result<'Success, 'Error>` jsou vhodné pro základní operace, kde nejsou vnořené, a volitelné typy F # jsou ideální pro reprezentaci, když může něco vrátit *něco* nebo *nic*.</span><span class="sxs-lookup"><span data-stu-id="89e46-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="89e46-222">Nejsou náhradou za výjimky, ale a neměly by se používat v pokusu o nahrazení výjimek.</span><span class="sxs-lookup"><span data-stu-id="89e46-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="89e46-223">Místo toho by se měly použít uvážlivě k vyřešení konkrétních aspektů zásad výjimky a správy chyb, a to cílené způsobem.</span><span class="sxs-lookup"><span data-stu-id="89e46-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="89e46-224">Částečné a bezplatné programování aplikací a koncových bodů</span><span class="sxs-lookup"><span data-stu-id="89e46-224">Partial application and point-free programming</span></span>

<span data-ttu-id="89e46-225">Jazyk F # podporuje částečnou aplikaci, a proto různé způsoby programování ve stylu bez bodu.</span><span class="sxs-lookup"><span data-stu-id="89e46-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="89e46-226">To může být užitečné pro opětovné použití kódu v rámci modulu nebo implementace nějakého, ale není něco k tomu, abyste veřejně zveřejnili.</span><span class="sxs-lookup"><span data-stu-id="89e46-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="89e46-227">Obecně platí, že programování bez koncových bodů není v a samo samé a může přidat významnou bariéru rozpoznávání pro lidi, kteří nejsou ve stylu ponořeni.</span><span class="sxs-lookup"><span data-stu-id="89e46-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="89e46-228">Nepoužívejte částečné aplikace a procesu curryfikace ve veřejných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="89e46-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="89e46-229">S malou výjimkou může být použití částečné aplikace ve veřejných rozhraních API pro uživatele matoucí.</span><span class="sxs-lookup"><span data-stu-id="89e46-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="89e46-230">`let`Hodnoty jsou obvykle vázané v kódu F #, nikoli **values** **hodnoty funkcí**.</span><span class="sxs-lookup"><span data-stu-id="89e46-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="89e46-231">Kombinování hodnot a hodnot funkcí může mít za následek uložení malého počtu řádků kódu v Exchangi pro poměrně bitovou zátěž, zejména v případě kombinace s operátory, jako je například `>>` vytváření funkcí.</span><span class="sxs-lookup"><span data-stu-id="89e46-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="89e46-232">Vezměte v úvahu dopady nástrojů pro programování bez jakéhokoli bodu.</span><span class="sxs-lookup"><span data-stu-id="89e46-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="89e46-233">Funkce curryfikované nepopisují své argumenty.</span><span class="sxs-lookup"><span data-stu-id="89e46-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="89e46-234">To má vliv na nástroje.</span><span class="sxs-lookup"><span data-stu-id="89e46-234">This has tooling implications.</span></span> <span data-ttu-id="89e46-235">Vezměte v úvahu tyto dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="89e46-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="89e46-236">Obě jsou platné funkce, ale `funcWithApplication` je curryfikované funkcí.</span><span class="sxs-lookup"><span data-stu-id="89e46-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="89e46-237">Když najedete myší na své typy v editoru, uvidíte toto:</span><span class="sxs-lookup"><span data-stu-id="89e46-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="89e46-238">V lokalitě volání popisy v nástrojích, jako je například Visual Studio, neposkytnou smysluplné informace o tom, jaké `string` typy a `int` vstupní hodnoty skutečně reprezentují.</span><span class="sxs-lookup"><span data-stu-id="89e46-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="89e46-239">Pokud narazíte na kód bez bodu `funcWithApplication` , který je veřejně vhodný, doporučuje se provést úplné rozšíření η, aby nástroj mohl pro argumenty vybrat smysluplné názvy.</span><span class="sxs-lookup"><span data-stu-id="89e46-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="89e46-240">Kromě toho může být kód bez bodu ladění náročný, pokud není možný.</span><span class="sxs-lookup"><span data-stu-id="89e46-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="89e46-241">Nástroje pro ladění spoléhají na hodnoty vázané na názvy (například `let` vazby), abyste mohli kontrolovat mezilehlé hodnoty prostřednictvím provádění.</span><span class="sxs-lookup"><span data-stu-id="89e46-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="89e46-242">Pokud váš kód nemá žádné hodnoty ke kontrole, není k dispozici žádný k ladění.</span><span class="sxs-lookup"><span data-stu-id="89e46-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="89e46-243">V budoucnu se ladicí nástroje můžou vyvíjet k syntetizaci těchto hodnot na základě dříve provedených cest, ale není dobré zakládat své tipy na *možné* funkce ladění.</span><span class="sxs-lookup"><span data-stu-id="89e46-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="89e46-244">Zvažte částečnou aplikaci jako metodu pro snížení interního často používaného textu.</span><span class="sxs-lookup"><span data-stu-id="89e46-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="89e46-245">Na rozdíl od předchozího bodu je částečná aplikace vynikajícím nástrojem pro omezení často používaného textu v rámci aplikace nebo hlubších vnitřních funkcí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="89e46-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="89e46-246">To může být užitečné při testování jednotek implementace složitějších rozhraní API, kde často je často jednodušší se vypořádat s.</span><span class="sxs-lookup"><span data-stu-id="89e46-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="89e46-247">Například následující kód ukazuje, jak můžete dosáhnout toho, co nejpodobující architektury poskytují, aniž byste museli přebírat externí závislost na takové architektuře a musí se naučit související rozhraní Bespoke API.</span><span class="sxs-lookup"><span data-stu-id="89e46-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="89e46-248">Zvažte například následující topografii řešení:</span><span class="sxs-lookup"><span data-stu-id="89e46-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="89e46-249">`ImplementationLogic.fsproj` může vystavit kód jako:</span><span class="sxs-lookup"><span data-stu-id="89e46-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="89e46-250">Testování částí `Transactions.doTransaction` v nástroji `ImplementationLogic.Tests.fsproj` je snadné:</span><span class="sxs-lookup"><span data-stu-id="89e46-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="89e46-251">Částečně použití `doTransaction` s objektem s napodobnou kontextovou funkcí umožňuje zavolat funkci ve všech testech jednotek bez nutnosti sestavit napodobný kontext pokaždé, když:</span><span class="sxs-lookup"><span data-stu-id="89e46-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="89e46-252">Tato technika by se nedala univerzálně aplikovat na celý základ kódu, ale je dobrým způsobem, jak omezit často používané složité interní prvky a testování jednotek těchto interních.</span><span class="sxs-lookup"><span data-stu-id="89e46-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="89e46-253">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="89e46-253">Access control</span></span>

<span data-ttu-id="89e46-254">Jazyk F # má více možností pro [řízení přístupu](../language-reference/access-control.md)zděděné od toho, co je k dispozici v modulu .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="89e46-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="89e46-255">Nedají se použít jen pro typy – můžete je používat i pro funkce.</span><span class="sxs-lookup"><span data-stu-id="89e46-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="89e46-256">Preferovat `public` netypy a členy, dokud je nepotřebujete, aby byli veřejně spotřební.</span><span class="sxs-lookup"><span data-stu-id="89e46-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="89e46-257">Tím se taky minimalizuje to, k čemu se spotřebitelé pojí.</span><span class="sxs-lookup"><span data-stu-id="89e46-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="89e46-258">Snažte se zachovat všechny funkce pomocníka `private` .</span><span class="sxs-lookup"><span data-stu-id="89e46-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="89e46-259">Zvažte použití `[<AutoOpen>]` funkce na privátním modulu pomocných funkcí, pokud se stanou řadou.</span><span class="sxs-lookup"><span data-stu-id="89e46-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="89e46-260">Odvození typu a obecné typy</span><span class="sxs-lookup"><span data-stu-id="89e46-260">Type inference and generics</span></span>

<span data-ttu-id="89e46-261">Odvození typu vám může ušetřit od zadání spousty často používaného textu.</span><span class="sxs-lookup"><span data-stu-id="89e46-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="89e46-262">A Automatická generalizace v kompilátoru F # vám může pomáhat při psaní obecnější kódu s téměř nepřímým úsilím na vaši část.</span><span class="sxs-lookup"><span data-stu-id="89e46-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="89e46-263">Tyto funkce nejsou ale všeobecně dobré.</span><span class="sxs-lookup"><span data-stu-id="89e46-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="89e46-264">Zvažte označení názvů argumentů explicitními typy ve veřejných rozhraních API a nespoléhejte se na odvození typu.</span><span class="sxs-lookup"><span data-stu-id="89e46-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="89e46-265">Důvodem **je, že byste měli** mít kontrolu nad tvarem rozhraní API, nikoli kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="89e46-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="89e46-266">I když může kompilátor provést podrobnější úlohu při odvozování typů za vás, je možné mít tvar svého rozhraní API změněn, pokud interní funkce, na kterých závisí, mají změněné typy.</span><span class="sxs-lookup"><span data-stu-id="89e46-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="89e46-267">To může být to, co potřebujete, ale téměř jistě by to mělo za následek přerušující změnu rozhraní API, o kterou budou moct vzdálení uživatelé řešit.</span><span class="sxs-lookup"><span data-stu-id="89e46-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="89e46-268">Místo toho, pokud explicitně ovládáte tvar veřejného rozhraní API, můžete tyto zásadní změny řídit.</span><span class="sxs-lookup"><span data-stu-id="89e46-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="89e46-269">V DDD výrazy to lze představit jako vrstvu odolnou proti poškození.</span><span class="sxs-lookup"><span data-stu-id="89e46-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="89e46-270">Zvažte poskytnutí smysluplného názvu obecným argumentům.</span><span class="sxs-lookup"><span data-stu-id="89e46-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="89e46-271">Pokud nezapisujete skutečně obecný kód, který není specifický pro konkrétní doménu, smysluplný název může pomáhat ostatním programátorům pochopit doménu, ve které pracují.</span><span class="sxs-lookup"><span data-stu-id="89e46-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="89e46-272">Například parametr typu s názvem `'Document` v kontextu interakce s databází dokumentu umožňuje vymazat, že obecné typy dokumentů mohou být přijaty funkcí nebo členem, se kterými pracujete.</span><span class="sxs-lookup"><span data-stu-id="89e46-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="89e46-273">Zvažte pojmenování obecných parametrů typu pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="89e46-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="89e46-274">Toto je obecný způsob, jak provádět akce v .NET, takže se místo snake_case nebo camelCase doporučuje používat PascalCase.</span><span class="sxs-lookup"><span data-stu-id="89e46-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="89e46-275">Kromě toho automatické generalizace není vždy Boon pro uživatele, kteří jsou novinkou v jazyce F # nebo ve velkém základu kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="89e46-276">Při používání komponent, které jsou obecné, se vyvnímání zátěže.</span><span class="sxs-lookup"><span data-stu-id="89e46-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="89e46-277">Kromě toho, pokud jsou automaticky zobecněné funkce použity s různými vstupními typy (ať už jsou určeny pro použití jako takové), neexistují žádné výhody, které jsou v daném časovém okamžiku v tomto okamžiku obecně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89e46-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="89e46-278">Vždy zvažte, jestli kód, který píšete, bude mít ve skutečnosti obecný přínos.</span><span class="sxs-lookup"><span data-stu-id="89e46-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="89e46-279">Výkon</span><span class="sxs-lookup"><span data-stu-id="89e46-279">Performance</span></span>

### <a name="consider-structs-for-small-types-with-high-allocation-rates"></a><span data-ttu-id="89e46-280">Zvažte struktury pro malé typy s vysokými sazbami přidělení.</span><span class="sxs-lookup"><span data-stu-id="89e46-280">Consider structs for small types with high allocation rates</span></span>

<span data-ttu-id="89e46-281">Použití struktur (označovaných také jako typy hodnot) může často vést k vyššímu výkonu pro určitý kód, protože obvykle brání přidělení objektů.</span><span class="sxs-lookup"><span data-stu-id="89e46-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="89e46-282">Nicméně struktury nejsou vždy tlačítko "Přejít rychleji": Pokud velikost dat ve struktuře překročí 16 bajtů, může kopírování dat často vést k většímu množství času procesoru než při použití typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="89e46-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="89e46-283">Pokud chcete zjistit, jestli byste měli použít strukturu, vezměte v úvahu následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="89e46-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="89e46-284">Pokud velikost dat je 16 bajtů nebo menší.</span><span class="sxs-lookup"><span data-stu-id="89e46-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="89e46-285">Pokud pravděpodobně máte mnoho instancí těchto typů rezidentní v paměti v běžícím programu.</span><span class="sxs-lookup"><span data-stu-id="89e46-285">If you're likely to have many instances of these types resident in memory in a running program.</span></span>

<span data-ttu-id="89e46-286">Pokud se použije první podmínka, měli byste obecně použít strukturu.</span><span class="sxs-lookup"><span data-stu-id="89e46-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="89e46-287">Pokud platí obě, měli byste téměř vždy používat strukturu.</span><span class="sxs-lookup"><span data-stu-id="89e46-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="89e46-288">Můžou nastat případy, kdy platí předchozí podmínky, ale použití struktury není lepší nebo horší než použití typu odkazu, ale je pravděpodobné, že budou výjimečné.</span><span class="sxs-lookup"><span data-stu-id="89e46-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="89e46-289">Při provádění změn, jako je to třeba, i když nefungují na předpokladu nebo Intuition, je důležité vždy změřit.</span><span class="sxs-lookup"><span data-stu-id="89e46-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="consider-struct-tuples-when-grouping-small-value-types-with-high-allocation-rates"></a><span data-ttu-id="89e46-290">Vzít v úvahu řazené kolekce členů struktur při seskupování malých hodnotových typů s vysokými sazbami přidělení</span><span class="sxs-lookup"><span data-stu-id="89e46-290">Consider struct tuples when grouping small value types with high allocation rates</span></span>

<span data-ttu-id="89e46-291">Vezměte v úvahu tyto dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="89e46-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="89e46-292">Při srovnávacích testech těchto funkcí se statistickým nástrojem pro srovnávací testy, jako je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že `runWithStructTuple` funkce, která používá řazené kolekce členů struktury, je rychlejší než 40% a přiděluje žádnou paměť.</span><span class="sxs-lookup"><span data-stu-id="89e46-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="89e46-293">Tyto výsledky ale neplatí vždy v případě vlastního kódu.</span><span class="sxs-lookup"><span data-stu-id="89e46-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="89e46-294">Pokud označíte funkci jako `inline` , kód, který používá řazené kolekce členů, může získat některé další optimalizace, jinak by kód, který by měl být přidělen, mohl být pouze optimalizován.</span><span class="sxs-lookup"><span data-stu-id="89e46-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="89e46-295">Měli byste vždycky měřit výsledky vždy, když je dotčen výkon, a nikdy nefungovat na základě předpokladů nebo Intuition.</span><span class="sxs-lookup"><span data-stu-id="89e46-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="consider-struct-records-when-the-type-is-small-and-has-high-allocation-rates"></a><span data-ttu-id="89e46-296">Zvažte záznamy struktury, pokud je typ malý a má vysoké sazby přidělení.</span><span class="sxs-lookup"><span data-stu-id="89e46-296">Consider struct records when the type is small and has high allocation rates</span></span>

<span data-ttu-id="89e46-297">Pravidlo popsaných povýšení pro [typy záznamů F #](../language-reference/records.md)je také uloženo.</span><span class="sxs-lookup"><span data-stu-id="89e46-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="89e46-298">Vezměte v úvahu následující datové typy a funkce, které je zpracovávají:</span><span class="sxs-lookup"><span data-stu-id="89e46-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="89e46-299">To se podobá předchozímu kódu řazené kolekce členů, ale tentokrát v příkladu používá záznamy a vloženou vnitřní funkci.</span><span class="sxs-lookup"><span data-stu-id="89e46-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="89e46-300">Při srovnávacích testech těchto funkcí se statistickým nástrojem pro srovnávací testy, jako je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že se bude `processStructPoint` spouštět téměř 60% rychleji a na spravované haldě se nic nealokuje.</span><span class="sxs-lookup"><span data-stu-id="89e46-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="consider-struct-discriminated-unions-when-the-data-type-is-small-with-high-allocation-rates"></a><span data-ttu-id="89e46-301">Zvažte možnost struktury rozlišených sjednocení, když je datový typ malý s vysokými sazbami přidělení.</span><span class="sxs-lookup"><span data-stu-id="89e46-301">Consider struct discriminated unions when the data type is small with high allocation rates</span></span>

<span data-ttu-id="89e46-302">Předchozí poznámky o výkonu s řazenými kolekcemi členů struktury a záznamy jsou také uloženy pro [rozlišené sjednocení F #](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="89e46-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="89e46-303">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="89e46-303">Consider the following code:</span></span>

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

<span data-ttu-id="89e46-304">Je běžné definovat jednotně rozlišené sjednocení jako v případě modelování domén.</span><span class="sxs-lookup"><span data-stu-id="89e46-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="89e46-305">Při srovnávacích testech těchto funkcí se statistickým nástrojem pro srovnávací testy, jako je [BenchmarkDotNet](https://benchmarkdotnet.org/), zjistíte, že `structReverseName` spuštění přibližně o 25% rychlejší než `reverseName` u malých řetězců.</span><span class="sxs-lookup"><span data-stu-id="89e46-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="89e46-306">U velkých řetězců provede obě stejnou operaci.</span><span class="sxs-lookup"><span data-stu-id="89e46-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="89e46-307">Takže v tomto případě je vždy vhodnější použít strukturu.</span><span class="sxs-lookup"><span data-stu-id="89e46-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="89e46-308">Jak už bylo uvedeno výše, vždy změřte a nespouštějte na základě předpokladů nebo Intuition.</span><span class="sxs-lookup"><span data-stu-id="89e46-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="89e46-309">I když předchozí příklad ukázal, že se strukturou rozlišené sjednocení vrátilo lepší výkon, je běžné mít při modelování domény větší rozlišené sjednocení.</span><span class="sxs-lookup"><span data-stu-id="89e46-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="89e46-310">Větší datové typy, jako třeba, se nemusí provádět, i když se jedná o struktury v závislosti na operacích, které by mohly být součástí dalších kopírování.</span><span class="sxs-lookup"><span data-stu-id="89e46-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="89e46-311">Funkční programování a mutace</span><span class="sxs-lookup"><span data-stu-id="89e46-311">Functional programming and mutation</span></span>

<span data-ttu-id="89e46-312">Hodnoty F # jsou ve výchozím nastavení neměnné, což umožňuje vyhnout se určitým třídám chyb (zejména ty, které se týkají souběžnosti a paralelismu).</span><span class="sxs-lookup"><span data-stu-id="89e46-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="89e46-313">Nicméně v některých případech, aby bylo dosaženo optimální (nebo ještě rozumně) efektivity času spuštění nebo přidělení paměti, je možné, že je možné využít rozsah práce pomocí místní mutace stavu.</span><span class="sxs-lookup"><span data-stu-id="89e46-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="89e46-314">To je možné na základě výslovného souhlasu s F # s `mutable` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="89e46-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="89e46-315">Použití `mutable` v jazyce F # se může cítit v lichá s funkcí čistoty.</span><span class="sxs-lookup"><span data-stu-id="89e46-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="89e46-316">To je srozumitelnější, ale funkční čistota všude může být v lichá s cíli výkonu.</span><span class="sxs-lookup"><span data-stu-id="89e46-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="89e46-317">Ohrožením je zapouzdření mutací tak, že volající nemusí dbát na to, co se stane při volání funkce.</span><span class="sxs-lookup"><span data-stu-id="89e46-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="89e46-318">To umožňuje napsat funkční rozhraní přes implementaci na základě mutací pro kód kritický pro výkon.</span><span class="sxs-lookup"><span data-stu-id="89e46-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="89e46-319">Zalamování měnitelného kódu v neměnných rozhraních</span><span class="sxs-lookup"><span data-stu-id="89e46-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="89e46-320">V případě referenční transparentnosti jako cíle je velmi důležité napsat kód, který nezveřejňuje proměnlivou podšpičku funkcí kritických pro výkon.</span><span class="sxs-lookup"><span data-stu-id="89e46-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="89e46-321">Například následující kód implementuje `Array.contains` funkci v základní knihovně F #:</span><span class="sxs-lookup"><span data-stu-id="89e46-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="89e46-322">Vícenásobné volání této funkce nemění podkladové pole, ani nevyžaduje, abyste zachovali proměnlivý stav, který je v tom, že ho budete spotřebovávat.</span><span class="sxs-lookup"><span data-stu-id="89e46-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="89e46-323">Je tak transparentní, i když skoro každý řádek kódu v něm používá mutace.</span><span class="sxs-lookup"><span data-stu-id="89e46-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="89e46-324">Zvažte zapouzdření proměnlivých dat ve třídách</span><span class="sxs-lookup"><span data-stu-id="89e46-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="89e46-325">Předchozí příklad používal jednu funkci k zapouzdření operací pomocí proměnlivých dat.</span><span class="sxs-lookup"><span data-stu-id="89e46-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="89e46-326">To není vždy dostačující pro složitější sady dat.</span><span class="sxs-lookup"><span data-stu-id="89e46-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="89e46-327">Vezměte v úvahu následující sady funkcí:</span><span class="sxs-lookup"><span data-stu-id="89e46-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="89e46-328">Tento kód je proveden, ale zveřejňuje datovou strukturu založenou na mutacích, kterou volající zodpovídá za údržbu.</span><span class="sxs-lookup"><span data-stu-id="89e46-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="89e46-329">To lze zabalit do třídy bez základních členů, které mohou změnit:</span><span class="sxs-lookup"><span data-stu-id="89e46-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="89e46-330">`Closure1Table` zapouzdřuje základní datovou strukturu založenou na mutacích, a proto nenutí volající, aby zachoval základní datovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="89e46-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="89e46-331">Třídy představují účinný způsob, jak zapouzdřit data a rutiny, které jsou založené na mutacích bez odhalení podrobností volajícím.</span><span class="sxs-lookup"><span data-stu-id="89e46-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="89e46-332">Preferovat `let mutable` odkazování na buňky</span><span class="sxs-lookup"><span data-stu-id="89e46-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="89e46-333">Odkazové buňky představují způsob, jak znázornit odkaz na hodnotu namísto samotné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="89e46-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="89e46-334">I když je lze použít pro kód kritický pro výkon, nejsou doporučovány.</span><span class="sxs-lookup"><span data-stu-id="89e46-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="89e46-335">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="89e46-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="89e46-336">Použití referenční buňky teď "znečišťující" všechny následné kódy, které se musí přesměrovat a znovu odkazovat na podkladová data.</span><span class="sxs-lookup"><span data-stu-id="89e46-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="89e46-337">Místo toho zvažte `let mutable` následující:</span><span class="sxs-lookup"><span data-stu-id="89e46-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="89e46-338">Kromě jediného bodu mutace uprostřed výrazu lambda se všechny ostatní kódy, které se můžou dotknout, `acc` tak, aby se nelišily způsobem, který se liší od použití `let` neměnné hodnoty normální vazby.</span><span class="sxs-lookup"><span data-stu-id="89e46-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="89e46-339">To usnadňuje změnu v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="89e46-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="89e46-340">Programování objektů</span><span class="sxs-lookup"><span data-stu-id="89e46-340">Object programming</span></span>

<span data-ttu-id="89e46-341">Jazyk F # má úplnou podporu pro objekty a koncepty orientované na objekt (ó).</span><span class="sxs-lookup"><span data-stu-id="89e46-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="89e46-342">I když je mnoho konceptů ú náročných a užitečných, ne všechny z nich jsou ideální pro použití.</span><span class="sxs-lookup"><span data-stu-id="89e46-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="89e46-343">V následujících seznamech jsou uvedeny doprovodné materiály k kategoriím funkcí ó na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="89e46-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="89e46-344">**Zvažte použití těchto funkcí v mnoha situacích:**</span><span class="sxs-lookup"><span data-stu-id="89e46-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="89e46-345">Tečkový zápis ( `x.Length` )</span><span class="sxs-lookup"><span data-stu-id="89e46-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="89e46-346">Členy instance</span><span class="sxs-lookup"><span data-stu-id="89e46-346">Instance members</span></span>
* <span data-ttu-id="89e46-347">Implicitní konstruktory</span><span class="sxs-lookup"><span data-stu-id="89e46-347">Implicit constructors</span></span>
* <span data-ttu-id="89e46-348">Statické členy</span><span class="sxs-lookup"><span data-stu-id="89e46-348">Static members</span></span>
* <span data-ttu-id="89e46-349">Notace indexeru ( `arr.[x]` )</span><span class="sxs-lookup"><span data-stu-id="89e46-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="89e46-350">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="89e46-350">Named and Optional arguments</span></span>
* <span data-ttu-id="89e46-351">Implementace rozhraní a rozhraní</span><span class="sxs-lookup"><span data-stu-id="89e46-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="89e46-352">**Tyto funkce nejdřív nemusíte používat, ale v případě, že jsou praktické k vyřešení problému, je třeba je použít uvážlivě:**</span><span class="sxs-lookup"><span data-stu-id="89e46-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="89e46-353">Přetížení metody</span><span class="sxs-lookup"><span data-stu-id="89e46-353">Method overloading</span></span>
* <span data-ttu-id="89e46-354">Zapouzdřená proměnlivá data</span><span class="sxs-lookup"><span data-stu-id="89e46-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="89e46-355">Operátory na typech</span><span class="sxs-lookup"><span data-stu-id="89e46-355">Operators on types</span></span>
* <span data-ttu-id="89e46-356">Automatické vlastnosti</span><span class="sxs-lookup"><span data-stu-id="89e46-356">Auto properties</span></span>
* <span data-ttu-id="89e46-357">Implementace `IDisposable` a `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="89e46-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="89e46-358">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="89e46-358">Type extensions</span></span>
* <span data-ttu-id="89e46-359">Události</span><span class="sxs-lookup"><span data-stu-id="89e46-359">Events</span></span>
* <span data-ttu-id="89e46-360">Struktury</span><span class="sxs-lookup"><span data-stu-id="89e46-360">Structs</span></span>
* <span data-ttu-id="89e46-361">Delegáti</span><span class="sxs-lookup"><span data-stu-id="89e46-361">Delegates</span></span>
* <span data-ttu-id="89e46-362">Výčty</span><span class="sxs-lookup"><span data-stu-id="89e46-362">Enums</span></span>

<span data-ttu-id="89e46-363">**Obecně se vyhnete těmto funkcím, pokud je nemusíte používat:**</span><span class="sxs-lookup"><span data-stu-id="89e46-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="89e46-364">Hierarchie typů založené na dědičnosti a dědičnost implementace</span><span class="sxs-lookup"><span data-stu-id="89e46-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="89e46-365">Hodnoty null a `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="89e46-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="89e46-366">Preferovat kompozici před děděním</span><span class="sxs-lookup"><span data-stu-id="89e46-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="89e46-367">[Kompozice proti dědičnosti](https://en.wikipedia.org/wiki/Composition_over_inheritance) je dlouhodobá idiomá, kterou může dobrý kód F # dodržet.</span><span class="sxs-lookup"><span data-stu-id="89e46-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="89e46-368">Základní princip je, že byste neměli vystavovat základní třídu a vynutit, aby volající dědili z této základní třídy, aby získala funkčnost.</span><span class="sxs-lookup"><span data-stu-id="89e46-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="89e46-369">Použití výrazů objektů k implementaci rozhraní, pokud nepotřebujete třídu</span><span class="sxs-lookup"><span data-stu-id="89e46-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="89e46-370">[Výrazy objektů](../language-reference/object-expressions.md) umožňují implementovat rozhraní za chodu, vázání implementovaného rozhraní na hodnotu, aniž by bylo nutné tak učinit uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="89e46-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="89e46-371">To je užitečné, zejména _Pokud potřebujete implementovat_ rozhraní a nemusíte mít úplnou třídu.</span><span class="sxs-lookup"><span data-stu-id="89e46-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="89e46-372">Například zde je kód, který je spuštěn v [Ionide](https://ionide.io/) a poskytuje akci opravy kódu, pokud jste přidali symbol, který nemáte `open` příkaz pro:</span><span class="sxs-lookup"><span data-stu-id="89e46-372">For example, here is the code that is run in [Ionide](https://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="89e46-373">Vzhledem k tomu, že při interakci s rozhraním API Visual Studio Code není potřeba žádná třída, jsou výrazy objektu ideálním nástrojem.</span><span class="sxs-lookup"><span data-stu-id="89e46-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="89e46-374">Jsou také cenné pro testování částí, pokud chcete odhlásit rozhraní s testovacími rutinami v ad hoc.</span><span class="sxs-lookup"><span data-stu-id="89e46-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="89e46-375">Zvažte zkratky typu pro zkrácení signatur.</span><span class="sxs-lookup"><span data-stu-id="89e46-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="89e46-376">[Zkratky typů](../language-reference/type-abbreviations.md) jsou pohodlný způsob, jak přiřadit popisek jinému typu, jako je například signatura funkce nebo složitější typ.</span><span class="sxs-lookup"><span data-stu-id="89e46-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="89e46-377">Například následující alias přiřadí popisek k tomu, co je potřeba k definování výpočtu pomocí [CNTK](https://docs.microsoft.com/cognitive-toolkit/), knihovny hloubkového učení:</span><span class="sxs-lookup"><span data-stu-id="89e46-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="89e46-378">`Computation`Název je pohodlný způsob, jak si poznamenat jakoukoliv funkci, která odpovídá signatuře, se kterým je alias.</span><span class="sxs-lookup"><span data-stu-id="89e46-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="89e46-379">Použití zkratek typů, jako je to pohodlné a umožňuje výstižnější kód.</span><span class="sxs-lookup"><span data-stu-id="89e46-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="89e46-380">Nepoužívejte zkratky typů k vyjádření vaší domény.</span><span class="sxs-lookup"><span data-stu-id="89e46-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="89e46-381">I když zkratky typu jsou vhodné pro poskytnutí názvu podpisům funkcí, mohou být matoucí při abbreviating jiných typů.</span><span class="sxs-lookup"><span data-stu-id="89e46-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="89e46-382">Zvažte tuto zkratku:</span><span class="sxs-lookup"><span data-stu-id="89e46-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="89e46-383">To může být matoucí v několika ohledech:</span><span class="sxs-lookup"><span data-stu-id="89e46-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="89e46-384">`BufferSize` není abstrakce; je to pouze jiný název pro celé číslo.</span><span class="sxs-lookup"><span data-stu-id="89e46-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="89e46-385">Pokud `BufferSize` je zveřejněné ve veřejném rozhraní API, může být snadno neinterpretované na více než jen jednou `int` .</span><span class="sxs-lookup"><span data-stu-id="89e46-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="89e46-386">Obecně platí, že doménové typy mají více atributů a nejsou primitivní typy jako `int` .</span><span class="sxs-lookup"><span data-stu-id="89e46-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="89e46-387">Tato zkratka je v rozporu s tímto předpokladem.</span><span class="sxs-lookup"><span data-stu-id="89e46-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="89e46-388">PascalCase (velká a malá písmena `BufferSize` ) znamená, že tento typ obsahuje více dat.</span><span class="sxs-lookup"><span data-stu-id="89e46-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="89e46-389">Tento alias nenabízí větší přehlednost v porovnání s poskytnutím pojmenovaného argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="89e46-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="89e46-390">Zkratka nebude manifest v kompilovaném IL; je to jenom celé číslo a tento alias je konstrukce, která je v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="89e46-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="89e46-391">V souhrnu Pitfall s zkratkami typu je, že nejsou abstrakce prostřednictvím typů, **které jsou abbreviating** .</span><span class="sxs-lookup"><span data-stu-id="89e46-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="89e46-392">V předchozím příkladu `BufferSize` je pouze `int` v rámci pokrývání bez dalších dat, ani žádné výhody z typu systému než to `int` již má.</span><span class="sxs-lookup"><span data-stu-id="89e46-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="89e46-393">Alternativním přístupem k použití zkratek typů k vyjádření domény je použití sjednocených sjednocení.</span><span class="sxs-lookup"><span data-stu-id="89e46-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="89e46-394">Předchozí vzorek lze modelovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="89e46-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="89e46-395">Pokud píšete kód, který funguje v souvislosti s `BufferSize` a jeho základní hodnotou, je nutné sestavit místo toho, aby předával libovolné libovolné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="89e46-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="89e46-396">To snižuje pravděpodobnost neúspěšného předání libovolného celého čísla do `send` funkce, protože volající musí vytvořit `BufferSize` typ pro zabalení hodnoty před voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="89e46-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
