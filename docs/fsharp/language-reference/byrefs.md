---
title: Parametry ByRef
description: Další informace o typu byref a typů předávané v F#, které se používají pro programování nízké úrovně.
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055362"
---
# <a name="byrefs"></a><span data-ttu-id="b8c56-103">Parametry ByRef</span><span class="sxs-lookup"><span data-stu-id="b8c56-103">Byrefs</span></span>

<span data-ttu-id="b8c56-104">F#má dva hlavním oblastem funkcí, které pracují v prostoru nízké úrovně programování:</span><span class="sxs-lookup"><span data-stu-id="b8c56-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="b8c56-105">`byref` / `inref` / `outref` Typy, které jsou spravované ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b8c56-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="b8c56-106">Mají omezení týkající se použití tak, aby program, který není platný v době běhu nelze zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="b8c56-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="b8c56-107">A `byref`– například struktura, která je [struktura](structures.md) , který má podobnou sémantikou a omezení kompilace jako `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="b8c56-108">Jedním z příkladů je <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="b8c56-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8c56-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8c56-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="b8c56-110">ByRef, inref a outref</span><span class="sxs-lookup"><span data-stu-id="b8c56-110">Byref, inref, and outref</span></span>

<span data-ttu-id="b8c56-111">Existují tři formy `byref`:</span><span class="sxs-lookup"><span data-stu-id="b8c56-111">There are three forms of `byref`:</span></span>

* `inref<'T>`<span data-ttu-id="b8c56-112">, spravovaného ukazatele pro čtení zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8c56-112">, a managed pointer for reading the underlying value.</span></span>
* `outref<'T>`<span data-ttu-id="b8c56-113">, spravovaného ukazatele k zápisu do základní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8c56-113">, a managed pointer for writing to the underlying value.</span></span>
* `byref<'T>`<span data-ttu-id="b8c56-114">, spravovaného ukazatele pro čtení a zápis zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8c56-114">, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="b8c56-115">A `byref<'T>` mohou být předány kde `inref<'T>` očekává.</span><span class="sxs-lookup"><span data-stu-id="b8c56-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="b8c56-116">Podobně `byref<'T>` mohou být předány kde `outref<'T>` očekává.</span><span class="sxs-lookup"><span data-stu-id="b8c56-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="b8c56-117">Pomocí ByRef</span><span class="sxs-lookup"><span data-stu-id="b8c56-117">Using byrefs</span></span>

<span data-ttu-id="b8c56-118">Použití `inref<'T>`, je potřeba získat hodnotu ukazatele s `&`:</span><span class="sxs-lookup"><span data-stu-id="b8c56-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="b8c56-119">Zapsat do ukazatele s použitím `outref<'T>` nebo `byref<'T>`, musíte také vzít ukazatel na hodnotu `mutable`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="b8c56-120">Pokud vytváříte pouze ukazatele namísto jeho čtení, zvažte použití `outref<'T>` místo `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="b8c56-121">Sémantika Inref</span><span class="sxs-lookup"><span data-stu-id="b8c56-121">Inref semantics</span></span>

<span data-ttu-id="b8c56-122">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="b8c56-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="b8c56-123">Sémanticky to znamená, následující:</span><span class="sxs-lookup"><span data-stu-id="b8c56-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="b8c56-124">Držitel `x` ukazatele mohou používat pouze se načíst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8c56-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="b8c56-125">Získat jakýkoli ukazatel na `struct` pole vnořené `SomeStruct` se daný typ `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="b8c56-126">Toto je také true:</span><span class="sxs-lookup"><span data-stu-id="b8c56-126">The following is also true:</span></span>

* <span data-ttu-id="b8c56-127">Neexistuje žádné nepřímo další vlákna nebo aliasy nemáte oprávnění k zápisu do `x`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="b8c56-128">Neexistuje žádné nepřímo, který `SomeStruct` je neměnný základě `x` právě `inref`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="b8c56-129">Ale pro F# hodnotové typy, které **jsou** neměnné, `this` odvozena jako ukazatel `inref`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="b8c56-130">Všechna tato pravidla společně znamenají, že držitele `inref` ukazatel nesmíte upravovat okamžité obsah paměti, který ukazatel ukazuje.</span><span class="sxs-lookup"><span data-stu-id="b8c56-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="b8c56-131">Sémantika Outref</span><span class="sxs-lookup"><span data-stu-id="b8c56-131">Outref semantics</span></span>

<span data-ttu-id="b8c56-132">Účelem `outref<'T>` se k označení, že ukazatele by měli číst jenom z.</span><span class="sxs-lookup"><span data-stu-id="b8c56-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="b8c56-133">Nečekaně `outref<'T>` povolí čtení základní hodnotu bez ohledu na jeho název.</span><span class="sxs-lookup"><span data-stu-id="b8c56-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="b8c56-134">Toto je pro účely kompatibility.</span><span class="sxs-lookup"><span data-stu-id="b8c56-134">This is for compatibility purposes.</span></span> <span data-ttu-id="b8c56-135">Sémanticky `outref<'T>` se nijak neliší od `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="b8c56-136">Interoperabilita s C\#</span><span class="sxs-lookup"><span data-stu-id="b8c56-136">Interop with C\#</span></span>

