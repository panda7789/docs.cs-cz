---
title: 'Výjimky: Funkce failwith (F#)'
description: "Zjistěte, jak funkce 'failwith' vygeneruje výjimku F #."
ms.date: 05/16/2016
ms.openlocfilehash: 59f7129faf38668dd7390790e22d25f37c129750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563325"
---
# <a name="exceptions-the-failwith-function"></a>Výjimky: Funkce failwith

`failwith` Funkce vyvolá výjimku F #.


## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Poznámky
*Řetězec chybové zprávy* v předchozí syntaxe je řetězcový literál nebo se hodnota typu `string`. Bude `Message` vlastnosti výjimky.

Výjimka, která je generován `failwith` je `System.Exception` výjimky, která je odkaz, který má název `Failure` v F # – kód. Následující kód ukazuje použití `failwith` vyvolá výjimku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Typy výjimek](exception-types.md)

[Výjimky: `try...with` výraz](the-try-with-expression.md)

[Výjimky: `try...finally` výraz](the-try-finally-expression.md)

[Výjimky: `raise` – funkce](the-raise-function.md)
