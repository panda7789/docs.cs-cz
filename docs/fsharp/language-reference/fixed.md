---
title: Klíčové slovo fixed
description: 'Přečtěte si, jak můžete připnout místní do zásobníku, aby se zabránilo shromažďování pomocí klíčového slova "fixed" jazyka F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 786ffd706c243fc83f8fb3afc2201d2a34536372
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559177"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="f452f-103">Klíčové slovo fixed</span><span class="sxs-lookup"><span data-stu-id="f452f-103">The fixed keyword</span></span>

<span data-ttu-id="f452f-104">`fixed`Klíčové slovo umožňuje "připnout" místní na zásobník, aby se zabránilo jeho shromažďování nebo přesouvání během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f452f-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="f452f-105">Používá se v programovacích scénářích nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="f452f-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="f452f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f452f-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="f452f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f452f-107">Remarks</span></span>

<span data-ttu-id="f452f-108">Tím se rozšíří Syntaxe výrazů, aby bylo možné extrahovat ukazatel a vytvořit jeho vazbu na název, který se během uvolňování paměti nebrání v shromažďování nebo přesouvání.</span><span class="sxs-lookup"><span data-stu-id="f452f-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="f452f-109">Ukazatel z výrazu je opraven prostřednictvím `fixed` klíčového slova je svázán s identifikátorem prostřednictvím `use` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="f452f-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="f452f-110">Sémantika tohoto je podobná správě prostředků prostřednictvím `use` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="f452f-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="f452f-111">Ukazatel je pevně nastaven, je-li v oboru, a jakmile je mimo rozsah, již není nadále vyřešen.</span><span class="sxs-lookup"><span data-stu-id="f452f-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="f452f-112">`fixed` nelze použít mimo kontext `use` vazby.</span><span class="sxs-lookup"><span data-stu-id="f452f-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="f452f-113">Je nutné navazovat ukazatel na název pomocí `use` .</span><span class="sxs-lookup"><span data-stu-id="f452f-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="f452f-114">Použití `fixed` musí být ve výrazu ve funkci nebo metodě.</span><span class="sxs-lookup"><span data-stu-id="f452f-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="f452f-115">Nelze jej použít v oboru na úrovni skriptu nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="f452f-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="f452f-116">Podobně jako u všech kódů ukazatelů se jedná o nezabezpečenou funkci a při použití vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="f452f-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="f452f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f452f-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f452f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f452f-118">See also</span></span>

- [<span data-ttu-id="f452f-119">Modul NativePtr</span><span class="sxs-lookup"><span data-stu-id="f452f-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
