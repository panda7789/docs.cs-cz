---
title: Identifikátory zdrojového řádku, souboru a cesty
description: Naučte se používat předdefinované hodnoty F# identifikátorů, které vám umožní přístup ke zdrojovému číslu, adresáři a názvu souboru ve vašem kódu.
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216744"
---
# <a name="source-line-file-and-path-identifiers"></a>Identifikátory zdrojového řádku, souboru a cesty

Identifikátory `__LINE__` `__SOURCE_DIRECTORY__` a jsoupředdefinovanéhodnoty,kterévámumožnípřístupkezdrojovémučísluřádku,adresářianázvusouboruvevašemkódu.`__SOURCE_FILE__`

## <a name="syntax"></a>Syntaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Poznámky

Každá z těchto hodnot je typu `string`.

Následující tabulka shrnuje identifikátory zdrojového řádku, souboru a cesty, které jsou k dispozici v F#. Tyto identifikátory neobsahují makra preprocesoru; jsou to předdefinované hodnoty, které kompilátor rozpozná.

|Předdefinovaný identifikátor|Popis|
|---------------------|-----------|
|`__LINE__`|Vyhodnotí na aktuální číslo řádku a zváží `#line` direktivy.|
|`__SOURCE_DIRECTORY__`|Vyhodnotí na aktuální úplnou cestu ke zdrojovému adresáři, který `#line` zvažuje direktivy.|
|`__SOURCE_FILE__`|Vyhodnotí na aktuální název zdrojového souboru bez cesty, kde se `#line` dotýkají direktiv.|

Další informace o `#line` direktivě naleznete v tématu [direktivy kompilátoru](compiler-directives.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití těchto hodnot.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Výstup:

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Viz také:

- [Direktivy kompilátoru](compiler-directives.md)
- [Referenční dokumentace jazyka F#](index.md)
