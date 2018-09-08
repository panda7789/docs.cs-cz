---
title: Kontrolní výrazy (F#)
description: 'Zjistěte, jak použít výraz "výraz" jako funkce ladění pro testování výrazů v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206416"
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

Chyba kontrolního výrazu nejde zachytit pomocí zpracování výjimek v F #.

>[!NOTE]
`assert` Funkce se překládá na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití `assert` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