<span data-ttu-id="b8c56-137">C# podporuje `in ref` a `out ref` klíčová slova, kromě `ref` vrátí.</span><span class="sxs-lookup"><span data-stu-id="b8c56-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="b8c56-138">Následující tabulka ukazuje, jak F# interpretuje co C# vysílá:</span><span class="sxs-lookup"><span data-stu-id="b8c56-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="b8c56-139">Konstrukce jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8c56-139">C# construct</span></span>|<span data-ttu-id="b8c56-140">F#odvodí z něj</span><span class="sxs-lookup"><span data-stu-id="b8c56-140">F# infers</span></span>|
|------------|---------|
|`ref` <span data-ttu-id="b8c56-141">návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8c56-141">return value</span></span>|`outref<'T>`|
|`ref readonly` <span data-ttu-id="b8c56-142">návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8c56-142">return value</span></span>|`inref<'T>`|
|`in ref` <span data-ttu-id="b8c56-143">parametr</span><span class="sxs-lookup"><span data-stu-id="b8c56-143">parameter</span></span>|`inref<'T>`|
|`out ref` <span data-ttu-id="b8c56-144">parametr</span><span class="sxs-lookup"><span data-stu-id="b8c56-144">parameter</span></span>|`outref<'T>`|

<span data-ttu-id="b8c56-145">V následující tabulce jsou uvedeny co F# vysílá:</span><span class="sxs-lookup"><span data-stu-id="b8c56-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="b8c56-146">F#konstrukce</span><span class="sxs-lookup"><span data-stu-id="b8c56-146">F# construct</span></span>|<span data-ttu-id="b8c56-147">Emitovaný konstrukce</span><span class="sxs-lookup"><span data-stu-id="b8c56-147">Emitted construct</span></span>|
|------------|-----------------|
|`inref<'T>` <span data-ttu-id="b8c56-148">Argument</span><span class="sxs-lookup"><span data-stu-id="b8c56-148">argument</span></span>|`[In]` <span data-ttu-id="b8c56-149">atribut na argumentu</span><span class="sxs-lookup"><span data-stu-id="b8c56-149">attribute on argument</span></span>|
|`inref<'T>` <span data-ttu-id="b8c56-150">return</span><span class="sxs-lookup"><span data-stu-id="b8c56-150">return</span></span>|`modreq` <span data-ttu-id="b8c56-151">atribut na hodnotu</span><span class="sxs-lookup"><span data-stu-id="b8c56-151">attribute on value</span></span>|
|`inref<'T>` <span data-ttu-id="b8c56-152">abstraktní datovou oblast nebo provádění</span><span class="sxs-lookup"><span data-stu-id="b8c56-152">in abstract slot or implementation</span></span>|`modreq` <span data-ttu-id="b8c56-153">v argumentu nebo return</span><span class="sxs-lookup"><span data-stu-id="b8c56-153">on argument or return</span></span>|
|`outref<'T>` <span data-ttu-id="b8c56-154">Argument</span><span class="sxs-lookup"><span data-stu-id="b8c56-154">argument</span></span>|`[Out]` <span data-ttu-id="b8c56-155">atribut na argumentu</span><span class="sxs-lookup"><span data-stu-id="b8c56-155">attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="b8c56-156">Odvození typu proměnné a přetížení pravidla</span><span class="sxs-lookup"><span data-stu-id="b8c56-156">Type inference and overloading rules</span></span>

<span data-ttu-id="b8c56-157">`inref<'T>` Typu odvozuje F# kompilátoru v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="b8c56-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="b8c56-158">Parametr nebo návratový typ .NET, který má `IsReadOnly` atribut.</span><span class="sxs-lookup"><span data-stu-id="b8c56-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="b8c56-159">`this` Ukazatel na strukturu typu, který nemá žádné proměnlivé pole.</span><span class="sxs-lookup"><span data-stu-id="b8c56-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="b8c56-160">Adresa umístění v paměti odvozené z jiného `inref<_>` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b8c56-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="b8c56-161">Když implicitní adresu `inref` jsou přijata, přetížení s parametrem typu `SomeType` je upřednostňována před přetížení s parametrem typu `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="b8c56-162">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b8c56-162">For example:</span></span>

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

