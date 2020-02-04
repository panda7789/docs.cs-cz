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
# <a name="byrefs"></a><span data-ttu-id="f2c52-103">Parametry ByRef</span><span class="sxs-lookup"><span data-stu-id="f2c52-103">Byrefs</span></span>

<span data-ttu-id="f2c52-104">F#má dvě hlavní oblasti funkcí, které se týkají prostoru programování nízké úrovně:</span><span class="sxs-lookup"><span data-stu-id="f2c52-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="f2c52-105">`byref`/`inref`/typy `outref`, což jsou spravované ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f2c52-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="f2c52-106">Mají omezení používání, takže nemůžete kompilovat program, který je neplatný v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f2c52-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="f2c52-107">Struktura podobná `byref`, což je [Struktura](structures.md) , která má podobnou sémantiku a stejná omezení při kompilaci jako `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="f2c52-108">Jedním z příkladů je <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="f2c52-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c52-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2c52-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="f2c52-110">ByRef, inref a outref</span><span class="sxs-lookup"><span data-stu-id="f2c52-110">Byref, inref, and outref</span></span>

<span data-ttu-id="f2c52-111">Existují tři formy `byref`:</span><span class="sxs-lookup"><span data-stu-id="f2c52-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="f2c52-112">`inref<'T>`spravovaný ukazatel pro čtení podkladové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2c52-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="f2c52-113">`outref<'T>`spravovaný ukazatel pro zápis na podkladovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2c52-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="f2c52-114">`byref<'T>`spravovaný ukazatel pro čtení a zápis základní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2c52-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="f2c52-115">`byref<'T>` lze předat, pokud je očekávána `inref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="f2c52-116">Podobně je možné předat `byref<'T>`, kde se očekává `outref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="f2c52-117">Použití ByRef</span><span class="sxs-lookup"><span data-stu-id="f2c52-117">Using byrefs</span></span>

<span data-ttu-id="f2c52-118">Chcete-li použít `inref<'T>`, je třeba získat hodnotu ukazatele s `&`:</span><span class="sxs-lookup"><span data-stu-id="f2c52-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="f2c52-119">Chcete-li zapisovat do ukazatele pomocí `outref<'T>` nebo `byref<'T>`, je nutné také nastavit hodnotu, kterou jste převedli ukazatel na `mutable`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="f2c52-120">Pokud pouze píšete ukazatel namísto čtení, zvažte použití `outref<'T>` místo `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="f2c52-121">Sémantika Inref</span><span class="sxs-lookup"><span data-stu-id="f2c52-121">Inref semantics</span></span>

<span data-ttu-id="f2c52-122">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="f2c52-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="f2c52-123">Sémantika znamená následující:</span><span class="sxs-lookup"><span data-stu-id="f2c52-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="f2c52-124">Držitel `x`ového ukazatele ho může použít jenom ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2c52-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="f2c52-125">Jakýkoli ukazatel získaný pro `struct` polí vnořených v rámci `SomeStruct` je uveden typ `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="f2c52-126">Platí to i pro následující skutečnosti:</span><span class="sxs-lookup"><span data-stu-id="f2c52-126">The following is also true:</span></span>

* <span data-ttu-id="f2c52-127">Neexistují žádné nenásobení, že k `x`nejsou k dispozici další vlákna nebo aliasy.</span><span class="sxs-lookup"><span data-stu-id="f2c52-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="f2c52-128">Neexistuje žádné nenásobení, které `SomeStruct` není proměnlivé na základě `x` je `inref`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="f2c52-129">U F# typů hodnot, které **jsou** neměnné, však je ukazatel `this` odvozen jako `inref`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="f2c52-130">Všechna tato pravidla dohromady znamenají, že držitel `inref`ového ukazatele nemůže upravit okamžitý obsah paměti, na kterou se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="f2c52-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="f2c52-131">Sémantika Outref</span><span class="sxs-lookup"><span data-stu-id="f2c52-131">Outref semantics</span></span>

<span data-ttu-id="f2c52-132">Účelem `outref<'T>` je označit, že ukazatel by měl zapisovat pouze do.</span><span class="sxs-lookup"><span data-stu-id="f2c52-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="f2c52-133">Neočekávaně `outref<'T>` povoluje čtení základní hodnoty navzdory jejímu názvu.</span><span class="sxs-lookup"><span data-stu-id="f2c52-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="f2c52-134">Jedná se o účely kompatibility.</span><span class="sxs-lookup"><span data-stu-id="f2c52-134">This is for compatibility purposes.</span></span> <span data-ttu-id="f2c52-135">Sémanticky, `outref<'T>` se neliší od `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="f2c52-136">Spolupráce s C\#</span><span class="sxs-lookup"><span data-stu-id="f2c52-136">Interop with C\#</span></span>

