---
title: 'Výjimky: Funkce failwith (F#)'
description: Zjistěte, jak "failwith" funkce generuje výjimku F#.
ms.date: 05/16/2016
ms.openlocfilehash: 69a2eb69e0157d3bde8cb8884cb0ae960634dddc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863426"
---
# <a name="exceptions-the-failwith-function"></a>Výjimky: Funkce failwith

`failwith` Funkce generuje výjimku F#.

## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Poznámky

*Řetězec chybové zprávy* v předchozí syntaxi je řetězcový literál nebo hodnota typu `string`. Stane `Message` vlastnosti výjimky.

Výjimka, která je generován `failwith` je `System.Exception` výjimku, která je odkaz, který má název `Failure` v kódu F#. Následující kód ukazuje použití `failwith` vyvolají výjimku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` výraz](the-try-finally-expression.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)
