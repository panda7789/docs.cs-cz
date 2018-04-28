---
title: 'Výjimky: Funkce failwith (F#)'
description: "Zjistěte, jak funkce 'failwith' vygeneruje výjimku F #."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: af1e3b7dc96b3b822e2e19b7bac435940d15922f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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