<span data-ttu-id="f2c52-137">C#Kromě `ref` vrací i klíčová slova `in ref` a `out ref`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="f2c52-138">Následující tabulka ukazuje, jak F# interpretuje, C# co emituje:</span><span class="sxs-lookup"><span data-stu-id="f2c52-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="f2c52-139">C#Contains</span><span class="sxs-lookup"><span data-stu-id="f2c52-139">C# construct</span></span>|<span data-ttu-id="f2c52-140">F#odvodí</span><span class="sxs-lookup"><span data-stu-id="f2c52-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="f2c52-141">`ref` návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2c52-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="f2c52-142">`ref readonly` návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2c52-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="f2c52-143">`in ref` parametr</span><span class="sxs-lookup"><span data-stu-id="f2c52-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="f2c52-144">`out ref` parametr</span><span class="sxs-lookup"><span data-stu-id="f2c52-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="f2c52-145">Následující tabulka ukazuje, co F# emituje:</span><span class="sxs-lookup"><span data-stu-id="f2c52-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="f2c52-146">F#Contains</span><span class="sxs-lookup"><span data-stu-id="f2c52-146">F# construct</span></span>|<span data-ttu-id="f2c52-147">Emited – konstrukce</span><span class="sxs-lookup"><span data-stu-id="f2c52-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="f2c52-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="f2c52-148">`inref<'T>` argument</span></span>|<span data-ttu-id="f2c52-149">atribut `[In]` v argumentu</span><span class="sxs-lookup"><span data-stu-id="f2c52-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="f2c52-150">`inref<'T>` návrat</span><span class="sxs-lookup"><span data-stu-id="f2c52-150">`inref<'T>` return</span></span>|<span data-ttu-id="f2c52-151">`modreq` atribut pro hodnotu</span><span class="sxs-lookup"><span data-stu-id="f2c52-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="f2c52-152">`inref<'T>` v abstraktní patici nebo implementaci</span><span class="sxs-lookup"><span data-stu-id="f2c52-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="f2c52-153">`modreq` argumentu nebo návratem</span><span class="sxs-lookup"><span data-stu-id="f2c52-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="f2c52-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="f2c52-154">`outref<'T>` argument</span></span>|<span data-ttu-id="f2c52-155">atribut `[Out]` v argumentu</span><span class="sxs-lookup"><span data-stu-id="f2c52-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="f2c52-156">Odvození typu a pravidla přetížení</span><span class="sxs-lookup"><span data-stu-id="f2c52-156">Type inference and overloading rules</span></span>

<span data-ttu-id="f2c52-157">Typ `inref<'T>` je odvozen F# kompilátorem v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="f2c52-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="f2c52-158">Parametr nebo návratový typ .NET, který má atribut `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="f2c52-159">Ukazatel `this` u typu struktury, který nemá žádná proměnlivá pole.</span><span class="sxs-lookup"><span data-stu-id="f2c52-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="f2c52-160">Adresa umístění v paměti odvozeného od jiného ukazatele `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="f2c52-161">Když je využívána implicitní adresa `inref`, přetížení s argumentem typu `SomeType` je upřednostňováno na přetížení s argumentem typu `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="f2c52-162">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f2c52-162">For example:</span></span>

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

