---
title: Výpočetní výrazy (F#)
description: 'Naučte se vytvářet vhodné syntaxe pro psaní výpočtů v F #, která může být sekvencování a spojovat pomocí konstrukce toku řízení a vazeb.'
ms.date: 05/16/2016
ms.openlocfilehash: a4ddb3fde284452bc901c5270551611e43742c1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="computation-expressions"></a>Výpočetní výrazy

Výpočetní výrazy v jazyce F # poskytují pohodlný syntaxi pro zápis výpočtů, u kterých může být sekvencování a spojovat pomocí konstrukce toku řízení a vazeb. Slouží k poskytování vhodné syntaxe pro *monads*, funkční programovací funkce, která slouží ke správě dat, řízení a vedlejší efekty při funkční programy.


## <a name="built-in-workflows"></a>Předdefinované pracovní postupy
Sekvenční výrazy jsou příkladem výpočetní výraz, jako jsou asynchronní pracovní postupy a výrazy dotazů. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazy dotazů](query-expressions.md).

Některé funkce jsou společné pro sekvenční výrazy a asynchronní pracovní postupy a ilustrují, základní syntaxe pro výpočetní výraz:

```fsharp
builder-name { expression }
```

Předchozí syntaxe Určuje, že je daný výraz výpočetní výraz typu určeného *název tvůrce*. Výpočetní výraz může být předdefinované pracovního postupu, jako například `seq` nebo `async`, nebo může být něco definujete. *Název tvůrce* je identifikátor instance speciální typ označovaný jako *typu Tvůrce*. Tvůrce typ je typ třídy, která definuje speciální metody, které řídí způsob fragmentů výpočetní výraz se zkombinují, který je kód, které řídí, jak se provádí výraz. Dalším způsobem popisují třídu Tvůrce je to znamená, že umožňuje přizpůsobit operaci mnoho F # konstrukce, jako jsou smyčky a vazby.

Výpočetní výrazy je dostupná pro některé běžné jazykové konstrukty dva formuláře. Můžete vyvolat variant konstrukce pomocí! (bang) přípona na určité klíčová slova, jako například `let!`, `do!`a tak dále. Tyto speciální formuláře způsobit, že určité funkce definovaný ve třídě Tvůrce nahradit obyčejnou předdefinované chování těchto operací. Tyto formuláře vypadat `yield!` formu `yield` klíčové slovo, které se používá v pořadí výrazy. Další informace najdete v tématu [pořadí](sequences.md).


## <a name="creating-a-new-type-of-computation-expression"></a>Vytvoření nového typu – výpočetní výraz
Vytvoření třídy tvůrce a definováním některé speciální metody pro třídu můžete definovat vlastnosti vlastní výpočetní výrazy. Třída tvůrce můžete volitelně definovat metody, jak je uvedeno v následující tabulce.

Následující tabulka popisuje metody, které lze použít v třídě Tvůrce pracovního postupu.


|**– Metoda**|**Typické podpisy**|**Popis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Volá se pro `let!` a `do!` v výpočetní výrazy.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Zabalí výpočetní výraz jako funkce.|
|`Return`|`'T -> M<'T>`|Volá se pro `return` v výpočetní výrazy.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Volá se pro `return!` v výpočetní výrazy.|
|`Run`|`M<'T> -> M<'T>` Nebo<br /><br />`M<'T> -> 'T`|Spustí výpočetní výraz.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` Nebo<br /><br />`M<unit> * M<'T> -> M<'T>`|Volá se pro sekvencování v výpočetní výrazy.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` Nebo<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Volá se pro `for...do` výrazy v výpočetní výrazy.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Volá se pro `try...finally` výrazy v výpočetní výrazy.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Volá se pro `try...with` výrazy v výpočetní výrazy.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Volá se pro `use` vazby do ve výpočetní výrazy.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Volá se pro `while...do` výrazy v výpočetní výrazy.|
|`Yield`|`'T -> M<'T>`|Volá se pro `yield` výrazy v výpočetní výrazy.|
|`YieldFrom`|`M<'T> -> M<'T>`|Volá se pro `yield!` výrazy v výpočetní výrazy.|
|`Zero`|`unit -> M<'T>`|Volá se pro prázdný `else` větví z `if...then` výrazy v výpočetní výrazy.|
Mnoho z metod ve třídě Tvůrce použít a vrátit `M<'T>` konstrukce, což je většinou samostatně definovaný typ, který charakterizuje druh výpočty kombinováním, například, `Async<'T>` pro asynchronní pracovní postupy a `Seq<'T>` pořadí pracovních postupů. Podpisy z těchto metod je kombinaci a vnořené mezi sebou, povolit tak, aby pracovní postup objekt vrácený jeden konstrukce můžete předat na další. Kompilátor, při analýze výpočetní výraz Převede výraz na řadu vnořená volání funkcí pomocí metody v předchozí tabulce a kód v výpočetní výraz.

