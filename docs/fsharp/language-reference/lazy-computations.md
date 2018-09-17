---
title: Opožděné výpočty (F#)
description: 'Zjistěte, jak vylepšit výkon vašich aplikací a knihoven F # opožděné výpočty.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698205"
---
# <a name="lazy-computations"></a>Opožděné výpočty

*Opožděné výpočty* jsou výpočty, které není u nich vyhodnoceno okamžitě, ale místo toho se vyhodnocují v případě potřeby výsledek. To může pomoct zlepšit výkon kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *výraz* je kód, který je vyhodnocen pouze v případě, že výsledek je nutné použít, a *identifikátor* je hodnota, která ukládá výsledek. Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečný typ, který se používá pro `'T` se určí na základě výsledku výrazu.

Opožděné výpočty umožňují zvýšit výkon tím, že omezují spuštění výpočtu na pouze situace, ve kterých je potřeba výsledku.

K vynucení výpočtu, která se má provést, zavolejte metodu `Force`. `Force` způsobí, že spuštění provést pouze jednou. Následující volání `Force` vrátit stejný výsledek, ale neprovádět je jakýkoli kód.

Následující kód ukazuje použití opožděné výpočty a použití `Force`. V tomto kódu typu `result` je `Lazy<int>`a `Force` vrátí metoda `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Opožděné vyhodnocení, ale ne `Lazy` zadejte, se také používá pro pořadí. Další informace najdete v tématu [pořadí](sequences.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Lazyextensions – modul](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
