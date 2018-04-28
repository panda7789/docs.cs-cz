---
title: Zkratky typů (F#)
description: 'Další informace o F # zkratky typů pojmenovat typu smysluplnější abyste snadněji kódu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf17ee9795947fdc11fe958f09d52f5730b95bf8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-abbreviations"></a>Zkratky typů

A *– zkratka typu* je alias nebo alternativní název typu.

## <a name="syntax"></a>Syntaxe

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a>Poznámky
Zkratky typů můžete poskytnout typu více smysluplný název, abyste snadněji kódu. Můžete je také použít k vytvoření snadno použitelný názvu pro typ, který je jinak náročná zapsat. Kromě toho aby bylo snazší změna základního typu beze změny jejího kódu, který používá typ můžete zkratky typů. Toto je zkratka jednoduchého typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Zkratky typů může zahrnovat obecné parametry, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

V předchozí kód `Transform` je zkratka typu, který představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.

Zkratky typů nejsou zachována v rozhraní .NET Framework MSIL kódu. Proto při použití sestavení F # z jiný jazyk rozhraní .NET Framework, musíte použít název základního typu pro zkratka typu.

Zkratky typů můžete použít taky u měrné jednotky. Další informace najdete v tématu [měrné jednotky](units-of-measure.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

