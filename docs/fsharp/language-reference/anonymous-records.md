---
title: Anonymní záznamy
description: Naučte se používat vytváření a používání anonymních záznamů, funkce jazyka, která pomáhá s manipulací s daty.
ms.date: 06/12/2019
ms.openlocfilehash: 061fd3279c84b9a3161c687d9392947ee7ce9c83
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453023"
---
# <a name="anonymous-records"></a><span data-ttu-id="5d352-103">Anonymní záznamy</span><span class="sxs-lookup"><span data-stu-id="5d352-103">Anonymous Records</span></span>

<span data-ttu-id="5d352-104">Anonymní záznamy jsou jednoduché agregované pojmenované hodnoty, které není nutné deklarovat před použitím.</span><span class="sxs-lookup"><span data-stu-id="5d352-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="5d352-105">Můžete je deklarovat buď jako struktury, nebo na typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="5d352-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="5d352-106">Ve výchozím nastavení se jedná o typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="5d352-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d352-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d352-107">Syntax</span></span>

<span data-ttu-id="5d352-108">Následující příklady ukazují syntaxi anonymního záznamu.</span><span class="sxs-lookup"><span data-stu-id="5d352-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="5d352-109">Položky s oddělovači `[item]` jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="5d352-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="5d352-110">Základní využití</span><span class="sxs-lookup"><span data-stu-id="5d352-110">Basic usage</span></span>

<span data-ttu-id="5d352-111">Anonymní záznamy se nejlépe považují za F# typy záznamů, které není nutné deklarovat před vytvořením instance.</span><span class="sxs-lookup"><span data-stu-id="5d352-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="5d352-112">Tady je příklad, jak můžete pracovat s funkcí, která vytváří anonymní záznam:</span><span class="sxs-lookup"><span data-stu-id="5d352-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="5d352-113">V následujícím příkladu se rozšíří na předchozí s funkcí `printCircleStats`, která přebírá anonymní záznam jako vstup:</span><span class="sxs-lookup"><span data-stu-id="5d352-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="5d352-114">Volání `printCircleStats` s jakýmkoli typem anonymního záznamu, který nemá stejný "tvar", protože vstupní typ se nepodaří zkompilovat:</span><span class="sxs-lookup"><span data-stu-id="5d352-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="5d352-115">Strukturování anonymních záznamů</span><span class="sxs-lookup"><span data-stu-id="5d352-115">Struct anonymous records</span></span>

<span data-ttu-id="5d352-116">Anonymní záznamy lze definovat také jako strukturu s nepovinným klíčovým slovem `struct`.</span><span class="sxs-lookup"><span data-stu-id="5d352-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="5d352-117">Následující příklad rozšiřuje předchozí vyprodukováním a spotřebou anonymního záznamu struktury:</span><span class="sxs-lookup"><span data-stu-id="5d352-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="5d352-118">Odvození struktury</span><span class="sxs-lookup"><span data-stu-id="5d352-118">Structness inference</span></span>

<span data-ttu-id="5d352-119">Strukturování anonymních záznamů také umožňuje "odvození struktury", kde není nutné zadávat klíčové slovo `struct` na webu volání.</span><span class="sxs-lookup"><span data-stu-id="5d352-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="5d352-120">V tomto příkladu jste při volání `printCircleStats`Elide klíčové slovo `struct`:</span><span class="sxs-lookup"><span data-stu-id="5d352-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="5d352-121">Zpětný vzor – určení `struct`, když není vstupní typ struktura anonymního záznamu – selže kompilace.</span><span class="sxs-lookup"><span data-stu-id="5d352-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="5d352-122">Vkládání anonymních záznamů v rámci jiných typů</span><span class="sxs-lookup"><span data-stu-id="5d352-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="5d352-123">Je užitečné deklarovat [rozlišené sjednocení](discriminated-unions.md) , jejichž případy jsou záznamy.</span><span class="sxs-lookup"><span data-stu-id="5d352-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="5d352-124">Pokud jsou však data v záznamech stejného typu jako rozlišené sjednocení, je nutné definovat všechny typy jako vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="5d352-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="5d352-125">Použití anonymních záznamů zabraňuje tomuto omezení.</span><span class="sxs-lookup"><span data-stu-id="5d352-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="5d352-126">Co následuje příklad typu a funkce, pro kterou odpovídá vzorek:</span><span class="sxs-lookup"><span data-stu-id="5d352-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="5d352-127">Výrazy kopírování a aktualizace</span><span class="sxs-lookup"><span data-stu-id="5d352-127">Copy and update expressions</span></span>

