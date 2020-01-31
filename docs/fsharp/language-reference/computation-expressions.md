---
title: Výpočetní výrazy
description: Naučte se vytvářet praktické syntaxe pro psaní výpočtů v F# , která může být sekvencovaná a kombinovaná pomocí konstrukcí a vazeb toku řízení.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794552"
---
# <a name="computation-expressions"></a><span data-ttu-id="db085-103">Výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="db085-103">Computation Expressions</span></span>

<span data-ttu-id="db085-104">Výrazy výpočtů v F# poskytují pohodlný Syntax pro zápis výpočtů, které lze sekvencovat a kombinovat pomocí konstrukcí a vazeb toku řízení.</span><span class="sxs-lookup"><span data-stu-id="db085-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="db085-105">V závislosti na druhu výpočetního výrazu je možné si je představit jako způsob, jak vyjádřit monádami, monoids, Monad transformátory a Applicative funktory.</span><span class="sxs-lookup"><span data-stu-id="db085-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="db085-106">Na rozdíl od jiných jazyků (například in *-Notation* v Haskell) se však nevztahují na jednu abstrakci a nespoléhají na makra nebo jiné formy metaprogramování šablonou k dosažení praktické a kontextové syntaxe.</span><span class="sxs-lookup"><span data-stu-id="db085-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="db085-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="db085-107">Overview</span></span>

<span data-ttu-id="db085-108">Výpočty mohou trvat mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="db085-108">Computations can take many forms.</span></span> <span data-ttu-id="db085-109">Nejběžnější forma výpočtů je spuštění s jedním vláknem, které je snadné pochopit a upravit.</span><span class="sxs-lookup"><span data-stu-id="db085-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="db085-110">Ale ne všechny formy výpočtů jsou jednoduché jako provádění s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="db085-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="db085-111">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="db085-111">Some examples include:</span></span>

- <span data-ttu-id="db085-112">Nedeterministické výpočty</span><span class="sxs-lookup"><span data-stu-id="db085-112">Non-deterministic computations</span></span>
- <span data-ttu-id="db085-113">Asynchronní výpočty</span><span class="sxs-lookup"><span data-stu-id="db085-113">Asynchronous computations</span></span>
- <span data-ttu-id="db085-114">Ovlivněné výpočty</span><span class="sxs-lookup"><span data-stu-id="db085-114">Effectful computations</span></span>
- <span data-ttu-id="db085-115">Regenerační výpočty</span><span class="sxs-lookup"><span data-stu-id="db085-115">Generative computations</span></span>

<span data-ttu-id="db085-116">Obecně platí, že existují výpočty *závislé na kontextu* , které je nutné provést v určitých částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="db085-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="db085-117">Psaní kódu závislého na kontextu může být náročné, protože je snadné "nevracení" výpočtů mimo daný kontext bez abstrakcí, abyste se mohli vyhnout.</span><span class="sxs-lookup"><span data-stu-id="db085-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="db085-118">Tyto abstrakce jsou často náročné na to, aby je bylo možné napsat F# sami, což znamená, proč má zobecněný způsob, kterým se říká **výpočetní výrazy**.</span><span class="sxs-lookup"><span data-stu-id="db085-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="db085-119">Výrazy výpočtu nabízejí jednotnou syntaxi a abstraktní model pro kódování závislé na kontextu.</span><span class="sxs-lookup"><span data-stu-id="db085-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="db085-120">Každý výraz výpočtu je zálohovaný typem *Tvůrce* .</span><span class="sxs-lookup"><span data-stu-id="db085-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="db085-121">Typ Tvůrce definuje operace, které jsou k dispozici pro výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="db085-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="db085-122">Viz [Vytvoření nového typu výpočetního výrazu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výraz výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="db085-123">Přehled syntaxe</span><span class="sxs-lookup"><span data-stu-id="db085-123">Syntax overview</span></span>

