---
title: "Fixed – klíčové slovo (F #)"
description: "Zjistěte, jak vám může \"pin\" místní do zásobníku, aby se zabránilo kolekce s F # 'fixed' – klíčové slovo."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: 1605603bc35941e21c798600140036fb678869b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="65426-104">Fixed – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="65426-104">The Fixed Keyword</span></span>

<span data-ttu-id="65426-105">F # 4.1 zavádí `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunout během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="65426-105">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="65426-106">Používá se pro nízké úrovně scénáře programování.</span><span class="sxs-lookup"><span data-stu-id="65426-106">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="65426-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65426-107">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="65426-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65426-108">Remarks</span></span>

<span data-ttu-id="65426-109">Tato zásada rozšiřuje syntaxe výrazy umožňující extrahování ukazatel a vazbu na název, který je nemůže se shromažďují nebo přesunout během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="65426-109">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="65426-110">Ukazatel z výrazu vyřešen prostřednictvím `fixed` – klíčové slovo je vázána na identifikátor prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="65426-110">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="65426-111">Sémantika této je podobná Správa prostředků prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="65426-111">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="65426-112">Ukazatele vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, je už pevná.</span><span class="sxs-lookup"><span data-stu-id="65426-112">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="65426-113">`fixed`nelze použít mimo kontext `use` vazby.</span><span class="sxs-lookup"><span data-stu-id="65426-113">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="65426-114">Je třeba svázat ukazatel myši na název s `use`.</span><span class="sxs-lookup"><span data-stu-id="65426-114">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="65426-115">Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="65426-115">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="65426-116">Nelze zadat v úrovni skriptu nebo modul oboru.</span><span class="sxs-lookup"><span data-stu-id="65426-116">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="65426-117">Jako všechny ukazatele kód to je nebezpečné funkce a bude posílat upozornění při použití.</span><span class="sxs-lookup"><span data-stu-id="65426-117">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="65426-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="65426-118">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="65426-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="65426-119">See Also</span></span>

[<span data-ttu-id="65426-120">Nativeptr – modul</span><span class="sxs-lookup"><span data-stu-id="65426-120">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
