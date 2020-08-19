---
title: Výrazy Lazy
description: 'Přečtěte si, jak můžou opožděné výrazy F # zlepšit výkon vašich aplikací a knihoven.'
ms.date: 08/15/2020
ms.openlocfilehash: 71c466ca3b74c9e92b81a3c268e07438ec944905
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558085"
---
# <a name="lazy-expressions"></a>Výrazy Lazy

*Opožděné výrazy* jsou výrazy, které nejsou vyhodnocovány okamžitě, ale jsou vyhodnoceny, když je výsledek požadován. To může pomoci zvýšit výkon kódu.

## <a name="syntax"></a>Syntax

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *výraz* kódem, který je vyhodnocován pouze v případě, že je požadován výsledek, a *identifikátor* je hodnota, která ukládá výsledek. Hodnota je typu [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) , kde skutečný typ, který je použit pro, `'T` je určen z výsledku výrazu.

Opožděné výrazy umožňují zvýšit výkon omezením spouštění výrazů pouze na případy, kdy je zapotřebí výsledek.

Chcete-li vynutit, aby byly výrazy provedeny, zavolejte metodu `Force` . `Force` způsobí, že se provádění provede jenom jednou. Následná volání `Force` vrátí stejný výsledek, ale nespustí žádný kód.

Následující kód ilustruje použití opožděných výrazů a použití `Force` . V tomto kódu typ `result` je `Lazy<int>` a `Force` Metoda vrátí `int` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Opožděné vyhodnocení, ale ne `Lazy` typ, se používá také pro sekvence. Další informace najdete v tématu [sekvence](sequences.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Modul LazyExtensions](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
