---
title: 'Smyčky: Výraz while...do (F#)'
description: Naleznete v tématu jak při... proveďte použit výraz provádět iterativní spuštění (opakování), zatímco je zadaný testovací podmínka pravdivá.
ms.date: 05/16/2016
ms.openlocfilehash: 43e2098ad6c7f103babc2471aebe987040feb989
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127274"
---
# <a name="loops-whiledo-expression"></a>Smyčky: Výraz while...do

`while...do` Použit výraz provádět iterativní spuštění (opakování), zatímco je zadaný testovací podmínka pravdivá.

## <a name="syntax"></a>Syntaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky

*Výrazu testu* je vyhodnocen; Pokud je `true`, *výraz těla* provádí a testovací výraz je vyhodnocen znovu. *Výraz těla* musí mít typ `unit`. Pokud je test výraz `false`, konce iterace.

Následující příklad ukazuje použití `while...do` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Výstup předchozího kódu je datový proud náhodných čísel od 1 do 20, poslední z nich je 10.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Můžete použít `while...do` ve výrazech pořadí a jiných výrazech výpočtu se v takovém případě přizpůsobenou verzi `while...do` výraz je použit. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky: `for...in` Výraz](loops-for-in-expression.md)
- [Smyčky: `for...to` Výraz](loops-for-to-expression.md)
