---
title: Co je nového ve F# 4.5 - F# Guide
description: Získejte přehled o nových funkcích dostupných v f# 4.5.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186138"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="4ea36-103">Co je nového ve F# 4.5</span><span class="sxs-lookup"><span data-stu-id="4ea36-103">What's new in F# 4.5</span></span>

<span data-ttu-id="4ea36-104">F# 4.5 přidává více vylepšení jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="4ea36-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="4ea36-105">Mnohé z těchto funkcí byly sečteny, abyste mohli psát efektivní kód v F# a zároveň zajistit, že tento kód je bezpečný.</span><span class="sxs-lookup"><span data-stu-id="4ea36-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="4ea36-106">To znamená přidání několika konceptů do jazyka a značné množství analýzy kompilátoru při použití těchto konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="4ea36-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="4ea36-107">Začínáme</span><span class="sxs-lookup"><span data-stu-id="4ea36-107">Get started</span></span>

<span data-ttu-id="4ea36-108">F# 4.5 je k dispozici ve všech distribucích .NET Core a nástrojích Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ea36-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="4ea36-109">[Můžete začít s F#](../get-started/index.md) a dozvíte se více.</span><span class="sxs-lookup"><span data-stu-id="4ea36-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="4ea36-110">Span a byref-jako struktury</span><span class="sxs-lookup"><span data-stu-id="4ea36-110">Span and byref-like structs</span></span>

<span data-ttu-id="4ea36-111">Typ <xref:System.Span%601> zavedený v .NET Core umožňuje reprezentovat vyrovnávací paměti v paměti způsobem silného typu, který je nyní povolen v F# počínaje F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="4ea36-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="4ea36-112">Následující příklad ukazuje, jak můžete znovu použít <xref:System.Span%601> funkci pracující s různými reprezentacemi vyrovnávací paměti:</span><span class="sxs-lookup"><span data-stu-id="4ea36-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="4ea36-113">Důležitým aspektem je, že Span a další [byref-jako struktury](../language-reference/structures.md#byreflike-structs) mají velmi rigidní statické analýzy prováděné kompilátorem, které omezují jejich použití způsoby, které může být neočekávané.</span><span class="sxs-lookup"><span data-stu-id="4ea36-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="4ea36-114">Toto je základní kompromis mezi výkon, expresivita a bezpečnost, která je zavedena v F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="4ea36-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="4ea36-115">Přepracované byrefs</span><span class="sxs-lookup"><span data-stu-id="4ea36-115">Revamped byrefs</span></span>

<span data-ttu-id="4ea36-116">Před F# 4.5 [Byrefs](../language-reference/byrefs.md) v F# byly nebezpečné a nezdravé pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="4ea36-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="4ea36-117">Problémy se zvukem kolem byrefs byly řešeny v F# 4.5 a byla také použita stejná statická analýza provedená pro span a byref-like struktury.</span><span class="sxs-lookup"><span data-stu-id="4ea36-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="4ea36-118">inref<'T> a předčí<'T></span><span class="sxs-lookup"><span data-stu-id="4ea36-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="4ea36-119">Chcete-li reprezentovat pojem jen pro čtení, jen pro zápis a čtení a `inref<'T>`zápis `outref<'T>` spravované ukazatel, F# 4.5 zavádí , typy představují jen pro čtení a jen pro zápis ukazatele, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4ea36-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="4ea36-120">Každý z nich má jinou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="4ea36-120">Each have different semantics.</span></span> <span data-ttu-id="4ea36-121">Nelze například zapisovat do : `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="4ea36-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="4ea36-122">Ve výchozím nastavení odvození typu odvodí spravované ukazatele tak, `inref<'T>` aby byly v souladu s neměnnou povahou kódu F#, pokud již bylo něco deklarováno jako proměnlivé.</span><span class="sxs-lookup"><span data-stu-id="4ea36-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="4ea36-123">Chcete-li něco zapisovat, budete muset `mutable` deklarovat typ jako před předáním jeho adresu funkci nebo členovi, který s ním manipuluje.</span><span class="sxs-lookup"><span data-stu-id="4ea36-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="4ea36-124">Další informace naleznete v [tématu Byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="4ea36-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="4ea36-125">Struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ea36-125">Readonly structs</span></span>

<span data-ttu-id="4ea36-126">Počínaje F# 4.5, můžete anotovat strukturu <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> s jako takové:</span><span class="sxs-lookup"><span data-stu-id="4ea36-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="4ea36-127">To zakazuje deklarování proměnlivý člen v struktuře a vydává metadata, která umožňuje F# a C# považovat za jen pro čtení při spotřebovávat z sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ea36-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="4ea36-128">Další informace najdete v tématu [Struktury jen pro čtení](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="4ea36-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="4ea36-129">Void ukazatele</span><span class="sxs-lookup"><span data-stu-id="4ea36-129">Void pointers</span></span>

<span data-ttu-id="4ea36-130">Typ `voidptr` je přidán do F# 4.5, stejně jako následující funkce:</span><span class="sxs-lookup"><span data-stu-id="4ea36-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="4ea36-131">`NativePtr.ofVoidPtr`převedení ukazatele void na nativní ukazatel int</span><span class="sxs-lookup"><span data-stu-id="4ea36-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="4ea36-132">`NativePtr.toVoidPtr`převedení nativního ukazatele int na ukazatel void</span><span class="sxs-lookup"><span data-stu-id="4ea36-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="4ea36-133">To je užitečné při spolupráci s nativní komponenty, která využívá void ukazatele.</span><span class="sxs-lookup"><span data-stu-id="4ea36-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="4ea36-134">Klíčové slovo `match!`</span><span class="sxs-lookup"><span data-stu-id="4ea36-134">The `match!` keyword</span></span>

<span data-ttu-id="4ea36-135">Klíčové `match!` slovo vylepšuje porovnávání vzorů uvnitř výpočtového výrazu:</span><span class="sxs-lookup"><span data-stu-id="4ea36-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="4ea36-136">To umožňuje zkrátit kód, který často zahrnuje možnosti míchání (nebo jiné typy) s výpočetní výrazy, jako je například asynchronní.</span><span class="sxs-lookup"><span data-stu-id="4ea36-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="4ea36-137">Chcete-li se dozvědět více, viz [zápas!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="4ea36-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="4ea36-138">Uvolněné požadavky na upcasting ve výrazech pole, seznamu a sekvencí</span><span class="sxs-lookup"><span data-stu-id="4ea36-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="4ea36-139">Míchání typů, kde jeden může dědit z jiného uvnitř pole, seznam a sekvence výrazy tradičně `:>` vyžaduje, abyste upcast libovolný odvozený typ jeho nadřazený typ s nebo `upcast`.</span><span class="sxs-lookup"><span data-stu-id="4ea36-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="4ea36-140">To je nyní uvolněná, prokázáno takto:</span><span class="sxs-lookup"><span data-stu-id="4ea36-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="4ea36-141">Uvolnění odsazení pro výrazy pole a seznamu</span><span class="sxs-lookup"><span data-stu-id="4ea36-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="4ea36-142">Před F# 4.5 je třeba nadměrně odsadit pole a seznam výrazů při předání jako argumenty volání metody.</span><span class="sxs-lookup"><span data-stu-id="4ea36-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="4ea36-143">To již není nutné:</span><span class="sxs-lookup"><span data-stu-id="4ea36-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