Vnořené výraz je v následujícím formátu:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Ve výše uvedeném kódu volání `Run` a `Delay` byly vynechány, pokud nejsou definovány ve třídě výpočetní výraz Tvůrce. Tělo výpočetní výraz, zde označené jako `{| cexpr |}`, je přeložen do volání metody třídy tvůrce zahrnující překlady popsané v následující tabulce. Výpočetní výraz `{| cexpr |}` je definovaný rekurzivně podle těchto překladů kde `expr` je výraz F # a `cexpr` je výpočetní výraz.



|Výraz|Překlad|
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
V předchozí tabulce `other-expr` popisuje výraz, který není v opačném případě uvedené v tabulce. Třída Tvůrce není nutné k implementaci všechny metody a podporovat všechny překladů uvedené v předchozí tabulce. Tyto koncepty, která nejsou implementované nejsou k dispozici v výpočetní výrazy daného typu. Například, pokud nechcete pro podporu `use` – klíčové slovo v výpočetní výrazy, můžete vynechat definice `Use` v třídě Tvůrce.

Následující příklad kódu ukazuje výpočetní výraz, který zapouzdřuje výpočet jako sérii kroků, které lze vyhodnotit jeden krok najednou. Rozlišované sjednocení typ, A `OkOrException`, jak vyhodnotit dosavadní kóduje chybový stav výrazu. Tento kód ukazuje několik typické vzorů, které můžete použít v výpočetní výrazy, například standardní implementace některé metody Tvůrce.

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

Výpočetní výraz má základní typ, který vrací výraz. Základní typ může představovat výsledku počítaný nebo zpožděné výpočtu, který lze provést, nebo ho může poskytnout způsob, jak iteraci v rámci nějaký typ kolekce. V předchozím příkladu základní typ byl **nakonec**. Pro výraz pořadí je základní typ <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pro výraz dotazu je základní typ <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Pracovním postupu asychronous je základní typ [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Objekt představuje pracovní provést k výpočtu výsledek. Například volání [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) ke spouštění výpočet a vrátí výsledek.

## <a name="custom-operations"></a>Vlastní operace
Můžete definovat vlastní operaci na výpočetní výraz a použít vlastní operaci jako operátor v výpočetní výraz. Operátor dotazu může obsahovat třeba ve výrazu dotazu. Když definujete vlastní operace, je nutné definovat výnos a pro metody ve Výpočetní výraz. Chcete-li definovat vlastní operace, umístí jej do Tvůrce třídy pro výpočetní výraz a potom použít [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Tento atribut přebírá řetězec jako argument, což je název, který se má použít v rámci vlastní operace. Tento název se dodává do oboru na začátku otevření složené závorky výpočetní výraz. Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operaci v tomto bloku. Například nepoužívejte identifikátorů například `all` nebo `last` ve výrazech dotazů.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Asynchronní pracovní postupy](asynchronous-workflows.md)

[Sekvence](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Výrazy dotazu](query-expressions.md)
