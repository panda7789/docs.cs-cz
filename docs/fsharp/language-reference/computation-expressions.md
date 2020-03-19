---
title: Výpočetní výrazy
description: Naučte se, jak vytvořit pohodlnou syntaxi pro psaní výpočtů v F#, které lze sekvencovat a kombinovat pomocí konstrukce toku řízení a vazby.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400230"
---
# <a name="computation-expressions"></a><span data-ttu-id="b2fa6-103">Výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="b2fa6-103">Computation Expressions</span></span>

<span data-ttu-id="b2fa6-104">Výpočetní výrazy v F# poskytují pohodlnou syntaxi pro psaní výpočtů, které lze sekvencovat a kombinovat pomocí konstrukce toku řízení a vazeb.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="b2fa6-105">V závislosti na druhu výpočtového výrazu si je lze myslet jako způsob, jak vyjádřit monady, monoidy, monadové transformátory a aplikátory.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="b2fa6-106">Na rozdíl od jiných jazyků *(například donotace* v Haskellu) však nejsou vázány na jednu abstrakce a nespoléhají se na makra nebo jiné formy metaprogramování, aby bylo možné provést pohodlnou a kontextově citlivou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="b2fa6-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="b2fa6-107">Overview</span></span>

<span data-ttu-id="b2fa6-108">Výpočty mohou mít mnoho podob.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-108">Computations can take many forms.</span></span> <span data-ttu-id="b2fa6-109">Nejběžnější forma výpočtu je jednovláknové spuštění, které je snadno pochopitelné a upravit.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="b2fa6-110">Však ne všechny formy výpočtu jsou stejně jednoduché jako jednovláknové spuštění.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="b2fa6-111">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-111">Some examples include:</span></span>

- <span data-ttu-id="b2fa6-112">Nedeterministické výpočty</span><span class="sxs-lookup"><span data-stu-id="b2fa6-112">Non-deterministic computations</span></span>
- <span data-ttu-id="b2fa6-113">Asynchronní výpočty</span><span class="sxs-lookup"><span data-stu-id="b2fa6-113">Asynchronous computations</span></span>
- <span data-ttu-id="b2fa6-114">Efektivní výpočty</span><span class="sxs-lookup"><span data-stu-id="b2fa6-114">Effectful computations</span></span>
- <span data-ttu-id="b2fa6-115">Generativní výpočty</span><span class="sxs-lookup"><span data-stu-id="b2fa6-115">Generative computations</span></span>

<span data-ttu-id="b2fa6-116">Obecněji platí, že existují *kontextové* výpočty, které je nutné provést v určitých částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="b2fa6-117">Psaní kontextového kódu může být náročné, protože je snadné "nevracení" výpočty mimo daný kontext bez abstrakcí, aby vám v tom zabránit.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="b2fa6-118">Tyto abstrakce jsou často náročné psát sami, což je důvod, proč F# má zobecněný způsob, jak provést tak zvané **výpočetní výrazy**.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="b2fa6-119">Výpočetní výrazy nabízejí jednotný syntaktický a abstraktní model pro kódování kontextových výpočtů.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="b2fa6-120">Každý výpočetní výraz je zálohován typem *tvůrce.*</span><span class="sxs-lookup"><span data-stu-id="b2fa6-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="b2fa6-121">Typ tvůrce definuje operace, které jsou k dispozici pro výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="b2fa6-122">Viz [Vytvoření nového typu výpočetního výrazu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="b2fa6-123">Přehled syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2fa6-123">Syntax overview</span></span>

