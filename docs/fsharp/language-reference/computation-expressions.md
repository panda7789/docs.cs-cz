---
title: Výpočetní výrazy
description: Naučte se vytvářet praktické syntaxe pro psaní výpočtů v F# , která může být sekvencovaná a kombinovaná pomocí konstrukcí a vazeb toku řízení.
ms.date: 03/15/2019
ms.openlocfilehash: 9222be5a585914761d3001d6649b196030eec05e
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083060"
---
# <a name="computation-expressions"></a><span data-ttu-id="dab68-103">Výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="dab68-103">Computation Expressions</span></span>

<span data-ttu-id="dab68-104">Výrazy výpočtů v F# poskytují pohodlný Syntax pro zápis výpočtů, které lze sekvencovat a kombinovat pomocí konstrukcí a vazeb toku řízení.</span><span class="sxs-lookup"><span data-stu-id="dab68-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="dab68-105">V závislosti na druhu výpočetního výrazu je možné si je představit jako způsob, jak vyjádřit monádami, monoids, Monad transformátory a Applicative funktory.</span><span class="sxs-lookup"><span data-stu-id="dab68-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="dab68-106">Na rozdíl od jiných jazyků (například in *-Notation* v Haskell) se však nevztahují na jednu abstrakci a nespoléhají na makra nebo jiné formy metaprogramování šablonou k dosažení praktické a kontextové syntaxe.</span><span class="sxs-lookup"><span data-stu-id="dab68-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="dab68-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="dab68-107">Overview</span></span>

<span data-ttu-id="dab68-108">Výpočty mohou trvat mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="dab68-108">Computations can take many forms.</span></span> <span data-ttu-id="dab68-109">Nejběžnější forma výpočtů je spuštění s jedním vláknem, které je snadné pochopit a upravit.</span><span class="sxs-lookup"><span data-stu-id="dab68-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="dab68-110">Ale ne všechny formy výpočtů jsou jednoduché jako provádění s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="dab68-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="dab68-111">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="dab68-111">Some examples include:</span></span>

- <span data-ttu-id="dab68-112">Nedeterministické výpočty</span><span class="sxs-lookup"><span data-stu-id="dab68-112">Non-deterministic computations</span></span>
- <span data-ttu-id="dab68-113">Asynchronní výpočty</span><span class="sxs-lookup"><span data-stu-id="dab68-113">Asynchronous computations</span></span>
- <span data-ttu-id="dab68-114">Ovlivněné výpočty</span><span class="sxs-lookup"><span data-stu-id="dab68-114">Effectful computations</span></span>
- <span data-ttu-id="dab68-115">Regenerační výpočty</span><span class="sxs-lookup"><span data-stu-id="dab68-115">Generative computations</span></span>

<span data-ttu-id="dab68-116">Obecně platí, že existují výpočty *závislé na kontextu* , které je nutné provést v určitých částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="dab68-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="dab68-117">Psaní kódu závislého na kontextu může být náročné, protože je snadné "nevracení" výpočtů mimo daný kontext bez abstrakcí, abyste se mohli vyhnout.</span><span class="sxs-lookup"><span data-stu-id="dab68-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="dab68-118">Tyto abstrakce jsou často náročné na to, aby je bylo možné napsat F# sami, což znamená, proč má zobecněný způsob, kterým se říká **výpočetní výrazy**.</span><span class="sxs-lookup"><span data-stu-id="dab68-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="dab68-119">Výrazy výpočtu nabízejí jednotnou syntaxi a abstraktní model pro kódování závislé na kontextu.</span><span class="sxs-lookup"><span data-stu-id="dab68-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="dab68-120">Každý výraz výpočtu je zálohovaný typem *Tvůrce* .</span><span class="sxs-lookup"><span data-stu-id="dab68-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="dab68-121">Typ Tvůrce definuje operace, které jsou k dispozici pro výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="dab68-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="dab68-122">Viz [Vytvoření nového typu výpočetního výrazu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výraz výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="dab68-123">Přehled syntaxe</span><span class="sxs-lookup"><span data-stu-id="dab68-123">Syntax overview</span></span>

