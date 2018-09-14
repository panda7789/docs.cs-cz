---
title: Statisticky vyřešené parametry typu (F#)
description: 'Další informace o použití jazyka F # parametr staticky řešeného typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.'
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595133"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="00188-103">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="00188-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="00188-104">A *parametr staticky řešeného typu* je parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="00188-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="00188-105">Předchází jim symbol stříšky (^).</span><span class="sxs-lookup"><span data-stu-id="00188-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="00188-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00188-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="00188-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00188-107">Remarks</span></span>

<span data-ttu-id="00188-108">V jazyce F # existují dva odlišné typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="00188-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="00188-109">První druh je standardní obecný typ parametru.</span><span class="sxs-lookup"><span data-stu-id="00188-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="00188-110">Ty jsou označeny apostrofem ('), stejně jako v `'T` a `'U`.</span><span class="sxs-lookup"><span data-stu-id="00188-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="00188-111">Jsou ekvivalentní parametrům obecného typu v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00188-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="00188-112">Jiný typ je staticky řešen a je označen symbolem stříšky, stejně jako v `^T` a `^U`.</span><span class="sxs-lookup"><span data-stu-id="00188-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="00188-113">Staticky rozpoznávané parametry typu jsou především užitečné ve spojení s omezeními členů, což jsou omezení, které vám umožňují určit, že argument typu musí mít určitého člena nebo členy jinak se nedá použít.</span><span class="sxs-lookup"><span data-stu-id="00188-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="00188-114">Neexistuje žádný způsob, jak vytvořit tento druh omezení pomocí parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="00188-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="00188-115">Následující tabulka shrnuje podobnosti a rozdíly mezi těmito dvěma typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="00188-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="00188-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="00188-116">Feature</span></span>|<span data-ttu-id="00188-117">Obecné</span><span class="sxs-lookup"><span data-stu-id="00188-117">Generic</span></span>|<span data-ttu-id="00188-118">Statisticky vyřešené</span><span class="sxs-lookup"><span data-stu-id="00188-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="00188-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00188-119">Syntax</span></span>|<span data-ttu-id="00188-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="00188-120">`'T`, `'U`</span></span>|<span data-ttu-id="00188-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="00188-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="00188-122">Doba řešení</span><span class="sxs-lookup"><span data-stu-id="00188-122">Resolution time</span></span>|<span data-ttu-id="00188-123">Čas spuštění</span><span class="sxs-lookup"><span data-stu-id="00188-123">Run time</span></span>|<span data-ttu-id="00188-124">Doba kompilace</span><span class="sxs-lookup"><span data-stu-id="00188-124">Compile time</span></span>|
|<span data-ttu-id="00188-125">Členská omezení</span><span class="sxs-lookup"><span data-stu-id="00188-125">Member constraints</span></span>|<span data-ttu-id="00188-126">Nelze použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="00188-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="00188-127">Můžete použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="00188-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="00188-128">Generování kódu</span><span class="sxs-lookup"><span data-stu-id="00188-128">Code generation</span></span>|<span data-ttu-id="00188-129">Typ (nebo metoda) se standardními parametry obecného typu způsobí generování jednoho obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="00188-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="00188-130">Více instancí typů a metod jsou generovány, jeden pro každý typ, který je potřeba.</span><span class="sxs-lookup"><span data-stu-id="00188-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="00188-131">Použít s typy</span><span class="sxs-lookup"><span data-stu-id="00188-131">Use with types</span></span>|<span data-ttu-id="00188-132">Můžete použít u typů.</span><span class="sxs-lookup"><span data-stu-id="00188-132">Can be used on types.</span></span>|<span data-ttu-id="00188-133">Nelze použít u typů.</span><span class="sxs-lookup"><span data-stu-id="00188-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="00188-134">Použít s vloženými funkcemi</span><span class="sxs-lookup"><span data-stu-id="00188-134">Use with inline functions</span></span>|<span data-ttu-id="00188-135">Ne.</span><span class="sxs-lookup"><span data-stu-id="00188-135">No.</span></span> <span data-ttu-id="00188-136">Vložená funkce nemůže být parametrizována pomocí standardního obecného parametru typu.</span><span class="sxs-lookup"><span data-stu-id="00188-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="00188-137">Ano.</span><span class="sxs-lookup"><span data-stu-id="00188-137">Yes.</span></span> <span data-ttu-id="00188-138">Staticky rozpoznávané parametry typu nelze použít na funkce ani metody, které nejsou vložené.</span><span class="sxs-lookup"><span data-stu-id="00188-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="00188-139">Řada F # základních knihovních funkcí, hlavně operátory, má staticky řešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="00188-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="00188-140">Tyto funkce a operátory jsou vložené a výsledkem efektivní generování kódu pro numerické výpočty.</span><span class="sxs-lookup"><span data-stu-id="00188-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="00188-141">Vložené metody a funkce, které používají operátory nebo jiné funkce, které mají staticky řešené parametry typu, můžete také použít staticky rozpoznávané parametry typu sami.</span><span class="sxs-lookup"><span data-stu-id="00188-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="00188-142">Často odvození typu odvodí tyto vložené funkce pro staticky řešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="00188-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="00188-143">Následující příklad ukazuje definici operátoru, který je odvozen, aby měl parametr staticky řešeného typu.</span><span class="sxs-lookup"><span data-stu-id="00188-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="00188-144">Rozpoznaný typ `(+@)` je založen na použití obou `(+)` a `(*)`, o což vedlo odvození typu odvozuje členská omezení na staticky rozpoznávaných typových parametrů.</span><span class="sxs-lookup"><span data-stu-id="00188-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="00188-145">Rozpoznaný typ, jak je uvedeno v interpretátoru F # je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="00188-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="00188-146">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="00188-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="00188-147">Od verze F # 4.1, můžete také zadat názvy konkrétních typů v signaturách parametr staticky řešeného typu.</span><span class="sxs-lookup"><span data-stu-id="00188-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="00188-148">V předchozích verzích jazyka název typu nebylo možné odvodit skutečně kompilátorem, ale nemůže ve skutečnosti zadaná v signatuře.</span><span class="sxs-lookup"><span data-stu-id="00188-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="00188-149">Od verze F # 4.1 můžete také zadat názvy konkrétních typů v signaturách parametr staticky řešeného typu.</span><span class="sxs-lookup"><span data-stu-id="00188-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="00188-150">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="00188-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="00188-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00188-151">See also</span></span>

- [<span data-ttu-id="00188-152">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="00188-152">Generics</span></span>](index.md)
- [<span data-ttu-id="00188-153">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="00188-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="00188-154">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="00188-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="00188-155">Omezení</span><span class="sxs-lookup"><span data-stu-id="00188-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="00188-156">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="00188-156">Inline Functions</span></span>](../functions/inline-functions.md)