<span data-ttu-id="b2fa6-124">Všechny výpočetní výrazy mají následující tvar:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="b2fa6-125">kde `builder-expr` je název typu tvůrce, který definuje výpočetní výraz `cexper` a je tělem výrazu výrazu výpočtového výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="b2fa6-126">Kód výrazu `async` výpočtu může například vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="b2fa6-127">V rámci výpočtového výrazu je k dispozici speciální další syntaxe, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="b2fa6-128">Následující formuláře výrazů jsou možné s výpočetními výrazy:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="b2fa6-129">Každé z těchto klíčových slov a další standardní klíčová slova Jazyka F# jsou k dispozici pouze ve výpočtovém výrazu, pokud byla definována v typu tvůrce zálohování.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="b2fa6-130">Jedinou výjimkou je `match!`, což je samo o `let!` sobě syntaktický cukr pro použití následovaný vzor emblém na výsledek.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="b2fa6-131">Typ tvůrce je objekt, který definuje speciální metody, které řídí způsob, jakým jsou kombinovány fragmenty výrazu výpočtu; to znamená, že jeho metody řídí chování výpočtového výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="b2fa6-132">Dalším způsobem, jak popsat třídu tvůrce, je říci, že umožňuje přizpůsobit provoz mnoha konstrukcí F#, jako jsou smyčky a vazby.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="b2fa6-133">Klíčové `let!` slovo sváže výsledek volání na jiný výpočetní výraz s názvem:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="b2fa6-134">Pokud svážete volání s výrazem `let`výpočtu s , nezískáte výsledek výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="b2fa6-135">Místo toho budete mít vázané hodnoty *nerealizované* volání tohoto výpočtu výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="b2fa6-136">Slouží `let!` k vazbě na výsledek.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="b2fa6-137">`let!`je definován `Bind(x, f)` členem na typu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="b2fa6-138">Klíčové `do!` slovo je pro volání výpočetní výraz, který vrátí `unit`-like typ (definované `Zero` člen na tvůrce):</span><span class="sxs-lookup"><span data-stu-id="b2fa6-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="b2fa6-139">Pro [asynchronní pracovní](asynchronous-workflows.md)postup `Async<unit>`je tento typ .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="b2fa6-140">Pro ostatní výpočetní výrazy je pravděpodobně typ `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="b2fa6-141">`do!`je definován `Bind(x, f)` členem na typu tvůrce, `f` kde `unit`vzniká .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="b2fa6-142">Klíčové `yield` slovo je pro vrácení hodnoty z výpočtového výrazu tak, <xref:System.Collections.Generic.IEnumerable%601>aby mohla být spotřebována jako :</span><span class="sxs-lookup"><span data-stu-id="b2fa6-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="b2fa6-143">Ve většině případů jej mohou volající vynechat.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="b2fa6-144">Nejběžnější způsob, jak vynechat, `yield` je `->` s operátorem:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="b2fa6-145">Pro složitější výrazy, které by mohly přinést mnoho různých hodnot a možná podmíněně, jednoduše vynechání klíčové slovo může udělat:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="b2fa6-146">Stejně jako [u yield klíčové slovo v C#](../../csharp/language-reference/keywords/yield.md), každý prvek ve výpočtu výrazu je výnosný zpět, jak je iterováno.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="b2fa6-147">`yield`je definován `Yield(x)` členem na typu tvůrce, kde je položka, která `x` má být výnosná.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="b2fa6-148">Klíčové `yield!` slovo je pro sloučení kolekce hodnot z výpočtového výrazu:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="b2fa6-149">Při vyhodnocení bude mít výraz `yield!` výpočtu volaný položky, které jsou výnosné jeden po druhém, a výsledek se sloučí.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="b2fa6-150">`yield!`je definován `YieldFrom(x)` členem na typu tvůrce, kde `x` je kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="b2fa6-151">Na `yield` `yield!` rozdíl od , musí být explicitně zadán.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="b2fa6-152">Jeho chování není implicitní ve výpočtových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="b2fa6-153">Klíčové `return` slovo zabalí hodnotu v typu odpovídajícím výpočetnímu výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="b2fa6-154">Kromě používaných výpočetních `yield`výrazů se používá k "dokončení" výpočtu výrazu:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="b2fa6-155">`return`je definován `Return(x)` členem na typu tvůrce, kde je položka, kterou `x` má být zalamována.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="b2fa6-156">Klíčové `return!` slovo realizuje hodnotu výpočetního výrazu a obtéká, které mají za následek typ odpovídající výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="b2fa6-157">`return!`je definován `ReturnFrom(x)` členem na typu tvůrce, kde `x` je jiný výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="b2fa6-158">Klíčové `match!` slovo umožňuje vložit volání na jiný výpočetní výraz a vzor odpovídá jeho výsledku:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="b2fa6-159">Při volání výpočtu výraz `match!`s , bude realizovat výsledek `let!`volání jako .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="b2fa6-160">To se často používá při volání výpočetního výrazu, kde je výsledkem [volitelné](options.md).</span><span class="sxs-lookup"><span data-stu-id="b2fa6-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="b2fa6-161">Předdefinované výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="b2fa6-161">Built-in computation expressions</span></span>

