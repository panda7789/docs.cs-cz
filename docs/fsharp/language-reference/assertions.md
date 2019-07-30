---
title: Kontrolní výrazy
description: Naučte se používat výraz Assert jako funkci ladění pro testování výrazů v F# programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630035"
---
# <a name="assertions"></a>Kontrolní výrazy

`assert` Výraz je funkce ladění, kterou můžete použít k otestování výrazu. Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Poznámky

Výraz je typu `bool -> unit`. `assert`

V předchozí syntaxi *Podmínka* představuje logický výraz, který má být testován. Pokud se výraz vyhodnotí `true`jako, provádění pokračuje bez ovlivnění. Pokud se vyhodnotí `false`jako, vygeneruje se dialogové okno systémová chyba. Dialogové okno chyby obsahuje titulek, který obsahuje výraz řetězce, který **se nezdařil**. Dialogové okno obsahuje trasování zásobníku, které indikuje, kde došlo k chybě kontrolního výrazu.

Kontrola kontrolního výrazu je povolena pouze při kompilaci v režimu ladění; To znamená, že pokud je `DEBUG` konstanta definována. V systému projektu je `DEBUG` konstanta ve výchozím nastavení definována v konfiguraci ladění, ale ne v konfiguraci vydané verze.

Chyba při selhání kontrolního výrazu nemůže být zachycena pomocí F# zpracování výjimek.

> [!NOTE]
> Funkce překládá na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>. `assert`

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití `assert` výrazu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
