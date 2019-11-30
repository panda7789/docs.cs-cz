---
title: Anonymní záznamy
description: Naučte se používat vytváření a používání anonymních záznamů, funkce jazyka, která pomáhá s manipulací s daty.
ms.date: 06/12/2019
ms.openlocfilehash: 0a7a819cc471c6579feacd621ed15aa89a6423ba
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569475"
---
# <a name="anonymous-records"></a>Anonymní záznamy

Anonymní záznamy jsou jednoduché agregované pojmenované hodnoty, které není nutné deklarovat před použitím. Můžete je deklarovat buď jako struktury, nebo na typy odkazů. Ve výchozím nastavení se jedná o typy odkazů.

## <a name="syntax"></a>Syntaxe

Následující příklady ukazují syntaxi anonymního záznamu. Položky s oddělovači `[item]` jsou volitelné.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Základní využití

Anonymní záznamy se nejlépe považují za F# typy záznamů, které není nutné deklarovat před vytvořením instance.

Tady je příklad, jak můžete pracovat s funkcí, která vytváří anonymní záznam:

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

V následujícím příkladu se rozšíří na předchozí s funkcí `printCircleStats`, která přebírá anonymní záznam jako vstup:

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

Volání `printCircleStats` s jakýmkoli typem anonymního záznamu, který nemá stejný "tvar", protože vstupní typ se nepodaří zkompilovat:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Strukturování anonymních záznamů

Anonymní záznamy lze definovat také jako strukturu s nepovinným klíčovým slovem `struct`. Následující příklad rozšiřuje předchozí vyprodukováním a spotřebou anonymního záznamu struktury:

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

### <a name="structness-inference"></a>Odvození struktury

Strukturování anonymních záznamů také umožňuje "odvození struktury", kde není nutné zadávat klíčové slovo `struct` na webu volání. V tomto příkladu jste při volání `printCircleStats`Elide klíčové slovo `struct`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Zpětný vzor – určení `struct`, když není vstupní typ struktura anonymního záznamu – selže kompilace.

## <a name="embedding-anonymous-records-within-other-types"></a>Vkládání anonymních záznamů v rámci jiných typů

Je užitečné deklarovat [rozlišené sjednocení](discriminated-unions.md) , jejichž případy jsou záznamy. Pokud jsou však data v záznamech stejného typu jako rozlišené sjednocení, je nutné definovat všechny typy jako vzájemně rekurzivní. Použití anonymních záznamů zabraňuje tomuto omezení. Co následuje příklad typu a funkce, pro kterou odpovídá vzorek:

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

## <a name="copy-and-update-expressions"></a>Výrazy kopírování a aktualizace

Anonymní záznamy podporují vytváření pomocí [výrazů kopírování a aktualizace](copy-and-update-record-expressions.md). Tady je příklad, jak můžete vytvořit novou instanci anonymního záznamu, který zkopíruje existující data:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Na rozdíl od pojmenovaných záznamů ale anonymní záznamy umožňují vytvořit zcela různé formuláře s výrazy kopírování a aktualizace. Následující příklad používá stejný anonymní záznam z předchozího příkladu a rozbalí ho do nového anonymního záznamu:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Je také možné vytvořit anonymní záznamy z instancí pojmenovaných záznamů:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Můžete také kopírovat data do a z odkazů a struktury anonymních záznamů:

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

Anonymní záznamy mají řadu vlastností, které jsou nezbytné pro úplné porozumění způsobu jejich použití.

### <a name="anonymous-records-are-nominal"></a>Anonymní záznamy jsou nominální

Anonymní záznamy jsou [nominální typy](https://en.wikipedia.org/wiki/Nominal_type_system). Nejlépe se považují za pojmenované typy [záznamů](records.md) (které jsou také nominální), které nevyžadují deklaraci předem.

Vezměte v úvahu následující příklad se dvěma deklaracemi anonymního záznamu:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Hodnoty `x` a `y` mají různé typy a nejsou kompatibilní mezi sebou. Nejsou shodné a nejsou srovnatelné. K ilustraci použijte podobný záznam s názvem:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

U anonymních záznamů se v porovnání s jejich pojmenovaným záznamem neliší žádné podstatné informace, které se týkají rovnocennosti typu nebo porovnání.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonymní záznamy používají strukturální rovnost a porovnávání.

Podobně jako typy záznamů jsou anonymní záznamy strukturované a srovnatelné. To platí pouze v případě, že všechny typy prvků podporují rovnost a porovnávání, jako u typů záznamů. Pro podporu rovnosti nebo porovnání musí mít dva anonymní záznamy stejný "tvar".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonymní záznamy jsou serializovatelné.

Anonymní záznamy můžete serializovat stejně jako u pojmenovaných záznamů. Tady je příklad použití [Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonymní záznamy jsou užitečné pro posílání odlehčených dat v síti, aniž by bylo potřeba definovat doménu pro serializované/deserializované typy vpřed.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonymní záznamy spolupracující s C# anonymními typy

Je možné použít rozhraní .NET API, které vyžaduje použití [ C# anonymních typů](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#anonymní typy jsou triviální pro spolupráci s použitím anonymních záznamů. Následující příklad ukazuje způsob použití anonymních záznamů pro volání přetížení [LINQ](../../csharp/programming-guide/concepts/linq/index.md) , které vyžaduje anonymní typ:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

V rozhraní .NET je velké množství dalších rozhraní API, které vyžaduje použití předávání anonymního typu. Anonymní záznamy jsou nástroje pro práci s nimi.

## <a name="limitations"></a>Omezení

Anonymní záznamy mají určitá omezení používání. Některé jsou podstatou jejich návrhu, ale jiné jsou snadněji ke změně.

### <a name="limitations-with-pattern-matching"></a>Omezení s porovnáváním vzorů

Anonymní záznamy nepodporují porovnávání vzorů, na rozdíl od pojmenovaných záznamů. Existují tři důvody:

1. Vzor by musel být pro každé pole anonymního záznamu vyúčtován na rozdíl od pojmenovaných typů záznamů. Je tomu tak proto, že anonymní záznamy nepodporují strukturální podtypování – jedná se o nominální typy.
2. Vzhledem k tomu, že je (1), není možné mít ve výrazu porovnávání vzorů další vzory, protože každý odlišný vzor by znamenal jiný typ anonymního záznamu.
3. Z důvodu (3) by byl jakýkoli vzor anonymního záznamu podrobnější než použití notace "tečka".

Existuje návrh otevřeného jazyka, který umožňuje [porovnávání vzorů v omezeném kontextu](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Omezení pomocí proměnlivost

V současné době není možné definovat anonymní záznam s `mutable`mi daty. K dispozici je [Návrh otevřeného jazyka](https://github.com/fsharp/fslang-suggestions/issues/732) , který povoluje proměnlivá data.

### <a name="limitations-with-struct-anonymous-records"></a>Omezení pomocí anonymních záznamů struktury

Není možné deklarovat anonymní záznamy struktury jako `IsByRefLike` nebo `IsReadOnly`. K dispozici je [Návrh otevřeného jazyka](https://github.com/fsharp/fslang-suggestions/issues/712) pro `IsByRefLike` a `IsReadOnly` anonymní záznamy.