<span data-ttu-id="b2fa6-162">Základní knihovna Jazyka F# definuje tři předdefinované výpočetní výrazy: [Sekvenční výrazy](sequences.md), [Asynchronní pracovní postupy](asynchronous-workflows.md)a [Výrazy dotazu](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b2fa6-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="b2fa6-163">Vytvoření nového typu výpočetního výrazu</span><span class="sxs-lookup"><span data-stu-id="b2fa6-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="b2fa6-164">Můžete definovat charakteristiky vlastní výpočetní výrazy vytvořením třídy tvůrce a definováním určitých speciálních metod ve třídě.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="b2fa6-165">Třída tvůrce může volitelně definovat metody uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="b2fa6-166">Následující tabulka popisuje metody, které lze použít ve třídě tvůrce pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="b2fa6-167">**Metoda**</span><span class="sxs-lookup"><span data-stu-id="b2fa6-167">**Method**</span></span>|<span data-ttu-id="b2fa6-168">**Typický podpis (podpisy)**</span><span class="sxs-lookup"><span data-stu-id="b2fa6-168">**Typical signature(s)**</span></span>|<span data-ttu-id="b2fa6-169">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b2fa6-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="b2fa6-170">Volal `let!` a `do!` ve výpočtu výrazy.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="b2fa6-171">Zalomí výraz výpočtu jako funkci.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="b2fa6-172">Voláno `return` ve výpočtových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="b2fa6-173">Voláno `return!` ve výpočtových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="b2fa6-174">`M<'T> -> M<'T>` nebo</span><span class="sxs-lookup"><span data-stu-id="b2fa6-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="b2fa6-175">Spustí výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="b2fa6-176">`M<'T> * M<'T> -> M<'T>` nebo</span><span class="sxs-lookup"><span data-stu-id="b2fa6-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="b2fa6-177">Nazývá se řazení ve výpočtových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="b2fa6-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` nebo</span><span class="sxs-lookup"><span data-stu-id="b2fa6-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="b2fa6-179">Voláno `for...do` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="b2fa6-180">Voláno `try...finally` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="b2fa6-181">Voláno `try...with` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="b2fa6-182">Volána `use` pro vazby ve výpočtových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="b2fa6-183">Voláno `while...do` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="b2fa6-184">Voláno `yield` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="b2fa6-185">Voláno `yield!` pro výrazy ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="b2fa6-186">Nazývá se `else` prázdné `if...then` větve výrazů ve výpočetních výrazech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="b2fa6-187">Označuje, že výpočetní výraz je `Run` předán členovi jako nabídka.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="b2fa6-188">Překládá všechny instance výpočtu do nabídky.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="b2fa6-189">Mnoho metod ve třídě tvůrce používá `M<'T>` a vrací konstrukci, což je obvykle samostatně definovaný typ, který charakterizuje druh `Async<'T>` výpočtů, které jsou `Seq<'T>` kombinovány, například pro asynchronní pracovní postupy a pro pracovní postupy sekvence.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="b2fa6-190">Podpisy těchto metod umožňují jejich kombinování a vnoření mezi sebou, takže objekt pracovního postupu vrácený z jedné konstrukce může být předán dalšímu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="b2fa6-191">Kompilátor při analýzách výpočtového výrazu převede výraz na řadu vnořených volání funkcí pomocí metod v předchozí tabulce a kódu ve výpočtovém výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="b2fa6-192">Vnořený výraz má následující tvar:</span><span class="sxs-lookup"><span data-stu-id="b2fa6-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="b2fa6-193">Ve výše uvedeném kódu `Run` `Delay` volání a jsou vynechány, pokud nejsou definovány ve třídě tvůrce výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="b2fa6-194">Tělo výrazu výpočtu, zde označené `{| cexpr |}`jako , je přeloženo do volání zahrnujících metody třídy tvůrce překlady popsanými v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="b2fa6-195">Výpočetní výraz `{| cexpr |}` je definován rekurzivně podle těchto `expr` překladů, kde `cexpr` je výraz F# a je výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="b2fa6-196">Expression</span><span class="sxs-lookup"><span data-stu-id="b2fa6-196">Expression</span></span>|<span data-ttu-id="b2fa6-197">Překlad</span><span class="sxs-lookup"><span data-stu-id="b2fa6-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="b2fa6-198">V předchozí tabulce `other-expr` popisuje výraz, který není jinak uveden v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="b2fa6-199">Třída tvůrce nemusí implementovat všechny metody a podporovat všechny překlady uvedené v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="b2fa6-200">Tyto konstrukce, které nejsou implementovány nejsou k dispozici ve výpočtu výrazy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="b2fa6-201">Například pokud nechcete podporovat `use` klíčové slovo ve výpočtu výrazy, můžete vynechat definici `Use` ve třídě tvůrce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="b2fa6-202">Následující příklad kódu ukazuje výpočetní výraz, který zapouzdřuje výpočtu jako řadu kroků, které lze vyhodnotit jeden krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="b2fa6-203">Discriminated union typu `OkOrException`, kóduje chybový stav výrazu, jak byl dosud vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="b2fa6-204">Tento kód ukazuje několik typické vzory, které můžete použít ve výpočtu výrazy, jako je například často používaný počet implementací některých metod tvůrce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="b2fa6-205">Výpočetní výraz má základní typ, který výraz vrátí.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="b2fa6-206">Základní typ může představovat vypočítaný výsledek nebo zpožděný výpočet, který lze provést, nebo může poskytnout způsob, jak iterát prostřednictvím některého typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="b2fa6-207">V předchozím příkladu byl základní typ **nakonec**.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="b2fa6-208">Pro sekvenční výraz <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>je základní typ .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2fa6-209">Pro výraz dotazu je <xref:System.Linq.IQueryable?displayProperty=nameWithType>základní typ .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2fa6-210">Pro asynchronní pracovní postup je [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)základní typ .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="b2fa6-211">Objekt `Async` představuje práci, která má být provedena k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="b2fa6-212">Například volání [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) provést výpočtu a vrátit výsledek.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="b2fa6-213">Vlastní operace</span><span class="sxs-lookup"><span data-stu-id="b2fa6-213">Custom Operations</span></span>

