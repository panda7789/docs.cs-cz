---
title: 'Fixed – klíčové slovo (F #)'
description: "Zjistěte, jak vám může \"pin\" místní do zásobníku, aby se zabránilo kolekce s F # 'fixed' – klíčové slovo."
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563873"
---
# <a name="the-fixed-keyword"></a>Fixed – klíčové slovo

F # 4.1 zavádí `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunout během uvolňování paměti.  Používá se pro nízké úrovně scénáře programování.

## <a name="syntax"></a>Syntaxe

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Poznámky

Tato zásada rozšiřuje syntaxe výrazy umožňující extrahování ukazatel a vazbu na název, který je nemůže se shromažďují nebo přesunout během uvolňování paměti.  

Ukazatel z výrazu vyřešen prostřednictvím `fixed` – klíčové slovo je vázána na identifikátor prostřednictvím `use` – klíčové slovo.  Sémantika této je podobná Správa prostředků prostřednictvím `use` – klíčové slovo.  Ukazatele vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, je už pevná.  `fixed` nelze použít mimo kontext `use` vazby.  Je třeba svázat ukazatel myši na název s `use`.

Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.  Nelze zadat v úrovni skriptu nebo modul oboru.

Jako všechny ukazatele kód to je nebezpečné funkce a bude posílat upozornění při použití.

## <a name="example"></a>Příklad

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

## <a name="see-also"></a>Viz také

[Nativeptr – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
