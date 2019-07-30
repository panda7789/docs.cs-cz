---
title: Typy výjimek
description: Naučte se definovat a používat F# typy výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630313"
---
# <a name="exception-types"></a>Typy výjimek

Existují dvě kategorie výjimek v F#: typy výjimek rozhraní .NET a F# typy výjimek. Toto téma popisuje, jak definovat a používat F# typy výjimek.

## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *Typ výjimky* název nového F# typu výjimky a *typ argumentu* představuje typ argumentu, který lze zadat při vyvolání výjimky tohoto typu. Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.

Typická definice pro F# výjimku se podobá následujícímu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Výjimku tohoto typu můžete vygenerovat pomocí `raise` funkce následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Typ F# výjimky můžete použít přímo ve filtrech ve `try...with` výrazu, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ výjimky, který definujete pomocí `exception` klíčového slova v, F# je nový typ, který `System.Exception`dědí z.

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Výjimky: `raise` funkce](the-raise-function.md)
- [Hierarchie výjimek](https://msdn.microsoft.com/library/z4c5tckx.aspx)
