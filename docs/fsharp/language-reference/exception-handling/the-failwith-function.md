---
title: 'Výjimky: Funkce failwith'
description: Přečtěte si, jak funkce failwith generuje F# výjimku.
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630322"
---
# <a name="exceptions-the-failwith-function"></a>Výjimky: Funkce failwith

`failwith` Funkce vygeneruje F# výjimku.

## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Poznámky

*Řetězec chybové zprávy* v předchozí syntaxi je řetězcový literál nebo hodnota typu `string`. Bude se jednat o vlastnostvýjimky.`Message`

Výjimka, která je generována `failwith` nástrojem `System.Exception` je výjimka, která je odkazem, který má název `Failure` v F# kódu. Následující kód ilustruje použití `failwith` k vyvolání výjimky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
- [Výjimky: `raise` funkce](the-raise-function.md)
