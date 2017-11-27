---
title: "Typy výjimek (F#)"
description: "Zjistěte, jak definovat a používat výjimky typů F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
