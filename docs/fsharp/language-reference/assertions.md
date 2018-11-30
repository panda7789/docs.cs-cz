---
title: Kontrolní výrazy (F#)
description: Zjistěte, jak použít výraz "výraz" jako funkce ladění pro testování výrazy v F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: fbaf038f08cfc74e6cb262c110322dc586813c0c
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671901"
---
# <a name="assertions"></a>Kontrolní výrazy

`assert` Výrazu je funkce, ladění, která slouží k otestování výrazu. Po selhání v režimu ladění generuje kontrolní výraz dialogové okno chyby systému.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Poznámky

`assert` Výraz má typ `bool -> unit`.

V předchozí syntaxi *podmínku* představuje logický výraz, který se má testovat. Pokud je výraz vyhodnocen `true`, provádění pokračuje to neovlivní. Pokud je vyhodnocen jako `false`, je vygenerována chyba dialogové okno systému. Dialog s chybou má popisek, který obsahuje řetězec **chyba kontrolního výrazu**. Dialogové okno obsahuje trasování zásobníku, která určuje, kde došlo k selhání kontrolního výrazu.

Kontrolní výraz je povolená kontrola jenom při kompilaci v režimu ladění. To znamená pokud konstanty `DEBUG` je definována. V systému projektu, ve výchozím nastavení `DEBUG` – konstanta je definován v konfiguraci ladění, ale ne v konfiguraci vydané verze.

Chyba kontrolního výrazu nejde zachytit pomocí F# zpracování výjimek.

> [!NOTE]
> `assert` Funkce se překládá na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití `assert` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
