---
title: Statisticky vyřešené parametry typu
description: Naučte se používat F# staticky vyřešený parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.
ms.date: 05/16/2016
ms.openlocfilehash: bc3310192cdaa5ae4862b8aee46b6152f61da38a
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082928"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="d4964-103">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="d4964-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="d4964-104">*Staticky vyřešený parametr typu* je parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d4964-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="d4964-105">Předcházejí jim symbolem stříšky (^).</span><span class="sxs-lookup"><span data-stu-id="d4964-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4964-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4964-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="d4964-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4964-107">Remarks</span></span>

<span data-ttu-id="d4964-108">V F# jazyce existují dva různé druhy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="d4964-109">Prvním druhem je standardní parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="d4964-110">Jsou označeny apostrofem ('), jako v `'T` a. `'U`</span><span class="sxs-lookup"><span data-stu-id="d4964-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="d4964-111">Jsou rovnocenné parametrům obecného typu v jiných .NET Framework jazycích.</span><span class="sxs-lookup"><span data-stu-id="d4964-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="d4964-112">Druhý druh je staticky vyřešen a je označen symbolem blikajícího kurzoru, jako v `^T` a. `^U`</span><span class="sxs-lookup"><span data-stu-id="d4964-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="d4964-113">Staticky řešené parametry typu jsou primárně užitečné ve spojení s omezeními členů, což jsou omezení, která umožňují určit, že argument typu musí mít konkrétního člena nebo členy, aby jej bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="d4964-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="d4964-114">Neexistuje žádný způsob, jak vytvořit tento typ omezení pomocí běžného parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="d4964-115">Následující tabulka shrnuje podobnosti a rozdíly mezi dvěma druhy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="d4964-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="d4964-116">Feature</span></span>|<span data-ttu-id="d4964-117">Obecné</span><span class="sxs-lookup"><span data-stu-id="d4964-117">Generic</span></span>|<span data-ttu-id="d4964-118">Staticky vyřešeno</span><span class="sxs-lookup"><span data-stu-id="d4964-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="d4964-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4964-119">Syntax</span></span>|<span data-ttu-id="d4964-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="d4964-120">`'T`, `'U`</span></span>|<span data-ttu-id="d4964-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="d4964-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="d4964-122">Doba řešení</span><span class="sxs-lookup"><span data-stu-id="d4964-122">Resolution time</span></span>|<span data-ttu-id="d4964-123">Za běhu</span><span class="sxs-lookup"><span data-stu-id="d4964-123">Run time</span></span>|<span data-ttu-id="d4964-124">Čas kompilace</span><span class="sxs-lookup"><span data-stu-id="d4964-124">Compile time</span></span>|
|<span data-ttu-id="d4964-125">Omezení členů</span><span class="sxs-lookup"><span data-stu-id="d4964-125">Member constraints</span></span>|<span data-ttu-id="d4964-126">Nelze použít s omezeními členů.</span><span class="sxs-lookup"><span data-stu-id="d4964-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="d4964-127">Dá se použít s omezeními členů.</span><span class="sxs-lookup"><span data-stu-id="d4964-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="d4964-128">Generování kódu</span><span class="sxs-lookup"><span data-stu-id="d4964-128">Code generation</span></span>|<span data-ttu-id="d4964-129">Typ (nebo metoda) se standardními parametry obecného typu mají za následek generování jednoho obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="d4964-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="d4964-130">Je vygenerováno více instancí typů a metod, jeden pro každý typ, který je třeba.</span><span class="sxs-lookup"><span data-stu-id="d4964-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="d4964-131">Použít s typy</span><span class="sxs-lookup"><span data-stu-id="d4964-131">Use with types</span></span>|<span data-ttu-id="d4964-132">Lze použít pro typy.</span><span class="sxs-lookup"><span data-stu-id="d4964-132">Can be used on types.</span></span>|<span data-ttu-id="d4964-133">Nelze použít pro typy.</span><span class="sxs-lookup"><span data-stu-id="d4964-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="d4964-134">Použití s vloženými funkcemi</span><span class="sxs-lookup"><span data-stu-id="d4964-134">Use with inline functions</span></span>|<span data-ttu-id="d4964-135">Ne.</span><span class="sxs-lookup"><span data-stu-id="d4964-135">No.</span></span> <span data-ttu-id="d4964-136">Vložená funkce nemůže být Parametrizovaná s parametrem standardního obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="d4964-137">Ano.</span><span class="sxs-lookup"><span data-stu-id="d4964-137">Yes.</span></span> <span data-ttu-id="d4964-138">Staticky vyřešené parametry typu nelze použít pro funkce nebo metody, které nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="d4964-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="d4964-139">Mnoho F# základních funkcí knihovny, zejména operátory, mají staticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="d4964-140">Tyto funkce a operátory jsou vložené a výsledkem je efektivní generování kódu pro číselné výpočty.</span><span class="sxs-lookup"><span data-stu-id="d4964-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="d4964-141">Vložené metody a funkce, které používají operátory, nebo používají jiné funkce, které mají staticky vyřešené parametry typu, mohou také používat samotné staticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="d4964-142">Často odvození typu odvodí takové vložené funkce pro staticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="d4964-143">Následující příklad ukazuje definici operátoru, která je odvozena pro statický přeložený parametr typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="d4964-144">Vyřešený typ `(+@)` je založen na použití obou `(+)` a `(*)`, z nichž obě způsobují odvození typu pro odvození omezení členů u staticky vyřešených parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="d4964-145">Vyřešený typ, jak je znázorněno v F# Překladači, je následující.</span><span class="sxs-lookup"><span data-stu-id="d4964-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="d4964-146">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="d4964-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="d4964-147">Počínaje F# 4,1 můžete také zadat názvy konkrétních typů ve staticky vyřešených podpisech parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="d4964-148">V předchozích verzích jazyka mohl být název typu ve skutečnosti odvozen kompilátorem, ale v signatuře se v něm nedala zadat skutečná definice.</span><span class="sxs-lookup"><span data-stu-id="d4964-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="d4964-149">Od F# 4,1 můžete zadat také konkrétní názvy typů ve staticky vyřešených podpisech parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d4964-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="d4964-150">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="d4964-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4964-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4964-151">See also</span></span>

- [<span data-ttu-id="d4964-152">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d4964-152">Generics</span></span>](index.md)
- [<span data-ttu-id="d4964-153">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="d4964-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="d4964-154">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="d4964-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="d4964-155">Omezení</span><span class="sxs-lookup"><span data-stu-id="d4964-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="d4964-156">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="d4964-156">Inline Functions</span></span>](../functions/inline-functions.md)
