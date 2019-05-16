---
title: 'Výjimky: Funkce failwith'
description: Zjistěte, jak funkce "failwith" generuje F# výjimky.
ms.date: 05/16/2016
ms.openlocfilehash: 08107966ddc2f55625347deb92d224b286df7761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641953"
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
