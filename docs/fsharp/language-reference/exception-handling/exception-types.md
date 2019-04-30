---
title: Typy výjimek
description: Zjistěte, jak definovat a používat F# typy výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772720"
---
# <a name="exception-types"></a>Typy výjimek

Existují dvě kategorie výjimek v F#: typy výjimek .NET a F# typy výjimek. Toto téma popisuje, jak definovat a používat F# typy výjimek.

## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typ výjimky* je název nové F# typ výjimky a *typ argumentu* představuje typ argumentu, který může být zadán při vyvolání výjimky tohoto typu. Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.

Typické definici F# výjimek má následující podobu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Výjimka tohoto typu můžete vygenerovat pomocí `raise` fungovat, následovně.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Můžete použít F# typ výjimky přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ výjimky, který definujete pomocí `exception` – klíčové slovo v F# je nový typ, který dědí z `System.Exception`.

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Výjimky: `raise` – funkce](the-raise-function.md)
- [Hierarchie výjimek](https://msdn.microsoft.com/library/z4c5tckx.aspx)