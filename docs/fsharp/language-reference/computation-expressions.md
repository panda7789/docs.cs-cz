---
title: Výpočetní výrazy
description: Naučte se vytvářet praktické syntaxe pro psaní výpočtů v F# , která může být sekvencovaná a kombinovaná pomocí konstrukcí a vazeb toku řízení.
ms.date: 11/04/2019
ms.openlocfilehash: 4ff7def0ed3a46acd1b0b83b111f26f5d556071f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569456"
---
# <a name="computation-expressions"></a>Výpočetní výrazy

Výrazy výpočtů v F# poskytují pohodlný Syntax pro zápis výpočtů, které lze sekvencovat a kombinovat pomocí konstrukcí a vazeb toku řízení. V závislosti na druhu výpočetního výrazu je možné si je představit jako způsob, jak vyjádřit monádami, monoids, Monad transformátory a Applicative funktory. Na rozdíl od jiných jazyků (například in *-Notation* v Haskell) se však nevztahují na jednu abstrakci a nespoléhají na makra nebo jiné formy metaprogramování šablonou k dosažení praktické a kontextové syntaxe.

## <a name="overview"></a>Přehled

Výpočty mohou trvat mnoho forem. Nejběžnější forma výpočtů je spuštění s jedním vláknem, které je snadné pochopit a upravit. Ale ne všechny formy výpočtů jsou jednoduché jako provádění s jedním vláknem. Mezi příklady patří:

- Nedeterministické výpočty
- Asynchronní výpočty
- Ovlivněné výpočty
- Regenerační výpočty

Obecně platí, že existují výpočty *závislé na kontextu* , které je nutné provést v určitých částech aplikace. Psaní kódu závislého na kontextu může být náročné, protože je snadné "nevracení" výpočtů mimo daný kontext bez abstrakcí, abyste se mohli vyhnout. Tyto abstrakce jsou často náročné na to, aby je bylo možné napsat F# sami, což znamená, proč má zobecněný způsob, kterým se říká **výpočetní výrazy**.

Výrazy výpočtu nabízejí jednotnou syntaxi a abstraktní model pro kódování závislé na kontextu.

