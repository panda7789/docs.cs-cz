---
title: Identifikátory zdrojového řádku, souboru a cesty
description: Zjistěte, jak použít integrovaný F# hodnoty identifikátorů, které vám umožní přístup ke zdroji řádek číslo, adresář a název souboru ve vašem kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152056"
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

Následující tabulka shrnuje zdrojového řádku, souboru a cestu identifikátory, které jsou k dispozici v F#. Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznávány kompilátorem.

|Předdefinovaný identifikátor|Popis|
|---------------------|-----------|
|`__LINE__`|Aktuální číslo řádku, je vyhodnocen jako zvážení `#line` direktivy.|
|`__SOURCE_DIRECTORY__`|Vyhodnotí jako aktuální úplná cesta zdrojového adresáře, vzhledem k tomu `#line` direktivy.|
|`__SOURCE_FILE__`|Vyhodnotí jako aktuální název zdrojového souboru, bez jeho cestu vzhledem k tomu `#line` direktivy.|

Další informace o `#line` direktiv, viz [direktivy kompilátoru](compiler-directives.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití těchto hodnot.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Výstup:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Viz také:

- [Direktivy kompilátoru](compiler-directives.md)
- [Referenční dokumentace jazyka F#](index.md)
