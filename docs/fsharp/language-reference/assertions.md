---
title: "Kontrolní výrazy (F#)"
description: "Další informace o použití výrazu 'assert' jako ladění funkci pro testování výrazy v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a>Kontrolní výrazy

`assert` Výrazu je ladění funkce, která můžete použít k otestování výrazu. Kontrolní výrazy při selhání v režimu ladění, generuje dialogové okno chyby systému.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Poznámky

`assert` Výraz má typ `bool -> unit`.

V předchozích syntaxi *podmínku* představuje logický výraz, který má být testována. Pokud je výsledkem výrazu `true`, pokračuje v provádění neovlivní. Pokud je vyhodnocen jako `false`, generuje se dialogové okno chyby systému. Dialogové okno chyby má popisek, který obsahuje řetězec **kontrolní výraz**. Dialogové okno obsahuje trasování zásobníku, která určuje, kde došlo k selhání kontrolní výraz.

Kontrola kontrolní výraz je povoleno pouze v případě, že při kompilaci v režimu ladění; To znamená pokud konstanta `DEBUG` je definována. V systému projektu, ve výchozím nastavení `DEBUG` konstanta je definována v konfiguraci ladění ale není v rámci konfigurace verze.

Chyba předpokladu selhání nemůže být zachycena pomocí zpracování výjimek F #.

>[!NOTE]
`assert` Funkce přeloží na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití `assert` výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F #](index.md)
