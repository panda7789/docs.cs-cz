---
title: <paramref>– Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287308"
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

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
