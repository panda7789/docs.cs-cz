---
title: Typ jednotky (F#)
description: Zjistěte, jak "jednotka" typu jazyka F# se často používá k uložení na místě, kde hodnota vyžaduje syntaxi jazyka při je potřeba nebo požadovaných žádná hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204653"
---
# <a name="unit-type"></a>Typ jednotky

`unit` Typ je typ, který ukazuje na nepřítomnost určitou hodnotu; `unit` typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud neexistuje žádná hodnota nebo je potřeba.

## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Poznámky

Každý výraz F# se musí vyhodnotit na hodnotu. Pro výrazy, které nejsou generovány hodnotu, která je zapotřebí, hodnota typu `unit` se používá. `unit` Vypadá podobně jako typ `void` typ v jazycích, jako je C# a C++.

`unit` Typ má jednu hodnotu a tuto hodnotu je indikován token `()`.

Hodnota `unit` typ se často používá v programování pro uložení místo syntaxe jazyka vyžaduje hodnotu, ale pokud žádná hodnota je potřeba nebo požadovaného F#. Příkladem mohou být návratovou hodnotu `printf` funkce. Protože důležité akce `printf` ve funkci, dojde k operaci, funkce nemusí vrátit skutečnou hodnotu. Proto, že návratová hodnota je typu `unit`.

Očekávat některé konstrukce `unit` hodnotu. Například `do` vazby nebo jakéhokoli kódu na nejvyšší úrovni modulu se má vyhodnotit `unit` hodnotu. Kompilátor oznámí upozornění při `do` vazbami nebo kódem na nejvyšší úrovni modulu vytváří výsledek, než `unit` hodnotu, která se nepoužívá, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Toto upozornění je typické pro funkční programování. nezobrazí se v jiných .NET programovacích jazyků. Čistě funkční aplikaci, ve kterém funkce nemají žádné vedlejší účinky, poslední vrácená hodnota je jediným výsledkem volání funkce. Proto když výsledek je ignorován, je možné programovací chyba. I když F# není čistě funkcionálním programovacím jazyce, je vhodné provést funkční styl programování, kdykoli je to možné.

## <a name="see-also"></a>Viz také:

- [Primitivní](primitive-types.md)
- [Referenční dokumentace jazyka F#](index.md)
