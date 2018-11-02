---
title: Zkratky typů (F#)
description: 'Další informace o F # zkratky typů poskytnout smysluplnějšího názvu typu Pokud chcete, aby byl kód lépe čitelný.'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842421"
---
# <a name="type-abbreviations"></a>Zkratky typů

A *– zkratka typu* je alias nebo alternativní název typu.

## <a name="syntax"></a>Syntaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Poznámky

Zkratky typů můžete poskytnout typu výstižnější název, pokud chcete, aby byl kód lépe čitelný. Můžete také využít k vytvoření snadné použití názvu pro typ, který je jinak náročné vypsat. Kromě toho vám pomůže zkratky typů usnadňují změna základního typu bez úpravy veškerý kód, který používá typ. Toto je zkratka jednoduchého typu.

Výchozí hodnota dostupnost zkratek typů `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Zkratky typů můžete zahrnout obecné parametry, jak ukazuje následující kód.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

V předchozím kódu `Transform` je – zkratka typu, který představuje funkci, která přijímá jeden argument typu a, který vrací jedinou hodnotu stejného typu.

Zkratky typů není zachováno v kódu rozhraní .NET Framework MSIL. Proto při použití sestavení F # z jiného jazyka rozhraní .NET Framework, musíte použít název základního typu pro – zkratka typu.

Zkratky typů lze použít také na měrné jednotky. Další informace najdete v tématu [měrné jednotky](units-of-measure.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
