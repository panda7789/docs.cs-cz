---
title: 'Klíčové slovo Fixed (F #)'
description: "Zjistěte, jak vám může \"pin\" místní do zásobníku, aby se zabránilo kolekce s F # 'fixed' – klíčové slovo."
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624506"
---
# <a name="the-fixed-keyword"></a>Klíčové slovo Fixed

Zavádí F # 4.1 `fixed` – klíčové slovo, které umožňuje "připnout" místní do zásobníku, aby se zabránilo jejímu shromážděných nebo přesunuty během uvolňování.  Používá se pro programovacích scénářů pro nízké úrovně.

## <a name="syntax"></a>Syntaxe

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Poznámky

Tato zásada rozšiřuje syntaxe výrazy umožňují extrahování ukazatel a vytvoříte jejich vazbu na název, který je zabráněno shromážděných nebo přesunuty během uvolňování paměti.  

Ukazatel z výrazu je pevně prostřednictvím `fixed` – klíčové slovo je vázán na identifikátor rozhraní prostřednictvím `use` – klíčové slovo.  Sémantika této je podobný správu prostředků prostřednictvím `use` – klíčové slovo.  Ukazatel vyřešen, zatímco se nachází v oboru, a jakmile je mimo rozsah, už je pevná.  `fixed` nelze použít mimo kontext `use` vazby.  Je třeba svázat ukazatel myši na název s `use`.

Použití `fixed` musí nastat do během výraz ve funkci nebo metodu.  Nelze ji použít v oboru skriptu úrovni nebo modulu.

Stejně jako všechny ukazatele kód to je nebezpečné funkce a vygeneruje upozornění při použití.

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

## <a name="see-also"></a>Viz také:

- [Nativeptr – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
