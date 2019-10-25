---
title: Kontrolní výrazy
description: Naučte se používat výraz Assert jako funkci ladění pro testování výrazů v F# programovacím jazyce.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799071"
---
# <a name="assertions"></a>Kontrolní výrazy

Výraz `assert` je funkce ladění, kterou můžete použít k otestování výrazu. Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Poznámky

Výraz `assert` je typu `bool -> unit`.

Funkce `assert` překládá na <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. To znamená, že jeho chování je stejné jako volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> přímo.

Kontrola kontrolního výrazu je povolena pouze při kompilaci v režimu ladění; To znamená, pokud je definována konstanta `DEBUG`. V systém projektu je ve výchozím nastavení konstanta `DEBUG` definována v konfiguraci ladění, ale ne v konfiguraci vydané verze.

Chyba při selhání kontrolního výrazu nemůže být zachycena pomocí F# zpracování výjimek.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití výrazu `assert`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
