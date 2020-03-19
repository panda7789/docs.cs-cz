---
title: Anonymní záznamy
description: Naučte se používat konstrukce a použití anonymních záznamů, což je jazyková funkce, která pomáhá při manipulaci s daty.
ms.date: 06/12/2019
ms.openlocfilehash: ef3aa8fccdb6ff406542932816e4138040845a59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187497"
---
# <a name="anonymous-records"></a>Anonymní záznamy

Anonymní záznamy jsou jednoduché agregace pojmenovaných hodnot, které není nutné deklarovat před použitím. Můžete je deklarovat jako struktury nebo typy odkazů. Ve výchozím nastavení se neje vypořádají referenčními typy.

## <a name="syntax"></a>Syntaxe

Následující příklady ukazují syntaxi anonymního záznamu. Položky oddělené `[item]` jako volitelné.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Základní použití

Anonymní záznamy jsou nejlépe myšlenka jako F# typy záznamů, které není nutné deklarovat před instanci.

Zde například můžete pracovat s funkcí, která vytváří anonymní záznam:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Následující příklad rozbalí předchozí s `printCircleStats` funkcí, která bere anonymní záznam jako vstup:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

Volání `printCircleStats` s libovolným anonymním typem záznamu, který nemá stejný "tvar" jako vstupní typ, se nepodaří zkompilovat:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Strukturovat anonymní záznamy

Anonymní záznamy lze také definovat jako `struct` strukturu s volitelným klíčovým slovem. Následující příklad rozšiřuje předchozí tím, že produkuje a spotřebovává nitanonymní záznam:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Závěr o struktuře

Strukturovat anonymní záznamy také umožňují "odvození struktury", kde není `struct` nutné zadat klíčové slovo na webu volání. V tomto příkladu můžete `struct` elide `printCircleStats`klíčové slovo při volání :

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Reverzní vzor - `struct` určující, kdy vstupní typ není nitanonymní záznam - se nezdaří kompilovat.

## <a name="embedding-anonymous-records-within-other-types"></a>Vkládání anonymních záznamů do jiných typů

Je užitečné deklarovat [diskriminované odbory,](discriminated-unions.md) jejichž případy jsou záznamy. Ale pokud data v záznamech je stejný typ jako discriminated unie, je nutné definovat všechny typy jako vzájemně rekurzivní. Použití anonymních záznamů zabrání toto omezení. Následuje příklad typu a funkce, která se nad ním shoduje:

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>Kopírování a aktualizace výrazů

Anonymní záznamy podporují konstrukci s [výrazy kopírování a aktualizace](copy-and-update-record-expressions.md). Můžete například vytvořit novou instanci anonymního záznamu, který kopíruje data existujícího:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Na rozdíl od pojmenovaných záznamů však anonymní záznamy umožňují vytvářet zcela odlišné formuláře s výrazy kopírování a aktualizace. Následující příklad převezme stejný anonymní záznam z předchozího příkladu a rozbalí jej na nový anonymní záznam:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Je také možné vytvářet anonymní záznamy z instancí pojmenovaných záznamů:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Můžete také kopírovat data do a z referenčních a strukturovaných anonymních záznamů:

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>Vlastnosti anonymních záznamů

Anonymní záznamy mají řadu charakteristik, které jsou nezbytné pro úplné pochopení, jak mohou být použity.

### <a name="anonymous-records-are-nominal"></a>Anonymní záznamy jsou nominální

Anonymní záznamy jsou [nominální typy](https://en.wikipedia.org/wiki/Nominal_type_system). Oni jsou nejlépe myšlenka jako pojmenované typy [záznamů](records.md) (které jsou také nominální), které nevyžadují předem prohlášení.

Zvažte následující příklad se dvěma anonymními deklaracemi záznamů:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Hodnoty `x` `y` a mají různé typy a nejsou vzájemně kompatibilní. Nejsou schavitelné a nejsou srovnatelné. Pro ilustraci zvažte pojmenovaný ekvivalent záznamu:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Neexistuje nic ze své podstaty odlišné o anonymní záznamy ve srovnání s jejich pojmenované ekvivalenty záznamu, pokud jde o typ ekvivalence nebo porovnání.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonymní záznamy používají strukturální rovnost a porovnání

Stejně jako typy záznamů jsou anonymní záznamy strukturálně srovnatelné a srovnatelné. To platí pouze v případě, že všechny typy složek podporují rovnost a porovnání, jako u typů záznamů. Pro podporu rovnosti nebo porovnání musí mít dva anonymní záznamy stejný "tvar".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonymní záznamy lze serializovat.

Anonymní záznamy můžete serializovat stejně jako s pojmenovanými záznamy. Zde je příklad pomocí [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonymní záznamy jsou užitečné pro odesílání zjednodušených dat v síti bez nutnosti definovat doménu pro serializované/rekonstruované typy předem.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonymní záznamy spolupracují s anonymními typy jazyka C#

Je možné použít rozhraní .NET API, které vyžaduje použití [anonymních typů jazyka C#](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C# anonymní typy jsou triviální pro vzájemnou prosazení pomocí anonymních záznamů. Následující příklad ukazuje, jak pomocí anonymních záznamů volat [přetížení LINQ,](../../csharp/programming-guide/concepts/linq/index.md) které vyžaduje anonymní typ:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Existuje velké množství dalších rozhraní API používané v celé .NET, které vyžadují použití předávání v anonymní typ. Anonymní záznamy jsou vaším nástrojem pro práci s nimi.

## <a name="limitations"></a>Omezení

Anonymní záznamy mají určitá omezení v jejich použití. Některé z nich jsou vlastní jejich designu, ale jiní jsou přístupné ke změně.

### <a name="limitations-with-pattern-matching"></a>Omezení s porovnáváním vzorů

Anonymní záznamy nepodporují porovnávání vzorů, na rozdíl od pojmenovaných záznamů. Existují tři důvody:

1. Vzor by musel odpovídat za každé pole anonymního záznamu, na rozdíl od pojmenovaných typů záznamů. Je to proto, že anonymní záznamy nepodporují strukturální subtypování – jsou to nominální typy.
2. Z důvodu (1) není možné mít další vzory ve výrazu shody vzoru, protože každý odlišný vzor by znamenal jiný anonymní typ záznamu.
3. Z důvodu (3) by jakýkoli anonymní záznam vzor by být podrobnější než použití "tečka" zápis.

Existuje otevřený jazyk návrh [povolit porovnávání vzorů v omezených kontextech](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Omezení s proměnlivostí

V současné době není možné definovat `mutable` anonymní záznam s daty. Existuje [návrh otevřeného jazyka,](https://github.com/fsharp/fslang-suggestions/issues/732) který umožňuje proměnlivá data.

### <a name="limitations-with-struct-anonymous-records"></a>Omezení s nitkovými anonymními záznamy

Není možné deklarovat struktury `IsByRefLike` anonymní `IsReadOnly`záznamy jako nebo . Existuje [otevřený jazyk návrh](https://github.com/fsharp/fslang-suggestions/issues/712) `IsByRefLike` pro `IsReadOnly` anonymní záznamy.
