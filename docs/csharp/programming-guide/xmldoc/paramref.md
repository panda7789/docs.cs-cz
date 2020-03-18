---
title: <paramref>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793405"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (průvodce programováním Jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru, na který se má odkazovat. Název uzavřete do uvozovek (" ").

## <a name="remarks"></a>Poznámky

Značka \<paramref> vám dává způsob, jak označit, že slovo \<v komentářích kódu, například v souhrnné> nebo \<poznámky> bloku odkazuje na parametr. Soubor XML lze zpracovat pro formátování tohoto slova nějakým odlišným způsobem, například tučným písmem nebo kurzívou.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