<span data-ttu-id="f2c52-163">V obou případech jsou přetížení přebírající `System.DateTime` vyřešeny, nikoli přetížení, které přebírají `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="f2c52-164">Struktury podobné typu ByRef</span><span class="sxs-lookup"><span data-stu-id="f2c52-164">Byref-like structs</span></span>

<span data-ttu-id="f2c52-165">Kromě `byref`/`inref`/`outref` trojice můžete definovat vlastní struktury, které mohou splňovat `byref`jako sémantiku.</span><span class="sxs-lookup"><span data-stu-id="f2c52-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="f2c52-166">To se provádí s atributem <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:</span><span class="sxs-lookup"><span data-stu-id="f2c52-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="f2c52-167">`IsByRefLike` neznamená `Struct`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="f2c52-168">Oba typy musí být k dispozici na typu.</span><span class="sxs-lookup"><span data-stu-id="f2c52-168">Both must be present on the type.</span></span>

<span data-ttu-id="f2c52-169">Struktura "`byref`jako" v F# je typ hodnoty vázané na zásobník.</span><span class="sxs-lookup"><span data-stu-id="f2c52-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="f2c52-170">Nikdy se nepřiřazuje na spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="f2c52-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="f2c52-171">Struktura podobná `byref`je užitečná pro vysoce výkonné programování, protože se vynutila se sadou silných kontrol životního cyklu životnosti a bez zachycení.</span><span class="sxs-lookup"><span data-stu-id="f2c52-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="f2c52-172">Pravidla jsou:</span><span class="sxs-lookup"><span data-stu-id="f2c52-172">The rules are:</span></span>

* <span data-ttu-id="f2c52-173">Mohou být použity jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="f2c52-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="f2c52-174">Nemohou být statické nebo členy instance třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="f2c52-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="f2c52-175">Nemohou být zachyceny žádnou uzavírací konstrukcí (`async` metody nebo lambda výrazy).</span><span class="sxs-lookup"><span data-stu-id="f2c52-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="f2c52-176">Nelze je použít jako obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="f2c52-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="f2c52-177">Tento poslední bod je rozhodující pro F# programování ve stylu kanálu, protože `|>` je obecná funkce, která parameterizes své vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="f2c52-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="f2c52-178">Toto omezení může být pro `|>` v budoucnu odlehčené, protože je vložené a neprovádí v těle žádné volání obecných funkcí, které nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="f2c52-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="f2c52-179">I když tato pravidla omezují použití, tak aby mohli bezpečným způsobem plnit vysoce výkonné výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="f2c52-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="f2c52-180">ByRef – vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="f2c52-180">Byref returns</span></span>

<span data-ttu-id="f2c52-181">Návratové hodnoty F# ByRef z funkcí nebo členů lze vytvářet a spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="f2c52-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="f2c52-182">Při zpracování metody vracené `byref`se hodnota implicitně odkázat.</span><span class="sxs-lookup"><span data-stu-id="f2c52-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="f2c52-183">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f2c52-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="f2c52-184">Chcete-li vrátit hodnotu ByRef, proměnná, která obsahuje hodnotu, musí být živá déle než aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="f2c52-184">To return a value byref, the variable which contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="f2c52-185">Také pro návrat typu ByRef použijte & Value (kde value je proměnná, která je větší než aktuální rozsah).</span><span class="sxs-lookup"><span data-stu-id="f2c52-185">Also, to return byref, use &value (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="f2c52-186">Chcete-li se vyhnout implicitnímu odkázání, jako je například předání odkazu prostřednictvím více zřetězených volání, použijte `&x` (kde `x` je hodnota).</span><span class="sxs-lookup"><span data-stu-id="f2c52-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="f2c52-187">Můžete také přímo přiřadit k návratové `byref`.</span><span class="sxs-lookup"><span data-stu-id="f2c52-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="f2c52-188">Vezměte v úvahu následující (vysoce imperativně) program:</span><span class="sxs-lookup"><span data-stu-id="f2c52-188">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="f2c52-189">Toto je výstup:</span><span class="sxs-lookup"><span data-stu-id="f2c52-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="f2c52-190">Určení rozsahu pro parametry ByRef</span><span class="sxs-lookup"><span data-stu-id="f2c52-190">Scoping for byrefs</span></span>

<span data-ttu-id="f2c52-191">Hodnota vazby `let`nemůže mít odkaz nad rámec, ve kterém byla definována.</span><span class="sxs-lookup"><span data-stu-id="f2c52-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="f2c52-192">Například následující příkaz není povolen:</span><span class="sxs-lookup"><span data-stu-id="f2c52-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="f2c52-193">To vám zabrání v získání různých výsledků v závislosti na tom, jestli kompilujete s optimalizací nebo vypnuto.</span><span class="sxs-lookup"><span data-stu-id="f2c52-193">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
