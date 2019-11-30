---
title: Co je nového v F# 4,5 – F# příručka
description: Získejte přehled o nových funkcích dostupných v F# 4,5.
ms.date: 11/27/2019
ms.openlocfilehash: 780b33a564432aae5ec99c70ff8620988b553fd1
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644108"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="28438-103">Co je nového v F# 4,5</span><span class="sxs-lookup"><span data-stu-id="28438-103">What's new in F# 4.5</span></span>

<span data-ttu-id="28438-104">F#4,5 přidává k F# jazyku více vylepšení.</span><span class="sxs-lookup"><span data-stu-id="28438-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="28438-105">Mnohé z těchto funkcí byly přidány dohromady, aby bylo možné psát efektivní kód v F# nástroji a zároveň zajistit bezpečnost tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="28438-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="28438-106">To znamená, že přidání několika konceptů do jazyka a významného množství analýzy kompilátoru při použití těchto konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="28438-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="28438-107">Začínáme</span><span class="sxs-lookup"><span data-stu-id="28438-107">Get started</span></span>

<span data-ttu-id="28438-108">F#4,5 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28438-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="28438-109">Začněte [s F# ](../get-started/index.md) a získejte další informace.</span><span class="sxs-lookup"><span data-stu-id="28438-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="28438-110">Struktury typu span a ByRef</span><span class="sxs-lookup"><span data-stu-id="28438-110">Span and byref-like structs</span></span>

<span data-ttu-id="28438-111">Typ <xref:System.Span%601> představený v .NET Core umožňuje znázornit vyrovnávací paměti v paměti silným způsobem, který je teď povolený v F# počátečním F# 4,5.</span><span class="sxs-lookup"><span data-stu-id="28438-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="28438-112">Následující příklad ukazuje, jak lze znovu použít funkci, která pracuje na <xref:System.Span%601> s různými reprezentacemi vyrovnávací paměti:</span><span class="sxs-lookup"><span data-stu-id="28438-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="28438-113">Důležitým aspektem je, že rozsah a jiné [struktury typu ByRef](../language-reference/structures.md#byreflike-structs) mají velmi pevnou statickou analýzu provedenou kompilátorem, která omezuje jejich použití způsobem, který by mohl být neočekávaný.</span><span class="sxs-lookup"><span data-stu-id="28438-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="28438-114">Jedná se o zásadní kompromisy mezi výkonem, expresivity a bezpečností, které jsou F# představeny v 4,5.</span><span class="sxs-lookup"><span data-stu-id="28438-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="28438-115">Přepracované byrefs</span><span class="sxs-lookup"><span data-stu-id="28438-115">Revamped byrefs</span></span>

<span data-ttu-id="28438-116">Před F# 4,5 byly [parametry ByRef](../language-reference/byrefs.md) v v F# nebezpečném a nezvukovém případě řady aplikací.</span><span class="sxs-lookup"><span data-stu-id="28438-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="28438-117">V F# 4,5 byly vyřešeny problémy se zvukem u ByRef a byla použita stejná statická analýza pro rozsah a strukturu typu ByRef.</span><span class="sxs-lookup"><span data-stu-id="28438-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="28438-118">inref < t > a outref < t ></span><span class="sxs-lookup"><span data-stu-id="28438-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="28438-119">Aby reprezentovala pojem spravovaného ukazatele jen pro čtení, jen pro zápis a čtení a zápis, F# 4,5 zavádí `inref<'T>`, `outref<'T>` typy, které reprezentují ukazatele jen pro čtení a jen pro zápis, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="28438-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="28438-120">Každá z nich má různou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="28438-120">Each have different semantics.</span></span> <span data-ttu-id="28438-121">Například nemůžete zapisovat do `inref<'T>`:</span><span class="sxs-lookup"><span data-stu-id="28438-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="28438-122">Ve výchozím nastavení bude odvození typu odvodit spravované ukazatele jako `inref<'T>`, aby byly v souladu s neproměnlivou povahou F# kódu, pokud něco již nebylo deklarováno jako mutable.</span><span class="sxs-lookup"><span data-stu-id="28438-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="28438-123">Aby bylo možné zapisovat do stejného stavu, musíte deklarovat typ jako `mutable` před předáním jeho adresy funkci nebo členu, který ho zpracovává.</span><span class="sxs-lookup"><span data-stu-id="28438-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="28438-124">Další informace najdete v tématu [byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="28438-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="28438-125">Struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="28438-125">Readonly structs</span></span>

<span data-ttu-id="28438-126">Od F# 4,5 můžete k struktuře přidat poznámku <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> takto:</span><span class="sxs-lookup"><span data-stu-id="28438-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="28438-127">To vám neumožní deklarovat proměnlivého člena ve struktuře a emitovat metadata, která umožňují F# a C# považuje je jako ReadOnly, pokud je využívána ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="28438-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="28438-128">Další informace najdete v tématu [struktury jen pro čtení](../language-reference/structures.md#readonly-structs) .</span><span class="sxs-lookup"><span data-stu-id="28438-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs)</span></span>

## <a name="void-pointers"></a><span data-ttu-id="28438-129">Ukazatele void</span><span class="sxs-lookup"><span data-stu-id="28438-129">Void pointers</span></span>

<span data-ttu-id="28438-130">Typ `voidptr` se přidá do F# 4,5, jak jsou to tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="28438-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="28438-131">`NativePtr.ofVoidPtr` převést ukazatel void na nativní ukazatel int</span><span class="sxs-lookup"><span data-stu-id="28438-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="28438-132">`NativePtr.toVoidPtr` pro převod nativního ukazatele int na ukazatel void</span><span class="sxs-lookup"><span data-stu-id="28438-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="28438-133">To je užitečné při spolupráci s nativní komponentou, která využívá ukazatele void.</span><span class="sxs-lookup"><span data-stu-id="28438-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="28438-134">Klíčové slovo `match!`</span><span class="sxs-lookup"><span data-stu-id="28438-134">The `match!` keyword</span></span>

<span data-ttu-id="28438-135">Klíčové slovo `match!` vylepšuje porovnávání vzorů v rámci výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="28438-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="28438-136">To umožňuje zkrátit kód, který často zahrnuje možnosti kombinování (nebo jiných typů) s výpočetními výrazy, jako je například Async.</span><span class="sxs-lookup"><span data-stu-id="28438-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="28438-137">Další informace najdete v tématu věnovaném [shodě](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="28438-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="28438-138">Odlehčené požadavky na přetypování ve výrazech Array, list a Sequence</span><span class="sxs-lookup"><span data-stu-id="28438-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="28438-139">Kombinování typů, kde jedna může dědit z jiného uvnitř pole, a výrazy pořadí, je tradičně nutné k přetypování odvozeného typu na svůj nadřazený typ pomocí `:>` nebo `upcast`.</span><span class="sxs-lookup"><span data-stu-id="28438-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="28438-140">To je teď odlehčené, které ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="28438-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="28438-141">Zmírnění odrážek pro výrazy Array a list</span><span class="sxs-lookup"><span data-stu-id="28438-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="28438-142">Před F# 4,5 jste museli při předávání jako argumentů volání metody příliš odsazovat výrazy pole a seznamu.</span><span class="sxs-lookup"><span data-stu-id="28438-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="28438-143">Už to není potřeba:</span><span class="sxs-lookup"><span data-stu-id="28438-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
