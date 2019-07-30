---
title: Výrazy Lazy
description: Přečtěte F# si, jak opožděné výrazy můžou zlepšit výkon vašich aplikací a knihoven.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630750"
---
# <a name="lazy-expressions"></a>Výrazy Lazy

*Opožděné výrazy* jsou výrazy, které nejsou vyhodnocovány okamžitě, ale jsou vyhodnoceny, když je výsledek požadován. To může pomoci zvýšit výkon kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *výraz* kódem, který je vyhodnocován pouze v případě, že je požadován výsledek, a *identifikátor* je hodnota, která ukládá výsledek. Hodnota je typu [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečný typ, který je použit pro `'T` , je určen z výsledku výrazu.

Opožděné výrazy umožňují zvýšit výkon omezením spouštění výrazů pouze na případy, kdy je zapotřebí výsledek.

Chcete-li vynutit, aby byly výrazy provedeny, zavolejte `Force`metodu. `Force`způsobí, že se provádění provede jenom jednou. Následná volání `Force` vrátí stejný výsledek, ale nespustí žádný kód.

Následující kód ilustruje použití opožděných výrazů a použití `Force`. V tomto kódu `result` typ je `Lazy<int>` `Force`ametoda vrátí. `int`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Opožděné vyhodnocení, ale ne `Lazy` typ, se používá také pro sekvence. Další informace najdete v tématu [sekvence](sequences.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Modul LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
