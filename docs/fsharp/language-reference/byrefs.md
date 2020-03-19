---
title: Parametry ByRef
description: Další informace o byref a byref-like typy v F#, které se používají pro programování nižší úrovně.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187054"
---
# <a name="byrefs"></a>Parametry ByRef

F# má dvě hlavní oblasti funkcí, které se zabývají v prostoru programování nízké úrovně:

* `byref` / `inref` Typy, / `outref` které jsou spravované ukazatele. Mají omezení použití, takže nelze zkompilovat program, který je neplatný za běhu.
* -like `byref`struct, což je [struktura,](structures.md) která má podobnou sémantiku a stejné omezení kompilace jako `byref<'T>`. Jedním z <xref:System.Span%601>příkladů je .

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

## <a name="byref-inref-and-outref"></a>Byref, inref a outref

Existují tři formy `byref`:

* `inref<'T>`, spravovaný ukazatel pro čtení základní hodnoty.
* `outref<'T>`, spravovaný ukazatel pro zápis do podkladové hodnoty.
* `byref<'T>`, spravovaný ukazatel pro čtení a zápis podkladové hodnoty.

A `byref<'T>` může být `inref<'T>` předána tam, kde se očekává. Podobně může `byref<'T>` být předána, `outref<'T>` kde se očekává.

## <a name="using-byrefs"></a>Použití byrefs

Chcete-li `inref<'T>`použít , je třeba `&`získat hodnotu ukazatele s :

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Chcete-li zapsat na `outref<'T>` `byref<'T>`ukazatel pomocí nebo , musíte také `mutable`provést hodnotu, na kterou ukazatel uchopíte .

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

Pokud ukazatel píšete pouze místo toho, `outref<'T>` abyste `byref<'T>`ho četli, zvažte použití místo .

### <a name="inref-semantics"></a>Sémantiku inref

Uvažujte následující kód:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Sémanticky to znamená následující:

* Držitel `x` ukazatele jej může použít pouze ke čtení hodnoty.
* Všechny ukazatele `struct` získané na `SomeStruct` pole vnořené v rámci jsou uvedeny typu `inref<_>`.

Platí také toto:

* Neexistuje žádný důsledek, že jiná vlákna nebo `x`aliasy nemají přístup pro zápis do aplikace .
* Neexistuje žádný důsledek, který `SomeStruct` je neměnný na `x` základě toho, že `inref`je .

Pro typy hodnot F#, které **jsou** neměnné, je však `this` ukazatel odvozen za . `inref`

Všechna tato pravidla společně znamenají, `inref` že držitel ukazatele nemusí změnit okamžitý obsah paměti, na kterou se odkazuje.

### <a name="outref-semantics"></a>Sémantiku předčí

Účelem `outref<'T>` je označit, že ukazatel by měl být zapsán pouze do. Neočekávaně `outref<'T>` umožňuje čtení základní hodnoty i přes jeho název. Toto je pro účely kompatibility. Sémanticky, `outref<'T>` se `byref<'T>`nijak neliší od .

### <a name="interop-with-c"></a>Interop s C\#

C# podporuje `in ref` `out ref` a klíčová slova, `ref` kromě vrátí. Následující tabulka ukazuje, jak F# interpretuje to, co c# vydává:

|Konstrukce jazyka C#|F# odvodí|
|------------|---------|
|`ref`vrácená hodnota|`outref<'T>`|
|`ref readonly`vrácená hodnota|`inref<'T>`|
|`in ref`Parametr|`inref<'T>`|
|`out ref`Parametr|`outref<'T>`|

V následující tabulce je uvedeno, co f# vyzařuje:

|F# konstrukce|Vyzařovaná konstrukce|
|------------|-----------------|
|Argument `inref<'T>`|`[In]`atribut na argumentu|
|`inref<'T>`Vrátit|`modreq`atribut na hodnotě|
|`inref<'T>`v abstraktním slotu nebo implementaci|`modreq`na argument nebo návrat|
|Argument `outref<'T>`|`[Out]`atribut na argumentu|

### <a name="type-inference-and-overloading-rules"></a>Pravidla odvození typu a přetížení

Typ `inref<'T>` je odvozen kompilátorem F#v následujících případech:

1. Parametr .NET nebo návratový `IsReadOnly` typ, který má atribut.
2. Ukazatel `this` na typ struktury, který nemá žádná proměnlivá pole.
3. Adresa umístění paměti odvozené z `inref<_>` jiného ukazatele.

Při implicitní adresu `inref` je přijata, přetížení s `SomeType` argumentem typu je upřednostňována přetížení s argumentem typu `inref<SomeType>`. Například:

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

V obou případech přetížení `System.DateTime` přičemž jsou vyřešeny `inref<System.DateTime>`spíše než přetížení přičemž .

## <a name="byref-like-structs"></a>Byref-jako struktury

Kromě tria `byref` / `inref` / `outref` můžete definovat vlastní struktury, které mohou `byref`dodržovat sémantiku jako. To se provádí <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> s atributem:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`neznamená `Struct`. Oba musí být přítomen na typu.

Struktura`byref`"-like" v F# je typ hodnoty vázaný na zásobník. Nikdy přidělena na spravované haldy. -like `byref`struct je užitečné pro vysoce výkonné programování, protože je vynuceno se sadou silných kontrol o životnosti a bez zachycení. Pravidla jsou:

* Mohou být použity jako parametry funkce, parametry metody, lokální proměnné, výnosy metod.
* Nemohou být statické nebo instance členy třídy nebo normální struktury.
* Nemohou být zachyceny žádnou`async` uzavírací konstrukcí (metodami nebo výrazy lambda).
* Nelze je použít jako obecný parametr.

Tento poslední bod je rozhodující pro programování `|>` ve stylu kanálu F#, stejně jako obecná funkce, která parametrizuje jeho vstupní typy. Toto omezení může `|>` být uvolněno pro v budoucnu, protože je vložené a neprovádí žádné volání na nevložené obecné funkce v jeho těle.

Přestože tato pravidla silně omezují použití, činí tak, aby splnila slib vysoce výkonnévýpočetní techniky bezpečným způsobem.

## <a name="byref-returns"></a>Byref vrátí

Byref vrátí z F# funkce nebo členy mohou být vyrobeny a spotřebovány. Při spotřebovávání `byref`-returning metoda, hodnota je implicitně dereferenced. Například:

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Chcete-li vrátit hodnotu byref, proměnná, která obsahuje hodnotu musí žít déle než aktuální obor.
Chcete-li vrátit byref, použijte `&value` (kde hodnota je proměnná, která žije déle než aktuální obor).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Chcete-li se vyhnout implicitní dereference, jako je `&x` například `x` předávání odkazu prostřednictvím více zřetězených volání, použijte (kde je hodnota).

Můžete také přímo přiřadit `byref`k návratu . Zvažte následující (velmi imperativní) program:

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

## <a name="scoping-for-byrefs"></a>Vymezení oborů pro byrefs

Hodnota `let`-bound nemůže mít svůj odkaz překročit rozsah, ve kterém byla definována. Například následující je zakázáno:

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

Tím zabráníte získání různých výsledků v závislosti na tom, zda kompilujete s optimalizací nebo ne.
