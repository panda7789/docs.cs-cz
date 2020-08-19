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
# <a name="the-fixed-keyword"></a>Klíčové slovo fixed

`fixed`Klíčové slovo umožňuje "připnout" místní na zásobník, aby se zabránilo jeho shromažďování nebo přesouvání během uvolňování paměti.  Používá se v programovacích scénářích nízké úrovně.

## <a name="syntax"></a>Syntax

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Poznámky

Tím se rozšíří Syntaxe výrazů, aby bylo možné extrahovat ukazatel a vytvořit jeho vazbu na název, který se během uvolňování paměti nebrání v shromažďování nebo přesouvání.  

Ukazatel z výrazu je opraven prostřednictvím `fixed` klíčového slova je svázán s identifikátorem prostřednictvím `use` klíčového slova.  Sémantika tohoto je podobná správě prostředků prostřednictvím `use` klíčového slova.  Ukazatel je pevně nastaven, je-li v oboru, a jakmile je mimo rozsah, již není nadále vyřešen.  `fixed` nelze použít mimo kontext `use` vazby.  Je nutné navazovat ukazatel na název pomocí `use` .

Použití `fixed` musí být ve výrazu ve funkci nebo metodě.  Nelze jej použít v oboru na úrovni skriptu nebo modulu.

Podobně jako u všech kódů ukazatelů se jedná o nezabezpečenou funkci a při použití vygeneruje upozornění.

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

- [Modul NativePtr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
