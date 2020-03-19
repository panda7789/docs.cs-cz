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
# <a name="byrefs"></a><span data-ttu-id="3f9d4-103">Parametry ByRef</span><span class="sxs-lookup"><span data-stu-id="3f9d4-103">Byrefs</span></span>

<span data-ttu-id="3f9d4-104">F# má dvě hlavní oblasti funkcí, které se zabývají v prostoru programování nízké úrovně:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="3f9d4-105">`byref` / `inref` Typy, / `outref` které jsou spravované ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="3f9d4-106">Mají omezení použití, takže nelze zkompilovat program, který je neplatný za běhu.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="3f9d4-107">-like `byref`struct, což je [struktura,](structures.md) která má podobnou sémantiku a stejné omezení kompilace jako `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="3f9d4-108">Jedním z <xref:System.Span%601>příkladů je .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f9d4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f9d4-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="3f9d4-110">Byref, inref a outref</span><span class="sxs-lookup"><span data-stu-id="3f9d4-110">Byref, inref, and outref</span></span>

<span data-ttu-id="3f9d4-111">Existují tři formy `byref`:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="3f9d4-112">`inref<'T>`, spravovaný ukazatel pro čtení základní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="3f9d4-113">`outref<'T>`, spravovaný ukazatel pro zápis do podkladové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="3f9d4-114">`byref<'T>`, spravovaný ukazatel pro čtení a zápis podkladové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="3f9d4-115">A `byref<'T>` může být `inref<'T>` předána tam, kde se očekává.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="3f9d4-116">Podobně může `byref<'T>` být předána, `outref<'T>` kde se očekává.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="3f9d4-117">Použití byrefs</span><span class="sxs-lookup"><span data-stu-id="3f9d4-117">Using byrefs</span></span>

<span data-ttu-id="3f9d4-118">Chcete-li `inref<'T>`použít , je třeba `&`získat hodnotu ukazatele s :</span><span class="sxs-lookup"><span data-stu-id="3f9d4-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="3f9d4-119">Chcete-li zapsat na `outref<'T>` `byref<'T>`ukazatel pomocí nebo , musíte také `mutable`provést hodnotu, na kterou ukazatel uchopíte .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="3f9d4-120">Pokud ukazatel píšete pouze místo toho, `outref<'T>` abyste `byref<'T>`ho četli, zvažte použití místo .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="3f9d4-121">Sémantiku inref</span><span class="sxs-lookup"><span data-stu-id="3f9d4-121">Inref semantics</span></span>

<span data-ttu-id="3f9d4-122">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="3f9d4-123">Sémanticky to znamená následující:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="3f9d4-124">Držitel `x` ukazatele jej může použít pouze ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="3f9d4-125">Všechny ukazatele `struct` získané na `SomeStruct` pole vnořené v rámci jsou uvedeny typu `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="3f9d4-126">Platí také toto:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-126">The following is also true:</span></span>

* <span data-ttu-id="3f9d4-127">Neexistuje žádný důsledek, že jiná vlákna nebo `x`aliasy nemají přístup pro zápis do aplikace .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="3f9d4-128">Neexistuje žádný důsledek, který `SomeStruct` je neměnný na `x` základě toho, že `inref`je .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="3f9d4-129">Pro typy hodnot F#, které **jsou** neměnné, je však `this` ukazatel odvozen za . `inref`</span><span class="sxs-lookup"><span data-stu-id="3f9d4-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="3f9d4-130">Všechna tato pravidla společně znamenají, `inref` že držitel ukazatele nemusí změnit okamžitý obsah paměti, na kterou se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="3f9d4-131">Sémantiku předčí</span><span class="sxs-lookup"><span data-stu-id="3f9d4-131">Outref semantics</span></span>

<span data-ttu-id="3f9d4-132">Účelem `outref<'T>` je označit, že ukazatel by měl být zapsán pouze do.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="3f9d4-133">Neočekávaně `outref<'T>` umožňuje čtení základní hodnoty i přes jeho název.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="3f9d4-134">Toto je pro účely kompatibility.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-134">This is for compatibility purposes.</span></span> <span data-ttu-id="3f9d4-135">Sémanticky, `outref<'T>` se `byref<'T>`nijak neliší od .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="3f9d4-136">Interop s C\#</span><span class="sxs-lookup"><span data-stu-id="3f9d4-136">Interop with C\#</span></span>

<span data-ttu-id="3f9d4-137">C# podporuje `in ref` `out ref` a klíčová slova, `ref` kromě vrátí.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="3f9d4-138">Následující tabulka ukazuje, jak F# interpretuje to, co c# vydává:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="3f9d4-139">Konstrukce jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f9d4-139">C# construct</span></span>|<span data-ttu-id="3f9d4-140">F# odvodí</span><span class="sxs-lookup"><span data-stu-id="3f9d4-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="3f9d4-141">`ref`vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="3f9d4-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="3f9d4-142">`ref readonly`vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="3f9d4-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="3f9d4-143">`in ref`Parametr</span><span class="sxs-lookup"><span data-stu-id="3f9d4-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="3f9d4-144">`out ref`Parametr</span><span class="sxs-lookup"><span data-stu-id="3f9d4-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="3f9d4-145">V následující tabulce je uvedeno, co f# vyzařuje:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="3f9d4-146">F# konstrukce</span><span class="sxs-lookup"><span data-stu-id="3f9d4-146">F# construct</span></span>|<span data-ttu-id="3f9d4-147">Vyzařovaná konstrukce</span><span class="sxs-lookup"><span data-stu-id="3f9d4-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="3f9d4-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="3f9d4-148">`inref<'T>` argument</span></span>|<span data-ttu-id="3f9d4-149">`[In]`atribut na argumentu</span><span class="sxs-lookup"><span data-stu-id="3f9d4-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="3f9d4-150">`inref<'T>`Vrátit</span><span class="sxs-lookup"><span data-stu-id="3f9d4-150">`inref<'T>` return</span></span>|<span data-ttu-id="3f9d4-151">`modreq`atribut na hodnotě</span><span class="sxs-lookup"><span data-stu-id="3f9d4-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="3f9d4-152">`inref<'T>`v abstraktním slotu nebo implementaci</span><span class="sxs-lookup"><span data-stu-id="3f9d4-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="3f9d4-153">`modreq`na argument nebo návrat</span><span class="sxs-lookup"><span data-stu-id="3f9d4-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="3f9d4-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="3f9d4-154">`outref<'T>` argument</span></span>|<span data-ttu-id="3f9d4-155">`[Out]`atribut na argumentu</span><span class="sxs-lookup"><span data-stu-id="3f9d4-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="3f9d4-156">Pravidla odvození typu a přetížení</span><span class="sxs-lookup"><span data-stu-id="3f9d4-156">Type inference and overloading rules</span></span>