<span data-ttu-id="dab68-124">Všechny výpočetní výrazy mají následující formát:</span><span class="sxs-lookup"><span data-stu-id="dab68-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="dab68-125">kde `builder-expr` je název typu tvůrce, který definuje výraz výpočtu a `cexper` je tělo výrazu výpočetního výrazu.</span><span class="sxs-lookup"><span data-stu-id="dab68-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="dab68-126">Například kód výrazu `async` výpočtu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dab68-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="dab68-127">Ve výrazu výpočtu je k dispozici speciální další syntaxe, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="dab68-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="dab68-128">Ve výrazech výpočtu lze použít následující formuláře výrazů:</span><span class="sxs-lookup"><span data-stu-id="dab68-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="dab68-129">Každé z těchto klíčových slov a další klíčová slova standard F# jsou k dispozici pouze ve výrazu výpočtu, pokud byly definovány v typu zálohování.</span><span class="sxs-lookup"><span data-stu-id="dab68-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="dab68-130">Jedinou výjimkou je `match!`to, což je samotný syntaktický cukr pro `let!` použití následovaný porovnáváním vzorů ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="dab68-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="dab68-131">Typ Tvůrce je objekt, který definuje speciální metody, které určují způsob, jakým jsou kombinovány fragmenty výpočetního výrazu. To znamená, že jeho metody řídí, jak se výraz výpočtu chová.</span><span class="sxs-lookup"><span data-stu-id="dab68-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="dab68-132">Dalším způsobem, jak popsat třídu tvůrce, je říci, že umožňuje přizpůsobit operaci mnoha F# konstrukcí, jako jsou smyčky a vazby.</span><span class="sxs-lookup"><span data-stu-id="dab68-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="dab68-133">`let!` Klíčové slovo váže výsledek volání do jiného výpočetního výrazu do názvu:</span><span class="sxs-lookup"><span data-stu-id="dab68-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="dab68-134">Pokud svážete volání výrazu výpočtu s `let`, nebudete mít výsledek výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="dab68-135">Místo toho budete mít vazbu na hodnotu *nerealizovaného* volání tohoto výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="dab68-136">Slouží `let!` k vytvoření vazby na výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab68-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="dab68-137">`let!`je definována `Bind(x, f)` členem na typu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="dab68-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="dab68-138">Klíčové slovo je pro volání výrazu výpočtu, který `unit`vrací `Zero` typ podobný (definovaný členem na tvůrci): `do!`</span><span class="sxs-lookup"><span data-stu-id="dab68-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="dab68-139">Pro [asynchronní pracovní postup](asynchronous-workflows.md)je `Async<unit>`tento typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="dab68-140">Pro jiné výpočetní výrazy je typ pravděpodobně `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="dab68-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="dab68-141">`do!`je definována `Bind(x, f)` členem na typu tvůrce, kde `f` vytvoří `unit`.</span><span class="sxs-lookup"><span data-stu-id="dab68-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="dab68-142">Klíčové slovo slouží k vrácení hodnoty z výrazu výpočtu, aby ji bylo možné spotřebovat <xref:System.Collections.Generic.IEnumerable%601>jako: `yield`</span><span class="sxs-lookup"><span data-stu-id="dab68-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="dab68-143">Stejně jako u [klíčového slova C#yield v ](../../csharp/language-reference/keywords/yield.md)je každý prvek ve výrazu výpočtu vrácen zpět při iteraci.</span><span class="sxs-lookup"><span data-stu-id="dab68-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="dab68-144">`yield`je definována `Yield(x)` členem na typu tvůrce, kde `x` je položka, která má být vrácena.</span><span class="sxs-lookup"><span data-stu-id="dab68-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="dab68-145">`yield!` Klíčové slovo je pro sloučení kolekce hodnot z výpočetního výrazu:</span><span class="sxs-lookup"><span data-stu-id="dab68-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="dab68-146">Při vyhodnocování je výsledkem výrazu `yield!` výpočtu, který má za následek, že jeho položky budou vracet jeden po jedné a sloučí výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab68-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="dab68-147">`yield!`je definována `YieldFrom(x)` členem na typu tvůrce, kde `x` je kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="dab68-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="dab68-148">`return` Klíčové slovo obtéká hodnotu v typu odpovídajícím výpočetnímu výrazu.</span><span class="sxs-lookup"><span data-stu-id="dab68-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="dab68-149">Mimo použití `yield`výrazů výpočtu se používá k "dokončení" výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="dab68-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="dab68-150">`return`je definována `Return(x)` členem na typu tvůrce, kde `x` je položka, která má být zabalena.</span><span class="sxs-lookup"><span data-stu-id="dab68-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="dab68-151">`return!` Klíčové slovo realizuje hodnotu výrazu výpočtu a zalomí, jejichž výsledkem je typ odpovídající výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="dab68-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="dab68-152">`return!`je definována `ReturnFrom(x)` členem na typu tvůrce, kde `x` je jiný výraz výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="dab68-153">Počínaje F# 4,5, `match!` klíčové slovo umožňuje vložit volání do jiného výrazu výpočtu a porovnávání vzorů na výsledku:</span><span class="sxs-lookup"><span data-stu-id="dab68-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="dab68-154">Při volání výpočetního výrazu s `match!`, bude zapomenout výsledek volání jako. `let!`</span><span class="sxs-lookup"><span data-stu-id="dab68-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="dab68-155">To se často používá při volání výrazu výpočtu, kde výsledek je [nepovinný](options.md).</span><span class="sxs-lookup"><span data-stu-id="dab68-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="dab68-156">Předdefinované výrazy výpočtů</span><span class="sxs-lookup"><span data-stu-id="dab68-156">Built-in computation expressions</span></span>

