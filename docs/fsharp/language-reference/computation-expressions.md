---
title: Výpočetní výrazy (F#)
description: 'Zjistěte, jak vytvořit pohodlné syntaxe zápisu výpočtů v jazyce F #, která může být sekvencování a spojovat pomocí konstruktorů toků řízení a vazby.'
ms.date: 07/27/2018
ms.openlocfilehash: ce81af7966a436b3973de277fb2a78ec06f4c471
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365377"
---
# <a name="computation-expressions"></a><span data-ttu-id="5eca6-103">Výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="5eca6-103">Computation Expressions</span></span>

<span data-ttu-id="5eca6-104">Výpočetní výrazy v jazyce F # poskytuje pohodlné syntaxe pro zápis výpočty, které mohou být sekvencování a spojovat pomocí konstruktorů toků řízení a vazby.</span><span class="sxs-lookup"><span data-stu-id="5eca6-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="5eca6-105">V závislosti na typ výrazu výpočtu, můžete představit jako způsob, jak vyjádřit monády, monoids, monad transformátory a applicative funktory.</span><span class="sxs-lookup"><span data-stu-id="5eca6-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="5eca6-106">Ale na rozdíl od jiných jazyků (jako například *zápis* v Haskell), nejsou vázané na jednoho odběru a nespoléhejte na makra nebo jiné formy metaprogramování k provedení pohodlný a kontextová syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5eca6-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="5eca6-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="5eca6-107">Overview</span></span>

<span data-ttu-id="5eca6-108">Výpočty mohou mít mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="5eca6-108">Computations can take many forms.</span></span> <span data-ttu-id="5eca6-109">Nejběžnější forma výpočtu je spouštění s jedním vláknem, které je snadno srozumitelný a upravit.</span><span class="sxs-lookup"><span data-stu-id="5eca6-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="5eca6-110">Ne všechny formy výpočet jsou však tak přímočaré jako spuštění s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="5eca6-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="5eca6-111">Mezi příklady patří:</span><span class="sxs-lookup"><span data-stu-id="5eca6-111">Some examples include:</span></span>

* <span data-ttu-id="5eca6-112">Nedeterministické výpočty</span><span class="sxs-lookup"><span data-stu-id="5eca6-112">Non-deterministic computations</span></span>
* <span data-ttu-id="5eca6-113">Asynchronní výpočty</span><span class="sxs-lookup"><span data-stu-id="5eca6-113">Asynchronous computations</span></span>
* <span data-ttu-id="5eca6-114">Effectful výpočty</span><span class="sxs-lookup"><span data-stu-id="5eca6-114">Effectful computations</span></span>
* <span data-ttu-id="5eca6-115">Tvoří výpočty</span><span class="sxs-lookup"><span data-stu-id="5eca6-115">Generative computations</span></span>

<span data-ttu-id="5eca6-116">Obecně platí, existují *kontextové* výpočty, které je nutné provést v některých částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="5eca6-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="5eca6-117">Psaní kódu kontextové může být náročné, jako je "nevracení" výpočty mimo daný kontext bez odběrů a znemožnit vám tak snadné.</span><span class="sxs-lookup"><span data-stu-id="5eca6-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="5eca6-118">Tato abstrakce jsou často náročné napsat sami, což je důvod, proč F # má zobecněné způsob, jak provést tzv **výrazech výpočtu**.</span><span class="sxs-lookup"><span data-stu-id="5eca6-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="5eca6-119">Výpočetní výrazy nabízí jednotnou syntaxi a abstrakce model pro kódování kontextové výpočty.</span><span class="sxs-lookup"><span data-stu-id="5eca6-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="5eca6-120">Každý výraz výpočtu tímto modulem stojí *Tvůrce* typu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="5eca6-121">Typ Tvůrce definuje operace, které jsou k dispozici pro výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="5eca6-122">V tématu [vytváří se nový typ z výrazu výpočtu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výpočet výraz.</span><span class="sxs-lookup"><span data-stu-id="5eca6-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="5eca6-123">Přehled syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eca6-123">Syntax overview</span></span>

<span data-ttu-id="5eca6-124">Všechny výpočetní výrazy mají následující podobu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="5eca6-125">kde `builder-expr` je název typu Tvůrce výrazu výpočtu definuje a `cexper` výraz tělo výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="5eca6-126">Například `async` kód výrazu výpočtu může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="5eca6-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="5eca6-127">Je syntaxe speciální, navíc k dispozici v rámci výrazu výpočtu, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="5eca6-128">Následující výraz formuláře je možné pomocí výrazů výpočtu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="5eca6-129">Každá z těchto klíčových slov a ostatní standardní F # klíčová slova jsou k dispozici pouze ve výrazu výpočtu. Pokud byla definována v základní typ Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="5eca6-130">Jedinou výjimkou je `match!`, což je samotný syntaktické sugar pro použití `let!` následuje porovnávání na výsledek.</span><span class="sxs-lookup"><span data-stu-id="5eca6-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="5eca6-131">Typ Tvůrce je objekt, který definuje speciální metody, které řídí způsob, jakým jsou kombinované fragmenty výrazu výpočtu; To znamená její metody řídit chování výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="5eca6-132">Dalším způsobem, jak popisují třída tvůrců je Řekněme, že umožňuje přizpůsobit operace mnoho konstrukce F #, jako jsou smyčky a vazby.</span><span class="sxs-lookup"><span data-stu-id="5eca6-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="5eca6-133">`let!` – Klíčové slovo vytvoří vazbu na výsledek volání do jiného výrazu výpočtu k názvu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="5eca6-134">Pokud je vytvořit vazbu volání výrazu výpočtu s `let`, nezískáte výsledek výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="5eca6-135">Místo toho je bude ovládací prvek vázán hodnotu *Nerealizovaná* volání tohoto výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="5eca6-136">Použití `let!` vytvořit vazbu k výsledku.</span><span class="sxs-lookup"><span data-stu-id="5eca6-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="5eca6-137">`let!` je definován `Bind(x, f)` člen v typu Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="5eca6-138">`do!` – Klíčové slovo je pro volání výrazu výpočtu, která vrátí `unit`– typ, jako jsou (definované `Zero` člen Tvůrce):</span><span class="sxs-lookup"><span data-stu-id="5eca6-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! sumbitData data url
        ...
    }
