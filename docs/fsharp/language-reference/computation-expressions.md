---
title: Výpočetní výrazy (F#)
description: Zjistěte, jak vytvořit pohodlné syntaxe pro zápis výpočty v F# , můžete být sekvencované a kombinované pomocí řídit tok konstrukcí a vazby.
ms.date: 07/27/2018
ms.openlocfilehash: b1fee11f68e99e53d19b47bef9eca6298cce2f45
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169843"
---
# <a name="computation-expressions"></a>Výpočetní výrazy

Výpočetní výrazy v F# poskytuje pohodlné syntaxe pro zápis výpočty, které mohou být sekvencování a spojovat pomocí konstruktorů toků řízení a vazby. V závislosti na typ výrazu výpočtu, můžete představit jako způsob, jak vyjádřit monády, monoids, monad transformátory a applicative funktory. Ale na rozdíl od jiných jazyků (jako například *zápis* v Haskell), nejsou vázané na jednoho odběru a nespoléhejte na makra nebo jiné formy metaprogramování k provedení pohodlný a kontextová syntaxe.

## <a name="overview"></a>Přehled

Výpočty mohou mít mnoho forem. Nejběžnější forma výpočtu je spouštění s jedním vláknem, které je snadno srozumitelný a upravit. Ne všechny formy výpočet jsou však tak přímočaré jako spuštění s jedním vláknem. Možné příklady:

* Nedeterministické výpočty
* Asynchronní výpočty
* Effectful výpočty
* Tvoří výpočty

Obecně platí, existují *kontextové* výpočty, které je nutné provést v některých částí aplikace. Psaní kódu kontextové může být náročné, jako je "nevracení" výpočty mimo daný kontext bez odběrů a znemožnit vám tak snadné. Tato abstrakce jsou často náročné napsat sami, což je důvod, proč F# má zobecněné způsob, jak provést tzv **výrazech výpočtu**.

Výpočetní výrazy nabízí jednotnou syntaxi a abstrakce model pro kódování kontextové výpočty.

Každý výraz výpočtu tímto modulem stojí *Tvůrce* typu. Typ Tvůrce definuje operace, které jsou k dispozici pro výrazu výpočtu. V tématu [vytváří se nový typ z výrazu výpočtu](computation-expressions.md#creating-a-new-type-of-computation-expression), který ukazuje, jak vytvořit vlastní výpočet výraz.

### <a name="syntax-overview"></a>Přehled syntaxe

Všechny výpočetní výrazy mají následující podobu:

```
builder-expr { cexper }
```

kde `builder-expr` je název typu Tvůrce výrazu výpočtu definuje a `cexper` výraz tělo výrazu výpočtu. Například `async` kód výrazu výpočtu může vypadat například takto:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Je syntaxe speciální, navíc k dispozici v rámci výrazu výpočtu, jak je znázorněno v předchozím příkladu. Následující výraz formuláře je možné pomocí výrazů výpočtu:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Každá z těchto klíčových slov a ostatní standardní F# klíčová slova jsou k dispozici ve výrazu výpočtu, pouze pokud byla definována v základní typ Tvůrce. Jedinou výjimkou je `match!`, což je samotný syntaktické sugar pro použití `let!` následuje porovnávání na výsledek.

Typ Tvůrce je objekt, který definuje speciální metody, které řídí způsob, jakým jsou kombinované fragmenty výrazu výpočtu; To znamená její metody řídit chování výrazu výpočtu. Jiný způsob k popisu třídy tvůrce je Řekněme, že umožňuje přizpůsobit operace mnoha F# konstrukce, jako jsou smyčky a vazby.

### `let!`

`let!` – Klíčové slovo vytvoří vazbu na výsledek volání do jiného výrazu výpočtu k názvu:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Pokud je vytvořit vazbu volání výrazu výpočtu s `let`, nezískáte výsledek výrazu výpočtu. Místo toho je bude ovládací prvek vázán hodnotu *Nerealizovaná* volání tohoto výrazu výpočtu. Použití `let!` vytvořit vazbu k výsledku.

`let!` je definován `Bind(x, f)` člen v typu Tvůrce.

### `do!`

`do!` – Klíčové slovo je pro volání výrazu výpočtu, která vrátí `unit`– typ, jako jsou (definované `Zero` člen Tvůrce):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pro [asynchronního pracovního postupu](asynchronous-workflows.md), tento typ je `Async<unit>`. U jiných výrazech výpočtu typ by mohla být `CExpType<unit>`.

`do!` je definován `Bind(x, f)` člen v typu tvůrce, kde `f` vytváří `unit`.

### `yield`

`yield` – Klíčové slovo je tak, aby mohly využívat jako návratová hodnota z výrazu výpočtu <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Stejně jako u [yield – klíčové slovo v jazyce C#](../../csharp/language-reference/keywords/yield.md), každý prvek ve výrazu výpočtu, je vhodné, protože je provést iteraci.

`yield` je definován `Yield(x)` člen v typu tvůrce, kde `x` je položka výnosu zpět.

### `yield!`

`yield!` – Klíčové slovo je pro sloučení kolekci hodnot z výrazu výpočtu:

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

Po vyhodnocení výrazu výpočtu volány `yield!` budou mít položky vrátil zpět jeden po druhém, výsledek sloučení.

`yield!` je definován `YieldFrom(x)` člen v typu tvůrce, kde `x` je kolekce hodnot.

### `return`

`return` – Klíčové slovo obtéká hodnotu v typu odpovídá výrazu výpočtu. Kromě použití výrazech výpočtu `yield`, používá se "Dokončit" výrazu výpočtu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` je definován `Return(x)` člen v typu tvůrce, kde `x` je položka, kterou chcete zabalit.

### `return!`

`return!` – Klíčové slovo realizuje hodnotu výrazu výpočtu a zabalí výsledek typ odpovídající výrazu výpočtu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` je definován `ReturnFrom(x)` člen v typu tvůrce, kde `x` je jiného výrazu výpočtu.

### `match!`

Počínaje F# 4.5, `match!` – klíčové slovo vám umožní vložení volání jiného výpočtu výrazu a vzor se vyhledala shoda podle její výsledek:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Při volání výrazu výpočtu s `match!`, značným výsledek volání, například `let!`. To se často používá při volání výrazu výpočtu, kde výsledkem je [volitelné](options.md).

## <a name="built-in-computation-expressions"></a>Integrované výpočetní výrazy

F# Základní knihovna definuje tři předdefinované výpočetní výrazy: [Sekvence výrazů](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech dotazů](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Vytvoření nového typu výrazu výpočtu.

Vytvoření třídy tvůrce a definováním některých speciálních metod ve třídě můžete definovat vlastnosti výrazech výpočtu. Třída tvůrců Volitelně můžete definovat metody, jak je uvedeno v následující tabulce.

Následující tabulka popisuje metody, které je možné ve třídě Tvůrce pracovního postupu.

|**– Metoda**|**Typické podpisy**|**Popis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Volá se pro `let!` a `do!` ve výrazech výpočtu.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Zabalí výrazu výpočtu jako funkce.|
|`Return`|`'T -> M<'T>`|Volá se pro `return` ve výrazech výpočtu.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Volá se pro `return!` ve výrazech výpočtu.|
|`Run`|`M<'T> -> M<'T>` Nebo<br /><br />`M<'T> -> 'T`|Provede výrazu výpočtu.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` Nebo<br /><br />`M<unit> * M<'T> -> M<'T>`|Volá se pro určení posloupnosti ve výrazech výpočtu.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` Nebo<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Volá se pro `for...do` výrazy ve výrazech výpočtu.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Volá se pro `try...finally` výrazy ve výrazech výpočtu.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Volá se pro `try...with` výrazy ve výrazech výpočtu.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Volá se pro `use` vazby ve výrazech výpočtu.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Volá se pro `while...do` výrazy ve výrazech výpočtu.|
|`Yield`|`'T -> M<'T>`|Volá se pro `yield` výrazy ve výrazech výpočtu.|
|`YieldFrom`|`M<'T> -> M<'T>`|Volá se pro `yield!` výrazy ve výrazech výpočtu.|
|`Zero`|`unit -> M<'T>`|Volá se pro prázdný `else` větve z `if...then` výrazy ve výrazech výpočtu.|

Mnoho metod ve třídě Tvůrce používat a vrátit `M<'T>` konstrukce, která je obvykle samostatně definovaný typ, který charakterizuje druh výpočty se kombinovat, například, `Async<'T>` pro asynchronní pracovní postupy a `Seq<'T>` pro pracovní postupy pořadí. Podpisy z těchto metod je kombinovat a vnořené s kolegy a povolit tak, aby pracovní postup objekt vrácený z jednoho konstrukce mohou být předány Další. Kompilátor při analýze výrazu výpočtu, převede výraz na sérii volání vnořené funkce pomocí metod v předchozí tabulce a kódu ve výrazu výpočtu.

Vnořený výraz má následující formát:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Ve výše uvedeném kódu volání `Run` a `Delay` jsou vynechány, pokud nejsou definovány ve třídě Tvůrce výrazu výpočtu. Hlavní část výrazu výpočtu, zde označený jako `{| cexpr |}`, je přeložen do volání metody třídy tvůrce zahrnující podle překlady jsou popsané v následující tabulce. Výrazu výpočtu `{| cexpr |}` je definované rekurzivně podle tyto překlady kde `expr` je F# výraz a `cexpr` je výrazu výpočtu.

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

V předchozí tabulce `other-expr` popisuje výraz, který není jinak uvedená v tabulce. Třída tvůrců není potřeba implementovat všechny metody a podporují všechny převody uvedené v předchozí tabulce. Tyto konstrukce, které nejsou implementované nejsou k dispozici ve výrazech výpočtu daného typu. Například, pokud nechcete podporu `use` – klíčové slovo ve výrazech výpočtu, můžete vynechat definici `Use` ve své třídě Tvůrce.

Následující příklad kódu ukazuje, který zapouzdřuje výpočtu jako sérii kroků, které lze vyhodnotit jeden krok po jednom výrazu výpočtu. Rozlišované sjednocení typu A `OkOrException`, jak vyhodnotit zatím kóduje chybový stav výrazu. Tento kód ukazuje některé typické postupy, které můžete použít ve výrazech výpočtu, jako je například implementace často používaný text některé metody Tvůrce.

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

Výrazu výpočtu má základní typ, který vrací výraz. Nadřazený typ může představovat vypočítaný výsledek nebo opožděné výpočty, které lze provést nebo může poskytnout způsob, jak k iteraci v rámci nějaký typ kolekce. V předchozím příkladu byl nadřazený typ **nakonec**. Pro výraz pořadí základní typ je <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pro výraz dotazu, je základní typ <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Pro asynchronní pracovní postup, je základní typ [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Objekt představuje práce, která musí provést k výpočtu výsledku. Například volání [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) k provedení výpočtu a vrátí výsledek.

## <a name="custom-operations"></a>Vlastní operace

Můžete definovat vlastní operace na výrazu výpočtu a použít vlastní operace jako operátor ve výrazu výpočtu. Můžete například zahrnout – operátor dotazu ve výrazu dotazu. Když definujete vlastní operace, je nutné definovat výnos a pro metody ve výrazu výpočtu. K definování vlastní operace put ve třídě Tvůrce výrazu výpočtu a pak použít [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Tento atribut přijímá řetězec jako argument, což je název, který se má použít v rámci vlastní operace. Tento název vstupu do oboru na začátku otevírající složenou závorku výrazu výpočtu. Proto byste neměli používat identifikátory, které mají stejný název jako vlastní operace v tomto bloku. Například vyhnout použití identifikátorů, jako `all` nebo `last` ve výrazech dotazů.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Rozšíření stávajících počítačů s nové vlastní operace

Pokud už máte třídu tvůrce, je možné rozšířit své vlastní operace z mimo tuto třídu Tvůrce. Rozšíření musí deklarovat v modulech. Obory názvů nemůžou obsahovat členy rozšíření s výjimkou ve stejném souboru a do stejné skupiny deklarace oboru názvů, kde je definován typ.

Následující příklad ukazuje rozšíření existující `Microsoft.FSharp.Linq.QueryBuilder` třídy.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Asynchronní pracovní postupy](asynchronous-workflows.md)
- [Sekvence](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Výrazy dotazu](query-expressions.md)
