---
title: Zkratky typů
description: Další informace o F# typ – zkratky poskytnout smysluplnějšího názvu typu Pokud chcete, aby byl kód lépe čitelný.
ms.date: 05/16/2016
ms.openlocfilehash: 0deaef789367aad413e5a537bf7164034e1275c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683337"
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

Zkratky typů není zachováno v kódu rozhraní .NET Framework MSIL. Proto při použití F# sestavení z jiného jazyka rozhraní .NET Framework, musíte použít název základního typu pro – zkratka typu.

Zkratky typů lze použít také na měrné jednotky. Další informace najdete v tématu [měrné jednotky](units-of-measure.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)