```

<span data-ttu-id="5eca6-139">Pro [asynchronního pracovního postupu](asynchronous-workflows.md), tento typ je `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="5eca6-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="5eca6-140">U jiných výrazech výpočtu typ by mohla být `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="5eca6-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="5eca6-141">`do!` je definován `Bind(x, f)` člen v typu tvůrce, kde `f` vytváří `unit`.</span><span class="sxs-lookup"><span data-stu-id="5eca6-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="5eca6-142">`yield` – Klíčové slovo je tak, aby mohly využívat jako návratová hodnota z výrazu výpočtu <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="5eca6-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="5eca6-143">Stejně jako u [yield – klíčové slovo v jazyce C#](../../csharp/language-reference/keywords/yield.md), každý prvek ve výrazu výpočtu, je vhodné, protože je provést iteraci.</span><span class="sxs-lookup"><span data-stu-id="5eca6-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="5eca6-144">`yield` je definován `Yield(x)` člen v typu tvůrce, kde `x` je položka výnosu zpět.</span><span class="sxs-lookup"><span data-stu-id="5eca6-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="5eca6-145">`yield!` – Klíčové slovo je pro sloučení kolekci hodnot z výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="5eca6-146">Po vyhodnocení výrazu výpočtu volány `yield!` budou mít položky vrátil zpět jeden po druhém, výsledek sloučení.</span><span class="sxs-lookup"><span data-stu-id="5eca6-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="5eca6-147">`yield!` je definován `YieldFrom(x)` člen v typu tvůrce, kde `x` je kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="5eca6-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="5eca6-148">`return` – Klíčové slovo obtéká hodnotu v typu odpovídá výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="5eca6-149">Kromě použití výrazech výpočtu `yield`, používá se "Dokončit" výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="5eca6-150">`return` je definován `Return(x)` člen v typu tvůrce, kde `x` je položka, kterou chcete zabalit.</span><span class="sxs-lookup"><span data-stu-id="5eca6-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="5eca6-151">`return!` – Klíčové slovo realizuje hodnotu výrazu výpočtu a zabalí výsledek typ odpovídající výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="5eca6-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="5eca6-152">`return!` je definován `ReturnFrom(x)` člen v typu tvůrce, kde `x` je jiného výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="5eca6-153">Od verze F # 4.5, `match!` – klíčové slovo vám umožní vložení volání jiného výpočtu výrazu a vzor se vyhledala shoda podle její výsledek:</span><span class="sxs-lookup"><span data-stu-id="5eca6-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="5eca6-154">Při volání výrazu výpočtu s `match!`, značným výsledek volání, například `let!`.</span><span class="sxs-lookup"><span data-stu-id="5eca6-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="5eca6-155">To se často používá při volání výrazu výpočtu, kde výsledkem je [volitelné](options.md).</span><span class="sxs-lookup"><span data-stu-id="5eca6-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="5eca6-156">Integrované výpočetní výrazy</span><span class="sxs-lookup"><span data-stu-id="5eca6-156">Built-in computation expressions</span></span>

<span data-ttu-id="5eca6-157">Základní knihovny F # definuje tři předdefinované výpočetní výrazy: [výrazech pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [– výrazy dotazů](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5eca6-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="5eca6-158">Vytvoření nového typu výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="5eca6-159">Vytvoření třídy tvůrce a definováním některých speciálních metod ve třídě můžete definovat vlastnosti výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="5eca6-160">Třída tvůrců Volitelně můžete definovat metody, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="5eca6-161">Následující tabulka popisuje metody, které je možné ve třídě Tvůrce pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="5eca6-162">**– Metoda**</span><span class="sxs-lookup"><span data-stu-id="5eca6-162">**Method**</span></span>|<span data-ttu-id="5eca6-163">**Typické podpisy**</span><span class="sxs-lookup"><span data-stu-id="5eca6-163">**Typical signature(s)**</span></span>|<span data-ttu-id="5eca6-164">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5eca6-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="5eca6-165">Volá se pro `let!` a `do!` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="5eca6-166">Zabalí výrazu výpočtu jako funkce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="5eca6-167">Volá se pro `return` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="5eca6-168">Volá se pro `return!` ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="5eca6-169">`M<'T> -> M<'T>` Nebo</span><span class="sxs-lookup"><span data-stu-id="5eca6-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="5eca6-170">Provede výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="5eca6-171">`M<'T> * M<'T> -> M<'T>` Nebo</span><span class="sxs-lookup"><span data-stu-id="5eca6-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="5eca6-172">Volá se pro určení posloupnosti ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="5eca6-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` Nebo</span><span class="sxs-lookup"><span data-stu-id="5eca6-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="5eca6-174">Volá se pro `for...do` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="5eca6-175">Volá se pro `try...finally` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="5eca6-176">Volá se pro `try...with` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="5eca6-177">Volá se pro `use` vazby ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="5eca6-178">Volá se pro `while...do` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="5eca6-179">Volá se pro `yield` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="5eca6-180">Volá se pro `yield!` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="5eca6-181">Volá se pro prázdný `else` větve z `if...then` výrazy ve výrazech výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|

<span data-ttu-id="5eca6-182">Mnoho metod ve třídě Tvůrce používat a vrátit `M<'T>` konstrukce, která je obvykle samostatně definovaný typ, který charakterizuje druh výpočty se kombinovat, například, `Async<'T>` pro asynchronní pracovní postupy a `Seq<'T>` pro pracovní postupy pořadí.</span><span class="sxs-lookup"><span data-stu-id="5eca6-182">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="5eca6-183">Podpisy z těchto metod je kombinovat a vnořené s kolegy a povolit tak, aby pracovní postup objekt vrácený z jednoho konstrukce mohou být předány Další.</span><span class="sxs-lookup"><span data-stu-id="5eca6-183">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="5eca6-184">Kompilátor při analýze výrazu výpočtu, převede výraz na sérii volání vnořené funkce pomocí metod v předchozí tabulce a kódu ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-184">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="5eca6-185">Vnořený výraz má následující formát:</span><span class="sxs-lookup"><span data-stu-id="5eca6-185">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="5eca6-186">Ve výše uvedeném kódu volání `Run` a `Delay` jsou vynechány, pokud nejsou definovány ve třídě Tvůrce výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-186">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="5eca6-187">Hlavní část výrazu výpočtu, zde označený jako `{| cexpr |}`, je přeložen do volání metody třídy tvůrce zahrnující podle překlady jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-187">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="5eca6-188">Výrazu výpočtu `{| cexpr |}` je definované rekurzivně podle tyto překlady kde `expr` je výraz F # a `cexpr` je výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-188">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="5eca6-189">Výraz</span><span class="sxs-lookup"><span data-stu-id="5eca6-189">Expression</span></span>|<span data-ttu-id="5eca6-190">Překlad</span><span class="sxs-lookup"><span data-stu-id="5eca6-190">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="5eca6-191">V předchozí tabulce `other-expr` popisuje výraz, který není jinak uvedená v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-191">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="5eca6-192">Třída tvůrců není potřeba implementovat všechny metody a podporují všechny převody uvedené v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-192">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="5eca6-193">Tyto konstrukce, které nejsou implementované nejsou k dispozici ve výrazech výpočtu daného typu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-193">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="5eca6-194">Například, pokud nechcete podporu `use` – klíčové slovo ve výrazech výpočtu, můžete vynechat definici `Use` ve své třídě Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-194">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="5eca6-195">Následující příklad kódu ukazuje, který zapouzdřuje výpočtu jako sérii kroků, které lze vyhodnotit jeden krok po jednom výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-195">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="5eca6-196">Rozlišované sjednocení typu A `OkOrException`, jak vyhodnotit zatím kóduje chybový stav výrazu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-196">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="5eca6-197">Tento kód ukazuje některé typické postupy, které můžete použít ve výrazech výpočtu, jako je například implementace často používaný text některé metody Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-197">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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
        | Done value -> NotYetDone (fun () -> func value)
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
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="5eca6-198">Výrazu výpočtu má základní typ, který vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="5eca6-198">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="5eca6-199">Nadřazený typ může představovat vypočítaný výsledek nebo opožděné výpočty, které lze provést nebo může poskytnout způsob, jak k iteraci v rámci nějaký typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-199">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="5eca6-200">V předchozím příkladu byl nadřazený typ **nakonec**.</span><span class="sxs-lookup"><span data-stu-id="5eca6-200">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="5eca6-201">Pro výraz pořadí základní typ je <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5eca6-201">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5eca6-202">Pro výraz dotazu, je základní typ <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5eca6-202">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5eca6-203">Pro asynchronní pracovní postup, je základní typ [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="5eca6-203">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="5eca6-204">`Async` Objekt představuje práce, která musí provést k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="5eca6-204">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="5eca6-205">Například volání [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) k provedení výpočtu a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="5eca6-205">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="5eca6-206">Vlastní operace</span><span class="sxs-lookup"><span data-stu-id="5eca6-206">Custom Operations</span></span>

<span data-ttu-id="5eca6-207">Můžete definovat vlastní operace na výrazu výpočtu a použít vlastní operace jako operátor ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-207">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="5eca6-208">Můžete například zahrnout – operátor dotazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-208">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="5eca6-209">Když definujete vlastní operace, je nutné definovat výnos a pro metody ve výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-209">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="5eca6-210">K definování vlastní operace put ve třídě Tvůrce výrazu výpočtu a pak použít [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="5eca6-210">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="5eca6-211">Tento atribut přijímá řetězec jako argument, což je název, který se má použít v rámci vlastní operace.</span><span class="sxs-lookup"><span data-stu-id="5eca6-211">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="5eca6-212">Tento název vstupu do oboru na začátku otevírající složenou závorku výrazu výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5eca6-212">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="5eca6-213">Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="5eca6-213">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="5eca6-214">Například vyhnout použití identifikátorů, jako `all` nebo `last` ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="5eca6-214">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="5eca6-215">Rozšíření stávajících počítačů s nové vlastní operace</span><span class="sxs-lookup"><span data-stu-id="5eca6-215">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="5eca6-216">Pokud už máte třídu tvůrce, je možné rozšířit své vlastní operace z mimo tuto třídu Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="5eca6-216">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="5eca6-217">Rozšíření musí deklarovat v modulech.</span><span class="sxs-lookup"><span data-stu-id="5eca6-217">Extensions must be declared in modules.</span></span> <span data-ttu-id="5eca6-218">Obory názvů nemůžou obsahovat členy rozšíření s výjimkou ve stejném souboru a do stejné skupiny deklarace oboru názvů, kde je definován typ.</span><span class="sxs-lookup"><span data-stu-id="5eca6-218">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="5eca6-219">Následující příklad ukazuje rozšíření existující `Microsoft.FSharp.Linq.QueryBuilder` třídy.</span><span class="sxs-lookup"><span data-stu-id="5eca6-219">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="5eca6-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5eca6-220">See also</span></span>

- [<span data-ttu-id="5eca6-221">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="5eca6-221">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5eca6-222">Asynchronní pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="5eca6-222">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="5eca6-223">Sekvence</span><span class="sxs-lookup"><span data-stu-id="5eca6-223">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="5eca6-224">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="5eca6-224">Query Expressions</span></span>](query-expressions.md)