<span data-ttu-id="5d352-128">Anonymní záznamy podporují vytváření pomocí [výrazů kopírování a aktualizace](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5d352-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="5d352-129">Tady je příklad, jak můžete vytvořit novou instanci anonymního záznamu, který zkopíruje existující data:</span><span class="sxs-lookup"><span data-stu-id="5d352-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="5d352-130">Na rozdíl od pojmenovaných záznamů ale anonymní záznamy umožňují vytvořit zcela různé formuláře s výrazy kopírování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5d352-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="5d352-131">Následující příklad používá stejný anonymní záznam z předchozího příkladu a rozbalí ho do nového anonymního záznamu:</span><span class="sxs-lookup"><span data-stu-id="5d352-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="5d352-132">Je také možné vytvořit anonymní záznamy z instancí pojmenovaných záznamů:</span><span class="sxs-lookup"><span data-stu-id="5d352-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="5d352-133">Můžete také kopírovat data do a z odkazů a struktury anonymních záznamů:</span><span class="sxs-lookup"><span data-stu-id="5d352-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="5d352-134">Vlastnosti anonymních záznamů</span><span class="sxs-lookup"><span data-stu-id="5d352-134">Properties of anonymous records</span></span>

<span data-ttu-id="5d352-135">Anonymní záznamy mají řadu vlastností, které jsou nezbytné pro úplné porozumění způsobu jejich použití.</span><span class="sxs-lookup"><span data-stu-id="5d352-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="5d352-136">Anonymní záznamy jsou nominální</span><span class="sxs-lookup"><span data-stu-id="5d352-136">Anonymous records are nominal</span></span>

<span data-ttu-id="5d352-137">Anonymní záznamy jsou [nominální typy](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="5d352-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="5d352-138">Nejlépe se považují za pojmenované typy [záznamů](records.md) (které jsou také nominální), které nevyžadují deklaraci předem.</span><span class="sxs-lookup"><span data-stu-id="5d352-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="5d352-139">Vezměte v úvahu následující příklad se dvěma deklaracemi anonymního záznamu:</span><span class="sxs-lookup"><span data-stu-id="5d352-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="5d352-140">Hodnoty `x` a `y` mají různé typy a nejsou kompatibilní mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="5d352-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="5d352-141">Nejsou shodné a nejsou srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="5d352-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="5d352-142">K ilustraci použijte podobný záznam s názvem:</span><span class="sxs-lookup"><span data-stu-id="5d352-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="5d352-143">U anonymních záznamů se v porovnání s jejich pojmenovaným záznamem neliší žádné podstatné informace, které se týkají rovnocennosti typu nebo porovnání.</span><span class="sxs-lookup"><span data-stu-id="5d352-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="5d352-144">Anonymní záznamy používají strukturální rovnost a porovnávání.</span><span class="sxs-lookup"><span data-stu-id="5d352-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="5d352-145">Podobně jako typy záznamů jsou anonymní záznamy strukturované a srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="5d352-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="5d352-146">To platí pouze v případě, že všechny typy prvků podporují rovnost a porovnávání, jako u typů záznamů.</span><span class="sxs-lookup"><span data-stu-id="5d352-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="5d352-147">Pro podporu rovnosti nebo porovnání musí mít dva anonymní záznamy stejný "tvar".</span><span class="sxs-lookup"><span data-stu-id="5d352-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="5d352-148">Anonymní záznamy jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="5d352-148">Anonymous records are serializable</span></span>

<span data-ttu-id="5d352-149">Anonymní záznamy můžete serializovat stejně jako u pojmenovaných záznamů.</span><span class="sxs-lookup"><span data-stu-id="5d352-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="5d352-150">Tady je příklad použití [Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="5d352-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip') 

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="5d352-151">Anonymní záznamy jsou užitečné pro posílání odlehčených dat v síti, aniž by bylo potřeba definovat doménu pro serializované/deserializované typy vpřed.</span><span class="sxs-lookup"><span data-stu-id="5d352-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="5d352-152">Anonymní záznamy spolupracující s C# anonymními typy</span><span class="sxs-lookup"><span data-stu-id="5d352-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="5d352-153">Je možné použít rozhraní .NET API, které vyžaduje použití [ C# anonymních typů](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="5d352-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="5d352-154">C#anonymní typy jsou triviální pro spolupráci s použitím anonymních záznamů.</span><span class="sxs-lookup"><span data-stu-id="5d352-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="5d352-155">Následující příklad ukazuje způsob použití anonymních záznamů pro volání přetížení [LINQ](../../csharp/programming-guide/concepts/linq/index.md) , které vyžaduje anonymní typ:</span><span class="sxs-lookup"><span data-stu-id="5d352-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="5d352-156">V rozhraní .NET je velké množství dalších rozhraní API, které vyžaduje použití předávání anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="5d352-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="5d352-157">Anonymní záznamy jsou nástroje pro práci s nimi.</span><span class="sxs-lookup"><span data-stu-id="5d352-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="5d352-158">Omezení</span><span class="sxs-lookup"><span data-stu-id="5d352-158">Limitations</span></span>

<span data-ttu-id="5d352-159">Anonymní záznamy mají určitá omezení používání.</span><span class="sxs-lookup"><span data-stu-id="5d352-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="5d352-160">Některé jsou podstatou jejich návrhu, ale jiné jsou snadněji ke změně.</span><span class="sxs-lookup"><span data-stu-id="5d352-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="5d352-161">Omezení s porovnáváním vzorů</span><span class="sxs-lookup"><span data-stu-id="5d352-161">Limitations with pattern matching</span></span>

<span data-ttu-id="5d352-162">Anonymní záznamy nepodporují porovnávání vzorů, na rozdíl od pojmenovaných záznamů.</span><span class="sxs-lookup"><span data-stu-id="5d352-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="5d352-163">Existují tři důvody:</span><span class="sxs-lookup"><span data-stu-id="5d352-163">There are three reasons:</span></span>

1. <span data-ttu-id="5d352-164">Vzor by musel být pro každé pole anonymního záznamu vyúčtován na rozdíl od pojmenovaných typů záznamů.</span><span class="sxs-lookup"><span data-stu-id="5d352-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="5d352-165">Je tomu tak proto, že anonymní záznamy nepodporují strukturální podtypování – jedná se o nominální typy.</span><span class="sxs-lookup"><span data-stu-id="5d352-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="5d352-166">Vzhledem k tomu, že je (1), není možné mít ve výrazu porovnávání vzorů další vzory, protože každý odlišný vzor by znamenal jiný typ anonymního záznamu.</span><span class="sxs-lookup"><span data-stu-id="5d352-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="5d352-167">Z důvodu (3) by byl jakýkoli vzor anonymního záznamu podrobnější než použití notace "tečka".</span><span class="sxs-lookup"><span data-stu-id="5d352-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="5d352-168">Existuje návrh otevřeného jazyka, který umožňuje [porovnávání vzorů v omezeném kontextu](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="5d352-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="5d352-169">Omezení pomocí proměnlivost</span><span class="sxs-lookup"><span data-stu-id="5d352-169">Limitations with mutability</span></span>

<span data-ttu-id="5d352-170">V současné době není možné definovat anonymní záznam s `mutable`mi daty.</span><span class="sxs-lookup"><span data-stu-id="5d352-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="5d352-171">K dispozici je [Návrh otevřeného jazyka](https://github.com/fsharp/fslang-suggestions/issues/732) , který povoluje proměnlivá data.</span><span class="sxs-lookup"><span data-stu-id="5d352-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="5d352-172">Omezení pomocí anonymních záznamů struktury</span><span class="sxs-lookup"><span data-stu-id="5d352-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="5d352-173">Není možné deklarovat anonymní záznamy struktury jako `IsByRefLike` nebo `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="5d352-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="5d352-174">K dispozici je [Návrh otevřeného jazyka](https://github.com/fsharp/fslang-suggestions/issues/712) pro `IsByRefLike` a `IsReadOnly` anonymní záznamy.</span><span class="sxs-lookup"><span data-stu-id="5d352-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
