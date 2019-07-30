---
title: Zkratky typů
description: Přečtěte F# si o zkratkách typů, aby bylo možné zadat smysluplnější název, aby bylo snazší číst kód.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630210"
---
# <a name="type-abbreviations"></a>Zkratky typů

*Zkratka typu* je alias nebo alternativní název pro typ.

## <a name="syntax"></a>Syntaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Poznámky

Můžete použít zkratky typů k poskytnutí smysluplného názvu typu, aby bylo snazší číst kód. Můžete je také použít k vytvoření snadno použitelného názvu pro typ, který je jinak nenáročný na zápis. Kromě toho můžete použít zkratky typů pro snadnější změnu nadřazeného typu bez změny veškerého kódu, který používá typ. Následuje zkratka jednoduchého typu.

Dostupnost zkratek typu se nastaví na `public`výchozí hodnotu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Zkratky typů mohou zahrnovat obecné parametry, jako v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

V předchozím kódu `Transform` je zkratka typu, která představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.

V kódu .NET Framework jazyka MSIL nejsou zachovány zkratky typů. Proto pokud použijete F# sestavení z jiného .NET Framework jazyka, je nutné použít název základního typu pro zkratku typu.

Zkratky typů lze také použít pro měrné jednotky. Další informace najdete v tématu měrné [jednotky](units-of-measure.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