<span data-ttu-id="b2fa6-214">Můžete definovat vlastní operaci na výpočetní výraz a použít vlastní operaci jako operátor ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="b2fa6-215">Můžete například zahrnout operátor dotazu do výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="b2fa6-216">Při definování vlastní operace je nutné definovat metody Yield a For ve výpočetním výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="b2fa6-217">Chcete-li definovat vlastní operaci, vložte ji do třídy tvůrce [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)pro výpočetní výraz a potom použijte .</span><span class="sxs-lookup"><span data-stu-id="b2fa6-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="b2fa6-218">Tento atribut má řetězec jako argument, což je název, který má být použit ve vlastní operaci.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="b2fa6-219">Tento název přichází do oboru na začátku otevření složené závorky výpočtového výrazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="b2fa6-220">Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="b2fa6-221">Vyhněte se například použití `all` identifikátorů, jako jsou výrazy dotazu nebo `last` ve výrazech dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="b2fa6-222">Rozšíření stávajících stavitelů o nové vlastní operace</span><span class="sxs-lookup"><span data-stu-id="b2fa6-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="b2fa6-223">Pokud již máte třídu tvůrce, jeho vlastní operace lze rozšířit z mimo tuto třídu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="b2fa6-224">Rozšíření musí být deklarována v modulech.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="b2fa6-225">Obory názvů nesmí obsahovat členy přípony s výjimkou stejného souboru a stejné skupiny deklarací oboru názvů, kde je definován typ.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="b2fa6-226">Následující příklad ukazuje rozšíření existující `Microsoft.FSharp.Linq.QueryBuilder` třídy.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="b2fa6-227">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2fa6-227">See also</span></span>

- [<span data-ttu-id="b2fa6-228">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b2fa6-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b2fa6-229">Asynchronní pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="b2fa6-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="b2fa6-230">Sekvence</span><span class="sxs-lookup"><span data-stu-id="b2fa6-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="b2fa6-231">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="b2fa6-231">Query Expressions</span></span>](query-expressions.md)
