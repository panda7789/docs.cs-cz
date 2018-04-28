---
title: 'Fixed – klíčové slovo (F #)'
description: "Zjistěte, jak vám může \"pin\" místní do zásobníku, aby se zabránilo kolekce s F # 'fixed' – klíčové slovo."
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 8c1d486ec754335dfbaeec439b1eb949494e4241
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="d4cac-103">Fixed – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="d4cac-103">The Fixed Keyword</span></span>

<span data-ttu-id="d4cac-104">F # 4.1 zavádí `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunout během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4cac-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="d4cac-105">Používá se pro nízké úrovně scénáře programování.</span><span class="sxs-lookup"><span data-stu-id="d4cac-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4cac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4cac-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="d4cac-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4cac-107">Remarks</span></span>

<span data-ttu-id="d4cac-108">Tato zásada rozšiřuje syntaxe výrazy umožňující extrahování ukazatel a vazbu na název, který je nemůže se shromažďují nebo přesunout během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4cac-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="d4cac-109">Ukazatel z výrazu vyřešen prostřednictvím `fixed` – klíčové slovo je vázána na identifikátor prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d4cac-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="d4cac-110">Sémantika této je podobná Správa prostředků prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d4cac-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="d4cac-111">Ukazatele vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, je už pevná.</span><span class="sxs-lookup"><span data-stu-id="d4cac-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="d4cac-112">`fixed` nelze použít mimo kontext `use` vazby.</span><span class="sxs-lookup"><span data-stu-id="d4cac-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="d4cac-113">Je třeba svázat ukazatel myši na název s `use`.</span><span class="sxs-lookup"><span data-stu-id="d4cac-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="d4cac-114">Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="d4cac-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="d4cac-115">Nelze zadat v úrovni skriptu nebo modul oboru.</span><span class="sxs-lookup"><span data-stu-id="d4cac-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="d4cac-116">Jako všechny ukazatele kód to je nebezpečné funkce a bude posílat upozornění při použití.</span><span class="sxs-lookup"><span data-stu-id="d4cac-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="d4cac-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4cac-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="d4cac-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4cac-118">See Also</span></span>

[<span data-ttu-id="d4cac-119">Nativeptr – modul</span><span class="sxs-lookup"><span data-stu-id="d4cac-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
