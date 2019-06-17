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
# <a name="anonymous-records"></a><span data-ttu-id="a5198-103">Anonymní záznamů</span><span class="sxs-lookup"><span data-stu-id="a5198-103">Anonymous Records</span></span>

<span data-ttu-id="a5198-104">Anonymní záznamy jsou jednoduché agregace pojmenovaných hodnot, které nemusí být deklarované před použitím.</span><span class="sxs-lookup"><span data-stu-id="a5198-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="a5198-105">Můžete je deklarovat jako typy struktur nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="a5198-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="a5198-106">Jsou to typy odkazů ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a5198-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="a5198-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5198-107">Syntax</span></span>

<span data-ttu-id="a5198-108">Následující příklady ukazují syntaxi anonymní záznamu.</span><span class="sxs-lookup"><span data-stu-id="a5198-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="a5198-109">Oddělené položky jako `[item]` jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a5198-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="a5198-110">Základní informace o využití</span><span class="sxs-lookup"><span data-stu-id="a5198-110">Basic usage</span></span>

<span data-ttu-id="a5198-111">Anonymní záznamy jsou nejlépe představit jako F# typy záznamů, které nemusí být deklarován před vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="a5198-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="a5198-112">Například tady jak můžete pracovat s funkcí, která vytváří záznam o anonymní:</span><span class="sxs-lookup"><span data-stu-id="a5198-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="a5198-113">Následující příklad rozšiřuje možnosti s předchozím histogramem `printCircleStats` funkci, která přebírá anonymní záznam jako vstup:</span><span class="sxs-lookup"><span data-stu-id="a5198-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="a5198-114">Volání `printCircleStats` s jakékoli anonymní typ záznamu, který nemá stejné "tvar" jako vstupní typ se nepodaří zkompilovat:</span><span class="sxs-lookup"><span data-stu-id="a5198-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="a5198-115">Záznamy anonymní struktury</span><span class="sxs-lookup"><span data-stu-id="a5198-115">Struct anonymous records</span></span>

<span data-ttu-id="a5198-116">Anonymní záznamy lze také definovat jako struktury s nepovinným `struct` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a5198-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="a5198-117">Následující příklad rozšiřuje předchozí vytváření a využívání záznam anonymní struktury:</span><span class="sxs-lookup"><span data-stu-id="a5198-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="a5198-118">Odvození Structness</span><span class="sxs-lookup"><span data-stu-id="a5198-118">Structness inference</span></span>

<span data-ttu-id="a5198-119">Záznamy anonymní struktury také umožňují "structness odvození" kde není potřeba zadat `struct` – klíčové slovo v lokalitě volání.</span><span class="sxs-lookup"><span data-stu-id="a5198-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="a5198-120">V tomto příkladu elide `struct` – klíčové slovo při volání metody `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="a5198-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="a5198-121">Naopak vzorku – určení `struct` Pokud vstupní typ není záznam anonymní struktury – se nepodaří zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="a5198-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="a5198-122">Vkládání anonymní záznamy v ostatních typů</span><span class="sxs-lookup"><span data-stu-id="a5198-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="a5198-123">Je vhodné deklarovat [rozlišovaná sjednocení](discriminated-unions.md) jehož případy se záznamy.</span><span class="sxs-lookup"><span data-stu-id="a5198-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="a5198-124">Ale pokud jsou data v záznamech stejného typu jako diskriminovaného sjednocení, je nutné definovat všechny typy jako vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="a5198-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="a5198-125">Toto omezení se vyhnete pomocí anonymní záznamů.</span><span class="sxs-lookup"><span data-stu-id="a5198-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="a5198-126">Následuje příklad typu a funkce tento vzor odpovídá přes něj:</span><span class="sxs-lookup"><span data-stu-id="a5198-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="a5198-127">Kopírování a aktualizace výrazů</span><span class="sxs-lookup"><span data-stu-id="a5198-127">Copy and update expressions</span></span>