<span data-ttu-id="db085-124">Všechny výpočetní výrazy mají následující formát:</span><span class="sxs-lookup"><span data-stu-id="db085-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="db085-125">kde `builder-expr` je název typu tvůrce, který definuje výraz výpočtu a `cexper` je tělo výrazu výpočtu výrazu.</span><span class="sxs-lookup"><span data-stu-id="db085-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="db085-126">Například kód výrazu výpočtu `async` může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="db085-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="db085-127">Ve výrazu výpočtu je k dispozici speciální další syntaxe, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="db085-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="db085-128">Ve výrazech výpočtu lze použít následující formuláře výrazů:</span><span class="sxs-lookup"><span data-stu-id="db085-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="db085-129">Každé z těchto klíčových slov a další klíčová slova standard F# jsou k dispozici pouze ve výrazu výpočtu, pokud byly definovány v typu zálohování.</span><span class="sxs-lookup"><span data-stu-id="db085-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="db085-130">Jedinou výjimkou je `match!`, což je vlastní syntaktický cukr pro použití `let!` následovaný porovnáváním vzorů ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="db085-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="db085-131">Typ Tvůrce je objekt, který definuje speciální metody, které určují způsob, jakým jsou kombinovány fragmenty výpočetního výrazu. To znamená, že jeho metody řídí, jak se výraz výpočtu chová.</span><span class="sxs-lookup"><span data-stu-id="db085-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="db085-132">Dalším způsobem, jak popsat třídu tvůrce, je říci, že umožňuje přizpůsobit operaci mnoha F# konstrukcí, jako jsou smyčky a vazby.</span><span class="sxs-lookup"><span data-stu-id="db085-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="db085-133">Klíčové slovo `let!` váže výsledek volání do jiného výpočetního výrazu do názvu:</span><span class="sxs-lookup"><span data-stu-id="db085-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="db085-134">Pokud svážete volání výrazu výpočtu s `let`, nebudete mít výsledek výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="db085-135">Místo toho budete mít vazbu na hodnotu *nerealizovaného* volání tohoto výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="db085-136">K vytvoření vazby na výsledek použijte `let!`.</span><span class="sxs-lookup"><span data-stu-id="db085-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="db085-137">`let!` definuje člen `Bind(x, f)` na typu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="db085-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="db085-138">Klíčové slovo `do!` je určeno pro volání výrazu výpočtu, který vrací typ `unit`typu (definovaný členem `Zero` na tvůrci):</span><span class="sxs-lookup"><span data-stu-id="db085-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="db085-139">Pro [asynchronní pracovní postup](asynchronous-workflows.md)je tento typ `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="db085-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="db085-140">Pro jiné výpočetní výrazy je typ pravděpodobně `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="db085-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="db085-141">`do!` je definována `Bind(x, f)` členem na typu tvůrce, kde `f` vytvoří `unit`.</span><span class="sxs-lookup"><span data-stu-id="db085-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="db085-142">Klíčové slovo `yield` slouží k vrácení hodnoty z výrazu výpočtu, aby ji bylo možné spotřebovat jako <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="db085-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="db085-143">Ve většině případů je lze vynechat volajícími.</span><span class="sxs-lookup"><span data-stu-id="db085-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="db085-144">Nejběžnější způsob, jak vypustit `yield`, je pomocí operátoru `->`:</span><span class="sxs-lookup"><span data-stu-id="db085-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="db085-145">U složitějších výrazů, které by mohly vracet mnoho různých hodnot a možná podmíněně, stačí vynechat klíčové slovo, které může:</span><span class="sxs-lookup"><span data-stu-id="db085-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

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

