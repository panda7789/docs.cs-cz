---
title: Identifikátory zdrojového řádku, souboru a cesty (F#)
description: 'Naučte se používat integrované F # hodnoty identifikátorů, které vám umožní přístup k číslo řádku zdroje, adresář a název souboru ve svém kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="source-line-file-and-path-identifiers"></a>Identifikátory zdrojového řádku, souboru a cesty

Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup k zdroj řádku číslo, adresář a název souboru ve svém kódu.


## <a name="syntax"></a>Syntaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Poznámky
Všechny tyto hodnoty má typ `string`.

Následující tabulka shrnuje zdrojového řádku, souboru a cesty identifikátorů, které jsou k dispozici v F #. Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznány kompilátorem.

|Předdefinované identifikátor|Popis|
|---------------------|-----------|
|`__LINE__`|Výsledkem je aktuální číslo řádku, s `#line` direktivy.|
|`__SOURCE_DIRECTORY__`|Vyhodnotí jako aktuální úplnou cestu zdrojového adresáře s `#line` direktivy.|
|`__SOURCE_FILE__`|Vyhodnotí aktuální název zdrojového souboru a jeho cesty s `#line` direktivy.|
Další informace o `#line` direktivy, viz [direktivy kompilátoru](compiler-directives.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití těchto hodnot.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Výstup:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Viz také
[Direktivy kompilátoru](compiler-directives.md)

[Referenční dokumentace jazyka F#](index.md)