<span data-ttu-id="3f9d4-157">Typ `inref<'T>` je odvozen kompilátorem F#v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="3f9d4-158">Parametr .NET nebo návratový `IsReadOnly` typ, který má atribut.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="3f9d4-159">Ukazatel `this` na typ struktury, který nemá žádná proměnlivá pole.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="3f9d4-160">Adresa umístění paměti odvozené z `inref<_>` jiného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="3f9d4-161">Při implicitní adresu `inref` je přijata, přetížení s `SomeType` argumentem typu je upřednostňována přetížení s argumentem typu `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="3f9d4-162">Například:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-162">For example:</span></span>

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

<span data-ttu-id="3f9d4-163">V obou případech přetížení `System.DateTime` přičemž jsou vyřešeny `inref<System.DateTime>`spíše než přetížení přičemž .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="3f9d4-164">Byref-jako struktury</span><span class="sxs-lookup"><span data-stu-id="3f9d4-164">Byref-like structs</span></span>

<span data-ttu-id="3f9d4-165">Kromě tria `byref` / `inref` / `outref` můžete definovat vlastní struktury, které mohou `byref`dodržovat sémantiku jako.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="3f9d4-166">To se provádí <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> s atributem:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="3f9d4-167">`IsByRefLike`neznamená `Struct`.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="3f9d4-168">Oba musí být přítomen na typu.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-168">Both must be present on the type.</span></span>

<span data-ttu-id="3f9d4-169">Struktura`byref`"-like" v F# je typ hodnoty vázaný na zásobník.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="3f9d4-170">Nikdy přidělena na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="3f9d4-171">-like `byref`struct je užitečné pro vysoce výkonné programování, protože je vynuceno se sadou silných kontrol o životnosti a bez zachycení.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="3f9d4-172">Pravidla jsou:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-172">The rules are:</span></span>

* <span data-ttu-id="3f9d4-173">Mohou být použity jako parametry funkce, parametry metody, lokální proměnné, výnosy metod.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="3f9d4-174">Nemohou být statické nebo instance členy třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="3f9d4-175">Nemohou být zachyceny žádnou`async` uzavírací konstrukcí (metodami nebo výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="3f9d4-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="3f9d4-176">Nelze je použít jako obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="3f9d4-177">Tento poslední bod je rozhodující pro programování `|>` ve stylu kanálu F#, stejně jako obecná funkce, která parametrizuje jeho vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="3f9d4-178">Toto omezení může `|>` být uvolněno pro v budoucnu, protože je vložené a neprovádí žádné volání na nevložené obecné funkce v jeho těle.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="3f9d4-179">Přestože tato pravidla silně omezují použití, činí tak, aby splnila slib vysoce výkonnévýpočetní techniky bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="3f9d4-180">Byref vrátí</span><span class="sxs-lookup"><span data-stu-id="3f9d4-180">Byref returns</span></span>

<span data-ttu-id="3f9d4-181">Byref vrátí z F# funkce nebo členy mohou být vyrobeny a spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="3f9d4-182">Při spotřebovávání `byref`-returning metoda, hodnota je implicitně dereferenced.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="3f9d4-183">Například:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="3f9d4-184">Chcete-li vrátit hodnotu byref, proměnná, která obsahuje hodnotu musí žít déle než aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="3f9d4-185">Chcete-li vrátit byref, použijte `&value` (kde hodnota je proměnná, která žije déle než aktuální obor).</span><span class="sxs-lookup"><span data-stu-id="3f9d4-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="3f9d4-186">Chcete-li se vyhnout implicitní dereference, jako je `&x` například `x` předávání odkazu prostřednictvím více zřetězených volání, použijte (kde je hodnota).</span><span class="sxs-lookup"><span data-stu-id="3f9d4-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="3f9d4-187">Můžete také přímo přiřadit `byref`k návratu .</span><span class="sxs-lookup"><span data-stu-id="3f9d4-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="3f9d4-188">Zvažte následující (velmi imperativní) program:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-188">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="3f9d4-189">Toto je výstup:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="3f9d4-190">Vymezení oborů pro byrefs</span><span class="sxs-lookup"><span data-stu-id="3f9d4-190">Scoping for byrefs</span></span>

<span data-ttu-id="3f9d4-191">Hodnota `let`-bound nemůže mít svůj odkaz překročit rozsah, ve kterém byla definována.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="3f9d4-192">Například následující je zakázáno:</span><span class="sxs-lookup"><span data-stu-id="3f9d4-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="3f9d4-193">Tím zabráníte získání různých výsledků v závislosti na tom, zda kompilujete s optimalizací nebo ne.</span><span class="sxs-lookup"><span data-stu-id="3f9d4-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