<span data-ttu-id="dab68-157">F# Základní knihovna definuje tři předdefinované výpočetní výrazy: [Výrazy sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výrazy dotazů](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="dab68-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="dab68-158">Vytvoření nového typu výrazu výpočtu</span><span class="sxs-lookup"><span data-stu-id="dab68-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="dab68-159">Můžete definovat charakteristiky vlastních výrazů výpočtu vytvořením třídy tvůrce a definováním určitých speciálních metod pro třídu.</span><span class="sxs-lookup"><span data-stu-id="dab68-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="dab68-160">Třída tvůrce může volitelně definovat metody, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dab68-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="dab68-161">Následující tabulka popisuje metody, které lze použít ve třídě tvůrce pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dab68-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="dab68-162">**– Metoda**</span><span class="sxs-lookup"><span data-stu-id="dab68-162">**Method**</span></span>|<span data-ttu-id="dab68-163">**Typické podpisy**</span><span class="sxs-lookup"><span data-stu-id="dab68-163">**Typical signature(s)**</span></span>|<span data-ttu-id="dab68-164">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dab68-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="dab68-165">Volá se `let!` pro `do!` a ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="dab68-166">Zabalí výraz výpočtu jako funkci.</span><span class="sxs-lookup"><span data-stu-id="dab68-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="dab68-167">Volá se `return` pro ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="dab68-168">Volá se `return!` pro ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="dab68-169">`M<'T> -> M<'T>`ani</span><span class="sxs-lookup"><span data-stu-id="dab68-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="dab68-170">Provede výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="dab68-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="dab68-171">`M<'T> * M<'T> -> M<'T>`ani</span><span class="sxs-lookup"><span data-stu-id="dab68-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="dab68-172">Volá se pro sekvencování ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="dab68-173">`seq<'T> * ('T -> M<'U>) -> M<'U>`ani</span><span class="sxs-lookup"><span data-stu-id="dab68-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="dab68-174">Volá se `for...do` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="dab68-175">Volá se `try...finally` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="dab68-176">Volá se `try...with` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="dab68-177">Volá se `use` pro vazby ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="dab68-178">Volá se `while...do` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="dab68-179">Volá se `yield` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="dab68-180">Volá se `yield!` pro výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="dab68-181">Volá se pro `else` prázdné `if...then` větve výrazů ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="dab68-182">Označuje, že výraz výpočtu je předán `Run` členu jako citace.</span><span class="sxs-lookup"><span data-stu-id="dab68-182">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="dab68-183">Převede všechny instance výpočtu do citace.</span><span class="sxs-lookup"><span data-stu-id="dab68-183">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="dab68-184">Mnohé z metod ve třídě tvůrce používají a vracejí `M<'T>` konstrukce, což je obvykle samostatně definovaný typ, který charakterizuje druh výpočtů, které jsou kombinovány, `Async<'T>` například pro asynchronní pracovní postupy a `Seq<'T>` pro sekvenční pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="dab68-184">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="dab68-185">Signatury těchto metod umožňují, aby byly vzájemně kombinovány a vnořeny, takže objekt pracovního postupu vrácený z jedné konstrukce lze předat dalšímu.</span><span class="sxs-lookup"><span data-stu-id="dab68-185">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="dab68-186">Kompilátor při analýze výrazu výpočtu Převede výraz na řadu vnořených volání funkcí pomocí metod v předchozí tabulce a kódu ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-186">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="dab68-187">Vnořený výraz má následující tvar:</span><span class="sxs-lookup"><span data-stu-id="dab68-187">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="dab68-188">Ve výše uvedeném kódu jsou volání `Run` a `Delay` vynechána, pokud nejsou definovány ve třídě Tvůrce výrazů výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-188">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="dab68-189">Tělo výrazu výpočtu, zde označovaného jako `{| cexpr |}`, je přeloženo na volání týkající se metod třídy tvůrce pomocí překladů popsaných v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dab68-189">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="dab68-190">Výraz `{| cexpr |}` výpočtu je definován rekurzivně podle těchto překladů, kde `expr` je F# výraz a `cexpr` výrazem výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-190">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="dab68-191">Výraz</span><span class="sxs-lookup"><span data-stu-id="dab68-191">Expression</span></span>|<span data-ttu-id="dab68-192">Překlad</span><span class="sxs-lookup"><span data-stu-id="dab68-192">Translation</span></span>|
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
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
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

