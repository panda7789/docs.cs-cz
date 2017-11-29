---
title: "Výjimky: Funkce failwith (F#)"
description: "Zjistěte, jak funkce 'failwith' vygeneruje výjimku F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2017
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
