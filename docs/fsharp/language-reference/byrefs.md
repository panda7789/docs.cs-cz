---
title: Parametry ByRef
description: Seznamte se s typy ByRef a ByRef jako F#v, které se používají pro programování na nízké úrovni.
ms.date: 11/04/2019
ms.openlocfilehash: 05a40059ad5b72829233b0c4135c76eb1cff4da5
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965812"
---
# <a name="byrefs"></a>Parametry ByRef

F#má dvě hlavní oblasti funkcí, které se týkají prostoru programování nízké úrovně:

* `byref`/`inref`/typy `outref`, což jsou spravované ukazatele. Mají omezení používání, takže nemůžete kompilovat program, který je neplatný v době běhu.
* Struktura podobná `byref`, což je [Struktura](structures.md) , která má podobnou sémantiku a stejná omezení při kompilaci jako `byref<'T>`. Jedním z příkladů je <xref:System.Span%601>.

## <a name="syntax"></a>Syntaxe

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>ByRef, inref a outref

Existují tři formy `byref`:

* `inref<'T>`spravovaný ukazatel pro čtení podkladové hodnoty.
* `outref<'T>`spravovaný ukazatel pro zápis na podkladovou hodnotu.
* `byref<'T>`spravovaný ukazatel pro čtení a zápis základní hodnoty.

`byref<'T>` lze předat, pokud je očekávána `inref<'T>`. Podobně je možné předat `byref<'T>`, kde se očekává `outref<'T>`.

## <a name="using-byrefs"></a>Použití ByRef

Chcete-li použít `inref<'T>`, je třeba získat hodnotu ukazatele s `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Chcete-li zapisovat do ukazatele pomocí `outref<'T>` nebo `byref<'T>`, je nutné také nastavit hodnotu, kterou jste převedli ukazatel na `mutable`.

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Pokud pouze píšete ukazatel namísto čtení, zvažte použití `outref<'T>` místo `byref<'T>`.

### <a name="inref-semantics"></a>Sémantika Inref

Vezměte v úvahu následující kód:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Sémantika znamená následující:

* Držitel `x`ového ukazatele ho může použít jenom ke čtení hodnoty.
* Jakýkoli ukazatel získaný pro `struct` polí vnořených v rámci `SomeStruct` je uveden typ `inref<_>`.

Platí to i pro následující skutečnosti:

* Neexistují žádné nenásobení, že k `x`nejsou k dispozici další vlákna nebo aliasy.
* Neexistuje žádné nenásobení, které `SomeStruct` není proměnlivé na základě `x` je `inref`.

U F# typů hodnot, které **jsou** neměnné, však je ukazatel `this` odvozen jako `inref`.

Všechna tato pravidla dohromady znamenají, že držitel `inref`ového ukazatele nemůže upravit okamžitý obsah paměti, na kterou se odkazuje.

### <a name="outref-semantics"></a>Sémantika Outref

Účelem `outref<'T>` je označit, že ukazatel by měl zapisovat pouze do. Neočekávaně `outref<'T>` povoluje čtení základní hodnoty navzdory jejímu názvu. Jedná se o účely kompatibility. Sémanticky, `outref<'T>` se neliší od `byref<'T>`.

### <a name="interop-with-c"></a>Spolupráce s C\#

C#Kromě `ref` vrací i klíčová slova `in ref` a `out ref`. Následující tabulka ukazuje, jak F# interpretuje, C# co emituje:

|C#Contains|F#odvodí|
|------------|---------|
|`ref` návratová hodnota|`outref<'T>`|
|`ref readonly` návratová hodnota|`inref<'T>`|
|`in ref` parametr|`inref<'T>`|
|`out ref` parametr|`outref<'T>`|

Následující tabulka ukazuje, co F# emituje:

|F#Contains|Emited – konstrukce|
|------------|-----------------|
|Argument `inref<'T>`|atribut `[In]` v argumentu|
|`inref<'T>` návrat|`modreq` atribut pro hodnotu|
|`inref<'T>` v abstraktní patici nebo implementaci|`modreq` argumentu nebo návratem|
|Argument `outref<'T>`|atribut `[Out]` v argumentu|

### <a name="type-inference-and-overloading-rules"></a>Odvození typu a pravidla přetížení

Typ `inref<'T>` je odvozen F# kompilátorem v následujících případech:

1. Parametr nebo návratový typ .NET, který má atribut `IsReadOnly`.
2. Ukazatel `this` u typu struktury, který nemá žádná proměnlivá pole.
3. Adresa umístění v paměti odvozeného od jiného ukazatele `inref<_>`.

Když je využívána implicitní adresa `inref`, přetížení s argumentem typu `SomeType` je upřednostňováno na přetížení s argumentem typu `inref<SomeType>`. Příklad:

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

V obou případech jsou přetížení přebírající `System.DateTime` vyřešeny, nikoli přetížení, které přebírají `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>Struktury podobné typu ByRef

Kromě `byref`/`inref`/`outref` trojice můžete definovat vlastní struktury, které mohou splňovat `byref`jako sémantiku. To se provádí s atributem <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` neznamená `Struct`. Oba typy musí být k dispozici na typu.

Struktura "`byref`jako" v F# je typ hodnoty vázané na zásobník. Nikdy se nepřiřazuje na spravovanou haldu. Struktura podobná `byref`je užitečná pro vysoce výkonné programování, protože se vynutila se sadou silných kontrol životního cyklu životnosti a bez zachycení. Pravidla jsou:

* Mohou být použity jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.
* Nemohou být statické nebo členy instance třídy nebo normální struktury.
* Nemohou být zachyceny žádnou uzavírací konstrukcí (`async` metody nebo lambda výrazy).
* Nelze je použít jako obecný parametr.

Tento poslední bod je rozhodující pro F# programování ve stylu kanálu, protože `|>` je obecná funkce, která parameterizes své vstupní typy. Toto omezení může být pro `|>` v budoucnu odlehčené, protože je vložené a neprovádí v těle žádné volání obecných funkcí, které nejsou vloženy.

I když tato pravidla omezují použití, tak aby mohli bezpečným způsobem plnit vysoce výkonné výpočetní výkon.

## <a name="byref-returns"></a>ByRef – vrácené hodnoty

Návratové hodnoty F# ByRef z funkcí nebo členů lze vytvářet a spotřebovat. Při zpracování metody vracené `byref`se hodnota implicitně odkázat. Příklad:

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Chcete-li vrátit hodnotu ByRef, proměnná, která obsahuje hodnotu, musí být živá déle než aktuální obor.
Také pro návrat typu ByRef použijte & Value (kde value je proměnná, která je větší než aktuální rozsah).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Chcete-li se vyhnout implicitnímu odkázání, jako je například předání odkazu prostřednictvím více zřetězených volání, použijte `&x` (kde `x` je hodnota).

Můžete také přímo přiřadit k návratové `byref`. Vezměte v úvahu následující (vysoce imperativně) program:

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

Toto je výstup:

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Určení rozsahu pro parametry ByRef

Hodnota vazby `let`nemůže mít odkaz nad rámec, ve kterém byla definována. Například následující příkaz není povolen:

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

To vám zabrání v získání různých výsledků v závislosti na tom, jestli kompilujete s optimalizací nebo vypnuto.
