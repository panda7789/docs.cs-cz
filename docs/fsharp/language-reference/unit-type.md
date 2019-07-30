---
title: Typ jednotky
description: Zjistěte, F# jak se typ Unit často používá k uchování místa, kde je hodnota požadovaná syntaxí jazyka, když není nutná žádná hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630172"
---
# <a name="unit-type"></a>Typ jednotky

Typ je typ, který označuje absenci konkrétní hodnoty `unit` ; typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je vyžadována. `unit`

## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Poznámky

Každý F# výraz se musí vyhodnotit na hodnotu. Pro výrazy, které negenerují hodnotu, která je zajímavá, je použita hodnota typu `unit` . Typ se podobá `void` typu v jazycích, jako jsou C# a C++ `unit`

Typ má jedinou hodnotu a tato hodnota je označena tokenem `()`. `unit`

Hodnota `unit` typu se často používá při F# programování k uchování místa, kde je hodnota požadovaná syntaxí jazyka, ale když není potřebná nebo požadovaná hodnota. Příkladem může být návratová hodnota `printf` funkce. Vzhledem k tomu, že ve `printf` funkci dojde k důležitým akcím operace, funkce nemusí vracet skutečnou hodnotu. Proto je návratová hodnota typu `unit`.

Některé konstruktory očekávají `unit` hodnotu. Například `do` vazba nebo jakýkoli kód na nejvyšší úrovni modulu se očekává pro vyhodnocení `unit` na hodnotu. Kompilátor ohlásí upozornění, pokud `do` vazba nebo kód na nejvyšší úrovni modulu vytvoří výsledek jiný `unit` než hodnota, která není použita, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Toto upozornění je charakteristické pro funkční programování; nezobrazuje se v jiných programovacích jazycích .NET. V čistě funkčním programu, ve kterém funkce nemají žádné vedlejší účinky, je konečný návratová hodnota jediným výsledkem volání funkce. Proto pokud je výsledek ignorován, může to být chyba programování. I F# když není čistě funkční jazyk programování, je dobrým zvykem sledovat funkční styl programování, kdykoli je to možné.

## <a name="see-also"></a>Viz také:

- [Primitivní](primitive-types.md)
- [Referenční dokumentace jazyka F#](index.md)
