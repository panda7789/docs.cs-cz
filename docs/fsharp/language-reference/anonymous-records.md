---
title: Anonymní záznamů
description: Zjistěte, jak použít konstrukce a použít anonymní záznamy, funkce jazyka, který pomáhá při manipulaci s daty.
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041794"
---
# <a name="anonymous-records"></a>Anonymní záznamů

Anonymní záznamy jsou jednoduché agregace pojmenovaných hodnot, které nemusí být deklarované před použitím. Můžete je deklarovat jako typy struktur nebo odkaz. Jsou to typy odkazů ve výchozím nastavení.

## <a name="syntax"></a>Syntaxe

Následující příklady ukazují syntaxi anonymní záznamu. Oddělené položky jako `[item]` jsou volitelné.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Základní informace o využití

Anonymní záznamy jsou nejlépe představit jako F# typy záznamů, které nemusí být deklarován před vytváření instancí.

Například tady jak můžete pracovat s funkcí, která vytváří záznam o anonymní:

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

Následující příklad rozšiřuje možnosti s předchozím histogramem `printCircleStats` funkci, která přebírá anonymní záznam jako vstup:

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

Volání `printCircleStats` s jakékoli anonymní typ záznamu, který nemá stejné "tvar" jako vstupní typ se nepodaří zkompilovat:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Záznamy anonymní struktury

Anonymní záznamy lze také definovat jako struktury s nepovinným `struct` – klíčové slovo. Následující příklad rozšiřuje předchozí vytváření a využívání záznam anonymní struktury:

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

### <a name="structness-inference"></a>Odvození Structness

Záznamy anonymní struktury také umožňují "structness odvození" kde není potřeba zadat `struct` – klíčové slovo v lokalitě volání. V tomto příkladu elide `struct` – klíčové slovo při volání metody `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Naopak vzorku – určení `struct` Pokud vstupní typ není záznam anonymní struktury – se nepodaří zkompilovat.

## <a name="embedding-anonymous-records-within-other-types"></a>Vkládání anonymní záznamy v ostatních typů

Je vhodné deklarovat [rozlišovaná sjednocení](discriminated-unions.md) jehož případy se záznamy. Ale pokud jsou data v záznamech stejného typu jako diskriminovaného sjednocení, je nutné definovat všechny typy jako vzájemně rekurzivní. Toto omezení se vyhnete pomocí anonymní záznamů. Následuje příklad typu a funkce tento vzor odpovídá přes něj:

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

Anonymní záznamy podpora konstrukce s [kopírování a aktualizace výrazů](copy-and-update-record-expressions.md). Tady je například jak můžete vytvořit novou instanci třídy anonymní záznam, který zkopíruje existující jeden z dat:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Na rozdíl od pojmenované záznamy anonymní záznamy vám ale umožní sestavit zcela různé tvary s kopírování a aktualizace výrazů. Následující příklad používá stejný anonymní záznam z předchozího příkladu a rozšíří na nový anonymní záznam:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Je také možné vytvořit anonymní záznamy z instance s názvem záznamů:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Data můžete také kopírovat do a z odkazu a struktura anonymní záznamy:

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

## <a name="properties-of-anonymous-records"></a>Vlastnosti záznamů anonymní

Anonymní záznamy mají několik specifických vlastností, které jsou zásadní pro plně pochopení, jak můžete použít.

### <a name="anonymous-records-are-nominal"></a>Anonymní záznamy jsou nominální

Anonymní záznamy jsou [nominální typy](https://en.wikipedia.org/wiki/Nominal_type_system). Jsou nejvhodnější přiměje jako pojmenované [záznam](records.md) typy (které jsou také nominální), které nevyžadují počáteční deklaraci.

Podívejte se na následující příklad se dvě deklarace anonymního záznam:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` a `y` hodnot mají různé typy a nejsou kompatibilní se sebou. Nejsou equatable a nejsou srovnatelné. Pro znázornění, vezměte v úvahu pojmenované záznam ekvivalentní:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Není nic jiného ze své podstaty anonymní záznamy ve srovnání s jejich ekvivalenty pojmenované záznam, pokud jde o typ referenčních materiálech o ekvivalenci nebo jejich porovnávání.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonymní záznamů, použijte porovnání a strukturální rovnost

Stejně jako typy záznamů anonymní záznamy jsou strukturálně equatable a srovnatelné. Toto je pouze hodnotu true, pokud všechny základní typy podporu rovnosti a porovnání, stejně jako s typy záznamů. Pro podporu rovnosti nebo jejich porovnávání, musí mít dva záznamy anonymní stejné "tvar".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonymní záznamy jsou serializovatelné

Anonymní záznamů může serializovat, stejně jako v pojmenované záznamy. Tady je příklad použití [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonymní záznamy jsou užitečné pro odesílání zjednodušené dat přes síť, aniž by bylo nutné definovat domény pro serializují a deserializují typů ještě před zahájením.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonymní záznamy vzájemnou spolupráci se službami C# anonymní typy

Je možné použít rozhraní API .NET, která vyžaduje použití [ C# anonymní typy](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#anonymní typy jsou jednoduché vzájemnou spolupráci se službami pomocí anonymní záznamy. Následující příklad ukazuje, jak použít anonymní záznamy pro volání [LINQ](../../csharp/programming-guide/concepts/linq/index.md) přetížení, které vyžaduje anonymního typu:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Existují různé další rozhraní API používaný v celém rozhraní .NET, která vyžadují použití předávání anonymního typu. Anonymní záznamy jsou vašeho nástroje pro práci s nimi.

## <a name="limitations"></a>Omezení

Anonymní záznamy mají určitá omezení jejich využití. Některé vyplývají jejich návrhu, ale ostatní jsou vydávání kompaktních změnit.

### <a name="limitations-with-pattern-matching"></a>Omezení s porovnáváním vzorů

Anonymní záznamy nepodporují porovnávání vzorů, na rozdíl od pojmenované záznamy. Existují tři hlavní důvody:

1. Vzor musí účet pro každé pole anonymní záznamu, na rozdíl od typů s názvem záznamu. Je to proto anonymní záznamy nepodporuje strukturální vytvoření podtypů – jsou nominální typy.
2. Z důvodu (1) neexistuje žádná možnost Další vzory ve výrazu match vzor jako každý jedinečných vzor by vyžadovalo jiný anonymní typ záznamu.
3. Z důvodu (3) může být libovolný vzor anonymní záznam podrobnější než při zápisu "tečka".

Dojde open jazyk návrh na [Povolit porovnávání vzorů v omezené kontexty](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Omezení proměnlivost

Není aktuálně možné definovat anonymní záznam s `mutable` data. Je [otevřete návrh jazyka](https://github.com/fsharp/fslang-suggestions/issues/732) umožňující proměnlivé datové.

### <a name="limitations-with-struct-anonymous-records"></a>Omezení se záznamy anonymní struktury

Není možné deklarovat strukturu anonymní záznamy jako `IsByRefLike` nebo `IsReadOnly`. Je [otevřete návrh jazyka](https://github.com/fsharp/fslang-suggestions/issues/712) k pro `IsByRefLike` a `IsReadOnly` anonymní záznamy.
