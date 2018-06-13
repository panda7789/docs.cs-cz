---
title: Statisticky vyřešené parametry typu (F#)
description: 'Naučte se používat F # typu určené statisticky parametr, který se nahradí skutečný typ v době kompilace místo v době běhu.'
ms.date: 05/16/2016
ms.openlocfilehash: 12c2af4d9df7ae1e5e77efc9413eb8777459a83c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233779"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="d82fd-103">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="d82fd-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="d82fd-104">A *parametr typu určené statisticky* je parametr typu, který se nahradí skutečný typ v době kompilace místo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="d82fd-105">Před symbol šipka nahoru (^).</span><span class="sxs-lookup"><span data-stu-id="d82fd-105">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="d82fd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d82fd-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="d82fd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d82fd-107">Remarks</span></span>
<span data-ttu-id="d82fd-108">V jazyce F # existují dva odlišné typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="d82fd-109">Prvním typem je parametr standardní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="d82fd-110">Apostrof ('), bude označen jako v `'T` a `'U`.</span><span class="sxs-lookup"><span data-stu-id="d82fd-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="d82fd-111">Jsou ekvivalentní parametry obecného typu v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d82fd-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="d82fd-112">Další typ je statisticky a je indikován symbol pomocí kurzoru, jako v `^T` a `^U`.</span><span class="sxs-lookup"><span data-stu-id="d82fd-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="d82fd-113">Parametry typu určené statisticky jsou užitečné hlavně v kombinaci s omezeními člen, které jsou omezení, která umožňují určit, že argument typu musí mít konkrétní člena nebo členy aby bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="d82fd-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="d82fd-114">Neexistuje žádný způsob, jak vytvořit tento druh omezení pomocí parametru regulární obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="d82fd-115">Následující tabulka shrnuje podobnosti a rozdíly mezi dva typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="d82fd-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="d82fd-116">Feature</span></span>|<span data-ttu-id="d82fd-117">Obecné</span><span class="sxs-lookup"><span data-stu-id="d82fd-117">Generic</span></span>|<span data-ttu-id="d82fd-118">Statisticky vyřešené</span><span class="sxs-lookup"><span data-stu-id="d82fd-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="d82fd-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d82fd-119">Syntax</span></span>|<span data-ttu-id="d82fd-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="d82fd-120">`'T`, `'U`</span></span>|<span data-ttu-id="d82fd-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="d82fd-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="d82fd-122">Doba řešení</span><span class="sxs-lookup"><span data-stu-id="d82fd-122">Resolution time</span></span>|<span data-ttu-id="d82fd-123">Čas spuštění</span><span class="sxs-lookup"><span data-stu-id="d82fd-123">Run time</span></span>|<span data-ttu-id="d82fd-124">Doba kompilace</span><span class="sxs-lookup"><span data-stu-id="d82fd-124">Compile time</span></span>|
|<span data-ttu-id="d82fd-125">Člen omezení</span><span class="sxs-lookup"><span data-stu-id="d82fd-125">Member constraints</span></span>|<span data-ttu-id="d82fd-126">Nelze použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="d82fd-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="d82fd-127">Lze použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="d82fd-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="d82fd-128">Generování kódu</span><span class="sxs-lookup"><span data-stu-id="d82fd-128">Code generation</span></span>|<span data-ttu-id="d82fd-129">Na typ (nebo metoda) s parametry obecného typu standardní výsledkem generování jeden obecný typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="d82fd-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="d82fd-130">Více instancí možnosti typy a metody jsou generovány, jednu pro každý typ, který je potřeba.</span><span class="sxs-lookup"><span data-stu-id="d82fd-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="d82fd-131">Použít s typy</span><span class="sxs-lookup"><span data-stu-id="d82fd-131">Use with types</span></span>|<span data-ttu-id="d82fd-132">Lze použít na typech.</span><span class="sxs-lookup"><span data-stu-id="d82fd-132">Can be used on types.</span></span>|<span data-ttu-id="d82fd-133">Nelze použít na typech.</span><span class="sxs-lookup"><span data-stu-id="d82fd-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="d82fd-134">Použití s vložené funkce</span><span class="sxs-lookup"><span data-stu-id="d82fd-134">Use with inline functions</span></span>|<span data-ttu-id="d82fd-135">Ne.</span><span class="sxs-lookup"><span data-stu-id="d82fd-135">No.</span></span> <span data-ttu-id="d82fd-136">Vložená funkce nelze parametry s parametrem standardní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="d82fd-137">Ano.</span><span class="sxs-lookup"><span data-stu-id="d82fd-137">Yes.</span></span> <span data-ttu-id="d82fd-138">Parametry typu určené statisticky nelze použít na funkce nebo metody, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="d82fd-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="d82fd-139">Mnoho F # základní funkce knihovny, hlavně operátory, mají statisticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="d82fd-140">Tyto funkce a operátory vložené a výsledkem generování efektivní kódu pro číselné výpočty.</span><span class="sxs-lookup"><span data-stu-id="d82fd-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="d82fd-141">Vložené metody a funkce, které použijte operátory, nebo použijte jiné funkce, které mají statisticky vyřešené parametry typu, můžete také parametry typu určené statisticky, sami.</span><span class="sxs-lookup"><span data-stu-id="d82fd-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="d82fd-142">Odvození typu často odvodí takové funkce vložené do mají statisticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="d82fd-143">Následující příklad ukazuje definici operátor odvozené tak, aby měl parametr typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="d82fd-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="d82fd-144">Přeložit typ `(+@)` je založen na používání obou `(+)` a `(*)`, z které způsobit odvození typu odvodit člen omezení pro parametry typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="d82fd-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="d82fd-145">Vyřešení typu, jak je znázorněno v překladač F # je následující.</span><span class="sxs-lookup"><span data-stu-id="d82fd-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="d82fd-146">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="d82fd-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="d82fd-147">Od verze 4.1 F #, můžete také zadat konkrétní typ názvy v podpisy parametr typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="d82fd-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="d82fd-148">V předchozích verzích jazyka název typu ve skutečnosti se nedá odvodit kompilátorem, ale nelze zadat ve skutečnosti v podpisu.</span><span class="sxs-lookup"><span data-stu-id="d82fd-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="d82fd-149">Od verze F # 4.1 můžete také určit konkrétní typ názvy v typu určené statisticky parametr podpisy.</span><span class="sxs-lookup"><span data-stu-id="d82fd-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="d82fd-150">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="d82fd-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="d82fd-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="d82fd-151">See Also</span></span>
[<span data-ttu-id="d82fd-152">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d82fd-152">Generics</span></span>](index.md)

[<span data-ttu-id="d82fd-153">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="d82fd-153">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="d82fd-154">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="d82fd-154">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="d82fd-155">Omezení</span><span class="sxs-lookup"><span data-stu-id="d82fd-155">Constraints</span></span>](constraints.md)

[<span data-ttu-id="d82fd-156">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="d82fd-156">Inline Functions</span></span>](../functions/inline-functions.md)