<span data-ttu-id="db085-146">Stejně jako u [klíčového slova C#yield v ](../../csharp/language-reference/keywords/yield.md)je každý prvek ve výrazu výpočtu vrácen zpět při iteraci.</span><span class="sxs-lookup"><span data-stu-id="db085-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="db085-147">`yield` je definována `Yield(x)` členem na typu tvůrce, kde `x` je položka, která se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="db085-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="db085-148">Klíčové slovo `yield!` slouží ke sloučení kolekce hodnot z výpočetního výrazu:</span><span class="sxs-lookup"><span data-stu-id="db085-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="db085-149">Při vyhodnocování je výsledkem výrazu výpočtu, který vyvolal `yield!`, jeho položky zpět po jednom, které budou shrnuty do výsledku.</span><span class="sxs-lookup"><span data-stu-id="db085-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="db085-150">`yield!` je definována `YieldFrom(x)` členem na typu tvůrce, kde `x` je kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="db085-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="db085-151">Na rozdíl od `yield`je třeba explicitně zadat `yield!`.</span><span class="sxs-lookup"><span data-stu-id="db085-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="db085-152">Jeho chování není ve výrazech výpočtu implicitní.</span><span class="sxs-lookup"><span data-stu-id="db085-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="db085-153">Klíčové slovo `return` obtéká hodnotu v typu odpovídajícím výpočetnímu výrazu.</span><span class="sxs-lookup"><span data-stu-id="db085-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="db085-154">Kromě výrazů výpočtu, které používají `yield`, se používá k "dokončení" výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="db085-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="db085-155">`return` je definována `Return(x)` členem na typu tvůrce, kde `x` je položka, která se má zabalit.</span><span class="sxs-lookup"><span data-stu-id="db085-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="db085-156">Klíčové slovo `return!` realizuje hodnotu výrazu výpočtu a zabalí, jejichž výsledkem je typ odpovídající výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="db085-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="db085-157">`return!` je definována `ReturnFrom(x)` členem na typu tvůrce, kde `x` je jiný výraz výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="db085-158">Klíčové slovo `match!` umožňuje vložené volání do jiného výrazu výpočtu a porovnávání vzorů na jeho výsledku:</span><span class="sxs-lookup"><span data-stu-id="db085-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="db085-159">Při volání výrazu výpočtu se `match!`, bude mít výsledek volání jako `let!`.</span><span class="sxs-lookup"><span data-stu-id="db085-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="db085-160">To se často používá při volání výrazu výpočtu, kde výsledek je [nepovinný](options.md).</span><span class="sxs-lookup"><span data-stu-id="db085-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="db085-161">Předdefinované výrazy výpočtů</span><span class="sxs-lookup"><span data-stu-id="db085-161">Built-in computation expressions</span></span>

<span data-ttu-id="db085-162">F# Základní knihovna definuje tři předdefinované výpočetní výrazy: [výrazy sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výrazy dotazů](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="db085-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="db085-163">Vytvoření nového typu výrazu výpočtu</span><span class="sxs-lookup"><span data-stu-id="db085-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="db085-164">Můžete definovat charakteristiky vlastních výrazů výpočtu vytvořením třídy tvůrce a definováním určitých speciálních metod pro třídu.</span><span class="sxs-lookup"><span data-stu-id="db085-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="db085-165">Třída tvůrce může volitelně definovat metody, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="db085-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="db085-166">Následující tabulka popisuje metody, které lze použít ve třídě tvůrce pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="db085-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="db085-167">**– Metoda**</span><span class="sxs-lookup"><span data-stu-id="db085-167">**Method**</span></span>|<span data-ttu-id="db085-168">**Typické podpisy**</span><span class="sxs-lookup"><span data-stu-id="db085-168">**Typical signature(s)**</span></span>|<span data-ttu-id="db085-169">**Popis**</span><span class="sxs-lookup"><span data-stu-id="db085-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="db085-170">Volá se pro `let!` a `do!` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="db085-171">Zabalí výraz výpočtu jako funkci.</span><span class="sxs-lookup"><span data-stu-id="db085-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="db085-172">Volá se pro `return` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="db085-173">Volá se pro `return!` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="db085-174">`M<'T> -> M<'T>` nebo</span><span class="sxs-lookup"><span data-stu-id="db085-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="db085-175">Provede výpočetní výraz.</span><span class="sxs-lookup"><span data-stu-id="db085-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="db085-176">`M<'T> * M<'T> -> M<'T>` nebo</span><span class="sxs-lookup"><span data-stu-id="db085-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="db085-177">Volá se pro sekvencování ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="db085-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` nebo</span><span class="sxs-lookup"><span data-stu-id="db085-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="db085-179">Volá se pro `for...do` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="db085-180">Volá se pro `try...finally` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="db085-181">Volá se pro `try...with` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="db085-182">Volá se pro `use` vazby ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="db085-183">Volá se pro `while...do` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="db085-184">Volá se pro `yield` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="db085-185">Volá se pro `yield!` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="db085-186">Volá se pro prázdné `else` větve `if...then` výrazů ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="db085-187">Označuje, že výraz výpočtu je předán členu `Run` jako citace.</span><span class="sxs-lookup"><span data-stu-id="db085-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="db085-188">Převede všechny instance výpočtu do citace.</span><span class="sxs-lookup"><span data-stu-id="db085-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="db085-189">Mnoho metod ve třídě tvůrce používá a vrací `M<'T>` konstrukce, což je obvykle samostatně definovaný typ, který charakterizuje druh výpočtů, které jsou kombinovány, například `Async<'T>` pro asynchronní pracovní postupy a `Seq<'T>` pro pracovní postupy sekvence.</span><span class="sxs-lookup"><span data-stu-id="db085-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="db085-190">Signatury těchto metod umožňují, aby byly vzájemně kombinovány a vnořeny, takže objekt pracovního postupu vrácený z jedné konstrukce lze předat dalšímu.</span><span class="sxs-lookup"><span data-stu-id="db085-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="db085-191">Kompilátor při analýze výrazu výpočtu Převede výraz na řadu vnořených volání funkcí pomocí metod v předchozí tabulce a kódu ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="db085-192">Vnořený výraz má následující tvar:</span><span class="sxs-lookup"><span data-stu-id="db085-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="db085-193">Ve výše uvedeném kódu jsou volání `Run` a `Delay` vynechána, pokud nejsou definována ve třídě Tvůrce výrazů výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="db085-194">Tělo výrazu výpočtu, zde označovaného jako `{| cexpr |}`, je přeloženo do volání, která zahrnují metody třídy tvůrce, pomocí překladů popsaných v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="db085-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="db085-195">Výraz výpočtu `{| cexpr |}` je rekurzivně definován podle těchto překladů, kde `expr` je F# výraz a `cexpr` je výraz výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="db085-196">Výraz</span><span class="sxs-lookup"><span data-stu-id="db085-196">Expression</span></span>|<span data-ttu-id="db085-197">Překlad</span><span class="sxs-lookup"><span data-stu-id="db085-197">Translation</span></span>|
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

<span data-ttu-id="db085-198">V předchozí tabulce `other-expr` popisuje výraz, který není jinak uveden v tabulce.</span><span class="sxs-lookup"><span data-stu-id="db085-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="db085-199">Třída tvůrce nemusí implementovat všechny metody a podporovat všechny překlady uvedené v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="db085-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="db085-200">Tyto konstrukce, které nejsou implementovány, nejsou k dispozici ve výrazech výpočtu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="db085-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="db085-201">Například pokud nechcete podporovat klíčové slovo `use` ve výrazech výpočtu, můžete vynechat definici `Use` ve třídě tvůrce.</span><span class="sxs-lookup"><span data-stu-id="db085-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="db085-202">Následující příklad kódu ukazuje výraz výpočtu, který zapouzdřuje výpočet jako řadu kroků, které lze vyhodnotit v jednom kroku.</span><span class="sxs-lookup"><span data-stu-id="db085-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="db085-203">Typ rozlišeného sjednocení, `OkOrException`, zakóduje chybový stav výrazu jako dosud vyhodnocený.</span><span class="sxs-lookup"><span data-stu-id="db085-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="db085-204">Tento kód ukazuje několik typických vzorů, které lze použít ve výrazech výpočtů, jako jsou například často používané implementace některých metod Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="db085-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="db085-205">Výraz výpočtu má základní typ, který vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="db085-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="db085-206">Nadřízený typ může představovat vypočítaný výsledek nebo zpožděné výpočty, které lze provést, nebo může poskytnout způsob, jak iterovat v některém typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="db085-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="db085-207">V předchozím příkladu byl **nakonec**základní typ.</span><span class="sxs-lookup"><span data-stu-id="db085-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="db085-208">Pro výraz sekvence je nadřízený typ <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db085-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db085-209">Pro výraz dotazu je nadřízený typ <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db085-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db085-210">Pro asynchronní pracovní postup je nadřízený typ [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="db085-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="db085-211">Objekt `Async` představuje práci, která má být provedena k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="db085-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="db085-212">Například zavoláte [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pro spuštění výpočtu a vrácení výsledku.</span><span class="sxs-lookup"><span data-stu-id="db085-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="db085-213">Vlastní operace</span><span class="sxs-lookup"><span data-stu-id="db085-213">Custom Operations</span></span>

<span data-ttu-id="db085-214">Můžete definovat vlastní operaci na výpočetním výrazu a použít vlastní operaci jako operátor ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="db085-215">Do výrazu dotazu můžete například zahrnout operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="db085-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="db085-216">Při definování vlastní operace je nutné definovat yield a metody ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="db085-217">Chcete-li definovat vlastní operaci, vložte ji do třídy tvůrce pro výraz výpočtu a pak použijte [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="db085-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="db085-218">Tento atribut přebírá řetězec jako argument, což je název, který se má použít ve vlastní operaci.</span><span class="sxs-lookup"><span data-stu-id="db085-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="db085-219">Tento název se nachází v rozsahu na začátku počáteční složené závorky výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="db085-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="db085-220">Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="db085-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="db085-221">Vyhněte se například použití identifikátorů, jako je `all` nebo `last` ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="db085-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="db085-222">Rozšíření stávajících tvůrců s novými vlastními operacemi</span><span class="sxs-lookup"><span data-stu-id="db085-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="db085-223">Pokud již máte třídu tvůrce, její vlastní operace lze rozšířit mimo tuto třídu tvůrce.</span><span class="sxs-lookup"><span data-stu-id="db085-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="db085-224">V modulech musí být deklarována rozšíření.</span><span class="sxs-lookup"><span data-stu-id="db085-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="db085-225">Obory názvů nemůžou obsahovat členy rozšíření kromě stejného souboru a stejné skupiny deklarací oboru názvů, kde je definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="db085-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="db085-226">Následující příklad ukazuje rozšíření existující třídy `Microsoft.FSharp.Linq.QueryBuilder`.</span><span class="sxs-lookup"><span data-stu-id="db085-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="db085-227">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db085-227">See also</span></span>

- [<span data-ttu-id="db085-228">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="db085-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="db085-229">Asynchronní pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="db085-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="db085-230">Sekvence</span><span class="sxs-lookup"><span data-stu-id="db085-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="db085-231">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="db085-231">Query Expressions</span></span>](query-expressions.md)
