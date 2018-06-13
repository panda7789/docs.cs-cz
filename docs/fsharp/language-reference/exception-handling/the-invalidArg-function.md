---
title: 'Výjimky: Funkce invalidArg (F#)'
description: "Zjistěte, jak funkce 'invalidArg' F # vygeneruje výjimku argument."
ms.date: 05/16/2016
ms.openlocfilehash: 43e1b6f3f36774ac50aeff147f75f133d6e3e5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564505"
---
# <a name="exceptions-the-invalidarg-function"></a>Výjimky: Funkce invalidArg

`invalidArg` Funkce vyvolá výjimku argumentu.


## <a name="syntax"></a>Syntaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Poznámky
Název parametru v předchozí syntaxi je řetězec s názvem parametr, jehož argument byl neplatný. *Řetězec chybové zprávy* řetězcový literál nebo se hodnota typu `string`. Bude `Message` vlastnost objekt výjimky.

Výjimky generovaných `invalidArg` je `System.ArgumentException` výjimka. Následující kód ukazuje použití `invalidArg` vyvolá výjimku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Výstupem je následující příkaz, za nímž následuje trasování zásobníku (není vidět).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Typy výjimek](exception-types.md)

[Výjimky: `try...with` výraz](the-try-with-expression.md)

[Výjimky: `try...finally` výraz](the-try-finally-expression.md)

[Výjimky: `raise` – funkce](the-raise-function.md)

[Výjimky: `failwith` – funkce](the-failwith-function.md)
