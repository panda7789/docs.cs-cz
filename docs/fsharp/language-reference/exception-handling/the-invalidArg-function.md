---
title: 'Výjimky: Funkce invalidArg (F#)'
description: Zjistěte, jak "invalidArg" funkce jazyka F# vygeneruje výjimka argumentu.
ms.date: 05/16/2016
ms.openlocfilehash: 8bf65fae9392a88205e3cdec8b7d7a3ff42f8416
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44180316"
---
# <a name="exceptions-the-invalidarg-function"></a>Výjimky: Funkce invalidArg

`invalidArg` Funkce generuje výjimku argument.

## <a name="syntax"></a>Syntaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Poznámky

Název parametru v předchozí syntaxi je řetězec názvu parametru, jehož argument byl neplatný. *Řetězec chybové zprávy* řetězcový literál nebo je hodnota typu `string`. Stane `Message` vlastnost v objektu výjimky.

Výjimky generované `invalidArg` je `System.ArgumentException` výjimky. Následující kód ukazuje použití `invalidArg` vyvolají výjimku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Výstup je následující, za nímž následuje trasování zásobníku (nezobrazení).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` výraz](the-try-finally-expression.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)
- [Výjimky: `failwith` – funkce](the-failwith-function.md)