Každý výraz výpočtu je zálohovaný typem *Tvůrce* . Typ Tvůrce definuje operace, které jsou k dispozici pro výpočetní výraz. Viz [Vytvoření nového typu výpočetního výrazu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výraz výpočtu.

### <a name="syntax-overview"></a>Přehled syntaxe

Všechny výpočetní výrazy mají následující formát:

```fsharp
builder-expr { cexper }
```

kde `builder-expr` je název typu tvůrce, který definuje výraz výpočtu a `cexper` je tělo výrazu výpočtu výrazu. Například kód výrazu výpočtu `async` může vypadat takto:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Ve výrazu výpočtu je k dispozici speciální další syntaxe, jak je znázorněno v předchozím příkladu. Ve výrazech výpočtu lze použít následující formuláře výrazů:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Každé z těchto klíčových slov a další klíčová slova standard F# jsou k dispozici pouze ve výrazu výpočtu, pokud byly definovány v typu zálohování. Jedinou výjimkou je `match!`, což je vlastní syntaktický cukr pro použití `let!` následovaný porovnáváním vzorů ve výsledku.

Typ Tvůrce je objekt, který definuje speciální metody, které určují způsob, jakým jsou kombinovány fragmenty výpočetního výrazu. To znamená, že jeho metody řídí, jak se výraz výpočtu chová. Dalším způsobem, jak popsat třídu tvůrce, je říci, že umožňuje přizpůsobit operaci mnoha F# konstrukcí, jako jsou smyčky a vazby.

### `let!`

Klíčové slovo `let!` váže výsledek volání do jiného výpočetního výrazu do názvu:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Pokud svážete volání výrazu výpočtu s `let`, nebudete mít výsledek výrazu výpočtu. Místo toho budete mít vazbu na hodnotu *nerealizovaného* volání tohoto výrazu výpočtu. K vytvoření vazby na výsledek použijte `let!`.

`let!` definuje člen `Bind(x, f)` na typu tvůrce.

### `do!`

Klíčové slovo `do!` je určeno pro volání výrazu výpočtu, který vrací typ `unit`typu (definovaný členem `Zero` na tvůrci):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pro [asynchronní pracovní postup](asynchronous-workflows.md)je tento typ `Async<unit>`. Pro jiné výpočetní výrazy je typ pravděpodobně `CExpType<unit>`.

`do!` je definována `Bind(x, f)` členem na typu tvůrce, kde `f` vytvoří `unit`.

### `yield`

Klíčové slovo `yield` slouží k vrácení hodnoty z výrazu výpočtu, aby ji bylo možné spotřebovat jako <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Ve většině případů je lze vynechat volajícími. Nejběžnější způsob, jak vypustit `yield`, je pomocí operátoru `->`:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

U složitějších výrazů, které by mohly vracet mnoho různých hodnot a možná podmíněně, stačí vynechat klíčové slovo, které může:

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

Stejně jako u [klíčového slova C#yield v ](../../csharp/language-reference/keywords/yield.md)je každý prvek ve výrazu výpočtu vrácen zpět při iteraci.

`yield` je definována `Yield(x)` členem na typu tvůrce, kde `x` je položka, která se má vrátit.

### `yield!`

Klíčové slovo `yield!` slouží ke sloučení kolekce hodnot z výpočetního výrazu:

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

Při vyhodnocování je výsledkem výrazu výpočtu, který vyvolal `yield!`, jeho položky zpět po jednom, které budou shrnuty do výsledku.

`yield!` je definována `YieldFrom(x)` členem na typu tvůrce, kde `x` je kolekce hodnot.

Na rozdíl od `yield`je třeba explicitně zadat `yield!`. Jeho chování není ve výrazech výpočtu implicitní.

### `return`

Klíčové slovo `return` obtéká hodnotu v typu odpovídajícím výpočetnímu výrazu. Kromě výrazů výpočtu, které používají `yield`, se používá k "dokončení" výrazu výpočtu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` je definována `Return(x)` členem na typu tvůrce, kde `x` je položka, která se má zabalit.

### `return!`

Klíčové slovo `return!` realizuje hodnotu výrazu výpočtu a zabalí, jejichž výsledkem je typ odpovídající výrazu výpočtu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` je definována `ReturnFrom(x)` členem na typu tvůrce, kde `x` je jiný výraz výpočtu.

### `match!`

Klíčové slovo `match!` umožňuje vložené volání do jiného výrazu výpočtu a porovnávání vzorů na jeho výsledku:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Při volání výrazu výpočtu se `match!`, bude mít výsledek volání jako `let!`. To se často používá při volání výrazu výpočtu, kde výsledek je [nepovinný](options.md).

## <a name="built-in-computation-expressions"></a>Předdefinované výrazy výpočtů

F# Základní knihovna definuje tři předdefinované výpočetní výrazy: [výrazy sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výrazy dotazů](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Vytvoření nového typu výrazu výpočtu

Můžete definovat charakteristiky vlastních výrazů výpočtu vytvořením třídy tvůrce a definováním určitých speciálních metod pro třídu. Třída tvůrce může volitelně definovat metody, které jsou uvedeny v následující tabulce.

Následující tabulka popisuje metody, které lze použít ve třídě tvůrce pracovního postupu.

|**Metoda**|**Typické podpisy**|**Popis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Volá se pro `let!` a `do!` ve výrazech výpočtu.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Zabalí výraz výpočtu jako funkci.|
|`Return`|`'T -> M<'T>`|Volá se pro `return` ve výrazech výpočtu.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Volá se pro `return!` ve výrazech výpočtu.|
|`Run`|`M<'T> -> M<'T>` nebo<br /><br />`M<'T> -> 'T`|Provede výpočetní výraz.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` nebo<br /><br />`M<unit> * M<'T> -> M<'T>`|Volá se pro sekvencování ve výrazech výpočtu.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` nebo<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Volá se pro `for...do` výrazy ve výrazech výpočtu.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Volá se pro `try...finally` výrazy ve výrazech výpočtu.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Volá se pro `try...with` výrazy ve výrazech výpočtu.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Volá se pro `use` vazby ve výrazech výpočtu.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Volá se pro `while...do` výrazy ve výrazech výpočtu.|
|`Yield`|`'T -> M<'T>`|Volá se pro `yield` výrazy ve výrazech výpočtu.|
|`YieldFrom`|`M<'T> -> M<'T>`|Volá se pro `yield!` výrazy ve výrazech výpočtu.|
|`Zero`|`unit -> M<'T>`|Volá se pro prázdné `else` větve `if...then` výrazů ve výrazech výpočtu.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Označuje, že výraz výpočtu je předán členu `Run` jako citace. Převede všechny instance výpočtu do citace.|

Mnoho metod ve třídě tvůrce používá a vrací `M<'T>` konstrukce, což je obvykle samostatně definovaný typ, který charakterizuje druh výpočtů, které jsou kombinovány, například `Async<'T>` pro asynchronní pracovní postupy a `Seq<'T>` pro pracovní postupy sekvence. Signatury těchto metod umožňují, aby byly vzájemně kombinovány a vnořeny, takže objekt pracovního postupu vrácený z jedné konstrukce lze předat dalšímu. Kompilátor při analýze výrazu výpočtu Převede výraz na řadu vnořených volání funkcí pomocí metod v předchozí tabulce a kódu ve výrazu výpočtu.

Vnořený výraz má následující tvar:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Ve výše uvedeném kódu jsou volání `Run` a `Delay` vynechána, pokud nejsou definována ve třídě Tvůrce výrazů výpočtu. Tělo výrazu výpočtu, zde označovaného jako `{| cexpr |}`, je přeloženo do volání, která zahrnují metody třídy tvůrce, pomocí překladů popsaných v následující tabulce. Výraz výpočtu `{| cexpr |}` je rekurzivně definován podle těchto překladů, kde `expr` je F# výraz a `cexpr` je výraz výpočtu.

|Výraz|Překlad|
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

V předchozí tabulce `other-expr` popisuje výraz, který není jinak uveden v tabulce. Třída tvůrce nemusí implementovat všechny metody a podporovat všechny překlady uvedené v předchozí tabulce. Tyto konstrukce, které nejsou implementovány, nejsou k dispozici ve výrazech výpočtu tohoto typu. Například pokud nechcete podporovat klíčové slovo `use` ve výrazech výpočtu, můžete vynechat definici `Use` ve třídě tvůrce.

Následující příklad kódu ukazuje výraz výpočtu, který zapouzdřuje výpočet jako řadu kroků, které lze vyhodnotit v jednom kroku. Typ rozlišeného sjednocení, `OkOrException`, zakóduje chybový stav výrazu jako dosud vyhodnocený. Tento kód ukazuje několik typických vzorů, které lze použít ve výrazech výpočtů, jako jsou například často používané implementace některých metod Tvůrce.

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

Výraz výpočtu má základní typ, který vrací výraz. Nadřízený typ může představovat vypočítaný výsledek nebo zpožděné výpočty, které lze provést, nebo může poskytnout způsob, jak iterovat v některém typu kolekce. V předchozím příkladu byl **nakonec**základní typ. Pro výraz sekvence je nadřízený typ <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pro výraz dotazu je nadřízený typ <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Pro asynchronní pracovní postup je nadřízený typ [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). Objekt `Async` představuje práci, která má být provedena k výpočtu výsledku. Například zavoláte [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pro spuštění výpočtu a vrácení výsledku.

## <a name="custom-operations"></a>Vlastní operace

Můžete definovat vlastní operaci na výpočetním výrazu a použít vlastní operaci jako operátor ve výrazu výpočtu. Do výrazu dotazu můžete například zahrnout operátor dotazu. Při definování vlastní operace je nutné definovat yield a metody ve výrazu výpočtu. Chcete-li definovat vlastní operaci, vložte ji do třídy tvůrce pro výraz výpočtu a pak použijte [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Tento atribut přebírá řetězec jako argument, což je název, který se má použít ve vlastní operaci. Tento název se nachází v rozsahu na začátku počáteční složené závorky výrazu výpočtu. Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku. Vyhněte se například použití identifikátorů, jako je `all` nebo `last` ve výrazech dotazů.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Rozšíření stávajících tvůrců s novými vlastními operacemi

Pokud již máte třídu tvůrce, její vlastní operace lze rozšířit mimo tuto třídu tvůrce. V modulech musí být deklarována rozšíření. Obory názvů nemůžou obsahovat členy rozšíření kromě stejného souboru a stejné skupiny deklarací oboru názvů, kde je definovaný typ.

Následující příklad ukazuje rozšíření existující třídy `Microsoft.FSharp.Linq.QueryBuilder`.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Asynchronní pracovní postupy](asynchronous-workflows.md)
- [Sekvence](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Výrazy dotazu](query-expressions.md)
