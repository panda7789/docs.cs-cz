---
title: 'Výjimky: Funkce invalidArg'
description: Zjistěte, jak F# "invalidArg" funkce generuje výjimku argument.
ms.date: 05/16/2016
ms.openlocfilehash: 7fd8d48b80970dbbafc0c23a478b4ccf3490f3ee
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613333"
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
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)
- [Výjimky: `failwith` – Funkce](the-failwith-function.md)