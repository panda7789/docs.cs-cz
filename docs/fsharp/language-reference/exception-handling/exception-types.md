---
title: Typy výjimek (F#)
description: 'Zjistěte, jak definovat a používat typy výjimek F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858818"
---
# <a name="exception-types"></a>Typy výjimek

Existují dvě kategorie výjimek v jazyce F #: typy výjimek .NET a typy výjimek F #. Toto téma popisuje, jak definovat a používat typy výjimek F #.

## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typ výjimky* je název nového F # výjimka typu, a *typ argumentu* představuje typ argumentu, který může být zadán při vyvolání výjimky tohoto typu. Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.

Typické definici pro výjimku F # se podobá následující.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Výjimka tohoto typu můžete vygenerovat pomocí `raise` fungovat, následovně.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Typ výjimky F # můžete použít přímo ve filtrech v `try...with` výrazu, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ výjimky, který definujete pomocí `exception` – klíčové slovo v jazyce F # je nový typ, který dědí z `System.Exception`.

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)
- [Hierarchie výjimek](https://msdn.microsoft.com/library/z4c5tckx.aspx)
