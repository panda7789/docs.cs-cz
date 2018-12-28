---
title: 'Výjimky: Funkce failwith'
description: Zjistěte, jak funkce "failwith" generuje F# výjimky.
ms.date: 05/16/2016
ms.openlocfilehash: 05d385ddfc98a910779a6f59949a7187c38f0812
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610109"
---
# <a name="exceptions-the-failwith-function"></a>Výjimky: Funkce failwith

`failwith` Funkce generuje F# výjimky.

## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Poznámky

*Řetězec chybové zprávy* v předchozí syntaxi je řetězcový literál nebo hodnota typu `string`. Stane `Message` vlastnosti výjimky.

Výjimka, která je generován `failwith` je `System.Exception` výjimku, která je odkaz, který má název `Failure` v F# kódu. Následující kód ukazuje použití `failwith` vyvolají výjimku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)