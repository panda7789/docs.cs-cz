---
title: "Statisticky vyřešené parametry typu (F#)"
description: "Naučte se používat F # typu určené statisticky parametr, který se nahradí skutečný typ v době kompilace místo v době běhu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 88b4590a4323e75949c1915503b51793283792de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="ca6c9-104">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="ca6c9-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="ca6c9-105">A *parametr typu určené statisticky* je parametr typu, který se nahradí skutečný typ v době kompilace místo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="ca6c9-106">Před symbol šipka nahoru (^).</span><span class="sxs-lookup"><span data-stu-id="ca6c9-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="ca6c9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca6c9-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="ca6c9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca6c9-108">Remarks</span></span>
<span data-ttu-id="ca6c9-109">V jazyce F # existují dva odlišné typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="ca6c9-110">Prvním typem je parametr standardní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="ca6c9-111">Apostrof ('), bude označen jako v `'T` a `'U`.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="ca6c9-112">Jsou ekvivalentní parametry obecného typu v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="ca6c9-113">Další typ je statisticky a je indikován symbol pomocí kurzoru, jako v `^T` a `^U`.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="ca6c9-114">Parametry typu určené statisticky jsou užitečné hlavně v kombinaci s omezeními člen, které jsou omezení, která umožňují určit, že argument typu musí mít konkrétní člena nebo členy aby bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="ca6c9-115">Neexistuje žádný způsob, jak vytvořit tento druh omezení pomocí parametru regulární obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="ca6c9-116">Následující tabulka shrnuje podobnosti a rozdíly mezi dva typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="ca6c9-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="ca6c9-117">Feature</span></span>|<span data-ttu-id="ca6c9-118">Obecné</span><span class="sxs-lookup"><span data-stu-id="ca6c9-118">Generic</span></span>|<span data-ttu-id="ca6c9-119">Statisticky vyřešené</span><span class="sxs-lookup"><span data-stu-id="ca6c9-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="ca6c9-120">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca6c9-120">Syntax</span></span>|<span data-ttu-id="ca6c9-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="ca6c9-121">`'T`, `'U`</span></span>|<span data-ttu-id="ca6c9-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="ca6c9-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="ca6c9-123">Doba řešení</span><span class="sxs-lookup"><span data-stu-id="ca6c9-123">Resolution time</span></span>|<span data-ttu-id="ca6c9-124">Čas spuštění</span><span class="sxs-lookup"><span data-stu-id="ca6c9-124">Run time</span></span>|<span data-ttu-id="ca6c9-125">Doba kompilace</span><span class="sxs-lookup"><span data-stu-id="ca6c9-125">Compile time</span></span>|
|<span data-ttu-id="ca6c9-126">Člen omezení</span><span class="sxs-lookup"><span data-stu-id="ca6c9-126">Member constraints</span></span>|<span data-ttu-id="ca6c9-127">Nelze použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="ca6c9-128">Lze použít s omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="ca6c9-129">Generování kódu</span><span class="sxs-lookup"><span data-stu-id="ca6c9-129">Code generation</span></span>|<span data-ttu-id="ca6c9-130">Na typ (nebo metoda) s parametry obecného typu standardní výsledkem generování jeden obecný typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="ca6c9-131">Více instancí možnosti typy a metody jsou generovány, jednu pro každý typ, který je potřeba.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="ca6c9-132">Použít s typy</span><span class="sxs-lookup"><span data-stu-id="ca6c9-132">Use with types</span></span>|<span data-ttu-id="ca6c9-133">Lze použít na typech.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-133">Can be used on types.</span></span>|<span data-ttu-id="ca6c9-134">Nelze použít na typech.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="ca6c9-135">Použití s vložené funkce</span><span class="sxs-lookup"><span data-stu-id="ca6c9-135">Use with inline functions</span></span>|<span data-ttu-id="ca6c9-136">Ne.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-136">No.</span></span> <span data-ttu-id="ca6c9-137">Vložená funkce nelze parametry s parametrem standardní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="ca6c9-138">Ano.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-138">Yes.</span></span> <span data-ttu-id="ca6c9-139">Parametry typu určené statisticky nelze použít na funkce nebo metody, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="ca6c9-140">Mnoho F # základní funkce knihovny, hlavně operátory, mají statisticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="ca6c9-141">Tyto funkce a operátory vložené a výsledkem generování efektivní kódu pro číselné výpočty.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="ca6c9-142">Vložené metody a funkce, které použijte operátory, nebo použijte jiné funkce, které mají statisticky vyřešené parametry typu, můžete také parametry typu určené statisticky, sami.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="ca6c9-143">Odvození typu často odvodí takové funkce vložené do mají statisticky vyřešené parametry typu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="ca6c9-144">Následující příklad ukazuje definici operátor odvozené tak, aby měl parametr typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="ca6c9-145">Přeložit typ `(+@)` je založen na používání obou `(+)` a `(*)`, z které způsobit odvození typu odvodit člen omezení pro parametry typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="ca6c9-146">Vyřešení typu, jak je znázorněno v překladač F # je následující.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member (+) : ^a * ^b -> ^d) and
(^a or ^c) : (static member (+) : ^a * ^c -> ^b)
```

<span data-ttu-id="ca6c9-147">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="ca6c9-148">Od verze 4.1 F #, můžete také zadat konkrétní typ názvy v podpisy parametr typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="ca6c9-149">V předchozích verzích jazyka název typu ve skutečnosti se nedá odvodit kompilátorem, ale nelze zadat ve skutečnosti v podpisu.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="ca6c9-150">Od verze F # 4.1 můžete také určit konkrétní typ názvy v typu určené statisticky parametr podpisy.</span><span class="sxs-lookup"><span data-stu-id="ca6c9-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="ca6c9-151">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="ca6c9-151">Here's an example:</span></span>

```fsharp
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

## <a name="see-also"></a><span data-ttu-id="ca6c9-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca6c9-152">See Also</span></span>
[<span data-ttu-id="ca6c9-153">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ca6c9-153">Generics</span></span>](index.md)

[<span data-ttu-id="ca6c9-154">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="ca6c9-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="ca6c9-155">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="ca6c9-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="ca6c9-156">Omezení</span><span class="sxs-lookup"><span data-stu-id="ca6c9-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="ca6c9-157">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="ca6c9-157">Inline Functions</span></span>](../functions/inline-functions.md)
