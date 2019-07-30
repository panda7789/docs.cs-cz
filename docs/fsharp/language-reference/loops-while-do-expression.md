---
title: 'Smyčky: Výraz while...do'
description: Podívejte se, jak while... výraz do se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630752"
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

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Můžete použít `while...do` ve výrazech pořadí a dalších výrazech výpočtu. v takovém případě se používá přizpůsobená verze `while...do` výrazu. Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky `for...in`Vyjádření](loops-for-in-expression.md)
- [Smyčky `for...to`Vyjádření](loops-for-to-expression.md)
