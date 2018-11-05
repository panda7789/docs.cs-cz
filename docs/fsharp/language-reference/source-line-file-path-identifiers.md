---
title: Identifikátory zdrojového řádku, souboru a cesty (F#)
description: Další informace o použití integrovaných F# hodnoty identifikátorů, které vám umožní přístup k číslo zdrojového řádku, adresář a název souboru ve vašem kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865124"
---
# <a name="source-line-file-and-path-identifiers"></a>Identifikátory zdrojového řádku, souboru a cesty

Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup ke zdrojové řádek číslo, adresář a název souboru ve vašem kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Poznámky

Každá z těchto hodnot obsahuje typ `string`.

Následující tabulka shrnuje zdrojového řádku, souboru a cesty identifikátorů, které jsou k dispozici v jazyce F#. Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznávány kompilátorem.

|Předdefinovaný identifikátor|Popis|
|---------------------|-----------|
|`__LINE__`|Aktuální číslo řádku, je vyhodnocen jako zvážení `#line` direktivy.|
|`__SOURCE_DIRECTORY__`|Vyhodnotí jako aktuální úplná cesta zdrojového adresáře, vzhledem k tomu `#line` direktivy.|
|`__SOURCE_FILE__`|Vyhodnotí na aktuální název zdrojového souboru a jeho cestu vzhledem k tomu `#line` direktivy.|
Další informace o `#line` direktiv, viz [direktivy kompilátoru](compiler-directives.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití těchto hodnot.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Výstup:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Viz také:

- [Direktivy kompilátoru](compiler-directives.md)
- [Referenční dokumentace jazyka F#](index.md)
