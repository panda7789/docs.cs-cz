---
title: 'Smyčky: Výraz while...do'
description: Podívejte se, jak while... výraz do se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216631"
---
# <a name="loops-whiledo-expression"></a>Smyčky: Výraz while...do

`while...do` Výraz se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.

## <a name="syntax"></a>Syntaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky

*Test-Expression* je vyhodnocen; Pokud je `true`, je proveden *výraz tělo* a testový výraz je znovu vyhodnocen. *Výraz body* musí být typu `unit`. Pokud je `false`výraz testu, iterace skončí.

Následující příklad ilustruje použití `while...do` výrazu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Výstupem předchozího kódu je datový proud náhodných čísel od 1 do 20, přičemž poslední z nich je 10.

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Můžete použít `while...do` ve výrazech pořadí a dalších výrazech výpočtu. v takovém případě se používá přizpůsobená verze `while...do` výrazu. Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky `for...in`Vyjádření](loops-for-in-expression.md)
- [Smyčky `for...to`Vyjádření](loops-for-to-expression.md)
