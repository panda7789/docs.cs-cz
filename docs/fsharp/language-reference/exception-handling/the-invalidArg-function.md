---
title: 'Výjimky: Funkce invalidArg'
description: Přečtěte si F# , jak funkce invalidArg generuje výjimku argumentu.
ms.date: 05/16/2016
ms.openlocfilehash: 010dbfe313f539093b4ee7a19984ef54500b072d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630307"
---
# <a name="exceptions-the-invalidarg-function"></a>Výjimky: Funkce invalidArg

`invalidArg` Funkce vygeneruje výjimku argumentu.

## <a name="syntax"></a>Syntaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Poznámky

Parametr-Name v předchozí syntaxi je řetězec s názvem parametru, jehož argument je neplatný. *Chyba-zpráva-řetězec* je řetězcový literál nebo hodnota typu `string`. Bude se `Message` jednat o vlastnost objektu Exception.

Výjimka vygenerovaná nástrojem `invalidArg` `System.ArgumentException` je výjimka. Následující kód ilustruje použití `invalidArg` k vyvolání výjimky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Výstup je následující a následuje trasování zásobníku (nezobrazuje se).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
- [Výjimky: `raise` funkce](the-raise-function.md)
- [Výjimky: `failwith` Funkce](the-failwith-function.md)