<span data-ttu-id="dab68-193">V předchozí tabulce `other-expr` popisuje výraz, který není jinak uveden v tabulce.</span><span class="sxs-lookup"><span data-stu-id="dab68-193">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="dab68-194">Třída tvůrce nemusí implementovat všechny metody a podporovat všechny překlady uvedené v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="dab68-194">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="dab68-195">Tyto konstrukce, které nejsou implementovány, nejsou k dispozici ve výrazech výpočtu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="dab68-195">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="dab68-196">Například pokud nechcete podporovat `use` klíčové slovo ve výrazech výpočtu, můžete vynechat `Use` definici ve třídě tvůrce.</span><span class="sxs-lookup"><span data-stu-id="dab68-196">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="dab68-197">Následující příklad kódu ukazuje výraz výpočtu, který zapouzdřuje výpočet jako řadu kroků, které lze vyhodnotit v jednom kroku.</span><span class="sxs-lookup"><span data-stu-id="dab68-197">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="dab68-198">Typ `OkOrException`rozlišeného sjednocení, zakóduje chybový stav výrazu jako dosud vyhodnocený.</span><span class="sxs-lookup"><span data-stu-id="dab68-198">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="dab68-199">Tento kód ukazuje několik typických vzorů, které lze použít ve výrazech výpočtů, jako jsou například často používané implementace některých metod Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="dab68-199">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="dab68-200">Výraz výpočtu má základní typ, který vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="dab68-200">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="dab68-201">Nadřízený typ může představovat vypočítaný výsledek nebo zpožděné výpočty, které lze provést, nebo může poskytnout způsob, jak iterovat v některém typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="dab68-201">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="dab68-202">V předchozím příkladu byl **nakonec**základní typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-202">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="dab68-203">Pro výraz sekvence je <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>základní typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-203">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dab68-204">Pro výraz dotazu je <xref:System.Linq.IQueryable?displayProperty=nameWithType>základní typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-204">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dab68-205">Pro asynchronní pracovní postup je [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)základní typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-205">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="dab68-206">`Async` Objekt představuje práci, která má být provedena k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="dab68-206">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="dab68-207">Například zavoláte [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) k provedení výpočtu a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab68-207">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="dab68-208">Vlastní operace</span><span class="sxs-lookup"><span data-stu-id="dab68-208">Custom Operations</span></span>

<span data-ttu-id="dab68-209">Můžete definovat vlastní operaci na výpočetním výrazu a použít vlastní operaci jako operátor ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-209">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="dab68-210">Do výrazu dotazu můžete například zahrnout operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="dab68-210">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="dab68-211">Při definování vlastní operace je nutné definovat yield a metody ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-211">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="dab68-212">Chcete-li definovat vlastní operaci, vložte ji do třídy tvůrce pro výraz výpočtu a pak použijte [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="dab68-212">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="dab68-213">Tento atribut přebírá řetězec jako argument, což je název, který se má použít ve vlastní operaci.</span><span class="sxs-lookup"><span data-stu-id="dab68-213">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="dab68-214">Tento název se nachází v rozsahu na začátku počáteční složené závorky výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="dab68-214">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="dab68-215">Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="dab68-215">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="dab68-216">Vyhněte se například použití identifikátorů, jako jsou `all` nebo `last` ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="dab68-216">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="dab68-217">Rozšíření stávajících tvůrců s novými vlastními operacemi</span><span class="sxs-lookup"><span data-stu-id="dab68-217">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="dab68-218">Pokud již máte třídu tvůrce, její vlastní operace lze rozšířit mimo tuto třídu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="dab68-218">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="dab68-219">V modulech musí být deklarována rozšíření.</span><span class="sxs-lookup"><span data-stu-id="dab68-219">Extensions must be declared in modules.</span></span> <span data-ttu-id="dab68-220">Obory názvů nemůžou obsahovat členy rozšíření kromě stejného souboru a stejné skupiny deklarací oboru názvů, kde je definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="dab68-220">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="dab68-221">Následující příklad ukazuje rozšíření existující `Microsoft.FSharp.Linq.QueryBuilder` třídy.</span><span class="sxs-lookup"><span data-stu-id="dab68-221">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="dab68-222">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab68-222">See also</span></span>

- [<span data-ttu-id="dab68-223">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="dab68-223">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="dab68-224">Asynchronní pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="dab68-224">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="dab68-225">Sekvence</span><span class="sxs-lookup"><span data-stu-id="dab68-225">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="dab68-226">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="dab68-226">Query Expressions</span></span>](query-expressions.md)
