---
title: Typ jednotky
description: Zjistěte, F# jak se typ Unit často používá k uchování místa, kde je hodnota požadovaná syntaxí jazyka, když není nutná žádná hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424028"
---
# <a name="unit-type"></a>Typ jednotky

Typ `unit` je typ, který označuje absenci konkrétní hodnoty; typ `unit` má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je potřeba.

## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Poznámky

Každý F# výraz se musí vyhodnotit na hodnotu. Pro výrazy, které negenerují hodnotu, která je zajímavá, je použita hodnota typu `unit`. Typ `unit` se podobá `void` typu v jazycích, jako jsou C# a C++.

Typ `unit` má jedinou hodnotu a tato hodnota je označena `()`tokenu.

Hodnota typu `unit` se často používá při F# programování k uchování místa, kde je hodnota požadovaná syntaxí jazyka, ale když není potřebná nebo požadovaná hodnota. Příkladem může být návratová hodnota funkce `printf`. Vzhledem k tomu, že ve funkci dojde k důležitým akcím operace `printf`, funkce nemusí vracet skutečnou hodnotu. Proto je návratová hodnota typu `unit`.

Některé konstruktory očekávají `unit` hodnotu. Například `do` vazba nebo jakýkoli kód na nejvyšší úrovni modulu se očekává, že se vyhodnotí na hodnotu `unit`. Kompilátor ohlásí upozornění, když `do` vazba nebo kód na nejvyšší úrovni modulu vytvoří výsledek jiný než hodnota `unit`, která není použita, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Toto upozornění je charakteristické pro funkční programování; nezobrazuje se v jiných programovacích jazycích .NET. V čistě funkčním programu, ve kterém funkce nemají žádné vedlejší účinky, je konečný návratová hodnota jediným výsledkem volání funkce. Proto pokud je výsledek ignorován, může to být chyba programování. I F# když není čistě funkční jazyk programování, je dobrým zvykem sledovat funkční styl programování, kdykoli je to možné.

## <a name="see-also"></a>Viz také:

- [Primitivní](basic-types.md)
- [Referenční dokumentace jazyka F#](index.md)
