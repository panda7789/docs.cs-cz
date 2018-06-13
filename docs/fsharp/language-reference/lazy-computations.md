---
title: Opožděné výpočty (F#)
description: 'Zjistěte, jak vylepšit výkon aplikace a knihovny F # opožděné výpočty.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563929"
---
# <a name="lazy-computations"></a>Opožděné výpočty

*Opožděné výpočty* jsou výpočty, které se nevyhodnotily okamžitě, ale místo toho vyhodnocují potřeby výsledek. To vám může pomoct zlepšit výkon vašeho kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Poznámky

V předchozích syntaxi *výraz* je kód, který se vyhodnotí jenom v případě, že v důsledku toho je nutné, a *identifikátor* je hodnota, která ukládá výsledek. Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečnou typu se používá pro `'T` se určí na základě výsledku výraz.

Opožděné výpočty umožňují vylepšit výkon, omezení provádění výpočtu pouze situací, ve kterých je potřeba výsledku.

Chcete-li vynutit výpočet provést, volejte metodu `Force`. `Force` způsobí, že provádění provést pouze jednou. Následující volání `Force` vrátí stejné vést, ale nemůžou provést žádný kód.

Následující kód ukazuje použití opožděné výpočty a použití `Force`. V tomto kódu typ `result` je `Lazy<int>`a `Force` metoda vrátí `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Opožděné vyhodnocení, ale ne `Lazy` typem, se taky používá pro pořadí. Další informace najdete v tématu [pořadí](sequences.md).

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)

[Lazyextensions – modul](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