<span data-ttu-id="b8c56-163">V obou případech se přetížení, přičemž `System.DateTime` jsou vyřešeny místo přetížení, přičemž `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="b8c56-164">Struktury předávání odkazem.</span><span class="sxs-lookup"><span data-stu-id="b8c56-164">Byref-like structs</span></span>

<span data-ttu-id="b8c56-165">Kromě `byref` / `inref` / `outref` trojice, můžete definovat vlastní struktury, která může splňovat `byref`-sémantiky, jako je.</span><span class="sxs-lookup"><span data-stu-id="b8c56-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="b8c56-166">Používá se k tomu <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atribut:</span><span class="sxs-lookup"><span data-stu-id="b8c56-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` <span data-ttu-id="b8c56-167">neznamená `Struct`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-167">does not imply `Struct`.</span></span> <span data-ttu-id="b8c56-168">Oba musí být k dispozici u typu.</span><span class="sxs-lookup"><span data-stu-id="b8c56-168">Both must be present on the type.</span></span>

<span data-ttu-id="b8c56-169">A "`byref`– stejně jako" struktura v F# je typ hodnoty vázané na zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b8c56-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="b8c56-170">Přiděluje se nikdy na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="b8c56-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="b8c56-171">A `byref`– jako – struktura je užitečné pro vysoce výkonné programování, jak se vynucuje sadu silné kontroly o životnost a zachycení snímků.</span><span class="sxs-lookup"><span data-stu-id="b8c56-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="b8c56-172">Pravidla jsou:</span><span class="sxs-lookup"><span data-stu-id="b8c56-172">The rules are:</span></span>

* <span data-ttu-id="b8c56-173">Se může sloužit jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="b8c56-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="b8c56-174">Nemohou být statické nebo členy třídy či struktury normální instance.</span><span class="sxs-lookup"><span data-stu-id="b8c56-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="b8c56-175">Nemůže být zachyceno libovolné konstrukce uzavření (`async` metodách a výrazech lambda).</span><span class="sxs-lookup"><span data-stu-id="b8c56-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="b8c56-176">Nelze je použít jako na generický parametr.</span><span class="sxs-lookup"><span data-stu-id="b8c56-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="b8c56-177">Tento poslední bod je zásadní pro F# programování ve stylu kanálu jako `|>` je obecný, který parametrizuje vstupní typy. funkce.</span><span class="sxs-lookup"><span data-stu-id="b8c56-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="b8c56-178">Toto omezení mohou být zmírněny pro `|>` v budoucnu, jako je vložená a nepoužívá všechna volání do jiných vložených obecné funkce v těle.</span><span class="sxs-lookup"><span data-stu-id="b8c56-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="b8c56-179">I když tato pravidla omezují velmi silného využití, dělají to ke splnění uskutečnění vysokovýkonného výpočetního prostředí bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b8c56-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="b8c56-180">Hodnoty typu ByRef</span><span class="sxs-lookup"><span data-stu-id="b8c56-180">Byref returns</span></span>

<span data-ttu-id="b8c56-181">ByRef vrátí z F# funkce nebo členy můžete vytvořen a využívat.</span><span class="sxs-lookup"><span data-stu-id="b8c56-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="b8c56-182">Při využívání `byref`– vrátí metoda hodnotu přistoupí implicitně přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b8c56-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="b8c56-183">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b8c56-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="b8c56-184">Chcete-li zabránit implicitní zrušení odkazu, například předání odkazem do více zřetězených volání, použijte `&x` (kde `x` je hodnota).</span><span class="sxs-lookup"><span data-stu-id="b8c56-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="b8c56-185">Můžete také přímo přiřadit k vrácení `byref`.</span><span class="sxs-lookup"><span data-stu-id="b8c56-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="b8c56-186">Vezměte v úvahu následující program (vysoce imperativní):</span><span class="sxs-lookup"><span data-stu-id="b8c56-186">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="b8c56-187">Toto je výstup:</span><span class="sxs-lookup"><span data-stu-id="b8c56-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="b8c56-188">Vytváření oborů pro parametry ByRef</span><span class="sxs-lookup"><span data-stu-id="b8c56-188">Scoping for byrefs</span></span>

<span data-ttu-id="b8c56-189">A `let`-vázaná hodnota nemůže mít svůj odkaz překročí obor, ve kterém byl definován.</span><span class="sxs-lookup"><span data-stu-id="b8c56-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="b8c56-190">Například následující není povolena:</span><span class="sxs-lookup"><span data-stu-id="b8c56-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="b8c56-191">Předchází se tak získání odlišné výsledky v závislosti na tom, pokud kompilujete s optimalizací zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="b8c56-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
