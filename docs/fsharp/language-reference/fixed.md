---
title: 'Klíčové slovo Fixed (F #)'
description: "Zjistěte, jak vám může \"pin\" místní do zásobníku, aby se zabránilo kolekce s F # 'fixed' – klíčové slovo."
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201410"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="e8cb7-103">Klíčové slovo Fixed</span><span class="sxs-lookup"><span data-stu-id="e8cb7-103">The Fixed Keyword</span></span>

<span data-ttu-id="e8cb7-104">Zavádí F # 4.1 `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunuty během uvolňování.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="e8cb7-105">Používá se pro programovacích scénářů pro nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8cb7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8cb7-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="e8cb7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8cb7-107">Remarks</span></span>

<span data-ttu-id="e8cb7-108">Tato zásada rozšiřuje syntaxe výrazy umožňují extrahování ukazatel a vytvoříte jejich vazbu na název, který je zabráněno shromážděných nebo přesunuty během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="e8cb7-109">Ukazatel z výrazu je pevně prostřednictvím `fixed` – klíčové slovo je vázán na identifikátor rozhraní prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="e8cb7-110">Sémantika této je podobný správu prostředků prostřednictvím `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="e8cb7-111">Ukazatel vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, už je pevná.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="e8cb7-112">`fixed` nelze použít mimo kontext `use` vazby.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="e8cb7-113">Je třeba svázat ukazatel myši na název s `use`.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="e8cb7-114">Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="e8cb7-115">Nelze ji použít v oboru skriptu úrovni nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="e8cb7-116">Stejně jako všechny ukazatele kód to je nebezpečné funkce a vygeneruje upozornění při použití.</span><span class="sxs-lookup"><span data-stu-id="e8cb7-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="e8cb7-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8cb7-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e8cb7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8cb7-118">See also</span></span>

- [<span data-ttu-id="e8cb7-119">Nativeptr – modul</span><span class="sxs-lookup"><span data-stu-id="e8cb7-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