<span data-ttu-id="a5198-128">Anonymní záznamy podpora konstrukce s [kopírování a aktualizace výrazů](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a5198-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="a5198-129">Tady je například jak můžete vytvořit novou instanci třídy anonymní záznam, který zkopíruje existující jeden z dat:</span><span class="sxs-lookup"><span data-stu-id="a5198-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="a5198-130">Na rozdíl od pojmenované záznamy anonymní záznamy vám ale umožní sestavit zcela různé tvary s kopírování a aktualizace výrazů.</span><span class="sxs-lookup"><span data-stu-id="a5198-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="a5198-131">Následující příklad používá stejný anonymní záznam z předchozího příkladu a rozšíří na nový anonymní záznam:</span><span class="sxs-lookup"><span data-stu-id="a5198-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="a5198-132">Je také možné vytvořit anonymní záznamy z instance s názvem záznamů:</span><span class="sxs-lookup"><span data-stu-id="a5198-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="a5198-133">Data můžete také kopírovat do a z odkazu a struktura anonymní záznamy:</span><span class="sxs-lookup"><span data-stu-id="a5198-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="a5198-134">Vlastnosti záznamů anonymní</span><span class="sxs-lookup"><span data-stu-id="a5198-134">Properties of anonymous records</span></span>

<span data-ttu-id="a5198-135">Anonymní záznamy mají několik specifických vlastností, které jsou zásadní pro plně pochopení, jak můžete použít.</span><span class="sxs-lookup"><span data-stu-id="a5198-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="a5198-136">Anonymní záznamy jsou nominální</span><span class="sxs-lookup"><span data-stu-id="a5198-136">Anonymous records are nominal</span></span>

<span data-ttu-id="a5198-137">Anonymní záznamy jsou [nominální typy](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="a5198-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="a5198-138">Jsou nejvhodnější přiměje jako pojmenované [záznam](records.md) typy (které jsou také nominální), které nevyžadují počáteční deklaraci.</span><span class="sxs-lookup"><span data-stu-id="a5198-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="a5198-139">Podívejte se na následující příklad se dvě deklarace anonymního záznam:</span><span class="sxs-lookup"><span data-stu-id="a5198-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="a5198-140">`x` a `y` hodnot mají různé typy a nejsou kompatibilní se sebou.</span><span class="sxs-lookup"><span data-stu-id="a5198-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="a5198-141">Nejsou equatable a nejsou srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="a5198-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="a5198-142">Pro znázornění, vezměte v úvahu pojmenované záznam ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="a5198-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="a5198-143">Není nic jiného ze své podstaty anonymní záznamy ve srovnání s jejich ekvivalenty pojmenované záznam, pokud jde o typ referenčních materiálech o ekvivalenci nebo jejich porovnávání.</span><span class="sxs-lookup"><span data-stu-id="a5198-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="a5198-144">Anonymní záznamů, použijte porovnání a strukturální rovnost</span><span class="sxs-lookup"><span data-stu-id="a5198-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="a5198-145">Stejně jako typy záznamů anonymní záznamy jsou strukturálně equatable a srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="a5198-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="a5198-146">Toto je pouze hodnotu true, pokud všechny základní typy podporu rovnosti a porovnání, stejně jako s typy záznamů.</span><span class="sxs-lookup"><span data-stu-id="a5198-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="a5198-147">Pro podporu rovnosti nebo jejich porovnávání, musí mít dva záznamy anonymní stejné "tvar".</span><span class="sxs-lookup"><span data-stu-id="a5198-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="a5198-148">Anonymní záznamy jsou serializovatelné</span><span class="sxs-lookup"><span data-stu-id="a5198-148">Anonymous records are serializable</span></span>

<span data-ttu-id="a5198-149">Anonymní záznamů může serializovat, stejně jako v pojmenované záznamy.</span><span class="sxs-lookup"><span data-stu-id="a5198-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="a5198-150">Tady je příklad použití [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="a5198-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="a5198-151">Anonymní záznamy jsou užitečné pro odesílání zjednodušené dat přes síť, aniž by bylo nutné definovat domény pro serializují a deserializují typů ještě před zahájením.</span><span class="sxs-lookup"><span data-stu-id="a5198-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="a5198-152">Anonymní záznamy vzájemnou spolupráci se službami C# anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a5198-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="a5198-153">Je možné použít rozhraní API .NET, která vyžaduje použití [ C# anonymní typy](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5198-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="a5198-154">C#anonymní typy jsou jednoduché vzájemnou spolupráci se službami pomocí anonymní záznamy.</span><span class="sxs-lookup"><span data-stu-id="a5198-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="a5198-155">Následující příklad ukazuje, jak použít anonymní záznamy pro volání [LINQ](../../csharp/programming-guide/concepts/linq/index.md) přetížení, které vyžaduje anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="a5198-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="a5198-156">Existují různé další rozhraní API používaný v celém rozhraní .NET, která vyžadují použití předávání anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="a5198-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="a5198-157">Anonymní záznamy jsou vašeho nástroje pro práci s nimi.</span><span class="sxs-lookup"><span data-stu-id="a5198-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="a5198-158">Omezení</span><span class="sxs-lookup"><span data-stu-id="a5198-158">Limitations</span></span>

<span data-ttu-id="a5198-159">Anonymní záznamy mají určitá omezení jejich využití.</span><span class="sxs-lookup"><span data-stu-id="a5198-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="a5198-160">Některé vyplývají jejich návrhu, ale ostatní jsou vydávání kompaktních změnit.</span><span class="sxs-lookup"><span data-stu-id="a5198-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="a5198-161">Omezení s porovnáváním vzorů</span><span class="sxs-lookup"><span data-stu-id="a5198-161">Limitations with pattern matching</span></span>

<span data-ttu-id="a5198-162">Anonymní záznamy nepodporují porovnávání vzorů, na rozdíl od pojmenované záznamy.</span><span class="sxs-lookup"><span data-stu-id="a5198-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="a5198-163">Existují tři hlavní důvody:</span><span class="sxs-lookup"><span data-stu-id="a5198-163">There are three reasons:</span></span>

1. <span data-ttu-id="a5198-164">Vzor musí účet pro každé pole anonymní záznamu, na rozdíl od typů s názvem záznamu.</span><span class="sxs-lookup"><span data-stu-id="a5198-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="a5198-165">Je to proto anonymní záznamy nepodporuje strukturální vytvoření podtypů – jsou nominální typy.</span><span class="sxs-lookup"><span data-stu-id="a5198-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="a5198-166">Z důvodu (1) neexistuje žádná možnost Další vzory ve výrazu match vzor jako každý jedinečných vzor by vyžadovalo jiný anonymní typ záznamu.</span><span class="sxs-lookup"><span data-stu-id="a5198-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="a5198-167">Z důvodu (3) může být libovolný vzor anonymní záznam podrobnější než při zápisu "tečka".</span><span class="sxs-lookup"><span data-stu-id="a5198-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="a5198-168">Dojde open jazyk návrh na [Povolit porovnávání vzorů v omezené kontexty](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="a5198-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="a5198-169">Omezení proměnlivost</span><span class="sxs-lookup"><span data-stu-id="a5198-169">Limitations with mutability</span></span>

<span data-ttu-id="a5198-170">Není aktuálně možné definovat anonymní záznam s `mutable` data.</span><span class="sxs-lookup"><span data-stu-id="a5198-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="a5198-171">Je [otevřete návrh jazyka](https://github.com/fsharp/fslang-suggestions/issues/732) umožňující proměnlivé datové.</span><span class="sxs-lookup"><span data-stu-id="a5198-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="a5198-172">Omezení se záznamy anonymní struktury</span><span class="sxs-lookup"><span data-stu-id="a5198-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="a5198-173">Není možné deklarovat strukturu anonymní záznamy jako `IsByRefLike` nebo `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="a5198-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="a5198-174">Je [otevřete návrh jazyka](https://github.com/fsharp/fslang-suggestions/issues/712) k pro `IsByRefLike` a `IsReadOnly` anonymní záznamy.</span><span class="sxs-lookup"><span data-stu-id="a5198-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
