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
# <a name="computation-expressions"></a>Výpočetní výrazy

Výpočetní výrazy v F# poskytují pohodlnou syntaxi pro psaní výpočtů, které lze sekvencovat a kombinovat pomocí konstrukce toku řízení a vazeb. V závislosti na druhu výpočtového výrazu si je lze myslet jako způsob, jak vyjádřit monady, monoidy, monadové transformátory a aplikátory. Na rozdíl od jiných jazyků *(například donotace* v Haskellu) však nejsou vázány na jednu abstrakce a nespoléhají se na makra nebo jiné formy metaprogramování, aby bylo možné provést pohodlnou a kontextově citlivou syntaxi.

## <a name="overview"></a>Přehled

Výpočty mohou mít mnoho podob. Nejběžnější forma výpočtu je jednovláknové spuštění, které je snadno pochopitelné a upravit. Však ne všechny formy výpočtu jsou stejně jednoduché jako jednovláknové spuštění. Možné příklady:

- Nedeterministické výpočty
- Asynchronní výpočty
- Efektivní výpočty
- Generativní výpočty

Obecněji platí, že existují *kontextové* výpočty, které je nutné provést v určitých částech aplikace. Psaní kontextového kódu může být náročné, protože je snadné "nevracení" výpočty mimo daný kontext bez abstrakcí, aby vám v tom zabránit. Tyto abstrakce jsou často náročné psát sami, což je důvod, proč F# má zobecněný způsob, jak provést tak zvané **výpočetní výrazy**.

Výpočetní výrazy nabízejí jednotný syntaktický a abstraktní model pro kódování kontextových výpočtů.

