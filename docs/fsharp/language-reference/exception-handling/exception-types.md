---
title: Typy výjimek (F#)
description: 'Zjistěte, jak definovat a používat výjimky typů F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564035"
---
# <a name="exception-types"></a>Typy výjimek

Existují dvě kategorie výjimek v jazyce F #: typy .NET výjimky a výjimky typů F #. Toto téma popisuje postup definice a používání výjimka typů F #.


## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi *typ výjimky* je název nové F # výjimka typu, a *typ argumentu* představuje typ argument, který můžete zadat při vyvolat výjimku tohoto typu. Můžete zadat několik argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.

Typické definici výjimku F # vypadá přibližně takto.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

K výjimce typu můžete vygenerovat pomocí `raise` fungovat, následujícím způsobem.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Typ výjimky F # můžete použít přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Typ výjimky, které definujete s `exception` – klíčové slovo v F # je nový typ, který dědí z `System.Exception`.


## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Výjimky: `raise` – funkce](the-raise-function.md)

[Hierarchie výjimek](https://msdn.microsoft.com/library/z4c5tckx.aspx)
