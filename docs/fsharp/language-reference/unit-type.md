---
title: Typ jednotky (F#)
description: 'Zjistěte, jak je "jednotkou" typ F # často používané pro udržení na místě, kde hodnota je vyžadováno pomocí syntaxe jazyka žádná hodnota, je potřeba nebo požadovaných.'
ms.date: 05/16/2016
ms.openlocfilehash: fdd6b62f9d5c6d73407d5326c7d1f66d55780682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="unit-type"></a>Typ jednotky

`unit` Typ je typ, který ukazuje na nepřítomnost konkrétní hodnotu `unit` typ má pouze jednu hodnotu, která funguje jako zástupný znak, pokud jiná hodnota existuje nebo je potřeba.


## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Poznámky
Každý výraz F # musí vyhodnotit na hodnotu. Pro výrazy, které nevydávají hodnotu, která je v zájmu, hodnota typu `unit` se používá. `unit` Vypadá takto: typ `void` typu v jazyků, například c a C++.

`unit` Typ má jednu hodnotu a tato hodnota je indikován token `()`.

Hodnota `unit` typu se často používá v programování pro uložení na místě, kde hodnota vyžadují na syntaxi jazyka, ale v případě, že žádná hodnota, je potřeba nebo požadovaných F #. Příkladem může být návratová hodnota `printf` funkce. Protože důležité akce `printf` operace nastat ve funkci, funkce nemá vrátit skutečnou hodnotu. Proto se vrácená hodnota je typu `unit`.

Některé konstrukce očekávat `unit` hodnotu. Například `do` je očekávána vazba nebo žádný kód na nejvyšší úrovni modulu k vyhodnocení `unit` hodnotu. Kompilátor sestavy upozornění při `do` vazba nebo kódu na nejvyšší úrovni modulu vytvoří výsledek jiné než `unit` hodnotu, která se nepoužívá, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Toto upozornění je vlastnost funkční programování; nezobrazí se v jiných .NET programovacích jazyků. V čistě funkční programu, ve kterém funkce nemají žádné vedlejší účinky poslední vrácená hodnota je pouze výsledek volání funkce. Proto když výsledek je ignorován, je možné chybě programování. I když F # není plně funkční programovací jazyk, je vhodné postupovat podle funkční programovací styl, kdykoli je to možné.

## <a name="see-also"></a>Viz také
[Primitivní](primitive-types.md)

[Referenční dokumentace jazyka F#](index.md)