Každý výpočetní výraz je zálohován typem *tvůrce.* Typ tvůrce definuje operace, které jsou k dispozici pro výpočetní výraz. Viz [Vytvoření nového typu výpočetního výrazu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výpočetní výraz.

### <a name="syntax-overview"></a>Přehled syntaxe

Všechny výpočetní výrazy mají následující tvar:

```fsharp
builder-expr { cexper }
```

kde `builder-expr` je název typu tvůrce, který definuje výpočetní výraz `cexper` a je tělem výrazu výrazu výpočtového výrazu. Kód výrazu `async` výpočtu může například vypadat takto:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

V rámci výpočtového výrazu je k dispozici speciální další syntaxe, jak je znázorněno v předchozím příkladu. Následující formuláře výrazů jsou možné s výpočetními výrazy:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Každé z těchto klíčových slov a další standardní klíčová slova Jazyka F# jsou k dispozici pouze ve výpočtovém výrazu, pokud byla definována v typu tvůrce zálohování. Jedinou výjimkou je `match!`, což je samo o `let!` sobě syntaktický cukr pro použití následovaný vzor emblém na výsledek.

Typ tvůrce je objekt, který definuje speciální metody, které řídí způsob, jakým jsou kombinovány fragmenty výrazu výpočtu; to znamená, že jeho metody řídí chování výpočtového výrazu. Dalším způsobem, jak popsat třídu tvůrce, je říci, že umožňuje přizpůsobit provoz mnoha konstrukcí F#, jako jsou smyčky a vazby.

### `let!`

Klíčové `let!` slovo sváže výsledek volání na jiný výpočetní výraz s názvem:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Pokud svážete volání s výrazem `let`výpočtu s , nezískáte výsledek výrazu výpočtu. Místo toho budete mít vázané hodnoty *nerealizované* volání tohoto výpočtu výrazu. Slouží `let!` k vazbě na výsledek.

`let!`je definován `Bind(x, f)` členem na typu tvůrce.

### `do!`

Klíčové `do!` slovo je pro volání výpočetní výraz, který vrátí `unit`-like typ (definované `Zero` člen na tvůrce):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pro [asynchronní pracovní](asynchronous-workflows.md)postup `Async<unit>`je tento typ . Pro ostatní výpočetní výrazy je pravděpodobně typ `CExpType<unit>`.

`do!`je definován `Bind(x, f)` členem na typu tvůrce, `f` kde `unit`vzniká .

### `yield`

Klíčové `yield` slovo je pro vrácení hodnoty z výpočtového výrazu tak, <xref:System.Collections.Generic.IEnumerable%601>aby mohla být spotřebována jako :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Ve většině případů jej mohou volající vynechat. Nejběžnější způsob, jak vynechat, `yield` je `->` s operátorem:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Pro složitější výrazy, které by mohly přinést mnoho různých hodnot a možná podmíněně, jednoduše vynechání klíčové slovo může udělat:

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

Stejně jako [u yield klíčové slovo v C#](../../csharp/language-reference/keywords/yield.md), každý prvek ve výpočtu výrazu je výnosný zpět, jak je iterováno.

`yield`je definován `Yield(x)` členem na typu tvůrce, kde je položka, která `x` má být výnosná.

### `yield!`

Klíčové `yield!` slovo je pro sloučení kolekce hodnot z výpočtového výrazu:

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

Při vyhodnocení bude mít výraz `yield!` výpočtu volaný položky, které jsou výnosné jeden po druhém, a výsledek se sloučí.

`yield!`je definován `YieldFrom(x)` členem na typu tvůrce, kde `x` je kolekce hodnot.

Na `yield` `yield!` rozdíl od , musí být explicitně zadán. Jeho chování není implicitní ve výpočtových výrazech.

### `return`

Klíčové `return` slovo zabalí hodnotu v typu odpovídajícím výpočetnímu výrazu. Kromě používaných výpočetních `yield`výrazů se používá k "dokončení" výpočtu výrazu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`je definován `Return(x)` členem na typu tvůrce, kde je položka, kterou `x` má být zalamována.

### `return!`

Klíčové `return!` slovo realizuje hodnotu výpočetního výrazu a obtéká, které mají za následek typ odpovídající výrazu výpočtu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`je definován `ReturnFrom(x)` členem na typu tvůrce, kde `x` je jiný výpočetní výraz.

### `match!`

Klíčové `match!` slovo umožňuje vložit volání na jiný výpočetní výraz a vzor odpovídá jeho výsledku:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Při volání výpočtu výraz `match!`s , bude realizovat výsledek `let!`volání jako . To se často používá při volání výpočetního výrazu, kde je výsledkem [volitelné](options.md).

## <a name="built-in-computation-expressions"></a>Předdefinované výpočetní výrazy

Základní knihovna Jazyka F# definuje tři předdefinované výpočetní výrazy: [Sekvenční výrazy](sequences.md), [Asynchronní pracovní postupy](asynchronous-workflows.md)a [Výrazy dotazu](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Vytvoření nového typu výpočetního výrazu

Můžete definovat charakteristiky vlastní výpočetní výrazy vytvořením třídy tvůrce a definováním určitých speciálních metod ve třídě. Třída tvůrce může volitelně definovat metody uvedené v následující tabulce.

Následující tabulka popisuje metody, které lze použít ve třídě tvůrce pracovního postupu.

|**Metoda**|**Typický podpis (podpisy)**|**Popis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Volal `let!` a `do!` ve výpočtu výrazy.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Zalomí výraz výpočtu jako funkci.|
|`Return`|`'T -> M<'T>`|Voláno `return` ve výpočtových výrazech.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Voláno `return!` ve výpočtových výrazech.|
|`Run`|`M<'T> -> M<'T>` nebo<br /><br />`M<'T> -> 'T`|Spustí výpočetní výraz.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` nebo<br /><br />`M<unit> * M<'T> -> M<'T>`|Nazývá se řazení ve výpočtových výrazech.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` nebo<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Voláno `for...do` pro výrazy ve výpočetních výrazech.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Voláno `try...finally` pro výrazy ve výpočetních výrazech.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Voláno `try...with` pro výrazy ve výpočetních výrazech.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Volána `use` pro vazby ve výpočtových výrazech.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Voláno `while...do` pro výrazy ve výpočetních výrazech.|
|`Yield`|`'T -> M<'T>`|Voláno `yield` pro výrazy ve výpočetních výrazech.|
|`YieldFrom`|`M<'T> -> M<'T>`|Voláno `yield!` pro výrazy ve výpočetních výrazech.|
|`Zero`|`unit -> M<'T>`|Nazývá se `else` prázdné `if...then` větve výrazů ve výpočetních výrazech.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Označuje, že výpočetní výraz je `Run` předán členovi jako nabídka. Překládá všechny instance výpočtu do nabídky.|

Mnoho metod ve třídě tvůrce používá `M<'T>` a vrací konstrukci, což je obvykle samostatně definovaný typ, který charakterizuje druh `Async<'T>` výpočtů, které jsou `Seq<'T>` kombinovány, například pro asynchronní pracovní postupy a pro pracovní postupy sekvence. Podpisy těchto metod umožňují jejich kombinování a vnoření mezi sebou, takže objekt pracovního postupu vrácený z jedné konstrukce může být předán dalšímu. Kompilátor při analýzách výpočtového výrazu převede výraz na řadu vnořených volání funkcí pomocí metod v předchozí tabulce a kódu ve výpočtovém výrazu.

Vnořený výraz má následující tvar:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Ve výše uvedeném kódu `Run` `Delay` volání a jsou vynechány, pokud nejsou definovány ve třídě tvůrce výrazu výpočtu. Tělo výrazu výpočtu, zde označené `{| cexpr |}`jako , je přeloženo do volání zahrnujících metody třídy tvůrce překlady popsanými v následující tabulce. Výpočetní výraz `{| cexpr |}` je definován rekurzivně podle těchto `expr` překladů, kde `cexpr` je výraz F# a je výpočetní výraz.

|Expression|Překlad|
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

V předchozí tabulce `other-expr` popisuje výraz, který není jinak uveden v tabulce. Třída tvůrce nemusí implementovat všechny metody a podporovat všechny překlady uvedené v předchozí tabulce. Tyto konstrukce, které nejsou implementovány nejsou k dispozici ve výpočtu výrazy tohoto typu. Například pokud nechcete podporovat `use` klíčové slovo ve výpočtu výrazy, můžete vynechat definici `Use` ve třídě tvůrce.

Následující příklad kódu ukazuje výpočetní výraz, který zapouzdřuje výpočtu jako řadu kroků, které lze vyhodnotit jeden krok za krokem. Discriminated union typu `OkOrException`, kóduje chybový stav výrazu, jak byl dosud vyhodnocen. Tento kód ukazuje několik typické vzory, které můžete použít ve výpočtu výrazy, jako je například často používaný počet implementací některých metod tvůrce.

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

Výpočetní výraz má základní typ, který výraz vrátí. Základní typ může představovat vypočítaný výsledek nebo zpožděný výpočet, který lze provést, nebo může poskytnout způsob, jak iterát prostřednictvím některého typu kolekce. V předchozím příkladu byl základní typ **nakonec**. Pro sekvenční výraz <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>je základní typ . Pro výraz dotazu je <xref:System.Linq.IQueryable?displayProperty=nameWithType>základní typ . Pro asynchronní pracovní postup je [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)základní typ . Objekt `Async` představuje práci, která má být provedena k výpočtu výsledku. Například volání [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) provést výpočtu a vrátit výsledek.

## <a name="custom-operations"></a>Vlastní operace

Můžete definovat vlastní operaci na výpočetní výraz a použít vlastní operaci jako operátor ve výrazu výpočtu. Můžete například zahrnout operátor dotazu do výrazu dotazu. Při definování vlastní operace je nutné definovat metody Yield a For ve výpočetním výrazu. Chcete-li definovat vlastní operaci, vložte ji do třídy tvůrce [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)pro výpočetní výraz a potom použijte . Tento atribut má řetězec jako argument, což je název, který má být použit ve vlastní operaci. Tento název přichází do oboru na začátku otevření složené závorky výpočtového výrazu. Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku. Vyhněte se například použití `all` identifikátorů, jako jsou výrazy dotazu nebo `last` ve výrazech dotazu.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Rozšíření stávajících stavitelů o nové vlastní operace

Pokud již máte třídu tvůrce, jeho vlastní operace lze rozšířit z mimo tuto třídu tvůrce. Rozšíření musí být deklarována v modulech. Obory názvů nesmí obsahovat členy přípony s výjimkou stejného souboru a stejné skupiny deklarací oboru názvů, kde je definován typ.

Následující příklad ukazuje rozšíření existující `Microsoft.FSharp.Linq.QueryBuilder` třídy.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
- [Asynchronní pracovní postupy](asynchronous-workflows.md)
- [Sekvence](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Výrazy dotazu](query-expressions.md)
