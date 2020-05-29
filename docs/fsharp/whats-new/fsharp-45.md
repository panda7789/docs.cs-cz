---
title: 'Co je nového v příručce F # 4,5-F #'
description: 'Získejte přehled o nových funkcích dostupných v F # 4,5.'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202352"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="a292f-103">Co je nového v jazyce F # 4,5</span><span class="sxs-lookup"><span data-stu-id="a292f-103">What's new in F# 4.5</span></span>

<span data-ttu-id="a292f-104">Jazyk f # 4,5 přidává více vylepšení jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="a292f-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="a292f-105">Mnohé z těchto funkcí byly přidány dohromady, aby bylo možné psát efektivní kód v F # a zároveň zajistit bezpečnost tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="a292f-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="a292f-106">To znamená, že přidání několika konceptů do jazyka a významného množství analýzy kompilátoru při použití těchto konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="a292f-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="a292f-107">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a292f-107">Get started</span></span>

<span data-ttu-id="a292f-108">F # 4,5 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a292f-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="a292f-109">Začněte [s F #](../get-started/index.md) a získejte další informace.</span><span class="sxs-lookup"><span data-stu-id="a292f-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="a292f-110">Struktury typu span a ByRef</span><span class="sxs-lookup"><span data-stu-id="a292f-110">Span and byref-like structs</span></span>

<span data-ttu-id="a292f-111"><xref:System.Span%601>Typ zavedený v .NET Core umožňuje znázornit vyrovnávací paměti v paměti se silným typem, který je teď povolený v f # počínaje f # 4,5.</span><span class="sxs-lookup"><span data-stu-id="a292f-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="a292f-112">Následující příklad ukazuje, jak lze znovu použít funkci, která pracuje <xref:System.Span%601> s různými reprezentacemi vyrovnávací paměti:</span><span class="sxs-lookup"><span data-stu-id="a292f-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="a292f-113">Důležitým aspektem je, že rozsah a jiné [struktury typu ByRef](../language-reference/structures.md#byreflike-structs) mají velmi pevnou statickou analýzu provedenou kompilátorem, která omezuje jejich použití způsobem, který by mohl být neočekávaný.</span><span class="sxs-lookup"><span data-stu-id="a292f-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="a292f-114">Jedná se o zásadní kompromisy mezi výkonem, expresivity a bezpečností, které jsou představeny v F # 4,5.</span><span class="sxs-lookup"><span data-stu-id="a292f-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="a292f-115">Přepracované byrefs</span><span class="sxs-lookup"><span data-stu-id="a292f-115">Revamped byrefs</span></span>

<span data-ttu-id="a292f-116">Před F # 4,5 byly [byrefs](../language-reference/byrefs.md) v jazyce f # nebezpečné a nezvukové pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="a292f-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="a292f-117">V jazyce F # 4,5 byly vyřešeny problémy se zvukem ByRef a byla použita stejná statická analýza pro rozsah a strukturu typu ByRef.</span><span class="sxs-lookup"><span data-stu-id="a292f-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="a292f-118">inref< t> a outref< t></span><span class="sxs-lookup"><span data-stu-id="a292f-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="a292f-119">Aby reprezentovala pojem spravovaného ukazatele jen pro čtení, jen pro zápis a čtení a zápis, F # 4,5 představuje `inref<'T>` `outref<'T>` typy, které reprezentují ukazatele jen pro čtení a jen pro zápis, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a292f-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="a292f-120">Každá z nich má různou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="a292f-120">Each have different semantics.</span></span> <span data-ttu-id="a292f-121">Například nemůžete zapisovat do `inref<'T>` :</span><span class="sxs-lookup"><span data-stu-id="a292f-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="a292f-122">Ve výchozím nastavení bude odvození typu odvodit spravované ukazatele jako `inref<'T>` v souladu s neproměnlivou povahou kódu F #, pokud něco již nebylo deklarováno jako mutable.</span><span class="sxs-lookup"><span data-stu-id="a292f-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="a292f-123">Aby bylo možné zapisovat do libovolného textu, je nutné deklarovat typ jako `mutable` před předáním jeho adresy funkci nebo členu, který je s ním manipulován.</span><span class="sxs-lookup"><span data-stu-id="a292f-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="a292f-124">Další informace najdete v tématu [byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="a292f-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="a292f-125">Struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a292f-125">Readonly structs</span></span>

<span data-ttu-id="a292f-126">Počínaje F # 4,5 můžete přidat do struktury poznámku <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> jako takovou:</span><span class="sxs-lookup"><span data-stu-id="a292f-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="a292f-127">To vám neumožní deklarovat proměnlivého člena ve struktuře a emitovat metadata, která umožňují jazyku F # a C# zacházet jako ReadOnly při spotřebování ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="a292f-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="a292f-128">Další informace najdete v tématu [struktury jen pro čtení](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="a292f-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="a292f-129">Ukazatele void</span><span class="sxs-lookup"><span data-stu-id="a292f-129">Void pointers</span></span>

<span data-ttu-id="a292f-130">`voidptr`Typ je přidán do F # 4,5, jak jsou následující funkce:</span><span class="sxs-lookup"><span data-stu-id="a292f-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="a292f-131">`NativePtr.ofVoidPtr`převod ukazatele void na nativní ukazatel int</span><span class="sxs-lookup"><span data-stu-id="a292f-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="a292f-132">`NativePtr.toVoidPtr`převod nativního ukazatele int na ukazatel void</span><span class="sxs-lookup"><span data-stu-id="a292f-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="a292f-133">To je užitečné při spolupráci s nativní komponentou, která využívá ukazatele void.</span><span class="sxs-lookup"><span data-stu-id="a292f-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="a292f-134">Klíčové slovo `match!`</span><span class="sxs-lookup"><span data-stu-id="a292f-134">The `match!` keyword</span></span>

<span data-ttu-id="a292f-135">`match!`Klíčové slovo vylepšuje porovnávání vzorů v rámci výrazu výpočtu:</span><span class="sxs-lookup"><span data-stu-id="a292f-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="a292f-136">To umožňuje zkrátit kód, který často zahrnuje možnosti kombinování (nebo jiných typů) s výpočetními výrazy, jako je například Async.</span><span class="sxs-lookup"><span data-stu-id="a292f-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="a292f-137">Další informace najdete v tématu věnovaném [shodě](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="a292f-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="a292f-138">Odlehčené požadavky na přetypování ve výrazech Array, list a Sequence</span><span class="sxs-lookup"><span data-stu-id="a292f-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="a292f-139">Kombinování typů, kde jedna může dědit z jiného objektu Array, list a Sequence Expressions, je tradičně nutné k přetypování odvozeného typu na svůj nadřazený typ pomocí `:>` nebo `upcast` .</span><span class="sxs-lookup"><span data-stu-id="a292f-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="a292f-140">To je teď odlehčené, které ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="a292f-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="a292f-141">Zmírnění odrážek pro výrazy Array a list</span><span class="sxs-lookup"><span data-stu-id="a292f-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="a292f-142">Před F # 4,5 jste museli při předávání jako argumentů volání metody příliš odsazovat výrazy pole a seznamu.</span><span class="sxs-lookup"><span data-stu-id="a292f-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="a292f-143">Už to není potřeba:</span><span class="sxs-lookup"><span data-stu-id="a292f-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
