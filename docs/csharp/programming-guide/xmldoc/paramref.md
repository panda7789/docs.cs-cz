---
title: <paramref>– Průvodce programováním v C#
description: Přečtěte si o <paramref> značce XML. Tato značka poskytuje způsob, jak označit, že slovo v kódu je parametr.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381837"
---
# <a name="paramref-c-programming-guide"></a>\<paramref>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru, na který se má odkazovat Název uzavřete do uvozovek ("").

## <a name="remarks"></a>Poznámky

`<paramref>`Značka poskytuje způsob, jak označit, že slovo v komentářích kódu, například v `<summary>` bloku nebo, `<remarks>` odkazuje na parametr. Soubor XML lze zpracovat pro formátování tohoto slova nějakým způsobem, například tučným písmem nebo kurzívou.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
