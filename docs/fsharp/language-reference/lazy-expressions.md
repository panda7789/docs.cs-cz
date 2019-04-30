---
title: Opožděné výrazy
description: Zjistěte, jak F# opožděné výrazů může zlepšit výkon aplikací a knihoven.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904108"
---
# <a name="lazy-expressions"></a>Opožděné výrazy

*Opožděné výrazy* jsou výrazy, které není u nich vyhodnoceno okamžitě, ale místo toho se vyhodnocují v případě potřeby výsledek. To může pomoct zlepšit výkon kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *výraz* je kód, který je vyhodnocen pouze v případě, že výsledek je nutné použít, a *identifikátor* je hodnota, která ukládá výsledek. Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečný typ, který se používá pro `'T` se určí na základě výsledku výrazu.

Opožděné výrazy umožňují zvýšit výkon tím, že omezují spuštění výrazy pouze takové situace, ve kterých je potřeba výsledku.

K vynucení výrazů, která se má provést, zavolejte metodu `Force`. `Force` způsobí, že spuštění provést pouze jednou. Následující volání `Force` vrátit stejný výsledek, ale neprovádět je jakýkoli kód.

Následující kód ukazuje použití opožděné výrazů a použití `Force`. V tomto kódu typu `result` je `Lazy<int>`a `Force` vrátí metoda `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Opožděné vyhodnocení, ale ne `Lazy` zadejte, se také používá pro pořadí. Další informace najdete v tématu [pořadí](sequences.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Lazyextensions – modul](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
