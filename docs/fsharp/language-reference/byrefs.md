---
title: Parametry ByRef
description: Další informace o typu byref a typů předávané v F#, které se používají pro programování nízké úrovně.
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055362"
---
# <a name="byrefs"></a>Parametry ByRef

F#má dva hlavním oblastem funkcí, které pracují v prostoru nízké úrovně programování:

* `byref` / `inref` / `outref` Typy, které jsou spravované ukazatele. Mají omezení týkající se použití tak, aby program, který není platný v době běhu nelze zkompilovat.
* A `byref`– například struktura, která je [struktura](structures.md) , který má podobnou sémantikou a omezení kompilace jako `byref<'T>`. Jedním z příkladů je <xref:System.Span%601>.

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

* `inref<'T>`, spravovaného ukazatele pro čtení zdrojovou hodnotu.
* `outref<'T>`, spravovaného ukazatele k zápisu do základní hodnotu.
* `byref<'T>`, spravovaného ukazatele pro čtení a zápis zdrojovou hodnotu.

A `byref<'T>` mohou být předány kde `inref<'T>` očekává. Podobně `byref<'T>` mohou být předány kde `outref<'T>` očekává.

## <a name="using-byrefs"></a>Pomocí ByRef

Použití `inref<'T>`, je potřeba získat hodnotu ukazatele s `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Zapsat do ukazatele s použitím `outref<'T>` nebo `byref<'T>`, musíte také vzít ukazatel na hodnotu `mutable`.

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

Pokud vytváříte pouze ukazatele namísto jeho čtení, zvažte použití `outref<'T>` místo `byref<'T>`.

### <a name="inref-semantics"></a>Sémantika Inref

Vezměte v úvahu následující kód:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Sémanticky to znamená, následující:

* Držitel `x` ukazatele mohou používat pouze se načíst hodnotu.
* Získat jakýkoli ukazatel na `struct` pole vnořené `SomeStruct` se daný typ `inref<_>`.

Toto je také true:

* Neexistuje žádné nepřímo další vlákna nebo aliasy nemáte oprávnění k zápisu do `x`.
* Neexistuje žádné nepřímo, který `SomeStruct` je neměnný základě `x` právě `inref`.

Ale pro F# hodnotové typy, které **jsou** neměnné, `this` odvozena jako ukazatel `inref`.

Všechna tato pravidla společně znamenají, že držitele `inref` ukazatel nesmíte upravovat okamžité obsah paměti, který ukazatel ukazuje.

### <a name="outref-semantics"></a>Sémantika Outref

Účelem `outref<'T>` se k označení, že ukazatele by měli číst jenom z. Nečekaně `outref<'T>` povolí čtení základní hodnotu bez ohledu na jeho název. Toto je pro účely kompatibility. Sémanticky `outref<'T>` se nijak neliší od `byref<'T>`.

### <a name="interop-with-c"></a>Interoperabilita s C\#

C# podporuje `in ref` a `out ref` klíčová slova, kromě `ref` vrátí. Následující tabulka ukazuje, jak F# interpretuje co C# vysílá:

|Konstrukce jazyka C#|F#odvodí z něj|
|------------|---------|
|`ref` Návratová hodnota|`outref<'T>`|
|`ref readonly` Návratová hodnota|`inref<'T>`|
|`in ref` Parametr|`inref<'T>`|
|`out ref` Parametr|`outref<'T>`|

V následující tabulce jsou uvedeny co F# vysílá:

|F#konstrukce|Emitovaný konstrukce|
|------------|-----------------|
|`inref<'T>` Argument|`[In]` atribut na argumentu|
|`inref<'T>` Vrátí|`modreq` atribut na hodnotu|
|`inref<'T>` abstraktní datovou oblast nebo provádění|`modreq` v argumentu nebo return|
|`outref<'T>` Argument|`[Out]` atribut na argumentu|

### <a name="type-inference-and-overloading-rules"></a>Odvození typu proměnné a přetížení pravidla

`inref<'T>` Typu odvozuje F# kompilátoru v následujících případech:

1. Parametr nebo návratový typ .NET, který má `IsReadOnly` atribut.
2. `this` Ukazatel na strukturu typu, který nemá žádné proměnlivé pole.
3. Adresa umístění v paměti odvozené z jiného `inref<_>` ukazatele.

Když implicitní adresu `inref` jsou přijata, přetížení s parametrem typu `SomeType` je upřednostňována před přetížení s parametrem typu `inref<SomeType>`. Příklad:

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

V obou případech se přetížení, přičemž `System.DateTime` jsou vyřešeny místo přetížení, přičemž `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>Struktury předávání odkazem.

Kromě `byref` / `inref` / `outref` trojice, můžete definovat vlastní struktury, která může splňovat `byref`-sémantiky, jako je. Používá se k tomu <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atribut:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` neznamená `Struct`. Oba musí být k dispozici u typu.

A "`byref`– stejně jako" struktura v F# je typ hodnoty vázané na zásobníku. Přiděluje se nikdy na spravované haldě. A `byref`– jako – struktura je užitečné pro vysoce výkonné programování, jak se vynucuje sadu silné kontroly o životnost a zachycení snímků. Pravidla jsou:

* Se může sloužit jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.
* Nemohou být statické nebo členy třídy či struktury normální instance.
* Nemůže být zachyceno libovolné konstrukce uzavření (`async` metodách a výrazech lambda).
* Nelze je použít jako na generický parametr.

Tento poslední bod je zásadní pro F# programování ve stylu kanálu jako `|>` je obecný, který parametrizuje vstupní typy. funkce. Toto omezení mohou být zmírněny pro `|>` v budoucnu, jako je vložená a nepoužívá všechna volání do jiných vložených obecné funkce v těle.

I když tato pravidla omezují velmi silného využití, dělají to ke splnění uskutečnění vysokovýkonného výpočetního prostředí bezpečným způsobem.

## <a name="byref-returns"></a>Hodnoty typu ByRef

ByRef vrátí z F# funkce nebo členy můžete vytvořen a využívat. Při využívání `byref`– vrátí metoda hodnotu přistoupí implicitně přes ukazatel. Příklad:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Chcete-li zabránit implicitní zrušení odkazu, například předání odkazem do více zřetězených volání, použijte `&x` (kde `x` je hodnota).

Můžete také přímo přiřadit k vrácení `byref`. Vezměte v úvahu následující program (vysoce imperativní):

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

## <a name="scoping-for-byrefs"></a>Vytváření oborů pro parametry ByRef

A `let`-vázaná hodnota nemůže mít svůj odkaz překročí obor, ve kterém byl definován. Například následující není povolena:

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

Předchází se tak získání odlišné výsledky v závislosti na tom, pokud kompilujete s optimalizací zapnutí nebo vypnutí.
